---
title: "Adobe answers cries for 64-bit Flash on Linux"
date: 2008-11-17
forum: The Cafe
---

### Post by Meetloaf13 on 2008-11-17
Hey guys/gals, just saw this article.  Linux wins, we get the x64 flash goodness first.

Linky:
[http://mcall.com.com/8301-1001_3-10097931-92.html](http://mcall.com.com/8301-1001_3-10097931-92.html)

---

### Post by Arup on 2008-11-17
This is indeed good news, now the only thing to watch out is for a complete proper removal of the installed Flash as well as getlibs which won't be needed anymore unless one plans to run x32 apps.

---

### Post by BobCFC on 2008-11-17
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

go go go

---

### Post by BobCFC on 2008-11-17
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by tom66 on 2008-11-17
Cool. I don't use 64-bit but I'm sure it will help others who do.

---

### Post by Arup on 2008-11-17
I removed the x32 plugin via synaptic and just did a sudo cp libflashplayer.so .usr/lib/mozilla/plugin and it works fine, both FF and Opera picked it up without any issues and youtube runs fine on both browsers. Many thanks to BobCFC for posting the good news. Now its all x64. Hopefully I can remove getlibs as well as its no loger needed.

---

### Post by miggols99 on 2008-11-17
Yay :D Adobe has finally heard us! No more lib32-* files needed anymore :) Soo....how do I install this then?

---

### Post by BobCFC on 2008-11-17
Works great on Youtube and iPlayer for me.  Just uninstall flashplugin-nonfree from Synaptic first

instructions from the [64bit release notes]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html"):


>    1.  [Download the plugin]("http://labs.adobe.com/downloads/flashplayer10.html") to begin installation. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Quit your browser.
   4. Remove all existing Adobe Flash Player installations from the system.
   5. Unpackage the file. A directory with contains libflashplayer.so will be created.
   6. Copy libflashplayer.so to ~/.mozilla/plugins. Create the 'plugins' folder if it does not exist yet.
   7. Launch your brower. To verify installation in Firefox choose Help > About Plug-ins from the browser menu.

---

### Post by FuturePilot on 2008-11-17
Whoohoo! :guitar:

---

### Post by pt123 on 2008-11-17
damn so whinging works

---

### Post by BobCFC on 2008-11-17
Works great on YouTube and BBC iPlayer for me. Just uninstall **flashplugin-nonfree** from Synaptic first

instructions from the [64bit release notes]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html"):

> 1. [Download the plugin]("http://labs.adobe.com/downloads/flashplayer10.html") to begin installation. A dialog box will appear asking you where to save the file.
2. Save the .tar.gz file to your desktop and wait for the file to download completely.
3. Quit your browser.
4. Remove all existing Adobe Flash Player installations from the system.
5. Unpackage the file. A directory with contains libflashplayer.so will be created.
6. Copy libflashplayer.so to ~/.mozilla/plugins. Create the 'plugins' folder if it does not exist yet.
7. Launch your brower. To verify installation in Firefox choose Help > About Plug-ins from the browser menu.

---

### Post by Bölvaður on 2008-11-17
> **BobCFC said:**
> instructions from the....

7. Launch your brower. To verify installation in Firefox choose Help > About Plug-ins from the browser menu. 

it also needs to be linked to /usr/lib/xulrunner-1.9.0.3/plugins doesnt it?

---

### Post by FuturePilot on 2008-11-17
> **Bölvaður said:**
> it also needs to be linked to /usr/lib/xulrunner-1.9.0.3/plugins doesnt it?

Nope, it will work just fine from ~/.mozilla/plugins. It only needs to be placed in /usr/lib/xulrunner-1.9.0.3/plugins if you want it available system-wide.

---

### Post by loomsen on 2008-11-17
Not 2 hard, as it's only one file actually (which I didn't even install)
```

locate flash | grep -v home | grep so

```
And then just link it to common places...This is where mine go for opera
```

/usr/lib/flash-player/flashplayer.so
/usr/lib/flash-plugin/flashplayer.so
/usr/lib/flashplugin-nonfree/flashplayer.so

```

*edit*

Tested, works with opera, CPU load caused by opera while watching youtube videos 1%-3%O:)

---

### Post by Arup on 2008-11-17
> **BobCFC said:**
> Works great on YouTube and BBC iPlayer for me. Just uninstall **flashplugin-nonfree** from Synaptic first

instructions from the [64bit release notes]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html"):

Did you remove the nsplugin as the site suggested?

---

### Post by wmcbrine on 2008-11-17
Is there any chance of this getting into Intrepid? The 32-bit Flash is pretty unstable for me (fortunately it only takes itself out, not the whole browser).

---

### Post by loomsen on 2008-11-17
?

Klick the link above, download it, copy it to the places above, and ship.

```

me[~] uname -a
Linux tiffany 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
me[~] 

```

---

### Post by Arup on 2008-11-17
> **wmcbrine said:**
> Is there any chance of this getting into Intrepid? The 32-bit Flash is pretty unstable for me (fortunately it only takes itself out, not the whole browser).

Why not install as suggested, its relatively easy, just make sure to remove nsplugin wrapper and x32 Flash via Synaptic, do a complete removal which removes all traces of previous flash. If you wait for it to come to the repos, expect a long one.

---

### Post by Retrograde77 on 2008-11-17
Yes :) flash has been the only small niggling problem I had with 64bit Ubuntu.  Installed and working perfectly, and I swear the first time full screen mode in iPlayer has run super smooth.  

Very happy :)

---

### Post by ultravga1280 on 2008-11-17
I removed all traces of Flash and the nsplugin with Synaptic. Unfortunately, when I try to move libflashplayer.so into the /usr/lib/mozilla/plugins folder I get an "Error moving file: Permission denied" message. 

Any thoughts?

---

### Post by Arup on 2008-11-17
> **ultravga1280 said:**
> I removed all traces of Flash and the nsplugin with Synaptic. Unfortunately, when I try to move libflashplayer.so into the /usr/lib/mozilla/plugins folder I get an "Error moving file: Permission denied" message. 

Any thoughts?


You have to do sudo. Make sure your browser is turned off.Do a sudo cp libflashsplayer.so /usr/lib/mozilla/plugins

---

### Post by wmcbrine on 2008-11-17
> **Arup said:**
> If you wait for it to come to the repos, expect a long one.Yeah, I did the manual install, and so far, it's working a lot better than the 32-bit version (it comes up almost immediately, unlike before).

I just like to keep my system as package-managed as possible... funny, 'cause I used to run Slackware and build everything from tarballs... but, that's why I prefer it managed now. I learned my lesson. :)

---

### Post by ultravga1280 on 2008-11-17
> **Arup said:**
> You have to do sudo. Make sure your browser is turned off.Do a sudo cp libflashsplayer.so /usr/lib/mozilla/plugins
Thanks for the youngin' help!

---

### Post by Arup on 2008-11-17
> **wmcbrine said:**
> Yeah, I did the manual install, and so far, it's working a lot better than the 32-bit version (it comes up almost immediately, unlike before).

I just like to keep my system as package-managed as possible... funny, 'cause I used to run Slackware and build everything from tarballs... but, that's why I prefer it managed now. I learned my lesson. :)

I am like that as well, thats why I switched from Mandriva to Ubuntu, however I am also a latest freak so do install stuff from getdeb from time to time, for instance Deluge, Asunder etc. are really good with latest features and that can't be found from the repos. Also in special cases like this, we would have to resort to the manual no rep way.

---

### Post by ultravga1280 on 2008-11-17
> **Arup said:**
> You have to do sudo. Make sure your browser is turned off.Do a sudo cp libflashsplayer.so /usr/lib/mozilla/plugins
Uh-oh. Spoke too soon. Flash 10 is not showing up in Firefox Tools -> Add-ons -> Plugins even though it was successfully copied to /usr/lib/mozilla/plugins. 
Yes, I made sure firefox was closed. 
In addition, youtube, pandora etc... now say I have an old version of flash.

