---
title: "Get Back Into Already Running Program After SSH Connection Drops"
date: 2010-05-02
forum: Server Platforms
---

### Post by pgn674 on 2010-05-02
I've kind of wondered about this ever since I started using Linux, and now I have to find out. Is there any way to get back into the input/output stream (including past output) of a program if you start the program in terminal over SSH and the SSH connection gets temporarily dropped?

I started upgrading from 9.10 to 10.04 on my server (it's on a virtual machine at a far away host) over SSH, as described here: [Upgrading to Ubuntu 9.10 | Ubuntu]("http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29") Everything was going fine, until it got to generating locales. It seemed to hang, and after some 10 minutes I hit space, and I got "Write failed: Broken pipe". The SSH connection had dropped. I am able to reconnect just fine, on the same port.

However, I of course am now not seeing the progress of the upgrade any longer. How do I know when it's done? Looking at ps -A, I don't see any processes that's obviously the upgrader. And more importantly, what if it wants to ask me a question, like whether or not to keep a configuration file? The upgrader will be paused indefinitely.

So, is there any way to get the upgrader process to start pumping standard out and standard in back to my SSH view again? And if I can, will I be able to see past output, in case it has already asked me a question and is waiting for an answer?

---

### Post by CharlesA on 2010-05-02
I don't know of any way to do that outside of running a vnc server and doing everything on vnc (then you are SOL when vnc crashes).

In my experience, anything started in an SSH session is closed or killed when that session ends.

I have been able to start things and then send them to the background before disconnecting and they run fine. I guess that's just the way it works.

---

### Post by pgn674 on 2010-05-02
Well, I just tried starting nano on the server, then cutting my connection by disconnecting the ethernet. I then closed the terminal, reconnected to ethernet, SSH'd back in, and now nano is running as a process on the server (it wasn't before). So I don't think dropped SSH connections kill a process running and displaying over it. And now I have nano running, and I can't quit it internally, not that that is much of a problem.

Also, I don't have any graphical interface like X, Gnome, or Metacity installed on this server, so VNC wouldn't work until I set those up. Plus, it's already too late :P

Thanks for the info/ideas, any others from you or anyone else?

---

### Post by pgn674 on 2010-05-03
I tried starting the distribution upgrade again, and it said none was needed. so I tried apt-get's update and upgrade, and both time it said files were locked. So I did a reboot (no force necessary), and now SSH isn't working. I have the alternative port the extra deamon uses written down at home, so I'll try that later.

---

### Post by windependence on 2010-05-03
Take a look at screen. You can disconnect and resume from an ssh session among other things.

-Tim

---

### Post by evilsee on 2010-05-04
yip, screen is what you need.

---

### Post by uberlinuxnerd on 2010-05-04
+1 for screen!

---

