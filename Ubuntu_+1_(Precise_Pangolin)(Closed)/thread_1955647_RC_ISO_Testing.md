---
title: "RC ISO Testing"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cariboo on 2012-04-09
Although there hasn't been an official RC release, we are working our way to the final release of Precise Pangolin. To that end we need as many people as possible to test the iso.

If youi aren't sure what you need to do to test the iso, effenber0x0 has created a howto located [here]("https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-main").

Testing will take place from April 9/12 - April 12.

For support, check the [U+1 Precise]("http://ubuntuforums.org/forumdisplay.php?f=412") sub-forum

or

#ubuntu-testing, on IRC

---

### Post by ventrical on 2012-04-10
Just a note: I corrected  the /paste/ code for the zsync.

Thanks Cariboo.

---

### Post by keithpeter on 2012-04-10
Hello All

How long does a complete QA test run take in a single session?

We have 256 kb/s 'broadish' band and its a quad core PC.

I'm on the road a bit today and Thursday but there is a window on Wednesday 11th for a few hours.

---

### Post by grahammechanical on 2012-04-10
@keithpeter

From my experience the issue it this:

Do you already have any of these ISO images on your hard disk? If so you can use Zsync to update the bits that are different and that is less data to download and therefore quicker than downloading a complete ISO image.

The issue is all the more significant due to the fact that there is not a fixed image to be tested. The ISO images are being altered daily.

For example, yesterday I used Zsyn to update Xubuntu amd64 & i386 to the 20120409 image but I only managed to test i386. Now I find that I need to Zsync again because the image has changed to 20120410.

There are still some 20120409 Lubuntu images but they will change to 20120410 during the day.

I have a download cap between 08:00 and 24:00. So, I do not like updating these images during the day.

The testing sessions are simple. We are testing the install process.

Does the Live session load to the desktop? Does the Live session shutdown as it should. Test Done.

There are three hard disk install tests.

a) Use Entire Disk
b) Alongside
C) Manual

It is a bit more complicated than that but as you can see, you like me, might only be able to do (c) and not (a) or (b) or you might only want to do the Live Session tests. So, the time varies and we are not on-line at the time.

Regards.

---

### Post by keithpeter on 2012-04-10
Hello Grahammechanical

OK, I thought the QA test was more involved.

I have an image I can zsysnc for Ubuntu and for Xubuntu so I'll see which one has the least tests already

Thanks

---

### Post by jerrylamos on 2012-04-10
Successful install on Acer Aspire 5253 which has a 1366x768 screen which randomly Grib2 has not been able to support.  O.K. this time, let me try an update-grub which has failed randomly to produce a legible boot screen.

Unsuccessful lubuntu 20120410 install on IBM Thinkpad R31.  Gets all the way through ubiquity stetup, about 1/3 the way through copying and the ubiquity window juist disappears.  Bug #978489.  Copying seems to go on in the background but the rest of the install is never done.

I could try unity-2D install on the R31 but it's a bit sluggish on the R31, which does have the -pae flag.  1 GHz Celeron, 512 MB, intel integrated graphics (sluggish).  Lubuntu is a better fit.

Jerry

---

### Post by misterblobby on 2012-04-11
Upgraded fine on ASUS N73J laptop with Win7 dual boot, from Ubuntu 11.10. 

Quite a few programs need to be reinstalled (VLC, GIMP, Blender....) but the installer did come up with a message saying that not all packages could be restored.

---

### Post by ventrical on 2012-04-11
The only problem I had so far on an install to an hdd from a USB was this continuous "Debconf on Desktop" window popping up when I tried to install restricted extras from software centre. Also, at first loadup on one of 2.2GHz towers there was a white square to the top LEFT hand of the screen after install. When  I installed synaptic and rebooted it was no longer there. So , for the most part it is a successful install and is working as good as beta2-dvd. Also I did a "something else" and that worked just excellent.

---

### Post by jerrylamos on 2012-04-11
Fresh install today 3.2.0-23-generic-pae got Bug #968198 gnome-settings-daemon crashed with SIGSEGV.  Seems a bunch of people are getting this.  Not a showstopper still running.

Jerry

---

### Post by treesurf on 2012-04-11
Installation from the amd64 live cd totally hung at the "Choose User" screen.  This is a known issue.  Have now successfully installed from the alternate CD.

Nice to see that Unity is improving, but the new default theme is definitely a step backwards.  What's with these ugly light right-click menus?  Overall, though, 12.04 feels much better than 11.10...and it's not even final yet!

---

### Post by Irihapeti on 2012-04-12
I did two tests. One was full-disk Ubuntu i386 desktop, which went without incident (other than a grub bug that's been bothering me for ages). The other was a full-disk Ubuntu alternate i386 install, which failed at "select and install software". Oddly enough, repeating that step manually (as recommended) caused the install to complete successfully, as far as I can tell.

I'll try again tomorrow and see what happens.

---

### Post by ventrical on 2012-04-13
Todays build  (just hot off the server) works beautifully on the USB in the 'Live' Session.  It is an "all you need" desktop experience. Nice work Mr.Shuttleworth. Unity 2D has not been left to the wayside. Something for everybody here. I am sittting here asking myself why I would want to install such a masterpiece to an hdd :):) , but I will.

Here goes ....this comming from a Gigabyte MoBo running 2.2 GHz with NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2), 1GB of DDR.

 And the audio is on by defualt with the live session.

Here goes <something else> :)

---

### Post by ventrical on 2012-04-13
Hey cool. Click on Release notes>community and Ubuntu Forums link is there!

---

### Post by ventrical on 2012-04-13
precise-desktop-i386 ....... the 12 and 1/2 minute install wonder .. :)

Nice work !

---

### Post by Miykel on 2012-04-13
G'Day;  Went to the QA site and logged into launchpad, downloaded the appropriate .iso, all good, then received email;

miykel, 

