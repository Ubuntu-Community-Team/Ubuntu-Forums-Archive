---
title: "security for online audio converter tools?!"
date: 2014-06-06
forum: Security
---

### Post by zanoos800 on 2014-06-06
I'm using  an online service in order to convert my audio files [http://www.etyn.com/tools/audio-converter](http://www.etyn.com/tools/audio-converter) but I know nothing about the safeness of these tools.
If it's not safe so how can it harm my PC, however I believe MAC and Unix like OS are more secure, again I appreciate your help.

---

### Post by tgalati4 on 2014-06-06
The risk is low, but it is still a risk.  What file formats are you converting from and to?  Are there no linux tools available to perform the same conversion, locally, on your machine?

The main risk is putting malicious code in the header file (ID3) that could exploit a music player with a buffer overflow and then execution of malicious code.  Unless you run your music players as root, this is a low-risk issue because an ordinary user can't destroy the entire system without sudo/root privileges.

The bigger risk is collection of data that is shared with other parties.  You have no idea how that data can be used against you in the future.

---

### Post by zanoos800 on 2014-06-09
thanks for your nice information.
I convert mostly acc and amr (from my old cellphone;)) to mp3, I didn't search for a linux tool and locally ... no, it's just me and my browser.

---

