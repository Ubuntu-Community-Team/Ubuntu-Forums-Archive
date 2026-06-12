---
title: "WineASIO 0.7.4 - 32 and 64 bit DEBs here"
date: 2009-08-15
forum: Ubuntu Studio
---

### Post by falkTX on 2009-08-15
Does anyone want them?
Grab them on the attachments.

Don't forget to:
```
regsvr32 wineasio.dll
```
after install, as normal user (no sudo!)

--------------


...I'm glad to help

---

### Post by reaper_rr on 2009-08-24
> **falkTX said:**
> Does anyone want them?
Grab them on the attachments.

Don't forget to:
```
regsvr32 wineasio.dll
```
after install, as normal user (no sudo!)

--------------



You may ask - How did you made this packages?

A: The i386 (32bit) deb, I took from 64studio repository (jaunty-backports). I modify the deb to make it work under 64bit OSes.



...I'm glad to help

Is here the ASIO SDK precompiled?

---

### Post by falkTX on 2009-08-24
> **reaper_rr said:**
> Is here the ASIO SDK precompiled?

the asio.h is always needed to compile WineASIO, if that's what your asking

---

### Post by Exershio on 2009-08-26
Thanks so much for this. I've been having a hard time finding the correct SDK that includes asio.h, thus I've been unable to compile this myself.

---

### Post by falkTX on 2009-08-26
> **Exershio said:**
> Thanks so much for this. I've been having a hard time finding the correct SDK that includes asio.h, thus I've been unable to compile this myself.
I didn't compile this either :lolflag:

"Stolen" from the 64Studio repo, then converted into a 64bit DEB

---

### Post by postrg on 2009-10-07
Thanks a lot!
Very tired to search for a ready package.
:)

---

### Post by falkTX on 2009-10-08
> **postrg said:**
> Thanks a lot!
Very tired to search for a ready package.
:)

Glad to help

