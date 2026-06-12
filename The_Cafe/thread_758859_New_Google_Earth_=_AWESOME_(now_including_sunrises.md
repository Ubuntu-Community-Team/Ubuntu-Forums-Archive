---
title: "New Google Earth = AWESOME (now including sunrise/sunset!)"
date: 2008-04-18
forum: The Cafe
---

### Post by Mazza558 on 2008-04-18
Well, I've just installed the latest Google Earth, and it's something to behold. It is fast approaching photorealism, now including realistic shadows and colours to improve things massively. It also has street view, which zooms down to street level in order to explore this way. Obviously my integrated ATi card is no way to showcase this app properly, so if someone with a better card (e.g nvidia 8800gtx, etc) could give it a run, this'd be interesting.

After gaping at the screenshots (attached), you can install it with this command:

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin ; chmod +x GoogleEarthLinux.bin ; sudo ./GoogleEarthLinux.bin
```

If you already have the previous version, find the install directory (default is in your home folder), and run uninstall.sh.

---

### Post by jrebernik on 2008-04-18
well i tried taking a look at it but when i run the programs all the fonts are extremely small... impossible to read at all. any ideas on how to fix this?

---

### Post by fluteflute on 2008-04-18
Yep it is very good. My XP install got booted up for the first time in a while because of it. Shame my graphic card's drivers (a Radeon 9600 Pro) can't handle GE. :(

---

### Post by Mazza558 on 2008-04-18
flute, in Hardy, you can run 3D apps properly due to the new ATi drivers. They aren't brilliant, but they do the job provided you turn off compiz when you want to use 3d apps.

---

### Post by fieldstone on 2008-04-18
> **jrebernik said:**
> well i tried taking a look at it but when i run the programs all the fonts are extremely small... impossible to read at all. any ideas on how to fix this?

I am also having the tiny font problem. Thoughts, anyone?

---

### Post by Mazza558 on 2008-04-18
Can you post a screenie of the tiny fonts?

---

### Post by rfruth on 2008-04-18
it is amazing, makes me want to get a graphics card ...

---

### Post by jrebernik on 2008-04-18
here ya go

---

### Post by caravel on 2008-04-18
Crashing here.  I've googled and it seems a lot of people are having the same problem and reporting the bug today.

```
caravel@caravel-desktop:~$ googleearth
Google Earth has caught signal 4.

Stacktrace from glibc:
  ./googleearth-bin [0x804f3c7]
  ./googleearth-bin [0x804f8ed]
  [0xffffe420]
  ./libbase.so(_ZN5earth17ScopedPerfSetting6createERK7QStringbb+0x64) [0xb70e40f2]
  ./libbase.so(_ZN5earth17ScopedPerfSettingC2ERK7QStringbb+0x45) [0xb70e418b]
  ./libbase.so(_ZN5earth20LogScopedPerfSettingC1ERK7QString+0x35) [0xb70e4257]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application13setupQtLocaleEv+0x42) [0xb72fca60]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x31) [0xb72fcda9]
  ./googleearth-bin(main+0x2a1) [0x8050b77]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7133050]
  ./googleearth-bin [0x804f201]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/caravel/.googleearth/crashlogs/crashlog-FEF3D97C.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

caravel@caravel-desktop:~$ 
```

---

### Post by Mazza558 on 2008-04-18
> **jrebernik said:**
> here ya go

Try changing the application font from Sans to something else?

I don't know about the crashes though.

---

### Post by jrebernik on 2008-04-18
> **Mazza558 said:**
> Try changing the application font from Sans to something else?

I don't know about the crashes though.

Nope no dice. regardless of what i change any font to and what size it is it doesn't effect it.

---

### Post by Mazza558 on 2008-04-18
Okay, try turning compiz off with

> metacity --replace

then try google earth again.

You can turn compiz back on with

> compiz --replace

---

### Post by kystorms on 2008-04-18
> **Mazza558 said:**
> Well, I've just installed the latest Google Earth, and it's something to behold. It is fast approaching photorealism, now including realistic shadows and colours to improve things massively. It also has street view, which zooms down to street level in order to explore this way. Obviously my integrated ATi card is no way to showcase this app properly, so if someone with a better card (e.g nvidia 8800gtx, etc) could give it a run, this'd be interesting.

After gaping at the screenshots (attached), you can install it with this command:

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin ; chmod +x GoogleEarthLinux.bin ; sudo ./GoogleEarthLinux.bin
```

If you already have the previous version, find the install directory (default is in your home folder), and run uninstall.sh.

after getting the download as you suggest, it loads fine, no erroes, but the icon on my desktop has a lock on it, and when i click nothing happens???? did i miss a step?
newbie here
:KS

---

### Post by jrebernik on 2008-04-18
> **Mazza558 said:**
> Okay, try turning compiz off with



then try google earth again.

You can turn compiz back on with

sadly enough still not working hmmm i cant figure out a reason that it wouldnt display right.................

---

### Post by Mazza558 on 2008-04-18
> **kystorms said:**
> after getting the download as you suggest, it loads fine, no erroes, but the icon on my desktop has a lock on it, and when i click nothing happens???? did i miss a step?
newbie here
:KS

