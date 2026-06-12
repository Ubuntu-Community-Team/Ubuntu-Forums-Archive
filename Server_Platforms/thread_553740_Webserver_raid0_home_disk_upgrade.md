---
title: "Webserver raid0 home disk upgrade"
date: 2007-09-18
forum: Server Platforms
---

### Post by helmeester on 2007-09-18
Hello all,

i started my first webserver on ubuntu and it has been working out great for me, its a super distro for serverbeginners like me.

when i setup my server i used one 8gb ide disk as an os disk and 2 sata 160gb disks in raid0 as /home disk.

now im starting to need some more space, and im thinking about upgrading to 2x500gb sata raid0, but i don't really have a clue how to commence the upgrade, because i can't get two raids running at the same time for i have only 2 sata slots on the mb. the logical steps i could think of were:

[LIST=1]
[*]backup all data from /home somewhere
[*]unmount /dev/md0 and destroy/delete the raidvolume
[*]insert new disks
[*]setup raid0 again on md0
[*]copy data back
[/LIST]

my question is: will this work? will the services that are running not trouble with a new md0? and furthermore: am i missing some steps i should not forget in this process? the plus of my system is that my osdisk is seperate, so everything on my raid should be purely /home content that is not needed essentially on booting etc.

thanks in advance!

kind regards,
Peter

---

### Post by dantrevino on 2007-10-04
Assuming you keep all your data in the same folder structure, that'll work.  

I'd do some integrity checking on your backed up data before you destroy your current md0.

You're serving your web content from /home?

dan

---

