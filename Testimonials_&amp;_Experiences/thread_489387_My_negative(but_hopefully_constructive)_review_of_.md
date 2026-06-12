---
title: "My negative(but hopefully constructive) review of Kubuntu"
date: 2007-07-01
forum: Testimonials &amp; Experiences
---

### Post by Noremacam on 2007-07-01
I'm an enthusiast who enjoys trying out different distributions, and every time I install linux I encounter all sorts of incredibly annoying errors and hurdles that have to be wrestled through. When I installed kubuntu last night, I decided to write down every error and challenge that I faced running it. I'd like to stress, that I did dumb myself down a little bit for this to put myself in the shoes of what a new(but intelligent) user would try to do, as I have actually been using linux for a couple years now. But rather than argue that it simply isn't a polished interface, I'll get into the deep and dirty details instead.

Problems with using Kubuntu:
Installation went fine. I dedicated an entire drive to kubuntu because I didn't want to risk repartitioning issues.

Opening up Konqueror; spent over an hour(no exaggerations) trying to change single click to open files  to double click. I also tried installing Dolphin file manager to see if I could change the settings in the preferences on that program. Nope. Gave up and looked it up on internet forums. I eventually found it on ubuntuforums.org. I had to use a mouse configuration utility(?!) in kcontrol(which doesn't exist in the K programs menu) to change it to double click. The system settings program has no mouse configuration utility in it. Why is a preference for konqueror in the mouse config instead of in konqueror preferences? Why must I launch kcontrol from the command line?

Decided to use konqueror as my main web browser. Forward and back buttons on my mouse don't work. When using the back button, I get error messages containing information that I last highlighted on the page. I use the middle mouse button to close the tab(like on firefox) and I get another error message filled with garbage. Apparently I have to right click the tab and then choose close. I cannot get the middle mouse button to behave correctly(or at least the way I want it to). At this point I give up and I install firefox, which behaves more or less like it's supposed to. I don't like the non-native look, but at least when I middle click to close a tab I don't get error messages.

Apparently my back mouse button also serves as the middle mouse button(or at least they have the same effect). There is absolutely nothing in kcontrol or in the System Settings to correct this behavior. Windows 2000 supports using the back and forward buttons out of the box. However in 2007, 7 years later(almost 8 if you note the fact that win2000 actually came out in late 1999), linux still hasn't caught up with this. This little detail just boggles my mind. I gave up trying to get my mouse buttons working for now.

Knetworkmanager(just like the nm-applet in ubuntu), won't stop asking me for a password to login to my home network every time I turn my computer on. So now I have to put my password in twice before my computer is ready to go. No option could be found in the applet to change this behavior.

I installed the program ntfs-config to setup my 2nd internal drive(which is ntfs). After running it my drive did not appear on the desktop, but being resourceful I looked in the /media folder. There I find the sdb1 folder and open it and it's empty. So in other words, ntfs-config failed silently without any error messages so I have absolutely no idea why I can't see the contents of my drive. After countless rebooting with no results, I discovered that if I turn off writing, I can read the drive. This makes no sense to me. However, even though I got the drive to read it still did not show as an icon on my desktop. Eventually I'll need to re-enable writing, as this is my media drive as well as my backup drive, and I'll inevitably want to copy music/video/documents to it.

Now that I have it running I decide to install and use vlc to play my favorite episode of "whose line is it anyway" which I had backed up to my 2nd drive. VLC plays it like a champ. Awesome. I close the program. The sound continues. The program, in spite of being closed, is still running and playing the audio. The only way I could stop the sound was to restart my computer. I later found the program Ksysguard, and in the "process table" tab I found "wxvlc". I couldn't find it beginning with V, but thankfully I caught wxvlc. I right click to end process/task, and that option is not available. Under the "send signal" button SIGKILL looks promising. Do I want to send the signal? You bet! Huzzah! I finally got vlc to exit!

So, by now, I'm getting tired of 1024x768, so I right click the desktop, and go to Configure Desktop. Well crap, there's no options in any of that window to change resolution, which is just like how it is in both ubuntu and in windows. Luckily, while mouse config does not exist in System Settings, Monitor and Display settings do! I want to use 1152x864. The max resolution I'm allowed is 1024x768. Ugh. I later discover by reading that the nv driver sucks **** and determining acceptable resolutions. OK. I install the nvidia video driver. I go into my /etc/X11/xorg.conf file and make sure the driver is set to use "nvidia"(and it was!). I restart my computer. There's the nvidia logo! I bet it's working now! I'm excited by my progress. I go back to the System Settings, go to "Moniter and Display" and ... oh crap. 1024x768 is still the highest resolution I can choose. It looks like changing resolution is almost harder than pulling teeth. 

Luckily, I found Nvidia Settings in the Settings submenu of the K menu. Yay. I run it, click on the X Server Display. I can change the resolution to 1152x864 now! Huzzah! I hit apply, and it works!!! I hit save to x configuration file. Ahh. Finally I'm getting some leverage over my computer.... until I restart. In spite of saving to the x configuration file, when I reboot I'm left with 1024x768 AGAIN.

So now, when I turn on my computer, I must, enter my password twice(one to login and another to get on my own network), and then run the nvidia utility and change the resolution. I must do this every time on startup.

Last night I downloaded secondlife from secondlife's website and I double clicked and opened the tar.bz2 file. After waiting a minute for it to open I clicked the topmost folder and began to drag it to the desktop. At that point I'm delighted with an error message "Error - Ark; Could not start a subprocess." OK. At this point my mouse cursor changes into an X, but clicking luckily reverted my mouse back to normal. Fortunately the extract button let me actually extract the contents of the file(although I had the extra step of pointing it to my desktop, instead of my home folder).

Lastly occasionally, at random, when I start applications from the K menu, I see it's icon bouncing away from my mouse cursor and after waiting forever it stops and no program launches. I have no idea why. Sometimes launching it again works; sometimes it doesn't. It happens so much at random it's hard to replicate. It doesn't appear to be any specific program.

So here you have it; my user experience with Kubuntu. The desktop is so unpolished in certain areas it takes all kinds of hacking(and forum hunting) to make it run right. I'm confident that all(I hope) of the problems I listed have solutions, but these are crazy. These are errors that should've been fixed before kubuntu was ever released. I actually know the solution to some of these problems, but I intentionally was doing my best to avoid the command line(and subsequently command hunting on the internet), to show how painful it would be to try to use common sense when setting up your computer. Fantastic operating system and desktop, especially when you consider it was all done as a community effort but... the lack of polish renders it *almost *unusable to me. 

Perhaps, I'll do another review of Ubuntu and see how that goes. I'm much more familiar with it, but I have bugs with it as well, but I never took the time to write them down, so perhaps next time I try it(probably v 7.10),

---

### Post by wolfen69 on 2007-07-01
i have had a few very minor issues using kubuntu, and felt it wasnt quite for me. however, installing ubuntu, i had NO issues. and there are people out there that havnt had the problems you've had with kubuntu. so it's most likely a hardware compatibility problem. installing ntfs-config (will show up in Applications/System Tools) will allow you to read/write to your drives. or try ubuntu, and see if the situation improves.

---

### Post by lunarcloud on 2007-07-01
I also hate the kde wallet system that makes you input your password in knetworkmanager.

And... guy, the mouse settings for single/double click are right in the default systemsettings, although double click SHOULD be the default.

Kubuntu is one of the few kde-centric OS's that doesnt have resolution in the configure desktop area, I find that weird, but it's just as easy to go to systemsettings.

Your mouse isssue is a common one that needs to be fixed.

VLC is great, but kaffeine is also a VERY good media player nowadays.

Killing a program is easy if you enable the kill cursor, kust CTRL ALT ESC and your cursor is a skull and crossbones ready to close ANYTHING you click without argument.

***

I do feel that they haven't taken as much pride in kubuntu as lots of cool new managers advertised for feisty aren't available in kubuntu. 
I want ntfs, restricted module, and desktop effects managers on kubuntu, and think it's stupid to exclude them in kubuntu because no one has written a Qt version yet. I'll take the gtk one for now!

---

### Post by Scotty Bones on 2007-07-03
I have also had a few issues with kubuntu.  the most annoying one that i have come across is that Adept and automatix don't play nice with each other.   Using either one means that the other won't work unless i restart, telling me that apt is already in use.  no such problem using synaptic and automatix in Ubuntu (or linux mint for that matter -- love the mint menu and all the other preinstalled goodies, it saves me a lot of time).  Although I do, for the  most part, like the look of kde, I do have to agree that its implementation in kubuntu leaves a lot to be desired in the way of feel and functionality.

---

### Post by wirelessmonkey on 2007-07-05
Scott Bones: You can apt-get synaptic, which works just fine, and honestly I've never had any problems with automatix.

zarquad: I prefer Single Click. Why should double be default?

p.s. multi button mice can/must be configured in xorg.conf  my back, forward, scroll, press-scroll, etc... work fine.

---

### Post by Geekkit on 2007-07-06
Yep. Same frustration from me, just different problems. I also congratulate you in posting a complaint thread about Kubuntu and not being accused of spreading FUD - you must be wearing anti-troll lotion or something. ;)

