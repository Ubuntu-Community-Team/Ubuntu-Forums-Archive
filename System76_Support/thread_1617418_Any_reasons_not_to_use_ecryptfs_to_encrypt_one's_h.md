---
title: "Any reasons not to use ecryptfs to encrypt one's home directory?"
date: 2010-11-09
forum: System76 Support
---

### Post by Dave_L on 2010-11-09
[Ubuntu 10.04, model star3]

I've read everything I could find on ecryptfs, and plan to encrypt the existing home directory on my netbook using the instructions here: [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

That article is dated June, 2009.  I suppose it's still applicable for Ubuntu 10.04.

After that, I plan to encrypt the swap partition with dm-crypt.

Are there hidden pitfalls?
Will I lose any of the normal Ubuntu functionality?
Could I encounter any problems doing normal package upgrades with synaptic?
If I need to boot into single-user mode as root, or boot from a live USB, to perform maintenance, will there be added complications due to the encryption (other than having to mount the /home directory using the passphrase)?

---

### Post by isantop on 2010-11-09
It will probably work quite well until the next Ubuntu release. Then, the horrors of an encrypted home directory will set in. It is quite difficult to recover files on an encrypted home partition, and unless you have an extremely sensitive environment, I wouldn't recommend it yet.

---

### Post by Dave_L on 2010-11-10
Thanks for the response.

But why will the next Ubuntu release make a difference?  Are major upgrades always a problem with an encrypted /home?

---

### Post by jdb on 2010-11-10
> **Dave_L said:**
> Thanks for the response.

But why will the next Ubuntu release make a difference?  Are major upgrades always a problem with an encrypted /home?

/home has a LOT of configuration files & it's your login directory.
If it doesn't get unlocked properly on the first reboot
after an upgrade your system is hosed.

I make a separate partition I name data and encrypt that.
I keep everything sensitive/private there.
Since it doesn't contain any system stuff it won't keep the
system from booting if it's not available.
I've never had a problem opening it once the system is up & running.

jdb

---

### Post by 3Miro on 2010-11-10
Some sensitive data can be stored in browser cache which is in a .cache folder at /home/user (like Firefox remembering credit card numbers). I don't think you can keep everything sensitive on another partition.

Wouldn't it be better to avoid upgrades and just go for a clean install. From LiveCD, mount the encrypted /home, move the use folder to user_old. Install the new OS. Once you have the new OS, just move all of your files (including things like .mozilla)

---

### Post by Dave_L on 2010-11-11
Now I'm confused about what's best to do.

I wouldn't bother with encryption for a desktop computer that stays in my home, but this is a netbook that I take places, which greatly increases the risk of it being lost or stolen.

There will be personal information that I really wouldn't want others to access.

As 3Miro said, private info is automatically placed in the /home directory.  That's an important reason for encrypting that directory.

jdb referred to the encrypted /home directory failing to get unlocked properly on the first reboot after an upgrade, resulting in the system getting "hosed".  Is that really a likely scenario?  I haven't seen that problem discussed elsewhere.

And when you say to "avoid upgrades and just go for a clean install", are you talking only about a major upgrade, such as Ubuntu 10.04 to 10.10? Or does that also apply to routine upgrades of individual packages, and occasional installation of new packages?

---

### Post by zitch on 2010-11-11
I would backup your encrypted directories at home to an unencrytped drive (on your desktop computer, for example) on a regular basis.  As you say, you won't need encryption on your desktop, but I can see why you would want it for your netbook.

It could be as simple as a scheduled (or one you kick off manually) rsync to you desktop.  Or you can do what I do for my main laptop (though with an unencrypted home dir): using BackInTime to backup to a USB drive that you leave at home on a nightly schedule (The software won't do a backup if the drive's not available if you set things up right).  Basically, I bring my laptop home, power it up, log in, and plug in the drive and make sure it auto-mounts; at this point, it's ready for the backup that night without any further intervention on my part (of course, I can also start working normally from here, too).  I'm sure there's more involved and flexible solutions out there too.

