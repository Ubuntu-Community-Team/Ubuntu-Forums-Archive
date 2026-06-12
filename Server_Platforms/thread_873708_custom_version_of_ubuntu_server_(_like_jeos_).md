---
title: "custom version of ubuntu server ( like jeos )"
date: 2008-07-29
forum: Server Platforms
---

### Post by letronje on 2008-07-29
JeOS is a minimalistic version of ubuntu server edition and is optimized for virtualization. 

I wanted to make a custom stripped down version of ubuntu server edition, similar to JeOS. The differences being,

1) I don't want to optimize my  OS for virtualization.
2) I have a custom list of apps that i want to be installed when my OS is installed. 

I am sure there is a script involved in the creation of JeOS which would generate the iso or its components given a list of packages. I wanted to use this script to generate my own custom lightweight server distro.

Whom should i contact ?

-- Thnx in advance :)

---

### Post by songshu on 2008-07-29
just contact google ;)

there is a file on the server cd called preseed.cfg basically you can set all the answers that are asked by the debian installer (like the expert mode, not the standard ubuntu questions)

ubuntu-standard is the complete base system (server) that is marked there, if you replace that with the names of the packages you want i think you are about done.

---

