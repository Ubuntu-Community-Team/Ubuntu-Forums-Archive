---
title: "WoW Launcher starts, but thats it."
date: 2010-05-14
forum: Wine
---

### Post by trevsbe on 2010-05-14
I have World of Warcraft downloaded, installed, and updated, the launcher will open, but when you click "Play" button it closes the launcher and nothing happens. If you try and start it via a terminal this is the error that it gives

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc4d9a9

Any ideas?

---

### Post by hikaricore on 2010-05-14
Don't use the launcher for starters, run wow directly from a terminal and post any error output.
Be sure you are using reasonable video hardware and drivers, integrated intel chipsets usually don't cut it.
Double check that you're starting Wow in opengl mode as instructed by every single howto guide on the internet.

---

### Post by trevsbe on 2010-05-15
> **hikaricore said:**
> Don't use the launcher for starters, run wow directly from a terminal and post any error output.
Be sure you are using reasonable video hardware and drivers, integrated intel chipsets usually don't cut it.
Double check that you're starting Wow in opengl mode as instructed by every single howto guide on the internet.

I have tried it with and without launcher, manually by clicking and via the terminal. The error that I get from the terminal is the error in my initial post

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr  0x7bc4d9a9

I assume I'm using reasonable hardware/drivers as its the same as when I was using XP. I am running integrated but its ATI Radeon. As far as I know I am starting in OpenGL, however I never had a Config.wtf file so I had to create my own. I've also tried the command in a terminal to manually start WoW in OpenGL mode.

---

### Post by cburner on 2010-05-15
Paste the command you are using to start WoW and we will go from there. What most likely happened is since you tried to start the game from the WoW launcher it locked down the World of Warcraft folder so you can't write to it. Check the permissions on that folder and see if you have read and write access. If not, you need to change it so that you do.

---

### Post by trevsbe on 2010-05-16
> **cburner said:**
> Paste the command you are using to start WoW and we will go from there. What most likely happened is since you tried to start the game from the WoW launcher it locked down the World of Warcraft folder so you can't write to it. Check the permissions on that folder and see if you have read and write access. If not, you need to change it so that you do.

The command that I'm using via the terminal is

wine "C:\Program Files\World of Warcraft\WoW.exe

Anytime I try and change the File access to Read and Write, it immediately returns it to "---." I do have "Create and delete files" as the Folder access. WoW.exe has Read and Write permissions.

---

### Post by cburner on 2010-05-16
What is the permissions of .wine folder in your Home directory?

---

### Post by trevsbe on 2010-05-16
> **cburner said:**
> What is the permissions of .wine folder in your Home directory?

Owner
Folder Access: Create and delete files

Group
Folder Access: Access files

Other
Same as above

It does say at the bottom of the screen "You are not the owner, so you cannot change these permissions." Dunno if that makes any difference.

---

### Post by hikaricore on 2010-05-16
> **trevsbe said:**
> Owner
Folder Access: Create and delete files

Group
Folder Access: Access files

Other
Same as above

It does say at the bottom of the screen "You are not the owner, so you cannot change these permissions." Dunno if that makes any difference.

Yes that makes a difference.

Please post the output of the following:
> ls -la ~ | grep .wine

---

### Post by trevsbe on 2010-05-17
> **hikaricore said:**
> Yes that makes a difference.

Please post the output of the following:

drwxr-xr-x  4 trevsbe trevsbe    4096 2010-05-16 17:53 .wine

---

### Post by hikaricore on 2010-05-17
Well then it shouldn't say you aren't the owner..
You've done something weird to your install along the way but I"ve not the foggiest what.

---

### Post by trevsbe on 2010-05-17
> **hikaricore said:**
> Well then it shouldn't say you aren't the owner..
You've done something weird to your install along the way but I"ve not the foggiest what.

I totally new to Linux, so its possible, but I followed instructions on how to install it. I'm fairly good at following instructions, so I'd hope it couldn't install wrong.

I kinda figure its a hardware issue, hope not, but most likely is. Its an acer. Was running super slow with XP, so I figured I wipe clean and switch to Linux, runs alot faster now, but its still pretty much useless.

---

