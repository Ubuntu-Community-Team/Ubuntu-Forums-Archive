---
title: "large file transfers break up with ssh/ftp"
date: 2008-07-07
forum: Server Platforms
---

### Post by minuxx on 2008-07-07
Hi!

I have a big issue with transferring files in my local network.
My Server is an unbuntu 8.04 and my desktop is a winxp.
I have set up ssh with rsa keys and tried using WinSCP and Bitvise tunelier to transfer files.
WinSCP tells me randomly after starting to copy or even after finishing: Corrupted MAC on input. If the file was transferred it is always corrupted.
Tunnelier gives the same error message.
Then I resorted to a ftp server on my winxp and logged on from my ubuntu.
I switched to binary ( wanted to copy a 100MB *.sh file ) to my ubuntu. About 3/4 into the transfer I get the message
netin: Connection reset by peer


Downloading directly from the web to my ubuntu with wget e.g. works like a charm.
Also downloading from www to my winxp works flawless. I ran a couple of checksums tests and they all worked out.

I am really running short on ideas. Does anyone know by what this could be caused ?
Any help would be greatly appreciated!

---

### Post by windependence on 2008-07-08
You can use wget locally also.

-Tim

---

### Post by hyper_ch on 2008-07-08
or mount it with sshfs

---

### Post by minuxx on 2008-07-08
> **windependence said:**
> You can use wget locally also.

-Tim

That came to my mind a bit later also. Works like a charm.
Only downside to It I have to anonymously share my ftp folders and every time set a new one depending on the files I need.

sshfs sounds interesting. I am going to give that a shot later on.

But does anyone have an idea what the cause of my problem is in the first place ?

---

### Post by windependence on 2008-07-08
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/60764](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/60764)

Still researching.....

-Tim

---

