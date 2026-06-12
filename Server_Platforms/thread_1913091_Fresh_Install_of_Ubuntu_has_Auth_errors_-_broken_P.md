---
title: "Fresh Install of Ubuntu has Auth errors - broken PAM?"
date: 2012-01-21
forum: Server Platforms
---

### Post by Cueball61 on 2012-01-21
I recently rebuilt one of my servers into an ESXi 5 VM Host, and just attempted an install of Ubuntu Server 11.10.

I went through the setup, mounted the ISO, installed Ubuntu, all good so far.

But SSH doesn't work at all with password authentication. Literally no user can login without a public key, if I go through VNC and use the local console then I can login and use sudo fine, but on SSH even if I login using keys sudo doesn't work and returns "Sorry, try again".

I checked Auth.log and it was filled with PAM complaining about "conversation failed" whenever an authentication attempt was made.

Just to clear a few things up pre-emptively:

Yes I am using the correct user/password combo.
No password Auth is not disabled in sshd_config.
Yes my passwd/shadow files are owned by root and have correct permissions.
Yes the box can resolve its host name to the right IP.

Hopefully that'll clear up any initial questions.


Any ideas guys? Currently stuck with a VM Host with a bunch of useless Guests right now.

Oh, something else I noticed, SFTP fails to connect as well, not sure if it's related though.

Cheers
Cue

---

