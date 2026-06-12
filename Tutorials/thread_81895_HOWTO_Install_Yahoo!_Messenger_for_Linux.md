---
title: "HOWTO: Install Yahoo! Messenger for Linux"
date: 2005-10-25
forum: Tutorials
---

### Post by linbetwin on 2005-10-25
[color=navy]_Edit_: bodhi.zazen ~ Please take note that this how to was written in 2005 and *may* be outdated. In addition Ubuntu now includes applications by default ( Ubuntu and Xubuntu = Pidgin ; Kubuntu = Kopete) that will access the Yahoo network (so not need to install the Yahoo client).[/color]


1. Install libssl0.9.6 through Synaptic or
> sudo apt-get install libssl0.9.6 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
> sudo dpkg -i /[COLOR=Red]path[/COLOR]/ymessenger_1.0.4_1_i386.deb replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

---

### Post by linbetwin on 2005-10-25
Better use Gaim. Yahoo! Messenger for Linux is ridiculously old and rudimentary.

---

### Post by urbanus6 on 2005-10-25
I have a problem with the configuration of both programs. In the configuration of Gaim there is no field to enter the login name and in the configuration of Yahoo messenger there is no field to enter the screen name.
Is there another messenger program in which I can configure both (different) names?

---

### Post by GazaM on 2005-10-26
[QUOTE=urbanus6]I have a problem with the configuration of both programs. In the configuration of Gaim there is no field to enter the login name and in the configuration of Yahoo messenger there is no field to enter the screen name.
Is there another messenger program in which I can configure both (different) names?[/QUOTE]

Gaim does have a field to enter the login name... The Screen Name field is for your login name and the 'Alias' field is for what you are calling the Screen name, if I understand you correctly.

---

### Post by cjm5229 on 2006-01-06
Try kopete, it's a KDE messenger but I have it installed in Ubuntu and it works quite well, or forget Yahoo all together and use Skype if your trying to get voice messenger working. Good Luck.
Carl

---

### Post by byen on 2006-01-06
[QUOTE=linbetwin]Better use Gaim. Yahoo! Messenger for Linux is ridiculously old and rudimentary.[/QUOTE]
I second that. I have almost all my friends on yahoo and would love to get the latest version up and running...but what they have for linux right now is pretty sad. i suggest using gaim or kopete instead.

---

### Post by speeves on 2006-01-20
The dependencies are pretty old too...  I used Debian about a year ago, and had these problems as well:

(today on Ubuntu Dapper)
me@mylaptop:~/downloads$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 151246 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

I'm not finding libssl0.9.6 in the Ubuntu repositories anymore, but you can find it in Debian Sarge.  (The Debian repositories are under extreme strain right now due to major changes in X, so please be patient).  

Apparently, xlibs is being transitioned into xlibs-dev on Ubuntu.  This change seems to be coming from Debian.   Here is an excerpt from the package page:

"This package smooths upgrades from Debian 3.0 by depending on libice-dev, libsm-dev, libx11-dev, libxext-dev, libxi-dev, libxmu-dev, libxmuu-dev, libxpm-dev, libxrandr-dev, libxt-dev, libxtrap-dev, libxtst-dev, libxv-dev, x-dev, and xlibs-static-dev. This transitional package is only depended upon by packages that haven't yet corrected their dependencies to reflect the new library arrangement."

With the little research that I did, it appears that ymessenger on Ubuntu is really not worth the effort, and GAIM, Kopete, and friends are really the correct way to go.  Besides, shouldn't we be supporting Free Software anyways...? ;)

speeves

---

### Post by BLTicklemonster on 2006-01-30
Our gaming clan uses yahoo for voice chat in our biweekly meetings, so I put in vmware and xp and use yahoo messenger in it to talk. I really wish there was a way to use voice chat in yahoo in ubuntu without having to do all that.

---

### Post by daredevil on 2006-03-01
Wit hkopete u can neither send a file nor join a conference. But u can do both with Gaim

---

### Post by Corvair on 2006-03-13
Hy,
Talk about newby, I just installed Ubuntu Linux on the weekend and I have a lot of things I want to implant, like a messenger. Where is the best way to start. I was hoping to install Yahoo but if there is something better like GAIM, I understand, then shoot it to me

Claude:mrgreen:

---

### Post by tsmets on 2006-03-27
So for the one who first installed the yahoo-messenger & then happily installed Gaim.. 
**How to uninstall yahoo-messenger ...  :) ?**

\T,

---

### Post by Corvair on 2006-03-28
[QUOTE=Corvair]Hy,
Talk about newby, I just installed Ubuntu Linux on the weekend and I have a lot of things I want to implant, like a messenger. Where is the best way to start. I was hoping to install Yahoo but if there is something better like GAIM, I understand, then shoot it to me

Claude:mrgreen:[/QUOTE]
After reading some of the articles on the forum I have finely been able to use GAIM and have access to msn messenger and yahoo! messenger. Thanks to everyone for the info.

---

### Post by stalefries on 2006-03-28
BLTicklemonster: As far as I know, Yahoo! uses SIP for its voice chat. All you need is a program that supports SIP.

---

### Post by kpaul_nyc on 2006-06-27
tihs maehotd deos not wrok at all . im srory for the icnonivinence.. hpoe you can be albe to raed tihs...lol.!!!


is there an easier way for getting yahoo linux?!?!?! so i can be able to use webcam?!?!?!?!

---

### Post by loell on 2006-07-05
[gyachi]("http://ubuntuforums.org/showthread.php?t=190900&highlight=gyachi")
it supports webcam and voice chat room :)

---

### Post by adam.tropics on 2006-07-06
Ekiga does voip voice chat, IM, and video conferencing, and supports SIP, and whats more it comes on a default Ubuntu install!

---

### Post by Blacktalon on 2006-07-07
This may sound stupid and that I am a newbi to this.  Well its true, I still an learning this.  Anyways would anyone mind telling me what I go to do to get GRIAM or whatever it was call on my mechine.



Thanks for any help you can provide
   ~BT;)

---

### Post by finferflu on 2006-07-27
open a terminal and type:

```
sudo apt-get install gaim
```

---

### Post by fakie_flip on 2006-08-07
gyatch is supposed to support mic on linux for yahoo. ive tried but never got it working with voice chat, but i know others have. i will use skype, and gnomemeeting. both are compatible with windows users except. gnomemeeting is compatible with netmeeting, but i am not sure if the voice chat is. wengophone is a really good one to try for voip. if you want support for webcam with msn, try amsn. if you want webcam support for msn and yahoo, try kopete.

---

### Post by loell on 2006-08-07
gyachi voice chat only works on chat rooms unfortunately, its not yet sip base like the one on the current yahoo version for windows, to talk on voice enabled chat room, launch the voice chat, and click and toggle the "Talk" button" to talk and untoggle the button for others to talk to the public mic. :)

---

### Post by mrojas73 on 2006-08-07
I also like yahoo with voice because I can make cheap international calls.  I was able to install the windows version using wine, but it doesn't run.  It may be time to start contacting yahoo asking them to upgrade their old linux version.  We deserve better!!!

---

### Post by mudpuppys1x on 2006-08-08
help! how do i install yahoo messenger? nuthin works. i tried all suggested methods and seem to run into sum of the same problems others encountered: missing or outdated files. i found them and installed them but met with the same result...nuthin works. i tried to run an older version of yahoo thru wine...how does it work or does it? btw, microtrash and yahoo have entered into a "partnership" so i wouldn't look for yahoo to "improve" it's debian version to run in ubuntu anytime soon. if anyone out there has installed messenger and gotten the mic and cam to work, plzzzzzz help!

