---
title: "Ubuntu One Will Not Sync Files"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by emagine on 2010-05-01
Hello everyone,

I have my ubuntu one account setup, but when I try to sync anything to ubuntu one, nothing happens.  It still says I have 0.0kb uploaded.  I am using 10.04.  Also, will ubuntu one work in the background, or must you always leave it open for it to sync files?

Thank you.

---

### Post by gdi2k on 2010-05-01
I'm having the same problem. I set Ubuntu One up on the day Lucid was released and set it to sync my "Documents" folder, which contains about 500 MB of stuff. I also tried to have it sync a test file. After about 24 hours, the files were listed in my Ubuntu One account online, but in gray with "uploading" next to them - nothing ever actually gets uploaded though, "0 Bytes Used". 

In Ubuntu One Preferences things look normal, my account is registered, my computer is listed as a connected device, and the status is "Synchronization in progress...". I've tried pressing "Restart" and "Disconnect" and "Connect" a number of times. I've also restarting the whole system a few times. I've left the machine online for the last 48 hours, but still nothing. 

In Nautilus, the files are marked with gray arrows and and exclamation mark (!). 

I've also had a play with the command line tools, but things look normal there too - no errors reported.

I've had look at some log files too, my syncdaemon.log is full of stuff like: 
```
2010-05-01 21:22:07,413 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T 8a0b1df0-de75-4eab-b498-e2d0a6f18629 ['fb807c37-ff56-4a1a-a2f4-f3116e8debc8'::'09605aa5-d37c-4663-bbb0-ad12f2afb770'] ''Documents/Manuals/x200'' | Called get_dir (In: T:NONE:T)
```

My syncdaemonexceptions.log has some stuff like this in it: 
```
2010-05-01 13:36:31,619 - ubuntuone.SyncDaemon.ActionQueue - ERROR - The request 'oauth_authenticate' failed with the error:

TRY_AGAIN

2010-05-01 13:36:35,622 - twisted - ERROR - Unhandled error in Deferred:
2010-05-01 13:36:35,623 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.storageprotocol.errors.TryAgainError: TRY_AGAIN
```

But it's not a massive amount. 

Any ideas?

---

### Post by emagine on 2010-05-01
> **gdi2k said:**
> I'm having the same problem. I set Ubuntu One up on the day Lucid was released and set it to sync my "Documents" folder, which contains about 500 MB of stuff. I also tried to have it sync a test file. After about 24 hours, the files were listed in my Ubuntu One account online, but in gray with "uploading" next to them - nothing ever actually gets uploaded though, "0 Bytes Used". 

In Ubuntu One Preferences things look normal, my account is registered, my computer is listed as a connected device, and the status is "Synchronization in progress...". I've tried pressing "Restart" and "Disconnect" and "Connect" a number of times. I've also restarting the whole system a few times. I've left the machine online for the last 48 hours, but still nothing. 

In Nautilus, the files are marked with gray arrows and and exclamation mark (!). 

I've also had a play with the command line tools, but things look normal there too - no errors reported.

I've had look at some log files too, my syncdaemon.log is full of stuff like: 
```
2010-05-01 21:22:07,413 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:T 8a0b1df0-de75-4eab-b498-e2d0a6f18629 ['fb807c37-ff56-4a1a-a2f4-f3116e8debc8'::'09605aa5-d37c-4663-bbb0-ad12f2afb770'] ''Documents/Manuals/x200'' | Called get_dir (In: T:NONE:T)
```

My syncdaemonexceptions.log has some stuff like this in it: 
```
2010-05-01 13:36:31,619 - ubuntuone.SyncDaemon.ActionQueue - ERROR - The request 'oauth_authenticate' failed with the error:

TRY_AGAIN

2010-05-01 13:36:35,622 - twisted - ERROR - Unhandled error in Deferred:
2010-05-01 13:36:35,623 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.storageprotocol.errors.TryAgainError: TRY_AGAIN
```

But it's not a massive amount. 

Any ideas?

I am not sure.  It seems like a pretty easy issue to solve.  I am sure we will figure it out.  It could even be caused by all the traffic caused by new accounts.  After all, 10.04 is the first release that truly incorporates ubuntu one.  I am sure many people made an account when they upgraded to 10.04.  We will see.

---

### Post by xxander on 2010-05-02
My files are sometimes gray'd out and look contain *, -,and the work 'lock'... i cannot seem to fix it.

---

### Post by silvari on 2010-05-02
Appears to be a known issue with the service:

"We're currently experiencing an intermittent issue that may cause the website and phone syncing to stop responding."

[http://identi.ca/notice/30584701](http://identi.ca/notice/30584701)

---

### Post by gk_manutd on 2010-05-02
I'm experiencing the same issues as gdi2k.

---

### Post by josteinaj on 2010-05-02
I think I'm having the same problem. As I've had problems before with 9.10 and 9.04 (problem syncing files), I decided to remove all other connected computers from my Ubuntu One account until I've had them all upgraded to 10.04. So now there's a bunch of files on my Ubuntu One account, and only my new 10.04 installation connected to it.

In the "Settings for Ubuntu One" window that I find by clicking my username on the panel and then "Ubuntu One..."; it says "Synchronization is being done...", and the window becomes non-responsive.

(I don't use Ubuntu in english so I don't know the exact phrasings)

Even if there were problems with the servers... the client shouldn't freeze... is this a different problem than what you guys are having?

---

### Post by spych102 on 2010-05-02
It would be such a perfect service if only it Just Worked TM.

---

### Post by GatuRatz on 2010-05-02
> **josteinaj said:**
> 

Even if there were problems with the servers... the client shouldn't freeze... is this a different problem than what you guys are having?

The problem about the freezing client can be fixed by using the new one from lucid-proposed.
But this will just prevent the freezing, the conection does not work anyway.

Br,
GatuRatz

---

### Post by emagine on 2010-05-02
I am certain we will figure it out.  If anyone figures it out, report back here!

---

### Post by josteinaj on 2010-05-02
> **GatuRatz said:**
> The problem about the freezing client can be fixed by using the new one from lucid-proposed.

Thanks. Good to know it's being looked at. I'm guessing the one in lucid-proposed will be approved pretty soon then?

---

### Post by Majorflam on 2010-05-02
I've just installed Lucid and according to Ubuntu One it is always attempting to synchronise, but never actually does! I'm assuming it's the same problem so I'll watch this thread for a fix.

---

### Post by japher on 2010-05-02
I don't think this has anything to do with load on the servers. This doesn't seem to affect Karmic, so I'm pretty sure it must be some problem with the Lucid code-base.

---

### Post by gdi2k on 2010-05-02
I've updated the packages: 
[LIST]
[*]python-ubuntuone-client
[*]ubuntuone-client
[*]ubuntuone-client-gnome
[/LIST]

to the versions from Lucid proposed updates. After a reboot, there was a brief flurry of CPU and disk activity originating from Ubuntu One, but after that little more. 

Leaving the Ubuntu One Preferences window open for a while shows "Synchronisation in progress..." most of the time, but briefly switches to "Disconnected" every few minutes. 

Interestingly some of my directories are now showing green tick / check marks in place of the gray arrows and exclamation mark, but on the website, still not a single byte has been uploaded (all the files and directories are listed, but in gray, with "uploading" next to them). 

Nothing new is showing up in the exceptions log, and the daemon log looks normal as far as I can tell.

---

### Post by DariusKu on 2010-05-03
I am affected by this too. Is there an open bug thread on Launchpad for this?

---

### Post by dulbirakan on 2010-05-03
I guess I will try the DropBox until U1 becomes stable...

---

### Post by japher on 2010-05-03
> **DariusKu said:**
> I am affected by this too. Is there an open bug thread on Launchpad for this?

There may well already be a ticket in Launchpad for this, but I couldn't find it. I've created a new one here:
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/574586](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/574586)

