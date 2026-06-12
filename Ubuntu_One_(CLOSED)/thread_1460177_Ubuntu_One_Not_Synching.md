---
title: "Ubuntu One Not Synching?"
date: 2010-04-22
forum: Ubuntu One (CLOSED)
---

### Post by jaco223 on 2010-04-22
I have a question. When Ubuntu One is synched, should I see those files in my
Ubuntu One folder on my computer? It seems before my last reinstall of Lucid, when
Ubuntu One was synched my files appeared in my Ubuntu One folder.  After installing
Ubuntu Lucid from a daily build Apr.19th, Ubuntu One say's it's synched, but no files
appear in my folder. 

Thanks.

Jaco

---

### Post by joshuahoover on 2010-04-22
> **jaco223 said:**
> I have a question. When Ubuntu One is synched, should I see those files in my
Ubuntu One folder on my computer? It seems before my last reinstall of Lucid, when
Ubuntu One was synched my files appeared in my Ubuntu One folder.  After installing
Ubuntu Lucid from a daily build Apr.19th, Ubuntu One say's it's synched, but no files
appear in my folder. 

Thanks.

Jaco

Hi Jaco,

Yes, you should see the files synchronized to your ~/Ubuntu One folder. This assumes that Ubuntu One is connected and has had time to synchronize files. You can check the status of the connection by running the following via a terminal session: u1sdtool -s

Thank you,

Joshua

---

### Post by jaco223 on 2010-04-22
> **joshuahoover said:**
> Hi Jaco,

Yes, you should see the files synchronized to your ~/Ubuntu One folder. This assumes that Ubuntu One is connected and has had time to synchronize files. You can check the status of the connection by running the following via a terminal session: u1sdtool -s

Thank you,

Joshua

Joshua, thanks for the quick reply. I've restarted the Ubuntu One client and will
leave it running to see if the files show up in ~/Ubuntu one.
Earlier today it said synchronization complete, but there were no files in the folder.

Jaco

---

### Post by Cix6 on 2010-04-22
I Have the same Problem...

Synchronize complete, but no Files in my Ubuntu One Folder!

Cix6

---

### Post by jaco223 on 2010-04-22
> **Cix6 said:**
> I Have the same Problem...

Synchronize complete, but no Files in my Ubuntu One Folder!

Cix6


Joshua,

I'm letting the client run minimized in the tray, and when I run

```
u1sdtool -s
```
I'm getting:

jaco@ubuntu:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Am assuming *processing queues* means it's synching, whereas my client
again say's synchronization complete.

Jaco

---

### Post by joshuahoover on 2010-04-23
> **jaco223 said:**
> Joshua,

I'm letting the client run minimized in the tray, and when I run

```
u1sdtool -s
```I'm getting:

jaco@ubuntu:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

Am assuming *processing queues* means it's synching, whereas my client
again say's synchronization complete.

Jaco

Hi Jaco,

