---
title: "ubuntu one not connecting."
date: 2009-10-02
forum: Ubuntu One (CLOSED)
---

### Post by millstone on 2009-10-02
Hello,
Ubuntu one is not connecting, even after I click "connect"
what is the problem?
Any help will be much appreciated, :)

---

### Post by sulio on 2009-10-03
yep, same here. In the upper right corner of the Ubuntu One folder the button stays "Connecting" and nothing. Moving the mouse over the applet and it says "Disconnected". If I close the applet and start it again it asks for password and it dosn't accept any. Maybe both thing are connected, but not sure how.
9.04/i386 version.
Update : I have changed on this machine the password of my account few times and it accepted one of my old passwords. After that the applet updated the files and it works for now :)

---

### Post by joey-elijah on 2009-10-04
My issue has been similar, but although it says it connects and my files are up-to-date - nothing in my ubuntuone folder is useable; photos are 'not valid photo formats' etc but downloading them from online, they're fine.

---

### Post by vinutux on 2009-10-16
is there is any fix for this prob ?

---

### Post by andrea000 on 2009-10-16
I have had this problem since Thursday ubuntu one
just went down and a update this morning did not
fix it.From what i can find it's a problem with
there server and has nothing to do with the software.

---

### Post by jordilin on 2009-10-17
Same problem in here with Jaunty. Ubuntu one is in beta and they have been updating it quite often last days with karmik just around the corner.

---

### Post by volkswagner on 2009-10-17
My icon just has the x, indicating it is not connected.  When I try to connect nothing happens.  

/var/log/auth.log is littered with the following.

```
Oct 17 16:27:04 T43 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3370 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.46" (uid=0 pid=4010 comm="/usr/bin/python /usr/lib/system-service/system-ser"))
Oct 17 16:27:05 T43 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3370 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.47" (uid=109 pid=4012 comm="/usr/lib/policykit/polkitd "))
Oct 17 16:27:36 T43 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3370 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.48" (uid=0 pid=2815 comm="/usr/sbin/cupsd "))
Oct 17 16:30:01 T43 CRON[4192]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 17 16:30:01 T43 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3370 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.49" (uid=0 pid=4192 comm="/USR/SBIN/CRON "))
Oct 17 16:30:01 T43 CRON[4192]: pam_unix(cron:session): session closed for user root
Oct 17 16:40:01 T43 CRON[4375]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 17 16:40:01 T43 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3370 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.50" (uid=0 pid=4375 comm="/USR/SBIN/CRON "))
Oct 17 16:40:02 T43 CRON[4375]: pam_unix(cron:session): session closed for user root
Oct 17 16:50:01 T43 CRON[4608]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 17 16:50:01 T43 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=3370 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.51" (uid=0 pid=4608 comm="/USR/SBIN/CRON "))

```

Also Firefox CPU usage goes to nearly 50% for first couple minutes after first launch.  Disk usage is also very high at that time.

I am not sure if the above is related or not.

Via the Ubuntu-One web interface, My files are missing although it shows usage as correct.

---

### Post by windowsfree on 2009-10-19
will ubuntu one work with version 9.10 when released?

---

### Post by TwistedNsanity on 2009-10-20
Ubuntu One is pre-installed on Karmic although it seems a little buggy.

---

### Post by Mia1990 on 2009-10-20
Mine has n't worked for a few days now i am able to connect and upload a few files then the home folder and all the files comes up with u1 conflict???:confused:
what do i do?

---

### Post by skbhat03 on 2009-10-22
Mine works some times and some times it doesn't, i am using 9.10:(

---

### Post by joshuahoover on 2009-10-22
> **skbhat03 said:**
> Mine works some times and some times it doesn't, i am using 9.10:(

Apologies for the intermittent issues. We've been making some enhancements on the server side that should address this issue. If you're still having problems, please report a bug by right-clicking on the Ubuntu One client and selecting "Report a Problem".

Thank you,

Joshua

---

