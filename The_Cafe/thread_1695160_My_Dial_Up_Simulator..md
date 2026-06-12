---
title: "My Dial Up Simulator."
date: 2011-02-25
forum: The Cafe
---

### Post by jjpcexpert on 2011-02-25
BEFORE YOU DOWNLOAD ANYTHING FROM ME:
 
```
sudo apt-get install sox wondershaper
```Kde users, before you download anything from me, get your GNOME running.
 
I have created a dial-up emulator.
 
The attachment containing what will be your ~/bin is here: [ATTACH]184454[/ATTACH].
 
You extract the contents of this tarball into your home ( **~** on the terminal) (it **must** come out as one folder), and then make ~/bin/dialup.bash executable (you should not have to).
 
I have tested it, and if you follow my instructions above, it will (repeat: ) WILL work.
 
K?
 
I know it's stupid, but it should hark an 21-year-old back to 1996.
 
It uses wondershaper to slow you down to 56kbit/s (plus compression gains makes it 133kbit/s) down and 33kbit/s up.
 
Those speeds familiar?
 
You type at a terminal emulator window:
 
```
~/bin/dialup.bash
```It makes a dial sound using sox.

---

### Post by Lucradia on 2011-02-25
Code for the bash file, if anyone needs to know:

```
#!/bin/bash
zenity --info --title="Modem Dialer (simulator)" --text="You would like to dial your net company."
zenity --info --title="Just doing it now..." --text="Simulated Dialer..." &
play ~/bin/tone.wav > /dev/null
kill %1
gksudo -m "Enter your password to connect to the Internet.\nNo, it will not be forwarded\nto some idiot in the kitchen." wondershaper eth0 133 33
gksudo wondershaper eth1 133 33
gksudo wondershaper eth2 133 33
gksudo wondershaper ra0 133 33
gksudo wondershaper ra1 133 33
gksudo wondershaper ra2 133 33
gksudo wondershaper wlan0 133 33
gksudo wondershaper wlan1 133 33
gksudo wondershaper wlan2 133 33
gnome-open http://www.google.com
```

Also note: You could have renamed it .sh instead of .bash, and told people to use sh ./filename.sh instead. Also note: Not everyone has gnome-open. (Which also means they may not have gksudo.)

---

### Post by Dustin2128 on 2011-02-25
why not just set up a simple dial-up proxy to your broadband connected desktop? Still, good work. And for the record, I had dial up until 2004 :(

---

