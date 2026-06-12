---
title: "freshclam not working"
date: 2014-05-04
forum: Ubuntu Studio
---

### Post by shaun57661 on 2014-05-04
Hi. I have outdated definitions since the upgrade to 14.04, which I did in the Beta 1 days... freshclam is now noticeably not working, This is what I get after sudo freshclam in terminal

ClamAV update process started at Sun May  4 09:52:34 2014
nonblock_connect: connect(): fd=4 errno=22: Invalid argument
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
WARNING: Can't download main.cvd from 10
Trying again in 5 secs...
ClamAV update process started at Sun May  4 09:52:39 2014
nonblock_connect: connect(): fd=4 errno=22: Invalid argument
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
WARNING: Can't download main.cvd from 10
Trying again in 5 secs...
ClamAV update process started at Sun May  4 09:52:44 2014
nonblock_connect: connect(): fd=4 errno=22: Invalid argument
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
WARNING: Can't download main.cvd from 10
Trying again in 5 secs...
ClamAV update process started at Sun May  4 09:52:49 2014
nonblock_connect: connect(): fd=4 errno=22: Invalid argument
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
WARNING: Can't download main.cvd from 10
Trying again in 5 secs...
ClamAV update process started at Sun May  4 09:52:54 2014
nonblock_connect: connect(): fd=4 errno=22: Invalid argument
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
ERROR: Can't download main.cvd from 10
Giving up on 10...
Update failed. Your network may be down or none of the mirrors listed in /etc/clamav/freshclam.conf is working. Check [http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem) for possible reasons.

I really don't know how to use terminal functions except from copy-paste from sites posting code, or doing the apt-get update and upgrade commands. Any step-by-step help in achieving a fix of this problem would be helpful, as I am a complete dummy in this area. Studio has worked well for me for a few years of upgrades, but since 14.04 I have gone through a lot of bugginess. Is this just me, or is everyone else having trouble with this release?

thanks in advance,
Shaun

---

### Post by SeijiSensei on 2014-05-04
Open /etc/freshclam.conf with sudo in an editor.  What do you have for the DatabaseMirror directives?  In mine, I use
```

DatabaseMirror db.us.clamav.net
DatabaseMirror db.de.clamav.net
DatabaseMirror db.jp.clamav.net

```
That uses the US mirror first, but falls back to the German and Japanese mirrors if earlier ones are unreachable.

You have a strange entry in those errors:
```
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
```
That tells me you don't have the correct mirrors configured.

---

### Post by shaun57661 on 2014-05-05
> **SeijiSensei said:**
> Open /etc/freshclam.conf with sudo in an editor.  What do you have for the DatabaseMirror directives?  In mine, I use
```

DatabaseMirror db.us.clamav.net
DatabaseMirror db.de.clamav.net
DatabaseMirror db.jp.clamav.net

```
That uses the US mirror first, but falls back to the German and Japanese mirrors if earlier ones are unreachable.

You have a strange entry in those errors:
```
Can't connect to port 80 of host 10 (IP: 0.0.0.10)
```
That tells me you don't have the correct mirrors configured.

This is all Greek to me, and I don't have root privileges to edit the doc and save it. That is by default... I am not a terminal user, except for fetching updates and copy/pasting for installs of stuff not in Synaptic or Software Center, that isn't already packed in a .deb file. I hope that clears up any misunderstanding.

---

### Post by shaun57661 on 2014-05-05
Plus, I don't know how to find what you are asking for.... I'm borderline n00b, even though I've used Studio faithfully for several years. I just had things work without having to do all this crap.

---

### Post by SeijiSensei on 2014-05-05
Well, from the errors you posted, I don't see much hope unless you can edit freshclam.conf.  Try opening a terminal and running 
```
sudo nano /etc/freshclam.conf
```
You'll see a menu of commands at the bottom of the window.  The "^" means hold down the Ctrl key and type the associated letter. Ctrl-x (or Ctrl-X) means "exit" for instance.

Find the DatabaseMirror lines and edit them as I suggested.  Use Ctrl-X to exit and type "y" to save the file when prompted.

The other alternative is to try removing and reinstalling freshclam:
```

sudo apt-get purge clamav-freshclam 
sudo apt-get install clamav-freshclam

```

---

### Post by shaun57661 on 2014-05-05
your second soution worked! thank you!!! Now, let's mark this as SOLVED :)

---

### Post by SeijiSensei on 2014-05-05
You'll find it in **Thread Tools** at the top of the page.

---

