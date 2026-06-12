---
title: "Anti-virus ... AVG Free for Linux - challenge!"
date: 2010-02-23
forum: Security
---

### Post by jzelliott on 2010-02-23
AVG have a Free version for Linux users.  I downloaded it and installed it, but could not find it afterwards, so, today, I downloaded it again and went to install it but was told "package already installed".  I re-installed it anyway, because I could not find the fist installation ... now I cannot find the second installation. Where does one look for such a program?  I need to find it to configure it, and also just to check it is actually there and working. 

Maybe I am doing something wrong when installing it.
Ubuntu is based on the Debian Distro, is it not?

Any help would be much apprciated

Kind regards and many thanks,  James

---

### Post by giammy on 2010-02-23
Hi

open a terminal and issue the command

dpkg --listfiles  (name of avg package)


this shows you where the installed files are!

bye
giammy

---

### Post by mkvnmtr on 2010-02-23
Is it by chance a command line app? If so you might have to start it in the terminal.

---

### Post by scottuss on 2010-02-23
Yeah, I was under the impression that AVG for Linux was a command line application... could be wrong though.

---

### Post by giammy on 2010-02-23
> **mkvnmtr said:**
> Is it by chance a command line app? If so you might have to start it in the terminal.

Hi,

is, it's a terminal app (you have to open the terminal :-)

bye
giammy

---

### Post by ajgreeny on 2010-02-23
This is a command line application, with no GUI, so you will need to use the terminal; it is not like AVG for windows with its GUI.  You will need to start it with a terminal command (I've no idea what) or simply schedule it to run at specific times, once you can find the configuration, of course.

In a recent test in Linux Format magazine here in UK it did poorly, getting 2/10 in the list.  Clamav did a lot better with 8/10, as did clamtk.  The best, at 9/10 were Avast and BitDefender, also free for personal use.

I have now given up using a virus scanner completely, as I do not use windows at all, though I did used to run clamav occasionally, when I first used Ubuntu.  I just couldn't get used to not having that job running, I suppose.

---

### Post by Sir Jasper on 2010-02-23
Hi,

If you want to try avast (debian version) as ajgreeny suggested then download it to your desktop double left click and it will probably install in Accessories.

It does a full (not incremental) update, usually twice daily, so it ideally needs broadband for fast downloads.

I use Wine so I run a scan once or twice a week on my Home directory (or sometimes just my Wine folders), but, as again suggested by ajgreeny, you may not need any of the programs mentioned above.

My regards

PS avast has a GUI

---

### Post by jzelliott on 2010-02-23
Thanks to you all for all the information - James

---

