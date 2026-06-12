---
title: "Help:Natty Apt-get update hash mismatch"
date: 2011-05-22
forum: Server Platforms
---

### Post by RegistrationHate on 2011-05-22
I keep getting a very frustrating error after reinstalling 11.04 on a 64-bit server:```
W:  Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources   Hash Sum mismatch
```which follow```

bzip2: Data integrity error when decompressing.

```and occasionally```
W:  GPG error: http://security.ubuntu.com natty-security Release: The  following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>
``` Because I have limited experience with Ubuntu server I was sure to check around for solutions. I have tried the following:
Flushing the package lists:```

sudo rm -rf /var/lib/apt/lists/*
mkdir -p /var/lib/apt/lists/partial

```Changing ```
/etc/apt/sources.list
``` from us.archive to archive and back. I have linked the [contents]("http://bit.ly/mePa44").

After  reading several threads about ISP caching causing similar issues I  switched from my primary (roadrunner cable) to my secondary internet  connection (speakeasy ADSL) and problems persisted.

I have not  configured an apt proxy and in an effort to be sure I wasn't making a  stupid mistake I md5'd my download ```
MD5  (Desktop/ubuntu-11.04-server-amd64.iso) =  355ca2417522cb4a77e0295bf45c5cd5
``` it looks okay.

I  originally installed 11.04 on this system with the same disk so I'm  confused as to what is happening. I have tried using different CD's and  even installed of a USB. The memory test of the installer came back  okay. The box has two PCI NICs that are recognized and  functioning. The only package I have installed is openssh as this is a  headless box.

What makes this even more odd is that I have a  newly installed 32-bit 11.04 server with the same procedure on the same  network and it does just fine.

I hope I have been thorough enough  in my search and investigation that someone can point me in the right  direction. After reinstalling 3 times I am at a loss and I know 11.04  can run on my box without problem (as it did before the reinstall).Tonight  I'm going to reinstall with the built in interface unplugged and the  two NICs removed, I'm hoping this will prevent apt from bricking itself  during the install, which is the only think left I can think of.

I greatly appreciate any help on this issue as I have dumped hours searching for a solution.

I also looked around in syslog and didn't see anything.

I suspect the issue has to do with the nic despite it appearing to function properly I am unable to uncompress the archives in question on, my workstation, when they are downloaded on the sever but can successfully uncompress the same files when downloaded on the workstation.

[B]SOLUTION:
[/B]    I pulled both NIC's and enabled the integrated interface and it is all working. I wonder why they didn't work though...

---

### Post by dodo_ur on 2011-09-07
thank you alot it works for me :)

---

### Post by ludovic1 on 2011-09-19
Had the same problem here but only 1 nic installed, so it could not be it...but it turns out mine was a hard drive error! I did not think of this first since it was a brand new hard disc.

So i ran: **sudo touch /fsck** and ***rebooted*** my ubuntu desktop the problem went away

---

### Post by bigtel on 2011-12-01
sorry for sounding a bit stupid but what is an NIC..?

---

### Post by krige on 2011-12-13
> **RegistrationHate said:**
> [B]SOLUTION:
[/B]    I pulled both NIC's and enabled the integrated interface and it is all working. I wonder why they didn't work though...

I am having the same problem but I have only two integrated interfaces and no NICs. The "sudo touch /fsck" solution didn't work. Has anyone else found an alternative solution to this problem? 


> **bigtel said:**
> sorry for sounding a bit stupid but what is an NIC..?

NIC = Network Interface Card

---

### Post by pbulteel on 2012-05-07
Possibly a proxy? I had to change the proxy that I was going through at the company I work at. I assume that somehow the file I tried to download was corrupt and every time I requested it, the proxy said "I've got that!" and sent me a incomplete/corrupt file. 

If your ISP proxies connections, then they possibly have a corrupt file cached. How can you circumvent this? Maybe going through a different proxy or downloading the file in question yourself. Use an alternate connection (3G instead of LAN.)

It's a pain to troubleshoot because you never know what is the REAL cause of this.

-P

---

