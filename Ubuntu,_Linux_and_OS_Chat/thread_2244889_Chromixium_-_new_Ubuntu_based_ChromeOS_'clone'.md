---
title: "Chromixium - new Ubuntu based ChromeOS 'clone'"
date: 2014-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by rv_happy on 2014-09-19
Hello all

I am pleased to announce a new downloadable live ISO of my new project **Chromixium**:
[https://sourceforge.net/projects/theme-ix/files/Chromixium/](https://sourceforge.net/projects/theme-ix/files/Chromixium/)

This is an attempt to recreate Chrome/ChromiumOS on a conventional desktop Linux base - in this case Ubuntu 14.04 LTS. This allows us to get over some of the shortfalls of the real ChromeOS, namely the ability to install on any hardware we want, ability to use any amount of local file storage, ability to install local applications (not just use webapps), ability to connect USB devices including printers... The interface is clean, modern and uncluttered whilst remaining fairly light, as it uses Openbox as the window manager. It is an almost exact replica of Chrome/ChromiumOS in look and feel:
[[IMG]http://i1270.photobucket.com/albums/jj609/richjack76/Chromixium/31269d29-f2b7-4622-b3ec-4be1ff02ee65_zpsfa4c53b8.png[/IMG]]("https://a.fsdn.com/con/app/proj/theme-ix/screenshots/ChromixiumAlpha4.png")

A full announcement can be found on my website:
[http://linuxthemer.blogspot.com](http://linuxthemer.blogspot.com)

...and more details are on the Sourceforge download page above.

This is very early days in this project and an ideal opportunity for anyone who would like to contribute in any way - technical, testing, artwork or just sharing your thoughts and ideas.

I hope someone out there likes it :)

Cheers
RichJack

---

### Post by endlessinstant on 2014-09-19
Interesting.  Any particular reason you're switching to Ubuntu? Seems like less trouble to run with Chromium OS and put back in the missing Gentoo pieces first.  

If your goal is to provide stability but still have it largely replicate Chrome OS, I'd think moving to Debian would be good as it has stable packages for most of the kinds of software that people are calling for in Chrome OS (and, in fact, that's why I run Debian on my chromebook).   Ubuntu seems like a good choice if you want to keep the look and feel of Chrome OS but provide more packages.  I'd love to see Steam running on this.

---

### Post by rv_happy on 2014-09-19
> **endlessinstant said:**
> Interesting.  Any particular reason you're switching to Ubuntu? Seems like less trouble to run with Chromium OS and put back in the missing Gentoo pieces first. 

Debian based distros are what I know best. Plus I needed to recreate Chrome OS, rather than integrate the Ash desktop into regular Linux. I am already aware that you can run the Chrome development version in Linux and force the Ash desktop to appear, but that rather locks you into Chrome/Chromium - I'm not aware of a method of getting Ash to see non-Chrome apps. So for me, at least, hacking ChromeOS/Gentoo would definitely be more trouble!

Also, this project is really an extension of existing work that I have showcased on my blog - recreating the look of ChromeOS in XFCE, testing Docks within XFCE and creating a Debian based Xubuntu. In the end for this one, I veered away from XFCE, but it isn't ruled out indefinitely.

> If your goal is to provide stability but still have it largely replicate Chrome OS, I'd think moving to Debian would be good as it has stable packages for most of the kinds of software that people are calling for in Chrome OS (and, in fact, that's why I run Debian on my chromebook).   Ubuntu seems like a good choice if you want to keep the look and feel of Chrome OS but provide more packages.  I'd love to see Steam running on this.

Both - Stability and apps, which to my mind can be offered by Debian Stable or Ubuntu LTS. But just now, it seems better to wait for feature freeze in Jessie before committing any further work on Debian testing and it would need pulling some packages from Experimental (notably Plank), so right now Ubuntu LTS seems the better option. Having said that I do intend to create a Debian build in due course, if just to see the difference in base size and performance.

But these are exactly the kind of discussions I want to have going forward to get the most out of this project so thanks for your prompt comments :)

I am not a big gamer, but I'd be interested to see how Steam performs on this set up - I might give it a whirl some time!

---

### Post by rv_happy on 2014-09-19
Here are some screenshots to whet your appetites!

