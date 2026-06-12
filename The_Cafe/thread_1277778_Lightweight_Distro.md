---
title: "Lightweight Distro"
date: 2009-09-28
forum: The Cafe
---

### Post by Grifulkin on 2009-09-28
So I used the Minimal Install image and made myself a *buntu of some sorts.  I have lxde for the DE, and I have Wicd for Network Access, and I have Midori for a web browser.  I am also using a server kernel with only the necessary modules.

Also 
```
ryan@Laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.4G  1.1G  6.3G  16% /
tmpfs                 485M     0  485M   0% /lib/init/rw
varrun                485M   72K  485M   1% /var/run
varlock               485M     0  485M   0% /var/lock
udev                  485M  148K  485M   1% /dev
tmpfs                 485M     0  485M   0% /dev/shm
/dev/sda1              89M  9.0M   77M  11% /boot
/dev/sda4              11G  5.0M   11G   1% /home

```

```
ryan@Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           969        286        683          0          0        153
-/+ buffers/cache:        131        837
Swap:          525          0        525

```

so basically is anyone else running a system using less that 286 mb of RAM and is there anyone that has made a distro using the Minimal Install with a DE that uses less than 1.1 GB of space?

I am really just curious I feel accomplished that I have made a full system on such small resources.

---

### Post by earthpigg on 2009-09-28
it is indeed rewarding.

i maintain a very similar project :D

how come your RAM usage is so high? you must have web browser and other programs open, yes?

---

### Post by xuCGC002 on 2009-09-28
> **Grifulkin said:**
> 
so basically is anyone else running a system using less that 286 mb of RAM and is there anyone that has made a distro using the Minimal Install with a DE that uses less than 1.1 GB of space?

My minimal Debian setup (with IceWM) uses about 16mb idle. I have 2GB of RAM, though. All the rest of that is used by whatever program I may be running.

As far as HDD space goes, It uses <1.1GB, leaving about >78.9GB space for whatever I want to install.

---

### Post by oboedad55 on 2009-09-28
> **earthpigg said:**
> it is indeed rewarding.

i maintain a very similar project :D

how come your RAM usage is so high? you must have web browser and other programs open, yes?

I'd definitely take a look at Masonux as well as Crunchbang.

---

### Post by Grifulkin on 2009-09-28
> **earthpigg said:**
> it is indeed rewarding.

i maintain a very similar project :D

how come your RAM usage is so high? you must have web browser and other programs open, yes?

Yes I had Madori running, and a terminal up I believe.

---

