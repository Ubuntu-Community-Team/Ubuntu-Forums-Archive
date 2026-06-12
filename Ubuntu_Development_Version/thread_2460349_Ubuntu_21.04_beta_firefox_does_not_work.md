---
title: "Ubuntu 21.04 beta: firefox does not work"
date: 2021-04-08
forum: Ubuntu Development Version
---

### Post by pwowqxbirt on 2021-04-08
Greetings. I updated the question to better describe the problem: 
updated Ubuntu and the beta version works fine. However, Firefox does not work. It looks like it is launching but no windows open. I tried reinstalling it. Did not work. I can launch it from terminal though. Any ideas how to fix this? Thank you for your help
[B]
SOLVED:[/B]
I removed FF again. This time I also removed everything related to FF (archive files, symbols, everything I could find!), and reinstalled everything back and IT WORKS! As  algreeny suggested something, somewhere must have been corrupt.   **Thank you for everyone. Learned heaps again!!**

---

### Post by QIII on 2021-04-08
I assume that by "Ubuntu 21 Beta" you mean the development version of 21.04?  Moved to Ubuntu Development Version.

I have removed your .pdf attachment.  If you have text to present that is too long to contain between code tags (see below), please use [Ubuntu Pastebin]("https://paste.ubuntu.com/") to post it as plain text so that you are not asking the community to open a potentially malicious file type.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by pwowqxbirt on 2021-04-08
thank you! I tried the pastebin, hope I got I right

---

### Post by dino99 on 2021-04-08
Looks like a latin fonts encoding issue. Which language is set on that system ? Try one without dot or accent above letters (like English) for testing firefox.

---

### Post by pwowqxbirt on 2021-04-08
Thanks. I changed it into English. Still not working. However, the terminal error message is gone.

---

### Post by guiverc on 2021-04-08
There is no Ubuntu 21 release, so please be exact in future.

Assuming it's 21.04, I'd look for clues in /var/crash/ (ie. is there a crash file).

If a crash file is present, please submit the bug report  (it'll contain useful details in finding a bug if one is found, or even for us to get clues).  To submit the bug use

```
ubuntu-bug /var/crash/*[filename]*.crash
```

where you'll need to replace *[filename**]* with the correct name, and thank you for helping to test Ubuntu 21.04, and helping to make it better on it's release.

---

### Post by pwowqxbirt on 2021-04-08
Thank you. Corrected the title. Did not find any crash files. The terminal gave me this: 
> Gdk-Message: 10:34:25.948: Unable to load openhand from the cursor theme
Gdk-Message: 10:34:25.948: Unable to load
5aca4d189052212118709018842178c0 from the cursor theme

###!!! [Parent][RunMessage] Error: Channel closing: too late to
send/recv, messages will be lost

---

### Post by ajgreeny on 2021-04-08
Try temporarily renaming the hidden ***.mozilla*** folder in your home and see if FF will now start using a completely new profile and configuration.

It may be that having previously used the beta version of FF you are now trying to start an instance of a lower numbered FF version which can cause difficulties with some applications, thunderbird being the most obvious one that I can think of at present. A new profile may be all that is needed and could be a lot simpler than troubleshooting this sort of problem.

---

### Post by pwowqxbirt on 2021-04-08
Thank you. I agree this must be a relatively simple problem. The problem is that I know very little of Ubuntu, and it was really quite unfortunate that I installed the beta version in the first place. Anyway, I tried renaming the file. Unfortunately it did not work. Tried also creating a new profile on FF. Did not help either.

---

### Post by dino99 on 2021-04-08
To increase your ubuntu's knowledge, glance at possible error(s) using this command into a terminal:
> journalctl -b

warnings are listed as yellow lines (info, quite harmless)
errors are the red lines

This can help you solve such an issue. Note that i can't find something related to 'openhand' inside the ubuntu's repositories: so the cursor theme seems a non genuine one; have you selected a third source for it ? Better use the ones provided by ubuntu if you cant deal with related error. Go to the 'system settings' menu (top right menu bar icon) and swith the actual theme to an other.

---

### Post by pwowqxbirt on 2021-04-08
nothing weird that I could see. I only use the ubuntu updates.

---

### Post by pwowqxbirt on 2021-04-08
Did not see anything yellow or red.

---

### Post by corradoventu on 2021-04-09
Message seems refer to a problem with cursor theme, did you try to change cursor theme?  you can do it easily with gnome-tweaks.

---

### Post by pwowqxbirt on 2021-04-09
No I did not. How can I change that. Newbie instructions, please!

---

### Post by corradoventu on 2021-04-09
in gnome-tweaks (you can install it from Ubuntu software) select 'appearance' and change the theme for cursor. the standard one is Yaru.

---

### Post by pwowqxbirt on 2021-04-10
Thanks for the tip but it did not help. FF does not open

---

### Post by ajgreeny on 2021-04-10
I wonder if your install of FF is corrupt in some way; it doesn't happen often but is not unknown.

So try totally removing FF from your system with ```
sudo apt purge firefox
``` then remove the firefox package from ***/var/cache/apt/archives*** if it's there and finally reinstall firefox as usual with ```
sudo apt install firefox
```

---

### Post by pwowqxbirt on 2021-04-10
I found this file  ///var/cache/apt/archives/firefox_87.0+build3-0ubuntu2_amd64.deb 
However, I cannot find a way to remove it.

---

### Post by corradoventu on 2021-04-10
Try ```
sudo apt autoremove --purge
```

---

### Post by deadflowr on 2021-04-10
> I found this file ///var/cache/apt/archives/firefox_87.0+build3-0ubuntu2_amd64.deb
However, I cannot find a way to remove it.
Use apt clean or apt autoclean to clean out the cache.
```
sudo apt clean
```
cleans the whole archives.
```
sudo apt autoclean
```
wipes out only the older versions of packages,
but keeps the latest.

---

### Post by pwowqxbirt on 2021-04-11
Thank you! I did that. Now, when I try open FF a CLOSE FF -window opens after a short while. However, that window has only the title and a frame, nothing in the middle but my screen picture and the window vibrates. Looks really odd.

I think I thank you all for help and give up.

---

### Post by corradoventu on 2021-04-11
Provare con versione Firefox Nightly?
[https://www.mozilla.org/it/firefox/channel/desktop/](https://www.mozilla.org/it/firefox/channel/desktop/)

---

### Post by pwowqxbirt on 2021-04-12
Grazie. Di nouvo una versione beta :shock:  ....grazie ma no grazie...

---