Nah, it's google's fault. Delete it - you can still access it from Applications > Internet.

---

### Post by Jareth on 2008-04-18
So just to clarify, the google-googleearthdesktop icon can be deleted?

Ta

---

### Post by Mazza558 on 2008-04-18
Yes. Yes it can.

---

### Post by tigerplug on 2008-04-18
> **Mazza558 said:**
> flute, in Hardy, you can run 3D apps properly due to the new ATi drivers. They aren't brilliant, but they do the job provided you turn off compiz when you want to use 3d apps.



Uber cool!

---

### Post by ofb on 2008-04-18
Problems with 4.3 may be related to this,
[http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5](http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5)

> I thought you guys deserved an update. The long and short of it is 
that Google Earth 4.3 only works in Linux on machines with processors 
that support SSE2. This means a P4, A64, or greater is now required.

---

### Post by icechen1 on 2008-04-18
They've put a flight simulator in this one,see [http://earth.google.com/intl/en/userguide/v4/flightsim/index.html](http://earth.google.com/intl/en/userguide/v4/flightsim/index.html)

---

### Post by Lostincyberspace on 2008-04-18
when did this one come out I installed just about a week ago.  is that new enought to be this one?

Edit: No I have to reinstall it now poo. :(

---

### Post by DUfire on 2008-04-18
Mine just gets to 'Initializing' and stops.
Quite annoying, actually.

Ran another install, caught this error: 
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

```

---

### Post by swoll1980 on 2008-04-19
on the first run it works great, but when I close it and reopen it the earth is gone. I tried to reinstall it  and it worked fine again untill I closed it. When I reopened it same thing happend
I reinstalled it one more time to make sure and I have the same problem. Any ideas? google earth just isn't as fun with out the earth for some reason

---

### Post by imon9 on 2008-04-19
> **swoll1980 said:**
> on the first run it works great, but when I close it and reopen it the earth is gone. I tried to reinstall it  and it worked fine again untill I closed it. When I reopened it same thing happend
I reinstalled it one more time to make sure and I have the same problem. Any ideas? google earth just isn't as fun with out the earth for some reason

+1
same happening to me..i reinstall 4.2 and i can use google-earth normally

reinstall 4.3 doesnt resolve the problem (even after reboot, deleting config files)

---

### Post by rcdeacon on 2008-04-19
My Google-earth install logs me out. I would like to uninstall but using the code sudo /opt/google-earth/uninstall does not work to uninstall. I also tried using uninstall.sh in the code all to no avail. I went to synaptic but it is not there either.

---

### Post by Mazza558 on 2008-04-19
Strange how many people are having problems with this... As someone mentioned above, it will only work in the first place with a new-ish processor.

---

### Post by Tomosaur on 2008-04-19
Same deal as the guys a few posts above me - the earth disappears when I close and re-open Google Earth, reinstalling doesn't help :(

It's a shame, I love Google Earth. The flight simulator is a lot of fun :P

---

### Post by The Pinny Parlour on 2008-04-19
I downloaded from google.  How do install the thing?  I have a googleearthlinux.bin sitting on the desktop and have no idea how to install it.
thanks.

---

### Post by Tomosaur on 2008-04-19
> **The Pinny Parlour said:**
> I downloaded from google.  How do install the thing?  I have a googleearthlinux.bin sitting on the desktop and have no idea how to install it.
thanks.

Right click it, go to properties, then the permissions tab, and set it to be executable. Then just double-click on it (or single click if you're like me :P ) and it should work.

---

### Post by The Pinny Parlour on 2008-04-19
> **Tomosaur said:**
> Right click it, go to properties, then the permissions tab, and set it to be executable. Then just double-click on it (or single click if you're like me :P ) and it should work.

Thanks for your assistance but it didn't work.
There is no application installed for this file type.

---

### Post by DUfire on 2008-04-19
If you can't see the Earth.....

Compiz + XGL + ATI = No 3D Acceleration.

: |

---

### Post by Mazza558 on 2008-04-19
> **DUfire said:**
> If you can't see the Earth.....



...look down at the floor :p

---

### Post by DUfire on 2008-04-19
> **Mazza558 said:**
> ...look down at the floor :p

Thanks, it worked! : D

...But, if you can't see the eiffel tower o.o...

---

### Post by Mazza558 on 2008-04-19
> **DUfire said:**
> Thanks, it worked! : D

...But, if you can't see the eiffel tower o.o...

I heard the devs are fixing a bug called NOT_IN_PARIS_ERROR. It should be fixed, but you have to pay some money to get there, and the "update" takes about an hour if you're in the UK.

---

### Post by DUfire on 2008-04-19
> **Mazza558 said:**
> I heard the devs are fixing a bug called NOT_IN_PARIS_ERROR. It should be fixed, but you have to pay some money to get there, and the "update" takes about an hour if you're in the UK.

Okay, screw this, I'm in the US! 

:(

---

### Post by The Pinny Parlour on 2008-04-19
Anyone got any ideas on how to install GoogleEarthLinux.bin?
It's on my desktop, I just need to get it installed.
Thanks

---

### Post by DUfire on 2008-04-19
> **The Pinny Parlour said:**
> Anyone got any ideas on how to install GoogleEarthLinux.bin?
It's on my desktop, I just need to get it installed.
Thanks

Just drag it to your home folder and run the commands on the first page of this thread.
: D


...Shapow.

---

### Post by The Pinny Parlour on 2008-04-19
> **DUfire said:**
> Just drag it to your home folder and run the commands on the first page of this thread.
: D


...Shapow.

Thanks.  That didn't work.  It wanted to download the whole thing again.

got any other suggestions?

---

### Post by Mazza558 on 2008-04-19
You just double click the file and click "open in Terminal" - why doesn't this work for you?

---

### Post by diablo75 on 2008-04-19
All you have to type to install Google earth is

```
sh GoogleEarthLinux.bin
```

while you're sitting in the same path as the bin file you downloaded.


Anyway, I was just wanting to check in and see if people were still hitting that bug with Google Earth not running after installation.  I just wiped 8.04 beta off and installed 8.04 RC last night.  I just reinstalled it on 8.04 RC and the same bug comes up (mentioned earlier in this thread by others).

Anybody know how to fix this?

---

### Post by cardinals_fan on 2008-04-19
Whenver I run it it crashes X :(

---

### Post by Mazza558 on 2008-04-19
> **cardinals_fan said:**
> Whenver I run it it crashes X :(

Turn off compiz first.

---

### Post by chris4585 on 2008-04-19
I tried, at first it looked like it was all good, the fonts were good, but trying to maximize the windows ferked it up.

---

### Post by Whiffle on 2008-04-19
Pretty neat.  Not photorealistic by any means, but not too shabby either.  I just checked out the national park I went backpacking in a few weeks ago, it was pretty cool.

---

### Post by rune0077 on 2008-04-19
For those of you who get the disappearing earth, it's some kind of weird permission problem. You can run googleearth with sudo/gksu, and it should work fine.

I tried changing the actual launch-file permissions, but that didn't change anything, so the problem is some other file. Anyways, run it with sudo/gksu and it works on my end.

---

### Post by olzak on 2008-04-20
I can see earth and use this new Google Earth 4.3 only when open as administrator (as Rune0077 said previous message).

When using as normal user there is no earth, only space and stars.

---

### Post by Christmas on 2008-04-20
[quote=olzak]I can see earth and use this new Google Earth 4.3 only when open as administrator (as Rune0077 said previous message).
 
 When using as normal user there is no earth, only space and stars.[/quote]
I'm not sure because I didn't try it, but after you installed it did you run it as root? You know, when it asks to run it immediately after you installed it. Because it's possible that Google Earth created its configuration files as root and you can't access them as normal user. Try to modify the permissions of directory ~/.googleearth, or just delete it (sudo rm ~/.googleearth) and run it again as normal user. ~ is your home folder.

Screenshot on Debian Lenny with KDE:

---

### Post by picopir8 on 2008-04-20
Deleting the ~/.googleearth directory did not work for me.  I also copied the .googleearth dir from /root/ into ~ and changed permissions and it did not work.  All the googleearth permissions in /opt are the same for all owner/group/other so it does no look like a permission problem there.

My temporary solution was to change the right click "applications", click "edit menus" then edit the google earth icon and replaced the command with "gksu googleearth".  Then it will prompt you for a password when launched and run with root privileges.

---

### Post by swoll1980 on 2008-04-20
I think the firewall is causing the disappearing earth but don't know how I would fix it.

---

### Post by chris4585 on 2008-04-20
sudo googleearth

works for me, I'm not worried about it then

---

### Post by rfruth on 2008-04-20
DON'T install GE with sudo (the docs don't say this but they should) unless you run GE as root

---

### Post by cardinals_fan on 2008-04-20
> **Mazza558 said:**
> Turn off compiz first.
I don't use Compiz, but I updated my Zenwalk Snapshot and it started working.  Yes!

---

### Post by sefs on 2008-04-20
Jre if you look carefully not only are the fonts too small, but there is no earth, and no data in places, or layers.  Which is the same problem I have.  

Howerver the earth and data in side bars seem to load in all accounts accepty the main ubuntu user account.  why is that.

> **jrebernik said:**
> here ya go

---

### Post by sefs on 2008-04-20
If you log in via the root terminal and navigate to the goole earth dir and run the uninstall as actual root user (not using sudo) uninstall should work.

> **rcdeacon said:**
> My Google-earth install logs me out. I would like to uninstall but using the code sudo /opt/google-earth/uninstall does not work to uninstall. I also tried using uninstall.sh in the code all to no avail. I went to synaptic but it is not there either.

---

### Post by Can+~ on 2008-04-20
For those who installed used the command (which is wrong, since it installed with sudo):

I got the problem that when trying to uninstall I got something like
"Unable to alocate uninstaller"

When executing the uninstaller in /opt/google-earth/

So I checked the bash file with gedit, and found that it traces back to:

```
/root/.loki/installed/bin/Linux/x86/uninstall
```

I ran that with:

[PHP]root@asgard:/root/.loki/installed/bin/Linux/x86# ./uninstall google-earth
Product: Google Earth
Installed in /opt/google-earth
Uninstalling desktop menu entries...
Uninstalling mimetypes...
# Installed by xdg-mime from googleearth-mimetypes.xml
# Installed by xdg-mime from googleearth-mimetypes.xml
# Installed by xdg-mime from googleearth-mimetypes.xml
# Installed by xdg-mime from googleearth-mimetypes.xml
Could not remove install directory: Directory not empty
Google Earth has been successfully uninstalled.[/PHP]

The folder inside loki/installed is different for each architecture and OS, so it may vary.

And the uninstall was successful

[PHP]root@asgard:/root/.loki/installed/bin/Linux/x86# googleearth
bash: googleearth: command not found
root@asgard:/root/.loki/installed/bin/Linux/x86# exit
exit
canxp@asgard:/root$ [/PHP]

---

### Post by rajeev1204 on 2008-04-21
I have the same font problem. Cant read   a  thing.

Iam on 64 bit so probably its a reason? Cos when i run it from terminal, i get wrong elf class 64 errors for some gtk libraries.

---

### Post by Xbehave on 2008-04-21
Is there any solution to the lack of earth if you install it outside of /home/ & dont use sudo 

Im no security nut, but google earth, by default loads unrecognised xml, i dont want anything running as root doing anything unrecognised
And i have noexec on my /home, so installing it to /home/ apart from being messy simply wont work for me.

---

### Post by the8thstar on 2008-04-21
Hello,

I can see everything but GE is awfully slow! The version I'm using is:

> 
Google Earth 4.3.7191.6508 (beta)
Date de la version Apr 11 2008
Heure de la version 17:53:01
Moteur de rendu OpenGL
Système d'exploitation Linux (2.6.24.0)
Pilote vidéo Tungsten Graphics, Inc
Taille de texture maximale 2048x2048
Serveur kh.google.com

I have turned off the desktop eye-candy but it doesn't change anything. Is there anything I could do from there?

---

### Post by Mazza558 on 2008-04-21
> **the8thstar said:**
> Hello,

I can see everything but GE is awfully slow! The version I'm using is:



I have turned off the desktop eye-candy but it doesn't change anything. Is there anything I could do from there?

You have a low-performance integrated card, so there's not much you can do. Try turning the detail down in the options, and perhaps increasing the amount of memory you allow for it will make a difference (don't give it your whole RAM though!)

---

### Post by rajeev1204 on 2008-04-22
> **rajeev1204 said:**
> I have the same font problem. Cant read   a  thing.

Iam on 64 bit so probably its a reason? Cos when i run it from terminal, i get wrong elf class 64 errors for some gtk libraries.



Recent updates seem to have solved the font problem,Its still tiny though.

But now i have the problem other people are facing -- cant log into session.

So using cached images.

---

### Post by gjwolfswinkel on 2008-04-22
Adding 'sudo' to the startup command in the launcher solved my 'missing earth' problem - thanks for that. 

I have an ATI Mobility Radeon HD 2300 card and a dual core Intel centrino processor; this machine is able to run GE with either Compiz or Metacity.

---

### Post by sefs on 2008-04-22
Why would one or should one have to run google earth with admin privileges?  Ludicrous.

---

### Post by rune0077 on 2008-04-22
> **sefs said:**
> Why would one or should one have to run google earth with admin privileges?  Ludicrous.

If one does not install it as admin or with sudo, one does not have to.

---

### Post by Blue Heron on 2008-04-22
Isn't it ridiculous?
A software that's awesome because it simulates the sunrise?

I like the real sunrise.

---

### Post by Xbehave on 2008-04-22
I installed it to /opt/ as a normal user and it still doesn't work, it appears to want to have the right to execute scripts in my /home/.googleearth/ but as it doesn't complain I cant seam to figure out what's going wrong.

Azureus (non-repo version) for example wanted to unpack swt.jar in my /tmp, but as it at least gave me a clue i managed to fix this. any ideas what it does in my /home/ ?

---

### Post by sefs on 2008-04-22
That does not make sense.  I have firefox in /opt and its installed with root permissions on the files....yet I can use firefox without sudo or admin, as well as tbird, adobe reader etc, and they operate as expected or should. In fact previous to googleearth 4.3 googlearth operated this way.  Explain to me what I am misunderstand here.  You make it sound that you must run an app as root/admin if it's installed with sudo etc., and as far as I can see this is not the case.

> **rune0077 said:**
> If one does not install it as admin or with sudo, one does not have to.

---

### Post by EfChou on 2008-04-23
Alrighty,

Here's how I made google-earth work as user and not root:

First run the uninstaller in the directory you installed to (mine was /opt/google-earth)

so it was

```
sudo /opt/google-earth/uninstaller
```

then 

```
rm -rf /opt/google-earth/
``` 

and after that

```
cd ~/.config 
```

then do a 

```
rm -f Google/
```

finally, 

```
rm -rf .googleearth/
```

rerun the installer as root, and install to the default locations, after it is done installing **DO NOT** click start, click **QUIT** and then start google earth as your user, it worked for me. I guess the initial run is a setup of the files, so if you run it as root, it sets permissions for root only! :)

---

### Post by rune0077 on 2008-04-23
> **sefs said:**
> That does not make sense.  I have firefox in /opt and its installed with root permissions on the files....yet I can use firefox without sudo or admin, as well as tbird, adobe reader etc, and they operate as expected or should. In fact previous to googleearth 4.3 googlearth operated this way.  Explain to me what I am misunderstand here.  You make it sound that you must run an app as root/admin if it's installed with sudo etc., and as far as I can see this is not the case.

You're right, it does not make sense at all, and no, Google Earth didn't use to behave that way. I assume it's a bug of some kind (if it's not, it's a very stupid design). But currently, that seems to be the way to do it.

I don't understand it either, but when I install Google Earth with the sudo command, it will only run if I run it with sudo. As said, I think it's a bug (or should be) with Google Earth, for no other app I heard of, ever behaved that way.

---

### Post by sefs on 2008-04-23
I wish i could do it that way...but I feel as if my system would be open to a clear vector of attack. I'll try EfChou solution a bit later...I hope I have luck with that.

> **rune0077 said:**
> ...but when I install Google Earth with the sudo command, it will only run if I run it with sudo...

---

### Post by asnd16 on 2008-04-23
I am kinda mad. . . with the new version I am having serrious slow issues . . I need a graphics card errr. . . anyone know how to go back to the previous version? LOL I hate to say it.   2 days till Hardy yeah!!

---

### Post by olzak on 2008-04-23
> **EfChou said:**
> 
rerun the installer as root, and install to the default locations, after it is done installing **DO NOT** click start, click **QUIT** and then start google earth as your user, it worked for me. I guess the initial run is a setup of the files, so if you run it as root, it sets permissions for root only! :)

Thank You, EfChou! That works for me. I uninstall Google Earth and install it (not to the default folder  (I install it /usr/lib/googleearth, which is Ubuntu's default) but that isn't the point. The point is that _"after it is done installing **DO NOT** click start" click quit or stop installing._

After that I can start my Google Earth as user. I change GE's desktop icons user rights to my name.

It's something to do with ~/config/Google directory's GoogleEarthPlus.conf file . It was earlier installation  Administrators rights and now mine (user rights). Perhaps it is so simple that change this user rights to yours, and no re-installing needed.

---

### Post by sefs on 2008-04-23
If you are experiencing fonts that just do not look right... see here...

[http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/e328f8f2a04c08c6?lnk=raot#e328f8f2a04c08c6](http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/e328f8f2a04c08c6?lnk=raot#e328f8f2a04c08c6)

---

### Post by the8thstar on 2008-04-24
> **Mazza558 said:**
> You have a low-performance integrated card, so there's not much you can do. Try turning the detail down in the options, and perhaps increasing the amount of memory you allow for it will make a difference (don't give it your whole RAM though!)

I disagree with you. I installed the latest in Vista and it runs like a charm. So what could it be?

---

### Post by smartboyathome on 2008-04-24
I didn't realise I had to uninstall (I installed the new version), and now when I try to uninstall it says "Could not find a usable uninstall program. Aborting."

---

### Post by keithrennie on 2008-04-26
Same problem.  Just installed ubuntu 8.04 and google earth.  The installation performed, but the application crashes and forces a reboot.  Used to work find under kubuntu 7.10.  Any ideas how to go about fixing this?  Keith :(

---

### Post by rcdeacon on 2008-04-26
Google Earth on my box was an abysmal failure. I cannot seem to uninstall it. I cannot sign in as root to remove it and it will not remove using the sudo command. It tells me that the uninstall command is not found. Does anyone know how to get this off. I have read that I need to use a different install procedure but I cannot do that until the old one is off.

---

### Post by the8thstar on 2008-04-26
> **rcdeacon said:**
> Google Earth on my box was an abysmal failure. I cannot seem to uninstall it. I cannot sign in as root to remove it and it will not remove using the sudo command. It tells me that the uninstall command is not found. Does anyone know how to get this off. I have read that I need to use a different install procedure but I cannot do that until the old one is off.

Try to log in as root by configuring the login screen to allow you to do it (in Preferences -> Login).

---

### Post by rcdeacon on 2008-04-26
Thank you the8thstar but sadly I still cannot remove google earth from my box. I can log in as root but it will not uninstall. I go to the directory (/opt/google-earth) and type uninstall and it tells me something to the effect of "no command" or file. Not sure what the problem is. Whenever I try to start google earth my box goes into a reboot cycle. I need to get rid of it and start fresh.

---

### Post by the8thstar on 2008-04-26
Well, if all else fails, log in as root and destroy the whole /opt/google-earth directory with the trashcan. That's expeditive and rough, but it works.

---

### Post by smartboyathome on 2008-04-26
I have the same problem, nothing works. :(

---

### Post by JayBee808 on 2008-04-26
I followed the instructions in the original post.  Everything seemed to install okay.

When I run Google Earth, I get an error saying that it cannot connect to the servers.  It says to check the firewall to see if GE is allowed.

I am running Hardy, and I have not installed any firewall software.

Does anyone know how I can allow GE to connect?  Is this problem caused by something else?

EDIT:
I was able to uninstall everything by running this command:
 sudo /root/.loki/installed/bin/Linux/x86/uninstall google-earth

I tried installing from Synaptic (I think it was in the Medibuntu repos), but it does the same thing.

[I]Google Earth detected an error while trying to authenticate Please check the following:
-your network connection (can you get to [www.google.com?](www.google.com?))
-your firewall settings
(are you blocking /usr/lib32/googleearth/googleearth-bin?)

Error code: 29
For more information, visit:[/I]

There is no website listed.  I checked and I don't have firestarter installed, and UFW says Firewall not loaded.  Google Earth 4.2 runs fine in WinXP and on a Gutsy machine on the same network.  I haven't tried upgrading them to 4.3 yet.

I'd appreciate any help I can get on this.  Google Earth is about the only thing I still use Windows for.  It just works so much better there.  I wish this wasn't the case.

---

### Post by JayBee808 on 2008-04-27
Adding this package solved the Error 29 problem:

sudo apt-get install lib32nss-mdns

This was posted in an older thread about GE connection problems:
[http://ubuntuforums.org/showpost.php?p=4809830&postcount=13](http://ubuntuforums.org/showpost.php?p=4809830&postcount=13)

---

### Post by Puppy fam on 2008-04-27
I just installed Google Earth 4.3 and the font is really small. I don't know if I have to change the font or just make it bigger. In either case I don't know how to. Thanks for any help.

(A screen shot is attached)

---

### Post by gewitty on 2008-04-28
I'm getting the same error after installing:

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-3DC3121E.txt

Does anyone know if this has been fixed yet?

---

### Post by BigSilly on 2008-04-28
I dunno, but I'm getting an error just trying to download this from Medibuntu. Have they removed it? I've installed other packages from them just fine, but Google Earth (any version) gives me this error in Synaptic:

```
W: Failed to fetch http://packages.medibuntu.org/pool/non-free/g/googleearth-4.2/googleearth-4.2-data_4.2.205.5730-0medibuntu3_all.deb
  404 Not Found [IP: 213.186.45.139 80]


W: Failed to fetch http://packages.medibuntu.org/pool/non-free/g/googleearth-4.2/googleearth-4.2_4.2.205.5730-0medibuntu3_i386.deb
  404 Not Found [IP: 213.186.45.139 80]


W: Failed to fetch http://packages.medibuntu.org/pool/non-free/g/googleearth/googleearth_4.3.7191.6508-0medibuntu2_all.deb
  404 Not Found [IP: 213.186.45.139 80]
```

I've been trying it sporadically all day but to no avail.

---

### Post by rajeev1204 on 2008-04-28
New Google Earth = AWESOME CRAP !

---

### Post by rune0077 on 2008-04-28
> **rajeev1204 said:**
> New Google Earth = AWESOME CRAP !

I really enjoy these intelligent comments, very well thought through and really full of insight :confused:

---

### Post by rajeev1204 on 2008-04-28
> **rune0077 said:**
> I really enjoy these intelligent comments, very well thought through and really full of insight :confused:


Sorry man. Just got frustrated trying to get this to run.Keeps on freezing my machine and i have to restart.

Iam calm now :)


Anyways,this is a cafe post not really a support thread is it.

---

### Post by bikeboy on 2008-04-28
Maybe you'll have more success with medibuntu's repo version.

---

### Post by rune0077 on 2008-04-28
> **rajeev1204 said:**
> Sorry man. Just got frustrated trying to get this to run.Keeps on freezing my machine and i have to restart.

Iam calm now :)


Anyways,this is a cafe post not really a support thread is it.

Sure, no prob. Been there, done that. :)

---

### Post by Quillz on 2008-04-28
The new Google Earth is amazing, plain and simple. It's getting to the point where you don't even need to take vacations anymore.

---

### Post by sefs on 2008-04-28
see [http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/e328f8f2a04c08c6?lnk=raot#e328f8f2a04c08c6](http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/e328f8f2a04c08c6?lnk=raot#e328f8f2a04c08c6)

for solution to small fonts.


> **Puppy fam said:**
> I just installed Google Earth 4.3 and the font is really small. I don't know if I have to change the font or just make it bigger. In either case I don't know how to. Thanks for any help.

(A screen shot is attached)

---

### Post by phrostbyte on 2008-04-28
You can also get googleearth from Medibuntu.

---

### Post by qhaz on 2008-04-28
> **JayBee808 said:**
> Adding this package solved the Error 29 problem:

sudo apt-get install lib32nss-mdns

This was posted in an older thread about GE connection problems:
[http://ubuntuforums.org/showpost.php?p=4809830&postcount=13](http://ubuntuforums.org/showpost.php?p=4809830&postcount=13)

Thanks . . . I must have missed the earlier thread about this problem.  It has fixed mine too.

cheers

---

### Post by BigSilly on 2008-04-29
> **BigSilly said:**
> I dunno, but I'm getting an error just trying to download this from Medibuntu. Have they removed it? I've installed other packages from them just fine, but Google Earth (any version) gives me this error in Synaptic:

```
W: Failed to fetch http://packages.medibuntu.org/pool/non-free/g/googleearth-4.2/googleearth-4.2-data_4.2.205.5730-0medibuntu3_all.deb
  404 Not Found [IP: 213.186.45.139 80]


W: Failed to fetch http://packages.medibuntu.org/pool/non-free/g/googleearth-4.2/googleearth-4.2_4.2.205.5730-0medibuntu3_i386.deb
  404 Not Found [IP: 213.186.45.139 80]


W: Failed to fetch http://packages.medibuntu.org/pool/non-free/g/googleearth/googleearth_4.3.7191.6508-0medibuntu2_all.deb
  404 Not Found [IP: 213.186.45.139 80]
```

I've been trying it sporadically all day but to no avail.

Come back to this today, and I still get the same above errors when trying to download from Medibuntu. Am I doing something wrong? Cheers Ubuntu-ites!

---

### Post by JayBee808 on 2008-04-29
Here is what I did to get it working with the Medibuntu repos:

1.  Add the repos as specified at medibuntu.org
2.  Open Synaptic, search for "googleearth"
3.  First select "googleearth-4.3" for install
4.  Next select "googleearth-4.3-data"
5.  Last select "googleearth" (the meta package).  I found if I selected this one first, it was trying to install GE 4.2
6.  Apply the changes, wait for the downloads.
7.  Select and install "lib32nss-mdns" to fix the Error 29 problem

These steps got it up and running for me.  The performance seems to be better than it was with 4.2.  It still works better in Windows (unfortunately) but it is getting better.  It is very usable.

---

### Post by gewitty on 2008-04-30
Still getting a problem. When following the instructions above, I get an error when attempting to run sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update. This seems to go OK, but then throws up an error saying that the public key is not available, as shown below:

dave@dave-desktop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get: 1 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release.gpg [189B]                      
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Get: 2 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release [700B]                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 190B in 0s (361B/s)
Reading package lists... Done
W: GPG error: [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot libxalan110 libtimedate-perl dpkg-dev patch libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get: 1 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release.gpg [189B]                      
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Translation-en_GB                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Get: 2 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release [700B]                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 190B in 0s (415B/s)
Reading package lists... Done
W: GPG error: [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: You may want to run apt-get update to correct these problems

I ran apt-get update, but that didn't cure the problem.

When I try to run Google Earth from Terminal I get this error report:


dave@dave-desktop:~$ googleearth
Google Earth has caught signal 4.

Stacktrace from glibc:
  ./googleearth-bin [0x804f3c7]
  ./googleearth-bin [0x804f8ed]
  [0xb7fba420]
  ./libbase.so(_ZN5earth17ScopedPerfSetting6createERK7QStringbb+0x64) [0xb71070f2]
  ./libbase.so(_ZN5earth17ScopedPerfSettingC2ERK7QStringbb+0x45) [0xb710718b]
  ./libbase.so(_ZN5earth20LogScopedPerfSettingC1ERK7QString+0x35) [0xb7107257]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application13setupQtLocaleEv+0x42) [0xb7328a60]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x31) [0xb7328da9]
  ./googleearth-bin(main+0x2a1) [0x8050b77]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7156450]
  ./googleearth-bin [0x804f201]

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/dave/.googleearth/crashlogs/crashlog-F6A1A5D3.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

I'm now unclear as to whether this is a bug in Google Earth or a problem resulting from the lack of a public key when accessing the repositories (although this seems to be an issue with VirtualBox, rather than Google Earth).

Any ideas?

---

### Post by Melk79 on 2008-05-01
For GE 4.3 on Hardy, I did the following and it worked:

1. Install GE 4.3 via Synaptic Package Manager (rather than from Google)

2. At this point, I get Error 29 and no connection

3. Run sudo apt-get install lib32nss-mdns  (thanks acope) (For 64bit anyways)

4. Error 29 is gone, but no earth appears as user.  Only sudo googleearth works.

5. Remove .config/Google and .googleearth from my home directory and restart googleearth (thanks phoolish)

6. Everything works great.

---

### Post by DJ_Peng on 2008-05-03
> **sefs said:**
> see [http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/e328f8f2a04c08c6?lnk=raot#e328f8f2a04c08c6](http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/e328f8f2a04c08c6?lnk=raot#e328f8f2a04c08c6)

for solution to small fonts.
That's ok for a workaround, but I'm still seeing some issues including images not being clear in the Tip window. I'm also not fond of the Lucida fonts but I can't seem to get the settings right to use the Dejavu Sans that I prefer to the point of having them as my system font.

---

### Post by junior aspirin on 2008-05-03
not sure if anyone has mentioned, but the new google earth is in the Medibuntu repos

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by DJ_Peng on 2008-05-04
Thanks for posting that, junior. I hadn't realized that it wasn't posted but that's where I got it from. With Automatix2 being at end of life and things moved into Medibuntu I usually just check the repos to see if packages are available, but I also forget to point out things are found there now.

---

### Post by the8thstar on 2008-05-04
I don't understand. I've installed the latest Google Earth but it's terribly slow. The strange thing is, the same version runs very well on my Vista partition! All I see is a boring slideshow.

**[COLOR="Blue"]Any ideas on how to improve this? Thanks![/COLOR]**

---

### Post by Mazza558 on 2008-05-04
> **the8thstar said:**
> I don't understand. I've installed the latest Google Earth but it's terribly slow. The strange thing is, the same version runs very well on my Vista partition! All I see is a boring slideshow.

**[COLOR="Blue"]Any ideas on how to improve this? Thanks![/COLOR]**

Are you running Compiz?

---

### Post by the8thstar on 2008-05-04
Hey **Mazza558**,

I always turn off desktop effects before running GE. I took this habit from the older versions that would give me the black screen.

---

### Post by the8thstar on 2008-05-04
Bump

---

### Post by BigSilly on 2008-05-04
It's been in the Hardy Medibuntu Repo for a while. Sadly, it's a bit of a mess. Only GE 4.2 is working. Version 4.3 won't start, and I'm getting an error readout from the terminal -

```
Google Earth has caught signal 4.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin [0x804f3c7]
  /usr/lib/googleearth/googleearth-bin [0x804f8ed]
  [0xb7f62420]
  /usr/lib/googleearth/libbase.so(_ZN5earth17ScopedPerfSetting6createERK7QStringbb+0x64) [0xb70ae0f2]
  /usr/lib/googleearth/libbase.so(_ZN5earth17ScopedPerfSettingC2ERK7QStringbb+0x45) [0xb70ae18b]
  /usr/lib/googleearth/libbase.so(_ZN5earth20LogScopedPerfSettingC1ERK7QString+0x35) [0xb70ae257]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application13setupQtLocaleEv+0x42) [0xb72d0a60]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x31) [0xb72d0da9]
  /usr/lib/googleearth/googleearth-bin(main+0x2a1) [0x8050b77]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70fd450]
  /usr/lib/googleearth/googleearth-bin [0x804f201]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/kproject/.googleearth/crashlogs/crashlog-FFF78057.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.