---

### Post by bgmke7 on 2007-07-07
i had some of the same things when i tried kubuntu.programs wouldnt start,firefox wouldnt work,and things just didnt work well together.i just went back to ubuntu.i seem to get along with it much better.

---

### Post by travist120 on 2007-07-11
Haha, honestly, I hate the way Kubuntu works and behaves. I have had two experiences with KDE and Knoppix was my other experience. I think Kubuntu is ugly, just a personal opinion. I also hate how they have to have everything begin with a K, I mean, I know it's for KDE, but can you keep it to yourselves? gedit is a GNOME text editor, but Ubuntu just calls it Text Editor. I used to be a Windows power user, and they said that KDE is good for people like that. I personally found the interface very annoying, sorry, I should probably take this up with the Kubuntu guys. But I can see why you've had such hell with it. All I can say is Ubuntu is much better, and I've had to go into xorg.conf a couple times myself, but it was much easier.

---

### Post by AusIV4 on 2007-07-13
There are some great things about KDE. I think Amarok is the greatest music player ever. I don't like Konqueror for web browsing, but for file management, FTP, SCP, ripping music, and a number of other tasks, it's awesome.

But ultimately, I've gone to Gnome for now. I had a number of issues.

Kopete had some formatting issues and lacked some features I wanted, so I chose Gaim instead. Gaim never seemed to be able to identify when I was idle or when I came back, and just arbitrarily reported my away status. I also never noticed the taskbar flashing when I got a new message, because it would only flash maybe 3 times.

Then there was KNetworkManager. At first I was excited by KNetworkManager, it seemed like it was a great idea, and it worked well most of the time. I gave it a wallet with no password, so I didn't have the password issue (that part was harder to resolve in Gnome). But every so often, the connection would hang at 28%, and just stay there. I thought this was a bug in the network manager backend, but I heard that nm-applet never had that problem. Since nm-applet used Gnome's keyring, I decided I'd try out Gnome and see if it worked better. Everything has worked a lot more smoothly on Gnome. I still use Amarok for my music,

I think the Ubuntu team has put a lot more focus into polishing Gnome than KDE, and the KDE team is much more focused on KDE4 than keeping its userbase in the meantime. Once KDE4 is out, I may switch back, but for now everything works in Gnome.

---