I also created an HOW-TO "FL Studio 9 using Wine" 
[http://ubuntuforums.org/showthread.php?p=8019030](http://ubuntuforums.org/showthread.php?p=8019030)

---

### Post by Cerberus108 on 2009-11-01
o_o I must be dreaming...
thank you so much!

---

### Post by no_martini_no on 2010-01-27
I feel very lucky. Thank you very much!

---

### Post by jungletek on 2010-02-14
0.7.5 is out, if anyone is interested... [http://sourceforge.net/projects/wineasio/](http://sourceforge.net/projects/wineasio/)

Also, anyone looking for asio.h: It's not that hard. Wineasio even tells you where, in the readme, IIRC. The link to the ASIO SDK is [http://www.steinberg.net/en/company/3rd_party_developer/sdk_download_portal/asio_sdk.html](http://www.steinberg.net/en/company/3rd_party_developer/sdk_download_portal/asio_sdk.html)

It's pretty effing cool to have Ableton Live running in Linux, at almost the same latency I get in Windows.

---

### Post by likemopinto on 2010-03-02
Thank you for this. I am very grateful. You are making my Linux experience that much better!

;)

---

### Post by zeitmeister on 2010-04-02
Hi all,

If anyone wants wineasio 0.7.5 (32-bit only), I've made a binary available here:

[http://tuxaudio.blogspot.com/2010/04/wineasio-075-binary-download.html]("http://tuxaudio.blogspot.com/2010/04/wineasio-075-binary-download.html") 

0.7.5 is required if you're using latest betas of wine. You'll have to install wineasio by hand to use it (as detailed in the above link).

---

### Post by afde on 2010-04-12
Thank you!
great job!!!!!!!!!!!!!!
It is a real pain messing with 32bit stuff
on a 64 bit system!!

---

### Post by CShaum on 2010-04-13
I know I'm reviving an old thread.  But I tried to download the wineasio driver in the first thread. And I get this error message: /tmp/wineasio_0.7.4+pljones2-3~jaunty1_i386-6.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences. Now what does this all mean?? I pretty new at this ubuntu thing. Thanks in advance.

---

### Post by sgx on 2010-04-14
Once you download a .deb, try this command:

sudo dpkg -i /home/CShaum/wineasio_0.7.4+pljones2-3~jaunty1_i386-6.deb

adjust according to the folder your .deb is in.

Cheers

and normal user, not sudo, runs this command:

regsvr32 wineasio.dll

---

### Post by lordofmiscreation on 2010-04-16
I've been having trouble with wineasio 32bit

this is for CShaum

enter this command into the terminal to download all the needed components 

sudo apt-get -y install wine wine-dev libjack0.100.0-dev \
qjackctl build-essential

find and download a wineasio 7.4.dll, it may work with zeitmeister's 7.5.dll but I'm not sure

go to home folder, file system, user, lib, wine, and copy the .dll into that folder (you'll have to open the file as root, if your not able to do it then google open file as root script and enter that into your terminal, that script will allow you to make administrative changes to  your system without the command line)

copy this line into your terminal, that will create a link between wineasio and jack.  In theory jack will bridge the gap between wine and the audio application you are using.

sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0

I obtained and used this information from this website to put your mind at ease, I'm not trying to hack your box, it's word for word.

[http://www.sandgreen.dk/index.php?side=linux_wineasio](http://www.sandgreen.dk/index.php?side=linux_wineasio)

I am by no means an expert and if anyone can see something that needs to be corrected to help CShaum please let me know, thanks

---

### Post by CShaum on 2010-04-17
I guess I didn't make myself clear enough. I can't even download it. When I click on the link too download. Than I this error message pops up (in my first thread). And in my download window it says failed. Thanks

Oops, I guess this not an old thread after all. looked wrong

---

### Post by sgx on 2010-04-17
> **CShaum said:**
> I guess I didn't make myself clear enough. I can't even download it. When I click on the link too download. Than I this error message pops up (in my first thread). And in my download window it says failed. Thanks

Oops, I guess this not an old thread after all. looked wrong

Hi, probably any wineasio .deb file will work. I just downloaded one
at the link beleow. Use a different browser if you must, I used Opera.

[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

There is an rpm version (just a different package format) here:

[http://rpm.pbone.net/index.php3/stat/4/idpl/12577827/dir/pclinuxos/com/wineasio-0.5-1pclos2007.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/12577827/dir/pclinuxos/com/wineasio-0.5-1pclos2007.i586.rpm.html)

that can be converted to a .deb file using the alien command

sudo alien this.rpm

A new this.deb file is made, and can be installed by

sudo dpkg -i this.deb

Cheers

---

### Post by falkTX on 2010-04-21
Debs have been updated to 0.7.5, check first post attachments and enjoy! 
:guitar:

---

### Post by RightIsLeft on 2010-05-06
> **falkTX said:**
> Debs have been updated to 0.7.5, check first post attachments and enjoy! 
:guitar:

Thanks.

Any idea why guitar rig 4 crashes when selecting ASIO from the sound options?

I'm on ubuntu 64bit amd 10.4

---

### Post by falkTX on 2010-05-06
> **RightIsLeft said:**
> Thanks.

Any idea why guitar rig 4 crashes when selecting ASIO from the sound options?

I'm on ubuntu 64bit amd 10.4

Maybe it doesn't work in realtime mode?
I don't know, sorry.

---

### Post by RightIsLeft on 2010-05-06
> **falkTX said:**
> Maybe it doesn't work in realtime mode?
I don't know, sorry.

Thanks now it doesn't crash anymore , and qjackctl works.But i only hear noise.Any idea what i could be doing wrong?

Thanks again.

---

### Post by falkTX on 2010-05-06
> **RightIsLeft said:**
> Thanks now it doesn't crash anymore , and qjackctl works.But i only hear noise.Any idea what i could be doing wrong?

Thanks again.

I would say some configuration is not compatible with wineasio.
Try set sample rate to 44100, buffer size to 1024, and force 16bit.

---

### Post by RightIsLeft on 2010-05-06
> **falkTX said:**
> I would say some configuration is not compatible with wineasio.
Try set sample rate to 44100, buffer size to 1024, and force 16bit.

Thanks , but still can't get it to play.
I have attached a screenshot with my configuration just in case :KS 
Note : the guitar was disconnected at the time i took the screenshot

---

### Post by falkTX on 2010-05-06
> **RightIsLeft said:**
> Thanks , but still can't get it to play.
I have attached a screenshot with my configuration just in case :KS 
Note : the guitar was disconnected at the time i took the screenshot

I'm out of ideas... :(

---

### Post by RightIsLeft on 2010-05-06
> **falkTX said:**
> I'm out of ideas... :(

Ok thanks :)

By  the way i have the guitar connected in line port which works under  windows7 64bit

ps
One note : If i set the audio interface to "plughw0" i hear some intense buzzing and the IN progress bar is filled.

---

### Post by sgx on 2010-05-06
> **RightIsLeft said:**
> Ok thanks :)

By  the way i have the guitar connected in line port which works under  windows7 64bit

ps
One note : If i set the audio interface to "plughw0" i hear some intense buzzing and the IN progress bar is filled.

GR works using reaper to host it, as does Amplitube3, on my 32bit linux.  The standalones also work. Did you install GR4 using the defaults its installer provided?

Are your wine prefs, jackd prefs, and vst host prefs all using the same numbers? 44.1 or 48K uniformly?

Your midi setting in qjackctl setup screen is rawmidi, choose none.

 How is your guitar connected to the line-in? A pre-amped signal is needed, whether from a hardware preamp/fx processor, a dedicated compatible guitar interface that accepts wineasio, or the line-out from a digital guitar amp, like the Line6 Spider products.

If things appear totally **** up, start over with Studio 8.04:

[http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release](http://cdimage.ubuntu.com/ubuntustudio/releases/8.04.1/release)

and older versions of wine/wineasio

or 64studio, or other distro.
Cheers

---

### Post by eric71 on 2010-05-07
> **RightIsLeft said:**
> Ok thanks :)

By  the way i have the guitar connected in line port which works under  windows7 64bit

ps
One note : If i set the audio interface to "plughw0" i hear some intense buzzing and the IN progress bar is filled.

I don't use the Gnome version of Ubuntu any more for recording, mainly because although pulse audio now works pretty well with Jack, the default volume/mixer control is very limiting. All the options like setting the capture input, or muting/unmuting certain channels are not obvious. Try installing gnome-alsamixer. Maybe something isn't set up correctly for capturing your line in. gnome-alsamixer should let you see that and fix it.

---

### Post by RightIsLeft on 2010-05-07
Sorry for the trouble.I managed to fix it.
I had forgotten to toggle the input sound from the sound preferences menu :)

It works really good now.It sounds even better than windows and there is no delay at all.I love it! :guitar:

---

### Post by PC_load_letter on 2010-06-01
Thank you, thank you, thank you! I had given up on WineAsio more than a yr ago since I moved to 64bits. This is a godsend to say the least.


**EDIT:** Forgot to mention, it works like a charm w/ Karmic 64bit running energyXT v2.5.2 under Wine.

---

### Post by sgx on 2010-06-01
> **PC_load_letter said:**
> Thank you, thank you, thank you! I had given up on WineAsio more than a yr ago since I moved to 64bits. This is a godsend to say the least.


**EDIT:** Forgot to mention, it works like a charm w/ Karmic 64bit running energyXT v2.5.2 under Wine.

wineasio has both liberated many windows musicians from OS tyranny, and enabled many linux musicians to utilize some great software instruments.
Its the best app, byte-for-byte, in the history of computer aided music!
:)

---

### Post by falkTX on 2010-06-01
> **PC_load_letter said:**
> Thank you, thank you, thank you! I had given up on WineAsio more than a yr ago since I moved to 64bits. This is a godsend to say the least.


**EDIT:** Forgot to mention, it works like a charm w/ Karmic 64bit running energyXT v2.5.2 under Wine.

You may want to check my festige PPA:
[https://launchpad.net/~falk-t-j/+archive/festige](https://launchpad.net/~falk-t-j/+archive/festige)

It has Wine with a special RT patch, useful to get better latency.

---

### Post by thorgal on 2010-06-01
hi falkTX, what is this RT patch to wine ? could you elaborate a little ? thanks :)

---

### Post by falkTX on 2010-06-01
> **thorgal said:**
> hi falkTX, what is this RT patch to wine ? could you elaborate a little ? thanks :)

It just helps you run wine under lower buffer sizes (128 or 256).

I made a test with FL Studio 9.1 -> The audio never failed, although the GUI was (sometimes) getting "stuck".

I'm not the author of the patch though, one of the LAD devs made it.

---

### Post by thorgal on 2010-06-01
thanks for the feedback. Can we have a pointer to this patch ?

---

### Post by falkTX on 2010-06-01
> **thorgal said:**
> thanks for the feedback. Can we have a pointer to this patch ?

Sure!

Here you go:
[http://kxstudio.sourceforge.net/downloads/0001-Initial-rt-patch.patch](http://kxstudio.sourceforge.net/downloads/0001-Initial-rt-patch.patch)

---

### Post by thorgal on 2010-06-01
great :)

Which version of wine does it apply to ?

---

### Post by falkTX on 2010-06-01
> **thorgal said:**
> great :)

