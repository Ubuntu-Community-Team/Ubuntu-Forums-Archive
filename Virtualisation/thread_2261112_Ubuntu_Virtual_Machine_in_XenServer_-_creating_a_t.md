---
title: "Ubuntu Virtual Machine in XenServer - creating a template (cloning)"
date: 2015-01-16
forum: Virtualisation
---

### Post by Stan_1936 on 2015-01-16
Hi,

I am working with XenServer 6.2. I have created an Ubuntu Virtual Machine (VM) and am looking to now convert this into a template. I will want to then use the template to create multiple clones of the first VM.

As per this(pg. 18, section 4.3, second paragraph), XenServer requires a utility called SysPrep:
[http://support.citrix.com/servlet/KbServlet/download/34965-102-704217/QuickStartGuide_BasicVersion.pdf](http://support.citrix.com/servlet/KbServlet/download/34965-102-704217/QuickStartGuide_BasicVersion.pdf)

In Ubuntu, a tool called virt-sysprep is available through a package called libguestfs:
[http://manpages.ubuntu.com/manpages/precise/man1/virt-sysprep.1.html](http://manpages.ubuntu.com/manpages/precise/man1/virt-sysprep.1.html)
The way that sysprep works in Windows is shown in this video (from 12:25-13:25): [https://www.youtube.com/watch?v=hK0P6I-JPgo](https://www.youtube.com/watch?v=hK0P6I-JPgo)

I have installed libguestfs as per:
[http://askubuntu.com/questions/432562/how-to-install-python-guestfs-and-libguestfs-tools-in-python-virtual-environment](http://askubuntu.com/questions/432562/how-to-install-python-guestfs-and-libguestfs-tools-in-python-virtual-environment)

Instructions are shown here for setting it up (I have not yet done this step):
[http://libguestfs.org/guestfs-faq.1.html](http://libguestfs.org/guestfs-faq.1.html)

But, how do I use sysprep in Ubuntu? I need to somehow shut down Ubuntu "gracefully" and get it ready for cloning.

How do I use virt-sysprep in Ubuntu?

---

