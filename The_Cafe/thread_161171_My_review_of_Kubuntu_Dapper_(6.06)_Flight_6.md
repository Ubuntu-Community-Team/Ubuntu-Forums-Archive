---
title: "My review of Kubuntu Dapper (6.06) Flight 6"
date: 2006-04-16
forum: The Cafe
---

### Post by miklp on 2006-04-16
Hi,
After having used Kubuntu Dapper flight 6 during more than one week now (I also tried Ubuntu Dapper Flight 5 with Gnome, so I will make some comparisons with it), I wanted to share my thoughts about it, hoping it can be useful for future improvements. Sometimes it's just my opinion, so it doesn't have necessarily to be taken into account. Some issues I mention are very important.
I tell more drawbacks than advantages, but (K)Ubuntu goes in the right direction, becomes really better. I hope I will make it my primary system one day.

**Installation**

During the installation, I had one problem : it was not easy to make the installation process to detect my network. My hardware is detected without any problem (ipw2200), but the available wireless networks were not all detected. It always chose one of the network (which is not mine) by default. And even when I entered my ESSID, it was still stuck to the network it had detected first (and therefore my password didn't work). So I restarted the installation process several times, after finally my network was chosen first and thus the connection could be established.
I think there is definitely some bugs concerning the wireless detection of networks (as in Ubuntu 5.10) during the install process. At least, the "Detection of available networks" seems to be too fast to detect all networks.

An other problem during the installation (which is new since Dapper) : it doesn't detect my Windows partition ((K)Ubuntu 5.10 did), and so the first time I restart, I don't have Windows in the Grub list... and have to edit grub.lst . This is a big problem, I hope it will be fixed.

**First start**

First thing which amazed me : my X600 mobility graphic card now works by default in (K)Ubuntu !!! Before that, it was complicated as I had "No screens found" message, as other people having this graphic card. So, thanks to have listened to us !
First impressions of the desktop :

[LIST]
[*] No antialias, even if it's enabled in the configuration : this is definitely a bug (the system doesn't look good at all), but I think it's already fixed. I could make it work (by disabling it and enabling it again just after), but in some applications there's still no antialias, sometimes.
    [*] The default background of Kubuntu doesn't look good to my opinion (a texture, as in old Linux times). It would be preferable to have a background such as the "default" KDE one, all blue with shapes (it looks modern and professional, even if it's not beautiful also !), with Kubuntu written somewhere. Here I really prefer the background of Ubuntu (with Gnome), which is very good ! But the maroon wouldn't be a good idea with KDE here.
    [*] I don't like the default window decoration (the blue is much too strong, and the gradiant doesn't look good to my opinion), but I go to change it and put the default Plastik one, which is good. But after having preferred the look of Kubuntu during a long time, I have to say that Ubuntu 6.06 looks much better now ! The situation reversed. But the human theme wouldn't fit well to KDE I think, and the KDE look is good, especially with Plastik (or Liptik as in Kubuntu 5.10).
    [*] A good point : the Side bar in Konqueror is now enabled by default ! Thanks a lot, it's much clearer.
[/LIST]

**After several minutes of use**

[LIST]
[*] As usual, I'm glad to see that Kubuntu installs by default few applications (not 5 applications for the same purpose, as I remember in Mandrake for example) : it makes it very easy to find what you need for each purpose, even when you're a beginner who doesn't know names of software (as for me I know that Amarok is a software for playing music, OpenOffice Write a word processor, ...). Good point, even if it's not new to the 6.06 version.
    [*] My wireless connexion works, that's good. However, there is a big issue !! When I'm using Linux while I use batteries, it doesn't work anymore !! At the beginning I didn't understand why for some sessions my connexion didn't work...
    [*] There are two error messages when launching Adept : I think this will be fixed soon. Apart from that, Adept works. It could be a little bit more intuitive I think (take some ideas from Ubuntu, but with a KDE style).
    [*] First thing I want to do : installing Skype. I go to download the .deb . Clicking on it doesn't install it, I thought that it was a new feature (very useful !) of (K)Ubuntu 6.06, so either it's a bug or it is not a new feature for the 6.06 version (for other future versions instead) as I thought. So I used dkpg...
    [*] When I installed some applications, they didn't appear in the K menu. I was really deceived. But after a restart they appeared (even Skype, which I installed with the deb file), so it wasmaybe due to the fact it was still my first session.
    [*] Right clicking on an item in the K menu doesn't do anything (in some other distribs (even in Ubuntu 5.04, with the KDE package (not the Kubuntu one), it worked). The K edit menu item should appear after such a click. But for this, the best is Windows. Maybe a feature for KDE 4.
    [*] I don't understand what "Add / Remove programs" (in the K menu) is supposed to do : for me it just launches an "empty" window.
    [*] I think it's useful to have "by default" the most used applications in the K menu, and it reflects Windows functionnality (good for "switching" people (at least people who tries Kubuntu))