Which version of wine does it apply to ?

I've tested it against 1.2~rc1 and 1.2~rc2

---

### Post by PC_load_letter on 2010-06-02
> **sgx said:**
> wineasio has both liberated many windows musicians from OS tyranny, and enabled many linux musicians to utilize some great software instruments.
Its the best app, byte-for-byte, in the history of computer aided music!
:)

Totally agree, and the 2nd best thing would have to be the Linux native version of Pianoteq, which I only knew about its existence a few days ago. This is :guitar::guitar::guitar:

---

### Post by PC_load_letter on 2010-06-02
> **falkTX said:**
> You may want to check my festige PPA:
[https://launchpad.net/~falk-t-j/+archive/festige](https://launchpad.net/~falk-t-j/+archive/festige)

It has Wine with a special RT patch, useful to get better latency.

Will check it out, thanks!

---

### Post by mdharp on 2010-08-23
Hi - help. 
Having trouble with installing wineasio on Hardy. Had a great set up Reaper in Wine before & lost it. Just tried installing deb 32 bit package.
Terminal reads as below ;
md@Linux:~$ regsvr32 wineasio.dll
err:winedevice:ServiceMain driver L"AFS2K" failed to load
err:module:load_builtin_dll failed to load .so lib for builtin L"wineasio.dll": /usr/bin/../lib/wine/wineasio.dll.so: undefined symbol: jack_client_real_time_priority
Failed to load DLL wineasio.dll

Any help would be greatly appreciated.
Hoping Linux isn't blocking these drivers for some reason.

---

### Post by falkTX on 2010-08-23
> **mdharp said:**
> Hi - help. 
Having trouble with installing wineasio on Hardy. Had a great set up Reaper in Wine before & lost it. Just tried installing deb 32 bit package.
Terminal reads as below ;
md@Linux:~$ regsvr32 wineasio.dll
err:winedevice:ServiceMain driver L"AFS2K" failed to load
err:module:load_builtin_dll failed to load .so lib for builtin L"wineasio.dll": /usr/bin/../lib/wine/wineasio.dll.so: undefined symbol: jack_client_real_time_priority
Failed to load DLL wineasio.dll

Any help would be greatly appreciated.
Hoping Linux isn't blocking these drivers for some reason.

You're probably using a (very) old version of Jack.
Please upgrade your system

---

### Post by Mezzo on 2010-09-08
Thanks a lot !
I just install it, run the command, and Reaktor 5 works perfectly on my kubuntu 10.04 64bits ;-)
With my midi keyboard.
it uses jackd.

