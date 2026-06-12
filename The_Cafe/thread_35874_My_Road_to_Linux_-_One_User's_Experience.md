---
title: "My Road to Linux - One User's Experience"
date: 2005-05-20
forum: The Cafe
---

### Post by Nu-Buntu on 2005-05-20
Here is a little essay I wrote about my path to Ubuntu bliss. Yours may be similar, but I figured I'd share it here.

-----------------------------------------------------------------

My Road to Linux - One User's Experience

Computer operating systems are like religions. They all have their fundamentalist zealots as well as their more moderate adherents. Unbridled zealotry in any form goes beyond the realm of reason and into blind faith. You can talk to many proponents of Microsoft Windows, Macintosh OSX, or Linux, and you will find those who think there own choice is perfect and all others are pure evil. Linux or Mac users deride the Microsoft product as "M$ Windoze", 
"M$ Winblows", and other less than complementary names. As long as they dominate the market, Microsoft will continue to be the target of such disdain.

Yes, I know about the security issues, the questionable marketing practices, product activation and the many other issues surrounding Windows. Even so, one must recognise that Microsoft is a company in business to make a profit. There is nothing wrong with that. Secondly, the de facto Windows standard has no doubt helped the penetration of personal computers into our business and personal lives. The product works with a wide variety of hardware, and for many users, the simplicity it offers is reason enough to stick with it. As for me, I always am looking for more.

I started using PCs when MS-DOS was the market-leading OS. There was no multimedia, no web browsers, and every program had its own user interface. The slash menu of Lotus 1-2-3 and the F-key combinations for WordPerfect were burned into the genetic makeup of my fingers. The mark of a true DOS Jockey was the ability to use the Edlin line editor to edit text files and create batch files. 
Early versions of Microsoft Excel for Windows eventually hit the market, complete with a limited "run-time" version of Windows 2.0 to allow the spreadsheet program to run on any DOS computer. Few people actually owned a full copy of Windows back then, with its klunky MS-DOS Executive text interface and crude icons. The Macintoshes, Lisas and Amigas of the day were far ahead in their implementation of graphical computing.

Despite the quirkiness of DOS programs, there was something very satisfying about DOS computing. Things like mastering autoexec.bat and config.sys; loading ansi.sys to create colorful, customized DOS prompts; and using batch files to create a menu system. Working with the computer at that level is something I enjoyed, and Windows hides all of that deep within its innards.

Those DOS skills and knowledge are, for the most part, still within my head. What I hadn't realized was how much they wanted to get out and be used. I still enjoy working a bit at the C:> prompt. DOS is still as good an operating system as it ever was, but it lacks native support for such modern niceties as USB devices, network servers and other tasks routine to modern computing.

In using Linux, I have found a great amalgam of command-line and graphical computing. Learing the Unix equivalents of familiar DOS commands and remembering to use a forward slash in path names rather than the DOS backslash, and I find I can do a lot of system maintenance from the Linux prompt. Yet at any time, I can use any number of graphical desktops, including the K Desktop Environment (KDE), Gnome and other more lightweight options. Oh, the power! Guys who like cars enjoy tinkering under the hood. Geeks like me enjoy tinkering with our computers at a lower level than Windows typically allows.

I first tried Linux about six years ago, and was impressed at how a team of geographically-separated developers could put something as complex as an OS together. It was particularly impressive that they were sharing their work freely with others. I started with Mandrake Linux 7.2, and found it a little frustrating trying to get Linux to work appropriately with my hardware. I kept checking back on Linux (more properly GNU/Linux) as new versions were released, and gave Red Hat, Corel Linux, Turbo Linux, Storm Linux, Caldera OpenLinux, and a few others a shot at becoming my OS of choice. I have intermittently used Mandrake through versions 9 and 10, but only very superficially, and usually through KDE or Gnome. After rebuilding my system last year, I didn't bother to reinstall Linux, but always having the intention to do so.

Recently, I found out about a new distribution (distro in Linuxspeak), known as Ubuntu, sponsored by a South African company named Canonical. Based on the Debian distribution, Ubuntu is free to use, free to copy, and no clubs to join. Although it shows its newness by a few rough edges, this is one great Linux distro. It comes as a downloadable CD image, and as a bonus, the CD contains some Windows versions of some great free, open source programs. Canonical will even mail you a premade CD at no charge!

