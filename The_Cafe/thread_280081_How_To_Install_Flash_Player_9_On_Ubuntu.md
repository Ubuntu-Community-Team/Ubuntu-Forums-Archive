---
title: "How To Install Flash Player 9 On Ubuntu"
date: 2006-10-18
forum: The Cafe
---

### Post by kungfuice on 2006-10-18
Well Adobe just released the flash player 9 beta for Linux to the public.  I decided that I would throw together a quick howto on how to install it on Ubuntu.  This howto was written for Edgy, but it should work for Dapper and Breezy as well.

This is my first howto so I appreciate any comments or suggestions.

The howto is posted on my blog

[http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/]("http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/")

Hope this helps everyone out :)

---

### Post by aysiu on 2006-10-18
This is more appropriate in the Cafe.

---

### Post by catlett on 2006-10-18
Thank you kungfuice! I read a piece about an adobe develeoper who got the pre-release flash 9 and he posted screenshots but I didn't know it was this close. Anyways I didn't know until you posted that it was here. 
P.S. Why wasn't it as simple as copying the plugin file to /usr/lib/firefox for flash 7? Who cares now! I'm off to surf! It is great to right click and see "about Flashplayer 9".
Thanks again.

---

### Post by kungfuice on 2006-10-18
I was at least expecting them to have an installer, especially since the file on their site is appropriately named "Download Installer for Linux", but I guess they have omitted all the fancy stuff for the beta.

So far it runs great on my system, I'm very happy to finally have an up to date flash player.

Kudos Adobe, better late then never

---

### Post by randell6564 on 2006-10-18
> **kungfuice said:**
> Well Adobe just released the flash player 9 beta for Linux to the public.  I decided that I would throw together a quick howto on how to install it on Ubuntu.  This howto was written for Edgy, but it should work for Dapper and Breezy as well.

This is my first howto so I appreciate any comments or suggestions.

The howto is posted on my blog

[http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/]("http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/")

Hope this helps everyone out :)
Did'nt work for me [here]("http://www.tbolin.com/audiovideo/index.html"). I'll keep trying though thanks!

---

### Post by kungfuice on 2006-10-19
> **randell6564 said:**
> Did'nt work for me [here]("http://www.tbolin.com/audiovideo/index.html"). I'll keep trying though thanks!

Hmm what happens when you goto that site, I loaded it fine here

When you installed the plugin did you make sure to close down any firefox/mozilla browsers, you might want to do:
```
ps -ale
```
Check and see if there are any lingering firefox/mozilla processes running

---

### Post by randell6564 on 2006-10-19
> **kungfuice said:**
> Hmm what happens when you goto that site, I loaded it fine here

When you installed the plugin did you make sure to close down any firefox/mozilla browsers, you might want to do:
```
ps -ale
```
Check and see if there are any lingering firefox/mozilla processes running
I closed firefox. I copied and pasted your instructions to my desktop before attempting to install.

---

### Post by randell6564 on 2006-10-19
Oh and BTW, this is the only reference to firefox when doing a ```
 sudo ps -ale
```
> 0 S  1000 11236     1  5  75   0 - 66302 stext  ?        00:00:08 firefox-bin


Anyway.,gotta get some sleep!  I'll be back tomorrow!  Thanks for the help!!

---

### Post by RAV TUX on 2006-10-19
> **kungfuice said:**
> Well Adobe just released the flash player 9 beta for Linux to the public.  I decided that I would throw together a quick howto on how to install it on Ubuntu.  This howto was written for Edgy, but it should work for Dapper and Breezy as well.

This is my first howto so I appreciate any comments or suggestions.

The howto is posted on my blog

[http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/](http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/)

Hope this helps everyone out :)

Thanks I reposted in the **["Ubuntu enantiomorphs"]("http://cafelinux.org/forums/index.php/board,81.0.html") **forum here :
[http://cafelinux.org/forums/index.php/topic,578.new.html#new](http://cafelinux.org/forums/index.php/topic,578.new.html#new)

---

### Post by NoTiG on 2006-10-19
now what are the chances of getting shockwave?

---

### Post by kungfuice on 2006-10-19
> **yozef said:**
> Thanks I reposted in the **["Ubuntu enantiomorphs"]("http://cafelinux.org/forums/index.php/board,81.0.html") **forum here :
[http://cafelinux.org/forums/index.php/topic,578.new.html#new](http://cafelinux.org/forums/index.php/topic,578.new.html#new)

Thanks :)

---

### Post by kungfuice on 2006-10-19
> **NoTiG said:**
> now what are the chances of getting shockwave?

Let's hope that Adobe keeps up with developing Linux products, so far they have done fairly well

Step by step Linux is becoming more and more of a desktop replacement

---

### Post by Polygon on 2006-10-19
i havent seen a shockwave application in years.....

and even then the only use i had for it was playing games on shockwave.com...

---

### Post by Treviño on 2006-10-19
I've packaged the flashplayer and the flashplugin...
Take them from my repository: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

Bye!

---

### Post by kungfuice on 2006-10-19
> **Treviño said:**
> I've packaged the flashplayer and the flashplugin...
Take them from my repository: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

Bye!

Thanks I updated my blog to point people to your repo, thanks again :)

---

### Post by lanxu on 2006-10-19
This is still just a beta release. You shouldn't install it to */usr/lib/firefox/plugins/* as system-wide. Instead, I would recommend to install it to your *~/.mozilla/plugins/*. This way you don't need any root access and you don't make other users on your system vulnerable (when they get beta flash as a default). It also doesn't overwrite any official stuff that's installed by package manager.

Just my humble opinion. :)

---

