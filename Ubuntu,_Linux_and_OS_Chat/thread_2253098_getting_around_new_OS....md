---
title: "getting around new OS..."
date: 2014-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by leilamoniz on 2014-11-17
hi all;

so i been a new ubunt user now for the past month and so far i can see some great benifits, however at the same time i can see some really hardship to try and adapt into this new OS world.

So ill breif my experience into 2 cat e.g (Pros and Cons)

Starting with Good points:

1.fast internet 
2.fast applicattion loader
3.fast boot time (howeve i did run chk/compar to win vista) and had diference of 5sec to completley load OS/start firefox/youtube/play/load video
4.great cummunity for help and support (love the irc channel) just dont know how to enter the right ones for my needs.


Cons.

1.most apps i need are only available via windows e.g(photshop/dreamweaver)
i know you can load them via the wine,whoever i found this extremelly comlicated and hard at most times/time consuming
2.keep crashing with xbmc and also doesnt install PVR addons as default.
3.cant install my drivers, being a newbie i try installing however the "Make file" is jusst something out of my understanding at this early stage.
4.addtional drivers option doesnt really pull my proprietary drivers (result- poor graphics as compared to windows)


So there is a lot more i can say both ways (good and bad) but im just focusing on the points i find more relevant.
The point of this tread is to see if any new users like my self can comment and maybe help others in understand what to expect/share and explain what they find good and hard or how to get round when changing from windows.

I started with ubuntu 14LTS however i decided to change to xubuntu, has i found more user freindly and faster in comparission to ubuntu. (probally my pc spec nt being the best) but i found even with a few tweaks to speed up OS, system response was not that great, in fact i found windows to be much faster in most common task for that matter., untl i tried xubuntu taht is. Also changing from windows i must say i found in xubuntu a much great comfort browsing through OS. So in this instance i would say is much more user friendly.

---

### Post by buzzingrobot on 2014-11-17
Windows applications are for Windows only.  Wine simulates a Windows environment that allows some Windows programs to run inside it, with varying degrees of success. Wine is not intended to be a magic solution that allows any and all Windows programs to run on Linux. Best to find Linux alternatives than to try to finagle Windows programs into working on Linux.

