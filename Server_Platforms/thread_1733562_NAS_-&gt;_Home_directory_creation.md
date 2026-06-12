---
title: "NAS -&gt; Home directory creation"
date: 2011-04-19
forum: Server Platforms
---

### Post by Herazio on 2011-04-19
Hello all !

Here I am again with one of my silly questions. I'm terribly sorry for bothering you so much. I however have a problem with my server setup.

My setup is as follows:
A) 1 FreeNX terminal server
B) FreeNAS server

On the FreeNAS server I created myself a volume + a Unix share with NFS called /mnt/home. No one, EXCEPT root should be able to write in this directory. The reason that root should have write access is because pam_mkhomedir is called in my terminal server if the user doesn't have a homedirectory yet.

The problem is that I created this NFS share but once I mount it in my terminal server and I switch to my superuser and try to create a directory. I get a permission denied error. Does anyone have any idea why this might be ?

I guess it has a lot to do with FreeNAS and my FreeNX server having different passwd and group files or something. I really don't dare to say.

Any help is greatly appreciated and once again. Terribly sorry for being such a bother !

Kind regards

Herazio

---

