---
title: "Add user to vsftpd"
date: 2008-04-10
forum: Server Platforms
---

### Post by billenium14 on 2008-04-10
I would like to set 5 users to 5 different directories on my server. They will have full access (write, delete, edit, rewrite,add and the whole nine yards). But i wont them to be locked inside that folder... As in they cannot go to other folders before that one... so they are locked in say /home/user and ever dir in /home/user.

Thank you!

Also, is there a way to make the ftp server look nicer? Like instead of it looking like a folder type thing, make it have a nice look that goes with a site... Thanks!

---

### Post by Rafa.Supr on 2008-04-28
In the vsftpd.conf you have some options for it, maybe you uncomment it and set YES to NO. 

> # You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list

---

