---
title: "instability rant"
date: 2006-06-19
forum: The Cafe
---

### Post by lapsey on 2006-06-19
Aaargh! Nvu crashes on inserting characters (unless run as root), firefox crashes randomly on scrolling, inkscape crashes when changing line and fill properties, smbfs still causes gthumb and nautilus to crash when viewing busy locations on a network, and vlc plays through the audio of a dvd image even when killed.

While some of these problems are fixable though a search of the forums and a few commands - I am getting really really frustrated with the instabilities in [COLOR="LemonChiffon"]breezy[/COLOR] dapper. Many of these are long-standing, well documented bugs. Nor have I done anything but install the latest nvidia drivers and kernel bits for amd

i really like these programs but they have been shipped in a shape that does them no justice. :mad:

---

### Post by professor_chaos on 2006-06-19
I can understand your frustration considering those problems. Have you considered upgrading to dapper to see if some of your problems get solved?

---

### Post by nalmeth on 2006-06-19
[B]Ubuntu 6.06 User

[/B]But you're using Breezy?

---

### Post by lapsey on 2006-06-19
just checked
apparently i'm using dapper!

---

### Post by nalmeth on 2006-06-19
Weird, I haven't experienced the problems you're having.

I don't use NVU, but
I find Firefox Stable as ever, 

Xine is a great app I bust out just to play DVD's. Some kind of aesthetic feel I like about watching movies with it.

sudo apt-get install xine-ui

Do you have your video drivers installed?
EDIT: I see you have... heh

You should try kubuntu out. Konqueror rulez

sudo aptitude install kubuntu-desktop

---

### Post by lapsey on 2006-06-19
I wasn't really looking for solutions - just a place to rant - but thanks for the suggestion. 

I realise that Ubuntu can't be 100% Debian Stable quality but some of these (Nvu, Inkscape) are pretty significant problems. And apparently this is not a unique 'YMMV' situation. 
Or is it more beneficial to release a buggy program than to make people wait for one that works?

Also, shouldn't ubuntu have a proper bug reporting mechanism by now? Lord knows I've tried going through bugzilla but that is pain without gain (especially when reporting gnome bugs is concerned)

---

### Post by nalmeth on 2006-06-19
Bad habit of mine I guess. I always find that either in short-term or long-term, there is always at least a patch-type fix to most problems. :)

[https://launchpad.net/](https://launchpad.net/)

---

### Post by lapsey on 2006-06-20
you know i can't help think that many open source devs forget at least one of the 'release early, release frequently, listen to userbase' rules; thereby rendering it useless

---

### Post by tseliot on 2006-06-20
[QUOTE=lapsey]Aaargh! Nvu crashes on inserting characters (unless run as root), firefox crashes randomly on scrolling, inkscape crashes when changing line and fill properties, smbfs still causes gthumb and nautilus to crash when viewing busy locations on a network, and vlc plays through the audio of a dvd image even when killed.

While some of these problems are fixable though a search of the forums and a few commands - I am getting really really frustrated with the instabilities in [COLOR="LemonChiffon"]breezy[/COLOR] dapper. Many of these are long-standing, well documented bugs. Nor have I done anything but install the latest nvidia drivers and kernel bits for amd

i really like these programs but they have been shipped in a shape that does them no justice. :mad:[/QUOTE]
I use the programs you're having problems with but I haven't experienced any of the problems you mentioned.

Are you using Ubuntu 64 bit?

---

### Post by lapsey on 2006-06-20
i'm afraid not. regular amd (k7) single processor

I am glad to hear you have had no such problems, i just hope you are in the majority

---

### Post by Arktis on 2006-06-20
It sounds to me as if you are using an old installation of breezy which has been upgraded to dapper (more or less) and that's where your issues are coming from (the transition didn't go too well).  I'm guessing maybe you've been using apt-get/aptitude dist-upgrade instead of simply apt-get/aptitude upgrade?

If this is in any way the case here, then I recommend that you back up all your important files, grab a copy of the dapper install cd, burn it, boot from it and run an it's integrity check menu option, then proceed to do a fresh install if everything checks out.

You probably know this but there are two versions; there is a live install version which boots into a desktop which you use to install while you can browse the net in case you need assistance, and the now 'alternative' version which has the text based installs.

---

### Post by lapsey on 2006-06-20
it's a toally fresh install of dapper with only automatix, nvidia drivers, k7 kernel bits and regular updates.

I know that some people find automatix doesn't work well for them but I wouldn't go so far as to blame that either.

It could be the kernel updates breaking existing software but I trust that the updates wouldn't be released if it broke existing packages.

---

### Post by WildTangent on 2006-06-20
[QUOTE=lapsey]Also, shouldn't ubuntu have a proper bug reporting mechanism by now? Lord knows I've tried going through bugzilla but that is pain without gain (especially when reporting gnome bugs is concerned)[/QUOTE]
We haven't used bugzilla for sometime now. The new bug tracker is here: [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

-Wild

---

### Post by Arktis on 2006-06-20
[QUOTE=lapsey]it's a toally fresh install of dapper with only automatix, nvidia drivers, k7 kernel bits and regular updates.

