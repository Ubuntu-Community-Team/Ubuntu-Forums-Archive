---
title: "hebUbuntu"
date: 2005-10-01
forum: The Cafe
---

### Post by mangar on 2005-10-01
note: Sorry for the missuse of the thread, I wanted a quick, user editable 
place to hold some files.

*** [COLOR="Blue"]current version 0.9.3[/COLOR] ***

-- Notice: targets release 5.10 of ubuntu (the breezy badger)
-- Notice: Older version of HebUbuntu are not supported, as there are massive bug fixes in each version

[COLOR="Red"]what is HebUbuntu?[/COLOR]
it's a script that automates the most common initial steps a new,
hebrew language speaking, user does.
Heavily based on Keyes's EasyUbuntu, and Automatix (in a monkey see, monkey do fashion)

Goals:
Ask no questions, make anything Just-Work.

Does:
1. installs hebrew support, hebrew applets, spellcheckers, etc.
2. install multimedia codecs.
3. installs plugins for firefox.
4. sets up 3d acceleration for ATI/nVidia video cards.
5. installs midi support
6. fixes autohinting, changes some fonts.
7. installs some basic p2p programs.
8. more. read the changelog!

Todo:
1. make it a single file.
2. remove user interaction from the 3d acceleration support. (Done for nVidia)
3. add support for dialers. (see "The Israeli Internet Wizard", at the bottom)
    NOT maintained by me.
4. make it a generic, auto locale dependant, tool, for the rest of the world.

How to run HebUbuntu:
01. left-click on the archive, select - extract here.
    note - must not be to a fat32 or ntfs partition (both windows file systems).
02. double click on the folder "HebUbuntu"
03. double click on the file "hebUbuntu"
04. a dialog will appear, choose "run"
05. read the following window carefully!
06. close your firefox sessions
07. insert your root password
08. notice: if you haven't closed your firefox sessions, they will be killed.
09. take your time, stuff is downloaded.
10. when prompted, set up your nVidia or ATI card.
     choose "fglrx" for ATI card
     choose "nvidia" for nVidia card.
11. reboot (or restart your x-session)


How can YOU help?
1. fix bugs.
2. add features.

[COLOR="Red"]
Workflow: [/COLOR]
Versioning is done in a x.y.z-yourname fashion
If you find a bug and fix it,    add 1 to the value in z (0.1.1 -> 0.1.2)
If you add a feature,            add 1 to the value in y (0.1.1 -> 0.2.1)
If you made a major change,  add 1 to the value in x (0.1.1 -> 1.1.1)

For example: if you've fixed a bug, and your name is "kenny", and the last
version on this post is, for example, 10.9.2-cartman,
upload your new version, and name it 10.9.3-kenny

I don't promise to maintain the program, please don't ask me for features
or bugfixes (but you are free to implement and upload it yourself!).

[COLOR="Red"]Changelog:[/COLOR]
whats new in version 0.9.3:
1. fix to the broken package status of skype (by using the plf packages)
    --only good for x86.
2. updates openoffice.org to version 2 final (supposed to fix some hebrew bugs)
3. updated repositories.

whats new in version 0.9.2:
1. a bug was fixed - wrong permissions (thanks yotama9 !)
2. added some extra progress windows.
3. cleaned the sources.list files

