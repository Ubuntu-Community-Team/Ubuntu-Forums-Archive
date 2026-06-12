---
title: "Ubuntu Server, Samba, ext4 partition, and windows executable"
date: 2017-03-23
forum: Server Platforms
---

### Post by aeronutt on 2017-03-23
Big mistake, odd problem:
Ubuntu server, Samba, a disk partition formatted as ext4. Add in a Windows 8.1 machine for fun.
I 'forgot' and via the windows machine installed windows programs on the ext 4 partition. Of course, the install went fine. Surprisingly, some but not all executables run (from Windows of course). And of course, the one that won't run at all is the uninstall program!

After some investigation, it appears to be a permissions problem? OR, is this an ext4 issue and I simply won't be able to get the executables to run once (I just want to uninstall).

Is there a way to set permissions (via Samba, or Windows, or when booting the server and mounting the ext4 drive, etc) to give the executables on the ext4 partition and windows the correct permissions to run the executables, once?

---

### Post by TheFu on 2017-03-23
Would need to know what permissions (or username) Windows requires to run the uninstall programs.  I suspect that it uses the "SYSTEM" account, which doesn't have permissions via samba. Check that with some Windows installer experts. I haven't written a Windows installer since the late 1990s, sorry.

This has NOTHING to do with ext4.  Windows only sees the CIFS storage.

---

### Post by mastablasta on 2017-03-24
easiest solution would be to just delete the programs, then use some registry & disk cleaner. there are various 3rd party programs that will do that on Windows rather well.


mkae sure you backup important data first before messing arround with disk and OS files.

---

### Post by aeronutt on 2017-03-25
> **TheFu said:**
> Would need to know what permissions (or username) Windows requires to run the uninstall programs.  I suspect that it uses the "SYSTEM" account, which doesn't have permissions via samba. Check that with some Windows installer experts. I haven't written a Windows installer since the late 1990s, sorry.

This has NOTHING to do with ext4.  Windows only sees the CIFS storage.

So does that mean there's a possible fix via Samba settings?
(I'm a rookie with this Samba/windows thing.)
God help me if I have to join a Windows forum. lol.

---

### Post by aeronutt on 2017-03-25
> **mastablasta said:**
> easiest solution would be to just delete the programs, then use some registry & disk cleaner. there are various 3rd party programs that will do that on Windows rather well.


mkae sure you backup important data first before messing arround with disk and OS files.

I'd consider that, do you have a recommended 3rd party tool that is free and that you trust? I've seen a few that cost $.

---

### Post by mastablasta on 2017-03-27
there used to be a good one i used, but forgot it's name. and i am not sure they sitll make it...

anyway ccleaner is used a lot. there are a bunch that have free version that will do the registry clean at least. also i saw Avast has some tool now as well. basically you need something that will clean up the leftover files and registry.

some are shareware, but they have day limit. so you can install them, clean up your OS and then remove them.


for example here is a list of 36 of them with short review for each: [https://www.lifewire.com/free-registry-cleaners-2626176](https://www.lifewire.com/free-registry-cleaners-2626176)

---

### Post by aeronutt on 2017-03-27
Thanks folks. I tried a handful of things to change the permissions (via Samba and via W8), and nothing I did helped. There's likely a proper fix, but I don't need the .exe's on a remote partition that bad.
I manually edited the registry, used ccleaner, and reinstalled under W8.
All is good now (except for having to run W8 at all :))

Thanks for the help.

---

