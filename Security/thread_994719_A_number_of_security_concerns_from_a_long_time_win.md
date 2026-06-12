---
title: "A number of security concerns from a long time windows user, now ubuntu newbie"
date: 2008-11-27
forum: Security
---

### Post by cshard on 2008-11-27
As I have recently installed Ubuntu and am still in the process of securing things, I have a few concerns with regards to how things work.

1. I've just recently installed Ubuntu and I am currently going through updating stuff, making things secure and all, and generally getting used to the OS. Now, if I wanted to encrypt the hard disk at this stage, am I still able to do so? 

I could of course, install truecrypt and use that to encrypt it, but I've heard that Ubuntu has an option to encrypt the partition when first installing using the alternate install CD. Short of reinstalling everything again, can I activate encryption even at this stage?

If I have to reinstall my Ubuntu OS because of the above, is there anyway for me to retain all my current updates and settings? My /home partition is on it's own separate partition already,and I haven't got much files in Ubuntu yet, so files are not a problem, but the initial update took an entire day just to complete, and I don't want to go through that again.

---------------------------------------

2. Now I know that windows is generally extremely sloppy and saves temporary files everywhere and anywhere. In addition it also uses a portion of the HDD as virtual memory, which is used to supplement the ram when loading programs, and as a scratch disk for certain graphic applications. I'm not sure, but I assume something similar is done during video and audio playback to improve performance.

Does Ubuntu do such things? For example, if I opened a large file, say a movie file, that was stored on another/external HDD, would the file, or parts of it be cached in the /root temporarily to improve performance, or would it simply be read from wherever it was stored, maybe cached only in that same disk drive it came from?

---------------------------------------

3. While I understand that Linux is resistant to Windows based viruses, I would like to ask that if I have several windows NTFS/FAT32 partitions in my PCs, should I be concerned about possible infections to the files in those harddisks? Suppose I get an attack while using Ubuntu, and subsequently, I boot into windows later in the day. Would I be at risk from that virus?

If a HDD is present, but unmounted, it's also still listed when I check all my drives. Is there a way to hide them from view while in Ubuntu, until I want to access them for certain? 

---------------------------------------

4. When I first installed Ubuntu, there was already an included BT client + IRC Client. How much do these clients differ from an equivalent WinXP one, such as BitComet and MIRC? 

Does the BT client encrypt the connection and is there any additional functionality unique to Linux versions? What other alternative clients are recommended for use in Linux?

Does the IRC client support SSL connections out of the box, or do I have to install additional plugins?

Is there anything other than using a secure SSL connection that can be done to protect me when using any Ubuntu IRC client? for example, can I use Privoxy to protect my IP while using an IRC client?

---

### Post by weemadarthur on 2008-11-27
> 2. Now I know that windows is generally extremely sloppy and saves temporary files everywhere and anywhere. In addition it also uses a portion of the HDD as virtual memory, which is used to supplement the ram when loading programs, and as a scratch disk for certain graphic applications. I'm not sure, but I assume something similar is done during video and audio playback to improve performance.

Does Ubuntu do such things? For example, if I opened a large file, say a movie file, that was stored on another/external HDD, would the file, or parts of it be cached in the /root temporarily to improve performance, or would it simply be read from wherever it was stored, maybe cached only in that same disk drive it came from?Yes, Linux uses a swap partition for the same purpose. It is generally used to provide applications with more memory than is physically available. The installer should have created a swap partition for you if you chose the default partition options during install. 
More info at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq).__

> **cshard said:**
> 
4. When I first installed Ubuntu, there was already an included BT client + IRC Client. How much do these clients differ from an equivalent WinXP one, such as BitComet and MIRC? 

Does the BT client encrypt the connection and is there any additional functionality unique to Linux versions? What other alternative clients are recommended for use in Linux?

Does the IRC client support SSL connections out of the box, or do I have to install additional plugins?

Is there anything other than using a secure SSL connection that can be done to protect me when using any Ubuntu IRC client? for example, can I use Privoxy to protect my IP while using an IRC client?

As far as functionality goes, these clients should provide every feature you are used to on your Windows box. 

The Bit torrent client can encrypt connections, however this may not be enabled by default. You will need to read the docs for the client to figure out how to enable encryption.