Thank you for registering at Ubuntu QA. You may now log in by clicking this 
link or copying and pasting it to your browser: 

[http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY](http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY) 

This link can only be used once to log in and will lead you to a page where 
you can set your password. 

After setting your password, you will be able to log in at 
[http://iso.qa.ubuntu.com/user](http://iso.qa.ubuntu.com/user) in the future using: 

username: miykel 
password: Your password 

--  Ubuntu QA team 

Went to top link and told "access Denied" , went to bottom link and launchpad login password was not accepted ???
Regards Miykel

---

### Post by cariboo on 2012-04-13
> **Miykel said:**
> G'Day;  Went to the QA site and logged into launchpad, downloaded the appropriate .iso, all good, then received email;

miykel, 

Thank you for registering at Ubuntu QA. You may now log in by clicking this 
link or copying and pasting it to your browser: 

[http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY](http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY) 

This link can only be used once to log in and will lead you to a page where 
you can set your password. 

After setting your password, you will be able to log in at 
[http://iso.qa.ubuntu.com/user](http://iso.qa.ubuntu.com/user) in the future using: 

username: miykel 
password: Your password 

--  Ubuntu QA team 

Went to top link and told "access Denied" , went to bottom link and launchpad login password was not accepted ???
Regards Miykel

The link is a time limited, did you perhaps wait to long? The QA team won't allow you to use your Launchpad id, As far as I'm concerned, that's something that needs to be fixed.

---

### Post by ventrical on 2012-04-13
> **Miykel said:**
> G'Day;  Went to the QA site and logged into launchpad, downloaded the appropriate .iso, all good, then received email;

miykel, 

Thank you for registering at Ubuntu QA. You may now log in by clicking this 
link or copying and pasting it to your browser: 

[http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY](http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY) 

This link can only be used once to log in and will lead you to a page where 
you can set your password. 

After setting your password, you will be able to log in at 
[http://iso.qa.ubuntu.com/user](http://iso.qa.ubuntu.com/user) in the future using: 

username: miykel 
password: Your password 

--  Ubuntu QA team 

Went to top link and told "access Denied" , went to bottom link and launchpad login password was not accepted ???
Regards Miykel


me too ... same thing..

---

### Post by Miykel on 2012-04-13
G'day;  Thanks for the reply, I clicked on the link within a minute of receiving the email.
Regards Miykel

---

### Post by Doug S on 2012-04-13
> **Miykel said:**
> G'Day; Went to the QA site and logged into launchpad, downloaded the appropriate .iso, all good, then received email;
 
miykel, 
 
Thank you for registering at Ubuntu QA. You may now log in by clicking this 
link or copying and pasting it to your browser: 
 
[http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY](http://iso.qa.ubuntu.com/user/reset/29627/1334304080/DYo504RLI6pgujNDoBKLKBVzSGRaxg0E9kJos6U9qLY) 
 
This link can only be used once to log in and will lead you to a page where 
you can set your password. 
 
After setting your password, you will be able to log in at 
[http://iso.qa.ubuntu.com/user](http://iso.qa.ubuntu.com/user) in the future using: 
 
username: miykel 
password: Your password 
 
-- Ubuntu QA team 
 
Went to top link and told "access Denied" , went to bottom link and launchpad login password was not accepted ???
Regards Miykel
It was the same with me on February 29th. And I was within minutes of getting the e-mail, as far as I recall. I gave up and seem to be able to do what I need to using my launchpad ID. (All I do is enter test results into the qa tracker thing).
 
Edit: I actually think it might have worked properly, even though all indications were that it did not. Sorry, It was a while ago and I don't recall clearly.

---

### Post by Miykel on 2012-04-14
G'day; I'm not sure if I've pulled a clanger, is the RC version of Ubuntu still called   Ubuntu 12.04 LTS ???
Regards Miykel

---

### Post by josephmills on 2012-04-14
Im on it sounds fun ! Love testing

---

### Post by andrewabc on 2012-04-14
> **Miykel said:**
> G'day; I'm not sure if I've pulled a clanger, is the RC version of Ubuntu still called   Ubuntu 12.04 LTS ???
Regards Miykel

Not sure on exact question.

But yes there is no official RC, so what you have running should only say "ubuntu 12.04 LTS". It shouldn't say beta/rc or anything.

---

### Post by Miykel on 2012-04-14
Thanks for the reply Andrewabc, thats exactly what I was wanting to know.

Is anyone else having trouble installing Java ??, I've tried the terminal and the update manager but java will not install, always end up with error 1, tried the codes here;

  [http://ubuntuforums.org/showthread.php?t=1956559](http://ubuntuforums.org/showthread.php?t=1956559)

but nothing works.
any thoughts would be appreciated
Regards Miykel

---

### Post by misterblobby on 2012-04-15
Open-jre installed without incident for me, but I had to install Sun Java anyway due to kids playing minecraft. 

I did it from here: [http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en), which I found on another forum somewhere.

---

### Post by ventrical on 2012-04-15
Todays build , Apr. 15/2012 worked (installed)flawlessly from USB install on a P4M266A-8273, 2.8GH Dual Core with 512 DDR and  01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
w 4oGB WD

---

### Post by sudodus on 2012-04-16
This should be useful for you, who download the daily builds to test Ubuntu +1. I made a small shell-script that uses dd to clone the iso file and makes it safer and more convenient to transfer the daily build from the iso file to the USB pendrive.

The first time you have to do a little manual work, but there is help to decrease the risks with dd. The next daily builds will automatically select the correct USB drive. See this link

[[COLOR="Red"]_http://Howto make USB boot drives_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by ventrical on 2012-04-16
Install Ubuntu is a One Shot Deal on the recent daily builds with persistive file from USB to HDD. Once a user name and password are entered in, this is carried over  when trying to use the USB stick on another PC. It will not clear the username and even when you clear in manually the install will fail (even with option <somthing else>). It tries to import other user files after choosing (Install Ubuntu-Erase Entire Disk) option. It notifies you that the installation was complete and asks you to restart. Then , after restart , blank screen . no  terminal , no grub - shift key does not work.

Work around:  Use starup disk creator to overwrite the USB and do not choose persistive file or, choose persitive file  with option of having to reinstall .ISO for next install.

---

### Post by ventrical on 2012-04-16
The below option worked better and I got a good install on Dell Dimension 3100. There was also a GRUB problem . That Dell PC has a SATA drive in it and I installed  a 3oGB Maxtox for testing purposes and disabled the SATA in BIOS. However , Ubiquity still recognized that drive as a primary drive and so each time with "Install Ubuntu" it would go first to SATA drive. By clicking display bar , choose Maxrtor 30GB. Install would crash. SATA has to be physically unhooked from power.

 But I had the above mentioned bug on another machine with it crashing after it was not able to import files from other operating system when using "Install Ubuntu" from the live CD .. So I did this:

---

### Post by sudodus on 2012-04-16
Hi ventrical,

I have done as suggested in the Desktop Test Case - Live Session chapter, and selected to make a casper-rw partition on the HDD. It will not disturb the behaviour of the live sessions or installations. I activate persistence temporarily adding persistent to the boot command line.

Of course, this is something different than having a portable persistent live system. I have also tested with unetbootin, to enter persistent to the first menu entry, but not to the second one, to have a choice between persistence and 'regular volatile' USB live booting with a casper-rw file on the pendrive.

*Edit: Maybe I misunderstood: Are you describing something that used to work, but has stopped working now because of a new bug?*

---

### Post by ventrical on 2012-04-16
> **sudodus said:**
> Hi ventrical,

I have done as suggested in the Desktop Test Case - Live Session chapter, and selected to make a casper-rw partition on the HDD. It will not disturb the behaviour of the live sessions or installations. I activate persistence temporarily adding persistent to the boot command line.

Of course, this is something different than having a portable persistent live system. I have also tested with unetbootin, to enter persistent to the first menu entry, but not to the second one, to have a choice between persistence and 'regular volatile' USB live booting with a casper-rw file on the pendrive.

*Edit: Maybe I misunderstood: Are you describing something that used to work, but has stopped working now because of a new bug?*

Hi Sudodus,

 Yes, I believe it is an new bug because I did not have it before. Beta2-dvd.ISO worked great. Then I started to zsync  the .iso files.  That worked until yesterday when I zsynced the last .iso to current and that bug has carried over. it is only when I try to install it a second time that the bug comes up. Now, after choosing  the option to discard , the problem has gone, but I can still use the Live  USB if I wish also.

    I haven't filed a bug for this yet because I just haven't had the time.. so if somebody picks up on it (or mabey it is not a bug) then I though I would just post it. The only reason I posted it is because it failed 4 times on two different machines with different hdds.

  I'm testing 9 different units.

---

### Post by sudodus on 2012-04-16
> **ventrical said:**
> Hi Sudodus,

 Yes, I believe it is an new bug because I did not have it before. Beta2-dvd.ISO worked great. Then I started to zsync  the .iso files.  That worked until yesterday when I zsynced the last .iso to current and that bug has carried over. it is only when I try to install it a second time that the bug comes up. Now, after choosing  the option to discard , the problem has gone, but I can still use the Live  USB if I wish also.

    I haven't filed a bug for this yet because I just haven't had the time.. so if somebody picks up on it (or mabey it is not a bug) then I though I would just post it. The only reason I posted it is because it failed 4 times on two different machines with different hdds.

  I'm testing 9 different units.
I'm focusing on Lubuntu i386, and I can check if I'm getting the same problem soon with a used casper-rw file or partition on the USB drive.

---

### Post by ventrical on 2012-04-16
> **sudodus said:**
> I'm focusing on Lubuntu i386, and I can check if I'm getting the same problem soon with a used casper-rw file or partition on the USB drive.

Thanks.

---

### Post by sudodus on 2012-04-16
> **ventrical said:**
> Install Ubuntu is a One Shot Deal on the recent daily builds with persistive file from USB to HDD. Once a user name and password are entered in, this is carried over  when trying to use the USB stick on another PC. It will not clear the username and even when you clear in manually the install will fail (even with option <somthing else>). It tries to import other user files after choosing (Install Ubuntu-Erase Entire Disk) option. It notifies you that the installation was complete and asks you to restart. Then , after restart , blank screen . no  terminal , no grub - shift key does not work.

Work around:  Use starup disk creator to overwrite the USB and do not choose persistive file or, choose persitive file  with option of having to reinstall .ISO for next install.

I have tried something similar and my results are somewhat similar. Let's try to interpret what is happening.

I made the USB install drive with gparted and unetbootin. Instead of a casper-rw file I made a casper-rw partition. I had used it, so that it was not identical to the original install drive (only squashfs from the iso file). I ran it with persistence on an IBM thinkpad t41 single 32-bit cpu without pae, and then on an HP xw8400 workstation with 2x2 xeon 64-bit cpus. Also the graphics are very different.

1. It was possible to install the second time, the result was a working system (apparently different result from yours).

2. But the result was different from the result, when installing from the same iso file without stored results in the casper-rw partition (similar result to yours).

- The graphics was not identified as well, but defaulted to 1024x768, and I had to install a proprietary nvidia driver to get beyond that. (Without persistence, full graphics was installed directly.) I think this corresponds to your totally broken system, maybe the difference between the results is due to the different pairs of computers in the test.

- I had installed htop in the persistent system, and it was automatically transferred to the installed system. I guess this corresponds to your problem with custom users.

My conclusion is that we should switch off the persistence when installing from the USB drive. It works by removing the word *persistent* from the boot command line. The persistence disappears and *I have now checked* that the installer does not use the casper-rw data, and I have verified the different results with and without persistence.

What do you think?

---

### Post by ventrical on 2012-04-16
I have a screenshot below of how the Precise Beta2 was laid except it is Precise beta1. I used the same method as I had mentioned earlier, the Startup Disk Creator and Brasero when needed. Statrtup Disk Creator is used for making USB  pendrives (as you know). I have always chosen the "Stored in reserved extra space" option and have not had problems like this before. This will create a persistive drive which you can create accounts on, etc.  The thing is , is that when  I am doing an <Install Ubuntu> from the Opening Ubiquity screen it will ask  for whereabouts, keyboard, name and password. It will also assign a name to the computer. Still follow me ?  

 So the <Install Ubuntu> completes (no updates-no third party drivers) successfully.  Then I close that system down and take the thumbdrive to another PC (or I will use the same PC but just switch  to a different hdd) and when  it gets to the stage of asking me for  my name and password it is already presenting me with the name I used on the previous install.

Enter Name-John Doe (already there)
ComputerName - myalreadynamedPC
RealName -John Doe (already there)



 I have allowed this and have tried to change this (even have used (something else) and reformatted the drive [Erase and Install to HardDisk]) but it will still fail .. it will erroneously tell me that  the install has been successful and I need to restart. Following all successful past installs , but this time it fials .. no terminal., no x, no <SHIFT<SHIFT> GRUB .. just a blinking cursor. So then I bring the disk back to my Dell and then use Startup Disk Creator to overwrite and the file Install pendrive is good to go. However, I found using "Discard on shutdown, unless you use them elsewhere" is the best way to save downtime in this situation.

 Now... to verifiy it is not something buggy  with my pendrive  or PC I am going to  copy the current ISO to another PC and then go from there, but this Dell has been very reliable so far.

  What I think? I think there are still some real, honest bugs with the Ubiquity Installer , but they are very hard to validate and authenticate .

  So _if_ you are trying to duplicate the bug THEN download the precise-desktop-i386.iso  (or zsync it) THEN use Startup Disk Creator and choose "stored in Reserved extra space option".  (be careful because there seems to be another bug with Startup Disk Creator because when it is ready to install the GRUB bootloader it will ask for  your password. If you wait too long to enter the password it will crash.. so you have to babysit it a bit).

  After this is done then  pick one of your PCs and  install Precise .iso  to an hdd.  Use <Install Ubuntu/Erase and Use entire Disk>. It should install seamlessly.  Then, get another hdd and stick that one on there and  boot the USB again and install it  to the other hdd (or use a different PC) with different hdd) and then report please.

---

### Post by ventrical on 2012-04-16
screenshot:

---

### Post by ventrical on 2012-04-16
sheesh :)

screenshot doh!

---

### Post by ventrical on 2012-04-16
Here is the "Discard on shutdown , unless you use them elsewhere" option from Startup Disk Creator file directory , beta2daily-zsync build.

---

### Post by ventrical on 2012-04-16
> **sudodus said:**
> 

My conclusion is that we should switch off the persistence when installing from the USB drive. It works by removing the word *persistent* from the boot command line. The persistence disappears and *I have now checked* that the installer does not use the casper-rw data, and I have verified the different results with and without persistence.

What do you think?

 I agree with this and thanks for your hard work and response. Although I must say I am concerned about if this bug gets rolled out with the final. So , a teacher, for instance, takes his freshly created USB drive and goes forward to populate a network of PCs  only to fine that it is only good for one shot from the standard persitsive drive.  I must apologize for my boldness..as I should further validate  and document my assumptions here before declaring that there is a definitive bug.

---

### Post by sudodus on 2012-04-16
> **ventrical said:**
> ... The thing is , is that when  I am doing an <Install Ubuntu> from the Opening Ubiquity screen it will ask  for whereabouts, keyboard, name and password. It will also assign a name to the computer. Still follow me ?  

 So ... when  it gets to the stage of asking me for  my name and password it is already presenting me with the name I used on the previous install.

Enter Name-John Doe (already there)
ComputerName - myalreadynamedPC
RealName -John Doe (already there)

... However, I found using "Discard on shutdown, unless you use them elsewhere" is the best way to save downtime in this situation.
I think I understand. "Discard on shutdown..." means no casper-rw file, no persistence, so nothing is remembered until next boot.
> 
 Now... to verifiy it is not something buggy  with my pendrive  or PC I am going to  copy the current ISO to another PC and then go from there, but this Dell has been very reliable so far.

  What I think? I think there are still some real, honest bugs with the Ubiquity Installer , but they are very hard to validate and authenticate .

I'm almost 100% sure your pendrive and computer are OK. This is the behaviour of the installer. It uses 'persistent' information. The question is, if it should or not: is it a bug, or is it an intended feature to allow people to customize the installations? I agree that it is kind of funny to prompt with the same name on different computers :p Other things, like installed software, language and time-zone are more reasonable to remember for customization.
> 
  So _if_ you are trying to duplicate the bug THEN download the precise-desktop-i386.iso  (or zsync it) THEN use Startup Disk Creator and choose "stored in Reserved extra space option".  (be careful because there seems to be another bug with Startup Disk Creator because when it is ready to install the GRUB bootloader it will ask for  your password. If you wait too long to enter the password it will crash.. so you have to babysit it a bit).

From the screenshots I guess you are installing vanilla Ubuntu. Which Startup Disk Creator are you running (belonging to which Ubuntu version)?
> 
  After this is done then  pick one of your PCs and  install Precise .iso  to an hdd.  Use <Install Ubuntu/Erase and Use entire Disk>. It should install seamlessly.  Then, get another hdd and stick that one on there and  boot the USB again and install it  to the other hdd (or use a different PC) with different hdd) and then report please.

I'm in Europe and need some sleep now. I hope to get some time tomorrow.

---

### Post by ventrical on 2012-04-17
"From the screenshots I guess you are installing vanilla Ubuntu. Which  Startup Disk Creator are you running (belonging to which Ubuntu  version)?"

  I am using Stable Oneiric 11.10 on Dell Optiplexgx270, 2.8GHz,1GBddr.

  Hmmm.. I am going to try Maveric on another machine and see what happens.

5:30 am here .. must be tea time in England :)

---

### Post by sudodus on 2012-04-17
> **ventrical said:**
> "From the screenshots I guess you are installing vanilla Ubuntu. Which  Startup Disk Creator are you running (belonging to which Ubuntu  version)?"

  I am using Stable Oneiric 11.10 on Dell Optiplexgx270, 2.8GHz,1GBddr.

  Hmmm.. I am going to try Maveric on another machine and see what happens.

5:30 am here .. must be tea time in England :)
Things are changing. I updated the iso file to the current version, and did something that is at least rather close to what you want. For some reason the start-up disk creator of Ubuntu 10.04 LTS failed to make a bootable USB drive, so I went back to unetbootin.

I had persistence switched on, and did two installs, one at the first boot with the USB drive, and one after rebooting and checking that commands etc were remembered in the terminal window (bash history).

1. There was no issue with graphics this time.

2. I had installed htop into the live system, but it was not transferred to the installed system.

3. But I had the same behaviour as you described with user name and computer name. Furthermore the language and time-zone were also remembered and transferred.

So I think someone has debugged the code, and I have a feeling that the user & locale transfer is intentional. I'm thinking of a company or institution, where the user names and computer names are alphanumeric, so you only 'add one', for example
user0007 --> user0008
pc0003 --> pc0004
I realize that many companies would prefer to install and maintain its computer software via the network, so I don't really know.

By the way, I like tea and drink most of it in Sweden :-)

---

### Post by ventrical on 2012-04-17
I copied the .iso to another system with precise .23 and used startup disk creator on that.

 I got the same error with SDC  that I did with Oneiric.  I did successfully install it .. however .. I have a meeting right now and will post the rest of those results later.

Here is one of the bugs I am planning to file:

---

### Post by ventrical on 2012-04-17
Ok.. that bug was solved, There must be a problem with  Start-up Disk Creator on Oneiric Ocelot. All is working well with persitive here, this USB disk created with Precise beta-daily, Startup Disk Creator.Intell MoBo.

However . the name and stats still appear from the last install.

---

### Post by sudodus on 2012-04-17
> **ventrical said:**
> ... However . the name and stats still appear from the last install.

OK, who can tell if it is supposed to be like this?

---

### Post by nm_geo on 2012-04-17
> **sudodus said:**
> OK, who can tell if it is supposed to be like this?

I have encountered the exact things you are talking about in my precise iso-testing.

!) Startup Disk Creator -I can get the USB written with persistence in Lucid 10.04 but it never shows to be finished. Appears to stop at 99% 

