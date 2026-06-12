---
title: "swfdec already better than gnash, fedora brings it by default now"
date: 2008-03-25
forum: The Cafe
---

### Post by madjr on 2008-03-25
in fedora beta release notes (bleeding edge all over!):
[http://fedoraproject.org/f9-beta-relnotes](http://fedoraproject.org/f9-beta-relnotes)

swfdec will be now included (i guess there will be also an option to install normal flash?)

by these screenshots it seems to be working well:
[http://swfdec.freedesktop.org/wiki/ScreenShots](http://swfdec.freedesktop.org/wiki/ScreenShots)

[IMG]http://swfdec.freedesktop.org/wiki/ScreenShots?action=AttachFile&do=get&target=youtube-embed.png[/IMG]

seems to be able to play a "number" of games too.

i think gnash and swfdec **should merge** into 1 effort.

also hardy should include it instead of gnash (not by default, but available in the install list).

last time i tried gnash the youtube video controls were all broken..

it would be good not having firefox crash :)

---

### Post by ubuntu-freak on 2008-03-26
I've never even tried it, will have to check it out, thanks. 
 
Nathan

---

### Post by zmjjmz on 2008-03-26
Looking in to it, the latest version is .6, we have .5-1 in synaptic.

---

### Post by madjr on 2008-03-26
> **zmjjmz said:**
> Looking in to it, the latest version is .6, we have .5-1 in synaptic.

anybody tried it yet?

am still downloading hardy to try the latest 1

anyone really uses gnash ?? if you do please state what works for you.

---

### Post by ubuntu-freak on 2008-03-26
I tried Gnash on YouTube and it worked, but was pixelated and the controls were not shown correctly. I think there's gonna be a new version very soon with improvements, it can only get better anyway. I do think a merge would be great though.
 
Nathan

---

### Post by geoken on 2008-03-26
It's wierd that they wouldn't merge. I mean, what differences could be keeping them apart?

---

### Post by Company on 2008-03-26
Yeah, I think Swfdec and Gnash should merge, too. But last time I asked the Gnash guys to switch to Swfdec they didn't want to. Slackers!

On a more serious note, can we *please* stop these useless merge discussions? And Swfdec is still i some 0.5-outdated version in Hardy, because it has no maintainer in Ubuntu. Pretty much every other distro ships 0.6 these days.

---

### Post by linuxisfree on 2008-03-26
That is THE question, actually... They would do loads better by merging, though. But, there must be some reason that they haven't done so already. (What that reason is, I haven't a clue.)

---

### Post by ubuntu-freak on 2008-03-26
> **Company said:**
> 
On a more serious note, can we *please* stop these useless merge discussions?



You can stop anytime you want. 
 
Nathan

---

### Post by FranMichaels on 2008-03-26
Wow swfdec really is great. I just tried the stand alone player in Hardy, the 6.x version must be even better. I might just have to compile it and give it a go for the browser too :)

Smooth, and in sync.

Anyway, I wouldn't worry about a merge, not sure of the reason, but I'm sure the authors can share work or whatever if need be. Having one project doesn't always make things better, especially if the devs want to go in different directions. :KS

---

### Post by Ebuntor on 2008-03-26
Perhaps the reason they don't want to merge is because Swfdec is licensed under the [LGPL]("http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License") while Gnash is under the GPL. Also Gnash is cross platform while Swdec is confined to Linux and FreeBSD.

---

### Post by phrostbyte on 2008-03-26
SWFDec is written in C and Gnash is written in C++, Gnash uses OpenGL for the primary backend.. SWFDec uses Cairo. The chances that any usable code could be shared between them is minimal. Even so, SWFDec and Gnash use incompatible licenses, and could not legally be merged.

---

### Post by phrostbyte on 2008-03-26
> **Company said:**
>  And Swfdec is still i some 0.5-outdated version in Hardy, because it has no maintainer in Ubuntu. Pretty much every other distro ships 0.6 these days.

Thank you for volunteering to be the maintainer. :)

---

### Post by Ebuntor on 2008-03-26
> **phrostbyte said:**
> SWFDec is written in C and Gnash is written in C++, Gnash uses OpenGL for the primary backend.. SWFDec uses Cairo. The chances that any usable code could be shared between them is minimal. Even so, SWFDec and Gnash use incompatible licenses, and could not legally be merged.

Ah, well that's even a better explanation than mine. :)

---

### Post by madjr on 2008-03-26
> **Company said:**
> Yeah, I think Swfdec and Gnash should merge, too. But last time I asked the Gnash guys to switch to Swfdec they didn't want to. Slackers!

On a more serious note, can we *please* stop these useless merge discussions? And Swfdec is still i some 0.5-outdated version in Hardy, because it has no maintainer in Ubuntu. Pretty much every other distro ships 0.6 these days.

