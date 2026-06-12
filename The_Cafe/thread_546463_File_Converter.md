---
title: "File Converter?"
date: 2007-09-08
forum: The Cafe
---

### Post by blithen on 2007-09-08
Anyone know of a good file converter, specifically a ISO, to IMG file?

---

### Post by HermanAB on 2007-09-08
Well, ISO 9660 is the standard which everybody should be using for CD/DVD images.  What program do you have a problem with?

---

### Post by blithen on 2007-09-08
QEMU.
I'm not running it on linux, I'm trying to get it working on Windows.
But it doesn't like .iso

---

### Post by BoyOfDestiny on 2007-09-08
> **blithen said:**
> QEMU.
I'm not running it on linux, I'm trying to get it working on Windows.
But it doesn't like .iso

Hmm... Maybe we should try to help with qemu? What's the output/error?

Anyway, back when I used Windows, I used daemon tools to mount the iso (I'm thankful to be able to mount them or just extract the content from them under Ubuntu with no fuss...)

---

### Post by blithen on 2007-09-08
[http://i13.photobucket.com/albums/a273/blithen/weee.jpg](http://i13.photobucket.com/albums/a273/blithen/weee.jpg)
There, that's a screenshot of the error.
Good luck @__@

---

### Post by starcraft.man on 2007-09-08
Just a thought, but you can try [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") if your not dead set on QEMU. I don't see why it doesn't support ISO, I know VBox does cuz I've installed from those.

---

### Post by BoyOfDestiny on 2007-09-08
> **blithen said:**
> [http://i13.photobucket.com/albums/a273/blithen/weee.jpg](http://i13.photobucket.com/albums/a273/blithen/weee.jpg)
There, that's a screenshot of the error.
Good luck @__@

show me the syntax of the command, I think I might have an idea.

if you are trying to pass -hda blah.iso... try
-cdrom blah.iso

And don't worry, QEMU handles ISO fine. Virtualbox is based off its code :)

---

### Post by blithen on 2007-09-08
It needs to be small and able to fit on a 256mb flashdrive. Does Virtual Box do that?

---

### Post by blithen on 2007-09-08
> **BoyOfDestiny said:**
> show me the syntax of the command, I think I might have an idea.

if you are trying to pass -hda blah.iso... try
-cdrom blah.iso

And don't worry, QEMU handles ISO fine. Virtualbox is based off its code :)

C:\blah\blah qemu.exe -L . -hda linux.img
That's what I use, but I will try that.

---

### Post by starcraft.man on 2007-09-08
> **BoyOfDestiny said:**
> show me the syntax of the command, I think I might have an idea.

if you are trying to pass -hda blah.iso... try
-cdrom blah.iso

And don't worry, QEMU handles ISO fine. Virtualbox is based off its code :)

Oh right, hehe. Well ok then, I forgot >.<.

> **blithen said:**
> It needs to be small and able to fit on a 256mb flashdrive. Does Virtual Box do that?

Uh, just what did you expect to fit on 256 MB? A complete VM solution with a Linux OS will never fit on that... least certainly not Ubuntu.

---

### Post by BoyOfDestiny on 2007-09-08
> **blithen said:**
> C:\blah\blah qemu.exe -L . -hda linux.img
That's what I use, but I will try that.

Ok, I'm not 100% what you're going for... If you want a linux distro in your pocket. Then go for qemu + DamnSmallLinux

Just grab the iso,

and it should be like
qemu -cdrom dsl.iso -m 256 -boot d -soundhw sb16 -localtime 

Keep at it.

---

### Post by BoyOfDestiny on 2007-09-08
> **starcraft.man said:**
> Oh right, hehe. Well ok then, I forgot >.<.



Uh, just what did you expect to fit on 256 MB? A complete VM solution with a Linux OS will never fit on that... least certainly not Ubuntu.

There are some really cool "light" distros.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

50mb :)

---

### Post by starcraft.man on 2007-09-08
> **BoyOfDestiny said:**
> There are some really cool "light" distros.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

50mb :)

Ya I knew that. There's also Puppy. Those aren't for me though, I gave em a look. >.>

If you want Ubuntu blithen my recommendation is to pay for a cheap 4 GB pen drive [(example)]("http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10084409&catid=") and install following the [pen drive install instructions.]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") In addition, it will be a persistent install so you will save your settings and info after you exit. Oh and you can install from Windows, scroll down the guide. This way also does away with the need for any VM...

That's how I'd do it IMO :).

Edit: Oh and if you want lot's of space you may want an 8...

---

### Post by blithen on 2007-09-08
> **starcraft.man said:**
> Oh right, hehe. Well ok then, I forgot >.<.



Uh, just what did you expect to fit on 256 MB? A complete VM solution with a Linux OS will never fit on that... least certainly not Ubuntu.

LIES!
I fit virtual box, a virtual OS with no HDD on a 256mb, and it boots Grml-small
8D!
Starcraftman, you ARE thee man!

---

### Post by blithen on 2007-09-08
> **BoyOfDestiny said:**
> There are some really cool "light" distros.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

50mb :)

I've tried a lot of those. I just want a command line based one.
I'm planning on ya' know...'playing' with my schools computers  >_> <_<

---

### Post by BoyOfDestiny on 2007-09-08
> **starcraft.man said:**
> Ya I knew that. There's also Puppy. Those aren't for me though, I gave em a look. >.>

If you want Ubuntu blithen my recommendation is to pay for a cheap 4 GB pen drive [(example)]("http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10084409&catid=") and install following the [pen drive install instructions.]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") In addition, it will be a persistent install so you will save your settings and info after you exit. Oh and you can install from Windows, scroll down the guide. This way also does away with the need for any VM...

That's how I'd do it IMO :).

Edit: Oh and if you want lot's of space you may want an 8...

++
Considering how common faster machines nowadays. But depending on what he wants this for (maybe to just browse or store documents on, DSL will do fine with 256mb...)

---

### Post by blithen on 2007-09-08
Oh, I should've made this clear from the beginning.
I have 2 Flash Drive
One is a 256mb
and then the other more...advanced is a 2gig.

---

### Post by starcraft.man on 2007-09-08
> **blithen said:**
> LIES!
I fit virtual box, a virtual OS with no HDD on a 256mb, and it boots Grml-small
8D!
Starcraftman, you ARE thee man!

LOL! Yay, well glad your happy. And course I'm the man, it's in the name 8-)

> **blithen said:**
> I've tried a lot of those. I just want a command line based one.
I'm planning on ya' know...'playing' with my schools computers  >_> <_<

I didn't do it. I take no responsibility for what you do with that... don't even tell me. Just uh... you didn't even see me.... *ducks out of the thread*

---

### Post by blithen on 2007-09-08
> **starcraft.man said:**
> LOL! Yay, well glad your happy. And course I'm the man, it's in the name 8-)



LOL! I didn't do it. I take no responsibility for what you do with that... don't even tell me. Just uh... you didn't even see me.... *ducks out of the thread*

Haha, do you want me to PM you what I do with it.
'Cause once upon a time they blocked me out of network access to a special folder were a lot of teachers kept answers to tests they have so...I might take a peek. >_> <_<
Man, I love linux 8D
....I mean...nevermind. I just wanted a bootable linux on a pendrive. <_<;;

---