Linux is excellent at detecting hardware and installing the correct open source drivers. I.e., things should 'just work' unless you have hardware components for which no open source drivers are available. This is unusual these days, but can happen with wifi cards and, sometimes, printers. (if that's the case, post a separate question here with details about your hardware.) You should avoid the Windows-ism of searching the net for drivers to download and install.  That's not how it's done in Linux. (Any archive with a 'make' file contains only source code that needs to be compiled and installed correctly,  They are intended for use by developers, not ordinary users. Avoid them.)

'Additional Drivers' will detect and install the appropriate proprietary driver from the Ubuntu repositories.  If you have a hybrid system -- switchable between onboard Intel video and a discrete video card -- the discrete card must be enabled for it to be detected. You also need to reboot for any new driver to become active.

Nvidia and AMD do not share the source code for their drivers.  They simply release a single compiled file.  As a result, Linux developers can't really be sure what those drivers are doing.

---

### Post by matt_symes on 2014-11-17
Hi

If you *need* windows applications and cannot use any Linux alternatives then do yourself a favour and use windows.

Otherwise you are trying to fit a square peg into a round hole.

Of course, you could dual boot or use some virtualisation software but your main OS should be the OS you *need*.

Kind regards

---

### Post by Rob Sayer on 2014-11-17
I certainly agree that if you *really* need photoshop ... for real work involving publishing that is ... you need windows or a Mac.  It uses proprietary standards like Pantone colors and the file format used by digital publishers.  No matter that any FOSS zealot tells you, Gimp just doesn't compete on those grounds.

But for hobby use Gimp is just fine.

As far as your other issues go, it's quite normal to have to do more configuring on a linux install than with windows.  But people are usually comparing it with pre installed windows, which isn't 100% fair.  If you buy a copy of windows and install it you'll quite often have to install drivers.

It's hard to tell what your issues actually are without knowing what hardware you're using.  When I first installed linux I guess I was lucky.  I knew enough to look up the computer peripherals in windows under system information and then look up potential hardware support issues in ubuntu.  So while my netbook has had issues in linux (apparently fixed in 14.04) I knew what to expect.  Most noobs don't seem to.

One thing that raises a big red flag for me is someone who's as new to linux as you are talking about installing drivers with makefiles.  Be *very* careful what you read.  IMHO ubuntu noobs should stick to here and askubuntu for tech support.  There are good linux blogs.  There are also very bad ones.  The info may be out of date ... never try a solution unless it specifically says it's for your ubuntu release version ... or just plain bad.

The other thing about a lot of those blogs is that they rarely tell you how to undo the changes they recommend if they don't work.  Just because someone writes a linux blog does not mean they actually know what they're doing.

If you're having trouble with your video config I'd recommend starting another thread.  Enter this in terminal:

sudo lshw -C video

and post the results there, using [CODE] tags for readability.

BTW it is not Ubuntu's fault if XBMC doesn't include pvr plugins by default.

---

### Post by mastablasta on 2014-11-17
for each of the issues you can post a spearate thread. your Photoshop/dreamweaver combo is indeed best served on Windows. 

i use GIMP and INkscape on Windows as well. the website we have looks nice using those tools.

---

### Post by stalkingwolf on 2014-11-17
Ill second the statement if you need windows specific software use windows .   you can always dual boot .

---

### Post by leilamoniz on 2014-11-18
thx all for comments.

regarding some replies in connection to graphics and software.

i do understand the best is to run windows apps on its own OS, i was just commenting as new user so far on my overall progress on ubuntu and later xubuntu.

same goes for xbmc, i do understand its not OS fault software keeps crashing & does not come with same defaults PVR as it does for windows.

as to follow tweaks online o improve/change how system handles/responds.
 i only follow/done it to improve system performance in ubuntu and thats why later i just change to xubuntu (found ubuntu some how slow)

the tuts i followed wr found _**[here]("http://m.youtube.com/watch?v=vwBoHZuauL8")**_

Since i saw no improvement i then decided to try xubuntu and folllow the same tutorial and found a slight better response and increase on speed/performance.
Its worth saying i also done few xtras tweaks found **[here]("http://itsfoss.com/speed-up-ubuntu-1310/")** as well. (im now some how concer after reading not to follow anything posted out on web)? can someone advise if this tweaks command are wr safe to use?

The result:

total time to boot/login start firefox and load minecraft as an example on you tube with xubuntu was of (58sec.)

same as above again on windows was 1.03sec. (5 sec diference apart from both OS)


My PC Spec in case it help:


Manufacturer: Acer
Model: Aspire 5920
Processor Intel(R) Core(TM)2 Duo CPU T5750 @ 2.00GHz 2.00GHz
RAM: 2 GB
HDD:250GB

---

### Post by Paul_Simmons on 2014-11-18
I am an old ubuntu user but joined this community recently. It has been always helpful for me, Whatever the problem is mostly there are thread available on that with the solutions suggested by rest of the members.

---

### Post by mastablasta on 2014-11-18
> **leilamoniz said:**
> 
The result:

total time to boot/login start firefox and load minecraft as an example on you tube with xubuntu was of (58sec.)

same as above again on windows was 1.03sec. (5 sec diference apart from both OS)

My PC Spec in case it help:

Manufacturer: Acer
Model: Aspire 5920
Processor Intel(R) Core(TM)2 Duo CPU T5750 @ 2.00GHz 2.00GHz
RAM: 2 GB
HDD:250GB

you shouldn't follow such guides unless you know what you are doing or trying to do. 
having a fast operating system vs. having system that boots fast are two very different things. one could argue that in Linux you can do all in CLI and that one should boot pretty fast. of if not sclit her eis plenty windows managers that will load very fast.

so what is your goal here? if everything should be really fast then get a newer PC. :P

and I hope you are not comparing boot to some fast boot (which is hibernation)

you say computer was slow. that is a bit strange with that setup. is the graphics card intel chip? if so then it is understandable, since the interface is a big heavy and needs good GPU. the lkatest Intel chips do just fine. but I am not sure about the older ones.


though I have to admit that I too am a bit disappointed with Gnome 3 and the "progress" in desktops. Ubuntu 10.04 booted in 14 secs. now it's been a while since a measured the boot (it is easily measured using bootchart) but it does take longer than 14 secs these days. Though some managed to get boot time down using SSD.

but unless you are using some device that is moved arround a lot and need to constantly be turned on and off then there is really no need for extra fast boot time. you can just leave it on.

if you want a cleaner system use Ubuntu minimal iso and then build by adding only the things you need. e.g. don't install Bluetooth monitor/manager if you do not have any Bluetooth device etc. to make if faster use more plain windows theme, use some small picture for background or no picture at all  etc.

---

### Post by leilamoniz on 2014-11-19
"...so what is your goal here? if everything should be really fast then get a newer PC...."

i alwys make use of all i have until i can no longer use them. Why spend if all is working is my way of thinking. 
having said that, maybe if i was rich i wouldnt really care and just go ahead and buy the best money can buy.
(but then i wouldnt be here and also not be very interested in learning or changing or trying a new OS.)

the point or goal was just to share and make conversation (be a bit social) by sharing my first xperience with ubuntu with all new users.
also, since you mentioned, i do want to make my pc fast as possible e.g (boot, loading apps, internet, etc..).

is there any reliable source i can follow instruction to tweak system?
in windows you can change this for pc best performance at a click of a button, is this the same in xubuntu, ubuntu ?

---

### Post by slickymaster on 2014-11-19
*Moved to the ***Ubuntu, Linux and OS Chat*** sub-forum*

---

### Post by leilamoniz on 2014-11-19
> **slickymaster said:**
> *Moved to the ***Ubuntu, Linux and OS Chat*** sub-forum*

eeehhh mano....es tuga, se bem !):P

