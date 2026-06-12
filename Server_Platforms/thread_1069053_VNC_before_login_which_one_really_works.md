---
title: "VNC before login which one really works?"
date: 2009-02-13
forum: Server Platforms
---

### Post by Dougie085 on 2009-02-13
Ok I've been searching around for this solution and there are tons of different things out there but most of them seem quite outdated? Can anyone point me or tell me a solution that will work? I'm running Intrepid and I am going to be accessing the server from a windows machine. I have been using tightvnc on the windows machine and it works great except that if I reboot I have to go hookup a keyboard and login to the server. Then I can run VNC from the desktop.

---

### Post by bean72 on 2009-02-13
Hi there,

I have used this guide to setup a VNC server: [http://ubuntuforums.org/showthread.php?t=122402]("http://ubuntuforums.org/showthread.php?t=122402")

I have only tried this for Hardy, but I'm sure it won't take much to get it going in Intrepid. You may run into problems with the config, due to a different version of VNC, but if you go to page two of that thread it will show the proper config for the xinetd.d service.

Let me know how this goes, as I am also working on an Intrepid server, and I would like to get VNC going on it without having to log in after every reboot.

---

### Post by Dougie085 on 2009-02-13
Well so far I can't even get past step 1 :) There is no XDMCP option where it says to look. Maybe I need to install XDMCP I'll try that.

---

### Post by lykwydchykyn on 2009-02-13
XDMCP is built into X, it's not something you seperately install.

If the GUI config option is not there, you can just edit the file /etc/gdm/gdm.conf-custom and add the line "Enable=true" under the [xdmcp] heading.

I've tried a few different methods of auto-enabling VNC, and the one in this tutorial has been the most stable and usable so far (at least as VNC goes; most of the time nowadays I just do X forwarding over ssh).  So I second the recommendation.

---

### Post by Dougie085 on 2009-02-13
Ok I did what the guide said..I read through a couple pages to and for some reason I can't get it working. This is the output I get. 

```

harold@media-server:~$ sudo killall Xvnc
Xvnc: no process killed
harold@media-server:~$ sudo /etc/init.d/xinetd start
 * Starting internet superserver xinetd                                   [ OK ] 
harold@media-server:~$ vncviewer localhost:1
vncviewer: read: Connection reset by peer

```

I don't seem to be having the same issues as the people that were posting there.

---

### Post by HermanAB on 2009-02-13
VNC is almost always the wrong solution for Linux.  SSH can do everything VNC does and it is secure.  So quit playing with VNC and install ssh-server on Linux and install Xming and PuTTY on Windows.  

Once SSH server is running on Linux, you can change the runlevel to 3 with the command "init 3", since when you use SSH you need not run X on the server.

Then connect with something like this:
ssh user@server gnome-panel

Cheers,

Herman

---

### Post by bean72 on 2009-02-13
Hi Dougie,

I have made an attempt to install VNC server myself, and a headache later i got it working.
Use this config:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}
```


Notice the fonts path, in the newer versions of X the fonts folder and X11 are reversed, try that and restart xinetd and you should be running fine.

---

### Post by Dougie085 on 2009-02-13
Hey that worked somewhat! Now the problem is the screen that comes up is the patterned screen with the black X as a mouse pointer? The login screen is not coming up... any idea's?

---

### Post by bean72 on 2009-02-13
do you have a desktop manager installed on your server?

---

### Post by lykwydchykyn on 2009-02-13
> **Dougie085 said:**
> Hey that worked somewhat! Now the problem is the screen that comes up is the patterned screen with the black X as a mouse pointer? The login screen is not coming up... any idea's?

That usually means either gdm is not correctly configured or not running.  Issue a /etc/init.d/gdm restart and if that doesn't fix it post your /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom.

---

### Post by Dougie085 on 2009-02-14
Well being as I'm posting inside gnome I'd imagine it's installed and setup properly :)

---

### Post by windependence on 2009-02-14
FreeNX is a much more secure and a much faster solution than VNC. As Hermann stated, the best solution is X forwarding. You can run GUI apps securely one at a time in an ssh session. Try it!

-Tim

---

### Post by Dougie085 on 2009-02-14
What would you use on the Windows side to connect to FreeNX?

---