---

### Post by gdi2k on 2010-05-03
I've now fiddled and faffed with everything so much that nothing really works anymore. 

What is the current procedure for completely resetting Ubuntu One? 

I also need to remove all the files online, but can't as the "Documents" folder does not offer a delete option (after "More" is pressed), and a test file has status "uploading" and therefore has no options associated with it.

---

### Post by japher on 2010-05-03
> **gdi2k said:**
> What is the current procedure for completely resetting Ubuntu One?

Help with completely resetting Ubuntu One (the client anyway):
[https://answers.launchpad.net/ubuntuone-client/+faq/778](https://answers.launchpad.net/ubuntuone-client/+faq/778)

Not sure if/how you can reset your account (and sync'd files) completely.

---

### Post by kernelles on 2010-05-03
I'm having the same issue with lucid.

---

### Post by gdi2k on 2010-05-03
Thanks japher, I've now completely reset everything and added just one file to the Ubuntu One directory, as instructed in the FAQ. It still doesn't sync. However, looking in the logs, I may have found my issue:

```
2010-05-03 21:36:10,864 - ubuntuone.SyncDaemon.Main - NOTE - Local rescan finished!
2010-05-03 21:36:10,864 - ubuntuone.SyncDaemon.Main - INFO - hash queue empty. We are ready!
2010-05-03 21:37:20,098 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F cff9e6e9-8e58-4c27-a8dc-4d69eb9d2e37 ['root'::marker:cff9e6e9-8e58-4c27-a8dc-4d69eb9d2e37] ''Ubuntu One/Screenshot.png'' | Called new_local_file (In: F:NA:NA)
2010-05-03 21:37:20,105 - ubuntuone.SyncDaemon.sync - INFO - T:NONE:F cff9e6e9-8e58-4c27-a8dc-4d69eb9d2e37 ['root'::marker:cff9e6e9-8e58-4c27-a8dc-4d69eb9d2e37] ''Ubuntu One/Screenshot.png'' | Called calculate_hash (In: T:NONE:F)
2010-05-03 21:37:20,144 - ubuntuone.SyncDaemon.ActionQueue - INFO - Not enough space for upload 784760 bytes (available: None)
```

So it sounds like the client is being told by the server that I have no space remaining. After that, it just keeps on connecting, then disconnecting, like this: 
```
2010-05-03 21:38:32,100 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection started to host fs-1.one.ubuntu.com, port 443.
2010-05-03 21:38:32,343 - ubuntuone.SyncDaemon.ActionQueue - INFO - Connection made.
2010-05-03 21:38:32,344 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2010-05-03 21:38:33,127 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'protocol_version' finished OK.
2010-05-03 21:38:33,369 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2010-05-03 21:38:33,611 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request 'caps_raising_if_not_accepted' finished OK.
2010-05-03 21:39:23,616 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionDone'>: Connection was closed cleanly.
].
2010-05-03 21:39:23,619 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection was closed cleanly.
```

Can others affected by this issue check their ~/.cache/ubuntuone/log file and report if they similar things happening? 

My account has 0 bytes used, so space shouldn't be an issue!

---

### Post by japher on 2010-05-03
> **gdi2k said:**
> Can others affected by this issue check their ~/.cache/ubuntuone/log file and report if they similar things happening?

My logs show the following:
```

2010-05-03 19:46:45,512 - ubuntuone.SyncDaemon.ActionQueue - ERROR - The request 'oauth_authenticate' failed with the error:

TRY_AGAIN

2010-05-03 19:46:49,515 - twisted - ERROR - Unhandled error in Deferred:
2010-05-03 19:46:49,515 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.storageprotocol.errors.TryAgainError: TRY_AGAIN

```

So I now know I'm experiencing bug 573800:
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/573800](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/573800)

---

### Post by joshuahoover on 2010-05-03
> **japher said:**
> My logs show the following:
```

2010-05-03 19:46:45,512 - ubuntuone.SyncDaemon.ActionQueue - ERROR - The request 'oauth_authenticate' failed with the error:

TRY_AGAIN

2010-05-03 19:46:49,515 - twisted - ERROR - Unhandled error in Deferred:
2010-05-03 19:46:49,515 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.storageprotocol.errors.TryAgainError: TRY_AGAIN

```So I now know I'm experiencing bug 573800:
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/573800](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/573800)

Yes you are and we're looking into this right now. It appears to be related to load on the database side of things. We'll keep posting updates on the bug as we make further progress.

Thank you,

Joshua

---

### Post by pjones0404 on 2010-05-03
I have noticed that it will not sync the files located in the ubuntu one folder in my home directory. I am able to add files to the one website and they are sent down to the home folder but it will not sync up to the cloud. 

Should I be able to sync the firefox bookmarks that I have to the one storage as well? Is there anything in particualr that i need to do to make this work?

---

### Post by bryceowen on 2010-05-04
I've reinstalled Lucid (with an official ISO and not a pre-release this time) and am still suffering the folders-but-no-files bug.

Is there any information I can provide that would be helpful or have you collected enough?

---

### Post by serfcx on 2010-05-04
Have installed Lucid and for a while I had the folders synced but no files. Now on my laptop I have no folders or files - the folders and files are still on the cloud. This product seems to be going nowhere fast. By the way Dropbox works perfectly -  I guess I will stick to Dropbox then !](*,)

---

