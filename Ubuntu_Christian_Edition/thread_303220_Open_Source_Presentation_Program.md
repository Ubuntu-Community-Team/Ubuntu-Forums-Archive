---
title: "Open Source Presentation Program?"
date: 2006-11-19
forum: Ubuntu Christian Edition
---

### Post by jordoex on 2006-11-19
I was wondering if there was a good open source presentation program like PowerPoint or Media Shout(you can google media shout to find about it and how how much it costs; I saw it being used at a youth retreat), especially geared towards worship singing.  Otherwise, I've thought of programming one myself.  Currently I know Java and could learn C++ easily. Tell me what you think!

---

### Post by GameGod on 2006-11-19
[OpenOffice]("http://www.openoffice.org") has a presentation program that's a pretty good replacement for MS Powerpoint...

I wish there was something more slick though. The ill-fated Agnubis never really took off, and [Criawips]("http://www.nongnu.org/criawips/") (which doesn't seem very advanced) hasn't had a new release in over a year (is it dead?)...

---

### Post by loell on 2006-11-19
i think openoffice impress is already adequate when it comes to presentation in community gatherings and church worship, you'll just gonna have to befamiliar with the tool, since your into programming too, ooo impress has an api, so that it can be extended.

---

### Post by jordoex on 2006-11-20
Yeah, I know about OpenOffice, just I'm kinda annoyed with Impress since I have had some major problems with it while presenting (Blue screen of death, I don't have Linux on my family's main computer, just Xubuntu on my own P2).  I don't know If it would work properly on different computers, it probably will.  The main feature that I really would like to put in if i program my own is to have visualizations (like most media players) from a mic or line in input.  But I know if I program my own i'll have to either make my own visualizations and/or figure out a way to import visualizations from another program somehow, which means looking throuh a myriad of libraries or spending a lot of time making my own.  

However, if this can be done in impress(although i might have to learn C++ to hack OOo) or if there already is something out there already(i'll look now) then that's exactly what I need.

The main reason why I want this is that I'd like to bring something more to the worship sessions for the teen weeks at the church camp I volunteer at in the summer.

*edit* looked, didn't find any macros or plugins that did visualization for OOo, Currently looking at API

---

### Post by garybrlow on 2006-11-20
If you are running your presentation on a windows machine you can use the portable version of OpenOffice.Org and a host of other useful applications at [http://www.portableapps.com](http://www.portableapps.com) it requires no installation and runs on the fly either locally, via usb, or on CD. You can also export your presentations as flash animations if you want.

cheers :-D

---

### Post by tuxcantfly on 2006-11-20
or, another way to do it is to export them as pdfs, and have them automatically start in fullscreen mode

---

### Post by silvagroup on 2006-11-20
Not sure if this is what your looking for but it maybe worth looking at [http://lds.sourceforge.net/index.shtml]("http://lds.sourceforge.net/index.shtml")
I installled it and messed with it on the computer seems like a good program. I am just keeping it in the back burner till I have the need for it.

---

### Post by sebastiansantoso on 2006-11-29
> **silvagroup said:**
> Not sure if this is what your looking for but it maybe worth looking at [http://lds.sourceforge.net/index.shtml]("http://lds.sourceforge.net/index.shtml")
I installled it and messed with it on the computer seems like a good program. I am just keeping it in the back burner till I have the need for it.

I'm using old 'celeron' machine with just 32MB of RAM. I plan to replace its OS (currently windows) with DSL. Almost new to it, could u tell me how i can install this "Lyricue" program on DSL? 
I've read the manual of how-to-install Lyricue, but, you know, my Unix knowledge just way to far to understand that.
So, please be more specific when you tell me what to do (i.e. the command line, step by step) ... Please.....
Many thanks before.

---

### Post by silvagroup on 2006-11-29
It's been a very long time since I have looked at DSL. So I am not very familiar with it. You may want to check on the DSL user forum for instructions. I did a quick look at the DSL site and it seems likely that Lyricue could run on DSL. You need to know this to install mysql which is under testing category [HTML]http://www.damnsmalllinux.org/wiki/index.php/FAQ#MyDSL:_Installing_Extensions[/HTML]
Next check this link [HTML]http://damnsmalllinux.org/wiki/index.php/Apt-get[/HTML] you have to have a DSL installed in standard/enhanced from what I can see on the site and because it's not a pure Debian system some of the .deb programs may not run (check the warning at the bottom of the wiki page).
You may want to try xubuntu it has a small foot print, not as small as DSL but it will have allot less problems with deb applications.
After you have done all the above then try the instructions for the debian install in Lyricue site again, you only need to go to a text editor open /etc/apt/sources.list and add ```
deb http://www.adebenham.com/debian/ ./
``` to it.
Then run synaptic from DSL and you should be able to install Lyricue from Synaptic. [HTML]http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=5;t=15811;hl=installing+deb[/HTML]
Hope this helps some or gets you turned in the right direction anyway:)

---

### Post by doobit on 2006-11-29
It's also not difficult to make .dsl packages from .tar.gz packages. They have a tutorial on their wiki.

---

### Post by peanut butter on 2006-11-29
it probably wont run on 32mb ram, as it requires mysql.

---

### Post by eg-maverick on 2006-11-29
> **silvagroup said:**
> Not sure if this is what your looking for but it maybe worth looking at [http://lds.sourceforge.net/index.shtml]("http://lds.sourceforge.net/index.shtml")
I installled it and messed with it on the computer seems like a good program. I am just keeping it in the back burner till I have the need for it.

This is close to what I am looking for. I would like an equvalent to Sunday Show Plus for linux. This doesn't appear to support dynamic (video) backgrounds.

---

### Post by Darrious on 2006-11-29
Has anyone heard of Easy Worship.

---

### Post by doobit on 2006-11-30
I tried lyricue last night. It seemed to install OK, but I can't get it to open eith by the icon in the menu or in the terminal. There was also a problem downloading the interface. The checksums didn't match.

---

### Post by den benne on 2006-11-30
I've heard of fancy presentations made in latex...

---

### Post by sebastiansantoso on 2006-12-05
> doobit I tried lyricue last night. It seemed to install OK, but I can't get it to open eith by the icon in the menu or in the terminal. There was also a problem downloading the interface. The checksums didn't match.

Is it already solved? How do u solve it?

> doobit It's also not difficult to make .dsl packages from .tar.gz packages. They have a tutorial on their wiki. 
Running on Xubuntu.

> Darrious Has anyone heard of Easy Worship. 

Unfortunately, that is a shareware...

> peanut butter it probably wont run on 32mb ram, as it requires mysql. 

It's ok. Currently running on Xubuntu, under Duron 850, 256DDR.

@Silvagroup
My church doesn't have an internet connection. So the only feasible option is to do it manually..

I'm taking your advice (poor my 32MB machine..., i guess it'll become rubbish), and installed Xubuntu 6.06 under Duron 850, 256 DDR (is it enough?). I've also already download the lyricue.193.deb package. What step next? What other dependencies (MySQL, Pearl, gtk-perl stuff?
Anyways, "Silvagroup" (i don't now precisely your name is...), I really need more elaborate command line installation instruction. Like:

1. run in terminal mode, Code: xxx/xxx/xxx
2. unzip the package, Code: .../..../.....
3......
4....

Sorry, if I'm wasting a lot of your time, since like i said before: I'm definitely a nuxbies.

---

### Post by doobit on 2006-12-05
To manually install a .deb package un Xubuntu terminal:

sudo dpkg -i </packagepath/packagename.deb>

Carefully watch the output for any errors or dependancy issues. If there are unresolved dependancies, then you will need to go get and install those packages.

With 256MB of RAM and a 512MB swap file you should be able to rn Open Office Impress just fine, however, and it's a very nice program.

---

### Post by silvagroup on 2006-12-05
Sorry haven't checked the post for awhile.
When I installed lyricue it was on Kubuntu, had all the dependencies already installed and it worked great right out of the install.
Haven't tried it with Xubuntu, because I haven't tried Xubuntu, but it should not be too much different.
As for the install doobit's got it down. As he mentioned you may also want to try Impress, it's the linux answer for power point. You don't have some of the features of lyricue but then you may not need them all anyway.
As for your dependencies use synaptic to install and to check if they need to be installed, that's the easiest way to install them. Do this first and you may not have any other dependency issues, it may just install. I already had these in my Kubuntu so I had no dependency issues. You can install these from your install cd. You will need the programs perl and mysql. Then proceed with doobit's process and you should be up and running.
Not having used xubuntu I can not give you a blow by blow but I think synaptic will be a right mouse click menu option on the desktop as more than likely also terminal. Doobit maybe has more info in that regard. You could do it from terminal but I am trying to keep it simple, goes well with my simple mind.

---

### Post by sebastiansantoso on 2006-12-05
It's true, and I prefer to choose that simple one. Unfortunately, as i said before, I have neither a modem nor internet connection.
Already download the dependencies (8 app.), from ubuntu packages and will try to install them first.
Impress doesn't have lyricue-free-distraction and dual display features, which both are necessity.

---

### Post by sebastiansantoso on 2006-12-06
Dear All,

When I try to install the dependencies with package installer, they keep showing errors: "dependencies is not satisfied." or "cannot install mysql-server."
Previously, when I try to install Lyricue.deb package (in the terminal, using sudo dpkg), the output was:..."however,xxx not installed..." (xxx is the dependencies and the output only shows 8 broken programs. I have it all downloaded, put it in the /home/programfiles folder).

Am I in the right direction of installing something in ubuntu, manually?:confused:

---

### Post by silvagroup on 2006-12-07
[http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/")Yes you are here's a link to install deb's, I keep it close by at all times 
Also this link from another post may be of help since you do not have a internet connection [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html]("http://www.debian.org/doc/FAQ/ch-pkgtools.en.html")

---

### Post by Darrious on 2006-12-08
I've been following this post and have had similar problems until the deb.

Thanks for the deb works fine now.

---

### Post by silvagroup on 2006-12-08
> Thanks for the deb works fine now.
"Praise God from wham all blessings flow!"
How are you coming along sebastiansantoso.

---

### Post by sebastiansantoso on 2006-12-11
@Silvagroup: Almost give up on this.....](*,) 

> When I installed lyricue it was on Kubuntu, had all the dependencies already installed and it worked great right out of the install I ran Kubuntu, but the dependency problem still persist.... :( 

> I already had these in my Kubuntu so I had no dependency issues. You can install these from your install cd.
Can you describe in more detail?

> You will need the programs perl and mysql
already download it. How do I manage those?

Refer to: "Update or Install Applications on Debian/Ubuntu Without an Internet Connection", can i do it with machine running on Kubuntu-Live CD? It is strictly forbidden to install other OS in my office.

---

### Post by silvagroup on 2006-12-11
sebastiansantoso
What os are you using on the computer you want to install lyricue and what os are you using on the work computer, I know it's a CE forum but I'd rather not assume.
Ubuntu/Kubuntu/CE/Ichthux (just to name a few of the *buntu's),5.10, 6.06 or 6.10? 
Let me install the os again and I'll go through the process myself once again to be able to better assist you.
I switched form *bunut's to another os awhile back.
I have an extra hard drive I use for messing around with different programs and settings so I'll do your version of the os and do it again. 
And if I remember correctly you have no internet connection on the system you want to install lyricue onto?
It will take me a couple of days after you give me the information.
God bless and thank you for your patience.

---

### Post by sebastiansantoso on 2006-12-12
@Silvagroup,

It's me that should thank to you..:)

Start from the very beginning,
1. I install the DSL 3.0, but as i read the threads on Lyricue community, saying it'll be pretty hard to install Lyricue 1.9.3 on DSL since the OS doesn't have gnome, perl or ehmm... i can't remember, so I'm taking your suggestion, that is
2. Installing Xubuntu 6.06, which is the lightest version of Ubuntu (RAM constraint), but stuck with dependency errors. After reading and getting some advice from Chris Debenham, the author of Lyricue, and Andrew Walbran, still doesnt't work... (obviously, it's not their fault). So, i review all the mail that comes to me, and reply messages on every threads that I've been asking the same questions. Finally, I make my own conclusion: that it should be much more simple if I install Lyricue in Kubuntu/Ubuntu with their more complete package, so I'm taking my last effort
3. Partitioned the hard drive with Gparted, and install the Xubuntu 6.06 and Kubuntu 6.06. But, again, I'm stuck with the dependency errors....

Anyways, Christmas is coming and running out of time already, I chose the easiest windows-way, enter the freeforchurch.com, and download the freeware "worship software" (BeamIt, Luminous, ScreenMonkey, EasiSlides, OpenSong, etc....). Haven't try them at this point of time. But, it should be an easily achieved task with windows setup, I assume....

Your effort, to give a me a step by step of how to install Lyricue 1.9.3 on Kubuntu 6.06 (If you don't mind DSL 3.1 also :) ) with no internet connection, will be highly appreciated :-D

I'm using XP Pro SP2 built 5.01.2600, in my office.

in Christ,
Sebastian

---

### Post by silvagroup on 2006-12-13
Well God bless you and I pray things go better with windows.

---

