---
title: "I need to use a keylogger"
date: 2006-11-19
forum: Server Platforms
---

### Post by bionnaki on 2006-11-19
I need a keylogger on computer. I suspect something illegal is going on and I need evidence. what is the best way to do this?

I install lkl but I receive an error whenever I use it:

> sudo lkl -l -k /home/name/.lkl/keymaps/us_km -o log.file

Started to log port 0x60. Keymap is /home/name/.lkl/keymaps/us_km. The logfile is log.file.
Segmentation fault (core dumped)


I have no idea what that means.

what other linux keylogger is out there? any that can run under wine? any other techniques that would log keystrokes?

Please do not lecture me about keyloggers - I am an adult and I need to do this with my computer. If that is your sentiment, please leave it to yourself and do not derail this thread like every other keylogger thread on this forum. I am not listening.

---

### Post by aysiu on 2006-11-19
Maybe this?
[http://pykeylogger.sourceforge.net/wiki/index.php/Main_Page](http://pykeylogger.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by bionnaki on 2006-11-19
that's windows only right? I wasnt able to get that running in wine.

so far, I tried lkl but I get that weird error and PyKeylogger but that's windows only (as far as I can tell).

hmmm

---

### Post by tturrisi on 2006-11-19
[http://www.google.com/search?hl=en&q=linux+keylogger&btnG=Google+Search](http://www.google.com/search?hl=en&q=linux+keylogger&btnG=Google+Search)

---

### Post by ChadMMc on 2006-11-19
Also try as a search: [http://www.google.com/linux?hl=en&lr=&q=keylogger&btnG=Search](http://www.google.com/linux?hl=en&lr=&q=keylogger&btnG=Search)

---

### Post by bionnaki on 2006-11-19
well, google is a great search engine, but do you have any recommendations. I see only lkl and windows apps.

---

### Post by mlw4428@gmail.com on 2006-11-19
I would wonder if it would be possible to just write a script that looks at the output of the keyboard device (one of them in /dev?) and if it's more than zero stick it into a file? 

I'm very new to Linux, but I wonder if this would be a possible solution :confused:

---

### Post by tturrisi on 2006-11-20
> **bionnaki said:**
> well, google is a great search engine, but do you have any recommendations. I see only lkl and windows apps.
on first page of google search:
[http://www.securiteam.com/tools/6B00L0U95Q.html](http://www.securiteam.com/tools/6B00L0U95Q.html)

---

### Post by monkieie on 2006-11-20
I don't know if this is still any use to you - I have just stumbled across this request.

Concerning the logger, you can either check out this [whitepaper]("http://www.thc.org/papers/writing-linux-kernel-keylogger.txt") or otherwise look at [this download.]("http://linux.softpedia.com/get/System/Logging/THC-vlogger-10388.shtml")

---

### Post by MJN on 2006-11-21
<Duff info snipped> (sorry!)

Incidentally, how do you delete a post on here? The ALT text on the scissors says 'Edit/Delete' however I'll be damned if I can actually delete the entire post!

Mathew

---

### Post by dataw0lf on 2006-11-21
Use snoop.  It can monitor nearly anything that is represented by a file descriptor.

---

### Post by fakie_flip on 2007-05-28
> **dataw0lf said:**
> Use snoop.  It can monitor nearly anything that is represented by a file descriptor.

Where do you get snoop? This is what I found, but I don't think it is right.

[http://freshmeat.net/projects/bsnoop/](http://freshmeat.net/projects/bsnoop/)

---

### Post by fakie_flip on 2007-05-28
Currently there is no keylogger software that works with usb keyboards in Linux.

---

