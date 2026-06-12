---
title: "Multiple Ubuntu One Problems"
date: 2010-04-28
forum: Ubuntu One (CLOSED)
---

### Post by flloyd on 2010-04-28
I'm having nothing but problems with Ubuntu One.

I made the mistake of selecting to sync a folder with Ubuntu a few weeks ago when I was testing out Lucid and noticed it as an option. What a huge mistake. Ubuntu One has since spent the last week thrashing my hard drive constantly while doing absolutely nothing productive. The foloder is huge (100+ GBs of Flacs) so I have tried to cancel syncing since I realized that it started immediately without any notice.

Telling it to stop syncing in nautilus does nothing. There is no option to delete the folder on the website. I have completely uninstalled Ubuntu One and even deleted my account. No matter what I do Ubuntu One always starts thrashing my hard drive and brings down my computer to a halt. The only reason I reinstalled Ubuntu One was to use the music store (who's idiotic decision was that to require Ubuntu One to purchase music?). Now I've wasted $3 and Ubuntu won't even let me have access to my songs. It downloaded one and now the other three are nowhere to be found.

Rhythmbox won't even open up now since Ubuntu One has killed it.

What the heck am I supposed to do? There isn't even a support link for Ubuntu One.

Any help would be greatly appreciated that would get me the songs I purchased and forever purge Ubuntu One from my computer. Thanks in advance.

---

### Post by wojox on 2010-04-28
Did you remove ubuntuone from the start up applications?

---

### Post by flloyd on 2010-04-28
Thanks, I just did that. I still need to get my songs somehow though. Or a refund would be perfectly acceptable. Don't want to deal with Canonical's shoddy software anymore.

---

### Post by ajgreeny on 2010-04-28
I always knew I didn't trust on-line services such as that.  I don't think I will ever have an inclination to try ubuntu-one or any other "cloud" storage system as I don't want to lose control of my own data to some nebulous place, which through no fault of my own, could lose it for me.

I do hope you manage to get around your problem, but can give you no ideas about how to do it, I'm afraid.

PS:

Are you really using 7.04, Feisty fawn, or have you just not updated your profile?  If you are still on 7.04, could that be part of the problem?

---

### Post by flloyd on 2010-04-28
Nope now on Lucid, I've now updated that. Thanks. Haven't been on this forum in ages.

The problem is not with cloud services but with U1's software. I've used JungleDisk and Dropbox for the last ~3 years and the expirience has been pretty much flawless. With JungleDisk you only pay for what you use ($0.15/GB) which is great and I've never had any problems. Dropbox is like U1 but works on all three OS's, is bug free, and has more features.

The only reason I tried U1 again was to get the music store working. Once Canonical can help me get my songs then I can uninstall U1 again. I just have no clue how to get help since they only have FAQs and Developer support on the U1 site.

---

### Post by thebear78 on 2010-04-28
Hi flloyd,

Happy to help. Just saw this post in my daily digest. I'm actually updating the music store help information ("Help" link in the music store) right now in preparation for the official launch tomorrow.

Selecting a folder to sync that exceeds your Ubuntu One plan's capacity should only synchronize up to the plan limit. The sync client does have to do quite a bit of work to index the files in the folder in the first place so that's most likely the reason for the churn.

Your purchase should have first transferred from 7digital to your Ubuntu One personal cloud. Check [https://one.ubuntu.com/files](https://one.ubuntu.com/files) and verify. If the transfer did not complete, click on the 'try again' link on the My Downloads page of the music store. If that still doesn't work, we are running a script (hopefully tonight if we can get some infrastructure improvements completed) that should automatically kick off the process of grabbing purchased songs from 7digital and transferring them to your Ubuntu One personal cloud. Once they are in the cloud, you can either wait for them to sync or go to [https://one.ubuntu.com/files](https://one.ubuntu.com/files) and manually download them.

Sorry for the inconvenience. Much of this is related to the infrastructure improvements we have been implementing over the last 24 hours. Once they are in place, everyone should see performance improvements.

Matt

---

### Post by flloyd on 2010-04-28
Hi, thanks for getting to me.

the problem with the indexing is that it never stops. i let my computer run overnight and it was still thrashing my hard drive and hardly any files had been uploaded. Worse of all when I tell U1 to stop synschronizing the folder it never does. I've tried uninstalling U1 using the directions provided and dleting every trace of it that I could find, deleting my subscription online, and still as soon as I reinstall and sign up again it finds the "synced" folder in my U1 account and starts all over again. Is there no way to delete the synced folder from the U1 account online?

As for 7digital songs. As I stated, only one made it to U1. I would love to "try again" but as I stated Rhythmbox no longer works as long as I have U1 installed.

Once (if) I get my songs, how do I permanently delete my account? Last time I did it they still kept my synced folder even though U1 claimed that they would delete all files.

---

### Post by joshuahoover on 2010-04-29
> **flloyd said:**
> Hi, thanks for getting to me.

First, I'm sorry our software is playing nice on your computer. You  should be able to stop the synchronizing in situations like this. I'm  going to try to reproduce this problem and file a bug with the steps so  we can look into this further and get it fixed.

> the problem with the indexing is that it never stops. i let my computer run overnight and it was still thrashing my hard drive and hardly any files had been uploaded. Worse of all when I tell U1 to stop synschronizing the folder it never does. I've tried uninstalling U1 using the directions provided and dleting every trace of it that I could find, deleting my subscription online, and still as soon as I reinstall and sign up again it finds the "synced" folder in my U1 account and starts all over again. Is there no way to delete the synced folder from the U1 account online?

Now onto the problem at hand... OK, so you still have Ubuntu One installed? To stop it from syncing, can you try the following command in a terminal session (Applications->Accessories->Terminal):

killall ubuntuone-syncdaemon

Then, if you want to uninstall Ubuntu One, run the following command:

apt-get remove ubuntuone-client*

> As for 7digital songs. As I stated, only one made it to U1. I would love to "try again" but as I stated Rhythmbox no longer works as long as I have U1 installed.

Is this because of the high resource usage of Ubuntu One or is the Ubuntu One Music Store plugin not allowing you to open Rhythmbox? If Rhythmbox won't open, can you try opening it from a terminal session and report back any errors/messages: rhythmbox

> Once (if) I get my songs, how do I permanently delete my account? Last time I did it they still kept my synced folder even though U1 claimed that they would delete all files.

We currently don't delete the files right away. We're going to fix this in the not too distant future. So, for now, it can take several days for the files to actually go away. Contact Matt or I directly if you want your files completely removed and we'll make sure it gets done ASAP.

Thank you,

Joshua

---

### Post by joshuahoover on 2010-04-29
> **ajgreeny said:**
> I always knew I didn't trust on-line services such as that.  I don't think I will ever have an inclination to try ubuntu-one or any other "cloud" storage system as I don't want to lose control of my own data to some nebulous place, which through no fault of my own, could lose it for me.

We realize our services aren't for everyone, but I do want to clarify that Ubuntu One synchronizes content, which means it is on local devices as well as in the cloud. We aren't doing a cloud storage like some where you put your content up in the cloud and that is the only place it is accessible. There are pros and cons to both approaches but we think synchronization gives you the best of both worlds.

Thank you,

Joshua

---

### Post by flloyd on 2010-04-29
Thanks, I've already uninstalled U1 since that was the only way to get it to stop thrashing my hard drive. Maybe I'll retry it once it's out of alpha status.

Now I'm just waiting to get my songs since they still haven't shown up on U1's website. I think I might be suffering from [this bug]("https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/547074") though. Since I ordered [this "single"]("http://us.7digital.com/artists/uffie/pop-the-glock-remixes/").

Still haven't heard back from U1's billing assistance about getting my songs or a refund yet though. Though it's only been about 24 hours I guess and I'm sure Lucid's launch is hurting them as well.

Sorry I can't help with the Rhythmbox bug since I've uninstalled the Music Store and U1 and won't be trying again. The problem was that as long as I had the plugin installed after ordering the songs I couldn't open Rhythmbox. The icon would be visible in the system tray but if I clicked it rather than getting the usual dropbox (Show Rhythmbox, Skip, etc) I got a small, square. empty blob (about 12x12 pixels) and that's it. There wasn't anyway to get it to display. I don't think this was caused by U1's resource hogging though since Firefox and other programs worked, though they frequently paused and went dark.

---

### Post by thebear78 on 2010-04-30
> **flloyd said:**
> Thanks, I've already uninstalled U1 since that was the only way to get it to stop thrashing my hard drive. Maybe I'll retry it once it's out of alpha status.

Now I'm just waiting to get my songs since they still haven't shown up on U1's website. I think I might be suffering from [this bug]("https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/547074") though. Since I ordered [this "single"]("http://us.7digital.com/artists/uffie/pop-the-glock-remixes/").

Still haven't heard back from U1's billing assistance about getting my songs or a refund yet though. Though it's only been about 24 hours I guess and I'm sure Lucid's launch is hurting them as well.

Sorry I can't help with the Rhythmbox bug since I've uninstalled the Music Store and U1 and won't be trying again. The problem was that as long as I had the plugin installed after ordering the songs I couldn't open Rhythmbox. The icon would be visible in the system tray but if I clicked it rather than getting the usual dropbox (Show Rhythmbox, Skip, etc) I got a small, square. empty blob (about 12x12 pixels) and that's it. There wasn't anyway to get it to display. I don't think this was caused by U1's resource hogging though since Firefox and other programs worked, though they frequently paused and went dark.

Billing Assistance... that's me :) Right now, we are running a process that will automatically transfer your songs to your Ubuntu One storage. You can use your web browser and get them from [https://one.ubuntu.com/files](https://one.ubuntu.com/files) if you prefer.

If you still want a refund, please click on Help in the Ubuntu One Music Store and scroll down to Contact Us. 7digital handles the billing for the music store and their Customer Service team will have to handle any refunds.

---

### Post by dumas33 on 2010-04-30
It looks I did same mistake. :(
When trying new features in nautilus I clicked on sync on Ubuntu One of Downloads (20Gb). So, each time after logging in I need to wait for 5 minutes to start to work Ubuntu syncdeamon consumes 50-70% of my CPU, and hard disks turns a-round all the time.
Stop syncing does not work - I still can see sync icon on forders.

I purged Ubuntu-one from PC using:
apt-get purge ubuntuone-client*

Speed improvements were exciting. But I decided to reinstalled u1 again. Somehow U1 remembers, folder that needs to be sync, and again, I cant use my PC for a 5 minutes after logging in. 
How to remove that folder from syncing? 
Or U1 is to buggy and I need to look for something else?

---

### Post by joshuahoover on 2010-04-30
> **dumas33 said:**
> It looks I did same mistake. :(
When trying new features in nautilus I clicked on sync on Ubuntu One of Downloads (20Gb). So, each time after logging in I need to wait for 5 minutes to start to work Ubuntu syncdeamon consumes 50-70% of my CPU, and hard disks turns a-round all the time.
Stop syncing does not work - I still can see sync icon on forders.

I purged Ubuntu-one from PC using:
apt-get purge ubuntuone-client*

Speed improvements were exciting. But I decided to reinstalled u1 again. Somehow U1 remembers, folder that needs to be sync, and again, I cant use my PC for a 5 minutes after logging in. 
How to remove that folder from syncing? 
Or U1 is to buggy and I need to look for something else?

You can stop synchronizing a file by running the following command in a terminal session (Applications->Accessories->Terminal):

u1sdtool --list-folders
u1sdtool --unsubscribe-folder=ID-FROM-COMMAND-ABOVE

The first command should return something like this:

id=c4d1e6f9-931b-45c6-8fac-830390815242 subscribed=True path=/home/jhoover/Documents

Copy the part that comes after "id=", which in the example above would be "c4d1e6f9-931b-45c6-8fac-830390815242" and put it in the next command where it says ID-FROM-COMMAND-ABOVE. That should stop synchronizing that folder for you. If it doesn't work, please let me know.

Thank you,

Joshua

---

### Post by sloze on 2010-04-30
Hi Joshua,

I just read your thread, i've a similary problem with my U1 account could you delete the files for me ?

2 files stay in "uploading" mode and i can't delete them.

Thanks a lot

> 

We currently don't delete the files right away. We're going to fix this in the not too distant future. So, for now, it can take several days for the files to actually go away. Contact Matt or I directly if you want your files completely removed and we'll make sure it gets done ASAP.

Thank you,

Joshua

---

### Post by flloyd on 2010-04-30
Hi, I tried one more time to install U1 and see if this would work. I am trying to unsync the folder Music. These were my results:

```
chris@chris-desktop:~$ u1sdtool --list-folders
Folder list:
  id=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e subscribed= path=/home/chris/Music
  id=fc4c7fa5-8796-4b96-b566-4955ab2ec71d subscribed= path=/home/chris/.ubuntuone/Purchased from Ubuntu One
chris@chris-desktop:~$ u1sdtool --unsubscribe-folder=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e

Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 307, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 354, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 123, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 763, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
chris@chris-desktop:~$ u1sdtool --list-folders
Folder list:
  id=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e subscribed= path=/home/chris/Music
  id=fc4c7fa5-8796-4b96-b566-4955ab2ec71d subscribed= path=/home/chris/.ubuntuone/Purchased from Ubuntu One
chris@chris-desktop:~$ u1sdtool --unsubscribe-folder=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e

Oops, an error ocurred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 249, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 92, in parse_reply
    *message.get_args_list()))
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 307, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 354, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/defer.py", line 371, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/bin/u1sdtool", line 123, in <lambda>
    d.addErrback(lambda r: show_error(r, out))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/tools.py", line 763, in show_error
    raise error.value
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
chris@chris-desktop:~$ 
```

---

### Post by flloyd on 2010-04-30
After trying it again here is what I am getting:

```
chris@chris-desktop:~$ u1sdtool --list-folders
Folder list:
  id=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e subscribed= path=/home/chris/Music
  id=fc4c7fa5-8796-4b96-b566-4955ab2ec71d subscribed= path=/home/chris/.ubuntuone/Purchased from Ubuntu One
chris@chris-desktop:~$ u1sdtool --unsubscribe-folder=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e
chris@chris-desktop:~$ u1sdtool --list-folders
Folder list:
  id=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e subscribed= path=/home/chris/Music
  id=fc4c7fa5-8796-4b96-b566-4955ab2ec71d subscribed= path=/home/chris/.ubuntuone/Purchased from Ubuntu One
chris@chris-desktop:~$ 
```

---

### Post by flloyd on 2010-05-05
I guess Canonical has given up?

They can't even [fix problems for or even bother to respond to paying customers]("https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/547074")?

---

### Post by joshuahoover on 2010-05-05
> **flloyd said:**
> I guess Canonical has given up?

They can't even [fix problems for or even bother to respond to paying customers]("https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/547074")?

No, not giving up, just incredibly busy trying to address these issues. My apologies for the lack of response on all the issues. I just updated the status on that bug and let everyone know what is going on. 

I'm looking into the issues reported in this particular thread and will have a response soon.

Thank you,

Joshua

---

### Post by joshuahoover on 2010-05-05
> **flloyd said:**
> After trying it again here is what I am getting:

```
chris@chris-desktop:~$ u1sdtool --list-folders
Folder list:
  id=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e subscribed= path=/home/chris/Music
  id=fc4c7fa5-8796-4b96-b566-4955ab2ec71d subscribed= path=/home/chris/.ubuntuone/Purchased from Ubuntu One
chris@chris-desktop:~$ u1sdtool --unsubscribe-folder=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e
chris@chris-desktop:~$ u1sdtool --list-folders
Folder list:
  id=a36a54ee-dbdd-4d7a-b0ed-b8effba3764e subscribed= path=/home/chris/Music
  id=fc4c7fa5-8796-4b96-b566-4955ab2ec71d subscribed= path=/home/chris/.ubuntuone/Purchased from Ubuntu One
chris@chris-desktop:~$ 
```

Phew! That took a while to sort out, but I think I have a better answer for you now. After discussing this with some of the team, I filed a bug that we're going to use to track work against getting the expected behavior implemented: [https://bugs.launchpad.net/ubuntuone-client/+bug/576080](https://bugs.launchpad.net/ubuntuone-client/+bug/576080) 

In that bug I detail a workaround that I've tested and worked for me. I'd love to hear if you get the same results. Here are those steps:

1. In a terminal session (Applications->Accessories->Terminal)  run: u1sdtool --list-folders
2. Copy the ID of the folder you want to stop synchronizing
3. In a terminal session run (replacing ID-COPIED-FROM-STEP-2):  u1sdtool -q; u1sdtool --start; u1sdtool --unsubscribe-folder=ID-COPIED-FROM-STEP-2;  u1sdtool -c
 Note, syncdaemon will do a local rescan of the folder you  unsubscribed (stopped syncing) which means it will take some time  processing this folder one last time, but will not attempt to do a sync.  After that, the folder will no longer be processed.


Thank you,


Joshua

---

### Post by flloyd on 2010-05-05
I'll move discussion to the bug report that you have opened. Your commands are still not working for me.

I've also started following the bug report for the multiple same-named songs bug as well so I guess that we can close this forum discussion.

It would be nice if U1 made it more clear of where the best place to bring up problems and complaints. I'm not a developer so using a bug tracking site doesn't seem the most natural place for an average Ubuntu user to go to.

---

