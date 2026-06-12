---
title: "My Ubuntu Guest wont let me mount shared folders!!!!!"
date: 2009-07-27
forum: Virtualisation
---

### Post by Bluehotdog5 on 2009-07-27
Host: Windows Vista Home Edition
Guest: Ubuntu 8.10
VM software: Virtualbox by Sun

I'm trying to share my public Documents folder in Vista with Ubuntu. so I have it configured with the name 'Documents'
I tried this command:

sudo mount -t vboxsf Documents /home/russell/desktop

but I got this Error:

/sbin/mount.vboxsf: mounting failed with the error: No such file or directory

I also tried this command:

sudo mount.vboxsf Documents /home/russell/desktop

and yet again got another error:

mount.vboxsf: mounting failed with the error: No such file or directory

I'm really frustrated at this point. anyway What am I doing wrong?

---

### Post by Dedoimedo on 2009-07-28
Did you install Guest Addons ... BTW, why do you want to mount them to Desktop ...? Why not a more modest directory somewhere under the home directory ...?

Cheers,
Dedoimedo

---

### Post by ubu-for on 2009-12-11
> **Bluehotdog5 said:**
> I tried this command:

sudo mount -t vboxsf Documents /home/russell/desktop

but I got this Error:

/sbin/mount.vboxsf: mounting failed with the error: No such file or directory

I also tried this command:

sudo mount.vboxsf Documents /home/russell/desktop

and yet again got another error:

mount.vboxsf: mounting failed with the error: No such file or directory

I'm really frustrated at this point. anyway What am I doing wrong?
Today I had the same problem with a different folder name, but solved it!

You have to create the folder "/home/russell/desktop" at first, because the default name is "Desktop" and not "desktop".

---

### Post by joes7 on 2009-12-11
That is because you don't have enough permissions. Log in as "root" (it has no password, unless otherwise stated).

---

### Post by TJRC on 2010-12-24
I know this is an old thread, but since I had the same problem, I thought I'd document why I had the problem and what fixed it.

In my case, it turned out to be a version mismatch between the Virtualbox release installed on the Windows host and the VB guest additions installed on the Linux guest.  I was running VirtualBox 3.2.12 with guest additions 3.2.6.  Reinstalling the guest additions from the 3.2.12 CD image fixed it.

I installed VB 3.2.6 in June, and installed Lucid, with guest additions 3.2.6 at that time.   I wanted the enhanced video and shared clipboard features, but did not use shared folders at that time.

Sometime in November, I upgraded VirtualBox to 3.2.12.  The enhanced video and shared clipboard continued to work, so it never occurred to me to update the guest additions.

I first started trying to use shared folders a few days ago, and could not.  I got the same "No such file or directory" error listed above.  It worked on another system I had, and it also worked on a test Fedora install.  I decided to reinstall guest additions, just in case.  I was surprised to see in the install messages that my guest additions had been at 3.2.6.  In any event, after a reinstall of the guest additions and a reboot, everything works fine.

---