### Post by kungfuice on 2006-10-19
> **lanxu said:**
> This is still just a beta release. You shouldn't install it to */usr/lib/firefox/plugins/* as system-wide. Instead, I would recommend to install it to your *~/.mozilla/plugins/*. This way you don't need any root access and you don't make other users on your system vulnerable (when they get beta flash as a default). It also doesn't overwrite any official stuff that's installed by package manager.

Just my humble opinion. :)

I agree, and you could definitely install the plugin into your home directory, however you would still have to remove the nonfreeflash plugin that is installed from Ubuntu, since both flashplayer7 and flashplayer9 cannot co-exist together.

In fact through my testing firefox will always choose to run flashplayer7 in that case.

So if you want to, you can install it in your home directory, but none the less you will still have to remove flashplayer7, so you might as well install the replacement system wide

---

### Post by lanxu on 2006-10-19
> **kungfuice said:**
> I agree, and you could definitely install the plugin into your home directory, however you would still have to remove the nonfreeflash plugin that is installed from Ubuntu, since both flashplayer7 and flashplayer9 cannot co-exist together.

In fact through my testing firefox will always choose to run flashplayer7 in that case.

So if you want to, you can install it in your home directory, but none the less you will still have to remove flashplayer7, so you might as well install the replacement system wide

Weird. On my machine firefox shows flashplayer9 instead of flashplayer7 after adding pluging to my home directory. I still have flashplugin-nonfree package installed. I also tested this: I renamed the plugin from my home directory and after I restarted firefox it showed flashplayer7 again. In my case this definitely works. Did you remember to kill all firefox processes? I'm using Firefox 1.5.

EDIT: However, adding plugin to home directory seems to affect only Firefox. Other browsers like Epiphany and Opera still seek plugin from /usr/lib/firefox/plugins/.

---

### Post by Treviño on 2006-10-19
My package automatically remove any previous version of the plug-in installed in your home-dir ;)

---

### Post by Colonel Kilkenny on 2006-10-19
> **lanxu said:**
> EDIT: However, adding plugin to home directory seems to affect only Firefox. Other browsers like Epiphany and Opera still seek plugin from /usr/lib/firefox/plugins/.
In Opera you can add/remove/edit locations if you want Opera to search plugins from different places.

ctrl+F12 -> Advanced -> Content -> Plug-in options 

I think the defaults are /usr/lib/opera/plugins, /usr/lib/firefox/plugins and ~/.netscape/plugins

---

### Post by NoWhereMan on 2006-10-19
> **kungfuice said:**
> Well Adobe just released the flash player 9 beta for Linux to the public. 

at last!

---

### Post by hinanzo on 2006-10-19
anyone having trouble with flash 9 on ppc. i am running xubuntu ppc and I cant seem to get it installed correctly...it doesn't even see flash 7 i think it sees flash 4...ive been trying every which way cant seem to find an answer...

---

### Post by kungfuice on 2006-10-19
> **hinanzo said:**
> anyone having trouble with flash 9 on ppc. i am running xubuntu ppc and I cant seem to get it installed correctly...it doesn't even see flash 7 i think it sees flash 4...ive been trying every which way cant seem to find an answer...

As far as I know this release is only for x86, still no 64bit runtime and still no ppc

---

### Post by catlett on 2006-10-19
> **hinanzo said:**
> anyone having trouble with flash 9 on ppc. i am running xubuntu ppc and I cant seem to get it installed correctly...it doesn't even see flash 7 i think it sees flash 4...ive been trying every which way cant seem to find an answer...

Are you sure you downloaded the correct version of the flashplayer? There is a flash 9 beta plugin for Mac PPC and Mac intel, as well as a standalone player for Mac.
I do not know about ppc's but as far as ubuntu, all I did was extract the tar and copy the plugin library into /usr/lib/firefox/plugins. That was it. No intstallaion or ./configure-make, just a drag and drop from a root nautilus into /usr/lib/firefox/plugins. How are you trying to install the plugin?

---

### Post by kowsik on 2006-10-22
Thanks a lot! Now I can see flash 9 animation on firefox, but firefox has slowed down a lot (and even crashed twice). Did anyone else notice the same?

---

### Post by Deus42 on 2006-10-23
Worked like a charm for me on 6.06.

---

### Post by a_dumb_fake_name on 2006-11-14
Kungfuice, you RULE! I installed some other version of flash player a half-dozen times, and then gave up a few weeks ago. THANKS! 
Everyone, check this out w/ your flash player: [http://youtube.com/watch?v=NINJQ5LRh-0](http://youtube.com/watch?v=NINJQ5LRh-0)

---

### Post by Ziggurat on 2006-11-14
Hi, ive tried flah 9 this days and works, but it make my browsers terrible slow. Ive tried opera and firefox, and both with multiple tabs and a flash page open slows like hell the browsers.

---

### Post by crwnsop on 2006-11-14
So I'm running the 64-bit 6.06, and followed the instructions from kungfuice.com, but I still have no luck. Any help? I checked the folder and have copies of the libflashplayer.so and flashplayer.xpt in the /usr/lib64/firefox/plugins folder.

---

### Post by kungfuice on 2006-11-15
> **crwnsop said:**
> So I'm running the 64-bit 6.06, and followed the instructions from kungfuice.com, but I still have no luck. Any help? I checked the folder and have copies of the libflashplayer.so and flashplayer.xpt in the /usr/lib64/firefox/plugins folder.

The problem is you can't run a 32-bit flash binary on a 64bit firefox install.

You have to install the 32-bit version of firefox and then install the flashplayer for that instance of firefox.

There have been rumours that Adobe is working on a 64-bit flash pluggin but as of right now I don't know of any floating around

---

### Post by Stew2 on 2006-12-22
> **Treviño said:**
> I've packaged the flashplayer and the flashplugin...
Take them from my repository: [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

Bye!


Thank you! Works great :D .

Regards,
Stew2

---

