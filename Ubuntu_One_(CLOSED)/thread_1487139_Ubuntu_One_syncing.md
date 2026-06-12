---
title: "Ubuntu One syncing"
date: 2010-05-18
forum: Ubuntu One (CLOSED)
---

### Post by daz4126 on 2010-05-18
I like the look of Ubuntu One in Lucid. I'd like to set it up so that the Desktops of my 3 machines are all synced to the service. So anything I drop onto the desktop automatically appears on the desktop of all 3 computers. I would then use this for stuff I'm currently working on.

I've right-clicked on the desktop folder and selected 'sync with Ubuntu One' but so far I don't seem to be seeing the same things appearing on all the desktops.

Am I doing something wrong or is this just not possible?

cheers,

DAZ

---

### Post by duanedesign on 2010-05-19
Have you added all the computers to your Ubuntu One account. They show up under [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/) as well as in Me Menu -> Ubuntu One Preferences Panel under Devices.

---

### Post by joshuahoover on 2010-05-20
> **daz4126 said:**
> I like the look of Ubuntu One in Lucid. I'd like to set it up so that the Desktops of my 3 machines are all synced to the service. So anything I drop onto the desktop automatically appears on the desktop of all 3 computers. I would then use this for stuff I'm currently working on.

I've right-clicked on the desktop folder and selected 'sync with Ubuntu One' but so far I don't seem to be seeing the same things appearing on all the desktops.

Am I doing something wrong or is this just not possible?

cheers,

DAZ

This is possible. You'll need to make sure all the computers are setup on the same Ubuntu One account, as Duane recommended you check your account to make sure you see all the computers on the account. If things look OK there and files still aren't synchronizing to the other two computers, then you should try this from a terminal session (Applications->Accessories->Terminal):

```
touch ~/Desktop/placeholder; u1sdtool -q; u1sdtool -c
```

If after doing that you don't see files start to sync on the other two computers, we'll need you to file a bug report with debug logs. You can do that by following these steps:

1. Run the following from a terminal session: echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c 

2. File a bug report at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1_logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1_logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by daz4126 on 2010-05-21
Thanks for the responses guys.

I've definitely got all 3 computers added under devices.

When I try this code in the terminal:
touch ~/Desktop/placeholder; u1sdtool -q; u1sdtool -c

I get the following message:
ubuntuone-syncdaemon stopped.

I can't seem to get my desktop computer to connect. If I open the Ubuntu One Preferences panel and click on the 'connect' button it tries to connect (the button becomes unpressable), but nothing happens. It has connected a few times and said 'synchronisation in progress...' but nothing seems to have actually synced.

Should I file a bug report?

cheers,

DAZ

---

### Post by daz4126 on 2010-05-21
I tried Joshua's code above and a placeholder file appeared on the desktop. It has a little cloud and a cross in the corner. The Ubuntu One Preferences Panel says 'synchronisation in process' ... but this has been for about 10 minutes, surely it shouldn't take this long to synch such a small file?

DAZ

---

### Post by joshuahoover on 2010-05-21
> **daz4126 said:**
> I tried Joshua's code above and a placeholder file appeared on the desktop. It has a little cloud and a cross in the corner. The Ubuntu One Preferences Panel says 'synchronisation in process' ... but this has been for about 10 minutes, surely it shouldn't take this long to synch such a small file?

DAZ

Hi DAZ,

No, it shouldn't take 10 minutes to sync a file that size. Did you run the touch command on one of the other two computers you're trying to get synchronized? How many files are you trying to sync from the first computer to the other two?

I think it's probably time to file a bug report. Let me know the number and I'll be sure it gets looked into ASAP.

Thanks,

Joshua

---

### Post by daz4126 on 2010-05-22
Thanks for the reply Joshua.

I've realised that all 3 desktops the 3 computers had a lot of files on them, so maybe it was too much to be syncing all at once. I've removed all the folders from all the desktops and cleared everything from my Ubuntu One account. I will try to get it working again with a clean slate and if that doesn't work then I'll file a bug and let you know. While I was doing this, a couple of questions occurred to me:

1) When syncing between multiple devices, what takes precedence? For example if I removed a folder from one desktop, would it be removed from my Ubuntu One account and from all the other desktops?

2) Does syncing take place constantly? When I logged in just now, I had to open up the Ubuntu One Preferences panel and manually click connect.

cheers,

DAZ

---

### Post by daz4126 on 2010-05-22
Okay, starting afresh, I tried this code:
```
touch ~/Desktop/placeholder; u1sdtool -q; u1sdtool -c
```

And got this error message after about 30secs:

