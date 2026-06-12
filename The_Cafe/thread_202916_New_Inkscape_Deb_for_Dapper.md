---
title: "New Inkscape: Deb for Dapper"
date: 2006-06-24
forum: The Cafe
---

### Post by kleeman on 2006-06-24
Version 0.44 of inkscape has lots of interesting new features. See here:

[http://www.inkscape.org/](http://www.inkscape.org/)

The site is slashdotted at present so I compiled a Dapper deb using their Debian infrastructure (i.e. it is a higher quality deb than that produced by checkinstall). Looks nice! Grab it here:

[http://www.yourfilelink.com/get.php?fid=126052](http://www.yourfilelink.com/get.php?fid=126052)

Install using

sudo dpkg -i inkscape_0.44-1_i386.deb

---

### Post by gingermark on 2006-06-24
Pah, I preferred the old .43 "About" splash screen...

Thanks for the deb by the way!

---

### Post by beercz on 2006-06-24
[QUOTE=kleeman]Version 0.44 of inkscape has lots of interesting new features. See here:

[http://www.inkscape.org/](http://www.inkscape.org/)

The site is slashdotted at present so I compiled a Dapper deb using their Debian infrastructure (i.e. it is a higher quality deb than that produced by checkinstall). Looks nice! Grab it here:

[http://www.yourfilelink.com/get.php?fid=126052](http://www.yourfilelink.com/get.php?fid=126052)

Install using

sudo dpkg -i inkscape_0.44-1_i386.deb[/QUOTE]
Thanks kleeman

---

### Post by lapsey on 2006-06-24
Not bad. unlike the ubuntu binary, this version doesn't constantly crap all over gtk and eventually crash :cool:

I like some of the interface changes but they could still do with getting rid of most of the popup dialog windows and getting a bit more layout polish in there

---

### Post by kleeman on 2006-06-24
Played around with it a bit and it works quite well. Colored arrows would be nice,,,,

---

### Post by bruce89 on 2006-06-24
[QUOTE=gingermark]Pah, I preferred the old .43 "About" splash screen...[/QUOTE]
The new one fits in to the Dapper colours (orange) though, but I prefer the old one.  Actually it fitted in with the Breezy colours (brown).

---

### Post by MetalMusicAddict on 2006-06-24
NICE! The new "Layers" dialog was need.

---

### Post by dare2dreamer on 2006-06-24
the deb coughed up the following error 

dependancy not satisfiable: libpango1.0-0

---

### Post by kleeman on 2006-06-24
[QUOTE=dare2dreamer]the deb coughed up the following error 

dependancy not satisfiable: libpango1.0-0[/QUOTE]
Are you using Dapper?

---

### Post by mduran on 2006-06-24
thanks, works ok

---

### Post by jasay on 2006-06-24
[QUOTE=kleeman]Are you using Dapper?[/QUOTE]Oddly enough, dapper has a newer version of libpango1.0-0 than edgy does.  I couldn't install the new inkscape on edgy, I wonder if that was his problem.

---

### Post by zenwhen on 2006-06-24
Works great here. Thanks.

---

### Post by alphaomega on 2006-06-24
I used autopackage...harking back to my old xandros/mandrake days....arrrgh
installed fine

I just checked out some of the new features. Clipping Mask works great, seems to be able to export to a few new file types. Interface/GUI a bit different. Not a fan of the icons, but at least they aren't trying to copy adobe. They added some effects. Good effort. Hope they add to to the respositories. It's an excellent upgrade.

---

### Post by lapsey on 2006-06-24
[QUOTE=alphaomega]Not a fan of the icons, but at least they aren't trying to copy adobe.[/QUOTE]

what's wrong with that? 
for the most part adobe's interfaces are near to perfect for the job .. to deviate significantly from those is like insisting on making a chair or a table with only 2 legs.

---

### Post by dare2dreamer on 2006-06-25
Yes, on dapper. Seems I actually have a more recent version of libpango than it requires.

Any chance of a fix?

---

### Post by rai4shu2 on 2006-06-25
There's a new libpango going around? Here's the one I have:

```
libpango1.0-0:
  Installed: 1.12.3-0ubuntu1
  Candidate: 1.12.3-0ubuntu1
```

---

### Post by vinodis on 2006-06-25
you can easily get rid of the dependency issues if you choose to install with the Inkscape AutoPackage option!
Autopackage works perfectly.

---

### Post by sipstar on 2006-06-25
Works great! Thanks!
:KS

---

### Post by kleeman on 2006-06-25
[QUOTE=dare2dreamer]Yes, on dapper. Seems I actually have a more recent version of libpango than it requires.

Any chance of a fix?[/QUOTE]
Usually a later version is not a problem. What version of libpango have you got? Is it the Dapper one (check using the properties tag in synaptic).

---

### Post by neoncode on 2006-06-26
[QUOTE=gingermark]Pah, I preferred the old .43 "About" splash screen...

Thanks for the deb by the way![/QUOTE]
I thought that the .43 "About" Splash was hideous myself. I **much** Preffer the new one.
And thank you so much for the .deb! I'm on Kubuntu and for some reason the compile was not working. ](*,) (But the .deb works for me, horray for package management!)

---

### Post by bruce89 on 2006-06-26
[https://launchpad.net/distros/ubuntu/+source/pango1.0](https://launchpad.net/distros/ubuntu/+source/pango1.0) reveals that Pango on Edgy is 1.12.2-0ubuntu3 and Dapper is 1.12.3-0ubuntu1.  This is because when Dapper was released, 1.12.2-0ubuntu3 was the latest, so Edgy inherited it.  1.12.3-0ubuntu1 is a dapper-update.  I can't use the DEB as I have an AMD64 (no I will not --force-architechure), I'll just wait for a backport.

---

### Post by kleeman on 2006-06-26
[QUOTE=bruce89][https://launchpad.net/distros/ubuntu/+source/pango1.0](https://launchpad.net/distros/ubuntu/+source/pango1.0) reveals that Pango on Edgy is 1.12.2-0ubuntu3 and Dapper is 1.12.3-0ubuntu1.  This is because when Dapper was released, 1.12.2-0ubuntu3 was the latest, so Edgy inherited it.  1.12.3-0ubuntu1 is a dapper-update.  I can't use the DEB as I have an AMD64 (no I will not --force-architechure), I'll just wait for a backport.[/QUOTE]
So if this was the problem for dare2dream then he should install the latest libpango from dapper-update on his edgy platform ......

---

### Post by bruce89 on 2006-06-26
[QUOTE=kleeman]So if this was the problem for dare2dream then he should install the latest libpango from dapper-update on his edgy platform ......[/QUOTE]
I suppose that might work.

---

### Post by volfro on 2006-06-28
Awesome work!

Installed and functions perfectly for me.  I'm really glad you did this, as I was chomping at the bit for the new version, and waiting on Ubuntu repos is gruelling when all you want is some dang layer masking abilities.

Thanks so much!

---

### Post by tikal26 on 2006-06-28
I get the following error message
dpkg-deb: `inkscape_0.44-1_i386.deb' is not a debian format archive
dpkg: error processing inkscape_0.44-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 inkscape_0.44-1_i386.deb
any help?

---

### Post by kleeman on 2006-06-28
Sounds like your download did not complete and you have a corrupted file. Try to redownload.

---

### Post by OneSeventeen on 2006-07-21
Cool, thanks for this update!!

I'm redesigning my department's website with inkscape:
[img]http://bin.woventhorns.com/pageRender_01_small.png[/img]
(rough draft)

Such an awesome tool, and even though I've been using this version for a month in windows to show other people, I still didn't know about the layers pallette!!! awesome!

---

### Post by Irony on 2006-07-22
Should I uninstall the 0.43 version or will this 0.44 version just upgrade the 0.43 version like it was from the repositories?

---

### Post by kleeman on 2006-07-22
> **Irony said:**
> Should I uninstall the 0.43 version or will this 0.44 version just upgrade the 0.43 version like it was from the repositories?
No need, it is a fairly good deb so just install the new version and don't bother unistalling the Dapper version

---

### Post by OneSeventeen on 2006-07-22
> **kleeman said:**
> Version 0.44 of inkscape has lots of interesting new features. See here:

[http://www.inkscape.org/](http://www.inkscape.org/)

The site is slashdotted at present so I compiled a Dapper deb using their Debian infrastructure (i.e. it is a higher quality deb than that produced by checkinstall). Looks nice! Grab it here:

[http://www.yourfilelink.com/get.php?fid=126052](http://www.yourfilelink.com/get.php?fid=126052)

Install using

sudo dpkg -i inkscape_0.44-1_i386.deb

Would you mind if I put this on my website to avoid the javascript download and advertisements?  (I guess it is technically Open Source, but I'd rather have permission first, in case you would prefer to keep it on yourfilelink.com for some reason)

---

### Post by Irony on 2006-07-24
Thanks kleeman it installed fine (Dapper) with the GDebi installer - the 0.44 version replaced the 0.43 version like you said.

---

### Post by 'ntoni on 2006-08-09
thanks, it works well and much better than the 0.43 default one. I think that this package may better replace the old one in the repos. Bye,
'ntoni

---

### Post by bluntu on 2006-08-16
I can't seem to download that .deb file...

Is there anyway you can upload it elsewhere like, wikiupload.com?

---

### Post by Highlag on 2006-09-03
I am trying to use Tile clone tool but colour controls does not work yet. Is this a bug or is this feature not implemented yet?  Anyone knows anything about it? Or perhaps someone can point in right direction for asking this question. 

Also where can I look for translating the program? 

Just upgraded to V 0.44 as mentioned in first post of this thread. 



I just love this program =D>  
Hope it stays free...

---

### Post by Garyu on 2006-09-03
very nice. works like a charm, and much nicer interface this time around. :)

there should be a special forum/thread that is moderated and kept tidy with all the latest howto's on where and how to get the latest apps for ubuntu since the repos sometimes are months behind...

---

### Post by Ryan H on 2006-12-31
I am on Drapper 64-bit edition and I force installed okay but now I get this error: > inkscape: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
I know I have libgtkmm-2.4-1c2a installed, what's the problem?

-Ryan H

---

### Post by kleeman on 2006-12-31
> **Ryan H said:**
> I am on Drapper 64-bit edition and I force installed okay but now I get this error: 
I know I have libgtkmm-2.4-1c2a installed, what's the problem?

-Ryan H
Your problem may be with forcing a i386 deb. Deinstall it and install this one instead:

[http://www.math.nyu.edu/faculty/kleeman/amd64/inkscape_0.44-1_amd64.deb](http://www.math.nyu.edu/faculty/kleeman/amd64/inkscape_0.44-1_amd64.deb)

---

