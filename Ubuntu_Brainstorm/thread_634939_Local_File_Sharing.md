---
title: "Local File Sharing"
date: 2007-12-08
forum: Ubuntu Brainstorm
---

### Post by thewarlock on 2007-12-08
Currently, there is no easy way to share files properly between local users.

Using ACLs you can set up a shared directory  (lets call it /shared for this)  and set permissions so that files CREATED in there are RWX for the users you want.

The problem is, that users who create files in say, their /home/user/Documents/   then go "oops" and copy it over, the permissions are NOT changed by default.  Same if they download something, then realize they didn't to the "save as" to the right spot (or at all)

Currently I can get around this with a reboot and a line in rc.local to set the permissions the way it's needed, but having to reboot isn't really a good option.

Using a samba share could also get around this, but when it's just one machine (no home network) and 2 users, this isn't optimal.

Now having the basic  cp and mv commands include this would be more difficult to change (and I can do this with an alias anyway), but having the graphical file managers do it would be better. (this is what the users would use anyway)

I've searched high and low, and it appears that you currently CANNOT copy files into a shared folder and have them changed automagically.

How hard would it be to have Nautilus check the permissions for the destination directory and set them on the file being copied automatically?  I should think this would be the default (at least change the group permissions, leaving the owner alone would be fine)

---

### Post by smartboyathome on 2007-12-08
I don't think that should be default, because of one glaring security hole: ROOT FILES BEING COPIED TO YOUR /HOME AND THEN BEING ABLE TO BE MODIFIED. This could have the consequence of a program becoming a security target.

---

### Post by thewarlock on 2007-12-12
> **smartboyathome said:**
> I don't think that should be default, because of one glaring security hole: ROOT FILES BEING COPIED TO YOUR /HOME AND THEN BEING ABLE TO BE MODIFIED. This could have the consequence of a program becoming a security target.

Well, you have to have access to the files to begin with.
If I have enough access to copy them, then I can also change the permissions.  Or, I can read the file, copy the contents to another file with my own permissions.

Right now I can accomplish the same thing automaticaly with a script in rc.local. This runs automatically and changes the perimissions on the shared folder on every reboot.

I just want to be able to eliminate the reboot step.

If I go through the trouble of setting up ACLs for a directory, then why not have it change whatever goes in there (copying I mean)

I fail to see how this will compromise security in any way.

---

### Post by coolen on 2007-12-12
If root files are copied there and modified, I fail to see how this could affect the rest of your system. It's not like the kernel goes through the entire filesystem looking for, say, your xorg.conf, and goes with whatever it finds. As long as only root can copy the file back to the original location, it shouldn't be a problem. Also, I assume root would still be the only user allowed to copy files to which other users have no read access.
These things could be ironed out in the development, anyway. I think this would be a good idea, personally. A shared space for the whole family. A little UI integration idea: an option to share files/directories? It could place a symlink in the shared directory, and change the individual file's permissions appropriately, or perhaps just copy it straight over. Saves you having to navigate to the shared folder to share a file.

---

### Post by smartboyathome on 2007-12-12
> **coolen said:**
> If root files are copied there and modified, I fail to see how this could affect the rest of your system. It's not like the kernel goes through the entire filesystem looking for, say, your xorg.conf, and goes with whatever it finds. As long as only root can copy the file back to the original location, it shouldn't be a problem. Also, I assume root would still be the only user allowed to copy files to which other users have no read access.
These things could be ironed out in the development, anyway. I think this would be a good idea, personally. A shared space for the whole family. A little UI integration idea: an option to share files/directories? It could place a symlink in the shared directory, and change the individual file's permissions appropriately, or perhaps just copy it straight over. Saves you having to navigate to the shared folder to share a file.

There is a mini filesystem structure in your /home/username partition, and these files could be copied, modified, and then used on your account.

---

### Post by coolen on 2007-12-12
Which is why the shared folder would not be in your home account.

---

