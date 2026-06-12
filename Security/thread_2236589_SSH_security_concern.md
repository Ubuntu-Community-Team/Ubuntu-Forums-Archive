---
title: "SSH security concern"
date: 2014-07-27
forum: Security
---

### Post by yos2 on 2014-07-27
Hi, nub ubuntu desktop user, used Linux years back, re-entering the scene.. running Ubuntu 14.04.1 LTS (trusty)

I noticed a folder under /tmp named: /tmp/ssh-xxxxxxxxxxxx with an ssh agent "agent.nnnn" created today.

after reading this [post]("http://ubuntuforums.org/showthread.php?t=1288051") it appears to me that I have a security concern on my hands. 

To the best of my recollection, I had not enabled, or disabled SSH after my install. My questions are:

1. Does Ubuntu desktop default install, enable SSH? If it does, how do I disable it.
2. Any way for me to identify who/what created that agent, and what was accessed?
3. How do I get rid of the agent?

Thanks a lot,

Yos

---

### Post by bashiergui on 2014-07-27
> after reading this post it appears to me that I have a security concern on my hands. Not sure where you got the security concern from that thread. I see no security concern.
> 1. Does Ubuntu desktop default install, enable SSH? If it does, how do I disable it.The ssh client is installed by default in all *buntus. This allows you to ssh to another server, but it doesn not allow anyone to connect to your computer. You have to install the ssh server manually if you want others to ssh to your computer. > 2. Any way for me to identify who/what created that agent, and what was accessed?Read the thread you linked carefully. Unspawn explained that it's a folder that the ssh client will use if you ever connect to another server. The folder's existence does not necessarily indicate that you have *used* ssh, only that the client is *installed*.> 3. How do I get rid of the agent?```
sudo apt-get remove openssh-client
```

---

### Post by Lars Noodén on 2014-07-29
That temp file is from the [ssh-agent](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-agent.1.html) that Ubuntu starts for you as part of the graphical interface.  If you don't want the agent running you could probably turn it off by editing the file */etc/X11/Xsession.options* and commenting out the line with *use-ssh-agent*.  I haven't tried that but it looks to be the way to go.  

That said the agent does not do anything unless you tell it to.  If you just use the SSH client without first loading any keys into the agent, it is ignored.  To load a private key into the agent for re-use during that X11 session, use [ssh-add](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-add.1.html).  

Also, the SSH client is inactive unless you manually run it.  The SSH server is another matter, but that is not installed by default and you have to go out of your way to install it by adding the package openssh-server.  

In short, everything is fine as you found it.

---