whats new in version 0.9.1:
1. now uses sijp packages for culmus and culmus-fancy fonts
   (fixes a bug in the official packages.
2. added a changelog file

whats new in version 0.9.0 (YAAR!!! - Yet Another Automatix Ripoff)
1. removed user interactioin from nVidia card setup
2. enabled DMA for optical drives for AMD and Intel.

whats new in version 0.8.1
disabled the font changing - doesn't work for certain users
(Thanks DimaIL !)

whats new in version 0.8.0 
bug fix release (and I broke my own workflow, yay!)

whats new in version 0.7.6
1. bug fix. thanks sijp
2. disabled installation of azureus for now. will fix it later

whats new in version 0.7.5
1. new way to change firefox's fonts.
2. changed w32codecs server to a less crowded one (thank testing bunny!)
3. some code cleanups
4. added a reboot message.
5. trying to fix an issue with the gnome interface fonts

whats new in version 0.6.4
bug fix release - thanks Erthium!

whats new in version 0.6.3
1. changed mplayer-386 to mplaye-custom
2. added a purge to mozplugger
3. kills any open firefox windows

whats new in version 0.6.1 "Automatix ripoff "
1. changed the way azureus is installed.
2. changed mplugger to mozilla-mplayer (works better)
3. added support for midi
4. added a bugfix for multiple audio sink.

whats new in version 0.4.1:
1. enables embedded web-media (installs totom-xine and mozplugger)
2. experimental fix for the firefox font problem 
    --will not work without closing all active firefox instances before running
    the script!
3. clearer legal warning

whats new in version 0.3.1:
1. fixes the week-doesn't-start-on-sunday problem.
(note: changes en_US and he_IL locale files, may require a reboot to 
work)

whats new in version 0.2.1:
1. added Support for amd64 (not perfect, see README)
2. added support for fonts (enables autohinter, changes some of gnome's fonts)
3. some bugfixes
4. bundled some fonts.

as usual, I'll need your feedback and bug reports.




Update: 
1. A link to [COLOR="DarkOrange"]The Israeli Internet Wizard[/COLOR] (ADSL/ Cable / Dialup support)
[http://kinneret.berlios.de/forums/viewtopic.php?t=1764](http://kinneret.berlios.de/forums/viewtopic.php?t=1764)
(note: I do NOT maintain the Wizard)

2. if you want to post bug report in hebrew, you can do it at 
[www.whatsup.org.il](www.whatsup.org.il)
I post there as &#1502;&#1504;&#1495;&#1501; (&#1500;&#1488; &#1502;&#1495;&#1493;&#1489;&#1512;
  menahem
--read the forum's rules first!

---

### Post by eyalben on 2005-10-01
I tried to run this scripts, but I recieved:
cp: cannot stat `lang/en/EasyUbuntu.mo': No such file or directory
./eu: line 11: syntax error near unexpected token `multimedia'
./eu: line 11: `        multimedia'

---

### Post by Avi on 2005-10-01
Hey fellow Israelis.
Sounds great!
One of the biggest issues I had with Ubuntu is the lacking Hebrew support. (You can read about my troubles in the 4 episodes of my [ So I've decided to switch to Linux](http://www.avidardik.com/2005/02/13/so-ive-decided-to-switch-to-linux-episode-1-introduction/) journal)
In any case I BEG of you to make sure the most important feature is there:
Have two distinct options:
1. Full Hebrew Support - Everything you detailed in your post.
2. "Enabled" Hebrew Support - EVERYTHING support Hebrew reading and writing but NO Hebrew menues!!!
That's super important!
I know MANY people are like me with this. We do want full Hebrew support of course, but we our regular English interface.

I know you didn't want feature requests, but since I'm a user and not a programmer, I cannot do this myself so I'm requesting only...

---

### Post by mangar on 2005-10-01
I've made some extra simplification to the script,
please try it now.
(caution is advised, it wasn't extensively tested..)

(if you have the time, please read the script, and tell me where to improve it.)

Avi: the scripts target the upcoming version 5.10, which have a Language
Selector component, that enables exactly what you want.
(and please, you don't have to beg.. I'm editing this script without any
previous knowledge in bash scripting, and its a miss and hit kind of thing,
so, don't hesitate to make any changes you see fit)

I want a minimum user interaction, therefore the script shouldn't ask
the user what he wants (I know it can be annoying, but I'm trying to aim
to the lower common denominator here)

If you can, please improve this script! 
Ideas (that I'm not sure how to implement, you help is welcome):

1. set up fonts for firefox and the interface (I'm not sure how to
edit the configuration files, especially when we don't want to break 
the current user files! (otherwise, I'll just overwrite them)

2. edit the /etc/X11/xorg.conf file, without telling the user to run
dpkg-reconfigure xserver-xorg (same problem as with item #1)

3. I don't remember what troubled me when using linux for the first time,
I'm running the current install from the warty days, and most stuff has 
been automagically fixed along the way (or that I've fixed it in a few 
minutes and forgot about it). Bummer (I mean: Ba'a'sa)

---

### Post by t_ras on 2005-10-08
so is there or isn't there support for herbrew in obuntu? (at list to write inbrowser+office)

---

### Post by t_ras on 2005-10-08
ok tryed it (o 5.04 AMD64)
seems like it did alot but at the end did nothing, still all the same. I saw it changed cofiguration files, and as I logged in I was prompted that GNOME and X KB definitions are diferent (for wich I choosen GNOME), I still don't write hebrew.
any thing I can do?

---

### Post by mangar on 2005-10-08
Hi Ras!
Hebrew support is enabled in ubuntu, but my script doesn't take care of it.
The Hebrew support should have been configured when you've installed 
Ubuntu in the first time (note - I'm refering to 5.10, I don't rememeber
what happened before that)
the easy way to configure hebrew support, is to run from the console:
sudo dpkg-reconfigure xserver-xorg
and when you'll have a dialog with the title:

"please select your keyboard layout"

write in the text-box : us,il
there will be some other question,
then you'll get a question:
"Please select your keyboard options"
write: grp:alt_shift_toggle

answer the rest as you see fit, and it should work.

&#1499;&#1502;&#1493; &#1513;&#1488;&#1514;&#1492; &#1512;&#1493;&#1488;&#1492; (&#1488;&#1504;&#1497; &#1502;&#1511;&#1493;&#1493;&#1492;), &#1488;&#1508;&#1513;&#1512; &#1500;&#1499;&#1514;&#1493;&#1489; &#1489;&#1506;&#1489;&#1512;&#1497;&#1514; &#1489;&#1500;&#1497;&#1504;&#1493;&#1511;&#1505; (&#1499;&#1512;&#1490;&#1506;, &#1506;&#1500; &#1489;&#1512;&#1497;&#1494;&#1497; &#1493;&#1508;&#1497;&#1497;&#1512;&#1508;&#1493;&#1511;&#1505;)

&#1489;&#1492;&#1510;&#1500;&#1495;&#1492;!
&#1491;&#1512;&#1498; &#1488;&#1490;&#1489;, &#1488;&#1501; &#1497;&#1513; &#1500;&#1498; &#1512;&#1506;&#1497;&#1493;&#1504;&#1493;&#1514;, &#1488;&#1513;&#1502;&#1495; &#1500;&#1513;&#1502;&#1493;&#1506;

---

### Post by mangar on 2005-10-08
I forgot a few points:
1. when prompted, select the xorg rules (that's what we're changing - 
    to alt_shift)
2. what where you expecting that will happen, and didn't? please note 
that the groups switching (i.e. from hebrew to english with alth_shift)
isn't at the scope of the script.

3. did the w32codecs and flash work for you? I was told that they are 
problematic under amd64 installation (I don't have amd64, so I can't check 
it myself. on the other hand, if you've got a spare machine... ;) )

!×‘×”×¦×œ×—×”

---

### Post by mangar on 2005-10-08
new version!

---

### Post by t_ras on 2005-10-10
[QUOTE=mangar]I forgot a few points:
1. when prompted, select the xorg rules (that's what we're changing - 
    to alt_shift)
2. what where you expecting that will happen, and didn't? please note 
that the groups switching (i.e. from hebrew to english with alth_shift)
isn't at the scope of the script.

3. did the w32codecs and flash work for you? I was told that they are 
problematic under amd64 installation (I don't have amd64, so I can't check 
it myself. on the other hand, if you've got a spare machine... ;) )

!×‘×”×¦×œ×—×”[/QUOTE]


all worked fine I think. only office is lacking hebrew....

---

### Post by mangar on 2005-10-10
in OpenOffice writer, 
click on the menu:
tools->options->language-settings->language

and in the box :
Enable for complex txt Layout - mark it with a V

in the box:
CTL

choose Hebrew.

---

### Post by mangar on 2005-10-14
new version

---

### Post by mangar on 2005-10-16
new version

---

### Post by mangar on 2005-10-23
new version

---

### Post by yotama9 on 2005-11-15
hello.

I have downloaded, enabled the script to rum (through chmod) and run it, using sudo 

then a window opend telling me what will happen. 

afterwards abusukutky nothing have happened

what am I douing wrong?

thank you yotam

---

### Post by mangar on 2005-11-17
yotama9's reported bug has been fixed.
new version 0.9.3

---

### Post by yotama9 on 2006-02-04
hi

remember me? long time...

any way I have just finshed installing dapper and used the hedubuntu script.

it had made alot of problam and I had to change the script so the p2p programs won't be install:confused: . finally I have maaged to use hebrew at openoffice writer....\\:D/ 

I suggest you to check it out:-k 

bye
yotam

---

### Post by lodp on 2006-03-13
does this thing do anything with the culmus package? 

culmus 0.101-2, which is the one available in the ubuntu repositories, doesn't go smooth with openoffice2 (i only got empty squares displayed, and i've heard other people bitchin about the same problem). 

i downgraded to culmus 0.93 (which you can get on their sourceforge page: [http://sourceforge.net/project/showfiles.php?group_id=59410)](http://sourceforge.net/project/showfiles.php?group_id=59410)), now it works fine..

---

### Post by mangar on 2006-03-27
hi Yotam!
the hebUbuntu script supports only version 5.10 of Ubuntu, and will not,
in any stage, support the development release - too much stuff is changed
and fixed, and i don't have the time to follow suit.

I'll write a script for dapper (version 6.06) when it will be officially out,
until then:
1. install breezy
2. run HebUbuntu
3. upgrade to dapper.

temporary solution (i use dapper myself, so i've had those problems):
download azureus from it's website, and unzip it in some directory.
it works for me, but ymmv.


mangar

---

### Post by haimroman on 2007-01-07
I came here because I have Ubuntu 6.10.  I have Hebrew, but many "common" Hebrew fonts don't show up in Open Office 2 (e.g., David, Frank Ruehl).  Yes, I enabled "CTL".

I might be going crazy, but I couldn't find in this forum from where to download hebubuntu.  Where is it?

Does it support Ubunut 6.10?

Does it have an option for leaving the menus in English?

Thanks.

-- Haim

---

### Post by raziv on 2007-02-28
> **haimroman said:**
> I came here because I have Ubuntu 6.10.  I have Hebrew, but many "common" Hebrew fonts don't show up in Open Office 2 (e.g., David, Frank Ruehl).  Yes, I enabled "CTL".

I might be going crazy, but I couldn't find in this forum from where to download hebubuntu.  Where is it?

Does it support Ubunut 6.10?

Does it have an option for leaving the menus in English?

Thanks.

-- Haim

Ahlan Haim,

From googling around, it seems the latest version is 0.9.3, and a link to that version can be found in the first post of this thread (right at the bottom of the post - really hard to find indeed).
I'm running ubuntu Dapper, and I directly installed the culmus and culmus-fancy fonts packages via synaptic. The culmus fonts were installed corretly (on my distribution's native OOo 2.0 installation) :) , but the culmus-fancy ones were not :( .

-- raziv

---