2) Startup Dsk Creator in Precise Lubuntu 12.04 -  I have now started to use this one as it always finishes cleanly and I also get the notification when I choose to Erase the USB.  I believe it is just a timing issue, and the erase completes everytime.

3) Installing the iso to HDD from persistent USB. The locale is known because I am using a persistent USB. If the iso install is an Along Side or Manual and I have already completed an entire disk install the network, computer name and user do default from the first installed sda1 install Yes.

4) Just in case I encounter a critical bug during the install I always use the word **_test_** for network, computer name, user and password.  It does tell me the password is to short but let's me continue.  That way I never worry about security issues when sending information to launchpad.

5) Most of my installs are done on a Dell D620 laptop and I have that infamous b43 driver.  I do not like to connect to an ethernet cable (wrong room I like to work on my soft bed) :p.  So I have the b43 firmware folder saved on another USB and just open it save it to Desktop. Then ```
cd Desktop
sudo mv b43 /lib/firmware
```Wifi light comes on and I connect to my network ddwrt wireless router.
Sometimes I do not even have to put in the WPA phase.. It just picks up and goes. After the install completes I do that same process to get wireless working in the new install for internet and iso-tracker.
Saves me time

6) I have three HDD all the same brand and size. One is dedicated strictly for testing isos and I can change HDD out in about 2 minutes  lots of practice.