Similarly, while the IRC client supports SSL connections out of the box, it may not be enabled by default.

---

### Post by hyper_ch on 2008-11-27
> **cshard said:**
> 1. I've just recently installed Ubuntu and I am currently going through updating stuff, making things secure and all, and generally getting used to the OS. Now, if I wanted to encrypt the hard disk at this stage, am I still able to do so?
Yes, there are ways to do that but it's not simple...

> **cshard said:**
> 
I could of course, install truecrypt and use that to encrypt it, but I've heard that Ubuntu has an option to encrypt the partition when first installing using the alternate install CD. Short of reinstalling everything again, can I activate encryption even at this stage?
Depending on what you want, you can encrypt individual partitions and mount them almost anywhere in the filesystem... but full disk encryption will be not as simple.

> **cshard said:**
> 
If I have to reinstall my Ubuntu OS because of the above, is there anyway for me to retain all my current updates and settings? My /home partition is on it's own separate partition already,and I haven't got much files in Ubuntu yet, so files are not a problem, but the initial update took an entire day just to complete, and I don't want to go through that again.
The downloaded .deb files are in /var/cache/apt/[something]... so you can just save them and also put them back later again - this means you don't have to download them again but install them. All user settings are in your homefolder... system-wide settings in /etc.
Also note: that when you want to encrypt using luks/dm-crypt you will need to get all the data off of your home partition, encrypt it, then put it back on - so you will need at least equal space somewhere of what your /home partition is using.

> **cshard said:**
> 3. While I understand that Linux is resistant to Windows based viruses, I would like to ask that if I have several windows NTFS/FAT32 partitions in my PCs, should I be concerned about possible infections to the files in those harddisks? Suppose I get an attack while using Ubuntu, and subsequently, I boot into windows later in the day. Would I be at risk from that virus?
Ubuntu will download and process the files containing malware.. however it will not do damage to it.
Yet if you download a virus infected file with ubuntu, put it on a ntfs drive... then you boot windows and open the file from there, it can (and probably will) cause damage... keep using antiviruse etc. on windows to be safe.
But an attack by a third party on your ntfs/fat32 drives is very unlikely.

> **cshard said:**
> 4. When I first installed Ubuntu, there was already an included BT client + IRC Client. How much do these clients differ from an equivalent WinXP one, such as BitComet and MIRC? 
depends... what is bitcomet and mirc like?
You have multiple bt clients and irc clients in the repos... I personally use rtorrent as bt client (it's CLI only but it's very powerfull and very light on resources and once you get used to it it's great, because you can run it in "screen" and disconnect the session and reconnect it from anywhere in the world where you have ssh available).
And I like konversation as irc client.

---

### Post by steveneddy on 2008-11-27
In a nutshell on security, you should be OK with the stock install of Ubuntu as far as security goes unless you are running a server open to the internet.

---

### Post by digitalbrain on 2008-11-27
@cshard
There are useful threads about security on the forum but I just want to add a little thing. If you do not run the codes coming from _untrusted_ sites (I mean programs and scripts) and always run programs and codes from trusted, official servers, plus, if you use a strong password then you will be 99.9% safe. And also if you are behind a router, then you won't need a firewall. :guitar:

---

### Post by cshard on 2008-11-27
**@weemadarthur:** So in other words, instead of Windows' messy method of having temp files strewn all over, we only have a single pre defined partition where all files go in and out of?

Out of curiosity, if I were to resell that HDD with the swap partition on, how likely is it that a person analysing the disk can get back any photos, documents, music, videos, in fact anything at all, from the swap partition?

I'll check the options out in the default clients then about SSL and encryption then.

**@hyper_ch:** Ideally I would need to reinstall everything then? I'm pretty sure Truecrypt has an option to encrypt the HDD when it is first installed. I'm just wondering which one protects the HDD better.

I have more than enough HDD space right now, so backing it all up will be no problem whatsoever.

While in Ubuntu, I don't intend to mount any windows HDDs if I'm not using them so I suppose that should suffice as security. I'm more interested in knowing if I can hide my HDDs from the OS, until I want them to be detected.

Well, as long as the Linux flavours of such BT and MIRC have all the same functions, I'm fine with that.XD

**@steveneddy:** Nope, not running a server yet, although I might want to set up a file server for my family in future.

**@digitalbrain:** By default, I'm already extremely paranoid about any website that gets flagged as harmful, and I have multiple layers of protection in Win XP. As for Ubuntu, I'm already double and triple checking stuff I install and click on, plus I don't go to sites that have a high risk factor. I guess I have that part covered already. XD

---

### Post by falcon61102 on 2008-11-27
> **cshard said:**
> Out of curiosity, if I were to resell that HDD with the swap partition on, how likely is it that a person analysing the disk can get back any photos, documents, music, videos, in fact anything at all, from the swap partition?


Theoretically it's possible for someone to use some data recovery tools out there to extract information off your SWAP partition if it was not cleaned out prior to shutdown.  A simple way to eliminate that from ever happening would be to wipe the drive before selling it.  All data and partitions can be erased and depeding on the method, you can completely fill the drive with bogus, random data that over-writes anything that might have survived the wipe.

---

### Post by hyper_ch on 2008-11-28
> **cshard said:**
> Ideally I would need to reinstall everything then?
Read my response again...

> **cshard said:**
> I'm pretty sure Truecrypt has an option to encrypt the HDD when it is first installed.
Not on  linux

> **cshard said:**
> I have more than enough HDD space right now, so backing it all up will be no problem whatsoever.
You should always have backups ;)

