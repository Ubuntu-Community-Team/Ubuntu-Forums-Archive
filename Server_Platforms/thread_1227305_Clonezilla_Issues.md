---
title: "Clonezilla Issues"
date: 2009-07-30
forum: Server Platforms
---

### Post by sliggy on 2009-07-30
Hey everyone,

I'm working on getting Clonezilla setup on a Ubuntu server box following a guide ([this one]("http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/")). I've gotten everything to work, and the client machine even boots off of the server, but when I try to load up the backup/restore menu, I get this error:

```
The kernel requires the following features which are not present on your CPU:
pae

```

After some searching, I figured out that the server kernel doesn't support the old CPU's on these laptops, but I'm not sure where to go from here to make it work. Could anyone help me out?

---

### Post by Kolipoki on 2009-07-30
Hihi. I am not totally sure what PAE is/does, but I have seen some posts here talking about settings in the BIOS, related to PAE. Good luck.

---

### Post by ktrnka on 2009-07-30
> **Kolipoki said:**
> Hihi. I am not totally sure what PAE is/does, but I have seen some posts here talking about settings in the BIOS, related to PAE. Good luck.

PAE stands for Physical address extension which allows a 32bit os to use more than 4GB of ram. It is on all procs from the pentium pro through now except for a couple of pentium-m's.

[http://en.wikipedia.org/wiki/Physical_Address_Extension]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

Not sure why it's not booting though. What are the specs of your machine that you're having problems with?

---

### Post by sherl0k on 2009-07-30
From my experiences, using the "Alternative" version of Clonezilla, which uses the Ubuntu kernel rather than Debian's, works best with Ubuntu installs. Especially since the Debian kernel doesn't have ext4 support (at least when I tried it).

---

