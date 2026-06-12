---
title: "Breezy Backport, When"
date: 2005-10-13
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-10-13
Hi, everyone

Do you know when will be the official :KS [SIZE="5"][FONT="Comic Sans MS"][COLOR="DarkOrange"]breezy backport[/COLOR][/FONT][/SIZE]:KS  available? Thanks a lot!

---

### Post by strikeforce on 2005-10-13
When the version after breezy is starting to get put together.

---

### Post by tzutolin on 2005-10-13
I've herad it will be ready a week after breezy is released, is it true? :KS

---

### Post by poofyhairguy on 2005-10-13
[QUOTE=tzutolin]Hi, everyone

Do you know when will be the official :KS [SIZE="5"][FONT="Comic Sans MS"][COLOR="DarkOrange"]breezy backport[/COLOR][/FONT][/SIZE]:KS  available? Thanks a lot![/QUOTE]


When the servers for development Dapper open.

---

### Post by tzutolin on 2005-10-13
[QUOTE=poofyhairguy]When the servers for development Dapper open.[/QUOTE]
All right. Thanks :-)

It seems development Dapper forum has been opened, will the backport be available too? :KS

---

### Post by Nomearod on 2005-10-13
I installed Ubuntu 5.10 today ( 2 hours ago ), and I would like to use backports. What do I need to do? In the other version, I just added mirrormax and other mirrors, but it looks like they don't work with 5.10...

---

### Post by Seth on 2005-10-13
There are no backports in Breezy since everything is by definition up-to-date. Once Dapper gets underway backports will reopen.

---

### Post by tzutolin on 2005-10-14
Thanks :KS 
So what should we do if we want to install w32codecs, flashplugin, acroread, java, and azureus?

---

### Post by Nomearod on 2005-10-14
[QUOTE=tzutolin]Thanks :KS 
So what should we do if we want to install w32codecs, flashplugin, acroread, java, and azureus?[/QUOTE]


That's what I would like to know... without backports, this programs don't appear in Synaptic.:(

---

### Post by feloc on 2005-10-14
This is something that I'm wondering about too.... :???:

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=tzutolin]Thanks :KS 
So what should we do if we want to install w32codecs, flashplugin, acroread, java, and azureus?[/QUOTE]

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by John.Michael.Kane on 2005-10-14
look here [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs#head-ae79fed9d60ccdf06f400ae76ad53867d94bb2b8)

it's tried and tested..

Edit: poofyhairguy beat me to it

---

### Post by sander marechal on 2005-10-14
That doesn't work anymore. For the codecs you need

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

and that's not available anymore (apt-get update halts with an error claiming not to find it). What now?

---

### Post by TheRay1987 on 2005-10-14
So what are these for?
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

---

### Post by Nomearod on 2005-10-14
[QUOTE=sander marechal]That doesn't work anymore. For the codecs you need

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

and that's not available anymore (apt-get update halts with an error claiming not to find it). What now?[/QUOTE]

I used that to install W32Codecs, and it worked. 

To install Adobe, you can use Synaptic with the default sources, I think...

What I would like to know, is how can I install Azureus.... : /

---

### Post by xalphas on 2005-10-15
> What I would like to know, is how can I install Azureus.... : /

I've installed Azureus this way:

```
wget http://ovh.dl.sourceforge.net/sourceforge/azureus/Azureus_2.3.0.4_linux.GTK.tar.bz2
```
```

sudo tar jxvf Azureus_2.3.0.4_linux.GTK.tar.bz2 -C /opt/
```
```
sudo chown -R root:root /opt/azureus/
```
```
sudo gedit /usr/share/applications/Azureus.desktop
```

Paste this 

>           [Desktop Entry]
          Name=Azureus
          Comment=Azureus
          Exec=/opt/azureus/azureus
          Icon=/opt/azureus/Azureus.png
          Terminal=false
          Type=Application
          Categories=Application;Network;



And you have to see it in Applications-Internet

Hope this helps you.

thx

---

### Post by NeoChaosX on 2005-10-15
[QUOTE=TheRay1987]So what are these for?
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted[/QUOTE]
Those lines are there for when Breezy Backports *is* finally open. So just wait until development on Dapper starts.

---

### Post by sparhawk on 2005-10-16
[QUOTE=tzutolin]Thanks :KS 
So what should we do if we want to install w32codecs, flashplugin, acroread, java, and azureus?[/QUOTE]


I don't know how many times I have seen people asking about w32codecs. They won't be in backports or extra's or anything because they are not free open source codecs. The companies that own the rights to them want money for them which means either you pay ubuntu for them... or they pay for them and accept the loss or they get shut down due to law suites. The ubuntu team have decided to remove them which I think is the right move because there are plenty of open source alternatives out there. If you want a free operating system you can't use software that the authors want money for... its that simple. Check out:

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)
and
[https://wiki.ubuntu.com/FreeFormats](https://wiki.ubuntu.com/FreeFormats)

That should give you a better idea of whats going on.

---

### Post by sparhawk on 2005-10-16
[QUOTE=sparhawk]
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)
and
[https://wiki.ubuntu.com/FreeFormats](https://wiki.ubuntu.com/FreeFormats)

That should give you a better idea of whats going on.[/QUOTE]


Sorry that should be:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
and 
[https://wiki.ubuntu.com/FreeFormats](https://wiki.ubuntu.com/FreeFormats)

---

### Post by fragmental on 2005-10-16
[QUOTE=sparhawk]I don't know how many times I have seen people asking about w32codecs. They won't be in backports or extra's or anything because they are not free open source codecs. The companies that own the rights to them want money for them which means either you pay ubuntu for them... or they pay for them and accept the loss or they get shut down due to law suites. The ubuntu team have decided to remove them which I think is the right move because there are plenty of open source alternatives out there. If you want a free operating system you can't use software that the authors want money for... its that simple. Check out:

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)
and
[https://wiki.ubuntu.com/FreeFormats](https://wiki.ubuntu.com/FreeFormats)

That should give you a better idea of whats going on.[/QUOTE]

Yes, it's too bad that so many websites use non-free non-open codecs.  There isn't much that anyone can do about it though.  I guess, we could all send e-mails to those websites and complain.  Something like "Theora would be nice, but at least support Realplayer!"  At least the bbc is pretty[ cool.]("http://www.bbc.co.uk/opensource/")

---

### Post by LongTooth on 2005-10-16
With a new PC and a fresh install of Breezy I too would like to work on multimedia and all the plugins needed. I stay away from tarballs as much as I can. So what the next step? 

On another machine I took the drastisc step of adding the Hoary back ports and following the steps for multimedia. For the most part I'm satified with the results but...(you know this was coming, didn't you?) I can't play mpeg embeded video of Firefox. Oddly I have no problems with Epiphany. 

With a clean slate - fresh install on a new PC - I'd like to enable multimedia, flash, java, etc the proper, Debian way. Namely apt-get install etc... I'll keep an eye on this thread. 

Hopefully a 5.10 Starter Guide is in the works.

---

### Post by alastair lewis on 2005-10-17
On the same theme.
I got liblame0 and gstreamer-0.8-lame from the Hoary backport.

Where do I go now?

By the way, Breezy is otherwise excellent.

---

### Post by tzutolin on 2005-10-17
According to the development forum, it seems the Dapper Drake repository will be open later today.

Will the **Breezy Backport** be opened at the same time? :KS

---

### Post by moepud on 2005-10-18
While I've been using Debian for a while, and thus familiar with the apt system, I've just recently started trying ubuntu to see what all the fuss is about. Now, I might be wrong about this, but aren't the "backports" repos just future, "experimental" versions of software already found in the "official" or "regular" repos? This would be analogous to the "stable" and "unstable" apt repos in Debian. I'm fairly certain that you can just append "universe" and "multiverse" to your existing, working lines in your apt sources list.

it might look something like this:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) breezy universe multiverse