---

### Post by beniwtv on 2008-11-17
Sniff.. I have tears in my eyes right now. :( I didn't think I would ever see the day Adobe releases the Flash Player for 64 bit. 

But on the other hand...

woot! :guitar::popcorn:

:lolflag:

Finally!

Now, for those who have tried it, is is more stable than the 32 bit version? No more grey flash areas? How's the performance?

Cheers,

---

### Post by Arup on 2008-11-17
> **ultravga1280 said:**
> Uh-oh. Spoke too soon. Flash 10 is not showing up in Firefox Tools -> Add-ons -> Plugins even though it was successfully copied to /usr/lib/mozilla/plugins. 
Yes, I made sure firefox was closed. 
In addition, youtube, pandora etc... now say I have an old version of flash.

That means you didn't do a complete removal of Flash from Synaptics, you have to select mark for complete uninstall rather than just uninstall. Now you need to do cd /usr/lib/mozilla/plugins and then rm libflashplayer.so

Then go to Synaptic and look for nonfree-flashplugin and do a complete remove and reinstall Flash 10 same way described above.

---

### Post by mips on 2008-11-17
[http://www.kaourantin.net/2008/11/64-bits.html](http://www.kaourantin.net/2008/11/64-bits.html)

---

### Post by amauk on 2008-11-17
> **beniwtv said:**
> Now, for those who have tried it, is is more stable than the 32 bit version? No more grey flash areas? How's the performance?

Cheers,

More responsive
Definitely more stable
Haven't come across any issues so far

No more white boxes (while nspluginwrapper fires up)
Embedded content loads instantly now
No more grey boxes (when nspluginwrapper fails)

I've been purposefully trying to break it
(loading up and immediately cancelling multiple embedded videos, etc.)

Flash video (youtube & others) seems to be flawless
Flash games work perfectly

I'm very happy at the moment

64-bit flash down
Next on the list, Nvidia supporting compositing across GPU's

---

### Post by blakjesus on 2008-11-17
Any idea when this could make it into the repositories? what im wondering is that if i install it like this and afterwards it makes it into the repositories will i be able to easily update it that way?

---

### Post by H4rold on 2008-11-17
Hi,

 I get a seg fault on gmail and the website [www.deezer.com](www.deezer.com) with this new plugin.
(with ndiswrapper gmail always worked fine and deezer crashed 60% of the time but it just displayed a grey window, nothing like a segfault)

Any clue ?

Thanks

Harold

---

### Post by Arup on 2008-11-17
> **H4rold said:**
> Hi,

 I get a seg fault on gmail and the website [www.deezer.com](www.deezer.com) with this new plugin.
(with ndiswrapper gmail always worked fine and deezer crashed 60% of the time but it just displayed a grey window, nothing like a segfault)

Any clue ?

Thanks

Harold


No segfault here with Opera 9.62, btw thanks for the station.

Did you do a complete remove of older flash and nsplugin?

---

### Post by H4rold on 2008-11-17
> **Arup said:**
> No segfault here with Opera 9.62, btw thanks for the station.

Did you do a complete remove of older flash and nsplugin?

Yep I'll retry.

---

### Post by Arup on 2008-11-17
> **H4rold said:**
> Yep I'll retry.

You need to do complete uninstall via synaptic or sudo apt-get --purge remove nonfree-flashplugin nsplugin-wrapper

---

### Post by H4rold on 2008-11-17
> **H4rold said:**
> Hi,

 I get a seg fault on gmail and the website [www.deezer.com](www.deezer.com) with this new plugin.
(with ndiswrapper gmail always worked fine and deezer crashed 60% of the time but it just displayed a grey window, nothing like a segfault)

Any clue ?

Thanks

Harold

Sorry my fault, I hade removed completely flashplugin-nonfree but not nspluginwrapper.

So be sure to remove flashplugin-nonfree and nspluginwrapper

Seems to work now :)

Thanks.

(it's actually great, a flash plugin that will work most of the time !!!)

---

### Post by pider55 on 2008-11-17
Hi
Just installed Adobe flash x64, and I do not have 
```
"To verify installation in Firefox choose Help > About Plug-ins from the browser menu"
```
If I go to version information : You have version 10,0,20,7 installed
How do I find out if I got the 64 installed?

---

### Post by Luke has no name on 2008-11-17
ONE LITTLE FILE solves all our flash issues. Beautiful, and about damned time.

I know SRUs are rare, but this should be an exception. This is absolutely terrific!

---

### Post by SunnyRabbiera on 2008-11-17
about bloody time

---

### Post by bash on 2008-11-17
Wow. That Adobe managed to bring out something 64bit, didn't think we would see that any time soon. Sadly don't have time to test it yet. Now we just need to hope for a 64-bit Adobe Reader and Skype.

---

### Post by H4rold on 2008-11-17
> **pider55 said:**
> Hi
Just installed Adobe flash x64, and I do not have 
```
"To verify installation in Firefox choose Help > About Plug-ins from the browser menu"
```
If I go to version information : You have version 10,0,20,7 installed
How do I find out if I got the 64 installed?

[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

Last stable version : 10.0.12.36
Last alpha version 10.0.20.7

You've got it :)

---

### Post by zenarcher on 2008-11-17
It's working great here, too!  Just did the 64 bit flash install on three machines.  Thanks so much for this info!

Cheers,
zenarcher

---

### Post by hessiess on 2008-11-17
Finally!

---

### Post by qazwsx on 2008-11-17
64bit is Linux only :lolflag: :popcorn::guitar:

---

### Post by soxs on 2008-11-17
It was about time...

---

### Post by pablosanchezuy on 2008-11-17
web fixed.

Pablo

---

### Post by Afi on 2008-11-17
This is great! Just removed flashplugin nonfree and copied libflashplayer.so to homedir/.mozilla/plugins/ 
It seems to be working great.:)

---

### Post by plun on 2008-11-17
> We are pleased to announce that there is now a version of the Flash Player for Linux that supports 16 theoretical exabytes of physical memory. This technological feat is accomplished using a bleeding edge type of processor known as a 64-bit CPU.  :lolflag:

[http://blogs.adobe.com/penguin.swf/2008/11/now_supporting_16_exabytes.html](http://blogs.adobe.com/penguin.swf/2008/11/now_supporting_16_exabytes.html)


Test for "freaks"....

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by bufsabre666 on 2008-11-17
> **qazwsx said:**
> 64bit is Linux only :lolflag: :popcorn::guitar:

never thought id see the day this line could be used with something regarding flash

EDIT: MY TOTAL NEWB BRAIN KICKED IN: THE DAILY SHOW AND COLBERT REPORT FULL EPS WORK NOW!!!!!!!

---

### Post by Zero Prime on 2008-11-17
It works GREAT!!
And to think, this is an alpha release, I can't wait for the full release.

---

### Post by Arup on 2008-11-17
> **Afi said:**
> This is great! Just removed flashplugin nonfree and copied libflashplayer.so to homedir/.mozilla/plugins/ 
It seems to be working great.:)

Make sure to remove nsplugin or else there can be issues.

---

### Post by gnomeuser on 2008-11-17
Now.. skype I am looking at you, the last widely used 32bit only application (also clean up your freaking mess in the sound area, pulseaudio will help you I promise).

---

### Post by ronacc on 2008-11-17
Thanks plun I d/l'd it and have it installed in jaunty and it seems to work ok and it works with 64bit Opera:) , perhaps you should post that link on the opera linux forum , there are always bitches there about 64bit opera and flash .

---

### Post by aaaantoine on 2008-11-17
Blarg...

I promised myself I would no longer install software that didn't at least come in a .deb package.  Now I might have to make an exception.

---

### Post by OffHand on 2008-11-17
> **aaaantoine said:**
> Blarg...

I promised myself I would no longer install software that didn't at least come in a .deb package.  Now I might have to make an exception.

Well, copying it to a folder in your /home drive isn't really installing it... at least it doesn't leave a mess  ;)

---

### Post by iamnotthemessiah on 2008-11-17
maybe im wrong but wouldnt it be safer to place libflashplayer.so in for example /opt and create a symlimk to it in homedir/.mozilla/plugins/

---

### Post by kperkins on 2008-11-17
Not only is it almost here, it is here.
Yay!!
Thanks for the info on installing folks.
Not only does it work great in Firefox (so far), but it is working in Opera, and Liferea is finally able to play flash videos.  
Again--Yay!!!

And Treasury is working on Etsy for me now.
I'm just giddy with excitement.

---

### Post by Ago12 on 2008-11-17
Great news :)

