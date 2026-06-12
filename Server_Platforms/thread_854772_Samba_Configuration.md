---
title: "Samba Configuration"
date: 2008-07-09
forum: Server Platforms
---

### Post by TreeFinger on 2008-07-09
Hello, I have a Samba server set up. I am going to explain what I would like to do. I am wondering if it is possible.

For the first thing, I do not want my 2 users to have to enter a password to access the share.

I'd like both users to have their own writable share but be readable for each other. 

One user has Windows, the other using Ubuntu.


Is this possible?

---

### Post by doogy2004 on 2008-07-10
yes, very possible with very little configuration needed

to start the user names must be the same on every computer.  so user: "meadmin" must have the same username and password on every computer that needs access to the samba server.  please note in Windows user: "meadmin" is different from user: "Me Admin" and if the password is changed on the client computer the password will need to be changed on the server.

---

### Post by TreeFinger on 2008-07-12
Thank for your reply. I don't think my windows computer has a username. Unless it is Administrator? Also, no password is required for the windows computer..

I don't want my 2 users to have to enter anything to access the shares.. I'm not sure if I made that clear.

Is that still possible?

2 Shares which are both readable by my two users
1 share is writable for user A
1 share is writable for user B

---

### Post by spuncut on 2008-07-12
> #2 : Why is it impossible to put in the credentials, when asked, and get access to any Samba share..??

---

### Post by TreeFinger on 2008-07-12
Not sure if you are talking to me or not..

I don't want my users to have to bother with inputting a password.

---

### Post by doogy2004 on 2008-07-12
> **TreeFinger said:**
> Thank for your reply. I don't think my windows computer has a username. Unless it is Administrator? Also, no password is required for the windows computer..

I don't want my 2 users to have to enter anything to access the shares.. I'm not sure if I made that clear.

Is that still possible?

2 Shares which are both readable by my two users
1 share is writable for user A
1 share is writable for user B

Does each user use a different computer or do both the users use each computer?

---

### Post by spuncut on 2008-07-12
I'll better explain, I'am having an almost similar problem. I can ONLY access a Sambashare which credentials corresponds with a windows account. I would like to access ANY Sambashare, but when I get the login sign in windows well...I can forget it...how come..??

---

### Post by doogy2004 on 2008-07-12
> **spuncut said:**
> I'll better explain, I'am having an almost similar problem. I can ONLY access a Sambashare which credentials corresponds with a windows account.

This is a security issue, one user should never be able to access another user's files.  However multiple users can access the same shares depending on how one configures the share/server.

> **spuncut said:**
> I would like to access ANY Sambashare

This can be done, please post your current configuration with ```
cat /etc/samba/smb.conf
```

> **spuncut said:**
> but when I get the login sign in windows well...I can forget it...how come..??

What does this sentence mean?  You forget what your login credentials are when you attempt to login to the computer? I don't quite understand what you mean, please elaborate.

---

### Post by TreeFinger on 2008-07-12
> **doogy2004 said:**
> Does each user use a different computer or do both the users use each computer?

Both users use a different computer.

---

### Post by doogy2004 on 2008-07-12
> **TreeFinger said:**
> Both users use a different computer.

What version of Windows are you using? (e.g. XP Home, XP Pro, Vista Business, Vista Home, etc)

---

### Post by nix4me on 2008-07-12
Just remove the need for login on samba.  Change security=user to security=share in the /etc/samba/smb.conf file.  That will eliminate the need for authentication.

---

### Post by TreeFinger on 2008-07-12
> **doogy2004 said:**
> What version of Windows are you using? (e.g. XP Home, XP Pro, Vista Business, Vista Home, etc)

XP Pro


> **nix4me said:**
> Just remove the need for login on samba.  Change security=user to security=share in the /etc/samba/smb.conf file.  That will eliminate the need for authentication.

I have got my share to have no need for auth but I want to have 2 shares with no need for pw with different permissions for each user.

---

### Post by doogy2004 on 2008-07-12
> **TreeFinger said:**
> XP Pro




I have got my share to have no need for auth but I want to have 2 shares with no need for pw with different permissions for each user.

please post the contents of your samba configuration

```
cat /etc/samba/smb.conf
```

---

### Post by TreeFinger on 2008-07-12
> **doogy2004 said:**
> please post the contents of your samba configuration

```
cat /etc/samba/smb.conf
```

```

# This is /etc/samba/smb.conf

[global]
        netbios name = SHAREFILES
        security = share
        public = yes
        guest ok = no
        workgroup = WORKGROUP
        log level = 1
        max log size = 1000
        socket options = TCP_NODELAY IPTOS_LOWDELAY
[test]
        browseable = yes
        read only = no
        guest ok = yes
        path = /home/public

```

---

### Post by doogy2004 on 2008-07-12
> **TreeFinger said:**
> ```

# This is /etc/samba/smb.conf

[global]
        netbios name = SHAREFILES
        security = share
        public = yes
        guest ok = no
        workgroup = WORKGROUP
        log level = 1
        max log size = 1000
        socket options = TCP_NODELAY IPTOS_LOWDELAY
[test]
        browseable = yes
        read only = no
        guest ok = yes
        path = /home/public

```

simply add another share and point it to a different path such as

```
[test2]
  browseable = yes
  read only = no
  guest ok = yes
  path = /home/public2
```

Each section that startes with a [word] starts the configuration for a new share.  Except for [global] or course.

---

### Post by TreeFinger on 2008-07-12
> **doogy2004 said:**
> simply add another share and point it to a different path such as

```
[test2]
  browseable = yes
  read only = no
  guest ok = yes
  path = /home/public2
```

Each section that startes with a [word] starts the configuration for a new share.  Except for [global] or course.

yes, i understand how to create different shares. I would like share X be viewable by bother users A B but only writable for user A. share Y viewable by both users A B but writable for user B

---

### Post by doogy2004 on 2008-07-12
> **TreeFinger said:**
> yes, i understand how to create different shares. I would like share X be viewable by bother users A B but only writable for user A. share Y viewable by both users A B but writable for user B

try changing the owner of shares to match which user you want to be able to write to. then change the permissions to allow other to read and execute.  if this does not work then you will need a more indepth configuration and you will need to know/change the user names on the clients to a unix friendly name and password, then use TweakUI to auto login with the users on each computer.

---

### Post by spuncut on 2008-07-12
I'am going to start a new thread..cya

---