Ubuntu Linux is available as a single CD to install on your hard drive, a Live CD which runs Ubuntu without installing it at all, or a DVD that will do either. The standard Ubuntu Linux uses Gnome as its desktop, but you can either install KDE (easy to do in Ubuntu), or download the Kubuntu variant which uses KDE by default. The Ubuntu version I downloaded is the "Hoary Hedgehog" release. The previous version was Warty Warthog, while the next one is to be named Breezy Badger.

The Ubuntu install routine lacks the polish of the latest Mandrake or Novell/SuSE intallers. Eschewing graphical eye candy, Ubuntu installs from text mode. After setting up your hard disk partitions, it asks a few simple questions, then loads the OS and a nice variety of application files onto the system. At the end of this part of the installation, Ubuntu told me it found Windows XP on my system, and reassured me that I should install the bootloader (GRUB) into the Master Boot Record (MBR) of the Windows partition. I have done this with Mandrake in the past, causing no end to trouble getting back into my Windows installation. Since no other distro had ever given me any reassurance on this in the past, it was with much trepidation that I agreed to let Ubuntu proceed.

After it had done this, Ubuntu rebooted my system, and as the BIOS screen went by, I was nervous. Suddenly, a GRUB menu appeared, with Windows XP as a boot choice. I select Windows, and to my surprise, I was back on my XP desktop! Success! Now, back to Ubuntu.

I told Windows to reboot the system, and this time selected Ubuntu from the Grub boot menu. I thought I would be going directly to Ubuntu, but unlike other distros I have tried, Ubuntu went into a text-mode process, doing initial configurations on the software it had installed. Once it was finished with that, I found myself at a graphical login screen. Logging in with the user ID I had created for myself during install put me at an attractive Gnome desktop.

Quickly searching through the menus, I found I had a fully business-ready Linux machine. OpenOffice.org, The GIMP, and other useful tools were ready to go to work. 

This first installation was on a Dell CSx laptop machine that has a D-Link 650+ wifi card. Mandrake and SuSE could not find this device. I opened up the Network configuration in Ubuntu, and the card was there, ready to configure with my WEP key and network SSID. Just like that, I was on my LAN and on the Web!

Opening up the Mozilla project's Firefox browser, I head over to ubuntuforums.org. There I learned about enabling extra repositories of software available. Having used RPM-based distros, and the accompanying dependency nightmares associated with them, I found that all I needed to do was to open a terminal (command line) and type in "sudo apt-get install" and the software name. Ubuntu took care of the rest. Apparently, this is how Debian-based distros all work, but this was my first experience with it. All library dependencies were taken care of automatically. If one wants to go the graphical route, Synaptic is included, which lets you browse for software in the repositories, as well as install and uninstall them from a graphical shell.

A word about sudo. Ubuntu doesn't set up a root account by default. Instead, one uses the sudo command and their own password to perform system maintenance. I like this setup, but if one wants greater security in a multiuser environment, it is a simple command to set up a password for a true root account.

One way that Mandrake has Ubuntu beat in a dual-boot environment, is that is mounts your Windows drives automatically. In Ubuntu, you have to futz with the /etc/fstab file and create directories in the /media directory for each device. This is not difficult, but I had to do a little reading at ubuntuforums about how this is accomplished. Once I figured it out, it wasn't that difficult to do, but for a newbie, it would have been nice if these were mounted by default. The good news is that performing this configuration taught me a bit more about my system and Linux. USB thumb drives and flash media card readers seem to work in the default installation. 

This is where the old DOS jockey started coming out. The more I experimented and tried a few simple script files, the more success I found, and the more fun the Linux command line was becoming. I am finding out that the BASH Linux shell is far more powerful than the DOS equivalent, command.com, or cmd, its Windows cousin. I am starting to feel less like a Linux noob and more like an intermediate Linux user. I am actually having fun just playing around with the system and the OS again. Some people just want a system that they can do certain tasks on, and if that works it is fine. I am not that kind of person. I enjoy digging into the system and learning how things operate. I am starting to wonder what took me so long to make the dive into Linux. Since the success on my laptop, I have also installed Ubuntu on my primary desktop machine with equal success.

I still boot into Windows occasionally at home. I love to play SimCity 4, and use Adobe Photoshop and Acrobat. The Linux equivalents are still not up to their standards, in my opinion. I also must use Windows at work. However, I am finding that well over 90% of the time, I am happily using my Linux installation and getting real work done while learning valuable Linux skills. 

