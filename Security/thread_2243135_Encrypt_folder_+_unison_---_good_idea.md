---
title: "Encrypt folder + unison --- good idea?"
date: 2014-09-06
forum: Security
---

### Post by evencoil on 2014-09-06
I have a directory with sensitive records in it that lives in my home directory.

I'd like to back it up to another computer I own that lives in a different physical location.

For non-sensitive files, I use unison and it works great. To automate the process I put my unison scripts in my regular user's crontab.

My initial thought is to do the following:
1. Encrypt the directory with the sensitive records.
2. Unison the encrypted directory and any configuration directories required for the encryption (i.e. ~/Private and ~/.Private)

However I know very little about encryption and security, so my overall question is: is this a good idea?

Also, is there a way to do this and still be able to run my unison script as a regular user (vs. root user)?

Thanks!

---

### Post by tornadof3 on 2014-09-07
Once this folder has been encrypted, what is the frequency of access going to be like? Is the encryption solely for the purposes of moving the files, or will you keep the 'local' copy on your computer encrypted too?

If you just want to encrypt a folder so that its contents can be transferred elsewhere without risk of being read by bad guys, probably the quickest option would be to zip the folder into an archive (eg .tar.gz, .tar.bz2 or good old .zip) and then use GPG (PGP) to encrypt the resulting archive.... see [http://xmodulo.com/2013/08/how-to-pgp-encrypt-decrypt-digitally-sign-files-via-gnupg-gui.html](http://xmodulo.com/2013/08/how-to-pgp-encrypt-decrypt-digitally-sign-files-via-gnupg-gui.html) for how to use Seahorse integrated into nautilus file manager to do this graphically. If GPG is properly installed and set up, then you can also do this from the command line, which you could incorporate into your cron job.

Hope this is a little help.

---

### Post by bashiergui on 2014-09-07
> 1. Encrypt the directory with the sensitive records.
2. Unison the encrypted directory and any configuration directories required for the encryption (i.e. ~/Private and ~/.Private)If you store the private key with the encrypted data, you might as well not encrypt it at all.

---

### Post by evencoil on 2014-09-07
> **tornadof3 said:**
> Once this folder has been encrypted, what is the frequency of access going to be like? Is the encryption solely for the purposes of moving the files, or will you keep the 'local' copy on your computer encrypted too?

If you just want to encrypt a folder so that its contents can be transferred elsewhere without risk of being read by bad guys, probably the quickest option would be to zip the folder into an archive (eg .tar.gz, .tar.bz2 or good old .zip) and then use GPG (PGP) to encrypt the resulting archive.... see [http://xmodulo.com/2013/08/how-to-pgp-encrypt-decrypt-digitally-sign-files-via-gnupg-gui.html](http://xmodulo.com/2013/08/how-to-pgp-encrypt-decrypt-digitally-sign-files-via-gnupg-gui.html) for how to use Seahorse integrated into nautilus file manager to do this graphically. If GPG is properly installed and set up, then you can also do this from the command line, which you could incorporate into your cron job.

Hope this is a little help.

My aim was to also have the local versions encrypted. Ideally I would like the directories not to be decrypted automatically when I login, but to have to take some extra action to decrypt them, and then re-encrypt them again when I'm done with them.

[QUOTE=bashergui] If you store the private key with the encrypted data, you might as well not encrypt it at all. [/QUOTE]

I'm confused by this...my understanding was that one still uses a password to decrypt? For example, if one encrypts the entire home directory then there's the .ecryptfs directory which contains a subdirectory called .Private, but one still needs the user password to decrypt the data. And in order to backup the encrypted data correctly you would want to make sure to include .Private. Is that not how this works?

---

