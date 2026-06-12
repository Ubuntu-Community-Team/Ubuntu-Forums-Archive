---
title: "Goodbye Debian, hello Ubuntu"
date: 2011-10-19
forum: Testimonials &amp; Experiences
---

### Post by Mr. Jay on 2011-10-19
After almost 14 years of using Debian, I've switched to Ubuntu 11.10 and currently migrate my old system (original installation from 1997, kept up to date and converted to 64 bits semi-manually some years ago).

It's relieving not having to hack lots of parts of the system to get around the notoriously weird and geeky "Debian way", which in the end led to package management being broken beyond repair here. I can use Ubuntu almost as is. Heck, I didn't even compile a kernel myself.

I got to know every bit of my old system; this would take forever now. Lots of additional complexity added behind the scenes. I hope this won't result in the "Windows effect" and everything blowing up some day. Let's see. For now I like it, in spite of some issues (e.g. a showstopper problem during installation) which I'll discuss separately.

---

### Post by crazy bird on 2011-10-19
Welcome to the world called Ubuntu!
 
I had Debian running on my system for a while and kicked it off my system due to bad (let's face it: very poor crappy) font smoothing. Posted many times on the Debian forum and got many answers but not 1 solution fixed my very poor crappy font smoothing! Never had any issues with Ubuntu with font smoothing. Not even with Fedora, Linux Mint, Xubuntu, OpenSuse. Just Debian was like that. Although it is a very stable system, you have to move heaven and earth to get something done!

---

### Post by sffvba[e0rt on 2011-10-19
Not often these days to here of someone coming from Debian to Ubuntu (it tends to be the other way around)...

Welcome :)


404

---

### Post by MartyBuntu on 2011-10-19
> **Mr. Jay said:**
> (original installation from 1997, kept up to date and converted to 64 bits semi-manually some years ago).



This is fascinating.

Please, tell us more about how you kept a rolling Debian install going for 14+ years and converted 32-bit to 64-bit. I'd be very interested.

---

### Post by craig10x on 2011-10-19
> **crazy bird said:**
> Welcome to the world called Ubuntu!
 
I had Debian running on my system for a while and kicked it off my system due to bad (let's face it: very poor crappy) font smoothing. Posted many times on the Debian forum and got many answers but not 1 solution fixed my very poor crappy font smoothing! Never had any issues with Ubuntu with font smoothing. Not even with Fedora, Linux Mint, Xubuntu, OpenSuse. Just Debian was like that. Although it is a very stable system, you have to move heaven and earth to get something done!

Yeah...debian refuses to use the excellent ubuntu patching to libcairo that give ubuntu it's excellent font rendering...

Clem (head of linux mint) had no hesitation in adding it into the mint debian edition after many mentioned that the first mint debian isos had crummy font rendering (courtesy debian...lol)....

And of course, main edition mint is ubuntu based...and OpenSuse i believe also uses the patches...and all other ubuntu based distros have the same great rendering as well...

---

### Post by lancest on 2011-10-20
Interesting about Debian upgrading!  The only other distro that I've been able to get good smooth fonts in was Arch.  Follow their instructions. Still can't figure out why Fedora, SuSE and Debian don't come up to speed on that. Guess it depends on your point of view.  
I also find Ubuntu fonts better than Windows.

---

### Post by Mr. Jay on 2011-10-20
> **MartyBuntu said:**
> how you kept a rolling Debian install going for 14+ years and converted 32-bit to 64-bit.
I disabled many distro features, simplified many things, and pinned the installation to old binaries a few times when I had too many problems with never versions.
But it increasingly became a frankenstein construct, for example until last year I was still using a 32 bit fvwm on top of the 64-bit X because the configuration file had changed 10 years ago or so, and I was too lazy to convert it. Some library update finally made it crash.
But it was really fine until about 2-3 years ago, I had very little problems, and if I did, they could be worked out with tools like strace. The real problems started when the Intel GMA modesetting drivers packaged with newer X never worked properly, same with the keyboard maps. I had to pin X and related libs, more and more parts couldn't then be updated because of their dependencies on them. A few months ago I wanted to install the latest Hugin, apt touched too much stuff and at last it all blew up (while Hugin still didn't work). I had to use the backup to re-replace a lot of binaries and now the system is in a state where any apt action will probably break it for good.

I'll keep Debian on my rented server but I also had problems there. Debian wouldn't supply Exim4 linked to OpenSSL because of one of their usual license hair splitting things, while linked to GnuTLS it produced timeouts. I compiled it myself, forgot to update when a buffer overflow remote exploit appeared, and got 0wned. Great.

About the 32-bits to 64, I don't even remember exactly but with the dpkg tools you can write your package configuration into a file, then install a new 64 bit system and push the old package configuration into the new system with "some_program <file". Some manual adaptions had to be done afterwards but all in all it worked quite well.

About the font smoothing, I don't want it and I was running the gnome-settings-daemon under fvwm to get rid of it and get programs to use the bitmap helvetica font. Fortunately this was easy to set up in Ubuntu.

---