7) When I do not need a persistent USB I use the dd command to write my USBs typically in 3 to 4 minutes they are ready to use.

Just some random information and techniques that your thread made me think of.

---

### Post by ventrical on 2012-04-17
Thanks for sharing your experience on this. I had assumed it was a critical bug. It is odd , however, that I was able to use Startup Disk Creator to create a USB on the same Dell OptiplexGX270 without any  of the errors that I have had been having with the daily zsynced RCs.

 I am tempted to try to duplicate this bug using precise-desktop-i386.iso.zs-old.

hmmmm... anyways the installs are getting faster! :)

---

### Post by nm_geo on 2012-04-17
> **ventrical said:**
> Thanks for sharing your experience on this. I had assumed it was a critical bug. It is odd , however, that I was able to use Startup Disk Creator to create a USB on the same Dell OptiplexGX270 without any  of the errors that I have had been having with the daily zsynced RCs.

 I am tempted to try to duplicate this bug using precise-desktop-i386.iso.zs-old.

hmmmm... anyways the installs are getting faster! :)

If you are talking about the Start-up Creator notification that you took the snap shoot of I would say it is not critical, but you may be speaking of another bug.  I do get that notification on a precise amd64 installation that I have kept on my production drive when I erase the USB. 

 However it does continue and does erase the data on the USB so I just ignore it.  I would guess you would report that notification bug on the project or application. That package is not even included in the Lubuntu Desktops amd64 or i386.. I just installed it because it is a easy path for me to create persistent USBs.

