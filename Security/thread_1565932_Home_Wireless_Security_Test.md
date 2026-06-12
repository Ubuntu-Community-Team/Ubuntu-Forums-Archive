---
title: "Home Wireless Security Test"
date: 2010-09-01
forum: Security
---

### Post by duds2008 on 2010-09-01
Hello. I set up WEP on my home router and successfully attacked and cracked the passwd. I no longer use WEP and strongly discourage people I know from using it, due to it's "flawed" design.
I enabled WPA2 on my router and performed a *slightly* more strategic attack on my own network using the aircrack-ng suite. I was able to capture the 4 way handshake within about 2 minutes. My question is: what precisely am I supposed to do with this .cap file (where the h/shake is kept) ??
I have read numerous *horror* stories about people paying BIG money to sites that offer the service of cracking the .cap file if you upload it to them and provide payment details. I have heard that john may help, but am not entirely sure how to code the command to perform the attack?? The man page for john is not *very* helpful?
All I need to do is decrypt the handshake. Any ideas? Thanks in advance. Dudley.

---

### Post by OpSecShellshock on 2010-09-01
So they'll crack the file after receiving your CC information? That's nice of them.

What kind of processing resources and time have you got? I guess you'd be trying to brute force the exchange after working backwards through the handshake to obtain the hash (if that's even possible/practical)? Or what's the plan? I think part of the new process for meeting the standard involves designing the AP such that even a weak passphrase would exceed most real-world acceptable thresholds for time and resource use.

---

### Post by BkkBonanza on 2010-09-01
You would probably have better luck researching this at [www.backtrack-linux.org](www.backtrack-linux.org)

And in particular this may help 
[http://www.backtrack-linux.org/forums/backtrack-howtos/68-password-cracking-guide.html](http://www.backtrack-linux.org/forums/backtrack-howtos/68-password-cracking-guide.html)

---

### Post by CharlesA on 2010-09-01
Eh, you could always use [coWPAtty]("http://www.wirelessdefence.org/Contents/coWPAttyMain.htm"), which is included in Backtrack.

The only real way to crack it that doesn't take insane amounts of time is using rainbow tables, but I believe they are SSID specific.

Anyway, you'd probably have better lucky asking over on the backtrack forums.

---

### Post by Ernie S. on 2010-09-19
In order to crack wpa/wpa2 you need to use a dictionary file or rainbow tables. Rainbow tables are faster, but also ssid specific. Dictionary files can be found in a number of places for download or you can create your own. I have heard of dictionary files being upwards of 5GB. The best place for more info on breaking wpa is the aircrack-ng docs [http://www.aircrack-ng.org/documentation.html](http://www.aircrack-ng.org/documentation.html). Or you could order wifu from the guys at offensive-security.org (They make Backtrack) It costs over $300 but it is an awesome course.

---

### Post by baseball9 on 2010-11-28
I wanted to audit my home wireless WPA network and have spent a lot of  time looking for a quality rainbow table. I was able to find a torrent  file for wpa psk-h1kari renderman. It's a .lzma.tar file. I'm using  backtrack 4 and which already had lzma installed in its newest version. I  began to decompress the file in terminal but near the end of the file  it gave an error message. Any one had any problems with decompressing  .lzma.tar files or wpa psk-h1kari renderman in particular. Any one know  of any other free rainbow tables?

---

### Post by spiky001 on 2010-11-28
Here is a link for wpa cracking down the bottom a section on cracking the handshake, the problem is the password has to be in the dictionary you use  [http://www.aircrack-ng.org/doku.php?id=cracking_wpa](http://www.aircrack-ng.org/doku.php?id=cracking_wpa)  or here for rainbow tables  [http://www.hak5.org/forums/index.php?showtopic=12708](http://www.hak5.org/forums/index.php?showtopic=12708)

---

