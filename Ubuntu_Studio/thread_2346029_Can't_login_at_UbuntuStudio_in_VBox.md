---
title: "Can't login at UbuntuStudio in VBox?"
date: 2016-12-10
forum: Ubuntu Studio
---

### Post by benny74402 on 2016-12-10
I've tried some combinations but it keeps asking me a valid password. My version is 16.04, I'm trying to run it inside VBox under Win10 at a Toshiba Satellite L555. I also tried many of the files that one can see after Mounting the iso file to check if that info was contained there in a readable manner but failed. I know I've seen that info somewhere but can't recall where.

Does anybody around could tell what are the Username & Password that Ubuntu Studio awaits for starting to show a desktop? Thanks in advanced!

---

### Post by kpatz on 2016-12-10
It should have asked you to select a login name and password when you installed it.

---

### Post by benny74402 on 2016-12-10
Thank you kpatz for replying!

Normally, it should ask such but since this's a virtual installation somehow it never asked

My question is still the same: what are those for Ubuntu Studio? These are, normally, set to something like Ubuntu (for the username) root (for the password) aor something like these...

Do you know?

---

### Post by kpatz on 2016-12-10
The only account that is created when installing an Ubuntu distro is the one you select during the install.  The root account is disabled by default.

Now maybe Ubuntu Studio is different?  I would think it would let you select a username and password on install.  Running in a virtual machine should make no difference.  I'm downloading it now to try in virtualbox.

EDIT: Yes, UbuntuStudio prompts you for a user name/password just like any other Ubuntu install.

If you forgot what it is, you can always reinstall from the ISO, or boot from the ISO and look at /mnt/etc/passwd after mounting the root partition to /mnt to get the account name.  If you don't know the password, you can chroot the /mnt and use passwd to change the password.

---

### Post by benny74402 on 2016-12-12
Thanks for replying, kpatz!

Yes, I uninstalled my previous Studio VMachine & reinstalled a new one because all I had on the screen was garbled. Now, the first thing it asks for is a pwd. Tried with my Windows machine acct pwd, root, linux, [nothing] but all failed.

Think I've stated that have looked for that pre-configured pwd but have found nothing. If it's asking for a new pwd then it shouldn't complain unless I use an invalid character; if it's asking for a pre-determined pwd then I should have had that info prior to any kind of installation.

The only thing that might be considered a bug is that it's asking for a pwd but dealing with it as if it's a username...

Any ideas?

Edit: my version is ubuntustudio-16.04.1-dvd-amd64.

---

