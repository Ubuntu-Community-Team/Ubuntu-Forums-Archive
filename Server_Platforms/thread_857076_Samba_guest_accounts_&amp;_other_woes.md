---
title: "Samba guest accounts &amp; other woes"
date: 2008-07-12
forum: Server Platforms
---

### Post by trbabb on 2008-07-12
Hi,

I have a headless Ubuntu server, and I have three user directories in /home/: "tbabb", "ababb", and "media". Currently, 'media' is a folder/user with weaker permissions that any valid user should be able to use & dump files into.

Now, I want anybody on the *local* network to be able to open up the server through SMB and access /home/media without having to supply a username or password. However, I want /home/ababb and /home/tbabb (and any other user directory that I may add) to be accessible through SMB only with the valid unix passwords of their respective accounts.

What's the best way to go about this?

---

### Post by trbabb on 2008-07-12
Okay, so I've got the server running, and /home/media is mapped to the guest account. However, no matter what I do, it's read-only. I've found the "guest account = nobody" option in smb.conf, and have tried changing it to "= media", but this doesn't seem to work. An excerpt of my smb.conf:

```

[Guest Share]

   writeable = yes
   path = /home/media
   write list = @everyone
   guest ok = yes
   only guest = yes
   public = yes
   readonly = no
   create mode = 0777
   directory mode = 0777

```

I should mention that media's umask is (I believe) 775, and it'd be great if I could get access to all the files that are already in /home/media by using the media user (instead of chmodding everything that's already there).

Any help would be appreciated.

---

