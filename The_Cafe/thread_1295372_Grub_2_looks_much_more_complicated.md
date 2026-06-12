---
title: "Grub 2 looks much more complicated"
date: 2009-10-19
forum: The Cafe
---

### Post by Sealbhach on 2009-10-19
I'm not looking forward to when I have to fiddle about with it. I mean, just check this out:

[SIZE=2][COLOR=Black][Grub 2 Title Tweaks]("http://ubuntuforums.org/showpost.php?p=8082954&postcount=1")[/COLOR][/SIZE]

and this is the new way to restore Grub after installing Windows (requires chroot):

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Looks like a lot more stuff to do, this will not be easy to convey to beginners in the Absolute Beginners Forum.... 

.

---

### Post by lukjad on 2009-10-19
Errr... wrong thread.

---

### Post by hoppipolla on 2009-10-19
It's probably a better bootloader though. I mean maybe the solution is just to have more GUI tools to configure and reinstall it.

---

### Post by jaxxstorm on 2009-10-19
I also though this. My Windows 7 partition is on a weird drive root, with Grub1 it takes 2 seconds to change the numbers, with grub 2 it seems terrifying!

---

### Post by Exodist on 2009-10-19
Grub2 is still to early. I am not sure it will be "rock-solid" enough in time for Lucid. I am betting the Devs think it will be, but It should have been solid for this release before being put into Lucid.

---

### Post by hoppipolla on 2009-10-19
> **Exodist said:**
> Grub2 is still to early. I am not sure it will be "rock-solid" enough in time for Lucid. I am betting the Devs think it will be, but It should have been solid for this release before being put into Lucid.

it does work fine for me though and it even boots Windows! Are people still having usability problems with it other than it's complexity?

---

### Post by Xbehave on 2009-10-19
until grub2 supports locking it will not be taken seriously by distros, what is the point in having a secure linux install if i can just boot to an old kernel/single user mode, anyway?

BTW switching to xubuntu is silly because xubuntu will switch to grub2 when ubuntu does.

---

### Post by koenn on 2009-10-19
> **Sealbhach said:**
> I'm not looking forward to when I have to fiddle about with it. I mean, just check this out:

[SIZE=2][COLOR=Black][Grub 2 Title Tweaks]("http://ubuntuforums.org/showpost.php?p=8082954&postcount=1")[/COLOR][/SIZE]

and this is the new way to restore Grub after installing Windows (requires chroot):

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Looks like a lot more stuff to do, this will not be easy to convey to beginners in the Absolute Beginners Forum.... 

.
that doesn't look too bad;

restoring grub after installing Windows is still just a few simple commands that absolute beginners can copy and paste. 

The tweaks look elaborate on first sight, but it's still just text editing. And only geeks will want to customize their boot menu, so no problem there - geeks love to learn stuff like this.

---

### Post by Bachstelze on 2009-10-19
> **lukjad007 said:**
> Which is why I'm going to be switching to Xubuntu. :)

What does it have to do with GRUB?

---

### Post by coldReactive on 2009-10-19
> **Bachstelze said:**
> What does it have to do with GRUB?

+1, because the release notes of 9.10 Xubuntu state that they're using GRUB 2 as well.

---

### Post by Xbehave on 2009-10-19
> **coldReactive said:**
> +1, because the release notes of 9.10 Xubuntu state that they're using GRUB 2 as well.
wait grub2 is in karmic ? LAME i was going to come back to *buntu on 9.10 but i do not want to be dealing with grub2 unless it can password protect options.

---

### Post by Bachstelze on 2009-10-19
> **Xbehave said:**
> wait grub2 is in karmic ? LAME i was going to come back to *buntu on 9.10 but i do not want to be dealing with grub2 unless it can password protect options.

[http://packages.ubuntu.com/karmic/grub](http://packages.ubuntu.com/karmic/grub)

GRUB 0.97 is still there, so even if GRUB 2 gets installed by default, you can just replace it with:

```
sudo apt-get install grub
```

BTW, I would be very surprised if GRUB 2 couldn't password-protect some boot options.

---

### Post by Exodist on 2009-10-19
> **hoppipolla said:**
> it does work fine for me though and it even boots Windows! Are people still having usability problems with it other than it's complexity?

Seems a few are. Something I hoped would have already been resolved. Hate to see G2 going into Karmic with even one known bug. Reason being that would give us 6 months to make sure there was NO issues when using in Lucid.

---

### Post by coldReactive on 2009-10-19
> **Bachstelze said:**
> [http://packages.ubuntu.com/karmic/grub](http://packages.ubuntu.com/karmic/grub)

GRUB 0.97 is still there, so even if GRUB 2 gets installed by default, you can just replace it with:

```
sudo apt-get install grub
```

BTW, I would be very surprised if GRUB 2 couldn't password-protect some boot options.

Wouldn't that give the good 'ol "package is referred by another package" error?

---

### Post by Bachstelze on 2009-10-19
> **coldReactive said:**
> Wouldn't that give the good 'ol "package is referred by another package" error?

Nope.

---

### Post by BrokenKingpin on 2009-10-20
What are the benefits of GRUB 2 over GRUB 1? I guess I could look it up, but I am far too lazy :P

---