I mean, it was time!

---

### Post by kperkins on 2008-11-17
> **iamnotthemessiah said:**
> maybe im wrong but wouldnt it be safer to place libflashplayer.so in for example /opt and create a symlimk to it in homedir/.mozilla/plugins/
or maybe even better put it in /opt, and symlink in /usr/lib/mozilla/plugins/?  That way it works for Opera, and maybe some other things also.

---

### Post by plun on 2008-11-17
> **ronacc said:**
> Thanks plun I d/l'd it and have it installed in jaunty and it seems to work ok and it works with 64bit Opera:) , perhaps you should post that link on the opera linux forum , there are always bitches there about 64bit opera and flash .

Well I am not using "16 theoretical exabytes"....:)

I have never understand 64 bits for clients...  except for servers and workstations with a lot of calculations.


It is also a "alpha" and must be threated as an Alpha version until a "couple of freaks" can say its OK after testing ....

---

### Post by LowSky on 2008-11-17
I just read about this on [Yahoo]("http://tech.yahoo.com/news/cnet/20081117/tc_cnet/8301100131009793192")

Im so happy I can now have almost everything running in native 64bit mode.

---

### Post by ronacc on 2008-11-17
someone else has already posted it to the opera linux forum , about the same time as you posted it here .

---

### Post by plun on 2008-11-17
> **ronacc said:**
> someone else has already posted it to the opera linux forum , about the same time as you posted it here .

OK...I saw it on Planet Ubuntu

A testing ppa would be the best solution...

---

### Post by ronacc on 2008-11-17
do we really need a ppa ? just uninstall (completely) flashplugin-nonfree
then unzip the bz2 and copy libflashplayer.so to /usrlib/mozzila/plugins  , anyone that should be testing it should be able to handle that:lolflag:

---

### Post by Slug71 on 2008-11-17
This is good news!

---

### Post by Quikee on 2008-11-17
> **plun said:**
> 
I have never understand 64 bits for clients...  except for servers and workstations with a lot of calculations.


And clients that want to use more than 3GB of RAM in the system without "hacks" like PAE.

---

### Post by Arup on 2008-11-17
Just placing it in /usr/lib/plugin/mozilla works fine for Opera, nothing else is needed except proper removal of old flash plugin and nsplugin.

---

### Post by plun on 2008-11-17
> **Quikee said:**
> And clients that want to use more than 3GB of RAM in the system without "hacks" like PAE.

Well, how many needs more then 3GB RAM  :confused:

and what software ?

Maybe a Windows Vista user with software filled with "concrete"...:lol:

---

### Post by ronacc on 2008-11-17
no one will ever need more than 640k of ram:lolflag:

---

### Post by toupeiro on 2008-11-17
Huzzah!

Thanks for sharing this!

---

### Post by plun on 2008-11-17
> **ronacc said:**
> no one will ever need more than 640k of ram:lolflag:

OK.....:-\"   maybe OT but a great demo. 

**Watch out after 30 seconds !!!**

**Look behind his head  !!!**:shock:


[http://svt.se/svt/road/Classic/shared/mediacenter/index.jsp?&d=99395&a=1312508](http://svt.se/svt/road/Classic/shared/mediacenter/index.jsp?&d=99395&a=1312508)


The man talking is the boss for swedish central bank talking the usual "blah, blah, blah" about crazy companys, its inside the Swedish parlament in a session room for echonomics.  


(for those with broken Flash...[http://ubuntu-pics.de/bild/5716/ubu_kCixWv.jpg](http://ubuntu-pics.de/bild/5716/ubu_kCixWv.jpg)  )

---

### Post by gnomeuser on 2008-11-17
> **plun said:**
> Well I am not using "16 theoretical exabytes"....:)

I have never understand 64 bits for clients...  except for servers and workstations with a lot of calculations.


It is also a "alpha" and must be threated as an Alpha version until a "couple of freaks" can say its OK after testing ....

More registers.. hell string optimization alone makes it worth it.

---

### Post by Zorael on 2008-11-17
> **kperkins said:**
> or maybe even better put it in /opt, and symlink in /usr/lib/mozilla/plugins/?  That way it works for Opera, and maybe some other things also.
Better *yet*, put it in /opt and add it as an xdg-utils alternative, then use update-alternatives --config <alternative> to change between gnash, flash, swfdec and whatnot. I think there's an alternative called **mozilla-flashplayer.so**, no? On a Windows machine right now so can't verify.

It's a messy and needlessly roundabout solution in the sense that you have to go through plugin directories to make sure that you only have one alternative being linked towards - and yet a very beautiful solution in the sense that when that's done, you can change what flash your browsers should use with update-alternatives.

I always sift through /usr/lib/{mozilla,firefox,firefox-3.0,firefox-addons,...}/plugins and make sure that the only flash symlink is in /usr/lib/mozilla/plugins/ and links towards /etc/alternatives/mozilla-flashplayer.so.

---

### Post by insane_alien on 2008-11-17
...and the linux community collectively nerdgasms.

---

### Post by loomsen on 2008-11-17
> **loomsen said:**
> 
```

sudo updatedb
locate flash | grep -v home | grep so

```

This should report any occurrences of flash player on your computer. remove all, in doubt simply by sudo rm <path>/<to>/<flash*>.to.

It's a plugin, nothing will happen to other programs if you remove it.

Then copy the 64bit version to the places where flash usually gets installed to, like for example the three places I posted earlier in this thread.

---

### Post by eragon100 on 2008-11-17
YIPPIIEEEE! Now I might finally move to 64 bit!! And....... It's linux only??? WOOHHHOOOO!!!! :) :popcorn: :KS :guitar:

---

### Post by Half-Left on 2008-11-17
> **eragon100 said:**
> YIPPIIEEEE! Now I might finally move to 64 bit!! And....... It's linux only??? WOOHHHOOOO!!!! :) :popcorn: :KS :guitar:

Yes because our x86_64 is actually worth it and useful. :)

---

### Post by cowanh00 on 2008-11-17
I'm still getting a crash when I view Gmail. I have removed everything as described above.

When I run ```
locate flash | grep -v home | grep so
``` I get ```
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashlx.so

```

The files starting with npwrapper don't seam to exist when I check the folders....

EDIT: Bizarrely after a reboot Gmail isn't crashing FF anymore...weird. So what are those mystery files about?

---

### Post by Polygon on 2008-11-17
i think adobe has had a 64 bit version for windows for a while. its just that there is one exe for all windows platforms and it just chooses which binary to install from there.

---

### Post by eragon100 on 2008-11-17
> **Polygon said:**
> i think adobe has had a 64 bit version for windows for a while. its just that there is one exe for all windows platforms and it just chooses which binary to install from there.

No, this is directly from their website's FAQ about it:

Question: "When will 64-bit versions of Flash Player for Windows and Mac be available?"

Answer: "We expect to provide native support for 64-bit platforms in an upcoming major release of Flash Player. Windows, Macintosh and Linux players will ship at the same time."

A nice video to celebrate: [http://www.youtube.com/watch?v=YCj-RyKCmHQ](http://www.youtube.com/watch?v=YCj-RyKCmHQ) Clear message from adobe to MS: YOU LOSE :popcorn:

---

### Post by ronacc on 2008-11-17
@plun   :)  and btw it plays fine on 64bit Opera with the 64bit flash .

---

### Post by Half-Left on 2008-11-17
It's about time Adobe showed Linux some love, Now port Photoshop and we will welcome you. :guitar:

---

### Post by mrgnash on 2008-11-17
I wish I could share in all the jubilation over this, but I: 1. get no sound, 2. experience terrible performance. Looks like I'll be sticking with the 32-bit version with nspluginwrapper for now... sigh :(

---

### Post by Aenoble on 2008-11-17
Wow, the only thing keeping me from going 64bit. Thank you Adobe :)