Based on that output from u1sdtool -s it does look like the preferences app is not reporting accurately. Assuming you have the latest updates, can you file a bug and include this information there? [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

Thank you,

Joshua

---

### Post by jaco223 on 2010-04-23
Joshua,

Thanks for the reply. Yes, I will file a bug report. It's just not synching for me even
though I have the latest updates as of today 5pm Eastcoast time.

Jaco

---

### Post by cyberplasma on 2010-04-26
I have the same problem with Ubuntu One. I created one free account and installed it on 2 laptops running Ubuntu 9.10. It connects without any error message but when I put files in the Ubuntu One folder on one computer it tells me it's updating, but I don't see any files appearing on the other laptop - and vice versa. Files I uploaded using the web interface also don't appear on neither of my pc's

The command u1sdtool does exist on my system, but it doesn't support the -s parameter (no such option) so I suppose I'm using an older version. I went on and turned on the pre-release updates (karmic-proposed) and I get about 50 new updates available for installation, but none of them is an update for Ubuntu one.

Kind of stuck here - does anyone have a solution so I can just make it work like it's supposed to?

---

### Post by duanedesign on 2010-04-26
If you are using an older version of Ubuntu One that does not have the -s option for u1sdtool you can get the same, albeit more verbose, information with.

```
dbus-send --session --print-reply  --dest=com.ubuntuone.SyncDaemon --type=method_call /status com.ubuntuone.SyncDaemon.Status.current_status
```

Also you might want to see if anything is in the following file.

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

---

### Post by adeypoop on 2010-05-02
Hi I'm getting similar problems. When I was running Karmic everything in my Ubuntu One folder was synching correctly. Since I upgraded to Lucid I'm finding that my Ubuntu One folder looks like it is not synchronised and the folder remains empty. (I can see the files in the web app so I know they are still there on the cloud) 

When i attempt to synch. Ubuntu One preferences say Synchronisation in progress for about 10 or 15 minutes, then it says synchronisation complete and disconnects. However the Ubuntu One folder still contains nothing. The emblem on the icon looks like a 'greyed out' exclamation mark.


u1sdtool -s reports a variety of messages to do with processing queues and working on metadata


Aside from the fact synchronising my Ubuntu One folder is not working, I'm a  bit disappointed I have to manually go in and start the connection. I hope these things get sorted out because it is a nice idea and a feature I would like to use.

---

### Post by pomprint on 2010-05-02
I have just upgraded my Ubuntu Studio to Lucid and I am having the same problem. Nothing at all appears to be working with Ubuntu One. 

If I use Ubuntu One Preferences, it does not show my name, email address or plan, and I can't connect as I get the same 10 minute message about synchronization in progress and then get disconnected. I can, however, use the 'Manage my account' button, which DOES know who I am, and my email address.

If I move a file into the Ubuntu One folder it shows synchronization (the two arrows), but tells me (after 3 hours) on the website that it is uploading.

Furthermore, I downloaded Rhythmbox (not standard on Studio), and don't see the Ubuntu Music Store.

I hope that this gets sorted out soon as I think that I will be using the store in place of iTunes and Napster.

---

### Post by doko1 on 2010-05-02
i have exactly the same problem here like pomprint...

---

### Post by nejode on 2010-05-02
Same here... not synching... Lucid fresh install + updates.  On for hours and no files in the ~Ubuntu One folder.  Verified that all files are available in the cloud and sync correctly on 2 Karmic laptops.

---

### Post by apacheuk on 2010-05-03
same here.... fresh 10.04 install with any updates applied

---

### Post by meho_r on 2010-05-03
No offense ubuntuone devs, but the best solution for U1 problems (for me) was to purge everything that has "ubuntuone" in its name. I can't remember a day in which U1 worked fine, counting from the very beginning of its existence. I mean, seriously, how can I rely on service that fails every now and then (or, a little bit more precisely, mostly doesn't work)? For your (i.e. Ubuntu's) sake, I hope things gonna be sorted out soon and wish you well. But, for the moment, I personally would use more reliable services like Dropbox and similar.

---

### Post by joeyjoejo on 2010-05-03
I too have a similar problem. It used to work on 9.10, but now the best I can get is the little dedicated app to say 'synchronisation in process', but without ever showing any progress - it stays static for quite a while before disconnecting

One really interesting thing is that it has sync'd some files, but only about 4 out of the lot, and none which have been added in 10.04 (although it claims to have sync'd 4 folders, but nothing in the folder.

Could this be a network issue at canonical's end?

---

### Post by Ambystoma on 2010-05-03
> **joeyjoejo said:**
> I too have a similar problem. It used to work on 9.10, but now the best I can get is the little dedicated app to say 'synchronisation in process', but without ever showing any progress - it stays static for quite a while before disconnecting

One really interesting thing is that it has sync'd some files, but only about 4 out of the lot, and none which have been added in 10.04 (although it claims to have sync'd 4 folders, but nothing in the folder.

Could this be a network issue at canonical's end?

+1 on the progress bar but with no actual synchronization taking place.

---

### Post by joshuahoover on 2010-05-03
> **pomprint said:**
> I have just upgraded my Ubuntu Studio to Lucid and I am having the same problem. Nothing at all appears to be working with Ubuntu One. 

If I use Ubuntu One Preferences, it does not show my name, email address or plan, and I can't connect as I get the same 10 minute message about synchronization in progress and then get disconnected. I can, however, use the 'Manage my account' button, which DOES know who I am, and my email address.

If I move a file into the Ubuntu One folder it shows synchronization (the two arrows), but tells me (after 3 hours) on the website that it is uploading.

Furthermore, I downloaded Rhythmbox (not standard on Studio), and don't see the Ubuntu Music Store.

I hope that this gets sorted out soon as I think that I will be using the store in place of iTunes and Napster.

Our service has been experiencing large spikes in new users and overall use with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. Without seeing any logs, I can guess that you're being affected by these issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

My apologies to all for the inconvenience and thanks to everyone for all your patience. We want this fixed ASAP. We hate letting all of you down.

Joshua

---

### Post by joeyjoejo on 2010-05-04
don't know about everyone else, but mine is working fine now. Must have been a network issue from the higher load.

Anyway, it works well. Thanks for all the good work : )

