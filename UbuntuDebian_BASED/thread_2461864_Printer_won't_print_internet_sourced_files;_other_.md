---
title: "Printer won't print internet sourced files; other files work fine"
date: 2021-05-08
forum: Ubuntu/Debian BASED
---

### Post by joe12122 on 2021-05-08
Have been printing with the same setup for ages.  All of a sudden, now internet files are a problem. Any ideas?  I.m an old newbie who typically has no idea what posters and responders are talking about, so please dumb down your response as much as possible.  Thanks much.

---

### Post by TheFu on 2021-05-08
Perhaps you could clarify what "internet sourced files" means, exactly?  Seems like you could just save the file locally, then print it.
Also, maybe if you said which Ubuntu release you are running and which DE, then someone might be able to help?

---

### Post by joe12122 on 2021-05-09
Hi TheFu.  

The old 64bit laptop is running KDE neon 5.20, so i'm assuming the latest LTS release of ubuntu.  I'll double check on downloaded (from the internet) files, but i think they are not printing either.

Joe

---

### Post by DuckHook on 2021-05-09
Please post back to this thread the output of: ```
uname -a
``````
lsb_release -a
``````
sudo lshw -sanitize
```Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar..

You also need to tell us what make and model your printer is, what driver you are using and how you installed that driver. Further info that would help would be what sort of files you are successful with and what sort chokes. Are they PDFs? MS Office? Graphics? Native LibreOffice?

---

### Post by joe12122 on 2021-05-10
I did check on downloaded internet files( PDF, jpg, ?) and i was able to print them.  There was a message, however, on PDF files that read: "this document has XFA forms, which are currently unsupported".  Also, i updated to KDE neon 5.21.4.  The laptop is connected (via usb cable) to a Brother MFC-7360N printer.  Can't remember how i got it going; maybe installed a cups driver?  Will follow through on other suggestions as soon as i can.  Thanks.
Joe

---

### Post by him610 on 2021-05-10
> ...Brother MFC-7360N printer.
I have one of these printers; although, mine is connected to my home network via a Cat5 cable. The 'N' in the model represents 'network'. Typically, the installation script may be downloaded from [https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=mfc7360n_all]("https://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=mfc7360n_all")
My MFC-7360N has been a very good, dependable printer, scanner, copy, facsimile device that I have had for several years now. Never had any issues with it printing anything. I just recently replaced the original toner cartridge.

---

### Post by QIII on 2021-05-10
Moved to Ubuntu/Debian BASED.  KDE Neon is a distinct distribution and not one of the official flavors of Ubuntu.

---

### Post by joe12122 on 2021-05-10
One exception to printed downloads is HTML files.  Those i can't print directly; i can take a screen shot and print the screen shot tho. The main problem remains printing directly from the webpage, which is a no go.  Joe

---

### Post by TheFu on 2021-05-10
> **joe12122 said:**
> One exception to printed downloads is HTML files.  Those i can't print directly; i can take a screen shot and print the screen shot tho. The main problem remains printing directly from the webpage, which is a no go.  Joe

Please help us out.

"it doesn't print" is lacking details.  

**Which program** are you trying to use to print?  Last time I checked, no printers accept raw HTML files. They have to go through a conversion process to either PCL or postscript for a printer to do something.  That is normally handled by the printer driver.  The last 12-18 months, the Chromium browser was installed as a snap package in Ubuntu. If you are trying to print using that, there could be security confinement conflicts by the snap packaging.

If you don't know which program is being used, at least tell us exactly what buttons you press/click/type so that someone with a similar setup might figure it out?

I know you don't mean for this to be painful to help you. Inexact  posts, without details or technically accurate information make it very difficult to help.  It is fine not to know stuff. Nobody knows it, but don't make it a world-wide egg-hunt either, please.

---

