---
title: "Restore EE server"
date: 2009-01-17
forum: Server Platforms
---

### Post by Nirva on 2009-01-17
Hay,

recently I stumbled upon Restore-EE on this site [Restore manual]("http://www.howtoforge.com/restore-ee-user-manual").

In the manual they talk about ubuntu/debian packages.  I googled quite a lot but I couldn't find them on the internet...  
Does anyone knows where I can find them ?

Or give me an alternative for restore ?
I know about the existence of bacula and amanda but they dont meet the following constraints ( unless one of you can prove me wrong )

- Supports Linux, Windows and OSX backup
- Easy to use (web)interface for the clients ( not only for the server )
- Free

Thanks

---

### Post by HermanAB on 2009-01-17
There is nothing like what you want.  On Linux the best backup solutions are specialized and automated to the point where they are maintenance and worry free, using rsync.  So DIY is pretty much the name of the game.

Cheers,

Herman

---

### Post by flandercan on 2009-07-29
Hi, 

This is an old post , but I just stumbled across restore-ee , it is a great product, schedule backups over sftp, ftp and mysql. 

Perfect for what I need and does indeed work really well although I am running into a small problem, 

I can only find an ISO on SF based on GUTSY and can not update the system to fix some SSH problems.

After trying a full upgrade to Hardy it completely broke restore-ee !! It does say in some How-To-Forge docs that restore-ee is available via APT but I can not find it :-(

The restore-ee web site has moved to SF but has very little info, so if anyone uses the product and has managed to get it running on a later version of ubuntu or managed to upgrade somehow, I would be great full to find out how.

Thanks 
Paul

---

### Post by flandercan on 2009-07-30
ok a little bit of hunting around and I found

[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

Altered "/etc/apt/source_list" and ran "apt-get update" and "apt-get upgrade" the system now works correctly and all of the issues around sftp backup have been resolved (Which was the old ssh blacklist issue because openssh was an oldish version).


fc

---