I typically am looking for kernel and iso failure Bugs at least right now in the testing process.

---

### Post by jerrylamos on 2012-04-17
12.04 Xubuntu 20120416 install got an "internal error"

so it automatically started a terminal session.  So I did:

xubuntu@xubuntu:~$ ubuntu-bug ubiquity
xubuntu@xubuntu:~$ Error: No running window found


?  Obviously it's in a terminal session which is running, what does "No running window found" mean?

Any clue?  How do I file a bug on that, there's two bugs now?

Thanks, Jerry

---

### Post by sudodus on 2012-04-17
> **ventrical said:**
> Thanks for sharing your experience on this... :)
+1
*@nm_geo*

It's a nice feeling, that other people are also concerned :-)

---

### Post by ventrical on 2012-04-17
> **jerrylamos said:**
> 12.04 Xubuntu 20120416 install got an "internal error"

so it automatically started a terminal session.  So I did:

xubuntu@xubuntu:~$ ubuntu-bug ubiquity
xubuntu@xubuntu:~$ Error: No running window found


?  Obviously it's in a terminal session which is running, what does "No running window found" mean?

Any clue?  How do I file a bug on that, there's two bugs now?

Thanks, Jerry

Honestly , i can't find anything comprehensive on that one.

err I'm just curious .... to use my old .iso (precise-desktop-i386.iso.zs.old) would I just have to rename it?