```
ubuntuone-syncdaemon still running.

Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Is this better filed as a bug?

DAZ

---

### Post by daz4126 on 2010-05-22
I've filed a bug - it's #584160:
[https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584160](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584160)

DAZ

---

### Post by daz4126 on 2010-05-23
I think the main problem is that my computer is not connecting properly to Ubuntu One.

I've just tried to buy some music from the Ubuntu One store through Rythmbox and it just says 'Connecting to the Ubuntu One store' and hangs.

I tried this code:
u1sdtool -q; killall ubuntuone-login; u1sdtool -c

And I just get the message:
ubuntuone-syncdaemon stopped.

Any way I can get myself connected because I think the idea of Ubuntu One is excellent and really want to use the service.

cheers,

DAZ

---

### Post by joshuahoover on 2010-05-24
> **daz4126 said:**
> I've filed a bug - it's #584160:
[https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584160](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584160)

DAZ

I replied to the bug report. I think you got that error because the syncdaemon is attempting to process all the delete requests (it does this in a suboptimal way right now, which we are going to address during the Maverick cycle). 

Thanks,

Joshua

---

### Post by joshuahoover on 2010-05-24
> **daz4126 said:**
> 
1) When syncing between multiple devices, what takes precedence? For example if I removed a folder from one desktop, would it be removed from my Ubuntu One account and from all the other desktops?

Yes, unless the folder on your other desktop had files that were modified locally that would cause a conflict to occur. In this case, the folder would be marked as Desktop.u1conflict and left for you to decide what to do with it (delete it or not in this case).

> 2) Does syncing take place constantly? When I logged in just now, I had to open up the Ubuntu One Preferences panel and manually click connect.

Ubuntu One should automatically connect at startup. If it continues to not connect at startup, let me know. The best way to see if it's connected right now (for troubleshooting purposes) is to run the following command about a minute after you login to your computer: u1sdtool -s

The "is_connected" part of the output from that command should show "True" if it's connected. If it's not "True" then it may be that we have a problem connecting when syncdaemon is very busy processing files. I'm not sure, that's just a guess. I'll need to follow up with some developers if you continue to not be able to auto-connect at startup.

Thank you,

Joshua

---

### Post by daz4126 on 2010-05-28
Hi Joshua,

Thanks for all your help on this. I'm still having to connect manually each time I log in. I've been leaving it to do its thing for a few hours now, hoping that those delete requests will get processed, but as yet things are still not syncing. There would be over 1000 files on my Desktop that now need deleting (although most of them were small text files). Any idea how long it will take and is there any way of knowing when the sync daemon has got through all the requests?

The good news is that I can connect to the music store now, although I'm holding off ordering any music until I know that the syncing stuff is working.

Thanks again,

DAZ

---

### Post by duanedesign on 2010-05-28
daz4126,
Some commands I use when I want to monitor a sync are:

leave this terminal window open to see what gets written to syncdaemion.log
```
tail -fn 50 ~/.cache/ubuntuone/log/syncdaemon.log
```

To see how many metadata/content items are waiting to sync.
```
u1sdtool --waiting-metadata | wc -l
```

```
u1sdtool --waiting-content | wc -l
```

You can also run the last two commands with out the |wc -l. The wc -l is helpfull though.  Running it over time you can see if the numbers get smaller.

thank you,
duanedesign

[Ubuntu One Client Control]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl")

---

### Post by daz4126 on 2010-05-28
Cheers for those commands duanedesign - turns out there are over 3000 metadata requests queued up, which I think are the delete requests (are they known as 'unlink'. They are reducing slowly, so I'll just stick with it.

DAZ

---

### Post by daz4126 on 2010-05-28
Crikey! Joshua, I know you said it was slow, but it's taken about 4 hours to delete 200 metadata files and there are still 3000 left! Is there any way to speed the process up ... reset the account or something?

cheers,

DAZ

---

### Post by daz4126 on 2010-05-31
It is taking a whole day to clear 500 metadata files, but each new day, there are about 200 new ones and I haven't even used Ubuntu One. All I do, is connect then let it sync. Where can these new files be coming from and why is it taking so long to clear them?

DAZ

---

### Post by daz4126 on 2010-06-22
Just wanted to say a belated Thank You to Joshua and duanedesign.

I totally overloaded Ubuntu One with files when I first tried using it, but when the backlog had cleared it started to work perfectly.

I can not save any files to my desktop and have access to them on the desktops of all 3 of my computers.

I can also create backups of important files right on the desktop using the built in Ubuntu One folder.

I also have web access to all my files at work.

The music service is also excellent. I've bought a number of songs and been really impressed with the way the music is automatically saved online to my One account and also saved in my Music folder.

This is an amazing service, thanks to everbody that helped to make it happen. To me it is a killer app for Ubuntu - a cross between iTunes and Dropbox!

Thanks again,

DAZ

---

### Post by duanedesign on 2010-06-23
> **daz4126 said:**
> Just wanted to say a belated Thank You to Joshua and duanedesign.

I totally overloaded Ubuntu One with files when I first tried using it, but when the backlog had cleared it started to work perfectly.

I can not save any files to my desktop and have access to them on the desktops of all 3 of my computers.

I can also create backups of important files right on the desktop using the built in Ubuntu One folder.

I also have web access to all my files at work.

The music service is also excellent. I've bought a number of songs and been really impressed with the way the music is automatically saved online to my One account and also saved in my Music folder.

This is an amazing service, thanks to everbody that helped to make it happen. To me it is a killer app for Ubuntu - a cross between iTunes and Dropbox!

Thanks again,

DAZ

Thank you for taking the time to provide some positive feedback. All to often people only make noise when they are frustrated. I am glad you are enjoying the service. I agree with you, Ubuntu One, is super useful.

I heard yesterday there were some new changes made server side. I synced some files late last night and was very pleased by the speed. 

thanank you,
duanedesign

---

### Post by daz4126 on 2010-07-27
Thanks duanedesign - I agree that we need to make more time to say thanks when we get help.

It blows me away how good the software in Ubuntu is and how ready the community is to help if things don't work.

Ubuntu One keeps getting better and better - could be the 'killer app' for Ubuntu!

Keep up the good work helping people with Ubuntu One!

DAZ

---

