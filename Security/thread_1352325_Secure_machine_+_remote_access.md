---
title: "Secure machine + remote access?"
date: 2009-12-11
forum: Security
---

### Post by Casualuser on 2009-12-11
Posted something similar to this last year, but I didn't pursue it any further.  Now I am moving into an apartment, and the manager is a former IT guy.  I will be away most of the time in other cities, and I want to leave the computer on at home to download HD tv shows etc that I can bring with me to watch later.  

The computer will be on 24/7.  Here's what I want.

1. Password protection from someone trying to log on.

2. Any way to protect the password/data via encryption etc?  I don't want someone to be able to reset the password easily.  I'd like to make it difficult enough to get in so it won't worth their time.

3. Hard drive encryption.  Not sure if I'll be using internals or externals.  If someone pops the case open, I want the drive to be useless for him.

3. Remote access.  I'd like to logon from my hotel to check up on things(download status, maybe check a security cam hooked up etc).

I know this probably sounds like overkill, but if it's not difficult to setup, why not do it? 

Thanks:)

---

### Post by cdenley on 2009-12-11
1. Ubuntu is password-protected by default. As with any OS, if they have full access to the filesystem, they can reset the password.

2. If /etc/shadow resides on an encrypted partition, then even with physical access, they wouldn't be able to change your password unless they have access to a root or admin account (or manage to retrieve your encryption key from memory).

3. You can encrypt filesystems at install using the alternative installation disc.

4. SSH is the standard way for accessing your system remotely.
```

sudo apt-get install openssh-server

```
Don't set a root password, and only use strong passwords when enabling any kind of remote authentication. Better yet, only allow key authentication.

---

### Post by SilverTFOF on 2009-12-11
I was pretty much in the same boat up until recently.  I bought a Mini 10v laptop (not suggesting you do this), and wanted most of the same things.  Cdenley is exactly right.  OpenSSH is the way to go for remote access.  There are plenty of tuts on the interweb; just make sure you setup for public key logins.  I've found that Unison is an excellent program to keep files sync'd between the two machines.  The only other thing I would suggest is setting up a VPN server.  It can be a tricky, but through that it'll be like you're at home.  If you don't want to go through that hassle, learn which logs you need to check.  Cheers!

---

### Post by Lars Noodén on 2009-12-12
As cdenley  mentioned the standard way for secure remote access is to use OpenSSH-server.  Be sure to disable remote root login.  Using keys with good passphrases for authentication helps prevent unwanted access. 

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

SSH supports port forwarding / tunelling and SOCKS proxies.  Some applications support SOCKS proxies, so you can even use ssh to connect back to your machine with other applications.  For example, firefox can use socks proxies.  

[http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)
[http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/](http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/)
[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

---

### Post by Cheesemill on 2009-12-12
Physical Access = Root Access

If anyone else can touch your server then it is vulnerable.

By setting up full disk encryption you can limit this vulnerability to only being able to delete/destroy your files instead of gaining access to them.

However, if you set up full disk encryption then you need to be present to type in your pass-phrase every time you need to reboot your machine, which may not be feasible.

Ideally, you need to restrict physical access by locking your machine in a secure location.

---

### Post by BkkBonanza on 2009-12-13
If you're mainly concerned about people getting into your movie files when away then using truecrypt with a nice sized partition is ideal. You will still be able to reboot remotely and then after it's up you login and mount the volume to use it, unmount when done and it's safe. If data is more seriously private then you could consider full disk encryption but as mentioned it's not of much use if power goes out or you need to reboot. Regarding power outage you would need to configure a way to auto power the machine if power is cut. 

And yes, ssh is the way to go. You can use X forwarding with ssh to have a remote desktop or use VNC (tunneled by ssh for security). And you can use ssh to proxy from afar through your machine so that your usage appears to come from your home machine or if you need access to other machines on the home LAN.

If you're on a typical home connection then your IP may be dynamic. In that case you need to configure a dynamic dns name to get connected home as your IP could change. Another way is to have a reverse proxy tunnel to a public server you control. Then connecting to that server with ssh will forward to you home machine as well without needing to open ports for ssh at home or have a static IP. It just depends on your exact details.

---

