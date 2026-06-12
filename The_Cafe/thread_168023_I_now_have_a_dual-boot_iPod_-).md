---
title: "I now have a dual-boot iPod :-)"
date: 2006-04-29
forum: The Cafe
---

### Post by mostwanted on 2006-04-29
I just installed iPodLinux on my iPod and it's quite cool. Installation was just as smooth as installing Ubuntu, only a lot quicker.

The only real problem was that the contrast was set too low when the iPodLinux OS boots. The solution to that was to enable constant backlight (a hardware built-in) so I could read the menu options, then I went to settings and changed the contrast rate. There's an option to save the default settings, so I did that. Now it works perfectly!

The UI, podzilla, looks like the standard iPod user interface. It comes with a pretty much the standard iPod settings, apps + a big selection of games (TuxChess looks really good) and fun graphics tests (fractal and 3D stuff) and there's even a file browser there. Seeing the UNIX file-structure in a file browser on your iPod is a really awesome experience!

I've got to put some music on and see how well it copes with that. I'm especially eager to see if it'll play Ogg Vorbis (it says it can play 128+ bitrates on the website).

Here are some photos I took:

[IMG]http://monkeyblog.org/img/photos/ipodlinux_1.jpg[/IMG]

[IMG]http://monkeyblog.org/img/photos/ipodlinux_2.jpg[/IMG]

[IMG]http://monkeyblog.org/img/photos/ipodlinux_3.jpg[/IMG]

---

### Post by Ob1 on 2006-04-29
Does the iPodLinux software change the filesystem to FAT? 

that's cool by the way.

---

### Post by Tedd on 2006-04-29
That is very cool. I have a Creative Zen Micro- well, had, it got stolen out of my locker. Good Christian school...

But I digress, that is very awesome.

---

### Post by -Rick- on 2006-04-29
I got iPodLinux on my nano too, very nice to impress people with doom and quake mods for doom :)

[QUOTE=Ob1]Does the iPodLinux software change the filesystem to FAT? 

that's cool by the way.[/QUOTE]
iPodLinux itself wants a ext3 filesystem. You have to create an additional partition for that. The already existing partition which contains the music needs to be FAT afaik, since ipodlinux can't read the fs from apple.

---

### Post by Wallakoala on 2006-04-29
What kind of ipod do you have? I am thinking about doing this with my ipod mini. My main concern is how well it plays music...

---

### Post by mostwanted on 2006-04-30
I have a 4G ipod (no colour screen, but click-wheel). The original iPod software is there as well, it's possible to boot into each OS when you need to. The only difference in the file system is that the default NTFS or FAT file-system (not sure which one it is, think it's NTFS) is made slightly smaller, to make room for a very small (about 24 MB) Ext2 partition with iPodLinux on it.

I'm gonna attempt putting some music on and see if I can play it from iPodLinux. BTW this thing has Vi (useless without a keyboard, but nevertheless!).

---

### Post by -Rick- on 2006-04-30
[QUOTE=Wallakoala]What kind of ipod do you have? I am thinking about doing this with my ipod mini. My main concern is how well it plays music...[/QUOTE]
Music playing on my nano with linux is pretty bad(gives memory errors). When I want music I boot to the original OS.

---

### Post by mostwanted on 2006-04-30
[QUOTE=-Rick-]Music playing on my nano with linux is pretty bad(gives memory errors). When I want music I boot to the original OS.[/QUOTE]

I've tried playing some AAC and Mp3 in Podzilla 1.0. It's okay, but every song takes a few seconds to buffer so skipping between songs is not continious. It reads the iPod database just fine and allows me view playlists and music in pretty much the same way the normal firmware does.

I updated to Podzilla 2.0 because it's much nicer (has more apps, better interface), but there's a bug loading the music player module unfortunately. Doesn't matter ;)

About to install iDoom.

---

### Post by guine on 2006-04-30
I've been considering installing ipod linux on my nano but the main thing holding me back is not knowing how many songs id still be able to store on my ipod.  Does anyone have any clues as to how many songs i'd still be able to have on my 2gb nano if i installed linux on it?  Thanks.

---

### Post by mostwanted on 2006-04-30
On my 4G iPod, the default install method of iPodLinux is to shrink the firmware partition (which Apple has made a lot bigger than it has to be) and use 24 MB space taken from there. That way you don't lose any space for your songs, since the data partition stays the same size.

I still shrunk the data partition to get 256 MB for iPodLinux for future apps :P.

iDoom works btw! But only on Podzilla 1 (couldn't launch anything from the file browser in Podzilla 2). Too bad I can't have Podzilla 2 at the same time :(

---

### Post by bestiarosa on 2006-06-09
Hi!
I don't know whether you can help me out. I have a very simple problem but I can't see how to solve it.
I have wget'd and gunzip'd the ipodlinux-installer-2.2l
I try to run it: ./ipodlinux-installer-2.2l.run
I get a permission denied error.
So I try with: sudo ./ipodlinux-installer-2.2l.run
Says that "command is not found".

What's my problem here?

---

### Post by bestiarosa on 2006-06-09
Ok, all I had to do was chmod +x ipodlinux-installer-2.2l
Shouldn't somebody also specify this passage on the ipolinux help?

---

### Post by oss_monkey on 2006-08-09
I have a more damning problem. I was able to extract the installer and the little tux/ipod icon, but when I run the installer, I get:

> installer: error while loading shared libraries: libcrypto.so.0.9.7: cannot open shared object file: No such file or directory

Anyone have an idea as to what happened? I've installed the libpng3 package, as the website has said.

---

### Post by oss_monkey on 2006-08-10
Out of frustration, I decided to go with an alternative: [Rockbox]("http://www.rockbox.org"). The ipod took it pretty well. Now I'm playing OGG with no problems. :)

---

### Post by RAV TUX on 2006-08-10
> **oss_monkey said:**
> Out of frustration, I decided to go with an alternative: [Rockbox]("http://www.rockbox.org"). The ipod took it pretty well. Now I'm playing OGG with no problems. :)
simply awesome.

---

### Post by MetalMusicAddict on 2006-08-10
Yea, Rockbox is pretty awesome. Mostly because it works for ton of players. I have yet to tackle it on my iRiver H360 but its on my list. You can even play Doom on it. :)

---

### Post by hanzomon4 on 2006-08-11
And You can make it super pretty

---

