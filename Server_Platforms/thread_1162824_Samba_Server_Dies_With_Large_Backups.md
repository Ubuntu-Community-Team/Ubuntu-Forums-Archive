---
title: "Samba Server Dies With Large Backups"
date: 2009-05-18
forum: Server Platforms
---

### Post by contax on 2009-05-18
I have an Ubuntu 9.04 server running Samba, but it consistently bombs in the middle of large uploads.. 20GB+.  Network computers lose connectivity and the server freezes.  Plenty of drive space.  Where do I start looking for a cause?  What logs are relevant?

---

### Post by wirelessmonkey on 2009-05-18
Are you mounting your samba share with smbfs or cifs?

Appropriate logs are /var/log/messages and those in /var/log/samba/

---

### Post by contax on 2009-05-18
I didn't even know what CIFS was until your post.  In fact, after looking at the logs, I think that I'm way over my head.  The files were originally mounted using SAMBA, so I think that they are smbfs.

I'm going to delete all of the logs mentioned and then stress the system and see what pops up.

Thanks

---

### Post by capscrew on 2009-05-18
> **contax said:**
> I have an Ubuntu 9.04 server running Samba, but it consistently bombs in the middle of large uploads.. 20GB+.  Network computers lose connectivity and the server freezes.  Plenty of drive space.  Where do I start looking for a cause?  What logs are relevant?

How have you set up the server IP addressing?  Does it get its a IP address via dhcp?  If so read ***from post #13 on*** of this:
[_http://www.ubuntuforums.org/showthread.php?t=1140094&page=2_]("http://www.uluga.ubuntuforums.org/showthread.php?t=1140094")

---

### Post by contax on 2009-05-18
That was a great thread, but I'm running a static address.  The symptoms sound suspiciously like mine, but my server will go down with the lapse of service.

---

### Post by JohnnyVW on 2009-05-19
I'm having the very same problem...

There is a related discussion here:  [http://ubuntuforums.org/showthread.php?t=1091406](http://ubuntuforums.org/showthread.php?t=1091406)

It's a work-around, but I'm having the problem with a Samba share AND using scp without dealing with Samba.

Same exact problem.  The network services go down on the server.

Now, the only way I was able to get the large files to transfer was the --bwlimit switch (bandwidth limit) on scp.  

I kept bringing up the bandwidth in small steps until it started to fail again.  I got it to 2000KBps (~16.4Mbps), WAY below the available 100Mbps!  2000KBps still would stall, but would continue after a few seconds.

Attached is a screenshot of the network monitor stalling...

---

### Post by HermanAB on 2009-05-19
Howdy,

If you can fix the problem by throttling, then the system must be running out of resources: Memory, file handles, buffers...

This is a common problem when transferring large amounts of data between systems and is one of the reasons why scp and rsync have BW parameters.

You may be able to balance things better by adjusting something in the kernel.

---

### Post by JohnnyVW on 2009-05-19
The thing that bugs the heck out of me is that this is an easy thing to do between two Window$ boxes.

I'm going to try this between a Windows box and the server to see how it works...

Here's the command I used tonight.  It just crashed.  I did notice that if I tap the power button on the server, its networking comes back up...  it doesn't seem to kill the Ubuntu box I'm on (transferring from).

```

/usr/bin/nice -n +19 rsync -e ssh -avz --bwlimit=2000 /home/johnny johnny@ubuntuserver.local:/media/music/johnny_BU

```

---

### Post by HermanAB on 2009-05-19
I have had rsync crash between two Windows boxes too.  The only solution was to throttle the transfers.

---

