---
title: "Remotely control a running X session on a computer behind a NAT"
date: 2012-11-07
forum: Security
---

### Post by Willard on 2012-11-07
Hi,

I am trying to remotely control a running X session on a computer running Ubuntu 12.04 LTS.

Here is the setup:

[LIST]
[*]A: Windows 7 64 bit machine (I also have an Arch Linux machine I can use instead, if that is easier)
[*]P: Ubuntu 11.04 server (GNU/Linux 2.6.38-8-server x86_64). This machine has a public IP, and a domain that refers to it (I will call this domain P).
[*]Z: Ubuntu 12.05 LTS desktop (GNU/Linux 3.2.0-27-generic x86_64). This machine is behind a NAT which I cannot configure.
[/LIST]

I have administrative privileges on all these machines; just not the NAT between Z and the world.

The below describes the means by which I tried to achieve the above-stated objective. It is my hope that you can identify where I went wrong, or suggest to me viable alternatives.

[LIST=1]
[*]Configure and start a vnc4server server on Z, following [these instructions](http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/).
[*]Forward port 5902 from P to Z via a reversessh tunnel initiated from Z to P, using this command: 
```
ssh -nNTR 5901:localhost:5901 myusername@P
```
(I tried 5902 as well)
[*]Use [vncviewer](http://www.realvnc.com/download/viewer/) from A to connect to P:1.
[/LIST]

This gives me an error "connect: Connection refused (10061)".

Kind regards,
Willard.

---

### Post by papibe on 2012-11-08
Hi Willard.

I believe that you must map forward 2 ports: 5901 and 5801 (source: [Setting up Remote Desktop]("http://support.godaddy.com/help/article/6012/setting-up-remote-desktop-for-your-centos-or-fedora-linux-dedicated-server#access")).

Take it with a grain of salt though, I'm not very familiar with vnc4server.

Regards.

---