```

I tried installing version 4.2 and letting it perform an update via the net, but it just crashes Firefox. So for me at least, it's v. 4.2 or nothing at the moment.

---

### Post by the8thstar on 2008-05-05
Google Earth 4.3 doesn't work. I'm reverting to 4.2.

If anyone with an Intel 945GM can make it work, let me know.

---

### Post by daverave999 on 2008-05-05
For those who need the old version, they've made 4.2 available to download again:

[http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin](http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin)

A heads-up for anyone who needed it, as I just noticed...

---

### Post by Maximiliano on 2008-05-16
Googleearth 4.3 works with Ubuntu Hardy

Error Signal 4 when install from medibuntu.
Uninstall from synaptic
Download from googleearth, and install (don't run when the install promt to start googleearth, just cancel, Alt+F2 and type Googleearth

Have athlon xp +2400 and works perfect

--------------------------------

Googleearth 4.3 funciona perfecto con Ubuntu hardy

Cuando lo instale desde medibuntu no arrancaba, al querer arrancarlo desde el Terminal me daba error Signal 4.
Lo desinstale con synaptic.
Baje Googleearth desde la página de google y lo instale (click derecho, propiedades, permisos, permitir ejecutar como programa, luego doble click y comienza la instalación).
Al terminar la instalación te pregunta si desea arrancar Googleeart, presionar Alt+F2 y teclear googleearth para que arranque desde esa ventana. La ventana de la instalación cerrarla cancelando o saliendo.

Lei por alli que con Athlon +xp no funciona, y si funciona.
El problema es con la instalacion desde medibuntu.

----------------------------------------------

---

### Post by skychris on 2008-05-17
I've tried installing both from medibuntu and google web site but no luck I get this message when running it from terminal
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
```

any idea?

btw, I have a ATI card :)

---

### Post by gewitty on 2008-05-18
> **daverave999 said:**
> For those who need the old version, they've made 4.2 available to download again:

[http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin](http://dl.google.com/earth/client/GE4/release_4_2/GoogleEarthLinux.bin)

A heads-up for anyone who needed it, as I just noticed...

Having failed to get the new version running, I attempted to revert to 4.2, but this wouldn't work either. When I ran a file scan, I discovered that although I had done a complete uninstall of 4.3 in Synaptic, there are still quite a number of GoogleEarth folders scattered around different parts of the file system. I'm guessing that this is probably why the re-installation of 4.2 is failing. Now it looks as if I will have to track down each orphaned  file and delete them one at a time.

---

### Post by jaduncan on 2009-03-29
FYI, this works very well on Jaunty on an x4500 intel card with DRI2 indirect rendering.

Tested GE version is 5.0.

---

