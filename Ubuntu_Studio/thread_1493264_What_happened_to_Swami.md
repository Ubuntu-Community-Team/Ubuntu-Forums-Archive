---
title: "What happened to Swami?"
date: 2010-05-25
forum: Ubuntu Studio
---

### Post by pdxken on 2010-05-25
Swami SoundFont editor not in repos for Karmic or Lucid. Last in Jaunty.
Is there some other SF2 editor I don't know about?

Didn't use it that much but now that it's gone I want it. Murphy's law?

Thanks.
Ken.

---

### Post by sgx on 2010-05-26
> **pdxken said:**
> Swami SoundFont editor not in repos for Karmic or Lucid. Last in Jaunty.
Is there some other SF2 editor I don't know about?

Didn't use it that much but now that it's gone I want it. Murphy's law?

Thanks.
Ken.

[http://packages.debian.org/lenny/swami](http://packages.debian.org/lenny/swami)

look at the dependencies, if you have them, or modern versions, try installing it with dpkg -i

If you need to install it with dpkg -i --force

you may need to remove it temporarily to use synaptic, the reinstall.
I do that with phasex. No big deal.

I would install an older good ubuntu on a usbstick, maybe 8.04 Studio, for old apps that have become orphans, and to have a midnight emergency
distro if a mechanical failure ends a hard-disk.

Cheers

---

### Post by pdxken on 2010-05-26
Thanks sgx.
sudo dpkg -i swami.deb  Returned this:
dpkg: error processing swami.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 swami.deb

sudo dpkg -i --force swami.deb  Returned this:
dpkg: unknown force/refuse option `swami.deb' ...

I suspect I would need to add lenny to my sources.list. I don't know how to do that and read another post that mixing Ubuntu and debian sources is a bad idea. Don't really understand this very well.

Last year I managed to compile swami with Karmic. It was a newer version with color and was cooler looking.

I tried that in Lucid beta and it failed. Don't remember why. Compiler messages are a lot of incomprehensible weird stuff to me.
Haven't tried it sense release yet.

That brings up another question.
I still have Karmic on another partition. If swami works there why can't I copy it to my Lucid partition and how do I do that?
I'm thinking of creating a PPA on my data partition. Is that posible?

Thanks.
Ken.

---

### Post by lykeion on 2010-05-26
Swami seems to be have been dropped because of dependencies of old GTK+ libraries.

You can download a deb-package of Swami from the Debian Lenny repository and install manually, like previous poster mentioned.

I also found out that you need to install some GTK+ libraries to be able to install Swami, so...

[LIST]
[*]Browse to the links below ( note that the order is relevant).
[*]Scroll down to the **Download** header and select the download link for your computer (select **all** or **i386** if you have no clue).
[*]Select a mirror close to you and save the deb-file (on your desktop or whatever).
[*]Doubleclick the deb-file to install the package.
[/LIST]

After you've installed the first three GTK+1.2 libraries you should be able to install Swami.

1. libgtk1.2-common
[http://packages.debian.org/lenny/libgtk1.2-common](http://packages.debian.org/lenny/libgtk1.2-common)

2. libglib1.2ldbl
[http://packages.debian.org/lenny/libglib1.2ldbl](http://packages.debian.org/lenny/libglib1.2ldbl)

3. libgtk1.2
[http://packages.debian.org/lenny/libgtk1.2](http://packages.debian.org/lenny/libgtk1.2)

4. swami
[http://packages.debian.org/lenny/swami](http://packages.debian.org/lenny/swami)

---

### Post by pdxken on 2010-05-26
Thanks lykeion.

That got swami 0.94, as I recall installed.
No audio yet so I'll have to play with that.
It still works in Karmic which is swami 2.0 that I installed from source.

I think I will hang-on to my Karmic partition for a while until Lucid works for me better. The advantage of multi-boot for me is to be able to leap-frog releases to be sure the shiny new one works the way I want it to before abandoning the old one.:)

Rosegarden is my other reason to keep Karmic. I'll talk about that in a different post

Thanks.
Ken.

---

### Post by sgx on 2010-05-26
DOH! I forgot to post the link! :( Thank you for picking up
the slack :) Sorry pdxken for contributing confusion instead of
the goods.

---

### Post by pdxken on 2010-05-26
DOH! I forgot to post the link! 

Hey! DOH! is my middle name. Or is it my first name?

No, DOH is my first and middel name. DOH! DOH! Ken.:P

:popcorn: Ken.

---

### Post by grackleman on 2010-12-04
Hi
I found the same problem. Not knowing much about the details of the OS I simply installed Viena (1 n) in Wine and it works fine. Sfark also runs in Wine. 

[http://www.synthfont.com/](http://www.synthfont.com/)
[http://www.melodymachine.com/sfark.htm](http://www.melodymachine.com/sfark.htm)

OK that's cheating if you're a real Linux guru.

Peter

---

### Post by babarosa on 2010-12-06
Hi,

Swami v2.0 beta is available for Lucid and newer systems ([http://sourceforge.net/apps/mediawiki/swami/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/swami/index.php?title=Main_Page)), there is also a ppa.

I use it and it works very fine.

Regards,
Michael

---

