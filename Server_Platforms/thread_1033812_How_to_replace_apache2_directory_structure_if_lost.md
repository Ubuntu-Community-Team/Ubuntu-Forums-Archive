---
title: "How to replace apache2 directory structure if lost"
date: 2009-01-07
forum: Server Platforms
---

### Post by lumix on 2009-01-07
So I got fed up with trying to make Apache2 work and wanted to reinstall.  Unsurprisingly, apt-get remove doesn't clear out the dir structure and still contained potential culprits (for the non-working apache install).  So guess what, yeah, I deleted them.  Couldn't find any information to explain why Apache2 wouldn't serve up a page, so what else could I try?

So now how do I properly restore the apache2 directory structure (e.g. /etc/apache)?  apt-get can't handle that either.

---

### Post by volkswagner on 2009-01-07
If you don't have too much invested you may be better off with a fresh install.  It may be quicker in the long run.

---

### Post by lumix on 2009-01-07
Unfortunately I do.  

But as it turns out, synaptic package manager *does* reinstall the directory structure.  So what is SPM doing that I can do from a cli?

Thanks for the reply, btw.

---

### Post by Frazzled Penguin on 2009-06-16
When you used apt-get to remove and purge apache it didn't uninstall all the apache components.

To see what is installed that is apache related simply type:
[B]
dpkg -l | grep apache[/B]

The "**dpkg -l**" command will list all the apps that are installed. The rest of the command directs the output to "**grep**" which is then instructed to only show lines that contain the word "**apache**".

You'll probably see that there is still apache2.2-common installed. Use the following command to remove and purge it:

**apt-get remove --purge apache2.2-common**

Once that is done you can re-install apache2 by:

**apt-get install apache2**

and bingo, your config directory and all default files should be back. At least that's how I do it in Ubuntu server 8.04 LTS.

I know it's a bit late now, but I hope it helps you in the future or anyone else that may be struggling with the same issue/concept.

Ciao.
Frazz.

---

### Post by mathgirl on 2010-09-20
> **Frazzled Penguin said:**
> When you used apt-get to remove and purge apache it didn't uninstall all the apache components...


Thank you Frazz!  This was exactly my situation.  You saved me a reinstall!:KS

---

