---
title: "Problem setting up user with encrypted home when umask is 077"
date: 2011-01-06
forum: Security
---

### Post by roomey on 2011-01-06
Hello,

I just had this strange problem, and I didn't see any posts regarding it, so I thought I would share. I am not sure if this is a bug.

On the computers I manage, I have set the umask in /etc/profile to be:
umask 077
(the company is security conscious).

I was then trying to set up a user with an encrypted home using the command:
adduser --encrypt-home new_user 
(run as root)

The first warning sign I saw was that when I tried to enter the new users password, passwd kept giving a warning, saying it could not set the password. Despite this, the user was set up, with the password I had entered. But when I tried to log into the account, the home directory did not decrypt automatically, and when I tried to run:
ecryptfs-mount-private
I got an error: ERROR: Encrypted private directory is not setup properly

It seems that even if I fixed the permissions manually in /home/.ecrypt it still would not work (it was missing the wrapped passphrase I believe). 

My solution was to change the umask back to 022 in /et/profile run the adduser command again then revert the umask change. This seems to have worked as desired. 

Does anyone have any suggestions for why this is required? 

Either way I hope this helps someone else.
Regards,

---

