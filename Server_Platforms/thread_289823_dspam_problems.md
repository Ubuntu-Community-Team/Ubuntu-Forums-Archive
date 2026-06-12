---
title: "dspam problems"
date: 2006-10-31
forum: Server Platforms
---

### Post by sclough on 2006-10-31
Is anybody else running DSPAM and having any problems?  My problems seem to mostly be with the UI.  I frequently get an error when trying to do things and stuff like retraining sometimes takes a very long time to reload the page.  I'm going to restrat MySQL with the log running query option to see if I need to add some indexes, but now I have a new strange problem.  If you retrain a message, it will not retrain.  For example, if it's in the quarantine and you select "deliver checked" it removes it from quarantine, but does not show it as retrained in the history and does not actually delete the message.  Has anybody seen this kind of problem?

I'm using the lastest Dapper version and running the UI using SUEXEC as well as Apache 2.0.

---

### Post by jimm on 2006-10-31
Hi,

I installed DSPAM a while back and had masses of problems with the UI and getting it all working correctly. Whilst it was a good product, when I upgraded to Ubuntu I decided not to bother with it any more as it was such a pain to get going and I didn't write down what I did to get it working properly! (D'oh!)

However I do remember that most of my problems involved permissions and user setup when the CGI apps run. 

I had them running as a user called dspam, but I didn't notice that the dspam user had no rights on any of the log files or log directories. This caused issues with the interface (no history, nothing updating properly). So I would check that the dspam user and group (if you have one) has access to _all_ of the log directories and files dspam generates, otherwise the GUI doesn't work and doesn't give you a lot of feedback either.

I will try and load this app again sometime... when I get my stamina and tolerance levels back!

Thanks,
James

---

### Post by sclough on 2006-10-31
I think my permission are all good.  I found something interesting in the apache logs.  There are a lot of lines saying:
```

[error] Query call failed: MySQL server has gone away (2006)

```

I can't figure out why though.  It happens whether I tell DSPAM to go through the local socket or use TCP/IP connections.  I'm guessing the CGI must call the dspam client and it must be the one that's generating these errors, since I'm not seeing errors from the daemon in the mail.log.

---

### Post by byramm on 2008-07-18
The problem is not with dspam, but with libapache2-mod-auth-mysql (you can verify this by creating a text file under /var/www/dspam and trying to access that file).

Upgrading the package has proved successful so far... see also [http://ubuntuforums.org/showthread.php?t=641162](http://ubuntuforums.org/showthread.php?t=641162)

---

