---
title: "Hard disk compromised after a hacker?"
date: 2008-09-11
forum: Security
---

### Post by karrister on 2008-09-11
Hello all of you guys!

I have a problem. Well I got some newer hardware (finally!) and I decided to install Linux on it to have it as a server/general use computer. After a while of using it I wanted to test with Apache and dyndns to create my own server. It had been up for a few weeks and I was already happy that yay, I did it all by myself, with no problems! Until I noticed on one of my mounted NTFS-partitions is a folder called pamela...

Ok so here's how it is. I have 2 harddrives, one 40GB and one 500GB SATA. On the 40 I first installed XP, used it for a while and bought a half-tera HD. I made two partitions, called SATA and SATA-MEDIA. And then I decided to install as a second operating system Linux and didnt change any of the NTFS partitions I had. Then I started using Apache, and I used to log onto this Linux computer from my laptop with SSH to use irssi etc. I also used to every once in a while check my access log of apache. From the start already every now and then someone was trying to access on my page folder /SATA-MEDIA and it was a little weird to me, tried it myself on a browser and since it didnt work for me I didnt focus much on it.
But then one day I opened this mounted partition SATA-MEDIA and noticed in the root of the partition a file called I think XXX.folder (opened it in a text editor and during the first lines aleste was mentioned). Then I also noticed a folder called pamela. Now I started being really curious. It deffinately wasnt my creation!!!! Here's a list of the folder that I made:

yhteensä 1157 
-rwxrwxrwx 1 root root 197867 2004-07-29 02:31 _aleste.exe 
-rwxrwxrwx 1 root root 299 2008-06-19 23:06 Desktop.ini
-rwxrwxrwx 1 root root 5652 2008-06-19 23:08 Folder.htt
-rwxrwxrwx 1 root root 847920 2002-10-14 17:02 python22.dll
-rwxrwxrwx 1 root root 45103 2002-10-14 17:02 _socket.pyd
-rwxrwxrwx 1 root root 53292 2002-10-14 17:03 _sre.pyd
-rwxrwxrwx 1 root root 16384 2002-10-14 17:03 w9xpopen.exe

I panicked at first a little, I just tried to umount both of the SATA and SATA-MEDIA (cause the other SATA partition had some personal information, the XP partition wasnt so crucial but I dont have it mounted either anymore) and at first it didnt seem to work, I was still able access it. Then after a few tries I wasnt able to mount it back anymore. Booted to XP and it didnt show them either, only I was able access SATA and there were only a few files left.

So here's the main problem I have a question about: am I still able to recover both of the partitions entirely, or should I just forget about it and start from the scratch?


That was the most important thing I needed answer about, but also if you have tips about security with apache and this not happening again, you could let me know. Instantly afterwards I changed su so that it doesnt ask for the password of the user but password of root. So that like for instance if someone got my pass when I was logging to my ftp server, they could use it for su. But how did this happen?? And what is this thing that someone is all the time trying to access /SATA-MEDIA? How was anyone even able to know I have such a partition? What's going on?


Thanks guys for all the help! For sure if someone's gonna be able to help me with this it's worth at least one beer/coffee/whatever, if we just hopefully ever happened to meet somewhere! And that's a promise!


The Best greetings from already a little cold Finland,

Karri Kivelä

---

### Post by rogeriopvl on 2008-09-11
I'm not completely sure, but I think that you got those files and folders when you where using Windows. And probably you didn't see them in windows because they were hidden.

So don't worry too much about Ubuntu, because it's probably fine. Just run an antivirus over your windows partition.

---

### Post by cariboo on 2008-09-11
Those are windows executables thet you listed, they won't bother Ubuntu in the least. I would be worried about my windows installation though it does look like you have been infected with a worm of some sort.

Jim

---

### Post by karrister on 2008-09-12
Ok thanks guys!!!! Haha I never thought of that I could have gotten them thru Windows!


But do you know if there's a way for me to recover the two NTFS partitions on the half terabyte disk? Cause I cant access the files on them anymore, neither from Linux nor from Windows. They just like disappeared. The other one of the partitions has a few folders left but that's it!

---

### Post by karrister on 2008-09-12
NOW I'M SURE SOMEONE DID SOMETHING!

Look at this screenshot:

[IMG]http://karri.is-a-geek.org/misc/root-tmp.jpg[/IMG]


What do you make of that? I was trying to find something when I noticed that the tmp-folder appearead green like in the screenshot. That's EXACTLY what happened with the NTFS-partitions too - they also appearead green like that! And see the folders there in tmp? I cant even access them with my normal user!

What's going on in my comp?

---

### Post by rogeriopvl on 2008-09-12
> **karrister said:**
> NOW I'M SURE SOMEONE DID SOMETHING!

Look at this screenshot:

[IMG]http://karri.is-a-geek.org/misc/root-tmp.jpg[/IMG]


What do you make of that? I was trying to find something when I noticed that the tmp-folder appearead green like in the screenshot. That's EXACTLY what happened with the NTFS-partitions too - they also appearead green like that! And see the folders there in tmp? I cant even access them with my normal user!

What's going on in my comp?

I can't see any screenshot. And that doesn't mean anything, if those files on tmp where created by processes running with root privileges it's pretty normal that you can't access them.

---

### Post by EnGorDiaz on 2008-09-13
you have the win32.alespopen22.backdoortrojan you need to get a linux virus scanner to scan the partition then run in safe mode

---

### Post by EnGorDiaz on 2008-09-13
i just researched it on google i suggest you encrypt all your files and also get ipcop installed quickly after you do the scan

---