that sucks ballz...

it's so much better than gnash and the latest it's not even in the repos.

Hardy needs to come with swfdec and replace gnash... thats a **priority** :)

---

### Post by FranMichaels on 2008-03-26
Okay, I declare swfdec officially awesome. I'm using it now with the firefox3 in hardy, opened multiple flash sites, no problem even audio of both played, and best of all no crashing (like the adobe flash plugin did for me.)

Synaptic has all the dependencies besides libming (only 0.3.0 in the repos)

Get the latest beta of ming
[http://www.libming.org/moin.cgi/Releases](http://www.libming.org/moin.cgi/Releases)

Get swfdec, swfdec-mozilla, and swfdec-gnome (if you want standalone playback)
[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

Compile and install (the order I listed works :) ) Again, synaptic has all the dependencies, so if you get a libsoup or something missing, head to synaptic to install it. :) 

From there remove your adobe flash plugin from synaptic, or if you installed it manually to ~/.mozilla/plugins/ you can delete it (I renamed it to libflashplayer.old so I can easily switch back to it if I need to.)

From there make a symbolic link and firefox will see the new plugin
Do so by opening up a terminal and paste this
```
 
ln -s /usr/local/lib/mozilla/plugins/libswfdecmozilla.so ~/.mozilla/plugins/libswfdecmozilla.so

```

Then restart firefox and enjoy!

:guitar:

P.S. I have no need of the firefox extension flashblock anymore, flash content now has a play button with swfdec! Yay!

P.P.S As if I couldn't love this any more, if you right click on the flash vid, go to property, there is a Save as dialog... :biggrin:

---

### Post by heartburnkid on 2008-03-26
How does swfdec compare to Adobe Flash Player?  Because frankly, I'm getting really tired of Adobe's performance issues under Linux...  I'd assume that compatibility is not quite as good, but from a pure performance standpoint, how good is it?

---

### Post by ubuntu-freak on 2008-03-26
> **heartburnkid said:**
> How does swfdec compare to Adobe Flash Player?  Because frankly, I'm getting really tired of Adobe's performance issues under Linux...  I'd assume that compatibility is not quite as good, but from a pure performance standpoint, how good is it?

Did you read FranMichaels post? Sounds like it's pretty awesome. I'm gonna try it in Hardy.

Nathan

---

### Post by FranMichaels on 2008-03-26
> **heartburnkid said:**
> How does swfdec compare to Adobe Flash Player?  Because frankly, I'm getting really tired of Adobe's performance issues under Linux...  I'd assume that compatibility is not quite as good, but from a pure performance standpoint, how good is it?

I want to say it's better, but there is no performance difference *that I can notice*. Flash content plays like it should, and there are features (as noted in above post) that I really like. For what it's worth, my laptop fan hasn't kicked in while I'm using swfdec (sometimes adobe flash for sure was using a lot of cpu). As for incompatibility, haven't run into it yet. :)

---

### Post by bruce89 on 2008-03-26
I'm slightly confused as to why Ubuntu doesn't have a real maintainer for swfdec, especially since it's now part of GNOME. At least Debian bother - [http://packages.debian.org/source/sid/swfdec0.6](http://packages.debian.org/source/sid/swfdec0.6)

---

### Post by Ebuntor on 2008-03-26
Could someone help me? I'm trying to compile Swfdec using [this guide]("http://swfdec.freedesktop.org/wiki/Installation"). At some point they say
> Additionally, you need to install (somewhere in PKG_CONFIG_PATH) the fairly recent libming 0.4.0beta5: [http://sourceforge.net/project/showfiles.php?group_id=18365&package_id=187304&release_id=540333](http://sourceforge.net/project/showfiles.php?group_id=18365&package_id=187304&release_id=540333)What do they mean by PKG_CONFIG_PATH? I guess I could just extract and install it if that's what they mean.

EDIT: Never mind, I'll just do it the old fashion way via the source code. I didn't understand what git does anyway.

EDIT 2: Ok same problem with compiling it the normal way. I need to install libming "somewhere in PKG_CONFIG_PATH" whatever that means. Could someone explain please?

---

### Post by bruce89 on 2008-03-26
> **Ebuntor said:**
> EDIT 2: Ok same problem with compiling it the normal way. I need to install libming "somewhere in PKG_CONFIG_PATH" whatever that means. Could someone explain please?

Looks like you'll need to compile libming also.

---

### Post by Ebuntor on 2008-03-26
> **bruce89 said:**
> Looks like you'll need to compile libming also.

Thanks, I actually understood that part I just am unfamiliar with what "PKG_CONFIG_PATH" is supposed to be and what it has to do with compiling something. I assume it just is a variable for a path to a file or something like that.

---

### Post by bash on 2008-03-26
Got the same error. Do you have lipsoup2.4-dev installed?

```
sudo apt-get install libsoup2.4-dev
```

---

### Post by heartburnkid on 2008-03-26
Man, this is such a damn pain in Gutsy... swfdec balks because it wants libsoup-2.4, which isn't in the repositories.  So I download and attempt to compile libsoup-2.4, and it balks because GLIB is too old...  You know, I'll think I'll just pull 5.1 using Synaptic and play with that for a while until I'm ready for Hardy Heron.

--Later:

Ok, now I'm really stumped.  I installed 5.1 from Synaptic, and it did nothing.  So, I compiled 5.2 using the instructions from [http://swfdec.freedesktop.org/wiki/Installation](http://swfdec.freedesktop.org/wiki/Installation), and managed to make it all the way through this time, put the symlinks in the plugins directory and everything, and... still nothing.  about:plugins does not show the flash file types registered.  What now?  I assume that the symlink belongs somewhere else other than where that walkthrough had me put it, but for the life of me I can't figure out where.

Tried running firefox in a terminal, and got this message repeatedly:

```
LoadPlugin: failed to initialize shared library /usr/local/lib/mozilla/plugins/libswfdecmozilla.so [libswfdec-gtk-0.5.so.2: cannot open shared object file: No such file or directory]
```

---

### Post by Company on 2008-03-27
Hey, I have a fanboy. :)

