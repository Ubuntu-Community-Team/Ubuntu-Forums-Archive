---
title: "Virtual Box keeps aborting on XP install"
date: 2008-08-07
forum: Virtualisation
---

### Post by fidgaf on 2008-08-07
I cannot find a solution to this problem (though solved others with searches).


I'm running a vanilla Ubuntu 8.04.1 with all recent updates.

I want XP Pro as a virtual O/S.

The version of VirtualBox in the Add/Remove failed (vboxdrv problem).

A quick search indicated that **virtualbox_1.5.6-28266_Debian_etch_i386.deb** works fine.

It did.

I have also set up the users and activated the USB stuff.

Everything went well, the XP pro sp2 disc ran, found the virtual partition (10GB dynamic) and wanted to format it.

I said yes - after a looong wait - It Aborted.

The XP disc, thereafter, wants to boot from CD - and that's about as far as I get.

I have uninstalled VB and deleted the virtual partition several time with similar results.

I have noticed that on some attempts there is a new partition created 8MB in size (I always choose the 10GB partition).

I'm now in the process of becoming the very definition of stupid - Repeating the same things and expecting different results.

Can anyone help?


Thanks.

---

### Post by HermanAB on 2008-08-07
Try VMware Server!

Seriously, VM systems are very hardware dependent so I'm not surprized that Virtualbox gives you trouble. VMware works on a wider variety of hardware than Virtualbox in my experience, so give it a go.

---

### Post by tuxxy on 2008-08-07
Did you create the aprtition for XP and everything, maybe this guide will help 

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by fidgaf on 2008-08-08
> **tuxxy said:**
> Did you create the aprtition for XP and everything, maybe this guide will help 

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

I've read various guides and forums, including that one - Thanks - I know of nothing that I have missed - I'm lost as to what to do next.

---

### Post by fidgaf on 2008-08-08
> **HermanAB said:**
> Try VMware Server!

Seriously, VM systems are very hardware dependent so I'm not surprized that Virtualbox gives you trouble. VMware works on a wider variety of hardware than Virtualbox in my experience, so give it a go.

I'll give it a short while longer to see if anyone has had the exact same problem (and fixed it) then I will give VMware a go.

Ta!

---

### Post by EnGorDiaz on 2008-08-08
> **fidgaf said:**
> I cannot find a solution to this problem (though solved others with searches).


I'm running a vanilla Ubuntu 8.04.1 with all recent updates.

I want XP Pro as a virtual O/S.

The version of VirtualBox in the Add/Remove failed (vboxdrv problem).

A quick search indicated that **virtualbox_1.5.6-28266_Debian_etch_i386.deb** works fine.

It did.

I have also set up the users and activated the USB stuff.

Everything went well, the XP pro sp2 disc ran, found the virtual partition (10GB dynamic) and wanted to format it.

I said yes - after a looong wait - It Aborted.

The XP disc, thereafter, wants to boot from CD - and that's about as far as I get.

I have uninstalled VB and deleted the virtual partition several time with similar results.

I have noticed that on some attempts there is a new partition created 8MB in size (I always choose the 10GB partition).

I'm now in the process of becoming the very definition of stupid - Repeating the same things and expecting different results.

Can anyone help?


Thanks.

search up innotek virtual box installer thats the right one for you

---

### Post by matjazturinek on 2009-03-09
Hey, 

yesterday I tried to install windows XP tablet edition on my Intrepid and got the same error over and over again - no matter what I did it stopped while attempting to create a ntfs or fat32 partition...

still didn't find a solution...

cheers,
Matjaz

---

### Post by kurzon on 2009-08-09
I have the exact same problem. Still couldn't find any solution.

---

