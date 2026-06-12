---
title: "Samba auto connect from XP Pro"
date: 2009-05-14
forum: Server Platforms
---

### Post by orotrev on 2009-05-14
I have samba all setup and everything is working correctly except for one thing; Auto connect from Windows XP. I can map a drive to my samba server and connect to it. When I set XP to "Reconnect at Login" it does not reconnect. When I browse My Computer I see the disconnected drive. I click on the drive, I get prompted for a login and password, enter the same login and password as when I mapped the drive in the first place and everything connects. I checked the samba logs and did not see anything out of the ordinary. So long story short, how do you get XP to auto connect to a Samba share

---

### Post by a9k3d on 2009-05-14
Is this an overnight failure or immediate (logoff, reboot and no autoconnect)?

Is the samba server is getting it's IP from DHCP? If the server is a moving target XP won't autoconnect.

---

### Post by orotrev on 2009-05-14
It is immediate. Both the client and the server have static IP addresses. I have tried mapping the drive with the hostname of the samba server and the IP, no go

---

### Post by glasswalkerny on 2009-08-03
I am having this same problem.. I'm running XP Pro SP3 and when i map a drive i see the information but after a reboot windows marks the drives as not connected (by icon) but after opening the drive (no request for a password because my username/password in windows is identical to an allowed username/password on the server) i can see the data.. windows never updates the icons to online though. If i open, say Outlook, i get a "Can't find .pst" error (my pst's are on my server) but the dialog box that opens is looking right at the .pst...

i've attached my smb.conf

---

### Post by Thirtysixway on 2009-08-03
Try the solution I posted on my blog:

[http://noobbox.com/2009/04/auto-mount-samba-share-ubuntu-and-windows](http://noobbox.com/2009/04/auto-mount-samba-share-ubuntu-and-windows)

It has directions for both Ubuntu and Windows machines.

---

### Post by glasswalkerny on 2009-08-04
ah but the 'net use x:' command is what windows runs to re-establish mapped drives on startup.. my problem isn't that the connection isn't seen it's just not initialized properly.. the drives show up but i have to "ping" them with something to make them "active" 

trust me i'm a server admin.. i've tried things like this.. but thanks for the suggestion

---

### Post by garfonzo on 2009-08-04
> **glasswalkerny said:**
> ah but the 'net use x:' command is what windows runs to re-establish mapped drives on startup.. my problem isn't that the connection isn't seen it's just not initialized properly.. the drives show up but i have to "ping" them with something to make them "active" 

trust me i'm a server admin.. i've tried things like this.. but thanks for the suggestion

I had the same issue...sort of. when I would open Media Monkey on my Windows box, it would not find the music (all greyed out). All I had to do was close Media Monkey, open the "Unconnected Drive", wait a bit, and presto, files available. Open Media Monkey and everyone was fine. 

Unfortunately, for this thread, I never resolved it. Tis annoying!

---

### Post by Audiosears on 2010-07-22
Guys,

I have had this issue as well - With XP, we set up the shares such that passwords are saved.  When a user signs onto the machine (through our Active Directory domain), they reach their desktop and the drives do show as disconnected.  Since multiple shares are all on the same Samba server, a user has only to double click one of the network drives to activate it, and the rest become active as well.

If you map a drive in XP to another windows machine's share, you can observe that logging on and viewing the share, it appears to be already connected.  Not sure why Windows is able to activate shares in this way on other windows machines but not for Samba shares - have never deduced whether this needs to be corrected on the Windows or the Samba side (or both?).

With Windows 7, this problem is compounded a bit:

[http://ubuntuforums.org/showthread.php?t=1527521]("http://ubuntuforums.org/showthread.php?t=1527521")

I don't mind the XP issue much as it's a minor inconvenience, but the behavior of Win 7 showing a black screen for 3-5 mins on startup after login and having to kill your saved password is a PITA after awhile.  You have to some editing of the local security policy (or group policy via AD) to even get it to connect.

Anyone have any luck solving these issues?

---

