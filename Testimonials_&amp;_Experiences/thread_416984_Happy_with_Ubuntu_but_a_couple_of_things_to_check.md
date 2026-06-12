---
title: "Happy with Ubuntu but a couple of things to check"
date: 2007-04-21
forum: Testimonials &amp; Experiences
---

### Post by ZombiekE on 2007-04-21
Hello:

I switched to Ubuntu as my main operative system in Dapper and I must say I am very happy with the decision. I also would like to thank all those who make it possible. I try to make my small contribution my reporting bugs if possible.

I was using the Feisty beta and decided to do a clean install. Now with my clean Feisty Fawn I tried to do everything as if I were new to Ubuntu (I pretended as if I didn't know Automatix and other apps to make things easier). However I came across a couple of problems that I would not have expected, according to what I read at Ubuntu's website.

First: NTFS write/read. According to [Mounting Windows Partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions"):

> For NTFS partitions

Ubuntu 7.04 can read and write files on the NTFS drives commonly used by Windows. 

At least not in my case. I would not write in my Windows partition and the same happened with an external hard drive. So it seems that is not true for my computer. So I went on my own and installed ntfs-config, as they suggest with previous versions, and as I had in my beta and it worked. But why would a newcomer know that there is something called ntfs-config he/she must install? This is not friendly.

Then, I installed banshee, my favourite music player. Oh, surprise cannot play my mp3 files. However let's check what the [Ubuntu tour]("https://wiki.ubuntu.com/7.04Tour#head-8568011da129f88dc1d06521cfb21f8f49d09df9") has to say:

> Easy installation of multimedia codecs

Playing an MP3 or other media file just got a lot easier. If the required pieces are not yet installed, 7.04 will get the correct codecs for you, no more searching and no need for long and complicated instructions. 

7.04 did not get the correct codecs for me. That would mean that when I was going to open an mp3 file I would be asked if I wanted to install those codecs. Why do I have to know that my files are not playing because I don't have mp3 codecs? Solved just by going by myself to Add/remove applications and installed the codecs.

I don't know if I am the only one getting this bugs. If they are not bugs and this is supposed to work like this, I must say that the descriptions quoted are a bit misleading. Also sorry if there were options like the ntfs that were in some menu and I couldn't find them, but I tried hard to find them and it was no success, and I expected NTFS write/read in every unit by default.

---

### Post by 3rdalbum on 2007-04-22
Agreed, the first is somewhat misleading.

Disagreed with the second one. Banshee is not part of the default Ubuntu install. I believe it's not even in main.

---

### Post by ZombiekE on 2007-04-22
> **3rdalbum said:**
> Agreed, the first is somewhat misleading.

Disagreed with the second one. Banshee is not part of the default Ubuntu install. I believe it's not even in main.

I hadn't taken that into account. Thanks for pointing that out! So I guess I will restate the second part, not now as pointing out some "false claim" but a general proceeding for mp3s or other media:

It'd be nice if Ubuntu prompted users to install the codecs when any application tries to use mp3 files for example. I don't know if this is possible. But it would be more user-friendly.

Imagine you just install your favourite apps (whether it's in main or not) and don't install the codecs (like I did) and see that the player keeps skiping songs. Instead of figuring out on your own that you don't have the codecs, the prompt would be more of a dialogue between the computer and the user.

---

