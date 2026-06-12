---
title: "HOW TO: Configure wireless cards with Broadcom chipsets"
date: 2005-04-10
forum: Tutorials
---

### Post by jonny on 2005-04-10
[size=4]Edit: bodhi.zazen - [b][COLOR="DarkRed"]Please note, this thread is from 2005 and although it turns up on a google search the information is out of date.

Please see the [Ubuntu wiki broadcom page](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)[/b][/size][/COLOR]



[i]6 July 2006 Update
I haven't had a Broadcom card for many months, but I've been told this how-to doesn't work properly under Dapper.  Here are a couple of links that have been passed to me - but I can't vouch for their quality.

[http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working](http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working)
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Good luck.  I'm very happy that this how-to has helped so many people in the past year or so.[/i]

Broadcom wireless cards are tricky to set up in ubuntu, and the forums are full of frustrated users seeking advice.  Broadcom provide no Linux support (feel free to complain to your hardware vendor or choose a different card if you haven't yet shelled out your cash), but they can be made to work - and you're in the right place if you want to know how.

First, you need to find out if this How To is for you.  Broadcom wireless cards come under many brand names and, in particular, are used in many Dell and Acer laptops.  Look for the drivers supplied with your card (Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON); if you have a file called bcmwl5.inf or bcmwl5a.inf then keep on reading.  You won't succeed without following these instructions!

0. Before you start, clear out any mess from existing failed attempts to use ndiswrapper.  Note that you shouldn't use a root terminal to execute the code in this how-to; use a normal terminal session instead.```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```Some of these steps may report errors; just ignore them.

1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop

2. Follow the advice given here under [How to add extra repositories](http://ubuntuguide.org/#extrarepositories)

3. Open a terminal session and enter this code.  Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```4. Reboot your PC.  On restarting, the light on your wireless card should come on.  If not, try entering```
sudo modprobe ndiswrapper
```5. Your card is now working.  Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings.  Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one.  You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK.  The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK.  Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana.  If everything works, you can delete the file from your desktop.

13.  You might notice that the signal strength applet doesn't work properly.  This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled.  Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.

[COLOR=Indigo](Note: This how-to has been updated to reflect all comments from the thread up to 19 April)[/COLOR]

---

### Post by poofyhairguy on 2005-04-10
great Howto. I need this next weekend. What a lifesaver...

---

### Post by Chromance on 2005-04-11
what version of Ndiswrapper is included in the ubuntu 5.04? should be 1.1?

---

### Post by Remix_88 on 2005-04-12
You don't have to edit all the .conf files by hand. Replace steps 'sudo gedit' and Step 4 with the following...

```
$ sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
```

---

### Post by kuleali on 2005-04-12
it worked, thank you

---

### Post by jonny on 2005-04-12
[QUOTE=Remix_88]You don't have to edit all the .conf files by hand. Replace steps 'sudo gedit' and Step 4 with the following...

```
$ sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
```[/QUOTE]Thanks; I've updated the how-to.  I knew you could use sed instead of gedit, but couldn't get the syntax quite right.  You're obviously smarter then me!

By the way, if you get here from a search engine, I imagine this would work for any other Debian based distros.  Steps 5 onward need Gnome, but KDE has equivalent tools.

---

### Post by Musiknonstop on 2005-04-13
Hi,

When I use the sed command the output just oes to the terminal window. The files do not get changed. Does anyone know what I'm doing wrong here?

Thanks

---

### Post by jonny on 2005-04-13
I'll have to test this tomorrow.  In the meantime, you need to replace the sed command with these steps:

 - sudo gedit
 - This will open a text editor.  Open every file in the directory /etc/ndiswrapper/bcmwl5/ and replace every instance of RadioState|1 with RadioState|0
 - continue with step 4

Sorry for the confusion.

---

### Post by Antman on 2005-04-13
Thank you, thank you, thank you. I knew all the steps but the "sed" step.

I'm going to boot into Ubuntu now and try it. :smile: 

Ant

---

### Post by Antman on 2005-04-14
[QUOTE=jonny]I'll have to test this tomorrow.  In the meantime, you need to replace the sed command with these steps:

 - sudo gedit
 - This will open a text editor.  Open every file in the directory /etc/ndiswrapper/bcmwl5/ and replace every instance of RadioState|1 with RadioState|0
 - continue with step 4

Sorry for the confusion.[/QUOTE]

Johnny,

Thanks for posting this. After I edited the .conf files my card started working after doing modprobe. Writing post via my new wireless Ubuntu laptop....  \\:D/ 

Ant

---

### Post by jonny on 2005-04-14
I've updated the code to correct the error reported by Antman.  If you get any trouble, drop the 3 lines beginning with "for confile in..." and follow the temorary instructions that I gave to him (her?).

Could the first person to use this please report whether it succeeded.  It's hard for me to test it properly, as my wireless lan's already working!

---

### Post by jdodson on 2005-04-14
[QUOTE=Chromance]what version of Ndiswrapper is included in the ubuntu 5.04? should be 1.1?[/QUOTE]

its something like 1.0rc2 if memory serves.  it works really well from what i have seen.  occasionally there are some hiccups, but it is pretty stable.

---

### Post by kb00heda on 2005-04-15
Thanks jonny!

It worked perfect on my Acer Ferrari 3000 laptop. Had to "sudo modprobe ndiswrapper" after login, for wlan0 to show up as a selectable option in Gnome (i.e. under the network settings), but afterwards it was all OK.

Is there a way to do the configure the network settings outside Gnome, e.g., in XFCE, which I'm currently using? I suppose there must be but I don't know how. Does anyone else know better?

P.S. This message was also written/posted using WLAN. D.S.  :)

---

### Post by jonny on 2005-04-15
[QUOTE=kb00heda]Is there a way to do the configure the network settings outside Gnome, e.g., in XFCE, which I'm currently using? I suppose there must be but I don't know how. Does anyone else know better?[/QUOTE]

It's fairly simple to define network settings from the command line.  Without creating an enormous tutorial, this is what you do:

- Create some entries in /etc/network/interfaces.  The man pages for this file are pretty good, so you shouldn't have too much difficulty.  It's particularly powerful if you use the pre up, post up, pre down and post down functionality - for example to load / unload ndiswrapper or to mount / unmount network drives.

- To start, simply type sudo ifup.  Again, the man pages are good.

- sudo ifdown will disconnect you.

Bear in mind that the gnome networking tool overwrites this file.  Keep a backup if you ever plan to use that tool, or your hard work might be destroyed.

---

### Post by fazer on 2005-04-15
Hello,

I have a MN 720 Wifi card ( made from Microsoft) and I heard that it uses the Broadcom chipset.  I was wondeirng that if I could use this how-to:
[http://tuxspot.blogspot.com/2005/02/microsoft-mn-720-driver-update.html](http://tuxspot.blogspot.com/2005/02/microsoft-mn-720-driver-update.html)

will I have the same results?  That how-to was done on Suse 9.2.  Will I get the same results in Ubuntu?

Thanks.

---

### Post by vaughnet on 2005-04-17
[QUOTE=jonny]I've updated the code to correct the error reported by Antman.  If you get any trouble, drop the 3 lines beginning with "for confile in..." and follow the temorary instructions that I gave to him (her?).

Could the first person to use this please report whether it succeeded.  It's hard for me to test it properly, as my wireless lan's already working![/QUOTE]
 Hello,
I am brand new to linux and chose Ubuntu for the great community that seems to surround it. I am trying to get a Dell TrueMobile 1300 up and running with this "how to". I didn't have any trouble until I rebooted with no luck.

Upon entering "sudo modprobe ndiswrapper" I get the following message:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Any help would be greatly appreciated.

---

### Post by sparke67 on 2005-04-17
[QUOTE=vaughnet]Hello,
I am brand new to linux and chose Ubuntu for the great community that seems to surround it. I am trying to get a Dell TrueMobile 1300 up and running with this "how to". I didn't have any trouble until I rebooted with no luck.

Upon entering "sudo modprobe ndiswrapper" I get the following message:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Any help would be greatly appreciated.[/QUOTE]
 thanks for great write up I was directed here by fellow user with great patience --- I too an new and geting this :

sparke67@shawnlinux:~ $ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
sparke67@shawnlinux:~ $ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4321.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.conf: Permission denied
sparke67@shawnlinux:~ $

---

### Post by sparke67 on 2005-04-17
re ran as root and now like the other guy:
sparke67@shawnlinux:~ $ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format
sparke67@shawnlinux:~ $

---

### Post by jonny on 2005-04-17
[QUOTE=sparke67]re ran as root and now like the other guy:
sparke67@shawnlinux:~ $ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format
sparke67@shawnlinux:~ $[/QUOTE]Hmmm, that's two of you with an almost identical error message that I've never heard reported before.  I don't know what the issue is, but I suggest a few routes for exploring possible solutions:

1. Start again from the beginning.  Use ```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo rm -r /etc/ndiswrapper/bcmwl5
``` to undo the effects of what you've done to date.
2. There are two drivers associated with thes cards, bcmwl5 and bcmwl5a.  Most cards can accept either (mine certainly can), but some can only accept one or the other.  If you have the 5a driver available, try repeating the how-to but repeat every instance of "bcmwl5" with "bcmwl5a".
3. Try downloading the latest version of the XP drivers from [Dell's website](http://support.dell.com/support/downloads/index.aspx?c=us&cs=19&l=en&s=dhs) and starting again.  Try using both bcmwl5 and bcmwl5a
4. Just in case my script isn't working properly in all cases, try this: replace the three lines beginning with "for conffile...", "sudo cat..." and "done" with "sudo gedit".  This will open a text editor; use it to open every file in the directory /etc/ndiswrapper/bcmwl5/ and replace every instance of RadioState|1 with RadioState|0
5. (Yuk) Try grabbing the latest version of ndiswrapper and compiling it yourself.  You'll find several sets of instructions between the forums and the wiki.

Please post your results for the benefit of the rest of the community.

---

### Post by sparke67 on 2005-04-17
Some results of trying the first part :

sparke67@shawnlinux:~ $ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
sparke67@shawnlinux:~ $ sudo ndiswrapper -e bcmwl5
sparke67@shawnlinux:~ $ sudo ndiswrapper -l
No drivers installed


sparke67@shawnlinux:~ $ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules

sparke67@shawnlinux:~ $ sudo rm -r /etc/ndiswrapper/bcmwl5
rm: cannot remove `/etc/ndiswrapper/bcmwl5': No such file or directory
sparke67@shawnlinux:~ $

---

### Post by Seth on 2005-04-17
What does dmesg say after you try to modprobe it and it's invalid? I'll bet you have a compiler mismatch.

---

### Post by vaughnet on 2005-04-17
> **jonny]Hmmm, that's two of you with an almost identical error message that I've never heard reported before.  I don't know what the issue is, but I suggest a few routes for exploring possible solutions:

1. Start again from the beginning.  Use ```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo rm -r /etc/ndiswrapper/bcmwl5
``` to undo the effects of what you've done to date.
2. There are two drivers associated with thes cards, bcmwl5 and bcmwl5a.  Most cards can accept either (mine certainly can), but some can only accept one or the other.  If you have the 5a driver available, try repeating the how-to but repeat every instance of "bcmwl5" with "bcmwl5a".
3. Try downloading the latest version of the XP drivers from [Dell's website](http://support.dell.com/support/downloads/index.aspx?c=us&cs=19&l=en&s=dhs) and starting again.  Try using both bcmwl5 and bcmwl5a
4. Just in case my script isn't working properly in all cases, try this: replace the three lines beginning with "for conffile...", "sudo cat..." and "done" with "sudo gedit".  This will open a text editor said:**
> 
 1. I started again from the beginning.
2. I tried both drivers (starting from the beginning each time with the most recent version of each).
3. Double-checked with downloaded drivers from Dell.
4. Manually changed the RadioState for each .conf file
5. Researched and compiled the latest ndiswrapper (1.1)

Finally got this result:

[QUOTE]root@laptop:/home/vaughnet # modprobe ndiswrapper
root@laptop:/home/vaughnet #

Then went to System>Administration>Networking only to find no available wireless interface. Numerous restarts and plugging the card in and out has seemed to work. I truly believe I have exhausted every conceivable option. Any ideas...?

---

### Post by sparke67 on 2005-04-17
[QUOTE=Seth]What does dmesg say after you try to modprobe it and it's invalid? I'll bet you have a compiler mismatch.[/QUOTE]

is this what I am looking for ?

sparke67@shawnlinux:~ $ dmesg
Linux version 2.6.8.1-5-386 (buildd@rothera) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Thu Apr 7 08:47:11 UTC 2005

or maybe this ?

ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper (wrapper_init:2286): loadndiswrapper failed (1536);check utils version mismatch
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper (wrapper_init:2286): loadndiswrapper failed (1536);check utils version mismatch
sparke67@shawnlinux:~ $

 ](*,)

---

### Post by darthsabbath on 2005-04-18
Something interesting... my wireless was working fine until I did a clean installation of Hoary.  I'd originally started with the Release Candidate, and once I changed the RadioState, everything was gravy.  

However, I formatted and reinstalled to the "official" release, and now I'm getting the same "Error inserting ndiswrapper" issue that you guys are getting.  Were there any  changes between the Release Candidates and the Official release that could've caused this? 

Gonna play with it some tomorrow and see what I can figure out...

Serves me right for doing a format and reinstall. :-P

Phil

---

### Post by jonny on 2005-04-18
[QUOTE=darthsabbath]Something interesting... my wireless was working fine until I did a clean installation of Hoary.  I'd originally started with the Release Candidate, and once I changed the RadioState, everything was gravy.[/QUOTE]Phil, you might be on to something here.  My how-to was based on the release candidate too.

Good luck!

---

### Post by sparke67 on 2005-04-18
[QUOTE=jonny]Phil, you might be on to something here.  My how-to was based on the release candidate too.

Good luck![/QUOTE]
could that be the reason for this ?

ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper (wrapper_init:2286): loadndiswrapper failed (1536);check utils version mismatch
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ndiswrapper (wrapper_init:2286): loadndiswrapper failed (1536);check utils version mismatch
sparke67@shawnlinux:~ $

---

### Post by allen on 2005-04-18
hopefully you work something out phil,

i'm having the exact same problems as the others.

mine is a BT Voyager 1040 pci card and following the instructions gives the same errors as you described.

---

### Post by Seth on 2005-04-18
Phil, the version of utils in the repo's is something like .12. Looks like you're trying to use .10 of ndiswrapper. Grab ndiswrapper-source and ndiswrapper-utils out of the repo's and build your own set?

---

### Post by allen on 2005-04-18
heres a log of my problems

> root@allens:/home/allen # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
root@allens:/home/allen # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
root@allens:/home/allen # dmesg 

[*snip*]

ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper (wrapper_init:1494): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'


where would i find the system log ?

---

### Post by darthsabbath on 2005-04-18
Can't try any of this now, as I'm at work, but wanted to add that the ndiswrapper-utils I installed off the Hoary CD are version 0.11.  When I get home, I'll hook it up to my LAN and download the latest versions of both the kernel and ndiswrapper.

Phil

---

### Post by sparke67 on 2005-04-18
Oh God !!! The nightmare is over.

All I did was remove NDISWRAPPER via synaptic. 
Reboot and re add it again !!
I re ran modprobe and BOOM the lights show up at 100 % signal strength !!
All is re ran dmesg and it shows there also.

I did notice that after re installing ndiswrapper via synaotic I got different prompt about the the drivers not being supported by Ubuntu !!!

Thanks everyone who got me thinking along the right path -- \\:D/
WARNING:
This tool allows you to use a driver written for the Windows operating
system on Ubuntu. Please note that the use of such drivers is entirely
unsupportable by the Ubuntu team, and not recommended, even if it is
theoretically possible with this tool.

bcmwl5 is already installed. Use -e to remove it

sparke67@shawnlinux:~ $ sudo modprobe ndiswrapper

sparke67@shawnlinux:~ $ dmesg
Linux version 2.6.8.1-5-386 (buildd@rothera) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Thu Apr 7 08:47:11 UTC 2005

CPU: AMD Mobile AMD Athlon(tm) XP 2400+ stepping 00
Enabling fast FPU save and restore... done.

blah blah blah .......

wlan0: ndiswrapper ethernet device 00:90:96:70:d3:68 using driver bcmwl5.sys
ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
ndiswrapper: driver bcmwl5.sys (Broadcom,06/13/2003, 3.20.23.0) added
sparke67@shawnlinux:~ $

---

### Post by jonny on 2005-04-18
If I understand events properly, I should update the how-to to add the following steps right at the start:

 - remove any previous attempts at using ndiswrapper (remove the .inf file, remove the module and remove any residual files lurking around
 - remove any existing versions of ndiswrapper
 - remove the CD from the sources list

...and then continue as previously documented.  Does that sound right, sparke67?  Does it work for everyone else?  If so, I'll put it into noob friendly language and update accordingly.

---

### Post by sparke67 on 2005-04-18
yes that is what I did. I try to complile myself because I did not even know what synaptic was when I downloaded NDISWrapper the first time and tried to compile it.

I deleted all references to it I had downloaded. Removed and re added via Synaptic. Rebooted and was good to go ---  unfortunatly I am next to unsecured wireless connection and can not use the network tool to add it - or maybe I can but don't know who to enter the info here but neverless I have rebooted 4 times and it works each time ..

I hope this will help someone else //// :)


****** one thing I forgot, at each reboot I do have to run ---sudo modprobe ndiswrapper --- for the card to activate but this is small and I am sure I could play with it to go at start but for now I am happy --- :wink:  ;-)

---

### Post by darthsabbath on 2005-04-19
Hrm.  When I got home, I tried the above steps (removing Ndiswrapper and all associated files), then reinstalled from the repo... same problem. :/ One question: when you removed Ndiswrapper, what else did you take out?  

I removed:
ndiswrapper-utils
/etc/ndiswrapper/
/etc/modprobe.d/ndiswrapper

Anything else?

I also tried installing the latest 686 kernel, same problem.

I guess I can always go back to the release candidate and just upgrade, but damnit, I wanna know the problem. ;-)

Phil

---

### Post by jonny on 2005-04-19
I don't know if this has affected you, but have you copied the file bcmwl5.sys to your desktop along with bcmwl5.inf.  I've just realised that I missed this out of the how-to (it's about to be corrected).

If my faulty instructions are to blame, then I'm terribly sorry to have caused you so much hassle...

---

### Post by dcraven on 2005-04-19
Just in case anyone needs/wants to compile the newerver ndiswrapper v1.1, there are instructions on the wiki [here](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto).

HTH,
~djc

---

### Post by darthsabbath on 2005-04-19
Interestingly enough, I did a clean install of the Hoary Preview Release, and I experienced the same problem, so I remembered something from when I first installed Hoary... I'd turned off my wireless card, and it took me forever to figure out why it wasn't finding my wireless access point.

So I turned off my wireless, installed ndiswrapper, ran modprobe... BOOM!  Turned on wireless, it works!

Amazing the little quirks of Linux, eh? ;-) Still, I'm happy I got it working! Thanks ot all!

Phil

---

### Post by jonny on 2005-04-20
[QUOTE=darthsabbath]Interestingly enough, I did a clean install of the Hoary Preview Release, and I experienced the same problem, so I remembered something from when I first installed Hoary... I'd turned off my wireless card, and it took me forever to figure out why it wasn't finding my wireless access point.

So I turned off my wireless, installed ndiswrapper, ran modprobe... BOOM!  Turned on wireless, it works!

Amazing the little quirks of Linux, eh? ;-) Still, I'm happy I got it working! Thanks ot all!

Phil[/QUOTE]That's something else that I found out the hard way.  My laptop has an unmarked Fn+F2 key combination that toggles wireless activity.  In Linux, it only switches the wireless off, and the only way that I've found to re-enable power is to boot into Windows and press Fn+F2 again.

I've added a note to the How-to to this effect.

---

### Post by slipp3dstr3am on 2005-04-20
yes I have done it.... it only took me 2 weeks of reading and trying to figure out what i was doing wrong but i did it and now i'm wire free....

thanks to every one that has posted in here ... you have no idea how much this n00b feels right now ...  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/

---

### Post by slipp3dstr3am on 2005-04-25
> **jonny]Broadcom wireless cards are tricky to set up in ubuntu, and the forums are full of frustrated users seeking advice.  Broadcom provide no Linux support (feel free to complain to your hardware vendor or choose a different card if you haven't yet shelled out your cash), but they can be made to work - and you're in the right place if you want to know how.

First, you need to find out if this How To is for you.  Broadcom wireless cards come under many brand names and, in particular, are used in many Dell and Acer laptops.  Look for the drivers supplied with your card (Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON) said:**
> How to add extra repositories[/URL]

3. Open a terminal session and enter this code.  Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```4. Reboot your PC.  On restarting, the light on your wireless card should come on.  If not, try entering```
sudo modprobe ndiswrapper
```5. Your card is now working.  Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings.  Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one.  You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK.  The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK.  Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana.  If everything works, you can delete the file from your desktop.

13.  You might notice that the signal strength applet doesn't work properly.  This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled.  Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.

[COLOR=Indigo](Note: This how-to has been updated to reflect all comments from the thread up to 19 April)[/COLOR]





is there any way to get this pinned?
i would hate for some one to miss this

---

### Post by jardasarp on 2005-04-27
jonny, you are a god among men  :smile: 

I tried installing this on a Kubuntu 5.04 stable release and it worked fine with a Linksys WPC54G.

It should be noted that any supplementary wifi apps should be installed BEFORE doing this, as programs like wpa_supplicant seem to fuk up the settings on the card (could scan before installing other wifi apps, but not afterward).

---

### Post by Staesys on 2005-04-28
I've followed your steps closely for my Motorola WN825G PCMCIA wireless card and I can now get the power light to come on, but there is no communication through it at all. Here's some info:

[B]root@ubuntu:/home/paul # iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:C0AD-9DDC-5AFD-BC8B-AA46-CAE5-98   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9253   Missed beacon:0

root@ubuntu:/home/paul # dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:e5:52:a9:89
Sending on   LPF/wlan0/00:0c:e5:52:a9:89
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B] 

It can however scan for access points:

[B]root@ubuntu:/home/paul # iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:51:D2:2A
                    ESSID:"@home"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-70 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:50:0F:0F:EB
                    ESSID:"barry"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-88 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:09:5B:4E:D9:DA
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-86 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0[/B] 

Any ideas?

-Paul

---

### Post by kmyram on 2005-04-28
> ESSID:"@home"
ESSID:"barry"
ESSID:"NETGEAR"

So, these are the AP's you can see - which is yours? If it's "@home" then try:

$ iwconfig wlan0 essid @home
$ iwconfig wlan0 key C0AD-9DDC-5AFD-BC8B-AA46-CAE5-98
$ dhclient wlan0

Should work (if the key is right too :))

---

### Post by Staesys on 2005-04-28
[B]root@ubuntu:/home/paul # iwconfig wlan0 essid @home
root@ubuntu:/home/paul # iwconfig wlan0 key C0AD9DDC5AFDBC8BAA46CAE598
root@ubuntu:/home/paul # dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:e5:52:a9:89
Sending on   LPF/wlan0/00:0c:e5:52:a9:89
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B] 

Yeah, @home's mine...

I also tried it with the "-"'s in the key and it didn't make any difference.

I'm guessing it's either not transmitting or not recieving...perhaps both...  I know this card works, and I know the AP works, it's just getting this card working in Linux that's the rub...

Thanks, btw, I appreciate the help!

-Paul

---

### Post by jonny on 2005-04-28
Personally, I failed to configure my card using iwconfig, ifconfig, and dhclient - that's why I recommended using the Gnome tools - so I'm not the best person to advise you.  Your card is certainly receiving signals, but it's unclear to me why your DHCP request isn't being honoured.

You could try first removing WEP from the network.  That would eliminate a potential failure point.

Another approach that you might want to try is to use the Debian command line tools for networking.  That involves putting some entries into /etc/network and using ifup and ifdown to start and stop the network.  This works perfectly for me.

man interfaces and man ifup will give you the information you need.

---

### Post by Staesys on 2005-04-29
Know what?

I removed WEP and the card connected, in fact, I'm using it right now. I don't like to running an open WAP though, any ideas on how I can get WEP to work?

-Paul

---

### Post by jonny on 2005-04-29
Presumably you've tried the gnome tool described in the how-to?  And, if you entered your WEP key as a 5 or 13 character string, you put s: in front of it?  And you're sure the '@' symbol in your network name's not causing trouble?

If so, try editing /etc/network/interfaces directly.  Replace the existing stanza (if any) that refers to your card with this:```
iface wlan0 inet dhcp
wireless-essid @home
wireless-key s:paulz
```Set the WEP key on your router to 'paulz', and try ```
sudo ifup wlan0
```

---

### Post by Staesys on 2005-05-01
No go. Everytime I try to enable WEP the card and the wap stop talking. I'm really not sure what to do at this point.

My notebook has an internal card (802.11b), but it sucks and the one I'm using now supports 802.11g. Thing is, I had the same trouble with that one too. Currently, it's disabled and turned off so the only card I'm using is the Broadcom based (Motorola) card.

I tried it at two seperate coffe shops today and was able to connect to their wap's, although they were not running WEP.

I'm beginning to think there's something screwy in my setup or something...

-Paul  :-?

---

### Post by spd106 on 2005-05-01
Hi, you could try setting the key mode to open instead of the default restricted, maybe also specify the channel your AP is using. Though that shouldn't be necessary.

 ```
iwconfig wlan0 key open XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX
```

---

### Post by Staesys on 2005-05-02
Thanks everyone for their help. I finally fixed it... I went out and got a Belkin F5D7230-4 Wireless-G router to replace my Linksys WAP11. I set it up with 128 bit WEP encryption and entered the WEP key into System -> Administration -> Networking.

Guess what...?

The damn thing works now.

I guess my WAP11 wasn't allowing my card to connect with 128 bit WEP set up. Funny thing, it's the same card that connected just fine when I had Windows XP on this laptop. Oh well, I've got a better Router/AP now anyway.

:-)

-Paul

---

### Post by chroland on 2005-05-02
[QUOTE=Staesys][B]root@ubuntu:/home/paul # iwconfig wlan0 essid @home
root@ubuntu:/home/paul # iwconfig wlan0 key C0AD9DDC5AFDBC8BAA46CAE598
root@ubuntu:/home/paul # dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:e5:52:a9:89
Sending on   LPF/wlan0/00:0c:e5:52:a9:89
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B] 

Yeah, @home's mine...

I also tried it with the "-"'s in the key and it didn't make any difference.

I'm guessing it's either not transmitting or not recieving...perhaps both...  I know this card works, and I know the AP works, it's just getting this card working in Linux that's the rub...

Thanks, btw, I appreciate the help!

-Paul[/QUOTE]
 hi! i ve excatly the same problem with an hp compaq nx9105 laptop with an integrated broadcom wirelless card.
 I can now get the power light to come on, but there is no communication through it at all. when i switch to windows there is no problem an ican connect to the internet with my usrobotics wireless router

can you help me

---

### Post by Staesys on 2005-05-02
Have you tried running your router and card without wep? That was the only way I could get it to work on my Linksys WAP11. I just changed to a Belkin wireless router and was able to get it to work with 128 bit WEP encryption right off the bat.

what does a:

```
iwconfig
``` 
show?

Also...

```
iwlist scanning
``` 
Will show if you can see the access points around you.

```
ifconfig
``` 
Will show the wireless access card(s) configuration info.

Get me this info so I can see what's going on...

-Paul

---

### Post by Kbel on 2005-05-03
i am also having a problem with an HP laptop broadcom wlan
it simply does not pick up any networks with iwlist

---

### Post by Hieronymus on 2005-05-03
[QUOTE=Kbel]i am also having a problem with an HP laptop broadcom wlan
it simply does not pick up any networks with iwlist[/QUOTE]

I have had the same problem with my HP laptop broadcom wlan, the solution was to uninstall ndiswrapper version 1.1 and to install ndiswrapper version 1.2. You can download this here [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772) 

just unpack, make and make install after you have removed the old version. 

Good luck

---

### Post by Kbel on 2005-05-04
[QUOTE=Hieronymus]I have had the same problem with my HP laptop broadcom wlan, the solution was to uninstall ndiswrapper version 1.1 and to install ndiswrapper version 1.2. You can download this here [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772) 

just unpack, make and make install after you have removed the old version. 

Good luck[/QUOTE]

It worked thank you very much \\:D/

---

### Post by omegasoul on 2005-05-04
[QUOTE=Hieronymus]I have had the same problem with my HP laptop broadcom wlan, the solution was to uninstall ndiswrapper version 1.1 and to install ndiswrapper version 1.2. You can download this here [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772) 

just unpack, make and make install after you have removed the old version. 

Good luck[/QUOTE]
 Can you please tell me how to uninstall the old ndiswrapper and install the new without screwing up. I seem to be a complete idiot? Thanks in advance.

---

### Post by Hieronymus on 2005-05-04
[QUOTE=omegasoul]Can you please tell me how to uninstall the old ndiswrapper and install the new without screwing up. I seem to be a complete idiot? Thanks in advance.[/QUOTE]
  
Well, as follows:

 ```

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install linux-headers-2.6.10 (whatever version)
cd /usr/src/
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /usr/src/ndiswrapper-1.2-rc1/
sudo make
sudo make install
cd /the dir where your windows networkdrivers are/
sudo ndiswrapper -i bcmwl5 (or other driver name if you have another card)
sudo ndiswrapper -l (making sure the driver is installed)
sudo modprobe ndiswrapper
sudo dmesg (you sould see that the card is installed)
sudo iwlist wlan0 scan (to get a list of APs)
sudo ndiswrapper -m (ndiswrapper will now be loaded automatic at bootup)

```

now everything works you can goto network settings in administration. Here you can tell Ubuntu to get a dynamic ip (dhcp) and (if you need it) the wep encryption key. Then activate et voilà.

Good luck, Hieronymus

---

### Post by mike998 on 2005-05-04
Thank you Thank you Thank you.
This how-to FINALLY got my wireless up and running!

---

### Post by KrIaXPaTaLa on 2005-05-04
I'm on an acer travelmate 4002 wlmi, followed this howto and wireless works now. Hoary final. Tnkz everyone.

[QUOTE=jonny]
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
[/QUOTE]

In my case, this wasn't necessary. Don't ask me why. In the .conf files I had, there was no "RadioState|1". Just "StateName|" and "RadioEnable|0x1". Didn't changed anything.

Further more, I used this xp driver: 
[ftp://ftp.support.acer-euro.com/notebook/TravelMate_4000_4500/driver/80211bg.zip](ftp://ftp.support.acer-euro.com/notebook/TravelMate_4000_4500/driver/80211bg.zip)

Best regards,

Kriax, Portugal

---

### Post by omegasoul on 2005-05-04
[QUOTE=Hieronymus]Well, as follows:

 ```

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install linux-headers-2.6.10 (whatever version)
cd /usr/src/
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /usr/src/ndiswrapper-1.2-rc1/
sudo make
sudo make install
cd /the dir where your windows networkdrivers are/
sudo ndiswrapper -i bcmwl5 (or other driver name if you have another card)
sudo ndiswrapper -l (making sure the driver is installed)
sudo modprobe ndiswrapper
sudo dmesg (you sould see that the card is installed)
sudo iwlist wlan0 scan (to get a list of APs)
sudo ndiswrapper -m (ndiswrapper will now be loaded automatic at bootup)

```

now everything works you can goto network settings in administration. Here you can tell Ubuntu to get a dynamic ip (dhcp) and (if you need it) the wep encryption key. Then activate et voilà.

Good luck, Hieronymus[/QUOTE]


Thanks for your help but I still am wirelessless. When I used the method described by the original poster my light would not even come on. So i followed the instructions here: [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

I just replaced ndiswrapper1.1 with ndiswrapper1.2rc1. As a result the pretty little blue light came on but I can not ](*,)  connect to the net. I have been working on this for 3 days. Thanks again but I think I have no choice but to go back to the "Darkside" aka Microsoft.

---

### Post by Hieronymus on 2005-05-05
There are two things that I think could be wrong:


If you are using 64 bit Ubuntu you need 64 bit drivers, for my broadcom (the version that works with the bcmwl5 drivers) you can download it here: 
[http://ubuntuforums.org/attachment.php?attachmentid=186](http://ubuntuforums.org/attachment.php?attachmentid=186)

If you are just using 32 bit ubuntu, are you sure dhcp is running for your wlan card?

dhcp: system >> administration >> networking

then click on the wireless connection, this should be there if de wlan driver is correctly installed, to check this check the output of the following commands:

```

ndiswrapper -l (shows if the driver is installed correctly)
dmesg (shows if the hardware is recognised correctly)
iwconfig (shows all NICs and tells if they have a wireless extention)

```

next click on properties and check the radiobutton of "this device is configured" next click on the scroll down menu and choose your essid (access point) then enter (if you have one) your WEP encryption key and click on the configuration scrolldown menu and choose DHCP. Click ok and then on Activate. To test type the following command in a terminal:

```

ping -c 3 ubuntuforums.org

```

If this doesn't work, or your stuck earlier in this "how to" please post the output of:

```

ndiswrapper -l
dmesg
iwconfig

```

Good luck!

---

### Post by omegasoul on 2005-05-05
Here is the print out from from the commands you mentioned earlier. I hope there is something usefull in them. Also I have an **AMD64** processor but I am using the **32 bit version of Ubuntu** on a Compaq 3000 with internal wireless. Thanks again for helping me.

[COLOR=Red]strong@omega:~$ ndiswrapper -l[/COLOR]
Installed ndis drivers: 
bcmwl5 in driver present, hardware present

[COLOR=Red]This is only part of the output from dmesg[/COLOR]. 
NET: Registered protocol family 17
ndiswrapper version 1.2rc1 loaded (preempt=yes,smp=no)
ndiswrapper: driver bcmwl5 (Broadcom,10/20/2004, 3.70.22.0) loaded
ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 17
ndiswrapper: using irq 17
wlan0: ndiswrapper ethernet device 00:90:4b:b7:e9:b1 using driver bcmwl5, configuration file 14E4:4320:103C:12F8.5.conf
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ACPI: AC Adapter [ACAD] (off-line)
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x200-0x20f 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x2 (1500 mV)
powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x12 (1100 mV)
cpu_init done, current fid 0x8, vid 0x6
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
wlan0: no IPv6 routers present
eth0: no IPv6 routers present
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root

[COLOR=Red]strong@omega:~$ iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2152800   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Hieronymus on 2005-05-05
Ok, next you have to find your accespoint.

```

sudo iwlist wlan0 scan

```

This gives all accesspoint surrounding you, at least there should be your own accesspoint. When you know the name of the accesspoint you want to use (of course you have given this name to the accesspoint yourself :) ) tell the Wlan adapter to connect to it:

```

sudo iwconfig wlan0 essid accesspoint_name

```

If you are using WEP encryption make sure that your Wlan adapter knows it:

```

sudo iwconfig wlan0 enc key 

```

Now you should be connected, see if that is true:

```

sudo iwconfig

```

For your system the output should be something like:

```

[color=Red]strong@omega:~$ sudo iwconfig[/color]
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
 but has been compiled with version 17, therefore some driver features
 may not be available...
 
 wlan0     IEEE 802.11g  ESSID: **the_name_of_your_AP**
           Mode:Managed  Frequency:2.462 GHz  Access Point: **00:00:00:00:00:00 (for 00 read a number, this is the MAC adress of your AP)**
           Bit Rate:54 Mb/s   Tx-Power:25 dBm
           RTS thr:2347 B   Fragment thr:2346 B
           Power Management:  off
           Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:2152800   Missed beacon:0

```

If this is correct you are connected to the AP, now let's connect to the internet:

```

 sudo dhclient wlan0 (assigns a dynamic IP adress to the Wlan adapter)

```

and test the connection:

```

 sudo ping -c 3 [ubuntuforums.org]("http://www.ubuntu-linux.nl/")

```

Et voilà, you are connected. 

Tell me if it worked out, grz Hieronymus

---

### Post by eudemon on 2005-05-05
:) Thanks, great howto!  Worked perfectly.

---

### Post by omegasoul on 2005-05-05
My AP was detected but here is my system output

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2350866   Missed beacon:0

I know my AP was detected because I verified the MAC address on the router.
 :-| 
I copied and pasted the commands into my terminal so I dont think I put the wrong commands in. Do I need to add in the " " around the name of the AP or reset it?

---

### Post by Hieronymus on 2005-05-05
Ok, here is the output I get when I do all the steps, maybe it helps.

```

**root@home:/home/dusty # iwlist wlan0 scan**
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0	 Scan completed :
		  Cell 01 - Address: 00:90:96:CF:3B:60
				    ESSID:"Homenet"
				    Protocol:IEEE 802.11b
					Mode:Managed
				 Frequency:2.452 GHz (Channel 9)
				 Quality:0/100 Signal level:-54 dBm Noise level:-256 dBm
				    Encryption key:on
				    Bit Rate:1 Mb/s
				    Bit Rate:2 Mb/s
				    Bit Rate:5.5 Mb/s
				    Bit Rate:11 Mb/s
				    Extra:bcn_int=100
					Extra:atim=0

[b]root@home:/home/dusty # iwconfig wlan0 essid Homenet
root@home:/home/dusty # iwconfig[/b]
lo		no wireless extensions.

eth0	  no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0	 IEEE 802.11b  ESSID:"Homenet"
		  Mode:Managed  Frequency:2.452 GHz  Access Point: 00:90:96:CF:3B:60
		  Bit Rate=11 Mb/s   Tx-Power:25 dBm
		  RTS thr=2347 B   Fragment thr=2346 B
		  Encryption key:xxxx-xxxx-x   Security mode:restricted
		  Power Management:off
		  Link Quality:100/100  Signal level:-51 dBm  Noise level:-256 dBm
		  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
		  Tx excessive retries:6  Invalid misc:75   Missed beacon:0

sit0	  no wireless extensions.
[b]
root@home:/home/dusty # iwconfig wlan0 enc xxxxxxxxxx (here was my key, but I would like to keep it private ;) )
root@home:/home/dusty # iwconfig[/b]
lo		no wireless extensions.

eth0	  no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0	 IEEE 802.11b  ESSID:"Homenet"
		  Mode:Managed  Frequency:2.452 GHz  Access Point: 00:90:96:CF:3B:60
		  Bit Rate=11 Mb/s   Tx-Power:25 dBm
		  RTS thr=2347 B   Fragment thr=2346 B
		  Encryption key:xxxx-xxxx-x   Security mode:restricted
		  Power Management:off
		  Link Quality:100/100  Signal level:-54 dBm  Noise level:-256 dBm
		  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
		  Tx excessive retries:6  Invalid misc:75   Missed beacon:0

sit0	  no wireless extensions.

**root@home:/home/dusty # dhclient3 wlan0**
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:57:c4:e4
Sending on   LPF/wlan0/00:90:4b:57:c4:e4
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.138
bound to 10.0.0.171 -- renewal in 3284 seconds.
[b]
root@home:/home/dusty # ping -c 3 ubuntuforums.org[/b]
PING ubuntuforums.org (64.21.33.9) 56(84) bytes of data.
64 bytes from 64.21.33.9: icmp_seq=1 ttl=56 time=103 ms
64 bytes from 64.21.33.9: icmp_seq=2 ttl=56 time=103 ms
64 bytes from 64.21.33.9: icmp_seq=3 ttl=56 time=104 ms

--- ubuntuforums.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 103.036/103.432/104.107/0.546 ms

```

Does this output look like the output you get?

---

### Post by omegasoul on 2005-05-05
This is my output so far.

wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:71:AB:A6
                    ESSID:"Home"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-12 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@omega:~# iwconfig wlan0 essid Home
root@omega:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B

          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2750134   Missed beacon:0

sit0      no wireless extensions.

root@omega:~#

---

### Post by Hieronymus on 2005-05-05
I think the problem is reception, look at your output:

```

wlan0     Scan completed :
           Cell 01 - Address: 00:09:5B:71:AB:A6
                     ESSID:"Home"
                     Protocol:IEEE 802.11b
                     Mode:Managed
                     Frequency:2.462 GHz (Channel 11)
**                     Quality:0/100  **Signal level:-12 dBm  Noise level:-256 dBm
                     Encryption key: off
                     Bit Rate:1 Mb/s
                     Bit Rate:2 Mb/s
                     Bit Rate:5.5 Mb/s
                     Bit Rate:11 Mb/s
                     Extra:bcn_int=100
                     Extra:atim=0

```

can you get closer to the AP or something and try again?

---

### Post by omegasoul on 2005-05-05
I am sitting next to it  :)

---

### Post by Hieronymus on 2005-05-05
[QUOTE=omegasoul]I am sitting next to it  :)[/QUOTE]

...:-) Well, thats strange. 

But, we won't give up!

I notice that your AP is of version 802.11b which has a max bitrate of 11 Mbit/s. However, your Wlan adapter is of version 802.11g which has a max bitrate of 54 Mbit/s. I don't know if this can give problems, but we can at least try to change this.

```

iwconfig wlan0 rate 11M

```

or 

```

iwconfig wlan0 rate auto

```

I see the frequencies match, but to be sure try this too

```

iwconfig wlan0 channel 11

```

You can get info on the options of iwconfig by doing
```

iwconfig --help

```

and very good info on iwconfig by doing
```

man iwconfig

```

I'm curious if any of this works!

btw I had deleted my WEP key in the command, but not in the iwconfig output.....](*,) :-P

---

### Post by omegasoul on 2005-05-05
I looked at you output again and your quality was 0 until you changd the essid.
Then I looked at my output I saw that the quality was 100/100 after I tried to add the essid. I am getting a signal so it has to be something else  ](*,) . 

If your ready to give up on my crappy machine I will understand :-?

---

### Post by omegasoul on 2005-05-05
I tried it and my system rejected it my friend, the output is still the same.

---

### Post by Hieronymus on 2005-05-05
[QUOTE=omegasoul]I looked at you output again and your quality was 0 until you changd the essid.
Then I looked at my output I saw that the quality was 100/100 after I tried to add the essid. I am getting a signal so it has to be something else ](*,) . 

If your ready to give up on my crappy machine I will understand :-?[/QUOTE]

I'll keep on thinking on this one, I'm not a pro so maybe some things I think of won't be logical. Anyway, two minds can think of more than one (I guess).

Are you sure that your accesspoint is configured correctly? What I mean is if your AP allows every computer to connect or only computers with a certain name? 

Try working with the graphical interface: goto System >> Administration >> Networking, choose your wlan adapter >> properties and see if you can chose your essid. Next chose dhcp for configuration, close and activate. Does this work?

---

### Post by omegasoul on 2005-05-05
I forgot to mention that my none of my .conf files have the line RadioState|1 or RadioState|0 in them. I hope that is not important.

---

### Post by omegasoul on 2005-05-05
[QUOTE=Hieronymus]I'll keep on thinking on this one, I'm not a pro so maybe some things I think of won't be logical. Anyway, two minds can think of more than one (I guess).

Are you sure that your accesspoint is configured correctly? What I mean is if your AP allows every computer to connect or only computers with a certain name? 

Try working with the graphical interface: goto System >> Administration >> Networking, choose your wlan adapter >> properties and see if you can chose your essid. Next chose dhcp for configuration, close and activate. Does this work?[/QUOTE]


I have checked the network properties so many times I could draw you a picture of the layout. Do you think that I should start over using the original posters instructions. As I mentioned earlier I could not get them to work so I just used the HowToSetupNdiswrapper instructions.

[QUOTE=Hieronymus]
Are you sure that your accesspoint is configured correctly? What I mean is if your AP allows every computer to connect or only computers with a certain name?[/QUOTE]

I am sure that my network is completely open and unsecure :-)

---

### Post by Hieronymus on 2005-05-05
[QUOTE=omegasoul]I forgot to mention that my none of my .conf files have the line RadioState|1 or RadioState|0 in them. I hope that is not important.[/QUOTE]

I have to say I don't know, I have seen that other people on this thread have remarked something about this. Try to follow their instructions before you reset anything. 

Btw I have written a howto to install ndiswrapper so if you need it again it is easier to follow that all loose instructions [http://ubuntuforums.org/showthread.php?t=31926]("http://ubuntuforums.org/showthread.php?t=31926")

I will keep on thinking on this, but for now I'm out of options. If you got it working in the mean time please let me know. 

Greetings

---

### Post by Hieronymus on 2005-05-05
I just thought of something, probebly won't be the solution but you'll never know.

When I have both Wlan adapter and normal NIC adapter activated this gives problems with connecting to the net. It might also give other problems I haven't noticed. So if your also have your normal NIC activated try to deactivate and test again. 

grz

---

### Post by omegasoul on 2005-05-05
I had a break through. I double checked my properties in my router. Even though I turned off the MAC verification feature it would only let me on if I added the MAC for this computer. So now Here is my new out put:

root@omega:~# sudo iwlist wlan0 scan
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:71:AB:A6
                    ESSID:"Home"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-41 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@omega:~# sudo iwconfig wlan0 essid Home
root@omega:~# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:"Home"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:71:AB:A6
          Bit Rate:11 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-53 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3971117   Missed beacon:0

sit0      no wireless extensions.

root@omega:~# sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:b7:e9:b1
Sending on   LPF/wlan0/00:90:4b:b7:e9:b1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I hope you can help me from here.

---

### Post by Hieronymus on 2005-05-05
Well, at least you are connected. :-p

```

root@home:/ # dhclient3 wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:57:c4:e4
Sending on   LPF/wlan0/00:90:4b:57:c4:e4
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.138
bound to 10.0.0.171 -- renewal in 3478 seconds.
root@home:/ #

```

Ok, I have tested something. This is because you have also a dhcp lease on eth0. the solution:

```

dhclient -r
dhclient wlan0

```

Worked?

---

### Post by omegasoul on 2005-05-05
No, that is not working either. But it was a good idea.

---

### Post by Hieronymus on 2005-05-05
[QUOTE=omegasoul]No, that is not working either. But it was a good idea.[/QUOTE]
 Oh, that's ashame. Did you already try to configure your wlan card with system >> administration >> networking? And did you try a reboot?

(I guess these are my noob solutions :-) )

---

### Post by Hieronymus on 2005-05-05
[QUOTE=Hieronymus]Oh, that's ashame. Did you already try to configure your wlan card with system >> administration >> networking? And did you try a reboot?

(I guess these are my noob solutions :-) )[/QUOTE]
 btw if you add a network monitor the the gnome panel and set the conection name to wlan0 you can see if the connection itself is up or down. could be usefull

---

### Post by omegasoul on 2005-05-05
I am going to reboot to see if it helps. Yeah I know, I am grasping at straws.

---

### Post by omegasoul on 2005-05-05
My friend i would go in to battle with you anytime. I am free.

Thank you for all of your help \\:D/

---

### Post by Hieronymus on 2005-05-05
[QUOTE=omegasoul]My friend i would go in to battle with you anytime. I am free.

Thank you for all of your help \\:D/[/QUOTE]
 You're welcome, maybe you'll be able to help me out sometime :-)

---

### Post by dhanjel on 2005-05-06
It would be nice if all of you that got the broadcom chipset working wrote down your wifi-card name in this thread so you get this thread as a search result when searching for cards that works in the forums.

---

### Post by Hieronymus on 2005-05-06
[QUOTE=dhanjel]It would be nice if all of you that got the broadcom chipset working wrote down your wifi-card name in this thread so you get this thread as a search result when searching for cards that works in the forums.[/QUOTE]

Well, you're right, but I guess my info doesn't do much good. I have a broadcom 802.11b Wlan adapter integrated into my HP Pavilion zv5133ea laptop. The drivers that get my wlan adapter to work in 32 bit linux are the bcmwl5.inf drivers and in 64 bit linux netbc564.inf.

Besides this info all Broadcom cards will work with Ndiswrapper, are you having trouble with yours?

Hieronymus

---

### Post by dhanjel on 2005-05-06
[QUOTE=Hieronymus]Well, you're right, but I guess my info doesn't do much good. I have a broadcom 802.11b Wlan adapter integrated into my HP Pavilion zv5133ea laptop. The drivers that get my wlan adapter to work in 32 bit linux are the bcmwl5.inf drivers and in 64 bit linux netbc564.inf.

Besides this info all Broadcom cards will work with Ndiswrapper, are you having trouble with yours?

Hieronymus[/QUOTE]

Had a d-link g520+ and spent like 30 hours trying to get it to work before I figured out that it was broken, so I went to the store to get a new one, but they were all out on that card so I got a belkin card with broadcom chipset instead. Havn't had time to try it yet.

---

### Post by omegasoul on 2005-05-06
[QUOTE=Hieronymus]You're welcome, maybe you'll be able to help me out sometime :-)[/QUOTE]

Just let me know when. If I dont have an answer I will help you find it. :mrgreen:

---

### Post by Hieronymus on 2005-05-06
[QUOTE=omegasoul]Just let me know when. If I dont have an answer I will help you find it. :mrgreen:[/QUOTE]

Now you mention it, this [http://ubuntuforums.org/showthread.php?p=160846#post160846](http://ubuntuforums.org/showthread.php?p=160846#post160846) is my problem at the moment, I'm trying to install the cvs version of Xorg, but run into a lot of errors, so far I have solved them all, but we'll see how far I get.

---

### Post by Hieronymus on 2005-05-06
Ignore that last message, the problem is solved. 

Thx anyway!

---

### Post by dhanjel on 2005-05-06
Hi again guys, can't get this to work :/

Installed ndiswrapper and the drivers, activated the radio module in the conf file and everything, no error messages displayed in the message log but no networks are found when I scan and the leds on the network is not on.

Any suggestions?

The network card is a Belkin F5D7000yy.

---

### Post by Hieronymus on 2005-05-06
[QUOTE=dhanjel]Hi again guys, can't get this to work :/

Installed ndiswrapper and the drivers, activated the radio module in the conf file and everything, no error messages displayed in the message log but no networks are found when I scan and the leds on the network is not on.

Any suggestions?

The network card is a Belkin F5D7000yy.[/QUOTE]

Ok, that the LED is not on doen't have to mean anything, for my broadcom the LED only is on on data transfer. 
But to get things working please post the output of: 

```

iwconfig
dmesg
iwlist wlan0 scan

```

Are you sure there is a working network near you?
did you take all [ these ]("http://www.ubuntuforums.org/showthread.php?t=31926&highlight=howto%3A+wlan+ndiswrapper") steps?

Grz Hieronymus

---

### Post by dhanjel on 2005-05-06
Yeah, followed that guide. Here is some output.

Iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off


dmesg:
> 
ndiswrapper: using irq 19
wlan0: ndiswrapper ethernet device 00:11:50:06:91:0d using driver bcmwl5, configuration file 14E4:4320:1799:7000.5.conf
wlan0: encryption modes supported: WEP
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
drivers/usb/input/hid-input.c: event field not found
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
wlan0: no IPv6 routers present
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
NET: Registered protocol family 17
eth0: no IPv6 routers present
wlan0: no IPv6 routers present
wlan0: no IPv6 routers present


iwlist scan:
> 
iwlist wlan0 scan
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     No scan results


---

### Post by Hieronymus on 2005-05-06
[QUOTE=dhanjel]Yeah, followed that guide. Here is some output.

Iwconfig:


dmesg:


iwlist scan:[/QUOTE]
 The bcmwl5 driver is for Broadcom cards, so this could be the problem. What does

```

ndiswrapper -l

```

say?

---

### Post by dhanjel on 2005-05-06
[QUOTE=Hieronymus]The bcmwl5 driver is for Broadcom cards, so this could be the problem. What does

```

ndiswrapper -l

```

say?[/QUOTE]

Driver loaded, hardware loaded.

The belkin card has the broadcom chipset. The drivers are from the cd that came with the card.

---

### Post by andyk on 2005-05-06
well i've been away for awhile (trying my hand at slackware)  it was fun, but nothing gets recognized from my system.  spent more time configuring, than enjoying it.  so i came back to ubuntu.  and ndiswrapper install is a snap.  for my compaq laptop with b'com 94306 chipset heres my easy install. (BTW: i'm using hoary R/C)

grab driver's (inf and sys) from wherever (XP cd, Compaq Website) and put them whereever.

pop in hoary cd and go to package mgr, search ndiswrapper-utils, install it.

open command line and cd to wherever you put drivers.

**$ndiswrapper -i "your driver".inf**

**$ndiswrapper -l** (if all went well it should tell you what drivers and hardware is present)

if it's all kosher type: **$ ndiswrapper -m**

then type: **$ sudo modprobe ndiswrapper**

next step key: **$sudo gedit /etc/ndiswrapper/bcmwl5/"your conf".conf** (for me it's 14E4:4320.conf) and change radio state to "0" and save.

next: **$sudo gedit /etc/modules** and add ndiswrapper to the list and save.

open networking and click on wireless then on right side click properties, new window click radio box "this device is configured" and enter your settings.  click OK then at main window click activate.  Turn other interfaces off (eth0 etc) and exit.  reboot and you should be in business.

---

### Post by dhanjel on 2005-05-07
andyk: tried that with no luck. It just can't find the AP for some reason. Don't know how to solve this :/

---

### Post by Chromance on 2005-05-10
I did the steps above , isnt the Bcml5.inf supposed to be copied into the etc/ndiswrapper/bcml5 folder? I checked the folder and its not in there.
I even moved the drivers  into the bcml5 folder and im still getting an
invalid driver! I know this is the right driver I had this wireless up and
running a few months ago .  What am I doing wrong here

---

### Post by Zelut on 2005-05-10
Ok, I'm giving up & posting my info dump here.  Hopefully someone can tell me what I'm missing.  

HARDWARE:
emachines M5312 notebook - broadcom chipset 54g (bcmwl5 driver)

ndiswrapper -l:

> Installed ndis drivers:
bcmwl5 driver present, hardware present


iwconfig:
> 
wlan 0     IEEE 802.11g ESSID:off/any (should be havana!)
     Mode: Managed     Frequency: 2.462 GHz     Access Point: 00:00:00:00:00:00
     Bit Rate: 54 Mb/s     Tx-Power: 25 dBm
     RTS thr:2347 B     Fragment thr: 2346 B
     Encryption key: off
     Power management:off
     Link Quality:100/100     Signal level:-10 dBm     Noise level: -256 dBm
     Rx invalid nwid:0     Rx invalid crypt: 0     Rx invalid frag:0
     Tx excessive retries: 0     Invalid misc: 0     Missed beacon:0


dmesg:
> 
ndiswrapper: using irq 10
wlan0: ndiswrapper ethernet device 00:90:96:66:73:0c using driver bcmwl5
wlan0: encryption modes supported: WEP
ndiswrapper: driver bcmwl5 (Broadcom,10/28/2003, 3.40.25.3) added
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
... (battery info) ...
wlan0: no IPv6 routers present
eth0: no IPv6 routers present
wlan: 0.8.4.5 (EXPERIMENTAL)
ndiswrapper: device wlan0 removed
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 10 (level, low) -> IRQ 10
ndiswrapper: using irq 10
wlan0: ndiswrapper ethernet device 00:90:96:66:73:0c using driver bcmwl5
wlan0: encryption modes supported: WEP
ndiswrapper: driver bcmwl5 (Broadcom,10/28/2003, 3.40.25.3) added
wlan0: no IPv6 routers present


iwlist scan:
> 
wlan0     No scan results


I'm setup using a Linksys 54g wireless router.  I've got 3 boxes wired & the wireless notebook.  I've turned off WEP & MAC filtering.  

Any ideas on what I'm missing I'd greatly appreciate.

---

### Post by jonny on 2005-05-11
[QUOTE=Chromance]I did the steps above , isnt the Bcml5.inf supposed to be copied into the etc/ndiswrapper/bcml5 folder? I checked the folder and its not in there.
I even moved the drivers  into the bcml5 folder and im still getting an
invalid driver! I know this is the right driver I had this wireless up and
running a few months ago .  What am I doing wrong here[/QUOTE]This step```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```should copy the file.

I notice you refer to bcml5.inf.  It's actually bcmwl5.inf - that's not the problem, is it?

---

### Post by NoTiG on 2005-05-11
Hey . if anyone gets the error 

"failure inserting ndiswrapper" when they try to modprobe ndiswrapper... I had this problem. but fixed it by 

sudo cp /lib/modules/2.*/misc/ndiswrapper /lib/modules/2.*/extra/ndiswrapper

---

### Post by byen on 2005-05-13
After months of trying to install Fedora and Mandrake...i finally came here and with your help am up and running. this walkthrough is perfect! thank you.... really! thank you! \\:D/  \\:D/

---

### Post by maspro on 2005-05-13
Well to get my Wif-fi working on my Acer Ferrari 3200 I did the following and it worked perfectly  :grin: :
Although I have a laptop with a 64-bit AMD processor, I used the Ubuntu 32-bit version for x86 systems, with the Ndiswrapper v1.1.

- First I plugged in the UTP cable to get internet access (since Wi-fi doesn't work yet  ;-)) . If you have all of the below mentioned software, an off-line installation will also work. 
- Download the ndiswrapper-source (NOT the .deb file) from [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) 
- You will also need an appropriate .inf driver for your Wi-fi, I used bcmwl5.inf.
- If you can't find a suitable driver then take a look here: [http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)
- Then I downloaded **build-essential, linux-headers** and ndiswrapper utils through Synaptic. Although the ndiswrapper utils that are provided through Synaptic aren't really necessary I think because later on there are replaced by a newer version. 

Then I typed the following commands in a terminal-window:
[i]
sudo su <your own password> 
Copy the ndiswrappersource tar file to /usr/src
cd /usr/src
tar xvzf ndiswrapper*
cd ndiswrapper*
debian/rules binary
cd ..
dpkg -i ndiswrapper*.deb
Switch to your driver's directory with the cd command.
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
modprobe ndiswrapper
iwconfig
iwconfig wlan0 essid <fill in your own essid>
iwlist wlan0 scan
iwconfig wlan0 mode Managed
iwconfig wlan0 key restricted <your own wep-key 10 hex digits for 40-bit  encryption or 26 hex digits for 128-bit encryption>
iwconfig wlan0 essid <fill in your own essid>
ifconfig wlan0 up (or dhclient wlan0)
[/i][i]
- I then disabled my eth0 (the port with the UTP cable) in the Gnome GUI network utility. 
- Then use the Gnome GUI network utility to configure your wireless interface.
- Optionally you can download the KWifimanager through Synaptic and also make some configurations there, it also allows you to see if you have any signal strength and if you get an IP-address on your Wi-fi nic.
[/i]
When all works well I typed the following last command:

*ndiswrapper -m*
 
And I added the following line to my /etc/modules: *ndiswrapper*

Maybe there is some redundant stuff that I did in the above list, but it's works perfectly for me. 
So I guess that there are several ways to get your Wi-fi working in Ubuntu!  :razz:

---

### Post by CloudNine on 2005-05-14
Lo guys,

I'm currently working on a Linux driver for Broadcom chipsets. Currently I've got the bcm94306 chipset (the pci id is 14E4:4320) and it can read the MAC address of the card. However, it's really buggy atm, and not really that generic. Seeing as there's quite a few people struggling with ndiswrapper around here, it could be useful for the Linux commnity :) My personal motivation for this is to have a computer of completely free software   :wink: 

More details are at my website: [http://c9online.l2p.net](http://c9online.l2p.net)

Matt

---

### Post by KrIaXPaTaLa on 2005-05-14
Great iniciative ;)

---

### Post by dhanjel on 2005-05-14
[QUOTE=CloudNine]Lo guys,

I'm currently working on a Linux driver for Broadcom chipsets. Currently I've got the bcm94306 chipset (the pci id is 14E4:4320) and it can read the MAC address of the card. However, it's really buggy atm, and not really that generic. Seeing as there's quite a few people struggling with ndiswrapper around here, it could be useful for the Linux commnity :) My personal motivation for this is to have a computer of completely free software   :wink: 

More details are at my website: [http://c9online.l2p.net](http://c9online.l2p.net)

Matt[/QUOTE]

Yeah! I'm waiting for your drivers! Can't use linux until then :/

---

### Post by maspro on 2005-05-14
[quote=jonny]
Hieronymus, maspro

You've probably seen the How To that I wrote for Broadcom cards (I managed to get the repository ndiswrapper to work), and I imagine it didn't work for you. I'd like to point my How To to yours so that users who have similar problems aren't left high and dry. You mention AMD64. Are you using AMD64 ubuntu? If so, I imagine that these are the users that need redirection.

The other thread has had around 7,000 hits so far, so Broadcom cards are obviously presenting huge problems. It would be good to be able to present a cast iron solution set between us.

One minor point that might trip up some unwary noobs: I think that, from a fresh ubuntu install, you'd also need to do apt-get install build-essential before compiling ndiswrapper.[/quote]
The above quote is taken from the following thread: [HOWTO: WLan via Ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=31926)

Thx for your feedback jonny, I think that indeed it's handy to point to [this how-to](http://www.ubuntuforums.org/showthread.php?t=31926) in your thread. The more ways to get a Wi-fi card working under Linux the better!  :grin:

---

### Post by r0jaws on 2005-05-21
Just wanted to say thanks!! :grin: 
Probably one of the best walkthroughs I have found and used it to get sorted on my Avertec 3200. After about a week of frustration, this had me up and running in about 20 mins! TVM!!! \\:D/

---

### Post by aubreyisland on 2005-06-08
alright i just thought id throw out how i got my broadcom (motorola ws810g) going...

first) installed ndiswrapper and the driver bcml...
second) edited /etc/ndis.../bcml.../14...conf to have radiostate = 0
third) used ubuntu GUI to configure netowrk

now its woriking! it reads my AP and all... BUT...

when i finally got it going i wasnt able to browse the internet, 
i disabled ipv6 in firefox using about::config

so now internet browsing works, but as for all my other internet apps such as gaim, etc... they're not working. i even disabled ipv6 in /etc/...aliases and disabled the
ipv6 alias in modprobe.conf

any clue why i cant get internet to work on anything other than firefox?
why: need apt-get to update (wont work because of no internet access)
etc . ps my eth0 is down too...

---

### Post by mosfet on 2005-06-10
hi 
 
i tried everythin posted here...... i'm new using linux 

when i type this

root@ubuntu:/home # ndiswrapper -i ~/home/mosfet/Desktop/bcmwl5.inf

i get this error

Installing bcmwl5
cp: cannot stat `/root/home/mosfet/Desktop/bcmwl5.inf': No such file or directory

any ideas?
can anyone help me?

---

### Post by jonny on 2005-06-10
[QUOTE=mosfet]when i type this

root@ubuntu:/home # ndiswrapper -i ~/home/mosfet/Desktop/bcmwl5.inf[/QUOTE]You've typed the code incorrectly.  The '~' symbol is interpreted by Linux as your own home directory, so you've effectively asked ndiswrapper tp install the file /home/mosfet/home/mosfet/Desktop/bcmwl5.inf.

Try this instead```
ndiswrapper -i ~/Desktop/bcmwl5.inf
```

---

### Post by aubreyisland on 2005-06-10
thats an easy fix i hope...

cd into the directory....

cd /home
cd <userid>
cd Desktop

ndiswrapper -i bcmlw5.inf

install the file FROM the directory so it can also copy the .sys files.

---

### Post by mosfet on 2005-06-10
thanks guys it worked

---

### Post by topboi on 2005-06-12
Please Help I am A Newbie and I follow your steps and made it to #5 and everything but the powerlight and my Motorola WN825G went just like you said but then there is a dim light on but not like it is when I plug it in to my other laptop that is running XP. 
I am running Kubuntu 

When I run iwconfig wlan0 here is my results 

wlan0     Link encap:Ethernet  HWaddr 00:0C:E5:47:53:56
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:11000000-11001fff

and here is the results when I run ifconfig wlan0

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

when I run iwlist scan I get 

root@ubuntu:~ # iwlist scanning
lo        Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     No scan results
eth0      Interface doesn't support scanning.

Please Help 

Newbbie Chris 
 :???:

---

### Post by aubreyisland on 2005-06-12
try... (terminal)


ifconfig wlan0 down
ifconfig eth0 down

//then...

ifconfig wlan0 up

ifconfig <--- and see if you got an ap.

BTW. you arent getting any scans probably because you havent configured your conf files in ndiswrapper: RadioState|0 see my blog for a howto on doing that.

hope this helps you out...

ALSO: I would still like to note my previous post: that although I got my wireless working I still cannot get Gaim or Limewire to do anything.... I dont think its an ipv6 problem anymore as I removed the .ko file, but am pondering if its an ssh config or tpc config? I dont know anyone have any idea where to go?


CHANGES!
Okay limewire is now working? all i did was iwconfig wlan0 power all
but dont know if that is what fixed it?

---

### Post by topboi on 2005-06-14
here is the results of your sugestion 

root@ubuntu:~ # ifconfig wlan0 down
root@ubuntu:~ # ifconfig eth0 down
root@ubuntu:~ # ifconfig wlan0 up
root@ubuntu:~ # ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:138428 (135.1 KiB)  TX bytes:138428 (135.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:E5:47:53:56
          inet6 addr: fe80::20c:e5ff:fe47:5356/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:11000000-11001fff

root@ubuntu:~ # 

and still no bright light on the pcmcia card  ](*,) 


BTW. you arent getting any scans probably because you havent configured your conf files in ndiswrapper: RadioState|0 see my blog for a howto on doing that

thank you ever so much 
Newbbie

---

### Post by aubreyisland on 2005-06-14
by the end of ur message i cant tell if things worked out?:D but, send me iwconfig if it didnt. (looking) i dont get a light either btw. it just doesnt turn on. dont know why!

---

### Post by vtechstu on 2005-06-14
How would i complete steps 5 through the end in Kubuntu.  I'm new to all this and can't get it working! It's driving me crazy.

---

### Post by jonny on 2005-06-16
Sorry, don't know how to do this in kubuntu, as I've never used the KDE wireless network tools.  If anyone else can answer this question, I'll update the how-to for the benefit of other users.

---

### Post by EndersGame on 2005-06-20
Due to a long and painful adventure, I no longer have windows on my Dell Inspiron 5150.  This means I don't have the drivers for the (broadcom) wireless card that I could just point ndiswrapper to.   Therefore:
1.) Will ndiswrapper still work if I just downloaded someone else's bcmwl5 file(s)?
2.) If so, would someone be willing to either host the necessary file(s) or email them to me?
3.) If not, are there any other options available to me?

Thanks.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=EndersGame]
1.) Will ndiswrapper still work if I just downloaded someone else's bcmwl5 file(s)?
[/QUOTE]

Yep.

---

### Post by jonny on 2005-06-20
With a little hunting, you can get the files from Dell's website or from the ndiswrapper site (preferred).  Just remember to get all files starting with bcmwl5.

---

### Post by MetalMusicAddict on 2005-06-20
I FRIGGIN' LOVE YOU MAN!!!!

I got a Dell Inspiron 2200 a month ago. Real base model. For thr day-to-day stuff. Wireless and the screen were the 2 things I couldnt get to work.

I ended up changing the "i810" video driver to "vesa" for now. I've read this is some kinda bug. So I got a screen workin. But not quite. Hopefully Brezzy will fix this.

Now this. So awesome. :) One thing Im wondering. In windows I think the connections load balance and switch back and fourth. 

In Ubuntu if I "plug in" does the connection auto-switch to the faster "wired" one and then back if I unplug?

Also will this be fixed in Brezzy? This card workin' by default I mean.

EDIT:
Maybe I spoke too soon. 2 weird things.

1. I cant connect to my network. I dual boot with this machine and the info is the same on XP/Ubuntu.
2. Why do I have to "sudo modprobe ndiswrapper" everytime I wanna make the wireless work?

Sorry If this has been answered. I couldnt find it on the other pages.

---

### Post by filloy on 2005-06-21
ha, i cant get my wireless card to be On, not Off, not even the Function+F2 is working, dont know why, cuz in windows it does.
I've just modified my BIOS, cus theres an option to keep the Wireless Card on, or Off, but it keeps off.
Any idea of how to ? im using a Gateway Laptop with a Broadcom Wireless Card.
I really need that to work, otherwise, i wont get wireless working.



when i do

sudo modprobe ndiswrapper i get:
> root@marymoon:/home/filloy # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted 

and if i do: ndiswrapper -l i get:

> root@marymoon:/home/filloy # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 


So, i have the driver installed, the hardware present, but i cant start the frikin' card,any ideas

Thanx a lot !

---

### Post by MetalMusicAddict on 2005-06-21
[QUOTE=MetalMusicAddict]
1. I cant connect to my network. I dual boot with this machine and the info is the same on XP/Ubuntu.
2. Why do I have to "sudo modprobe ndiswrapper" everytime I wanna make the wireless work?[/QUOTE]
I found out that my "/etc/network/interfaces" wasnt being saved properly.

I had to do this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0 **<-**change to **wlan0**

 # The primary network interface**<- Move this down**
iface eth0 inet static
address *.*.*.*
netmask *.*.*.*
gateway *.*.*.*


**TO HERE!!**
iface wlan0 inet static
address *.*.*.*
netmask *.*.*.*
gateway *.*.*.*
wireless-essid ******
wireless-key ****************

auto wlan0
```
The network works great now. Just like it was plugged in. ;)

---

### Post by Seer on 2005-06-21
OK Here is a new one for yas... I thinK!!!!

Card is the (using latest winxp drivers) Belkin F5D8000 pre-n PCMIA in a PCI Bracket type card (thats a hotplug thing right???) Every thing appears to go swimmingly until the very last part....

A message from that bastard dmesg (he is always bringing me bad news!)

> ndiswrapper version 1.2 loaded (preempt=yes,smp=no)
ndiswrapper: driver netani (Belkin Software, Inc.,08/11/2004, 1.2.0.68) loaded
PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
PCI: Unable to reserve mem region #1:fffea000@fa020000 for device 0000:03:00.0
ndiswrapper (ndiswrapper_add_pci_device:198): couldn't request PCI regions: fffffff0
ndiswrapper: probe of 0000:03:00.0 failed with error -16
PCI: Failed to allocate mem resource #1:80000@fa080000 for 0000:03:00.0
PCI: Failed to allocate mem resource #0:20000@fa020000 for 0000:03:00.0

For the love of god someone help me :) Its taken me days just to get this far!!! ] (*,)

---

### Post by Seer on 2005-06-21
I may have found the source of my problem in a pretty obscure place - I am just not sure how to adapt the instructions to Ubuntu....

I found out this was the Rioch Rl5c475 PCI adapter from the Device Manager, and then I have read alll kinds of problems with other brands of cards using this too. Then I stumbled on this:

> [http://vprmatrixlinux.theeggbeater.net/](http://vprmatrixlinux.theeggbeater.net/)

Networking
802.11b Wireless Networking
The internal chipset is Mini PCI Orinoco (Ricoh Rl5c475). After working with this I found the following site that shows you how to setup the Ricoh Rl5c475

It is supported via the orinoco driver in PCMCIA-CS. The trick is the chipset is connected via the pci bus to a PCMCIA slot.

Short Install Instructions:
1) compile and install 2.4.x without PCMCIA support but with Wireless LAN support (just Wireless LAN support, none of the drivers under that option)
2) compile and install latest pcmcia-cs (Gentoo: emerge pcmcia-cs)
3) compile and install latest wireless-tools (Gentoo: emerge wireless-tools)
4) edit your pcmcia options so that your socket driver is i82365 and your PCIC_OPTS="irq_mode=0" (use only PCI IRQs) in /etc/conf.d/pcmcia
5) reboot
6) the Ricoh Rl5c475 will be recognized as eth1


So far I have checked for latest version of pcmcia-cs and wireless tools via synaptic.
Problem is I cannot find 4) edit your pcmcia options so that your socket driver is i82365 and your PCIC_OPTS="irq_mode=0" (use only PCI IRQs) in /etc/conf.d/pcmcia

I know its a different NIC actually in the adapter but the problem is apparently due to the kernel trying to assign the same IRQ twice and is present in both 2.4 and 2.6??

---

### Post by Seer on 2005-06-21
Well - the closest I could find was /etc/default/pcmcia which has the exact same layout.... so I followed the instructions (bearing in mind they were for the 2.4 kernel) and produced a file like so:

> # Defaults for pcmcia (sourced by /etc/init.d/pcmcia)
PCMCIA=yes
PCIC=i82365
PCIC_OPTS="irq_mode=0"
CORE_OPTS=
CARDMGR_OPTS=

Reboot and no joy ... so then I went and looked at /etc/init.d/pcmcia as referenced at the top of the file and found this little snippet...

> 		# Treat i82365 specially, as many people with yenta_socket
		# incorrectly has PCIC set to i82365 for historical reasons
		if [ "$PCIC" = i82365 ]; then
		    if ! bridge_module_loaded ; then
			# On 2.6 kernels, we must not load any other bridge
			# modules than the right one
			if cardbus_bridge_present ; then
			    [ "$VERBOSE" != no ] && log_warning_msg "Using yenta_socket instead of $PCIC"
			    load_module yenta_socket || failed_to_load yenta_socket

And bang went my hopes that this week old n00b had figured out something so detailed by himself lol!!!

Really I am going nuts now!!! Sorry for using this post like a journal of my actions but maybe some others with the same card but more knowledge can assist me !!

---

### Post by Seer on 2005-06-21
I promise my last post... (I'm about to pass out :) ) 

I have gone all round the houses reading the documentation and it seems whats needed is this.

You can exclude IRQ's that the Rioch gets assigned to using a file in the /etc/default/pcmcia directory - so in this case I excluded 19. 

Then I found out that this only excludes irqs for the PCI bridge itself and not for the actual card inserted into it. (the problem seeming to be that the machine is attempting to assign the same IRQ to both the PCI Socket and the card inserted into it) For this I presume I would need to exclude the IRQ 19 not with PCMCIA but with the hotplug module with something within the /etc/hotplug directory but I'll be buggered if I can find a file where this is possible.

So if anyone knows a way to exclude an IRQ for the PCMCIA Card that is inserted into the bracket.... I might be on a winner lol 

G'night!!

---

### Post by FesterHead on 2005-06-22
Thanks for the HOW-TO.
Works for me on an HP zd7168cl using the bcmwl5a.inf and bcmwl5.sys files from the latest HP SP.

Getting the wireless was the final straw for conversion to Ubuntu for me.
Rock on.

---

### Post by smedstadc on 2005-06-25
I'm having a problem with this howto. I need to change those radiostates for my card to function properly, but when I used the command suggested (even as superuser) I just get permission denied for each of the files that would have been changed.

I can't open them up to edit manually either... Can anyone help?

---

### Post by jonny on 2005-06-25
I imagine that they're locked by another process.  Did you start the how-to from the beginning, removing ndiswrapper and the existing drivers?  Other users (buried deep within this enormous thread) have reported various problems trying to fix an existing failed ndiswrapper installation, so I'd always recommend a clean restart.

---

### Post by smedstadc on 2005-06-26
Thanks, I'll try that but, in case it doesn't do the trick... what would be the next best course of action?

---

### Post by gushy on 2005-06-27
](*,) can't get my belkin f5d7010 working ... strange because I've had it working before ... with warty not hoary though.

[list][*]lspci shows the card is present
[*]ndiswrapper shows the driver loaded and the hardware present
[*]the ndiswrapper module is loaded
[*]iwconfig shows the card
[*]all the config files have RadioState|1
[/list]

yet the radio no the card will not come on, no green light. :(

Can anyone suggest what else I can look at?

---

### Post by jonny on 2005-06-27
Radiostate should be 0, not 1.  That's the central cause of the confusion with these cards.

This is the code that will fix it.  Cut, paste and enjoy wireless networking.```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

---

### Post by gushy on 2005-06-28
oh ok, I see that now in the other posts, but I was absolutely positive that when I had problems with the radio state in the past I had to change it to 1.  my bad.

now I feel like an idiot! :roll: 

thanks.

---

### Post by flibble on 2005-06-30
Woooo Hoooooo !

Found your guide and have wireless up with wpa-psk. Thank you! 

Information for others: I'm using a T23 thinkpad, model 2468-ra1, a Linksys WPC54G v1.2 (broadcom chip) as client and a Linksys WRT54G router. The Linksys drivers didn't work for me at all. I tried them all, including the betas. What did work was the latest dell drivers (lost the link but i got them from dell's website). These drivers also work for me under XP (for what it's worth). In Ubuntu, I used ndiswrapper and this guide to wpa_supplicant.

Many thank. :)

---

### Post by sds on 2005-07-03
Hi all,
First of all, thanks to the author for writing this - I'm a recent convert to Linux / Ubuntu and there is a huge learning curve.
I've followed the instructions to the letter (i.e. all Radiostates|0) and my Belkin FD7010 network card now lights up (just the power light).
I know my card definitely works as I've been using it in Windows XP which is also on this laptop.
However, it can't see the access point (despite me opening it up completely and being a metre away from it). I've followed other bits of info I've seen and changed the channel so its the same (5) and tried setting the SSID. However, I think that could be the problem - even after typing 
```
sudo iwconfig wlan0 essid shah
```

iwconfig wlan0 still gives:
```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I've set the WAP to broadcast its SSID but when I try "iwlist scan" I get:
```
root@LinuxLaptop:/home/sunil # iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

Changing the AP's channel doesn't help.

I've also tried deactivating the eth0 interface completely and trying it but that doesn't seem to work either.

ndiswrapper -l gives:
```
Installed ndis drivers:
bcmwl5  driver present, hardware present
```

dmesg gives me:
```
 0x1bf73fff
ACPI: FADT (v002 AMDK8  PTLTW    0x06040000 PTL_ 0x000f4240) @ 0x1bf79e77
ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1bf79efb
ACPI: MADT (v001 PTLTD           APIC   0x06040000  LTP 0x00000000) @ 0x1bf79fb0ACPI: DSDT (v001  VIA   PTL_ACPI 0x06040000 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x4008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:8 APIC version 16
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda4 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1601.235 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 446620k/458176k available (1436k kernel code, 10960k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3170.30 BogoMIPS (lpj=1585152)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000010 00000000 00000000
CPU: AMD Mobile AMD Sempron(tm) Processor 2800+ stepping 02
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd557, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Via IRQ fixup
PCI: Via IRQ fixup
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *11, disabled.
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 12 14 15) *10
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: Embedded Controller [EC] (gpe 11)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:05: ioport range 0x600-0x60f has been reserved
pnp: 00:05: ioport range 0x1c0-0x1cf has been reserved
pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:05: ioport range 0xfe10-0xfe11 could not be reserved
audit: initializing netlink socket (disabled)
audit(1120402439.567:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 4
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 Z007 ILAN  LID SLPB
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Thermal Zone [THRS] (27 C)
ACPI: Thermal Zone [THRC] (42 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:11.1
ACPI: PCI interrupt 0000:00:11.1[A]: no GSI - using IRQ 0
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
    ide0: BM-DMA at 0x1c60-0x1c67, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1c68-0x1c6f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: HTS424040M9AT00, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 78140160 sectors (40007 MB) w/1739KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 > p4
Probing IDE interface ide1...
hdc: UJDA760 DVD/CDRW, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 457812k swap on /dev/hda6.  Priority:-1 extents:1
EXT3 FS on hda4, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.8
 180 degree mounted touchpad
 Sensor: 18
 new absolute packet format
 Touchpad has extended capability bits
 -> 4 multi-buttons, i.e. besides standard buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio4
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ts: Compaq touchscreen protocol output
ndiswrapper: driver bcmwl5 (Broadcom,06/13/2003, 3.20.23.0) added
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected AGP bridge 0
agpgart: Maximum main memory to use for agp memory: 380M
agpgart: AGP aperture is 256M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
Yenta: CardBus bridge found at 0000:00:0b.0 [1025:006e]
Yenta: ISA IRQ mask 0x0c78, PCI irq 17
Socket status: 30000006
PCI: Enabling device 0000:00:0b.1 (0000 -> 0002)
ACPI: PCI interrupt 0000:00:0b.1[B] -> GSI 18 (level, low) -> IRQ 18
Yenta: CardBus bridge found at 0000:00:0b.1 [1025:006e]
Yenta: ISA IRQ mask 0x0c78, PCI irq 18
Socket status: 30000820
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:0b.2[C] -> GSI 19 (level, low) -> IRQ 19
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]
PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:06:00.0 to 64
ndiswrapper: using irq 18
USB Universal Host Controller Interface driver v2.2
wlan0: ndiswrapper ethernet device 00:11:50:10:97:b8 using driver bcmwl5
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0x1c00
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0x1c20
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae40444100f4e]
uhci_hcd 0000:00:10.2: irq 21, io base 0x1c40
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.3: irq 21, pci mem 0xd0005800
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
Initializing USB Mass Storage driver...
irda_init()
NET: Registered protocol family 23
usb 1-1: string descriptor 0 read error: -71
usb 1-1: string descriptor 0 read error: -71
usb 1-1: string descriptor 0 read error: -71
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb 1-1: USB disconnect, address 2
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb 4-1: new high speed USB device using ehci_hcd and address 2
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
via82xx: Assuming DXS channels with 48k fixed sample rate.
         Please try dxs_support=1 or dxs_support=4 option
         and report if it works on your machine.
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
usb 1-2: new low speed USB device using uhci_hcd and address 4
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [USB Wheel Mouse] on usb-0000:00:10.0-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
eth0: VIA Rhine II at 0x1800, 00:0a:e4:5e:1d:8d, IRQ 23.
eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
NET: Registered protocol family 17
  Vendor: Generic   Model: USB Flash Disk    Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
SCSI device sda: 255488 512-byte hdwr sectors (131 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 255488 512-byte hdwr sectors (131 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: unknown partition table
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
cpu_init done, current fid 0x8, vid 0x4
powernow-k8: ph2 null fid transition 0x8
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
wlan0: no IPv6 routers present
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
eth0: no IPv6 routers present
ibm_acpi: ec object not found
```

Finally I followed the instructions given on another howto somewhere in this thread (where he made ndiswrapper from source) but that still didn't work.

Please help!

---

### Post by DW5 on 2005-07-05
[QUOTE=dhanjel]It would be nice if all of you that got the broadcom chipset working wrote down your wifi-card name in this thread so you get this thread as a search result when searching for cards that works in the forums.[/QUOTE]

BCM 4301 802.11b built into a Compaq nx9010 laptop

I fiddled with this for a couple of hours, and after double checking the radio states manually (not all had changed using sed for some reason) and doing a couple of reboots, things worked. 

 I am having to do a #sudo modprobe ndiswrapper after each boot and having to turnoff eth0, and would ultimately like to know if someone knows how to fix that.

Thanks for the hard work everyone has put in on this howto.

DW

---

### Post by MetalMusicAddict on 2005-07-05
[QUOTE=DW5]BCM 4301 802.11b built into a Compaq nx9010 laptop

I fiddled with this for a couple of hours, and after double checking the radio states manually (not all had changed using sed for some reason) and doing a couple of reboots, things worked. 

 I am having to do a #sudo modprobe ndiswrapper after each boot and having to turnoff eth0, and would ultimately like to know if someone knows how to fix that.

Thanks for the hard work everyone has put in on this howto.

DW[/QUOTE]

Look at my posts on this page. #s 123&125. I had to turn off eth0 also. 

Search is your friend. ;)

---

### Post by DW5 on 2005-07-07
[QUOTE=MetalMusicAddict]Look at my posts on this page. #s 123&125. I had to turn off eth0 also. 

Search is your friend. ;)[/QUOTE]

Indeed.  I had read those but was not far enough along in the problem solving to recognize that changing the config file was the solution.  I mapped both wlan0 and eth0 and both seem to be active and hot at boot up.  

I have that crazy "SIOCGIFFLAGS error: No such device" on the network display applet on the panel now still and can't seem to get it gone (and search hasn't found the answer yet)--but at least I am networked both wired and wireless.


Thanks.

---

### Post by MetalMusicAddict on 2005-07-07
[QUOTE=DW5]...but at least I am networked both wired and wireless.[/QUOTE]

Are you connected to the same network both wired and wireless? I think I had to turn off my eth0 to connect wireless and vice-versa.

---

### Post by DW5 on 2005-07-08
[QUOTE=MetalMusicAddict]Are you connected to the same network both wired and wireless? I think I had to turn off my eth0 to connect wireless and vice-versa.[/QUOTE]

It appears so.  Both devices are active and the surfing is fine.  I wish I had the network applet working so that I could get a sense of connection speed.  My wired is 100btx and my wireless is 10bt.  I would like to see if there is automatic switching when I plug in to the wired or if I need to turn off wireless to get the better speed.

Anyway, I think maybe the mapping both wlan0 and eth0 might have done that.  I such a newbie though, that it's speculation on my part.

---

### Post by jonny on 2005-07-09
If you're using Gnome - I really can't understand why anyone would want to use KDE  :grin: (duck for cover) - and you configured your network settings using the gnome tools, you can tell which device is being used by looking in System --> Administration --> Networking.  The device listed under default gateway is the one that connects you to the internet.

To get a networking applet, right -click on your panel and select Add to Panel.  You neet to add the Network Monitor.  When it appears in your panel, click on it and change the properties to select wlan0 or whatever your wireless device is called.

I should make two warning here, though.  First, I find that the applet sometimes freezes my entire laptop when I change the device name.  Second, the signal strength meter doesn't work with my Broadcom card - but you can tell when you're transmitting or receiving.

---

### Post by Error1312 on 2005-07-10
Thank you so much to all of you! 

After reading 9 pages of this thread I finally managed to get my wireless up and running :grin: No more network cables for me.

---

### Post by luckyboylost on 2005-07-11
Okay my first post, and im a big fresh off the boat noob to linux.  These are the steps i took to make my wireless card work.  I have a motorola WPCI810G card that uses the windows bcmwl5.inf file.  Here is my step-by-step, noob-style, to get everything up and running on the wireless.  I did it from a fresh install of ubuntu.  So if you have ndiswrapper installed, you may want to unistall everything you have done with it before going through my steps.   Oh and im using the 5.04 version of ubuntu

Step 1:
 UPDATE UBUNTU!  Some people in these posts were getting an error upon the final step of "sudo modprobe ndiswrapper" (the steps listed at the beginning of this thread).  The error had something about not being able to find/use ndiswrapper.ko  I had this problem when i tried to do my own steps to installing my wireless card and forgot to update ubuntu before I started.  So make sure you are up to date.  Go to: System->Administration->Ubuntu Update Manager

Step 2:
INSTALL NDISWRAPPER!  I ultimatly ended up installing ndiswrapper-1.2  I used this page at wiki: [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) 
there is one slight difference.. the howto at wiki is for version 1.1 just substitute 1.2 for 1.1 in all the instructions.  I'm sure v1.1 would work fine though.  To open a terminal window go to Applications->System Tools->Terminal

Step 3:
REBOOT!  If you followed the instructions on the wiki page to the t, then you should see your wireless card in System->Administration->Networking before you reboot.  But the reboot allows ubuntu to talk to the wireless card.

Step 4:
CONFIGURE YOUR NETWORK!  Go to System->Administration->Networking.  Click on your Ethernet connection and click on Deactivate.  Then click on Wireless connection and click on Properties.  check the "This device is configured" box and select your ESSID which should pop up in the drop-down box.  Now one of the problems I originally had was that my network was set up with AES encryption.  I had to change it to WEP.  If you configured your WEP using a phrase, then when you enter the WEP key in the text-box you MUST preface it with s:   Under connection settings set the Configuration to DHCP (assuming your router is using a DHCP server which most do out of the box).  Click OK and you should be good to go.

One problem I still have at the time of this post is that upon reboot my eithernet is set to default.  I think that is fixed in the /etc/network/interfaces file, where it says 

```

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

```

I think the eth0 needs to be changed to wlan0.  Ill guess ill find out when I reboot, but if someone knows im wrong, could they let me know?

I want to give a big thanks to jonny for the how-to write up.  The community here, from what i have read thus far, is awsome.  This is what will liberate me somewhat from m$ and expensive software \\:D/ .   I only hope my little ultra noob write up helps some other ultra noob.

---

### Post by luckyboylost on 2005-07-12
nope editing the /etc/network/interface file by changing that one word from my last post didnt work.  I also moved the

iface eth0 inet dhcp

line down below the wireless stuff.  After reboot I have to reactivate my wireless card to get a connection.  Anyone have any thoughts as to how I can get the wireless to work upon boot up?  ](*,)

---

### Post by flak9 on 2005-07-13
Ok.  I have updated as it says above.  I have an emachines m6805 with the broadcom wireless chip and I have done exactly what was posted in the guide and am coming up with this error when I am booting: 

```
WARNING: /etc/modprobe.conf exists but does not include /etc/modprobe.d/
```

When I reboot and do a modprobe ndiswrapper, I can goto the Network and see my wireless device, but I think I only have an issue when it reboots.  How  can I restore modprobe.d?

I have removed the ndiswrapper source and utils through synaptic.  I think that i might have possibly deleted something called modprobe.d, when I was fussing around earlier.  Im not sure whats going on.

Can somebody who is using the broadcom driver post their modprobe.conf file?

What should I try next?  :-x

---

### Post by jaymacwade on 2005-07-14
I had read all 13 pages of this thread and spent about a day and a half trying every suggestion posted there without success.  No matter what I tried, ndiswrapper from the synaptic repository would not work.  ](*,) 

I ended up compiling ndiswrapper v1.2 from source.  Once that was done, everything suddenly fell into place.  I am now surfing without the wires.  Not bad considering that the Dell technician I talked to couldn't even help me get it working in M$Windows!    :grin: 

Now I just need to get the internal modem working.  (--No PCtel drivers for 2.6 kernel  ](*,) --)

Here are my specs:
Dell Latitude C640 laptop
Broadcom BCM4306 mini-pci wifi card (Dell TrueMobile 1300?)
Ndiswrapper v1.2 (compiled from source)
Windows XP driver (Dell download #R81433)

Hope this helps someone else,
~ j.Wade

---

### Post by pierre on 2005-07-18
Hi all,

My laptop is an HP zd8147ea with broadcom b/g
Kernel is a Ubuntu, kernel 2.6.10-5-686-smp
I've applied the following instructions ( Hieronymus code ) and it works well after a reboot.

 ```

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install linux-headers-2.6.10-5-686-smp 
*( Linux kernel headers 2.6.10 on PPro/Celeron/PII/PIII/PIV SMP )*
cd /usr/src/
sudo tar xvzf ndiswrapper-1.2 
([version ndiswrapper-1.2](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.2.tar.gz?download) *to be copied onto /usr/src/ *) 
cd /usr/src/ndiswrapper-1.2/
sudo make
sudo make install
cd /home/pierre/Desktop/
sudo ndiswrapper -i bcmwl5.inf 
sudo ndiswrapper -l
sudo modprobe ndiswrapper *( blue led appears now )*
sudo dmesg 
sudo iwlist wlan0 scan
sudo ndiswrapper -m 

```

I used Network Administration in order to manage Wlan Card ( DHCP, WEP Key ) and set wlan0 as default.
It works fine after reboot.

Hieronymus, Jonny , u all in this thread are really fantastic 

Kind regards,

Pierre

Added : Just in case for zd8147ea users who cannot find drivers for this laptop.
They are on my own ftp.
[bcmwl5.inf](http://www.lylyspace.com/nux/bcmwl5.inf) 
[bcmwl5.sys](http://www.lylyspace.com/nux/bcmwl5.sys) 
and
[ndiswrapper1.2](http://www.lylyspace.com/nux/ndiswrapper-1.2.tar.gz)

---

### Post by umdzig on 2005-07-25
I have installed ndiwswrapper. When i try to install the driver for my dell true mobile 1300, with the broadcom driver bcmwl5.inf all i get is this:

[COLOR=DarkOrange]root@laptopmike:/home/zig # sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
ls: /etc/ndiswrapper: No such file or directory
Installing bcmwl5
cp: cannot stat `/root/Desktop/bcmwl5.inf': No such file or directory[/COLOR]


Any help is appreciated as this has been driving me crazy!

---

### Post by zer on 2005-07-27
umdzig: You are already root, so the path is wrong ($HOME of root is another path as $HOME of the user)
Please open a gnome-terminal (pressing ALT+F2 and typing "gnome-terminal" followed by <Enter> will do it)
The follow the instructions.

---

### Post by Julius on 2005-07-28
This howto got my card to work under Linux!
However, I was not able to change the value to 0 in all the .inf files by the command, I had to do it manually instead.

The problem is that now I get tons of messages at boot, one for each single inf file.
The message says something like "file 123981290.inf~ ignored"

(the file name I wrote is just random :P)

---

### Post by umdzig on 2005-07-29
Julius: I had to do the same thing and im getting the same problem, however my wireless does work so im not too worried about it.

---

### Post by jonny on 2005-07-30
[QUOTE=Julius]This howto got my card to work under Linux!
However, I was not able to change the value to 0 in all the .inf files by the command, I had to do it manually instead.

The problem is that now I get tons of messages at boot, one for each single inf file.
The message says something like "file 123981290.inf~ ignored"

(the file name I wrote is just random :P)[/QUOTE]
You used gedit (Applications --> Accessories --> Text Editor) to do your amendments, right?  By default, when gedit overwrites and existing file, it creates a backup file with the same name, but with a ~ character added to the end.  These files can't be seen with Nautilus, even if you ask to see hidden files, but they're very real.

You can delete these files in a terminal session with the 'rm' command; that should make your problems go away.  But it still doesn't explain why the how-to didn't work properly.  Did you get any strange error messages when you tried the command to turn the zeroes into ones?

---

### Post by foxy123 on 2005-08-02
hi jonny,thanks a lot for the great howto. It worked out very well for me, I only needed to make changes in conf files manually and here I am with Belkin wifi card enabled.

---

### Post by Stelmate on 2005-08-03
SOLUTION FOUND:
If you have
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Check your system logs, what happened to me is the update manager installed a new version of ndiswrapper when I wasn't looking, just reinstall the older version from the synaptic manager under packages>force version> hoary version
than install the older one and packages>lock version so it doesn't happen again.
Hope that helped some of you

---

### Post by Ubuntu-one on 2005-08-03
Ok, so i've read every post tried a lot...

boris@ubuntu-one:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Keep getting this.

My version of ndsiwrapper is 0.12+1.0rc2-1, if I need another version please tell me which one and where i can get it. But all is configured according to this post. 
Dunno what to do please help.

--------------------------------------------
Ok.

Got it... 
I had compile ndiswrapper to get it work.
Work fine now thanx to the post by luckyboylost..

---

### Post by foxy123 on 2005-08-03
[QUOTE=Ubuntu-one]Ok, so i've read every post tried a lot...

boris@ubuntu-one:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Keep getting this.

My version of ndsiwrapper is 0.12+1.0rc2-1, if I need another version please tell me which one and where i can get it. But all is configured according to this post. 
Dunno what to do please help.[/QUOTE]
I've got the same version and no problem...

---

### Post by BlueJack on 2005-08-03
Thanks for this HOWTO, i am now able to connect to my wireless linksys router(WAG54G). However, i do have two small problems.

1. the local ip address of the machine with the wireless card keep increasing on every reboot (from 192.168.1.102 to 192.168.1.103 and so on) is this normal? if so, how can i use port forwarding to this machine?

2. while booting its takes an extra 30-60 secs to complete the Network Setup step, i can live with this, but would be nice to know of any way around it.

anyways, thanks again to everyone who has contributed to this HOW TO.


.

---

### Post by foxy123 on 2005-08-04
[QUOTE=BlueJack]
<snap>

2. while booting its takes an extra 30-60 secs to complete the Network Setup step, i can live with this, but would be nice to know of any way around it.
<snap>
[/QUOTE]
Got the same thing. Though, it took some time to connect to a router even via ethernet cable...

---

### Post by jonny on 2005-08-04
[QUOTE=BlueJack]Thanks for this HOWTO, i am now able to connect to my wireless linksys router(WAG54G). However, i do have two small problems.

1. the local ip address of the machine with the wireless card keep increasing on every reboot (from 192.168.1.102 to 192.168.1.103 and so on) is this normal? if so, how can i use port forwarding to this machine?

2. while booting its takes an extra 30-60 secs to complete the Network Setup step, i can live with this, but would be nice to know of any way around it.

anyways, thanks again to everyone who has contributed to this HOW TO.


.[/QUOTE]
1.  I've never seen this happen before, but, hey, it works.  If you want to keep the same IP address each time, you shouldn't use DHCP.  That only takes a small amount of fiddling in your router's settings and in your ubuntu network settings but presupposes a willingness to learn some networking basics.

2.  The delay happens while your laptop is waiting for an IP address to be allocated by your router.  If you don't plan to use the network in a particular session, or if you know that you're out of range of your wireless network, you can cut this step out by pressing ctrl-c.  In my experience the delay is usually shorter if you use static IP addressing.

---

### Post by gardnerm on 2005-08-04
I am having problems with a Dell Latitude D800 with the Dell Truemobile 1450. I have the wireless card working and can connect to access point fine as long as SSID is being broadcast and no encryption. When I try to disable SSID broadcast or use WEP I can not connect. Has anyone else had these problems?

---

### Post by BlueJack on 2005-08-04
[QUOTE=jonny]1.  I've never seen this happen before, but, hey, it works.  If you want to keep the same IP address each time, you shouldn't use DHCP.  That only takes a small amount of fiddling in your router's settings and in your ubuntu network settings but presupposes a willingness to learn some networking basics.

2.  The delay happens while your laptop is waiting for an IP address to be allocated by your router.  If you don't plan to use the network in a particular session, or if you know that you're out of range of your wireless network, you can cut this step out by pressing ctrl-c.  In my experience the delay is usually shorter if you use static IP addressing.[/QUOTE]

switching to staitc IP address fixed the first problem, i can live with the second.

thanks for your help jonny,

---

### Post by douglas_slac on 2005-08-11
So, this is the only thing I have found anywhere that has actually worked on getting the wireless working on my Dell laptop.  Makes me wonder why this only exists here and other people are either not having problems, or can get things working without help.  Anyway a few comments:

1. I needed the bcmwl5a.inf file for the card, not a big deal.

2. I got the drivers from an update on the Dell web pages.  The HOWTO here seems to suggest that people can copy this over from a Windows install on another partition.  Are people actually using Windows out there, and have this installed on another partition?  Weird.  So, the driver update came from Dell as a self extracting file that ended with a *.exe.  I had no idea really what to do with this, and neither did Ubuntu it seems.  I had to install wine to handle this file, and get the small *.inf file out of it.  Do people know if there is a better way to handle this?  How do people deal with these *.exe files in Ubuntu?

3. The shell script for loop with cat piping into sed and piped into a file is a little cludgy in the HOWTO.  perl can edit the files in place a little more cleanly with code like:

perl -pi -e 's/RadioState\|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf

This one line will do the same as the last three lines of code in your point 3 in the HOWTO.

4. Is there someway to put ndiswrapper supported wireless cards into ubuntu support such that these cards will hopefully just work when the computer gets installed?

Thanks for the only working help for the card I have found so far.

---

### Post by schultzy on 2005-08-11
Just wanted to say thanks for this walkthrough. It took me a couple of tries with different drivers, but it's working great! I've played with Linux from time to time, but always went back to windows because there was always something that I couldn't get working. This is the first distro I've tried that I could get everything working. Mainly due to the great how to's on these forums. Thanks to all that have posted them up. Hopefully, I will become savvy enough to post my own someday.

 =D>

---

### Post by Byggarn on 2005-08-12
Many thanks to everybody contributing in this thread, finally after 5 hours of tweaking and rebooting I got my Linksys WPC54G to work  :smile: .

Greetings from sunny Sweden //Byggarn

---

### Post by MarkN on 2005-08-15
I haven't checked this thread for about a week, so if the problem has already been solved then I give my apologies... :-)

If you are having trouble connecting to a wireless access point when using WEP, but it works perfectly when WEP is switched off, then try the following:

1. Open a terminal. Ensure that the ndiswrapper module is loaded and the card is activated (read the instructions on page 1).
2. Type: "sudo iwconfig wlan0 essid *youressidgoeshere*"
3. Type: "sudo iwconfig wlan0 key open *yourwepkeygoeshere*"
4. Now try to use the wireless network. If it works, go back to your terminal.
5. Using sudo, open an editor to edit the file "/etc/network/interfaces". (e.g. "sudo gedit /etc/network/interfaces").
6. In the section for "wlan0", insert the lines:
"wireless-mode Managed"
"wireless-keymode open"
7. Save the file.
8. Either restart the computer or type:
"sudo ifdown wlan0" then "sudo ifup wlan0" into the terminal.

Hope this helps!

---

### Post by lomomo on 2005-08-17
i've been all day trying to setup a belkin pci wireless card, finally i managed to compile and install ndiswrapper 1.2 and now i've the wlan0 device. The pci card light is on and i can set an IP to the interface.

The problem is i can't see my AP.

When i do sudo iwlist scan i get this:

> Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     No scan results

I'm using the bcmwl5a driver becouse the bcmwl5 was not working.

When i do dmesg after modprobe ndiswrapper i get this:

> ndiswrapper: using irq 17
wlan0: ndiswrapper ethernet device 00:11:50:3b:1a:69 using driver bcmwl5a, configuration file 14E4:4320.5.conf
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP

It seems to be all ok but i can see the AP. The AP is working fine and i'm using it with my laptop. I tryed to disable all security options on the AP but i got the same result. Any idea on how can i fix this?

---

### Post by S.nazari on 2005-08-18
> **jonny]Broadcom wireless cards are tricky to set up in ubuntu, and the forums are full of frustrated users seeking advice.  Broadcom provide no Linux support (feel free to complain to your hardware vendor or choose a different card if you haven't yet shelled out your cash), but they can be made to work - and you're in the right place if you want to know how.

First, you need to find out if this How To is for you.  Broadcom wireless cards come under many brand names and, in particular, are used in many Dell and Acer laptops.  Look for the drivers supplied with your card (Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON) said:**
> How to add extra repositories[/URL]

3. Open a terminal session and enter this code.  Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```4. Reboot your PC.  On restarting, the light on your wireless card should come on.  If not, try entering```
sudo modprobe ndiswrapper
```5. Your card is now working.  Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings.  Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one.  You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK.  The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK.  Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana.  If everything works, you can delete the file from your desktop.

13.  You might notice that the signal strength applet doesn't work properly.  This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled.  Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.

[COLOR=Indigo](Note: This how-to has been updated to reflect all comments from the thread up to 19 April)[/COLOR]
[B]
loadndisdriver error / Ignoring config files at start up.[/B]
Problem with config file Radiostate editing form 1 to 0:
driver not loading during startup.
The command above written by jonny:
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```
May not work in some cases. My case was one of them.
How to find out if you affected? during start up you will get the error something along the lines of loadndisdriver error / Ignoring config, to check what caused it after entering the command given by jonny, go to the config directory. This is the directory that the above command effects. You will find that all the config files have no size at all. **(have a look at the attached Screen Shot 1**.)
The command above has deleted them or something has gone. Wrong.
I would recommend manual editing of all the cofig files in this directory instead of using the command above. Therefore you must uninstall and then reinstall the bcmwl5 drivers as mentioned above but this time instead of using the command above to edit the radio state in the config files you should  open them one by one and follow below.
Alt3. Open each file and edit the RadioState|1 to RadioState|0

Alt3.1 Then save the changed files NOT TO THE SAME DIRECTORY (/ect/ndiswrapper/bcmwl5) but to another directory of you choice.

Alt3.2 After all four files have been changed and saved to an alternative directory form that above, select all the four Original corrupt config files (note that there is a short cut file also present, you do not need to do anything with this) to your desktop. 

Alt3.3 As soon as you have done this move, you will see that the shortcut file mentioned above will disappear. Do not worry! it will reappear as soon as you put the FOUR EDITED FILES to the /ect/ndiswrapper/bcmwl5 directory. 

Alt3.4 All you have to do now is restart the computer and the light on the card should come on.

Alt3.5 Use the GUI Networking tool in Ubuntu to activate the card and start your Internet connection, or you can use the command;
```
:~$ dhclient wlan0
```
And you should fine that an AP (access point is found), and an IP has been given to you computer.

(REMEMBER DO NOT SIMPLY OPEN THE CONIFG FILES AND SAVE TO THEIR ORIGINAL DIRECTORY, THE PROCESS MUST BE COMPLETELY MANUAL AS IN STEPS Alt3.-3.5)

---

### Post by dizbah on 2005-08-19
I am having a problem with step 4.  I get the following when running it: 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686-smp/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


I have rebooted and my wifi lite is still unlit.  I am using a dell 1350 wireless card and have the bcmwl5.inf saved on my desktop.  I am very new new to linux and would greatly appreciate the assistance.

---

### Post by lyzer on 2005-08-21
[QUOTE=kmyram]So, these are the AP's you can see - which is yours? If it's "@home" then try:

$ iwconfig wlan0 essid @home
$ iwconfig wlan0 key C0AD-9DDC-5AFD-BC8B-AA46-CAE5-98
$ dhclient wlan0

Should work (if the key is right too :))[/QUOTE]


after following the tut here and the one on the wiki with no luck i went and popped in my netgear M4A01 card from 4 years ago and ubuntu auto-detected and set it up no problem and i was running wifi. but my dell has an internal broadcom sooo i wanted to get it working, the only way i've gotten it to work is running the tutorials and then do 

$ iwconfig wlan0 essid linksys
$ dhclient wlan0

thanks so much kmyram! you made my day :)

---

### Post by Julius on 2005-08-21
[QUOTE=jonny]You used gedit (Applications --> Accessories --> Text Editor) to do your amendments, right?  By default, when gedit overwrites and existing file, it creates a backup file with the same name, but with a ~ character added to the end.  These files can't be seen with Nautilus, even if you ask to see hidden files, but they're very real.

You can delete these files in a terminal session with the 'rm' command; that should make your problems go away.  But it still doesn't explain why the how-to didn't work properly.  Did you get any strange error messages when you tried the command to turn the zeroes into ones?[/QUOTE]
 Yeah, some days ago I realized that those were the backups. I was using a root nautilus but I couldnt see them, but that was because the option of showing hidden files and backups wasnt checked.

The error I got was most likely access denied. I'm sorry I didn't copy the output for that command.

---

### Post by poetic_folly on 2005-08-23
please help! I am a complete noob here, and don't have access to anything other than wifi at the moment (well, without going to another house and setting stuff up). 

Is there ANY way to make my wifi card work WITHOUT having a net connection first?

---

### Post by ChamPro on 2005-08-25
Wireless and Ubuntu just don't mix well right now. It's enough trouble to get a Intel 2200 to work, but these Dell 1350 cards are impossible.

I tried following both sets of directions. The original set conks out on the "cat" command. If I run it in a root terminal, the command screws up all twenty of the .conf files by making them 0 bytes. Following the revised set of directions, I couldn't move the .conf files out of the directory in order to move the saved ones in.

So I'm stuck with unrecognized WiFi... and that crappy "Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted".

Any suggestions?

[QUOTE=S.nazari][B]
loadndisdriver error / Ignoring config files at start up.[/B]
Problem with config file Radiostate editing form 1 to 0:
driver not loading during startup.
The command above written by jonny:
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```
May not work in some cases. My case was one of them.
How to find out if you affected? during start up you will get the error something along the lines of loadndisdriver error / Ignoring config, to check what caused it after entering the command given by jonny, go to the config directory. This is the directory that the above command effects. You will find that all the config files have no size at all. **(have a look at the attached Screen Shot 1**.)
The command above has deleted them or something has gone. Wrong.
I would recommend manual editing of all the cofig files in this directory instead of using the command above. Therefore you must uninstall and then reinstall the bcmwl5 drivers as mentioned above but this time instead of using the command above to edit the radio state in the config files you should  open them one by one and follow below.
Alt3. Open each file and edit the RadioState|1 to RadioState|0

Alt3.1 Then save the changed files NOT TO THE SAME DIRECTORY (/ect/ndiswrapper/bcmwl5) but to another directory of you choice.

Alt3.2 After all four files have been changed and saved to an alternative directory form that above, select all the four Original corrupt config files (note that there is a short cut file also present, you do not need to do anything with this) to your desktop. 

Alt3.3 As soon as you have done this move, you will see that the shortcut file mentioned above will disappear. Do not worry! it will reappear as soon as you put the FOUR EDITED FILES to the /ect/ndiswrapper/bcmwl5 directory. 

Alt3.4 All you have to do now is restart the computer and the light on the card should come on.

Alt3.5 Use the GUI Networking tool in Ubuntu to activate the card and start your Internet connection, or you can use the command;
```
:~$ dhclient wlan0
```
And you should fine that an AP (access point is found), and an IP has been given to you computer.

(REMEMBER DO NOT SIMPLY OPEN THE CONIFG FILES AND SAVE TO THEIR ORIGINAL DIRECTORY, THE PROCESS MUST BE COMPLETELY MANUAL AS IN STEPS Alt3.-3.5)[/QUOTE]

---

### Post by kdavison007 on 2005-08-26
[QUOTE=poetic_folly]please help! I am a complete noob here, and don't have access to anything other than wifi at the moment (well, without going to another house and setting stuff up). 

Is there ANY way to make my wifi card work WITHOUT having a net connection first?[/QUOTE]

Just download Nndiswrapper and your windows driver from your other workstation and use a key drive, floppy, built in LAN, or CD-ROM to copy it to your Ubuntu system.  

The instructions in this thread are good, but I decided to get the latest ndiswrapper and then just follow the INSTALL instructions included with Ndiswrapper and I had it working in 5-10 minutes.  My only problem now is an IRQ conflict with Ndiswrapper and ACPI when my Dell D600 boots from the battery it hard locks.  Been working on that for a long time...

---

### Post by monpet on 2005-08-28
I'm an experienced Windows user, but a LINUX newbie. Have tried KUBUNTU, but found out, that UBUNTU fits better for me. Both KUBUNTU and UBUNTU installed without problems on my laptop, and while the wired network worked from the box, the wlan drove me crazy. I use an ASUS WL 500g AP and an ASUS WL 100g PCMCIA card. Works great with Windows XP.
Have surfed three days (and nights) through almost every Google link. Had the newest ndiswrapper 1.2 pluss utilities via Synaptic and the bcmlw5-driver from the ASUS-cd. After the usual ndiswrapper procedure, which is also described in this HowTo, the card came up and was recognized both with terminal commands and in the Networksettings-window. 
But whatever I did, I couldn't access the AP. Couldn't ping anything. Until I found this thread (havn't searched for Broadcom so much before).
Because I had done all the first described steps from a new install of UBUNTU 5.04 and after install and upgrade to ndiswrapper 1.2 pluss utilities via Synaptic before, I just edited the 3 *.conf files with 
'sudo gedit /etc/ndiswrapper/bcmwl5/*.conf' (for * I filled in the number/letter combination of each file)
and found in all files the 'RadioState|1' line, which I changed to 'RadioState|0'.
Saving.
Reboot.
And nearly unexspected after three days frustration, both LED's on the card worked and I was connected to Internet and home-network.

You all have done an amazing job with this Howto and saved my weekend and me from 'the great depression'  :razz: .

My specs:

CINET smartbook 830
Pentium M 1,7
512 RAM
30 Gb harddisk, dual boot Windows XP professional english and Ubuntu 5.04 german (this is workrelated)
ATI Randeon mobility M7 (7500)
Asus WL 100g PCMCIA card (recognizes as PCI card)
Asus WL 500g AP

---

### Post by ChamPro on 2005-08-30
[QUOTE=ChamPro]Wireless and Ubuntu just don't mix well right now. It's enough trouble to get a Intel 2200 to work, but these Dell 1350 cards are impossible.

I tried following both sets of directions. The original set conks out on the "cat" command. If I run it in a root terminal, the command screws up all twenty of the .conf files by making them 0 bytes. Following the revised set of directions, I couldn't move the .conf files out of the directory in order to move the saved ones in.

So I'm stuck with unrecognized WiFi... and that crappy "Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted".

Any suggestions?[/QUOTE]

I gave up on Hoary and installed Breezy Colony 3. The instructions provided worked fine this time (and the video drivers work by default!).

The problem I'm having now is that I can't get an IP from DHCP. I've tried through the Gnome network properties and using GTKwifi 1.08.1, but it just fails at securing an IP. "Ndiswrapper -l" shows that they're installed, "dmesg" shows them working with no errors, and "iwlist wlan0 scan" shows the available APs with MAC addresses. However, iwconfig shows my card connected to an access point with no MAC address and DHCP just fails everytime. Hmmm.

---

### Post by cokhavim on 2005-09-01
i'm having problems with the WEP key.  my Broadcom wireless card works great when WEP is disabled on my router (thanks to this great HOW-TO), however, when WEP is enabled, wireless stops working.  

i've tried using "s:" as a prefix to my WEP key (which is just numbers, btw), but it generated this error message:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

i tried putting the key in quotes which did nothing.

i tried setting the keymode to open, and again, nothing.

can anyone help me?  thanks.
jo

---

### Post by cokhavim on 2005-09-01
well, i got it working.  

what did i do?  

drum roll....

i unplugged the router and plugged it back in again.

---

### Post by h17m4n on 2005-09-01
After I finish all the commands and restart, I try to do sudo modprobe ndiswrapper, and I get: FATAL: Module ndiswrapper not found.

---

### Post by skirkpatrick on 2005-09-03
If I wasn't going bald before, I certainly am now.  Configuring wifi on my HP Pavilion laptop was a piece of cake.

Okay, I've read every message in this topic and several others as well.  I've followed almost every instruction given and some from links to other webpages.  I've got an Acer 3002LCi with built-in Broadcom wifi.  I have currently:

1) Built ndiswrapper v1.3rc1 and successfully installed it from a .deb (I've also tried v1.2).

2) I have installed the drivers that came with the Windows install and have even installed the ones specified on the ndiswrapper Wiki (currently installed).

3) I've installed acerhk and modprobed it as dictated on the ndiswrapper Wiki.

4) I've modprobed ndiswrapper and added it to /etc/modules.

5) All the .conf files have RadioState|0.

Dmesg looks fine, ifconfig looks fine, iwconfig looks fine.  The problem is that "sudo iwlist wlan0 scan" always reports "no scan results".  It's working fine in Windows, it's almost as if it's not turning on the radio but I can't find anything about turning it on in Linux.

Getting ACPI working correctly wasn't this hard.

---

### Post by JohnRM on 2005-09-05
I've read most of the posts in this topic and many more in other topics.

I still cannot get my wireless card to power on, let alone access the internet. :)

I have a Belkin High-Speed-Mode G Wireless Card 7001, using the broadcom chipset. I have bcmwl5.inf, bcmwl5a.inf, and bcmwl5.sys at my disposal.

Here is the procedure I used:

1. Clean Install of Hoary 5.04
2. Installed ndiswrapper via Synaptic Package Manager
3. Copied bcmwl5.inf and .sys to my desktop
4. Opened a terminal, and executed the code that was described in step 3 of the original HOW-TO
5. When I do a ndiswrapper -l, I get bcmwl5- Invalid driver

6. When I do a modprobe ndiswrapper, I get a failed to insert error, followed by a permission denied or something like that.

After a -m, I reboot, and still the light does not come on my wireless card.

I'm still figuring out the radiostate and new versions of ndiswrapper, but I do NOT have LAN as a fallback, I have only wireless LAN to connect to the internet on that machine. I do have the Ubuntu CD-ROM, and that is how I installed ndiswrapper.

Thanks to anyone who can give me some extra help.

---

### Post by lost.sync on 2005-09-05
just wanted to say thanks.  this actually worked and wasn't 9x more complicated than it needed to be.

just installed ubuntu today.  xp refugee.  tried mandrake/mandriva, linspire (they were giving it away), and fedora core before this, but i think this'll be the one to stick.

---

### Post by lost.sync on 2005-09-05
[QUOTE=JohnRM]I have bcmwl5.inf, bcmwl5a.inf, and bcmwl5.sys at my disposal. [/QUOTE]

i have no idea if this might work for you, but it helped me.  instead of using bcmwl5.inf, try bcmwl5a.inf. doing that made all the difference.

---

### Post by JohnRM on 2005-09-05
[QUOTE=lost.sync]i have no idea if this might work for you, but it helped me.  instead of using bcmwl5.inf, try bcmwl5a.inf. doing that made all the difference.[/QUOTE]
 Yes, I just tried that a few minutes ago.

Here's what my status is now:

When I installed the bcmwl5a.inf driver, -l says the driver is present, and hardware is present. I do a -m, and the light does not come on during boot. When back on the terminal, I type modprobe ndiswrapper, and then it goes to another blank prompt.

After doing a modprobe, the wireless connection appears in Network settings, and I ticked the "this connection is configured box", and filled in my SSID. (I have no WEP key)

Then I activated the connection. It took about 2 minutes to activate. Then I selected in as my default gateway, then pressed okay. It took about 2 minutes again to close. Whenever I come back to network settings, wlan0 is no longer the default gateway.

Still no light on my wireless card, and I cannot access the internet, even though the connection is activated.

One thing though. I have not changed any RadioState options in gedit, mainly because I cannot change permissions to writeable.

Still no connection. :(

---

### Post by skirkpatrick on 2005-09-05
JohnRM, my reply is based on getting wifi to work on my HP laptop, not my son's Acer laptop that I'm still fighting.

1) You should be using sudo with your gedit to change the config files.

2) When my wirelss is active, my LED doesn't come on under Linux.  I think with some laptops, it's not directly controlled by the wifi.

3) I have the same problem with wlan0 not being able to connect even though it is listed as the default gateway.  I always have to deactivate eth0 even if it's not connected.

---

### Post by JohnRM on 2005-09-06
[QUOTE=skirkpatrick]JohnRM, my reply is based on getting wifi to work on my HP laptop, not my son's Acer laptop that I'm still fighting.

1) You should be using sudo with your gedit to change the config files.

2) When my wirelss is active, my LED doesn't come on under Linux.  I think with some laptops, it's not directly controlled by the wifi.

3) I have the same problem with wlan0 not being able to connect even though it is listed as the default gateway.  I always have to deactivate eth0 even if it's not connected.[/QUOTE]
 I fixed the problem. I was doing so many things, I'm not sure which one fixed it! :)

But I'm pretty sure that the best explanation is to use bcmwl5a.inf, then follow the instructions at the beginning of the topic exactly.

I'm wireless now!

---

### Post by anitsirK on 2005-09-11
I just wanted to add another solution to potential problems to this thread.

I followed all of the instructions, and got no errors, until I went to try to ifup wlan0. wlan0 wasn't recognized.  I looked at dmesg's output, and it said something to the effect of:

```

loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
```

So, I looked in KSystemLog and found this:
```

loadndisdriver: load_driver(273): couldn't read conf file 14E4:4320:144F:7050.5.conf for driver bcmwl5 
```

Looked in /etc/ndiswrapper/bcmwl5 and found that 
14E4:4320:144F:7050.5.conf and 14E4:4320:144F:7051.5.conf were both 0 byte files, but 14E4:4320:144F:7053.5.conf looked like it contained useful stuff.  I did the following:

```

ln -b 14E4:4320:144F:7053.5.conf 14E4:4320:144F:7051.5.conf
ln -b 14E4:4320:144F:7053.5.conf 14E4:4320:144F:7050.5.conf

```

That links the two bad/empty files to the good one, and the -b backs up the old ones, just in case.

Rebooted, and did sudo modprobe ndiswrapper.  After that, ifup wlan0 worked perfectly.
 :D

---

### Post by bdwarr6 on 2005-09-11
ok guys i have done every single thing said in this thread and many others, I get no errors, i have eth0 off and wlan0 as primary and on configured my wep is on everything seems fine to me but I get nothing when I do ipconfig just the basic saying nothing connects all the 00,00, (id post exact thing but im no another pc
any ideas please help
Belkin f5d7011 wireless card used the dell drivers

dell latitude c600 laptop
I do have lights on my card
It shows up in network connections

It wont connect to anything, I also find no networks when I do a scan

---

### Post by mwarndt on 2005-09-11
I receive the same error message.  I performed an: sudo apt-get install linux-686.  Then, I rebooted into 686.

 Next, I perfomed a: sudo apt-get install ndiswrapper-utils.  Then, I installed the broadcom driver with: sudo ndiswrapper -i <location of the driver>.  Next, I entered: sudo ndiswrapper -m.  Then, I rebooted.  

After the reboot, I entered sudo modprobe ndiswrapper...without any problems! Yeah! 

Now, I get to the KWifiManager (using Kubutnu), I Scan For Networks, but no networks are found even though I get signal.  I go to Kcontrol via: sudo Kcontrol from the Shell.  I attempt to enable my wlan0, but my wlan0 immediately disables.

I've attempted to ask others on #kubuntu in IRC, but I've received little help other than people telling me to try a different ndiswrapper, which doesn't make much sense to me because ndiswrapper is fine and is doing it's job.  Plus, I've attempted to get "newer" ndiswrappers working without any success.

Please help...I will be forever in your debt!  

 ](*,)

---

### Post by chipotlehero on 2005-09-12
Hi I'm a linux/ubuntu noob but I can follow steps easily and know how to search forums for answers. I've searched the forum and this thread for my problem but it doesnt seem to come up, its probably just a small thing.

I go through all the steops in the first post in the thread and then when I type:

```

sudo modprobe ndiswrapper

```

i get the error:

```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

anyone have any ideas of what I'm doing wrong?

---

### Post by mwarndt on 2005-09-12
I upgraded the kernel using sudo apt-get install linux-686.  I used the ndiswrapper-utils that came with Synaptic/Kynaptic, and I followed the usual steps, and things worked for me when it came to using sudo modprobe ndiswrapper.

---

### Post by hangfire on 2005-09-13
Thanks for the info! I've gotten much further from this page than any other on my D800.

I have a slight correction. The shell snippet:

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

has a problem. It can create 0 byte files. The reason is, the > $confile can be executed before the cat of the file. Thus the redirection zeros the file, shell cats a zero byte file, seds it, and rewrites it as empty.

This only happens some of the time, in my case, usually on the conf file corresponding to my network adapter. It can be fixed by writing to a file in /tmp and then copying that file back to the current directory.

HF

---

### Post by jrzy on 2005-09-20
Guess  [www.ubuntuguide.org/#extrarepositories](www.ubuntuguide.org/#extrarepositories) is down and I need the instructions for step No.2. Can someone help me out ??

---

### Post by skirkpatrick on 2005-09-21
Here's a mirror for the Guide:
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)

---

### Post by tmmuk on 2005-09-25
i followed this guide and after checking sudo ndiswrapper -l it says 

Installed ndis drivers:
bcmwl5 invalid driver!

this is weird as I tried both bcmwl5 and bcmwl5a and they both came on the belkin cd

EDIT: nvm, downloaded the dell driver that was recommended, re installed using bcwml5a then removed bcmwl5

now when I go into KWifiManager it shows my card and its working

however when I scan for networks it doesn't find any even though there is one

---

### Post by rsankuratri on 2005-09-26
I have been trying various distributions on my Inspiron 9100 without luck. That was until I came upon Ubuntu linux and am extremely pleased with it. Configuring the wireless network on my laptop has been the most easiest of all. Here is what I had done...
1. Opened a terminal and copied the windows driver from Dell (R102319) onto the Desktop. (I had extracted the drivers into a folder called R102319).
2.  Entered the followinf command...
     a.  sudo bash
     b.  chmod -R 777 R102319/
3. Installed the default ndiswrapper that comes with the 5.10 distribution
4. Did a cd into the R102319 folder on my desktop and from within that folder (while still in the root terminal from step 2a) gave the following command...
   ndiswrapper -i bcmwl5.inf
  This resulted in output that stated that it was forcing the RadioState from 0 to RadioState 2
6.  Entered the following command
     ndiswrapper -m
7. Opened the network configuration tool from System --> Administration --> Networking and selected wlan0 and configured it as follows...
  a.  On the DNS tab entered the IP of the wreless router (192.168.1.1) 
  b. Selected the Wireless connection and clicked on the properties...
  c. Selected the check box Enable this connection
  d.  Selected the ESSID of my router from the dropdown
  e.  Entered the WEP key  with the Key type as Hexadecimal
  f.  Selected DHCP for the Connection Settings Configuration
  g.  Clliked OK.  The window closed in about 15 seconds
h. Selected the Default gateway device as wlan0 in the Network Settings window and clicked OK. This window lso closed after about 15 seconds also.
8.  Closed all windows and rebooted the laptop...
9.  Opened a browser and started documenting what I did.  :-)

Most of the steps are similar to the re-written procedure on page 4 of this discussion thread.  But I did not go through the hassle of changing the RadioState in the conf files using the looping since it was one automatically for me when I installed the driver.

This is a repeatable procedure since this is the second time I did this.  I had re-installed the Ubuntu 5.10 after a botched effort to install and see Fedora Core 4.  If you have any questions let me know

---

### Post by hangfire on 2005-09-27
[QUOTE=tmmuk]i followed this guide and after checking sudo ndiswrapper -l it says 

Installed ndis drivers:
bcmwl5 invalid driver!
[/QUOTE]

Check and see if that some of the sed'd files are zero bytes long. If they are you are a victim of the bug I noted above.

---

### Post by skirkpatrick on 2005-10-02
My problems are now fixed:  [http://www.ubuntuforums.org/showthread.php?p=383723#post383723](http://www.ubuntuforums.org/showthread.php?p=383723#post383723)

---

### Post by markr on 2005-10-04
Followed the instructions and my wireless network seems to work a treat - thanks for the info.

However,  when I boot my machine now (without a router in sight) my machine hangs for around a minute before continuing.

I assume this is because it's trying to retreive an ip address.  As I use my laptop standalone for alot of the time I was wondering what the best way of avoiding this delay when I'm not actually wanting to connect to the wireless router?

---

### Post by jonny on 2005-10-04
Hit ctrl-c when you get the delay, or set up your network to use static ip addressing.

---

### Post by laforge on 2005-10-04
Ok i get quite a few errors while doing everything.
```

#1
sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.
#2
sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
#3
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4311:1028:0007.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:1028:0007.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0005.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0006.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0005.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0006.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0003.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0004.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0003.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0004.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.conf: Permission denied

```

This is usually what i get.  Got the uninstalling to work this time so i will restart and see what happends.  Will edit if it works.

EDIT: Ok well i tried "sudo modprobe ndiswrapper" after and i got this "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted"

I searched this thread but found no answers.  Right now i am using LAN cable but its really annoying to keep around for school and it has to be positioned right to work.  I would like this to be fixed.  Also i like using Xfce4 but i will use Gnome or KDE to get wireless to work.

---

### Post by drogoh on 2005-10-04
[QUOTE=laforge]
```

#3
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4311:1028:0007.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:1028:0007.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0005.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0006.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0005.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0006.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0003.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0004.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0003.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0004.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.conf: Permission denied

```
[/QUOTE]

You can't pipe something when using sudo.  If you're piping anything and need root, sudo -s and do it again.

By the way, when/if I use sed, I always sed -i'' 's/foo/bar/' file

You don't need to mess with your catting and redirection, or even piping.  My method does everything yours does but without external processes (you can alternately use -i.bak if you so choose, the -i'' means "no backup extension")

By the way, with -i'', that is two single quotes and not one double quote.

---

### Post by laforge on 2005-10-04
Ok thanks but i still have a problem with
```
sudo modprobe ndiswrapper
```

---

### Post by drogoh on 2005-10-04
[QUOTE=laforge]Ok thanks but i still have a problem with
```
sudo modprobe ndiswrapper
```[/QUOTE]

sudo ndiswrapper -m

If that doesn't work, open up /etc/modules in your favorite text editor (under sudo, of course) and add ndiswrapper to the bottom on its own line.

---

### Post by laforge on 2005-10-04
Ok thanks again.  Now in Kwifimanager, it says not connect instead of not activated.  So inprovement.  What do i use to set up my wifi and all that jazz.

---

### Post by laforge on 2005-10-05
Ok when i restarted i noticed, something failed while loading modules.  Taking a closer look, low and behold its ndiswrapper.  So, i need to restart again to see in full detail but a glance go me this

It loaded ndiswrapper, but failed to find device type, and can't find the .conf file.  More in a min.

EDIT: Ok got most of it

It loaded ndiswrapper, but cound not find device type in settings.  Then it said it can't find .conf file, 14E44319:1028:0006.conf

Dunno if that is of any help.

---

### Post by laforge on 2005-10-06
still having trouble and off first page.

---

### Post by hangfire on 2005-10-07
Will everyone PLEASE stop doing this *PLEASE*?

  ** cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile**

Since bash interprets the > when it pleases, which may be FIRST, it can ZERO (empty) $confffile) BEFORE cat gets a chance to spew it! Remember, you are running this on a BASH command line, so even if "cat" comes first and > comes last, BASH is already there, nulling this file.

Yes, I am shouting here! This shell script is BROKEN, the HOWTO needs to be fixed. A fair number of people have GIVEN UP on wireless and/or Ubuntu because of this problem.

When I ran it, some files came out OK, some truncated, some with zero bytes. You know you're a victim if

    **ls -l /etc/ndiswrapper/bcmwl5/*.conf**

shows some zero-byte files.

HF

---

### Post by Jipstyle on 2005-10-07
Woohooo!  

I have created an account simply to be able to post in this thread and thank everyone for their help.  Particular thanks to the OP who started the thread and provided the initial script.

This was not an easy install, and I am not quite a linux n00b.  I've been running Gentoo on my desktop for about 2 years, but I decided I want a 'compile free' distro for my laptop ... enter Ubuntu.

The card that I bought is the newest Linksys .. the WPC54GS w/ SpeedBooster (ooooh ... larger TCP frame .. lol).

I had the devil's own time trying to get it to work.  First, I made the most hilarious error .. I miss typed RadioState as RadioShack ... and that didn't work out so well.

Next, I had the same error some have mentioned about 0 byte .conf files .. I fixed this by NOT forgetting to pipe the output from sed back to the conf files ( > $conffiles does not appear in my browser unless I scroll the embedded text window to the right and I missed it the first couple of times).

Finally, I was stumped so I read the .inf driver file and noticed that the .sys file declared in all caps in the .inf file.  I made a copy of the sys file with the same name but all caps, and badabing badaboom, ndis was properly inserted on reboot.

Now, I just have to configure my settings so my network plays nicely with my laptop.  

Thanks again, all .. you are a credit to the OSS community.

---

### Post by laforge on 2005-10-07
Hangfire do you have a solution to the problem?

---

### Post by Jipstyle on 2005-10-07
A quick fix for the problem is to manually edit the config files rather than using the concatenated sed command.

A more elegant fix is to use the perl command that someone posted in this thread .. I haven't the time to find it myself, but I did see it in this thread.  I didn't test it, but I assume it works.  If someone could test it and let us know, then perhaps the OP could edit his instructions in the first post.

Given the number of people for whom the sed command worked, though, I'm not sure this is a universal problem. Regardless, the perl command should work fine since the perl interpreter (to my knowledge) will not produce the same error as bash.

---

### Post by laforge on 2005-10-08
What file am i suppose to config, and what to?

---

### Post by ifwntrends on 2005-10-08
is there any way to extract the .inf files from the .exe driver istall application?

---

### Post by ifwntrends on 2005-10-08
is there any way to extract the .inf files from the sp21307.exe windows binary?

---

### Post by MetalMusicAddict on 2005-10-08
[QUOTE=ifwntrends]is there any way to extract the .inf files from the .exe driver istall application?[/QUOTE]
The 2 files you need are posted/hosted it this thread. Read through the thread. Theres lots more helpful info than just the 1st post. ;)

---

### Post by Protostar on 2005-10-10
Hello all. I too am having problems with my Broadcom wireless adapter. I've done everything the original poster said, twice over and it still refuses to work. My card is recognized but when I run iwconfig it says PowerMode=Off. I don't know what to do. If push comes to shove, I'll buy a PC wireless network card because I refuse to switch back to windows.

---

### Post by N6REJ on 2005-10-10
For the Belkin F5D7001 with 1101 on the bottom of box 
Broadcom 4306 chipset
use the belkin drivers bcmwl5A.  Also, when I installed it thought it was a firewire device so I had to remove that.  After that change it worked perfectly.  DON'T SKIP THE REBOOT STEP or this won't work.  Just copy them from the windows cd, they are under files/drivers.  You NEED BOTH the 5a.inf & 5a.sys

---

### Post by laforge on 2005-10-10
5a.sys and 5a.inf?  Do you need those?  I have ones without the 5.

---

### Post by hangfire on 2005-10-10
[QUOTE=Remix_88]You don't have to edit all the .conf files by hand. Replace steps 'sudo gedit' and Step 4 with the following...

```
$ sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
```[/QUOTE]

This dumps the edited contents of all the files to standard out.

---

### Post by hangfire on 2005-10-10
[QUOTE=Protostar] I run iwconfig it says PowerMode=Off.[/QUOTE]

To fix this, I had to switch back to Windows temporarily to "Enable" (power on) the WLAN interface, then warm-boot back to Ubuntu. Apparently there is an API to power on some chipsets that is missing in the Linux drivers.

Buying another Wireless Lan adapter is not a bad idea. We need to punish Broadcom for their atrocious lack of support.

HF

---

### Post by hangfire on 2005-10-10
[QUOTE=laforge]Hangfire do you have a solution to the problem?[/QUOTE]

Sorry. Try this:
[B]
cd /etc/ndiswrapper/bcmwl5
for conffile in *.conf; do
sed -e 's/RadioState|1/RadioState|0/' $conffile > /tmp/$conffile
sudo mv /tmp/$conffile .
done[/B]

If sudo works as usual, you should only need to type the password in once. You have to cd to the working directory, or otherwise code the basename of the conf file, so you don't create something like /tmp/etc/ndiswrapper/bcmwl5/*.conf :( 

HF

---

### Post by dizbah on 2005-10-10
All, I haved done every step here and my wireless lite is still not coming on.  Any additional information would be great at this point.](*,)

---

### Post by laforge on 2005-10-10
[QUOTE=dizbah]All, I haved done every step here and my wireless lite is still not coming on.  Any additional information would be great at this point.](*,)[/QUOTE]
I don't have a wirless light, but yea my wireless isn't working.

---

### Post by dizbah on 2005-10-11
all, here is where I stand.  Wireless light still off.

in device manager, it states the following:

Vendor:  Broadcom Corporation
Device: BCM4306 802.11b/g Wireless Lan
Status:  Status
Bus type: PCI

Device: Unknown
Capabilities: Unknown

 ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

Also, I get the following error on modprobe:

 modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686-smp/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


Any help would be great...Thanks

---

### Post by akb on 2005-10-13
howdy guys :-)

well, after studying this thread (and many others) i finally got a step more into it... had the same problems like some others here: i could not activate the chip, which resulted in successfully "running" drivers and modules, but no found networks in range.

i now solved this by using the module "acer_acpi". now i can scan for networks and it shows me my home network correctly. but... i cannot connect to it :-/

any tipps on this? dhclient doesnt receive DHCPOFFERS, also when i restart the router. before you ask: it is configured to broadcast its ssid... ok, otherwise i couldnt even scan for it. nevermind.

but now... what do i have to do to get it running?
i tried by calling iwconfig essid blah; iwconfig enc blah and so on... restarted the pc, called dhclient (see above), tried to set it up in /etc/network/interfaces and so on... i even shut it down and got it up again (ifconfig wlan0 down/up).

any ideas or handy guides? *lol* :-)

edit: uh... now i tried to start the device with "systemsettings" (manager for network and so on on kubuntu/kde) and the notebook got freezed... now for about 3 minutes, dont think it just broadcasts or something.

---

### Post by markr on 2005-10-13
I followed the instructions in this thread (Greate thread by the way!) and after rebooting my machine the wireless light did not come on.

entered "sudo modprobe ndiswrapper" and pop! on came the light.

Only problem is that when I reboot, I have to do the above command again to get my wireless working.  

Is there anyway I can get this to start at boot so I don't have to issue the command every time I start my laptop?

Thanks

Mark.

---

### Post by akb on 2005-10-13
YEEEEHAW
after sleeping a night over it, i got it running. just had to change the wireless_keymode to "open" manually (before it was not set). now i got access and can ping to outside. thx so much hunnys :->

the most funny thing: with windows the led lights up when the chip gets activated. now it flickers at it sends/receives data :D

so... your documentation from this thread + acer_acpi + keymode open = heaven :-)

---

### Post by skirkpatrick on 2005-10-13
[QUOTE=markr]I followed the instructions in this thread (Greate thread by the way!) and after rebooting my machine the wireless light did not come on.

entered "sudo modprobe ndiswrapper" and pop! on came the light.

Only problem is that when I reboot, I have to do the above command again to get my wireless working.  

Is there anyway I can get this to start at boot so I don't have to issue the command every time I start my laptop?

Thanks

Mark.[/QUOTE]


Mark, add the line "ndiswrapper" to the bottom of /etc/modules.

---

### Post by dizbah on 2005-10-13
[QUOTE=markr]I followed the instructions in this thread (Greate thread by the way!) and after rebooting my machine the wireless light did not come on.

entered "sudo modprobe ndiswrapper" and pop! on came the light.
[/QUOTE]

I still get the following when running the above command: 

 sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


What should I do?

---

### Post by dizbah on 2005-10-13
[QUOTE=markr]I followed the instructions in this thread (Greate thread by the way!) and after rebooting my machine the wireless light did not come on.

entered "sudo modprobe ndiswrapper" and pop! on came the light.stalled
[/QUOTE]

I still get the following when running the above command.  My wireless light never comes on, yet the driver is installed and present.  Message:

 sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


What should I do?

---

### Post by skirkpatrick on 2005-10-13
Ndiswrapper isn't getting loaded by the kernel.  Did you build your own kernel or your own copy of ndiswrapper?  Since ndiswrapper is a kernel loadable module, it needs to be built using the the kernel headers of the installed kernel.  If you didn't build either of them but just pulled them from the repositories, they should be in sync.

---

### Post by noelferreira on 2005-10-15
hi, people. i am new and thanks to you i almost have my wireless wlan0 card working. i have a compaq presario 1200 and an asus wl100g network pcmcia wireless card. i follow you instructions and i am connected to my router. 
when i do ping 192.168.1.1 (router) everything is ok.

however i cannot browsing any site in the internet. doing ping [www.xxxxx.com](www.xxxxx.com) the packets are sended, no one is lost, but i don't receive it back.

sometimes i can open some pages but it is just for a few seconds.

can you help me?
thanks,

noel ferreira

---

### Post by triviab0y on 2005-10-17
Noel

A few things to check:

1. Make sure you have a DNS entry so that you can resolve names to IP addresses. You can configure this in the network configuration applet in the "DNS" tab. Or you can do this manually by editing /etc/resolv.conf. Add the DNS servers given to you by your ISP.

2. Try bringing down any other network interfaces you might have, eg eth0. From the command line type: sudo ifdown eth0

Hope that helps.

Trivab0y

---

### Post by skirkpatrick on 2005-10-17
Yes, wlan0 won't work correctly if eth0 is enabled.

---

### Post by MetalMusicAddict on 2005-10-17
[QUOTE=noelferreira]hi, people. i am new and thanks to you i almost have my wireless wlan0 card working. i have a compaq presario 1200 and an asus wl100g network pcmcia wireless card. i follow you instructions and i am connected to my router. 
when i do ping 192.168.1.1 (router) everything is ok.

however i cannot browsing any site in the internet. doing ping [www.xxxxx.com](www.xxxxx.com) the packets are sended, no one is lost, but i don't receive it back.

sometimes i can open some pages but it is just for a few seconds.

can you help me?
thanks,

noel ferreira[/QUOTE]
I would make sure you MAC address is being allowed access.

---

### Post by anonOmus on 2005-10-19
Thanks for the howto took ten minutes and now my little light is glowing and i can see my wireless card in the system.  Just one problem now; will a sumbler program work with ndis wrappers? I have about 10 different wireless networks on  my univeristy campus and I just want my machine to search for them and not have to talk to the admins to get all the ips and the rest of the crappola. Is there any way to do this while running ndis wrappers?

---

### Post by akb on 2005-10-19
afaik the ndiswrapper seems to your kernel like any other module ("driver"), so it should also be handled the same way.

did you configure everything manually? i just used dhclient and the config where i had to put the essid and all this... (what should be handable with an external app)

---

### Post by triviab0y on 2005-10-19
Anon

Kismet (Linux wifi scanner [http://www.kismetwireless.net/](http://www.kismetwireless.net/)) will not work with ndiswrapper, sadly. The card needs to be put into monitor mode (RFMON) which requires direct access to the hardware. Check out [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml) for supported cards.

Triviab0y

[QUOTE=anonOmus]Thanks for the howto took ten minutes and now my little light is glowing and i can see my wireless card in the system.  Just one problem now; will a sumbler program work with ndis wrappers? <snip>[/QUOTE]

---

### Post by anonOmus on 2005-10-19
Thanks triva I had a feeling that was the case Damn! Well i suppose I can be still be happy. My machine is a 10 pound plus desktop replacement and rarel gets lugged around the university.

Thnx 

N

---

### Post by Eagleevil on 2005-10-19
I tried asking in another thread but got nothing, so maybe someone that looks at this one might have something.

I've been trying for a few days now to get my wireless card fully working and I'm having some trouble. I've tried the directions in this thread and still not working. I got the drivers working with ndiswrapper and so forth. 

My problem is when I try to set the essid and other stuff, it just doesn't take. What I put in doesn't show up at all, except I actually got the key to get set, but nothing else. 

Anyone know possibly how to fix this? If you need to know anything else, let me know.

---

### Post by triviab0y on 2005-10-20
Eagle

What sort of system are you running? If its a laptop, is there a key combo or switch that enables the hardware? Make sure its enabled! 

Other than this, do you get any errors? What hardware are you using? What have you tried?

Trivab0y

[QUOTE=Eagleevil]I tried asking in another thread but got nothing, so maybe someone that looks at this one might have something.

I've been trying for a few days now to get my wireless card fully working and I'm having some trouble. I've tried the directions in this thread and still not working. I got the drivers working with ndiswrapper and so forth. 

My problem is when I try to set the essid and other stuff, it just doesn't take. What I put in doesn't show up at all, except I actually got the key to get set, but nothing else. 

Anyone know possibly how to fix this? If you need to know anything else, let me know.[/QUOTE]

---

### Post by Eagleevil on 2005-10-20
Yes, it's a laptop and there is no key combination or anything to enable it.

The card is a Linksys WPC45G and as far as I can find no errors, but maybe I'm not looking in the right place.

I've tried other drivers, and searched mutliple times to see what others have done and tried those things and always end up with the same problem it seems.

Could it possibly be that it is trying to use it as something else so there is some other program or whatever using it and therefore not letting me use it? If so how can I check this for sure?

---

### Post by Tsume on 2005-10-21
Great guide!  Only issue is I had to use this:

"cd /etc/ndiswrapper/bcmwl5
for conffile in *.conf; do
sed -e 's/RadioState|1/RadioState|0/' $conffile > /tmp/$conffile
sudo mv /tmp/$conffile .
done"

Instead of what was in the original post (otherwise I got a bunch of Permission Denied).

Now I've got a new problem and I'm hoping someone's got an idea.

Every time I have to reboot now, it takes 5-10 minutes to boot, and almost all of that time is spent on the stage configuring network interfaces and waiting for network interfaces to come up.  When it finally boots, everything's working great.  Any ideas?  I use about 20% of my battery waiting for this thing to boot up.

---

### Post by skirkpatrick on 2005-10-21
I have the same problem and haven't quite figured out how to fix it, although there is a thread around hear about disabling ntp on startup but I'd like to have ntp later.  While it's waiting, I just hit Ctl-C and it continues on.

---

### Post by noelferreira on 2005-10-22
[QUOTE=triviab0y]Noel

A few things to check:

1. Make sure you have a DNS entry so that you can resolve names to IP addresses. You can configure this in the network configuration applet in the "DNS" tab. Or you can do this manually by editing /etc/resolv.conf. Add the DNS servers given to you by your ISP.

2. Try bringing down any other network interfaces you might have, eg eth0. From the command line type: sudo ifdown eth0

Hope that helps.

Trivab0y[/QUOTE]

thanks for help,

could you be more spcecific? how can i get that DNS servers?

in fact, i am trying to intall debian sarge 3.0 in my laptop (netinstaller version). when it tries to reach security.debian.org and other times the mirroir  i use to get packages, it fails. Most of times the system can't bring up eth0. 

i am using a wireless router (modem). it is strange. i live in portugal. if i do for example $ ping [www.uevora.pt](www.uevora.pt), everything ok. for example, $ ping [www.record.pt](www.record.pt) fails. some pings works and other, mostly, don't. there's something to do with the router?

i will give you my msn nick for a faster help if that is possible, of course.

[email]noel@oniduo.pt[/email]

thanks for your help,
best regards, 

noel ferreira

---

### Post by Eagleevil on 2005-10-23
Well now I have a different problem I guess...

For some reason I can now connect using wireless and I don't really know why it's working now. But I can't seem to connect to a router that is using a WEP key, though I've only tried one router with WEP so far. 

Could it just be that one router? I will probably have a chance to try another router sometime this week on campus.

If I have the same problem on campus, anyone know a way to fix this? or is it some problem that just exists right now with really no fix?

---

### Post by cajunaggie on 2005-10-30
I'm running a WinXP-Badger dual-boot. I installed a Belkin Wireless G USB network adapter, but Badger won't recognize it, even during installation. I did a file search in XP for the bcmwl5a.inf and bcmwl5.inf files. I found nothing. Does this mean I don't have a Broadcom chipset in the Belkin adapter? Where can I go to find out who makes the chipset for the adapter?

---

### Post by seismicmike on 2005-10-31
DUDE, You are my HERO!!! You should add this to the Wiki!!

---

### Post by adumas on 2005-10-31
Thank you!

---

### Post by Fiction on 2005-10-31
[QUOTE=Tsume]

Now I've got a new problem and I'm hoping someone's got an idea.

Every time I have to reboot now, it takes 5-10 minutes to boot, and almost all of that time is spent on the stage configuring network interfaces and waiting for network interfaces to come up.  When it finally boots, everything's working great.  Any ideas?  I use about 20% of my battery waiting for this thing to boot up.[/QUOTE]


What I found I had to do was to disable the ethernet interface (eth0) in order to boot more quickly.

To do this run ```
sudo network-admin
```
Then select your ethernet device and click the properties button.  On the next screen you will see a box that says "Enable this connection".  Unchecking that box is all I did to speed up my booting.

I had the "Default Gateway Device" set to wlan0 and still had the long booting until I disabled eth0.

I am guessing the delay is because the system is trying to connect using eth0 and eventually times out and then tries to connect using wlan0 and connects right away.  I could be completely wrong about that but it removed the huge delay from my boot times!

---

### Post by StaticBoy on 2005-11-03
Thanks! Only my second day using Ubuntu (or Linux for that matter) and this forum is a goldmine.

I had a couple of problems setting up my BT Voyager 1060 PCMCIA card, so I though I'd share my experiences getting things to work.

First off, the instructions in Step 2 of the original HOW TO [How to add extra repositories]("http://ubuntuguide.org/#extrarepositories") relates to Ubuntu 5.04, so for 5.10 the name needs changing from "hoary" to "breezy". Also, from what I can tell, there isn't a "breezy-backports"  yet at either [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) or [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) (although I did notice "breezy-backports-staging"). This led to an error when executing
```
sudo apt-get update
```
until I replaced the commenting in /etc/apt/sources.list file for the backports section.

Next, it was a complete pain getting the bcmwl5.inf and bcmwl5.sys files. This is because they were buried away inside a Windows Installer executable [BTVoyager1060.exe]("http://www.voyager.bt.com/1040_1060/downloads/BTVoyager1060.exe"), so I had to run the install on a Windows system to get the files (thanks BT for being so open-minded and only supporting  Microsoft OS's). I've attached the both files in the archive BTVOYAGER1060_bcmwl5.tar.gz.

The only other issue was that my router (BT Voyager 2100) was set to use WPA-PSK protection, which was OK with Windows, but not with Ubuntu. The router offers both 64-bit (which I'm using) and 128-bit (not tested) WEP, so once the changes were saved wifi worked first time! Ubuntu offers the option to enter your WEP key as either a ASCII or hex (nice).

I can also report that the signal strength doesn't work, it always reads 100%, and that disabling eth0 chops off about 2-3 minutes of boot time.

Hope that helps all the other Day 2 Newbies crying over their inoperative WiFi!

---

### Post by Maverick911 on 2005-11-09
My problem is getting the wireless to start up by itself at boot. I have an HP zx5000 with integrated Broadcom BCM4306 wireless. I have been able to get it working with the latest driver from HP's website and ndiswrapper1.5 from the terminal.

I have done

```
ndiswrapper -m
```


After a reboot

```
lsmod -l
```

shows that ndiswrapper is loaded.

```
iwconfig wlan0
```

shows no WEP or key or essid assigned even though I have entered them in network settings properties for wlano and in /etc/network/interfaces.

This is what it iwconfig shows immediately after startup

```
wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.462 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```


If I enter “iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX” at the command line and then iwconfig the connection comes up.(Sometimes)

```
wlan0 IEEE 802.11g ESSID:"Wireless100"
Mode:Managed Frequency:2.437 GHz Access Point: 00:09:5B:E9:B0:78
Bit Rate:11 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX Security mode:open
Power Management:off
Link Quality:100/100 Signal level:-71 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```


I then have to go back into network settings and set Default gateway device to wlan0 and disable eth0. (It always defaults to eth0)

I've set wlan0 up with a static IP address in System>Administration>Networking and entered the WEP key and essid.

Here is what's entered in /etc/network/interface

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0


iface eth0 inet static
address 192.168.1.13
netmask 255.255.255.0
gateway 192.168.1.1


# The primary network interface
iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Wireless100
wireless-keymode open
wireless-key open




auto wlan0


```

Although I can eventually get the wireless working by activating, deactivating, reactivating, rebooting, iwconfig wlan0 key, default gateway device...etc,etc, I'd like it to “just work”.

Any suggestions would be deeply appreciated.

**I Think I've fixed it!**
My Netgear router is set to WEP open mode, not restricted. There is no way to specify mode in System>Administration>Networking (It defaults to restricted) so you need to set it in /etc/network/interfaces.
The problem was those 2 lines in /etc/network/interfaces that say:

wireless-keymode open
wireless-key open

I had edited this file and entered my wireless WEP key XXXXXXXXXXXXXXXXXXXXXXXXX.
I had also entered the key and essid in System>Administration>Networking

The problem was that when the interface is activated the line wireless-keymode open would change the key from it's previous setting to "open" in both the interfaces file and the in the System>Administration>Networking wlan0 properties dialog.

With some trial and error of different commands in different orders, it is working on bootup now.
Here is what finally worked for me in the interfaces file.
```
# The primary network interface
iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key open XXXXXXXXXXXXXXXXXXXXXXXXXX (insert your WEP key here)
wireless-essid Wireless100 (replace Wireless100 with the essid of your network)

```
Remember, this assumes that you've got ndiswrapper module loading at boot and the proper drivers.

I apoligize if my explanation isn't all that clear. I'll try to write a howto that goes into detail and is laid out clearly like the original post here was. Thanks to all who's help I've read.

Wish You Were Here – Pink Floyd

---

### Post by hadelikaruna on 2005-11-09
Hello, hello.. 

Is there anybody who can help me with this kernel crash problem ? I have just bought a Belkin wireless PCMCIA. This is the result of the lspci:

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Then, I followed the whole steps to install the ndiswrapper. At the end, I did modprobe ndiswrapper. What happened next was the light at my PCMCIA card turned on, however the computer still doesnt detect my wireless card. Then I do dmesg, and I found out that my kernel crash with the wireless driver, 

This is part of the dmesg log. 
---
> 
[4295279.550000] ndiswrapper version 1.5 loaded (preempt=no,smp=no)
[4295279.575000] ndiswrapper: driver bcmwl5a (Belkin,02/19/2004, 3.50.21.11) loaded
[4295279.576000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[4295279.576000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4295279.576000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4295279.584000] ndiswrapper: using irq 11
[4295279.729000] Unable to handle kernel NULL pointer dereference at virtual address 00000001
[4295279.729000]  printing eip:
[4295279.729000] e0ce6018
[4295279.729000] *pde = 00000000
[4295279.729000] Oops: 0000 [#1]
[4295279.729000] Modules linked in: ndiswrapper rfcomm l2cap bluetooth speedstep_ich speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative pcmcia i915 drm video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac ipv6 af_packet floppy pcspkr rtc yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc tpm_atmel tpm_nsc tpm pci_hotplug intel_agp agpgart nls_iso8859_1 nls_cp437 vfat fat dm_mod joydev tsdev evdev psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan usbhid 3c59x mii uhci_hcd usbcore ide_disk ide_generic piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4295279.729000] CPU:    0
[4295279.729000] EIP:    0060:[<e0ce6018>]    Tainted: P      VLI
[4295279.729000] EFLAGS: 00010202   (2.6.12-9-386)
[4295279.729000] EIP is at 0xe0ce6018
[4295279.729000] eax: cd558b88   ebx: d8531c98   ecx: 00000002   edx: 00000000
[4295279.729000] esi: c8926004   edi: c8926768   ebp: d8531ca0   esp: d8531c24
[4295279.729000] ds: 007b   es: 007b   ss: 0068
[4295279.729000] Process loadndisdriver (pid: 8026, threadinfo=d8530000 task=d098b020)
[4295279.729000] Stack: c89260f8 c8926004 00000000 00000000 00000000 dcbabfa0 00000086 d7224588
[4295279.729000]        00000246 d8531c68 c0112cf8 d7224590 00000003 00000001 00000000 00000086
[4295279.729000]        c89f464c d8531cc8 000a0008 e0ce5d30 00120010 e0ce5d3c 00180016 e0ce5d18
[4295279.729000] Call Trace:
[4295279.729000]  [<c0112cf8>] __wake_up+0x14/0x1e
[4295279.729000]  [<e0c9ca4f>] miniport_init+0xee/0x16e [ndiswrapper]
[4295279.729000]  [<e0c9d789>] ndiswrapper_start_device+0x1a/0x469 [ndiswrapper][4295279.729000]  [<c0115742>] call_console_drivers+0xd3/0xdb
[4295279.729000]  [<c0115a68>] release_console_sem+0x2c/0x87
[4295279.729000]  [<c01159c4>] vprintk+0x1b1/0x1c2
[4295279.729000]  [<c01159c4>] vprintk+0x1b1/0x1c2
[4295279.729000]  [<c020b666>] pci_read+0x22/0x26
[4295279.729000]  [<c019fccb>] pci_bus_read_config_word+0x2f/0x43
[4295279.729000]  [<c01a10e7>] __pci_bus_find_cap+0x24/0xc1
[4295279.729000]  [<c01a119c>] pci_find_capability+0x18/0x1c
[4295279.729000]  [<c01a1306>] pci_set_power_state+0x3d/0x147
[4295279.729000]  [<e0c8f980>] ndiswrapper_add_pci_device+0x14d/0x1b5 [ndiswrapper]
[4295279.729000]  [<c01a2cdd>] pci_device_probe_static+0x2e/0x41
[4295279.729000]  [<c01a2d0f>] __pci_device_probe+0x1f/0x32
[4295279.729000]  [<c01a2d3e>] pci_device_probe+0x1c/0x31
[4295279.729000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4295279.729000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4295279.729000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4295279.729000]  [<c01ec7a5>] driver_register+0x23/0x25
[4295279.729000]  [<c01a2f01>] pci_register_driver+0x5f/0x72
[4295279.729000]  [<e0c909e6>] register_devices+0x393/0x4ab [ndiswrapper]
[4295279.729000]  [<e0c90b34>] wrapper_ioctl+0x36/0xaa [ndiswrapper]
[4295279.729000]  [<c0152fd8>] do_ioctl+0x48/0x4e
[4295279.729000]  [<c0153233>] vfs_ioctl+0x172/0x17f
[4295279.729000]  [<c0153286>] sys_ioctl+0x46/0x60
[4295279.729000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4295279.729000] Code: 54 07 00 00 00 80 be 2f 07 00 00 00 74 60 6a 02 8d 45 cc 50 ff 75 fc 8b c6 8d 5d f8 e8 68 ec ff ff 84 c0 74 42 8b 45 f8 8b 50 08 <80> 7a 01 00 8d be 34 07 00 00 8b cf 75 0e 0f b7 40 04 6a 20 50
[4295279.729000]  <3>ndiswrapper (wrapper_init:1830): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'


Is there anybody who know how can I fix this problem ? I have tried to browse, and did something for 3 hours, and I got no result. What a stressful job. I am very appreciate if anybody can help me. Please accept my gratitude for the help. 

Regards,

---

### Post by hadelikaruna on 2005-11-10
I have solved the problem by uninstalled the ndiswrapper 1.5 and changed it to ndiswrapper 1.1.

This site is very helpful. 
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

Thanks a lot to the writer.

---

### Post by daller on 2005-11-10
This is the repo-version in dapper...

Is it ok???

daniel@dallap:~$ sudo apt-cache show ndiswrapper-utils
Package: ndiswrapper-utils
Priority: optional
Section: misc
Installed-Size: 128
Maintainer: Andres Salomon <dilinger@debian.org>
Architecture: i386
Source: ndiswrapper
Version: 1.1-4ubuntu2
Depends: libc6 (>= 2.3.4-1), perl, ndiswrapper-modules-1.1
Suggests: ndiswrapper-source
Filename: pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb
Size: 25676
MD5sum: a2f339da1c7aca7e8747c54be6879259
Description: Userspace utilities for ndiswrapper
 Some wireless LAN vendors refuse to release hardware specifications or
 drivers for their products for operating systems other than Microsoft
 Windows. NdisWrapper makes it possible to use such hardware with Linux by
 means of a loadable kernel module that "wraps around" NDIS (Windows network
 driver API) drivers.
 .
 This package contains the userspace tools. The default Ubuntu kernel
 already provides the required modules. If you use a custom kernel,
 you might also need the kernel module package.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

daniel@dallap:~$

---

### Post by evilberg on 2005-11-12
I can't get this too work.
I suspect it's because I had wlan disabled when i threw windows out and installed ubuntu.

If someone could help i'd really appreciate it.

I have set the RadioState|0, compiled my own ndiswrapper-modules and utils (version 1.5).

```
berg@lappyn:~$ dmesg | grep ndiswrapper
[17179582.956000] ndiswrapper version 1.5 loaded (preempt=no,smp=no)
[17179583.136000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179583.148000] ndiswrapper: using irq 10
[17179584.152000] wlan0: ndiswrapper ethernet device 00:0e:9b:cc:a8:e7 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
```

```
berg@lappyn:~$ dmesg | grep wlan0      
[17179584.152000] wlan0: vendor: ''
[17179584.152000] wlan0: ndiswrapper ethernet device 00:0e:9b:cc:a8:e7 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
[17179584.152000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179676.268000] wlan0: no IPv6 routers present
```

```
berg@lappyn:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```

```
berg@lappyn:~$ sudo iwconfig wlan0
Password:
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm unable to change essid, channel e.t.c. Only thing I could change was power wich didn't do any difference. Weird thing is it does not return any error when doing "sudo iwconfig wlan0 essid <essid>" e.t.c.

```
wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:CC:A8:E7  
          inet6 addr: fe80::20e:9bff:fecc:a8e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:c0204000-c0205fff
```

```
berg@lappyn:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

Anyone have any idea what could be wrong?

Oh and I'm sry, did't see this was under hedgehog. If it matters I'm using breezy badger 5.10

---

### Post by bbruecker on 2005-11-14
Everything is working fine, but after every startup I have to do "modprobe ndiswrapper". Modeprobe -m didn't help to start the driver automatically. Can somebody help?
System: Dell Latitude 600, 
Network:  Broadcom 1350
Thanks, Benjamin

---

### Post by daller on 2005-11-14
[QUOTE=bbruecker]Everything is working fine, but after every startup I have to do "modprobe ndiswrapper". Modeprobe -m didn't help to start the driver automatically. Can somebody help?
System: Dell Latitude 600, 
Network:  Broadcom 1350
Thanks, Benjamin[/QUOTE]


Did you add "ndiswrapper" to the bottom of /etc/modules ???

---

### Post by bbruecker on 2005-11-15
Thank you Daller! Benjamin

---

### Post by TMG on 2005-11-17
im getting this error, i dunno whats going on...

```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

---

### Post by daller on 2005-11-18
[QUOTE=TMG]im getting this error, i dunno whats going on...

```

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```[/QUOTE]

It's obviously a permission error!

Did you remember to add "sudo" to the start of the command?

---

### Post by 11hjpphty76lkjj on 2005-11-19
I don't mean to be rude, but I don't believe his problem is a permissions issue.  I've been working with the wifi and a broadcom device all day today and finally got it working.  I ran into the exact same issues, and this is what I did to fix it.  I actually believe this error is some sort of compatibility issue with ndiswrapper and the kernel or something is broke in the Ubuntu ndiswrapper package.  But I could be wrong.

Steps:

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Install the kernel-headers for your kernel.  If you don't know what kernel you are using, type:
uname -a
then using synaptic (or apt-get if you prefer, search for the kernel-header that matches your kernel.
then,
sudo apt-get install gcc-3.4

Copy the bcmwl5.inf and bcmwl5.sys files to your desktop, or some location that you know where it is.

(I actually needed to use the bcml5a.inf, which took some searching to figure out, take that into consideration..maybe download both and have them both ready. If when you do a ndiswrapper -l )

Go here and download/complile then install the 1.5 release of ndiswrapper
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)
Download the 1.5 tarball
tar xvfz <file_name_here>
cd <file_dir>
sudo make
sudo make install

sudo ndiswrapper -i <dir_of_file>/bcmwl5.inf  

ndiswrapper -l

This steps IS most important, check and make sure the result is something like:

Installed ndis drivers:
bcmwl5a         driver present, hardware present

If it's not, you probably have the wrong driver, so don't waste any more time doing any other steps.  It MUST say the above to work correctly.  If you just tried the bcml5.inf and it didn't work you may need the bcml5a.inf driver.  Always check this step, else you would be wasting your time and energy.  Make sure the driver sees the device.

Then:

sudo ndiswrapper -m

Then:

sudo modprobe ndiswrapper

The next step is just as important as all the others, it wont work until you do it:

Go to the system, admin, networking, and enable, configure your wifi device and activate it.  deactive your eth0 connection.  (i'm assuming you just want to use the wifi..)

And it should now be working.

Can we update the how to?  It IS a good how to, but it's only a partial.  All steps to perform a function should always be included.  Like the steps for enabling the device and such, they should be part of the how to. INV.

And my wifi now is working!  Sorry if I'm not clear, let me know if there are any questions.  It's been a long day. :)

I've tested this several times on breezy and it works everytime for me.

Aaron

---

### Post by TMG on 2005-11-19
im going to give this a shot man, for the time being anyhow, i broke down and ordered an ORiNOCO Gold WiFi Card...hehe...thanks a ton!

---

### Post by TMG on 2005-11-19
here is what i get when trying to compile ndiwrapper

```

roger@rabbit:~/ndiswrapper-1.5$ sudo make
make -C driver
make[1]: Entering directory `/home/roger/ndiswrapper-1.5/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/roger/ndiswrapper-1.5/driver'
make: *** [all] Error 2

```

---

### Post by TMG on 2005-11-19
man, one thing after another, so i got all that squared away, installed the driver, everything looks good but when i modprobe i get this

```

roger@rabbit:~$ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/misc/ndiswrapper.ko): Invalid module format

```

---

### Post by 11hjpphty76lkjj on 2005-11-20
Did you reboot?  If not try restarting then giving that another shot..

Aaron

---

### Post by cayblood on 2005-11-24
Thanks for a great HOWTO.  Worked perfectly for me.  Now that I've finished the installation, can I delete the .inf and .sys files from my desktop?

---

### Post by punkr0x on 2005-11-25
Sweet!  After much configuration, removal and reconfiguration, I got my wireless card working on my compaq presario V2000 using this guide.  BUT...

I have disabled WEP.  I dunno if I was entering it in the appropriate format or what.  In the network settings panel, for my wlan0 card (ubuntu 5.10), do I enter my WEP key as (Hexadecimal) XXXXXXXXXX.... or (hexadecimal) XX:XX:XX:XX:XX:XX:XX..... or in some completely different form than the two I have been (unsuccessfully) trying?

Also I should note that it seemed like I had to restart the laptop AFTER making configuration changes to the wireless router.  I set my ESSID broadcast to on, but the laptop still could not see the router using

iwlist config

until after I rebooted.  Maybe that is part of my WEP problem, I will keep playing with it!

---

### Post by stylesuxx on 2005-11-27
Hi @ all! 
so, now i`ve spent the whole weekend trying to install my wlan but no way!
I`m really going mad now!

I`ve done everything what was described in the howto and tried some of the other things that were suposed, but with no effect!

the wireless connection is displayed in the networking screen, but when i do a scan i find nothing, i disabled wep.

stylesuxx@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     No scan results

stylesuxx@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


if there is something else you need to know please tell me!
i`m really going nuts.


chris
sorry for my bad english

---

### Post by Eagleevil on 2005-11-27
I have compiled and installed the 1.5 release of ndiswrapper.
I got the driver installed as well and the it says driver and hardware are present.

I can't seem to get it to connect and when I run iwconfig I get

Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

I get the same thing when I try to do: iwlist wlan0 scan
and it says No scan results

I have tried the version of ndiswrapper that can be installed with apt-get before and scan would work but I wouldn't be able to connect to anything so I thought I would try the newest release.

Anyone know what the problem is and how to fix it?

---

### Post by ErikTheRed on 2005-11-30
I follow kalosaurusrex's guide, and i got to the point where i modprobe the ndiswrapper driver and i get this:

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-amd64-k8/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


Any ideas?

EDIT: Figured it out. I had to use the 64-bit broadcom driver

---

### Post by schwascore on 2005-12-06
I successfully followed the guide with no problems at all, but my wireless card will not show up in System --> Administration --> Networking or under ifconfig.

ndiswrapper -l shows:
Installed ndis drivers:
bcmwl5  driver present, hardware present

I have found no errors at all, yet my wireless card does not show up.  Any help would be greatly appreciated!

---

### Post by 11hjpphty76lkjj on 2005-12-06
Did you reboot? also did you perform these functions?

Then:

sudo ndiswrapper -m

Then:

sudo modprobe ndiswrapper

Are the lights on your wifi card active?

Aaron

---

### Post by schwascore on 2005-12-06
Thanks for the response -

Yes, i did reboot and run those commands.

My wifi card does not have lights because it is embedded in my laptop.

I ran through the listed proceedure three full times without running into any errors, however the card still does not show up.

Any other suggestions?

---

### Post by 11hjpphty76lkjj on 2005-12-06
I'm assuming it worked with windows?

What's the model of the laptop/wnic?  Can you try the bcmwl5a.inf driver?

Aaron

---

### Post by bribera on 2005-12-06
Hello Everyone-

I noticed this on digg.com:
A group has been working on reverse engineering the driver for cards based on the broadcom 43xx chip, and they've recently released it.  I'm going to test it out on my Linksys card tonight... but I thought others might be interested in seeing if they can get a working driver without needing ndiswrapper.

**[SIZE=3] Some Options:[/SIZE]**

**Main Site:**
[http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/")

** Checkout SVN repository:**
svn checkout svn://svn.berlios.de/bcm43xx/trunk

** Daily snapshots are available at:**
[ftp://ftp.berlios.de/pub/bcm43xx/snapshots/]("ftp://ftp.berlios.de/pub/bcm43xx/snapshots/")

** Project Specifications:**
[http://linux-bcom4301.sourceforge.net/]("http://linux-bcom4301.sourceforge.net/")

It would be really cool if this proves to be a viable alternative to ndiswrapper!

---

### Post by schwascore on 2005-12-06
Thanks for the help,  I needed the other driver.

---

### Post by wish on 2005-12-07
great How-to, work perfectly on my dell inspiron 5160. 

Thank you very much.

---

### Post by asad112 on 2005-12-10
I am running an Hp Pavillion ze4900. I already have ndiswrapper installed. Can anyone point to where i need to go from here to get my wireless to work?

---

### Post by evilberg on 2005-12-10
I had it working!
Hadn't gotten it to work so i gave up. Some week later i thought i'd give it another try.
Found a page wich said i should use autowlan=1 poll=0 force_series=5020 verbose=3 usedritek=1 when modprobeing acerhk. Compiled my own ndiswrapper and sure as hell it worked.
Next day it was gone again. My light on the laptop is lit and i can use iwlist scan and find aps. But i can't add essid as before. This is really starting to be anoying.

Anyways, for you with acer laptops who can't enable the wlan card. Do this:
Compile acerhk. Modprobe with
sudo modprobe acerhk autowlan=1 poll=0 force_series=5020 verbose=3 usedritek=1

force_series doesn't have to be used anymore i think but.. Good luck

---

### Post by linguizic on 2005-12-11
I've done everything in this howto and it still doesn't work.  There is nothing in the output for iwconfig.  When more run 'more /etc/modprobe.d/ndiswrapper' the output is: "alias wlan0 ndiswrapper".  An interesting note: All the RadioState keys were already set to RadioState| 0.  I tried setting them all to 1, but that didn't work.  Does anyone have any clue as to what's going on here?

BTW- is it necessary to have both the bcmwl5.inf and bcmwl5.sys on your desktop?  It doesn't appear that anything gets done to the .sys.  I don't have it on my desktop, maybe I'll try it.

---

### Post by evilberg on 2005-12-12
[QUOTE=linguizic]I've done everything in this howto and it still doesn't work.  There is nothing in the output for iwconfig.  When more run 'more /etc/modprobe.d/ndiswrapper' the output is: "alias wlan0 ndiswrapper".  An interesting note: All the RadioState keys were already set to RadioState| 0.  I tried setting them all to 1, but that didn't work.  Does anyone have any clue as to what's going on here?

BTW- is it necessary to have both the bcmwl5.inf and bcmwl5.sys on your desktop?  It doesn't appear that anything gets done to the .sys.  I don't have it on my desktop, maybe I'll try it.[/QUOTE]

Afaik you don't have to save the .sys-files. And yeah it was changed to 0 for me to. Have tried 1 and 2 both disables the wlan completly.

I have notices something else about IRQ. Can this have anything to do with the card not working?

```

[17179585.932000] ndiswrapper version 1.6 loaded (preempt=no,smp=no)
[17179586.052000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179586.052000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[17179586.052000] ACPI: PCI Interrupt 0000:06:05.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[17179586.060000] ndiswrapper: using irq 10

```

---

### Post by galderz on 2005-12-15
Just registered and this is my first post:

installed linux for the first time ever yesterday and managed to get the wireless network card working the second time around!

thanks for this excellent how-to.

i'm loving ubuntu!

---

### Post by grsing on 2005-12-15
Argh, I had it working this morning, now it seems to be working, except I can't get it to connect to any APs.  Here's the output of iwconfig, if it helps:

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any suggestions?  If you need any more information, I'm happy to oblige (it's a Dell D600 with the Dell 1300 Broadcom chip).  Thanks!

PS:  WiFi Radar doesn't seem to be picking up any APs, either (I know they're out there).


Edit: Solved, I'm just stupid and didn't realize that at some point I had turned off the wireless while in Windows.  Works now, thanks anyway, and thanks for the great howto!

---

### Post by aredridel on 2005-12-27
[QUOTE=jonny]```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```[/QUOTE]

Close! The rewriting of the config files doesn't work since sudo only applies to the cat command, not the whole pipeline. More easily:

```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo sed -i -e 's/RadioState|1/RadioState|0/' $conffile
done
```

The -i means "in-place edit", and is possibly sed's coolest trick.

To make the driver load at every boot, add "ndiswrapper" to the list in /etc/modules --

```
sudo gedit /etc/modules
```

and add just "ndiswrapper" at the end of the list.

---

### Post by rajesh.balu on 2006-01-02
I performed all of the steps but couldn't get my card to work. In the Admin->Networking box, I dont see an entry for wlan0. When I do 
sudo ndiswrappler -l
I get: bcmwl5 Invalid driver!
When I try to start over by cleaning up with this:
sudo modprobe -r bcmwl5
I get: FATAL: Module bcmwl5 not found.
ANy ideas? Anywhere else I can check for any logs?

---

### Post by 11hjpphty76lkjj on 2006-01-03
Have you tried to use the bcmwl5a driver?  Sounds like your card doesn't like the bcmwl5 driver.

---

### Post by killab on 2006-01-03
:D :D :D :D :D 

[SIZE="4"]Thank you!!!![/SIZE]
[SIZE="4"]Thank you!!!![/SIZE]
[SIZE="4"]Thank you!!!![/SIZE]
[SIZE="4"]Thank you!!!![/SIZE]
[SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE]
[SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE][SIZE="4"]Thank you!!!![/SIZE]

I feel a little newbish for not figuring out this part

```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

I was never prompted for the password and I was denied access.
I needed to su in to a root console first in order for it to work.

But after that little hurdle.... SUCCESS!!!!


Thanks again.

---

### Post by Joel.s on 2006-01-03
Thanks for a good howto!

I've followed the howto several times without any luck.
When i was in mood of stop trying i turned broadcast ssid on on my AP. Then suddenly i could see the network but couldnt connect. Then i tried booth System-Administration-Networking and the prompt way. -No succes

Then i realised that i had to convert the ascii-key on the AP to Hex. Suddenly i was connected wireless!

Hope my experiences could help somebody!

---

### Post by Anivair on 2006-01-12
[QUOTE=jonny]
1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop[/QUOTE]

umm . . . I don't have these files.  Should I?  I just installed breezy and I'm trying to follow these instructions, but I lack these files and it's obviously a problem. 

Anyone?

---

### Post by 11hjpphty76lkjj on 2006-01-12
Do a google search dude.  Seriously.

okay here ya go:

[http://www.kalosaurusrex.com/Belkin%20FD7001%20Drivers/]("http://www.kalosaurusrex.com/Belkin%20FD7001%20Drivers/")

Try the bcmwl5.inf first then bcmwl5a.inf.

Post any issues, I hope you have none.

Aaron

---

### Post by MetalMusicAddict on 2006-01-12
Anivair. Please read through the thread or search the thread next time. Its been refrenced a couple of times. Reading is an important step of learning here.

---

### Post by Anivair on 2006-01-14
[QUOTE=jonny]Broadcom wireless cards are tricky to set up in ubuntu[/QUOTE]

No joke!

it took me 3 days and in the end I had to use the a inf file, but your howto made it happen.  thanks a bunch.

---

### Post by 11hjpphty76lkjj on 2006-01-14
I'm glad you got it working! Congrats!  Welcome to the world of Ubuntu and Wireless. :)

Sorry if I came off a bit rough.  

Take it easy!

Aaron

---

### Post by Anivair on 2006-01-14
[QUOTE=MetalMusicAddict]Anivair. Please read through the thread or search the thread next time. Its been refrenced a couple of times. Reading is an important step of learning here.[/QUOTE]

Sorry.  The reason the first 2 days weren't working is because I only had about an hour to dedicate to it at a time.  today i actually sat down and did the work and it was cake.

---

### Post by zossz on 2006-01-20
This how-to was a GREAT resource for me. One sweep through the directions and the only hiccup was a need to throw this command into a shell script before bash quit puking on the context:

```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

...surfing free and easy  ;)

---

### Post by awahl on 2006-01-23
I feel like I'm raining on the parade here--- but I have been unable to find joy with my broadcom laden pci card (belkin)- I tried the dell drivers, the belkin drivers (both bcmwl5 & bcmwl5a) - made sure my radio-state was set correctly, etc.

What's puzzling me is why I cannot set my essid (using iwconfig) unless I am in auto mode. (sudo iwconfig wlan0 mode auto). I can set via networking in gnome, and my /etc/network/interfaces file is correct- but when I sudo iwconfig wlan0 - I get ESSID off/any - Anybody else have that problem? 

Ndiswrapper is installed and working fine, driver/hardware present, etc- I've tried everything including forcing the ap (again via iwconfig)- I opened up my router to broadcast and remove wep- Still...no joy....:( 

Nevertheless- this IS a great how-to, and if I do find a solution (or the error in my ways)- I will update you all.

---

### Post by greymaiden on 2006-01-25
Hi,

Thank you so much for taking the time to offer such easy to follow steps.  Unfortunately, not only did this method not work for me, but it seems to have caused a problem: after I followed these directions, GNOME got really slow.  When I login it now takes five minutes for the desktop to load, and when I attempt to acess system -> administration -> networking it also hangs for about five minutes.  

I posted a separate help request, but I was wondering of you could tell me how to undo your original instructions?  (I'm a newbie - obviously alas - so please be specific!).

Thanks,
Jamie Lynn

---

### Post by DerDon on 2006-01-26
Unfortunately I just managed to read the first 5 pages of this thread. That's why I just post my problem.

I followed the instructions given on the first page to install my Belkin F5D7000 wireless card. But I think that it didn't work, because if I write "sudo modprobe ndiswrapper" following error message occurs:
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/misc/ndiswrapper.ko): Operation not permitted
```

What can I do to make my card working?

HP

---

### Post by mrfinch on 2006-01-26
I did all that, with BCMWL5A.inf ... I restarted and my Adapter has a partially illuminated light.

On LSUSB I get:
```
finch@neith:~$ lsusb
Bus 003 Device 002: ID 050d:7051 Belkin Components
```

NDISWRAPPER -L gives:
```
finch@neith:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present
```

But on the Network jobby it doesn't have anywhere to add a 'wlan0' connection. I did a 'modprobe ndiswrapper' but it doesn't do much help as far as I can see.


Any suggestions?

---

### Post by redheaddiesel on 2006-01-27
I have an IBM Thinkpad 600 (just 600) and a Dell truemobile 1300 wi fi card. My problem with the above instructions is twofold: 

1) I am not connected to the internet yet. 
2) There are no drivers on the laptop. 

So, I can stick stuff on there via a jumpdrive from another computer, but I'm not sure what to get, or where to put it, or how to install it once it is there. 

Did I mention that I am a total Newbie? Thanks for your patience! 

Matt

---

### Post by tekwarren on 2006-01-27
I've went over the tutorial several times and read through some of the initial problems some people had the possible solutions but I can't seem to get past this step using either driver. I have tried to remove ndiswrapper-utils and reinstall with synaptic as suggested but still get stuck here:

```
heath@ubuntu-Heath:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:103C:12F3.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:0E11:00E7.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F4.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F8.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FA.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FB.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12F9.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FC.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FD.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
heath@ubuntu-Heath:~$

```


EDIT: ok i'm not sure what i did well I do but as to why I don't know :P I ran: sudo modprobe ndiswrapper and ...*pushed the button to turn on the wireless on my laptop* and the light comes on AND it shows up in the network devices...so I guess i'm good to go...time test!


Thanks for the HOW-TO

---

### Post by eljaco on 2006-01-28
Hey, I recently gave up on Windows and decided to go Ubuntu on my laptop. I'm having problems (as you can guess) with my Dell TrueMobile 1300 on my Inspiron 8500. I followed the HOWTO but I got 
> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/misc/ndiswrapper.ko): Invalid argument

after rebooting and running ```
sudo modprobe ndiswrapper
```
I am using the bcmwl5, but I already tried using bcmwl5a and it didn't work.

Also, when I ran the for loop, I got the following warnings:
> > for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:1028:0407.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied


Thanks in advanced.

---

### Post by parad0x on 2006-01-31
I got the driver installed, ndiswrapper says its working and hardware is present.  I put ndiswrapper in the last line of /etc/modules, did sudo modprobe ndiswrapper and I still can't get the device to show up in the networking properties. Any hints?

---

### Post by Frizguru on 2006-01-31
Hey, I'm newer to Linux, and have spent about 10 hours now trying to get my Wireless to work. I have seen tons of sites saying what to do, but nothing seemed to work. Yours was the easiest to understand, but when I rebootedmy system, nothing worked. I continue to get error messages, and nothing happens.

---

### Post by joepotter on 2006-02-02
[QUOTE=parad0x]I got the driver installed, ndiswrapper says its working and hardware is present.  I put ndiswrapper in the last line of /etc/modules, did sudo modprobe ndiswrapper and I still can't get the device to show up in the networking properties. Any hints?[/QUOTE]


I get the same here. No errors, just no working wireless card.

---

### Post by evilmrt on 2006-02-04
Hey folks, I've got a huge headache from trying to get my Belkin F5D7001 wifi card working in Ubuntu. I'm posting this in windows :P

After installing ndiswrapper from source...

I'm running into a couple problems. After modprobing ndiswrapper (everything before that step went fine), the console just hangs. Dmesg gives me this:

[4294691.271000] ndiswrapper version 1.8 loaded (preempt=no,smp=no)
[4294691.315000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[4294691.320000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed

helllllpppp :???:

---

### Post by Leviathan148 on 2006-02-05
i used the how to, everything worked no errors nothing but still my wifi card does not show up in the networking menu. Anything thoughts?

---

### Post by YumaJim on 2006-02-07
I am tring to compile ndiswrapper-1.8 and the following messages come up:

jim@tesla:~/ndiswrapper/ndiswrapper-1.8$ make
make -C driver
make[1]: Entering directory `/home/jim/ndiswrapper/ndiswrapper-1.8/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/jim/ndiswrapper/ndiswrapper-1.8/driver \
        DRIVER_VERSION=1.8
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/jim/ndiswrapper/ndiswrapper-1.8/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/jim/ndiswrapper/ndiswrapper-1.8/driver/hal.o] Error 127
make[2]: *** [_module_/home/jim/ndiswrapper/ndiswrapper-1.8/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jim/ndiswrapper/ndiswrapper-1.8/driver'
make: *** [all] Error 2

Looks to me like I need gcc-3.4 - where do I get that or can I edit
some file to use the loaded gcc-4.0.2. gcc-3.4 is not on my system.

Thanks,
YumaJim

---

### Post by StaticBoy on 2006-02-08
I've been watching the posts on this forum with great interest. Trying to get my wifi card to work was the first sticking point I had with Ubunutu i.e. about 2 hours after starting the installation. It is this sort of thing that has forced a return to Microsoft Windows XP. I really like the ideals of open source and enjoy the community experience, but at the end of the day I need to get my job done, and all too often it ends up taking a very long time to get it set up. And I still haven't found a way to VPN into the company network and run a Remote Desktop in Ubuntu even though I've read plenty of threads.

Can you imagine your average user (sending email, browsing the net, writing a letter and possibly a few digital photos) having to compile their own drivers using a command line interface?

My own Linux experience is limited, but I am an experienced software developer and consider that I can turn my hand to most things computer related. Getting a wifi card to work shouldn't have taken as much effort as it did.

On the upside though I just tried Internet Explorer 7 Beta 2 Preview. It lasted all of 3 hours before it was uninstalled! It was just like FireFox 1.5 (tabbed browsing, Google search box, RSS, etc) except that it wasn't done half as well. And it had some quite unpleasant bugs...

---

### Post by byen on 2006-02-08
Staticboy. I agree with what you say. Infact, it was what I felt too when I first tried fedora and could not get my Broadcom wifi card to work.I was a new user and knew squat about using the teminal. So I did what most new users would do. I went back to windows ! Now.. after a couple of months a buddy of mine tried the same distribution (fedora 3) and suprisingly his wifi card just worked outside the box! I was amazed ,as he could get something up and working without having to compile or install anythin while I toiled for ages to get my card up and running. So I tried again...found this thread and have been an Ubuntu User for 9 months straight!
So what did I learn here? It was not Ubuntu's (linux) developers fault that the drivers were not released for certain hardware...it is the hardware maker who has decided to ditch Linux support. So the only way around is by using techniques such as these to get things working.

But all in all.. in the end, I hear you. Linux would have been so much more popular and widely used if not for these issues. Well someday....

---

### Post by StaticBoy on 2006-02-09
Byen. I too hear what you say! I should add that in actual fact for personal use I am still using both Ubuntu and Kubunutu on the family laptops. Being a "techy" of course I've got a server at home (an old Compaq Proliant 800) which is running Fedora Core 4. All of these operating systems have been great for home use, runnning all the usual everyday software: FireFox, Thunderbird, etc, and overall with considerably less hassle than when it was all running Win2000/WinXP (and infinitely cheaper too!).

My problem is trying to ditch WinXP on the company laptop. I've got a spare hardrive that I can swap to experiment with Linux, but there are still a few things that I need Windows for. For example, when a client sends me a Visual Studio .Net C# project what else can I open it with other than VS.Net to debug it?

Sorry, I'm probably getting a bit off-topic for this thread, but I did manage to get my WiFi card to work on both Ubunutu and Kubunutu, so if any one has a BT Voyager 1060 PCMCIA card I may be able to help.

---

### Post by macaodha on 2006-02-09
hi there, 
i trying to get my broadcom 4306 working on my hp amd64. when i load ndiswrapper it says device present using the bcwmla.inf (or what ever its called), but there is no wireless listng uner networking.
when i use the iwconifg command all i get is
l0
eth0
sit0
any idea what the sit0 is. why doesnt wlan0 get listed.

---

### Post by macaodha on 2006-02-09
hey YumaJim i feel your pain. i also tried to complie the latest ndiswrapper but with no luck. i got the same error as you.

---

### Post by YumaJim on 2006-02-10
Macaodha - did you read jonny's how to at the beginning of this thread? 
If so did it work for you. I am going to try it. Will post results later.

---

### Post by fizzybrain on 2006-02-10
Sorry, I am still positively soaking behind the ears at this ubuntu thing.

Err. Where do the files in /etc/ndiswrapper/bcml5/ come from? My directory is empty. Everything up to the setting of the RadioState seems to be fine

This topic is a bit huge - doesn't it deserve to be split up? I mean the pages of people saying "thanks it worked" are very heartening, but it takes up a hull of a lot of space (and time ... or should that be "space-time"?). I wonder if there is any better way of organising it (sorry, still also unfamiliar with how these posts are organised). Someone has probably suggested this on page 18 or so, but it would take an age to find it.

Share and Enjoy

---

### Post by Scotland on 2006-02-11
Sorry if this is on previous pages but my Broadcom 440x/10/100 wired connection was detected and works 'automagically' on breezy 5.1 on a Dell Inspiron 9400.

Waiting Q1 2006 for Intels wireless driver for 3945 abg wireless.

Dougie.

---

### Post by Disastorm on 2006-02-11
doesnt work for me. at the end when i try sudo modprobe ndiswrapper it says
Error inserting ndiswrapper (some stuff in here/ndiswrapper.ko): Operation not permitted

Ive tried with both bcmwl5 and bcmwl5a

---

### Post by evilmrt on 2006-02-13
WOOHOO! Finally got it to work! I used the newest 1.9 ndiswrapper (1.8 wouldn't work)....and it compiled and installed! \\:D/ 

This is great! And I was about to give up on ubuntu :-# 

I should mention that I have a Belkin F5D7001 card, and used the bcmwl5a.inf file from the AR folder in the driver package found on the Belkin website. I basically just followed the installation directions on the ndiswrapper site, and followed that up by configuring the ubuntu networking panel. Works!!! :-D 

If anyone needs help, I'll try to help!

ALSO:

Is there a utility I can install to see connection strength/info...maybe a scanner as well? A gui util please.

EDIT:

Found GTKWifi, in the 3rd party forums. Just what I was looking for! Works good as well.

---

### Post by ztirffritz on 2006-02-13
I've been watching this thread for several months.  Between getting my ATI 200m card working and the Wireless card, Linux has been a disaster.  I know that the OS is not at fault, but rather equipment vendors for not supporting it.  I would strongly recommend that every single person reading this thread should right an angry letter to ATI and Broadcom.  That would do more to solve this problem than posting angry letters.  I really think that the time has come for an opensource hardware movement.  Imagine Apple as an opensource movement.  We throw our resources toward designing, manufacturing, and selling quality equipment, but it is open source, so we control the whole process from top to bottom and it WORKS with Linux, Apple, and Windows.  It would be a win-win-win scenario.  Now if we could just get Shuttleworth to foot the bill...

---

### Post by YumaJim on 2006-02-13
I found the Broadcom driver files on my XP Windows Partition at:
C:\Driver\Wireless.

The built in PCI cards works very well with Windows so here's hoping I can get it working as well with Kububtu. System is an Emachines M6807 laptop.

---

### Post by YumaJim on 2006-02-13
Here's the attchments per previous post....

YumaJim

---

### Post by tjputerboy on 2006-02-13
Thanks for the information I have mine working just after a couple of hours and happily posting now from my Ubuntu Dell laptop via a wireless connection. My Specs  are the following: 

Dell Precision M50 Laptop
Ubuntu 5.10
Dell TrueMobile 1300
ndiswrapper 1.2
bcmwl5.inf driver
Linksys WRT54G

Thanks again for this wonderful community, being a linux noob I couldnt have done it without this forum.

---

### Post by hyde200j on 2006-02-13
Could someone please help me?  I've been trying for a sickening long time on this and am in desperate need of advice. 
I have a BCM 4306 and I managed to install ndiswrapper and the driver with relative success.  So ndiswrapper -l shows bcmwl5a installed and present.
After that, nothing can be done to configure the connection.  I followed all of the steps in the first post and looked at the wiki as well; nothing works.

For example, iwconfig will always show AP equal to 00:00:00... and ESSID as "off/any" regardless of what I do to change them (as far as I know).  Maybe this alone is the problem, but even that I cannot fix.

Please help.  Any advice you have is appreciated.

---

### Post by YumaJim on 2006-02-15
[QUOTE=hyde200j]Could someone please help me? I've been trying for a sickening long time on this and am in desperate need of advice. I have a BCM 4306 and I managed to install ndiswrapper and the driver with relative success. So ndiswrapper -l shows bcmwl5a installed and present. After that, nothing can be done to configure the connection. I followed all of the steps in the first post and looked at the wiki as well; nothing works. For example, iwconfig will always show AP equal to 00:00:00... and ESSID as "off/any" regardless of what I do to change them (as far as I know). Maybe this alone is the problem, but even that I cannot fix. Please help. Any advice you have is appreciated.[/QUOTE] I had to very same problem. Go through the procedure found at: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) starting at the "Install Windows Driver" I am writting this using my Broadcom card now. It is very important to do the "dhclient wlan0" or you will not be able to connect to any web sites.:-) YumaJim

---

### Post by swkiller on 2006-02-19
Hey everyone

I've recently installed Kubuntu and am trying to set up my wireless drivers through ndiswrapper.  I've followed the steps on page 1 and have skimmed through most of the other pages in search for my answer but nothing has helped :(

I've followed the steps and never can get wlan0 to show up when i type in iwconfig.  My driver is the bcmwl5

Has anyone else run into this problem, and actually fixed it?

side note:
  I THINK I was able to set up this driver back when I used ubuntu...so I see no reason why it wont work now...although I may be thinking of my past laptop that I tried it with.


EDIT:

I went and built ndiswrapper from the new test source and got my driver to be reconized.  Now I have a problem when I go to enable my wireless driver, that it disables itself....any help? :(

---

### Post by Spagnutty on 2006-02-21
I'm trying to help a friend with her Dell laptop.  It has a BCM4306 wireless chipset.  Will it be possible to get her wifi working just while using an Ubuntu Live CD?  Or would we have to do an actual install?

---

### Post by esmclega on 2006-02-25
I have been trying to get my wireless working on my HP DV4000 with on board Broadcom wireless for about a week now. I've tried just about everything in this thread but still can't get it working. Ubuntu sees my network and my neighbor's network but won't connect. I was trying to upgrade to a newer version of ndiswrapper (I'm using 1.1) but had problems with the installation. I was following the instructions on page 6 but it seems like anytime I stray from Synaptic I fall on my face. Does anyone know of any repositories that have a newer version of ndiswrapper than the Ubuntu ones?

---

### Post by hotpurple on 2006-02-26
Hi, I've followed the instructions through several times now. I keep getting an error message about the drivers.

```

ndiswrapper -l

Installed ndis drivers:
bcmwl5  invalid driver!


```

Any ideas anyone?

Cheers

Chris

---

### Post by Allianz on 2006-02-26
I'm quite new using linux, and i've heard alot of good things about ubuntu. I'm trying to install my wlan but it seems im doing something wrong. I'm following the steps below, maybe i'm missing something or i'm doing it wrong, but i dont have any RadioState in any of my file in the folder /etc/ndiswrapper/....

thx
Allianz

---

### Post by LinuxKid on 2006-02-28
Can you do this using live cd and is there any clearer instructions on how to set up repositories

---

### Post by pgoetz on 2006-03-02
The instructions provided at the beginning of this thread **will** **not** **work** with newer laptops unless you get a newer ndiswrapper first -- the ndiswrapper module which ships with Breezy -- version 1.1 is too old.  After wasting hours trying to find an "easy" way to build a package from newer source, I gave up and downloaded the ndiswrapper source tgz from sourceforge, installed the kernel-headers and gcc-3.4 packages, and simply ran "make" and "make install".  I consequently had functional wireless on my new Dell Latitude D610 with Broadcom 1370 wireless chip.

If you do this, you will need to set the following entry by hand in the /etc/network/interfaces file:

   iface wlan0 inet dhcp
   pre-up modprobe ndiswrapper
   post-down rmmod ndiswrapper

---

### Post by Viriiguy on 2006-03-03
I have been trying for months to get my wireless working on my M6805.
I have tried every method that I have read ont he net, and none of them will work for longer than one use.

Is there anyway I can get a Norton Ghost image of someone's WORKING Ubuntu on an Emachine's M6805?

I just simply cannot make this work.  :(

---

### Post by YumaJim on 2006-03-03
[QUOTE=hotpurple]Hi, I've followed the instructions through several times now. I keep getting an error message about the drivers.

```

ndiswrapper -l

Installed ndis drivers:
bcmwl5  invalid driver!


```

Any ideas anyone?

Cheers

Chris[/QUOTE]
Did you use the bcmwl5a.inf and bcmwl5.sys. It's quit important to use the
bcmwl5a.inf and not the bcmwl5.inf as the 'a' version is the ascii (text) version of the file that can be read by the system. I also had the bcmwl5.bin file with the other driver files just incase the system needed it.

YumaJim

---

### Post by clearscreen on 2006-03-03
I'm getting so frustrated.. just like anyone else, the wlan0 device shows up perfectly, it's in iwconfig, it's in ifconfig, ndiswrapper list displays that hardware is found, but it just does NOT find any AP's... All the .conf files already have RadioState set to 0.. I dont know if that's a good sign.. The light just doesnt come on, it doesnt come on when I install acer hk and I press it either.. :( I hate broadcom right now

---

### Post by clearscreen on 2006-03-03
Ok I've had it.. Im going to install 64bit linux so it supports acer_acpi which supposedly has to solve the problems.

---

### Post by YumaJim on 2006-03-03
Did do the following:
sudo dhclient wlan0    seems that one has to do this to get an Ip address assigned.

YumaJim

---

### Post by scottporad on 2006-03-03
[QUOTE=clearscreen]I'm getting so frustrated.. just like anyone else, the wlan0 device shows up perfectly, it's in iwconfig, it's in ifconfig, ndiswrapper list displays that hardware is found, but it just does NOT find any AP's... All the .conf files already have RadioState set to 0.. I dont know if that's a good sign.. The light just doesnt come on, it doesnt come on when I install acer hk and I press it either.. :( I hate broadcom right now[/QUOTE]
Have you checked the BIOS to verify that the wireless is turned on?  I've experienced many of the frustrations as the people on this thread.  I had a brand new Dell 600m, wiped the drive, then installed Ubuntu...wlan0 coudln't talk to the access point.  Ug!

Well, it turns out that Dell configures the BIOS to have the wireless off by default, then they have a service (Dell Quick Set) that runs under Windows that turns it on.  Obviously, since I wiped the drive and am running Ubuntu, Dell Quick Set wasn't getting the job done.

Anyhow, once I edited the BIOS to have the wireless be on by default, everything worked properly.

---

### Post by mooswa on 2006-03-07
[QUOTE=clearscreen]Ok I've had it.. Im going to install 64bit linux so it supports acer_acpi which supposedly has to solve the problems.. :) Wish me luck lol[/QUOTE]

You don't need to install 64bit linux for acer_acpi to work. I have seen several posts where peple for some reason associated acer_acpi with 64bit only. That is not true. I think the confusion comes from the fact that acer_acpi was developed to support 64bit because the way acerhk used to work was not available for 64bit (direct calls to BIOS or something like that). However, acer_acpi works for BOTH 32 and 64 bit. I have Acer TravelMate 4404 with ndiswrapper-1.10 and acer_acp-0.3 (both build from source) and my wireless works just fine on the 32 bit Breezy Badger.

EDIT: Also note that after enabling wireless with acer_acpi the light doesn't go on immediately. Don't get alarmed. You need to do ifup to see the light blinking.

---

### Post by NotJayKay on 2006-03-09
Ugh, for the life of me I cannot get my stupid WiFi working on Ubuntu.   I did have it working following these directions [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) last night.  However I screwed up my MBR earlier and couldn't recover so I had to flatten and reinstall everything.

I tried doing it again and now it wont appear in my stupid network connections.  **_The only difference I can think of, is that I might be using newer drivers for my Broadcom WiFi from Dell as I had to download them tonight.**_

(For what it's worth, I'm on a Dell Inspiron 2200 that has the MiniPCI 1370 WiFi.)

```

jaykay@jaykaylaptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

```

This shows me that the driver was installed correctly and the hardware seems to be present.

From digging around the ndiswrapper FAQ, it seems like my driver isn't compaitble with Linux.  Can someone help me out here?


Edit: This is the pertinent part of the dmesg

```

[4294930.003000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294930.011000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:strrchr
[4294930.011000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmFreeContiguousMemorySpecifyCache
[4294930.011000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmAllocateContiguousMemorySpecifyCache
[4294930.011000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmGetPhysicalAddress
[4294930.011000] ndiswrapper (load_sys_files:456): unable to prepare driver 'bcmwl5'
[4294930.030000] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'


```

and

```

jaykay@jaykaylaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

---

### Post by 11hjpphty76lkjj on 2006-03-09
Did you compile the ndiswrapper or do a sudo apt-get ndiswrapper?  Honestly I've found that the compiled version seems more stable for me.  and there is always a slight lag in when a version of software is released and when it's available as a deb package.  as well have you tried the bcmwl5a driver?  I've found that it worked better for my wifi card.  However I have a belkin broadcom based.

Aaron

---

### Post by NotJayKay on 2006-03-09
[QUOTE=kalosaurusrex]Did you compile the ndiswrapper or do a sudo apt-get ndiswrapper?  Honestly I've found that the compiled version seems more stable for me.  and there is always a slight lag in when a version of software is released and when it's available as a deb package.  as well have you tried the bcmwl5a driver?  I've found that it worked better for my wifi card.  However I have a belkin broadcom based.

Aaron[/QUOTE]

I actually ended up searching around the forums and found this thread here: [http://www.ubuntuforums.org/showthread.php?t=120383](http://www.ubuntuforums.org/showthread.php?t=120383) which recomeneded to try the Acer drivers which I found here [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

And guess what, it works!

---

### Post by umuro on 2006-03-15
Well, I tried the suggestions and failed. 

I have a Dell Inspiron 8600 with Dell True Mobile 1300. I have Ubutun 5.10

 I get:
> 
ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

However, the wireless card does not appear in the list of interfaces:
> 
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

I copied bcmvl5.inf and bcimwl5.sys from the working Windows XP installation. Failing on that I also downloaded from Dell and unzipped the setup. Still failed.

I searched found lots of pages about ndiswrapper. More or less they are telling the same thing. 

Is there anybody who could use Dell Inspirion with Dell TrueMobile 1300 WLAN?

I am hopeless now.

---

### Post by umuro on 2006-03-15
Strange but... I installed ndiswrapper graphical front end and...

Now I see wlan0

---

### Post by leon-1 on 2006-03-15
I am still playing with Ubuntu, but I had a very strange happening with a broadcom chipset on SuSE a couple of weeks ago (I have a linksys card with with a bcmwl5 chipset in one of my other computers).

I loaded ndiswrapper, got everything working and rebboted later, afterwards when it re-booted I could not get it to work. In the end I changed a name in my config file from wlan0 to the result from a lspci. So the device name was;

bus-pci:00:00:0a.0

afterward the card worked without a problem, if I get a chance I'll see if I can recreate it so that peple can see what sort of results you get.

---

### Post by kenny23692 on 2006-03-16
I'm pretty new to Ubuntu, just started like 2 days ago and when trying to install wireless care i got this after doing sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
I using the drivers i downloaded from the site..

ken23@ubuntu:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
ken23@ubuntu:~$  sudo ndiswrapper -l 

any responses would help

---

### Post by hanspb on 2006-03-16
Hi, I don't have the patience to read all 35 pages of this thread, but I can't get it to work. I have a HP Pavilion laptop with a Broadcom wireless card, which of course works flawlessly in Windows. I got as far as trying to substitute Radiostate|1 with RadioState|0 in the config files manually, because the automatic method failed. then I discovered that RadioState was not mentioned in any of the files. Then I found out that Ubuntu does not even know I have a wireless card! System>Administration>Networking does not mention my wlan0. Also the Device Manager lists my card as Unknown. But the vendor is recognized as Broadcom Corp. There is a light near the wireless on/off button, but the light is always on, at least in Linux. Haven't tried pressing that button in Windows...

Anyway, ndiswrapper seems to be installed:

```
hpb@HPlaptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
hpb@HPlaptop:~$

```
but 
```
hpb@HPlaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

so I guess I just wonder if there is any point in continuing with the guide? At the moment I am not within reach of a wireless network either...

Edit: Stupid me...
I just tried to reboot anyway, and my wireless card shows up all right. So I'll just wait until I get home to see if it all works!

---

### Post by brallan on 2006-03-22
YES! it works!!!!

I have an ASUS laptop Z9200U with an internal wlan card, which as far as i could tell was something generic, called an "ASUS 802.11g". In XP under properties it mentioned broadcom, and sure enough, it was a broadcom chipset. when i got back into ubuntu I mounted the xp partiton, searched for bcmwl5 and the sys and ini files came up in <programs><Asus><wlan card utilities><driver><WL-103&WL-120&WL-100g&WL-103g&WL-120g>. i followed the instructions, ignored the error messages, and it works wonderful!

is there a database where i can send data about my card so a hardware probe on dapper install could automate the ndiswrapper install for anyone with this card? since all i did was cut and paste, i'm guessing it could be automated, no?

the ubuntu community is amazing! thanks so much.

brian russell (barcelona)

---

### Post by fezzik on 2006-03-23
I have had this working several times now.  I recently tried to install Debian and it messed up my whole computer apparantly my computer scares the Debian Kernel cause it tends to get all paniced.   Anyway after all that and I reinstalled Ubuntu 5.10 from scratch I can't get the stupid wifi working.  I have done everything on this list except for using a newer Ndiswrapper cause everytime I try to install it it fails cause it is looking for some file that doesn't exist.  Besides I used to get it working with no trouble before.  Like I say I have done this several times before.  Including three fresh installs and two new kernel compiles.  Everything seems to come up fine like everything is working fine except the radio.  I tried doing the RadioState thing but the .conf files don't have it.  I tried newer Ndiswrappers but installing them always failed cause they were looking for a file that didn't exist or directory or something.  Can someone please help.  I don't know what I am missing.  Like I say it used to be fairly simple to get it going now it is like nothing works despite my doing everything exactly as I always have.](*,) ](*,) :confused: :confused: :-k :-k :mad: :mad:

---

### Post by utopcats on 2006-03-25
PLS help me ......
i am very new user of ubuntu ..
i have work on wireless problem about 2 mouth now ....
and after the frist clean install of 5.10...

then i have try every you say which inculde:
install ndiswrapper and the driver .....with no problem....
and the *.conf file are already 0 ......in /etc/ndiswrapper/bcmwl5/....
i even put ndiswrapper at the end of modules and hopedully it will make the ndiswrapper boot up it sef .....but it doesn;t work either
but how come the wireless light just doesn't turn on ......

---

### Post by utopcats on 2006-03-25
i sorry that i have forget to say i am using ferrari 4005 ....

---

### Post by sithia on 2006-03-26
I've been reading up on wireless tonight and I've managed to get wireless to scan and detect my AP but that's as far as I've gotten. Everytime I try to run iwconfig I get a warning about the version of Wireless Extension. Seems I've got v17 but I need v18. From what I can tell, this is built into the kernel so I'd need to build a new kernel from source to update this. Am I correct in this? I'm running the latest 2.6.12-10-amd64-generic (updated 5 minutes ago) and have build Wireless Tools v27 yet I still get the same warnings every time. I tried over and over to connect to my AP with iwconfig until I realized "key restricted" was trying to send a WEP key but I'm using WPA/TKIP which seems wasn't supported until v18 of Wireless Extension. I realize I could change my AP settings and run "key open" but that's not an option in my neighborhood. Way too many people crammed in here to open my bandwidth.

Can someone confirm any of this for me? Is a newer kernel with v18 built-in on the horizon anytime soon?

---

### Post by fezzik on 2006-03-30
I have now figured out what the problem was.  Last time I had everything working I went a long time without redoing anything.  During that time I had set up my router to stop broadcasting the essid.  I not only didn't know that I had done that (it had been quite a while) but I didn't even know what the name of it was.  I had changed it and Lord knows I didn't remember doing that.  I went into the set up and reset all the settings and now I have wireless working beautifully.  Now I can get back to the important things like getting dvd's working and mp3's and internet videos.  Freaking Microsuck Monopoly.  

Anyway thanks for all your help everyone.  I really was starting to feel like a Linux idiot.  Turns out I am just a networking idiot still.  And that is ok with me.

---

### Post by Llwyd on 2006-04-02
Great post,

I have followed many instructions in this thread which seems to be working.  

My issues are this do you have to use WEP encrytion for your wirless router my router set-up is currently using 'WPA-PSK' is this possible??

I have set the card up, it can scan for networks and information but I cant seem to connect to my network.

Any idears.

---

### Post by Jonhoo on 2006-04-02
Allright, pretty big Linux-newbie speaking :P

First of all, I just figured out I actually like tinkering around in Linux :)

Now, to my problem..

I have followed all of the instructions above, and have got no errors at all.. The network light on my F5D7010 is green (Not the powerlight strangely, only the traffic light which is on continously..) , and I can configure the device in the networking manager, the only problem is that the card doesn't find any networks.. :( I have SSID broadcasting enabled on my router which is placed a bit under 10 feet from laptop with the card...

Even if I try to set the SSID through iwconfig, the SSID simply says 'off/any' when I run iwconfig.. 

```
iwlist wlan0 scan
```

produces:

```
wlan0          No scan results
```

Does anyone know what may cause this to happen?

Appreciate the help :)
Jon

---

### Post by Jefim on 2006-04-03
Ok, everyone who didn't get this to work should first of all do a
> lsmod | grep bcm
and if you see something like bcm43xx, then remove it by doing
> sudo rmmod bcm43xx
And only after that do modprobe ndiswrapper. This was my problem. This bcm43xx is a kernel module for broadcom, which messes things up! It just has to be removed in order for ndiswrapper to work normally. I suppose, that this rmark could go to the front page.

---

### Post by suspend on 2006-04-03
Anyone know what this error means? I am trying to get a Broadcom to work on my Gateway 7405GX with 64bit Edubuntu(Dapper Drake).


Errhttp://archive.ubuntu.com dapper/main ndiswrapper-utils 1.8-0ubuntu2
  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (113 No route to host) [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_amd64.deb)  Could not connect to archive.ubuntu.com:80 (82.211.81.182). - connect (113 No route to host) [IP: 82.211.81.182 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Jefim on 2006-04-04
suspend, I guess that this means that you don't have internet access when you try to install ndiswrapper-tools - basically it says you, that it can't contact the ubuntu downloads site (archve.ubuntu.com).

So, first of all check if you cable in plugged in correctly, if yes, start up ubuntu and go to System->Administration->Networking and chck hat you have your device enabled and activated, if not, then click Properties, check "Use this device" and select DHCP from the drop-down list (this is the most common option). Press ok, select your net device and precc "Activate". Now you should have the access to internet and be able to install packages from synaptics.

I hope that this helps.

---

### Post by x5452 on 2006-04-04
ive just installed the new version ubuntu, breezy, and Ive tried following the how to steps at the beginning of this thread, but i cant open the /etc/ndiswrapper file thing. I type gedit and it brings up a blank page, i try open location and typed etc/ndiswrapper but it says it cant open it, not a normal file, so how can i edit things?  everything seemed to be entering fine as i followed along until the forconggile line... then i got syntax error near unexpected token sudo.  Thats when i tried to edit manually as per the temp instructions up front but cant open the file.  I have now just typed the commands in to 'wipe clean' what ive done and start over.  when i typed in i got:
FATAL: module bcmwl5 not gound.
ERROR: module ndiswrapper does not exist in /proc/modules

what is my next step, starting from thebeginning?
I have bcmwl5.inf and bcmwl5.sys on my desktop

---

### Post by Zoomy on 2006-04-05
Hi,

I am a newbie to Linux, but have done a fair amount of experimenting in a short time....  I started with an old laptop and installed Ubuntu, and was amazed that all the devices were correctly detected - except my Linksys wireless card.

Since then, I went out and bought a brand new laptop (Acer 5002WLMi)- it was time, I needed more space, and I looked forward to seeing how Linux would work on it.

I temporarily was unfaithful to Ubuntu and tried tried other flavors, then Fedora Core 5 -  I had read that this was the Linux of Linux's and the easiest.
However, Fedora didn't detect my soundcard, my video was locked at 800x600, and of course, the wireless on the new computer was Broadcom, and of course it didn't work either.

So - back to Ubuntu.  I FIXMBR'd the partition and started over.  Ubuntu again impressed, and detected everything, but the Broadcom is still an issue.
I tried the instructions in this post, but to no avail.  I copied the bcmwl5.inf and bcmwl5.sys from my Windows Xp installation to a CD, then rebooted and dragged them onto the desktop, but the files had a strange syringe symbol on the icon.  I can't interpret what that means, but it must be something to do with virus protection

Any ideas?

---

### Post by henkstubbe on 2006-04-07
If got the Gnome logo on bcmwl5.inf and bcmwl5.sys, looks something like this:
[IMG]http://developer.gnome.org/projects/gap/presentations/GUAD3C/making-apps-accessible/gnome-logo-large.gif[/IMG]

So, no problem if you have this.

---

### Post by henkstubbe on 2006-04-07
Finally got the broadcom BCM4306 working on my Dell Latitude D600!

After an upgrade to Dapper, the wireless connection did not work anymore. I just followed the instructions listed in this thread, but nothing worked. Until I did

$ sudo dmesg

This gave a lot of output and that last lines told me:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed

I found the solution here: [https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx)

What I did
$ lspci -v |grep -i bcm
$ sudo rmmod bcm43xx
$ sudo rmmod ndiswrapper
$ sudo modprobe ndiswrapper

This worked immediately, to get it working after reboot, visit the link I gave.

---

### Post by nate_k on 2006-04-10
The wireless how-to wiki and the instruction you give here are very helpful. With this information I was able to achieve connectivity with my router and reach the internet. However, once WPA was activated, I could no longer connect with the wireless router. 
I installed and configured the WPA supplicant, but had no success with connecting.
Have you or has anyone been able to achieve and maintain a connection to the Internet with Broadcom and WPA?

---

### Post by jscat on 2006-04-11
[QUOTE=henkstubbe]

$ sudo dmesg

This gave a lot of output and that last lines told me:

bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed

I found the solution here: [https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx)

What I did
$ lspci -v |grep -i bcm
$ sudo rmmod bcm43xx
$ sudo rmmod ndiswrapper
$ sudo modprobe ndiswrapper

This worked immediately, to get it working after reboot, visit the link I gave.[/QUOTE]


Thanks for that reply got it working right away! Motorola 825G

---

### Post by coderunner on 2006-04-12
Just as an FYI, in case someone else stumbled onto this thread after initially having trouble with ndiswrapper.  I actually tried the drivers that came with my laptop (presario v5000), and the included inf file did not work with breezy.  I spent a long time trying the howto here with the editing of the included inf file.  

I ended up getting mine to work by using the bcmwl5a.inf file included in this setup program:
[ftp://ftp.gateway.com/pub/hardware_support/drivers/win_xp/portable/m360/D00268-001-002.exe](ftp://ftp.gateway.com/pub/hardware_support/drivers/win_xp/portable/m360/D00268-001-002.exe)
since that model gateway uses the card in my laptop (bcm4318).  I just did a normal 

ndiswrapper -i bcmwl5a.inf 
modprobe ndiswrapper

and it showed up in networking options and connected to my router w/o problems.

---

### Post by Horizon on 2006-04-12
[QUOTE=Joel.s]Thanks for a good howto!

I've followed the howto several times without any luck.
When i was in mood of stop trying i turned broadcast ssid on on my AP. Then suddenly i could see the network but couldnt connect. Then i tried booth System-Administration-Networking and the prompt way. -No succes

Then i realised that i had to convert the ascii-key on the AP to Hex. Suddenly i was connected wireless!

Hope my experiences could help somebody![/QUOTE]
Just for the record, for ascii / plain text you can use 
```

sudo iwconfig wlan0 key s:<password here>

```

God forbid me having to dabble with HEX and the likes.
Besides, i prefer my 12345 to be ascii :mrgreen:

---

### Post by sliverman69 on 2006-04-12
does anyone know if this process works on Kubuntu?

---

### Post by coderunner on 2006-04-13
iirc, kubuntu is exactly the same as ubuntu except with the KDE window manager.  Then, whether or not it works would not have anything to do with whether you are using kubuntu or ubuntu.

---

### Post by sliverman69 on 2006-04-16
thanks I really appreciate the response, I thought that it was the same and it would be compatible, but I was not certain.

---

### Post by phyre-x on 2006-04-17
Hey, been reading this thread for a few hours now and tried to get my broadcom hunk of junk working. i must have had some success because i was able to run
```

phyre@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
phyre@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:B2:D7:AE
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-58 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
          Cell 02 - Address: 00:12:BF:07:43:B9
                    ESSID:"HVAC's Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
from here im well, frankly stuck lol. the network i want to connect to is my own and is wpa-psk protected but i have no idea. the other network is my school (live next door). i tried to connect with the system>admin>networking 'thing' and no joy. any chance someone can point me in a direction to connect to my own wpa-psk network ? or atleast get onto the other wlan which is unprotected. 

thanks

---

### Post by TRINIDADUBUNTU on 2006-04-17
This is sooooooo good.  Finally I am back up with wireless running on my Acer Aspire 3003 with broadcom wireless!!!

To all, don't forget to turn off the eth0 interface.  When I tried to connect wirelessly with eth0 still activated, X killed itself, lost the keyboard, and had to reboot.  Not so sure why X died, but no matter.  When I rebooted, I killed eth0 and I am up and running again.  I followed the instructions from the original post and voila!!! Instant wireless, no need to sudo modprobe ndiswrapper on reboot.  All I do is activate the wireless interface from network-admin and badda bing badda boom...I'm up and running.  Next is to tackle WPA so the networks not open to anyone.  Thanks for the original post.

-Trin

---

### Post by El Cacahuete on 2006-04-19
This thread is great. Just one problem internet speed is UBER slow. I have a 256k DSL connection that runs at 150k (its a long story and i am trying to fix it with qwest but they are being stupid :( )

I changed the radio settings too, but I did it a couple steps later, I wouldnt expect that to slow my connection down to non-excistant, would it?

---

### Post by El Cacahuete on 2006-04-19
[QUOTE=Zoomy]Hi,

I am a newbie to Linux, but have done a fair amount of experimenting in a short time....  I started with an old laptop and installed Ubuntu, and was amazed that all the devices were correctly detected - except my Linksys wireless card.

Since then, I went out and bought a brand new laptop (Acer 5002WLMi)- it was time, I needed more space, and I looked forward to seeing how Linux would work on it.

I temporarily was unfaithful to Ubuntu and tried tried other flavors, then Fedora Core 5 -  I had read that this was the Linux of Linux's and the easiest.
However, Fedora didn't detect my soundcard, my video was locked at 800x600, and of course, the wireless on the new computer was Broadcom, and of course it didn't work either.

So - back to Ubuntu.  I FIXMBR'd the partition and started over.  Ubuntu again impressed, and detected everything, but the Broadcom is still an issue.
I tried the instructions in this post, but to no avail.  I copied the bcmwl5.inf and bcmwl5.sys from my Windows Xp installation to a CD, then rebooted and dragged them onto the desktop, but the files had a strange syringe symbol on the icon.  I can't interpret what that means, but it must be something to do with virus protection

Any ideas?[/QUOTE]

Does it look like a little golden lock? Right mouse click on the file and click on properties. Give yourself write permisions to the three options it shows.

---

### Post by neopirus on 2006-04-28
[QUOTE=El Cacahuete]This thread is great. Just one problem internet speed is UBER slow. I have a 256k DSL connection that runs at 150k (its a long story and i am trying to fix it with qwest but they are being stupid :( )

I changed the radio settings too, but I did it a couple steps later, I wouldnt expect that to slow my connection down to non-excistant, would it?[/QUOTE]

I found the thread very helpful too, but just like El Cacahuete my connection is very slow.  In windows XP the connection is much faster.  Actually I had Mepis Linux 3.4 installed on my laptop and not only did Mepis automatically detect and configure my dell 1350 card, it works with with 128bit encryption and it's just as fast as my windows.  I'm not sure what the reason for having this happen with ubuntu is.  
i finally got my card to work with WEP with the WAP at work where I can't dissable the encryption.  I pick up an unencrypted signal which is pretty far from where I am and the internet speed seems to be the same as my work.  
Actually I looked in the .conf files in ndiswrapper.  I can't even find radio settings in there...
Any ideas?

Thanks

---

### Post by Nutronion on 2006-04-29
OK, I'm new to linux, so this is probaly just a n00bish problem but...

When looking for the drives for the wireless card I have a BVMWL5.SYS file but not a BVMWL5.inf file.. That original file was located in the SYSTEM32/Drivers folder (the directory listed in the guide was empty)

Where can I find this file?

---

### Post by neopirus on 2006-04-30
I have a dell inspiron which uses this driver.  i found the windows driver at the dell website and unzipped it.  it includes both the .inf and the .sys file.

---

### Post by luca.costantino on 2006-04-30
> **jonny]Broadcom wireless cards are tricky to set up in ubuntu, and the forums are full of frustrated users seeking advice.  Broadcom provide no Linux support (feel free to complain to your hardware vendor or choose a different card if you haven't yet shelled out your cash), but they can be made to work - and you're in the right place if you want to know how.

First, you need to find out if this How To is for you.  Broadcom wireless cards come under many brand names and, in particular, are used in many Dell and Acer laptops.  Look for the drivers supplied with your card (Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON) said:**
> How to add extra repositories[/URL]

3. Open a terminal session and enter this code.  Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```4. Reboot your PC.  On restarting, the light on your wireless card should come on.  If not, try entering```
sudo modprobe ndiswrapper
```5. Your card is now working.  Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings.  Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one.  You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK.  The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK.  Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana.  If everything works, you can delete the file from your desktop.

13.  You might notice that the signal strength applet doesn't work properly.  This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled.  Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.

[COLOR=Indigo](Note: This how-to has been updated to reflect all comments from the thread up to 19 April)[/COLOR]



hi
first of all sorry for my bad english

i followed step-by-step your tutorial, but my bcm4301 wifi card still does'nt work!

 now this is my situation

iwconfig returns
```

root@hfish-laptop:/home/hfish# iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"ZyXEL"  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off

eth0      no wireless extensions.

sit0      no wireless extensions.

root@hfish-laptop:/home/hfish#

```
so, I think that the problems is that aliases are made for wlan0 instead of eth1

now I have a fresh install of kubuntu 6.06 Beta 2


2 days ago i had 5.10, and wifi worked correctly, because the wifi adapter was recognized by wlan0 instead of eth1


what can i do??

thanks a lot
luca
[email]luca.costantino@gmail.com[/email]

---

### Post by luca.costantino on 2006-04-30
sorry...
i forgot one thing

modprobe -r bcmwl5 returns an error, module not found
modprobe bcmwl5 returns the same error

---

### Post by luca.costantino on 2006-04-30
here i am again...

i've noticed one thing

the module i have is not bcmwl5, but bcm43xx, and i get an error loading it



[4295206.083000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[4296540.396000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[4296540.400000] ieee80211_crypt: unregistered algorithm 'NULL'
[4296554.903000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[4296554.948000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[4296565.307000] ieee80211_crypt: registered algorithm 'NULL'
[4296565.311000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4296565.311000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4296565.369000] bcm43xx:  driver
[4296565.370000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 209
[4296565.654000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[4296565.665000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[email]root@hfish-laptop:/home/hfish/.aMul[/email]e#  

some hints
thanks

---

### Post by tomy4ever on 2006-04-30
luca, i'm trying to get my wireless working as well ;) I'm following step by step the thing that "jonny" posted but It still doesn't work. I've gotten the bcmwl5 module by typing that on google, it's on the first sites.
Well I've done everything Jonny's said until point 4. . However it's not working, the interface won't appear in System -> Administration -> Networking. 
I've got an icon on top right of my screen right next to the eth0 connection which is RJ45 and perfectly works (as i'm replying on this board ;d) 
Are there any tests I could make to know what is wrong according to the fact it couldn't really be an hardware issue since it's working on windows xp.


edit:
I actually noticed that the following hasn't got any effect:
> 
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

plus if I dont chmod 777 all the files (/etc/ndiswrapper/bcmwl5/*.conf) it says permission denied (lol) although the command is run as sudo.

---

### Post by Nutronion on 2006-04-30
[QUOTE=neopirus]I have a dell inspiron which uses this driver.  i found the windows driver at the dell website and unzipped it.  it includes both the .inf and the .sys file.[/QUOTE]

Cheers for that, found file, downloaded, followed instrucitions and BANG! Writing this from ubuntu WITHOUT wires =D

*is happy*

---

### Post by tomy4ever on 2006-04-30
I've just read something interesting :)

from [http://linux-laptop.net/hosted/dell-inspiron-9400.html]("http://linux-laptop.net/hosted/dell-inspiron-9400.html")

    *

      WLAN

   1.

      Download original driver from INTEL. Read and follow the installation instructions as described here in short:
   2.

      Download ieee80211 from [www.sourceforge.net](www.sourceforge.net)
   3.

      Build your own kernel WITHOUT ieee80211 support. Boot it.
   4.

      In the ieee80211-subdirectory do make && make install. (&#8222;y&#8220; to &#8222;delete old modules&#8220;)
   5.

      Now copy the INTEL Firmware to /lib/firmware (the INSTALL-Document by INTEL wants to use hotplug. Don't use the document here.)
   6.

      type &#8222;make&#8220; in the driver and daemon subdirectories. Copy the daemon to /sbin.
   7.

      Go into the driver subdir and type &#8222;./load&#8220; . If everything works, you copy the .ko-Module to /lib/modules/KERNEL-VERSION and do a &#8222;depmod -a&#8220;.
   8.

      Wonderful. We're done.

just when i read "Build your own kernel WITHOUT ieee80211 support. Boot it." I was like :wtf: how do u build your own kernel :o never done such a thing, if someone could help..

---

### Post by dunnerz on 2006-05-02
Hi,

The ndis solution did not work for me with dapper - i used the solution found here:

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

(the section about dapper)

I have to modprobe the driver at start up (apparntly i can add it to a list somewhere) + the connection is not as quick as the ndis - but it works, so thats good enough for me!!

hope this helps someone

---

### Post by DavidFourer on 2006-05-12
I got stelmate's error message and I'm trying to follow his advise:

If you have
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted    [COLOR="Blue"]That's what I got[/COLOR]

...just reinstall the older version from the synaptic manager under packages>force version> hoary version

[COLOR="Blue"]The pkg mgr menu selection package>force version>hoary version is faded and not accessible.  (I'm not at all familiar with compiling modules)  Am I doing something simple wrong?[/COLOR]

[COLOR="Indigo"]Perhaps I'm in the wrong forum--These instructions are only for Hoary?  I am using Breezy 5.10--I'm looking for another thread.[/COLOR]

---

### Post by ozzymud on 2006-05-12
*EDIT: replied to wrong message in wrong forum even.. sorry :(*

Card was picked up on install, but not working because of missing firmware, after Ubuntu finished installing, extracting firmware and rebooting... setup with no security (i used MAC filters on my router) and static IP (no dhcp) all worked,
here were my steps.

Chip is 4318 in HP/Compaq Presario M2000
kernel is: 2.6.15-22-386
install is Ubuntu Dapper Daily 05112006 (yesterdays as of this posting)

# bcm43xx-fwcutter -i bcmwl5.sys

  filename :  bcmwl5.sys
  version  :  3.100.46.0
  MD5      :  38ca1443660d0f5f06887c6a2e692aeb

(i got mine from a link in a Fedora post about this card:
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip))
i also attached the sys/inf files only in an attachment to this post.. i think :P

# sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-22-386/ bcmwl5.sys

clicked activate...

try google... bingo... connected to the net! *biggrin*

NetworkManager Applet 0.6.2 does not see it at all
(while downloadng this daily iso i tried Fedora FC5, NetworkManager
seen the connection although the signal strength didnt work.)

Blue wireless light works when wireless is up.

Wireless blue-light button DESTROYS connection until POWER DOWN reboot!!

after a hard reboot...

iwconfig eth1 gives:

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:11:XX:11:X1:11
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=185/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist eth1 scan gave:

eth1      Scan completed :
          Cell 01 - Address: 00:11:XX:XX:X1:11
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-169 dBm
                    Extra: Last beacon: 81ms ago

ifconfig eth1 down
will turn light and net off (i assume card is powered down)
ifconfig eth1 up
brings light back on and net is still down....

iwlist eth1 scan..
eth1      No scan results

iwconfig eth1 results are the same... no "Access Point: Invalid" looks
like everything is "ok" but it aint.


time for another power-down reboot.... but wait... lets try:

sudo ifconfig eth1 down
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx
(Note: Pressing the "wireless button" causes even this to fail to work)

... try google... WHEEE! it's back up :)

iwlist scan now shows my linksys router again...

NetworkManager still shows nothing (No Connections)

so...
System->Preferences->Sessions->Startup Programs->
nm-applet --sm-disable <--- disable

Network Monitor 2.12.0 properly shows eth1 up and 100% signal strength.
(gnome-netstatus) Network Monitor via "Add to Panel"

Just my $.02 for anyone still hassling with this card.

---

### Post by i++ on 2006-05-18
brilliant! amazingly helpful, thanks!

---

### Post by ztirffritz on 2006-05-21
OK, the good news is that the blue light on my Presario os finally blue.  The bad news is that it doesn't seem to do much of anything else besides being blue.  
1) How do I run the modprobe command during startup?
2) why doesn't eth1 show up in Network Manager?

After my original post in this thread about 5 months ago, I glad that the nerds kept at it and finally got this working...somewhat.  Shame on Broadcom for not helping though!

---

### Post by blackest_knight on 2006-05-23
thank you thank you-- perfect instructions for my nx6110 hp laptop

I copied the inf and sys file from the hp drivers dvd that came with this laptop and 
after the first line of the removal stuff said there wasnt anything to remove continued from the installation block of code

I very nearly didnt enter the following as one command line

"for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done"

(without the quotes of course)
thinking i was just meant to type 
"sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile"
which is wrong. 

I thought I'd mention this in case some else doesnt think type everything in the code box means everything :)

i rebooted after the code block and rebooted after the modprobe and configuring the wireless lan bit. (nothing seemed to want to connect after i switched to wifi)
on rebooting there was a longish pause before the networking setup (upto a minute max) before ubuntu carried on booting and wireless came on and is working flawlessly. 
I don't use wep encryption (just mac address filtering) so i just selected the ssid for my network and set wlan0 as the default gateway. 

Thanks again for perfect instructions on setting up wifi with broadcom and the ndiswrapper.

---

### Post by slyboots on 2006-05-25
Hello I use HP nx6110 (model PM730 Code PG841ES.) with Ubuntu Brezzy 5.10 (Linux zer0 2.6.12-10-686 #1 Fri Apr 28 13:21:56 UTC 2006 i686 GNU/Linux).

I have this card 0000:02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

It is corectly installed in windows but i cant find the bcmwl5.inf file. The bcmwl5.sys i found in c://windows/system32/

I will make on my wlan card becouse i will use it. I download Automatix with Windows wireless driver program and this program will help with them. But it will search for .inf file and i have  bcmwl5.inf not. I dont now why but i search on all prtitions and nothing...

I look in this forum and i see that you have make this guide... But what should i make?

Thanks for help.

---

### Post by slakkie on 2006-05-29
[QUOTE=jonny]```

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

This can be changed to:
```

for conffile in /etc/ndiswrapper/bcmwl5/*.conf
do
  sudo sed -i -e 's/RadioState|1/RadioState|0/'  $conffile
  # or via perl
  # sudo perl -p -i -e 's/(RadioState\|)1/${1}0/' $conffile
done

#
# OR..
#
sudo sed -i -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
# or perl again
# sudo perl -p -i -e 's/(RadioState\|)1/${1}0/' /etc/ndiswrapper/bcmwl5/*.conf

```



Because you sudo and then redirect you will not be able to write the new conffile. Your user is not allowed to recreate the files. 

And thanks for the HOWTO, I will try to get my wireless working in combination with the LiveCD (do not want to switch unless I get my primary needs working).

---

### Post by solarwind on 2006-05-30
My router is currently using WPA encryption for my wireless network. How do I get this to work with the dell 1370 cards? Do I have to install a special package? 

Thanks for any replies, all help is much appreciated.

---

### Post by slakkie on 2006-05-31
solarwind: [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by solarwind on 2006-05-31
Thanks a lot! Ubuntu 6.06 will surely own!

---

### Post by blackest_knight on 2006-06-01
or not just tried these instructions which worked under 5.10 and my wireless isnt working under 6.06  :(
any idea's ?

---

### Post by aldegaz on 2006-06-11
why when I input

ndiswrapper -|

I get thjis for an answer:

>

---

### Post by atrus123 on 2006-06-12
[QUOTE=aldegaz]why when I input

ndiswrapper -|

I get thjis for an answer:

>[/QUOTE]

It should be ndiswrapper -l (as in lamb or lame or lucky), not ndiswrapper -| (as in the pipe symbol).

J.

---

### Post by gregoo on 2006-06-12
Brilliant, thanx a million!!!

---

### Post by aldegaz on 2006-06-12
so, in this last part of the code, it would be the same?

sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile

???

---

### Post by jlpicardus on 2006-06-12
Did anyone get the Broadcom 4318 rev 02 working?
I read the forum and the internet back and forth, pulled all my hairs out, but my wireless is stil not working under Ubuntu. I have an ASUS A6U (6000 series), I have no errors during the install process as described in the first post here, but it just don't work.

My card is listed as eth0 although I get a wlan01 during installation of the drivers using ndiswrapper.

I am out of options here ...... nothing seems to work.

Regards from Germany,

Herman

---

### Post by aldegaz on 2006-06-12
Herman

I have got the same problem as you, you can read my thread here

[http://ubuntuforums.org/showthread.php?p=1129622#post1129622](http://ubuntuforums.org/showthread.php?p=1129622#post1129622)

---

### Post by asad112 on 2006-06-13
Hey, I followed the steps, and my light came on, but it is blinking. Is this wrong? I am still not able to get internet either...

---

### Post by jlpicardus on 2006-06-13
Today I thought about my old laptop wich had a Benq AWL-100 pcmcia-card. I installed this card on my new laptop and that worked without a glitch.

However, I will keep on trying to get my onboard wireless to work.

Herman

---

### Post by aldegaz on 2006-06-13
I am still trying to get the broadcom chip to work

This is PROOF that this tutorial IS NOT for everyone.

---

### Post by hangfire on 2006-06-18
[QUOTE=aldegaz]I am still trying to get the broadcom chip to work

This is PROOF that this tutorial IS NOT for everyone.[/QUOTE]

I hate to be critical, I'm sure the original poster had good intentions, but someone *really* needs to correct the original HOW-TO post which has caused so many people so many problems.

Details here:

[http://ubuntuforums.org/showpost.php?p=393062&postcount=210](http://ubuntuforums.org/showpost.php?p=393062&postcount=210)

HF

---

### Post by trubblemaker on 2006-06-18
here's some updated howto's that may help.  I prefer the native driver ones, (but you need to be using Dapper for them)

---

### Post by jak on 2006-06-19
Most broadcom chipsets have been supported out of the box in Dapper.
Upgrade!

---

### Post by trubblemaker on 2006-06-19
[QUOTE=jak]Most broadcom chipsets have been supported out of the box in Dapper.
Upgrade![/QUOTE]
sort of, if you had ndiswrapper before you upgraded unfortunately this 'causes issues, alot of people don't know that their is native support and go crazy trying to remove this "obviously broken driver"..... so think bigger, yes it's supported out of the box but their are complications.

---

### Post by thenowherekid on 2006-06-24
Im new to this ubuntu/kubuntu thing too. Ive been using slackware for the past  2 years, and i read that this was easily done on this Dell XPS m1710 laptop. well yeah everything was workin fine when i installed Kubuntu dapper. the wireless even worked. crazything. cuz since after that first boot, it hasnt worked. and now i am trying to ndiswrapper to work with this. i have the driver present. But i cannot get the hardware present. I've read and read and read. but i dont see anyone that didnt get the hardware present, plus its 3:30 in the morn. if someone  could maybe help me make ndiswrapper see the wireless device, i can get the wireless going again. thanks a million.

---

### Post by trubblemaker on 2006-06-24
Read the howto you need to make sure that you don't have both ndiswrapper and bcm43xx present at the same time that causes all sorts of issues. 

make sure to add:

blacklist bcm43xx to /etc/modules.d/blacklist (I"m pretty sure on a windows box so I can't check, but it's in the howto in my signature.)

I'm not on kubuntu, there is another forum for them and that may provide more help.  I think that this should be the key for you though post back and I'll try and help you some more.

All hail debian derivatives.

---

### Post by phyre-x on 2006-06-24
everything now works fine for my broadcom card with network manager and wpa support, had to black list the native broadcom driver and took a while playing around but all seems well now. thanks

---

### Post by Shane_S on 2006-07-04
I had beat my head against a wall for a week trying to get my Broadcom card in my Dell Inspiron 5160 working with Dapper. The tutorial in the first post in this thread worked PERFECTLY for Breezy. But wouldnt work at all with Dapper. I finally stumbled across a working fix for it after trying all of the other tutorials on the forums and beating google to death with the searches. lol.

[http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working](http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working)

It worked like a charm for me. Hopefully the origonater of this thread will add it to his initial post.

Enjoy

shane

---

### Post by rwestgeest on 2006-07-08
[QUOTE=jonny;125537][i]6 July 2006 Update
Sorry guys, 

But THIS 

```

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

```

Will erase all config files in /etc/ndiswrapper/bcmwl5/  !!!!!!!!!

Have you really tested this. 

The output of sed should be redirected to a tempfile instead and then copied back to the original.

Something like:

```

cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile.tmp
mv $conffile.tmp $conffile

```

If you have tested this and your conffiles have not been erased, then take a closer look. Have they really changed? I would expect not for i would expect that you need a sudo for the sed command, not for the cat command. 

Cheers 
Rob

---

### Post by trubblemaker on 2006-07-08
straight up forget that radio state bullshit, that needs to be taken out of the howto.

---

### Post by rodonea on 2006-07-16
OK!!I can't believe!
After a long day trying ](*,) now I'm posting with my wireless.
Features:
HP Pavilion zv5000
Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

Thank you for supporting

---

### Post by francisco tovar on 2006-08-27
hello
I have a problem, 
when I put:  
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' 
$conffile
done


I get:
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:103C:12F3.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1355.5.conf:.. Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1356.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1357.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
......
(and like fifteen lines similar)....

do you know what is the mistake?
thank you
FT

---

### Post by jedleman on 2006-08-28
hi.  Thank you for posting.  The steps are very clear.  However, I receive the following during step 4:  Can you assist?

jedleman@jedleman-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:1028:0407.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
jedleman@jedleman-laptop:~$

Thank you in advance...

---

### Post by trubblemaker on 2006-08-28
Yeah don't do the radio state thing it really out of date check the howto's in my signature to get you going or check the wiki for the howto on dniswrapper

---

### Post by turntabletux on 2006-09-05
Hey guys,

Little frustrated. I followed everything that I have read on this topic. Great tutorial by the way, helped me even though I am still not connected.

Anyways, I have ndiswrapper-utils and ndisgtk installed. I install the "bcmwl5.inf" file no problem. I ran "ndiswrapper -l" and my driver is there and present. However, when I open up Network Settings, that is where my probelm is. I click on eth1 and enter in my "ESSID," I have no "WEP Key," and I am using "DHCP."

I click "activate" and it hangs, so obviously it didn't activate. Then it says "eh1 activated." I click "ok" to exit and once again it hangs, so I know that it's not going to work. When I open Network Settings again, "eth1 is not active." 

I open "eth1 connection properties," and I have sent 9 packets and recieved 9 packets, but no signal whatsoever, the bar is still empty.

I do "iwconfig," and I get everything correct and fine, except no "Access Point." My wired and wireless connections on my other pc's at home work flawlessly.

When I ping a site, it won't go through. I have uninstalled ndiswrapper and my drivers. Rebooted, installed everything and still no luck. I have up to date drivers and ndiswrapper. Any command on this site that I have ran comes out with no errors.

I am so frustrated because I know that I am so close. I have no clue what I am missing, and usually I am very good with ndiswrapper as I have used it many times with Suse, so this is making me feel stupid. ](*,) 

Any help guys would be amazing. I start school again (ITT Tech) and I would like to have my wireless up and running because I use it during class, lab, and to keep myself from falling asleep sometimes.

Thanks guys for reading my novel. I woke up at 4 with hope and it is 8, so I have decided to call it quits until I wake up later. Thanks again guys and I hope to hear from you soon. I know you guy usually respond fast, this an amazing forum, I am proud to be a part of it.

Thanks!!

Ant

---

### Post by trubblemaker on 2006-09-05
ok so if you are using dapper and not hoary you might run into an issue with a the native driver that comes pre-installed.  to solve this issue you need to blacklist the bcm43xx driver 
```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist 
```
alternativly you could blacklist ndiswrapper and try use the native driver (but you may need to trouble shoot it as there is a reason you tried to use ndiswrapper)
```
echo "blacklist ndiswrapper" | sudo tee -a /etc/modprobe.d/blacklist 
```

the reason I'm guessing your on dapper is hoary is old and you talked about the computer hanging when you tried to activate the ndiswrapper.  The above steps should help you out.

if you really wanted to know if the driver was installed before you ran a code to remove it you could check many things one is too: 
```
lspci | grep controller
``` and if a broadcom driver is listed there and you are on dapper then you will have a native driver installed.

---

### Post by Karl S. on 2006-09-07
DHCPACK problem. Done various searches, and seen what looks to be similar problems, but I've not yet seen an answer that makes any sense to me (probably because I'm not a computer person)....

Here's my output:

> karl@karl:~/Desktop$ sudo ./ndiswrapper_setup
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ndiswrapper_setup, Copyright (C) 2006 Adam Blackburn
ndiswrapper_setup comes with ABSOLUTELY NO WARRANTY; for details
type please see the file gpl.txt in the same directory as this program.
This is free software, and you are welcome  to redistribute it
under certain conditions; type see the file gpl.txt in the same directory
as this program for details.
Installing ndiswrapper...
(Reading database ... 77822 files and directories currently installed.)
Preparing to replace ndiswrapper-utils 1.8-0ubuntu2 (using ndiswrapper.deb) ...
Unpacking replacement ndiswrapper-utils ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

Extracting the drivers...
Deleting temporary files...
Changing driver permissions...
Changing working directory...
Removing previous attempts to use ndiswrapper, if any...please ignore errors in this section...
Driver bcmwl5a is not installed.Use -l to list installed drivers
ndiswrapper died with exit status 23
Removing default driver...
ERROR: Module bcm43xx does not exist in /proc/modules
rmmod died with exit status 1
Installing driver through ndiswrapper...
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Installed ndis drivers:
bcmwl5          driver present, hardware present
ndiswrapper died with exit status 1
modprobe config already contains alias directive

Modprobing ndiswrapper...
Moving back to original working directory...
Deleting more temporary files...
Blacklisting bcm43xx...
Adding ndiswrapper to /etc/modules, so it should load on boot...
Removing excess entries from your network interfaces file...
Searching for a wifi point...
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:71:EC:EE
                    ESSID:"karl steel"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-33 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020000

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:1a:30:e3
Sending on   LPF/eth1/00:14:a5:1a:30:e3
Listening on LPF/eth0/00:c0:9f:d1:74:1b
Sending on   LPF/eth0/00:c0:9f:d1:74:1b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 35449 seconds

---

### Post by trubblemaker on 2006-09-08
I don't understand what your asking for help with... you have an Ip address,  "192.168.1.101" and you can see your wirless network.  I do see the ndiswrapper did have an error while installing, but what is your actuall problem? 

to be honest you need to format your output better, break it up into parts.  I'm willing to help you, but you need to put a little more effort into your post help the people that are trying to help you so to speak.

---

### Post by Trabi on 2006-09-10
who can help me...

I've changed from mandriva 2006 to kubuntu (latest version) and i'm trying to get my wli-cb-G54a broadcom to work. 
With mandriva it was no problem, i just had to load the bcmwl5a.inf with ndiswrapper and it worked, but with kubunu, damnd !!!

i followed the steps of the howto and this is the result:

```
stefan@Ledda:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present
```

this looks good, driver present and hardware present, but the indication lights on my card wont light up.

```
stefan@Ledda:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwconfig, it seems likes it works, bit rate = 1mb/s , verry strange, the lights wont light up, i have no wireless network (ps, in mandriva my wireless network interface was called wlan0)

dmesg gives me this :
```
[17179925.064000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179925.088000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

seems to be that there must be something wrong, but i cant find the solution... Can someone help me??

thanks !!!

---

### Post by Karl S. on 2006-09-10
My "actual problem" is that DHCPACK problem. I don't know what it's doing, but it seems that it's asking me to wait nearly 10 hours for it to 'renew.' Searching for DHCPACK on the forums indicates that other people seem to be having this problem.

If no one can help me, I'll just wait for Edgy Eft & maybe Ubuntu will have working wireless for non-computer people like me cursed w/ a Broadcom 4318.

....20 minutes later I have working wireless.

*shrugs shoulders* 

I have no idea how I got it working. If it was this thread (which was one of about 10 'how to' thread I read), thanks.

---

### Post by sirkamran32 on 2006-09-10
Hey, i have ubuntu 6.06. i also got ndiswrapper 1.23 on my machine.  However, my machine is not connected to the internet, and my "sudo make" commands do not work either (i cant find my disk).
can anyone help me get my wireless card (wmp54gs linksys) working?
i can get any necessary files from a windows machine and transfer them to my linux machine. this is frustrating, i dont have a wired connection near my linux computer.  I want to be able to get my wireless card working so i can play with linux. btw, i am a huge newbie.  thanks for any help.  a how-to install ndiswrapper w/o internet connection would be nice! i need that. just tell me what files to get from my windows machine, and ill transfer and install then on my linux one. i need "sudo make" to work and also ndiswrapper. thanks for any help!!!

---

### Post by trubblemaker on 2006-09-11
Tabi, what version of ubuntu are you running if your on dapper you need to blacklist the native driver also... the microcode issue I've seen before but was recently deleted off the wiki I wanted... but I've seen the error and i think it's cause the wrong driver was loaded, but I can't remeber however a quick search of the forms on micro code not loading should let you know

---

### Post by trubblemaker on 2006-09-11
sirkamran32.

I do have a link in my signature(the one on to the automated installation of ndiswrapper) that has zipped files at the end of the howto that should help you as an all in one solution. I'm not sure but I think that your driver might have native support but I"m not really sure which card you have.  can you run

```
 lspci | grep Broadcom 
``` and let me know what you get.
also you output for
```
 iwconfig list 
ifconfig

``` 
would also help out in helping you solve your issue, I will check my email again tomorrow am(PST) and will try and help you out.

---

### Post by sirkamran32 on 2006-09-11
trubblemaker.
thanks for the response! i will try what you said out as soon as i can, i am busy with other stuff, so dont think i'm ignoring you. Just to let you know, i have a desktop with a Linksys wmp54gs with speed booster PCI card. I'll post what happens soon, thanks again. btw, if i dont have to use ndiswrapper thats fine, i just need a solution, to make my wireless card work. thanks.

---

### Post by trubblemaker on 2006-09-11
ps if you just upgraded your machine and then wireless stopped working it's definitly the native driver/ ndiswrapper conflict.
in that case you need to blacklist one of the native driver or ndiswrapper.  if you do a search on blacklist on the howto in my signature you will get instructions on how to fix this.

---

### Post by method_lam on 2006-10-02
sorry the ultimate noob here, but i hope someone can help me.

problem with the WEP key...when it is enabled, i cant get on :(

in the initial post, it says to prefix the wep key with s:

say the wep key was 0123456789.  what do i type in?  surely not s:0123456789 because that doesnt work for me.

---

### Post by altern on 2006-10-03
hi

I am trying to get Belkin F5D701 to work on a IB X24. I am running Dapper. I followed few howtos with litle luck. I never get hardware present on ndiswrapper. This is the info i get from few commands on my system:

$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present


$ sudo ifup wlan
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan ; No such device.
SIOCSIFADDR: No such device
wlan: ERROR while getting interface flags: No such device
wlan: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan.


$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


$ lspci | grep Broadcom
0000:03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


I am wondering if i might be using a driver that doesnt work with my card. Or I have done something wrong in the process maybe.  

My /etc/networks/interfaces looks like this

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
wireless-ap any

I added ndiswrapper to /etc/modules and blacklist bcm43xx in /etc/modprobe.d as the howtos suggested

any ideas?? ... thanks!

---

### Post by trubblemaker on 2006-10-03
method_1am 

This is how I get my card to work in my /etc/network/interfaces file I have
```

auto lo
iface lo inet loopback

# The primary network interface
auto ra0

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid linksys
[COLOR="Red"]        pre-up /home/archiver/network[/COLOR]
        pre-up ifconfig ra0 up


```
then in the highlighted file /home/archiver/network
```

#/bin/bash
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=SHARED
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=610EDCE1B9

```
of course this isn't broadcom card but it might work for you so give it a shot.  also you can see now, I hope, how you can use pre-up to use commands to bring up your connection. If you can get your key entered succesfully and bring up your driver, then add those commands like I have to a script with a pre up.

ps any script that you run should have the permissions changed on it so that it can run.  (chmod u+x file-name)

---

### Post by trubblemaker on 2006-10-03
ok first try ndiswrapper -m 
then see if you have a wlan0
if you still don't 

Start again with the howto, and remove your installation of ndiswrapper.  I bet that if you look in you 
```
 dmesg 
``` 
that it says somewhere in there that the micro code didn't load.  I think that you probably used the incorrect driver.  if your on a dual boot windows can tell you what file to copy, ( I'm on the same driver)  you can also get the driver off the installation CD don't use the bcmwla driver it's the old windows98 wirless driver, use the bcmwl driver it's for XP not a big difference but I found I could do more with the XP driver.

---

### Post by method_lam on 2006-10-05
i have a d-link di-524 and still cant connect with WEP enabled.

i can connect to other routers running the same settings, but not mine at home.

authentication type is OPEN

how can i manually set the channel?

(trubblemaker: i havent tried what u suggested yet, but i will soon, thanks)

---

### Post by method_lam on 2006-10-10
didnt work trubblemaker, dammit.

---

### Post by trubblemaker on 2006-10-10
you don't want to set the channel generally the computer will pick the correct one.
You generally want to set the essid to the one you use at home.
```

iwlist scan

```
then [COLOR="Red"]if[/COLOR] you see the correct network:
change your essid with
```

iwconfig <interface> essid <linksys_or_your_router_essid>

```
then you need to do whatever you normally do to connect to a wep
setting the password and auth mode.
then type:
```

sudo dhclient <interface>

```
it's important not to use 'sudo ifup <interface>' as that reads you  /etc/network/interfaces file and will totally negate all the settings that you just changed.  Once you get connect adding all these commands to /etc/network/interfaces ifup will work to get you connected, but not until then.

in all this I assume that you have already connected to your network without encryption, if you have not, stop do that first then come and read these instructions over again.

---

### Post by ctopkelly on 2006-10-27
I am trying to get my hp zd 8215us with a Broadcom wnic.  i follow all of the howto. but when i get to the point
ckelly@ckelly-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done

what i get is here

bash: /etc/ndiswrapper/bcmwl5/14E4:4311:103C:1363.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311:103C:1364.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311:103C:1365.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:103C:135F.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:103C:1360.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:103C:1361.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312:103C:1362.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4312.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1355.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1356.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1357.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:1358.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:1359.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:135A.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:0E11:00E7.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F4.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F8.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FA.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FB.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12F9.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FC.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
i know i am really close to getting this to work,  

i am new to linux and i want to make the change but i need this to work.  so please someone help.

Thank Chris](*,)

---

### Post by trubblemaker on 2006-10-28
i don't know which howto you followed, but I suggest the one in red in my signature, or building it from source.  The instruction your talking about isn't as far as I know a vital step in getting you nic up and running, to help you further can you do a couple things for me.
give me the output of the following commands:
[code] 
lspci | grep road
ndiswrapper -l
iwlist scan
sudo dhclient wlan0
ping www.google.ca
cat /etc/network/interfaces
[code]

---

### Post by ctopkelly on 2006-10-30
ok thank you for your help.  here is what you requested
lspci
[code]
0000:0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[code]
ndiswrapper -l
[code]
Installed ndis drivers:
bcmwl5  invalid driver!
[code]
iwilist scan
[code]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.
[code]
sudo dhclient wlan0
[code]
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
[code]
ping www.google.ca
no responce

cat /etc/network/interfaces
[code]
auto lo
iface lo inet loopback
iface eth0 inet dhcp
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
auto eth1
auto eth0
[code]

I am going to try to set using your howto.  but if you can help me out that woule be great.  i want to make the switch to linux i am getting sick of Microsoft BS.  thanks
chris:D

---

### Post by trubblemaker on 2006-10-30
K so two things pop out I think you need add 'blacklist bcm43xx' to ```
/etc/modprobe.d/blacklist
``` as seeing eth1 with no scan results hints to you having the native bcm43xx driver enabled. it would also interfer with you ndiswrapper code loading at boot. so try blacklisting it and then reboot, see if internet comes up.

if it doesn't then you do need to start from scratch with the proper bcm driver, if you dual boot you can look at you network and get it to show you the driver it's using, (it will even show you the location on your windows partition.)  Don't ask me how to do it, I just dug around in the network settings and eventually I made it tell me.  Failing that there are lists of where to get drivers including the red howto in my signature that is an automated installation of ndiswrapper.  Try it out it might fix you up.

---

### Post by ctopkelly on 2006-10-30
I have tried the Red HowTo with no success.  I will trt the black list part and reboot.

In running through the HowTo i get all the way to the end and it asks me to run  ndiswrapper -l
and here are my results

Installed ndis drivers:
bcmwl5  invalid driver!

not sure if that helps out

if i duel boot in to windows and find the drivers that it is using i should move it over to the linux computer and run the first post in this string to get it to work?  I have see so many posts i am not sure what one is the best for my computer.

Thanks for your help
Chris
:D

---

### Post by trubblemaker on 2006-10-30
you want to get the driver, and then just use:
```
 ndiswrapper -e bcmwl5 
```
then make sure that the driver is removed
```
 ndiswrapper -l 
```
install the driver
```
 ndiswrapper -i /path/to/bcmwl5.inf
sudo ndiswrapper -m 
```
make sure ndis is loaded
```
 sudo modpobe ndiswrapper 
```
then try out 
```
 iwlist scan
```
if you get an essid listed then your on the road to the internet use:
```
 sudo iwconfig wlan0 essid <your-essid>
sudo dhclient wlan0 
```

Then we can move on to fixing your ugly /etc/network/interfaces file

---

### Post by ctopkelly on 2006-10-31
went and got the drivers from my windows XP drive.  here is what i get after following your directions.

root@ckelly-laptop:/home/ckelly# ndiswrapper -e bcmwl5
root@ckelly-laptop:/home/ckelly#

root@ckelly-laptop:/home/ckelly# ndiswrapper -l
No drivers installed

root@ckelly-laptop:/home/ckelly/Desktop# ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
root@ckelly-laptop:/home/ckelly/Desktop# sudo ndiswrapper -m
modprobe config already contains alias directive

root@ckelly-laptop:/home/ckelly/Desktop# sudo modprobe ndiswrapper
root@ckelly-laptop:/home/ckelly/Desktop# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      No scan results

The only thing is see diffrent is the when i goto the network app it says the wireless card is active.  It always said it was not active.  "Things that make you go hummmmm".  I do think we are on to some thing and i am learning about linux by doing this.  

oh yea... also when i look at the network app i see the AP name is the essid dropdown.  i tried to connect to it but that was a negitive.  

I will keep messing around with it till i hear back from you.

Thanks
Chris ( an almost Linux user).
:smile:

---

### Post by trubblemaker on 2006-10-31
ok now I want you to reboot the computer give me the output from these commands:
```

dmesg
ifconfig
iwlist scan 
iwconfig
ndiswrapper -l
cat /etc/modprobe.d/blacklist

```
and just because
```

sudo ifconfig wlan0 up; sudo dhclient wlan0

```

---

### Post by ctopkelly on 2006-10-31
This is great.  Thanks for the help one thing how do you get the little code boxes in your posts.

here we go
```

ckelly@ckelly-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fef0000 - 000000001fef9000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fef9000 - 000000001ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7a70
[17179569.184000] On node 0 totalpages: 130800
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126704 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f79c0
[17179569.184000] ACPI: RSDT (v001 HP     3082     0x06040000  LTP 0x00000000) @ 0x1fef1a59
[17179569.184000] ACPI: FADT (v001 HP     3082     0x06040000 PTL  0x00000003) @ 0x1fef8ec0
[17179569.184000] ACPI: MCFG (v001 HP     3082     0x06040000  LTP 0x00000000) @ 0x1fef8f34
[17179569.184000] ACPI: MADT (v001 HP     3082     0x06040000  LTP 0x00000000) @ 0x1fef8f70
[17179569.184000] ACPI: BOOT (v001     HP 3082     0x06040000  LTP 0x00000001) @ 0x1fef8fd8
[17179569.184000] ACPI: DSDT (v001 HP     3082     0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 2793.449 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.416000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.416000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179572.424000] Memory: 508212k/523200k available (1976k kernel code, 14412k reserved, 606k data, 288k init, 0k highmem)
[17179572.424000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.504000] Calibrating delay using timer specific routine.. 5592.98 BogoMIPS (lpj=11185978)
[17179572.504000] Security Framework v1.0.0 initialized
[17179572.504000] SELinux:  Disabled at boot.
[17179572.504000] Mount-cache hash table entries: 512
[17179572.504000] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[17179572.504000] CPU: After vendor identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[17179572.504000] monitor/mwait feature present.
[17179572.504000] using mwait in idle threads.
[17179572.504000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179572.504000] CPU: L2 cache: 1024K
[17179572.504000] CPU: After all inits, caps: bfebfbff 00100000 00000000 00000080 0000441d 00000000 00000000
[17179572.504000] mtrr: v2.0 (20020519)
[17179572.504000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[17179572.504000] Enabling fast FPU save and restore... done.
[17179572.504000] Enabling unmasked SIMD FPU exception support... done.
[17179572.504000] Checking 'hlt' instruction... OK.
[17179572.520000] checking if image is initramfs... it is
[17179573.060000] Freeing initrd memory: 6616k freed
[17179573.100000] ACPI: Looking for DSDT ... not found!
[17179573.124000] ENABLING IO-APIC IRQs
[17179573.124000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.268000] NET: Registered protocol family 16
[17179573.268000] EISA bus registered
[17179573.268000] ACPI: bus type pci registered
[17179573.284000] PCI: PCI BIOS revision 2.10 entry at 0xfd95e, last bus=11
[17179573.284000] PCI: Using MMCONFIG
[17179573.284000] ACPI: Subsystem revision 20051216
[17179573.312000] ACPI: Interpreter enabled
[17179573.312000] ACPI: Using IOAPIC for interrupt routing
[17179573.312000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.312000] PCI: Probing PCI hardware (bus 00)
[17179573.312000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.312000] Boot video device is 0000:01:00.0
[17179573.316000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.316000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.320000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[17179573.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[17179573.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179573.324000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *10 11 14 15)
[17179573.324000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 10 11 14 15) *5
[17179573.324000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 *11 14 15)
[17179573.324000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 10 11 14 15) *7
[17179573.324000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *7
[17179573.324000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.
[17179573.324000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)
[17179573.324000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 10 11 14 15) *7
[17179573.324000] ACPI: Embedded Controller [EC0] (gpe 29) interrupt mode.
[17179573.328000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.328000] pnp: PnP ACPI init
[17179573.332000] pnp: PnP ACPI: found 9 devices
[17179573.332000] PnPBIOS: Disabled by ACPI PNP
[17179573.332000] PCI: Using ACPI for IRQ routing
[17179573.332000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.332000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179573.332000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179573.332000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179573.352000] PCI: Bridge: 0000:00:01.0
[17179573.352000]   IO window: 4000-4fff
[17179573.352000]   MEM window: c8100000-c81fffff
[17179573.352000]   PREFETCH window: d0000000-d7ffffff
[17179573.352000] PCI: Bridge: 0000:00:1c.0
[17179573.352000]   IO window: disabled.
[17179573.352000]   MEM window: disabled.
[17179573.352000]   PREFETCH window: disabled.
[17179573.352000] PCI: Bus 12, cardbus bridge: 0000:0b:00.0
[17179573.352000]   IO window: 00005400-000054ff
[17179573.352000]   IO window: 00005800-000058ff
[17179573.352000]   PREFETCH window: 30000000-31ffffff
[17179573.352000]   MEM window: 32000000-33ffffff
[17179573.352000] PCI: Bridge: 0000:00:1e.0
[17179573.352000]   IO window: 5000-5fff
[17179573.352000]   MEM window: c8200000-c82fffff
[17179573.352000]   PREFETCH window: 30000000-31ffffff
[17179573.352000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.352000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.352000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179573.352000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.352000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.352000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.352000] Simple Boot Flag at 0x36 set to 0x1
[17179573.352000] audit: initializing netlink socket (disabled)
[17179573.352000] audit(1162341291.352:1): initialized
[17179573.352000] VFS: Disk quotas dquot_6.5.1
[17179573.352000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.352000] Initializing Cryptographic API
[17179573.352000] io scheduler noop registered
[17179573.352000] io scheduler anticipatory registered
[17179573.352000] io scheduler deadline registered
[17179573.352000] io scheduler cfq registered
[17179573.352000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.352000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.352000] assign_interrupt_mode Found MSI capability
[17179573.352000] Allocate Port Service[pcie00]
[17179573.352000] Allocate Port Service[pcie03]
[17179573.352000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179573.352000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.352000] assign_interrupt_mode Found MSI capability
[17179573.352000] Allocate Port Service[pcie00]
[17179573.352000] Allocate Port Service[pcie02]
[17179573.352000] Allocate Port Service[pcie03]
[17179573.352000] isapnp: Scanning for PnP cards...
[17179573.708000] isapnp: No Plug & Play device found
[17179573.724000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179573.732000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.732000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.732000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.736000] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 209
[17179573.736000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.736000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.736000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.736000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.736000] mice: PS/2 mouse device common for all mice
[17179573.736000] EISA: Probing bus 0 at eisa.0
[17179573.736000] Cannot allocate resource for EISA slot 1
[17179573.736000] Cannot allocate resource for EISA slot 3
[17179573.736000] Cannot allocate resource for EISA slot 4
[17179573.736000] Cannot allocate resource for EISA slot 5
[17179573.736000] EISA: Detected 0 cards.
[17179573.736000] NET: Registered protocol family 2
[17179573.772000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.772000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.772000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.772000] TCP: Hash tables configured (established 16384 bind 16384)
[17179573.772000] TCP reno registered
[17179573.772000] TCP bic registered
[17179573.772000] NET: Registered protocol family 1
[17179573.772000] NET: Registered protocol family 8
[17179573.772000] NET: Registered protocol family 20
[17179573.772000] Using IPI Shortcut mode
[17179573.772000] ACPI wakeup devices:
[17179573.772000]  LAN KBC0 MSE0
[17179573.772000] ACPI: (supports S0 S3 S4 S5)
[17179573.772000] Freeing unused kernel memory: 288k freed
[17179573.772000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.812000] vga16fb: initializing
[17179573.812000] vga16fb: mapped to 0xc00a0000
[17179573.928000] Console: switching to colour frame buffer device 80x25
[17179573.928000] fb0: VGA16 VGA frame buffer device
[17179574.996000] Capability LSM initialized
[17179575.144000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.144000] ACPI: Thermal Zone [THRM] (61 C)
[17179575.624000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.624000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 217
[17179575.624000] ICH6: chipset revision 3
[17179575.624000] ICH6: not 100% native mode: will probe irqs later
[17179575.624000]     ide0: BM-DMA at 0x3c40-0x3c47, BIOS settings: hda:DMA, hdb:DMA
[17179575.624000] Probing IDE interface ide0...
[17179575.916000] hda: ST9808211A, ATA DISK drive
[17179576.700000] hdb: MATSHITAUJ-840D, ATAPI CD/DVD-ROM drive
[17179576.756000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.760000] hda: max request size: 1024KiB
[17179576.760000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.768000] hda: cache flushes supported
[17179576.768000]  hda: hda1 hda2 < hda5 >
[17179576.812000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, (U)DMA
[17179576.812000] Uniform CD-ROM driver Revision: 3.20
[17179577.064000] usbcore: registered new driver usbfs
[17179577.064000] usbcore: registered new driver hub
[17179577.068000] USB Universal Host Controller Interface driver v2.3
[17179577.068000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 225
[17179577.068000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.068000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.068000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.068000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x00001800
[17179577.068000] hub 1-0:1.0: USB hub found
[17179577.068000] hub 1-0:1.0: 2 ports detected
[17179577.144000] ieee1394: Initialized config rom entry `ip1394'
[17179577.172000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 233
[17179577.172000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.172000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.172000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.172000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x000038c0
[17179577.172000] hub 2-0:1.0: USB hub found
[17179577.172000] hub 2-0:1.0: 2 ports detected
[17179577.276000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[17179577.276000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.276000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.276000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.276000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x000038e0
[17179577.276000] hub 3-0:1.0: USB hub found
[17179577.276000] hub 3-0:1.0: 2 ports detected
[17179577.380000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179577.380000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.380000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.380000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.380000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00003c00
[17179577.380000] hub 4-0:1.0: USB hub found
[17179577.380000] hub 4-0:1.0: 2 ports detected
[17179577.484000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 225
[17179577.484000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.484000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.484000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.484000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.484000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.484000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xc8000000
[17179577.488000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.488000] hub 5-0:1.0: USB hub found
[17179577.488000] hub 5-0:1.0: 8 ports detected
[17179577.592000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.592000] ACPI: PCI Interrupt 0000:0b:00.2[C] -> GSI 22 (level, low) -> IRQ 209
[17179577.640000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[209]  MMIO=[c8208000-c82087ff]  Max Packet=[2048]
[17179577.676000] Probing IDE interface ide1...
[17179578.256000] Attempting manual resume
[17179578.292000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.308000] kjournald starting.  Commit interval 5 seconds
[17179578.912000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08002856000a7eff]
[17179588.576000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.580000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.700000] hw_random: cannot enable RNG, aborting
[17179588.708000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.712000] agpgart: Detected an Intel 915G Chipset.
[17179588.728000] agpgart: AGP aperture is 256M @ 0x0
[17179589.348000] Real Time Clock Driver v1.12
[17179589.372000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179589.372000] Yenta: CardBus bridge found at 0000:0b:00.0 [103c:3082]
[17179589.372000] Yenta: Enabling burst memory read transactions
[17179589.372000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.372000] Yenta: Routing CardBus interrupts to PCI
[17179589.372000] Yenta TI: socket 0000:0b:00.0, mfunc 0x01a01b22, devctl 0x64
[17179589.520000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 209
[17179589.520000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179589.624000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[17179589.624000] Socket status: 30000006
[17179589.624000] Yenta: Raising subordinate bus# of parent bus (#0b) from #0d to #0f
[17179589.624000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[17179589.624000] cs: IO port probe 0x5000-0x5fff: clean.
[17179589.624000] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[17179589.624000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179589.660000] input: PC Speaker as /class/input/input1
[17179589.832000] intel8x0_measure_ac97_clock: measured 54304 usecs
[17179589.832000] intel8x0: clocking to 48000
[17179589.968000] cs: IO port probe 0x100-0x3af: clean.
[17179589.968000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179589.972000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.972000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.972000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.140000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a
[17179590.176000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179590.188000] ts: Compaq touchscreen protocol output
[17179590.356000] 8139too Fast Ethernet driver 0.9.27
[17179590.356000] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 20 (level, low) -> IRQ 50
[17179590.356000] eth0: RealTek RTL8139 at 0xe0a44400, 00:c0:9f:b9:58:7e, IRQ 50[17179590.356000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179590.364000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179590.424000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179590.424000] sdhci: Copyright(c) Pierre Ossman
[17179590.428000] PCI: Enabling device 0000:0b:00.4 (0000 -> 0002)
[17179590.428000] ACPI: PCI Interrupt 0000:0b:00.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179590.476000] sdhci: ============== REGISTER DUMP ==============
[17179590.476000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179590.476000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179590.476000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179590.476000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179590.476000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179590.476000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179590.476000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179590.476000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179590.476000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179590.476000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179590.476000] sdhci: ===========================================
[17179590.528000] mmc0: SDHCI at 0xc8209000 irq 169 DMA
[17179590.576000] sdhci: ============== REGISTER DUMP ==============
[17179590.576000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179590.576000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179590.576000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179590.576000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179590.576000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179590.576000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179590.576000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179590.576000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179590.576000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179590.576000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179590.576000] sdhci: ===========================================
[17179590.676000] mmc1: SDHCI at 0xc8208c00 irq 169 DMA
[17179590.724000] sdhci: ============== REGISTER DUMP ==============
[17179590.724000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179590.724000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179590.724000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179590.724000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179590.724000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179590.724000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179590.724000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179590.724000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179590.724000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179590.724000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179590.724000] sdhci: ===========================================
[17179590.824000] mmc2: SDHCI at 0xc8208800 irq 169 DMA
[17179591.400000] eth0: link down
[17179591.756000] lp: driver loaded but no devices found
[17179591.812000] SCSI subsystem initialized
[17179591.820000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179591.820000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.820000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179591.864000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179591.992000] ndiswrapper: driver bcmwl5 (Broadcom,07/21/2005, 3.140.16.0) loaded
[17179591.992000] PCI: Enabling device 0000:0b:03.0 (0000 -> 0002)
[17179591.992000] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179591.996000] ndiswrapper: using irq 177
[17179592.444000] NET: Registered protocol family 17
[17179593.008000] wlan0: vendor: ''
[17179593.008000] wlan0: ndiswrapper ethernet device 00:14:a5:14:0a:d6 using driver bcmwl5, 14E4:4320:103C:12F8.5.conf
[17179593.008000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179593.056000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1 across:1510068k
[17179593.292000] EXT3 FS on hda1, internal journal
[17179593.472000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.472000] md: bitmap version 4.39
[17179593.884000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179594.948000] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179594.948000] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }[17179594.948000] ide: failed opcode was: unknown
[17179594.948000] cdrom: open failed.
[17179600.240000] ACPI: AC Adapter [ACAD] (on-line)
[17179600.240000] ACPI: Battery Slot [BAT1] (battery present)
[17179600.316000] ACPI: Power Button (FF) [PWRF]
[17179600.316000] ACPI: Lid Switch [LID0]
[17179600.316000] ACPI: Power Button (CM) [PWRB]
[17179600.316000] ACPI: Sleep Button (CM) [SLPB]
[17179600.396000] ibm_acpi: ec object not found
[17179600.424000] pcc_acpi: loading...
[17179600.460000] wmi_add device=dfe2f800
[17179600.460000] calling WQBA
[17179600.512000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179604.612000] [drm] Initialized drm 1.0.1 20051102
[17179604.624000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179604.624000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179605.780000] [drm] Setting GART location based on new memory map
[17179605.780000] [drm] Loading R300 Microcode
[17179605.780000] [drm] writeback test succeeded in 1 usecs
[17179605.828000] ppdev: user-space parallel port driver
[17179606.540000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179606.540000] apm: overridden by ACPI.
[17179610.588000] Bluetooth: Core ver 2.8
[17179610.588000] NET: Registered protocol family 31
[17179610.588000] Bluetooth: HCI device and connection manager initialized
[17179610.588000] Bluetooth: HCI socket layer initialized
[17179610.636000] Bluetooth: L2CAP ver 2.8
[17179610.636000] Bluetooth: L2CAP socket layer initialized
[17179610.656000] Bluetooth: RFCOMM socket layer initialized
[17179610.656000] Bluetooth: RFCOMM TTY layer initialized
[17179610.656000] Bluetooth: RFCOMM ver 1.7
[17179632.012000] NET: Registered protocol family 10
[17179632.012000] lo: Disabled Privacy Extensions
[17179632.016000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179632.016000] IPv6 over IPv4 tunneling driver
[17179642.692000] eth1: no IPv6 routers present
[17179674.608000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179674.608000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179690.288000] eth0: no IPv6 routers present

ckelly@ckelly-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:B9:58:7E
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feb9:587e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1415995 (1.3 MiB)  TX bytes:307317 (300.1 KiB)
          Interrupt:50 Base address:0x4400

eth1      Link encap:Ethernet  HWaddr 00:14:A5:14:0A:D6
          inet6 addr: fe80::214:a5ff:fe14:ad6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:c8206000-c8208000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18972 (18.5 KiB)  TX bytes:18972 (18.5 KiB)

ckelly@ckelly-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

ckelly@ckelly-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ckelly@ckelhttp://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1695554ly-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

ckelly@ckelly-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
#module below does not work with Broadcom 4318 wireless cards
blacklist bcm43xx

ckelly@ckelly-laptop:~$ sudo ifconfig eth1 up; sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:14:a5:14:0a:d6
Sending on   LPF/eth1/00:14:a5:14:0a:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


the one thing i see is that the eth1 (Wireless) interface is setup with a inet6 addr: fe80::214:a5ff:fel4:ad6/64. it looks to me like the interface is not getting the ip address but an ip6 address?  coule this be the problem?

you are almost there my friend

Thanks
Chris ( About 98% linux user):-D

---

### Post by trubblemaker on 2006-10-31
nah but for kicks you can black list it

```
sudo vim /etc/modprobe.d/blacklist
```

add 

"blacklist ipv6"

do you like having eth1 as the ndiswrapper? as most howto's tell you to do ndiswrapper -m with would change the name to wlan0 you might give this a shot to change things up a bit.

what version of ndiswrapper did you use? I hate to make you do another howto but [here]("http://ubuntuforums.org/showpost.php?p=1696835&postcount=33")  is a link to another post to show you howto do it from source, I think it's a matter of being on the latest ndiswrapper version.  Wait your on edgy right or are you using dapper?

---

### Post by trubblemaker on 2006-10-31
you know what I changed my mind blacklist the ipv6 as I said above and while your at it for sure do 
```
 ndiswrapper -m 
```

if that doesn't work (after reboot for good measure) then try the howto.

---

### Post by ctopkelly on 2006-11-01
Right now i am using Dapper.  but i am going to upgrade to the latest version

---

### Post by ctopkelly on 2006-11-01
I know i am going to sound stupid but your first request was

```
sudo vim /etc/modprobe.d/blacklist
```not sure that i can edit that file.  i know ther is a way i can just blacklist something form the command line.  Do you know what that is ?

your second request was

```
 ndiswrapper -m
```this is what i get

```
ckelly@ckelly-laptop:~$  ndiswrapper -m
modprobe config already contains alias directive

```do i need to put eth1 or waln1 after that to make the change?

one other thing.   how long have you been working with linux?

Thanks
Chris 
> ( you can lead a horse to water but i cant get the broadcom chip to work )

---

### Post by trubblemaker on 2006-11-01
think it's time to start of with a clean install from source 

that means removing all instances of ndiswrapper
```

sudo rmmod ndiswrapper
ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper*
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 

```
*stop* if you can think of anywhere else that their might be ndiswrapper parts lying around, now is the time to find and destroy them.

then get and install from source. 
```

cd ~
sudo apt-get install build-essential          # install's make among other things
sudo apt-get install linux-headers-`uname -r`  #needed so you can  build kernel modules
wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.37.tar.gz
tar -zxvf ndiswrapper-1.37.tar.gz
cd ndiswrapper-1.37
sudo make uninstall
sudo make uninstall
make 
sudo make install
sudo modprobe ndiswrapper
ndiswrapper -i /path/to/drivers/bcmwl5.inf
sudo ndiswrapper -m

```
 just paste the commands and all should be well.

*note* some users have reported they had to put 'ndiswrapper' at the bottom of '/etc/modules' so that it would load on boot.

---

### Post by ctopkelly on 2006-11-01
Ok my friend  Let me tell you what i did, i just went out and got the latest version of ubuntu (the Edgy Eft 6.10) and installed it on my computer.

So i think i am starting from scrach as you are talking about in your post.

Lost allot of things i was working on but not a big deal.

if there is something i should do different then your post please let me know.  I thought that being on the most uptodate so might have fixed things.

thanks
Chris

---

### Post by trubblemaker on 2006-11-01
clean install or update?

update
the above should work, (i upgraded from dapper, sucks as things broke. not a good upgrade)

install (recommended)
you may have to 'blacklist bcm43xx' if you did a clean install and you'd also need to find the drivers for you wireless card again.

I still recommend making from source and above instructions should do that without an issue.

---

### Post by ctopkelly on 2006-11-01
```
sudo apt-get install linux-headers-`uname -r`
```

when i type this i get 

```
-laptop:~$ sudo apt-get install linux-headers-'uname-r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname-r

```

what is uname-r part?  sorry dont mean to sound stupid.
ctop

---

### Post by ctopkelly on 2006-11-01
it is a clean install

ctop

---

### Post by trubblemaker on 2006-11-01
awesome clean installs rule 
it's a back-quote [`] not a quote[']
```
 sudo apt-get install linux-headers-`uname -r`
```
it just gets you the name of your current kernel.
if you paste it as is it'll run

---

### Post by ctopkelly on 2006-11-01
> **trubblemaker said:**
> awesome clean installs rule 
it's a back-quote [`] not a quote[']
```
 sudo apt-get install linux-headers-`uname -r`
```
it just gets you the name of your current kernel.
if you paste it as is it'll run

when i run
 
```
chris@MyOwnGeek-laptop:~/ndiswrapper-1.28$ ndiswrapper -i ~/Desktop/bcmwl5.inf
```
bash: ndiswrapper: command not found

???
ctop

---

### Post by trubblemaker on 2006-11-01
and all the previous steps ran without error?  can you run and post the out put and yes I want you to run uninstall twice

sorry mixed up the order on some steps
```
 
sudo make install
ndiswrapper -i /path/to/drivers/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```
should have been
```
sudo make install
[COLOR="Red"]sudo modprobe ndiswrapper
ndiswrapper -i /path/to/drivers/bcmwl5.inf
[/COLOR]sudo ndiswrapper -m

```
my bad

---

### Post by ctopkelly on 2006-11-01
this is what i got.  but i think i got something diffrent the first time.  does this mean it is already installed?

```
chris@MyOwnGeek-laptop:~/ndiswrapper-1.28$ sudo make install
make -C driver install
make[1]: Entering directory `/home/chris/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/chris/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a 2.6.17-10-generic -b /
make[1]: Leaving directory `/home/chris/ndiswrapper-1.28/driver'
make -C utils install
make[1]: Entering directory `/home/chris/ndiswrapper-1.28/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:219: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:219: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:221: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:223: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:224: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:226: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:232: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:234: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:234: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:234: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:252: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:254: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:262: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:264: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:270: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:270: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:274: warning: implicit declaration of function ‘memset’
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:275: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:283: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:283: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:285: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function ‘stat’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:320: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:321: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:285: warning: unused variable ‘statbuf’
loadndisdriver.c:347: error: expected expression before ‘struct’
loadndisdriver.c:349: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:351: warning: implicit declaration of function ‘free’
loadndisdriver.c:358: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:371: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:374: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:377: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:378: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:380: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:380: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:403: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:371: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:415: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:415: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:420: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:422: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:425: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:430: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:431: error: dereferencing pointer to incomplete type
loadndisdriver.c:432: error: dereferencing pointer to incomplete type
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:444: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:461: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:461: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:469: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:469: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:470: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:470: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:485: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:486: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:486: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:486: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:488: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:493: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:509: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:509: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:513: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:515: warning: implicit declaration of function ‘printf’
loadndisdriver.c:515: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:525: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:540: warning: implicit declaration of function ‘atof’
loadndisdriver.c:547: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:554: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:588: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/chris/ndiswrapper-1.28/utils'
make: *** [install] Error 2

```

This i get this
```
chris@MyOwnGeek-laptop:~/ndiswrapper-1.28$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/misc/ndiswrapper.ko): Operation not permitted

```

and then this
```

chris@MyOwnGeek-laptop:~/ndiswrapper-1.28$ ndiswrapper -i ~/Desktop/bcmwl5.infbash: ndiswrapper: command not found

```

then
```
chris@MyOwnGeek-laptop:~/ndiswrapper-1.28$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found

```

Ctop

---

### Post by trubblemaker on 2006-11-01
looks like make never worked.  you need to run 
```

cd ndiswrapper-1.28
sudo make clean
sudo make uninstall
sudo make uninstall
make 
sudo make install
sudo modprobe ndiswrapper
ndiswrapper -i /path/to/drivers/bcmwl5.inf
sudo ndiswrapper -m

```
and post the output to me or check that all ran without errors, make sure to run "sudo make uninstall" twice this time. as you didn't install for some reason last time.  If the make step fails then their may have been an issue installing your kernel source

---

### Post by ctopkelly on 2006-11-02
the strangest things are happing my wireless card worked last night but today it is not showing up in the network App.  

when i do a ndiswrapper -l 
```
installed drivers:
bcmwl5,inf      invalid driver!
```

if config gives me this
```
th0      Link encap:Ethernet  HWaddr 00:C0:9F:B9:58:7E
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4313301 (4.1 MiB)  TX bytes:796894 (778.2 KiB)
          Interrupt:50 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

iwlist scan gives me this
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

also when i try to uninstall the bcmwl5.inf driver i get this
```
couldn't delete /etc/ndiswrapper/bcmwl5.inf

```

I have no idea.  i want this to work so bad 

Ctop](*,)

---

### Post by robin.w on 2006-11-02
Hey ctopkelly :-k ,

I also used ndiswrapper approx. 3 days ago and unfortunately I lost my wi-fi interface eth1, too!!! I checked all lists (lspci, modprobe) and everything seems to be fine but you know. ](*,)  It's awful. 

If you get any idea how to fix it please let me know.

---

### Post by ctopkelly on 2006-11-02
if i get anything i will post it for you

this is killing me 

ctop

---

### Post by trubblemaker on 2006-11-02
you need to remove the invalid driver and install the good one again.

there is a way to manually delete the "driver" it actaully just a folder located somewhere, sorry can't remeber where, I'll do a find and post back in a second.  

you should remove the driver, and then try to install the correct one, then modprobe ndiswrapper.

```
 dmesg | grep ndis 
``` will probably show some errors.

---

### Post by ctopkelly on 2006-11-02
yes i see this folder under etc/ndiswrapper/bcmwl6.inf   just delete the folder and reinstall the driver?

one other thing if you want to delete the folder in a file browser how do you do that?  it keeps telling me i do not have the rights.  or how do you get the root rights while doing that?

Thanks
ctop

---

### Post by trubblemaker on 2006-11-02
found it 
```

rm -r /etc/ndiswrapper/bcmwl5,inf

``` should get rid of your bad driver, then you just have to follow the rest of the above post
*note to others *
```
rm -r /etc/ndiswrapper/<name of driver> 
``` will remove other bad drivers

---

### Post by trubblemaker on 2006-11-02
> **ctopkelly said:**
> yes i see this folder under etc/ndiswrapper/bcmwl6.inf   just delete the folder and reinstall the driver?

one other thing if you want to delete the folder in a file browser how do you do that?  it keeps telling me i do not have the rights.  or how do you get the root rights while doing that?

Thanks
ctop

just do it in a terminal

sudo rm -r /etc/ndiswrapper/<bad driver>

---

### Post by ctopkelly on 2006-11-02
i just have one question. 

i just removed the driver and installed a new one but when i run the command

sudo ndiswrapper -m
modprobe config already contains alias directive

This is what i get?  is this right?

I am going to reboot and let you know what happens

Ctop

---

### Post by trubblemaker on 2006-11-02
that is the expected behavouir yes, if you've already done it once.
good luck

---

### Post by trubblemaker on 2006-11-02
FYI reboot are rarely necessary in linux, as we can load and unload drivers, unlike windows, only if you want to test boot time settings, or don't feel like stoping and starting a service.

---

### Post by ctopkelly on 2006-11-02
OK after reboot i checked the network app and it was there!!!!

then i did a sudo iwlist scan and got this
```
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:30:BD:63:A0:82
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:06:25:3C:1A:FB
                    ESSID:"NJPRWAP01"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:06:25:67:1C:C6
                    ESSID:"Audiology"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:12:17:A2:66:60
                    ESSID:"linksys-g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

looks like it is up and running.  great  i wounder what happend today and why it worked last night and not today?  clueless.....

Ctop

---

### Post by trubblemaker on 2006-11-02
probably some wierd driver loading thing, 

now there is the matter of my fee.  You have to at one point in your life, not necessarily today or tomorrow, help someone fix a problem on a forum. And  one day add something to a howto on a wiki. (not write a wiki-page but help contribute even if it's only one line)

Glad to have you one step closer to tossing windows out.

---

### Post by ctopkelly on 2006-11-02
> **robin.w said:**
> Hey ctopkelly :-k ,

I also used ndiswrapper approx. 3 days ago and unfortunately I lost my wi-fi interface eth1, too!!! I checked all lists (lspci, modprobe) and everything seems to be fine but you know. ](*,)  It's awful. 

If you get any idea how to fix it please let me know.

we worked out the answer to my problems.  you may wnat to read the post and fix yours.  what driver are you using?  first thing i did was delete the folder under /etc/ndiswrapper/bcmwl5.inf
then ran 
sudo ndiswrapper -e bcmwl5.inf
then reinstalled it
sudo ndiswrapper -i /path to the driver/bcmwl5.inf

i rebooted but i was told you dont have to reboot much in linux.  ( old windows habit)

if you have any questions let me know i am not the best but i just worked this whole thing out over the past two day.

latter

Ctop

---

### Post by freshmaker on 2006-11-06
I am abslolutely green newbie using Ubuntu or any kind of Linux for the first time in my life. I isntalled it on my Gateway 7430JP which is the Japanese version of Gateway 7510GX Laptop. Initially my Wireless Lan did not want to start at all. I tried everything I could find in ubuntu forums but nothing worked for me. I was almost desperate when I found this  [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) it took me not more than 5 minutes and ... everything went just the way it had to be. I am so excited now... 8) 
thank you ... :D

---

### Post by StormGuy on 2006-11-07
I attempted to follow the guide, but it's not working for me.  Whenever I ndiswrapper -l, it tells me that bcmwl5 and bcmwl5.inf are invalid drivers.  If I try to use the wireless config commands, it fails to find any wireless devices.  I have uninstalled ndiswrapper, attempted to uninstall the drivers (it won't let me, telling me it can't unlink them), and rebooted.  I've done these things in as many different orders as I can think of and also restarted at the beginning of the guide several times.

I'm a complete newb, so it's likely that I just don't really understand what I'm doing, and in trying to follow instructions, left something important out that was implied, but I failed to pick up or...I don't know. ](*,)

Sorry about the vagueness.  I know I have a broadcom 4311 card and that it is integrated into my machine.  I know the machine initially detected it when I installed Ubuntu, but now it isn't.  Other than that, I'm kinda lost. :confused:

This is the most recent thing I tried:

opus@Serenity:~/Desktop$ sudo ndiswrapper -i bcmwl5
Installing bcmwl5
couldn't copy bcmwl5 at /usr/sbin/ndiswrapper-1.8 line 144.
opus@Serenity:~/Desktop$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

edit: Oh...wasn't using sudo.  That's why I couldn't remove em.  Well, I can remove them now, but it still insists they're invalid when I attempt to reinstall them.

I then tried this:

opus@Serenity:~/Desktop$ sudo ndiswrapper -i bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
opus@Serenity:~/Desktop$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

:(

---

### Post by trubblemaker on 2006-11-07
did you remove the old driver first?
I suggest 
```
 sudo ndiswrapper -e bcmwl5 
ndiswrapper -l
[code]
if it's uninstalled great !
other wise to manually uninstall it.
[code] sudo rm -r /etc/ndiswrapper/bcmwl5 
```
make sure the old bcm43xx driver is blacklisted.
then add the new driver and reboot.
then try and see if the card is recognized.

---

### Post by StormGuy on 2006-11-07
```
opus@Serenity:~$ sudo rm -r /etc/ndiswrapper/bcmwl5
opus@Serenity:~$ ndiswrapper -l
No drivers installed
opus@Serenity:~$ sudo ndiswrapper -i bcmwl5
Installing bcmwl5
couldn't copy bcmwl5 at /usr/sbin/ndiswrapper-1.8 line 144.
opus@Serenity:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
opus@Serenity:~$ 
```


It looks like I'm able to remove it...but it's still invalid.  Also, what is blacklisting?  Sorry...I'm completely new :(

---

### Post by trubblemaker on 2006-11-07
ok so couple things, with the bcmwl5.inf file do you also have the bcmwl5.sys file? It's not often explicilty mentioned that both files need to be in the same dircectory when you run 
```
 
ndiswrapper -i bcmwl5.inf

```
or pointed to like so
```
 
ndiswrapper -i /path/to/driver/files/bcmwl5.inf

```
secondly there is a native driver that is installed by default that 'causes issues with ndiswrapper. We blacklist the driver so it doesn't load and we can use ndiswrapper.  (for instruction on howto use the native driver, check the howto in my signature.)
the onliner to blacklist the native driver is:
```

 echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```
you can get more info on why the driver failed to load with 
```
 
dmesg | grep ndis

```
it would also be nice if you posted the output of that above command so I could further help you

---

### Post by StormGuy on 2006-11-07
That command doesn't seem to work for me

```
opus@Serenity:~/broadcom$ dmeg | grep ndis
bash: dmeg: command not found
```

---

### Post by mrpeanut on 2006-11-07
Does anyone know whether or not this method works with the AMD64 version of Edgy?  I was browsing through the bcmwl5.inf file and I saw that there was a section labeled AMD64 Specific.  I have a HP Pavilion dv2125nr Notebook.  I will attempt this method soon on the AMD64 version, and post whether it's successful or not.

---

### Post by MisterD on 2006-11-07
> **StormGuy said:**
> That command doesn't seem to work for me

```
opus@Serenity:~/broadcom$ dmeg | grep ndis
bash: dmeg: command not found
```

Just a typo, instead of **dmeg** substitute **dmesg** and that will work.

---

### Post by StormGuy on 2006-11-07
Ah, sorry.

```

opus@Serenity:/sbin$ dmesg | grep ndis
[   39.217198] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   39.315461] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

```

This is what I found in the log file the command mentioned:

```

opus@Serenity:/sbin$ cat loadndisdriver
#!/bin/sh

set -e

if [ -z "$3" ]; then
        echo "Error: no version specified!" 1>&2
        exit 1
fi

/sbin/loadndisdriver-$3 "$@"
opus@Serenity:/sbin$ 

```

---

### Post by trubblemaker on 2006-11-07
don't have my machine to check but the ndiswrapper your using looks old (1.22) I thought the version you installed was 1.8?  and just to confirm, the bcmwl5.sys file is in the same directory as the bcmwl5.inf?

also I think that ```
 dmesg | grep loadndisdriver 
``` might also be helpfull I didn't think they meant to cat loadndisdriver, that message looks like it would print for you using the wrong driver or missing the bcmwl.sys file.

---

### Post by StormGuy on 2006-11-07
Ah, before I installed all of the ndis packages in synaptic.  I went back and only installed Common and 1.8utilities.  Is that right?

Here's what I get now:

```

opus@Serenity:~/Desktop$ sudo ndiswrapper -i bcmwl5
Password:
Installing bcmwl5
couldn't copy bcmwl5 at /usr/sbin/ndiswrapper-1.8 line 144.
opus@Serenity:~/Desktop$ ls
bcmwl5.inf  bcmwl5.sys
opus@Serenity:~/Desktop$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
opus@Serenity:~/Desktop$ 

```

and

```

opus@Serenity:~/Desktop$  dmesg | grep loadndisdriver
[   39.315461] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

```

And yeah, both bcmwl5.sys and .inf are on my desktop.  Though, it's only them.  And this is where I do my ndissing

---

### Post by trubblemaker on 2006-11-07
I don't know how else to say it, but it dapper /deb apparently doesn't work with edgy and I've been helping alot of people that upgraded and are now broken.

I suggest installing it from source, follow [this post]("http://ubuntuforums.org/showpost.php?p=1699287&postcount=451") and it should only take 10 mins.  Ignore the blacklisting of ipv6 that's for a different issue.

---

### Post by StormGuy on 2006-11-08
That worked perfectly, thank you so much :)

---

### Post by trubblemaker on 2006-11-08
it's all about karma, now hopefully you will help someone some day,

---

### Post by dtlinker on 2006-11-12
Thank you. This fixed my broken wireless connection on a Dell Inspiron B130 after upgrading to Edgy.

---

### Post by Protoplasm on 2006-11-17
hi... look here's my problem

6 July 2006 Update
I haven't had a Broadcom card for many months, but I've been told this how-to doesn't work properly under Dapper. Here are a couple of links that have been passed to me - but I can't vouch for their quality.

[http://www.beginningubuntu.com/dappe...wifi_wor](http://www.beginningubuntu.com/dappe...wifi_wor) king
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Good luck. I'm very happy that this how-to has helped so many people in the past year or so.

Broadcom wireless cards are tricky to set up in ubuntu, and the forums are full of frustrated users seeking advice. Broadcom provide no Linux support (feel free to complain to your hardware vendor or choose a different card if you haven't yet shelled out your cash), but they can be made to work - and you're in the right place if you want to know how.

First, you need to find out if this How To is for you. Broadcom wireless cards come under many brand names and, in particular, are used in many Dell and Acer laptops. Look for the drivers supplied with your card (Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON); if you have a file called bcmwl5.inf or bcmwl5a.inf then keep on reading. You won't succeed without following these instructions!

0. Before you start, clear out any mess from existing failed attempts to use ndiswrapper. Note that you shouldn't use a root terminal to execute the code in this how-to; use a normal terminal session instead.
Code:

sudo modprobe -r bcmwl5 sudo rmmod ndiswrapper sudo apt-get remove ndiswrapper-utils sudo rm -r /etc/ndiswrapper/ sudo rm -r /etc/modprobe.d/ndiswrapper

Some of these steps may report errors; just ignore them.

1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop

2. Follow the advice given here under How to add extra repositories

3. Open a terminal session and enter this code. Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.
Code:

sudo apt-get install ndiswrapper-utils sudo ndiswrapper -i ~/Desktop/bcmwl5.inf sudo ndiswrapper -m for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done

4. Reboot your PC. On restarting, the light on your wireless card should come on. If not, try entering
Code:

sudo modprobe ndiswrapper

5. Your card is now working. Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings. Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one. You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK. The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK. Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana. If everything works, you can delete the file from your desktop.

13. You might notice that the signal strength applet doesn't work properly. This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled. Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.

(Note: This how-to has been updated to reflect all comments from the thread up to 19 April)


i do all the thing but when i restarta my pc and start on ubuntu i type

 sudo modprobe ndiswrapper

but nothing happend... i can't use my card and on the networking window it not appear...

 pls help mee...](*,)

---

### Post by trubblemaker on 2006-11-18
Protoplasm great that you posted.  Next time, it would help if you did something to show the difference between the steps you followed and your question.  like using indentations or something.

Now as per your question.

well define nothing happens:

In linux, nothing happening is a sign that things are working properly so you won't get any output from "sudo modprobe ndiswrapper".  Can you post the output of the following commands for me:
```

sudo ifup wlan0 # looking for ip address if you get one... your done
ifconfig        # lists interfaces currently 'up'
iwconfig        # lists wirless interfaces
iwlist scan     # tells you close wireless networks
cat /etc/network/interfaces  # lists interfaces that wakeup on boot
ndiswrapper -l  # lists ndiswrapper installed drivers
dmesg | grep ndiswrapper # looks for ndiswraper errors
lspci | grep controller  # tells me your physical wireless card

ping 192.168.1.1  # tests local network

```

this will help me to figure out where your at

---

### Post by Early Uiniverse on 2006-11-23
Hi, I am trying to set up Ubuntu 6.06 on Acer 5102 WLMi (dual booting with Windows). I decided to go with the 64bit version... And as almost everybody here I have a problem setting up the wireless. I've seen some really promising threads on the Broadcom cards but alas none worked so far although I reckon it is just my inexperience] :-? 

To make it short: 

1. I have a fresh install and I followed the steps in this howto

2. I manage to install the drivers bcmwl5.inf/sys at least judging from 

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

But I have a problem using this driver instead of the 43xx one. When I blacklist the 43xx there is n wireless interface eth1/wlan0 vanish :( 
As far as I can tell it is probably connected to  

dmesg | grep ndiswrapper
[   44.449928] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   44.485584] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

The other problem I noticed is that during the boot there is a message that some .conf file cannot be read...

Yet another issue I'm not sure about is which interface ndiswrapper works with is it wlan0 or eth1 can there be a clash?? No clue on this...

Hope someone can help... Thx

---

### Post by trubblemaker on 2006-11-23
> **Early Uiniverse said:**
> Hi, I am trying to set up Ubuntu 6.06 on Acer 5102 WLMi (dual booting with Windows). I decided to go with the 64bit version... And as almost everybody here I have a problem setting up the wireless. I've seen some really promising threads on the Broadcom cards but alas none worked so far although I reckon it is just my inexperience] :-? 

To make it short: 

1. I have a fresh install and I followed the steps in this howto

2. I manage to install the drivers bcmwl5.inf/sys at least judging from 

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

But I have a problem using this driver instead of the 43xx one. When I blacklist the 43xx there is n wireless interface eth1/wlan0 vanish :( 
As far as I can tell it is probably connected to  

dmesg | grep ndiswrapper
[   44.449928] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   44.485584] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
The other problem I noticed is that during the boot there is a message that some .conf file cannot be read...

Yet another issue I'm not sure about is which interface ndiswrapper works with is it wlan0 or eth1 can there be a clash?? No clue on this...

Hope someone can help... Thx
yes totally there is a clash.  both drivers try and work with the hardware at the same time.  

I think that you need to actually work with the red howto in my signature as it has 64-bit drivers.  It's really easy, I think it even comes with a script to do it all  for you.

---

### Post by Early Uiniverse on 2006-11-25
Thanks trubblemaker for getting back to me... I tried that howto by compwiz412 as the first thing but it didn't work. I then found out that there is no driver ndiswrapper can work with as I didn't install the bcmwl5.inf/sys drivers. If it is supposed to load any of the 64-bit drivers than it failed as there was no output on 

ndiswrapper -l

Should I install the bcmwl5.inf before executing the script ?

Thx

---

### Post by trubblemaker on 2006-11-25
To get the best answer you should post on that forum.  I'm not sure of the exact steps that script follows it's been a while.  I'm aware of it's success and have heard alot about it's ease of use.  I'm sure if you post to it you'll get more specfic help

---

### Post by StormGuy on 2006-12-14
I somehow managed to break my wireless after having it work for several months.  It happened right after I changed a setting in my bios so that it knew that my OS was plug-and-play.  I tried changing it back, and that didn't help.  I also tried removing and reinstalling ndiswrapper along with the wrapped driver for my broadcom card...still nothing :(

I went back through all the steps I went through to get to this point...but something is still wrong.

---

### Post by trubblemaker on 2006-12-20
You might need to install from source it's a good fix if this doesn't work, check my signature "ndis for form source"

---

### Post by mzweili on 2006-12-28
Hi,
I folowed exactly your instruction and got the following message:
marc@marc-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission non accordée

Could you give me a hint how to continue?

Marc

Acer 500sWMLI Ubuntu 6.10 64 bit

---

### Post by trubblemaker on 2006-12-29
it sucks but you can manually 

sudo gedit /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf 

and change the radio state

RadioState|1  --> RadioState|0

then close and save the file then you can continue with the steps.

---

### Post by mzweili on 2007-01-04
> **trubblemaker said:**
> it sucks but you can manually 

sudo gedit /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf 

and change the radio state

RadioState|1  --> RadioState|0

then close and save the file then you can continue with the steps.

Could you tell me what I have to edit?

NdisVersion|0x50001
Environment|1
BusType|5
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
mac_address|XX:XX:XX:XX:XX:XX
driver_version|Broadcom,02/11/2005, 3.100.64.0

Afterburner|0
antdiv|-1
ApCompatMode|0
BadFramePreempt|0
BTCoexist|0
ccx_rm|1
ccx_rm_limit|300
Channel|11
Country|
EnableAutoConnect|0
EnableSoftAP|0
frag|2346
FrameBursting|0
gpio0|-1
gpio1|-1
gpio2|-1
gpio3|-1
IBSSGMode|2
IBSSGProtection|2
IBSSLink|1
Interference_Mode|3
MPC|0
NetworkAddress|
NetworkType|-1
PLCPHeader|0
PowerSaveMode|0
PwrOut|100
RadioState|0
Rate|0
RoamDelta|1
RoamTrigger|-70
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
SSID|
WEP|
WME|0
WZCCoexist|0

Marc

---

### Post by trubblemaker on 2007-01-05
> **mzweili said:**
> Could you tell me what I have to edit?

NdisVersion|0x50001
Environment|1
BusType|5
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
mac_address|XX:XX:XX:XX:XX:XX
driver_version|Broadcom,02/11/2005, 3.100.64.0

Afterburner|0
antdiv|-1
ApCompatMode|0
BadFramePreempt|0
BTCoexist|0
ccx_rm|1
ccx_rm_limit|300
Channel|11
Country|
EnableAutoConnect|0
EnableSoftAP|0
frag|2346
FrameBursting|0
gpio0|-1
gpio1|-1
gpio2|-1
gpio3|-1
IBSSGMode|2
IBSSGProtection|2
IBSSLink|1
Interference_Mode|3
MPC|0
NetworkAddress|
NetworkType|-1
PLCPHeader|0
PowerSaveMode|0
PwrOut|100
[COLOR="Red"]RadioState|0[/COLOR]
Rate|0
RoamDelta|1
RoamTrigger|-70
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
SSID|
WEP|
WME|0
WZCCoexist|0

Marc

so that file was already edited... weird, ok I guess it's time to try out ndiswrapper, 

try 
```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo dhclient wlan0
```

---

### Post by itsjustarumour on 2007-01-08
Oops, please ignore this post - wrong thread!

---

### Post by thoman on 2007-01-18
Hello all
been through all the step given but my wireless still not working... spent hours/day looking for the right solution...and headache too...up until now I cannot taste the joy and freedom of wireless technology. Never give up....hoping that some fine day I will find the right answer to this problem, Hope to find Ubuntu angel to light up my wireless button heheh....:D 

anyone ..please do not hesitate to help.....


everyday is a good day
tho

My system was 
Acer Aspire 3000

---

### Post by trubblemaker on 2007-01-18
Hey I'll try and help please post :

```

lspci | grep Broad
cat /etc/modprobe.d/blacklist

ifconfig
cat /etc/network/interfaces

iwconfig 
iwlist scan

ndiswrapper -l
dmesg | grep ndis

```
and I'll try and figure out what ails you.

---

### Post by emil0r on 2007-02-13
And another needing help :/.

Install works fine. Done it with both the install script and the instructions in this set. Distribution is Dapper.

lspci | grep Broad
> 
0000:06:05.0 Network Controller: Broadcom Corporation BMC4318 [AirForce One 54g] 802.11g Wireless Lan Controller (rev 02)


cat /etc/modprobe.d/blacklist
blacklist on:
> 
evbug
usbmouse
usbkbd
eepro100
de4x5
eth1394
snd_intel8x0m
i2c_i801
bcm43xx


ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:0A:E4:E8:17:27
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fee8:1727/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3879 (3.7 KiB)  TX bytes:6175 (6.0 KiB)
          Interrupt:66 Base address:0x6400

eth1      Link encap:Ethernet  HWaddr 00:14:A4:3C:86:40
          inet6 addr: fe80::214:a4ff:fe3c:8640/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:c0204000-c0206000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:256 (256.0 b)  TX bytes:256 (256.0 b)

cat /etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iwconfig 
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

ndiswrapper -l
> Installed ndis drivers:
bcmwl5          driver present, hardware present
dmesg | grep ndis
> [17179589.404000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179589.480000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179589.492000] ndiswrapper: using irq 177
[17179590.496000] wlan0: ndiswrapper ethernet device 00:14:a4:3c:86:40 using driver bcmwl5, 14E4:4318:1468:0311.5.conf

---

### Post by trubblemaker on 2007-02-13
well except for the small issue of your car coming up as eth1 (not really and issue) everything looks great.

Everything looks perfect.  It looks so good that I wonder if you have encryption setup on your router.  or maybe if you aren't broadcasting your essid.  that would make it appear as though it wasn't there but it is....

hope this helps to point you in the correct direction.

If eth1 continues to be your wireless connection you will need to fix your /etc/network/interfaces file fixed.

---

### Post by emil0r on 2007-02-13
Did a fresh install of 6.06.1 AMD64 Ubuntu and used the install script in your sig. Really miffed about this :(. Had it working on a 5.10 version about a year ago and then did a lot of OS swapping on the machine. Goes back and it no longer works :<. Any better chance of having it work on a 6.10 install?

dmesg | grep ndis

> [   95.433127] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   95.439743] ndiswrapper (load_pe_images:571): fixing KI_USER_SHARED_DATA address in the driver
[   95.441164] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   95.451230] ndiswrapper: using irq 177
[   96.453266] wlan0: ndiswrapper ethernet device 00:14:a4:3c:86:40 using driver bcmwl5, 14E4:4318.5.conf



sudo ifup wlan0
> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


---

### Post by trubblemaker on 2007-02-13
yeah, as I said above your wireless card is comming up under eth1 not wlan0.  And don't use 
```

sudo ifup eht1 

```
as you don't have eth1 setup in /etc/network/interfaces, so ifup won't work.
use:
```

sudo dhclient eth1

```
if you want it to be wlan0
add
```

wlan0 driver ndiswrapper

``` 
to you /etc/iftab file
```
 sudo gedit /etc/iftab
```

---

### Post by emil0r on 2007-02-13
sudo dhclient eth1

> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a4:3c:86:40
Sending on   LPF/eth1/00:14:a4:3c:86:40
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by trubblemaker on 2007-02-13
looks like your driver is working perfectly, I again suggest that you need to investigate the wireless router settings,

check if encryption is enabled
check for a wireless filter be turned on

to start with it would also be beneficial to broadcast your essid, until you have things up and running properly.

Can you connect to this wireless connection with another system (boot into some other OS if you have dual boot.)


also with wireless you need to set the essid before attempting to get an ip, my bad for not mentioning that

```

sudo iwlist scan

```
pick an essid
```
 
sudo iwconfig eth1 essid <your-essid>
sudo dhclient eth1

```

---

### Post by emil0r on 2007-02-14
The router has no keys set on the wlan and it's up and running according to the router. I can't check it on any other OS unfortunately.


sudo iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.


sudo iwconfig eth1 essid sweet0
> no output

sudo dhclient eth1
> 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a4:3c:86:40
Sending on   LPF/eth1/00:14:a4:3c:86:40
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by trubblemaker on 2007-02-14
yeah I'm going to say that you need check your getting a signal, or go to someplace you know has wireless and see if your laptop can see a signal.

```

iwlist scan

```

will tell you.  

Then you can rule in/out the router.

---

### Post by goldeneyeonline on 2007-02-15
Hey guys,

I now tried for several days to get my WPC54g v3 working with ubuntu edgy but always failed.
I installed ndiswrapper 1.22 and ndiswrapper-utils-1.8 and I took the right *.inf file (bcmwl5a.inf) for my card.
The installation and everything worked fine, the lamps are ON and I can activate the card in System->administration->network
But it just does not work... also it does call itself eth1 instead of wlan0...
I tried everything (I think i re-installed ndiswrapper at least 10 times with 3 different versions) but I wasn't able to fix it...
Anyone can help????:( 
would be really happy to find someone who knows what to do :)
THANK YOU!
Goldeneyeonline

---

### Post by emil0r on 2007-02-18
> **trubblemaker said:**
> yeah I'm going to say that you need check your getting a signal, or go to someplace you know has wireless and see if your laptop can see a signal.

```

iwlist scan

```

will tell you.  

Then you can rule in/out the router.

Router works fine. Posting this from my windows computer for which I bought a USB Wireless stick :\.

---

### Post by IkimashoZ on 2007-03-07
Hi, I've got a broadcom wlan card issue that I'm very anxious to get solved b/c my cable net hook-up is due to disappear any day now (the beaurocrats at the town hall have decided that they don't want any non-city-issued PCs hooked up the fancy new intranet they're installing).  I'm new to ubuntu and don't know much about working in linux, but I do have some programming experience.  Please bear with me.

I followed this how-to, and it seemed to be working, right up until the for loop in step 3.  Then this happened: [screenshot]("http://www.ikimashoz.com/0.png").

I've still got no lights or response from my card, and wlan0 does not appear as an option in connection properties.  I'm running Ubuntu 6.10.

---

### Post by navig8r on 2007-03-07
sweet after 4 hours at this I finally got it working thanks to you.....my first days with Ubuntu..wooohooo

---

### Post by Rhcd67 on 2007-03-20
Hello.  I am trying to get a Dell Wireless 1370 card on an Inspiron 600m to work.  I have followed the how-to but when I enter ```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
```
 I get:

```
:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:1028:0407.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
```


Any idea what is wrong?  Any help would be greatly appreciated.  Thanks.

---

### Post by Wolfhound23 on 2007-03-20
just install Ubuntu v6.10 on my Dell 600M laptop also.  Having the same problem at Rhcd67 with premission being denied

Ideals?  Comments?

Help.

Thanks

---

### Post by bytesmythe on 2007-03-21
YES!!!!! THANK YOU!!!!!!!!!

This reply gratefully composed via my newly working Broadcom 4318 wifi connection.

---

### Post by awthomp on 2007-04-01
I am running Fiesty Fawn and followed the setup post by the letter.

My card is recognized and I can see wireless networks under the network manager (it's also shown as wlan0), when I try to connect to one, however, it gets "stuck" at Activation stage: Configuring device.  Any suggestions as to how to connect?

---

### Post by Sokraates on 2007-04-03
Is there a router with WPA-encryption involved? If so, you won't have much luck, since wpa_supplicant is broken. Try an access point with WEP-encryption (or change it in your router, if you've got one). Then it should work with ndiswrapper. It should even work with bcm43xx, though it's less than stable.

---

### Post by awthomp on 2007-04-10
I have it set to filter by MAC addresses.  Wireless worked fine with the fixes posted in this forum on 6.10, but not on 7.04.  In the meantime, I've downgraded back to 6.10 since I use wireless frequently.

---

### Post by whitea on 2007-04-11
I'm not sure what I did wrong.  The light is now on but it doesn't show up in the network settings.  It used to at least show up and the light was always off.  Help!!!:confused:

---

### Post by whitea on 2007-04-11
Now the light is off again and the wireless is showing up as Eth1 in my network manager.  I'm not sure what I have done wrong now.

---

### Post by awthomp on 2007-04-19
Try to completely start over by typing in the following:

```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

Then follow the instructions given in the forum.

---

### Post by crwys on 2007-04-19
Hi i just joined the fourm.  My brother used someone else's wireless network with their premission.  After using it, he tried to connect to our wireless internet and it didnt work.  It keeps on saying, " Limited or no connectivity "  I know 100% sure the password is right.  But we are using a linksys router and it worked just fine before he connected to someone elses wireless interent.  For some reason the ip adress keeps on setting its self up to 169.254.226.68
I reseted the linksys router to its default settings, but it didnt help the problem.  We also tried hooking an ethernet cord up to the computer.  It went to the same ip adress.  I know how to manually set it up, but for some reason it wont work.  It will say, Linksys connection Excelent.  Connection speed 54.0 mbps.  I tried updating the driver.  Running system restore.  When it connects to the internet its suppose to look like somthing similar to this.

Ip adress>> 192.168.1.### (3 digets between 100-105)
Subnet mask>> 255.255.255.0
Default gateway>> 192.168.1.1
DNS server>> 68.87.76.178
Alternate DNS server>> 68.87.78.130
WINS server>> N/A

It should look something similar to this, when he connects to our wireless router.  If you need the routers model number please post that you do.  

:guitar: :mad: :lolflag: :confused: :( :) :popcorn: :KS

---

### Post by leonri on 2007-04-21
I have tried everything and that's all I've got.

leon@leon-laptop:~$ sudo apt-get install ndiswrapper-utils
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências       
Lendo informação de estado... Pronto
O pacote ndiswrapper-utils não está disponível, mas é referenciado por outro pacote.
Isso pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte
No entanto, os pacotes a seguir o substituem:
  ndiswrapper-common
E: O pacote ndiswrapper-utils não tem candidato para instalação
leon@leon-laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
leon@leon-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

leon@leon-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:12F3:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1355:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1356:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1357:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1358:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1359:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:135A:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:00E7:0E11.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:12F4:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:12F8:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:12FA:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:12FB:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:12F9:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:12FC:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:12FD:103C.5.conf: Permissão negada
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permissão negada
leon@leon-laptop:~$ 

Please, I need some help!

Obs.: "Permissão negada" is the portuguese for "Permission denied".

---

### Post by jaldred1 on 2007-04-21
I am one of the unfortuantes that also have a broadcom wireless card in my laptop.  I am about to install Ubuntu 7, has anyone tried to see if Broadcom works with this version of Ubuntu?

---

### Post by Sokraates on 2007-04-24
> **jaldred1 said:**
> I am one of the unfortuantes that also have a broadcom wireless card in my laptop.  I am about to install Ubuntu 7, has anyone tried to see if Broadcom works with this version of Ubuntu?

It depends on what card you have. 

I have bcm4318, one of the most tricky ones to setup, and it worked well (though by now I now what to do, so setting it up takes me but a few clicks). The native bcm43xx drivers work after adding the firmware, though very slowly. Ndiswrapper always did the trick for me, though now I can't connect to WPA-PSK-encrypted connections.

Best search for your card (e.g. 4318 in my case) in the forums and see, what you can find.

---

### Post by Average_Jake on 2007-05-10
I there, im about to pull the last strands of the hair on my head out...i just installed Ubuntu 6 on my Dell 600m laptop which is equipped with 1350 PCI wirless Card : 14e4:4320 : broadcom chipsets.

I have tried all of the aforemention links with so success:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")

I dont know where to start anymore, i've reinstalled 4 times and tried numberous fixes on the fresh install.

I know my linksys router is in working order.  It connected fine with Windows XP, I didn't change any settings...then i changed all the settings, No WEP, with WEP, changed network name etc...

My wireless card is 'enabled', and the "hardware is present" im currently using the bcmwl5a driver, tried the bcmwl5 without success (hardware not detected).  Something of annoyance, is everytime i open "network settings' the 'wireless connection' is always in the "Inactive" State...

umm....help!

---

### Post by Average_Jake on 2007-05-10
lspci

0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

ndiswrapper -l

Installed ndis drivers:
bcmwl5a         driver present, hardware present


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"connect"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:C5:DF:31
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7304 (7.1 KiB)  TX bytes:7304 (7.1 KiB)

---

### Post by hairyharry7 on 2007-05-21
hello, and thanks for the help in advance - I've gone over this tutorial and read some of the problems people have posted but I still can't get my wireless to work.  I get the same error message discussed on pages 2-4 in this thread.  it says -
> 
thedon@thedon:~$ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
thedon@thedon:~$ 

I tried removing and reinstalling like in step 0 but it still didn't work - I'm using edgy - Any suggestions? (Also I didn't need to change RadioState|1 to RadioState|0 because they were already like that, I don't know if that means anything :confused:)
Thanks

---

### Post by InfinityCircuit on 2007-05-27
In Ubuntu 7.04, whenever I try to change the .config files, there is nothing called "RadioState|1" to begin with.  My wireless still does not work.  Could this be a source of an error?

Similarly, if i try sudo modprobe ndiswrapper, it gives me an error:
FATAL: module ndiswrapper not found.

I have a wonderful BCM4318.

EDIT: My wireless is now working.  After I did what this article suggested I restarted.  No change.  I decided to try again with PCLinuxOS.  The LiveCD crashed, so I restarted into Ubuntu.  Suddenly, everything worked.

---

### Post by jargoman on 2007-06-02
I've put up a new how to. This one will compile ndiswraper and works for me every time. Fairly easy and straight foreward. 

[http://freeshells.ch/~jargoman/](http://freeshells.ch/~jargoman/)

---

### Post by Christopher Williams on 2007-06-03
This didn't work for me but the information in the following link did:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I used the bcmwl5.sys as opposed to the .o driver mentioned

basically:
1: Obtained windows drivers (bcmwl5.inf and bcmwl5.sys)
2: #sudo apt-get install bcm43xx-fwcutter
3: #sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/bcmwl5.sys
4: #sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/bcmwl5.sys
5: reboot

it all worked after that.

---

### Post by scottvan on 2007-06-14
Hey just wanted to say thanks for your link to HOWTOBroadcom..   it worked perfectly for me!  :)

---

### Post by bluecricket4400 on 2007-06-27
I do not have access to a wired network, how can I configure the Acer Aspire 3002LCi?

Thanks

I am new to this and only understand about half of what I have been reading...:(

---

### Post by plounted on 2007-07-14
hi. 
gone through the steps several times, and im to the point where the only problem i have is when i try to edit the .conf files, i get a permission denied message. what should i do?

is there a restriction i need to get rid of?

---

### Post by Sokraates on 2007-07-17
> **plounted said:**
> hi. 
gone through the steps several times, and im to the point where the only problem i have is when i try to edit the .conf files, i get a permission denied message. what should i do?

is there a restriction i need to get rid of?

A regular user is not allowed to edit system-files (actually, he's not allowed to edit anything outside of his home-folder and the tmp-folder). So you need to edit the file as administrator (aka super-user, aka root).

At least in KDE you can simply right-click on the file, select "root-actions" and the "edit with kwrite". Maybe GNOME also has this option, though there you'll use gedit.

From the command-line you will need to enter
```
sudo apptouse /path/to/file.conf
```

sudo will start the app as root. In any case, you will then be asked for a password. Simply enter your user password.

---

### Post by PePeR34GTR on 2007-07-18
I just downloaded Ubuntu and am looking to install it over windows on my Dell Inspiron 6400.

Sorry to post, but I kinda didnt want to go through the pages of the thread, is there an updated instruction guide on how to setup the wireless?

Thanks

---

### Post by Gwelmi on 2007-09-03
hi,

thanks a lot for this thread. I hope someone is still watching it.

I have been reading as much as could but couldn't get wireless to go.
Seems close, but no ... so frustrating. Posting as much info as i can below.

Thanks.

- Computer : Acer Aspire 3000 (3003LCi)

- dist : 7.04 feisty fawn.

- tried w/ both drivers bcmwl5.inf and bcmwl5a.inf as stated in some posts.

$ lspci | grep Broad
```

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
$ cat /etc/modprobe.d/blacklist
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

```
$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:DD:9B:B5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x1800 

eth0:avah Link encap:Ethernet  HWaddr 00:C0:9F:DD:9B:B5  
          inet addr:169.254.10.139  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13796 (13.4 KiB)  TX bytes:13796 (13.4 KiB)

```
$ cat /etc/network/interfaces
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```
$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
$ iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```
$ ndiswrapper -l 

```
bcmwl5a : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

```
$ dmesg | grep ndis

```
[  102.156000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[  102.216000] usbcore: registered new interface driver ndiswrapper

```
$ sudo dhclient eth1
```

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:14:a4:3a:60:4a
Sending on   LPF/eth1/00:14:a4:3a:60:4a
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Sokraates on 2007-09-03
I don't know, whether this is the sole problem, but first of all you will need to blacklist the builtin bcm43xx-driver (which became part of Ubuntu after this How-To was written).

Also I don't see any ESSID entered.

Alternatively, you can simply install the necessary firmware and keep using the bcm43xx (though it is less powerful, then the original drivers). Here you find how: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

And this is how I managed to make my bcm4318 work since Breezy: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Though after all your experiments it would be better to first clean up whatever you've changed and then proceed one command at a time (in the last example, simply copy them from the script). It may be possible that something other than the wireless driver is causing problems.

---

### Post by Gwelmi on 2007-09-03
Thanks for your reply.

> **Sokraates said:**
> I don't know, whether this is the sole problem, but first of all you will need to blacklist the builtin bcm43xx-driver (which became part of Ubuntu after this How-To was written).

Ok will try that. Should i just insert a line with 'blacklist bcm43xx-driver' ?

> **Sokraates said:**
> 
Also I don't see any ESSID entered.

Right. Not sure what to do here. 
- There is a roaming mode in which it seems it is not necessary to specify a ESSID. But as 'iwlist scan' does not give me any result, i guess this is useless.
- So i also tried to setup ESSID manually, but when i do 'iwconfig', only part of the ESSID i entered show : e.g. i enter "Wireless-G AP" and it only shows ...ESSID="Wireles" ...

Also what confuses me is that neither eth1 or wlan0 is present in 'ifconfig'.
As trubblemaker mentions in post 507 [http://ubuntuforums.org/showpost.php?p=2150471&postcount=507]("http://ubuntuforums.org/showpost.php?p=2150471&postcount=507") i tried to make wlan0 shows but no success.

> **Sokraates said:**
> 
Alternatively, you can simply install the necessary firmware and keep using the bcm43xx (though it is less powerful, then the original drivers). Here you find how: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

And this is how I managed to make my bcm4318 work since Breezy: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Though after all your experiments it would be better to first clean up whatever you've changed and then proceed one command at a time (in the last example, simply copy them from the script). It may be possible that something other than the wireless driver is causing problems.

The bad thing is that the wireless signal is a bit weak, as i am a little far from the source. So i'd rather use ndiswrapper with original drivers.

Anyway, i will download necessary file you mentionned here, Sokraates, boot back to ubuntu and give a go differents configs ...

thanks.
G.-

---

### Post by Gwelmi on 2007-09-03
> **Sokraates said:**
> I don't know, whether this is the sole problem, but first of all you will need to blacklist the builtin bcm43xx-driver (which became part of Ubuntu after this How-To was written).

Also I don't see any ESSID entered.

Alternatively, you can simply install the necessary firmware and keep using the bcm43xx (though it is less powerful, then the original drivers). Here you find how: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

And this is how I managed to make my bcm4318 work since Breezy: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Though after all your experiments it would be better to first clean up whatever you've changed and then proceed one command at a time (in the last example, simply copy them from the script). It may be possible that something other than the wireless driver is causing problems.
Yeess ! That was it ... the blacklist stuff ... 
Just added the line 'blacklist bcm43xx' into /etc/modprobe.d/blacklist and it worked !!
The interface 'wlan0' popped up perfectly and it could scan available networks around perfectly. No need to select any ESSID manually (used "Roaming profile" mode).

I think the feisty's bcm43xx new builtin module was also conflicting with my sooo dead battery power system, which seems to be resolved now.

Thanks so much Sokraates ! 
Posting this from Ubuntu thru wireless ... such a long time i was waiting this ... This is sooo gooood !
G.-

---

### Post by beleth on 2007-09-04
It feels so close x.x

working with Ubuntu 7.04 on an HP laptop of indeterminate origin, lspci returns "Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card".

I can't directly copy my code output because I'm posting from my gimpy windows laptop, but I've worked through the steps of the tutorial and everything seems to be similar in all respects to Gwelmi's setup a few posts up, except under iwconfig where my output looks like

lo  no wireless extensions.

eth0  no wireless extensions.

eth1  IEEE 802.11b/g ESSID:off/any  Nickname:"Broadcom 4311"
         same from here

and also under ndiswrapper -l, where I only get "bcmwl5: driver installed" with no mention of hardware

also, dmesg | grep ndis gives no output

driver installed was bcmwl5.inf, bcm43xx has been blacklisted, and my wireless connection is visible in NetworkManager Applet.

I'm hoping I've done something dumb and easily remedied...

Much respect to the people who have been participating in this thread so far, its been an extraordinary help.

---

### Post by beleth on 2007-09-04
finally found a landline, so here is the proper information

HP 530 Notebook running Ubuntu 7.04

~$ lspci | grep Broadcom
```

10:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
```

~$ cat /etc/modprobe.d/blacklist
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

blacklist bcm43xx

```

~$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:16:D4:EA:0E:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1460712 (1.3 MiB)  TX bytes:184988 (180.6 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:16:D4:EA:0E:EE  
          inet addr:169.254.9.91  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1038 (1.0 KiB)  TX bytes:1038 (1.0 KiB)
```

~$ cat /etc/network/interfaces
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0




iface eth1 inet dhcp
wireless-essid omgwtfbbq?



auto eth1
```

~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

~$ iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```



~$ ndiswrapper -l
```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```



~$ dmesg | grep ndis
```

[   20.296000] ndiswrapper version 1.47 loaded (smp=yes)
[   20.352000] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[   20.352000] usbcore: registered new interface driver ndiswrapper

```
^this part seems important, but I'm not exactly sure how to proceed x.x

~$ sudo dhclient eth1
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

I realized earlier that I'd made a typo when blacklisting the bcm43xx driver, and as soon as I'd corrected it I could no longer access my wireless card from the gui. Along with the dmesg | grep ndis output, that makes me think that my card is without a driver at the moment. 

But I'm probably missing the point entirely x.x *first day using linux*

---

### Post by beleth on 2007-09-05
I suppose it should go without saying that one should get drivers matching one's computer, but let me say it so that no-one need waste time like I've been doing: not every copy of bmcwl5.inf and bmcwl5.sys is the same. Get the drivers for your computer model, or risk wasting lots of time and looking rather silly for it afterwards ](*,)

I am, however, proud to say that my second day as a linux user finds me with a working wireless connection. Now I can finally sleep \\:D/

---

### Post by Michael Allison on 2007-09-13
I'm using a TrueMoble 1300, and got confused when you sent us off site.

Apparently we're supposed to install the repository Medibuntu?

I did that, and searched for Broadcom and found two things. Is one of those a script you meant for us to use?

:confused:

If so, I installed those two. Now onto step three:

michael@michael-laptop:~$ sudo modprobe -r bcmwl5
Password:
FATAL: Module bcmwl5 not found.
michael@michael-laptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
michael@michael-laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo: ndiswrapper: command not found
michael@michael-laptop:~$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found
michael@michael-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
michael@michael-laptop:~$ 

Did I do anything wrong? Because after restarting it, etc., the light still doesn't go on, and I'm not connected.

I also blacklisted that thing I was supposed to blacklist...

My third day of using Ubuntu, so bare with me? <3 lol

---

### Post by ldp205 on 2007-10-16
Hello.

When I 
sudo apt-get install ndiswrapper-utils
I end up getting 

Media change: please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter

I did install Ubuntu off of a CD - but I put it in hit enter and keep getting this message.

---

### Post by ldp205 on 2007-10-16
I just want to say that I´ve been going at it all day (trying to get my wireless card to look like it might work) and the only thing that I´ve accomplished is that the wireless connection icon has disappeared from System>Administration>Networking.
Some info:
IBM Thinkpad T23 laptop
Ubuntu 6.10 - Edgy
ndiswrapper 1.44
bcmwl5.inf driver

TIA for any help

---

### Post by heyster on 2007-11-08
The same for me ldp205.

But we must make help Ubuntu grow. That's why we must never give up.
As finishing touch God created the Dutch and Ubuntu.

This solution (including working links where you can download the driver) worked for my Lenovo 410a with a Broadcom card.

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

In the last hour of m holiday I got it working. Great!!

---

### Post by sbussy89 on 2007-12-13
HELP 
When I search my computer, it says I have no files called bcmwl5.inf or bcmwl5.sys.  Where do I get them????

---

### Post by sbussy89 on 2007-12-13
Embarrassing fix to my problem my problem... never loaded firmware in restricted drivers

---

### Post by dhl on 2007-12-21
Hello,
I am trying to use a wlan card based on a broadcom BCH4318 chip under Ubuntu 10.7. During install I have been following the instructions from here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
The bcmwl5.inf driver was successfully installed using ndiswrapper's ndisgtk. Note: lspci shows the wlan ID as 14e4:4318, here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) this ID is referenced to bcmwl5.sys and netg54s.inf drivers; bcmwl5.sys was present in my CD package, but I couldn't install it, while installing netg54s.inf in ndisgtk returned "Invalid driver!". So I have downloaded the bcmwl5.INF. 
But unfortunately there is still no wlan0 in ifconfig and no Wireless connection in Network utility.... What caould be the solutions to this problem?

---

### Post by Rafajafar on 2008-01-02
Same ^

I'm running a HP Pav dv2000 and I have quite literally been working on this all day to no avail. 

If you've got a forum post, I've probably seen it. 

My light on the wireless device does not turn on. I have the restricted driver registered. I have tried ndiswrapper and fwcutter. I have tried every crazy hack to get this to work I could find and none of them work.

I reinstalled the operating system 4 times just to be sure there were no artifacts from my attempts. I'm at a loss... where can I go for some help?

---

### Post by jan quark on 2008-01-03
you know what???

it didn't work but my internet connections is faster than ever.

when I say it didn't work I mean I have no wlanO device when I sudo iwlist scan
only my old eth0 is showing up

I used to or I am still using the bcm43xx firmware, but everything seems so much faster now.

There was also many disconnections in the past.

Until now not one.

I don't know if this is coincidence or if the installation of the drivers via the ndiswrapper as you have described it fixed something hidden in my configuration.

I will test my connection for a while and post back when I am sure that your guide really helped.

Now I am quite pleased with the result. I hope it will last long.

---

### Post by suman4674 on 2008-04-06
Trendnet TEW-444UB/A USB Wireless problem on UbuntuI


 am using following commands to install the Trendnet TEW-444UB/A USB Wireless .I am not getting any error.I can see the wireless Connection in Network settings and i have configured my ESSID correctly.Still i am not able to connect to internet.Any help will be appreciated

I removed the Device to reset the firmware and ran the below batch
lsusb
sudo rm -R /etc/ndiswrapper/*
cd Driver/
sudo ndiswrapper -i a*.inf
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo ndiswrapper -i n*.inf
sudo modprobe ndiswrapper
lsusb
iwconfig
/*****the output on terminal ****/
~$ sudo ndiswrapper -l
athfmwdl : driver installed
net5523 : driver installed
device (157E:3006) present

~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:"Kumar"
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by johnnyxxxcakes on 2008-04-14
I tried many things with your tutorial, but I don't think anything's working. I can't get it to work at all, unless I'm just doing something wrong on my end.

Is ndiswrapper a program I have to download? This it the result I get when I attempt your method:

sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.
john@john-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
john@john-laptop:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package ndiswrapper-utils
john@john-laptop:~$ sudo rm -r /etc/ndiswrapper/
rm: cannot remove `/etc/ndiswrapper/': No such file or directory
john@john-laptop:~$ sudo rm -r /etc/modprobe.d/ndiswrapper

I have the bcmwls5.sys and bcmwls5.inf files copied to the desktop, and nothing seems to work.

---

### Post by cameronschultz on 2008-05-17
okay, i know i am going to sound really dumb, but where do i imput the codes? i am brand new at this and i am trying to set up my internet on my hp pavillion dv6000, but i don't know how to download the software properly. sorry :/

---

### Post by CantRemember on 2008-06-20
I have a hp pavilion dv6000 with a broadcom-card. I've used this guide step by step but after I installed the bcmwl.inf (and .sys) it comes to a problem... My conf-files doesnt include "RadioState" so there's no value to change! And if I run:
 
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

All conf-files get empty! It seems that the drivers are correctly installed and if I typ "ndiswrapper -l" I see some messege like "bcmwl5 driver installed". The Dir "bcmwl5" also exists in the ndiswrapper Dir. Before I run the script the conf files includes alot of commands but there's no RadioState...
I'm a new ubuntu user and would appreciate if someone could help me with this because I really need the wireless-card to work.

---

### Post by Elliander on 2008-09-23
I am, sadly, using a broadcom but I have a few problems following the above.

For one, my computer only has: BCMWL5.SYS - there is no inf. Would it still work without the inf?

Two, I am only able to access using a wireless connection. But I have my computer in dual boot with Windows XP and that OS can read the internet just fine.

Is there a way to get it to work for those of us who can access the internet, but not in Ubuntu without first having a working wireless card?

And if not, if I bought a wireless card that supports Ubuntu (um.. any suggestions for a really good one that is also inexpensive?) would I also have to first have internet access in Ubuntu for it to work?

And.. um.. I actually don't understand the way we are supposed to install them. I am too used to windows. Are there any simple to understand guides for people to understand how to install in Ubuntu who are too used to Windows?

---

### Post by gaixixon on 2008-10-01
Hello, my laptop is Lenovo G410 with following LAN card:
Broadcom Corporation BCM4312 802.11b/g (rev 01)
Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

Wired connection is OK, wireless connection is OK when connects to AP WITHOUT password. When trying to connect to WPA protected it fails.

How do I make it connect to WPA encryption AP? I have wpa_supplicant installed. Do i need to install ndiswrapper? how?
thank you
gxx

---

### Post by kickwin on 2009-06-29
Another complete newbie having trouble with Dell Inspiron 1300 - Dell Wireless 1370 WLAN MiniPCI Card on Ubuntu 9.04. Tried many things posted in many forum posts and I have not got it working. Even uninstalled Ubuntu and switched to Xubuntu after a recommendation to do so. But I am now back to Ubuntu after finding out Xubuntu did not work either. Here are some details that may help you figure out what is wrong with my system. Thanks a lot guys.

lspci | grep Broad
> 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6c:05:df  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6c:5df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2654336 (2.6 MB)  TX bytes:435883 (435.8 KB)
          Interrupt:18
 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1528 (1.5 KB)  TX bytes:1528 (1.5 KB)
iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
iwlist scan
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
ndiswrapper -l
> 
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
dmesg | grep ndis
> 
[   12.408197] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.410984] usbcore: registered new interface driver ndiswrapper


---

### Post by kickwin on 2009-06-29
> **kickwin said:**
> Another complete newbie having trouble with Dell Inspiron 1300 - Dell Wireless 1370 WLAN MiniPCI Card on Ubuntu 9.04. Tried many things posted in many forum posts and I have not got it working. Even uninstalled Ubuntu and switched to Xubuntu after a recommendation to do so. But I am now back to Ubuntu after finding out Xubuntu did not work either. Here are some details that may help you figure out what is wrong with my system. Thanks a lot guys.


Sorry guys. I just had to go to System--> Administration --> Hardware Drivers and activate my Broadcom B43 wireless driver to get wireless working. Voila! But there is message in the dialog that says "The driver was just disabled, but still in use". I do not know what that is but I am happy that something got my wireless working after struggling for two days.

---

### Post by pablolie on 2009-07-03
i have followed every piece of advice i have found on getting my linksys wpc54g card to work in xubuntu 9.04 (it worked with ndiswrapper and ubuntu 8.04). 

supposedly here it is as simple as installing b43-fwcutter with synaptic, restarting and off you go. seems to have worked for others. not for me.
the system clearly is not using the card.

it is identified with
BCM 4306 
14e4:4320 rev 3

by the usual commands. but the hardware drivers system app does not see the card, nor do the networking applications see that another network card is available. 

any hints would be greatly appreciated.

---

### Post by pablolie on 2009-07-04
actually, a new install of xubuntu 9.04 while staying connected to the network (wired) solved the issue. the install suggested the driver all by itself, the wireless network works now. go figure. :-)

---

### Post by Carlmon on 2009-07-24
Modifying the modprobe and .conf files as well as using ndiswrapper I was able to get my Broadcom BCM94306MP working. What a PITA! Anyways...I love ubuntu. I have Karmic Koala installed on three of my computers at home. It is the shizzle-nizzle once you work out the kinks in any hardware. I would not recommend ubuntu for the computer-knowledge-challenged though. It definitely is not for the lay-person. Most dummies want plug and play capablilty like Windows. Lame!

---

### Post by Detroit_Bad_Boy on 2009-09-24
I followed the advice and used the commands. I opened a terminal and typed them in. This is what I got back

david@ubuntu:~/Desktop$ sudo apt-get install ndiswrapper-utils
[sudo] password for david: 
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package ndiswrapper-utils
david@ubuntu:~/Desktop$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo: ndiswrapper: command not found



david@ubuntu:~$ sudo modprobe -r bcmwl5
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release
FATAL: Module bcmwl5 not found
david@ubuntu:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
david@ubuntu:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Donefont-size: 16 pt
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils
david@ubuntu:~$ sudo rm -r /etc/ndiswrapper/
rm: cannot remove `/etc/ndiswrapper/': No such file or directory
david@ubuntu:~$ sudo rm -r /etc/modprobe.d/ndiswrapper


From what I see it seems to be saying that ndiswrapper doesn't exist. But when I do a file search it shows it in /lib
I should let you know that I do NOT have a DVD rom in this laptop (Compaq Presario M2000) and I installed Xubuntu 9.04 within windows, but it did create a partition for itself.
I am using a Broadcom BCM4318 chipset in the wireless controller.
I also noticed that it said 'E:'. I am not too familiar with linux and wondered if it could be referring to the flash drive I had plugged into the USB port at the time ? 
  Is there something I'm doing wrong here ?
Any help would be appreciated

NOTE: I THINK I may have pasted these 2 entries in the wrong order

---

### Post by squinter on 2009-11-09
Hi, Ubuntu 9.10 comes with restricted driver for broadcom :)

---

### Post by Justin90562 on 2009-11-26
[SIZE="3"]Can some one please write and up to date HOW TO because some of this code is obsolete.
 i am a First time Ubuntu user and i got it to kinda work but not really. When my card only turns on in only my user and only connects with Ad-hoc and then cuts out. when i searches all the names of the wireless net works are like all most wingdings and just alkfjaijflakjaijaljjakljklaj^^^wER#3a93 kinda like that. if i can get this to work i will write a new how to if no one wants to. i am  BCM4306/BCM2050 Rev.4.5[/SIZE]

---

### Post by hackedmind on 2010-02-05
WORKS LIKE MAGIC!!!!

Thank you so much! ^^

Maybe one day I'll be a great sorcerer like you, jonny  :P

---

### Post by Megaptera on 2010-02-05
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

This works on Dell Inspiron 1545 with _buntu 9.10 - used it several times - so hope it's of help to others?

---

### Post by muslim1 on 2010-03-30
guys ive been trying to get it to work for the past 3 days, used all alternatives like synaptics, bcw43, updates, third party drivers, and even tried to solve the karmic bug which wouldnt list third party at the hardware drivers things and nothing seems to solve it
heres the situation:



b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
cassiano@nb:~/networlk/network-manager-applet-0.8$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5a : driver installed
    device (14E4:4320) present (alternate driver: ssb)
cassiano@nb:~/networlk/network-manager-applet-0.8$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

cassiano@nb:~/networlk/network-manager-applet-0.8$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


the other guy who ha 4320 had to reinstall ubunto to get it working, will i have to do the same?

ive undone everything and tried bcmwl5 instead of bcmwl5a to no result, anyone has ANY thoughts on this one?

---

### Post by Canada Lee on 2010-04-24
I am running Ubuntu Karmic 9.10 (fresh install) on an Acer Aspire 3000 laptop with a Broadcom BCM4318 Airforce One 54g Rev 02 wireless...

I have wireless connectivity with the B43 driver showing up in the Hardware Drivers application. I have used fwcutter, and can't be certain it completed and downloaded the necessary firmware, as there is a known bug relating to it, where it has a YES / NO question about downloading the firmware, and once selecting YES it exits...without any explanations as to success or failure...search for that fwcutter bug, and you'll know what I mean.

Anyways, what I am experiencing like so many others with broadcom's are experiencing is connectivity with random disconnects. I have been trying to troubleshoot this for months, and I think we need to be digging deeper...not looking on the surface... Here's what I've found out...

Need to have a controlled environment, so...
Laptop is running on AC with battery disconnected to rule out any power saving modes or functions attempting to interfere with operation. Also, screen saver has been deactivated, and in power saving settings it is set while on AC to leave monitor on and never turn it off, and never spin down hard drives.

I have a big torrent downloading, and my wifi led light is flashing, and I have System Monitor running to show a graph of SENT & RECEIVED...when I see the LED light stop flashing (sometimes it may be off, or it may be on - but its state will remain constant, as in if its off, it stays off and doesnt fluctuate, if on, it stays on and doesnt fluctuate...and when I say the led may be off and stays in that state, I mean the wifi is on, but the led is blinking on and off to represent data xfer and the light just happened to be in the off state when it got HUNG UP.

When the led light gets stuck in whatever state, I know its about to loose connectivity, so I go to my terminal, and I >> ping -c 1 -I wlan0 [www.google.com]("http://www.google.com/") << and sure enough, the ping fails...so I do a >> sudo ifconfig wlan0 down << and if the led was stuck in the ON state, I will see the led go out, and the network manager starts scanning (it wont connect though till)...I then do a >> sudo ifconfig wlan0 up << and then the led light comes up...and the networking manager is still scanning and connects.

So...you dont have to do a reboot to get back your network connectivity...
So I made a little wireless script to KEEP-ALIVE the connection, and if lost, do the DOWN and UP command...sounds like it'd work you think...but makes me think something else may be causing the wireless to BE IGNORED...

Here's my keep-alive script...
#!/bin/bash
while [ 1 = 1 ]
do
if [[ ! `ping -c 1 -I wlan0 www.google.co.uk` ]]; then
echo "$(date)"
ifconfig wlan0 down
sleep 5s
ifconfig wlan0 up
sleep ${1}s
fi
done

I place it in my /usr/local/bin folder, make it executable...open a term, and run it with
sudo keep-alive 60
the 60 can be whatever you want it to be, it tells it to wait 60 seconds then ping, then wait 60 seconds then ping...it will run till you stop it with a CTRL-C...if a ping fails it will DROP the wlan0 interface, wait 5 seconds and then bring it back UP. It will also echo in the terminal the ping failure and the time and date.

Thing I noticed, the terminal window is open, my keep-alive is running (I even had it echoing the successful pings every 60 secs) and I can see my cursor blinking in the terminal window...but when I notice the wifi led light not blinking, I know it is going to loose connectivity...and the cursor in the terminal has stopped blinking, and it isnt echoing successful or failed pings, and the clock on the top panel has stopped updating...everything on the screen is frozen to a snapshot of when the wifi was working...if I hit the mouse touchpad, the cursor in the terminal starts blinking, the clock in the top panel updates, my torrent display updates. Its like the display went to sleep...and me touching the pad woke it...and it wasnt ASLEEP long enough for loss of connectivity, I know this cuz I waited longer before hitting the touchpad, and when that woke it, then I see a bubble saying disconnected from my network...and then the network manager scanning...and it wont connect, then my keep-alive script echoes a failed ping then drops the wlan and brings it up, and then the netman scanning connects...

But I know my keep-alive script was frozen, everything was frozen...no heavy CPU usage, just like asleep. and me touching the pad woke it from that sleep, and it continued where it was before the sleep...

What makes it sleep like that? What components of Ubuntu perform that job? It cant be the wifi driver just stopped communicating to the kernal, cuz me waking it by swiping my finger on the mouse touchpad should not be able to influence a modem communication driver...

On the other hand, a power savings mode, inactivity, screensavers and so on can be influenced by user input to interrupt their behavior.

So even when power savings is off, something is suspending things...and it is not at constant intervals, it is at random intervals. There is no overheating going on here, and the cpu in not throttling. I am using only max of 10% when torrent is dloading. And if there was overheating or throttling, who ever heard of influencing their state by swiping the touchpad!

Also, I have followed instructions from the following site to set up my firmware, as that site seemed to relate different scenarios for the b43legacy the b43 and the b43xx drivers (discriminating specific drivers for specific chipsets), while other sites seem to only use the b43 for all scenarios (no discrimination), or the b43xx for all scenerios (no discrimination)...

[http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp](http://wireless.kernel.org/en/users/Drivers/b43#fw-b43-lp)

I had the same connectivity with random disconnects before using the b43 provided by the Hardware Devices application, and after following that website.

No change in random disconnects...but it never disconnects when I'm at the laptop using it...because my every move keeps the computer in a state of being awake.

Its only once I have left it alone, that it seems to go to sleep (could be 6 hrs later, could be 20 seconds later) and when it does, everything even the screen display, and the wifi led light, just freezes or pauses...and will stay that way...and my keep-alive program wont save it, cuz it has stopped doing pings, cuz its been paused.

But I shouldnt have to be here to wake it from sleep.  There is no setting in the BIOS for this.

Anyone have an idea where to look in Ubuntu for things that behave like inactivity=suspend?!  Or like an inactivity applet that when it thinks INACTIVE has been triggered it just waits, maybe just waits because theres no screensaver enabled for the inactivity trigger to execute.

And yes, I had this same prob when I had a screensaver enabled...its just that in order to conduct experiments, you need to create a controlled environment, and rule out as many programs/features as possible.

---

### Post by Canada Lee on 2010-04-25
Well, I found a way to prevent my broadcom from disconnecting at random intervals...

You know when you watch a movie, it prevents the screensaver from starting while your watching the movie...it must be preventing the INACTIVITY timer from tripping...

Thats one way...or another way, less cpu intensive, is to play a MP3 with rhythmbox...set the volume low and have it repeat...

My keep-alive program, thats why I tried echoing successful pings every minute, to show Ubuntu there is a program active, and sending info to the screen...but that didnt stop the INACTIVITY timer I guess...

So now I can file a bug report, but against what PROCESS?  The inactivity timer?

---

### Post by NUboon2Age on 2010-05-26
> **Canada Lee said:**
> Broadcom BCM4318 Airforce One 54g Rev 02 wireless...


**I have the same wireless adapter** as Canada Lee.  I haven't experienced the issues that Canada Lee was talking about so I can't comment on that. But it was a bear for this Linux newbie to figure out how to install 'manually', via command line and editing files and so forth so I Just wanted to pass along that **I got the basic functions working on my 10.04/Lucid Lynx system by taking the following all-GUI steps** (step 0 is the only thing that is more involved):

0) You probably wouldn't be here if your wireless adapter was working out-of-the-box from an Ubuntu install. So you might need a proprietery Windows wireless driver and you can probably tell that by reading some of the discussions here and/or by looking at the charts and documentation at [http://wireless.kernel.org/en/users](http://wireless.kernel.org/en/users)
If you fall in this category, figure out which Windows driver your adapter needs.  

1) Get the Windows .inf and .sys driver files you need for your adapter and put them somewhere logical. These are on the Windows support disks from the manufacturer of the computer, or you can find them on the web. 

For me it is the bcmwl5.inf and bcmwl5.sys files. Today I found them in this zip file:
[ftp://ftp.support.acer-euro.com/notebook/aspire_5020/driver/xp/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_5020/driver/xp/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip)

2) Reading these forums and the above mentioned website I learned that my adapter uses Broadcom b43 driver which requires firmware support, so I:
a) Run Synaptic Package Manager (System-Administration->Synaptic Package Manager) & get fwcutter, install
b) Run jockey (ie. System->Administration->Hardware Drivers) and confirm Broadcom fwcutter firmware is installed and activated, and if not, install/activate it.

3a) Run Synaptic to install ndisgtk if its not already installed.
3b) Run ndisgtk (ie System->Administration->Hardware Drivers->Windows Wireless Drivers) and 'Add' a driver by pointing it at the driver's .inf file (in my case the bcmwl5.inf).

4) Run Synaptic to install (or reinstall if its already there) modemmanager

5) Reboot, and voila! Wireless is working for me.

(I'm not sure exactly what magic configuration modemmanager does under the covers, but it works.  ndisgtk takes care of configuring ndiswrapper and the blacklist items in the .conf files. )

---

### Post by internazional on 2010-05-30
Hi,

i've been my *Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)* card with fwcutter driver on ubuntu for quite a few years now, but i'm planning to do a revamp on my laptop, so figured it would be nice to try ndiswrapper driver, since fw-cutter driver keeps failing me with random disconnects, i've read about better wifi range while using ndiswrapper as well.

I follow the instructions and get my driver listed after **ndiswrapper -l** command:
> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
The problem is that it still won't appear in my Networks panel, since wlan0 isn't listed by **iwconfig** command:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0 was listed in iwconfig before blacklisting all the b43, b43legacy, ssb drivers.
Have spent a few days browsing for the answer, but no clues so far :/

---

### Post by NUboon2Age on 2010-05-30
> **internazional said:**
> Hi,

I follow the instructions and get my driver listed after **ndiswrapper -l** command:

Quote:
> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
device (14E4:431 present (alternate driver: ssb) 


I don't think the warning is at all important (a red herring).  You can resolve it by renaming the ndiswrapper file to ndiswrapper.conf   .

> 
The problem is that it still won't appear in my Networks panel, since wlan0 isn't listed by **iwconfig** command:

wlan0 was listed in iwconfig before blacklisting all the b43, b43legacy, ssb drivers.
Have spent a few days browsing for the answer, but no clues so far :/

Also it might be cleaner to use ndisgtk (aka Windows Wireless Driver) to do the driver installation for you.  You just start it and point to the bcmwl5.inf file.  It will handle all the blacklising & modprobe stuff cleanly.

Also it helped me to install/reinstall modemmanager and then reboot. I don't know why, but it worked.  See my post right above yours for my full run down.

---

### Post by internazional on 2010-05-31
Hi,

I've tried your trial above earlier already, it makes no difference: wireless won't appear neither in gnome panel, neither in iwconfig list.
Anyway, i prefer performing tasks in terminal myself vs ndisgtk, since then i know what exactly is happening.

---

### Post by NUboon2Age on 2010-06-01
> **internazional said:**
> Hi,

I've tried your trial above earlier already, it makes no difference: wireless won't appear neither in gnome panel, neither in iwconfig list.
Anyway, i prefer performing tasks in terminal myself vs ndisgtk, since then i know what exactly is happening.

Did you do the whole thing?  Including reinstalling modemmanager and rebooting?  That step was needed for me too.

Which driver (ie. which .inf file) are you using?

> wlan0 was listed in iwconfig before blacklisting all the b43, b43legacy, ssb drivers.

If you have everything blacklisted, maybe the correct driver is blacklisted too, preventing it from being used by modprobe and therefore not being visible gnome panel, etc.  

This is why I think its smart to use ndisgtk to make sure the blacklisted drivers are correct (ie. that the one you're trying to use isn't blacklisted and the one's you're not using are).  Yes, you could do it manually, but you'll need to know exactly which ones to blacklist and unblacklist.

If you wanted to learn what's ndisgtk does in this regard you might do a before and after look at the blacklist items.  And do a modprobe before and after

Reading your earlier note I'm wondering if you're trying to make it work with only ndiswrapper and w/o fwcutter at all (which would imply that you hadn't used jockey -- aka Hardware Drivers) to install the firmware.  Its likely that won't work since the firmware that fwcutter makes available is likely required in order to make any driver work.  So I'd start there. 

Also, I know it won't appeal to your desire to know exactly what's happening, but there is another program worth experimenting with that handles parts of this process called wifix (you can find it at Sourceforge) that others have recommended.

---

### Post by internazional on 2010-06-06
Yes, i followed all of your insturctions.

I tried unblacklisting the drivers in question and using ndisgtk to install both bcmwl5 / bcmwl5a drivers. wlan0 gets listed by iwconfig command, but there are no wireless networks shown to connect to. I think it is simply because unblacklisting allowed b43 and b43legacy drivers loaded to modprobe again
> modprobe -l | grep "b43"
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko

But obviously this is wrong, since both of the drivers don't suit me, since both aren't to be used with ndiswrapper. In that perspective, i think ndisgtk is of no use at all, since i think it does no blacklisting at all.

I also tried wifix, but it didn't help me.

Concerning of what i am trying to achieve:
as i said earlier on, i am able to make my broadcom wifi function by installing restricted drivers from the System -> Admin. -> Hardware drivers, which installs fwcutter - but the driver is faulty, does random disconnects, which requires me to restart my router, so i'm trying to make my wifi work with the help of ndiswrapper and bcmwl5 driver.

---

### Post by Canada Lee on 2010-06-09
This is an update about the random disconnects, in case this can benefit anyone else.

I thought it might have been the network manager periodically scanning to see what available wifi is in the area, and it randomly hanging...like when it sends a command to scan for avail wifi, it hangs, or maybe waiting for a response, it waits forever.

But I doubt that is the issue.

So far since I diagnosed my problem and solved it by playing a MP3 forever using rhythmnbox, my prob has stayed in the closet and has never shown its face.  So thats a few months of it being suppressed.

I recently connected to my net using the ethernet cable, and turned off my wifi radio, as well as right clicking on Network Manager and turning off Enable Wireless.

Being as I was using ethernet, and all wireless was off, I thought, HEY I should be able to QUIT rhythmnbox now...I dont need to keep the wifi AWAKE...

Surely enough, minutes later everything was sleeping...the little led light by the ethernet cable was lit solid...and the display was showing a still image of what was displayed last when it WAS awake.  Swiped my finger cross the touchpad...and immediately the display updated...this confirmed my suspicion that it was sleeping...then the ethernet light starts flashing...I watch the display and all the speed counters are dropping to ZERO...then a couple of minutes it starts making connections and the speed counters start increasing...

So, this random disconnects of mine, due to some kind of inactivity timer is not the BROADCOM driver...I thought the broadcom driver might have been written to be power saving or something...But when I right click on Network Manager and click on Connection Information, it shows the ETH0 connector using a different driver, not a broadcom one...

So this prob is either some kinda power savings mode, or inactivity for all communications.  Not just broadcom, not just wifi...  A little more system wide than that.

In my Ubuntu, I have turned off all forms of power savings I can find...spin down drives...turn of monitor...suspend etc etc.

And being a laptop, it may be a part of the BIOS.  I have flashed the BIOS with the latest available from the Acer website.  And going into the BIOS settings, there are no ACPI or power savings settings anywhere.  So they do not allow you to change them.

Playing an MP3 repeatedly keeps the system awake when using the ethernet as well...so I am still forced to play a MP3 to solve my prob whether I use wireless or wired.

Ubuntu may not even have any control over this problem if its embedded inside the BIOS itself.

Hope this helps someone.

---

### Post by sirajperson on 2010-07-10
Update Broadcom wireless driver install (10.04):

1: Removing old and non-proprietary drivers:
Open a command shell by going to Applications > Accessories > terminal
then enter:
```

sudo rmmod ssb
sudo rmmod b43
sudo rmmod bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-*
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

``` 
You may have a few error codes in the previous code if you don't have any wireless drivers installed.

2: Download the driver for your achitecture type (32 or 64)
 
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

3: Return to the terminal and enter the following:
```

cd Downloads
mkdir wl
mv hybrid-portsrc* wl
cd wl
tar -xvvf hybrid-portsrc* 

```

3: Install kernel dev tools:
```

sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
sudo apt-get install build-essential linux-headers-generic
sudo apt-get build-dep linux

```
You may get error codes if you have already installed all the above packages.

4: Build the module:
```

cd ~/Downloads/wl/
make clean
make
sudo make install

```

5: preventing non-proprietary driver conficts:
```

sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
sudo echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
sudo gedit /etc/rc.local

```

when gedit opens copy and past the following
```

rmmod ssb
modprobe wl

```
right before line that says
```

exit 0

```

6: reboot the machine:
```

sudo reboot

```

You should have your wireless working. Hope this helps. :D

---

### Post by yaaarrrgg on 2010-07-11
In my case, I didn't have much luck with the (recommended) driver b43legacy or wl.  The b43legacy driver worked to some degree, but drops the connection every minute and reconnects.  I saw a lot errors like:

> no probe response from ap 12:34:56:78:9a:bc after 500ms, disconnecting.


I did get it working with ndiswrapper though.  Here's my setup:

[B]Wifi Card:
[/B]
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Note: "rev 02" is significant, as it generally requires a different driver than "rev 03."

**pciid:** 14e4:4320

**Laptop:** Dell Inspiron 8600 with Ubuntu 10.04, with all updates applied.

**The router:**  configured with WPA Personal.  

Note: if you installed b43legacy, or wl, you will need to remove them, since only one driver will work at a time.  Installing more than one driver can cause the whole computer to run sluggishly.

[B]Here are the specifics: 
[/B]
Get the ndiswrapper utility.  I tried both the command line and GUI utiltiies, and had better luck with the GUI.

```
 
sudo apt-get install ndisgtk

```

blacklist the default b43legacy driver:

```

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

```

Download a new package of drivers: 

[http://ftp.us.dell.com/network/R90501.EXE]("http://ftp.us.dell.com/network/R90501.EXE")

You can extract the exe under linux, it's just a zip.  For example, right-click -> Extract Here.  Now go to:

> System -> Administration -> Windows Wireless Drivers


Now load the driver file **bcmwl5a.inf**, that was in the exe you downloaded, and you should be good to go.  

Wait now, and you should be prompted with the connection.  If not, reboot.   If it doesn't automatically connect, wait for a bit.  You should at least see available wifi points in the network manager applet to connect manually.


[B]For more info see:
[/B]
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I saw conflicting info on using the  bcmwl5.inf and  bcmwl5a.inf drivers.  I tried both and only bcmwl5a.inf worked for me.

[URL="http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Inspiron_5150_1350_Wireless_miniPCI"]http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Inspiron_5150_1350_Wireless_miniPCI
[/URL]

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Wireless_1350]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Dell_Wireless_1350")

---

### Post by g000we on 2010-11-26
I have a HP laptop and it has a Broadcom wirless card built in.
The orange light is constantly on (usually blue when switched on).

I did the non-dell instructions for a new driver (i.e. [Post by sirajperson on the 19th Jul 2010]("http://ubuntuforums.org/showpost.php?p=9573692&postcount=582")), but nothing changed.

Is there anyway I could test to see if there's a hardware fault with my Broadcom wireless?

I don't know where to start! /dev?
I have installed hwinfo, but I can't decypher anything from it.
What do I need to grep for?

Any help would be amazing.

btw: I got this error [modpost: missing MODULE_LICENSE()]("http://forums.linuxmint.com/viewtopic.php?f=90&t=34989&start=0") on Step 4, but the post says to do a few bits which I did, but it looked like the module installed correctly (i.e. I presume no errors in the end!).

---

### Post by mappit on 2011-01-04
This is my first dabble in Ubuntu (and Linux), which I installed from a USB drive on a Dell Latitude D610 that has a Dell wireless 1470 dual band WLAN Mini-PCI card (pci id 14e4:4319) but does not have a wired Internet connection.  I was pleasantly surprised at how much of the D610 was properly controlled by the USB drive installation: all but the WiFi ... which I've worked on now for about five hours without success.  (I can still boot the D610 in Windows XP to confirm that the WiFi hardware is working.)

The instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")suggest that it is possible to get WiFi working given Internet access on a different computer.  I've transferred

   1.  [http://packages.ubuntu.com/lucid/misc/ndiswrapper-common](http://packages.ubuntu.com/lucid/misc/ndiswrapper-common)
   2.  [http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9](http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9)
   3.  [URL="http://packages.ubuntu.com/lucid/ndisgtk"]http://packages.ubuntu.com/lucid/ndisgtk
[/URL]
as well as the bcmwl5.inf and bcmwl5.sys files (obtained from the Windows XP partition on the D610) to the Ubuntu partition via the USB port.

[CODE]$ ndiswrapper -l[CODE] results in "bcmwl5: driver installed device (14e4:4319) present (alternate driver: ssb)".

Loading the new driver module (with $ sudo depmod -a and $ sudo modprobe ndiswrapper) also seemed to be successful because the the output from $ tail /var/log/messages) contained "ndiswrapper version 1.56 loaded (smp=yes, preempt=no)".

However, "$ sudo iwconfig" does not list wlan0 and "$ sudo ifdown wlan0" results in "ifdown: interface wlan0 not configured"

I realized that it was a handicap to not have an Internet connection on the D610 as I tried to setup a Broadcom chipset WiFi, but now I'm starting to wonder if it is even possible.  Any suggestions on how to get this D610's WiFi working would be appreciated.

---

### Post by Bo Sischo on 2011-01-30
Hello, I'm using ubuntu 10.10
I did all of your commands.
But after the reboot when I enter the modprobe command I get this.

warning: all confic files need .conf: /conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


So what and i supposed to do?

---

### Post by hema87 on 2011-02-08
It is a  nice sharing.........

---

### Post by srikethireddy on 2011-03-03
Thanks jonny.... after two days trials i got my wifi working fine thanks for sharing information.


Many many more thanks....

> **jonny said:**
> [I]6 July 2006 Update
I haven't had a Broadcom card for many months, but I've been told this how-to doesn't work properly under Dapper.  Here are a couple of links that have been passed to me - but I can't vouch for their quality.

[http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working](http://www.beginningubuntu.com/dapper_tips.html#Using_Ndiswrapper_to_get_wifi_working)
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Good luck.  I'm very happy that this how-to has helped so many people in the past year or so.[/I]

Broadcom wireless cards are tricky to set up in ubuntu, and the forums are full of frustrated users seeking advice.  Broadcom provide no Linux support (feel free to complain to your hardware vendor or choose a different card if you haven't yet shelled out your cash), but they can be made to work - and you're in the right place if you want to know how.

First, you need to find out if this How To is for you.  Broadcom wireless cards come under many brand names and, in particular, are used in many Dell and Acer laptops.  Look for the drivers supplied with your card (Dell usually store a copy in C:/DRIVERS/NETWORK/ADDON); if you have a file called bcmwl5.inf or bcmwl5a.inf then keep on reading.  You won't succeed without following these instructions!

0. Before you start, clear out any mess from existing failed attempts to use ndiswrapper.  Note that you shouldn't use a root terminal to execute the code in this how-to; use a normal terminal session instead.```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```Some of these steps may report errors; just ignore them.

1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop

2. Follow the advice given here under [How to add extra repositories]("http://ubuntuguide.org/#extrarepositories")

3. Open a terminal session and enter this code.  Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```4. Reboot your PC.  On restarting, the light on your wireless card should come on.  If not, try entering```
sudo modprobe ndiswrapper
```5. Your card is now working.  Open the networking configuration tool System --> Administration --> Networking

6. Select your wireless network card (probably wlan0) and hit the properties button.

7. Tick the 'This device is configured' box, and enter your network name and connection settings.  Ask your office network administrator for support if you don't know what this question means, or copy your settings from Windows.

8. BE CAREFUL entering your WEP key, if you're using one.  You're expected to enter this in hexadecimal form; if you don't speak hex, prefix your key with s:

9. Click OK.  The screen should close fairly quickly; if it hangs, you probably aren't connected properly.

10. Back in the Network Settings screen, select your wireless device as the default gateway device.

11. Click OK.  Again, the screen should close fairly quickly.

12. Enjoy wireless nirvana.  If everything works, you can delete the file from your desktop.

13.  You might notice that the signal strength applet doesn't work properly.  This is a known bug with these cards.

If you have trouble, try booting into Windows - if you dual boot - and checking that the card is enabled.  Some laptops allow the wireless card to be switched off, usually with a special key combination, and I've not found a reliable way to make this work in Linux.

[COLOR=Indigo](Note: This how-to has been updated to reflect all comments from the thread up to 19 April)[/COLOR]

---

### Post by lady06 on 2011-09-16
..2 days later, this is the only thing that worked. Thank you:KS

---

### Post by SecretMastermx on 2012-02-26
Hola a todos les comentare mi experiencia y si me resulto:
Desapues de andar buscando y probando varias formas no podia instalar el firmware de mi chipset bcm 4318 busque en el Centro de Software de Ubuntu escribi bcm4318 y le di clic en buscar y que cren..... si hay un controlador (de hecho es el unico q aparece en la busqueda) solo lo instale y ya sin comandos locos q ni se que significan =) jejeje espero les sirva mi informacion.
suerte

---

### Post by SecretMastermx on 2012-02-26
Ups sorry I dont see that this forum is in english
Let me tell you how do I fix it whit a very simple thing,
After searching about to many diferent ways and comands that I dont now what menning, I search in the Ubuntu Software Center (where we search for install software) the model of my chipset (bcm4318) and there is only one installer in the result, I install this and ready my problem was solved.
I expect that my information be usefull for everyone here.

---

### Post by Ralph L on 2012-12-18
I got my Compaq Presario 2100 with Broadcom 4306 Rev 2 to work.  And its fast.  I did a more complete write-up on this at [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736)

---

