---
title: "Remote GUI"
date: 2011-05-30
forum: Server Platforms
---

### Post by ajrutta on 2011-05-30
I have a server that is sort of hard to run sometimes without a gui, but I dont want to compromise ram with a gui. Does anyone know if it is possible (and how) to have the gui run on a vnc client or something remote without having to run the GUI on the server? thanks 
(probably like a thin client setup, but without any new hardware. Also there is a $10 iPhone App called iSSH that is an ssh and vnc client and it says it has its own x server. would this help?)

---

### Post by ruffEdgz on 2011-05-30
You know if you have X11 installed on a server but boot into the system on INIT3, you can still SSH into the machine with X11Forwarding enabled. If the X11Forwarding was successful when logging into the server via SSH, you should be able to run GUI's like **gnome-calculator** if you really wanted to.

From my Mac at work or from another Linux machine, you can see if X11Forwarding works by using this command:
```

ssh -X <hostname HERE>

```
If that doesn't work, go into your server that you want to use X11Forwarding on and make sure you enable it in the following conf file:
```

sudo vim /etc/ssh/sshd_config

```
Restart the ssh daemon to make sure the settings are used:
```

/etc/init.d/ssh restart

```
I have all my servers booting into INIT3 but if I still need to use a GUI for something (which is very rare), I can just make sure I ssh into that box with X11Forwarding on.

Hope that helps.

---

### Post by arrrghhh on 2011-05-31
X11 forwarding is nice...

But it really depends on the tasks you want to achieve.  Perhaps a solution like Webmin would be more up your alley...?  Again, it really depends on what you need the GUI for!

---

### Post by Lars Noodén on 2011-05-31
> **ajrutta said:**
> ...it says it has its own x server. would this help?)

No.  As far as the X server goes, the client is the graphical program and the [server is the display](http://xwinman.org/intro.php) you are looking at.  So your workstation is running the X-server and the remote server you are connecting to is the client. 

So you can run graphical programs on the server and display them on your workstation (if you have one) or your desktop.

---

### Post by Lars Noodén on 2011-05-31
+1 for X11 Forwarding

---

### Post by hawkmage on 2011-05-31
I am another one for X tunneling through ssh.  Once thing you may run into is trying to run an X application after using sudo su - UID to another users ID.  

I add the following to my .bash_profile to make this easier:
```
export DISPLAY_NUMBER=`echo $DISPLAY | cut -f 2 -d: | cut -f 1 -d.`
export XAUTH_LINE=`xauth list | grep :$DISPLAY_NUMBER`
function xsu {
   sudo su - $1 -c "xauth add ${XAUTH_LINE}" > /dev/null
   sudo su - $1
   sudo su - $1 -c "xauth remove :${DISPLAY_NUMBER}" > /dev/null
}
```

If I need to become user2 and run an X application I just run:
```
xsu user2
```
and X tunneling works normally.

---

