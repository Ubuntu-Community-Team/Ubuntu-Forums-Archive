---
title: "Chrome won't run on Ubuntu 16.04 (VPS)"
date: 2016-09-18
forum: Ubuntu/Debian BASED
---

### Post by jackofdiamond5 on 2016-09-18
Hello!

I have a VPS and I installed Ubuntu 16.04 on it, first I installed it with all of it's libraries, etc, then I installed a clean version of it, no libraries, no nothing. But in both cases Google Chrome refuses to start up. I installed it using the terminal, on the clean version and with the installer on the full version. I really don't know why it refuses to load. I also tried different envirnoments xfce, unity, etc. Still no luck.

Any help will be greatly appreciated!

---

### Post by TheFu on 2016-09-18
If the VPS is remote then where is the X/Server running?  The choices are on your local system OR by using something like vncserver or x2go on the remote system.  You can't use only a terminal (like putty) to run GUI programs.

[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) might help explain.

Generally, heavy GUIs like Unity don't work over remote connections because they need, demand, direct access to a GPU.  A VPS probably doesn't even have any GPU installed.  If you use x2go (my recommendation), be certain to setup ssh first, test that, get it working, then install, configure x2go on both sides (server there, client here) and tweak the connection settings to slightly lower than your true bandwidth, reduce the screen/image compression size, disable audio and printing.  Then "be happy."

Of course, it would be best to just learn to use the VPS as it was designed - with ssh and terminals, but no GUI programs will work that way and if the point of the exercise is to have a remote desktop in "the cloud", you really want x2go.  I've been running my primary desktop in a "private cloud" for about 4 yrs (maybe 6 now). That desktop system is used to manage about 25 other servers which don't have **any** GUI.  It is nice to have the desktop available from anywhere in the world by just using 1 client application.

Here's an example from yesterday ... I didn't do this one, but OBS was used with 2 webcams for video input. HDMI video capture is still a bugger on Linux. [https://www.youtube.com/watch?v=TgJipN10TLU](https://www.youtube.com/watch?v=TgJipN10TLU)

---

### Post by jackofdiamond5 on 2016-09-18
Thanks for your reply!
For me the goal is to be able to run Google Chrome under linux and on a VPS. I use vncserver to connect to the VPS so that I can use the GUI. I connect without any problems to my VPS. And I can access all files, installed applications, all in GUI. But the only problem is that I cannot run Google Chrome. I have installed it multiple times, on different setups and different environments, but it just won't start. It doesn't even get a process in the System Monitor, while other programs, like firefox, obviously do.
If you have any ideas why that happens, I'd really appreciate it!

---

### Post by TheFu on 2016-09-18
a) using VPN or ssh tunnels, I hope.  VNC alone is NOT secure.  x2go is 2-3x faster, BTW.

b) Disable hardware acceleration inside chrome. That's all I got. I use firefox and chromium daily.  Never installed "chrome" on any of my systems and never plan to.

---

### Post by jackofdiamond5 on 2016-09-18
I use SSH tunnel, and I know that using VNC alone is not secure. But I cannot start Google Chrome at all. It won't run. No process in the System Monitor/Task Manager, nothing. I just try to open it and that's it. Not even an error report. Nothing. It just doesn't do anything. I have another instance of Ubuntu 16.04 running on my private server, and there Google Chrome is working fine. But on the VPS it just won't load, or do anything for that matter. No idea why, though. I'm open to any suggestions.

---

### Post by TheFu on 2016-09-18
Thanks for putting up with my poor assumptions.  Low-beans doesn't always mean what I assume, but it is best to be certain.

Have you checked permissions issues? Sometimes folks use sudo when they shouldn't and config files get owned by root under their userid. Some programs crash rather than handle that issue gracefully.

Have you tried opening a terminal and running chrome with more debug information output?  According to the chromium manpage, it supports the GTK+ options - [https://www.chromium.org/for-testers/enable-logging](https://www.chromium.org/for-testers/enable-logging) might work for chrome too.

Have you tried setting up a new userid with stock/default settings?  I realize doing this is a hassle for VNC-based connections.

Would be good to double-check the DISPLAY variable too.  Haven't used VNC in a very long time, but it should set the DISPLAY to something like :1 or :2 or :9 .... whatever VNC session number you've decided.  I assume the vncserver process is running with "--localhost" options to prevent accidentally using a non-secure, remote, connection.

Anyway, those are a few options.  If your local OS is linux, there is more that can be done like running it using a remote X/Windows call.  That link above explains - but you probably already know **ssh -X -C**

These are just things to try. No clue on my side.

---

### Post by jackofdiamond5 on 2016-09-20
Thanks for your help! I got it up and running. It was a permission issue, but it finally works. Thanks again!

---

### Post by TheFu on 2016-09-20
> **jackofdiamond5 said:**
> Thanks for your help! I got it up and running. It was a permission issue, but it finally works. Thanks again!

Would be helpful to others if you
a) marked the thread as "solved" - so people looking for a solution find it AND so people wanting to help don't bother.
b) explain the real issue AND the fix clearly. "permissions issue" is vague for people likely to be stuck.

---

### Post by jackofdiamond5 on 2016-10-04
To whoever is reading this and has encountered a similar issue: Never, ever use the root account to do little mundane things in your OS! Always, create another user. I was too lazy and I neglected this fact. Simply because the root account grants complete control over your system, third party software was completely blocked out (that was the case with me) so when I made a new user profile, it all came into place. Very stupid mistake on my end there, but oh, well, live and learn!

---

### Post by TheFu on 2016-10-04
Using root for any GUI stuff often, but not always, has unintended consequences.  

Really, the only time root should be used is for system management in a shell.  If it is GUI related - don't. Just don't.  That applies to editing system files with gedit too - there are situations where that any make for a really bad day just because root owned the config files automatically created.  CLI/shell tools don't usually (every?) automatically write to config files, which is why they don't have this issue.

BTW, using root isn't the intended way for Ubuntu to be used. sudo is. However, almost everyone, including me, will use **sudo -i** from time to time when I'm doing lots and lots of admin work directly on a system.

root with ssh should be blocked. Don't allow root to ssh into any system. There is a setting in /etc/ssh/ for that.

---

### Post by jackofdiamond5 on 2016-10-05
Some people might think "Oh, but when I include my user profile in sudo, I grant it root priviliges, so what's the difference if I use sudo or root?" Well, there IS a difference, which is basically that sudo allows you to run commands as any user, with the default being root. However never should root itself be used just for the heck of it. You could do some serious damage to your system, some even irreversable! If you want to use GUI or as is in my case - make a VPS server, with an ssh tunnel and all that stuff, create another user, add it to the sudo group and then do your thing. Just forget about root unless you know exactly what you're doing. And as for ssh, root should be completely disabled.

---

