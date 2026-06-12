---
title: "Running a server on a machine setup for dual booting."
date: 2007-09-03
forum: Server Platforms
---

### Post by Sephoroth on 2007-09-03
I am running a server on a Windows machine that also has Ubuntu installed.  I want it to be able to be able to host it while on either of the 2 OS's but the server requires a MySQL database which is hosted on the same machine.  I was wondering if I would be able to use the same MySQL database located on the Windows partition (and if so, how?).  If not, is there any other way to do this?

---

### Post by HermanAB on 2007-09-04
Install VMware/Virtualbox and install the guest OS in that.  Then you can simultaneously run Windows and Linux on a single machine - it will feel like you have two machines in one box.

Dual booting is yesteryear...

Cheers,

Herman

---

### Post by Sephoroth on 2007-09-04
Thanks for the fast reply.

Though that isn't a bad suggestion, I was hoping to not have to do that since I would prefer not having to use as many recourses and I would enjoy keeping Ubuntu's natural stability and low memory consumption.  There will also be multiple people using the computer who may be unfamiliar with the GNOME environment and would just rather use Windows.

Any other methods/suggestions?

---

### Post by KCPokes on 2007-09-04
MySQL is a service, thus if it was installed on one of the machines that isn't booted, its not going to be accessible.  Building a "server" on a machine that gets booted a lot, in general, is not typically the best approach.  The only option I could really foresee you pursuing would be to set up MySql in Windows, on a FAT partition, that you could then access via Ubuntu when you booted.  The data would be shared but each instance would have to have a MySQL service running using the shared mountpoint.  I'd hate to venture what kinds of issues you could run into moving back and forth, besides even getting it to work, but its an option.  

The virtual machine in Ubuntu is a far better option.  Of course it depends on what flavor of Windows you are running.

---

### Post by Brazen on 2007-09-04
theoretically, you should be able to install the ntfs driver in Ubuntu and MySQL server and serve up the same database files.  I'm not sure about the folder structure of a MySQL install on Windows, but you MIGHT be able to just (mount the drive and) symlink the "Program Files/MySQL-whatever" directory into /var/lib/mysql and start up the service and see what happens.  I would have a look over the default directory structure under /var/lib/mysql and compare it too what is under the Program Files directory in Windows (or wherever it stores the databases) to make sure the structures are similar.  Otherwise you might symlink the individial database files where they need to go.

---

### Post by KCPokes on 2007-09-04
> **Brazen said:**
> theoretically, you should be able to install the ntfs driver in Ubuntu and MySQL server and serve up the same database files.  I'm not sure about the folder structure of a MySQL install on Windows, but you MIGHT be able to just (mount the drive and) symlink the "Program Files/MySQL-whatever" directory into /var/lib/mysql and start up the service and see what happens.  I would have a look over the default directory structure under /var/lib/mysql and compare it too what is under the Program Files directory in Windows (or wherever it stores the databases) to make sure the structures are similar.  Otherwise you might symlink the individial database files where they need to go.

I was curious as to the stability of the NTFS drivers, for writing at least.  There always seemed to be a question as to how usable they'd be in a real time application.  I suppose if you are trying to do something like this, might as well throw in NTFS to make it even more fun.  :)

---

### Post by Brazen on 2007-09-04
KCPokes: I have not personally used it, but I here it currently works as reliably as any other file system driver.  Other than that, I can point you to the result of a quick goolgle search I did: [http://www.ntfs-3g.org/quality.html](http://www.ntfs-3g.org/quality.html)

---

### Post by hellonull on 2007-09-04
> **KCPokes said:**
> MySQL is a service, thus if it was installed on one of the machines that isn't booted, its not going to be accessible.  Building a "server" on a machine that gets booted a lot, in general, is not typically the best approach.  The only option I could really foresee you pursuing would be to set up MySql in Windows, on a FAT partition, that you could then access via Ubuntu when you booted.  The data would be shared but each instance would have to have a MySQL service running using the shared mountpoint.  I'd hate to venture what kinds of issues you could run into moving back and forth, besides even getting it to work, but its an option.  

The virtual machine in Ubuntu is a far better option.  Of course it depends on what flavor of Windows you are running.

I am doing something similar to what KCPokes is talking about. I have the document/data roots for both Apache and MySQL pointing to a folder that is on a third partition (FAT32 filesystem). The one issue that I have is that trying to access "localhost" via my browser in Ubuntu returns a "403 Forbidden" error. Once I get the permissions issue solved everything should be fine.

---