---

### Post by poodoopealeoaph on 2010-09-21
so, it seems like a very dumb question, I know... but how do I know if my ubuntu system installed as 32 or 64? When I installed, it just did it's thing and never let me choose.. so, I'm not really sure what package to install

---

### Post by Pablo_F on 2010-09-21
If you don't know, you most probably have 32 bit. It is not a thing you can choose at installation but you have to decide before you burn the installer CD. Launch:

uname -m

in a terminal. If you see i686 is 32 bit. 

Cheers! Pablo

---

### Post by marconbr on 2010-12-08
Hey guys, I've been facing a problem here:

I'm using an ubuntu 10.04 amd64bit version and I've installed the wineasio 0.7.5 deb package for 64 bit architecture, but when I type the command:

> regsvr32 wineasio.dll.soI got this error message:

> Failed to load DLL wineasio.dll.soDo anybody have any idea of what's going on?

Cheers,
Marco

---

### Post by Kitoo on 2010-12-19
> **marconbr said:**
> Hey guys, I've been facing a problem here:

I'm using an ubuntu 10.04 amd64bit version and I've installed the wineasio 0.7.5 deb package for 64 bit architecture, but when I type the command:

I got this error message:

Do anybody have any idea of what's going on?

Cheers,
Marco


Make sure wine has been installed before running the regsvr32 wineasio.dll command

---

### Post by Kitoo on 2010-12-19
Thanks for sharing the DEBS! 

I have got Guitar Rig 4 running successfully on Ubuntu 10.10 32 bit, however, in my AMD64 machine (Ubuntu Studio 10.10) it crashes when I try to select the ASIO driver from the program. It works if I didn't select de ASIO driver but then, I can't make the connection to Jack.

I am using the same audio interface (Edirol UA-25) in both systems and I've tried different configurations in Jack without luck. What is different though, is that in Ubuntu 10.10, wine gets installed in "/usr/lib" while in Ubuntu Studio AMD64 it's put in "/usr/lib32" instead. I wonder if this is why Guitar Rig can't see the ASIO driver.

I've spent the weekend trying to sort it out :-(.  I really need to get it running on the AMD64 machine as this is my main computer. 

Any idea or suggestion would be very much appreciated.

---

### Post by sgx on 2010-12-19
Hi, in the .wine folder, make sure you have the folders

Program Files/Steinberg/VstPlugins

Put all your vst plugin .dll files in VstPlugins.