---

### Post by loell on 2006-08-08
what yahoo messenger are you installing is it the ymessenger from yahoo or is it [GYachI]("http://ubuntuforums.org/showthread.php?t=190900&highlight=gyachi")
that supports cam and voice in rooms. ?

---

### Post by baghery.farhad on 2006-09-02
If I want to talk(Voice chat) to my friend, Can do this gaim?

---

### Post by gary4gar on 2006-09-02
> **baghery.farhad said:**
> If I want to talk(Voice chat) to my friend, Can do this gaim?
no Gaim does not support voice only **text**
for this u can use any VOiP app

---

### Post by Ranganaths on 2007-01-27
when i type this command i get the error as the package not found. please let me know wht to do.
sudo apt-get install libssl0.9.6
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libssl0.9.6


Regards

---

### Post by girard on 2007-03-14
> **linbetwin said:**
> 1. Install libssl0.9.6 through Synaptic or
 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
 replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

this is what i get:

:~$ sudo apt-get install libssl0.9.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libssl0.9.6

what does it mean? i tried skipping this part and running sudo dpkg -i...
it said this:

p:~$ sudo dpkg -i ~/Desktop/ymessenger_1.0.4_1_i386.deb
(Reading database ... 144715 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using .../ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

i'm new with this so let me try:
i need to sudo apt-get install the following: 
libgdk-pixbuf2 [what does (>=0.13.0 mean?)]
libssl0.9.6
xlibs [again.. what's (>>3.3.6) and do i include it?

thanks

---

### Post by maddog39 on 2007-03-14
> Better use Gaim. Yahoo! Messenger for Linux is ridiculously old and rudimentary.
Yes, unfortunetly the same goes for AIM, they only have version 2 or 3 for linux. When the windows and mac versions are up to 5 and 6.0 I think.

---

### Post by girard on 2007-03-14
> **linbetwin said:**
> 1. Install libssl0.9.6 through Synaptic or
 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
 replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

i cannot download the libssl

i get this:

:~$ sudo apt-get install libssl0.9.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libssl0.9.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libssl0.9.6 has no installation candidate

what does it mean?

---

### Post by aysiu on 2007-03-14
This HowTo is over a year and a half old and now obsolete. I haven't found any recent threads indicating successful installations of Yahoo! Messenger. Use Kopete or GAIM.

---

### Post by girard on 2007-03-15
> **speeves said:**
> The dependencies are pretty old too...  I used Debian about a year ago, and had these problems as well:

(today on Ubuntu Dapper)
me@mylaptop:~/downloads$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 151246 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

I'm not finding libssl0.9.6 in the Ubuntu repositories anymore, but you can find it in Debian Sarge.  (The Debian repositories are under extreme strain right now due to major changes in X, so please be patient).  

Apparently, xlibs is being transitioned into xlibs-dev on Ubuntu.  This change seems to be coming from Debian.   Here is an excerpt from the package page:

"This package smooths upgrades from Debian 3.0 by depending on libice-dev, libsm-dev, libx11-dev, libxext-dev, libxi-dev, libxmu-dev, libxmuu-dev, libxpm-dev, libxrandr-dev, libxt-dev, libxtrap-dev, libxtst-dev, libxv-dev, x-dev, and xlibs-static-dev. This transitional package is only depended upon by packages that haven't yet corrected their dependencies to reflect the new library arrangement."

With the little research that I did, it appears that ymessenger on Ubuntu is really not worth the effort, and GAIM, Kopete, and friends are really the correct way to go.  Besides, shouldn't we be supporting Free Software anyways...? ;)

speeves

so does this mean that i didn't actually do anything wrong, nor is there a problem with my system???

---

### Post by girard on 2007-03-15
> **aysiu said:**
> This HowTo is over a year and a half old and now obsolete. I haven't found any recent threads indicating successful installations of Yahoo! Messenger. Use Kopete or GAIM.

but neither of them can connect to both yahoo and msn people right? to make it simple...
what program should a linux user use to be able to chat (text and voice), view a webcam, send files, and voice chat with yahoo and msn users? nevermind the photo sharing

the way i see it, yahoo and msn are trying to make various interactions possible, there should be a way for linux users and opensource people to join in.

---

### Post by loell on 2007-03-15
> **girard said:**
> but neither of them can connect to both yahoo and msn people right? to make it simple...
what program should a linux user use to be able to chat (text and voice), view a webcam, send files, and voice chat with yahoo and msn users? nevermind the photo sharing

the way i see it, yahoo and msn are trying to make various interactions possible, there should be a way for linux users and opensource people to join in.

that would be

amsn =  has webcam support, and voice clips under way
gyachi = yahoo messenger with webcam support and voice chat in rooms

tapioca = for googletalk ----> with the help of [gtalk2voip]("http://www.gtal2voip.com") service you can do sip voice calls(pc to pc call)  to Yahoo and MSN


oh and Gaim does connect yahoo and msn and more

---

### Post by girard on 2007-03-16
here's the thing... you'd be able to install the 1.0.4-2 version of yahoo messenger but it sucks. previous posts are right when they said ubuntu users are better off using gain: at least you won't need different programs for the other clients because what i was after, why i persisted in finding out how to install yahoo linux version was the pc to pc calls and webcam. after 2days, i was successful, only in installing yahoo... but i did not get what i wanted it for.

i forgot where i got this already but this is what i followed:

[U]I too was having trouble installing the Yahoo!Messenger. It started out much the same as the first post with a litany of errors. After reading through this thread, I managed to get so far as to reduce the dependancy error to xlibs. However, no matter what I tried I couldn't find a way around it (yes, I even went to a debian oldsource library, but to no avail).

Then I started hunting through previously uninstalled utilities and I came across a real bute: alien. "alien is a program that converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. If you want to use a package from another linux distribution than the one you have installed on your system, you can use alien to convert it to your preferred package format and install it. It also supports LSB packages." (man alien)

I installed alien, double checked that I had rpm installed, then downloaded the rpm version of yahoo!messenger and converted it to a deb file (alien -c rh9.ymessenger-1.0.4-l.i386.rpm). This created a new deb file (ymessage_1.0.4-2_i386.deb) which I could then install with dpkg -i ymessage_1.0.4-2_i386.deb. After that it was a simple matter to run ymessage and away I went!

Now, just for the helluv it, I tried to use rpm to install the original rpm, but as you might expect, this was pointless. NOTE: I'm running Ubuntu 6.06 desktop.

My only disappointment (thus far) with ymessenger is that it does not support SMS messages in the linux version. Anyone have any suggestions for alternate IM tools that does support SMS messaging?

***

HI, HERE IS HOW YOU INSTALL YAHOO-MESSENGER ON UBUNTU, WITHOUT GOING THROUGH ALL THAT DEPENDENCY HELL ! -
1. user$sudo apt-get install alien #install's alien to convert rpm packages to .deb#
2. user$sudo apt-get install libgdk-pixbuf2 #a package needed by messenger#
3. Download the following - rh9.ymessenger-1.0.4-1.i386.rpm from here - [http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)
4. user$sudo alien -c rh9.ymessenger-1.0.4-1.i386.rpm #converts it to a debian package#
6. user$sudo dpkg -i ymessenger-1.0.4-i386.deb #installs the package#
8. user$ymessenger #starts yahoo messenger#[/U]

read through it and you'd get an idea how... basically it's getting the libss 's and the rpm, downloading the rpm (9) version (not the debian), converting it to debian, and that's the only time you can install... it's tedious i know.

i am actually going to remove it after all the work. 

what i think we should do it to put pressure on yahoo to make an upgrade for linux through their Y! Answers... that's a step.

---

### Post by BLTicklemonster on 2007-03-16
Well heck, does the new yahoo work with wine? Probably already mentioned here, but I'm lazy, you all know that.

---

### Post by loell on 2007-03-16
@girard , yahoo had been deaf and blind for years on request for new yahoo linux version. 

so further request is futile. they never listen.

---

### Post by girard on 2007-03-17
> **loell said:**
> @girard , yahoo had been deaf and blind for years on request for new yahoo linux version. 

so further request is futile. they never listen.
maybe if they'd realize that a lot of linux users also yahoo!, they would. pressure would eventually make them act on it.

---

### Post by rat1000 on 2007-03-17
If you need webcam support, use Gyachi.  You can send and view webcam with other yahoo users.    Otherwise, if you only need chat use gaim.

---

### Post by girard on 2007-03-18
> **rat1000 said:**
> If you need webcam support, use Gyachi.  You can send and view webcam with other yahoo users.    Otherwise, if you only need chat use gaim.
i need to have voice and webcam with my yahoo contact.

---

### Post by loell on 2007-03-18
after all the suggestions above, i think you need to dual boot windows , that could be your only last option with yahoo messenger.

---

### Post by Jennabob on 2007-03-25
You can try to install Yahoo! with wine but there are many bugs involved aparently...I've tried to install that way and I get the program installed but it will not work.

According to the wine website you can get 7.0 installed but it doesn't explain how anyone has managed this...

Anyway I'm going to keep at it and if I find out that I can get it working then I'll let you guys know. :) 

oh and here is the link for wine that  I found the information on

[http://appdb.winehq.org/appview.php?iAppId=29](http://appdb.winehq.org/appview.php?iAppId=29)

---

### Post by _hadi_ on 2007-05-08
I changed some dependecies in yahoo messengers package and it will be installed with no problems :)

---

### Post by BLTicklemonster on 2007-05-08
Wow, that's cool!!! No way of getting a later version, huh? The big sticking point for me so far is that we hold conferences in yahoo and use voice. I can't do that in linux, so I have to run xp in vmware and run yahoo in it.

---

### Post by BLTicklemonster on 2007-05-08
> **loell said:**
> after all the suggestions above, i think you need to dual boot windows , that could be your only last option with yahoo messenger.

Run XP in vmware server, and the latest yahoo works great. All the bells and whistles function. But I still want yahoo mess in linux!

---

### Post by loell on 2007-05-08
> **BLTicklemonster said:**
> Run XP in vmware server, and the latest yahoo works great. All the bells and whistles function. But I still want yahoo mess in linux!

 :lolflag:  you quoted my old post,

but actually, you can do voice with yahoo through ekiga using gtalk2voip,

[ekiga to yahoo]("http://ubuntuforums.org/showthread.php?t=414121")

i think this is the way to go for others like me, who could not afford a xp license nor the guts to load a pirated xp.

---

### Post by BLTicklemonster on 2007-05-09
So does the voice work in a conference in yahoo, or is it like using the voice chat in gyache, which is different?

---

### Post by loell on 2007-05-09
this is SIP voice calls

---

### Post by eelsquid on 2007-05-26
HI, HERE IS HOW YOU INSTALL YAHOO-MESSENGER ON UBUNTU, WITHOUT GOING THROUGH ALL THAT DEPENDENCY HELL ! -
1. user$sudo apt-get install alien #install's alien to convert rpm packages to .deb#
2. user$sudo apt-get install libgdk-pixbuf2 #a package needed by messenger#
3. Download the following - rh9.ymessenger-1.0.4-1.i386.rpm from here - [http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)
4. user$sudo alien -c rh9.ymessenger-1.0.4-1.i386.rpm #converts it to a debian package#
6. user$sudo dpkg -i ymessenger-1.0.4-i386.deb #installs the package#
8. user$ymessenger #starts yahoo messenger#


I did try all tat and in 
4. sudo alien Desktop/rh9.ymessenger-1.0.4-1.i386.rpm 
since i had the rpm file downloaded on to the desktop.
now after all this when i try to run 
8. $ymessenger # on the terminal, i get a message /usr/bin/ymessenger :permission denied...
i even tried by logging on from the root, yet doesnt work...
what should i do...???

---

### Post by SeaSky on 2007-06-06
sea@sea-laptop:~$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
dpkg: error processing ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ymessenger_1.0.4_1_i386.deb
sea@sea-laptop:~$ cd /home
sea@sea-laptop:/home$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 107440 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
sea@sea-laptop:/home$ sudo apt-get xlibs
E: Invalid operation xlibs
sea@sea-laptop:/home$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 107433 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger



ehhh sour grapes?...yeah...spoily grapes

---

### Post by meng on 2007-06-06
Use gaim! ymessenger for linux was abandoned years ago.

---

### Post by SeaSky on 2007-06-06
SPOILED GRAPES

sea@sea-laptop:~$ sudo apt-get xlibs
E: Invalid operation xlibs
sea@sea-laptop:~$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkb-data
E: Package xlibs has no installation candidate
sea@sea-laptop:~$ sudo apt-get install libxftl xkb-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxftl
sea@sea-laptop:~$ sudo apt-get install libxft1 xkb-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xkb-data is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ymessenger: Depends: xlibs (> 3.3.6) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
sea@sea-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  ymessenger
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 737kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107439 files and directories currently installed.)
Removing ymessenger ...
sea@sea-laptop:~$ sudo apt-get install libxft1 xkb-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xkb-data is already the newest version.
The following NEW packages will be installed:
  libxft1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.6kB of archives.
