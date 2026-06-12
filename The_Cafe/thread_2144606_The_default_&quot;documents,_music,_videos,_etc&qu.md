---
title: "The default &quot;documents, music, videos, etc&quot; folders suck in all operating systems"
date: 2013-05-12
forum: The Cafe
---

### Post by D7Gd on 2013-05-12
I have worked with computers for about 15 years now and there is something that I just have to get off my chest. Every single time that I have made use of the default  "documents, music, videos, etc" folders in either Windows or GNU/Linux, I have regretted it later.

The primary reason for it is that for some peculiar reason, those default folders always get filled with **random garbage** by various programs and I have to spend a great deal of time cleaning up the mess if I want to migrate from one OS to another.

Moreover, by default, programs constantly scan, index, and probe those folders. They lock certain files for no reason and prevent me from backing up the entire folders. It's just a complete nightmare and gets worse over time.

Because of this, whenever I do a clean install of any operating system for myself, I just create an another partition where I keep all my personal files and I've decided to tell those default folders to go eff themselves and ignore them completely.

Is it just me or does anyone else feel the same?

---

### Post by hansdown on 2013-05-12
Hi 
D7Gd .

I've never noticed a gnu/linux distro fill default folders with random garbage; except tmp folders, which get flushed on shutdown.

Which gnu/linux version are you using?

---

### Post by AllRadioisDead on 2013-05-12
I've yet to come across any software on any OS that functions as you've described, and if I did I would simply disable or change that behaviour.

---

### Post by deadflowr on 2013-05-13
> [COLOR=#000000]Is it just me or does anyone else feel the same?[/COLOR]

It's just you.

None of the default folders, excluding hidden folders for configurations, I have have any file which I personally did not put there.

And yes, indexing can be disabled, if you so please.

---

### Post by vasa1 on 2013-05-13
> **D7Gd said:**
> ... those default folders always get filled with **random garbage** by various programs and I have to spend a great deal of time cleaning up the mess if I want to migrate from one OS to another.
...
Never ever seen that happen.

---

### Post by VeeDubb on 2013-05-13
The only trouble I've had with default folders has bee with Wine applications that expect different file naming, but I've managed to solve that one with minimal headache.  I just move everything added by a wine program to the appropriate folder, then create a symlink with the name the windows program expects, pointing to the correct folder.  Then I just add all of the symlinks to .hidden so I don't have to look at them.

---

### Post by D7Gd on 2013-05-13
I guess it's just me then. I've used mostly Ubuntu, Windows XP/7 and Mandriva. However, it is especially bad in Windows where the "My Documents" folder gets filled with game save files, configuration files and temp files. Take a look at it after a few years. All sorts of programs ranging from Camtasia Studio to the simplest TADS text adventure program write their stuff in there. This folder is strictly for documents, not for huge game save files! Those files take up so much space that I can't even back up the "My Documents" folder to an external USB stick. That's why I don't keep anything in there.

The equivalent in GNU/Linux is the /home/user/ folder itself. My advice is to **never ever** save anything directly to something like */home/user/ImportantFile.txt* as most of the programs suggest for default. You will forget about that file after a a few years or it will get lost between all the configuration files and whatnot.

For backup purposes, I used to put the /home/user/ folder onto another partition, but later I realized that even if I don't put anything it in there manually, it just keeps getting bigger and bigger and as time goes on. Web browsers and other programs keep their cache in there and whatever else that I don't even know about. It slows down backups the bigger it gets and the more tiny files are in there. And why are there 10000 thumbnail files? I like thumbnails but I don't want to back them up!

For that reason, instead of configuring every program manually every single time I do a clean install, I just partition the drive like this:

1) Primary partition for the system and the default user folders **(that I never use)** (15GB)
2) Primary partition for all my files (450GB)

Then I back up the system with CloneZilla and my files with rsync or FreeFileSync. Everything is kept separately and backups are always very fast. I just wish I had read some tutorial a long time ago informing me about the disadvantages of using the default user folders rather than finding out about it myself through a lot of trial and error.

---

### Post by pqwoerituytrueiwoq on 2013-05-13
The only thing i have ever seen remotely close to what you describe is in windows where it adds Thumbs.db and some ini file to almost every folder

---

### Post by IWantFroyo on 2013-05-13
It's true that there's a lot of config files in /home/user/, but there shouldn't be any in /home/user/Documents.

I've never had any issue like that. (at least not in Linux)

---

