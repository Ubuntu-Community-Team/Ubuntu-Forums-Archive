---
title: "Bug confirmation request: Rhythmbox many errors when importing folder"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-30
Hi everyone. Another one that is failing repeatedly here today:

- Install rhythmbox if you don't already have it.
- Inside Rhythmbox, import a network (Samba/NFS tested) large folder with many different types of audio files (ogg, mp3, aac, etc). I'm importing a folder with approximately 4TB in an organized tree (artist/album/tracks).
- During import, it will complain about not having proper codecs to play such fyletypes, present checkboxes with codecs options to be installed. If you tr to install any of them, you get broken deps. 
- You won't get a chance to install them anyway. Look at dmesg.

> [ 4594.322883] rhythmbox-metad[3803] general protection ip:7fb31e9856ca sp:7fffbeaf1e70 error:0 in libgobject-2.0.so.0.3122.0[7fb31e952000+4f000]
[ 4727.880822] rhythmbox-metad[4278] general protection ip:7f09d8aba694 sp:7fffa6eebee0 error:0 in libgobject-2.0.so.0.3122.0[7f09d8a87000+4f000]
[ 4804.244726] rhythmbox-metad[5246] general protection ip:7feae62e66ca sp:7fff89f4d710 error:0 in libgobject-2.0.so.0.3122.0[7feae62b3000+4f000]
[ 4827.335518] rhythmbox-metad[6219]: segfault at 20 ip 00007f2313e021b4 sp 00007fff4fcc07c0 error 4 in libgstreamer-0.10.so.0.30.0[7f2313d8a000+de000]
[ 4849.937478] rhythmbox-metad[6269]: segfault at 8000000016 ip 00007fb6c7301694 sp 00007fffb95d58e0 error 4 in libgobject-2.0.so.0.3122.0[7fb6c72ce000+4f000]
[ 4852.340413] rhythmbox-metad[6287]: segfault at 120 ip 00007f750e59e1b4 sp 00007fff77b83a10 error 4 in libgstreamer-0.10.so.0.30.0[7f750e526000+de000]
[ 5074.855738] rhythmbox-metad[6296]: segfault at 7fb000000016 ip 00007fb025034694 sp 00007ffffb6586a0 error 4 in libgobject-2.0.so.0.3122.0[7fb025001000+4f000]
[ 5166.506923] rhythmbox-metad[8223] general protection ip:7f4a65d07694 sp:7fff13ba9650 error:0 in libgobject-2.0.so.0.3122.0 (deleted)[7f4a65cd4000+4f000]
[ 5168.449710] rhythmbox-metad[15448]: segfault at c0 ip 00007f904cf1d1b4 sp 00007fff12028350 error 4 in libgstreamer-0.10.so.0.30.0[7f904cea5000+de000]
If you confirm this, please +1 and add any details to [_**[COLOR=Red]Bug #969527[/COLOR]**_]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/969527") 


Thanks,
Effenberg

---

