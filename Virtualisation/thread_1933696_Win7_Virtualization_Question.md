---
title: "Win7 Virtualization Question"
date: 2012-02-29
forum: Virtualisation
---

### Post by ptmuldoon on 2012-02-29
I'm planning on a new build for my home server to a 'bigger' setup regarding cpu, ram, etc, and am thinking of the following, and hopeing somebody can lend some advice and tips.

I was planning to run Ubuntu Server (or Desktop) as the main OS on the system.  And than run Windows7 under a virtual setup.

Now, can you have the virtual system access the same shared/samba drives on your ubuntu installation?

Also, would I better off installing Win7 as the main OS, and than running Ubuntu as a virtual server?

I'm new to virtualization, so hope the above make sense,

---

### Post by UnknownFearNG on 2012-02-29
A quick Google search brought me to this link [here]("http://www.sysprobs.com/virtualbox-shared-folders-ubuntu-1010-guest-windows-7-host"). It's a full tutorial on how to share folders/files between the guest as Ubuntu and host as Windows 7. Should be identical if you want to do Windows 7 as guest and Ubuntu as the host.

---

### Post by ptmuldoon on 2012-03-08
UnknownFearNG..  

Thanks for the feedback.  I believe it should work find being able to share a drive/folder between the Virtual OS and the main OS. 

But do have another question.

If I am running Ubuntu Server as the main OS as a headless unit which has no GUI, Can I still install Windows as a Virtual OS and it will work correctly?  Or will the Virtual OS need a GUI on the main OS as well?

Edit:  I am uncertain if this helpful, but this may be how to use Win7 inside ubuntu server on a headless unit with no gui.
[http://fileformat.wordpress.com/2007/11/19/vmware-server-on-a-headless-debian-etch/](http://fileformat.wordpress.com/2007/11/19/vmware-server-on-a-headless-debian-etch/)

---

### Post by nothingspecial on 2012-03-09
*Thread moved to **Virtualization**.*

---

### Post by UnknownFearNG on 2012-03-11
> **ptmuldoon said:**
> 
If I am running Ubuntu Server as the main OS as a headless unit which has no GUI, Can I still install Windows as a Virtual OS and it will work correctly?  Or will the Virtual OS need a GUI on the main OS as well?

I have never ran Ubuntu Server so I am not sure how to help with with this question. I'll leave this open for discussion with someone else.

---

