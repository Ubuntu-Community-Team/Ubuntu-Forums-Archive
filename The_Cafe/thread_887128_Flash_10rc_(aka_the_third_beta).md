---
title: "Flash 10rc (aka the third beta)"
date: 2008-08-11
forum: The Cafe
---

### Post by geoken on 2008-08-11
It has just been released.

[http://labs.adobe.com/technologies/flashplayer10/]("http://labs.adobe.com/technologies/flashplayer10/")

[http://blogs.adobe.com/penguin.swf/]("http://blogs.adobe.com/penguin.swf/")

---

### Post by andamaru on 2008-08-11
Flash 10 works a lot better on my computer, but it makes firefox crash on some web sites. :( at least they're still improving it. I hope the RC works better

---

### Post by LaRoza on 2008-08-11
Installing. Although people seem to be having Fx troubles, Opera works fine.

EDIT: New beta doesn't work with Opera it seems.

---

### Post by stmiller on 2008-08-11
Thanks for the heads up. Installing now...

---

### Post by 5m0k3 on 2008-08-11
> **LaRoza said:**
> EDIT: New beta doesn't work with Opera it seems.

I experienced the same result.  Actually, I don't see it in Firefox 3, either?

---

### Post by LaRoza on 2008-08-11
> **5m0k3 said:**
> I experienced the same result.  Actually, I don't see it in Firefox 3, either?

Odd. I install Flash to ~/.mozilla/plugins and it didn't work in Opera (didn't try Fx), but the old beta 2 did.

---

### Post by steeleyuk on 2008-08-11
Working pretty well here, no crashes yet. Albeit its had little testing so far...

---

### Post by Superkoop on 2008-08-11
Ugh, I'm having troubles getting it to install on 64bit...

When running:
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

It gives me:
```
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```
I'm doing exactly what I did when I installed the 2nd beta and it's not working.
:(

---

### Post by LaRoza on 2008-08-11
For Opera, get the lastest Opera 9.51 and it works. 

[http://www.opera.com/download/](http://www.opera.com/download/)

(if the location is "Gundari" or whatever for US, chose another (too slow), like the Indiana one.)

---

### Post by High Roller on 2008-08-12
Seems to be a little bit more stable but the banner on youtube that reads "videos being watched right now" has some lines going through it.

Drop down menus on some websites that were previously hidden behind flash content now seem to be corrected.  But when right clicking on a flash item, Firefox trys to take priority and insert its own standard right click menu.

Also, some embedded content is displayed incorrectly or causes Firefox to crash altogether.

Overall stability seems to be better though.  Not as many random crashes, but still a few.

---

### Post by TheConstruct on 2008-08-12
> **Superkoop said:**
> Ugh, I'm having troubles getting it to install on 64bit...

When running:
```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

It gives me:
```
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```
I'm doing exactly what I did when I installed the 2nd beta and it's not working.
:(
According to the second link in the OP ([http://blogs.adobe.com/penguin.swf](http://blogs.adobe.com/penguin.swf)), the NSS and cURL libraries need to be installed or Flash won't work. This is a new requirement of the RC. If you make sure these are installed using Synaptic or whatever, hopefully it'll work. This is necessary even when using a stock 32-bit system as well. I'm thinking there might be an issue where the libs still won't work because Flash will be looking for the 32-bit versions, in which case you'll need to use the getlibs tool (found elsewhere) to pull in the libs.

---

### Post by caoyanzi on 2008-08-12
My friends, do you want to find a good website to buy everything you need when you play EVEonline. Now, I can recommend you a wonderful website named [www.evemaven.com](www.evemaven.com). They  sale eve online, eve online ships, eve online isk, eve online items, Age of Conan, Ever Quest II, Final Fantaxy XI in evemaven.com.And they promise favorable prices, speedy transactions, twenty four-hours customer online services, and financial security guarantee.  If you join it and become a member of their client, you can get more discount. Friends, trust me, I will never cheat you, Choose [www.evemaven.com](www.evemaven.com) will be the best choice for you!!!

---

### Post by no1wantdthisname on 2008-08-12
I got it to work on 64bit using _[getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")_ and getting these packages:
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3

```

---

### Post by hobbes_ba on 2008-08-12
> **no1wantdthisname said:**
> I got it to work on 64bit using _[getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")_ and getting these packages:
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3

```

Thanks! 

It worked for me too.

But I'm sad to see that returning from Full screen video is still not working properly using Compiz.

Is this a nsdispluginwrapper or a Flash 10 bug?

Anyone?


Ubuntu Intrepid Ibex 64 bits

---

### Post by TheConstruct on 2008-08-12
> **hobbes_ba said:**
> But I'm sad to see that returning from Full screen video is still not working properly using Compiz.
What is this problem you're referring to?

EDIT: Thanks for that no1wantdthisname. :)

---

### Post by hobbes_ba on 2008-08-12
> **no1wantdthisname said:**
> I got it to work on 64bit using _[getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")_ and getting these packages:
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3

```

It worked for me too.

Thanks! 

But I'm sad to see that returning from Full screen video is still not working properly using Compiz.

Is this a nspluginwrapper or a Flash 10 bug?

Anyone?

---

### Post by TheConstruct on 2008-08-12
> **hobbes_ba said:**
> But I'm sad to see that returning from Full screen video is still not working properly using Compiz.
The problem is that you're not clarifying exactly what the problem is. Describe it first, and then there'll be a chance we can help.

---

### Post by hobbes_ba on 2008-08-12
> **TheConstruct said:**
> What is this problem you're referring to?

EDIT: Thanks for that no1wantdthisname. :)

Just like that.

(64 bits + using compiz + nspluginwrapper + Flash 10 betas)

When you are watching a Full screen video (i.e. youtube) if you leave (hit esc) before it ends, the video will not return and play into the browser. It will apper just like frizzed on the last frame you saw before you entered the full screen mode, and it will stay like that for a while, sometimes the video ends before returns playing.

Just adding that audio keeps playing with no interruption.

If you minimize firefox and then maximize it, the video inside firefox will behave just like it should be.

This strange behavior started with the introduction of Flash 10.

hope that helps.

---

### Post by TheConstruct on 2008-08-12
Ah yes I've had (and still have) that issue. Didn't know which point of issue was causing it though - 64-bits/compiz/wrapper/flash.

It's stuff like this that tends to dull my perception about using Linux on the desktop, when I look over at my friends and their Windows machines and youtube works fine for them. It's pretty poor, and yes Adobe are to blame, but meh.

---

### Post by mc4100 on 2008-08-12
> **hobbes_ba said:**
> Just like that.

(64 bits + using compiz + nspluginwrapper + Flash 10 betas)

When you are watching a Full screen video (i.e. youtube) if you leave (hit esc) before it ends, the video will not return and play into the browser. It will apper just like frizzed on the last frame you saw before you entered the full screen mode, and it will stay like that for a while, sometimes the video ends before returns playing.

Just adding that audio keeps playing with no interruption.

If you minimize firefox and then maximize it, the video inside firefox will behave just like it should be.

This strange behavior started with the introduction of Flash 10.

hope that helps.

I'm seeing this too ... but it's not a :huge: issue, only an inconvenience, also, changing tabs will fix the video.

---

### Post by Polygon on 2008-08-12
> **hobbes_ba said:**
> It worked for me too.

Thanks! 

But I'm sad to see that returning from Full screen video is still not working properly using Compiz.

Is this a nspluginwrapper or a Flash 10 bug?

Anyone?

its a video driver bug. With ati at least their drivers cant allow two things using direct rendering at the same time, so flash uses software rendering. Turn off compiz if you want hardware rendering

---

### Post by hobbes_ba on 2008-08-12
> **mc4100 said:**
> I'm seeing this too ... but it's not a :huge: issue, only an inconvenience, also, changing tabs will fix the video.
I even alredy tested a Ibex's PPA version o nspluginwrapper_1.0.0 and the problem still persists.

It a let down for sure.

Hope they fix that before Ibex goes primetime.

---

### Post by hobbes_ba on 2008-08-12
> **mc4100 said:**
> I'm seeing this too ... but it's not a :huge: issue, only an inconvenience, also, changing tabs will fix the video.

> **TheConstruct said:**
> Ah yes I've had (and still have) that issue. Didn't know which point of issue was causing it though - 64-bits/compiz/wrapper/flash.

It's stuff like this that tends to dull my perception about using Linux on the desktop, when I look over at my friends and their Windows machines and youtube works fine for them. It's pretty poor, and yes Adobe are to blame, but meh.

> **Polygon said:**
> its a video driver bug. With ati at least their drivers cant allow two things using direct rendering at the same time, so flash uses software rendering. Turn off compiz if you want hardware rendering

Hum.. thanks for the info.

I am using the latest ati-radeon opensource driver packages on Ibex.

It improved a lot. I can now have two instances of totem playing video, but still is under development.

---

### Post by dspari1 on 2008-08-12
The only reason I'm not installing this is because I'm to lazy to uninstall kubuntu-restricted-extras and reinstalling everything manually with the exception of Flash. :confused:

I'll just wait for the full version to get in the repo.

---

### Post by LaRoza on 2008-08-12
> **dspari1 said:**
> The only reason I'm not installing this is because I'm to lazy to uninstall kubuntu-restricted-extras and reinstalling everything manually with the exception of Flash. :confused:

I'll just wait for the full version to get in the repo.

You don't have to do that. You can install it into ~/.mozilla/plugings without affecting other flash installs.

---

### Post by hobbes_ba on 2008-08-12
> **dspari1 said:**
> The only reason I'm not installing this is because I'm to lazy to uninstall kubuntu-restricted-extras and reinstalling everything manually with the exception of Flash. :confused:

I'll just wait for the full version to get in the repo.

Well.. I am not really into Kubuntu, but I have something that maybe can help you out.

Take a look on this how-to:

[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

I used myself.

PS: Just remember to change url to the new beta.

---

### Post by oedipuss on 2008-08-12
Hmm I can't see youtube thumbs anymore ..
Firefox3 with flash 10rc, on 32bit hardy, and compiz running (if that's anything to do with it)
Flash itself works, and the videos show up normally once I click them, but no thumbs.

---

### Post by mister_k81 on 2008-08-12
Well, I can't get this to work at all. I'm using Hardy 32bit without Compiz turned on, and neither Firefox 3 or Opera detects the latest RC. :|

I've tried uninstalling and reinstalling to different locations, like; ~/.mozilla/plugings, /usr/lib/firefox/plugins, and /usr/lib/flashplayer-nonfree, and nothing seems to work. Though, I can install any of the previous Flash 9 or 10 betas in any of these spots and it will run fine. 

I also checked, and don't seem to be missing any of the dependencies listed at: [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/). Could any of them be out of date? 

Any suggestions would be appreciated. :-?

---

### Post by gjoellee on 2008-08-12
> **andamaru said:**
> Flash 10 works a lot better on my computer, but it makes firefox crash on some web sites. :( at least they're still improving it. I hope the RC works better
  maybe it does in Firefox 3.1, you should give Mozilla a feedback and tell them about how mad Firefox is at the moment

---

### Post by mr bob on 2008-08-12
I am having a strange problem.

My system is 32-bit Hardy with Firefox 3.0.1 running.

When I install with flashplayer-installer, Firefox plays the flash movies and by right-clicking I can see that it is running Flash 10. 

The movies runs far smoother with Flash 10, a significant improvement over Flash 9.

However, when I close and then reopen Firefox, when I play a flash movie it has reverted to Flash 9. It is definitely using the original Flash 9 plugin because the movie is jerky again and by right-clicking it confirms Flash 9 (although the plugins window still says Shockwave Flash 10.0.0).

It suggests I am installing to the wrong place, can anyone help?

---

### Post by keiichidono on 2008-08-12
Thanks for the info, Flash 10 RC1 is working great for me, fixed the problem I had with the beta's. Fullscreen, multiple audio source support, and better speed overall out of the box is great. Hardy Heron, 32bit, Firefox 3.0.1 here.

---

### Post by billgoldberg on 2008-08-12
After installing it, I get the following error message when I run firefox in a xterm

LoadPlugin: failed to initialize shared library /home/rw/.mozilla/plugins/libflashplayer.so [libssl3.so: cannot open shared object file: No such file or directory]

What's libssl3.so?

---

### Post by mr bob on 2008-08-12
> **mr bob said:**
> However, when I close and then reopen Firefox, when I play a flash movie it has reverted to Flash 9.

Silly me, forgot **sudo**!

Now working permanently with Flash10 and far better performance than Flash9! Great.

So just to recap, from the directory you have extracted the Flash10 installer:
```
sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree
sudo ./flashplayer-installer

```

regards mr bob

---

### Post by SomeGuyDude on 2008-08-12
Does this one jack CPU usage? Currently I can't play many flash games because after about 5 minutes my CPU's running at near 80% and temperature goes from 34C to over 70.

---

### Post by Hells_Dark on 2008-08-12
Where to install it ?!
It rejects all the path i give.. -___-

---

### Post by ThrobbingBrain66 on 2008-08-12
install it to /usr/lib/firefox-3.0.1 to get the plugin system-wide or /home/*username*/.mozilla to enable it for just you.

---

### Post by Hells_Dark on 2008-08-12
> **ThrobbingBrain66 said:**
> install it to /usr/lib/firefox-3.0.1 to get the plugin system-wide or /home/*username*/.mozilla to enable it for just you.

Thanks.

> Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /home/hellsdark/.mozilla

WARNING: Please enter a valid installation path.


The first path did work. But :

> LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [libssl3.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type]

No flash now.

---

### Post by ThrobbingBrain66 on 2008-08-12
Did you uninstall the old flash package first?  If installed through the repos, you need to remove flashplugin-nonfree.  Are you running 64-bit by any chance?

---

### Post by Hells_Dark on 2008-08-12
Yeah. I did what mr bob said. 32bits.

---

### Post by lunarcloud on 2008-08-12
```
getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3
```

Produces:

```
libnss3-1d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

libnspr4-0d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
```I'm on 64bit Hardy

My sources.list is

```
## Add comments (##) in front of any line to remove it from being checked.
## This is a decent and organized sources.list unlike most people's

##### BASIC #####
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

##### PROPOSED #####
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed universe main multiverse restricted

##### MAJOR BUG FIX UPDATES #####
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

##### UBUNTU SECURITY UPDATES #####
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

##### BACKPORTS REPOSITORY #####
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe

##### CANONICAL COMMERCIAL REPOSITORY #####
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu/ hardy partner

##### NetworkManager 0.7 #####
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main

##### CinnamonPirate.com Repository - Emulators #####
#deb http://repository.cinnamonpirate.com/ hardy pirate

##### DVB #####
#deb http://ppa.launchpad.net/pitti/ubuntu hardy main
#deb-src http://ppa.launchpad.net/pitti/ubuntu hardy main

##### KDE4 Latest #####
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

##### Adept 3 latest #####
deb http://ppa.launchpad.net/mornfall/ubuntu hardy main

##### Plasmoids #####
#deb http://ppa.launchpad.net/echidnaman/ubuntu hardy main
#deb-src http://ppa.launchpad.net/echidnaman/ubuntu hardy main

##### Amarok Nightly #####
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main

##### Arora Latest #####
deb http://ppa.launchpad.net/sikon/ubuntu hardy main
deb-src http://ppa.launchpad.net/sikon/ubuntu hardy main

#### Google #####
#deb http://dl.google.com/linux/deb/ stable non-free

##### XBMC #####
#deb http://ppa.launchpad.net/team-xbmc-svn/ubuntu hardy main
#deb-src http://ppa.launchpad.net/team-xbmc-svn/ubuntu hardy main

##### Seveas #####
# sudo wget -q http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
deb http://mirror.ubuntulinux.nl gutsy-seveas all
deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

##### Latest Wine #####
# sudo wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
#deb http://wine.budgetdedicated.com/apt hardy main
#deb-src http://wine.budgetdedicated.com/apt hardy main

##### Viewizard Games repository #####
## sudo wget http://www.viewizard.com/linux/viewizard-gpg.asc -O- | sudo apt-key add -
deb http://viewizard.com/linux debian/

##### Virtualbox #####
## wget http://www.virtualbox.org/debian/innotek.asc
## sudo apt-key add innotek.asc
#deb http://www.virtualbox.org/debian hardy non-free

##### Emulators #####
deb http://home.icequake.net/~nemesis/debian binary/

##### Skype #####
#deb http://download.skype.com/linux/repos/debian/ stable non-free

##### Elisa #####
## sudo wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
#deb http://elisa.fluendo.com/packages gusty main

##### Debian Multimedia for KDENLIVE KDE4 #####
# wget http://debian-multimedia.org/gpgkey.pub -O - | sudo apt-key add - && sudo apt-get update && sudo apt-get install debian-multimedia-keyring
#deb http://debian-multimedia.org testing main
#deb http://debian-multimedia.org unstable main

##### Fonts #####
deb http://ppa.launchpad.net/corenominal/ubuntu hardy main

##### DVD Playback #####
# sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh

```I really wanna try the new rc.

---

### Post by no1wantdthisname on 2008-08-12
> **billgoldberg said:**
> After installing it, I get the following error message when I run firefox in a xterm

LoadPlugin: failed to initialize shared library /home/rw/.mozilla/plugins/libflashplayer.so [libssl3.so: cannot open shared object file: No such file or directory]

What's libssl3.so?
> **Hells_Dark said:**
> 

LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [libssl3.so: Ne peut ouvrir le fichier d'objet partagé: Aucun fichier ou dossier de ce type] 
[http://blogs.adobe.com/penguin.swf/2008/08/library_expansion.html](http://blogs.adobe.com/penguin.swf/2008/08/library_expansion.html)
Flash 10rc has new dependencies.  Get libnss3-1d, libnspr4-0d, and libcurl3.

> **zarquad said:**
> 
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3

```
Produces:

```
libnss3-1d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

libnspr4-0d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
```


Not really sure.  My source list doesn't look very different
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

```

Do you see the packages in synaptic at least?

---

### Post by Hells_Dark on 2008-08-12
> **no1wantdthisname said:**
> [http://blogs.adobe.com/penguin.swf/2008/08/library_expansion.html](http://blogs.adobe.com/penguin.swf/2008/08/library_expansion.html)
Flash 10rc has new dependencies.  Get libnss3-1d, libnspr4-0d, and libcurl3.


I've got the 3. I still have the libssl problem.

> hellsdark@green-lime:~$ sudo apt-get install libnss3-1d libnspr4-0d libcurl3
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
libnss3-1d est déjà la plus récente version disponible.
libnspr4-0d est déjà la plus récente version disponible.
libcurl3 est déjà la plus récente version disponible.


---

### Post by billgoldberg on 2008-08-12
No matter what I did, it couldn't make it work.

It installed fine, but it didn't work.

I'm back on flash 10 beta2. It works fine here.

I guess I'll wait for the next release in a few weeks.

---

### Post by Hells_Dark on 2008-08-12
Yep. I think i'll give up too...

---

### Post by mccord on 2008-08-12
> **Hells_Dark said:**
> I've got the 3. I still have the libssl problem.
had the same problem, apt-get told me the libraries were already installed and up-to-date
but it seemed flash couldn't find them

i looked around in /usr/lib and found:
/usr/lib/libnspr4.so.0d
/usr/lib/libnss3.so.0d
/usr/lib/libnss3.so.1d
/usr/lib/libssl3.so.0d
/usr/lib/libssl3.so.1d

but flash seems to be looking for:
/usr/lib/libnspr4.so
/usr/lib/libnss3.so
/usr/lib/libssl3.so

so i symlinked the files to those names and it seems to work fine now :)
```

sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so

```

seems like a 'dirty hack' to me, so take that with a grain of salt :P
maybe someone can come up with a better solution!

---

### Post by gjoellee on 2008-08-12
In Intrepid Flash 10 s the default flash version

---

### Post by Hells_Dark on 2008-08-12
Thanks mccord! It worked :)
Yes ! The fullscreen with flash is not as (so) slow as it was ! :D

---

### Post by billgoldberg on 2008-08-12
Thanks.

This release candidate performs MUCH better on fullscreen than beta 2, let alone flash player 9 did.

edit: you got a thanks on the blog post I did on this.

---

### Post by Superkoop on 2008-08-12
> **no1wantdthisname said:**
> I got it to work on 64bit using _[getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")_ and getting these packages:
```

getlibs -p libnss3-1d
getlibs -p libnspr4-0d
getlibs -p libcurl3

```

Awesome! Thanks! :biggrin:

This RC kicks tooshy! The last beta2 gave me really terrible video rendering, but now this one...is like WOAA! If it weren't for the compression, the videos would look as awesome as usual vids, something I haven't experienced with flash video before! :guitar:

---

### Post by mrgnash on 2008-08-12
> **no1wantdthisname said:**
> [http://blogs.adobe.com/penguin.swf/2008/08/library_expansion.html](http://blogs.adobe.com/penguin.swf/2008/08/library_expansion.html)
Flash 10rc has new dependencies.  Get libnss3-1d, libnspr4-0d, and libcurl3.



Not really sure.  My source list doesn't look very different
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

```

Do you see the packages in synaptic at least?

I'm having the same problem, and yes, I can see them in synaptic -- in fact, I already have them installed (the 64bit versions at least).

---

### Post by High Roller on 2008-08-14
> **High Roller said:**
> Seems to be a little bit more stable but the banner on youtube that reads "videos being watched right now" has some lines going through it.

**EDIT:  The above youtube problem seems to be fixed.  I guess youtube changed their code to function properly with Flash Player 10 RC1.**

---

### Post by ajgreeny on 2008-08-14
For the last few upgrades of flash 10, from beta1 to the new rc1, I have downloaded the tar.gz from adobe, extracted it to a folder in ~/Downloads, and the simply copied the libflashplayer.so to my** /usr/lib/flashplugin-nonfree** folder after renaming the last version so I know which is which.  It has always worked perfectly without any real problems and I find the new rc1 really good and smooth.

If I do find a problem I can go back to the previous working version by simply renaming the backup previously renamed copy of the plugin.  Simple but effective!

---

### Post by vasilis34 on 2008-08-15
My main problem with flash 10 is that when I play a video on fullscreen and then press ESC to return to normal mode, the video freezes and I can hear only the sound playing normally. Did anyone else face the same problem?

---

### Post by Colonel Kilkenny on 2008-08-15
> **vasilis34 said:**
> My main problem with flash 10 is that when I play a video on fullscreen and then press ESC to return to normal mode, the video freezes and I can hear only the sound playing normally. Did anyone else face the same problem?

After returning to normal mode scroll the page so that the flash object is not visible and then scroll back. That makes video work in Opera at least.
It seems there's some sort of bug.

---

### Post by stmiller on 2008-08-15
bbc news flash video works now. (Didn't work with previous 10 beta). Or perhaps the BBC folks updated their software to allow flash 10?

---

### Post by df9517 on 2008-08-17
It says in my plugin page that I use Shockwave flash 10.0.0.d569

Is that the RC?

---

### Post by billgoldberg on 2008-08-17
> **Colonel Kilkenny said:**
> After returning to normal mode scroll the page so that the flash object is not visible and then scroll back. That makes video work in Opera at least.
It seems there's some sort of bug.

True. I have the same issue and when scrolling the page, the video start playing again.


I love the fact that fullscreen playback isn't choppy at all anymore.

It's fluent.

I'm happy.

I do have some problems with some websites.

Like cnn.com. 

It says "you need flash player 8 or **higher** to view, you are using flash player 10".

Also zdnet.com videos don't seem to work.

That's about all.

---

### Post by KuBala on 2008-08-17
> **Polygon said:**
> its a video driver bug. With ati at least their drivers cant allow two things using direct rendering at the same time, so flash uses software rendering. Turn off compiz if you want hardware rendering

I experience the same problem with open-source ati drivers too. (mobility radeon 9000).

Is there any will to fix this problem? :confused:

(I reduce the cpu clock on my laptop to make the fans more silent, but when compiz is enabled the flashes are really slow. Youtube clips too.)

---

### Post by mips on 2008-08-17
I have been using gnash 0.8.3-2 for about a week now and I must say I have not experienced any problems yet and this is in a 64bit environment.

---

### Post by szandor on 2008-08-18
> **df9517 said:**
> It says in my plugin page that I use Shockwave flash 10.0.0.d569

Is that the RC?

yes. that is the 08-11-08 plugin.

---

### Post by crypto178 on 2008-08-18
Not much luck here, although performance has improved, it still crashes after a few videos or just instantly on some sites (such as bbc.co.uk). That and the back-from-fullscreen bug others have mentioned. Getting there, but not ready yet.


EDIT:
I followed [this guide]("http://ubuntuforums.org/showthread.php?p=5587712") as well as [these instructions](http://blogs.adobe.com/penguin.swf/2008/08/windowless_mode_fix.html) and things are going much better now. The first one seems to have eliminated the random crashes, while the second one stopped bbc.co.uk from crashing instantly. Only the back-from-fullscreen bug remains, but it's not a big deal. Great!

---

### Post by vasilis34 on 2008-08-18
Thx Colonel Kilkenny that did the trick. Another weird thing in youtube. When I choose the "watch in high quality" option I get the answer "We are sorry this video is no longer available". I have double checked it by reverting to the stable version and trying the same video and the high quality video exists and it's playable. 

Any trick for this ?

---

### Post by hobbes_ba on 2008-08-28
After latest intrepid (ia32-libs) updates Flash 10rc stopped working on amd64

LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: classe ELF errada: ELFCLASS32]

I already reinstall it using the very same method that worked last time. 

But the problem persists.

There is anybody else having this same issue?

**Update**: Now, it seems to be working again. But the above message persists.

I also noticed some new instability, lots of window detachments from main-window Firefox compared to before.

---

### Post by zakalwe_ukuk on 2008-09-19
Fullscreen performance is much improved but now tearing is really noticeable even in smaller windows. This is without compiz running. Anyone else have this problem?  I have no tearing with v9 or any other videos.

32 bit ubuntu
nvidia 7800gs

---

### Post by thushw on 2009-05-12
you might need t symlink all these files:

thushara@agni:~$ sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so 
thushara@agni:~$ sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
thushara@agni:~$ sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
thushara@agni:~$ sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
thushara@agni:~$ sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so

---

### Post by thushw on 2009-05-12
here's some info on how to debug this sort of thing:

[http://thushw.blogspot.com/2009/05/flash-plugin-for-firfox-on-ubuntu-8041.html](http://thushw.blogspot.com/2009/05/flash-plugin-for-firfox-on-ubuntu-8041.html)

---

