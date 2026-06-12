---
title: "weird file sharing permission issue"
date: 2008-07-16
forum: Virtualisation
---

### Post by frogotronic on 2008-07-16
Hello,

I cannot seem to get my samba share from my Guest WindowsXP to my Ubuntu 8.04.1 host to work.

At one point it was working, then I had a file permissions issue with my .dmrc file; which I fixed with this post: [http://ohioloco.ubuntuforums.org/showpost.php?p=2340094&postcount=8](http://ohioloco.ubuntuforums.org/showpost.php?p=2340094&postcount=8)

Then there was a kernel upgrade and I had to recompile VMWARE, but I suggested to keep my network settings.

Then my samba share stopped working.  I orginally set it up via this post: [http://ubuntuforums.org/showthread.php?t=652640](http://ubuntuforums.org/showthread.php?t=652640)

I cannot seem to access the "sharer" drive.

BUT I can see the "sharer" drive from my WindowsXP guest OS (see screenshot below).  I think its my file permissions on my Host (Ubuntu).  How do I change them "back" to "default"?  Does the home directory have the wrong permissions?

Any help would be appreciated...

- CH    :confused:

---

### Post by fjgaude on 2008-07-17
Within Ubuntu do you have your hosts file showing the right IP address?

If you handle the .dmrc file permissions correctly then your /home should be okay.

While in Ubuntu in Nautilus what does the folder shares show?

---

### Post by frogotronic on 2008-07-18
> **fjgaude said:**
> Within Ubuntu do you have your hosts file showing the right IP address?

Would that information be listed in my smb.conf file?

```
If you handle the .dmrc file permissions correctly then your /home should be okay.
```

I think I changed the entire /home directory...to 775...I think the default is 700?

```
While in Ubuntu in Nautilus what does the folder shares show?
```

I set the share properties on the "sharer" folder manually via the smb.conf file.  The permissions on the /home folder are for me only.  Is this your question?  I'm unclear as to what you are asking.  Do I set the share permissions via the GUI?

- Thanks

---

