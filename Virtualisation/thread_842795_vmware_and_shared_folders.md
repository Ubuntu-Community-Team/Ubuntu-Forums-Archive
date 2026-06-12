---
title: "vmware and shared folders"
date: 2008-06-27
forum: Virtualisation
---

### Post by jonlemur on 2008-06-27
Okay, I've done a lot of searching for how to do this, but everything that I've found is for a significantly different setup.  I'm sorry if this is a redundant post, but I haven't been able to find the answers I'm looking for yet. 

Here's the setup
I'm running Ubuntu on Hardy Heron.
I installed vmplayer 2.0.4
I'm trying to get a console-only (no GUI) RedHat 7.3 to be able to access files on the host system.  

I see under Player on the vmplayer window that there is a place to add shared folders.  I click "Always enabled" but I don't get any options under the **Folders** dialog like I assume I should.

I have a shared folder set up on the host in my home folder that everyone should be able to access.

What else do I need to do?

Also, is there a way for me to ssh (or something similar) from my host computer into the guest OS?  If so, what do I need to do for that?

Thanks

---

### Post by bodhi.zazen on 2008-06-27
IMO best to use a network protocol.

samba : [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)


sshfs : [http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

Other options include http, nfs, ftp ...

Once you learn a network protocol it seem easier then shared folders and works with virtualization and in the real world :twisted:

---

### Post by jonlemur on 2008-06-27
Thanks.  I followed the guide labeled samba until I got to the Windows part.  Now I'm not sure what to do.  I still don't see anything under the Folders section of the Shared folders part.  The vmware help tutorial said that shared folders would be mounted under /mnt/hgfs on the guest OS, but nothing is showing up there.  Is there something else I have to do (it can only be from the command line) on the guest OS that would be similar to the Windows section of that tutorial?

---

### Post by bodhi.zazen on 2008-06-27
You need to mount the samba share on the guest (assuming your samba server is on the host).

For windows guests see the section "Connecting to the share from within Windows".

For linux guests you can browse the network or in the gnome menu select "connect to a server". Put in your host IP , share name, user name, and password.

---

### Post by jonlemur on 2008-06-27
Can you explain how I mount it in the guest OS using only the command line?

I found this on another [thread]("http://ubuntuforums.org/showthread.php?t=582319")

```
mount -t cifs //server01/multimedia /home/username/network/multimedia -o username=username,uid=username,gid=groupname,file_ mode=0640,dir_mode=0750,iocharset=utf8
```

If this is the kind of thing I need to do, how can I find out what I need to put in these fields?

I've been using Ubuntu for some time now, but this networking protocol is very new to me.

---

### Post by bodhi.zazen on 2008-06-27
Yes, that is the command to use on the command line or fstab.

You may need to install some software on Fedora, I am not sure ...

On an Ubuntu guest Ubuntu you need to install smbfs :

```
apt-get install smbfs
```

cifs is part of the smbfs package :)

The basic syntax is :

mount -t cifs //server/share /mount/point -o user=samba_user

But you must either use the server ip address or add the server to /etc/hosts to use the name.

See if this helps : [uwiki]ComprehensiveSambaGuide[/uwiki]

[uhelp]community/SettingUpSamba[/uhelp]

---

### Post by bodhi.zazen on 2008-06-28
FYI: On Fedora, cifs is in the "samba-client" package.

---