To my understanding, and if ubuntu repos work anything like standard apt repos, this should give you access to everything that was available in the old backports, which is now simply a part of the current "breezy" disto.

If I totally got this wrong feel free to ignore me.

---

### Post by geearf on 2005-10-18
No you are right, backport is a bit like sid, it's bleeding edge stuff, but when breezy just got out, there is no newer ubuntu package anywhere so no backport ...

---

### Post by PuleX on 2005-10-18
[QUOTE=moepud]While I've been using Debian for a while, and thus familiar with the apt system, I've just recently started trying ubuntu to see what all the fuss is about. Now, I might be wrong about this, but aren't the "backports" repos just future, "experimental" versions of software already found in the "official" or "regular" repos? This would be analogous to the "stable" and "unstable" apt repos in Debian. I'm fairly certain that you can just append "universe" and "multiverse" to your existing, working lines in your apt sources list.

it might look something like this:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) breezy universe multiverse

To my understanding, and if ubuntu repos work anything like standard apt repos, this should give you access to everything that was available in the old backports, which is now simply a part of the current "breezy" disto.

If I totally got this wrong feel free to ignore me.[/QUOTE] 

Well, you are close, but not quite right. Using the debian example: 
1. Debian has backports, too: [http://backports.org/](http://backports.org/) 
2. The difference between unstable/testing and backports is that a backport is specifically made to run on a stable environment. That way, if you want the latest and greatest of *name great and up-to-date* package, that is only available in unstable with all kinds of unstable dependencies, you don't need to install all kinds of unstable libs or other dependencies too _if_ you use the backport.

---

### Post by ions on 2005-10-20
So are the Breezy Backports a go yet?  OOo2 final is finally final.

---

### Post by vaskark on 2005-10-20
And when they are finally open can someone post all the official breezy repos that are available. I want them all.

---

### Post by BoyOfDestiny on 2005-10-21
Actually I'm more interested in breezy-extras. I feel more comfortable keeping the "base" install official, and adding programs not included.

If there is anyway I can help you guys with a few...

Here are some I've built from source with checkinstall

[http://www.safaribans.com/gpl/](http://www.safaribans.com/gpl/)

All gpl, and no, not restricted format stuff...(and yes I included the tars with the original sources!)

---

### Post by Heretic09 on 2005-10-21
You could always use:
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all

w32 codecs and freenx are available there as well as some other stuff, package listing is here:

[http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/)

---

### Post by XDevHald on 2005-10-21
**EDIT:** ok fixed, didn't see the front page for the gpg :p 

Type in a terminal (no need for root)

> gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 
 gpg --export --armor 1135D466 | sudo apt-key add -

---

### Post by chetanthaker on 2005-10-21
Ok Steve, 

I'm downloading the tar.gz file from that website you noted ... 13MB

Ok, once I'm done downloading it, how do I install/compile it ??

Please do help me... kinda newbie to Linux

CeeTee

---

### Post by Blue1k on 2005-10-21
Um..the tar.gz package for open office over is 100MB big.
If I have time I will try to make a deb package for you (never made one for OO so we will see:p )

---

### Post by Blue1k on 2005-10-21
Why don't you download the deb file instead.

To install this:

**sudo dpkg -i w32codecs_20050412-0.0_i386.deb**

---

