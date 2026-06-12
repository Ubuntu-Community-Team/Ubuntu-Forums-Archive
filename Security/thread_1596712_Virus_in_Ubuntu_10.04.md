---
title: "Virus in Ubuntu 10.04"
date: 2010-10-14
forum: Security
---

### Post by EarendilTheMariner on 2010-10-14
VIRUS IN UBUNTU 10.04

This is my first post here, and I don't know much about Linux or Ubuntu.

I'm pretty sure I got a virus from a hacker while playing Yahoo chess back in August 2010, using Ubuntu and Linux.  Right after I beat him twice in a row, the hacker was really pissed and told me he gave me a virus, as revenge.

But I didn't take it seriously, because I thought Linux systems were invulnerable to malware.

Moments later Yahoo Chess crashed, and the next day, and ensuing days, I noticed that my web browser, Mozilla FireFox's window, would completely transform into something completely unreadable with all kinds of weird lines, so the whole window looked like a garbled mess.  But if I refreshed the browser, it would disappear.  But it often came back in the ensuing weeks, especially if I spent more than 30 to 60 mins on the same website, and recently, refreshing the screen doesn't work any more.

I also noticed that sometimes when on a website, the text would get garbled in some spots with weird characters, but like before, refreshing the page usually helped, until recently.  Also, the virus seems to have spread to Adobe Acrobat Reader and my desktop.

I know I should have done sth to fight the virus, but I was waiting for my guru, my brother to help me, because I'm so unfamiliar with Linux.  But he's 3,000 km from me and the remote host doesn't work in the Ubuntu environment, and I'm used to Windows, and didn't have time to deal with such a serious issue.  Neither does he, even though he's the one who built and customized my Linux computer.  But out of stupid laziness, I kept using my Linux computer to go online, because I wanted to keep my other computer offline.

My Linux computer is a dual boot computer with Windows XP installed on the same hard drive, but I was warned not to use Windows, because it's an old computer with limited speed, and there's no anti-virus software installed in Windows.

However, I have another computer, a customized multimedia computer, faster and with several huge hard drives with lots of memory, and it uses Windows XP.  I'm using it now to figure out how to deal with the virus on my Linux computer, but not getting anywhere.

I figure I should download ClamTK on my big multimedia computer and put it on a flash drive, then boot up my Linux computer with Ubuntu and install it, so I can do a scan for viruses.  Is this a good idea?

I also heard there's a website where you can get a free online virus scan for Ubuntu, but I can't find it.

I need help.

---

### Post by cariboo on 2010-10-14
You probably have a corrupted firefox profile. Press Alt-F2 and type:

```
firefox -ProfileManager
```

and create a new profile, try it for a while, if it solves the problem you can transfer your bookmarks from the old profile

---

### Post by rookcifer on 2010-10-14
*Yawn*  Not a virus.  More likely is either a corrupt profile (like the guy above said) or perhaps a hardware problem (video card).

---

