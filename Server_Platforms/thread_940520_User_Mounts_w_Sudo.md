---
title: "User Mounts w/ Sudo?"
date: 2008-10-07
forum: Server Platforms
---

### Post by chrispottrell on 2008-10-07
Hi guys,

I've got 35+ ldap users logging into a central Ubuntu Server where their profiles live.

I have a script that is run each time they login that does various things, ie let me know their IP/Who is sat where etc..

I'm looking to temporarily mount a Samba share in /mnt/Artwork on each machine for a couple of weeks so i've added some code that will do this in the login script.

My problem is that the umount/mount command requires Sudo, as the users have little rights on the client machines.

I've read that you can add stuff to the /etc/sudoers file, would I have to do this to EACH client? Or is that on the server that they authenticate against. I don't really want to go around each machine and edit /etc/fstab :\

Any ideas are greatly appreciated.

---

### Post by chrispottrell on 2008-10-07
Anyone have any insight to this at all?

Is there a temp way a mount can be added as a user?

If it helps I have used RickyJones' openldap/samba tutorial. All the users are in the Domain Users group, perhaps tehre is a way I can 'allow' users to mount things via group properties in openldap?

---

### Post by lykwydchykyn on 2008-10-07
Are you using the mount command or the smbmount command?  The latter typically does not require sudo, as long as the mountpoint is writeable by the user.

---

### Post by chrispottrell on 2008-10-08
Would this be easier to just create a key/relationship between the server and all the clients.

Then just SCP the new /etc/fstab?

---

### Post by lykwydchykyn on 2008-10-08
I guess you could do that, but you shouldn't need to.  If you use smbmount instead of mount and use a mountpoint the users control (say ~/Artwork), you should be able to do it in the login scripts as is.

---

