---
title: "Lost everything on UbuntuOne when added &quot;new&quot; computer"
date: 2010-05-06
forum: Ubuntu One (CLOSED)
---

### Post by Colin Keenan on 2010-05-06
Upgrade from 9.10 karmic to 10.04 lucid failed so I did a clean install.  Followed tutorial to add "new" computer to my UbuntuOne account.  It was actually the same computer wiped clean with a new install.  I clicked on connect and waited a really long time but no files were showing up in my local UbuntuOne folder.  I also had to keep clicking connect as it kept dropping the connection.

After waiting almost 1/2 an hour, decided to start manually downloading some files.  I managed to save a few trivial files that way, but pretty soon, everything was gone off the cloud!  The sync matched the cloud to my empty new install instead of the other way around.

I lost everything but those trivial files I downloaded before everything was gone.

Is there anyway to get the stuff back?  If I had really added a second computer, I could just get everything from the first computer.  But, this "second" computer was the same computer, so I lost everything.  Why would UbuntuOne work this way?  When first adding a second computer, it would make more sense to bring it up to date with the first computer by downloading all the files, not by deleting all the files online to make it match the empty new computer!

---

### Post by rtg on 2010-05-07
Hello, could you please run the script from [http://people.canonical.com/~roman.yepishev/ubuntuone-scripts/ubuntuone-account-info](http://people.canonical.com/~roman.yepishev/ubuntuone-scripts/ubuntuone-account-info) - that will give you the information that we will require to identify you and perform recovery.

I have filed a bug report - [LP:576912]("http://launchpad.net/bugs/576912")

Could you please provide the output of ubuntuone-account-info to [LP:576912]("http://launchpad.net/bugs/576912") so that we can start recovery process.

It would be great if you could provide the logs for syncdaemon activity from ~/.cache/ubuntuone/log - they may help to determine the reason of such behavior.

---

### Post by Colin Keenan on 2010-05-13
Thanks,

I have followed your instructions in LP:576912.  I don't know why I didn't get an email when you commented on this thread.  If I had, I would've followed your instructions days ago.

I had also filed a bug report, but I will just follow yours.

---

### Post by joshuahoover on 2010-05-14
> **Colin Keenan said:**
> Thanks,

I have followed your instructions in LP:576912.  I don't know why I didn't get an email when you commented on this thread.  If I had, I would've followed your instructions days ago.

I had also filed a bug report, but I will just follow yours.

Hi Colin, 

Thank you for providing all the information we requested. We have someone on the team looking into this right now and we'll follow up with comments on the bug. I've marked the bug as private so that others can't see the info you posted.

Thank you,

Joshua

---

