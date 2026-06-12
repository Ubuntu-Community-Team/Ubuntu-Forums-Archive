---
title: "all this permissions thing"
date: 2010-03-05
forum: Security
---

### Post by babagau on 2010-03-05
In both 9.04 & 9.10 I log in as normal user and cannot access (r,w,x) any hard drive / partition unless I open nautilus from terminal with gksu. What is the point in all this? How can I simply do anything I want? It's my computer after all! In 9.10 I used to log in as root and was happy and unrestricted(!), but I had to go back to 9.04 due to the sound card. How can I gain full permissions as user or log in as root in 9.04? I don't understand why all this oppression, its not a secret lab or organisation's PC, its my home computer!

---

### Post by ld.4lpha on 2010-03-05
> **babagau said:**
> It's my computer after all! 

It won't be for long if you go around doing everything as root.  You will be pwned.

This is one of the reasons *nix is inherently more secure than Windows: users aren't granted full admin (root) permissions for normal, every day tasks by default.

---

### Post by doas777 on 2010-03-05
you can enable the root account. it's a horrible idea, but you can do it.

---

### Post by babagau on 2010-03-05
[SIZE=3]I had xp for years but since 4 months I've been using ubuntu and puppy linux, so I am a newbie. I am not familiar with terminal commands, I use them very little, what serious damage can I do from the graphical environment? Something serious I did in ubuntu was to add ancient greek keyb layout but accidentally erased eng (or did not set keyb shortcut to change layout) so in the login screen I could not type in english the passwd! I learned my lesson well so the passwd since then is only numbers! ;)

&#959;&#922; guys I login as root now, wish me good luck![/SIZE]

---

### Post by mkvnmtr on 2010-03-05
Best of luck. Make sure you keep your install disk.

---

### Post by Ijan on 2010-03-05
It would be better to learn how to access files on other partitions without permanently working as root.

For occasional configuration tasks it is intended that you use sudo.

It is sort of essential to the ubuntu security model that you work permanently as what Windows calls a "restricted user" with very limited access to the system files.

---

### Post by HPD2 on 2010-03-06
> **babagau said:**
> [SIZE=3]... what serious damage can I do from the graphical environment?
... &#959;&#922; guys I login as root now, wish me good luck![/SIZE]

Its not to protect the operating system from you, but from the world. Logging in as root should be done only for as little amount of time possible. Instead you should use "sudo" to access things that you need administrative privileges for.

---

### Post by DawieS on 2010-03-06
> **babagau said:**
> How can I simply do anything I want?
If you have used the **Search** facility in these forums, you would have found many workable solutions, without severely risking the security of your Ubuntu installation.

If you are running 9.10 with some NTFS partitions, you would not be able to mount/unmount NTFS partitions without authorization, by only making adjustments in the /etc/fstab file, without running into other problems.

For more information see _**[this]("http://ubuntuforums.org/showthread.php?t=1417038")**_ thread. Also, check whether you are enabled in the **System - Administration - Users and Groups - Properties - Mount user-space filesystems (FUSE)** tab.:razz:

---

### Post by babagau on 2010-03-07
> **HPD2 said:**
> Its not to protect the operating system from you, but from the world.
Do you mean from crackers cyber-pranksters etc?

---

### Post by cariboo on 2010-03-07
Yes. If you run as root all the time, the cracker already knows that account name, so all he has to do is find the password, so if you have a weak password, it shouldn't take to long before he owns your system.

If you use the system as setup by default, the root account is disabled, so there is no way in through root. The bad guy first has to find out the user name you are using, and then needs to find the password, unless you have something the bad guy really wants on your system, he is more than likely going to give up before cracking the system.

---

### Post by Jive Turkey on 2010-03-07
I would advise that instead of enabling the root account you just tweak the ownership and or permissions of the files/directories where you need access.

read up on "chmod" and "chown."  Another handy tool is "sudo -i" which lets you be root in the terminal until you exit.

---

### Post by babagau on 2010-03-10
ah, I see, thanks guys!

---

