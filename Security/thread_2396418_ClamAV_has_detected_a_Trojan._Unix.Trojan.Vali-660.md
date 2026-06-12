---
title: "ClamAV has detected a Trojan. Unix.Trojan.Vali-6606621-0"
date: 2018-07-15
forum: Security
---

### Post by arwickkronos on 2018-07-15
I recently ran ClamAV and scanned the Filesystem Directory , which ended up detecting a gnome-rr-debug as a Trojan. I updated the virus definitions and also changed the settings to scan files larger than 20MB and Recursively Scan. This is what the Log says:


Found 1 possible threat (114139 files scanned).

/usr/lib/x86_64-linux-gnu/libgnome-desktop-3-17/gnome-rr-debug          
-------------------------------------------------------------------------------------------------------



Should I do something about this? It seems like a false-positive but I could'nt find much about the file on the internet. I've also checked the file with VirusTotal and such and it seems like only ClamAV considers this threat. I'm new to Linux, so it would be great to get some insight on this.

Thank you.

---

### Post by &amp;KyT$0P# on 2018-07-15
Step 1 is to run this command to determine which package installed that file -
```
dpkg-query -S /usr/lib/x86_64-linux-gnu/libgnome-desktop-3-17/gnome-rr-debug
```
It should probably say it's from [FONT=Courier New]libgnome-desktop-3-17[/FONT] .

Assuming it is, and your system is up to date and you have libgnome-desktop-3-17 version 3.28.2-0ubuntu1 installed, the SHA384 checksum of this file should be -
```
$ openssl dgst -sha384 /usr/lib/x86_64-linux-gnu/libgnome-desktop-3-17/gnome-rr-debug
SHA384(/usr/lib/x86_64-linux-gnu/libgnome-desktop-3-17/gnome-rr-debug)= 1a95ad861f056621770ff90301e35d6e8f79790747cf9303368c8dbf1c0413ac0e7b186397a7e2bb22a4e4363bb43c58

```
Does yours match that?  If so, it's a false positive.

By the way, scanning your entire file system with ClamAV does nothing for security of Ubuntu.  Please read [this post]("https://ubuntuforums.org/showthread.php?t=2337052&p=13546076&viewfull=1#post13546076") for your own safety.
For info on how to actually secure Ubuntu, [see this post by DuckHook]("https://ubuntuforums.org/showthread.php?t=2184758&p=12833795&viewfull=1#post12833795").

---

### Post by arwickkronos on 2018-07-16
I've confirmed the issue, Thank you. It was a False-Positive, I've checked with the commands you gave me and they were the same.

---

### Post by freddie.goodman on 2018-09-11
The "answer" that you replied to is not valid and should not be trusted -- not because it is wrong, necessarily, but because it is not valid. Why? Well, let me give you an example:

>be hacker
>spread virus
>search forums until someone asks about virus
>tell user it is okay and provide hash to seem legit
>laugh as user clicks [solved]
>reap benefits as every other user that finds the forum gets duped as well
>raep moar computers at will
>???
>PROFIT!

You should never trust a hash unless you find it on the company's website. Technically, you shouldn't trust a hash unless you meet a verified dev in person and get it from them face-to-face. But, for our purposes, the official website will have to do. If you're really paranoid (smart?) you'll go to a library or friend's house and check the hash on the website using their computer.

---

### Post by &amp;KyT$0P# on 2018-09-11
freddie.goodman, where on the [official website]("https://packages.ubuntu.com/bionic-updates/libgnome-desktop-3-17") is there a hash of this file?

---

### Post by archphoenix on 2018-09-23
You can download the package from your link, extract and check.
Package contains a file "md5sums" with checksums of files it contains.

---

### Post by &amp;KyT$0P# on 2018-09-23
> **archphoenix said:**
> You can download the package from your link, extract and check.
Package contains a file "md5sums" with checksums of files it contains.
Thanks archphoenix.

To expand on this -

1) download the .deb on another computer, extract it

2) extract [FONT=Courier New]control.tar.xz[/FONT]

3) get hash from [FONT=Courier New]md5sums[/FONT] file

4) compare with output of -
```
openssl dgst -md5 /usr/lib/x86_64-linux-gnu/libgnome-desktop-3-17/gnome-rr-debug
```

---

### Post by webmiester on 2018-09-24
What concerns me here is that clamAV was able to detect a "Unix virus".  People say that viruses for linux doesnt exist yet, so why does ClamAV have a definition for one?

---

### Post by TheFu on 2018-09-24
> **webmiester said:**
> What concerns me here is that clamAV was able to detect a "Unix virus".  People say that viruses for linux doesnt exist yet, so why does ClamAV have a definition for one?

There are thousands of Unix viruses, so that is incorrect information.  Read the sticky threads at the top of the Security sub-forum here.

---

