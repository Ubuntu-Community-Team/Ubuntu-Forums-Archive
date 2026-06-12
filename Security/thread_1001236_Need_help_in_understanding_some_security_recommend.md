---
title: "Need help in understanding some security recommendations ...."
date: 2008-12-03
forum: Security
---

### Post by sefs on 2008-12-03
Hey there

I was reading this article....

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

... and the guy mentioned some things I could not understand....

They are...

Reconfiguring shared memory
tmpfs /dev/shm tmpfs defaults,ro 0 0 


Limiting access to the "su" program
sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su

Securing the Home directory
chmod 0700 /home/username

Can someone in the know explain what these commands actually do and are they really recommended.

Thanks.

---

### Post by user12021 on 2008-12-03
Ah, a fellow Digger, I presume?
Well the last one means that you, personally have rwx access to the contents of your home directory, while others have no access.
I believe the second to last one restricts which users can run "su" but i'm not too sure about that one.
And I have no idea about the first one, especially because I don't have the man page for it.

---

### Post by cariboo on 2008-12-03
Did you actually check the page that is linked in the article? There is a much better explanation of why these changes may be needed here:

[https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)

This page should help you decide whether you should make the changed or not.

Jim

---

### Post by lovinglinux on 2008-12-04
> **sefs said:**
> Securing the Home directory
chmod 0700 /home/username

This is something I have been thinking about for a few days. Should I chmod my home folder as suggested? Could this affect any programs or scripts that are launched by cron and write data to this directory?

The folders in the home directory currently have drwxr-xr-x permissions.

Should I chmod the home folder on another machine that I access via ssh to transfer files inside my LAN?

---

### Post by Sarmacid on 2008-12-04
> **lovinglinux said:**
> This is something I have been thinking about for a few days. Should I chmod my home folder as suggested? Could this affect any programs or scripts that are launched by cron and write data to this directory?That depends on which user launches the scripts. Every user has a different cron so if you launch them with yours, it should be ok.

> **lovinglinux said:**
> 
The folders in the home directory currently have drwxr-xr-x permissions.

Should I chmod the home folder on another machine that I access via ssh to transfer files inside my LAN?

Doing this would be the same as using chmod on your other pc. It would restrict access to other users but not to the one you give all privileges.

---

