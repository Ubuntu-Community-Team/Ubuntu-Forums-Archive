---
title: "Dedicated UT goty Server on ubuntu 8.04"
date: 2008-12-22
forum: Server Platforms
---

### Post by DrZoidy on 2008-12-22
Dedicated UT goty Server on ubuntu 8.04
hi all.
i am setting up an UBUNTU 8.04 server to run as a dedicated server for Unreal Tournament GOTY. i have got as far as setting up samba to share folders as i dont have a CDROM on the machine its an old compaq P4 with a 512 ram.

i am using the unreal.tournament.436-multilanguage.goty.run installation script.

i have a folder that i have copyed the game disk to and run the command :
export SETUP_CDROM=/home/myuser/UT_INSTALL

i have renamed the .run file to ut-436-goty.run to make it easier to play with.

now when u run the install script using
sh ut-436-goty.run --target ut
i get this back

creating directory ut
verifying archive integrity... All Good.
uncompressing Unreal tournament 436-multilanguage.goty installer .................................................. ...................................
/home/my username/.setup5344: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

then goes back to command prompt.

question is can i find these libraries and dump them in the lib directory reboot the machine and all will be well?

any advice would be awsome.

---

### Post by TheFuzz4 on 2009-01-22
If you haven't got an answer to this yet you need to run this command

sudo apt-get install libgtk1.2

---

