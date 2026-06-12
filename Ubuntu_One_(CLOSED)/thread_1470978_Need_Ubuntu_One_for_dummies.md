---
title: "Need Ubuntu One for dummies"
date: 2010-05-03
forum: Ubuntu One (CLOSED)
---

### Post by Randymanme on 2010-05-03
Ubuntu One doesn't seem to be working for me; maybe I'm just dumb.  I go through all the motions of clicking on upload file, click browse, attach files, click on upload.  Then at the bottom of the screen, it says “sending request to files.one.ubuntu.com.”  That's what it said last night (nine hours ago) and there was no change this morning.  What do I need to do?

Further,  the Ubuntu One Dashboard says
Files
You are currently using 308.4 MB of your 2.0 GB available for synchronized data.  While under the Account tab, it accurately says that I have 50 GB.  Why isn't the dashboard in sync with my account?

Also, Ubuntu One doesn't work, i.e., Ubuntu One under system > preferences doesn't connect me to Ubuntu One, nor does Ubuntu One under Me (upper right corner).  What to do?

Any help given me will be much appreciated.

---

### Post by duanedesign on 2010-05-03
Were you able to successfully add your computer? Does your machine show up under:

[https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)

When you say that opening Ubuntu One from the Me Menu does not connect you. Does it open the 'Preferences' Window? Does it open it is just that clicking on Connect does not Connect you?

The service is a little slow right now because of the spike in activity associated with the release. The Ubuntu One Team deployed a whole new infrastructure and server farm to cope with the increasing load. They are in the process of fine-tuning things to take advantage of the new capacity. This has made it hard for some to connect. You should be able to upload from the webUI however.

Do you have anything in your /.cache/ubuntuone/log/syncdaemon-exceptions.log

If you post the logs here make sure to put the text in Code Tags.
[HTML]```
log text here
```[/HTML]

---

