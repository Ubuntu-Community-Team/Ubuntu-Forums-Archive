---
title: "SSH public key authentication"
date: 2008-07-17
forum: Security
---

### Post by bwilhiteforex on 2008-07-17
Hello all,

I'm running Xubuntu 8.04, and I'm trying to setup public key authentication for SSH (password authentication works fine).  Here are the tutorial resources I've been using...

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

...as well as a few others.  Every time I try to login I'm getting permission denied (public key).  This is true for both remote and local logins.  I'll post my latest login attempt with '-v' option in another message (I'm on host machine now).  

I sure would appreciate some help getting this to work correctly.

Thank you.

Brandon Wilhite

(edit)--I haven't figured out how to cut/paste the results from 'ssh -v' from cygwin, which is where I'm trying to login from...if someone could tell me how to get that output into a file, I'll gladly post it here

---

### Post by kevdog on 2008-07-17
On server, is public key within the authorized_keys file?

Are you specifying a username?

Redirect in cygwin to a file

ssh -v ...... > file_name


Or right click on the terminal prompt, select edit, and then select lines you want with left click, paste with right click.

---

### Post by bwilhiteforex on 2008-07-17
Yes, I had the authorized_keys file set and all that, but perhaps my sshd_configure was wrong somewhere...When I looked at the output, it seemed like the keys were being exchanged, but for some reason the server just wasn't finding the key.

I'll do the re-direct thing and post the contents of the file.  I'll also post my sshd_configure.  

oh...and I tried both with and without a username

BW

---