[COLOR=#000000][FONT=arial][ [IMG]http://2imgs.com/2i/t/10e0b69c4f.jpg[/IMG]]("http://2imgs.com/10e0b69c4f")  [/FONT][/COLOR][[IMG]http://2imgs.com/2i/t/55b5e3c91a.jpg[/IMG]]("http://2imgs.com/55b5e3c91a")  &#8203; [[IMG]http://2imgs.com/2i/t/33d385af7c.jpg[/IMG]]("http://2imgs.com/33d385af7c")  

[COLOR=#000000][FONT=arial][ [IMG]http://2imgs.com/2i/t/00e0b69c4f.jpg[/IMG]]("http://2imgs.com/00e0b69c4f")  [/FONT][/COLOR][[IMG]http://2imgs.com/2i/t/11f1a78d5e.jpg[/IMG]]("http://2imgs.com/11f1a78d5e")

[COLOR=#000000][FONT=arial]RichJack[URL="http://2imgs.com/00e0b69c4f"]
[/URL][/FONT][/COLOR][COLOR=#000000][FONT=arial][URL="http://2imgs.com/10e0b69c4f"]
[/URL][/FONT][/COLOR][COLOR=#000000][FONT=arial]

[/FONT][/COLOR]

---

### Post by d-cosner on 2014-09-19
Light and it looks great, downloading now. Thanks!

---

### Post by ibjsb4 on 2014-09-19
Think I will also take it for a test drive.  See how it compares to LXQt.

---

### Post by Tar_Ni on 2014-09-19
Awesome! I have been waiting for that kind of distro since the death of JoliOS. I have tried a chromebook and I really like the concept but indeed the OS is tied and locked into specific hardware. Since Chromium OS is open-source I was wondering why no one had considered making a real Linux distro out of it and attempt to make a ''Chrome OS for all PCs''.

I can only give you a big thumbs up for this and I hope your project becomes succesful! I will be following it closely.

---

### Post by jeff.zimmm on 2014-09-20
Wow, this is awesome. Downloading it now. Thank you, thank you, thank you.

I work for a school that is planning the addition of a large cart of ChromeBooks. How cool would it be if the computer lab PCs ran the "same" OS?

---

### Post by ibjsb4 on 2014-09-21
Well I loaded it up and it works, thats about all I can say.
Maybe I'm just getting too picky in my old age.

---

### Post by rv_happy on 2014-09-21
Hello everyone

Thanks for all the excitement :D Remember, it's only an alpha and there will be a few teething problems, like this one...

If you want to install it in **VirtualBox** (or any hardware) do make sure you already have at least one partition and a partition table on your virtual hard drive. If you are starting a fresh virtual machine, you will need to do this, then you can use the installer to re-partition it. 

If you don't want to use the command line, just install gparted using:   

> sudo apt-get update   
[type the password user]   
sudo apt-get install gparted

Of course you can just use fdisk/cfdisk. 

Alternatively, you can install the Ubuntu system installer by:  

> sudo apt-get install ubiquity-frontend-gtk

Or just use Synaptic to install these things (after reloading the package list).

I am going to start using the Sourceforge project page to track issues via the Tickets:
[https://sourceforge.net/p/theme-ix/tickets](https://sourceforge.net/p/theme-ix/tickets) 

Thanks all :)
RichJack

---

### Post by rv_happy on 2014-09-25
A quick update:

A [new Alpha is out ]("http://chromixium.wordpress.com/news/")and I have a [new website]("http://chromixium.wordpress.com") or you can follow me on [Google+]("https://plus.google.com/101417096007971328432").

Download the latest version here:
[https://sourceforge.net/projects/theme-ix/](https://sourceforge.net/projects/theme-ix/)

I have been amazed at the response, 570 downloads so far this week and this is the only place (apart from my own sites) where I have placed a link.

I am going to work heavily on documentation next and get the new website looking a bit more professional. Then I have a long list of features to try/change/fix before the next release comes out :)

Regards
RichJack

---

### Post by nomenkultur on 2014-09-27
I fail to comprehend how can anyone make openbox look so amazing... unfortunately I wasn't able to test it out since dd fails to produce a bootable iso, what tool is needed? unetbootin?

---

### Post by Tar_Ni on 2014-09-27
> **rv_happy said:**
> I have been amazed at the response, 570 downloads so far this week and this is the only place (apart from my own sites) where I have placed a link.

You would be surprised how many people seems to be googling ''Chrome OS''. I mean if Google had made a Linux distros out of it I am sure it would be near the top of distro watch..

> **rv_happy said:**
> I am going to work heavily on documentation next and get the new website looking a bit more professional. Then I have a long list of features to try/change/fix before the next release comes out :)

Great! I am waiting for a stable release.

But how will update works? Will it be a an automatic background type of update like Chrome OS and will we have to use the Update Manager?

Also what about Chromium's peppeflash? The package won't update itself, you have to run the update manually with the terminal in Ubuntu. That could pose some security issues for the unwary.

---

### Post by rv_happy on 2014-09-28
> **nomenkultur said:**
> I fail to comprehend how can anyone make openbox look so amazing... unfortunately I wasn't able to test it out since dd fails to produce a bootable iso, what tool is needed? unetbootin?

Thank you - it is Openbox, honest :D

And, yes, Unetbootin is the supported method of transferring the ISO to a USB stick - it also offers persistence. It's in the Ubuntu repos.

I have uploaded detailed installation instructions here:
[http://chromixium.wordpress.com/guidebook/](http://chromixium.wordpress.com/guidebook/)

I hope it works out for you :)
RichJack

---

### Post by rv_happy on 2014-09-28
> **Tar_Ni said:**
> Great! I am waiting for a stable release.
iThanks :) though It might be a little while coming. The Alpha is pretty solid, just a little rough around the 'internal' edges, so to speak. 

> But how will update works? Will it be a an automatic background type of update like Chrome OS and will we have to use the Update Manager?

Also what about Chromium's peppeflash? The package won't update itself, you have to run the update manually with the terminal in Ubuntu. That could pose some security issues for the unwary. 

I have got unattended-upgrades set to install security updates in the background. Chromium browser is usually pushed out through that channel. This is already in place in the Alpha release. I want to do away with the update manager if I can help it and keep the update process as close to that of Chrome OS as I can.

There is some discussion about moving pepperflash to the security channel, which would sort out that problem, but in the meantime, I might look into some sort of cron job to update it behind the scenes. That's not in the Alpha release just yet though. I might update the website with some information to that effect.

Cheers
RichJack

---

### Post by rv_happy on 2014-10-04
Hi everyone

Just wanted to update you all on the progress of this project...

I have had a busy week working on documentation as promised and you can now view and download a quick start guide and a detailed installation guide from the new website:
[http://chromixium.wordpress.com/guide](http://chromixium.wordpress.com/guide)

I've also been busy working on some updates to the icon set to bring it more in line with Chrome OS. I've spent quite a lot of time becoming aquainted with inkscape. I have been posting regular updates to Google +
[https://plus.google.com/101417096007971328432](https://plus.google.com/101417096007971328432)

Most importantly I have been collating testing feedback and I have a fairly long list of items to attend to before the next release. I'll keep you posted when that will be, but it's looking like a few weeks yet.

Thanks to everyone who has download, fed back and shown an interest in this project.

Regards
RichJack

---

### Post by conor5 on 2014-10-22
Hi,

This is a great project, I've been looking for just this for a while. I have an issue though. Unfortunately, I can't get the iso to boot from my usb for installation. I write the iso to the usb using unetbootin, but receive the message 'operating system missing' when attempting to boot. Am I being a fool and doing something wrong? 

great work again, I can't wait to use it.

Thanks.

---

### Post by rv_happy on 2014-10-22
Hi Conor5

First of all, thanks for your interest in my project :). But sorry that you aren't able to try it out at the moment :(.

I can confirm that UNetbootin does work with the ISO, but your error is not so unusual. It is very likely due to the USB stick in question or possibly a corrupted download.

Sometimes the flash memory on USB sticks doesn't get successfully overwritten, especially the boot sector. As a result, a computer BIOS may not see the boot flag set by Unetbootin and therefore reports Operating Missing. See here for a similar case: [http://ubuntuforums.org/showthread.php?t=2171393](http://ubuntuforums.org/showthread.php?t=2171393)

Steps to try and fix this:

1. Try a different brand of USB stick
2. If you are on Windows, try a different tool. LiLi is a great one and works well: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
3. If you are on Linux already, try to 'clean' the boot sector. From a root terminal (or use sudo) (where /dev/sdb is your USB device):

[FONT=courier new]```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```[/FONT]

Then you can recreate the MBR and a single bootable partition using fdisk (the command after the fdisk line are single character commands whilst in the fdisk console):

[FONT=courier new]```
fdisk /dev/sdb
o
n
p
1
<return>
<return>
a
1
w
```[/FONT]

Then format to FAT32:

```
[FONT=courier new]mkdosfs -F 32 -I /dev/sdb1[/FONT]
```

[FONT=arial]Finally try again with UNetbootin

4. Test the ISO boots in a virtual machine eg VirtualBox, Qemu...
5. If all this fails, do try to download the ISO again, you never know, it could be simple file corruption.

Trying a different USB stick is definitely the best option if you have one handy! I hope you get it going soon but if not, do ask again, and I'll do my best to help you.

Regards
RichJack[/FONT]

---

### Post by conor5 on 2014-10-27
> **rv_happy said:**
> Hi Conor5

First of all, thanks for your interest in my project :). But sorry that you aren't able to try it out at the moment :(.

I can confirm that UNetbootin does work with the ISO, but your error is not so unusual. It is very likely due to the USB stick in question or possibly a corrupted download.

Sometimes the flash memory on USB sticks doesn't get successfully overwritten, especially the boot sector. As a result, a computer BIOS may not see the boot flag set by Unetbootin and therefore reports Operating Missing. See here for a similar case: [http://ubuntuforums.org/showthread.php?t=2171393](http://ubuntuforums.org/showthread.php?t=2171393)

Steps to try and fix this:

1. Try a different brand of USB stick
2. If you are on Windows, try a different tool. LiLi is a great one and works well: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
3. If you are on Linux already, try to 'clean' the boot sector. From a root terminal (or use sudo) (where /dev/sdb is your USB device):

[FONT=courier new]```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```[/FONT]

Then you can recreate the MBR and a single bootable partition using fdisk (the command after the fdisk line are single character commands whilst in the fdisk console):

[FONT=courier new]```
fdisk /dev/sdb
o
n
p
1
<return>
<return>
a
1
w
```[/FONT]

Then format to FAT32:

```
[FONT=courier new]mkdosfs -F 32 -I /dev/sdb1[/FONT]
```

[FONT=arial]Finally try again with UNetbootin

4. Test the ISO boots in a virtual machine eg VirtualBox, Qemu...
5. If all this fails, do try to download the ISO again, you never know, it could be simple file corruption.

Trying a different USB stick is definitely the best option if you have one handy! I hope you get it going soon but if not, do ask again, and I'll do my best to help you.

Regards
RichJack[/FONT]


I skipped ahead and used another USB I had to hand. Worked a treat. Thanks!

---

### Post by rv_happy on 2014-10-28
Great glad it works and hope you enjoy using it. If you have any more questions feel free to ask.

---

### Post by conor5 on 2014-10-29
I installed it completely on an old netbook over the weekend. Seems to have very few issues and looks great. I look forward to a stable release to give it a try on other machines.

---

### Post by rv_happy on 2014-10-29
Excellent, thanks for reporting back. Could you let me know what model netbook it is? My next release will be out in a few weeks. Thanks :p

---

### Post by conor5 on 2014-11-12
[SIZE=2][FONT=arial]Sure, the netbook is a 12.1-inch ASUS Eee PC 1215B. Very old and batter but working a treat 

[/FONT][/SIZE]

---

### Post by rv_happy on 2014-11-14
[SIZE=2][FONT=arial]Hello everyone

I am pleased to announce a new release of Chromixium which is ready for download now:
[https://sourceforge.net/projects/chromixium/files/?](https://sourceforge.net/projects/chromixium/files/?)

The new version is still in Alpha Status but I am hoping with a bit of feedback over the coming weeks, any flaws can be ironed out and it can get moved onto Beta status.

For those that don't know, Chromixium is an attempt to recreate the look and feel of Chrome OS on Ubuntu 14.04 LTS (32 bit):

[/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=arial]LTS Linux Kernel 3.13[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Chromium Web Browser[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Pepperflash Plugin[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Openbox window manager[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Compton desktop compositor[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]Plank dock[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]LXPanel[/FONT][/SIZE]
[/LIST]
[FONT=sans-serif][SIZE=2][FONT=arial]Applications are largely GTK+3 to create a consistent and modern look and feel.[/FONT][/SIZE]

Screenshot:

[[IMG]https://a.fsdn.com/con/app/proj/chromixium/screenshots/Chromixium_Alpha6_Default_Desktop.png/182/137[/IMG]]("https://chromixium.files.wordpress.com/2014/11/chromixium_alpha6_default_desktop.jpg")[/FONT]

Main website: 
[http://chromixium.org](http://chromixium.org)

---

### Post by overdrank on 2014-11-14
Threads merged :)

---

### Post by bro2 on 2014-11-14
Going to check dis out :)


UI looks beary nice...I admit I'm a sucker for low-key (no very obvious desktop effects like Aero) pretty DEs!

---

### Post by jerzyglowacki on 2014-11-26
It looks very similar to [Chrome OS Linux]("http://getchrome.eu") from 2009 and [Evolve OS]("http://evolve-os.com") from 2014. Did the author know them when he created yet another Chrome OS substitute?

---

### Post by rv_happy on 2014-11-26
> **jerzyglowacki said:**
> It looks very similar to [Chrome OS Linux]("http://getchrome.eu") from 2009 and [Evolve OS]("http://evolve-os.com") from 2014. Did the author know them when he created yet another Chrome OS substitute?

Yes i did. I looked at both :)

Chrome OS Linux is undeveloped since at least late 2012, so not much help to me. Chrome OS has moved on a lot in that time. Cr OS was based on SUSE, Chromixium is based on Ubuntu. I have recreated the dock, app launcher, window and icon theme and tried to provide good integration with key Google services. I am not sure looking at the screenshots that Cr OS was anything other than LXDE + Chromium. I have tried to use a range of technologies to virtually recreate every aspect of Chrome OS.

I also spent some time evaluating Evolve OS. I am a big fan of Ikey Docherty's work and clearly the appearance of the Budgie desktop is inspired by Chrome OS, but that's as far as it goes. When I started developing Chromixium, Evolve was in a very early and undeveloped state. It was not finished and buggy in Ubuntu. I do intend to keep an eye on this project though, and if at some point in the future it becomes a better alternative to use Budgie rather than Openbox+Plank+LXPanel+Compton then I will probably switch.

My inspiration came because I couldn't get Chromium OS to do what I wanted which was install non-Chrome, Linux apps and have good integration with Google apps. You might know that Chromium OS needs Google APIs compiling just to get things like Google Drive to work? I also want to print directly to my printer, not necessarily via Cloud Print. Chromixium was the result of my experiments to see if I could do this on a conventional Linux base system. Once I was happy with the concept, I decided to share my project with the wider Linux world. 

There are literally hundred's of traditional desktop substitutes in the Linux world. There is 1 deprecated and possibly one other Chrome OS inspired system that you noted. I don't see Chromixium as "yet another Chrome OS substitute" - I wasn't aware the Linux world was awash with them.

PS The latest Alpha is out now for testing and feedback :D

Kind regards
RichJack aka rv_happy
[http://chromixium.org](http://chromixium.org)

---

### Post by mJayk on 2014-11-29
Looks very nice two quick questions if anyone has the time to answer;

- How stable is it for a production machine (writing my thesis)
- How compatible is it with debian based packages (in general)

---

### Post by rv_happy on 2014-11-29
Hi mJayk and thanks for your interest :)

> **mJayk said:**
> Looks very nice two quick questions if anyone has the time to answer;

- How stable is it for a production machine (writing my thesis)

At the moment, Chromixium is in Alpha status. What does that mean? Well, it doesn't mean it's unstable, what it means is that it contains a number of untested and experimental components. But the base system is Ubuntu 14.01 LTS, so it's not going to break. As these components mature, then it will become Beta and then eventually I plan a stable release in Q1 of 2015.

There is one issue at the moment which is actually an upstream bug in the current version of Chromium in the Ubuntu repos, which is currently making the browser crash when trying to access the Chrome Store or the new Maps app. However, there are instructions on the Wiki for swapping out Chromium with Google Chrome which is stable:
[http://chromixium.wikidot.com/switch-to-chrome](http://chromixium.wikidot.com/switch-to-chrome) 

If you write your thesis on Google Docs then it will be automatically saved to the cloud and you can work on it anywhere from any computer/device connected to the Net. If you install LibreOffice to write your thesis, then just make sure you save regularly and back up (but that is common sense advice).

Having said that, I am not generally saying "Yes go ahead and install on a production machine", but that choice is yours...

> - How compatible is it with debian based packages (in general)

Chromixium is based on and fully compatible with Ubuntu 14.04 and pulls packages from the Ubuntu Trusty repos, So it is a debian-based distro and you can install .debs and connect to 3rd party PPAs.

I hope this answers your questions.
Regards
RichJack aka rv_happy

---

### Post by vk2gpz on 2015-03-29
Huh this is neat I might try it

---

### Post by serge_o on 2015-04-05
Could it be run from a USB flash drive without installing ?

---

### Post by roger_1960 on 2015-04-28
Well

Just installed the first stable release - chromixium 1.0 on an Asus netbook.  Great - especially if you use chromebooks.  All the ubuntu facilities plus the clean chromebook interface..

---

### Post by vtpoet2 on 2015-04-30
> **rv_happy said:**
>  PS The latest Alpha is out now for testing and feedback :D

Kind regards
RichJack aka rv_happy
[http://chromixium.org](http://chromixium.org)

And just noticed stable was released. What's the memory footprint for your DE, out of curiosity? Is it a good DE for older systems? And yeah, soon as I'm around a high speed connection, I'm going to download and try it.

---

### Post by night_sky2 on 2015-05-02
> **vtpoet2 said:**
> And just noticed stable was released. What's the memory footprint for your DE, out of curiosity? Is it a good DE for older systems? And yeah, soon as I'm around a high speed connection, I'm going to download and try it.

It's around 300-350~ MB RAM at idle for the 32 bit release, so pretty much like XFCE (Xubuntu). Therefore it should run quite well on older hardware.

---

### Post by th3pun15h3r on 2015-06-03
I actually tried it on my acer c710 chromebook that I replaced with seabios to install any Linux distro natively.  It looks beautiful and is very polished!  I had a couple issues when using it.  First the right click surprisingly took a very long time to appear when right clicking especially for openbox.  Secondly, when I would open chrome or chromium the browser border would be there but the rest of the browser wouldn't show up, instead showing the desktop.  I can't remember if I had to minimize and remaximize the window to make it work.  I didn't know it had a compositor installed.  Maybe the one I tried was a earlier build.  I'll experiment with it maybe on my older netbook.  Also have you consider adding opensnap so you can aerosnap windows and skippy-xd?  Both work well other than having to maximize and de maximize the windows to get the windows to go back to default.  I was using both in a project when i was making a lightweight os similar to elementary and Mac to be beautiful and fast for netbooks and machines that couldn't run elementary with the compositing effects.

Anyway, thank you for sharing your custom distro!  Looks great, and definitely fills a want in the Linux community.

---

### Post by kagashe on 2015-06-03
Can I make EFI Bootable USB stick?
Can I use it on 64 Bit Laptop?

Kamalakar

---

### Post by rv_happy on 2015-06-05
@th3pun15h3r, thanks for your positive feedback and glad that you like the concept. The slow right-click menu is fixed in a recent update to 1.1.Aerosnap is included and bound to Super+alt+arrow keys.

@kagashe, EFI boot is capable with the 64bit RC version. Works best with secure boot off for the time being. Still working out a few issues with the RC but wouldn't hurt to try it in live mode :)

---

### Post by kagashe on 2015-06-05
> **rv_happy said:**
> @kagashe, EFI boot is capable with the 64bit RC version. Works best with secure boot off for the time being. Still working out a few issues with the RC but wouldn't hurt to try it in live mode :)Downloaded 64 Bit RC1 and running it now on live usb, started liking it. It is running with Secure Boot on my machine.

Kamalakar

---

### Post by him610 on 2015-06-09
For anyone who is interested:

RichJack recently released Chromixium 1.0. It is a 32b version, but he is also working on a 64b version also.

Download:
[http://chromixium.org/]("http://chromixium.org/")

Forum:
[http://chromixium.freeforums.org/index.php]("http://chromixium.freeforums.org/index.php")

---

### Post by neu5eeCh on 2015-06-12
Just installed and am using -- finally. Couple observations:


[LIST=1]
[*]There doesn't seem to be an autologin option, or at least one that works.
[*]There doesn't seem to be an option to turn off the auto-lock screen option. This is a deal-breaker since I like to stream while I'm working. Every time the system autolocks, it also kills the streaming.
[*]Right-cliking and choosing Applications results in a five to even second delay. Really weird.
[/LIST]

Other than these problems, it's lightweight and impressive.

---

### Post by guy-dewaerheid on 2015-07-22
Hello from Belgium,

I've installed it on an old tower and it works (No other Linux version works on thet tower except Handy Linux). I tried to to install several other programs, and that works too. I did not find Firefox as alternative browser but maybe I did not look far enough. This OS replace with a lot of plus points Handy Linux. Many thanks for such release. Adopted of course !

---

### Post by robot_chicken_parm on 2015-12-02
I love this distro.  I have installed it, and have been using it on a dedicated machine.  Here are some tools I am playing with in order to enhance the experince.  The first is Grive Tools, which is available and working perfectly on Chromixium and other Ubuntu 14.04 based systems, [http://linuxg.net/how-to-install-grive-tools-1-4-on-ubuntu-14-0413-1012-10-and-linux-mint-1614/](http://linuxg.net/how-to-install-grive-tools-1-4-on-ubuntu-14-0413-1012-10-and-linux-mint-1614/).  The next is called OwlReminder, found at [http://chromeism.com](http://chromeism.com), which has other tools as well.  I am interested to know some of the other tools and ideas anyone has to further the blending of the Chrome and Linux experiences, and make the experience even more seamless.

---

### Post by robot_chicken_parm on 2015-12-05
I was thinking, it would be cool if support for android apps could be native to this distro in a future release.  There is a way to run android apps in Chrome/Chromium using something called Archon.  With the talent you have for seamless blending of desktop experiences, maybe it could go further.

---

### Post by mystics on 2015-12-05
> **robot_chicken_parm said:**
> I was thinking, it would be cool if support for android apps could be native to this distro in a future release.  There is a way to run android apps in Chrome/Chromium using something called Archon.  With the talent you have for seamless blending of desktop experiences, maybe it could go further.

Just to point out, the developer doesn't appear very active on here. Their last time active was in June. Chromixium does have its own forums, though, and I'd imagine that they're much more active there, so your suggestions have a better chance of being heard there: [http://chromixium.freeforums.org/](http://chromixium.freeforums.org/)

---

### Post by night_sky2 on 2015-12-07
> **robot_chicken_parm said:**
> I was thinking, it would be cool if support for android apps could be native to this distro in a future release.  There is a way to run android apps in Chrome/Chromium using something called Archon.  With the talent you have for seamless blending of desktop experiences, maybe it could go further.
Chomixium is basically a one-man project. I doubt the dev neither as the time or ressources for such undertaking but I could be wrong. The way I see it, the project essentially aims at reviving older hardware by providing a lightweight Ubuntu-based distro that has the look & feel of Google's Chrome OS.

---

### Post by robot_chicken_parm on 2015-12-07
Thanks for the replies.  I am checking out that other forum now.

---

### Post by freeweazl on 2016-02-12
Hi all, 

Just wanted to let you know that Chromixium was Renamed to "Cub Linux".

Website: [cublinux.com]("https://cublinux.com/")

There you can also find the Cub Linux [forum]("https://cublinux.com/forum/")

I run Cub on a somewhat older home laptop. My children use Chrome OS at school so I thought it was a bright idea to speed up the laptop and at the same time provide a more recognizable Look and feel to my kids....

---

