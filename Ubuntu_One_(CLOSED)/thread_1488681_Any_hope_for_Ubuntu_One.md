---
title: "Any hope for Ubuntu One?"
date: 2010-05-20
forum: Ubuntu One (CLOSED)
---

### Post by Sisophon2001 on 2010-05-20
I upgraded to Ubuntu 10.04 as soon as it was released, and since then Ubuntu One has refused to synchronize with my online files. Only one file downloaded to my new install (and that was a file I modified on a second computer), five or six files are left. In total I use only 217KB. 

It is currently cycling between "Disconnected" or "Synchronization in progress" or "Synchronization Complete" but nothing is downloaded.

Depending on the activity I get this output from u1sdtool -s

State: AUTHENTICATE
    connection: With User With Network
    description: doing auth dance
    is_connected: True
    is_error: False
    is_online: False
    queues: IDLE

Or this:

State: WAITING
    connection: With User With Network
    description: waiting before try connecting again
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

Or this:

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

After two weeks, I am about to give up. Can it really take this long to fix? Are there any alternatives?

Garvan

---

### Post by duanedesign on 2010-05-20
That is definitely not how the program/service should be acting. Things were a little slow around the release but that has improved greatly.

> queues: IDLE

you should not reach that until all your files are synced.

I noticed you said you upgraded. Could you try the following and see if creating a new syncdaemon.conf helps.

Quit Ubuntu One Preferencese Panel ( if its open)

Open a terminal and run:
```
u1sdtool -q
```

Then rename the old syncdaemon.conf.
```
mv ~/.config/ubuntuone/syncdaemon.conf ~/.config/ubuntuone/syncdaemon.conf.orig
```

run in a Terminal:

```
u1sdtool --start; u1sdtool -c
```


Then give it about a minute and run u1sdtool -s
Could you please post that here?

---

### Post by hartl_vienna on 2010-05-20
> 
After two weeks, I am about to give up. Can it really take this long to fix? Are there any alternatives?


I tried it several weeks, but I cancelled my account today. U1 is so buggy that it's unusable. I filled a lot of bug reports, but I didn't get an answer so far. 

Sorry for that, maybe I will try it again in a few month.

---

### Post by joshuahoover on 2010-05-20
For those having issues: First, apologies for the inconvienence and hassle. Our intent is to release reliable software. With that said, we realize bugs happen for a variety of reasons and, aside from eliminating bugs prior to release, we want to fix them ASAP. It doesn't make us feel good when we hear that people are frustrated with our software. We want all of you to have a great experience with Ubuntu One. That is our goal, bottom line.

Now, if you're having a problem that you don't see an answer for in our [FAQ]("https://wiki.ubuntu.com/UbuntuOne/FAQ") or a status for on our [status]("https://wiki.ubuntu.com/UbuntuOne/Status") page, then the best bet is to file a bug report. Due to the interest in Ubuntu One and the many different channels to request help, we sometimes get a backlog in a particular channel. I think we have a log jam right now with bug reports. I'm going to make sure we (the Ubuntu One team) address this ASAP. 

