---
title: "Encrypt external/not primary hard drive for short duration"
date: 2014-04-20
forum: Security
---

### Post by josephellengar2 on 2014-04-20
Hi!

Here's a problem and I'm not sure if a solution exists.

I have a laptop with two hard drives in it. One I use as my primary and the other has a large amount of somewhat sensitive information on it. I have to send the laptop back to HP for repairs and I would prefer not to copy 400+ GB of data and clean the drive and then have to copy it back when I get the computer back. I can swap out my primary drive because I use my own drive and not theirs, but I cannot swap out the other drive.

So here's the problem:

Is there a way that I can encrypt the information on the second, sensitive drive, and then decrypt it permanently when I get the computer back? I don't want to encrypt my primary drive and I don't want to have to do some workaround like encrypt the data and when I get the computer back, decrypt it, copy it elsewhere, and then copy it back to the original drive. I've found a bunch of solutions like that online. I know that encrypting 400GB of data will take a while.

Anyway, any advice? I hope that I explained this well enough.

---

### Post by sudodus on 2014-04-21
I think such encryption and decryption takes longer time than ***copying the data to a new drive, that you keep at home***.


After that you can remove the information from the drive for example with ***hdparm*** according to this link
[URL="http://ubuntuforums.org/showthread.php?t=2124829"]
best way to wipe a drive[/URL]


When the computer returns you have two options:

1. Connect the new drive (and you need not copy anything back)
2. Copy the information back to the original drive

---

### Post by josephellengar2 on 2014-04-21
Thank you for the information. Actually, I just realized that I don't even own another drive that is large enough to store this data (only have one 250 GB external), so actually I have to encrypt it unless I were to purchase a new hard drive.

---

### Post by sudodus on 2014-04-21
These operations are really both safer (less risk of losing data) and faster if you have a 'third drive' that is big enough. There should be space enough to have both the original and the copy at the same time. If there is not space for the whole drive's data like that, there should be space for each individual file (encrypted and decrypted).

So you can use a method that encrypts each file (and then removes the original file). And when the computer returns, you can reverse the process. There are several encryption programs, for example gpg. Maybe there is a suitable tool for your particular case.

I'm not sure what would be the best for you. [COLOR=#ff0000]Let us hope someone who knows will read this and help you.[/COLOR]

---

