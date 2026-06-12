---
title: "lock user in home dir?"
date: 2009-10-01
forum: Server Platforms
---

### Post by 5millp0x on 2009-10-01
Hello, I have a svn user on the server, that also can get Shell access using putty, and that is all good but i want to be able to prevent the user from "cd" to anything below "/home/" 
or even look it inside the /home/svn/ folder?   

Thanks

---

### Post by peetbull on 2009-10-01
If I understand your request correctly, this user you refer to must belong in a group without execute privilege in no folder other than their home directory.

As a good starting point, you might create a group specific to that user, remove all other group associations it might have and give them execute permission in home directory.

A link that might help is: [http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html](http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html)

I should warn you, though, that changing privileges might cause some issues in a already configured production environment, so I highly suggest experimenting on a test user account first.

If you need specific commands for your work let us know.

---

### Post by windependence on 2009-10-01
Best way for this would be to jail the users:

[http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html](http://www.cyberciti.biz/tips/howto-linux-unix-rssh-chroot-jail-setup.html)

[http://www.ericstockwell.com/?p=54](http://www.ericstockwell.com/?p=54)

[http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)

[http://jblevins.org/computing/linux/ubuntu-chroot](http://jblevins.org/computing/linux/ubuntu-chroot)

-Tim

---