As for installing Swfdec: I wouldn't try it on Gutsy unless I knew what I'm doing. As for Hardy, there are packages around that can just be used, like [https://launchpad.net/~adam-caldwell/+archive](https://launchpad.net/~adam-caldwell/+archive)

---

### Post by heartburnkid on 2008-03-27
And so I re-install Adobe Flash Player, and somehow, Mozilla now picks up *both* SWFDEC and Flash Player... weird.

---

### Post by ubuntu-freak on 2008-03-27
Don't forget to let Firefox know you have changed plugins; 
 
**rm $HOME/.mozilla/firefox/pluginreg.dat** 
 
nAtHaN

---

### Post by Hibountu on 2008-03-28
Will be in  the repos soon : [https://bugs.launchpad.net/ubuntu/+bug/202468](https://bugs.launchpad.net/ubuntu/+bug/202468)

You can install the packages from this repo : [https://launchpad.net/~adam-caldwell/+archive/](https://launchpad.net/~adam-caldwell/+archive/)

---

### Post by FranMichaels on 2008-08-12
Just a little of a heads up, 
> Release time: Swfdec 0.7.4 (unstable) and Swfdec 0.6.8 (stable) are out.

[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

Gonna compile the unstable one right now.

Update: Works nicely. Noticeable change, pressing tab in flash goes over click-able things (accessibility thing, also handy for finding easter eggs in flash videos ;) )

Lastly, after installation
A symbolic link is needed for firefox to see it.
```
ln -s /usr/local/lib/mozilla/plugins/libswfdecmozilla.so /home/epimetheus/.mozilla/plugins/
```
Also, I recommend running
```
sudo ldconfig 
``` as well

---

### Post by FranMichaels on 2008-09-08
Another heads up:
Swfdec 0.8.0 and its respective mozilla plugin are just released.

[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

---

### Post by mrgnash on 2008-09-10
> **FranMichaels said:**
> Another heads up:
Swfdec 0.8.0 and its respective mozilla plugin are just released.

[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

Compiled and installed :) Can't really notice any drastic improvements over 0.7.4.

---

### Post by OZFive on 2008-09-12
I am in the midst of an issue with Flash Non-Free and Banshee not playing together nicely.  I have been told this is a Pluse Audio - Alsa conflict andi was trying out different flash plugins for Firefox. I noticed Gnash and Swfdec inthe repositories.  Gnash gave me pixelated frames.  And Swfdec 0.6 (from Synaptic) was fine in small screen but when I full screened, it was laggy and out of sync.  I want to try out 0.7.4 or even 0.8 but cannot seem to find any repositories that are carrying it at this time.  Anyone know of one for Hardy? Or a .deb? I am not great at building my own compiling stuff, I always get lost in the instructions.

Thanks!

---

### Post by Darkhack on 2008-09-12
Thankfully, someone (Stéphane Marguet) was kind enough to provide a PPA for swfdec so now it's easy to install and upgrade via apt.

[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

---

### Post by rajeev1204 on 2008-09-12
Hmm so good that many now know about swfdec.Its been better than gnash since hardy came out.(or maybe always better)

[http://ubuntuforums.org/showthread.php?t=778055](http://ubuntuforums.org/showthread.php?t=778055)

---

### Post by rab4567 on 2008-09-12
> Thankfully, someone (Stéphane Marguet) was kind enough to provide a PPA for swfdec so now it's easy to install and upgrade via apt.

[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

Can I simply uninstall nonfree plugin and install stephane's package?

---