---

### Post by loomsen on 2008-11-17
You seem to have missed to update your database.

```

sudo updatedb
```

the locate command uses a database, it doesn't actually perform a live search each time you run locate. So, update you db, and run it again. Should be gone then.

---

### Post by cowanh00 on 2008-11-17
> **loomsen said:**
> You seem to have missed to update your database.

```

sudo updatedb
```

the locate command uses a database, it doesn't actually perform a live search each time you run locate. So, update you db, and run it again. Should be gone then.

Well you learn something everyday! Thanks.

---

### Post by jorgis on 2008-11-17
This had me stumped for a while before finding the solution: in Ubuntu 8.04 (haven't tested in 8.10), you'll need to install the libflashsupport package to have sound from any flash movies. :)

---

### Post by Thelasko on 2008-11-17
> **amauk said:**
> 64-bit flash down
Next on the list, Nvidia supporting compositing across GPU's

I was going to say a 64-bit Java plugin, or at least one that supports LiveConnect.  I guess everyone has their own priorities.

---

### Post by patrickballeux on 2008-11-17
I am currently using it and it seems to work quite well.

I even tried broadcasting my webcam and wouhou! It works! 

The cpu usage seems to be a little lower also (-10%) when I'm broadcasting my webcam (using WebcamStudio for GNU/Linux of course... :) )

This day has to be remembered:  Linux users got it first!

Thanks Adobe!

---

### Post by patrickballeux on 2008-11-17
> **Thelasko said:**
> I was going to say a 64-bit Java plugin, or at least one that supports LiveConnect.  I guess everyone has their own priorities.

It's already available when you install the Sun Java 6 JRE 64 bits.  I think they are using something from the OpenJDK, but Java Applets are running in my browser, 64 bits...

I have no java 32 bits on my setup.

Tips:  Remove any Java, and reinstall only one JRE.  I don't remember the package, but via Synaptic, it will ask you if you want support for the applets.

---

### Post by Thelasko on 2008-11-17
> **patrickballeux said:**
> It's already available when you install the Sun Java 6 JRE 64 bits.  I think they are using something from the OpenJDK, but Java Applets are running in my browser, 64 bits...

I have no java 32 bits on my setup.

Tips:  Remove any Java, and reinstall only one JRE.  I don't remember the package, but via Synaptic, it will ask you if you want support for the applets.

Maybe you mean the [icedtea plugin.]("http://packages.ubuntu.com/intrepid/icedtea6-plugin")  It says it supports LiveConnect.  I'm running Hardy and was under the impression the latest Java was backported.  I must be mistaken.  Thanks for the info.

---

### Post by Vadi on 2008-11-17
I am happily impressed.

---

### Post by wvmac on 2008-11-17
thanks adobe and thanks for posting the instructions BobCFC.
works great.

---

### Post by Foster Grant on 2008-11-17
> **tom66 said:**
> Cool. I don't use 64-bit but I'm sure it will help others who do.

This is one of the things that would convince me to move to 64-bit. In fact, it's been a major obstacle that I've been waiting to see removed.


Further coverage from CNET via Yahoo: [http://tech.yahoo.com/news/cnet/20081117/tc_cnet/8301100131009793192](http://tech.yahoo.com/news/cnet/20081117/tc_cnet/8301100131009793192)

"We chose Linux as our initial platform in response to numerous requests in our public Flash Player bug and issue management system and the fact that Linux distributions do not ship with a 32-bit browser or a comprehensive 32-bit emulation layer by default."

Which does lead to an interesting question (given Apple's success with various emulation layers over the years {Motorola 68k and PowerPC processor emulators during transitions}, why didn't anybody ever try coding up a 32-bit emulation layer for Linux?) but I don't want to start trouble so I won't go there. :)

---

### Post by mips on 2008-11-17
> **Foster Grant said:**
> This is one of the things that would convince me to move to 64-bit. In fact, it's been a major obstacle that I've been waiting to see removed.

Is it really such a big issue? I have been running x86_64 linux for a long period of time now and for me it was never a major obstacle. Yes I did have the occasional issue with flash but it was not bad enought to make me switch back to 32bit.

---

### Post by soxs on 2008-11-17
> **cowanh00 said:**
> I'm still getting a crash when I view Gmail. I have removed everything as described above.

When I run ```
locate flash | grep -v home | grep so
``` I get ```
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashlx.so

```The files starting with npwrapper don't seam to exist when I check the folders....

EDIT: Bizarrely after a reboot Gmail isn't crashing FF anymore...weird. So what are those mystery files about?
You could avoid that by using find (with or without sudo):
```
find /target/folder -iname "*searchword*" | grep "anyword"
```

---

### Post by I-75 on 2008-11-17
Adobe answers cries for 64-bit Flash on Linux

[http://www.download.com/8301-2007_4-10097931-12.html](http://www.download.com/8301-2007_4-10097931-12.html)


"Release of this alpha version of 64-bit Flash Player on Linux is the first step in delivering on Adobe's plans to make Flash Player native 64-bit across platforms," Adobe said in a statement. "We chose Linux as our initial platform in response to numerous requests in our public Flash Player bug and issue management system and the fact that Linux distributions do not ship with a 32-bit browser or a comprehensive 32-bit emulation layer by default. With this prelease, Flash Player 10 is now a full native participant on 64-bit Linux distributions. We are committed to bringing native 64-bit Flash Player to Windows and Mac in future releases. We expect to provide native support for 64-bit platforms in an upcoming major release of Flash Player. Windows, Macintosh and Linux players are expected to ship simultaneously moving forward."

---

### Post by wmcbrine on 2008-11-17
> **wmcbrine said:**
> The 32-bit Flash is pretty unstable for me (fortunately it only takes itself out, not the whole browser).And now the downside of the native 64-bit Flash -- I just had Flash take down my browser for the first time. (It was an embedded Vimeo video on ScienceBlogs -- it crashes it repeatably. I had to remove my FlashBlock exception for ScienceBlogs.)

---

### Post by bash on 2008-11-17
> **gnomeuser said:**
> Now.. skype I am looking at you, the last widely used 32bit only application (also clean up your freaking mess in the sound area, pulseaudio will help you I promise).

We still have the fancy Adobe Reader as well. But with one Adobe program moving to 64-bit maybe the other will as well.

---

### Post by ronacc on 2008-11-17
strange I put the 64bit libflashplayer.so in /usr/lib/mozilla/plugins , Opera finds and uses it , Epiphany finds and uses it, FF3.03 dont :confused:

---

### Post by Slug71 on 2008-11-17
> **ronacc said:**
> strange I put the 64bit libflashplayer.so in /usr/lib/mozilla/plugins , Opera finds and uses it , Epiphany finds and uses it, FF3.03 dont :confused:

Why does that not surprise me! I really hope FF-3.1 is a huge improvement over the 3.0 series.
Has anyone tried FF-3.1 Beta2 with the 64bit Flash yet?

---

### Post by ronacc on 2008-11-17
is there a ppa for it ? I'll give it a shot ,Opera is my main browser so if I trash FF no big loss .

---

### Post by pferraro on 2008-11-17
> **ronacc said:**
> strange I put the 64bit libflashplayer.so in /usr/lib/mozilla/plugins , Opera finds and uses it , Epiphany finds and uses it, FF3.03 dont :confused:

For firefox, use either:
/usr/lib/xulrunner-addons/plugins
/usr/lib/firefox-addons/plugins

The former will make the flash plugin available to your other xulrunner-based apps (if any).

---

### Post by doorknob60 on 2008-11-17
Yeah, it's already in AUR :-D yaourt -S flashplugin-alpha-64



For all you fellow Arch users out there :) Apparently it's also in testing if you'd rather use that. Unfortunately I still need lib32 for Runescape, oh well, Java 64 bit plugin should be coming early next year too :-)

