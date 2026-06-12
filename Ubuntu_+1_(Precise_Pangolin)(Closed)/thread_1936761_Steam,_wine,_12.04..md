---
title: "Steam, wine, 12.04."
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Misantropen on 2012-03-06
So, messing around in 12.04. Everything seems to be working fine. (Even my ATI-card has stopped trying to murder gnome3).

But alas, there's a snake in the paradise, when trying to install Steam - I encounter this:

```
axel@TheOvermind:~$ winetricks steam 
Executing w_do_call steam
Executing load_steam
Executing mkdir -p /home/axel/.cache/winetricks/steam
Executing wine msiexec /i SteamInstall.msi
fixme:storage:create_storagefile Storage share mode not implemented.
wine: Unhandled page fault on write access to 0x000000b4 at address 0x7bc450e6 (thread 0028), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc47aac
------------------------------------------------------
Note: command 'wine msiexec /i SteamInstall.msi' returned status 5.  Aborting.
------------------------------------------------------
axel@TheOvermind:~$
```

I am puzzled, anyone care to help?

---

### Post by Narn on 2012-03-07
[FONT="Arial"][/FONT]I have exactly the same problem, and downloading and running the steam installer outside of winetricks doesn't help. Are there any fixes?

---

### Post by Misantropen on 2012-03-08
It appears using PlayOnLinux will solve this issue.
Just download it from their website, and it will install wine and Steam for you, and it works.

---

### Post by mc4man on 2012-03-08
Haven't used my steam account in years, just gave it a try after updating to latest winetricks
Went thru fine though did have to eventually retrieve forgotten password

Maybe try  clearing out any steam folders if they exist in ~/.cache/ & or ~/.local/share/wineprefixes/, then updating winetricks, ect.

---

### Post by daltonlaffs on 2012-03-09
I saw this one earlier, but, uh... I can't remember how I fixed it. :-\"

I think it had something to do with winetricks, maybe see if it has anything for this situation.

---

### Post by P-I H on 2012-03-12
After updates today, installation of the Steam client with Winetricks works OK.

---

### Post by Decalc on 2012-03-21
I've just installed 12.04 and installed playonlinux. I can't open Steam.. it updated asks for password after that gets stuck on connecting and crashes. Anyone?

---

### Post by jfernyhough on 2012-03-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

### Post by Decalc on 2012-03-21
I have found the problem i need the GL lib32 files for it to work. I use an ati mobility HD 3650.. were do i find those lib's? i searched everywere!

---

