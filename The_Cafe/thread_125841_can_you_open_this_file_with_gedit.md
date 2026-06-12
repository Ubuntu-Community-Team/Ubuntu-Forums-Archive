---
title: "can you open this file with gedit?"
date: 2006-02-05
forum: The Cafe
---

### Post by ice60 on 2006-02-05
hi, when i try and open this text file with gedit i get a popup saying it can't detect the charactor coding. i opened the file with OOo and every other letter was a # 

is this a local problem or do you have it too?
[http://wilderssecurity.com/attachment.php?attachmentid=174160&d=1139113710](http://wilderssecurity.com/attachment.php?attachmentid=174160&d=1139113710)

it seems to be fine for people using windows, i think it must a problem on my system :(

---

### Post by TechSonic on 2006-02-05
The file is currupt.

---

### Post by TTT_travis on 2006-02-05
The file appears to open for me fine on my mac

Statistics:
"Start time:	1/18/2006 5:56:02 PM"
"Completion time:	1/30/2006 11:50:56 AM"
"Attacks identified:	4"

Settings:
Notifications:
  ON
Blocking of the attacking computer:
  OFF
Invisible mode:
  OFF

Report:
UDP Port Scan;Attack via protocol UDP from address 192.168.1.254 to local port 4821 was successfully repelled.;1/21/2006 10:11:11 AM
UDP Port Scan;Attack via protocol UDP from address 192.168.1.254 to local port 4850 was successfully repelled.;1/21/2006 10:11:13 AM
UDP Port Scan;Attack via protocol UDP from address 192.168.1.254 to local port 4865 was successfully repelled.;1/21/2006 10:11:14 AM
UDP Port Scan;Attack via protocol UDP from address 192.168.1.254 to local port 4879 was successfully repelled.;1/21/2006 10:11:15 AM

---

### Post by ice60 on 2006-02-05
thanks, there's not much more i can say i have no clue what's going on.  :confused:

---

### Post by Jason_25 on 2006-02-05
vi can edit it just fine.


```

vi Report.txt

```

---

### Post by ice60 on 2006-02-05
thanks, Jason. i did manage to think about vim in the end, but there wasn't a problem with it so i didn't say anything. shouldn't gedit be able to open it? it's the output from kaspersky. KIS, i suppose it's called kaspersky (internet security ??) i think.

---

### Post by BoyOfDestiny on 2006-02-05
[QUOTE=ice60]thanks, Jason. i did manage to think about vim in the end, but there wasn't a problem with it so i didn't say anything. shouldn't gedit be able to open it? it's the output from kaspersky. KIS, i suppose it's called kaspersky (internet security ??) i think.[/QUOTE]

I've had gedit refuse to open files too... I ended up downloading ghex, I like it when a text editor can open anything (even if it shows garbage characters), but I don't run into that too often... oh well. :)

---

### Post by ice60 on 2006-02-05
[QUOTE=BoyOfDestiny]I've had gedit refuse to open files too... I ended up downloading ghex, I like it when a text editor can open anything (even if it shows garbage characters), but I don't run into that too often... oh well. :)[/QUOTE]
thanks, i have ghex too from when i was trying to extract checksums from torrent files, then i realised it's pointless if the torrent already does it :rolleyes: still i'd like to know how to do it if anyone knows though.

i didn't know gedit had problems with some files. i do plain to start using vim more because i want to start using my computer without a mouse so i don't use it so much.

---

### Post by ssam on 2006-02-05
sounds like its a binary file rather than ascii. maybe its unicode? you should probably file a bug at [http://launchpad.net/malone](http://launchpad.net/malone) or [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)

---

### Post by ice60 on 2006-02-05
[QUOTE=ssam]sounds like its a binary file rather than ascii. maybe its unicode? you should probably file a bug at [http://launchpad.net/malone](http://launchpad.net/malone) or [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)[/QUOTE]
thanks, how do i know if the same bug has been filed before? or should i just file it? i hope it's really obvious because i don't want to do the wrong thing and erase the whole server :-D

---

