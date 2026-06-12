---
title: "Autologin and autoshutdown with Ubuntu Server Edition 8.10"
date: 2009-03-19
forum: Server Platforms
---

### Post by mha2908 on 2009-03-19
Hi, I've got a brand new PC, which I use as server. It is headless, and I've got my BIOS set up to automatically boot at 8 AM, and since the PC is put away, and has no attached keyboard or mouse, i DO NOT want to type in my credentials. Instead I want it to autologin my user, or at least login using another PC. I was able to do this with the Desktop Edition using XDMCP, but I do n't know how to do it in the Server Edition. I can't access it with SSH as long as its not logged in.

And there's one more thing I want to do: Schedule an automatic shutdown at 24 PM. How do I do that?

Some might ask: Why shut it down? Then you don't have to login!
But, since it is placed in my home, I am paying for electricity, and those 8 hours is just a waste. I've also set up the BIOS to accept the WakeOnLan-signal, so I can turn it on between 24PM and 8AM if I want to.

---

### Post by windependence on 2009-03-19
I don't understand why you need to log into anything at all to access the machine from another box. You do NOT need to be logged in to ssh in to the box, you just have to have the daemon start at boot, so what's the problem?

As to the shutdown, I'm not going to give my usual speech except to say you don't realize what are "saving" is pennies, literally pennies.  If you are that anal about power you should be using the new ITX boards that draw about 35 watts of power.

-Tim

---

### Post by mha2908 on 2009-03-19
Actually my new PC is powersaving, using 39 watt. It is using the new Intel Atom processers which is saving a lot of power. Couldn't you plz tell me how to autoshutdown? 

But how do I start the ssh daemon on boot?

---

### Post by windependence on 2009-03-19
This is exactly what I had in mind. I run all desktops on the Atom, and they are in Apex cases that are very very small. Now that you said that, turning off the machine is basically meaningless. If you insist on deviling yourself to save 2 cents a month I guess you could run a cron job every day at the proper time.

As to the ssh daemon starting at boot, it should do that by default after you install OpenSSH . If not, you can add /usr/sbin/sshd at the end of your /etc/rc.local file.

What is the output of this:

```
ps aux | grep sshd
```-Tim

---

### Post by mha2908 on 2009-03-19
Yeah, it works! I dont know what I made wrong in the first place, but the SSH works without login!

But how to configure those "cron jobs", you see, there's a fire risk, too!

---