After unpacking 98.3kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libxft1 6.8.2-1 [25.6kB]
Fetched 25.6kB in 0s (31.9kB/s)
Selecting previously deselected package libxft1.
(Reading database ... 107428 files and directories currently installed.)
Unpacking libxft1 (from .../libxft1_6.8.2-1_i386.deb) ...
Setting up libxft1 (6.8.2-1) ...
sea@sea-laptop:~$

---

### Post by meng on 2007-06-06
Why on earth are you trying to do this? See my previous post.
gaim or kopete will connect to Yahoo!, MSN, ICQ and others

---

### Post by ragadanga63 on 2007-06-13
YM for Linux?  don't bother.  It doesn't have voice or webcam support and its interface is butt ugly.  Meng was right use Kopete, GAIM (No webcam/voice), or gyachi.

---

### Post by gundumfx on 2007-08-01
> **linbetwin said:**
> 1. Install libssl0.9.6 through Synaptic or
 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
 replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

after i did what you said well download the libssl0.9.6 well i clicked the link an then it gave me this problem 

file:///home/gundumfx/Screenshot-2.png               ( look at this link an you will see my problem )

so what do i do now

---

### Post by Cadillac on 2007-08-11
Hello, everyone!
I found some nice program for voice and webcam chat. Its name is Qnext. You can use it on Mac, Linux and Windows. It supports almost all known protocols including Yahoo! and MSN. The download link is here:
[http://www.qnext.com/download_linux.php]("http://www.qnext.com/download_linux.php")

---

### Post by MJWhiteDerm on 2007-08-28
When following the above directions, I get:  
poohbah@dell-unbuntu:~$ sudo apt-get libssl0.9.6
Password:
E: Invalid operation libssl0.9.6
poohbah@dell-unbuntu:~$ sudo apt-get install libssl0.9.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libssl0.9.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libssl0.9.6 has no installation candidate

So, this doesn't work. 

It has been suggested that we just use gaim instead.  I like gaim a lot, however, I cannot send files or receive files from yahoo IM users, when using gaim ... they get a message that says I am using an obsolete version of Yahoo IM.

It's some Catch, that Catch 22.

Anyone have any other ideas?

---

### Post by loell on 2007-08-28
i don't think you can transfer files to and from YMessenger linux version either.

in any case if you could just wait for gyachi's new version, say a month?  it can transfer 1 gig file to and from YM windows without a problem.

---

### Post by MJWhiteDerm on 2007-08-28
Thanks, Loell.

The current version doesn't allow file transfers?

Michael

---

### Post by loell on 2007-08-28
actually, it does but only limited to 250kb file per transfer

---

### Post by ekricyote on 2007-09-01
Does Kopete come with voice chat support? I'm interested in making phone calls out to regular telephone numbers (e.g. PC to POTS).

Yahoo messenger supports that, but AFAIK, the linux version does not, nor does gaim nor gyachi.

---

### Post by loell on 2007-09-01
try gizmoproject for linux  it can call yahoo and msn.

---

### Post by Myronray on 2007-10-15
root@myronray-desktop:~# sudo apt-get install libssl0.9.6 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libssl0.9.6

---

### Post by aniz on 2007-10-26
> **urbanus6 said:**
> I have a problem with the configuration of both programs. In the configuration of Gaim there is no field to enter the login name and in the configuration of Yahoo messenger there is no field to enter the screen name.
Is there another messenger program in which I can configure both (different) names?
i hav a problem in opening ymessgr
During opening an error message came "status Error:dependancy is not satisfiable: libssl0.9.6"
how can i rectify this error.....

---

### Post by hvmehta on 2007-12-04
libssl0.9.6 is not available and hence could not yahoo messenger.

---

### Post by manoynmonic on 2007-12-12
I have had some limited success installing yahoo messenger 7 (get it from filehippo) under wine.  At first had zero success, but after I installed ies4linux, I tried again, then downloaded the full installer from filehippo, and got it partially running.

Still not running how it should, but feel like progress is being made.  

-manoy

---

### Post by manoynmonic on 2007-12-12
more - this guy at winehq got further than me...

[http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=1411](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=1411)

---

### Post by CREEPING DEATH on 2007-12-12
I don't know why Yahoo is blowing off the *nix community.  I manually downloaded the needed dependency .debs from Debian ([www.packages.debian.org](www.packages.debian.org)) to try it out when it started wanting X libs.

CD

---

### Post by JoePits on 2008-01-30
> **_hadi_ said:**
> I changed some dependecies in yahoo messengers package and it will be installed with no problems :)

