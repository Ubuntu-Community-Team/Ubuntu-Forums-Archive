---
title: "Start script under root automatically"
date: 2007-04-02
forum: Server Platforms
---

### Post by silurius on 2007-04-02
I'm using Ubuntu 6.10 for a soon-to-be-production LAMP server.  I need a GUI for a while, because I am still new to Ubuntu.  As my confidance grows, I'll eventually not need the GUI at all, but for now I need to get the following working reliably.

The following packages have been installed for remote access: **xfce desktop** (and its supporting packages) **vnc-common**, and **tightvncserver**.

The system is essentially ready for use, with ssh, http and mysql all running fine.  However I still have to launch VNC manually after logging in as root.

[INDENT][FONT="Lucida Console"][COLOR="Navy"]su
*[PASSWORD]*
x11vnc -rfbauth ~/.vnc/passwd -display :0 &[/COLOR][/FONT][/INDENT]

This gets VNC going and I can get in fine, but I need to automate it.  I created a script, but my skills aren't yet strong enough to help me automate its launch without having to log in as root first (does not work when run w/o root).  Alternatively, perhaps I could automate the root login step as well, although that's obviously not as secure.

It would be great if someone could help me perfect this process so that I can get to a fully-functional Xfce GUi sesion after every reboot.  Once I have that, I can go ahead and rack the server as my OS-level configuration is probably done at that point.

I'm still of a Windows mindset, so spelling things out helps.

TIY

---

### Post by silurius on 2007-04-03
Anyone?

---

### Post by huygens on 2007-04-03
I'm not using VNC, but I guess you are trying to run the VNC server so that you can take control of your box from remote.
To run it automatically, you should create a initscript that you will install in /etc/init.d/ directory.
It is a bit complicated and you need to know a bit of shell scripting. There is a skeleton file (a model to reuse) under /etc/init.d which is called skeleton. You should copy and rename it, and then edit it to suit your needs. What you need to keep in mind is that a initscript can be started, stopped, restarted, etc. So there are entries for each case in the skeleton. It is difficult to tell you how to write it.
Perhaps, I'm sure there are some initscript in the wild that just do that. Try looking with the following keywords (some or all): initscript init.d vncserver (and optionally: start stop)

When you finally manage to create such a init script, just save it in a file that you put under /etc/init.d directory.
You should tweak its security access like this (example, I have assumed that the given filename was start-vnc):
```
sudo chown root:root /etc/init.d/start-vnc
sudo chmod 0550 /etc/init.d/start-vnc
```*N.B.: if you are root, you do not need to type 'sudo'.*

Before you tell Ubuntu to use it, you should test it. Simply try the following:
```
cd /etc/init.d
sudo ./start-vnc start
sudo ./start-vnc stop
sudo ./start-vnc restart
```*N.B.: if you are root, you do not need to type 'sudo'.*
If all these commands are doing what is expected from them, then you should be safe to "install" this script.

Now, you should "install" this script so that the system takes it into account. Type the next command:
```
sudo update-rc.d start-vnc defaults
```[I]N.B.: if you are root, you do not need to type 'sudo'.
[/I]
That should do it.

---

### Post by silurius on 2007-04-04
This is excellent information.  I am beginning the harrowing descent into trying to customize the skeleton script.  Wish me luck!

Meanwhile, does anyone have any idea if this script (and the customization process) has been documented to any extent, anywhere?

I would be most happy to add something to the ubuntuguide.org wiki, once I manage to actually get things going on my end.

---

### Post by craigp84 on 2007-04-04
Given that this is one of your first Linux servers, and you're keen to have a GUI, you'll have an easier life by installing the standard Ubuntu Desktop edition[1].

This will give you point and click ease for adding / removing users, managing files & permissions, browsing the web for help, connecting to IRC networks for tips etc. etc. whilst still allowing you to install server software easily and quickly.

You'll find that thanks to APT (google it), ubuntu is very modular, software can be plugged in and out rapidly with minimal fuss. This allows you to evolve the desktop install and mould to your exact needs, as you discover what they are, over time.

The GNOME environment provides a VNC server built in (it's called vino, google for info on it). You can use this to remotely access your desktop. You'll find it under the Settings menu.

As you become more proficient, you can turn the graphical environment off, very easily, to save processor cycles & memory.

This is a pragmatic approach, and will hopefully help you get the job done quicker. I hope this will help you.

Craig

[1] You don't have to uninstall & reinstall to do this, type "sudo apt-get install ubuntu-desktop" in your terminal to upgrade to the desktop environment.

---

### Post by silurius on 2007-04-04
I'm comfortable enough to switch desktops, and within a short time I'll feel ready to dump them altogether.  Thank you for this suggestion.

> **craigp84 said:**
> The GNOME environment provides a VNC server built in (it's called vino, google for info on it). You can use this to remotely access your desktop. You'll find it under the Settings menu.

You know, I have used VNC Server on Gnome, but wasn't actually aware of a variant that runs as a service w/o need for script-writing.  That's very useful to know, thanks.

---

