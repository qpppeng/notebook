##### 生成SSH key
1. 生成密钥
```shell script
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
2.
```shell script
# 如果要生成多个密钥，这里可以指定文件名
> Enter file in which to save the key (/c/Users/qip/.ssh/id_rsa): github
# 直接按 Enter
> Enter passphrase (empty for no passphrase):
> Enter same passphrase again:
The key fingerprint is:
SHA256:xnLo/bbLm82aCmi1xi70JE7icZXSYmc5TQR+Eb9zZwY qipneg.at.1991@gmail.com
The key's randomart image is:
+---[RSA 4096]----+
|      .o+.       |
|     .  .o       |
|     ..=. . E    |
``` 
##### 添加SSH到ssh-agent
1 确认ssh-agent 运行
```shell script
eval $(ssh-agent -s)
> Agent pid 8832
```
2 将私钥添加到ssh-agent
```shell script
ssh-add ~/.ssh/id_rsa
```
##### 将ssh添加到github账号
1 运行 `ll ~/.ssh`,可以看到两个文件, `github`私钥, `github.pub`公钥

2 执行`clip < ~/.ssh/github.pub`, copy公钥到github, settings > SSH and GPG keys  > New SSH key

##### 修改ssh config
> 如果以上生成的是默认配置公私钥文件（`id_rsa`, `id_rsa.pub`），可以忽略以下配置.
> 如果生成自定义的文件继续往下看

1 修改ssh 配置文件
* 在`.ssh/config`中配置，如果没有config，创建一个即可
```
# Work1
Host github.com
HostName github.com
IdentityFile ~/.ssh/github

# Work2
Host bitbucket.org
HostName bitbucket.org
IdentityFile ~/.ssh/bitbucket
```