---

### Post by joshuahoover on 2010-05-04
> **joeyjoejo said:**
> don't know about everyone else, but mine is working fine now. Must have been a network issue from the higher load.

Anyway, it works well. Thanks for all the good work : )

Good to hear! We're still working on improving a number of things, including contacts and notes sync. But we did make some updates late yesterday that have improved file sync for many users.

Thank you,

Joshua

---

### Post by EpoxyRepair on 2010-05-07
Ok, I'm confused about this. A plain file that place in, or remove from, from my Ubuntu One directory gets added to or removed from my online storage ok. However I bought a song from the online music store and there is no sign of the music directory in my Ubuntu One folder. I've had to manually download the song. Do I need the premium account for that feature 
to work.

I've given up on trying to sync Tomboy notes.

---

### Post by duanedesign on 2010-05-07
You should be able to see the songs in Rhythmbox, under Music. The files are downloaded locally into the folder:

~/.local/share/ubuntuone/Purchased from Ubuntu One

You may need to hit ctrl + h to see the .local folder in your $Home directory.

---

### Post by EpoxyRepair on 2010-05-09
Ok. Thank you for that. Found the files.Feel a bit silly that I didn't read the Rhythmbox help, as opposed to the Ubuntu One music store blurb.

---

### Post by pomprint on 2010-05-09
Just in case anyone is under the impression that the problem has now been sorted out after the initial interest following the release of Karmic, I have to report back as follows:-

Ubuntu One Preferences appears to work find using Ubuntu NBR on my Dell netbook.

Ubuntu One appears to function in a manner (waiting about 24 hours for files to upload and music from the store to download), but I have NEVER managed to get U1 Preferences to recognize my Ubuntu Studio machine. Has the program been successful for anyone else using Ubuntu Studio, or is this a problem brought about with the RT Kernel?

---

### Post by joshuahoover on 2010-05-11
> **pomprint said:**
> Just in case anyone is under the impression that the problem has now been sorted out after the initial interest following the release of Karmic, I have to report back as follows:-

Ubuntu One Preferences appears to work find using Ubuntu NBR on my Dell netbook.

Ubuntu One appears to function in a manner (waiting about 24 hours for files to upload and music from the store to download), but I have NEVER managed to get U1 Preferences to recognize my Ubuntu Studio machine. Has the program been successful for anyone else using Ubuntu Studio, or is this a problem brought about with the RT Kernel?

Do you mean that when you open Ubuntu One Preferences it never launches your web browser and prompts you to add your computer on Ubuntu Studio? If that is the case, have you tried this potential workaround? [https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?)

Thank you,

Joshua

---

### Post by pomprint on 2010-05-12
Joshua,

It is just as you say - it never opens the web browser and tells me that synchronisation is in progress for a few minutes. It then tells me that synchronisation is complete but the device name is showing as <LOCAL MACHINE> and all three entries in account information give 'unknown'. I have tried the work-around on numerous occasions and there is no difference.

This having been said, if I put a file in the U1 folder it transfers correctly and, if I buy music, this (eventually) transfers too.

Hope that this helps.

---

### Post by joshuahoover on 2010-05-12
> **pomprint said:**
> Joshua,

It is just as you say - it never opens the web browser and tells me that synchronisation is in progress for a few minutes. It then tells me that synchronisation is complete but the device name is showing as <LOCAL MACHINE> and all three entries in account information give 'unknown'. I have tried the work-around on numerous occasions and there is no difference.

This having been said, if I put a file in the U1 folder it transfers correctly and, if I buy music, this (eventually) transfers too.

Hope that this helps.