hey thanks dude i put linux on our home machine and my mom uses yahoo messenger and id hate to have to make her figure out pidgin (she tried before and didntl ike it ) :)

---

### Post by GamingMazter on 2008-01-30
Thanks. Been trying to do something like this for a bit...thank you!

---

### Post by JoePits on 2008-01-31
> **JoePits said:**
> hey thanks dude i put linux on our home machine and my mom uses yahoo messenger and id hate to have to make her figure out pidgin (she tried before and didntl ike it ) :)

well it didnt work that good so just usin the web based works fine.

---

### Post by rekanoell on 2008-02-19
hi! i'm a new ubuntu 7.10 user and i have basic knowledge on computers. i tried your instructions on my synaptic but it doesnt have a linssl 0.9.6 package in there so i cant install it. it only has libssl 0.9.8. what do i do?

thanks very much.

---

### Post by merlinDwizzard on 2008-02-19
I have a workaround for this, but you probably won't like it. I installed windows(sorry) in virtualbox and set it to NAT for the network. I can run windows and yahoo messenger from there. The only reason I have done this is because my wife likes to use the audibles to get my attention when i am away at school and I do the same to get her attention when I am on a break and can talk to her.

---

### Post by rekanoell on 2008-02-19
thanks.i tried qnext but how do you decompress it?i'm using ubuntu 7.10 and i can't find how to decompressit.

would appreciate very much if you could advise step-by-step like a for-dummies thing cause i'm a basic user
 
thanks again

---

### Post by imon9 on 2008-02-19
hi...just for ur info..this version of yahoo messneger is very very very old...i shall say, file transfer dun even work on it! (not compatible with the new messneger 7.5 and above

as such, ur best choice to come closest to yahoo is either Pidgin(previously know as GAIM) or Kopete....

or u could try XP in virtualbox (virtualization) just for the sake of running yahoo in it...sadly webcam wont work like that

---

### Post by bhavi on 2008-02-20
yes I do think so.. :)

---

### Post by keenlearner on 2008-02-25
I have install yahoo messenger of windows version successfully on top of WINE, but I can't login. Does anybody successfully did it ? I still believe the windows yahoo messenger is the best, in gaim I couldn't got to chatroom, not webcam too. Thank you

---

### Post by imon9 on 2008-02-26
well, i tried with yahoo viersion 8 and login in, see my fren, can even send flie, but cant type messgaes

---

### Post by matherians2 on 2008-02-26
Hmmmm.....Very interesting    :guitar:

---

### Post by hatmal on 2008-03-03
i have ubuntu 7.10 and try to download yahoo messenger

i tried to use the steps under y text but it failed and .
at the forth step i didnt find the ymessenger at the path /usr/bin/

so can any one help me

Install Yahoo! Messenger for Linux
1. Install libssl0.9.6 through Synaptic or
Quote:
sudo apt-get install libssl0.9.6
2. Download this file from messenger.yahoo.com.

3. In a terminal, write:
Quote:
sudo dpkg -i /path/ymessenger_1.0.4_1_i386.deb
replacing path with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

---

### Post by gegorospe on 2008-03-05
> **daredevil said:**
> Wit hkopete u can neither send a file nor join a conference. But u can do both with Gaim

does it support webcam viewings?

---

### Post by alecz20 on 2008-04-07
> **loell said:**
> [gyachi]("http://ubuntuforums.org/showthread.php?t=190900&highlight=gyachi")
it supports webcam and voice chat room :)

How do you get to make that work mate? I haven/t been able to get webcam and/or voice with Gyachi.

Thanks!

---

### Post by loell on 2008-04-07
what's the error when you use your webcam? also what's your webcam?

and what's the error in voice when you launch it after you entered a chatroom?

---

### Post by alecz20 on 2008-04-07
> **girard said:**
> maybe if they'd realize that a lot of linux users also yahoo!, they would. pressure would eventually make them act on it.

I think Yahoo doesn't want to improve Linux support because it is harder for them to SPAM the system compared to Windows instalations.

On windows if you install Yahoo messenger with the default settings you'll have toolbars and crap you don't want... well they can't really do this on Linux, so they don't want to update Yahoo for Linux.

That's my take on it... At least in North America most people use Hotmai or Gmail, so very few of my friends (mostly from Europe) use the crappy Yahoo service.

---

### Post by alecz20 on 2008-04-07
> **loell said:**
> after all the suggestions above, i think you need to dual boot windows , that could be your only last option with yahoo messenger.

Dual-booting sucks! I have dual-boot on my laptop, but it takes a hell lot of determination to re-enter the sloppy windows Vista. There's 2 reasons for which I keep windows: Yahoo messenger and Rome Total War.

---

### Post by loell on 2008-04-07
heh, why are you quoting old posts?  so what's your real question?

---

### Post by alecz20 on 2008-04-07
Ok, glad you asked!

My real question is:

How do you get chat, voice, and video on Linux (Ubuntu) with people using yahoo messenger?

Preferably in one program; basically a complete yahoo messenger alternative for Linux.


Thanks!

P.S. and sorry for not answering your previous question, but I am at work now, and you guessed; I'm using Windows (and it really pisses me off, but that's another story)
When i get home I'm gonna try Yahoo messenger webcam and voice chat with Ghyachi.

