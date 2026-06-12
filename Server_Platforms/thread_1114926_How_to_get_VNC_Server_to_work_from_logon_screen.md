---
title: "How to get VNC Server to work from logon screen?"
date: 2009-04-03
forum: Server Platforms
---

### Post by henriquelm on 2009-04-03
Hello there, I use the default vnc server that comes with ubuntu server 8.10, but everytime that the server has to be rebooted I need to log on to get the vnc server working again. I was wondering if there is any way to get the vnc server to start working from the logon screen so even if I have to reboot the server I'll still have remote access after the boot.

---

### Post by Kareeser on 2009-04-03
Some quick and dirty links:
I've read about someone using x11vnc to achieve this.

What might be easier would be setting ubuntu to automatically login. However, this is a security risk.

---

### Post by cdenley on 2009-04-03
vnc4server doesn't require someone to be logged on locally, because it creates a new session separate from the locally active one.

---

### Post by kanikilu on 2009-04-03
If you're not too attached to VNC, you could use NX:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by krunge on 2009-04-03
> **Kareeser said:**
> 
I've read about someone using x11vnc to achieve this.


Connecting x11vnc to the Login screen is described in the section marked 'Continously' at this link:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

You basically add the x11vnc command to the X display manager start script (e.g. /etc/gdm/Init/Default)

---

### Post by henriquelm on 2009-04-06
I have tried to install the x11vnc but I'm getting an error message. Some people over the ubuntu channel on irc told me to stop trying to install it, since I wasn't sure of what I was doing. So seems like it's not an easy job to install the x11vnc, but I'll keep trying!


Thanks for the help.

:p

---

### Post by krunge on 2009-04-06
If gdm/gnome is your display manager, put this:
```

/usr/bin/x11vnc -passwd mysecret -o /var/tmp/x11vnc.log -forever -bg

```
in the file
```
/etc/gdm/Init/Default
```
right near the bottom before the 'exit 0' or similar line.

Also in the file  /etc/gdm/gdm.conf make sure this is set:
```

[daemon]
KillInitClients=false

```
Then restart gdm or reboot. All described here: [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---

### Post by HermanAB on 2009-04-07
Well, you got to ask yourself why VNC?  It is good for training, where you want the local user to see what the remote user is doing.  However, for personal remote access you only need SSH, which is much easier to set up and less intensive on the server and most importantly, SSH is secure.

Try this from a remote machine:

```
ssh -X -C -c blowfish user@server gnome-panel
```

and go click happy.

Your server can then remain in runlevel 3 (no X needed on the server).  ***This is exactly why Ubuntu server edition ships without X - you don't need it.***

---

### Post by Shobuz99 on 2011-06-03
I'm removing this post and will create a new thread.
Thread title is: "X11vnc remote shift key won't work"
Thank you for your help

Shobuz99

---

