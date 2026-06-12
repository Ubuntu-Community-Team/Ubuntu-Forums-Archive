---
title: "How can limit the home directory size and change its location?"
date: 2008-10-01
forum: Server Platforms
---

### Post by grs on 2008-10-01
When I user is created there is a home directory to go with that user located at /home/grs The home directory, from what I can tell, has no size limit. How can I impose a limit of say 10GB per user, or allow some users have unlimited storage space and other have the restrictions.

The home dorectory is created on the same drive as the OS, how can set the home directory to another drive I have mounted at /mnt/sdd1?

---

### Post by lykwydchykyn on 2008-10-01
1. Do a search on "Ubuntu disk quotas".  You'll get tons of howtos on how to set up disk quotas.  Here's a good one:  [http://computingtech.blogspot.com/2008/09/ubuntu-linux-disk-quotas.html](http://computingtech.blogspot.com/2008/09/ubuntu-linux-disk-quotas.html)

2. Instead of moving the home directory to /mnt/sdd1, the better way is to mount your sdd1 to /home:
 - For best results, do this in recovery mode (runlevel 1)
 - mount /mnt/sdd1
```

mount /dev/sdd1 /mnt/sdd1

```
 - move all of the contents of /home to /mnt/sdd1
```

mv /home/* /mnt/sdd1/

```
 - Edit fstab so that /dev/sdd1 mounts at /home.  Just find the line containing /mnt/sdd1 and change that to /home
 - mount /home with the command "mount /home"
 - make sure your files are now under /home
 - reboot

---

### Post by grs on 2008-10-01
So I should add the following to /etc/fstab

```

/dev/sdd1      /home         ext3    defaults        1 2

```

After this everything within /home will now be on /dev/sdd1 instead of /dev/sda1 I understand what happening now!

How do I access recovery mode?

---

### Post by lykwydchykyn on 2008-10-01
I think it's a boot option (unless I'm getting confused with debian), press 'ESC' during boot to see the boot menu.   

Or, switch over to a virtual terminal (if you have a GUI) and type:
```

sudo init 1

```
This will drop you to runlevel 1 (single-user mode).  You'll get a "Recovery Menu" from which you select "root shell".

---

### Post by grs on 2008-10-01
> **lykwydchykyn said:**
> I think it's a boot option (unless I'm getting confused with debian), press 'ESC' during boot to see the boot menu.   

Or, switch over to a virtual terminal (if you have a GUI) and type:
```

sudo init 1

```
This will drop you to runlevel 1 (single-user mode).  You'll get a "Recovery Menu" from which you select "root shell".

Is this standard accross Linux? I'm actually using Clarkconnect, based on Red Hat Enterprise.

I've been reading several guides about quotas, its going to take me a while to work it out.

---

### Post by lykwydchykyn on 2008-10-01
Pretty much, about the only thing that would change is that some distros don't configure sudo by default, so you may have to "su" to a root prompt.  Also the boot menu may be different.

init is pretty consistent, and on every linux I've ever seen runlevel 1 is single-user mode.  The only reason I say you need to go to runlevel 1 is that /home cannot have any open files or directories when you do this.  If you log in as any other user but root, it will open files in /home.  On Ubuntu you can't log in directly as root except in runlevel 1 (unless you mess with the default security setup).

If you can login directly as root on your distro, that may be good enough.  But going to runlevel 1 is safer.

---

### Post by grs on 2008-10-01
I guessed it was to make sure no files were in use.
I run the CC box headless but when I do access it, it is through root user. I normally connect to it with PUTTY and WinSCP.

I found a good guide for quotas at 
[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/ch-disk-quotas.html#s1-disk-quotas-configuring](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/ch-disk-quotas.html#s1-disk-quotas-configuring)
Seems straight foward enough. Frist set the home directory to be controlled by quota, then create users and assign quotas.

---

### Post by windependence on 2008-10-02
> **lykwydchykyn said:**
> Pretty much, about the only thing that would change is that some distros don't configure sudo by default, so you may have to "su" to a root prompt.  Also the boot menu may be different.

init is pretty consistent, and on every linux I've ever seen runlevel 1 is single-user mode.  The only reason I say you need to go to runlevel 1 is that /home cannot have any open files or directories when you do this.  If you log in as any other user but root, it will open files in /home.  On Ubuntu you can't log in directly as root except in runlevel 1 (unless you mess with the default security setup).

If you can login directly as root on your distro, that may be good enough.  But going to runlevel 1 is safer.

You'll be surprised as I was that in Ubuntu, the standard run levels don't apply unless you set them up that way. I know, it's weird for those of s who have used non-debian based distros but in fact it isn't standard across all distros. Just FYI. So what you would think would be run level 3 won't be. I'm not sure if runlevel 1 is what we would expect or not either.

-Tim

---

### Post by lykwydchykyn on 2008-10-02
I've been using Debian for almost 5 years.  Runlevel 1 is single user mode.  I confirmed this before I gave it as advice.

---

