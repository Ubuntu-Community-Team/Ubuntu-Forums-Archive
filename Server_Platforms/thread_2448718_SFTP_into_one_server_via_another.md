---
title: "SFTP into one server via another?"
date: 2020-08-12
forum: Server Platforms
---

### Post by uc50_ic4more on 2020-08-12
Hello -

I have three machines:

DESKTOP

SERVER1, which only accepts ssh from...

SERVER2

Currently I can ssh into SERVER1 "directly" with this command from a terminal on DESKTOP:

ssh -t my_username@SERVER2 ssh my_username@SERVER1

I would like, however, to access SERVER1 using Nautilus on DESKTOP. Normally I'd click "Other Locations" and input sftp://my_username@SERVER_IP. Does anyone know the correct command to input into Nautilus that would effectively log me into SERVER1 via SERVER2 like my ssh command does?

Thanks!

---

### Post by uc50_ic4more on 2020-08-12
As usual, 30 seconds after posting here I found the solution. For those interested:

In ~/.ssh/config:

Host SERVER1
    HostName SERVER1_IP
    User my_username
    Port 22
    IdentityFile ~/.ssh/my_key
    IdentitiesOnly yes
    ProxyCommand ssh -W %h:%p SERVER2
    ForwardAgent yes

Host SERVER2
    HostName SERVER2_IP
    User my_username
    Port 22
    IdentityFile ~/.ssh/my_key
    IdentitiesOnly yes

In Nautilus I simply entered ssh://my_username@SERVER1

---

### Post by TheFu on 2020-08-12
I would use X11 forwardng:
```
ssh -X my_username@SERVER2 nautilus  &
```

Or better, rsync.

---

