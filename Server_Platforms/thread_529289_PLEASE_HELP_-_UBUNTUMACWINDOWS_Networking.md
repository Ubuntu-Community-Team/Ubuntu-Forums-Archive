---
title: "PLEASE HELP - UBUNTU/MAC/WINDOWS Networking"
date: 2007-08-19
forum: Server Platforms
---

### Post by moxon on 2007-08-19
First of all I am new to Ubuntu.  I tried Fedora Core years ago and gave up on Linux because I could not get some things working so I bailed out.  I don't want to this time.  But I follow all instructions on the forums and still cannot get some things to work.  I have searched the forums and followed many how-to's but still dosen't work......Frustrating!!!

So here is the deal.  I am trying to be able to access a USB drive attached to my Ubuntu machine from my MAC and Windows machine.  When I try and set permissions on the USB drive it says I am unable to change from read to read/write.  I have setup under sharing the USB drive for windows and unix sharing.

I followed the directions for setting up SAMBA from this link [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Oh, by the way, I tried going to network in Ubuntu, and connecting to the shared drive and it also does not let me do it, so obviously something is not setup correctly.

I had a few problems setting up the users.  When I went to set them up and add the password, it said password change failed???? Don't understand.  

Anywho,  I have tried access from both MAC/XP and they both see the shared drive, and when I try and access, it asks for a password, I give what I put in, in the directions, and on MAC it says alias not found.  And on Windows it says it says network resource not available.  

I really want to get his going and learn what I am doing wrong, so I can continue using Ubuntu.  

Please Help!  
Michael

---

### Post by broncavfan on 2007-08-19
It sounds like you're having a problem getting full access to the Windows NTSF file system.  For one reason or another NTSF isn't installed by default with Ubuntu.  There's a nice guide here [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) that'll help you get that working.  It will allow you to read and write to the NTSF filesystem, which the Mac can use as well.  If NTSF is good for something it's being fairly universal.  

I'm not quite sure what you're talking about with the Samba connection, but I just wanted to say that I used that guide to get Samba working (for my XBox) as well and I found it easier to just right click on a folder and scroll to 'Share Folder...' and change the 'Share through' to 'Windows Networks (SMB)'.  

However, I think my suggestion from the first paragraph should fix the problem you're having.  If you still can't get it working let us know and we'll try to help.  These forums have a lot of information, you just have to keep looking.

Good Luck!

---

