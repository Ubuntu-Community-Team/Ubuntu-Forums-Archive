---
title: "Released DebprootStrap and Debproot install bunldes (aka The UserLand Debian Distro)"
date: 2015-02-28
forum: Ubuntu, Linux and OS Chat
---

### Post by moise7864 on 2015-02-28
Hi there,

I just released debprootstrap aka The UserLand Debian Distro aka Stupid Deboostrap Install Bundle Maker (that supports all Ubuntu releases besides Lucid).

Debprootstrap allow the creation of debian/ubuntu container installers for most (any?) linux distributions including tar,gzip and base64 (RHEL,Arch,Debian,Slackware,...)

You can run those container as a regular user and install that cutting-edge software from debian-sid you always wanted in your home folder.

DepProotstrap heavily relies on proot ([http://proot.me](http://proot.me)) to achieve chroot/bind/syscall-intercept (well proot) at the user level.

I made a little snippet that sums it all :

```

user@host$ curl -sS http://debproot.siwhine.net/bundles/install-ubuntu-vivid-amd64-201502280227.bundle|bash -s -- vivid
Installing in vivid...
Installation done
Run vivid/start-container to chroot/proot in your new environment
user@host$ vivid/start-container 
root@vivid-container:~# apt-get moo 
                 (__) 
                 (oo) 
           /------\/ 
          / |    ||   
         *  /\---/\ 
            ~~   ~~   
..."Have you mooed today?"...
root@vivid-container:~# 

```

Links of the project :

[LIST]
[*]DebProotstrap : [https://github.com/gboddin/debprootstrap](https://github.com/gboddin/debprootstrap)
[*]Debproot bundles : [https://debproot.siwhine.net/bundles/](https://debproot.siwhine.net/bundles/)
[*]Proot : [http://proot.me](http://proot.me)
[/LIST]

Let me know what you think !

---