---

### Post by loell on 2008-04-07
my setup goes like this.. ;)

for webcam , room voice chat , file transfer, yahoo photos, audibles / smilies,   i'm still using gyachi.

for pc to pc call with YM ,  i'm using [Gizmo project for linux]("http://gizmo5.com/pc/download/"), after setting up a gizmo account which is of course free,  just type    [email]username@yahoo.com[/email] in the  call text/bar, you should be able to call your yahoo contact.

---

### Post by alecz20 on 2008-04-07
In Gyachi I click voice chat in the window with my contact, and I see: 
I "have enabled voice chat"
my contact "has enabled voice chat"

And a pop-up windows appears saying to start pY! voice chat.
So I do. Then I click 'On", but I don't see my buddy. At some point I was able to see me, but that's it.


As for the webcam, when i click "start my webcam" i get three messages:
1) Gyachi (webcam broadcaster):
An error occurred at 'ioctl VIDIOCSPICT'.
Could not set camera proprieties.

2) Gyachi (webcam broadcaster):
Error while querying mmap-buffers.

3) Gyachi (webcam broadcaster):
An error occurred at 'ioctl VIDIOCSPICT'.
Could not set camera proprieties.

then I click ok on message 1) or 3) and it closes.

I can however see someone elses webcam.

For the voice chat, I suppose I have to do the Pc to Pc calls thing, although why have different names (i.e. voice chat and PC-PC calls) for the same exact action.

Any help/suggestion would be greately appreciated.

Thanks.

---

### Post by loell on 2008-04-07
yes, voice chat has been confused as pc to pc call,  but among yahoo third party clients voice chating in public rooms is refered to as voice chat.

might as well create a new thread for your webcam problem, let me know the link, and i'll try to follow you up on there.

---

### Post by alecz20 on 2008-04-08
I don't really like the idea of starting a new thread since I believe someone already had this problem, started a thread, and got their problem solved.

If you think the above isn't the case, I will start a new thread, until then... I will try to do some searching.

---

### Post by ciprian_mohorea on 2008-04-15
i have this problem when i try to install yahoo messenger.. who can help me? I am new in linux. 
Urm&#259;toarele pachete au dependen&#355;e neîndeplinite:
  ymessenger: Depinde: libglib1.2 (>= 1.2.0) dar nu este instalabil
              Depinde: libssl0.9.6 dar nu este instalabil
              Depinde: xlibs (> 3.3.6) dar nu este instalabil

and when i try to intall this dependencies

root@ubuntu:~# apt-get install libglib1.2
Citire liste de pachete... Terminat
Se construie&#351;te arborele de dependen&#355;&#259;
Reading state information... Terminat
Pachetul libglib1.2 nu este disponibil, dar este men&#355;ionat de c&#259;tre alt pachet.
Aceasta ar putea însemna c&#259; pachetul lipse&#351;te, s-a învechit, sau
este disponibil numai din alt&#259; surs&#259;
Oricum urm&#259;toarele pachete îl înlocuiesc:
  libglib1.2ldbl

---

### Post by ciprian_mohorea on 2008-04-15
ymessenger_1.0.4-2_i386.deb generated
root@ubuntu:~# dpkg -i ymessenger-1.0.4-i386.deb
dpkg: eroare la procesarea ymessenger-1.0.4-i386.deb (--install):
 nu se poate accesa arhiva: No such file or directory
Erori întâlnite în timpul prelucr&#259;rii:
 ymessenger-1.0.4-i386.deb
root@ubuntu:~# dpkg -i /home/cip/Desktop/ymessenger-1.0.4-i386.deb
dpkg: eroare la procesarea /home/cip/Desktop/ymessenger-1.0.4-i386.deb (--install):
 nu se poate accesa arhiva: No such file or directory
Erori întâlnite în timpul prelucr&#259;rii:
 /home/cip/Desktop/ymessenger-1.0.4-i386.deb
root@ubuntu:~#     

i have this kind of errors.. what i can do ?


ok.. i resolved this problem alone... but.. it is still another one
it seem like this version of zahoo messenger it is no longer aviable... what can i do ?
I have some programs alternatives for connection to yahoo, but i am in a university and only yahoo messenger can deal well with proxy, and no other programs.

---

### Post by alecz20 on 2008-04-16
Ok, first things first:

The version of Yahoo messenger you are trying to install is way too old, and not only it will probably not provide the latest features such as pc call and webcam with newer version, and I think the packages it requires are also old and unsupported.

I usually install packages from the window manager, it just seems easier. but if you have to do it from the terminal... I only have a question: why you also put (--install) ? I just tested with a package and it worked without that option.
Then again, just to make sure you don't misspell, type the first few characters, then press tab...

I'm not an advanced user, pretty new to Linux myself.

One more thing.... it's probably easy to attempt a translation of the errors, not everyone here knows romanian, i'll do it for you this time:

[/translated]:

 ymessenger_1.0.4-2_i386.deb generated
root@ubuntu:~# dpkg -i ymessenger-1.0.4-i386.deb
dpkg: error processing ymessenger-1.0.4-i386.deb (--install):
cannot access archive: No such file or directory
Errors occurred while processing:
ymessenger-1.0.4-i386.deb
root@ubuntu:~# dpkg -i /home/cip/Desktop/ymessenger-1.0.4-i386.deb
dpkg: error precessing /home/cip/Desktop/ymessenger-1.0.4-i386.deb (--install):cannot access archive: No such file or directory
Errors occurred while processing:
/home/cip/Desktop/ymessenger-1.0.4-i386.deb
root@ubuntu:~#

i have this kind of errors.. what i can do ?


ok.. i resolved this problem alone... but.. it is still another one
it seem like this version of zahoo messenger it is no longer aviable... what can i do ?
I have some programs alternatives for connection to yahoo, but i am in a university and only yahoo messenger can deal well with proxy, and no other programs.

[/end translation]

As for the proxy issue, i can't help you with that, but I'm sure there is a yahoo compatible chat program that can work around it...

Good luck!

---

### Post by ciprian_mohorea on 2008-04-16
thank for your help. Also I have a problem and i am unable to change the language of sistem back in english, In system settings regional and language all it is in english and english it is deatful but... in the console still it is in romanian language,
What iti is the latest version of yahoo messenger for linux? How can i find it? With google this version ymessenger-1.0.4-i386.deb  it seems to be the newest but.. .. when i try to connect a error window   adivice me that this version expired in 2 abril this year,,,,
I need some advices.. I realy need.
Thank you all.

---

### Post by SirDevan on 2008-04-16
I noticed how so many people responded with a response that was like "what the hell is wrong with you trying to install Yahoo?! Just use gaim and giyachi" etc.

I have tried all of these programs. The main issue I have is webcam but I want a program that lets me do what yahoo lets me do in windows.

I dont want to install windows ONLY for yahoo.
I don't want to dual boot ONLY for yahoo.
I don't want to have to run 5 programs together to have the functionality yahoo has.

There has to be a way to do this. If we can run virtually all other programs in wine we can do this. I have messed with it quite a bit and tried both Yahoo 8 and Beta 9 in the latest wine, both were giving me an error like you don't have internet. But after installing the latest beta 8.04 Ubuntu it actually connects just fine. The only issue I have now is the default fonts arent installed that yahoo uses.

This to me is a much easier problem to resolve versus installing a 4 year old linux version or 5 other programs.

---

### Post by ciprian_mohorea on 2008-04-16
I use Kubuntu 8.04 but when i try to use yahoo messenger 8 or 9 with wine, when the messeger is conected sudenly the program stop to work and it is clausing. I dont know what to do....