---

### Post by loomsen on 2008-11-17
> **mips said:**
> Is it really such a big issue? I have been running x86_64 linux for a long period of time now and for me it was never a major obstacle. Yes I did have the occasional issue with flash but it was not bad enought to make me switch back to 32bit.

Yes it is. 

Just been chatting to a buddy yesterday, when he told me he installed 32bit Intrepid on his dual core, cause he read of better support for applications in general.

Well, I asked him then to take a screenshot of his CPU history, and so did I.

This is what we got:
[[img]http://www.ubuntu-pics.de/thumb/5911/screenshot_04_BAWFIi.png[/img]](http://www.ubuntu-pics.de/bild/5911/screenshot_04_BAWFIi.png)

Left 32 bit on 64 bit architecture, right mine.

As you see, the processors are not working together, but against each other. Look, if there's capacity for twice 32bit at the same time, and the hardware is meant to deal with both the best way possible, but there's only one block arriving, and due to the system, which can only handle one 32bit block at a time, one of the processors has to handle it, while the other one has to be brought down. 

My graph shows how the CPUs share work, they have the same tendencies.
On a 32bit OS they have to be inverse.

This could be compared to a car driving in a city and a car driving on a highway. Lets say both have massive 6l V12 engines.
The overall consumption of the car driving in the city will most likely be at least 20l/100km, while the car driving down the highway not only drives a lot faster, but because of consistency - usually there aren't red lights or sth on highways - also consumption at lets say 150km/h avg speed will prlly be sth like 12l/100km or so.


At least my buddy was convinced and immediately started grabbing Intrepid amd64 :)

---

### Post by kjb34 on 2008-11-17
I see this the alpha. Does anybody know when the stable version will be out?

---

### Post by ronacc on 2008-11-17
firefox-addons/plugins turned the trick thanks , as I said Opera is my main browser so I'm not up on firefoxes quirks :)

---

### Post by jtgd on 2008-11-17
Has anyone gotten it to work with Konqueror?  I am running Feisty amd64 and it just crashes.
The instructions say not to use nsplugin, but I don't see how to make it work without that.

---

### Post by loomsen on 2008-11-17
Very soon :lolflag:

---

### Post by mrgnash on 2008-11-18
> **doorknob60 said:**
> Yeah, it's already in AUR :-D yaourt -S flashplugin-alpha-64



For all you fellow Arch users out there :) Apparently it's also in testing if you'd rather use that. Unfortunately I still need lib32 for Runescape, oh well, Java 64 bit plugin should be coming early next year too :-)

It's called IcedTea.

---

### Post by jtgd on 2008-11-18
Has anyone gotten it to work with Konqueror? I am running Feisty amd64 and it just crashes.
 The instructions say not to use nsplugin, but I don't see how to make it work without that.

---

### Post by juphro on 2008-11-18
> **jorgis said:**
> This had me stumped for a while before finding the solution: in Ubuntu 8.04 (haven't tested in 8.10), you'll need to install the libflashsupport package to have sound from any flash movies. :)

Flash working great in Opera 9.62, Firefox crashing, installed libflashsupport from Synaptic Package Manager, no sound for flash videos in 8.04 in either. Anyone having similar problems?

---

### Post by mrgnash on 2008-11-18
> **juphro said:**
> Flash working great in Opera 9.62, Firefox crashing, installed libflashsupport from Synaptic Package Manager, no sound for flash videos in 8.04 in either. Anyone having similar problems?

Not exactly. But I'm using OSS4 (with the proper libflashsupport plugin installed), and I'm not getting sound with the 64bit version, and also experiencing lousy performance.

---

### Post by juphro on 2008-11-18
You gave me an idea..! Sound works for me on "autodetect" but not through "usb audio." I can live w/the FF problem; prefer Opera anyway.

---

### Post by doorknob60 on 2008-11-18
> **mrgnash said:**
> It's called IcedTea.
I use it for everything that's not Runescape (sound problems).

---

### Post by mips on 2008-11-18
> **loomsen said:**
> 
This is what we got:
[[IMG]http://www.ubuntu-pics.de/thumb/5911/screenshot_04_BAWFIi.png[/IMG]]("http://www.ubuntu-pics.de/bild/5911/screenshot_04_BAWFIi.png")

Left 32 bit on 64 bit architecture, right mine.

As you see, the processors are not working together, but against each other. Look, if there's capacity for twice 32bit at the same time, and the hardware is meant to deal with both the best way possible, but there's only one block arriving, and due to the system, which can only handle one 32bit block at a time, one of the processors has to handle it, while the other one has to be brought down. 

My graph shows how the CPUs share work, they have the same tendencies.
On a 32bit OS they have to be inverse.


I'm sorry but I strongly have to disagree with you here. There is no reason why the load of multicore cpu's should be in sync. **It all depends on the applications used**. One application could use 100% of a single core while the other core idles at say 5%.

Anyway, how is this related to 64bit flash? Since when does 64bit & multicore go hand in hand?

---

### Post by 3rdalbum on 2008-11-18
> **loomsen said:**
> 

As you see, the processors are not working together, but against each other. Look, if there's capacity for twice 32bit at the same time, and the hardware is meant to deal with both the best way possible, but there's only one block arriving, and due to the system, which can only handle one 32bit block at a time, one of the processors has to handle it, while the other one has to be brought down. 

My graph shows how the CPUs share work, they have the same tendencies.
On a 32bit OS they have to be inverse.

That's not how things work. A 64-bit processor is a processor that can handle longer memory addresses, it's not a processor that can handle twice as much throughput. There's nothing magical about it. A single-threaded program can only be run on one core at a time; you might see the task shifting from one core to another, but it's normal and it happens on 64-bit as well.

If you run a multi-threaded program where two threads are running at full steam, you do not see any sort of inverse effect; you just see two cores running at 100%. This applies on 64-bit as well as 32-bit.

I have not seen any speed improvement since switching to 64-bit, and neither did I expect to.

---

### Post by mips on 2008-11-18
> **3rdalbum said:**
> 
I have not seen any speed improvement since switching to 64-bit, and neither did I expect to.

The only place you will see a big increase in speed is in ripping/encoding audio&video.

---

### Post by eragon100 on 2008-11-18
And in gaming, right?

---

### Post by thefrozenpenguin on 2008-11-18
Works brilliant, hopefully it'll be more stable than 32 bit with pluginwrapper.  Well done Adobe :)

---

### Post by Thelasko on 2008-11-18
Very fast, very stable.  I love it!

---

### Post by stmiller on 2008-11-18
Works great for me in 64bit Firefox. Thank you adobe,

---

### Post by Slug71 on 2008-11-18
> **ronacc said:**
> is there a ppa for it ? I'll give it a shot ,Opera is my main browser so if I trash FF no big loss .

There was a PPA for it during Intrepid build but i cant remember what it was.


Edit: > sudo apt-get install firefox-3.1 firefox-3.1-gnome-support.

Thats what got 3.1 for me when i tested Beta1 i think in Intrepid.

---

### Post by ronacc on 2008-11-18
thanks tried that already ,it comes back firefox-3.1 not found I tried to install from the bz2 from mozilla and it locked up my sys so hard I had to hard reset , no time to investigate now, I'll try more later ,

---

### Post by soxs on 2008-11-18
> **eragon100 said:**
> And in gaming, right?
Not really. I didn't get anything, I think the advantege (if existant at all) is below 1 fps

---

### Post by Frak on 2008-11-18
> **eragon100 said:**
> And in gaming, right?
For pre-rendering (such as Quake III loading), yes. For live gameplay, no. Oh, and the game has to be 64-bit native, not just a recompilation of a 32-bit version.

---

### Post by loomsen on 2008-11-18
64bit means 8octets wide, right? Assuming a highway with 4 lanes, and one with 8 lanes. 

If there are 10 cars an hour, you don't feel the difference, cause theres enough space for both. But the higher the load gets, the more cars can pass the highway with 8 lanes, while the 4 lane highway reaches his max capacity. 

Therefore you won't notice to much of a difference with low system loads, but compiling, riping, encoding, when your CPU is under full load, will show.

Comparing low system loads is like saying hey, if carl lewis and me are going for a walk, I'm just as fast as him!

---

### Post by youssef77 on 2008-11-18
You can play youtube but it crashes FF when I use couple of Flex apps. 
Went to Flex showcases and it crashes too 
e.g. 
Try this [http://www.weberdesignlabs.com/flexibletask/FlexibleTasks.html](http://www.weberdesignlabs.com/flexibletask/FlexibleTasks.html)

---

### Post by samjh on 2008-11-18
Yipee!  Nice effort by Adobe! :)

It's surprisingly stable for an alpha release.  I was expecting a lot of crashes, but there haven't been any so far.

---

### Post by SunnyRabbiera on 2008-11-18
> **samjh said:**
> Yipee!  Nice effort by Adobe! :)

