---
title: "Why I decided yesterday that Ubuntu is better than Windows."
date: 2007-11-08
forum: Testimonials &amp; Experiences
---

### Post by jmetal88 on 2007-11-08
I've had Xubuntu and Windows on my computer together for a few weeks now. Yesterday, I changed motherboards. Windows not only required me to re-activate, but it somehow lost all the drivers for all the cards I had installed previously, so I could not connect to the internet to re-activate, and I had to phone in.  The activation process went smoothly, but I think that was an unnecessary waste of six minutes of my time. Afterwards, I booted up to Ubuntu, and X wouldn't start. All I had to do was type in sudo dpkg-reconfigure xserver-xorg, go through a minute or so or configuration pages (all I did was pretty much hit tab and enter, since it detected everything correctly), and restart. After that everything picked up like nothing was ever wrong, and I didn't have to reinstall any drivers at all. That was a whole lot easier than having to call up Microsoft. 

Plus today I wanted to install bittorrent, so I opened a terminal and typed sudo apt-get install bittorrent, and it's on my computer now. I like the command line better than synaptic, 'cause I don't have to search for packages, I can guess and a lot of times my guesses are right. In Windows I'd have to open up a browser and go search for an installer.  I don't think I could go back to that unless I had to, now.

---

### Post by brownknight on 2007-11-08
First of all congratulation on your new adventure! 

> Plus today I wanted to install bittorrent, so I opened a terminal and typed sudo apt-get install bittorrent, .

I would recommend using aptitude instead of apt-get
sudo aptitude install XXXXXX

They said it manages dependencies better than apt-get and its actually easier to type (with the help of tab completion).

---

### Post by jmetal88 on 2007-11-08
Hmm, thanks for the tip, I might try that out.

EDIT: I tried that to get the bittorrent GUI, but the GUI appears to not be working. I can get the text based version to download files within the terminal, though.

---

### Post by ericesque on 2007-11-08
For a great bittorrent front end, grab Deluge from [http://deluge-torrent.org/downloads](http://deluge-torrent.org/downloads)  There is a deb for Ubuntu.  It's obviously not as light weight as command line, but it sure is fast.  I've noticed torrents coming down at least 2-3 times faster than uTorrent in windows-- and that includes Deluge for Win or Linux(cross platform).

---

### Post by karellen on 2007-11-08
> **ericesque said:**
> For a great bittorrent front end, grab Deluge from [http://deluge-torrent.org/downloads](http://deluge-torrent.org/downloads)  There is a deb for Ubuntu.  It's obviously not as light weight as command line, but it sure is fast.  I've noticed torrents coming down at least 2-3 times faster than uTorrent in windows-- and that includes Deluge for Win or Linux(cross platform).

I used ktorrent but after trying deluge I'd recommend it too

---

### Post by por100pre1 on 2007-11-08
Even if you guesses are right, check this command for searching packages:

```
aptitude search *package*
```

(no need to use sudo for seaching). Enjoy! :)

---

### Post by jmetal88 on 2007-11-09
Thanks again for the tips, everyone. Hmm... For some reason Deluge keeps closing itself out. Any idea what's going on there?

---