---

### Post by cshard on 2008-12-01
@hyper_ch: Well, the impression I got was that full disk encryption is difficult, but not impossible once Ubuntu is fully installed. During my earlier research, I read a thread posting that one could encrypt the HDD during Ubuntu's install process using the alternate text installer disk, but it didn't really explain much. I can't recall which thread I read that in either...

Given that info, and since you mentioned some difficulty in doing the encrypting after installing, I assumed that a reinstall would do the trick with much less problems. I'll see if I can find a topic on disk encryption later, but I'd be thankful if you could suggest some keywords or a link I could use in my search. ^_^

You mentioned something about luks/dm-crypt - is this the name of a Linux disk encryption software package?



@falcon61102: Sorry for the late reply. In any case, basically a full disk wipe should be sufficient? 

I mean, I understand that current HDD forensics can find data from ages ago, despite multiple disk wipes, and I suppose that method's probably prohibitively expensive as well, but will a file shredder program do the trick?

---

### Post by falcon61102 on 2008-12-01
You can get some decent programs out there that will wipe and fill the drive with bogus data and many are open source.  Honestly, most people don't have the time or resources to do the extensive work it requires to really pick apart a previously wiped drive for data bits and then rebuild a file structure.  It takes a lot of work.  If you are really worried about your data being compromised, don't resell the drive.

---

### Post by hyper_ch on 2008-12-02
> **cshard said:**
> @hyper_ch: Well, the impression I got was that full disk encryption is difficult, but not impossible once Ubuntu is fully installed.
It is possible... however it requires quite some work and the only option I see is if you rent a server in a datacenter and you want to have it encrypted...

> **cshard said:**
> During my earlier research, I read a thread posting that one could encrypt the HDD during Ubuntu's install process using the alternate text installer disk, but it didn't really explain much. I can't recall which thread I read that in either...
You can... and it's simple... and I wrote an extensive howto on that.

> **cshard said:**
> You mentioned something about luks/dm-crypt - is this the name of a Linux disk encryption software package?
simply said: yes :)

---

### Post by cariboo on 2008-12-02
I think there is a bit misunderstanding about the swap partition. The swap partition is ithe same as pagefile.sys in windows, it is only used if you need more ram then there actually is to run programs.

Temporary internet files go into .mozilla which is a hidden directory in /home/<user>. Other temporary files go to /tmp which is in the root directory of the file system.

For more info on the Linux file system, have a look here:

[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

If you want to administer the system properly, you should know where all the files are located.

Jim

---

### Post by cshard on 2008-12-02
@falcon61102: Noted. Thanks for the clarification. I've always wanted to get that nagging concern cleared anyway.

@hyper_ch: I'll go do a check on that thread and that software you mentioned. I'm still not very clear on which method would likely be more efficient, timewise, but I guess I'll go test it out later.

@cariboo907: Thanks for the link. I'll go look through it

---

