---
title: "Cloning a USB install with encrypted home folder"
date: 2011-03-18
forum: Security
---

### Post by Veazer on 2011-03-18
I would like to give a few students a preconfigured Ubuntu USB stick with certain apps. I also encrypted the home folder in case of loss.

With TrueCrypt, cloning an encrypted container would be a big no-no because any one could just backup their header with a known pw and use it to decrypt anyone else's container due to each container using the same master key. I assumes the same applies to home folder encryption, yes? 

Is there a way, other than creating a new user with home folder encryption, of forcing a master key change?

---

### Post by BkkBonanza on 2011-03-18
The passphrase for an encrypted home is stored in 

/home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase

and is different from the login password. During login this passphrase is unlocked as master key so changing it would allow the same login on each copy to work with a differing encryption key.

You need to make this different for each copy probably by changing it on each image using the manual cmd line ecryptfs tools. I haven't done this so I'm just pointing in a direction to look for managing an encrypted home manually. I presume a script could be made to automate the copy and fix passphrase for each copy you make.

---

### Post by Veazer on 2011-03-18
> **BkkBonanza said:**
> The passphrase for an encrypted home is stored in 

/home/.ecryptfs/<user>/.ecryptfs/wrapped-passphrase

and is different from the login password. During login this passphrase is unlocked as master key so changing it would allow the same login on each copy to work with a differing encryption key.

You need to make this different for each copy probably by changing it on each image using the manual cmd line ecryptfs tools. I haven't done this so I'm just pointing in a direction to look for managing an encrypted home manually. I presume a script could be made to automate the copy and fix passphrase for each copy you make.

Right, i know that the two keys are different and changing login pw requires a change in the encryption pw.

however, wouldn't truly changing the master key require a rewrite of all encrypted files and folders using the new key? I'm told this is why TrueCrypt has no plans to support master key changes, they just want people to make new containers and transfer files.

---

### Post by BkkBonanza on 2011-03-18
Hmm. That sounds about right. You'd be better off to make a build script that copies a base system image and then adds the encrypted home and moves the user files into it. 

The encrypted home developer guru has a blog post (below) about steps to create an encrypted home afterwards. You can put those in a script, mount the usb drive as /mnt, add some bind mounts for /sys /dev /proc, chroot to /mnt and do the manual ecryptfs creation, then copy the users files and remove the non-encrypted home. It's a bit more work but if scripted could be repeated as often as needed.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

[http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html#comment-form](http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html#comment-form)

(I see he now says there is a built in command ecryptfs-migrate-home to migrate a home afterwards. Makes it easier.)

---

### Post by Veazer on 2011-03-18
> **BkkBonanza said:**
> Hmm. That sounds about right. You'd be better off to make a build script that copies a base system image and then adds the encrypted home and moves the user files into it. 

The encrypted home developer guru has a blog post (below) about steps to create an encrypted home afterwards. You can put those in a script, mount the usb drive as /mnt, add some bind mounts for /sys /dev /proc, chroot to /mnt and do the manual ecryptfs creation, then copy the users files and remove the non-encrypted home. It's a bit more work but if scripted could be repeated as often as needed.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

[http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html#comment-form](http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html#comment-form)

(I see he now says there is a built in command ecryptfs-migrate-home to migrate a home afterwards. Makes it easier.)

Excellent, that's actually not a bad idea if I can enable the encryption after the fact, then each user *will* have different key. Thanks for the link.

Greetings from Chiang Mai btw... Holy !@#$%! it's cold now.

---

### Post by BkkBonanza on 2011-03-18
Good that helps. 

(Yes, cold here in Bkk too. For a couple days anyway. 
I like it. No sweating profusely for a change.)

---

### Post by n.williams0440 on 2011-03-18
Thanks guys  for give information.....

---

### Post by bodhi.zazen on 2011-03-18
If it is of any use, you can use the debian live scripts to build a custom iso.

The debian live scripts automate the build process and there are several interesting options. First the resulting iso file is a hybrid, it can be used as an iso or copied to a usb directly.

Also you can use persistence, either for the entire file system or for /home.

You can also encrypt the entire iso.

[http://live.debian.net/](http://live.debian.net/)

[http://manpages.ubuntu.com/manpages/jaunty/man7/live-helper.7.html](http://manpages.ubuntu.com/manpages/jaunty/man7/live-helper.7.html)

[http://manpages.ubuntu.com/manpages/jaunty/man1/lh_config.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/lh_config.1.html)

There is a bit of a learning curve to using these scripts, but once you understand them it would be rather trivial to build a number of highly customized, encrypted images (usb).

---

### Post by Veazer on 2011-03-21
Thank you to everyone who offered advice!

I think the best overall solution was found in BkkBonanza's first link, the author mentions that encrypting an existing home folder is much easier now due to the new command **ecryptfs-migrate-home**. More info here: [http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html]("http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html")

This way i can do all my setup ahead of time and each can run the command later to encrypt their home folder (hopefully with a different master key??? gulp!)

@bodhi.zazen

Those scripts look useful as well, i will keep them on hand.

On a side note, I'm still kind of baffled why anyone would use a live drive + persistence, given all the limitations over actually just installing Ubuntu to the USB drive. The only advantage i see is that it can be used to install Ubuntu on other machines

---