I know that some people find automatix doesn't work well for them but I wouldn't go so far as to blame that either.

It could be the kernel updates breaking existing software but I trust that the updates wouldn't be released if it broke existing packages.[/QUOTE]
Well I guess I'm sort of baffled here; I have no idea why you're having these problems and I'm not, and nobody else who posted here seems to be having them either.  ](*,)

Maybe you could try out not limiting yourself to the latest k7, and instead install several kernel versions and test them all out?

---

### Post by disturbed1 on 2006-06-20
I'm using the same kernel as you, and have experienced some of the problems you mentioned.

Namely the samba issues. It happens with any program that uses the gnomevfs. In most cases, most users would never see a problem. If you just browse to the samba folder, grab a quick file or two, no problem. But if you're connected to a couple of samba shares, and these samba shares are also sharing with themselves on windows, once a few users start to pass files around, Nautilus will crash, rhythmbox and totem will crash. Apps without gnomevfs compiled in (VLC for one) can't open files on the share, on and on. Samba support is just weak. But it isn't an Ubuntu problem, it's a samba issue, always has been.

Just mount the samba share in your fstab, which has cured most of these problem for me.

The only firefox issues I have are with some sites that have improper flash use. Other than those 2 or 3 flash sites I've came across firefox has never given me an issue. It could be a locale problem with firefox or a faulty extension or 2 :confused: I don't use any extensions, since the ones I have tried have always been buggy. Not saying that every extension is buggy, but it is known that extensions can cause issues. That's the first step to debug firefox on the mozilla site. Step 1. disable all extensions.

I've experienced the VLC problem. It's quite freaky when you que an ogg file to play in VLC, close VLC and it is still playing even after you delete the ogg file and empty the trash. I don't know what causes this to happen, and can't reproduce it, but it has happened a couple of times. I noticed that the VLC available in the MOTU repos for ubuntu was a couple versions behind, so I compiled my own. I haven't had any ghost files playing, but now have a couple of new issues that weren't there before. So I used an official VLC debian file of a newer version, even worse problems than the version I compiled myself. These issues were reported in the VLC bugzilla though ;)


I've become spoiled by just how good Ubuntu really is, and take it for granted every now and then. When that starts to happen, I just download another distro and give a shot for a few hours, and quickly come to see just how problem free Ubuntu really is  for me on my hardware :). If you do try another distro, and it happens to work better for you, no sense in beating yourself up trying to make Ubuntu work for you, when another distro works out of the box. But let the devs know what didn't work on Ubuntu, and what distro X did to make it better.

---

### Post by lapsey on 2006-06-20
good points disturbed1. 
interesting stuff about samba but i am experiencing the same problems through smbmount-ed shares (this is so non gnomevfs using apps can acess the shares)

i will try disabling firefox extensions - this is the most likely culprit, i admit.



i was silly to think this wouldn't end up a tech support thread but i still say my whining still stands in regards to inskcape and nvu :grin:

```
(inkscape:7026): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'inkscape' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 434067 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
```
/usr/lib/nvu-1.0/run-mozilla.sh: line 159:  7019 Segmentation fault      "$prog" ${1+"$@"}
```

---

### Post by tseliot on 2006-06-20
[QUOTE=lapsey]good points disturbed1. 
interesting stuff about samba but i am experiencing the same problems through smbmount-ed shares (this is so non gnomevfs using apps can acess the shares)

i will try disabling firefox extensions - this is the most likely culprit, i admit.



i was silly to think this wouldn't end up a tech support thread but i still say my whining still stands in regards to inskcape and nvu :grin:

```
(inkscape:7026): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'inkscape' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 434067 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
```
/usr/lib/nvu-1.0/run-mozilla.sh: line 159:  7019 Segmentation fault      "$prog" ${1+"$@"}
```[/QUOTE]
What happens if you type:
```
glxgears
```

---

### Post by lapsey on 2006-06-20
[QUOTE=tseliot]What happens if you type:
```
glxgears
```[/QUOTE]

glxgears render, animate fine

---

### Post by disturbed1 on 2006-06-20
I don't use samba mount at all. I make an entry in the fstab, and define the filesystem as cifs. CIFS is basically an improved version of SMB.

I don't remember where I read it, but came across it in a google search on samba mounts file locking on me and getting multiple HAL_D errors. Everything seemed to point to using CIFS so I did, and haven't had any issues.


There's nothing wrong with *whining* ;) at least you've done it in good taste.

I don't use Inkscape or NVU. I did apt-get install inkscape. Ran it and looked at it, but wasn't sure what to do :lol:. So at least it runs ;) I'm not creative at all, more of a technical person. But I might try to do some layer blending and text overlays for a couple of DVD projects I've got coming up. I usually use Gimp for my menus, but Inkscape looks a bit more powerfull.

---

### Post by therunnyman on 2006-06-21
Oh, lapsey, brother, testify...

I fume every time I sit down at this infernal Dapper box.  My gripes are all over the place on the boards, the long and short being Dapper was just plain prematurely, erm, issued.  Even a couple, maybe more, maybe a lot of devs concur with the statement.

Just wanted to let you know you're not by yourself out there, and that you've rendered your vituperation deftly.  Blessings on your house.

runny

---

