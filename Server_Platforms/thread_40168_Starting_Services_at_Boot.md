---
title: "Starting Services at Boot"
date: 2005-06-08
forum: Server Platforms
---

### Post by echokilo on 2005-06-08
How do I configure services to start at boot? 

Is there a GUI for this? If not, what commands do this?

---

### Post by word_virus on 2005-06-08
[QUOTE=echokilo]How do I configure services to start at boot? [/QUOTE]

Which services? If you install them through Synaptic most of them will load at startup automatically: ssh, mysql, etc.

---

### Post by LordHunter317 on 2005-06-08
On Debian and Ubuntu, you either edit the symlinks in /etc/rc*.d manually, or you use update-rc.d(8).

---

### Post by ziggyboy on 2005-06-08
[QUOTE=echokilo]How do I configure services to start at boot? 

Is there a GUI for this? If not, what commands do this?[/QUOTE]
Ubuntu boots up just like Debian. After booting the kernel, it starts the script appropriate to its runlevel. By default Ubuntu runs at runlevel 2 but you can change this easily in /etc/inittab. The scripts executed at bootup is located in /etc/rc2.d. If you want to update this, I suggest using update-rc.d. Learn how to use it by typing 'man update-rc.d'. The scripts in rc2.d are actually symbolic links to the files in /etc/init.d. Reading through the files I mentioned will give you an idea how Linux bootup works. If you still don't get it then read about System-V init and runlevels.

---

### Post by Juippisi on 2005-06-08
[QUOTE=echokilo]Is there a GUI for this? If not, what commands do this?[/QUOTE]

Yes, there is. Install BUM ( [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html) ).

Oh, sorry. That isn't the solution for your problem. My mistake. I readed "How do I configure services _that_ start at bootup" :)

Sorry.

---