### Post by Jim Danner on 2010-05-04
> **japher said:**
> Help with completely resetting Ubuntu One (the client anyway):
[https://answers.launchpad.net/ubuntuone-client/+faq/778](https://answers.launchpad.net/ubuntuone-client/+faq/778)

Not sure if/how you can reset your account (and sync'd files) completely.This reset procedure may have been intended for an earlier version of Ubuntu One. After going through steps 1 through 8 (particularly, steps 7 and 8 ), my system has one new package it didn't have before:
[LIST]
[*]ubuntuone-client-tools
[/LIST]
and it has lost three packages it had before:
[LIST]
[*]libubuntuone-1.0-1
[*]python-ubuntuone
[*]rhythmbox-ubuntuone-music-store
[/LIST]I don't know if these packages are essential for Ubuntu One to function (most probably not), but it should be noted that your system is different after the procedure.

---

### Post by gdi2k on 2010-05-04
I also found that the procedure did not reset my sync'd directories as I expected it would. I don't understand where this information is stored if not within the Ubuntu One client (perhaps online)?

---

### Post by pingu1 on 2010-05-05
I have just started looking into Ubuntu One, but my problem is that the cloud that used to show up in the corner of the screen - now is lost somehow. I am also having the same problems as you guys report. Ubuntu One seems great! Hope this gets up and running soon....

Shame I did not start using it sooner...

---

### Post by pingu1 on 2010-05-05
If anybody knows why my "cloud" has disappeared, I greatly appreciate help.
If I start Ubuntu One from Programs>Internet>Ubuntu One - I just get a question wether it should always be showing in the tray or only when it is synchronizing.  I chose "Always show", and still it's not there.

Very pleased with 10.04.

---

### Post by DariusKu on 2010-05-05
I am confused now (after seeing Launchpad tickets). I don't really now by which particular bug I am affected. However, the bottom line is that it's quite not possible for many users to get there files synced. :/

---

### Post by Jim Danner on 2010-05-05
> **pingu1 said:**
> If anybody knows why my "cloud" has disappeared, I greatly appreciate help.
If I start Ubuntu One from Programs>Internet>Ubuntu One - I just get a question wether it should always be showing in the tray or only when it is synchronizing.  I chose "Always show", and still it's not there.

Very pleased with 10.04.On 10.04 I haven't ever seen that cloud icon -- even when the sync still worked (last Friday). I thought they removed it for the new version, but perhaps it's a sign of something?

---

### Post by xord on 2010-05-05
yeap, don't there's any cloud icon on tray. maybe he's upgrading from karmic perharps? I have about 1.1GB picture files on Ubuntu One and none of it on my PC. I can upload files but not downloading it.

---

### Post by pingu1 on 2010-05-05
Well - let's just be patient, and I bet they get it fixed sometime in the near future.
Toes crossed.

---

### Post by gdi2k on 2010-05-05
In Lucid there is no longer a tray icon for Ubuntu One. The client is accessed via Preferences -> Ubuntu One now.

---

### Post by bryceowen on 2010-05-05
Just wanted to mention that I checked my U1 folder this morning and SOME of the files have copied over.

I've run the update tool and see that there's a U1 update today. I'll let you know if there's any change after it installs.

---

### Post by gdi2k on 2010-05-05
Whahey, mine too, nice! Looks like all of my Documents are now sync'd. :-) 

I've still got a test file lurking online that I can't remove as it has "uploading" status, but maybe that will resolve itself with time. 

Things are looking up...

---

### Post by Majorflam on 2010-05-05
I too have had some success getting files to synch. However, I've added under 1MB of files today and they haven't synched.

This could be a good service if only it worked! I really can't see how Canonical can charge for a premium service with such unreliable software/service. I wouldn't consider upgrading until I was happy that these issues were resolved.

---

### Post by bryceowen on 2010-05-05
Alright, updated and rebooted. Can't really tell if it's actually updating or if it's frozen at this point. (It seems like there's no order to what files get updated.)

I only have about 230mb of files on U1 that need to sync and I know my internet connection isn't so bad that it will take all day, but I'll let it be and see if it finishes by tomorrow.

---

### Post by joshuahoover on 2010-05-05
We're still seeing fluctuations (both good and bad) in terms of file sync performance and apologize for the inconvenience this is causing everyone. We are focused on solving this problem and others that are impacting all of you from using the service. To get the latest updates on the status of the service and improvements we're making, please checkout the following:

[LIST]
[*][http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
[*][https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)
[/LIST]
Thank you,

Joshua

---

### Post by dulbirakan on 2010-05-07
Back to U1. I guess DBox did not posses that special ubuntu charm.

---

### Post by Karl S. on 2010-05-07
For what it's worth, it's working for me now, as of, apparently, 2 days and 21 hours ago. Excellent.

---

### Post by Pifilatakanemu on 2010-05-10
Just in case that somebody needs a working cloude storage service and can't wait until U1 handles the problems:
tThere is still [Dropbox]("https://www.dropbox.com/referrals/NTIwODg2NjM5"), which, IMHO, is a nice alternative.

It works cross plattform and offers more free space and more speed. Just to bridge until U1 works how it should.

---

### Post by RustyWyatt on 2010-05-10
Not working (never has since installation 5/9) for me also...

TCD

---

### Post by joshuahoover on 2010-05-11
> **RustyWyatt said:**
> Not working (never has since installation 5/9) for me also...

TCD

Do you have a bug report open already that I can look into? If not, can you file one following these steps so we can get some debug logs and get to the cause of the problem?

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[/LIST]
Thank you,

Joshua

---

### Post by Majorflam on 2010-05-16
Ubuntu One is still not working properly for me. In fact, I've had to disable it from the startup applications, because it is hogging all my bandwidth.

Hopefully someone will post here when this service is usable.

---

### Post by joshuahoover on 2010-05-17
> **Majorflam said:**
> Ubuntu One is still not working properly for me. In fact, I've had to disable it from the startup applications, because it is hogging all my bandwidth.

Hopefully someone will post here when this service is usable.

Sorry to hear things still aren't working properly for you. Can you tell me how many files/folders you were attempting to synchronize? Also, can you let me know if you had the bandwidth throttling settings in Ubuntu One Preferences->Devices enabled? 

Thank you,

Joshua

---

### Post by outleradam on 2010-05-23
I am having the same problem.   I've waited for a full 24 hours.  I've tried to delete everything.

1 installed fresh from CD ROM
2. attemted to connect up ubuntu one
3. while ubuntu one was doing nothing, I ran update manger
4. rebooted
5. checked on U1 again
6. waited 24 hours
7. found in logs that it is trying to synch 4 files when I have about 500  and it is not even receiving any of those 4 files.
8. deleted  ~/.cache/ubuntuone and ~/ubuntu one
9. rebooted and tried logging in many times.
10. now I'm here.

This works just fine on my adam-desktop computer and my adam-laptop flash drive installation, but it will not work on my new netbook.   It's a gateway NAV50.  Any help would be very much appreciated.  I'm on vacation and I can only access my files from the web browser.

---

### Post by outleradam on 2010-05-23
here's some more info

syncdaemon.log
```
2010-05-23 18:11:50,872 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_METADATA  connection 'With User With Network')>; queues: metadata: 4; content: 0; hash: 0, fsm-cache: hit=6 miss=1) ----
2010-05-23 18:12:00,809 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher stopped
2010-05-23 18:12:00,810 - ubuntuone.SyncDaemon.DBus - INFO - Shuttingdown DBusInterface!
2010-05-23 18:12:00,821 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionLost'>: Connection to the other side was lost in a non-clean fashion: Connection lost.
].
2010-05-23 18:12:00,823 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection to the other side was lost in a non-clean fashion: Connection lost.
```
u1prefs:
```
2010-05-23 18:02:54,473 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:03:00,108 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:03:00,974 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-05-23 18:03:01,542 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-05-23 18:03:02,722 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-05-23 18:03:52,460 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:03:52,701 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:10:07,970 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:10:08,353 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:10:49,783 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:10:52,790 - ubuntuone-preferences - ERROR - Invalid request token: vsN1zwSgVMsMVJrZznM7
2010-05-23 18:10:52,793 - ubuntuone-preferences - ERROR - Authorization was denied.
```
oauth
```
2010-05-23 18:02:57,510:510.953903198 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:10:10,400:400.512933731 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:10:52,787:787.875890732 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid request token: vsN1zwSgVMsMVJrZznM7'
2010-05-23 18:10:52,789:789.017915726 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:10:52,807:807.907104492 ubuntuone-login Invalid request token: vsN1zwSgVMsMVJrZznM7
2010-05-23 18:10:52,983:983.660936356 ubuntuone-login Access to Ubuntu One was denied.
```

Someone give me some tips.  I just got done with a complete remove and reinstallation of ubuntuone client and other things from the package manager.  If anyone has any suggestions, they would be  greatly appreciated.   

It's hard enough to use a netbook without a cd rom and a teeny tiny cramped keybard and a ill positioned trac pad which keeps loosing focus when I touch-type the space key...  I need ubuntu one to do anything on this computer.

---

### Post by outleradam on 2010-05-23
1/2 hour ago I deleted ~/.local/share/ubuntuone folder and rebooted.  It has obtained the folder structure from ubuntu one now!

It's been 1/2 hour and Ubuntu One folder now contains 18 items, 72 kb of information.  my ~/.cache/partials has 20 items totaling 0b of information.     What's going on with this?

---

### Post by outleradam on 2010-05-24
it's been 17 hours now and I have 152 items totaling 600kb.  I'm about 1/1000th of the way towards a sync.  I have only 500 megs to go.   As far as I can tell by browsing I have not received a single file.  Only the folder structures.   Why aren't my files downloading?

---

### Post by outleradam on 2010-05-25
I wouldn't say that, It worked on my desktop two weeks ago.  It's just not working on my laptop.

It's been about 48 hours now and here are the statistics.
storage: about 500 megs

~/ubuntu one/ folder: 152 items totaling 604kB
~/.cache/ubuntuone/partials/ folder: 1892 items totaling 0B
~/.cache/ubuntuone/log files:
oauth-login.log```
2010-05-23 18:02:57,510:510.953903198 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:10:10,400:400.512933731 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:10:52,787:787.875890732 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid request token: vsN1zwSgVMsMVJrZznM7'
2010-05-23 18:10:52,789:789.017915726 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:10:52,807:807.907104492 ubuntuone-login Invalid request token: vsN1zwSgVMsMVJrZznM7
2010-05-23 18:10:52,983:983.660936356 ubuntuone-login Access to Ubuntu One was denied.
2010-05-23 18:19:15,061:61.9139671326 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:20:00,785:785.077095032 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid oauth_verifier.'
2010-05-23 18:20:00,788:788.549900055 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:20:00,797:797.355890274 ubuntuone-login Invalid oauth_verifier.
2010-05-23 18:20:02,589:589.090108871 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid oauth_verifier.'
2010-05-23 18:20:02,590:590.750932693 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:20:02,598:598.350048065 ubuntuone-login Access to Ubuntu One was denied.
2010-05-23 18:20:21,017:17.9889202118 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:20:37,410:410.101890564 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid request token: KzsXqhN2d5cn7B9CmWwC'
2010-05-23 18:20:37,411:411.84592247 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:20:37,423:423.346996307 ubuntuone-login Invalid request token: KzsXqhN2d5cn7B9CmWwC
2010-05-23 18:20:37,577:577.043056488 ubuntuone-login Access to Ubuntu One was denied.
2010-05-23 18:25:04,807:807.346105576 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:25:23,680:680.40895462 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid oauth_verifier.'
2010-05-23 18:25:23,682:682.720899582 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:25:23,691:691.091060638 ubuntuone-login Invalid oauth_verifier.
2010-05-23 18:25:29,711:711.848020554 ubuntuone-login Access to Ubuntu One was denied.
2010-05-23 18:25:46,789:789.932012558 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:26:14,564:564.70990181 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid request token: pWJ1sXCskM7pDwq7fCjT'
2010-05-23 18:26:14,568:568.846940994 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:26:14,579:579.42700386 ubuntuone-login Invalid request token: pWJ1sXCskM7pDwq7fCjT
2010-05-23 18:26:14,707:707.825899124 ubuntuone-login Access to Ubuntu One was denied.
2010-05-23 18:26:40,885:885.204076767 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:31:11,786:786.045074463 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:31:56,328:328.541994095 UbuntuOne.OAuthDesktop.auth Token was not successfully retrieved: data was 'Invalid request token: VcdMfw9TXgSl57gDPgbq'
2010-05-23 18:31:56,331:331.764936447 UbuntuOne.OAuthDesktop.auth Failed to get access token.
2010-05-23 18:31:56,345:345.263957977 ubuntuone-login Invalid request token: VcdMfw9TXgSl57gDPgbq
2010-05-23 18:31:56,516:516.382932663 ubuntuone-login Access to Ubuntu One was denied.
2010-05-23 18:37:42,119:119.893074036 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 18:48:41,438:438.090085983 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-23 19:41:05,161:161.765098572 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-24 09:35:45,313:313.787937164 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-24 13:57:31,732:732.253074646 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
2010-05-24 21:16:42,062:62.8190040588 ubuntuone-login Starting Ubuntu One login manager version 1.2.1
```

syncdaemon.log
```
2010-05-25 01:04:42,367 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b9c404a6-7deb-4b5a-b11d-4d1092e235cf ['root'::'fc5ec6f0-c3e2-462b-ac76-abade0fad735'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/background1.jpg'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,567 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F bc7404f3-921d-45ef-9aee-566da32eef73 ['root'::'0566a5fd-e5d3-4174-b99e-94ff1744ad50'] ''Ubuntu One/Pictures/My Pictures/New Folder/5/6.jpg'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,750 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4e8f7e5f-19da-4cfd-8f1c-fd9ada664ae0 ['root'::'40d3893e-fcb6-45ff-a500-ad786fc9aa78'] ''Ubuntu One/Pictures/My Pictures/Export MPEG2 of 222009_193515.mpg'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,800 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4266be4b-dd33-4cb1-a62e-809a147178f5 ['root'::'4d894898-5385-4d05-ab94-5ea08cbe9832'] ''Ubuntu One/Pictures/My Pictures/car show/100_3193.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,846 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b3af9f21-f99a-4aff-ae46-93cd3084ad76 ['root'::'e9ac9b68-c48e-4854-b664-8d388cefdf5d'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F46/T246.ithmb'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,896 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 838cc6f7-f327-4b4d-8676-23c49cce1868 ['root'::'00c1a925-f611-4dbf-80fe-6fc2bfaca10c'] ''Ubuntu One/Pictures/My Pictures/New Folder/darkness/New Folder/Thumbs.db'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,941 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8476ec9c-6e4c-4a54-8984-ed1615ba8525 ['root'::'9e4a2436-a4bc-400f-999c-b6dfb3e34dd3'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/1.jpg'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:42,991 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4127d8eb-68c9-449c-baf3-575ede85394b ['root'::'66fa0ca4-3cee-4045-a75e-10e4b054b97d'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/OSX/hdhomerun_config_gui.xcodeproj/.svn/entries'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:43,037 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4d6b0ee3-96c2-4d8c-90ec-c64a23ac5687 ['root'::'95920fe6-d3e6-46e3-b6e2-9b56ef8e91d3'] ''Ubuntu One/Current Projects/hdhr/STREAMS/23.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:43,197 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4baf528f-7db5-4302-bbcb-e046cd249dce ['root'::'348fb22a-2084-4597-b49e-c19b4bcc7e90'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/hdhomerun_config.glade'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,159 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 89310f8b-a316-4b03-b8e5-c72fba6a02a8 ['root'::'b192a01c-8519-4a9f-b318-daf40b07097a'] ''Ubuntu One/Current Projects/hdhr/19.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,210 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8a008ac2-6785-410c-bf51-26a2f6955e29 ['root'::'f8ab1665-8e65-453c-9e4a-a3450d8a37cd'] ''Ubuntu One/Current Projects/hdhr/916music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,255 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F bd7d67f3-5676-4099-8857-8acbcbcb814f ['root'::'efc2da10-30b1-436a-860f-e9353051f481'] ''Ubuntu One/Current Projects/hdhr/939music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,307 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 77c16da4-cc95-460c-9a8c-e41c47f628b5 ['root'::'804a8e4d-253b-4917-9e3a-e630bba3a852'] ''Ubuntu One/Current Projects/hdhr/919music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,354 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 7ba0691f-d492-4198-adbe-26f87a21149d ['root'::'9eb91e6f-ac97-43e1-a663-ba17e4f7d833'] ''Ubuntu One/Current Projects/hdhr/STREAMS/21.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,404 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4364da76-8c86-4a0b-8b2a-5abaa06698a2 ['root'::'97f10ae5-d46b-4f3e-8965-429063a808ac'] ''Ubuntu One/Current Projects/hdhr/STREAMS/902music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,529 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b927c85a-1163-4bb3-949f-e7ecdd636ce6 ['root'::'cff5f283-4c5e-4761-8cc1-b72fcb7967e6'] ''Ubuntu One/Current Projects/hdhr/STREAMS/931music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:44,578 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 7831fe78-e921-44d2-b04b-fda4a4e454e0 ['root'::'83ae8458-c3aa-4ba9-a797-e923a2a82c6b'] ''Ubuntu One/Current Projects/SVN/Distribution Adam/BTVRename/BeyondTVLibrary.dll'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,165 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 749a8498-725a-4bc8-820c-f9ef2e902cec ['root'::'053bcfb2-b826-48cb-8933-af24e2c349c7'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/WIN/hdhomerun_config_gui.rc'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,237 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 81383cf0-5609-4f99-88f7-370b01bd7f74 ['root'::'a6e176de-f121-4363-a447-addf24136d5e'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/aclocal.m4'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,481 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8be1f595-b29f-4175-acc9-a6c876b3b4c9 ['root'::'9905589d-103d-43cf-aed2-0de3293af8c4'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/po/Makefile.in.in'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,560 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4a031e98-e915-4782-8d69-2ea6f3220ea4 ['root'::'6121b4c5-7e40-47f9-a5b0-59681db746e9'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/OSX/English.lproj/.svn/prop-base/._InfoPlist.strings.svn-base'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,611 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4f5db376-5d78-4de9-9ffa-8b78d2b01849 ['root'::'eb013515-5a3a-43fc-ac62-7dc1fcafc60b'] ''Ubuntu One/Current Projects/hdhr/STREAMS/918music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,656 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 84c91e1b-da10-49d1-979b-a3ff1bb49d18 ['root'::'54352237-7495-4222-9506-0eaf4db2615f'] ''Ubuntu One/Current Projects/hdhr/STREAMS/908music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,709 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8382d615-3c0a-4f0f-a224-8a88c1101e17 ['root'::'7a83e93a-7907-4355-b4a3-5c9e87826da1'] ''Ubuntu One/Current Projects/hdhr/STREAMS/921music.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,884 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 7c0c8fb1-1692-49e8-983d-d8458f30b613 ['root'::'18504665-0ec9-4902-a391-cbf771c4ec96'] ''Ubuntu One/Pictures/My Pictures/222009_193515.mtv'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,931 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 7dab084f-b946-444b-be0d-bacd3b85e8a8 ['root'::'cb2d6b4e-f2e9-4540-a1be-9ceff47b0878'] ''Ubuntu One/Pictures/My Pictures/turbosocks.psd'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:45,997 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 77b51fc7-f004-4bc4-b902-f0f38420d3d8 ['root'::'cfa8bd95-799a-400b-b402-491f58863174'] ''Ubuntu One/Pictures/My Pictures/car show/100_3152.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,044 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8e208435-19dd-4832-9018-1775d727f318 ['root'::'8e2cf694-b0fb-4274-adb5-9cc0f12ed8d4'] ''Ubuntu One/Pictures/My Pictures/car show/100_3176.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,096 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 881408e5-9358-4980-94eb-cf0c30011971 ['root'::'855ab331-fdb6-4489-abd1-51cb9c24a74c'] ''Ubuntu One/Pictures/My Pictures/Sample Pictures.lnk'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,143 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 844e4de9-330e-48b1-870e-554cb8ccd7cd ['root'::'1029353f-b3ea-4735-b139-b1e12ae38f7e'] ''Ubuntu One/Pictures/My Pictures/car show/100_3190.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,194 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8d0b3114-ff32-4495-9275-772eecdc58b6 ['root'::'7a2e1dfe-4be0-4ce4-b114-aa60a335a221'] ''Ubuntu One/Pictures/My Pictures/car show/100_3137.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,241 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F bf042701-760a-4ce6-8af7-5bda5d4f9c33 ['root'::'685dc07f-c885-41e2-b198-66dff665466b'] ''Ubuntu One/Pictures/My Pictures/car show/100_3166.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,293 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b0d4b0f4-5c77-4755-ba9f-c7103ac32b2c ['root'::'c1a5b1fb-33b9-4e0f-8db3-370ea233c887'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F17/T268.ithmb'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,340 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 42c70a5c-f8b4-4b7a-834c-8639d0ec5f29 ['root'::'508083c9-5525-4435-be4f-2453193dd6b8'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F08/T106.ithmb'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,460 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 87ebdd39-7bfd-47b6-8cf6-900d119c90fe ['root'::'4d370891-c8c5-4a4f-bf61-ac9241e46270'] ''Ubuntu One/Pictures/My Pictures/New Folder/5/2.jpg'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,561 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F bcf70a98-c3fd-476d-b4b1-a9e447129460 ['root'::'e64cc0fc-32d6-4651-b573-d577817fdd5d'] ''Ubuntu One/1apr/mythicalLibrarian SVN/librarian-notify-send'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,620 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 41054126-8d27-4776-bbfb-efd49d9e6d11 ['root'::'5f602a42-097c-443d-9867-5ce06b012af5'] ''Ubuntu One/Pictures/My Pictures/car show/100_3223.JPG'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,724 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b25a7033-9e3e-47b8-bbe8-081957e7849c ['root'::'620c3350-e124-409f-98c3-79f138327b87'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/OSX/hdhomerun_config_gui.xcodeproj/project.pbxproj'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:46,961 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 41b48f35-f9ea-4292-8daa-a245b555bdf0 ['root'::'63321483-4e90-44a6-ae97-4de55c071238'] ''Ubuntu One/icons/iomega.png'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:47,015 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F be9743a6-7849-4941-bf20-2ebfe84ccca6 ['root'::'75f1961e-764f-42ef-aad0-871475c38981'] ''Ubuntu One/Current Projects/hdhr/STREAMS/46.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:47,062 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b618b8f0-c8f9-408d-9e6e-3fa6eb763374 ['root'::'ccf393a8-9943-4d32-83d8-e3f00a87c4f0'] ''Ubuntu One/Current Projects/hdhr/1.strm'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:47,288 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 85f99043-d61e-41ff-97b7-5c1f646ffe04 ['root'::'3147b960-e9ac-45d6-80b4-42280ca6d3c9'] ''Ubuntu One/Current Projects/copy to XBMC/home/xbmc/hdhr/hdhomerun_config_gui/Makefile.am'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:47,653 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 78bbe42b-ab48-46d3-aedc-6d491b4db013 ['root'::'d1e32320-ad89-4d9c-9d63-58c0b7bb2de8'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F43/T294.ithmb'' | Called get_file (In: T:NONE:F)
2010-05-25 01:04:47,658 - ubuntuone.SyncDaemon.ActionQueue - INFO - The request '_get_root_and_query' finished OK.
2010-05-25 01:06:23,785 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F ae16059e-996f-4af3-ad72-fd84343c02cf ['root'::'3f78c692-329b-4fdf-ae3c-483f0a22db32'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/4.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 580; content: 1900; hash: 0, fsm-cache: hit=166307 miss=5095) ----
2010-05-25 01:06:53,889 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 15a78399-c2a1-4067-a873-aec617728a9c ['root'::'35ad1c3e-4d79-4112-89ad-cefa65c98167'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/5.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:07:47,798 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 31a0c3c8-2a17-41d9-81dd-1b936f4cc145 ['root'::'f1c3d14f-aadf-4d65-9a3d-2713cccd06aa'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/6.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:08:15,653 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F e14a2fc1-72d0-4956-a112-9176bdfd2b73 ['root'::'53d48bd4-9e0d-40d4-8fe2-4671c24aaae7'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/7.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 577; content: 1900; hash: 0, fsm-cache: hit=166427 miss=5095) ----
2010-05-25 01:09:46,817 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 7eb62978-dcf7-4cad-9b11-d31de944fe9f ['root'::'6a539e46-0b33-4c54-8b7c-dceaa2c3c01b'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/a.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:10:37,280 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F b9c404a6-7deb-4b5a-b11d-4d1092e235cf ['root'::'fc5ec6f0-c3e2-462b-ac76-abade0fad735'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/background1.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 575; content: 1900; hash: 0, fsm-cache: hit=166507 miss=5095) ----
2010-05-25 01:11:13,950 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 302ae196-d74a-4a8b-a437-96f4462370ee ['root'::'afae797f-cab0-4662-86f5-a191379380fa'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/b.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:12:22,975 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 6df1bc29-eeea-4296-9a8e-6ca67ca104f5 ['root'::'e201aeb6-ede2-4e6b-8481-a8cb9964b608'] ''Ubuntu One/Pictures/My Pictures/New Folder/1/Thumbs.db'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 573; content: 1900; hash: 0, fsm-cache: hit=166587 miss=5095) ----
2010-05-25 01:14:08,275 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 3bfa934d-28e6-4cee-87b2-836fa6092149 ['root'::'865998d6-0a56-4a10-9153-26d0733b1048'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F03/T152.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:14:31,467 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F c88cf8e2-bab6-4a42-8f3f-498fb408806e ['root'::'e051570a-ec55-42e9-956e-71accd439bfe'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F03/T203.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 571; content: 1900; hash: 0, fsm-cache: hit=166667 miss=5095) ----
2010-05-25 01:15:38,612 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F f025634e-3a0d-4bd6-84ae-35bdf3a27107 ['root'::'95080aa6-3254-4b58-a699-07c692b6268f'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F03/T254.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 570; content: 1900; hash: 0, fsm-cache: hit=166707 miss=5095) ----
2010-05-25 01:16:53,639 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4bcce394-b365-459d-a101-8e8fa5fb0cea ['root'::'07579b79-2af3-473e-8f0c-333402f19049'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F03/T305.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:17:44,586 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F e7447609-ee99-49f7-a0fb-7d55315fcc74 ['root'::'5829730d-2062-468d-8c01-c6fb6d5d9ab7'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F42/T140.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 568; content: 1900; hash: 0, fsm-cache: hit=166787 miss=5095) ----
2010-05-25 01:18:51,884 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 00bf1054-543d-46ed-87e9-0c8615edc3ce ['root'::'c680aca8-d72f-4659-8907-93da9d799d29'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F42/T191.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:20:17,417 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F ebc10647-5c0b-4829-911d-d483deaa4db1 ['root'::'8ef0a6c6-34c7-4eab-a75e-8fbcffb46619'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F42/T242.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 566; content: 1900; hash: 0, fsm-cache: hit=166867 miss=5095) ----
2010-05-25 01:20:56,419 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F da9ec4d4-b696-454a-8816-5ff053ed3bf1 ['root'::'c1b5e0e9-523f-4c3d-bda8-fdce21425adb'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F42/T293.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:21:17,506 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 5ef004e0-cd1f-428a-bb71-c55dd3a0a8c3 ['root'::'904df77f-937e-4b7b-8e97-b6ba33c69053'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F22/T120.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:22:07,334 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 91de091d-040e-4ff5-ad51-a42271962953 ['root'::'88004ed4-0ff0-44e6-8f1c-0d8975cd6a16'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F22/T171.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:22:14,705 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 2625778e-857b-4e36-baac-2258aad1eb8a ['root'::'82513517-adae-4fc6-a3ee-2c64b467ad6e'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F22/T222.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 562; content: 1900; hash: 0, fsm-cache: hit=167027 miss=5095) ----
2010-05-25 01:23:32,280 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 081f5c53-1c7f-4b94-8d2c-04b383ffa08d ['root'::'dbf28cda-7815-4cb5-b6ea-037db78974ce'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F22/T273.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:24:07,946 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 893a5d8a-6390-4734-8a01-b0232c0090ba ['root'::'62d69706-440e-41b1-be7b-25f1aaee7fdb'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F22/T324.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 560; content: 1900; hash: 0, fsm-cache: hit=167107 miss=5095) ----
2010-05-25 01:25:21,968 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F c31ebee1-7546-4c3e-8088-3c2b5d40c6ea ['root'::'26654076-0656-4d1f-a53a-2fa27a116ec5'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F43/T141.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:25:43,063 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 0b90956a-7d64-4092-a8bf-a787f8e7c1d9 ['root'::'7d9d3ec4-46d1-4446-b412-334defa6d5f5'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F43/T192.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 558; content: 1900; hash: 0, fsm-cache: hit=167187 miss=5095) ----
2010-05-25 01:27:01,131 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 0509744d-ac9f-4d53-9d97-b566c999c382 ['root'::'b57b774f-b0b9-470a-980d-1d4b4b8e64e3'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F43/T243.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:27:20,021 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 78bbe42b-ab48-46d3-aedc-6d491b4db013 ['root'::'d1e32320-ad89-4d9c-9d63-58c0b7bb2de8'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F43/T294.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:28:13,402 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F a15e7ca5-be95-448f-95f6-74e50e2651b0 ['root'::'ad93e732-7b70-40f0-b08d-241f7363529e'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F25/T123.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:28:21,439 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8857b079-62ff-41c0-8da5-57fa7d6e40bc ['root'::'0a50e3a0-6f2e-4b34-a5ac-1def788cbea8'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F25/T174.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 554; content: 1900; hash: 0, fsm-cache: hit=167347 miss=5095) ----
2010-05-25 01:29:46,615 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 04ae0ca6-4e84-4ca0-8921-c248cd0984e4 ['root'::'5b968c8b-f51e-491a-8a48-cd586c680e11'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F25/T225.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:30:26,366 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 06874e92-ec35-44bb-8cac-7548be39159d ['root'::'e3785391-bd89-49c7-88cd-a0fbed31d72f'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F25/T276.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 552; content: 1900; hash: 0, fsm-cache: hit=167427 miss=5095) ----
2010-05-25 01:31:49,510 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 39b76658-ef7e-4277-98ca-029536e42309 ['root'::'f90d04f4-3cfa-4079-801d-4c8884fe83a5'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F25/T327.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:32:27,056 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F c95da306-bb17-4643-9438-9801fe03ac40 ['root'::'0053176a-a496-495c-94ee-125468a6df4b'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F36/T134.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 550; content: 1900; hash: 0, fsm-cache: hit=167507 miss=5095) ----
2010-05-25 01:33:45,008 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 40c85f34-fc27-4e91-9822-41f6664d7ad9 ['root'::'cdf3738a-ec91-41be-b2ad-420210cb884e'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F36/T185.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:34:22,819 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F a77fd4d6-7fb1-46e7-a4e2-96b19721a94d ['root'::'ebcea426-f997-4292-9249-35d673e4fca9'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F36/T236.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 548; content: 1900; hash: 0, fsm-cache: hit=167587 miss=5095) ----
2010-05-25 01:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 548; content: 1900; hash: 0, fsm-cache: hit=167587 miss=5095) ----
2010-05-25 01:37:14,922 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F dee79b17-8ba7-49f7-8896-dec126d5a24e ['root'::'2626c8d7-fe3c-4d3b-8248-36bfb32dead8'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F36/T287.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:37:31,989 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F c1f23125-0f44-40fc-8343-5d66e6b83fc4 ['root'::'e0df36d7-2e17-4ca8-84a8-17cf8296fc3a'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F37/T135.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 546; content: 1900; hash: 0, fsm-cache: hit=167667 miss=5095) ----
2010-05-25 01:40:03,955 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 01051ff1-17b9-4487-82fd-53306807439a ['root'::'d5aebbe1-7b2b-441c-b8c8-cae431a6c869'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F37/T186.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:40:37,870 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F bd440e21-a116-413d-b3ae-1d1b70e1ede0 ['root'::'5d005d0f-8000-4f63-b970-0014bb8cdb34'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F37/T237.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 544; content: 1900; hash: 0, fsm-cache: hit=167747 miss=5095) ----
2010-05-25 01:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 544; content: 1900; hash: 0, fsm-cache: hit=167747 miss=5095) ----
2010-05-25 01:43:32,494 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 5ab65c17-bd30-40e2-bb16-8b44c863bc0a ['root'::'a5702f7c-1f44-4b54-a24f-bbe6e7de1796'] ''Ubuntu One/Pictures/My Pictures/iPod Photo Cache/F37/T288.ithmb'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 543; content: 1900; hash: 0, fsm-cache: hit=167787 miss=5095) ----
2010-05-25 01:45:07,018 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 8476ec9c-6e4c-4a54-8984-ed1615ba8525 ['root'::'9e4a2436-a4bc-400f-999c-b6dfb3e34dd3'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/1.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:46:03,952 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 63c803f2-2c10-435a-8524-59a084e80cac ['root'::'669753ba-28d3-4f11-acfb-18db79f3cfb3'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/2.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 541; content: 1900; hash: 0, fsm-cache: hit=167867 miss=5095) ----
2010-05-25 01:46:46,818 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F c746945e-5cd6-42fa-a06f-f6d55e850b66 ['root'::'b1649c9d-fe78-4ec2-8b8c-2181ebc2220c'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/3.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:48:03,158 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 4390c0fb-870f-456c-912d-c0fc302adabf ['root'::'8b70abee-fe10-41cf-ac4a-e3772eb8668c'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/6.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 539; content: 1900; hash: 0, fsm-cache: hit=167947 miss=5095) ----
2010-05-25 01:49:11,636 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F fa4aac6d-f5ae-481a-9bb8-285c8aa16ee5 ['root'::'937efcc8-6ae3-4584-ae89-c1cf1240aca5'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/7.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 538; content: 1900; hash: 0, fsm-cache: hit=167987 miss=5095) ----
2010-05-25 01:51:33,725 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 2faf13de-b431-4048-a210-79905ff600ec ['root'::'6a3a6206-6602-48cd-b083-a1c4ac6df449'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/7.psd'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 537; content: 1900; hash: 0, fsm-cache: hit=168027 miss=5095) ----
2010-05-25 01:53:05,691 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F f5ef297a-b887-416f-a7d4-9702ea0b6b8d ['root'::'564da052-60b9-47cf-85fe-56abcd4f31d3'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/A.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:54:27,406 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F ab7a4830-8d6a-45a5-a1c8-660dddc73a53 ['root'::'fb7c9709-22a2-4319-8ecd-ce11d5e5ab11'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/background4.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 535; content: 1900; hash: 0, fsm-cache: hit=168107 miss=5095) ----
2010-05-25 01:55:38,136 - ubuntuone.SyncDaemon.sync - INFO - T:SERVER:F 5360a3f9-1991-445c-b9fe-2f57e62271c4 ['root'::'43081241-d86f-4649-9880-e722fe77042b'] ''Ubuntu One/Pictures/My Pictures/New Folder/4/B.jpg'' | Called nothing (In: T:SERVER:F)
2010-05-25 01:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 01:58:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 02:58:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 03:58:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 04:58:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 05:58:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 06:58:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:52:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:54:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:56:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 07:58:40,812 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:00:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:02:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:04:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:06:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:08:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:10:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:12:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:14:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:16:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:18:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:20:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:22:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:24:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:26:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:28:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:30:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:32:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:34:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:36:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:38:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:40:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:42:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:44:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:46:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:48:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:50:40,808 - ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'QUEUE_MANAGER'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 534; content: 1900; hash: 0, fsm-cache: hit=168147 miss=5095) ----
2010-05-25 08:51:06,655 - ubuntuone.SyncDaemon.HQ - INFO - HashQueue: _hasher stopped
2010-05-25 08:51:06,656 - ubuntuone.SyncDaemon.DBus - INFO - Shuttingdown DBusInterface!
2010-05-25 08:51:06,670 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionLost'>: Connection to the other side was lost in a non-clean fashion: Connection lost.
].
2010-05-25 08:51:06,672 - ubuntuone.SyncDaemon.ActionQueue - WARNING - Connection lost: Connection to the other side was lost in a non-clean fashion: Connection lost.
```

u1-prefs.log
```
2010-05-23 18:02:54,473 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:03:00,108 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:03:00,974 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-05-23 18:03:01,542 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-05-23 18:03:02,722 - ubuntuone-preferences - ERROR - Database enablement is unavailable.
2010-05-23 18:03:52,460 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:03:52,701 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:10:07,970 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:10:08,353 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:10:49,783 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:10:52,790 - ubuntuone-preferences - ERROR - Invalid request token: vsN1zwSgVMsMVJrZznM7
2010-05-23 18:10:52,793 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:19:49,727 - ubuntuone-preferences - ERROR - BAD REQUEST
2010-05-23 18:19:50,042 - ubuntuone-preferences - ERROR - BAD REQUEST
2010-05-23 18:19:50,112 - ubuntuone-preferences - ERROR - BAD REQUEST
2010-05-23 18:19:50,490 - ubuntuone-preferences - ERROR - BAD REQUEST
2010-05-23 18:19:50,517 - ubuntuone-preferences - ERROR - Got empty result for devices list.
2010-05-23 18:19:51,073 - ubuntuone-preferences - ERROR - BAD REQUEST
2010-05-23 18:20:00,787 - ubuntuone-preferences - ERROR - Invalid oauth_verifier.
2010-05-23 18:20:00,791 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:20:02,592 - ubuntuone-preferences - ERROR - Invalid oauth_verifier.
2010-05-23 18:20:02,597 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:20:34,492 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:20:37,413 - ubuntuone-preferences - ERROR - Invalid request token: KzsXqhN2d5cn7B9CmWwC
2010-05-23 18:20:37,417 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:25:02,872 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:25:03,047 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:25:06,513 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:25:11,914 - ubuntuone-preferences - ERROR - Got empty result for devices list.
2010-05-23 18:25:23,682 - ubuntuone-preferences - ERROR - Invalid oauth_verifier.
2010-05-23 18:25:23,685 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:25:30,060 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:25:44,556 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:25:44,723 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:25:48,483 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:25:58,041 - ubuntuone-preferences - ERROR - Got empty result for devices list.
2010-05-23 18:26:12,852 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:26:14,568 - ubuntuone-preferences - ERROR - Invalid request token: pWJ1sXCskM7pDwq7fCjT
2010-05-23 18:26:14,572 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:26:38,292 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:26:38,504 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:26:42,363 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:27:56,410 - ubuntuone-preferences - ERROR - Got empty result for devices list.
2010-05-23 18:29:15,570 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
]
2010-05-23 18:29:26,641 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
]
2010-05-23 18:31:09,060 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:31:56,331 - ubuntuone-preferences - ERROR - Invalid request token: VcdMfw9TXgSl57gDPgbq
2010-05-23 18:31:56,357 - ubuntuone-preferences - ERROR - Authorization was denied.
2010-05-23 18:32:18,062 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
]
2010-05-23 18:33:14,168 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:37:39,804 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:37:39,969 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:37:43,749 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:46:31,056 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:46:31,232 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:46:33,640 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 18:48:37,949 - ubuntuone-preferences - DEBUG - starting
2010-05-23 18:48:38,349 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 18:48:44,022 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 19:41:02,767 - ubuntuone-preferences - DEBUG - starting
2010-05-23 19:41:03,029 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 19:41:06,670 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 19:46:01,460 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 19:53:51,573 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 19:58:48,281 - ubuntuone-preferences - DEBUG - starting
2010-05-23 19:58:48,557 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 19:58:50,832 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 22:05:19,774 - ubuntuone-preferences - DEBUG - starting
2010-05-23 22:05:19,970 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 22:05:22,852 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-23 23:55:36,843 - ubuntuone-preferences - DEBUG - starting
2010-05-23 23:55:37,126 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-23 23:55:40,319 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-24 09:35:41,478 - ubuntuone-preferences - DEBUG - starting
2010-05-24 09:35:42,054 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-24 09:35:48,563 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-24 13:57:28,902 - ubuntuone-preferences - DEBUG - starting
2010-05-24 13:57:29,315 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-24 13:57:34,472 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
2010-05-24 21:16:39,645 - ubuntuone-preferences - DEBUG - starting
2010-05-24 21:16:40,070 - ubuntuone-preferences - DEBUG - got limits: dbus.Dictionary({dbus.String(u'download'): dbus.Int32(2097152), dbus.String(u'upload'): dbus.Int32(2097152)}, signature=dbus.Signature('si'))
2010-05-24 21:16:44,626 - ubuntuone-preferences - ERROR - [Failure instance: Traceback (failure with no frames): <class 'dbus.exceptions.DBusException'>: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1307, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/filesystem_manager.py", line 549, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/adam/.ubuntuone/Purchased from Ubuntu One'

]
```




If someone can provide me with some tips, it would be great!   I know ubutu one works.  It's not working on THIS computer though.

In case it's a problem with my computer:
login:outleradam@hotmail.com
working computer:adam-desktop
this computer: adam-laptop

---

### Post by vevel on 2010-05-26
Unfortunately, I'm in a very similar situation.  Ubuntu One works on all but the newest one.   I've got a bug open on launchpad, so I'll let you know if I get a solution.

---

### Post by outleradam on 2010-05-30
I have a bug opened here [https://bugs.launchpad.net/ubuntu/+source/ubuntuone-storage-protocol/+bug/585639](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-storage-protocol/+bug/585639)

I also have a question opened here: [https://answers.launchpad.net/ubuntu/+question/112223](https://answers.launchpad.net/ubuntu/+question/112223)

Please add yourself as affected

---

### Post by gerowen on 2010-05-30
Just did a re-install of 10.04 after a disastrous experience with Windows 7.  I purchased some music from the Ubuntu One music store before when I had 10.04 installed and now when I visit the website it appears to be there, however my syncing is stuck at 45% and none of my cloud music is coming over to my client machine.  I've removed all the old copies of my computer from Ubuntu One so the only client configured for access is this one.  I'd really like to get my Jimi Hendrix back, I miss that guitar, :-)

---

### Post by gerowen on 2010-05-30
It seems to be going, just very slowly.  The only thing I have in Cloud Storage is my music (922 MB worth according to the client), and I think I've managed to download a dozen or so songs so far.

---

### Post by vevel on 2010-05-31
> **marcusdean.adams said:**
> Just did a re-install of 10.04 after a disastrous experience with Windows 7.  I purchased some music from the Ubuntu One music store before when I had 10.04 installed and now when I visit the website it appears to be there, however my syncing is stuck at 45% and none of my cloud music is coming over to my client machine.  I've removed all the old copies of my computer from Ubuntu One so the only client configured for access is this one.  I'd really like to get my Jimi Hendrix back, I miss that guitar, :-)

You should be able to download the music directly from the one.ubuntu.com page, regardless of your local sync state.  Also, I believe the music will go into your home directory in the .local folder by default:
"~/.local/share/ubuntuone/Purchased from Ubuntu One" 
So you can check that part separately from the 'Ubuntu One' directory to see if it is syncing more quickly.  Don't know if it will, but maybe worth a look.

---

### Post by dannyboy79 on 2011-11-06
i can't even figure out how to add my 10.04 computer to my ubuntuone account. It just will NOT make a webpage pop up which then has a button for allowing access to this computer or what have you. I have tried all the tutorials and FAQs out there. no matter what, it just will not allow me to add my 10.04 computer to ubuntuone. Please help.

---