---

### Post by sudodus on 2012-04-18
> **ventrical said:**
> Honestly , i can't find anything comprehensive on that one.

err I'm just curious .... to use my old .iso (precise-desktop-i386.iso.zs.old) would I just have to rename it?
I guess that would make the usb disk creator recognize it, or even better, make a hard link, for example
```
ln precise-desktop-i386.iso.zs.old old.iso
```

---

### Post by philinux on 2012-04-18
[http://iloveubuntu.net/ubuntu-1204s-rc-iso-call-testing](http://iloveubuntu.net/ubuntu-1204s-rc-iso-call-testing)

[https://lists.ubuntu.com/archives/ubuntu-release/2012-April/001083.html](https://lists.ubuntu.com/archives/ubuntu-release/2012-April/001083.html)
> 4/19 - release candidate creation.  
     - only fixes explicitly requested by release team for 
       seeded images and only those fixes that won't work as 
       SRUs will be considered.

---

### Post by ventrical on 2012-04-19
The final  RC for  Apr.19th just came in about an hour ago. Already zsynced here!

Off and testing.

Have a great testers day everyone ! :)

---

### Post by ventrical on 2012-04-19
From a fresh burn to a USB stick of Apr.19/2012 to GigabyteMoBo with maxtor 30GB hdd <erase entire disk> w 40GB WD on the side.

Error: No such device <verbose>

Grub Rescue>

This is one of my most reliable machines.

---

### Post by ventrical on 2012-04-19
This message from a live session on a CD of the same :
precise-desktop-i386.iso

 It crammed on to a CD but Brasero would not report a checksum but did make a successful burn and the CD would not eject manual , only after reboot.

---

### Post by ventrical on 2012-04-19
Grub Rescue CD saved the day and I got my Grub Menu back on the WD40GBhdd but lost the 30GB maxtorhdd.

 I will try a Something Else install with with the CD.

 hehe This is beta testing after all :)

*EDIT*

This was a total failure. The CD installed the RC flawlessly  <assumedly>. The kernel was then not registered with the other previously installed kernels of Precise and Oneiric.  I then was able to sudo update-grub from sda0 and the new kernel was recognized and registered by grub. Upon restart and choosing the above  said precise kernel an error was presented, "kernel must be loaded first , press any key to continue"

Next will try <Install Ubuntu> from CD

---

### Post by andrewabc on 2012-04-19
Anyone know when lubuntu RC out? I assume not going to be called RC in /releases, but just show up in /daily-live?

[http://cdimage.ubuntu.com/lubuntu/daily-live/](http://cdimage.ubuntu.com/lubuntu/daily-live/)
18 is last day, so I'll wait for 19.

Plan on liveusb, so want actual RC to test (no upgrading/updating of files).

---

### Post by sudodus on 2012-04-19
> **ventrical said:**
> Grub Rescue CD saved the day and I got my Grub Menu back on the WD40GBhdd but lost the 30GB maxtorhdd.

 I will try a Something Else install with with the CD.

 hehe This is beta testing after all :)
Yeah, indeed ;-) Did you check the md5sum?

The old mplayer2 crash bug for 32-bit computers is still there in Lubuntu (in the daily build day before RC). Otherwise I'm quite happy with Lubuntu :KS

Now I am waiting for the Lubuntu RC ...

---

### Post by ventrical on 2012-04-19
> **sudodus said:**
> Yeah, indeed ;-) Did you check the md5sum?

The old mplayer2 crash bug for 32-bit computers is still there in Lubuntu (in the daily build day before RC). Otherwise I'm quite happy with Lubuntu :KS

Now I am waiting for the Lubuntu RC ...


The USB came up ok (which failed) but the CD -Burn did not produce a checksum (as previously mentioned).

  I then tried again using the Installer from the Unity Launcher, then <Install Ubuntu> and got this on restart:

EDIT: Now going to try <Something Else> with USB key.

---

### Post by ventrical on 2012-04-19
I tested the USB again , no errors found.
Tested CD : No errors found.

---

### Post by ventrical on 2012-04-19
Trying no=modeset of 2 different machines.

*edit*

Nope .. nada .. no luck today.

I'll try to burn a USB non-persistive.

---

### Post by ventrical on 2012-04-19
Ok... success with the CD!!   I had a late bloomer working here. The new RC will install seamlessly , but only with one drive, not with multiple drives. Seems all of a sudden that there is a  huge problem with GRUB when installing to a system with multiple drives.

  I'll try the usb on the same system.

---

### Post by ventrical on 2012-04-19
This bug us now back .. all of a sudden.

[http://ubuntuforums.org/showpost.php?p=11847820&postcount=27](http://ubuntuforums.org/showpost.php?p=11847820&postcount=27)

---

### Post by sffvba[e0rt on 2012-04-19
Question - This ISO testing here, is it the same one that is currently happening [here?]("http://www.jonobacon.org/2012/04/17/adopt-an-iso/")


404

---

### Post by ventrical on 2012-04-19
Ok .. I finally got the bug report. What a tough nut to crack!

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/985783](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/985783)

