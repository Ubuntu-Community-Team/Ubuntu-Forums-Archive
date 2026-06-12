---
title: "Cygwin ssh key name change"
date: 2009-11-29
forum: Server Platforms
---

### Post by NertSkull on 2009-11-29
So I've discovered that if I try to change the file name on my cygwin ssh client from anything other than id_rsa (and id_rsa.pub) my keys wont work.

I'm trying to connect from a windows computer to my home ubuntu SSH server and I can not get authentication to work.  Logging in and everything works fine with the password.

Any one have ideas as to what I'm doing wrong/don't understand that is preventing this.  I like to name my own files with my own system and I can't change these ones. 

Thanks for the help.

---

### Post by NertSkull on 2009-12-01
Anyone run into this problem before?  That would make me think its definitely user error on my part.

---

### Post by NertSkull on 2009-12-11
I thought I'd try one more time.  Renaming keys in cygwin?  Anyone?

---

### Post by bodhi.zazen on 2009-12-11
Once you generate a key pair, you can not change the name of the private key.

You have to generate a new pair.

Run ssh-keygen and it will ask what name you wish, or you may specify a name on the command line.

ssh-keygen -f key_name

see man ssh-keygen for additional options.

---

