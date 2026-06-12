---
title: "Starting my own server..."
date: 2010-05-03
forum: Server Platforms
---

### Post by Chlorhydrikk on 2010-05-03
Hello ;)
I have an old a249.fr from HP that I would like to turn into a server.
Why? Well, I would be glad to download some essential files from anywhere I have Internet, and to host some rooms on games like Counter Strike...
I really don't know anything about servers. I just have an iso of Ubuntu Server Edition (the newest one) and my will :)
Hope you guys will help me ;)

---

### Post by CharlesA on 2010-05-03
Install the OS and go from there. It's not really that hard to set up a server.

I would suggest using SFTP/SSH to manage/transfer file to/from the machine.

As for hosting counter strike, I am not sure how that would work, but there are probably guides for doing that.

---

### Post by Halfbrazilian on 2010-05-03
If you need secure access to your files, you can use scp with a ssh server to transfer your files. It is as simple as typing

**sudo apt-get install ssh**

Once installed, use scp from the command line like this:

**scp localFileToCopy user@hostname:remoteLocationToCopyTo**

or

**scp user@hostname:remoteFileToCopy localLocationToCopyTo**

Also, you can use **ssh user@hostname** to connect in a remote command line if you simply want to manage your system.

If you like GUIs, you can use the "connect to server" option in Ubuntu, Filezilla on both Windows and Linux, or WinSCP in Windows.

Putty can be used for ssh sessions if you are using Windows.

As far as the Counter-Strike stuff goes, I never tried it. I would recommend Google.

---

### Post by Chlorhydrikk on 2010-05-03
Thank you ;)
I'm going to install it and then ask for any advanced help ;)

PS: Halfbrazilian, você fala português?

---

### Post by qstraza on 2010-05-03
> **Chlorhydrikk said:**
> Hello ;)
I have an old a249.fr from HP that I would like to turn into a server.
Why? Well, I would be glad to download some essential files from anywhere I have Internet, and to host some rooms on games like Counter Strike...
I really don't know anything about servers. I just have an iso of Ubuntu Server Edition (the newest one) and my will :)
Hope you guys will help me ;)
Llywelyn

I can help you with CS if you like, its really simple, all you need to do is download hlds from steampowered and run it with proper arguments. You need to open ports also, not only TCP but UDP too

let us know your progress.

---

### Post by dudumomo on 2010-05-03
Very interesting to start a server ! I did it 1 or 2 months ago and I really enjoy that !
(I've done several tutorial by the way, check my signature)

---