Strange. Although it's not the same issue, can you take a look at the following bug and try the workaround there and let me know if it helps? [http://launchpad.net/bugs/576263](http://launchpad.net/bugs/576263)

Thanks,

Joshua

---

### Post by pomprint on 2010-05-12
Joshua,

Works fine until I get to add my computer and then I get 'unable to connect' message.

Strange???

---

### Post by joshuahoover on 2010-05-13
> **pomprint said:**
> Joshua,

Works fine until I get to add my computer and then I get 'unable to connect' message.

Strange???

OK, so your browser opens, prompts you to give a computer name, you submit the form and then get the unable to connect message? Is it possible you have some sort of rules in your browser or elsewhere to block calls to localhost? 

Can you run the following command in a terminal session and make sure you have similar entries at the top of the output? more/etc/hosts

127.0.0.1    localhost
127.0.1.1    myusername

Thanks,

Joshua

---

### Post by El Zoido on 2010-05-14
I've also encountered lots of problems since upgrading to 10.04.

Ubuntu one is synching my files on one of my two connected PCs, but not on the other one (both Ubuntu 10.04, one 32bit, the other 64bit).

Also I really do hope that Evolution integration will be back soon, as I was relying on my contacts stored there.

I'm quite willing to show some patience here, but right now it seems to me that Ubuntu One went from late beta (Karmic) back to early alpha in Lucid.
Hope you'll figure it out soon!

---

### Post by joshuahoover on 2010-05-14
> **El Zoido said:**
> I've also encountered lots of problems since upgrading to 10.04.

Ubuntu one is synching my files on one of my two connected PCs, but not on the other one (both Ubuntu 10.04, one 32bit, the other 64bit).

On the computer that isn't syncing files, do you get past the step where you add your computer? Have you tried the suggested work around posted above? [https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?) I'd like to help get everyone up and running so any additional info you can provide is much appreciated.

Thank you,

Joshua

---

### Post by pomprint on 2010-05-14
> **joshuahoover said:**
> OK, so your browser opens, prompts you to give a computer name, you submit the form and then get the unable to connect message? Is it possible you have some sort of rules in your browser or elsewhere to block calls to localhost? 

Can you run the following command in a terminal session and make sure you have similar entries at the top of the output? more/etc/hosts

127.0.0.1    localhost
127.0.1.1    myusername

Thanks,

Joshua

If I understood correctly, this is my output.

steve@ubuntustudio:~$ more /etc/hosts

# The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

I trust that this means something to you?

---

### Post by pomprint on 2010-05-14
I have now discovered that the previous problem was with Firefox and not U1. I fixed the problem by installing Chromium, making this my default browser, and everything connected. i.e. I added this computer.

I am, however, now back to square one. Ubuntu One works, as far as I can ascertain, but the Ubuntu One Preferences still gives no machine name or account details (but it says that synchronisation is complete after a couple of minutes).

---

### Post by El Zoido on 2010-05-14
> **joshuahoover said:**
> On the computer that isn't syncing files, do you get past the step where you add your computer? Have you tried the suggested work around posted above? [https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?) 

The PC that is not synching is already added.
When starting the Ubuntu One client it is connecting and saying that is is syncronizing.
However, no files show up in the folder (which also has a lock symbol on it, not a check mark as on the other PC).

Edit: I tried removing the PC. When doing so, Firefox is automatically opening the tab to add the PC again.
I added it again but it seems it is still not synching.

Edit 2: u1sdtool -s is not showing any output at all.

---

### Post by joshuahoover on 2010-05-14
> **El Zoido said:**
> The PC that is not synching is already added.
When starting the Ubuntu One client it is connecting and saying that is is syncronizing.
However, no files show up in the folder (which also has a lock symbol on it, not a check mark as on the other PC).

Edit: I tried removing the PC. When doing so, Firefox is automatically opening the tab to add the PC again.
I added it again but it seems it is still not synching.

Edit 2: u1sdtool -s is not showing any output at all.

Hmmm... u1sdtool -s should show something along these lines:

```
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```

Try this set of commands and see if it outputs anything:

u1sdtool -d; u1sdtool -c; u1sdtool -s

Thanks,

Joshua

---

