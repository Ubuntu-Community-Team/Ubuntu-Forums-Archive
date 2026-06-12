---
title: "how to backup server using external hard drive...?"
date: 2008-09-10
forum: Server Platforms
---

### Post by hockey97 on 2008-09-10
HI I want to make an exact copy of the partician and also backup files.

I have 2 computers one is kinda old has windows xp the other own is new but has windows xp.

the old computer is currently in a dual boot with ubuntu and  windows xp.

the old one I usally use for personal use. I am still trying to decided which computer would be the main server.

I have ubuntu all set up with all servers required and also have my website files on it.

I want to copy in a way so I can handle 2 computers meaning have a backup in a way where I can make the new computer have an exact same config as the old one that has ubuntu.

I know of clonezilla but I want to avoid having to burn something on a cd.

I want a full backup meaning if My computer crashes and I can't even boot my system I want to be able to install ubuntu again but instead of creating a new partician I want to just point the ubuntu install cd to just copy over from  my external hard drive the copy of the ubuntu system. so I can just reboot and then see my system again all working.

what is the best way to do this??? I want to fiddle less with this.

I seek a simple solution that I can just select the partician and hit copy and if I want to restore to be able to just click restore.

Is there anything out there that can copy the partician??

I might just backup the files. SO I can just backup  one set of files and also back up any system files those will be 2 backups one for each computer.

would that be better and I found a tar zipped tutorial on ubuntu forms and tried to create a tar file to my external hard drive but never was able to. SO I just make the tar in my root directory and then copied it over to the external hard drive.

Is there any good way to backup your system???

---

### Post by cariboo on 2008-09-11
Have a look at partimage, it is available in the repositories:

```
sudo aptitude install partimage
```

Jim

---

### Post by p_quarles on 2008-09-11
> **hockey97 said:**
> I know of clonezilla but I want to avoid having to burn something on a cd.
Why? If you want to use partimage or dd (the tools that will do what you want), you shouldn't run them from the installed OS. That would be data suicide. Burn or cd, or change your plans.

> I might just backup the files. SO I can just backup  one set of files and also back up any system files those will be 2 backups one for each computer.
This is simpler. rsync or unison will accomplish what you're looking for here.

---

