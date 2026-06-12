---
title: "[SOLVED] Problems Configuring Print Server"
date: 2008-12-14
forum: Server Platforms
---

### Post by bluesy321 on 2008-12-14
Hello Everyone!  First off, I wanted to just say hi to everyone on the forums.  I've been hunting around the forums for different things for awhile now and just never had a need to register yet.  I apologize if I give too much info in my post, but I'd like to include everything relevant.

My problem is with trying to setup a File/Print Server with Ubuntu.  I've been messing around with this idea for awhile now, as I'm finally setting up a file/print server for all the PCs (and XBMC) in my house.  I've played around with Ubuntu Server with a few different desktops, as just a CLI box with SSH, and finally have decided to use Ubuntu Server with Webmin as it seems to give me the best balance between working with CLI only and wasting resources/security risks of running a full GUI on my server. BTW, I'm using Ubuntu 8.04, and Webmin 1.441 currently.

I've been able to setup the file server portion of this without any major problems.  It took awhile to get everything setup and figure out how to give specific file permissions, but thanks to this forum especially it wasn't too bad.

I've moved on to setting up the print server for my HP OfficeJet 5610 All-In-One.  Here's where I have run into major problems.  I can't seem to add a printer either through the CUPS web interface, or through Webmin.  I have managed to get the drivers downloaded and installed for my printer, and it is detected by CUPS.

I've tried searching the forums for awhile and haven't found a ton of info on this subject.  However, I did stumble upon the HOWTO ([http://ubuntuforums.org/showthread.php?t=310450](http://ubuntuforums.org/showthread.php?t=310450)) concerning this and it has helped me make some progress.  The problem with this method seems to be with the CUPS user.  I can get as far as the "Allow CUPS to read the password file" section before running into problems.  When I try to run the command "adduser cupsys shadow", I receive an error stating "adduser: The user `cupsys' does not exist."  I am then able to access the CUPS web interface and can attempt to add a new printer.  The system detects the HP OfficeJet 5610 I mentioned previously, and recognizes the driver I installed.  Once I get past those steps and it attempts to actually install the printer with the settings I've selected, I'm prompted for login information.  I enter the correct login information for the sudo user I'm currently using, but it fails the authentication and I'm then locked out of the CUPS web interface for a period of time.  I can't help but think this is related to the step of allowing CUPS to read the password file as I've ensured the user I'm logging in as is part of the lpadmin group and I've checked the CUPS error log which shows "unauthorized" errors.

When I try adding the printer from Webmin, I am able to enter all the information for my printer and see the driver I have installed for the CUPS driver section.  But, when I try to click the Create button, I receive the following error:
Failed to save printer : lpadmin failed :
lpadmin: Unable to connect to server: Connection refused

If anyone can assist me with this issue, I'd greatly appreciate it.  I apologize if any of this is been covered extensively, but I've tried searching the forums and have gone through the HOWTO I mentioned before along with a few other recommended resources like the Ubuntu Server Guide, and the Community Documentation without finding the info I need.

Thanks!

---

### Post by bluesy321 on 2008-12-20
Well, I was going to bump my own thread a couple days ago; however, I figured out my problem.  I will mark the thread solved, but I wanted to post my solution in case anyone else runs into this problem and stumbles on my thread.

As I thought, it was something in the configuration file that I was doing incorrectly.  I can't say exactly which parts I left out because I didn't save a copy of the bad config file and the cups web interface overwrote my working config file once I setup the printer.  Just to throw it out there though, this is one reason why you always want to backup config files before editing them.  If I hadn't been able to restore the config file, I'm not sure I ever would have figured it out.

So I restored the cups config file and began editing it.  Essentially what I wasn't doing was commenting out all the security parts and it was causing the system to try and force a login when it couldn't access the password file.  Unfortunately, I never was able to allow the cups system to access the password file and couldn't play around with security at all.  However, I was able to load the CUPS web interface after commenting out all the security parameters where it was looking for SYSTEM or OWNER user's.

---