It's surprisingly stable for an alpha release.  I was expecting a lot of crashes, but there haven't been any so far.

well the flash 10 series seems to be be more stable then 9 by most reports

---

### Post by aktiwers on 2008-11-18
This is great!!!   This alpha release runs 100 times better than the 32bit on 64bit..  ! 
Awesome!

---

### Post by ronacc on 2008-11-18
just to update , the lockup was a coincidence not related to the FF3.1 bz2 and never returned , I couldn't get it to install anyway, it keeps saying libuuid isnt installed when infact it is ,  and since the installer is a binary I can't hack it to point it at the right place . I did find the PPA from intrepid for FF and he has a jaunty dir but no ff3.1 in there yet . heres a link to the PPA    [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu)    .

---

### Post by pgatrick on 2008-11-18
> **jtgd said:**
> Has anyone gotten it to work with Konqueror?  I am running Feisty amd64 and it just crashes.
The instructions say not to use nsplugin, but I don't see how to make it work without that.

I'm not on Ubuntu, but the 64bit flash works fine with konqueror here. Just put libflashplayer.so in /usr/lib/mozilla/plugins, /usr/lib/iceweasel/plugins, or whatever directory, and have konqueror rescan for plugins.

---

### Post by Ocxic on 2008-11-18
Just installed works great

---

### Post by bufsabre666 on 2008-11-18
> **samjh said:**
> Yipee!  Nice effort by Adobe! :)

It's surprisingly stable for an alpha release.  I was expecting a lot of crashes, but there haven't been any so far.

seriously no crashes yet over here, this seems way more stable the 32bit on 32bit let alone 32bit on 64bit

---

### Post by jtgd on 2008-11-19
> **pgatrick said:**
> I'm not on Ubuntu, but the 64bit flash works fine with konqueror here. Just put libflashplayer.so in /usr/lib/mozilla/plugins, /usr/lib/iceweasel/plugins, or whatever directory, and have konqueror rescan for plugins.
I did that, and it finds the flashplayer, but it crashes on any flash page (the flash crashes, not Konqueror).  I assume it's because the instructions say not to use nsplugin but there is no way to use it without nsplugin.  Does anybody know of a way to get the flash player plugged into Konqueror without nsplugin?

---

### Post by xebian on 2008-11-19
> **jtgd said:**
> I did that, and it finds the flashplayer, but it crashes on any flash page (the flash crashes, not Konqueror).  I assume it's because the instructions say not to use nsplugin but there is no way to use it without nsplugin.  Does anybody know of a way to get the flash player plugged into Konqueror without nsplugin?

You mean like white or grey screen?  You just have to be patient and do a page reload.  Konqueror play Flash with the nspluginviewer module.
This is different from the nspluginwrapper that FFox use for the 32-bit.

---

### Post by jtgd on 2008-11-19
> **xebian said:**
> You mean like white or grey screen?  You just have to be patient and do a page reload.  Konqueror play Flash with the nspluginviewer module.
This is different from the nspluginwrapper that FFox use for the 32-bit.

It seems as though nspluginwrapper is meant for running 32-bit plugins in a 64-bit environment.  Why do we need that for a 64-bit plugin?

I do have partial success.  I did reload and after dismissing crash handler and javascript error boxes and reloading 1-3 times I do eventually have a playing flash, so YEAH!  But can it be made to play right the first time?

---

### Post by xebian on 2008-11-19
> **jtgd said:**
> It seems as though nspluginwrapper is meant for running 32-bit plugins in a 64-bit environment.  Why do we need that for a 64-bit plugin?

nspluginwrapper != nspluginviewer

nspluginwrapper is an application to make the 32-bit flash act/look like 64-bit so FireFox can play flash in 64-bit environment.  So with the native 64-bit Flash, there is no need for the nspluginwrapper.

nspluginviewer is a module used by Konqueror to play Flash whether native 64-bit or 32-bit 'wrapped' to look/act like 64-bit.

> **jtgd said:**
> 
I do have partial success.  I did reload and after dismissing crash handler and javascript error boxes and reloading 1-3 times I do eventually have a playing flash, so YEAH!  But can it be made to play right the first time?

I'm sure the Konqueror devs are now looking into this.

---

### Post by mrgnash on 2008-11-19
It's not stable, or even functional, if you're using anything other than Alsa/Pulseaudio. 

I'm still not impressed.

---

### Post by grappler on 2008-11-19
I just installed on intrepid. 

After the install I restarted firefox and it crashed on gmail - a major issue! But after a reboot it appears stable - and at last I can view the videos at Comedy Central again!

---

### Post by miggols99 on 2008-11-19
Works perfectly for me :D And even the right click menu is themed now instead of ugly grey :) Also looks like it's a lot less CPU intensive as well.

---

### Post by Vadi on 2008-11-19
> **mrgnash said:**
> It's not stable, or even functional, if you're using anything other than Alsa/Pulseaudio. 

I'm still not impressed.

I have a feeling they weren't out to impress you in a clearly labelled alpha release ;)

(and you know, they *do* have a bugtracker)

---

### Post by mrgnash on 2008-11-19
> **Vadi said:**
> I have a feeling they weren't out to impress you in a clearly labelled alpha release ;)

(and you know, they *do* have a bugtracker)

