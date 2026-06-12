---
title: "Change File Owner"
date: 2008-06-22
forum: Security
---

### Post by iSuck on 2008-06-22
Xubuntu 8.04 Hardy Heron
HP Pavilion dv6458se (Laptop)

I was trying to change the tags of mp3s, but my program wouldn't let me. The reason: the files were owned by "root". Sure as hell I won't use the Terminal to change the tags (I don't even know how).

Weird thing, these files were transferred from my XP, which could edit these files without a hassle. How did "root" own my files automatically?

Is there a way to change the owner of the files or at least a way that enables me to change the properties of the files without going into the terminal?

Many thanks in advance.

Sinc,
TN

---

### Post by The Cog on 2008-06-22
Probably, but I don't know it. I don't quite know how they could have ended up belonging to root either.

Ah - are they still on the Windows partition? If so, you can't change the ownership because NT doesn't store Unix file ownership and permissions tags. Copy them to your home partition and they should then belong to you.

FYI, to change the owner in command line, the command is:
sudo chown <username> <filename>
for instance,
sudo chown iSuck mysong.mp3

---

### Post by iSuck on 2008-06-22
Uhhh, I'm still new with terminal. What do I do here?

Many thanks in Advance.

Sinc,
TN

---

### Post by The Cog on 2008-06-23
Good start. You have hit a little problem with filenames that have spaces in them. When you said:
**sudo chown uffda 01 - Open Spaces.mp3**
it thought you were trying to change the ownership of 4 separate files, called 01, -, Open and Spaces.mp3.
The lazy way would be:
**sudo chown uffda *.mp3**
which would do all of them at once, * being a "wild card". To do just one, you need to put quotes round the name to hold the different parts together like this:
**sudo chown uffda '01 - Open Spaces.mp3'**
or alternatively, you can "escape" the spaces with backspace like this:
**sudo chown uffda 01\ -\ Open\ Spaces.mp3**
which doesn't look as pretty or intuitive. The reason I mention it is that a lazy way to enter a long filename (I like lazy) is to type the first few characters and then hit tab to invoke "filename completion". So if you type:
**sudo chown uffda 01**
and then hit the tab key, it will enter the rest of the filename for you.

Note that if a command is succesful, it won't print anything - it just goes back to the prompt. This is the Unix Way. It won't say "Yes I've done that, aren't I clever". It only says something if there's a problem.

You might prefer the output of **ls -l** which lists the files one per line with more details on each. The -l asks for a long print format, I think.

Actually, you might be able to tinker with the file ownership by right-clicking the icon and choosing Properties (or something like that) - I haven't ever actually tried Xubuntu, and I really should, and that's a nice clean-looking desktop you have there. But I'm pleased you are prepared to have a stab at the command line. It really is astonishingly powerful once you find your way around.

I am still a bit worried that these tracks might be on an NTFS partition, in which case you will not be able to change the owner, you will still get permission denied. If that's the case, can you post the output of the command mount and we'll see how the partition is mounted, what options etc. Or perhaps explain why you are trying to change the file tags.

---

### Post by iSuck on 2008-06-30
Dood,

You totally f_ rawked. Especially the lazy tricks, extra rawk. Many thanks.

Right now my internal HDD is built into 3 partitions. Windows | Xubuntu | Wibuntu (I'm genius, I know, you'll see why, haha). 55 GB, 55GB, 40GB, in order. NTFS, ext3, FAT32, in order. I did this configuration because I want to have my media files and personal documents shared between the two OSs. 

I did a little research and found out that Linux can't exactly read NTFS correctly. I saw that Linux read my Ex-HD with FAT32 without any problem. With that knowledge, I created my partitions the way I have it now. Really handy if you're dual-booting. Geez, you're more adv, I'm pretty sure you knew that.

The reason I want to change the properties of the file: I'm very anal with my music library. I have over 5000 songs with most of the songs correctly tagged (artist, album, blah blah). That 2% of incorrect tagging was due to the root file ownership. Then here we are.

Real quick, where's a good guide for a beginner like me to understand terminal? Better question: Where's a good guide for a beginner like me to understand Linux/Ubuntu (Coming for a guy that switched from a Windows platform)? There are too many sites out there for beginners, and I'm just a little overwhelmed.

Many thanks in advance, again.

Sinc,
TN

---

### Post by The Cog on 2008-06-30
I assume rawking is good. :)

As for resources, I can't think of a really good command-line intro because there are so many. I normally just google for a subject when needed. I think this is a very good introduction site though:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

The command line is a tricky thing though - you can get very deep into it if you want. Don't think there's a point you can reach where you know it all. Learn the bits you need to make your life easier and just remember there is always a lot more should you develop new needs. But it does make computing fun again. It makes your computer a "general purpose computer" rather than just the "applications platform" that windows is. If your interest is in computing rather than just running applications, that matters.

---

### Post by iSuck on 2008-06-30
rawk = rock
thus:
rawked = rocked
rawking = rocking

Again, thanks for the tips.

Sinc,
TN

---

