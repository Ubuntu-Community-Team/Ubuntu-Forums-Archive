---
title: "What an amazing concept!.../home on it's own partition"
date: 2009-12-27
forum: The Cafe
---

### Post by stuart.reinke on 2009-12-27
I know this is nothing new, but I just recently got confident enough with partitioning during installation to set up things manually.

I have a bad habit of tweaking my system until I break it. My preferred course of action is to reinstall and start over tweaking again.:)

With /home on a separate partition, all my data, downloads, and settings remain in tact. 

I think this is my new favorite feature in Linux. 

I guess I have no question for anyone to answer so I'll just invite comment on the subject.

---

### Post by dragos240 on 2009-12-27
> **stuart.reinke said:**
> I know this is nothing new, but I just recently got confident enough with partitioning during installation to set up things manually.

I have a bad habit of tweaking my system until I break it. My preferred course of action is to reinstall and start over tweaking again.:)

With /home on a separate partition, all my data, downloads, and settings remain in tact. 

I think this is my new favorite feature in Linux. 

I guess I have no question for anyone to answer so I'll just invite comment on the subject.

Enjoy. Make sure to edit /etc/fstab accordingly!

---

### Post by stuart.reinke on 2009-12-27
> **dragos240 said:**
> Enjoy. Make sure to edit /etc/fstab accordingly!

please explain. what is /ect/fstab and what needs to be edited and why?

---

### Post by gs777 on 2009-12-27
u just used a feature of linux

---

### Post by dragos240 on 2009-12-27
> **stuart.reinke said:**
> please explain. what is /ect/fstab and what needs to be edited and why?

If you are using ubuntu, then you don't need to. However many distros need to have the fstab edited when partitioning is done. fstab is a config file that tells your linux system what to mount at boot and where to mount it.

---

### Post by stuart.reinke on 2009-12-27
> **dragos240 said:**
> If you are using ubuntu, then you don't need to. However many distros need to have the fstab edited when partitioning is done. fstab is a config file that tells your linux system what to mount at boot and where to mount it.

I see, thanks. I am using Ubuntu so that's probably why I didn't know about it or what it is for.

---

### Post by castrojo on 2009-12-27
> **stuart.reinke said:**
> With /home on a separate partition, all my data, downloads, and settings remain in tact.

You know the installer has an option to do a clean install while keeping your /home intact already right? No need for a separate partition. ;)

FWIW, I keep my /home on a separate drive entirely, which is pretty handy.

---

### Post by stuart.reinke on 2009-12-27
> **whiprush said:**
> You know the installer has an option to do a clean install while keeping your /home intact already right? No need for a separate partition. ;)

FWIW, I keep my /home on a separate drive entirely, which is pretty handy.

I've never seen that. Probably looked past it a hundred times. Where is it?

---

### Post by pelle.k on 2009-12-27
> **stuart.reinke said:**
> With /home on a separate partition, all my data, downloads, and settings remain in tact. 

I've done that for years. However, i don't save my home when reinstalling. It's just that i like to keep it separated from the rest of the system, in case i fill up my home, the system disk still hums along nicely.

That said, i always keep a data partition that spans almost the whole HD, where i keep my stuff (organized with subfolders, of course). Back in the days, i had to add it after an install (in /etc/fstab), but nowadays, i can just add it manually in the installer.
Even if one doesn't add it during an install, gnome can mount it for you when you click it. There's a downside to the latter method though - if such a partition has say a .jpg that you use as a background image, said partition has to be mounted before gnome starts up, naturally.

---

### Post by macogw on 2009-12-27
> **stuart.reinke said:**
> I've never seen that. Probably looked past it a hundred times. Where is it?

Go into Manual Partitioning, tell it to use the same / partition as before, and tell it not to format.

---

### Post by Bachstelze on 2009-12-27
> **gs777 said:**
> u just used a feature of linux

Pretty much every modern OS has that feature. Yes, even Windows since at least XP.

---

### Post by chriswyatt on 2009-12-27
I used to do the same thing with Windows, I used to keep Windows setup and My Documents / Desktop on a separate partition, made clean installing Windows much less of a headache :).

---