Install Reaper in your /home/username folder, then use its preferences
to select wineasio as the asio device, and have it scan your VstPlugins
folders to find the plugins. There are tons of youtubes to visualize this,
but in reaper, search menus, and right-left-middle click in every space, to see what appears. Reaper is at this point, the only sensible way to fully utilize multiple vsts in a project in linux, noting that Cantabile, MULAB, FLStudio, and others, may be good backup options.

Thw whole Reaper output can be treated as a single separate instrument, and mixed/routed/recorded with linux instruments like phasex, hydrogen, yoshimi/zynaddsubfx, using qjackctl, patchage, perhaps some others.

Plugins with dongles, ilok, and pace copy protection are best left to
windows/mac. 90% of the rest work fine, a very few Synthmaker, or
Synth Edit plugins fail.
Cheers

google these 3 terms

 wineasio reaper 2010

 for tons of info

---

### Post by Kitoo on 2010-12-20
> **sgx said:**
> Hi, in the .wine folder, make sure you have the folders

Program Files/Steinberg/VstPlugins

Put all your vst plugin .dll files in VstPlugins.

Install Reaper in your /home/username folder, then use its preferences
to select wineasio as the asio device, and have it scan your VstPlugins
folders to find the plugins. There are tons of youtubes to visualize this,
but in reaper, search menus, and right-left-middle click in every space, to see what appears. Reaper is at this point, the only sensible way to fully utilize multiple vsts in a project in linux, noting that Cantabile, MULAB, FLStudio, and others, may be good backup options.

Thw whole Reaper output can be treated as a single separate instrument, and mixed/routed/recorded with linux instruments like phasex, hydrogen, yoshimi/zynaddsubfx, using qjackctl, patchage, perhaps some others.

Plugins with dongles, ilok, and pace copy protection are best left to
windows/mac. 90% of the rest work fine, a very few Synthmaker, or
Synth Edit plugins fail.
Cheers

google these 3 terms

 wineasio reaper 2010

 for tons of info

Thanks for the fast reply!

I've never heard of Reaper before, googled it and found that it's a DAW. My intention is to use Ardour as my DAW and Jack to make the connection with Guitar Rig. I am familiar with Ardour and woudn't like to re-learn how to do things in Reaper. Also, I try to stay away from commercial software as much a I can (I know, but  I don't have a good alternative to Guitar Rig :().

I have installed Wine 1.3.9 and wineasio 0.9 beta and GR does not crash anymore when selecting the ASIO driver, however, Jack can't see the application yet :sad:

Any other suggestion?

---

### Post by landstander on 2012-06-20
> **jungletek said:**
> 0.7.5 is out, if anyone is interested... [http://sourceforge.net/projects/wineasio/](http://sourceforge.net/projects/wineasio/)

Also, anyone looking for asio.h: It's not that hard. Wineasio even tells you where, in the readme, IIRC. The link to the ASIO SDK is [http://www.steinberg.net/en/company/3rd_party_developer/sdk_download_portal/asio_sdk.html](http://www.steinberg.net/en/company/3rd_party_developer/sdk_download_portal/asio_sdk.html)


_**Problem**_:
The link to the AISO SDK is dead. It returns a 404 not found website error.

_**Question**_:
Is any one having any luck finding the correct aiso.h file in order to compile the latest version? 

There have been some fixes released since wineaiso v0.7.5
Here is a quote from the change log:
> CHANGE LOG
-------------

0.9.0
19-FEB-2011: Nearly complete refactoring of the wineasio codebase (asio.c) (JH)

0.8.1:
05-OCT-2010: Code from Win32 callback thread moved to JACK process callback, except for bufferSwitch() call.
05-OCT-2010: Switch from int to float for samples.

0.8.0:
08-AUG-2010: Forward port JackWASIO changes... needs testing hard. (PLJ)

0.7.6:
27-DEC-2009: Fixes for compilation on 64bit platform. (PLJ)

---

### Post by sgx on 2012-06-20
[http://www.steinberg.net/en/company/developer.html](http://www.steinberg.net/en/company/developer.html)

Did you create an account? I think that is mandatory,
to enable the download.
Cheers

---

### Post by Script Warlock on 2012-07-04
after creating an account i choose "extend your mystienberg account" before actually obtaining the sdk.

---

### Post by windeguy on 2012-07-26
Please see: 

[http://ubuntuforums.org/showthread.php?t=2001698](http://ubuntuforums.org/showthread.php?t=2001698)

For problems using wineasio with the latest version of WINE. A registry edit solves the problem for WINEASIO users, but the link to that information is down at the moment. If anyone has the information on how to do that edit, please post it.

---

### Post by Miguel325 on 2012-08-26
Thank you very much

---

