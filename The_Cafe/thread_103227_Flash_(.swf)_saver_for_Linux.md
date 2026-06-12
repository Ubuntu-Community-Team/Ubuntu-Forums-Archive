---
title: "Flash (.swf) saver for Linux"
date: 2005-12-13
forum: The Cafe
---

### Post by dolny on 2005-12-13
I really didn't know where to put it. So I'll ask here and maybe the mods will move it somewhere. Is there a .swf file saver for Linux? Some kind of browser plugin or something like that.

---

### Post by bionnaki on 2005-12-13
In firefox, if you go to tools>page info>media
you can select the flash & "save as..."

---

### Post by matthew on 2005-12-13
Wow. I had never opened that menu options in Firefox (which is unusual...I generally tinker with everything). That's cool. Thanks for the info!

---

### Post by dolny on 2005-12-13
Anybody has a clue how to do it with Opera?

---

### Post by iamrizki on 2009-01-03
how about file .flv, the other type of flash file? can it also applied here?

---

### Post by roachk71 on 2009-01-03
Right-clicking and saving never worked for me, so I use the Video DownloadHelper Add-on for .flv files. And, since I own a PSP, I had to download and install PSPVC.

If you own a PSP and are interested in watching downloaded videos on that, you can find PSPVC [here]("http://pspvc.sourceforge.net/"). Be sure to read the README and INSTALL files, since you will need a few development libraries to build it.

Oops, I'd nearly forgotten: The documentation doesn't tell you, but you also need **yasm** from the repos for PSPVC.

---

### Post by creek23 on 2009-01-03
> **iamrizki said:**
> how about file .flv, the other type of flash file? can it also applied here?

You can just copy the file from Firefox's "cache". It's what I do.

---

### Post by DOS4dinner on 2009-01-03
Get the download helper addon for firefox. (it's icon is 3 balls--blue, yellow, and red).

Go to the preferences for it and go to medialink tab.

Type "swf" (without quotes) and hit add.

Now just click the download helper icon and download as you please.

---

### Post by Bölvaður on 2009-01-03
> **iamrizki said:**
> how about file .flv, the other type of flash file? can it also applied here?

with nautilus, any file manager or the terminal browse your way to /tmp and feast your eyes on the glory of the videos you are watching atm.


so in terminal either do

cd /tmp
ls -l

or

nautilus /tmp


note that the content of this file disappears when you dont have the content in firefox any more.

---

