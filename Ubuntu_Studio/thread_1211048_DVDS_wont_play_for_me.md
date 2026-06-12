---
title: "DVDS wont play for me"
date: 2009-07-12
forum: Ubuntu Studio
---

### Post by jgomez2 on 2009-07-12
So I have installed Jaunty on my laptop and I went to 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

that walk through followed the steps. And for about 20 or so hours my DVD player worked for me just great. Then when I attempted to load disc 2 of a movie I was watching, all of a sudden now it does not want to play. The errors I get are as follows:

Movie Player: will not even acknowledge when I click load cdrom0

Dragon Player: same thing

GNOME MPlayer:Couldn't open DVD device:  to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://

VLC:   p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disk "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///dev/sr0'. Check the log for details.[/COLOR]






[COLOR=#000000]What is going on? What did I do/didnt do?
[/COLOR]

---

### Post by ajgreeny on 2009-07-12
Very odd!  Make sure the DVD disk is not damaged, so try it in another player, and also try the first disk again, if you haven't done so already, just to make sure it's not hardware failure.  Lastly reboot and try the second disk, first this time, to see if it will play.

Other than that, and you may already have tried it all, I can't suggest anything else.

---

### Post by lisati on 2009-07-12
Hmmmm.... maybe here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by jgomez2 on 2009-07-12
thanks for the advice. Ive tried all of that. I tried disk one, which does not work. I tried rebooting and then placing either disk in the tray, still doesn't read it.

---

### Post by jgomez2 on 2009-07-12
jgomez2@jgomez2:~/Desktop$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.


That is the error I got when trying region set :(

---

### Post by fwaokda on 2009-07-12
I can't play any DVDs either... using Jaunty and have 2 different drives I've tried through Totem.

---