k bom ver alguem da terra .. vou fexar o topico.

---

### Post by bro2 on 2014-11-19
The biggest use-cases for Linux are for old computers, or if your job involves using Linux (servers or w/e). Or hobbists wanting to learn more about computers. And people that love open source (it's a big deal knowing that your OS isn't spying or whatever on you). For old computers that can't run 7/8 well, Linux is amazing. Way better speed/hardware support then XP in general. Corporate uses are obvious.

For everyone else, dual booting is the best solution (gives choice). I dual boot Win 8 with Ubuntu, and I have the Elementary Freya Beta installed on a USB 2.0 (I love the Pantheon DE!!!). If you want to use an OS on multiple computers, installing a Linux distro to an external/flash drive is a great idea, as I've had 0 issues using Elementary(Ubuntu derivative for those that don't know) with 2 computers...it just loads the relevant drivers on boot, and runs really well off an external drive. Way faster then I expected.

---

### Post by buzzingrobot on 2014-11-19
> **bro2 said:**
> The biggest use-cases for Linux are for old computers, or if your job involves using Linux (servers or w/e). Or hobbists wanting to learn more about computers...  For everyone else, dual booting is the best solution (gives choice).

Dual booting is a choice if Windows is a choice you want to make. ;)

I've been using Linux on the desktop since the mid-nineties.  The last Windows I bought for my own use was the initial XP release.  The reasons I don't use Windows are (1) I don't need to use any Windows applications and, for the things I do want to do, the apps on Linux are better; (2) I don't like how Windows looks, AKA I don't like to look at Windows; the font rendering is headache-inducing, which is odd since MS apparently owns patents that hinder U.S.-based distributions from implementing the patches Ubuntu uses.

C'est la vie & ymmv.

---

