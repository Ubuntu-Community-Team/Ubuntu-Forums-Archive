---
title: "Ubuntu Server Upgrade Interrupted"
date: 2016-07-29
forum: Server Platforms
---

### Post by chase-gooding on 2016-07-29
Last night I began the 16.04 LTS upgrade for my home server running Ubuntu Server.  It got to the point where it asked to replace the Gnome defaults (or something). I hit C (I think) to compare the two files.  I then realized that most of the changes were syntax changes and mainly for programs I wasn't planning on using on the server anyway (e.g. Libre Office, Rhythmbox etc.). I tried to get out so I could then select "y" to allow the overwrite.  I tried hitting Esc, q, and eventually Ctrl+C. Nothing happened...I finally figured out how to get out and then the Ctrl+C went through and cancelled the remaining steps.  I haven't restarted or closed the Terminal yet. I'm afraid that if I do, I will have all kinds of problems. I tried doing do-release-upgrade again to see if it would pick up where it left off, but now it doesn't see any available upgrades.

So what should I do? Is there some way to have it pick up where it left off or to start from the beginning?  Should I restart and hope for the best?  Thanks

---

### Post by kyrithis on 2016-07-29
Run these commands sequentially, then attempt a reboot (Using the "reboot" command). With any luck, this should pick it up where it left off or at least complete what isn't there.
apt-get autoremove
apt-get autoclean
apt-get update
apt-get -f install
apt-get dist-upgrade
apt-get upgrade

EDIT: Did forget to mention, I usually err on the side of caution and append sudo to commands like that. Up to you, it may have a better effect.

---

### Post by chase-gooding on 2016-07-29
After I run sudo apt-get autoremove, I get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by kyrithis on 2016-07-29
Use this command:
ps aux | grep apt
With any luck, it will show an "apt" process or anything similarly named. If it does, take down it's process ID, then use this command to kill it:

kill [ID]
Assuming all goes well from here, try "apt-get autoremove" again and report back here.

---

### Post by chase-gooding on 2016-07-29
ps aux | grep apt produces lines like this.

chase    28904  0.0  0.0  14156   992 pts/1    S+   11:11   0:00 grep --color=auto apt

The 28904 number changes each time I do it, but the rest of it stays the same.  I have tried killing 28904, 14156 and the other numbers that keep changing. Each time it says "No such process". I ran autoremove again and it's the same issue.

---

### Post by howefield on 2016-07-29
Hi chase-gooding,

I have moved your thread to the ""*Server Platforms* although it is certainly about upgrading to the next release, it is also about the Server edition. Hopefully one of the real Server experts will spot the thread and chime in.

---

