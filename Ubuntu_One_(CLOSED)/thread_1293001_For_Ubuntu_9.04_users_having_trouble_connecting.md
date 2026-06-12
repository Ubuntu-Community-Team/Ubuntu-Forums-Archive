---
title: "For Ubuntu 9.04 users having trouble connecting"
date: 2009-10-16
forum: Ubuntu One (CLOSED)
---

### Post by castrojo on 2009-10-16
> We have discovered a bug that affects Ubuntu 9.04 users with our latest
client (255) who did not already authorize their computer with the
service. This problem is a result of having a dependency on Python 2.6.3
while 9.04 has Python 2.6.2. What this means currently is that you won't
be able to connect to the service. We apologize for the inconvenience
and hassles this may be causing some of you. We're working on a
solution. The bug we're tracking this problem can be found at:

[https://bugs.edge.launchpad.net/ubuntuone-client/+bug/451670](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/451670)

Thank you for your patience and support!

Joshua


Original announcement here: [https://lists.launchpad.net/ubuntuone-users/msg00275.html](https://lists.launchpad.net/ubuntuone-users/msg00275.html)

---

### Post by joshuahoover on 2009-10-19
Good news! We've fixed this nasty bug and recommend everyone to update to the latest client. Thank you for your patience!

Joshua Hoover

---

### Post by niw_uk1964 on 2009-11-01
On both of my systems runninfg 9.10 the Ubuntu One client will not connect.

I have a validated account and both systems are listed in the attached machines list. One is my workstation running the 64-bit version, the other is my Dell Mini-8 running the UNR version.

I get no errors. They just won't connect when I ask them too.

If I delete their keyrings to start again, it prompts the whole registration process again as you'd might expect, but with the same results.

The system crash handler does report a crash on each system when booting, but not what the crash might be. It might be related, but I have no idea what it might be. I see nothing obvious in the logs, but I am not sure where to look or what to look for anyway.

Any ideas? TIA.

---

### Post by RavanH on 2009-11-05
> **niw_uk1964 said:**
> On both of my systems runninfg 9.10 the Ubuntu One client will not connect.

I have a validated account and both systems are listed in the attached machines list. One is my workstation running the 64-bit version, the other is my Dell Mini-8 running the UNR version.

I get no errors. They just won't connect when I ask them too.

If I delete their keyrings to start again, it prompts the whole registration process again as you'd might expect, but with the same results.

The system crash handler does report a crash on each system when booting, but not what the crash might be. It might be related, but I have no idea what it might be. I see nothing obvious in the logs, but I am not sure where to look or what to look for anyway.

Any ideas? TIA.

Are you using Network Manager to connect? If not, that might be causing it. See [https://bugs.launchpad.net/ubuntuone-client/+bug/357395](https://bugs.launchpad.net/ubuntuone-client/+bug/357395)

---

### Post by Roger Allott on 2009-11-05
> **joshuahoover said:**
> Good news! We've fixed this nasty bug and recommend everyone to update to the latest client. Thank you for your patience!

Joshua Hoover

Are you sure this bug has been fixed? I'm still having problems with my ubuntu 9.04 machine - I cannot connect to UbuntuOne via Nautilus.

The packages installed are:
ubuntuone-client 1.1+r273-0ubuntu1~ppa2~jaunty
ubuntuone-client-gnome 1.1+r273-0ubuntu1~ppa2~jaunty
python-ubuntuone-client 1.1+r273-0ubuntu1~ppa2~jaunty
ubuntuone-ppa-beta 2009.05.14-0ubuntu1
python-ubuntuone-storageprotocol 1.0.0+r73-0ubuntu1~ppa1~jaunty


My second machine runs xubuntu 9.10. I was under the impression that UbuntuOne was pre-installed in 9.10 distributions, but I can't find it at all in my Applications menus. How do I initiate it?

---

### Post by Placidia on 2009-11-07
I am having problems as well. I am running Jaunty 9.04. I installed it within the past week. (upgraded to Karmic; it broke my USB dongle; returned to Jaunty with a clean install; most recent upgrades)

I installed the Ubuntu One client.

Ubuntu One claims to connect, but files are not being transferred properly. My Tomboy notes did not upload -- they got synchronized to the Ubuntu One folder on my machine, but went no further.

---

### Post by RealG187 on 2009-11-09
How do I update, what command do I type?

---

### Post by robtg on 2009-11-14
My 9.04 laptop won't connect to Ubuntu One.  It connected once immediately after I installed it a few days ago but will not connect now (either through Nautilus or the icon in the notification area).

Rob

---

### Post by centralmtk on 2009-11-15
> **robtg said:**
> My 9.04 laptop won't connect to Ubuntu One.  It connected once immediately after I installed it a few days ago but will not connect now (either through Nautilus or the icon in the notification area).

Rob

i believe to be having the same problem. Im running ubuntu server 9.10. it wont connect when running "aptitude update"

---

### Post by Roger Allott on 2009-11-18
3 new update files came through just now on Update Manager.

And for the first time ever, I've managed to connect through Nautilus!!!! And I've managed to transfer/upload a file to UbuntuOne simply by copy/pasting!!!!

However, I uploaded a file via Firefox some time ago, and whilst I can still see that file via Firefox, I can't see it via Nautilus.

A big improvement, but still not quite right.

---

### Post by robtg on 2009-11-18
> **Roger Allott said:**
> 3 new update files came through just now on Update Manager.



I just applied (probably) the same 3 updates; still can't connect (Nautilus or through the notification-area icon).

Is there a way to see an error message or log which will tell me why it won't connect?

Rob

---

### Post by moz44 on 2009-12-03
Guys I am having problems also with connecting my client with cloud Ubuntu One service. My Ubuntu 9.10 is updated as of Dec 3 2009 (today).  I could catched an error message, please see attached image. I hope the image helps someone identify the problem and post a solution.

thanks

---

### Post by KaYnemO on 2010-01-14
I cannot figure out for the life of me how to sync Evolution contacts with Ubuntu One, also cannot connect through Nautilus. When I hit connect in Nautilus it connects and then immediately drops the connection. With Evolution, I get an error message that says the URL is wrong (????) and that there is an issue with permissions. Any ideas?

---

### Post by AlexanderDGreat on 2010-03-09
Using Jaunty, Ubuntu One DOESN'T WORK Anymore after UPGRADE! It's Mar. 9, 2010.

---

### Post by crf112 on 2010-03-11
I also found that Ubuntu One doesn't work anymore on my 9.04 system after working fine for several months.  It looks like /usr/bin/u1sync and /usr/bin/ubuntuone-client-applet have disappeared.

I have removed Ubuntu One and have not been able to reinstall it.  I had to give up working on the problem because of other more important issues and will try again tomorrow.  Has the installation procedure changed since two months ago?

---

### Post by RealG187 on 2010-03-11
I've been using Windows for a while and started using Ubuntu a little while ago and it doesn't look like it's been syncing for a while. I am still on 9.04

---

### Post by derrek.cooper on 2010-03-16
not working for me on 9.10 for the last week or so? cloud icon has an !.. when I attempt to connect, says apport= collecting problem informatio

then attempts to collect info, but crashes- cannot collect crash data.check internet connection

---

### Post by flattop1 on 2010-04-01
Yeah mine hasn't worked for a few weeks now.
The cloud has a red dot inside it and the cloud icon now longer appears in the task area.
It doesnt say that Im not connected but I know from checking online that nothing is syncing to the cloud.

[IMG]http://i910.photobucket.com/albums/ac306/paradiseliving/trash/Screenshot.png[/IMG]

any fixes?

---

### Post by Andre_luis_bsrsoft on 2010-04-12
In all 9.10 desktops in my company the Ubuntu One dont connect. Anybody know everything about this issue?

---

### Post by hoeltgman on 2010-04-18
Either I'm too stupid to use this. Or it doesn't sync for me as well.

---

### Post by mok0 on 2010-06-27
UbuntuOne is completely unfunctional for me on my Jaunty machine. Using u1sdtool -s I get an auth error no matter what, even though I am connected via the web interface. I am soon to give up on UbuntuOne, it is not reliable enough for my purposes.

---

### Post by duanedesign on 2010-07-16
if you are having authentification problems I would try and reauthorize your computer. The steps are:

   1. Quit the Ubuntu One client (if its open)
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after following these steps.

thank you,
duanedesign

---

