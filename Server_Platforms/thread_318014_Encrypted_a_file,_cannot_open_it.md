---
title: "Encrypted a file, cannot open it"
date: 2006-12-13
forum: Server Platforms
---

### Post by PartisanEntity on 2006-12-13
I have been trying to play around with en/decryption. I am somewhat familiar with the process, on my Windows machine I used to use PGP Desktop.

In Ubuntu (Dapper), I was able to import my keys, I used the Seahorse gui.

Today I wanted to encrypt a file just to see how it works. I selected a file called screenshot.png, I right clicked on it and selected 'encrypt'.

This brought up a window which allowed me to choose recipients, I chose myself, and then signed it too.

I was asked for my passphrase and then the file was encrypted and a new copy appeared on my desktop called screenshot.png.pgp

Now when I double click on screenshot.png.pgp I get a message saying: Couldn't display "home/me/Desktop/screenshot.png.pgp"

What am I doing wrong?

Thanks in advance.

---

### Post by PartisanEntity on 2006-12-14
Just a polite bump. thanks.

---

### Post by PartisanEntity on 2006-12-15
bump

---

### Post by PartisanEntity on 2006-12-16
bumptybump...

---

### Post by PartisanEntity on 2006-12-18
yet another hopeful bump.

---

### Post by etienne.navarro on 2007-01-20
The file screenshot.png.pgp is the GPG encrypted file, so of course you cannot open it.
There seems to be a problem with menu context and file extension, the file extension should be .gpg not .pgp. So rename the file to screenshot.png.gpg.
Then you can right click on the file and there should be an option to decrypt it.
Alternatively, use the commandline and issue
```
gpg -o screenshot.png -d screenshot.png.gpg
```

---

### Post by MJN on 2007-01-22
Huh?

He's already said he's using PGP, hence a .pgp extension sounds pretty reasonable to me! :confused:

Mathew

---

### Post by etienne.navarro on 2007-01-22
Yeah but he said he was using Seahorse which uses GnuPG so the extension would be .gpg.

When he right clicks on the file and selects "Encrypt", the file is encrypted using OpenPGP and the encrypted file is called **originalfilename.ext.pgp**. There is no context associated with a .pgp file so if the file is renamed to **originalfilename.ext.gpg** there is a context associated to decrypt it.

I believe this is a bug. What do you think?

---

### Post by MJN on 2007-01-23
Ah... Twas me that has made the mistake... Sorry. I read the bit about having used 'PGP Desktop' but not the fact that this was when they were using Windows...

---

### Post by PartisanEntity on 2007-01-23
Thanks for the info, since posting these questions I have reinstalled Ubuntu on a new hard disk, I have not gotten around to setting up Seahorse, once I do so I will give the en/decryption another go and post back.

---

