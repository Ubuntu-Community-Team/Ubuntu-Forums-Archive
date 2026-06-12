---
title: "ssh -X not working"
date: 2007-11-30
forum: Server Platforms
---

### Post by davidmaxwaterman on 2007-11-30
Hi,

I am using ssh between an of several computers (fc6, Apple OS X, MS Window XP) and an ubuntu server (Ubuntu 4.1.2-16ubuntu2).

There are occasions where it would be useful to run s/w that is an X client - eg gvim, mysql-admin, and most recently geany.

When I'm using a system on the same LAN, I just ssh in, set DISPLAY appropriately and I'm good to go.

However, I want to do similarly through a couple of firewalls. I can ssh in without any trouble, but using the -X option to forward X through the tunnel doesn't seem to work.

Things I've checked/tried :
1) done xhost + on X server (local system)
2) check /etc/ssh/ssh_config on ssh server (remote system) for X11Forwarding and it's set to 'yes'
3) set DISPLAY on remote system to ':10' (value of X11DisplayOffset in ssh_config)
4) tried same technique over LAN (also doesn't work), implying it's not a firewall issue
5) tried same technique from OS X to fc6 - also doesn't work
6) same ssh session but with DISPLAY to xserver:0 then it works (xserver is local system - remote to command line).

Error when I start (eg) xeyes, is :

```
Error: Can't open display: :10.0
```

What have I missed?

Max.

---

### Post by Tom Y on 2007-12-03
Have you tried ssh -Y instead of ssh -X ??

---

### Post by The Cog on 2007-12-03
I wonder if you're doing to much. When I ssh between machines, I just do something like these commands:
> ssh -X 1.2.3.4
xeyes
and the eyes appear. It is not necessary to mess around with setting environment variables etc - SSH does it all for you. I wonder if you are breaking all the good work SSH has done by changing the DISPLAY after logging in.

---

### Post by davidmaxwaterman on 2007-12-03
> **The Cog said:**
> I wonder if you're doing to much. When I ssh between machines, I just do something like these commands:

and the eyes appear. It is not necessary to mess around with setting environment variables etc - SSH does it all for you. I wonder if you are breaking all the good work SSH has done by changing the DISPLAY after logging in.

I just tried it, and DISPLAY isn't set when I log in - that's the main reason I set it, since I know it needs to be set for it to work at all.

So, perhaps it is set automatically in your case. Can you check? Do a 'printenv DISPLAY' right after you log in and see what it says.

Thanks.

Max.

---

### Post by davidmaxwaterman on 2007-12-03
> **Tom Y said:**
> Have you tried ssh -Y instead of ssh -X ??

I have now ;) - it doesn't make any difference, ie it still doesn't work :(

---

### Post by The Cog on 2007-12-04
I just tried ssh to another machine with and without the -X option. Without the -X option, $DISPLAY is blank. With the -X option, $DISPLAY is **localhost:10.0**. Interestingly, when I ssh -X to a solaris host that has no GUI software installed, ssh -X does not set $DISPLAY. 

Try using **ssh -X 127.0.0.1** on the Ubuntu server, to see if $DISPLAY is set up correctly then. If it is, I wonder if the clients aren't doing the ssh setup properly - try from another Linux system.
.

---

### Post by davidmaxwaterman on 2007-12-04
> **The Cog said:**
> I just tried ssh to another machine with and without the -X option. Without the -X option, $DISPLAY is blank. With the -X option, $DISPLAY is **localhost:10.0**. Interestingly, when I ssh -X to a solaris host that has no GUI software installed, ssh -X does not set $DISPLAY. 

Try using **ssh -X 127.0.0.1** on the Ubuntu server, to see if $DISPLAY is set up correctly then. If it is, I wonder if the clients aren't doing the ssh setup properly - try from another Linux system.
.

Aha. Yes. This is a clue :)

I tried logging into my fc6 machine from my Windows machine using ssh -X and it sets DISPLAY correctly (ie localhost:10.0), and xeyes works.

The same command on my ubuntu server fails to set DISPLAY.

'ssh -X localhost' doesn't work at all, for some reason; but if I connect through the firewall (ie, out and back in again), then it connects, but DISPLAY isn't set.

It can't be missing X client libs because if I set DISPLAY to the remote system it works fine.

One difference between the fc6 system and the ubuntu system is that sshd is running on different ports -on fc6  it's the usual 22, while the ubuntu system is a different port. The firewalls both forward that different port appropriately, but the from=to for ubuntu while from!=to for fc6.

Any ideas?

Max.

---

### Post by bodhi.zazen on 2007-12-05
check /etc/ssh/sshd_config on the ubuntu server and make sure x forwarding is enabled.

---

### Post by davidmaxwaterman on 2007-12-05
> **bodhi.zazen said:**
> check /etc/ssh/sshd_config on the ubuntu server and make sure x forwarding is enabled.

Yes, I did that already : 

```
X11Forwarding yes
X11DisplayOffset 10

```

Rebooted a few times since too, but no joy :(

Max.

---

### Post by The Cog on 2007-12-05
I notice in man sshd that there is a -d debug option. 
Perhaps stopping the daemon and running sshd -d from the terminal might output any useful messagaes as the client connects.

---

### Post by Tom Y on 2007-12-06
This may be really obvious, but just thought I'd check:

If you are trying to reach your Ubuntu box from a Mac,  you need to use an X11 terminal rather than a regular Terminal window  

If I use X11 on a mac, I get the following:
```

myMacBox$ ssh -Y me@myUbuntuBox
myUbuntuBox$ printenv
DISPLAY=localhost:10.0
...

```
 - and X applications work fine.

If I use a regular terminal window it doesn't complain about using the ssh -X flag, but the DISPLAY variable is not set (and obviously X11 apps don't work).  

This doesn't explain why your Windows box can log into some things but not Ubuntu though!

(X11 is available on the OSX install disc but (I think) not installed by default.)

---

### Post by bodhi.zazen on 2007-12-12
Just an update :

I am having problems forwarding X on Gutsy (7.10).

Yes, I know how to forward X and it is working just fine from Feisty (7.04) thank you :)

I filed this bug report (if you want more details)

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/175815](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/175815)

---

### Post by davidmaxwaterman on 2007-12-20
> **bodhi.zazen said:**
> Just an update :

I am having problems forwarding X on Gutsy (7.10).

Yes, I know how to forward X and it is working just fine from Feisty (7.04) thank you :)

I filed this bug report (if you want more details)

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/175815](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/175815)

I see a reboot fixed your problem...however, I had rebooted my system many times to no avail.

Following your bug report, I find another [_**bug**_]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/51774") entitled 'ssh -X fails without warning when xauth not installed' and, sure enough, installing xauth fixes my problem :)

Thanks!

Max.

---