I ended up finding the solution on the [Open Sound Forums](http://www.4front-tech.com/forum/viewtopic.php?t=2960). I should have realized from the start that I would need a **64bit** version of libflashsupport compiled with OSS4 support. 

Anyway, compiled it from source, and now the 64bit version of Flash runs fine. I still think it would be nice if they supported OSS by default -- particularly if they want to support BSD systems in addition to Linux -- but even Swfdec doesn't do that, so oh well.

---

### Post by emshains on 2008-11-19
> **Arup said:**
> I removed the x32 plugin via synaptic and just did a sudo cp libflashplayer.so .usr/lib/mozilla/plugin and it works fine, both FF and Opera picked it up without any issues and youtube runs fine on both browsers. Many thanks to BobCFC for posting the good news. Now its all x64. Hopefully I can remove getlibs as well as its no loger needed.

I may be a little bit behind the main-stream news, because I haven't been visiting this site for a while, but since when did opera, on linux, support flash ?

---

### Post by Crinos512 on 2008-11-19
[http://www.osnews.com/story/20549/Adobe_Releases_64-bit_Flash_Alpha_for_Linux](http://www.osnews.com/story/20549/Adobe_Releases_64-bit_Flash_Alpha_for_Linux) :popcorn:
 
> "An alpha version of [64-bit Adobe Flash Player 10]("http://labs.adobe.com/technologies/flashplayer10/") for Linux operating systems was released on 11/17/2008 and is available for download. This offers easier, native installation on 64-bit Linux distributions and removes the need for 32-bit emulation." The pre-release can be downloaded from [Adobe Lab Downloads]("http://labs.adobe.com/downloads/flashplayer10.html").



Interestingly enough Adobe has chosen Linux as its initial platform of choice to launch their native 64-bit flash-player. The reason behind this decision is explained in their [FAQ]("http://labs.adobe.com/technologies/flashplayer10/faq.html"). 
 
Key New Features: 
[LIST]
[*]3D Effects
[*]Custom Filters and Effects
[*]Advanced Text Layout
[*]Enhanced Drawing API
[*]Visual Performance Improvements
[*]Enhanced Sound APIs
[/LIST]

---

### Post by Thelasko on 2008-11-19
[From 2 days ago.]("http://ubuntuforums.org/showthread.php?t=985479")

Sorry to burst your bubble.

P.S. It's not too hard to install, just uninstall the old plugin and nspluginwrapper and put the new plugin in ~/.mozilla/firefox/plugins

---

### Post by drs305 on 2008-11-19
On the positive side, I've been running it without any issues since its release. :)

---

### Post by steveneddy on 2008-11-19
I saw this today at work and finally got around to installing it tonight.

All of my issues I ever has before are finally gone.

The drop down menus finally drop down over the main flash video on a web page.

This is finally what we were needing.

---

### Post by Roger_Smith on 2008-11-20
Been running for awhile here, so far the difference in performance great.

Noticed sites with a lot of flash on them still seem to have some issues, but for alpha software can't complain here.

---

### Post by Progressive on 2008-11-20
Working fantastically! (in Firefox at least)

I used to have to refresh the page occasionally because the flash player wouldn't load properly.

Can't wait for it to work in Konqueror!

---

### Post by mips on 2008-11-20
> **emshains said:**
> I may be a little bit behind the main-stream news, because I haven't been visiting this site for a while, but since when did opera, on linux, support flash ?

Opera since 9.50 (I think) has it's own built in 32-bit wrapper. It works just fine for me.

---

### Post by fjgaude on 2008-11-20
Did you folks uninstall the Ubuntu-installed wrapper and flash before you installed the Adobe 10?

---

### Post by Roger_Smith on 2008-11-20
Yes, you have to uninstall the flashplugin-nonfree and nspluginwrapper.

Then you can either create a plugins folder in ~/.mozilla or put the new flash pluging into the /usr/lib/mozilla/plugins folder. For now I put it in the ~/.mozilla so its easily removed, but if you have multiple users, the /usr/lib/mozilla/plugins folder would be your best option.

---

### Post by fjgaude on 2008-11-20
Thanks, the beginning of a new ear for Linux, eh?

---

### Post by Progressive on 2008-11-20
After restarting X Server, Flash seems to be working in Konqueror, but I'm having a similar problem as with the 32 bit version, where I have to refresh the page occasionally.

---

### Post by motang on 2008-11-20
Well I took the plunge into 64bit computing since Flash is out...love it!  Thanks Adobe! :-D

---

### Post by istblacken on 2008-11-21
yesterday i installed it and it is perfectly stable for a alpha software, though it still has this annoying bug about unicode input [http://bugs.adobe.com/jira/browse/FP-40](http://bugs.adobe.com/jira/browse/FP-40)

---

### Post by rv65 on 2008-11-21
OSS will require a 64 bit libflashsupport.so. There are ways to do it though. I used a script from queleimporta and it worked fine. Could have done it by doing the actual instructions but the script works. Just have to get audio working since I will have to compile a 64 bit libflashsupport in order for it to work. Someone should try it and make a how-to in the Open Sound Help document. Making a section for 64 bit flash would also help.

---

### Post by _alex_ on 2008-11-21
Seems to perform worse on vimeo videos compared to 32bit+nspluginwrapper. For example, this video [http://www.vimeo.com/1211060?pg=embed&sec=1211060](http://www.vimeo.com/1211060?pg=embed&sec=1211060) played back smoothly before, now it stutters in the 64bit alpha.

Can anyone confirm?

Alex

---

### Post by Thelasko on 2008-11-21
> **_alex_ said:**
> Seems to perform worse on vimeo videos compared to 32bit+nspluginwrapper. For example, this video [http://www.vimeo.com/1211060?pg=embed&sec=1211060](http://www.vimeo.com/1211060?pg=embed&sec=1211060) played back smoothly before, now it stutters in the 64bit alpha.

Can anyone confirm?

Alex

[Write a bug report.]("https://bugs.adobe.com/flashplayer/")

---

### Post by _alex_ on 2008-11-21
> **Thelasko said:**
> [Write a bug report.]("https://bugs.adobe.com/flashplayer/")

That's actually the point of why I'm asking. If someone can confirm that this isn't an isolated case*, I'd be more than happy to.

* I mess with my system quite a bit, so it's far removed from a default install.

---

### Post by Thelasko on 2008-11-21
> **_alex_ said:**
> That's actually the point of why I'm asking. If someone can confirm that this isn't an isolated case*, I'd be more than happy to.

* I mess with my system quite a bit, so it's far removed from a default install.

Do it anyway.  Part of any good bug tracking system is confirmation.

---

### Post by slowtrain on 2008-11-28
Hi folks:  I don't seem able to get Firefox to recognize the Flash 10 plugin (doesn't show in Tools > Add-Ons and Flash sites indicate I'm missing a Flash player).  I completely removed both nspluginwrapper and flashplugin-nonfree, not once but twice (reinstalled then completely removed).

I've tried putting the libflashplayer.so in:

~/.mozilla/plugins
~/.mozilla/firefox
/usr/lib/mozilla/plugins
/usr/lib/xulrunner-addons/plugins
/usr/lib/firefox-addons/plugins

Still, the plugin isn't recognized by Firefox.  Am running Firefox 3.0.4 on the latest stable release Intrepid system.

My only guess as to what might be causing this is perhaps interference from another plugin that handles Flash files.  I've got the following web browser plugins that supposedly can run Flash:  Totem and Xine.  I'm not sure whether these are normal for Ubuntu or whether I might have added them a long time ago in an effort to see Flash movies.  I could try erasing them if they aren't normal to the system.  On the other hand, it's not clear to me why these would prevent Firefox from even seeing the Flash 10 plugin.

Any thoughts? 

Slowtrain

---

### Post by mrgnash on 2008-11-28
> **slowtrain said:**
> Hi folks:  I don't seem able to get Firefox to recognize the Flash 10 plugin (doesn't show in Tools > Add-Ons and Flash sites indicate I'm missing a Flash player).  I completely removed both nspluginwrapper and flashplugin-nonfree, not once but twice (reinstalled then completely removed).

I've tried putting the libflashplayer.so in:

~/.mozilla/plugins
~/.mozilla/firefox
/usr/lib/mozilla/plugins
/usr/lib/xulrunner-addons/plugins
/usr/lib/firefox-addons/plugins

Still, the plugin isn't recognized by Firefox.  Am running Firefox 3.0.4 on the latest stable release Intrepid system.

My only guess as to what might be causing this is perhaps interference from another plugin that handles Flash files.  I've got the following web browser plugins that supposedly can run Flash:  Totem and Xine.  I'm not sure whether these are normal for Ubuntu or whether I might have added them a long time ago in an effort to see Flash movies.  I could try erasing them if they aren't normal to the system.  On the other hand, it's not clear to me why these would prevent Firefox from even seeing the Flash 10 plugin.

Any thoughts? 

Slowtrain

What does your about:plugins say?

---

### Post by slowtrain on 2008-11-28
Hi mrgnash:  The only references to flash I see in about:plugins are under Totem and Xine.  Adobe Flash doesn't appear at all.  

I did notice that under .mozilla I have a file called pluginreg.dat that looks like a "database" of applications for running given files.  In that, there are references to flashplugin-nonfree/npwrapper and Shockwave Flash 9.0--even though those have been wiped off my system.  There's no reference to Flash 10 & I'm wondering whether I need to somehow get Flash 10 into this database.  On the other hand, pluginreg.dat says it's a generated file and asks that it not be edited.  

One weird thing I've noticed in the past is that even though I have set my Preferences > Applications to "always ask" what application to use for swf files, it has never asked and has always tried using Flash 9.  Evidently, something in my system, perhaps the pluginreg.dat file, is setting me to use Flash 9.

---

### Post by slowtrain on 2008-11-28
Hi again:  Success!  I renamed pluginreg.dat so the software couldn't use it.  I also reinstalled libflashplayer.so (it's possible I might have gotten version 10 mixed up w/ another version sitting on my system).  Between the two changes, Firefox can now see Flash 10, and I can run CBS TV shows--pretty nice!  One thing that still doesn't work is NBC Video Rewind.

---

### Post by mrgnash on 2008-11-28
> **slowtrain said:**
> Hi again:  Success!  I renamed pluginreg.dat so the software couldn't use it.  I also reinstalled libflashplayer.so (it's possible I might have gotten version 10 mixed up w/ another version sitting on my system).  Between the two changes, Firefox can now see Flash 10, and I can run CBS TV shows--pretty nice!  One thing that still doesn't work is NBC Video Rewind.

Glad to hear that you got it working :) Flash can be a bit tricky at times when switching between/upgrading to different versions. It usually pays to make sure that you clear all the Flash-related plugins from the relevant directories, and run ldconfig. Sometimes it's also worthwhile deleting/renaming pluginreg.dat, as you did :)

---

### Post by slowtrain on 2008-11-28
Thanks mrgnash.  Incidentally, how would you use ldconfig?  Feed it the directory in which libflashplayer.so is located?  It does seem my new Flash is a bit unstable--took down my browser.

---

### Post by vgrisham on 2008-11-29
> **BobCFC said:**
> Works great on Youtube and iPlayer for me.  Just uninstall flashplugin-nonfree from Synaptic first

instructions from the [64bit release notes]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html"):

Wow, that was easy. 

And we're the first to get 64-bit flash! Nice touch Adobe!

---

### Post by mrgnash on 2008-11-29
> **slowtrain said:**
> Thanks mrgnash.  Incidentally, how would you use ldconfig?  Feed it the directory in which libflashplayer.so is located?  It does seem my new Flash is a bit unstable--took down my browser.

I just run it as:

```
sudo ldconfig
``` 

-- without any additional parameters.

---

### Post by slowtrain on 2008-11-30
Thanks mcgnash!  When I run that, I get a number of lines similar to:

/sbin/ldconfig.real: /lib32/libQtGui.so.4 is not a symbolic link

I've noticed this before when installing software, and as far as I can tell it hasn't been a problem.  i think this began when i initially installed Skype on my 64 bit system.  Any thoughts on what, if anything, should be done about this?

---

### Post by kioftes on 2008-12-02
Installs like a charm on kubuntu intrepid! Refreshing a couple of times is still necessary with konqueror (i wonder whether this is an issue with flash or npviewer...). Keep up the good work (and hope to see it in repos soon ;-))!!

---

### Post by mrgnash on 2008-12-02
> **slowtrain said:**
> Thanks mcgnash!  When I run that, I get a number of lines similar to:

/sbin/ldconfig.real: /lib32/libQtGui.so.4 is not a symbolic link

I've noticed this before when installing software, and as far as I can tell it hasn't been a problem.  i think this began when i initially installed Skype on my 64 bit system.  Any thoughts on what, if anything, should be done about this?

Nope, sorry, I have no idea :( I haven't seen that error message before, and it doesn't look like it's related to Flash anyway.

---

### Post by Laysan_A on 2008-12-21
HURRAY!!! 
I was feeling frustrated and confused because I could watch Hulu but not CBS. FIXED!!!
THANK YOU ALL!!!

---

### Post by MikeTheC on 2008-12-22
> **pt123 said:**
> damn so whinging works

Whinging? As in "winging it"? I'd just as soon not wing it when I can do it properly.

However, at the moment I'm not running 64bit Ubuntu, so it really doesn't matter. But I am glad Adobe did it, though.

Guess that means when I do finally get a new laptop I can go 64 bit on it. (Well, assuming no other app or driver issues...)

---

### Post by samjh on 2008-12-22
Whinging = complaining in an annoying manner. ;)

---

### Post by MikeTheC on 2008-12-22
> **samjh said:**
> Whinging = complaining in an annoying manner. ;)