[/LIST]

Among my first concerns when I install a system : accessing my file and playing music. Impressions about it with Kubuntu 6.06 Flight 6

First thing I have to say : I have on my harddisk a NTFS partition where Windows is installed, and a FAT32 partition for sharing file among systems (if one day I decide to use Linux often).
I go in the devices, my FAT32 drive appears, but with a strange name (with "little squares" chars). I click on it : it opens. That's good. I try to write on it. It doesn't. Not very good for the beginner, even if I'm happy to see it's not difficult to configure it in the Configuration center. But maybe not intuitive all the same.
An other problem : files using some characters (such as accents : é, è, ... as in my MP3 / OGG files) doesn't appear well ("little square" chars instead of accents). The same problem happens on some web pages.

**Now, let's talk about multimedia :**

[LIST]
[*] I launched Amarok, indicated the folders for my library (on the FAT32 drive) : the directories were scanned, but when I click on the files in Amarok they were not found. Strange. Same thing if I did it using Konqueror (it was Ogg files). Finally, I made it work, but I don't remember how.
    [*] I know that this is for legal reasons, but I'm always disappointed that it's "hard" to make MP3 files working, same for DVDs. Maybe one day Ubuntu will be also sold in stores, and such software will be included.
    [*] Plug in my MP3 player (iRiver H320) worked amazingly good : I really like the fact that the icon appears on the desktop and that a window pops up to ask what you want to do (better than Windows' one).
    [*] You will shout, but that's a pity WMA DRM files can't be played. I do hate this format, but I sometimes download music legally, because this is the only way to get it (I'm in an other country for a long time, and can't find CDs here, and ordering them is too expensive). The solution for this would be an "open-source" DRM system, instead of Microsoft's one. Because, yes, this is a necessity (such websites do want to put some protections on their files, and that's normal, even if I don't like it). But here it's not a problem of Ubuntu.
    [*] After having installed support for some formats (MP3, WMA without DRM), I've been very surprised (in the good way) that I could listen to Radio France radios, inside Konqueror (Kaffeine launches in it), although it's someWMA (embedded in the web page, what's more). However it happens that it makes Konqueror to crash. (By the way, Radio France has some Ogg streamings, but the quality is very very low).
[/LIST]

**Laptop issues**

[LIST]
[*] When running on batteries, the hard disk goes to standby all the time, which makes it restart / stop every 5 seconds. I think 1 minute would be better by default
    [*] A problem of Kubuntu, when compared to Ubuntu : now way to go to standby mode, or hibernate mode. This new window when logging out is an amazing feature of Ubuntu 6.06 : I was very surprised that standby and hibernate modes work with Linux ! This should be included in Kubuntu also.
    [*] As I said before, there is a big bug : when I'm running on batteries, my wifi connexion doesn't work
[/LIST]

**Other issues**

[LIST]
[*] A bug I already had with Kubuntu 5.04 (on an other computer), but this is an issue of KDE I think. Sometimes, when I launch an application, I see it being launched in the taskbar, but it never launches : it waits a long time and finally it disappears... When I launch it again it works. This is very common (let's say 10%). The KDE team should work on this annoying bug.
    [*] Graphic elements are very slow : for example moving a window is very slow, to the contrary to Windows. That's an important problem to my opinion.
[/LIST]

---

### Post by balilu on 2006-04-16
> The default background of Kubuntu doesn't look good to my opinion (a texture, as in old Linux times). It would be preferable to have a background such as the "default" KDE one, all blue with shapes (it looks modern and professional, even if it's not beautiful also !), with Kubuntu written somewhere. 

i don't what you are talking about old texture but the deafult is the bubbles one. is that the one you're getting??

> First thing I want to do : installing Skype. I go to download the .deb . Clicking on it doesn't install it, I thought that it was a new feature (very useful !) of (K)Ubuntu 6.06, so either it's a bug or it is not a new feature for the 6.06 version (for other future versions instead) as I thought. So I used dkpg... 

you could press right click on the deb then "Kubuntu Package Menu" --> "Install Package"

> I don't understand what "Add / Remove programs" (in the K menu) is supposed to do : for me it just launches an "empty" window.

that is supposesd to launch an app which makes it easier to install apps than adept.  mine works maybe it's an issue with your configuratio or something. try filing a bug or see if there is arleady one.

---

### Post by awakatanka on 2006-04-16
> **balilu]
you could press right click on the deb then "Kubuntu Package Menu" --> "Install Package"

[/QUOTE]Think he means the click on deb file launches a installer like gnome has now, gdebi if i'm right.

Kubuntu doesn't have that tool now but what balilu said works very good our install kpackage that can install on click to ( it launce the prg and needs 2 more clicks  said:**
> As I said before, there is a big bug : when I'm running on batteries, my wifi connexion doesn't work Don't have that bug, maybe it has something to do with the type of wificard that is used, got a ra2500.

And i have also that nasty bug of launch and nothing happens, i had it in breezy and now in dapper and also in mepis, looks like a kde bug.

---

### Post by FedeXX on 2006-04-18
I also tried Ubuntu and Kubuntu dapper 6, and i'd like to tell something too :D

(first of all, i'm italian... keep children away from my english... :P )

Kubuntu dapper...works. No much to say about installation, because i've upgraded from breezy.

- In the control center there's no theme manager :D You must run "kcontrol" to change theme...
- No way to use two or more audio application together. Each application which plays audio uses ALL the engines at the same time :| 
-Sometimes (mmmmmmmmm a bit more than sometimes) konqueror decide that's better keep the cursor bouncing for a while...and nothing more. Restart x to fix (aaaaaaaaaaaaaaaaaargh!!!!!!!).
-If you are using amarok, the problem before WILL come up. Use xmms. Same problem when there are adept notifications. Better use synaptic or something else. (connected with the engines problem?)
-Nice idea put the bcm43xx driver, but someone forgot the firmware :D which must be installed manually (and for me too it DOESN'T work on battery)
-Sometimes there's no loopback signal. "sudo ifconfig lo up" to fix.
-kdebluetooth must be killed if you like to use a gprs/edge/umts connection. i don't know why...
-I've two ext3 partitions. The one where is running Kubuntu have a "/" label, and i suppose that's ok. But the other one have a "/" label too! :D
-i'd like some "windows like" icons on the desktop... :)

I think that's all... however, except for these minor bugs, it's a great and complete distro!


PS
(xgl+compiz+kde=eyecandy) :P

---

### Post by ComplexNumber on 2006-04-18
wow! kubuntu sure has a lot of issues :shock:. surely it can't be that bad.

---

### Post by aysiu on 2006-04-18
[QUOTE=ComplexNumber]wow! kubuntu sure has a lot of issues :shock:. surely it can't be that bad.[/QUOTE] I've actually found Kubuntu to be even more stable in Dapper Alpha (Beta now?) than in Breezy...

---

### Post by ComplexNumber on 2006-04-18
[quote=aysiu]I've actually found Kubuntu to be even more stable in Dapper Alpha (Beta now?) than in Breezy...[/quote]
then again, kubuntu breezy was not meant to be that hot from what i've gathered. maybe a lot of the bugs will be ironed out by the time of the final release, or soon after.

---

### Post by miklp on 2006-04-19
Thanks for your answers !
Ok, I didn't think to try to right-click on the DEB file ! Maybe it would be good just to have to click on it.
I don't experience the problem with the sound, when 2 sounds are played in 2 different applications (for example I can hear the KDE sounds when I'm playing a file in Amarok).
However, here is an other issue : I can't read midi file (I tried in KGuitar).

I just hope that our posts will be read, because some issues are important (no detection of Windows when installing Grub, strange characters for special characters in file names (or in Amarok for example), no standby mode as in Ubuntu).

And I experience quite a few crashes in KDE applications, but I think it's mainly due to the problem of stability of KDE... I do like KDE, but it's full of bugs.

Yes, the default background I get is the bubble one, it doesn't look "professional" at all (to my opinion), to the contrary of Ubuntu's one.
Concerning the wifi which doesn't work when running on batteries, I use an intel ipw2200 card.

---

### Post by helpme on 2006-04-19
First off, I installed kubunt dapper about a week ago here to test it out and so far I did find it to be impressively stable. Your installed is definately borked.

> First thing I want to do : installing Skype. I go to download the .deb . Clicking on it doesn't install it, I thought that it was a new feature (very useful !) of (K)Ubuntu 6.06, so either it's a bug or it is not a new feature for the 6.06 version (for other future versions instead) as I thought. So I used dkpg...
Others have already answered this, but if you want to use gdebi, just install it, it also works with kde. ;-D

> Right clicking on an item in the K menu doesn't do anything
Brings up a menu here which includes the option to edit the menu.

> I don't understand what "Add / Remove programs" (in the K menu) is supposed to do : for me it just launches an "empty" window.
Works just fine here. It's just a more userfriendly way to install applications.

> I know that this is for legal reasons, but I'm always disappointed that it's "hard" to make MP3 files working, same for DVDs.
Takes roughly 2 minutes. I wouldn't call that hard.

> You will shout, but that's a pity WMA DRM files can't be played. I do hate this format, but I sometimes download music legally, because this is the only way to get it (I'm in an other country for a long time, and can't find CDs here, and ordering them is too expensive). The solution for this would be an "open-source" DRM system, instead of Microsoft's one.
No, it wouldn't, as you would still be unable to play MS DRMed files with an other DRM system.

> Because, yes, this is a necessity (such websites do want to put some protections on their files, and that's normal, even if I don't like it).
No, it's not.

> However it happens that it makes Konqueror to crash
I think that's a kaffeine problem. Get rid of it and install kmplayer. Much better.

> When running on batteries, the hard disk goes to standby all the time, which makes it restart / stop every 5 seconds. I think 1 minute would be better by default
Doesn't happen here. Anyway, I'd recommend installing kpowersave anyway. It's a lot better than klaptop.

> A problem of Kubuntu, when compared to Ubuntu : now way to go to standby mode, or hibernate mode. This new window when logging out is an amazing feature of Ubuntu 6.06 : I was very surprised that standby and hibernate modes work with Linux ! This should be included in Kubuntu also.
You probably simply need to close the lid of your laptop. Anyway, if you install kpowersave you'll have these options readily available and I even think they were available with klaptop. Just right click on the battery applet and see if you get the options.

> A bug I already had with Kubuntu 5.04 (on an other computer), but this is an issue of KDE I think. Sometimes, when I launch an application, I see it being launched in the taskbar, but it never launches
No, it's a Kubuntu, not a KDE bug. It happens because Kubuntu uses sudo. That said, I didn't notice this bug was still around in dapper, but maybe I was just lucky.

> Graphic elements are very slow : for example moving a window is very slow, to the contrary to Windows. That's an important problem to my opinion.
Just enable the build in compositor and this will go away.

---

### Post by awakatanka on 2006-04-19
[QUOTE=helpme]
No, it's a Kubuntu, not a KDE bug. It happens because Kubuntu uses sudo. That said, I didn't notice this bug was still around in dapper, but maybe I was just lucky.


[/QUOTE]
Think its a kde bug because i have it to with mepis alpha 6, it doesn't use sudo but a root account.

ps. complexnumber must have a love/hate relation with kde because he is always in a kde thread :mrgreen:

---

### Post by helpme on 2006-04-19
[QUOTE=awakatanka]Think its a kde bug because i have it to with mepis alpha 6, it doesn't use sudo but a root account.
[/QUOTE]
Hm, but then again, I honestly never had this problem with any other distro I used and seeing that the mepis alpha is build on the same base as kubuntu I'm still not convinced it's a KDE problem.

---

### Post by angkor on 2006-04-19
@miklp: You do realise you wrote a review about beta software? Please write a review once dapper is released. Right now it is still in the development process and you would be helping the community / devs more by filing bug reports about problems you encounter or suggestions you have while testing dapper than by posting a review on this forum where the devs probably aren't going to see it.

That said. Interesting read nonetheless. I don't use kde but I must say I'm very pleased with dapper since I installed it on a test partition in January. Very stable (even with Xgl & Compiz) and looks great imo.

---

### Post by miklp on 2006-04-20
Yes I know this is an alpha version. That's the reason for which I wrote this review, so that bugs which were potentially not known can be fixed and to pinpoint what could be enhanced, at least to my opinion. And that's why I initially posted this post in the Dapper forum, but someone moved it here (maybe it was more accurate).

---

### Post by aysiu on 2006-04-20
[QUOTE=miklp]Yes I know this is an alpha version. That's the reason for which I wrote this review, so that bugs which were potentially not known can be fixed and to pinpoint what could be enhanced, at least to my opinion.[/QUOTE] I think you may have missed the point of the previous post--the developers don't scour the forums looking for suggestions on what to fix.

They do, however, respond to bug reports. If you want the developers to implement your suggestions, file bug reports here:
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Writing a review on these forums does not do a thing to help improve Dapper.

---

### Post by miklp on 2006-04-20
Ok ! I didn't know. But I feel I'm not enough an expert to fill bugs correctly, so I will try the final version of Ubuntu when it's released and will decide then if I keep it or not !

---

### Post by aysiu on 2006-04-20
[QUOTE=miklp]Ok ! I didn't know. But I feel I'm not enough an expert to fill bugs correctly[/QUOTE] You don't need to be expert enough. Just describe the problem. If the devs need more details from you, they'll ask.

---

