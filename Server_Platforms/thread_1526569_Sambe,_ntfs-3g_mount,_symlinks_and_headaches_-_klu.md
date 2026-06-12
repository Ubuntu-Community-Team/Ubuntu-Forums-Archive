---
title: "Sambe, ntfs-3g mount, symlinks and headaches - kludge needed"
date: 2010-07-08
forum: Server Platforms
---

### Post by frankvw on 2010-07-08
Hi, everyone,

Once more I'm trying to do something that is necessary, yet contrary to design... or so it seems. :-)

I used to have a proper server, but that gave up the ghost. So right now I make do with a laptop, into which I have plugged a USB harddisk. That used to be my backup of /home, but because I run XP on my workstation (which, sadly, I cannot avoid if I want to get paid at the end of the month, but mainly use to access my Linux server) that USB disk has an NTFS file system. Which is useful, given the fact that sometimes I have to take it with me and plug it into a Windoze box.

When my server passed on to that great server room in the sky, everything went with it, including the data volume. So what I did, this being an emergency, was to plug the USB disk into a spare laptop, install Karmic Server onto it, and edit /etc/fstab to mount the USB disk on /home, using the appropriate uid/gid to mount it under the ownership of my own user account.

Fine - so far so good. This gives me /home/share which is shared as a public samba mount, and /home/frankvw which is shared as a password-protected directory. It also gives me /home/www which is not shared, this being the Apache docroot. I have proper access to everything, and the people rejoice.

Now for the dirty business. To make life easier, I have a symlink 'www' in my home directory:

[INDENT]~/www -> /home/www[/INDENT]

which works fine from the Linux command prompt (an "ls ~/www") lists the docroot, and "cd ~/www" gets me there) but of course Samba refuses to play ball here. From a Windows client I can see 'www' in my home dir but cannot access it. From a Linux workstation (Intrepid Workstation) in Nautilus I cannot even see 'www' in my homedir - apparently Nautilus is aware of the dirty deeds going on here and prudently hides it.

What can I do (short of rearranging the file/directory structure on my USB disk which I'd rather not do) to work around this (otherwise very sensible) restriction?

---

### Post by byStanderone on 2010-07-08
...try the fix that seshomaru did for his smb share, not sure but i hope that works in your situation: 
[http://ubuntuforums.org/showthread.php?t=1521595](http://ubuntuforums.org/showthread.php?t=1521595)

---

### Post by Morbius1 on 2010-07-08
There was a change to how Samba deals with symlinks because of a security issue: [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

To restore it to it's old operation you could try this:

Add the following lines to the [global] section of smb.conf:
```
follow  symlinks = yes
wide links = yes
unix extensions = no
```Then restart the samba service

---

### Post by frankvw on 2010-07-08
> **Morbius1 said:**
> There was a change to how Samba deals with symlinks because of a security issue: [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

To restore it to it's old operation you could try this:

-- snip --



Yep - that worked! Thank you so much!!

// FvW

---

