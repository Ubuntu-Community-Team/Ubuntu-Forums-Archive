---
title: "[SOLVED] NX free server timeout (not FreeNX) bug and how to fix it"
date: 2007-11-20
forum: Server Platforms
---

### Post by vinicius.vbf on 2007-11-20
Hi folks!

I've just download the nxclient, nxnode and nxserver .deb packages from NoMachine's site and installed it... and then I found some problems. 

The .deb files and versions that I've installed to my ubuntu box are:
nxclient_3.0.0-84_i386.deb
nxnode_3.0.0-88_i386.deb
nxserver_3.0.0-74_i386.deb

And the free client for Win XP SP2:
nxclient-3.0.0-83.exe

I found this bug when I ran some heavy-network using programs (like torrent clients) in a NX session.

In some time between the client and the server negotiation the nxnode process invoke the command "netstat -etl" and, once I have some hundreds of connections stabilished by my torrent client, this command takes about 30 minutes to finish. So, when I try to resume a previous working session, my client can't connect due to the error "Timeout in communication with the NX server". This behavior was random (and, now I understand, so was the number of active connections). The error logs just keep telling me that a timeout occurs, but I couldn't find any reference to these errors at NoMachine's site nor internet. Now I know: the problem was that netstat was trying to resolve each hostname one by one.

I have fixed it by editing the nxnode binary and replacing the parameters "-etl" by "-enl", since this "n" tell to the netstat to not resolve hostnames and the command is finished in less than a second. This have fixed the error. The parameter is located at 0x003C1D1D in the file "/usr/NX/bin/nxnode".

Also, I couldn't find any reference to the "-t" parameter of netstat in the man nor internet docs.

That's it.

Regards,

Vinicius

Keywords: NX, free, freenx, timeout, connection, server, nxserver, nxnode, nxclient, ubuntu, gutsy, signal 15, ssh, sshd.

---

### Post by nosleep on 2007-11-26
Thank you  vinicius.vbf,

It was giving me trouble for a long long time, first noticed it 6 months ago      and  was allways related to P2P programs (amule, mldonkey).

Everything works perfec now.

Once again, thx for solution.

Best regards,
NoSleep

---

### Post by vinicius.vbf on 2007-11-26
Hi nosleep! I'm glad to help you ;)

I've notified the NoMachine NX team of this bug and here is they answer:

----------------------------------------------------------------------------
Dear Vinicius,

thank you for contacting us.

This indeed looks like a bug, so we will open a Trouble Report which will be fixed in the next maintenance release.

Please keep checkingo our Trouble Reports section in our Knowledge Base to see updates.

Kind regards,

The NoMachine Team
----------------------------------------------------------------------------

---

### Post by daflame on 2007-11-26
Nice bug fix...  However, your report about there being no package for FreeNX is not entirely true.  There is no official packages right now, but I have set up a forum thread with packages of FreeNX 0.7.1 and nx-3.0 here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by vinicius.vbf on 2007-11-27
> **daflame said:**
> Nice bug fix...  However, your report about there being no package for FreeNX is not entirely true.  There is no official packages right now, but I have set up a forum thread with packages of FreeNX 0.7.1 and nx-3.0 here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

That's great daflame! :)

I'll try your packages today and see the FreeNX improvements. But, as you can see, my post was posted before yours and, until then, I couldn't find any updated FreeNX .deb packages :)

Anyway, I've edited my original post and removed that information.

Great work!

Regards,

Vinicius

---

### Post by nkef on 2007-12-31
Great Great thanks Vinicius i was searching for the NX connection timeout problems for months !!!

I am using the nxnode_3.1.0-3_x86_64.deb and i located the -etl at offset 0x0045C94D and replaced
the "t" with "n".

---

### Post by Alex^77 on 2008-04-18
Hello vinicius.vbf,
I have found very usefull your post!!

Many days ago, I have formatted my server with new Ubuntu (8.04) and  I have change my old no machine server (I had before Ubuntu 6.04 with a very old NX server)

And I have found this bad bug.

I have patched it with a ghex2 and I have change chmod in 755 and WOW! All is perfect!!

But now, I need to understand HOW and WHERE you have find thet the problem was in netstat.

In linux, the most important thing is to understand how to solve and debug the problems!!

MANY Thanks!!
Alex

---

### Post by DDM on 2008-05-19
Thank god. I rely on NX to administrate my Media Center, and this bug was really getting on my nerves. Like the post above me, I used ghex2 to find "etl" and replaced it. I had to do a "Save As..." and moved the file over the old nxnode, and had to do a chmod 755.

---

### Post by rajwani on 2008-06-16
I have:

nxclient_3.2.0-9_i386.deb
nxnode_3.2.0-10_i386.deb
nxserver_3.2.0-13_i386

and I'm not seeing the problem anymore, with the previous versions I would get the timeout issues.

Happy that it's all working so well now, NX is the best!

Arif

---

### Post by nzgreen on 2008-07-01
I've just run into this problem using nxnode_3.2.0-11.  I also run a BitTorrent client on the box I was trying to connect to and it had been working fine for ages.

This version of nxnode is still running netstat -etl which takes over 2mins on my box (the timeout is 60sec).  The workaround is to install xfs.  nxnode will then find a running font server and won't bother running the netstat command.
```
sudo apt-get install xfs
```

See here for more details and another workaround:
[http://www.nomachine.com/tr/view.php?id=TR04F02051](http://www.nomachine.com/tr/view.php?id=TR04F02051)

---

