---
title: "Setting up a system for preschool teachers"
date: 2008-03-01
forum: Testimonials &amp; Experiences
---

### Post by caduceus1 on 2008-03-01
The daycare/learning center that my daughter goes to has a computer that the teachers use.  The Win98 hard drive died and they have no IT people managing any of their computers.  I volunteered to help.  I replaced the hard drive and installed Gutsy Ubuntu.

The teachers use the system mainly for internet access, word processing, some spreadsheet work, and email.  Fairly straightforward stuff.

The system is up an running and it works great.  Before I bring it back to the daycare, I'm wondering if any of you have suggestions (or links) on tweaking things to make it as simple as possible for a bunch of not terribly computer savvy teachers, using a common login.

I'm most interested in:

1)  Avoiding them having to deal with software updates.
2)  Interoperability with Windows Office document formats.
3)  Suggestions for programs useful for preschool teachers.
4)  Common directory for storing documents, etc.
5)  Minimizing the chances that a teacher (or a toddler) mess up the system beyond requiring a reinstall.
5)  Basically making things as useful (and dummy-proof) for them as possible.

I don't think any of the teachers have had any exposure to alternate operating systems.  I'm hoping to make it easy enough so they don't call back clamoring for Windows to be put back on it.

If you've had any experience in this area, I'd love to hear your thoughts.  Thanks :)

=caduceus1=

---

### Post by buzzmandt on 2008-03-01
put all links they need on desktop, change it so it's one click run.  programs like firefox, open office (or koffice whichever you set up), thunderbird (or other mail link)

also go to add remove programs and check out the edutainment tab, might be something usefull in there.

also, when I set up my mom and dads comp I set it to log in automatically, they don't need to know the password.  While that lets anyone run the system, they can't install or do anything requiring the password since they don't know it.  This might be an option for you, although I do all the updates/upgrades to it.

---

### Post by seshomaru samma on 2008-03-01
I set up a computer system for a kindergarten with similar needs. The biggest difficulty was to convince them to use Open Office, they couldn't find all their favourite functions fromT MS Word (and many times I couldn't as well). I ended installing MS Office 2000 with Wine, it was a little difficult to get it to print, you had to edit the registry in Wine.
I think you can safely disable the updates. Create a /home partition (if you ever need to reinstall) . Create big icons for all the applications they need, I put it on the top panel (and doubled its size). Make sure all picture formats open with the same application. If Jpeg opens with picture viewer but PNG opens with gThumb they will get confused. I think gThumb is better as it allows for some simple picture ediiting.
There was a computer in each classroom for the children to play games on . At first I run Xubuntu but the kids managed to delete all the icons and the panels .I then tried IceWM and the icons survived. I wouldn't use IceWM for the teachers' computer. Though IceWM + nautilus might be interesting
I made sure all audio formats openned with the same player and that flash , Java and all possible codecs were installed as well as k3b, aMSN and Picasa. You can make the computer boot directly into Gnome and don't tell them the user password. They will have a difficult time messing up the system without it. You should clean the home folder and create folders like Music / Docs / Pictures or whatever and then put a big My Documents Icon on the top panle and tell them they can find their stuff there. If you can get the Icon from a Windows install that would be great.

---

### Post by schmildo on 2008-03-01
I reckon once you've got the 'perfect' setup, burn it to a live CD or something. So if they stuff it up you can tell them to just stick the CD in the drive and boot from that. (You might have to setup the bios for them too)

---

### Post by iheartubuntu on 2008-03-01
> **buzzmandt said:**
> also, when I set up my mom and dads comp I set it to log in automatically, they don't need to know the password.

How do you do that?

---

### Post by azimuth on 2008-03-01
> **shirteesdotnet said:**
> How do you do that?

System>Administration>Login Window>Security and check box for Enable Automatic Login

---

### Post by iheartubuntu on 2008-03-01
> **azimuth said:**
> System>Administration>Login Window>Security and check box for Enable Automatic Login

Wow, 6 months into Ubuntu and I never knew that was there :)

Thanks!

---

### Post by azimuth on 2008-03-01
> **shirteesdotnet said:**
> Wow, 6 months into Ubuntu and I never knew that was there :)

Thanks!

A long time Linux user would have given you a one line script to just cut and paste. Quick and dirty and very efficient. I am still learning the bash commands, so you are stuck with the time consuming and inefficient clicking through menus. While you are at it, spend some time looking through the System>Administration menus, You'll be suprised at the gems you'll find there. Don't go changing things there unless you're reasonably sure of the outcome, it is an excellent place to break your system.

---

### Post by caduceus1 on 2008-03-06
Many thanks to everyone.  I've been installing and tweaking things for the past few days.  I think I'm close to bringing the box back to the daycare.  I had a few glitches on the way.  I ran into the bootup screen resolution bug, but figured that one out.  Also the flash plugin checksum bug, but that's fixed now too.

I installed Picasa, a few simple Firefox plugins (PDF download and AdBlock Plus), codecs, etc.

I threw Firefox and OO Writer icons on the desktop for easy access.

I threw in a second hardrive and installed Sbackup so it backs up /home daily.  Ran into a nasty problem with that program taking root control of the entire second drive, but sorted that out.

I backed up all the installed packages to an .iso file with AptOnCD to the backup drive, just in case.  I hope I never have to figure out how do a compete restore! :)

I removed several items from the menus to prevent messing things up.

I configured OO Writer to save as Winword .doc files by default (bad idea?  I have no experience with OO).

I'm gonna throw a textfile on the desktop with some simple instructions on "how to use this computer".

The only other ideas I had was:
1) any way to have a panel item that will restore the desktop/menus back to the current settings?

2) it would be nice to have a **simple **way to image the main drive for quick restoration in case the whole system crashes.  This machine doesn't have any disc writer on it, although I have the backup drive in there (only 15 gig drive; main is 40 gigs), and an external HD of my own where I could write the image to.

Thanks so much for all your help.  It's been a fun experience overall.

---

### Post by hyper_ch on 2008-03-06
change the default document format in OpenOffice to Microsoft Office....

is it only the teachers that access teh computer? If not for the kids you might install edubuntu.

---