---

### Post by alecz20 on 2008-04-17
I didn't hear of anyone actually having succes with Yahoo messenger on Wine. Maybe you were lucky! Did EVERYTHING work? By that I mean webcam, pc to pc calls, other things you might need.

However I've heard some people having success with Gizmo for pc-to-pc calls (aka voice chat) and Kopete or Gyachi for webcam, they both support text chat, so if you don't care about webcam, go with gizmo only, if you don't care about pc-to-pc call go with Gyachi or Kopete only.

Personally, I prefer Kopete vs gyachi. It has a much nicer interface than Gyachi IMO, and it detected my webcam out of the box, which gyachi didn't.

I haven't testes voice on Gizmo, but it looks very promising.

To summarize:

- kopete or gyachi for text and webcam
- gizmo for text and voice (pc-to-pc call)

---

### Post by alecz20 on 2008-04-17
> **ciprian_mohorea said:**
> I use Kubuntu 8.04 but when i try to use yahoo messenger 8 or 9 with wine, when the messeger is conected sudenly the program stop to work and it is clausing. I dont know what to do....

I never actually bothered trying to get Yahoo messenger to work on Linux because I hate the messenger client in the first place. Similar situation with Windows Live Messenger. I use aMSN for it, and I like it better.

Remember that WINE is supposed to be used as a last resort. For example... why use DVD Shrink on Wine if you have so many options natively on Linux (DVD95, and K9copy come to mind right now). Same goes for everything else. I admit I run utorrent on Wine, but if you go on their website you see this:

"For Wine, Windows 95 (Winsock2), 98/ME, NT/2000, XP, 2003, and Vista."
source: [http://www.utorrent.com/download.php](http://www.utorrent.com/download.php)

I also play Diablo 2 :), but apart from these I merely test the windows programs on WINE nothing for long term use.

In your situation, the only thing I'm not comfortable with is the proxy stuff... I haven't really dealt with proxy so I can't say if the programs I listed above are going to work or not. I just think they will.

---

### Post by merwizard on 2008-04-22
I am really happy that file transfer now works in Pidgin (Ubuntu 8.04 with Pidgin from the official repos). The inability of the Linux YM clients to perform file transfers was  one of the reasons for many of my friends had to go back to windows, after convincing them to try Linux.

---

### Post by PenguinTUX on 2008-04-28
hic hic, i'm poor. i can't install Y!M on my Ubuntu! :((

---

### Post by alecz20 on 2008-04-28
> **PenguinTUX said:**
> hic hic, i'm poor. i can't install Y!M on my Ubuntu! :((

Read this entire thread... you might be surprised!

---

### Post by ibharathy on 2008-05-17
but i can't use my web cam in Ubuntu and i want to use yahoo messager in ubuntu hardy or suggestion.. Please help me..

---

### Post by atomkarinca on 2008-05-17
> **ibharathy said:**
> but i can't use my web cam in Ubuntu and i want to use yahoo messager in ubuntu hardy or suggestion.. Please help me..

Take a look at [this thread]("http://ph.ubuntuforums.com/showthread.php?t=773802").

---

### Post by neochu on 2008-06-07
as of today it looks like even Pidgin is failing with the newest yahoo logon credential requirements.

so its either the outdated abandonware (that you have to break up the .deb package and remove the dependency criteria in the control documents and get the libraries you can then repackage) or use the other alternatives.

Its sad too because I have friends that refuse to use anything else BUT yahoo.

---

### Post by loell on 2008-06-07
what's your location? i too could not log in to Yahoo, but there web messenger seems to be connecting and half of my contacts is online too, so this may have something to do with we are at.

---

### Post by hoverkar on 2008-06-28
sudo apt-get install libssl0.9.6

when i tried this command, i get like this,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libssl0.9.6

what i want to do?

---

### Post by atomkarinca on 2008-06-28
> **hoverkar said:**
> sudo apt-get install libssl0.9.6

when i tried this command, i get like this,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libssl0.9.6

what i want to do?

You can find it [here]("http://packages.debian.org/libssl0.9.6").

---

### Post by Mgiacchetti on 2008-08-11
> **PenguinTUX said:**
> hic hic, i'm poor. i can't install Y!M on my Ubuntu! :((
nope, not gonna be able to be done, at least not the new version that works.

Virtual box is the only option as of now, besides dual booting.  in Wine it crashes, none of the programs mentioned support pc to pc calls, except maybe qnext but i havent really played with it enough to tell you yes or no.

--UPDATE--
In qnext i see the pc to pc call button, but i am unable to click it.  It sees my input device though, so we're on the right track, i think the devs just need to update the protocol to match the newest from Yahoo.

HINT HINT! :lolflag:


Other than that, I cannot wait for the Summer of Code to finally pay off with pidgin audio/video support




BTW  The OP should mention in post #1 that it is not currently possible to voice at all (pc to pc or in chat room ive tried them all pidgin, gyachI, gyachE, ekiga, etc.  the only one that seems to work is Skype.) with THIS howto.

---

### Post by loell on 2008-08-11
> none of the programs mentioned support pc to pc calls

i don't need no friggin virtual box and a copy of XP/vista just to call a YM user!! :lolflag:

i can just use [gizmo project]("http://gizmo5.com/pc/") to call them. ;)

---

### Post by sayad on 2008-08-11
you can try the simple teqnique.

I suggest you use Gaim instead because YM for Linux is very hard.. =) 
But if you insist on using YM for Linux, here are the instructions: 

1. Download the debian package from the Internet: 

[http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb) 

2. Go to the directory where you saved the debian package and then 
input this line in the terminal: 

sudo dpkg -i ymessenger_1.0.4_1_i386.deb 

3. Wait....And that is it.. =) 

> Thanks to everyone in advance. 

You are welcome.. =)

---

### Post by SnakeMedia on 2008-08-14
Hello do not use YM only Kopete has new feature of Cam driver on Linux :)
If your old cam? please use with spc5xx module driver once making and installing. Thanks :)

Bye SnakeMedia

---

### Post by sayantandas on 2008-09-02
> **PenguinTUX said:**
> hic hic, i'm poor. i can't install Y!M on my Ubuntu! :((
well , u can try anyone of the two things
alt 1. use VoIP and call yahoo messenger / gtalk users from ekiga
here is the setup link[ http://ubuntuforums.org/showthread.php?t=414121]("http://ubuntuforums.org/showthread.php?t=414121")

alt 2. for yahoo messenger video calls use meebo. it provides easy interface to call. may be a little slow though, but effective.   [www.meebo.com](www.meebo.com)
enjoy :)

---

### Post by sayantandas on 2008-09-02
and try gizmo5 as well.
seems to be cool..

---

### Post by skywise on 2008-10-01
The thing missing from the clone yahoo messengers that I'm in need of is the ability to free SMS text to international cell phones.
Now, if someone knows a way to 2way SMS for free (to the Philippines)
I'm all ears and I'll be a much happier ubuntu user.  :)

Sky

---

### Post by gychang on 2008-11-16
> **atomkarinca said:**
> You can find it [here]("http://packages.debian.org/libssl0.9.6").

not there.

gychang

---

### Post by gychang on 2008-11-16
> **atomkarinca said:**
> You can find it [here]("http://packages.debian.org/libssl0.9.6").
sorry, repost.

gychang

---

### Post by loell on 2008-11-16
> **gychang said:**
> sorry, repost.

gychang

just don't install it. ;)

this thread has outdated information and it's more than three years now.

for the nth time, just try the alternatives.

[B]pidgin
kopete
gyachi[/B]

---

### Post by gychang on 2008-11-16
> **loell said:**
> just don't install it. ;)

this thread has outdated information and it's more than three years now.

for the nth time, just try the alternatives.

[B]pidgin
kopete
gyachi[/B]

thanks got pidgin working....

gychang

---

### Post by Uncle Che on 2008-11-19
> **skywise said:**
> The thing missing from the clone yahoo messengers that I'm in need of is the ability to free SMS text to international cell phones.
Now, if someone knows a way to 2way SMS for free (to the Philippines)
I'm all ears and I'll be a much happier ubuntu user.  :)