This way, you also have a backup of your files when you do an upgrade (or do a wipe clean and reinstall the newer release, as it looks like upgrades don't fully work with encrypted home partitions.

---

### Post by 3Miro on 2010-11-11
jdb is talking about a release upgrade (like 9.10 to 10.04). /home keeps configuration files for individual users, when you go for a major release upgrade, all of those files have to be updated for the graphical environment (like Gnome 2.28 to Gnome 2.30). The upgrade comes with scripts that will make the proper conversion, however, the scripts run at first boot and if they fail, you will have a /home with incompatible configuration. The system is not completely destroyed, but it will take quite a bit of effort to fix something like this.

zitch probably has the best solution (provided you have another unencrypted computer). When the new release comes up, just backup everything and make a clean install; you can even backup things like .mozilla that will keep the bookmarks and such. Also, if you lose your laptop (or it gets stolen) you will at least have backup for all of your files.

---

### Post by Dave_L on 2010-11-11
Thanks for the additional info.

I was planning on setting up regular backups to an external USB drive using rsnapshot (an incremental backup script that uses rsync).

In addition, I may image the partition(s) periodically.

So that should enable me to recover from any problems.

---

### Post by isantop on 2010-11-11
An upgrade would definitely fail with an encrypted /home. You would loose your data on a fresh install unless you back them up somewhere.

If you do decide to encrypt your home directory, then I'd go with a backup solution like what has been mentioned. Imaging, rsync, or even simple drag and drops would work fine. 

Keep in mind though, that if something happened to your system, and you hadn't backup up in a while, you would loose any data not saved in your last backup.

The lack encryption is generally not a security risk anyway, as you'd need either your password or administrator rights to access your home folder anyway. The firefox cache should be cleared on exit, and you can manually clear it by going to Tools > Clear Recent History... which can clear all of your saved information like that. However, if you're worried about it, and are prepared for frequent backups, I'd say go ahead.

---

### Post by Dave_L on 2010-11-12
> **isantop said:**
> The lack [of] encryption is generally not a security risk anyway, as you'd need either your password or administrator rights to access your home folder anyway.

Unless you boot into recovery/single-user mode, boot from a Live USB, or yank out the hard drive and attach it as a secondary device on another computer.

---

### Post by Megaptera on 2010-11-12
> **Dave_L said:**
> Now I'm confused about what's best to do.

I wouldn't bother with encryption for a desktop computer that stays in my home, but this is a netbook that I take places, which greatly increases the risk of it being lost or stolen.

There will be personal information that I really wouldn't want others to access.

Have you considered using TrueCrypt to store & backup what's personal? TrueCrypt 'volumes' can be quite large I believe.  [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by StephenDavison on 2010-11-14
I'd like to ask it the other way: Is there any reason to encrypt one's entire home directory?  It's easy to setup the encrypted ~/Private directory and store sensitive data there.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by Dave_L on 2010-11-14
Megaptera:

I'm currently using Truecrypt. The disadvantage is that I have to explicitly keep track of which files I need/want to encrypt, and place those files accordingly.

StephenDavison:

As noted earlier in this thread, many files get created and updated automatically in /home.  Some of those files contain private information. Relocating those files elsewhere, e.g. in a Truecrypt volume or a Private subdirectory may be difficult or even impossible, depending on the application that uses the files.

Suppressing the storage of some of the private information, such as browser cache/history/cookies/passwords, is possible. You can also use webmail via https, rather than a local email client. That's what you'd do if you're using a shared public computer.  But it's also a big inconvenience.  By encrypting the entire /home directory, you don't have to worry about this.

---

### Post by jdb on 2010-11-14
> **Dave_L said:**
> Megaptera:

I'm currently using Truecrypt. The disadvantage is that I have to explicitly keep track of which files I need/want to encrypt, and place those files accordingly.

StephenDavison:

As noted earlier in this thread, many files get created and updated automatically in /home.  Some of those files contain private information. Relocating those files elsewhere, e.g. in a Truecrypt volume or a Private subdirectory may be difficult or even impossible, depending on the application that uses the files.

Suppressing the storage of some of the private information, such as browser cache/history/cookies/passwords, is possible. You can also use webmail via https, rather than a local email client. That's what you'd do if you're using a shared public computer.  But it's also a big inconvenience.  By encrypting the entire /home directory, you don't have to worry about this.

I have a separate partition that is encrypted, I use Cryptsetup with LUKS support.
I move file browser or mail program directories there
and put symbolic links to them in the places that the browser or mail program expects to find them.
Any partitions encrypted with a LUKs format will show up in the
'Places' tab in the Ubuntu menu bar.
When you click on them it will prompt you for the password and
then mount them.
There are other ways to manage them but 'Places' is the simplest.

jdb

---

### Post by isantop on 2010-11-15
It sounds to me that the best solution, given the various folders that personal data gets stored in, would be to setup encryption on ~/Private, ~/.cache, and ~/.evolution or ~/.mozilla. That should get most of it, though jdb's solution also sounds good.

---

### Post by StephenDavison on 2010-11-16
> **Dave_L said:**
> 
...
As noted earlier in this thread, many files get created and updated automatically in /home.  Some of those files contain private information. Relocating those files elsewhere, e.g. in a Truecrypt volume or a Private subdirectory may be difficult or even impossible, depending on the application that uses the files.
...


Does anyone have an example of an application for which this is difficult or impossible?  So far I've found it to be a cinch using symbolic links as described in the EncryptedPrivateDirectory instructions.

I wouldn't necessarily discount using encryption for sensitive material on a desktop computer.  They can be stolen too.

---

### Post by Dave_L on 2010-11-16
I withdraw my "difficult or impossible" statement. I can't think of a reason why symbolic links would not work.  But you still have to go to the trouble of determining which subdirectories to relocate, and setting up the symlinks. Encrypting the whole directory avoids this task.

You're right about desktops.  Encryption can be worthwhile there too.

---

