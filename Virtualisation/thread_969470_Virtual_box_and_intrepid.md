---
title: "Virtual box and intrepid"
date: 2008-11-03
forum: Virtualisation
---

### Post by Robbyx on 2008-11-03
Having upgraded to Intrepid, VB no longer loads at startup. Does this mean that I have to reinstall VB with the intrepid version?

---

### Post by FAMUgolfer on 2008-11-03
I'm guessing that you mean VB doesn't load up whatever OS you are trying run?  If this is the case, just reinstall VB via the website [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).  I had this same problem and after reinstalling it with the key (it's on the webpage) VB worked just like it did in Hardy.  

P.S. there isn't an intrepid repo yet for VB so just add the hardy one instead.

---

### Post by snowpine on 2008-11-03
I just installed virtualbox on intrepid using synaptic. It was incredibly easy, much easier than I remember the process being with hardy (I didn't have to find any kernel modules or add myself to a user group).

---

### Post by uidb4056 on 2008-11-03
> **FAMUgolfer said:**
> I'm guessing that you mean VB doesn't load up whatever OS you are trying run?  If this is the case, just reinstall VB via the website [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).  I had this same problem and after reinstalling it with the key (it's on the webpage) VB worked just like it did in Hardy.  

P.S. there isn't an intrepid repo yet for VB so just add the hardy one instead.

Even the web page doesn't show intrepid repository it's already existing and running, just replace 'Hardy' with 'Intrepid' I've upgraded my previous install of 2.04 from Hardy to the same version for intrepid and it runs OK.

---

### Post by Robbyx on 2008-11-03
I have the  i386 version working in Intrepid. The download source had changed from my original entry. I also needed to save the key to my Hard disk and load it into the update manager.

Thanks for helping.

There is this comment on the VB web site:

> Note: Ubuntu users might want to install the dkms package (not available on Debian) to ensure that the VirtualBox host kernel module (vboxdrv) is properly updated if the linux kernel version changes during the next apt-get upgrade. 

Is it a big deal to follow this advice? I can see no guidance on the site as to what to do.

---

### Post by uidb4056 on 2008-11-03
> **Robbyx said:**
> I changed the repository detail for vb from hardy to intrepid and there was a report that it could not download all repository indexes when I let the software manager update the software.

Sorry I forget to say that I'm using VBox AMD64 on 64 bits 8.10. I've no tested with i386 packages.

---

### Post by DoDoENT on 2008-11-04
> **Robbyx said:**
> 
There is this comment on the VB web site:

Is it a big deal to follow this advice? I can see no guidance on the site as to what to do.

DKMS is now part of 2.6.27 kernel and it is not necessary to install it separately.

---