### Post by Zenuno on 2009-10-25
Hi to all...

I have the same problem, here in Portugal, i can't log in in Ubuntu One.

I hope this problem is fixed in Ubuntu 9.10

I tell you in about 4 days...lol

---

### Post by Glugglug on 2009-10-26
I'm using Karmic RC  and getting the same   just  a cloud on the top panel with a  ! mark inside  it  .


It must have connected at  some time  because some of the files are in the folder  but not the most recent ones .

---

### Post by johnswb on 2009-10-28
Same problem here.  I was able to upload and now I can not.  Also, if I create a folder on the Ubuntu One site and sign out, it will be gone when I sign back in.

Will Ubuntu One be beta when 9.10 is released?

---

### Post by andrea000 on 2009-10-28
Mine still doesn't work i have uninstall it
i just don't know what else to do.I'M going
to give it a while then after i upgrade to
9.10 i may give it a go again i just don't
know maybe give it a few weeks and then
reinstall it....

---

### Post by vinutux on 2009-10-28
not working...ok wait for karmic....

---

### Post by yellerKat on 2009-10-29
"Capabilities Mismatch" anyone?

---

### Post by ChrisGaeth on 2009-10-29
Yup.  I am getting the same error.

---

### Post by Merovius on 2009-10-29
I have the mismatch too.

---

### Post by bertmanphx on 2009-10-29
Ditto...

---

### Post by joshuahoover on 2009-10-29
> **yellerKat said:**
> "Capabilities Mismatch" anyone?
[FONT=monospace]
[/FONT]The "Capabilities Mismatch" message notes a current issue we're working[FONT=monospace] [/FONT]through. You can follow our progress at: [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/462828](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/462828)

Thank you,

Joshua Hoover

---

### Post by marquinos on 2009-11-04
> **Hakkatuka said:**
> Deleting everything in ~/.local/share/ubuntuone/syncdaemon/ directory fixed it for me. It gets recreated as soon as you start ubuntuone client again. Also make sure you have the computer added just once on one.ubuntu.com website.

[This]("http://www.uluga.ubuntuforums.org/showthread.php?t=1291576") works for me.

---

### Post by yazid_j on 2009-11-05
Hi,

I just upgrade from Ubuntu 8.04 LTS to Ubuntu 9.10. I was about to try new features of Ubuntu One but it seem not connecting when I press the "Connect" button on the upper right side window (go to Places > Ubuntu One).

I have a valid lunchpad user ID and I have setup everything accordingly. Hmm... maybe it's still in beta.

Anyway, if you guys have any idea/solutions on how to sort it out, please share it with all of us.

---

### Post by tcole on 2009-11-05
I guess first, try quitting the applet, deleting ~/.config/ubuntuone/ubuntuone-client.conf, then restarting the applet and see if that makes a difference.

---

### Post by Tman5293 on 2009-11-06
I think I have solved the problem for 9.10 users.

First exit out of the U1 client

Then go to /home/(username)/.config/ubuntuone and delete everything in that folder.

After that just restart the U1 client and it should work.

---

### Post by vashman on 2009-11-07
This workaround for my connection problem in karmic, with everything updated. Just hitting connect then going to settings and checking the limit band width box. will work sometimes I can turn off the system and it will actually connect by itself. 

note: found this to be a definite bug, it should be noted that the limit band width option never saves and reverts back as soon as the windows is closed.

Ubuntu One client: package: ubuntuone-client
                            version:  1.0.2-0ubuntu2

---

### Post by mickcalcara on 2009-11-08
I installed Karmic about a week ago. Ubuntu One worked for about two days then stopped working. The client says it is updating files but when I logged on to Ubuntu One those files are not updated. And the same is true when I add files through the web interface and files are my desktop do not get updated.

What is strange, as I said, this was working for a few days then just stopped.

Any suggestions? Thanks

---

