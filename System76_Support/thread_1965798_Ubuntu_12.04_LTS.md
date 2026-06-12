---
title: "Ubuntu 12.04 LTS"
date: 2012-04-26
forum: System76 Support
---

### Post by isantop on 2012-04-26
Another six months past, and now the awesome team at Canonical have another version of Ubuntu out the door. Precise is the only word I can think of to describe it; it's definitely the best version yet. As such, all System76 users are clear to upgrade immediately.

Fresh installations may proceed at will. Online upgrades are looking good too, though as always, we recommend waiting a week or two for the servers to cool down to ensure a reliable upgrade. 

Current and future versions of the System76 Driver (version 2.7.3 and up) are fully compatible with 12.04 LTS. 

Nevertheless, we'd recommend backing up data in any case, just in case. It's always better to be safe.

Full upgrade instructions are available [here](http://knowledge76.com/index.php/PreciseUpgrade)

As an added bonus, all System76 Laptops with Fingerprint Readers are now able to use the reader for authentication.

---

### Post by kwoodie on 2012-04-26
I am excited that the fingerprint reader should work as designed!  However, will the integration with Gnome/X be better than it has in the past?

---

### Post by isantop on 2012-04-26
> **kwoodie said:**
> I am excited that the fingerprint reader should work as designed!  However, will the integration with Gnome/X be better than it has in the past?

The integration is really good, and it works pretty much anywhere PAM is used for authentication. You can use it for:

PolicyKit Authentication (software center, control center, etc.)
Logging in, unlocking the screen.
gksudo 
sudo in a terminal window
logging in and sudo from the virtual terminal/Ctrl+Alt+F1-F7

It's not the most pretty thing in the world, but now that it's working, we can focus on making it look nice for future versions.

---

### Post by kend650 on 2012-04-26
"Current and future versions of the System76 Driver (version 2.7.3 and up) are fully compatible with 12.04 LTS. "

And how do you find out which version of the System76 Driver you have?  Dmesg doesn't have it, and it is not identified in the system settings.

---

### Post by isantop on 2012-04-26
> **kend650 said:**
> "Current and future versions of the System76 Driver (version 2.7.3 and up) are fully compatible with 12.04 LTS. "

And how do you find out which version of the System76 Driver you have?  Dmesg doesn't have it, and it is not identified in the system settings.

You'll want to open up the driver, then click on "About". That said, you can always download the latest version [url=http://planet76.com/[/url]. It will always support all of our systems.

---

### Post by kend650 on 2012-04-26
"You'll want to open up the driver, then click on "About". That said, you can always download the latest version [url=http://planet76.com/[/url]. It will always support all of our systems."

Sorry to be so naive, but where/how do you open the driver?  Where is it, and what is it called?

Thanks,
Ken

---

### Post by isantop on 2012-04-26
Press the Ubuntu key on your keyboard to open the dash, then type in "System76". That should bring up the system76 driver entry.

---

### Post by kend650 on 2012-04-26
typing system76 in the dash brings up nothing.  Now what?

---

### Post by kend650 on 2012-04-26
Well, I went ahead and installed the latest version of the System76 driver, so now I'll wait a week or two before upgrading to 12.04 and actually trying out the fingerprint reader hw/sw...


Thanks,
Ken

---

### Post by icewater on 2012-04-27
I upgraded my Darter Ultra to 12.04 last night, and it seemed to work OK with ethernet and a USB mouse; but today I boot up away from the office and find that wifi and the touchpad are not working.

I'm on kernel 3.2.0-24-generic #37-Ubuntu SMP x86_64.

Any suggestions?

---

### Post by kend650 on 2012-04-27
Make sure wifi and touchpad are enabled.  The default may be to have them turned off.

---

### Post by isantop on 2012-04-27
Was it a fresh installation or an upgrade? If it was an upgrade, I'd suggest running from a Live CD to ensure there isn't a software problem. If that fails, then the best thing to try would be downloading and installing the latest System76 Driver.

---

### Post by b3d on 2012-04-28
I did the network upgrade from 11.10 to 12.04 last night. When I reboot after the upgrade, grub can't find the partition to boot. Any ideas or suggestions for me? 

error: no such partition.
error: no such partition.
error: no such partition.

Press any key to continue ...


I have a Gazelle Pro.

Thanks.

---

### Post by shochatd on 2012-04-29
> **kend650 said:**
> typing system76 in the dash brings up nothing.  Now what?
I just brought it up from System Settings. There was even an icon for it (the System 76 Driver) in the Launcher when I first fired up my new lemu4 (which just arrived Friday). But I'm confused about one thing. The instructions linked here imply that you have to re-install the System 76 Driver *after* doing the normal Ubuntu upgrade. So it seems to me that getting the latest version *before* doing the upgrade would be pointless. Am I missing something here?
-- David

---

### Post by b3d on 2012-04-29
I figured it out.

> **b3d said:**
> I did the network upgrade from 11.10 to 12.04 last night. When I reboot after the upgrade, grub can't find the partition to boot. Any ideas or suggestions for me? 

error: no such partition.
error: no such partition.
error: no such partition.

Press any key to continue ...


Just reinstall the GRUB bootloader:
[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

And BTW, I had to do this again after installing the System76 drivers.

HTH the next person who has this problem.

---

### Post by sibir on 2012-04-30
I made the same grub mistake, but I have been unable to get the live cd to boot. It loads just fine, then I select the  first menu option to run it live, and after some spinning of the cd and some waiting... nothing happens. It just hangs on an empty screen with a flashing cursor and nothing else. Is there something about system76 machines that requires special care when starting a live cd?

---

### Post by isantop on 2012-04-30
> **sibir said:**
> I made the same grub mistake, but I have been unable to get the live cd to boot. It loads just fine, then I select the  first menu option to run it live, and after some spinning of the cd and some waiting... nothing happens. It just hangs on an empty screen with a flashing cursor and nothing else. Is there something about system76 machines that requires special care when starting a live cd?

Instead of making a selection there, go ahead and just let it sit after selecting to boot from the CD Drive. It will go through the purple screen with the white icons, then continue to boot normally. Also, check the other thread you posted in, as I left some feedback there too.

---

### Post by shochatd on 2012-05-05
Last night I did the upgrade to 12.04 on my brand new Lemur Ultra, and all is well. However, there were a few hitches along the way:
1. The scariest moment was when it said that the device to install grub to was missing (!) or had a different name, and mentioned to options: /dev/hda and /dev/hda1. It said if I wasn´t sure to choose both (I think that is what it was saying). So I checked both and it worked. I´m sad to have seen this because it could be totally bewildering to someone who had no idea what these things mean. I´ve done many Ubuntu upgrades on various desktops and never seen this before. Now that the system is up and running, I see that / is on /dev/hda1. Does anyone know what was going on here?
2. Once the system came up, I proceeded to download the .deb for ¨System 76 Driver¨ per the instructions, which say to choose the default option of picking Ubuntu Software Center. However, that option did not show up, even as a non-default. So I looked in /usr/bin to see what the executable is called and didn´t find it. So I ran the thing via Dash and then used ps to see what it is called, finding that the answer is simply /usr/bin/software-center. Armed with that knowledge, I went back to the ¨helper¨ dialog and via Filesystem, picked that executable. After all that, Ubuntu Software Center came up and told me that the thing I wanted to install was already installed! So why do the instructions say you have to download and install it? Anyway, the rest of the instructions (running it, doing a restore) worked as advertised. Once again, I´m afraid someone without Unix knowledge might have been totally thrown by this.
Well, all´s well that ends well. I´m very happy with the machine. Nice to see that they finally added an easy-to-find way to alter the launcher icon size. But they should have done the same with the hide option. I should think that would be popular with the limited screen space of a laptop, especially since you can no longer shove it out of the way (for some reason). How is someone supposed to think of ¨CompizConfig Settings Manager¨? Presumably, Launcher auto-hide will be in ¨Appearance¨ in a future release.
-- David

---

### Post by christopherbalz on 2012-05-06
On the Launcher behavior, I was able to find it without too much trouble under 'System Settings -> Appearance -> Behavior".  

But I too would have been without my o/s without Unix knowledge on this install: I thought it was incredibly rough.  Most everything has become so easy on Ubuntu, but not the upgrade process, by a long shot:  [http://chrismbalz.typepad.com/computerburn/2012/05/rough-upgrade-from-ubuntu-1004-lts-to-1204-lts.html](http://chrismbalz.typepad.com/computerburn/2012/05/rough-upgrade-from-ubuntu-1004-lts-to-1204-lts.html)

---

### Post by shochatd on 2012-05-06
> **christopherbalz said:**
> On the Launcher behavior, I was able to find it without too much trouble under 'System Settings -> Appearance -> Behavior".

Thank you for pointing that out to me. I just didn't see the "Behavior" tab. I guess I owe someone an apology -- they had in fact done exactly what I was saying I wished they had done!
-- David

---

### Post by MoebusNet on 2012-05-06
> **shochatd said:**
> Last night I did the upgrade to 12.04 on my brand new Lemur Ultra, and all is well. However, there were a few hitches along the way:
1. The scariest moment was when it said that the device to install grub to was missing (!) or had a different name, and mentioned to options: /dev/hda and /dev/hda1. It said if I wasn´t sure to choose both (I think that is what it was saying). So I checked both and it worked. I´m sad to have seen this because it could be totally bewildering to someone who had no idea what these things mean. I´ve done many Ubuntu upgrades on various desktops and never seen this before. Now that the system is up and running, I see that / is on /dev/hda1. Does anyone know what was going on here?
2. Once the system came up, I proceeded to download the .deb for ¨System 76 Driver¨ per the instructions, which say to choose the default option of picking Ubuntu Software Center. However, that option did not show up, even as a non-default. So I looked in /usr/bin to see what the executable is called and didn´t find it. So I ran the thing via Dash and then used ps to see what it is called, finding that the answer is simply /usr/bin/software-center. Armed with that knowledge, I went back to the ¨helper¨ dialog and via Filesystem, picked that executable. After all that, Ubuntu Software Center came up and told me that the thing I wanted to install was already installed! So why do the instructions say you have to download and install it? Anyway, the rest of the instructions (running it, doing a restore) worked as advertised. Once again, I´m afraid someone without Unix knowledge might have been totally thrown by this.
Well, all´s well that ends well. I´m very happy with the machine. Nice to see that they finally added an easy-to-find way to alter the launcher icon size. But they should have done the same with the hide option. I should think that would be popular with the limited screen space of a laptop, especially since you can no longer shove it out of the way (for some reason). How is someone supposed to think of ¨CompizConfig Settings Manager¨? Presumably, Launcher auto-hide will be in ¨Appearance¨ in a future release.
-- David

+1

The Upgrade Available message popped up for me, so after backing everything up, I performed all available updates then the upgrade to 12.04. I was also thrown by the grub choice, and like David I checked both choices. During the upgrade process before this there were 2 instances where I had to view the details in the Upgrade GUI to select "OK" in the Terminal to continue the upgrade. A complete newby would have been stumped there.

Everything seems to be working properly, but I wish I knew what the proper choice for Configure Grub-PC should have been. Is there anything I'll need to do from here? Will I need to install/reinstall the System76 driver?

Serval Pro 7 with the OEM 11.10 install updated to 12.04

---

### Post by shochatd on 2012-05-06
It's my understanding (from the document linked from the 1st message in this thread), that after you've done the regular Ubuntu upgrade, you have to reinstall the System 76 Driver (although it seemed like it was already there in my case). If you go into System Settings, you'll see the big black and white 76 if you have it. Then you need to run that and select "restore system". Anyway, that's what I did and things seem to be working fine. 
-- David

---

### Post by jr223 on 2012-05-07
A strange thing happened to my Ratel?

Hi all,

I just wanted to mention this rather strange accurance which happened yesterday (Sunday 05/06).
I had turned on my System76 Ratel (a great Machine) and surfed a bit.

Then left to go to my Mom's house for the rest of the day leaving my Ratel on and connected to the internet (no worries its not Windwoz).
When I returned home and sat down at my Ratel I noticed that the Automatic Updates had come on and was downloading the Update to 12.04 LTS (from my current 11.04).
Weird, anyway I stopped the update nothing was upgraded, but it seemed to run the upgrade automatically and stopped on a request for user intput in a tick box, hence I was able to stop upgrade. 

This is kinda weird I think.

Thanks
Regards
JR223

---

### Post by suspended on 2012-05-28
Last night I figured I was behind in my upgrades (just a year) and I upgraded from 11.04 to 11.10 without any issues. Now, this morning, I was going to upgrade from 11.10 to the latest and greatest 12.04 and it pops up with an error.

> [SIZE=3]Not enough free disk space[/SIZE]
The upgrade has aborted. The upgrade needs a total of 3,219 M free space on disk '/'. Please free at least an additional 184 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.So I ran df -h with the following output
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  8.1G  5.1G  62% /
udev                  2.0G  4.0K  2.0G   1% /dev
tmpfs                 785M  952K  785M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  180K  2.0G   1% /run/shm
/dev/sda3             442G   30G  390G   8% /home
```

Not sure where it is looking for the 3.2G.

I have a daru3 (Darter Ultra), not sure if this is really a system76 issue, but thought I would start here. 

-JK

---

### Post by suspended on 2012-05-31
Problem resolved its self. I was able to upgrade without any issues a few reboots later. Not really sure what caused the issue, so that will eat at me. But the overall issue of not upgrading is done.
 
Now I can get to recustomizing.
 
-JK

---

### Post by 0tto on 2012-06-04
How big is 12.04 supposed to be and what can I do free up some space?  Just upgraded to 12.04 and my Lemur Ultra thin now has full 40gb SATA solid state hard drive.  Computed janitor ran and did little to nothing. 

How big is 12.04 supposed to be and what can I do free up some space? 

Thanks!

---

### Post by madjr on 2012-06-04
> **0tto said:**
> How big is 12.04 supposed to be and what can I do free up some space?  Just upgraded to 12.04 and my Lemur Ultra thin now has full 40gb SATA solid state hard drive.  Computed janitor ran and did little to nothing. 

How big is 12.04 supposed to be and what can I do free up some space? 

Thanks!

you should delete or uninstall stuff you dont need.

check your home folder and ubuntu software center for stuff you can get rid of.

you can also backup some stuff to ubuntu one.

---

### Post by 0tto on 2012-06-04
> **madjr said:**
> you should delete or uninstall stuff you dont need.

check your home folder and ubuntu software center for stuff you can get rid of.

you can also backup some stuff to ubuntu one.

Both of your suggestions would only free up 10gb max as Ubuntu 1 is 5 gigs the software I have might be 5 gb.  I say again the 40gb HD is maxed out by 12.04 and I have run clean sweep.

---

### Post by abimael08 on 2012-06-04
Do SYSTEM76 laptops work well?? better than main stream laptops, like Dell, HP or Toshiba??

---

### Post by madjr on 2012-06-05
> **abimael08 said:**
> Do SYSTEM76 laptops work well?? better than main stream laptops, like Dell, HP or Toshiba??

here is a review:

[http://www.omgubuntu.co.uk/2012/06/hands-on-with-the-system76-lemur-ultra-ubuntu-laptop](http://www.omgubuntu.co.uk/2012/06/hands-on-with-the-system76-lemur-ultra-ubuntu-laptop)

---

### Post by 0tto on 2012-06-05
> **abimael08 said:**
> Do SYSTEM76 laptops work well?? better than main stream laptops, like Dell, HP or Toshiba??

If I could get $200 for my Lemur I'd take it.  Its flimsy with a horrid keyboard.  Had I an opportunity to feel it prior to purchase Id of never done it. It also has a flimsy cover on the back of the lcd.  I took it out of my bag one day and the lcd was shattered. System 76 tried to tell me I closed a pencil on it or something.  The wanted $400 + replace the screen.  Then after begging them to sell me a screen as if I was after the queen mums balls they wanted an insane price for just a screen and insisted it could not be replaced. Enter google, $115 and about 20 minutes and I was back in business.  I sill can't wrap my head around who they want to be their customer. 

There are many companies I will not do business with as a result of their business practices.  I'll happily pay more from a small company to support it depending on what its up to.  I have never been in a Wallmart, I am done forever with Exxon/Mobil, BP, Micro$oft and others.  All that said Dell would at least sell you the friggin part.  IMHO Thinkpads have the only usable keyboards and generally are reliable but ya cant get a new one without an OS.  

I had a zareason prior to this system 76.  It was well built and fabulously constructed but the modem never worked and after a month of being jerked about by their tech support and the CEO I sent it back did a charge back as vendors are required to deliver working products, contrary to what the CEO was trying to blow up my skirt.  

I say again people:  HOW BIG should 12.04 be as mine is 30+gigs and what is the work around to reclaim some of my HD space?

---

### Post by abimael08 on 2012-06-06
> **madjr said:**
> here is a review:

[http://www.omgubuntu.co.uk/2012/06/hands-on-with-the-system76-lemur-ultra-ubuntu-laptop](http://www.omgubuntu.co.uk/2012/06/hands-on-with-the-system76-lemur-ultra-ubuntu-laptop)

thank you

---

### Post by 0tto on 2012-06-06
Not enough free disk space
The upgrade has aborted. The upgrade needs a total of 3,219 M free space on disk '/'. Please free at least an additional 184 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Thanks for reposting this to me.   Running sudo apt-get clean was good for about 3 gigs so 12.04 is down to about 19 gigs.  That seems HUGE to me. 1/2 of my HD taken up by the OS might be workable for a Winblow$ set up but Ubuntu?  How big is your OS?

---

### Post by suspended on 2012-06-06
> **0tto said:**
> Not enough free disk space
The upgrade has aborted. The upgrade needs a total of 3,219 M free space on disk '/'. Please free at least an additional 184 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Thanks for reposting this to me.   Running sudo apt-get clean was good for about 3 gigs so 12.04 is down to about 19 gigs.  That seems HUGE to me. 1/2 of my HD taken up by the OS might be workable for a Winblow$ set up but Ubuntu?  How big is your OS?


Here is a good resource for you: [https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html)

However, as you shrink the install size you shrink the capabilities. If I look at my partitions (as I posted on the previous page) you can see that I am using 8.9G (after installing 12.04) on my root, with the bulk of my data in my /home folder . There are plenty of things that I have installed that could be bulking up my root as well. When I get things from the software store I don't pay attention to where they install (maybe I should) to know if they are in my home folder or elsewhere.

Not sure if that really helps, but it might give you a better idea. 

Hope that helps...
 (maybe someone with more knowledge than me can chime in here)

---

### Post by 0tto on 2012-06-06
you can see that I am using 8.9G (after installing 12.04) on my root, with the bulk of my data in my /home folder . 


Well there it is.  You have 12.04 running at 8.9G and mine is 19G.  so what I am looking for is what to get rid of and how to do it. What could be so hard about that?

---

### Post by Newbunto on 2012-06-15
> **shochatd said:**
> Last night I did the upgrade to 12.04 on my brand new Lemur Ultra, and all is well. However, there were a few hitches along the way:
1. The scariest moment was when it said that the device to install grub to was missing (!) or had a different name, and mentioned to options: /dev/hda and /dev/hda1. It said if I wasn´t sure to choose both (I think that is what it was saying). So I checked both and it worked. I´m sad to have seen this because it could be totally bewildering to someone who had no idea what these things mean. I´ve done many Ubuntu upgrades on various desktops and never seen this before. Now that the system is up and running, I see that / is on /dev/hda1. Does anyone know what was going on here?
-- David

Did the update today.

Like you I was unsure when I got to that point. Fortunately I have lots of PCs so I did some research on another PC before proceeding.

Like you I was a bit mystified as to which if any of a) "was missing" or b) "had a different name" applied.

I think / was on /dev/hda1 *before* your upgrade i.e. no change there.

I believe that you did not choose the correct option. I think you are supposed to choose only /dev/hda

The help available on that dialog box itself suggests only installing on the drive, not on partitions (if I recall correctly).

Also, this page [http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader) says
[INDENT]** Important Note About GRUB Updates!**

If you need to configure grub-pc (for example, after an update),  installing grub to all devices will break GRUB. You will need to install  to /dev/sda (not /dev/sda1) **only**. Installing everywhere **will**  break the bootloader. 
[/INDENT] 
Given that it says "will break" but you do not appear to have "broken" I don't know what is going on.

---

### Post by Newbunto on 2012-06-15
> **0tto said:**
> How big is 12.04 supposed to be

I'm using a shade under 10 GB on / and that's with basically no files (because all my files are on a file server) so I suppose that 10 GB is just software. I don't have much installed over and above what comes with Ubuntu. That doesn't include the swap partition.

There could be file system overheads. That's going to depend on what file system you have. I have ext4.

Is this typical?

---

### Post by isantop on 2012-06-15
> **Newbunto said:**
> I'm using a shade under 10 GB on / and that's with basically no files (because all my files are on a file server) so I suppose that 10 GB is just software. I don't have much installed over and above what comes with Ubuntu. That doesn't include the swap partition.

There could be file system overheads. That's going to depend on what file system you have. I have ext4.

Is this typical?

I would check that you don't have local copies of files. Ubuntu should occupy less than 3 GB of space installed.

---

### Post by linux12 on 2012-06-16
> **isantop said:**
> Precise is the only word I can think of to describe it 

How about "pangolin"?:P

---

### Post by Newbunto on 2012-06-17
> **isantop said:**
> I would check that you don't have local copies of files.

Local copies of what files?

How would I check that?

Where would I look?

---

### Post by isantop on 2012-06-18
> **Newbunto said:**
> Local copies of what files?

How would I check that?

Where would I look?

Local copies of your files that are kept on the file server. I'm sure where they would be, since it depends on what file server you're using. Also, make sure you don't have things lying around in the trash. 

You can also use the included "Disk usage Analyzer" to find trouble apps.

---

### Post by Newbunto on 2012-06-19
> **isantop said:**
> You can also use the included "Disk usage Analyzer" to find trouble apps.

Thanks for the tip. Yep, that enabled me to look around for the reason for my higher than expected usage.

/var/cache/apt* - lots of .deb files (happy to leave them there) and other stuff

~/.mozilla/firefox/Cache - hmmm, possibly FireFox is storing a bit more than I want

~/Downloads - oops, one for the Red Faces department - multiple Ubuntu .iso files as I flailed around trying to get a Live anything to boot (now resolved) (I cleaned some of them up)

Any insight into why Disk Usage Analyser reports / as having a size of 5.6 GB but says that the disk space used is 7.4 GB?

As far as I can tell, 7.4 GB means "decimal GB" and matches the output from "df /" which is 7188784 1K-blocks used (where I take K here to mean "binary K" i.e. 1024).

---

### Post by joe4ska on 2012-06-20
**Additionally** you can **remove cached packages** to free up some space. This comes in handy if you installed a ton of stuff and decided to remove it later.  The files are still on the system if you want to reinstall so you won't have to download it again. 

> $ sudo apt-get clean

or

> # apt-get clean

[Source info]("http://www.cyberciti.biz/faq/debian-ubuntu-linux-clear-the-package-cache/")

---

### Post by PantherFarber on 2012-06-20
kill unity. it blows. it takes twice as long to find the ap i want then it did with gnome. never going to win if we are always taking two steps back and none forward. this release i would say is 5 steps back. 10.10 was better and more usable. fix it. you have huge amounts jumping ship. pretty much all the secondlife linux users have had to jump ship from this crap because you broke every thing that worked. quit breaking things that work dumbasses.

this is all at ubuntu. system 76 rules. its unfortunate that ubuntu is draging a great linux comp maker down with it. system 76 needs to jump ship

---

### Post by isantop on 2012-06-20
> **PantherFarber said:**
> kill unity. it blows. it takes twice as long to find the ap i want then it did with gnome. never going to win if we are always taking two steps back and none forward. this release i would say is 5 steps back. 10.10 was better and more usable. fix it. you have huge amounts jumping ship. pretty much all the secondlife linux users have had to jump ship from this crap because you broke every thing that worked. quit breaking things that work dumbasses.

this is all at ubuntu. system 76 rules. its unfortunate that ubuntu is draging a great linux comp maker down with it. system 76 needs to jump ship

Actually, it doesn't look like we're being dragged down. Most of our users appear to be quite happy with Unity, and it hasn't affected sales at all. On the contrary, we're seeing record growth.

Unity may not work for some people, but but for a vast, decidedly silent majority, it works great, particularly in 12.04. It had some hiccups early on, and we don't even talk about 10.10 netbook's Unity (wait, I thought 10.10 didn't have a netbook edition!).

---

### Post by jakobcreutzfeldt on 2012-06-21
> **0tto said:**
> Well there it is.  You have 12.04 running at 8.9G and mine is 19G.  so what I am looking for is what to get rid of and how to do it. What could be so hard about that?

Run Baobab ("Disk Usage Analyzer") or run "du" in a terminal. For example, ```
$ sudo du -hm {/var,/usr,/etc,/opt} | sort -h | tail -n20
``` will find the top 20 directories and subdirectories in disk usage (in megabytes). 

Your disk usage sounds abnormal, so no one will be able to help you until you give more relevant information. Not to mention, your words aren't very inviting to people to potentially help you.

---

### Post by Newbunto on 2012-06-22
> **isantop said:**
> Most of our users appear to be quite happy with Unity

I'm only one user but as a more or less brand new Linux user, I don't have any baggage about earlier Linux user interfaces. I'm happy with Unity. I am more likely to be comparing with some Windows version.

The launcher bar is good! I've even managed to customise in a few things  e.g. right mouse on nautilus (Files) gives direct access to some frequently  used files.

I think it's great that you can type what you are looking for because  one of the worst things about Windows is that with hundreds of things in  menus (and moving to different menus every Windows version), you just know that what you  want is there but you will never find it. Unless you use Windows Help and let it jump you straight there - which defeats the point of having a menu - and which is sort of what the Unity launcher bar is giving you.

I'm not really sold on the unified menu bar though e.g. just means more mouse movement to move between the window and its menu bar. (I would hate to be doing all that mousing on a trackpad but I normally have an external mouse plugged in.) I've turned the unified menu bar off for a few applications.

My 2c

---

### Post by jrbrtsn on 2012-08-29
I just upgraded my panp6 from Ubuntu 10.04 to 12.04, and now closing the lid no longer suspends the system.  I can successfully suspend the system from a GUI menu pick, and wake it up by pressing the Fn+F4 keys simultaneously.

I have the System76 "driver" v 3.0.0, and have applied the "Install Driver" procedure.  Anyone with a similar experience?  Any thoughts on how to get the lid switch working again?

---

### Post by shochatd on 2012-08-30
> **jrbrtsn said:**
> I just upgraded my panp6 from Ubuntu 10.04 to 12.04, and now closing the lid no longer suspends the system.  I can successfully suspend the system from a GUI menu pick, and wake it up by pressing the Fn+F4 keys simultaneously.

I have the System76 "driver" v 3.0.0, and have applied the "Install Driver" procedure.  Anyone with a similar experience?  Any thoughts on how to get the lid switch working again?

I generally use the menu to do the suspend. But after reading your post, I did try the lid closing method and it worked for me. 12.04 on a Lemur Ultra.
-- David

---

### Post by verysimple on 2012-09-03
> **jrbrtsn said:**
> I just upgraded my panp6 from Ubuntu 10.04 to 12.04, and now closing the lid no longer suspends the system.  I can successfully suspend the system from a GUI menu pick, and wake it up by pressing the Fn+F4 keys simultaneously.

I have the System76 "driver" v 3.0.0, and have applied the "Install Driver" procedure.  Anyone with a similar experience?  Any thoughts on how to get the lid switch working again?

I am in the exact same situation.

Panp6 with 10.04 upgraded to 12.04 today. Lid no longer suspends the system, but Suspend from GUI and resume from Fn+F4 works. S76 driver 3.0.0 installed as per the documentation.

Any help on this?

---

### Post by clixis on 2012-09-14
I new and and confused. The update manager has a button to upgrade to 12.04.01 LTS. I am running a Starling star5 netbook with Unity desktop version 10.04 LTS (I think). Can I upgrade directly from 10.04 to 12.04? Surely the update manager wouldn't lead me astray?
Should I do a fresh install instead? Thanks.

---

### Post by Carborundum on 2012-09-14
> **clixis said:**
> I new and and confused. The update manager has a button to upgrade to 12.04.01 LTS. I am running a Starling star5 netbook with Unity desktop version 10.04 LTS (I think). Can I upgrade directly from 10.04 to 12.04? Surely the update manager wouldn't lead me astray?
Should I do a fresh install instead? Thanks.
It's theoretically possible to upgrade from 10.04.4 to 12.04.1 without reinstalling, but doing so often results in breakage. If you want to avoid headache, I strongly recommend you to do a clean install.

---