---

### Post by sudodus on 2012-04-19
Today's daily build of Lubuntu is available now !

---

### Post by ventrical on 2012-04-19
> **not found said:**
> Question - This ISO testing here, is it the same one that is currently happening [here?]("http://www.jonobacon.org/2012/04/17/adopt-an-iso/")


404

 We are now testing the Pre-release at : [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

I apologize if this is off topic but since the bug (just reported) has migrated from beta2 to the pre-release then I thought perhaps it was still on topic?

---

### Post by ventrical on 2012-04-19
> **sudodus said:**
> I have tried something similar and my results are somewhat similar. Let's try to interpret what is happening.

I made the USB install drive with gparted and unetbootin. Instead of a casper-rw file I made a casper-rw partition. I had used it, so that it was not identical to the original install drive (only squashfs from the iso file). I ran it with persistence on an IBM thinkpad t41 single 32-bit cpu without pae, and then on an HP xw8400 workstation with 2x2 xeon 64-bit cpus. Also the graphics are very different.

1. It was possible to install the second time, the result was a working system (apparently different result from yours).

2. But the result was different from the result, when installing from the same iso file without stored results in the casper-rw partition (similar result to yours).

- The graphics was not identified as well, but defaulted to 1024x768, and I had to install a proprietary nvidia driver to get beyond that. (Without persistence, full graphics was installed directly.) I think this corresponds to your totally broken system, maybe the difference between the results is due to the different pairs of computers in the test.

- I had installed htop in the persistent system, and it was automatically transferred to the installed system. I guess this corresponds to your problem with custom users.

My conclusion is that we should switch off the persistence when installing from the USB drive. It works by removing the word *persistent* from the boot command line. The persistence disappears and *I have now checked* that the installer does not use the casper-rw data, and I have verified the different results with and without persistence.

What do you think?

I was able to log onto the iso tracker and both ubiquity and casper are reported as 'affected' and I was able to successfully report at least one bug anyways, the one that I had thought was a non bug is back.

whew !

---

### Post by sffvba[e0rt on 2012-04-19
> **ventrical said:**
> We are now testing the Pre-release at : [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

I apologize if this is off topic but since the bug (just reported) has migrated from beta2 to the pre-release then I thought perhaps it was still on topic?

K Cool... then I am also helping with this (busy testing on the 64-bit WUBI track) :) (I think, all this is very new to me)


404

---

### Post by ventrical on 2012-04-19
> **not found said:**
> K Cool... then I am also helping with this (busy testing on the 64-bit WUBI track) :) (I think, all this is very new to me)


404

That makes two of us .. :)

---

### Post by sudodus on 2012-04-19
> **ventrical said:**
> I was able to log onto the iso tracker and both ubiquity and casper are reported as 'affected' and I was able to successfully report at least one bug anyways, the one that I had thought was a non bug is back.