Oh! You mean "whining". Sorry, I thought you meant some other expression.

---

### Post by samjh on 2008-12-22
Not whining.  Whining is pronounced like "wining".

The other word is whinging, which is pronounced like "winjing".

---

### Post by Frak on 2008-12-22
> **MikeTheC said:**
> Oh! You mean "whining". Sorry, I thought you meant some other expression.

> **samjh said:**
> Not whining.  Whining is pronounced like "wining".

The other word is whinging, which is pronounced like "winjing".

Both are correct synonyms of "complaint". They share the same definition.

---

### Post by Listen2TheTruth on 2008-12-22
Read this post before it gets deleted and my account suspended.

I guess there will always be people who can look at gold and throw it away and think its "fake" or "can't be" or "im an ignorant moron". Pick one of the above im pretty sure you are right up there with any of the above described. 

Ok to clarify. I've build and been using an HHO system in my car for the past 6 months. If anyone can tell you about results, its not a oil lobbied PhD holder, a fake scientist or a opinionated freak who is so paraniod thinking his birth is a conspiracy, no..but someone like me- a regular consumer who has used it and loves it to death!

I drive a volvo that gets 31 MPG HWY with my HHO system off, 53MPG HWY with it on. Any questions? Didnt think so! 

Besides some of you (removed by moderator) forgot that Hydrogen can be extracted from water using electroalysis with solar panels, windenergy etc. so although the extraction process may not be 100% efficient, it sure as hell can be "FREE" if we choose to. 

Oil requires a hell lot of energy to obtain too. Researching, Drilling, Extracting, destilling etc...look at all the processes that it has to go through before it can be made available as a combustable gas. Do some research before you post your ignorant, nonsensical opinions on a topic you have no idea about! 

Do a google search on zero point energy or zero field energy, a guy in kansas invented a device that produces more energy (output)than the energy put into the system to extract it (input). Thats the future of energy "creation" and if you are one of those misleading, good-for-nothing opinionated pinheads thinking "oh matter can neither be created nor distroyed - i learned that in High School...waahhh waahhhh cryyy cryyy" then all i have to say is "you have been living on the moon" for science and technology is a dynamic world and it changes every nanosecond of your existence! So get with the plan and stop being ignorant and crying about a solution that really works!

Lastly, watch ZEITGEIST 1 + 2 and be changed forever.

---

### Post by innerproduct on 2009-02-12
The install script on this website works seamlessly:

(I ran it using "sudo sh <scriptname>")

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

---

### Post by HuaiDan on 2009-02-24
!!!!!
I thought this was about a Flash editor for Linux. Any idea when one of those will be released?  I'm a bit astonished by the lack of literature on the conspicuous absence of an SWF editor for Linux.  Half the internet is flash animation, yet you can't do that in Linux. Hmmm.

---

### Post by MasterNetra on 2009-02-24
> **HuaiDan said:**
> !!!!!
I thought this was about a Flash editor for Linux. Any idea when one of those will be released?  I'm a bit astonished by the lack of literature on the conspicuous absence of an SWF editor for Linux.  Half the internet is flash animation, yet you can't do that in Linux. Hmmm.

*Seconds this*
Although there is Synfig Studio...but that isn't flash, suppose to be similar though, haven't used it myself however.

---

### Post by HuaiDan on 2009-02-24
There's Uira, and F4L, but they're not mature. Synfig's tools and interface are the most mature, but can't edit .fla's or .swf's.


Those three guys (Synfig, Uira, and F4L) ought to get together and combine their efforts.


Mark my words:  a true flash editor for linux will make linux's popularity explode.  So many kids out there want to do flash games and scripts, and open source flash could give them the opportunity.

---

