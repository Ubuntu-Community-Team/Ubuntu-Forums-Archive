---
title: "HOWTO: Blowfish passwords &amp;&amp; password checks"
date: 2006-11-15
forum: Tutorials
---

### Post by NiN on 2006-11-15
Ubuntu uses per default md5 hashed passwords.
md5 is a 128bit hash and nowadays not too secure anymore.
[http://en.wikipedia.org/wiki/Md5](http://en.wikipedia.org/wiki/Md5) has a description of hash collisions.

There is support for an alternate hash, blowfish. This has proven quite secure in openbsd.

To enable it, you have to install libpam-unix2.
```

apt-get install libpam-unix2

```

Next replace all references of pam_unix.so with pam_unix2.so in all files under /etc/pam.d

Note: The number of references in the files depends on installed pam modules.

In common-password add the following:
```

password required      pam_unix2.so nullok use_authok obscure min=9 max=72     blowfish

```

To enable password checks when changing passwords, install
libpam-passwdqc
and add the following to your /etc/pam.d/common-password:
```

apt-get install libpam-passwdqc

```
edit /etc/pam.d/common-password and add
```

password required      pam_passwdqc.so max=72 similar=deny enforce=everyone retry=2 ask_oldauthtok=update check_oldauthtok

```

for a list of options look at [http://www.die.net/doc/linux/man/man8/pam_passwdqc.8.html](http://www.die.net/doc/linux/man/man8/pam_passwdqc.8.html).

Note: To finalize the changes, all passwords have to be reentered!!
If you restart at this point, you will be unable to log in again!
Set a new password with the passwd command ( can be the same as before, but it has to be reset to use the new hash!)

Problems: For those of you in trouble after a reboot:
you can boot to your system without a password, if you append a init=/bin/bash to your grub kernel parameter.
To enter that, type "e" at the grup prompt and you can edit the entry.

IMPORTANT: This does only secure Ubuntu passwords! You still can log in with things like knoppix or other methods like deskribed above!
For a fully secured system you have to encrypt harddrives!

[update]
There have been some problems (experienced by me and others) when using gnome-screensaver.
The problem relies in the libpam-unix2 package. It does not feature a equivalent for unix_checkpwd.

There are already bugreports at [https://bugs.launchpad.net/ubuntu/+source/libpam-unix2/+bug/82518](https://bugs.launchpad.net/ubuntu/+source/libpam-unix2/+bug/82518) and  [https://bugs.launchpad.net/ubuntu/+source/libpam-unix2/+bug/106670](https://bugs.launchpad.net/ubuntu/+source/libpam-unix2/+bug/106670).

Someone willing to try can compile the patch from novell and try out the unix2_checkpwd program and report back.

---

### Post by Ferio on 2006-11-15
It's pam_unix.so, and I hope it's pam_unix2.so, because that's the change I've done :???:

Apart from that, it should be clarified that this change has to be made only in 2 files under /etc/pam.d, because there's no use of this library in the rest of them.

---

### Post by NiN on 2006-11-15
Ok, I'll change it

---

### Post by Ferio on 2006-11-16
It seems to work flawlessly, and the explanation is quite clear now, thank you!

---

### Post by Ramaddan on 2006-11-30
Hi, thanks for the HOWTO, but I got locked out of my system, even after making sure I regenerated my password before logging out.

This has also thought me something else. I was able to easily reboot with the Live CD, and re-edit the files, and re-enter. This seems quite insecure.

This is really a major concern now. Does it mean anyone can just use a Live CD on my computer and hack away?

Also, is it possible to provide your changed files, so I can compare with what I did?

Is there a way to encrypt sensitive files so as not to enable others to do what I did above? Thanks.

---

### Post by NiN on 2006-11-30
Ok, changed the little vague description of the changes in common-password.

As for security: I use the libpam-encfs plugin to provide encrypted home folders alongi with encrypted swap and tmp drives using crypt-utils and libpam-tempdir to secure access.

---

### Post by damatta on 2007-08-11
I have done this under Kubuntu Fesity Fawn and everything is working perfectly, except when i click block session - I cannot login back from that window!
Any clues?
Thanks

---

### Post by NiN on 2007-08-21
The problem is, that the libpam-unix2 package does not contain an equivalent of unix_checkpwd.
This little helper application runs suid root and checks the password against the hash stored in /etc/shadow, since the screensavers run as user and not as root.

There is currently only one workaround, but be warned!

THIS WILL OPEN A SECURITY HOLE IN YOUR SYSTEM!
DO NOT CONTINUE, IF YOU HAVE SENSITIVE INFORMATION!

The screen lock works, when you eighter change the ownership of /etc/shadow to some group your user is member of and give read access, or make it world readable.

BE CAREFUL!

---

### Post by derNarr on 2007-12-03
There is a quite simple way to test or to change to the blowfish hashing without changing all old passwords.

simply add above the old lines the following lines

in /etc/pam.d/common-account

  account sufficient    pam_unix2.so
  account required      pam_unix.so
  
/etc/pam.d/common-auth

  auth    sufficient    pam_unix2.so nullok
  auth    required      pam_unix.so nullok_secure
  
/etc/pam.d/common-session

  session sufficient    pam_unix2.so
  session required      pam_unix.so

As the authentication with the pam_unix2.so modules ist sufficient the blowfish hashed passwords work, but if something fail, the old (pam_unix.so) module will do their job.

I don't know if this handles the screensafer-problem or the block-session-problem.

Enjoy (K)Ubuntu :)

---

### Post by fitzhugh on 2012-01-25
I know this is an old old thread, but I thought it important enough to comment nonetheless.

Changing permissions of your shadow file to work around the screensaver problem might "work" but makes no sense in this context, as I think it safe to assume you are changing to blowfish for security reasons. Just disable your screensaver and, if you really need to, turn off the screen manually. I'd guess you could just disable the lock on the screensaver and let it blank and avoid the issue. 

I appreciate the work shared here by NIN, but the suggestion to change shadow perms is just too iffy. You end up losing the whole reason for moving to shadow from passwd file in the first place.

---