### Post by joshuahoover on 2009-11-09
> **mickcalcara said:**
> I installed Karmic about a week ago. Ubuntu One worked for about two days then stopped working. The client says it is updating files but when I logged on to Ubuntu One those files are not updated. And the same is true when I add files through the web interface and files are my desktop do not get updated.

What is strange, as I said, this was working for a few days then just stopped.

Any suggestions? Thanks

Did you possibly try to set the bandwidth settings in the Ubuntu one client preferences? There is a known bug that we're currently fixing to resolve this, but for now, it's safer to leave this preference alone. You can try deleting ~/.config/ubuntuone/syncdaemon.conf and starting up the client again.

If you still have problems connecting, please file a bug report by right-clicking on the Ubuntu One client and selecting "Report a Problem". 

Thank you,

Joshua

---

### Post by yurx cherio on 2009-11-09
Looks like UbuntuOne client is relying on NetworkManager, though the later one is not a dependency. I am not using NetworkManager neither at home nor at the office. In fact I uninstall it. Instead I use WICD (when connecting wirelessly) or simply update network configuration files.

Honestly relying on NetworkManager presence doesn't seem to be a good design decision in my mind. As long as internet/network connection is present this should be more than enough for filesharing, syncronization etc. I haven't seen a program (browser, messenger, any protocol client, etc) which would rely on a specific connection manager.

---

### Post by Kirk M on 2009-11-10
> **Tman5293 said:**
> I think I have solved the problem for 9.10 users.

First exit out of the U1 client

Then go to /home/(username)/.config/ubuntuone and delete everything in that folder.

After that just restart the U1 client and it should work.

Please excuse a newbie question but what's the command for restarting the Ubuntu One client? I've Googled all over the place trying to find it (can find any other terminal command but that) and no luck. ](*,)

---

### Post by rodrigo_ on 2009-11-10
> **Kirk M said:**
> Please excuse a newbie question but what's the command for restarting the Ubuntu One client? I've Googled all over the place trying to find it (can find any other terminal command but that) and no luck. ](*,)
You should be able to select Quit on the right-click menu on the applet, and then, run it again by going to Applications->Internet->Ubuntu One

---

### Post by Frdbrkl on 2009-11-30
I had the same issues...manually deleted files, reinstalled-same problem. Could not  get it to connect at all.

Then I went to System/Preferences/Startup Applications and checked the box next to "Remote Desktop"....

VIOLA!

In my paranoia, I had disabled this....

{EDITED}

Well....that didn't work after a reboot.  I'll just wait for lucid and do a fresh install.

---

### Post by babusar on 2009-12-12
> **Tman5293 said:**
> I think I have solved the problem for 9.10 users.

First exit out of the U1 client

Then go to /home/(username)/.config/ubuntuone and delete everything in that folder.

After that just restart the U1 client and it should work.

This worked perfectly for me, thanks!

---

### Post by switch10 on 2009-12-12
> **Tman5293 said:**
> I think I have solved the problem for 9.10 users.

First exit out of the U1 client

Then go to /home/(username)/.config/ubuntuone and delete everything in that folder.

After that just restart the U1 client and it should work.

This worked for me...

---

### Post by piojunbabia on 2009-12-13
i uploaded a sample file on my ubuntu 1 account but after uploading, it cant be seen in the files.. it only shows "loading" but i waited long for it to load and now its not showing any. I uploaded a .jpg

by the way, as far as i know ubunut has many bugs, these bugs can be found here: [https://launchpad.net/ubuntu/+bugs]("https://launchpad.net/ubuntu/+bugs"), a few of the bugs includes ubuntu one.... hope they fix these bugs... thanks Canonical

---

### Post by MickeyMcP on 2010-02-12
> **Tman5293 said:**
> I think I have solved the problem for 9.10 users.

First exit out of the U1 client

Then go to /home/(username)/.config/ubuntuone and delete everything in that folder.

After that just restart the U1 client and it should work.

Solved my connecting problem - Thanks Tman!  Now to upload/sync some files and see if I can see and access them.

---

