---
title: "slow ssh"
date: 2005-11-30
forum: Server Platforms
---

### Post by jaykup on 2005-11-30
I'm transfering files between the machine in my profile, and a 333 AMD box, and its going extremely slow.. I'm managing around 600-700 KB!  If I get a file off of the 333, I can get around 1.8MB/s which is slightly better.. but still shitty.  I thought the processor was at fault, but its at a steady 25% on the 333.  All the network stuff is 10/100, with a 100mb switch

I've heard of encryption overhead... but this is ridiculous, the 333's hard drive is barely working!

---

### Post by LordHunter317 on 2005-11-30
Encryption overhead on a box that old will be substantial if you're still using AES.  Switch to blowfish for a substantial performance gain.

---

### Post by cactus on 2005-11-30
if you are doing local traffic, where encryption isn't *that* important, you could even use rc4, which is a stream cipher.

---

### Post by joselin on 2005-11-30
[QUOTE=LordHunter317]Encryption overhead on a box that old will be substantial if you're still using AES.  Switch to blowfish for a substantial performance gain.[/QUOTE]

How?

I have the same problem.

Regards.

---

### Post by J.C. Denton on 2005-11-30
[QUOTE=joselin]How?

I have the same problem.

Regards.[/QUOTE]
Use the -c option with scp:
```
scp -c blowfish file user@remotehost:/remotepath
```

Hope this helps :)!

---

### Post by grendelkhan on 2005-11-30
if it's just local traffic just use ftp, much less overhead and if it's local you don't have to worry about security.

---

### Post by jaykup on 2005-11-30
its actually an IPCOP box that i'm transfering files to, so i'd rather not set up an FTP server on it, but I will try blowfish.

btw, how can i do this when i click "places" then "connect to server" to select different encryption?

---

### Post by J.C. Denton on 2005-11-30
[QUOTE=jaykup]its actually an IPCOP box that i'm transfering files to, so i'd rather not set up an FTP server on it, but I will try blowfish.

btw, how can i do this when i click "places" then "connect to server" to select different encryption?[/QUOTE]
What client are you using?

---

### Post by jaykup on 2005-12-01
Breezy with gnome, by default that top task bar you can click Places, then Connect to Server

---

### Post by jaykup on 2005-12-06
though the command line blowfish encryption goes much faster, im getting average of 2.8 - 3 MB a second, which is much better than before.  Is this the limit of the 333?

Also, how can I change the encryption though nautilus when im browsing the machine though its ssh viewer?

---

### Post by J.C. Denton on 2005-12-11
[QUOTE=jaykup]though the command line blowfish encryption goes much faster, im getting average of 2.8 - 3 MB a second, which is much better than before.  Is this the limit of the 333?[/QUOTE]Most likely.  You also have to take into account other things like network speed, and disk I/O.

[QUOTE=jaykup]Also, how can I change the encryption though nautilus when im browsing the machine though its ssh viewer?[/QUOTE]I didn't see a way to do this in GNOME itself.  You could create $HOME/.ssh/config, and add the following:
```
Cipher blowfish
```
...which will default the cipher to blowfish.  Hope this helps :)!

---