Things I like about Ubuntu:
	* WiFi works
	* The sudo apt-get software system
	* A single CD image to download

Things I dislike about Ubuntu:
	* Windows drives are not automounted

---

### Post by testingubuntu on 2005-05-20
You can get adobe reader version 7 instead of the version 5 default it is a matter of adding a set of repos to your sources.list 

Have you reallly given the gimp a shot?  I love it better than photoshop! 

Good write tho

---

### Post by 1337sithlord on 2005-05-20
Wow nice essay lol.  I used DOS when I was 5, had to ask my dad how to access every program.  Then in 95 i got win95 and never really got into the command based attitude.  Ive learned some simple languages tho, and am going to keep doing so, so Linux is going to grow on me.  Glad it all worked out for u, this OS is awesome lol, a perfect example of how u can have a successful computer without spending a dime, or compromising anything :)

---

### Post by maspro on 2005-05-20
[QUOTE=Nu-Buntu]Here is a little essay I wrote about my path to Ubuntu bliss. Yours may be similar, but I figured I'd share it here.

Things I like about Ubuntu:
	* WiFi works
[/quote]
How really lucky you are.......!  :)

---

### Post by tread on 2005-05-20
Nicely written article. My introduction to Linux was scarier .. for my first Linux installation (which happened a week after I got my first computer :)) I was staring blankly at the screen wondering what this is all about. (That was fdisk .. paritioning time!)

---

### Post by poofyhairguy on 2005-05-21
Wow! As a professional writer let me say- that is good stuff.

---

### Post by Nu-Buntu on 2005-05-21
Thanks for all the comments. It is a first draft, but I figured, "Why not share?"

---

### Post by smog on 2005-05-21
This is a great piece. I think I will use it to show others how they can expect things to go. I have been a Debian user for about 8 years and have also tried many of the other distros you mentioned. I have always come back to Debian because of the flexibility and ease of administration. I now have Ubuntu installed on all of my desktop machines and am working on replacing my server. I love this distro!
I also like to play the occasional game as you have mentioned. I got around the dual boot problem by running Transgaming's Cedega. This is another great linux package. They charge $5/month to update with each months latest fixes. You should take a look at it for you home computers. I am Windows free on everything except my wife's laptop which may also find the light soon.

[http://www.transgaming.com/](http://www.transgaming.com/)

Check it out...

---

### Post by totalshredder on 2005-05-21
[QUOTE=testingubuntu]Have you reallly given the gimp a shot?  I love it better than photoshop! [/QUOTE]
Hehe, not really ;)

Really good read, It's fun to read about other peoples experiences. Not many people settle down without a thrash or two  :-)

---

### Post by David Kaisemann on 2005-05-21
Good work. you must finish it (if not already) and publish somewhere (may be here too).

---

### Post by GarySaved on 2005-05-21
Very nicely done.  I enjoyed reading it.

I tried Linux several times over the years, but Ubuntu is the first that I managed to get everything working on my system.

---

### Post by treris on 2005-06-06
Very well done!! It kinda matches my own experiences as a n00b linux user, my first try at a linux distro was a Ubuntu Live Cd, and when I decided I wanted to go linux I found that the ubuntuforums and ubuntuguide are really great tools for getting help, even for people who are running kubuntu instead of ubuntu

I have since considered switching to SuSe but have found it lacking in its forums and guides. Kubuntu is now my main OS although from time to time I still switch to windows for games and some other stuff, I guess about 5% of my total computer time. 

I would definetly recommend (K)Ubuntu to anybody wanting to switch from windows to linux. And allthough at first some computer skills come in handy (when installing everything) after all that is done and the system is completely set up anybody can use it and keep it up to date using Synaptic, very user friendly even for people who are not very computer minded.

---

### Post by Paul Bramscher on 2005-06-10
My introduction with linux began with Red Hat 5.2 around May, 1999.  I remember it well since it was around the time my first son was born, I had some vacation time, his crying kept my wife up at night and I was able to delve into the OS into the wee hours.  Now having 2 kids and a career, I don't have time to custom-compile drivers for my network card, etc.  And -- fortunately -- I haven't had to.

I've tried various Red Hats up to 9, SuSE from 6.x to 8.x, Debian, m68K linux, and Red Hat AS 3 at work.  I had one linux box, an AMD K6-2 400 MHz running 24/7 for about 4 years crunching SETI@Home work units.  In that time I don't recall it crashing.

