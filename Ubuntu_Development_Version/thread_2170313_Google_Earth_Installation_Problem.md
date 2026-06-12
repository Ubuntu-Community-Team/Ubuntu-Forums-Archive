---
title: "Google Earth Installation Problem"
date: 2013-08-25
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-08-25
I'm running a live session of a recent daily build of Ubuntu 13.10 and i installed Google Earth to see if i could get it running...
There are many sites that tell you how to install it and i used the terminal commands it showed and supposedly the program is now installed (or so the terminal had said...lol)...
Anyway, the problem is i can't find it to open it...when i search on the dash it does not come up...This is the 64 bit version, by the way...

I've had this problem when trying to install Google earth even on previous ubuntus....seems to install fine but then cannot be located...
Any suggestions on how to find and open it?  I did this on live session because i hesitated to play with it on my currently installed ubuntu 13.04...

Thanks ;)

---

### Post by monkeybrain20122 on 2013-08-25
Hi,

If you can start it in the terminal then it is installed. I haven't tried 13.10 but I experienced the same problem in Debian Sid and I think the reason and the solution ae the same. It is simply that the .desktop file  is not copied to or linked to /usr/share/applications when you install a third party applications like GE or Chrome, you will find it in /opt/google/google-earth/ or something like that. So you either just copy the .desktop file to /usr/share/applications or make a symlink to it and you should see it in the dash. In 13.04 and before when you install a third party application like GE or Chrome the .desktop file is automatically copied to /usr/share/applications or /usr/local/share/applications. I hope this is a bug and will be fixed at release so new users don't get confused.

---

### Post by craig10x on 2013-08-25
The terminal can't seem to locate it so makes me wonder if it really got installed...Funny thing is i have had the same problem even trying to add it to previous ubuntus as well...Would be so much easier if it was actually in the software center...then at least the dash search would bring it up...

I'm going to run this live session through monday afternoon...maybe i will try installing using the deb and the ubuntu software center...though i doubt if i will have any better luck...
Does it matter which bit version you use?...64 bit was the one i tried for and used terminal commands for it...

edit: i just left clicked on the deb file in nautilus and ubuntu software center reads the package but has a message that says:
dependency is not satisfiable  ia32-libs
I did a little googling on that and apparently that was a hack that use to enable you to install a 32 bit package in 64 bit ubuntu....

Does that mean that i need to install 32 bit Google earth instead?  (I assumed the 64 bit version would work)...
If so, i will try getting the deb file from Google for 32 and see if the ubuntu software center can install it...

---

### Post by monkeybrain20122 on 2013-08-25
if you can start it with the terminal command 'google-earth' then it means it is installed
If you try to use the locate command to find stuffs you need to update your database first, because the database is updated at regular time intervals and locate would not find things that you just installed without upgrading the database. the command is 

```
sudo updatedb
```

---

### Post by craig10x on 2013-08-25
No luck...tried your ideas and 32 bit also and it was also missing something...will probably give up unless someone comes along with some other idea...
Google earth seems to be a rather frustrating problem to install on Linux...on windows and mac it is a snap...Never had a problem installing Chrome either it's just this Earth program that seems to be a pain in the rear in linux...

---

### Post by mc4man on 2013-08-25
Your best bet is to wait until google-earth redo's their package & stops requiring a now non-existent meta package (ia32-lbs) which actually used to install more than was needed anyway.

If really inclined it can be done now, just did, took a couple of minutes.

