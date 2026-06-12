---
title: "Using a Windows XP client to set permissions on a Samba share"
date: 2007-02-08
forum: Server Platforms
---

### Post by Wendellz on 2007-02-08
Any ideas on how to use a Windows XP client (in an active directory environment) to set permissions 

on a folder or file located on a Linux Server running Samba? I'm looking for a way similar to how a WinXP client sets permissions on folders on a windows file server(GUI)...right -clicking on the folder icon, setting the permissions, and having the permissions stay set on the samba share. I''m part of a team that is researching different possibilities....however, we're looking for other options....Any suggestions?

---

### Post by Brazen on 2007-02-08
In an Active Directory environment, setting permissions through the regular Windows gui "just works."  You don't have to do anything special; you set permissions just like it was a Windows share.

However, in a standalone environment (ie, no Active Directory) this is not the case.

---

### Post by Wendellz on 2007-02-09
First ...thanks for the reply to my post!

I understand what you're saying; however, we want to prepare for possible issues with the shares on our network...ie: "...but Samba doesn't seem to translate actions in the Windows permissions editor to changes in the Unix permissions perfectly all of the time, so sometimes weird things happen (eg. removing Everyone from a file doesn't always work, CREATOR GROUP and CREATOR OWNER are added sometimes, etc.)..."

see link below - [http://www.bluelightning.org/linux/samba_acl_howto/](http://www.bluelightning.org/linux/samba_acl_howto/)

I've just received this from the CentOS development team:

You will need to enable / mount your samba partition with posix ACLs to have the permissions 

controls you want.

[http://mirror.centos.org/centos/4/docs/html/rhel-sag-en-4/ch-acls.html](http://mirror.centos.org/centos/4/docs/html/rhel-sag-en-4/ch-acls.html)

You will also need to ensure that the following is ON in your smb.conf:

nt acl support = Yes

***Haven't had the change to test this yet, but it looks promising.<<

---