### Post by bro2 on 2014-11-19
> **buzzingrobot said:**
> Dual booting is a choice if Windows is a choice you want to make. ;)

I've been using Linux on the desktop since the mid-nineties.  The last Windows I bought for my own use was the initial XP release.  The reasons I don't use Windows are (1) I don't need to use any Windows applications and, for the things I do want to do, the apps on Linux are better; (2) I don't like how Windows looks, AKA I don't like to look at Windows; the font rendering is headache-inducing, which is odd since MS apparently owns patents that hinder U.S.-based distributions from implementing the patches Ubuntu uses.

C'est la vie & ymmv.

That's awesome. But for a lot of people converting from Windows, one of their Windows programs mite not work via Wine (for me, Word 2007 works, but Powerpoint won't launch). Rather then jumping to Linux 100%, I like having a smaller Windows partition for convience sake (like if I don't feel like troubleshooting Wine). But yes, if someone grows up using Linux (like those using Mac), then they won't be dependent on Windows and won't care about dual booting.

ps: Ubuntu's font is great :)

---

### Post by leilamoniz on 2014-11-20
> **bro2 said:**
> it just loads the relevant drivers on boot, and runs really well off an external drive. Way faster then I expected.

thats sound interesting...if i then want to just load my pc driveres and use pc for internet and xbmc use, would i be able to discard all other option that come with ubuntu or xubuntu or any other OS for that matter to work round only based on my needs?

Was this what you wr trying to say, or am i getting this wrong?

---

### Post by ian-weisser on 2014-11-20
> **leilamoniz said:**
> thats sound interesting...if i then want to just load my pc driveres and use pc for internet and xbmc use, would i be able to discard all other option that come with ubuntu or xubuntu or any other OS for that matter to work round only based on my needs?

Yes you can customize your kernel by recompiling from source with fewer options.
You can also add/delete software packages using the Software Center.
You can also replace some packages entirely with customized, compiled applications....

But compiling is not easy for beginners. There's a learning curve. Your customizations limit our ability to help you when you get into trouble.
It also, in my experience, does not much improve or speed your system. Changing from HDD to SSD, increasing RAM, and other hardware tweaks often make a much bigger difference.

---

### Post by bro2 on 2014-11-21
> **leilamoniz said:**
> thats sound interesting...if i then want to just load my pc driveres and use pc for internet and xbmc use, would i be able to discard all other option that come with ubuntu or xubuntu or any other OS for that matter to work round only based on my needs?

Was this what you wr trying to say, or am i getting this wrong?

Interesting question :). You should read the comment above mine (and if compiling is unfamilier to you, consider a lightweight Linux distro like Ubuntu MATE or Xbuntu, which use lightweight DEs.

However, no, when I switch computers, my Linux distro loads ALL relevent drivers for the new system. I don't have an option to configure it to load less.

Also lol I dunno how lightweight this is, but Justbrowsing: [http://justbrowsing.info/](http://justbrowsing.info/) (seriously, it can only do web browsing)

---

### Post by leilamoniz on 2014-11-24
so i downloaded and run justbrowsing on very ol spec pc (256mb ram) and unfortunnatley i didnt go well.
by this i mean to say it did boot but i didnt run.

i then downloaded xubuntu 9 and installed as it only requires 196mb ram...so this isnt slow but after an update i was able to get ubuntu software centre, wr i been able to downalod and install flash and able to run on my pc when browsing through youtube videos, etc...

anyways, thanks all for your comments and suggestions.

Leila

---

### Post by mastablasta on 2014-11-25
256MB ram :-O

I have one like that. and 32MB of that small RAM are taken by the GPU. I used Chrunchbang. however if I wanted to use it just for browsing the easiest would be to install debian netinstall or better yet ubuntu minimal and then just install a windows manager (openbox, iceWM, JWM) and flash.

you can also look at Bodhi or ToriOS - both Ubuntu based and extremely light with not many programs installed by default. so you can only add what you need.

software center is not necessary as it is easy to install what you need with a simple apt-get command.

---

