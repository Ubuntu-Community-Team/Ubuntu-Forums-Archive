---
title: "cron job + gpg issue"
date: 2009-01-29
forum: Security
---

### Post by RickshawDriver on 2009-01-29
Hello all, I hope you can help me out.  I have been banging my head against a wall for several days.  Here is my situation:

I have multiple gpg encrypted files coming in from different sources.  I own the private and secret keys and they encrypt using my public key.  They each drop their file into their own sftp folder, owned by them with permission 750 applied.  The secret keyring is under my user account.

My script takes their encrypted file from their folder, copies it to my home folder, decrypts it, pushes to an internal server via samba and then deletes both encrypted files (my home and their ftp) and the decrypted file in my home folder.

If I run this script manually (bash d_client) it processes the file without problems.  If I run it under my crontab (crontab -e) it will copy, decrypt and push the file, but permission is denied to delete the encrypted file in their ftp folder.  If I run the job under the root crontab (sudo crontab -e) it will copy, push and delete, but says that there is no secret key available.

I have tried to copy the seckey.gpg from my .gnupg folder to the /root/.gnupg folder but that did not work.

Can someone please help me figure out how to keep the folders locked down and still be able to run these scripts?

---

### Post by e1mer on 2009-01-29
cron strips away the environment for the user that runs it.

It sounds like you are permitted to remove the file because
of group permissions for your user instead of owner permission.

I believe you are allowed to specify the user to run a command
as under cron.

crontab -e 
then make it:
time_spec   user_name   command_string

That should let you use directory AND file owners name for your rm command

---

