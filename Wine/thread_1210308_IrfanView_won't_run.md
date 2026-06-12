---
title: "IrfanView won't run"
date: 2009-07-11
forum: Wine
---

### Post by Solipsil on 2009-07-11
I've managed to install IrfanView through Wine (along with needed .dll) but unlike in Mint, it won't run in Ubuntu. I've tried all of the options in Wine regarding specific Windows system emulation, as well as .dll overrides, but none of these worked. I can see the CPU struggling to open, but nothing happens.
I have been instructed to take a look at [http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)
This is where I learned how to override dlls and tweak Wine to see which setting works with the application I want to run, but I haven't managed to solve the problem.

(in case you are wondering, the reason why I want IrfanView is because of the very easy way to crop images with predefined crop selection size that I can paste onto the image I want to crop.)

Any help appreciated.

---

### Post by ackanao on 2009-07-11
Just use winetricks to install comctl32 - here's winetricks wiki page:

[http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")

It's better to create new wineprefix for IrfanView because there's possibility that winetricks will mess up your default wineprefix (.wine folder).

---

### Post by Solipsil on 2009-07-11
Thanks for that, installed Winetricks and now about to install comctl32.
I unzipped it into C:\windows\temp.
How do I go about creating a new wineprefix and what do I do afterwards? Sorry, I'm a beginner.

EDIT:
I didn't have to do anything after all, it works now! Thanks very much!

---

### Post by ackanao on 2009-07-11
OK. First delete your .wine folder because it's obviously messed up; Then, start terminal and type **winecfg** - this will recreate .wine folder.

To create new wineprefix type this command:

```
WINEPREFIX=~/Desktop/IrfanView wineboot
```
*This will create IrfanView wineprefix on your Desktop - use another path if you want*

Downlad winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

Use winetricks to install "stuff" needed for IrfanView:
```
WINEPREFIX=~/Desktop/IrfanView sh winetricks mfc42 comctl32
```

Start IrfanView installer:
```
env WINEPREFIX=~/Desktop/IrfanView wine /home/Solipsil/Desktop/iview425_setup.exe
```
*IrfanView installer is placed on my Desktop - adjust path accordingly*

Start IrfanView:
```
env WINEPREFIX=~/Desktop/IrfanView wine "C:\Program Files\IrfanView\i_view32.exe"

```

To install IrfanView plugins, type this (I didn't test them so I don't know whether they work or not):

```
env WINEPREFIX=~/Desktop/IrfanView wine /home/Solipsil/Desktop/irfanview_plugins_425_setup.exe

```

*IrfanView plugins installer is also placed on my Desktop*

---

### Post by ackanao on 2009-07-11
There's a chance that some other applications will not work because you used winetricks on your default wineprefix (.wine folder). Please recreate your default wineprefix and use another for IrfanView.

---

### Post by Solipsil on 2009-07-11
Thanks a lot for those tips, I really appreciate it.
I got it to work without any changes, but I'm saving your tips in my designated Ubuntu help folder in case next time I'm not so lucky.

Thanks!

---

### Post by ackanao on 2009-07-11
Solipsil, believe me it's really important to keep your default wineprefix in a good shape - There's a good chance that another application you try to install will not work just because you used winetricks on default wineprefix... If you're having troubles creating a new one (for IrfanView) I'll do my best to help you...

---

### Post by ackanao on 2009-07-11
I corrected some mistakes I made in commands - you can use them now.

---

### Post by Solipsil on 2009-07-11
I see, in that case, I'll get right to it.  I'll post here in case I encounter problems.

---

### Post by Solipsil on 2009-07-11
This might be a really stupid question (sorry about that) but - where do I find the Wine folder so I can delete it?

---

### Post by ackanao on 2009-07-11
Goto Places -> Home Folder; Goto View and check "Show Hidden Files" option - now look for .wine folder and delete it. Start up terminal and type winecfg to recreate it.

---

### Post by peterqb on 2009-09-30
Hello,

It works as far as this:


Start IrfanView installer:
```
env WINEPREFIX=~/Desktop/IrfanView wine /home/Solipsil/Desktop/iview425_setup.exe
```
*IrfanView installer is placed on my Desktop - adjust path accordingly*

It isn't on mine. Where might I be going wrong?

Start IrfanView:
```
env WINEPREFIX=~/Desktop/IrfanView wine "C:\Program Files\IrfanView\i_view32.exe"

```

So here there is nothing for the computer to work on...


Many thanks.
--
pqb

---

### Post by Sir Jasper on 2009-10-03
Hi,

If you were to install Wine-Doors you could then install IrfanView 4 from its menu.

I haven´t tried it but they could easily be uninstalled  if it didn´t work.

My regards

---

### Post by peterqb on 2009-10-04
Tried that, but could not get the archives to open to load it.

Not having much luck here :-(
--
pqb

---

### Post by shantiq on 2011-10-08
> **ackanao said:**
> OK. First delete your .wine folder because it's obviously messed up; Then, start terminal and type **winecfg** - this will recreate .wine folder.

To create new wineprefix type this command:

```
WINEPREFIX=~/Desktop/IrfanView wineboot
```
*This will create IrfanView wineprefix on your Desktop - use another path if you want*

Downlad winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

Use winetricks to install "stuff" needed for IrfanView:
```
WINEPREFIX=~/Desktop/IrfanView sh winetricks mfc42 comctl32
```

Start IrfanView installer:
```
env WINEPREFIX=~/Desktop/IrfanView wine /home/Solipsil/Desktop/iview425_setup.exe
```
*IrfanView installer is placed on my Desktop - adjust path accordingly*

Start IrfanView:
```
env WINEPREFIX=~/Desktop/IrfanView wine "C:\Program Files\IrfanView\i_view32.exe"

```

To install IrfanView plugins, type this (I didn't test them so I don't know whether they work or not):

```
env WINEPREFIX=~/Desktop/IrfanView wine /home/Solipsil/Desktop/irfanview_plugins_425_setup.exe

```

*IrfanView plugins installer is also placed on my Desktop*



wow brilliant still works with 430 current version



Did it a slightly less command line way **[here]("http://ubuntuforums.org/showpost.php?p=11322743&postcount=10")**

---