I'm most interested in linux because I'm a cheapsake and tinkerer.  Linux has achieved the coveted combination of an OS that allows total under-the-hood control to those with special needs, time on their hands, or a visionary project.  But it's also simple enough for a non-techie to use.   Today I fall into the middle category.  I just want a box to serve up a LAMP stack (linux, apache, mysql, php), sftp, ssh with none of the built-in crippling that the closed source OS's introduce to suck some more money out of you.  Rather than forcing me to pay for my hardware's potential (licenses), linux frees the machine.

---

### Post by hypeiv on 2005-06-10
I always mess around with linux in college but never saw it as a practical main os. However now that I dont game on the computer any more and work 8 hours a day in solaris the weakness of windows command prompt just drove me crazy. I was mainly only using free software like firefox on my PC anyway. I even ran abiword in windows b/c I didn't want to pay for office. I set up Ubuntu on my desktop and I dual boot it on my laptop (but I rarly use windows I just don't want to give up on it just yet) but for my HTPC I have some pretty exact settings I have to run to get my video card to work and I wouldn't dare try to run linux on that... well not yet at least.

The only windows only program I use is DVD shrink and it runs fine in wine.

---

### Post by jpkeisala on 2005-06-10
[QUOTE=Nu-Buntu]http://www.ubuntuforums.org/showpost.php?p=180444&postcount=1[/QUOTE]
 WIFI works also on my Laptop! Acer Travelmate 435. I tried Fedora Core 3, SuSe 9.3 before but Ubuntu was the first one where everything worked without forging around.

I am first time very happy about Linux. Well... GNOME really needs major update, its really behind when comparing to MacOS Tiger.

---

### Post by RastaMahata on 2005-06-10
[QUOTE=Nu-Buntu]Things I dislike about Ubuntu:
	* Windows drives are not automounted[/QUOTE]
I second this.
And dmix for default...

---

### Post by pdk001 on 2005-06-10
it takes plent of time to read that -_-

---

### Post by matthew on 2005-06-11
Hey, great job! Clear, concise and readable. I'm also glad you have had such a good experience.

---

### Post by alive on 2005-06-11
Great story. I've gotta say though that I take issue with this:

"Even so, one must recognise that Microsoft is a company in business to make a profit. There is nothing wrong with that. Secondly, the de facto Windows standard has no doubt helped the penetration of personal computers into our business and personal lives."

Vendor lockin is not good for customers. Things that would otherwise be evil and bad are not automatically okay if someone is profiting from them.

Call me an "anti-vendor-lockin zealot" if you must.

---

### Post by aysiu on 2005-06-11
In some ways, it's like saying the original white settlers in America were just trying to make a profit, and--okay, so they killed a few Native Americans along the way--they still built a great country... and they did.

Even though Microsoft may have paved the way, how they did it was evil.

---

### Post by phen on 2005-06-12
what about mac os x, btw? Does the apple os come with media player and internet explorer integrated in its system? I am just curious, whether MS really has a bad policy and unfair market strategy compared to another operating system vendor. Or are they doing the same thing with media player and internet explorer but aren't blamed because they are smaller?

cheers,

kai

---

### Post by aysiu on 2005-06-12
[QUOTE=phen]what about mac os x, btw? Does the apple os come with media player and internet explorer integrated in its system? I am just curious, whether MS really has a bad policy and unfair market strategy compared to another operating system vendor. Or are they doing the same thing with media player and internet explorer but aren't blamed because they are smaller?

cheers,

kai[/QUOTE]

I don't think the integration of IE into Windows is what people think Microsoft is evil for doing. By the way, though, Safari is *not* integrated into Mac OS X, *and* it can be uninstalled. There is no way to uninstall IE from Windows.

---

### Post by alive on 2005-06-14
But Firefox can't be uninstalled from Ubuntu because yelp depends on it :(

Talk about unfair and monopolistic! (Just jesting, of course.)

---

### Post by carverj on 2006-07-20
> I love to play SimCity 4, and use Adobe Photoshop and Acrobat. The Linux equivalents are still not up to their standards, in my opinion.

A friend seemed to think that games run much faster with Linux, has anyone done a benchmark comparison?

_________________
Success is being able to go from one failure to the next
-W.Churchill

---