Sky

You can't be serious, can you? If you are sending sms messages to the Philippines under Windows than you obviously know about Chikka. And if you know about Chikka then you know their widely publicized link up with Google Talk. 

In other words, you can send sms messages to the Philippines for free if you use Pidgin, Empathy, Kopete or any other client that allows Google Talk. Heck, I send free SMS messages straight from my gmail account. 

Log into your google talk account from Pidgin and send a message to 629*********@chikkatalk.com

Substitute the stars for the rest of the mobile number. 

Sorted.

---

### Post by skywise on 2008-11-20
Thanks for the tip but it has a bit of a drawback.
Chikka does allow free SMS to a .ph phone, but only so many are allowed before chikka wants the person with the .ph phone to SMS back (at P2.50 each SMS) so overall it comes out to be fairly expensive.
(I carry a .ph cell phone with me and my wife SMS's that phone back to keep the costs as low as possible)
But it does leave me without a way to fire back SMS to her phone from ubuntu.

---

### Post by Ripfox on 2008-11-20
+1 for Gizmo5 I use it all the time!! (voice aspect)

---

### Post by loell on 2008-11-20
> **skywise said:**
> Thanks for the tip but it has a bit of a drawback.
Chikka does allow free SMS to a .ph phone, but only so many are allowed before chikka wants the person with the .ph phone to SMS back (at P2.50 each SMS) so overall it comes out to be fairly expensive.
(I carry a .ph cell phone with me and my wife SMS's that phone back to keep the costs as low as possible)
But it does leave me without a way to fire back SMS to her phone from ubuntu.

how about, letting her create another YM account, make that account as one of your buddy list, and let that account log in to "mobile"?

---

### Post by rkspaul on 2008-12-27
dpkg: error processing /path/ymessenger_1.0.4_1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/ymessenger_1.0.4_1_i386.deb

---

### Post by rkspaul on 2008-12-27
> **Corvair said:**
> Hy,
Talk about newby, I just installed Ubuntu Linux on the weekend and I have a lot of things I want to implant, like a messenger. Where is the best way to start. I was hoping to install Yahoo but if there is something better like GAIM, I understand, then shoot it to me

Claude:mrgreen:how to install yahoo messenger
Error : Dependency is not satisfiable: libglib1.2

---

### Post by wstay on 2009-01-27
> **linbetwin said:**
> [color=navy]_Edit_: bodhi.zazen ~ Please take note that this how to was written in 2005 and *may* be outdated. In addition Ubuntu now includes applications by default ( Ubuntu and Xubuntu = Pidgin ; Kubuntu = Kopete) that will access the Yahoo network (so not need to install the Yahoo client).[/color]


1. Install libssl0.9.6 through Synaptic or
 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
 replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

I downloaded libssl0.9.6 and tried to install it as follow and got an error message:
root@ubuntu8:/home/wstay/Desktop# apt-get install libssl0.9.6_0.9.6a-1_arm.ipk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libssl0.9.6_0.9.6a-1_arm.ipk
root@ubuntu8:/home/wstay/Desktop#

Could you please help out with this and I could not see or find the partition E: in my computer?

---

### Post by acceph on 2009-01-31
Hello Linbetwin
I don't know exactly your problem already fix or not.
but I used Ubuntu 8.04, there are pidgin on it.
I found that it's very easy to use, it's multi protocol.

but there are some bugs I think, because I couldn't connect to my Yahoo, 
then I change into it's IP address
Then OK ^^
please visit [**www.cah25.wordpress.com**]("http://cah25.wordpress.com/2009/01/08/yahoo-messenger-di-ubuntu/")

---

### Post by mtcycler on 2009-06-25
64bit anyone, what it the link to the 64bit yahoo messenger, I can download the i386 but I need a amd64 / x86_64 .deb

---

### Post by fish_b0oy on 2009-06-29
don't install that old YM for Linux!
better use [http://webmessenger.yahoo.com/](http://webmessenger.yahoo.com/)

---

### Post by Short__Error on 2009-07-01
As long as you have Pidgin then you are able to login to your Yahoo Messenger with no problems.

---

### Post by Gonzalo_VC on 2009-07-17
> **Short__Error said:**
> As long as you have Pidgin then you are able to login to your Yahoo Messenger with no problems.

[COLOR="Navy"]That's the point! Recently (July2009) Yahoo system is not accepting some "old protocols" for connection with yahoo messenger, thus, Pidgin is not connecting:(  aMSN doesn't connect to yahoo or other protocols but MSN. 
I run the Y-m installer with wine. It did install smoothly :o but it doesn't connect, either :confused:.

However, Kopete stills connects... but it has to install some KDE stuff on your Gnome-Ubuntu (no big deal).

Some people might say "Why do you want yahoo messenger, or anything else 'window$ world' like on your Ubuntu?" And I may say: why not!? Linux is **freedom** to choose and use what you want or need! and for the Yahoo-mail users, the Y-messenger is quite useful and fun! ;) 
Programers keep inventing different messengers... please, revive the old Yahoo messenger for *nix!!!

Cheers![/COLOR]

---

### Post by kickwin on 2009-07-31
Can this older version of YM support calling phones using Yahoo Voice?

---

### Post by Gokul Krishnan.G on 2009-08-18
> **linbetwin said:**
> [COLOR=navy]_Edit_: bodhi.zazen ~ Please take note that this how to was written in 2005 and *may* be outdated. In addition Ubuntu now includes applications by default ( Ubuntu and Xubuntu = Pidgin ; Kubuntu = Kopete) that will access the Yahoo network (so not need to install the Yahoo client).[/COLOR]


{ 1. Install libssl0.9.6 through Synaptic or
 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
 replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.  }
  

I tried.. but at the very beginning it shows this error....

E: Couldn't find package libssl0.9.6

Wat shall i do now?

---

### Post by tmsbrdrs on 2009-09-01
> **BLTicklemonster said:**
> Our gaming clan uses yahoo for voice chat in our biweekly meetings, so I put in vmware and xp and use yahoo messenger in it to talk. I really wish there was a way to use voice chat in yahoo in ubuntu without having to do all that.

Have you tried GyachI?

I know it does file transfer and webcams work perfectly. It also does rooms and apparently has voice support, though I haven't gotten it to work yet. 

Anyway, the PPA can be found at the link below.
[https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)

---

### Post by m.alaa8 on 2010-05-12
you can use [skype]("http://www.skype.com") and leave yahoo
download linux version

---

### Post by Linuxforall on 2010-05-12
Gyachi works very good and latest can be found at [https://launchpad.net/~baudm/+archive/ppa](https://launchpad.net/~baudm/+archive/ppa)

---

### Post by msrinath80 on 2010-05-13
Thanks very much for that link Linuxforall. I was planning on building it from scratch and you saved my time :)

---

### Post by poricoder on 2010-06-21
oOoOoOoOH.
hi to all.
im beginner in ubuntu and want to chat with YAHOO MESSENGER but can't.
can u help me to do chat with another program in ubuntu like a gaim.
very Thanks .:lolflag:

---

### Post by Gonzalo_VC on 2010-06-21
> **poricoder said:**
> oOoOoOoOH.
hi to all.
im beginner in ubuntu and want to chat with YAHOO MESSENGER but can't.
can u help me to do chat with another program in ubuntu like a gaim.
very Thanks.

[COLOR="Navy"][SIZE="2"]I prefer [Pidgin]("http://pidgin.im/")... but Ubuntu comes with Gnome's [Empathy]("http://live.gnome.org/Empathy") nowadays... Both may work as yahoo-messenger clients and you can communicate with all your YM and MSN contacts.
Cheers![/SIZE][/COLOR]

---

### Post by proggy on 2010-06-21
There is nothing that is better for Yahoo Messenger on Linux that Gyachi ,I don`t know why it`s not more widely used

---

### Post by bjorkiii on 2010-06-22
I use a programme called y!epic through wine no cam use at the minute i know but it does for me.

---

### Post by Linuxforall on 2010-06-22
> **proggy said:**
> There is nothing that is better for Yahoo Messenger on Linux that Gyachi ,I don`t know why it`s not more widely used

Agreed, its actually more full fledged and safer than Yahoo messenger itself.

---

### Post by YannBuntu on 2010-07-05
A more recent version of Gyachi is here : [https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)

Has anyone managed to do voice calls with Gyachi ?


FYI, to do voice/video calls with Windows interlocutors, I recommend :
- Ekiga (which exists also on Windows)
- Empathy (with Telepathy PPA , and ubuntu-restricted-extras package, and of course a Jabber account e.g. gmail address), that can do voice&video calls with Windows Gtalk interlocutors
- Skype (which exists also on Windows), but this one is not open-source

---

### Post by proggy on 2010-07-05
> **YannBuntu said:**
> A more recent version of Gyachi is here : [https://launchpad.net/~loell/+archive/ppa]("https://launchpad.net/%7Eloell/+archive/ppa")

Has anyone managed to do voice calls with Gyachi ?


FYI, to do voice/video calls with Windows interlocutors, I recommend :
- Ekiga (which exists also on Windows)
- Empathy (with Telepathy PPA , and ubuntu-restricted-extras package, and of course a Jabber account e.g. gmail address), that can do voice&video calls with Windows Gtalk interlocutors
- Skype (which exists also on Windows), but this one is not open-source
voice wont work in 64 bit but i think it does in 32 bit

---

### Post by YannBuntu on 2010-07-05
Thank you. Anyone can confirm audio calls work on Gyachi 32 bits ?

---

### Post by anish_sha on 2010-12-30
i want yahoo chat rooms... and the given [procedure is not working... how to get it guys?

---

### Post by Thras0 on 2011-01-07
i used the win version of yahoo messenger on  64 bit ubuntu under wine and it kinda works, but has crashed several times. i haven't tried the 32 bit version.

---

### Post by YannBuntu on 2011-01-07
> **Thras0 said:**
> i used the win version of yahoo messenger on  64 bit ubuntu under wine and it kinda works, but has crashed several times. i haven't tried the 32 bit version.

Have you been able to do audio or audio+video call ?

---

### Post by louiech21 on 2011-03-02
I know this is a very old discussion, just wanted to share this site with you guys.  It's a web gui to use all sorts of different instant messengers.

[https://imo.im/]("https://imo.im/")

---

### Post by marl30 on 2011-03-02
> **louiech21 said:**
> I know this is a very old discussion, just wanted to share this site with you guys.  It's a web gui to use all sorts of different instant messengers.

[https://imo.im/](https://imo.im/)

Great mention. I shared this in a thread a few days ago. I surprise not much persons actually responded, as I've seen quite a few threads asking how to make voice calls using Yahoo and Messenger Live on Linux.

---

### Post by Gonzalo_VC on 2011-03-02
> **marl30 said:**
> Great mention. I shared this in a thread a few days ago. I surprise not much persons actually responded, as I've seen quite a few threads asking how to make voice calls using Yahoo and Messenger Live on Linux.

Yeah... Imo, eBuddy, etc. ... but web-messengers are not the same that an installed one ;) If I can't get yahoo messenger, I rather stay with Pidgin or Kopete :) (I don't like Empathy).

In the past I also tried Y-messenger under wine, 32 bits Ubuntu, but _didn't work_ well.

Cheers.

---

### Post by rvchari on 2011-03-02
> **linbetwin said:**
> [color=navy]_Edit_: bodhi.zazen ~ Please take note that this how to was written in 2005 and *may* be outdated. In addition Ubuntu now includes applications by default ( Ubuntu and Xubuntu = Pidgin ; Kubuntu = Kopete) that will access the Yahoo network (so not need to install the Yahoo client).[/color]


1. Install libssl0.9.6 through Synaptic or
 2. Download [this]("http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb") file from messenger.yahoo.com.

3. In a terminal, write:
 replacing [COLOR=Red]path[/COLOR] with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

for those who wish to have a yahoo messenger for windows / mac like experience, its better to install yahoo messenger for windows under wine. linux version is seemingly out dated and unfortunately there isnt any upgrades coz options like pidgin / empathy / kopete come shipped with the ubuntu install...

---

### Post by marl30 on 2011-03-04
> **Gonzalo_VC said:**
> Yeah... Imo, eBuddy, etc. ... but web-messengers are not the same that an installed one ;) If I can't get yahoo messenger, I rather stay with Pidgin or Kopete :) (I don't like Empathy).

In the past I also tried Y-messenger under wine, 32 bits Ubuntu, but _didn't work_ well.

Cheers.

Yeah, but those can't make voice calls while IMO can. If I just need to do text chat, I'll use the installed ones. But for Voice chat over Yahoo and MSN, I use IMO.

---

### Post by YannBuntu on 2011-03-04
Thanks for the tip :)
Is it possible to do video+voice conversation with YahooM protocol, via IMO ?

---

### Post by marl30 on 2011-03-05
> **YannBuntu said:**
> Thanks for the tip :)
Is it possible to do video+voice conversation with YahooM protocol, via IMO ?

