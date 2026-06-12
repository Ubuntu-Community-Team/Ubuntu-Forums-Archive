---
title: "ssh, pgp, pidgin keys on usb drive ONLY - and maybe thunderbird"
date: 2009-10-19
forum: Security
---

### Post by bcn17 on 2009-10-19
I have been trying to figure out how to put my private keys on a removable drive so that they are not just sitting on  my computer. 

I managed successfully to put my ssh private key on my thumbdrive, edit my fstab so that my thumbdrive always mounts to the same directory, and edit the /etc/ssh/ssh_config file to look for my private key on the thumbdrive. It works great. 

I have been able to find my pgp key at: /home/username/.gnugp/secring.pgp 
( I am assuming it is this although for some reason I cannot open it in a text editor similar to my ssh key) 

and I can find my pidgin key at: /home/username/.purple/otr.private_key 
readable in plain text) 

However, I cannot figure out how to instruct pidgin and seahorse to look (and it would be convenient to create/save) for my private keys in a specific directory- my usb drive. 

Any help would be much appreciated. 

Also, if you know how to direct thunderbird to look at a usb drive that would be really convenient as well.

---

### Post by Lars Noodén on 2009-10-19
One way, of several, would be if the drive is always mounted at the same mount point, to make a symbolic link to it and call that .gnupg
Works also for specific files.

e.g.
```

# directories
ln -s /media/bcn17-usb/gnupg /home/bcn17/.gnupg
ln -s /media/bcn17-usb/ssh   /home/bcn17/.ssh

# individual file
ln -s /media/bcn17-usb/purple/otr.private_key /home/username/.purple/otr.private_key 

```

Another option, which is a guess, could be to have the various directories you have in mind mounted from disk images stored on the usb key.  

```

# preserve the old directory as it is
mv /home/bcn17/.ssh /home/bcn17/.ssh.orig
# new directory, useless except as a mount point
mkdir --mode 0000 /home/bcn17/.ssh

# prepare an unencrypted disk image
dd if=/dev/zero of=/media/bcn17-usb/ssh.img bs=1k count=2048

mkfs -t ext3  /media/bcn17-usb/ssh.img 

mount -t ext3 /media/bcn17-usb/ssh.img /home/bcn17/.ssh

cd /home/bcn17/.ssh.orig

tar cpf - |*( cd /home/bcn17/.ssh ; tar xpf - )

umount /home/bcn17/.ssh

```

Obviously the order in /etc/fstab is important.  Some lines in sudo might help too.

Also, the loop example above does not use encryption.  For that see the packages cryptsetup and cryptmount.

---

