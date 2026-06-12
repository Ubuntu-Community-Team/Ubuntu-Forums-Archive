---
title: "SSH Key -- Converting PEM to PUB"
date: 2010-12-14
forum: Server Platforms
---

### Post by trentscott on 2010-12-14
I'm using a code editor called Espresso on Mac that has a built in SFTP feature but doesn't like using .pem keys. Instead, it looks for the keyfile to be ~/.ssh/id_rsa.pub or ~/.ssh/id_dsa.pub. My .pem file is currently at ~/.ssh/TTS.pem. I'm trying to connect to an instance on Amazon EC2 which generated that TTS.pem private key file.

I tried renaming my key from TTS.pem to id_rsa.pub and although I can connect just fine using this renamed key in Terminal, Espresso still doesn't like it. I contacted their support and they told me to regenerate new keys instead of renaming .pem's. Could that have an impact on this?

To generate new keys, can I just run the ssh-keygen command on my Mac and upload/set the generated public key using AWS Management Console?

---

### Post by rubylaser on 2010-12-14
You can either make an rsa key like this...

```
ssh-keygen -t rsa
```
This will create the file in ~/.ssh and it will be named id_rsa.pub

Or, you can extract the public key from the private key using ssh-keygen, copy the new key-pair into place, and test it out.

1. Copy the private SSL key to ~/.ssh/id_ssl.
```
cp ~/.ssh/TTS.pem ~/.ssh/id_ssl
```

2. Extract the public SSH key using ssh-keygen.
```
ssh-keygen -y -f ~/.ssh/id_ssl > ~/.ssh/id_rsa.pub
```

I think that should do it for you. (I'd just do the first one, as it's one command and works great :) )

---