I've never tried video chat before, but I'm positive voice chat works as I have used it. You only have to make sure you enable microphone from settings. It does say it supports video chat though.

---

### Post by xx58 on 2011-03-05
:rolleyes:I like install Gyachy on Ubuntu 11.04 Natty Narwal. Where I can find it???

---

### Post by arisepeter on 2011-11-12
Yahoo messenger for Linux is a very old version. I have downloaded it and it is not easy to configure it. There is program called "Gyache'  is almost same as Yahoo messenger. Unlike other IM in Linux like AIM or Empathy it can be used for getting rooms and chat with anybody.
please check this link to download it
[[COLOR=Blue]http://www.messengeroo.com/yahoo-messenger/chat-client/gyachi-yahoo-messenger-for-linux-with-webcam-voice-n-chat-room[/COLOR]]("http://www.messengeroo.com/yahoo-messenger/chat-client/gyachi-yahoo-messenger-for-linux-with-webcam-voice-n-chat-room/")

---

### Post by atoztoa on 2012-12-09
Also check out : [http://www.atoztoa.com/2009/06/yahoo-messenger-in-ubuntu.html](http://www.atoztoa.com/2009/06/yahoo-messenger-in-ubuntu.html)

---

### Post by atoztoa on 2012-12-09
> **xx58 said:**
> :rolleyes:I like install Gyachy on Ubuntu 11.04 Natty Narwal. Where I can find it???

Use this tutorial : [http://www.atoztoa.com/2009/06/yahoo-messenger-in-ubuntu.html](http://www.atoztoa.com/2009/06/yahoo-messenger-in-ubuntu.html)

---

### Post by Sef on 2012-12-09
Locked. Necromancing.

---

