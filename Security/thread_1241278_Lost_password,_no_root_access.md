---
title: "Lost password, no root access"
date: 2009-08-15
forum: Security
---

### Post by DnDer on 2009-08-15
What are my options? Went back to Xubuntu to play around and learn more for the first time in... too long. I'm sure I changed the root pw for security, and I don't remember the one I had for the single user I created (me).

Can I get in anymore? Or do I need to just re-install and wipe the old stuff, since there was nothing there, anyway?

---

### Post by john stiles on 2009-08-15
Sounds like a reinstall, but unless you encrypted the drive/files you can manually partition the install and save your home directory. At the partition stage, choose manual and set the root as your current drive, but unclick the format box. The install will copy over the system files but leave your home untouched. The newer ubuntu editions even prompt for this "import". No data loss at all, just reload any extra programs again to be back where you started. I've done this about a dozen times with various machines for various reasons. Works a charm.

---

### Post by stlsaint on 2009-08-15
yes...agreed go thru the re-install and i know in jaunty you will be asked to import any users and just choose whoever "you" was on the old profile!

---

### Post by wojox on 2009-08-15
Try this:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bodhi.zazen on 2009-08-16
You can reset your password with any live CD or if you are running linux.

I will assume your xubuntu partition is /dev/sda1 , adjust accordingly if it is an alternate partition.

```
sudo mount /dev/dsa1 /mnt
sudo chroot /mnt bash #This will give you a root shell in Xubuntu

ls /home
passwd user #set a new password
exit

```

Reboot to xubuntu.

And as this shows, there really is no need to set a root password, it does not increase security to do so, in fact it lessens security.

---

### Post by Mariane on 2009-10-09
Thanks wojox you've just saved my life with this link!

---

