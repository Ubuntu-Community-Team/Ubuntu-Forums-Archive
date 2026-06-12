---
title: "frustrated"
date: 2008-05-17
forum: Server Platforms
---

### Post by nix4me on 2008-05-17
Just changed my server to 8.04 and i have a serious issue with proftpd.  The service does not always start after a reboot.  I have no idea why.  When it doesn't start, i can manually restart it and it runs fine.  Any ideas why it's not working every time?

---

### Post by HalPomeranz on 2008-05-17
I don't have a lot of experience with ProFTPD, but the first thing I'd do is check the logs to see if there are any error messages that might indicate what's wrong...

---

### Post by nix4me on 2008-05-17
I see nothing in the logs about it.  Which log should I see a failed process start?

---

### Post by HalPomeranz on 2008-05-17
You may see something in /var/log/messages ("grep -i proftp /var/log/messages"), but my guess is that ProFTPD has its own log files.  Can you tell from looking at the ProFTPD config file where it's putting its logs?  

Alternatively, you might try:

find /var/log -type f | xargs grep -li proftp

The above command will give you a list of all files under /var/log that contain the string "proftp" (case-insensitive match).

---

### Post by nix4me on 2008-05-17
i see nothing pertaining to a failed start.  This is frustrating.  A manual start works fine.  Could it be that proftpd is trying to start before networkmanager has the network up?

I see no way to switch from networkmanager to network to try it though.

---

### Post by HalPomeranz on 2008-05-17
Well, as an ugly work-around you could put something like this in /etc/rc.local:

```
# Start ProFTP if it didn't start properly at boot time
if [ ! "`lsof -t -c proftpd`" ]; then
        /etc/init.d/proftpd start
fi
```

Still it would be better to figure out why it's bombing during the normal startup.  Maybe turning up the debugging level higher?

---

### Post by nix4me on 2008-05-17
Fixed.  It was networkmanager.  Networkmanager starts too late in the boot process and thus proftpd was starting before it, which was causing it not to start.

I changed network to non roaming mode and all seems fine now.

---

### Post by cdtech on 2008-05-17
That dosen't seem like a fix but rather a workaround. How did you do the upgrade. I'm sure your using run level 2 (command line - runlevel). Check the etc/rc2.d folder and see if your S50proftpd link is there and that it starts with an "S" and not a "K" and in which order it runs at. Mine starts at "S50" you can change the order.

---

### Post by hyper_ch on 2008-05-18
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by nix4me on 2008-05-18
> **cdtech said:**
> That dosen't seem like a fix but rather a workaround. How did you do the upgrade. I'm sure your using run level 2 (command line - runlevel). Check the etc/rc2.d folder and see if your S50proftpd link is there and that it starts with an "S" and not a "K" and in which order it runs at. Mine starts at "S50" you can change the order.

It is S50 in the rc2.d.

All I know is that it works perfectly now since i unticked "roaming mode" in the network applet and set the configuration to DHCP.

---

### Post by cdtech on 2008-05-18
Great!

---