### Post by joshuahoover on 2010-05-14
> **pomprint said:**
> I have now discovered that the previous problem was with Firefox and not U1. I fixed the problem by installing Chromium, making this my default browser, and everything connected. i.e. I added this computer.

I am, however, now back to square one. Ubuntu One works, as far as I can ascertain, but the Ubuntu One Preferences still gives no machine name or account details (but it says that synchronisation is complete after a couple of minutes).

It looks like you're using IPv6 and I'm not sure how that might affect the way Ubuntu One (in particular the Prefs app) works. I need to ask some of the devs as I don't have a good way to test this myself.

Thank you,

Joshua

---

### Post by El Zoido on 2010-05-14
> **joshuahoover said:**
> Try this set of commands and see if it outputs anything:

u1sdtool -d; u1sdtool -c; u1sdtool -s


No, no uotput on any of these commands.
The task seems to be running (i.e. the terminal will not accept another command), but either it locks up or takes forever to complete.

It worked fine on the other PC (the one that is synching) but not on this one.

---

### Post by joshuahoover on 2010-05-14
> **El Zoido said:**
> No, no uotput on any of these commands.
The task seems to be running (i.e. the terminal will not accept another command), but either it locks up or takes forever to complete.

It worked fine on the other PC (the one that is synching) but not on this one.

I think I'll need to see some log files from the computer that isn't working. Can you file a bug from this computer by following these steps please?

[LIST=1]
[*][https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
[*]At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
[/LIST]
Thanks,

Joshua

---

### Post by Odisej on 2010-05-22
Well. It's not working for me either. It never really has. For a long time I thought it should actually work in a way I upload and download files manually but since I bought quite a few songs on ubuntu one it became impractical to do so. Finally read about how Ubuntu One should work. Well, it doesn't. 

No files, synch in progress forever, never moving an inch. No files in "shared with me". Music available via web and no other way

u1sdtool -s gives:

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

Needless to say... nothing happening. 

This whole thing makes my Ubuntu One experience quite similar to Linux experience 5 years ago... endless searching for answers to never ending problems.

---

### Post by joshuahoover on 2010-05-24
> **Odisej said:**
> Well. It's not working for me either. It never really has. For a long time I thought it should actually work in a way I upload and download files manually but since I bought quite a few songs on ubuntu one it became impractical to do so. Finally read about how Ubuntu One should work. Well, it doesn't. 

No files, synch in progress forever, never moving an inch. No files in "shared with me". Music available via web and no other way

u1sdtool -s gives:

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH

Needless to say... nothing happening. 

This whole thing makes my Ubuntu One experience quite similar to Linux experience 5 years ago... endless searching for answers to never ending problems.

Based on that status, things appear to be processing. How many files and folders are you attempting to synchronize? Are you just synchronizing music purchases or have you selected to synchronize other files on your computer? If you continue to have problems, please file a bug report following the steps below. Post the number here and I'll look into it ASAP.

1. Run the following from a terminal session: echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py; u1sdtool -q; u1sdtool -c 

2. File a bug at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

3. Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######

4. Run this command from a terminal session: tar cjf ~/u1logs.tar.bz2 ~/.cache/ubuntuone/log

5. Attach ~/u1logs.tar.bz2 to the bug report

Thank you,

Joshua

---

### Post by B Crowther on 2010-06-02
The only part of Ubuntu One I really need to work for me is syncing notes and contacts.

Every day I check, every day this function is still disabled.

Kinda feels like a government promise, at the moment, Ubuntu One: we are told it will happen, but not in whose lifetime.

---

### Post by doko1 on 2010-06-02
Ubuntu One didn't work for me in the last 2 Months. I have read this thread and several bug reports connected with this problem, but couldn't solve the problem. 
In one of the bug report I remember reading something like "... synching problems / bugs won't get solved until the next Ubuntu distribution release..." I don't know how reliable this information is, and I am sorry if i tell something wrong here. 

Nevertheless, my patience has been tested enough. I use [Dropbox]("https://www.dropbox.com/referrals/NTc2NzkwMjk5") now. It's totally free of bugs so far and works really fast. 
Still, I will keep an eye on Ubuntu One in the future. It's a great project. :)

---

### Post by duanedesign on 2010-06-02
There was a large increase in users with the last release. This degraded performance of the U1 service. New server farms are being brought online and we should be seeing an increase in speed very soon.

---

