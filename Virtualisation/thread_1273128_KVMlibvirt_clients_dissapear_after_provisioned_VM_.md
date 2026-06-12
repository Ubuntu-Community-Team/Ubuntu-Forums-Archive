---
title: "KVM/libvirt clients dissapear after provisioned VM shuts down"
date: 2009-09-23
forum: Virtualisation
---

### Post by freakalad on 2009-09-23
Sometimes I need to port VM systems between my home & work systems.

I can do this simply by making use of a script that brings the running systems down (or "destroy" if it's stubborn), makes a copy of the image & does a "dumpxml" of the system in question's config data to a portable XML file.
I then simply take these copies with me & make use of "virsh create xyz.xml" to recreate the system on the new server (if necessary).

So far, so good. Works pretty well.

Unfortunately the VM disappears from virsh/virt-manager once I'm done with the system (but this can be easily addressed by simply re-running the "virsh create xyz.xml" command)

Issue is not universal, since some of the systems remain after I've manually created them, so I doubt it's related to permissions.
Only seems to affect VM's provisioned using the "virsh create xyz.xml" method

Don't know if this is a bug (in which case I'll report it), or if it's an oversight on my part.
Pretty sure my permissioning is right; data owned by "me:libvirtd" (where "me" is part of libvirtd group), & chmod is 664

---

### Post by freakalad on 2009-10-02
doh! problem solved

`virsh define`, not `virsh create`

---

