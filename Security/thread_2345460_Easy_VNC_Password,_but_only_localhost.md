---
title: "Easy VNC Password, but only localhost?"
date: 2016-12-04
forum: Security
---

### Post by mikey93898 on 2016-12-04
Hey all,

I hate having passwords to remember, so ... I leave my VNC server always set to a password of "aaaaaaaa". But then I try to balance this out by only accepting localhost connections, and then disabling password SSH logins.

(and of course, VNC is generally disabled unless I need to activate it for a moment)

Is this reasonable or am I shooting myself in the foot?

---

### Post by TheFu on 2016-12-04
Makes perfect sense provided you have a way to get console access for emergencies. You don't need to use VNC always, use ssh when needed for most admin stuff.  I wouldn't bother disabling VNC on a normal VM/system. If it isn't doing anything, there isn't much overhead and it will be swapped out.

However, you might be happier using an NX-based remote desktop. NX feels 2-3x faster than any VNC I've tried and uses ssh for the tunnel and ssh-keys for authentication. The easiest/most popular implementation is X2GO.

There's an unsaid caveat - ensure that ssh really has been secured.

---

### Post by bearlake on 2016-12-04
Have so many test drives and laptops that I was able to test many programs and also just using terminal.

Totally agree with TheFu, and must add X2GO was one of the NX-based remote desktop I tested locally and over the Internet.

---

### Post by HermanAB on 2016-12-05
VNC is practically the only way that Ubuntu systems get hacked, so using a weak password on VNC is not a good idea.

Why use VNC at all, if you already have SSH running?

Something like this will pop up a graphical program on your local desktop without the need for VNC:
$ ssh user@ipaddress "gedit filename"

---

### Post by TheFu on 2016-12-05
> **HermanAB said:**
> VNC is practically the only way that Ubuntu systems get hacked, so using a weak password on VNC is not a good idea.

Why use VNC at all, if you already have SSH running?

Something like this will pop up a graphical program on your local desktop without the need for VNC:
$ ssh user@ipaddress "gedit filename"

Missing -X?
```

$ ssh -X user@ipaddress "gedit filename" 
```
However, this isn't really fast enough over a WAN connection. Use it all the time on a LAN, but not WAN.  Plus, for remote editing, scp works with vim to xfer the file for local editing and xfer them back when complete.  **vim scp://ip/path/to/file** On my LAN, I use **ssh -X** all-the-time.  But going from London to Atlanta using tunneled ssh for X/Windows is just too slow. Heck, doing it from the local cafe is too slow.  Maybe when everyone has GigE connections it won't matter. Today, NX is needed.  I've used it over dialup connections. For productivity-type stuff, it is fantastic.

IMHO.

Also, I think Herman missed the --localhost mention for VNC.  That prevents all remote connections, effectively requiring an ssh tunnel to use VNC. If only ssh is allowed in from the internet using ssh-keys for authentication, no passwords allowed, then only ssh users with keys will even have an opportunity to attempt VNC passwords.  Of course, if the ssh-keys are stolen due to poor opsec outside the network, all bets are off.

---

### Post by mikey93898 on 2016-12-07
Thanks for the input, friends :)

I tried X2Go in the past but it seemed to keep crashing on ubuntu, and used high cpu even when totally idle on some centos 6 servers, so I uninstalled it. I agree that X11 forwarding is too slow over a WAN (*tears of sadness). I definitely use mostly ssh/shell, but occasionally need to use something graphical, so that's when I momentarily turn on VNC. 

How will VNC get hacked when I'm only bound to localhost?

And aside from disabling cleartext passwords (forcing only key based logins), and having a firewall like CSF ... what are the other major gotchas that might make my openssh daemon vulnerable?

---

### Post by CharlesA on 2016-12-07
The risk should be minimal in that case. However, you should also ensure that the firewall is blocking that port on external interfaces just in case the VNC  configuration changes. That would add an extra layer of security to the situation.

FWIW, I have used [NX]("https://help.ubuntu.com/community/FreeNX") in the past, but it does require a separate client, so I don't think it would really be all that much different from using an SSH tunnel to connect to VNC.

---

### Post by HermanAB on 2016-12-07
Well, my point is that if you need to use ssh to tunnel VNC, then rather just use ssh alone.  It will be much faster, while on a LAN, ssh alone is fast enough and then you don't need VNC either.  So WAN/LAN - either way - you don't really need VNC.

---

### Post by TheFu on 2016-12-07
Lots of ways to secure ssh. Recently wrote a bunch in another post in these forums with mitigation methods.  Firewalls are 1 method, but only if completely locked down to the specific client IPs needed.  I can't do that, don't always know where users will be in the world, so need more general protections.

> 
How will VNC get hacked when I'm only bound to localhost?
You are doing the "best practice" - don't worry.  If ssh has been properly secured, then it isn't a risk.

x2go doesn't work with heavy GUIs, so it doesn't work with Unity.  Use a lighter DE or a plain WM and it works very well.
There are times when a remote GUI is more convenient. For example, when on travel, I don't want to bring any sensitive data on my devices, but may want to edit a spreadsheet or presentation or email or ... .  A remote desktop allows this.  When providing support to family 500+ miles away, sometimes seeing what they see is necessary. ssh doesn't fit all requirements.

I've been using a private cloud-based desktop the last 3-5 yrs.  It has worked very nicely. My files are secure and available always.  It runs inside a KVM VM, so even local access uses a remote desktop, x2go.  For the way I work, it is wonderful.  If my travel laptop dies, a $99 chromebook can be used to be productive in a few minutes - back to my real desktop at home. No muss or fuss.  Plus backups happen daily, automatically, on the home network.  Not everyone wants to work this way and that is fine. Some people do. [http://yieldthought.com/post/31857050698/ipad-linode-1-year-later](http://yieldthought.com/post/31857050698/ipad-linode-1-year-later) like that guy.

---

### Post by mikey93898 on 2016-12-07
> **CharlesA said:**
> The risk should be minimal in that case. However, you should also ensure that the firewall is blocking that port on external interfaces just in case the VNC  configuration changes. That would add an extra layer of security to the situation.

Ah yeah, port is definitely blocked in the firewall. The config starts out very restrictive and I only open ports as needed.

---