To file a bug report with the most useful information, here are the steps you should take (I'm going to add this to the FAQ):

1. Run the following from a terminal session: 
echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf \
sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py \
u1sdtool -q; u1sdtool -c

2. Attempt to reproduce the problem you're experiencing and file a bug with as much info (steps you took that resulted in the problem, your setup (multiple computers?), etc) at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1_logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1_logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by bootedguy on 2010-05-21
I have installed 10.04 on three of my computers.  Two were clean installs, the other was an update from 9.10.  Two are 64 bit, one is 32 bit.  Processors are I7, dual core (a laptop), and an AMD.  All three  are registered with the website, and all show up in the Ubuntu One Preferences  menu.  When I try to sync, I get a syncing in progress, and syncing completed messages. But nothing happens.  I have tried repeatedly.  On my laptop I tried uninstall and reintall.  No change.  No error  messages.

I feel like it must be something I have done or missed since the problem is the same on such different PCs.  Very frustrating.

Bootedguy

---

### Post by hartl_vienna on 2010-05-21
Hi joshuahoover!

In fact I'm not frustrated with Ubuntu One. I understand that this is just the beginning of a great project and it need some time to become as stable as it should be. **In the future I'll definitely use Ubuntu One.** But at the moment I can't use it because it simply doesn't work.

I have one example:
There is a problem with one of my notes. I can't open it and I can't delete it. And I think this problem cause also the syncing problems with Tomboy. I'm working on different computers and notes are very important for me. 

I didn't find a way to get support. I also tried to delete my account and start from the scratch, with no success.

So this is the reason why I will try it in a few month again. But nevertheless Ubuntu One is absolutly fantastic and I can't wait until I can use it again. :)

[https://bugs.launchpad.net/ubuntuone-client/+bug/578365]("https://bugs.launchpad.net/ubuntuone-client/+bug/578365")
[https://bugs.launchpad.net/ubuntuone-client/+bug/571900]("https://bugs.launchpad.net/ubuntuone-client/+bug/571900")

PS: I don't know, maybe my bug reports are just scrap. If yes, I would appreciate if someone could tell how to do it better.

---

### Post by joshuahoover on 2010-05-21
> **bootedguy said:**
> I have installed 10.04 on three of my computers.  Two were clean installs, the other was an update from 9.10.  Two are 64 bit, one is 32 bit.  Processors are I7, dual core (a laptop), and an AMD.  All three  are registered with the website, and all show up in the Ubuntu One Preferences  menu.  When I try to sync, I get a syncing in progress, and syncing completed messages. But nothing happens.  I have tried repeatedly.  On my laptop I tried uninstall and reintall.  No change.  No error  messages.

I feel like it must be something I have done or missed since the problem is the same on such different PCs.  Very frustrating.

Bootedguy

Hi! Can you please file a bug report following the steps I posted in this thread and let me know the bug #? I want to get this working for you but will need to see some debug logs to do that. :)

Thanks!

Joshua

---

### Post by joshuahoover on 2010-05-21
> **hartl_vienna said:**
> Hi joshuahoover!

In fact I'm not frustrated with Ubuntu One. I understand that this is just the beginning of a great project and it need some time to become as stable as it should be. **In the future I'll definitely use Ubuntu One.** But at the moment I can't use it because it simply doesn't work.

I have one example:
There is a problem with one of my notes. I can't open it and I can't delete it. And I think this problem cause also the syncing problems with Tomboy. I'm working on different computers and notes are very important for me. 

I didn't find a way to get support. I also tried to delete my account and start from the scratch, with no success.

So this is the reason why I will try it in a few month again. But nevertheless Ubuntu One is absolutly fantastic and I can't wait until I can use it again. :)

[https://bugs.launchpad.net/ubuntuone-client/+bug/578365](https://bugs.launchpad.net/ubuntuone-client/+bug/578365)
[https://bugs.launchpad.net/ubuntuone-client/+bug/571900](https://bugs.launchpad.net/ubuntuone-client/+bug/571900)

PS: I don't know, maybe my bug reports are just scrap. If yes, I would appreciate if someone could tell how to do it better.

Thank you for the kind words and posting the bug numbers here. I'm following up on both. I'll need to get in contact with one of the devs on the team who is most familiar with notes syncing issues. Once I do (Monday), I'll update the bugs.

Oh yes, your bug reports are good ones. :)

Thanks!

Joshua

---

### Post by Sisophon2001 on 2010-05-24
> **duanedesign said:**
> <snip>
Then give it about a minute and run u1sdtool -s
Could you please post that here?


State: AUTHENTICATE
    connection: With User With Network
    description: doing auth dance
    is_connected: True
    is_error: False
    is_online: False
    queues: IDLE

No change that I can see. I think I mislead you when I said I upgraded from 9.10. What I did was a backup of home, and a full new install. I copied back only visible folders .fonts, email and FF bookmarks.

Thanks for you help, and sorry for the slow reply, I was out of town this weekend.

Garvan

---

### Post by Sisophon2001 on 2010-05-24
> **joshuahoover said:**
> For those having issues: First, apologies for the inconvienence and hassle. Our intent is to release reliable software. With that said, we realize bugs happen for a variety of reasons and, aside from eliminating bugs prior to release, we want to fix them ASAP. It doesn't make us feel good when we hear that people are frustrated with our software. We want all of you to have a great experience with Ubuntu One. That is our goal, bottom line.

Now, if you're having a problem that you don't see an answer for in our [FAQ]("https://wiki.ubuntu.com/UbuntuOne/FAQ") or a status for on our [status]("https://wiki.ubuntu.com/UbuntuOne/Status") page, then the best bet is to file a bug report. Due to the interest in Ubuntu One and the many different channels to request help, we sometimes get a backlog in a particular channel. I think we have a log jam right now with bug reports. I'm going to make sure we (the Ubuntu One team) address this ASAP. 

To file a bug report with the most useful information, here are the steps you should take (I'm going to add this to the FAQ):

1. Run the following from a terminal session: 
echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf \
sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py \
u1sdtool -q; u1sdtool -c

2. Attempt to reproduce the problem you're experiencing and file a bug with as much info (steps you took that resulted in the problem, your setup (multiple computers?), etc) at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1_logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1_logs.tar.bz2 to the bug report

Thank you,

Joshua

Thanks for your help. 

The process of filing bugs is not easy despite the tools designed to help. It takes about half an hour of studying the instructions to get it correct. Do not expect all users to manage to complete the task. Your summary will be helpful and I will try it tonight.

I still have the option of un-installing and reinstalling Ubuntu One. I will do that first before filing a bug report.

Best regards,

Garvan

EDIT:

Reinstalling Ubuntu One (U1) did not work. Deleting and re-registering my computer with U1 did not work.

Is it possible to copy U1 settings from by UBR 10.04 computer to my desktop computer? My UNR Netbook is working properly with U1.

Garvan

---

### Post by FrancoNero on 2010-05-24
I am also back to Dropbox for now. I need a reliable backup mechanism for my documents, and Ubuntu One just doesn't sync the way it is supposed to. I wonder how Dropbox can deliver a better service on ubuntu than Ubuntu One, which is sort of a product out of the same house

---

### Post by joshuahoover on 2010-05-24
> **Sisophon2001 said:**
> Reinstalling Ubuntu One (U1) did not work. Deleting and re-registering my computer with U1 did not work.

Is it possible to copy U1 settings from by UBR 10.04 computer to my desktop computer? My UNR Netbook is working properly with U1.

Garvan

Garvan, 

I'm sorry to hear Ubuntu One is still not working properly for you. I realize the steps for filing a bug take a while but at this point I need to see those debug logs to get a better look at what might be causing you so many problems with the service. If you can do that and post the bug number here I'll look into it ASAP.

Thank you,

Joshua

---

### Post by Sisophon2001 on 2010-05-25
Joshua,

I will file the bug report, but my habit is to try everything I can first to understand the problem so I can make the bug report as helpful as possible.

This is what I have tried tonight.
1. I copied the missing files to my U1 folder from a USB drive and they synced correctly, with the green check mark shown on each file.
2. Nautilus still shows that U1 is not synchronised. It displays an icon with an emblem for "Ubuntuone-unsynchronized" for the Ubuntu One folder. If I change the emblem manually, it immediately reverts to unsynchronized
3. I created a new file and it uploaded correctly to the web site from my U1 folder. This did not work before I copied the missing files in manually.
4. My UNR Netbook does not download the new file. It now displays the unsynchronized emblem, where previously it displayed a synchronized emblem. My conclusion is that both my installs of U1 are not working correctly.

My next step will be to test my UBR Netbook with a different network.

Best regards,

Garvan

EDIT1: Using a different network made no difference.

EDIT2: A Bug has already been files with what seems the same problem, BUG: 583295
When I follow your instructions using apport-collect I am warned that I am not the owner of the bug report and it is much easier to do something else which I do not understand and do I really want to proceed?

So, should I file a new duplicate bug report instead, or try attaching details to an existing bug report?

Garvan

---

### Post by joshuahoover on 2010-05-25
> **Sisophon2001 said:**
> Joshua,

I will file the bug report, but my habit is to try everything I can first to understand the problem so I can make the bug report as helpful as possible.

This is what I have tried tonight.
1. I copied the missing files to my U1 folder from a USB drive and they synced correctly, with the green check mark shown on each file.
2. Nautilus still shows that U1 is not synchronised. It displays an icon with an emblem for "Ubuntuone-unsynchronized" for the Ubuntu One folder. If I change the emblem manually, it immediately reverts to unsynchronized
3. I created a new file and it uploaded correctly to the web site from my U1 folder. This did not work before I copied the missing files in manually.
4. My UNR Netbook does not download the new file. It now displays the unsynchronized emblem, where previously it displayed a synchronized emblem. My conclusion is that both my installs of U1 are not working correctly.

My next step will be to test my UBR Netbook with a different network.

Best regards,

Garvan

EDIT1: Using a different network made no difference.

EDIT2: A Bug has already been files with what seems the same problem, BUG: 583295
When I follow your instructions using apport-collect I am warned that I am not the owner of the bug report and it is much easier to do something else which I do not understand and do I really want to proceed?

So, should I file a new duplicate bug report instead, or try attaching details to an existing bug report?

Garvan

Hi Garvan,

Since it's hard to say whether your bug is the same or not (since we can't see your debug logs), it's better to file a new bug report. Let me know the number here and I'll be sure to follow up on it.

Thanks,

Joshua

---

### Post by Sisophon2001 on 2010-05-26
I filed a bug report from my Netbook. All files are now showing as synced, and the icons show it is synced, but not all files have been downloaded from the server. At first I thought it was working properly because of the icons, but on second check I can see that there are missing files.

The report number for my Netbook is 585840

Thanks

Garvan

---

### Post by dulbirakan on 2010-05-27
> **FrancoNero said:**
> I am also back to Dropbox for now. I need a reliable backup mechanism for my documents, and Ubuntu One just doesn't sync the way it is supposed to. I wonder how Dropbox can deliver a better service on ubuntu than Ubuntu One, which is sort of a product out of the same house

I guess it is because they have had a longer time to develop it. I believe if we wait some more the people at canonical will fix it.

---

### Post by bootedguy on 2010-05-28
Hi Joshua,

Sorry it took so long to get back on this.  I don't think the first time I tried to file a bug report, I did it correctly.

After doing a complete uninstall/reinstall, I was able to get my laptop to upload a few files.  Unfortunately, a day later Ubuntu One would not work again.  The bug report was filed for the laptop.

Ironically, a year or so when Ubuntu One was first introduced (I can't remember which version of the OS I was using), Ubuntu One really worked well for me.

Bootedguy

---

### Post by Sisophon2001 on 2010-05-29
Hi,

I think my Netbook is now syncing correctly with the help of duanedesign (see [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/585840]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/585840"))
- but my desktop will still not synchronize. I have created a new bug report for my desktop. Bug #587120

Thanks for all the help so far.

Garvan

---