### Post by Raffles10 on 2009-09-28
[#!Crunchbang]("http://crunchbanglinux.org/") Lite loads up using just 160 Mb RAM. Crunchbang is just about the best *buntu you can get.

---

### Post by snowpine on 2009-09-28
RAM usage depends on your hardware. You can say "Distro X only uses 100mb!" but the same distro might use more on my computer if I have more RAM. 

On my lowest-ram box (128mb) I use SliTaz. It uses about 30mb of ram (for me).

---

### Post by earthpigg on 2009-09-28
> **snowpine said:**
> RAM usage depends on your hardware. You can say "Distro X only uses 100mb!" but the same distro might use more on my computer if I have more RAM. 

On my lowest-ram box (128mb) I use SliTaz. It uses about 30mb of ram (for me).

i dont know... i have seen various Ubuntu-derivatives use about the same between my netbook, laptop, and in VBox with 1gb, 4gb, and 512mb respectively. there is certainly a variance, but i've never seen it be more than +/- 20% or so.

incidentally, Masonux uses 60-65 at boot, so SliTaz has my project beat in that category :popcorn:

> #!Crunchbang Lite loads up using just 160 Mb RAM. Crunchbang is just about the best *buntu you can get.

+1 for Crunchbang ***Lite*** as a great distribution.

---

### Post by jaxxstorm on 2009-09-29
I maintain a distribution thaty pretty much includes the things you've just described.

Wicd for networking, IceWM for window manager, Midori as its default web browser.

Its called Spri. You can take a look at it here - [http://www.sprilinux.com](http://www.sprilinux.com)

Its lighter than Crunchbang, (I'll hopefully have some stats to back this up soon enough) and uses about 40 - 50mb of RAM from idle on the Live CD.

---

### Post by ~sHyLoCk~ on 2009-09-29
The best way to build your ultimate minimal system is through arch or gentoo.

---

### Post by tcoffeep on 2009-09-29
@~sHyLoCk~:
True that. However, my system occasionally begins to get weighed down by the building process. Like, at the moment, my /usr/portage file is 2.2gb large, and the /usr/src is 570mb. And since I'm using 64 bit, my libs are rather heavy too : /usr/lib64 is 625mb compared to /usr/lib32's 115mb.

Aside from those files, my system is rather lightweight. (mind you, i'm not mentioning ccache in /var)

> 
/dev/root             4.9G  741M  3.9G  16% /
/dev/sda7              15G  286M   14G   3% /home
/dev/sda8             9.7G  1.6G  7.7G  17% /var
/dev/sda9             3.9G   72M  3.6G   2% /tmp
/dev/sda11             49G  4.2G   42G  10% /usr


Thing is, I have a very minimal system with only the necessities installed. I did not install anything that wouldn't be used constantly, and the USE flags were set up so I don't install with anything I wouldn't need (in general).

---

### Post by mmix on 2009-09-29
slitaz or cross-lfs remastered over it.

---

### Post by Mulenmar on 2009-09-29
> **~sHyLoCk~ said:**
> The best way to build your ultimate minimal system is through arch or gentoo.

What was that post that said that as the length of a Ubuntuforum thread increased, the probability of Arch being mentioned approaches one? :P

Anyhow, between those two, I'd say Arch -- all the flexibility of Gentoo IF you want to use it, but in byte-sized pieces. :lolflag:

Or you can pull a K. Mandla and try Crux! :)

---

### Post by sertse on 2009-09-29
See my nick ;) Too quick, too quick for an Arch-godwin though :P

I'll just say distro design (and choices) is only one factor that includes machine specs and deciding what apps to use. Personally my choices in the latter have gotten to extent that changing distros were likely to be minimal and won't be worth it. 

For the record: Debian Xfce/Fluxbox hybrid (no session manager, fluxbox replaces xfce panel and xfwm), built from a minimal install, I get 36 ram on boot up. Atm I have midori, emesene and xchat on, and it's steady at 142/512 ram.

---

### Post by ~sHyLoCk~ on 2009-09-29
> **Mulenmar said:**
> What was that post that said that as the length of a Ubuntuforum thread increased, the probability of Arch being mentioned approaches one? :P


OHNOEZ I has been branded as one of them :( lol no, infact I was one of "those" who disliked that practice of feeding arch to ubuntu people in their own forum. :D I was just giving my opinion, and hey I mentioned **gentoo** as well, and you seem to have carefully ignored it? :P

tcoffeep

Hmm I know what you mean, thats why I always backup my cache files elsewhere. However, during recompile I have to copy them back. Gentoo is a pain seriously. Btw, I'm trying out the new Gentoo 10.0 LiveDVD. Really excited about this release. [2 years is a long time.]

---

### Post by Grifulkin on 2009-09-29
Well thanks for all the responses and I know there are ubuntu based distro's that are minimal like crunchbang but I just wanted to see how small I could get it and how little RAM I could use.  The point wasn't to download a distro and install it for me, I was trying to do it myself.  But I do believe Arch is the best for a minimal install just my opinion.

---

### Post by Grifulkin on 2009-09-29
Also can anyone point me in the direction of how to get my sound to work on said minimal install, since last night I removed lxde and now have openbox and I don't know how to get the sound to work.

---

### Post by NormanFLinux on 2009-09-29
I think LXDE is a good compromise between minimalism and a full OS. I like a real desktop. For others, YMMV.

---

### Post by earthpigg on 2009-09-29
> **Grifulkin said:**
> Also can anyone point me in the direction of how to get my sound to work on said minimal install, since last night I removed lxde and now have openbox and I don't know how to get the sound to work.

have you tried alsamixer?

```
alsamixer
```

---

### Post by kk0sse54 on 2009-09-29
> The best way to build your ultimate minimal system is through arch or gentoo. 

Totally untrue. Most distros come with some sort of minimal install cd or netinstall that can be used to build an excellent base for a minimal system. While it's true that certain distros allow greater configuration work better with older hardware, and are generally regarded as being faster, in most cases the best minimal system is the one that you are most comfortable with and that's coming from a Gentoo user ;)

> **NormanFLinux said:**
> I think LXDE is a good compromise between minimalism and a full OS. I like a real desktop. For others, YMMV.

If you don't want to go the route of dwm and tiling WMs, Lxde is definitely great for a minimal setup. My older computer with 256 MB Ram idles at about 44 MB Ram running standard Debian Lxde. If only I could put Crux or NetBSD on it... :twisted:

---

### Post by Stan_1936 on 2009-09-29
> **Grifulkin said:**
> ..is anyone else running a system using less that **286 mb of RAM** ...

**That's insanely high!!!**

For me:

Ubuntu - 159 MB RAM
Xubuntu - 135 MB RAM
Crunchbang - 64 MB RAM
**[COLOR="DarkRed"]Linux Mint[/COLOR]** - >200 MB RAM(**[COLOR="DarkRed"]YUCK![/COLOR]**)
Crunchbang LITE - 55 MB RAM

All these numbers are IMMEDIATELY AFTER first boot following installation to the hard drive(7200 RPM WD Caviar 8MB Cache) of a system with 2.00 GB RAM BUT a 1.00 GHZ AMD K-7 CPU.

EDIT:  Snowpine is correct about different systems responding differently to the SAME distribution!

---

### Post by ve4cib on 2009-09-29
> **Grifulkin said:**
> So I used the Minimal Install image and made myself a *buntu of some sorts.  I have lxde for the DE, and I have Wicd for Network Access, and I have Midori for a web browser.  I am also using a server kernel with only the necessary modules.

...

so basically is anyone else running a system using less that 286 mb of RAM and is there anyone that has made a distro using the Minimal Install with a DE that uses less than 1.1 GB of space?

I am really just curious I feel accomplished that I have made a full system on such small resources.

I did a similar thing a while back; I installed Ubuntu (command-line) onto a 2GB thumbdrive and then started adding extras on top of that.  I splurged with some of the applications and extras I installed.  Off the top of my head I've got...

- Fluxbox
- PCManFM
- Firefox (with some plugins, including Flash)
- VLC (with Qt dependencies)
- Audacious
- AbiWord
- Gnumeric
- Brasero
- Filezilla
- Gparted
- Pidgin
- Conky
- Eog (though I think I'll replace that with gThumb someday)
- Wicd
- Geany
- Synaptic
- Aterm

Originally I had it down to about 1.1-1.2 GB, but I decided that I just wanted a few more of the heavier apps I'm used to, which brought it up to closer to 1.4GB.  And as long as it fit on a 2GB stick with some room to spare I was happy.  It runs just fine on my old laptop with 512MB of memory (I'd be worried if it didn't).

It is fun to build your entire system from a bare minimum.  Well, fun for some of us anyway.

---

### Post by Mulenmar on 2009-09-29
> **~sHyLoCk~ said:**
> OHNOEZ I has been branded as one of them :( lol no, infact I was one of "those" who disliked that practice of feeding arch to ubuntu people in their own forum. :D I was just giving my opinion, and hey I mentioned **gentoo** as well, and you seem to have carefully ignored it? :P

:-# Whoa, wasn't saying that of you, I thought it was a funny quote. And after that, I said that I preferred Arch, and that I liked how you can have Gentoo-like flexibility if you want it. I like the best of both packaging and compiling, plus excellent documentation. It's the best of both worlds, in my opinion.  

Whatd'ya mean, I'm advertising Arch? I don't know whatcha mean. :-\" O:) Seriously though, trying to put Ubuntu on my Poulsdo-chipset netbook, so I'm finding Ubuntu to be a better deal atm. Can't wait for the Karmic Koala release, it sounds like it'll be terrific. :popcorn:

---

### Post by stanca on 2009-10-04
I experienced with E17 and Fluxbox only 60-90mbs ram minimum.

---

### Post by NormanFLinux on 2009-10-04
Lubuntu - still no beta download.

---

### Post by SomeGuyDude on 2009-10-04
> **earthpigg said:**
> how come your RAM usage is so high? you must have web browser and other programs open, yes?

Integrated video card, perhaps?

---

### Post by Glucklich on 2009-10-04
I've been on the same quest as the OP. I've recently dug up my Pentium MMX to execute this experiment. Being the main objective to figure out the right combination to maximize the performance on more recent productivity machines, especially my laptop. And since it is a productivity machine, can't use it to make these experiments.

My question is, why did so many people advised Crunchbag (which uses OpenBox) instead of DSL, for example (which uses Fluxbox)? Is OpenBox lighter than Fluxbox? Or it has nothing to do with lightness and more with security or any other reason? It's something I always intended to ask and this seems the perfect topic for it. Thanks in advance.

Though, Crunchbag does look kickass on the screenshots.

---

### Post by Warpnow on 2009-10-04
> **NormanFLinux said:**
> Lubuntu - still no beta download.

There is a beta download. There was a post about it recently.

---

### Post by snowpine on 2009-10-04
> **Glucklich said:**
> I've been on the same quest as the OP. I've recently dug up my Pentium MMX to execute this experiment. Being the main objective to figure out the right combination to maximize the performance on more recent productivity machines, especially my laptop. And since it is a productivity machine, can't use it to make these experiments.

My question is, why did so many people advised Crunchbag (which uses OpenBox) instead of DSL, for example (which uses Fluxbox)? Is OpenBox lighter than Fluxbox? Or it has nothing to do with lightness and more with security or any other reason? It's something I always intended to ask and this seems the perfect topic for it. Thanks in advance.

Though, Crunchbag does look kickass on the screenshots.

Actually try DSL and you won't have to ask that question. :) It uses an extremely outdated 2.4 kernel, Firefox 1.0, etc... Crunchbang on the other hand uses the same up-to-date repository as Ubuntu 9.04. Of course, DSL is much lighter, so it will run on really, really hardware that has no chance of running an Ubuntu derivative like Crunchbang.

Your assumption is flawed anyways... a distribution that's optimized for ancient hardware is not necessarily the best choice for newer hardware.

---

### Post by Glucklich on 2009-10-04
> **snowpine said:**
> Actually try DSL and you won't have to ask that question. :) It uses an extremely outdated 2.4 kernel, Firefox 1.0, etc... Crunchbang on the other hand uses the same up-to-date repository as Ubuntu 9.04. Of course, DSL is much lighter, so it will run on really, really hardware that has no chance of running an Ubuntu derivative like Crunchbang.

Your assumption is flawed anyways... a distribution that's optimized for ancient hardware is not necessarily the best choice for newer hardware.

True. I realized that after posting. I should've given Fluxbuntu or Mint 6 Fluxbox CE as an example. Though, you did not answered my question ;)
Which basically intended to be, under the same circumstances, which one is lighter? Fluxbox or Openbox?

---

### Post by snowpine on 2009-10-04
> **Glucklich said:**
> True. I realized that after posting. I should've given Fluxbuntu or Mint 6 Fluxbox CE as an example. Though, you did not answered my question ;)
Which basically was, under the same circumstances, which one is lighter? Fluxbox or Openbox?

I can't tell a difference in performance between Openbox and Fluxbox (having used both Crunchbang and Fluxbuntu extensively). Both are so fast as to be nearly instantaneous and use a tiny amount of ram. I would say the difference pales in comparison to which applications you choose. :)

(edit) According to this unscientific thread I just read, the two are less than 2mb difference in terms of ram used: [http://ubuntuforums.org/showthread.php?p=8051807](http://ubuntuforums.org/showthread.php?p=8051807)

---

### Post by fela on 2009-10-04
```
[fela@dogeatdog:~]$ free -m                                             (10-04 21:14)
             total       used       free     shared    buffers     cached
Mem:          3967       3862        105          0         20       2530
-/+ buffers/cache:       1311       2656
Swap:         4730         15       4714
```

I am using 3.9 of 4GB RAM. That sucks.

Although I do have open:
Amarok 2.1 with a large (4200 songs) collection;
Three Konqueror windows open with 14 web pages between them;
A konsole window running zsh with *lots* of customizations;
Dolphin file manager with a folder loaded with previews of 21 1080p HD wallpapers;
Kmail with two accounts, 7664 messages between them
Kopete instant messenger with 4 IM accounts online;
Korganizer;
Running on KDE 4.3 which takes up alot of memory by itself

Also, unused memory is wasted memory and I get decent performance with things like the GIMP and hires images.

---

### Post by Glucklich on 2009-10-04
> **snowpine said:**
> I can't tell a difference in performance between Openbox and Fluxbox (having used both Crunchbang and Fluxbuntu extensively). Both are so fast as to be nearly instantaneous and use a tiny amount of ram. I would say the difference pales in comparison to which applications you choose. :)

Thank you very much ;)

---

### Post by snowpine on 2009-10-04
To put it in perspective, on my system at the moment, Firefox is using 225mb.... the windows manager is a drop in the bucket. :)

---

### Post by NormanFLinux on 2009-10-04
That was the alpha. I checked and its still b23. Lubuntu hasn't been updated since September.

---

### Post by earthpigg on 2009-10-05
> **fela said:**
> ```
[fela@dogeatdog:~]$ free -m                                             (10-04 21:14)
             total       used       free     shared    buffers     cached
Mem:          3967       3862        105          0         20       2530
-/+ buffers/cache:       1311       2656
Swap:         4730         15       4714
```

I am using 3.9 of 4GB RAM. That sucks.


it looks to me like you are using 1.3 of 4 gb of RAM... that 3862 includes cache, and it is good that so much of it is in use. it should always be like that.

---

### Post by fela on 2009-10-05
> **earthpigg said:**
> it looks to me like you are using 1.3 of 4 gb of RAM... that 3862 includes cache, and it is good that so much of it is in use. it should always be like that.

Oh yeah, I didn't look at the 'cached' bit, d'oh!

I might reduce my swappiness to 0 - it's not like I need a swap with 4GB RAM. The only reason I keep it is so I can suspend to disk. My next project will be making a swap file that is only as big as it needs to be - ie dynamic in size...sounds cool doesn't it?

---

### Post by oboedad55 on 2009-10-05
Here's a link to a Lubuntu beta. I don't guarantee how recent it is. 
[http://blog.lxde.org/?p=514](http://blog.lxde.org/?p=514)

---

### Post by ve4cib on 2009-10-05
It's interesting that in all the back-and-forth over which WM is lighter no one's mentioned JWM yet.  It's smaller than Fluxbox and (arguably) easier to use, since it has the ability to *gasp* put buttons and menus on the panel!

It doesn't look nearly as nice as Fluxbox, and it doesn't handle arbitrary key-bindings as well (it can clobber other applications' quick-keys if you're not careful), but if all you care about is the footprint it's a good option.

And for those who've never even heard of JWM before I offer a quick screenshot:

[img]http://www.mts.net/~ibis/ve4cib/img/screenshots/cvjwm-1.1.0.jpg[/img]

---

### Post by oboedad55 on 2009-10-05
> **ve4cib said:**
> It's interesting that in all the back-and-forth over which WM is lighter no one's mentioned JWM yet.  It's smaller than Fluxbox and (arguably) easier to use, since it has the ability to *gasp* put buttons and menus on the panel!

It doesn't look nearly as nice as Fluxbox, and it doesn't handle arbitrary key-bindings as well (it can clobber other applications' quick-keys if you're not careful), but if all you care about is the footprint it's a good option.

And for those who've never even heard of JWM before I offer a quick screenshot:

[img]http://www.mts.net/~ibis/ve4cib/img/screenshots/cvjwm-1.1.0.jpg[/img]

This looks very interesting. How did you go about getting it to run on your system? I looked at the web page but it wasn't enough information for me to proceed.

---

### Post by earthpigg on 2009-10-05
> **oboedad55 said:**
> This looks very interesting. How did you go about getting it to run on your system? I looked at the web page but it wasn't enough information for me to proceed.

look for jwm in synaptic :D

if you find and install it, log out and at the login screen look for sessions -> jwm... or something similar.

---

### Post by ve4cib on 2009-10-05
> **oboedad55 said:**
> This looks very interesting. How did you go about getting it to run on your system? I looked at the web page but it wasn't enough information for me to proceed.

Two options for JWM.  First off there's the classic
```

$ sudo apt-get install jwm

```

That should install it and add it to your list of default sessions.  Log out, and when GDM/KDM asks you to log back in select "JWM" from the list of available options.

If for some reason JWM did not get added to your sessions you can add it by creating

**/usr/share/xsessions/jwm.desktop**
```

[Desktop Entry]
Encoding=UTF-8
Name=JWM
Comment=Joe's Window Manager
Exec=/usr/local/bin/jwm
Type=Application

```

Alternatively, if you're feeling courageous, you can try my own slightly-hacked version of JWM, dummed "CvJWM" (for "Chris' version of Joe's Window Manager").  It's basically exactly the same as JWM, but with a shade button on the window border, and support for a few extra icon formats (notably PPM and PGM, with SVG support nominally in-progress -- though truthfully I haven't looked at it in months), and I eliminated the case-sensitivity for the config file (it's a manually-edited XML file -- forcing case-sensitivity seemed like a stupid idea to me, even though it's not *proper* XML).

CvJWM can be downloaded here:

[http://www.mts.net/~ibis/ve4cib/cvjwm.html](http://www.mts.net/~ibis/ve4cib/cvjwm.html)

Installation instructions are included.  It's the usual

```

$ ./autogen.sh
$ ./configure
$ make
$ sudo make install

```

(Personally though I prefer "sudo checkinstall" for the last step -- it'll compile a .deb package and install that for you, making it easier to get rid of if you don't want it anymore).

JWM replaced Fluxbox as the default WM in DSL several months (year?) ago.  It's markedly smaller, both in terms of storage and in terms of memory footprint.  I'd definitely suggest checking it out if you're into that sort of thing.

_______
One word of warning: the default configuration file for CvJWM has all sorts of launchers and start-up apps that you may not have installed.  It is **strongly-recommended** to copy it to $HOME/.cvjwm and edit it to suit your needs.  Everything is in one XML file, and it's pretty intuitive what changes what.  If you run into problems check out the man page and/or [the official JWM configuration documentation](http://joewing.net/programs/jwm/config.shtml)


EDIT: Damn! Ninja'd!

---

### Post by Stan_1936 on 2009-10-05
> **ve4cib said:**
> It's interesting that in all the back-and-forth over which WM is lighter no one's mentioned JWM yet.  It's smaller than Fluxbox...if all you care about is the footprint it's a good option.

And for those who've never even heard of JWM before I offer a quick screenshot:

[img]http://www.mts.net/~ibis/ve4cib/img/screenshots/cvjwm-1.1.0.jpg[/img]

I looks as though you'ev got a dual core system.  Why are you running JWM when your hardware could support something MUCH MUCH heavier?

---

### Post by earthpigg on 2009-10-05
> **Stan_1936 said:**
> I looks as though you'ev got a dual core system.  Why are you running JWM when your hardware could support something MUCH MUCH heavier?

i run LXDE and i have a quad core intel i7 with 6gb of RAM.

something that often comes with 'lightweight' and/or 'minimalist' is 'easy for earthpigg to understand'.

which i like.

---

### Post by Grifulkin on 2009-10-06
JWM seems like a very nice Window Manager I will have to try it out, and thank you everyone for the input on how to make things lighter.  I really want to take that older laptop and give it some zing make it fly can anyone recommend a good lightweight web browser that won't crash everytime I try to use flash.  Midori did that and I hated it, rather than try to figure out why, I didn't really like the interface for Midori so I went with Chromium which doesn't crash but is there anything more lightweight than that?

Also since the last time I posted I removed anything on there that had something to do with a GUI excpet of course X itself.  Right now it is only taking up 890 mb on disk and I use a very very small amount of RAM I can't remember exactly.  So I am going to try JWM and see if that keeps the RAM low nothing else I have used has really kept it Low.

---

### Post by SomeGuyDude on 2009-10-06
> **earthpigg said:**
> i run LXDE and i have a quad core intel i7 with 6gb of RAM.

something that often comes with 'lightweight' and/or 'minimalist' is 'easy for earthpigg to understand'.

which i like.

Well there are two kinds of minimalistic systems: minimalist in features and minimalist in footprint. I like the former, don't really care about the latter. Though they do often coincide. :)

And one of the nice things about having a big honkin' proc with RAM to spare is you can just look for the FASTEST setup, which may not necessarily be the smallest either.

---

### Post by ve4cib on 2009-10-06
> **Stan_1936 said:**
> I looks as though you've got a dual core system.  Why are you running JWM when your hardware could support something MUCH MUCH heavier?

Normally I run Gnome (or Fluxbox if I'm in the mood) on that machine.  But I was doing my CvJWM development on it, and needed to test things out.  And since they worked I figured then was as good a time as any to put together a screenshot to show off the basic look and feel.  You'll notice there are also a few launchers for traditionally "heavy" applications, like Amarok and Firefox.

There's also just something nice about using something tiny and minimalistic.  I mean, what does Gnome really do that something like JWM, LXDE, or Fluxbox can't?  They all draw windows with pretty borders around them (some prettier than others, granted), they give you the ability to manage your windows, move them around, maximize them, close them, etc...  Some let you have icons on your desktop, others don't.

If you're on a laptop using something uber-tiny like JWM might be able to squeeze some extra juice out of the battery for you.  (I say "might" because I've honestly never done a thorough comparison and thus can't say for certain).

And if you're using a lot of memory-happy applications (say Rhythmbox or Amarok open with libraries that can last 2+ weeks if played continuously, editing massive photos in GIMP -- or better yet with Blender, and using Firefox with a crap-tonne of plugins and a dozen tabs) why bother wasting RAM on a heavier WM?  Some would argue it's better to use that memory and processing power for your applications and keep the WM as small and light as possible.

Ultimately it's personal preference.  I like Gnome, and I'm not about to change from it full-time (unless I decide I hate what they do with Gnome3, at which point I'll either go to KDE or go back to Fluxbox full-time).

---