Basically you install what it does need (or at least min. to run..
```
sudo apt-get install libc6:i386 lsb-core
```

Then you take the downloaded google-earth current deb package & r. click extract. Once extracted open the extracted folder > Debian. Inside is a control file. Open it in gedit & remove the dep on ia32-libs, save. (once saved remove back up "control~" file
Then delete or move the orig. google-earth-stable_current_amd64.deb package & rebuild the edited folder with dpkg -b /path/to/extracted-folder

Ex.
I downloaded the .deb, put in a new folder called gefix. Then extracted, edited the control file, saved.
**The orig .deb I deleted**, leaving just "google-earth-stable_current_amd64" folder in gefix.


From terminal - 
> doug@doug-XPS-M1330:~/Downloads/gefix$ dpkg -b '/home/doug/Downloads/gefix/google-earth-stable_current_amd64' 
dpkg-deb: building package `google-earth-stable' in `/home/doug/Downloads/gefix/google-earth-stable_current_amd64.deb'.
doug@doug-XPS-M1330:~/Downloads/gefix$

Once the debian package is created then a simple - 
sudo dpkg -i  /home/doug/Downloads/gefix/google-earth-stable_current_amd64.deb

screen one shows all I've mentioned, screen 2 ge running on saucy 64 bit

---

### Post by craig10x on 2013-08-25
Wow...a rather complex way to get it running...Google really should get that straightened out...it should be as easy to install as the Chrome Browser...
Appreciate your post...i guess i will wait for Google to smooth this out...too much of a hassle right now ;)

---

### Post by tdockery97 on 2013-08-26
@craig10x:  The easiest way is just download the Google Earth 32bit version and install using gdebi.  Worked great on my 13.10 64bit.

---

### Post by craig10x on 2013-08-26
Really? and no dependency problems, tdockery97?  If so, thanks for the tip...i will have to try it that way and see how it goes...did it come up in the dash search for you to launch it the first time?
Thanks...:)

---

### Post by tdockery97 on 2013-08-27
> **craig10x said:**
> Really? and no dependency problems, tdockery97?  If so, thanks for the tip...i will have to try it that way and see how it goes...did it come up in the dash search for you to launch it the first time?
Thanks...:)
No dependency problems.  And yes, it showed up right away in the Dash search, upon which I moved it to the Launcher.  Good luck.

---

### Post by craig10x on 2013-08-27
I installed gdebi and downloaded the Google Earth deb file from their website...i right clicked the file and selected gdebi and it was able to find all the packages necessary....
The only problem i am having is that gdebi is asking for my password and when i type it in, it says "incorrect password"...anyone know what to do about that?
I decided to try it on my installed 13.04 but this incorrect password problem seems to be the only thing that is holding me up...

Thanks ;)

edit:  I did get it installed with the ubuntu software center, and the launcher does appear in dash search...however, it won't launch...can't get the program to open...
Software Center does show it as being installed and even though it shows in the dash, it just will not launch...:confused:

---

### Post by mc4man on 2013-08-27
> **craig10x said:**
> 

edit:  I did get it installed with the ubuntu software center, and the launcher does appear in dash search...however, it won't launch...can't get the program to open...
Software Center does show it as being installed and even though it shows in the dash, it just will not launch...:confused:

open a terminal & run google-earth
See what it says, (if anything), at the moment you can ignore any ERROR:nss_ocsp.cc* errors as they don't prevent running

( if nothing useful in terminal & using unity then after trying to start GE open ~/.cache/upstart/gnome-session.log, scroll to bottom area & see if anything related is logged.

Your issue with gdebi may be because it's using gksudo in su mode, check with 
```
gksu-properties
```
If set to su then change to sudo, if set to sudo then change to su then back to sudo

---

### Post by scouser73 on 2013-10-14
Thank you, your instructions worked perfectly.

---

### Post by doorunrun on 2013-10-17
> **mc4man said:**
> Your best bet is to wait until google-earth redo's their package & stops requiring a now non-existent meta package (ia32-lbs) which actually used to install more than was needed anyway.

If really inclined it can be done now, just did, took a couple of minutes.

Basically you install what it does need (or at least min. to run..
```
sudo apt-get install libc6:i386 lsb-core
```

Then you take the downloaded google-earth current deb package & r. click extract. Once extracted open the extracted folder > Debian. Inside is a control file. Open it in gedit & remove the dep on ia32-libs, save. (once saved remove back up "control~" file
Then delete or move the orig. google-earth-stable_current_amd64.deb package & rebuild the edited folder with dpkg -b /path/to/extracted-folder

Ex.
I downloaded the .deb, put in a new folder called gefix. Then extracted, edited the control file, saved.
**The orig .deb I deleted**, leaving just "google-earth-stable_current_amd64" folder in gefix.


From terminal - 


Once the debian package is created then a simple - 
sudo dpkg -i  /home/doug/Downloads/gefix/google-earth-stable_current_amd64.deb

screen one shows all I've mentioned, screen 2 ge running on saucy 64 bit

This procedure worked for me, thanks!!

---

### Post by David_OConnor on 2013-10-27
Thanks - this worked for me.

---

### Post by cariboo on 2013-10-27
Now that Saucy has been released, there is no need for this thread to be open. Closed

---