whew !
I have reported some testcases for today's daily build (=RC?) of Lubuntu at
[[COLOR="Red"]*http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15709/testcases/*[/COLOR]]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15709/testcases/")

I think we have (or at least focus on) different issues.

---

### Post by grahammechanical on 2012-04-19
I am testing the upgrade path. Here is a weird thing:

When I upgrade a default 10.04 to 12.04 the menus for applications stay in the application's window in a panel immediately under the window's top panel . They do not move into the top panel (global menu) as they are supposed to do.

I do not like to think of this as a bug. It might be something that 10.04 users would prefer. Maybe it is intentional.

Regards.

---

### Post by cariboo on 2012-04-19
> **grahammechanical said:**
> I am testing the upgrade path. Here is a weird thing:

When I upgrade a default 10.04 to 12.04 the menus for applications stay in the application's window in a panel immediately under the window's top panel . They do not move into the top panel (global menu) as they are supposed to do.

I do not like to think of this as a bug. It might be something that 10.04 users would prefer. Maybe it is intentional.

Regards.

I'd report the problem, if it is supposed to be that way, it will be marked invalid.

---

### Post by sudodus on 2012-04-20
> **grahammechanical said:**
> I am testing the upgrade path. Here is a weird thing:

When I upgrade a default 10.04 to 12.04 the menus for applications stay in the application's window in a panel immediately under the window's top panel . They do not move into the top panel (global menu) as they are supposed to do.

I do not like to think of this as a bug. It might be something that 10.04 users would prefer. Maybe it is intentional.

Regards.
Interesting ;-)

---

### Post by ventrical on 2012-04-20
> **sudodus said:**
> I have reported some testcases for today's daily build (=RC?) of Lubuntu at
[[COLOR=Red]*http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15709/testcases/*[/COLOR]]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15709/testcases/")

I think we have (or at least focus on) different issues.

 I just discovered that one of my Maxtor drives is not reporting in a reliable way because it failed on two machines and it is fairly new. So often in the past I have been through the squirell cage of trying to test software when all of the time  it has been the hardware that has been the culprit. The bug I reported is legitimate but it helps having verifyable working hardware.

  I remember a specific case several years ago with a malware removal problem.  It was a study case  and , in the end, it turned out to be a faulty ATI video adapter card that was actually emulating a malware like activity.

  I had a case yesterday where all of a sudden my USB key was not working on one of my test machines. I had pulled the Maxtor drive and tried a dry-start from USB with no hdd. Some motherboard will not boot up from USB unless there is an hdd connected. I of all people should know better .. but for a brief instance I assumed that I blew out the USB data pump on board. Not so.

  So I'm just making a note that half of the work involved in testing is ensuring that we have reliable hardware working reliably .

---

### Post by ventrical on 2012-04-20
> **grahammechanical said:**
> I am testing the upgrade path. Here is a weird thing:

When I upgrade a default 10.04 to 12.04 the menus for applications stay in the application's window in a panel immediately under the window's top panel . They do not move into the top panel (global menu) as they are supposed to do.

I do not like to think of this as a bug. It might be something that 10.04 users would prefer. Maybe it is intentional.

Regards.

I feel the same way here.. I really do not like to flag bugs .. I always want to give the benefit of doubt  to the program and look for something else.  I have yet to try this migration.

---

### Post by sudodus on 2012-04-20
Today's harvest contains the same old bugs, but nothing new is broken.

[[COLOR="Red"]_http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15752/testcases/1145/_[/COLOR]]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15752/testcases/1145/")

I keep testing the lubuntu desktop i386 iso. I have a general question: if the tasks of the testcase works, should I report success, even if I know about bugs, and find them easily running 'live and/or installed'? In other words, is it meaningful to nag about bugs?

---

### Post by nm_geo on 2012-04-20
> **sudodus said:**
> Today's harvest contains the same old bugs, but nothing new is broken.

[[COLOR="Red"]_http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15752/testcases/1145/_[/COLOR]]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15752/testcases/1145/")

I keep testing the lubuntu desktop i386 iso. I have a general question: if the tasks of the testcase works, should I report success, even if I know about bugs, and find them easily running 'live and/or installed'? In other words, is it meaningful to nag about bugs?

Here is the way I look at it when doing iso-testing.  If the iso installs and works then I see that as successful. Now, if I encounter a Bug on one of the applications I file a Bug against the application, and IMHO they are typically not critical as far as the iso install.

Now I get a kernel or Ubiquity Bug that causes the install to crash those I will always mark as critical. Just my thoughts.

---

### Post by jerrylamos on 2012-04-21
> **nm_geo said:**
> Here is the way I look at it when doing iso-testing....Now I get a kernel or Ubiquity Bug that causes the install to crash those I will always mark as critical. Just my thoughts.
On my 2005 Thinkpad R31 1 Ghz 512 MB, Precise B2 won't install.  I've tried Lubuntu first, then Xubuntu, Ubuntu and all fail in the copy files step. There's bugs written - it's a showstopper. Should be marked critical??  I've Lubuntu running on this 2006 Thinkpad T40 Pentium M O.K.

There's another partition Lubuntu Alpha installed on the R31 and is running O.K., a bit sluggish.  It's had thousands of "updates".

Do note, on the R31 the latest Mint 12 LXDE installed perfectly and runs perfectly, nice and fast and polished. Beautiful (in the eyes of the beholder).  If Precise is never fixed Mint will do fine.  It's based on Oneiric I think.

Jerry

---

### Post by sudodus on 2012-04-21
It is strange, that it fails in the copy files step. That should be simple. Could it be lack of memory? Would it be worth trying to install directly without starting the whole desktop, or trying with the alternate install on the R31?

---

### Post by sudodus on 2012-04-21
> **nm_geo said:**
> Here is the way I look at it when doing iso-testing.  If the iso installs and works then I see that as successful. Now, if I encounter a Bug on one of the applications I file a Bug against the application, and IMHO they are typically not critical as far as the iso install.

Now I get a kernel or Ubiquity Bug that causes the install to crash those I will always mark as critical. Just my thoughts.

Thanks, I'll follow those guidelines.

---

### Post by spsf on 2012-04-21
Asus Notebook, if I suspend the machine freezes completely... power button does not work (even long press for >15secs), it is necessary to remove the battery to shutdown the computer...
Besides this problem it works fine

---

### Post by sudodus on 2012-04-24
I am right now testing 'Live Session in Lubuntu Desktop i386 for Precise Pre-release'

IBM Thinkpad T41:

The testcase works including persistence. But I found a weird bug:
```
sudo blkid
``` works in volatile mode, but it hangs (nothing happens until I press ctrl c) in persistent mode after one or several reboots, so it seems to be consistent.

HP xw8400:

```
sudo blkid
``` works also in persistent mode (with the same usb drive that failed a moment ago in my IBM Thinkpad T41) in this 64-bit machine.

I get no automatic bug-tracker window, and I cannot understand how to file a bug report at Launchpad without that automation. I can browse bugs, but I cannot find anywhere to start reporting bugs. Please help me if it is possible, or else let me know it is impossible to file a bug report without that automatic bug tracker!

---

### Post by ventrical on 2012-04-24
> **sudodus said:**
> I am right now testing 'Live Session in Lubuntu Desktop i386 for Precise Pre-release'

IBM Thinkpad T41:

The testcase works including persistence. But I found a weird bug:
```
sudo blkid
``` works in volatile mode, but it hangs (nothing happens until I press ctrl c) in persistent mode after one or several reboots, so it seems to be consistent.

HP xw8400:

```
sudo blkid
``` works also in persistent mode (with the same usb drive that failed a moment ago in my IBM Thinkpad T41) in this 64-bit machine.

I get no automatic bug-tracker window, and I cannot understand how to file a bug report at Launchpad without that automation. I can browse bugs, but I cannot find anywhere to start reporting bugs. Please help me if it is possible, or else let me know it is impossible to file a bug report without that automatic bug tracker!


 I had the same problems a while back.  I think you can still file bugs manually, (I did), 
Ubuntu-bug etc.. but in some cases even that did not work.

---

### Post by sudodus on 2012-04-24
> **ventrical said:**
> I had the same problems a while back.  I think you can still file bugs manually, (I did), 
Ubuntu-bug etc.. but in some cases even that did not work.
Thank you :KS
```
ubuntu-bug <pid>
``` worked. But it did not work with
```
ubuntu-bug blkid
``` because ubuntu-bug needed the package name, and I didn't know in which package blkid is delivered.

So now I have reported it as a bug. By the way, during the report the command finished with a correct output. So I guess the bug is making it extraordinary slow (while similar commands like ```
sudo fdisk -lu
``` works normally in persistent live mode).

*Edit: This bug shows up only in my IBM thinkpad t41 in persistent live sessions. My Dell dimension 4600 and HP xp8400 are not affected.*

---

