---
title: "Basic server! Can't find a good tutorial"
date: 2014-05-30
forum: Server Platforms
---

### Post by apple6 on 2014-05-30
All I'm currently trying to do is access my CLI from one computer to another, on my home network. Once I've got that I'll move onto accessing from external networks, automating back ups etc. I'm just trying to take baby steps on it. 

I've [followed this tutorial]("https://www.digitalocean.com/community/articles/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu") but I'm just getting errors. 

I have two computers, one running Ubuntu 14 and the other running Mint Mate. I'm trying to access the Mint one from the Ubuntu one, though I doubt there's any difference if it was the other way around. 

I've installed ssh on both of them using : 

```

sudo apt-get install openssh-server openssh-client
```

I'm really lost though, everyone say's how easy it is but I can't get it to work and the guides really aren't step by step enough for someone like me. 

If anyone could give me some advice that would be ace. 

cheers

---

### Post by steeldriver on 2014-05-30
Hello and welcome to the forums

I only scanned the tutorial you linked - it seems pretty good, but it covers a LOT of material - where are you getting stuck? what **exactly** are the errors you are getting?

IMHO you should start with basic password-based authentication on the default port and verify everything works BEFORE starting to play with the sshd_config file.

---

### Post by Morbius1 on 2014-05-30
I'll be out most of the day but let's get this started ......

Once the packages get installed you should be able to just access it like this:

_* From CLI on Mint:*_
```
ssh username@ubuntu14-host-name.local
```
[COLOR=#0000cd]* You are using the mDNS qualified ( the .local part ) host name of the Ubuntu machine so replace with real name.*[/COLOR]

Worst case access it by ip address. For example:
```
ssh username@192.168.0.100
```

_* From Caja run this in the terminal:*_
```
caja ssh://username@ubuntu14-host-name.local
```
OR
```
caja ssh://username@192.168.0.100
```

[COLOR=#0000cd] **Note**: You may get an error message that looks something like this:[/COLOR]
> The authenticity of host 'bravo.local (192.168.0.100)' can't be established.
ECDSA key fingerprint is 6f:ac:67:4f:10:20:ff:02:3b:27:34:01:85:3c:03:4d.
Are you sure you want to continue connecting (yes/no)?
Just say yes.

---

### Post by tgalati4 on 2014-05-30
It helps to set up static IP's on your computers and put the IP's in your /etc/hosts file on each computer.  It's old school, but that makes things easier.

---