### Post by chase-gooding on 2016-07-29
I found this: [http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

I typed this:
[COLOR=#111111][FONT=Consolas]sudo lsof /var/lib/dpkg/lock

[/FONT][/COLOR]It gave me the dpkg process ID.  I sudo killed it.  Now I'm running autoremove and it eventually prompted me with the same gnome/defaults prompt.  So far, so good.  I'll report back when this is done.

---

### Post by kyrithis on 2016-07-29
My apologies for not being a "real" expert. I've ran enough servers to give some input I'd think.

If you wish to continue following my advice, run this command. It's not the best way to do this, but it'll allow you to proceed.

"sudo rm /var/lib/dpkg/lock"
Then you can continue on with my first post.

EDIT: Killing the dpkg process is pretty dangerous, but what's done is done. With any luck, there won't be any corruption from it (Seeing as it shouldn't have been doing anything). Let me know how it goes.

---

### Post by chase-gooding on 2016-07-29
Thanks for your help kyrithis. I went through the rest of the list and there weren't any issues.  I'm guessing I can restart and see what happens.

---

### Post by kyrithis on 2016-07-29
Go for it. Make sure to post back with the result.

---

### Post by chase-gooding on 2016-07-29
I'm working remotely so I can't physically turn it off/on at the moment. This is the error I'm getting when I try to reboot:

Failed to set wall message, ignoring: Interactive authentication required.
Failed to reboot system via logind: Interactive authentication required.
Failed to start reboot.target: Interactive authentication required.
See system logs and 'systemctl status reboot.target' for details.
Failed to open /dev/initctl: Permission denied
Failed to talk to init daemon.

---

### Post by kyrithis on 2016-07-29
o.O So it looks like it wants user authentication....but from a desktop GUI instead of a server CLI.....Maybe try "sudo reboot"? I have no idea why a reboot would require authentication but it wants it.

---

### Post by chase-gooding on 2016-07-29
sudo reboot seems to be doing something. I'm not physically next to it to see what's going on.  I had VNC/SSH setup so I could access the desktop gui remotely.  Now the VNC isn't working.  My guess is that it's restarting, but my VNC service (x11vnc) isn't starting.  Also, I'm able to access my mythweb online, but there's no info.  I'm guessing I broke a few services somewhere along the way.

---

### Post by kyrithis on 2016-07-29
Yea. With any luck, we've salvaged the install, but there's bound to be one or two things broken. Occupational hazard for this sort of thing. When you're able to physically access it, we can go from there.

Feel free to PM me later if you need more help, or just reply again here. I'll keep an eye on the thread. At least we've saved your files hopefully.

---

### Post by chase-gooding on 2016-07-29
All of the important documents are stored on a separate hard drive.  The OS and all server programs are stored on a small SSD.  It would suck, but worst case I reinstall the OS on the SSD, but I don't think we'll have to do that.

---

### Post by cariboo on 2016-07-29
I'd suggest you ssh into your server and run the following command:

```
sudo apt-get -f install
```

This should install the missing packages, and get back to a running server.

---

### Post by chase-gooding on 2016-07-29
I've done that.  I appear to have a running server at this point.  I think I'm just missing a few services: x11vnc and mythtv. I also can't find my ZFS partitions.  I'm guessing it has something to do with the new systemctl.

---

### Post by chase-gooding on 2016-07-29
Good news.  I got x11vnc working...sort of. I went through the intructions for Vivid+ here: [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)
I then ran: sudo service x11vnc start
I guess I need to work on making it start automatically.  But I have a GUI now, so that's something.

---

### Post by kyrithis on 2016-07-29
Cool beans. I think we can call this issue solved now eh? Or is there more we can help you with ^_^?

---

### Post by chase-gooding on 2016-07-29
I got my ZFS pools to show up. I had to remove zfs-docs (sudo apt remove zfs-docs).  You might also have to remove zfsutils-linux.  I then reinstalled zfsutils-linux. Voila!

VNC is working at startup now too.

Now I need to figure out the mythtv issue.

---

### Post by chase-gooding on 2016-07-29
Regarding Mythtv:

Based on this thread: [https://code.mythtv.org/trac/ticket/12713](https://code.mythtv.org/trac/ticket/12713)
I added "[COLOR=#000000]sql_mode=NO_ENGINE_SUBSTITUTION" to the end of [/COLOR][COLOR=#000000][FONT=Verdana]/etc/mysql/conf.d/mythtv.cnf
Then, I ran mythtv-setup...I probably could have used "sudo service mythtvbackend restart" instead. Followed up with reboot and all seems to be working.
[/FONT][/COLOR]

---

### Post by kyrithis on 2016-07-29
An update on my end, I'm looking for some information as we speak, but it's approaching my bedtime (Night shift sucks) so I'm beginning to wear out. I may not be able to give you what I've figured out until later when I wake up. It does appear that it's a halfway common issue with a few fixes, so I'm confident we can make it work properly.

EDIT: That sounds as though part of the problem may not be on your end. A potential server error on their end, neh?

---

### Post by chase-gooding on 2016-07-29
Apparently this mysql change messes with a lot.  Also go to /etc/mysql/my.cnf and add "[COLOR=#000000]sql_mode = NO_ENGINE_SUBSTITUTION" to the [mysqld] section.  That fixed my Zoneminder as well.[/COLOR]

---

