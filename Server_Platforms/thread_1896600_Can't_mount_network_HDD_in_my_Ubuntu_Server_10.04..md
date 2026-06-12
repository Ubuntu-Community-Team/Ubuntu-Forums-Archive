---
title: "Can't mount network HDD in my Ubuntu Server 10.04.3"
date: 2011-12-17
forum: Server Platforms
---

### Post by darkod on 2011-12-17
Hi all.

It sounds like a very easy task, but it simply doesn't work for me or I am doing something way wrong. I have a WD My Book World Edition network hdd with a static IP. I recently purchased HP Proliant Microserver and installed it with 10.03.4 32bit server.
All the shares on both the WD and the ubuntu server work fine on my desktop and netbook, both in win7 and ubuntu desktop 11.10. The shares are open, no username/password needed.
The Connect To Server.. works just fine (I don't want them mounted as boot right now).

I am trying now to manually mount the WD on my ubuntu server to try copy something directly between them. But nothing I have seen on the net seems to work. I have ping to the WD all right.
I have tried:
sudo mount -t cifs -o guest //IP-WD/share /mnt
sudo mount -t cifs -o guest //IP-WD/share /media/temp (I have previously created the folder)
sudo mount.cifs //IP-WD/share /media/temp -o guest

I also tried with -o username/password combination. Nothing.
In ubuntu desktop I can mount it with command line as well as with Connect To Server...

Any ideas? Anything I need to check and report back? You would just need to tell me what, I don't have much experience with the server version.
The server is just a simple install with OpenSSH and Samba Server, nothing else. I am accessing it with ssh because it's headless, no problems to access it.
I want to learn this to allow me to copy directly. Thanks in advance.

---

### Post by BC59 on 2011-12-17
You can try through Storage Device Manager. Maybe you have to configure the options of the drive and set them to default.

---

### Post by darkod on 2011-12-17
> **BC59 said:**
> You can try through Storage Device Manager. Maybe you have to configure the options of the drive and set them to default.

Are we talking about a command line tool?

If I wasn't too clear in the first post, I am talking about a headless ubuntu server running in text mode only. No GUI and tools/programs that come with it.

I am actually not looking for the network HDD to be mounted all the time. Just a command to mount it when I need to copy something.

---

### Post by darkod on 2011-12-17
OK, I've got it. First of all, even though the share is open it seems you have to specify a username and password so I used the root user since that is the only user existing on the WD network hdd.
Second, it seems the parameter for the username depends on the exact syntax of the command:
For mount -t cifs you use -o username, but that didn't work even with the credentials of root.
However, what worked was:
sudo mount.cifs //IP/share /media/temp -o user=root,password=***

That worked straight away. My previous attempt with mount.cifs was with using the parameter username, not user. I should have looked at the man pages earlier really. :)

---

