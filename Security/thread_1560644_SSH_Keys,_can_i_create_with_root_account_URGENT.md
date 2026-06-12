---
title: "SSH Keys, can i create with root account? URGENT"
date: 2010-08-25
forum: Security
---

### Post by mokachoka on 2010-08-25
Can i login to my server using my root account and create a public+private key for one of my users and then manually paste it into his authorized_keys file and give him the private key?

The user im giving it to has a chrooted FTP account...

Is it still ok that i used the root account to create it? He is not going to have root access or nothing is he? This is not a security breach in any way is it?

The user doesn't have shell access to create their own so this is the only way i can think of doing it...

Also what access should the user have to their .ssh folder + the authorized_keys file...?

Are they allowed to read the key? What about write?

---

### Post by Bachstelze on 2010-08-25
Technically you can, but it's terrible admin practice.  Let the user create his keys for himself. He can create his keypair on his own system, and give you the public key so you can copy it where it needs to be on your system.

---

### Post by mokachoka on 2010-08-25
Ok thanks for you speedy reply.

Can i ask what the permissions should be on the .ssh folder and the authorized_keys file?

Im guessing they should not have write access to it? read?

---

### Post by Bachstelze on 2010-08-25
They can be world-readable, there's nothing secret in them.  The private key, on the other hand, must of course be chmod 600.  Also, write access should be given only to the owner.

---

### Post by mokachoka on 2010-08-25
Ok, ive wrote a little script that creates a public and private key for an account i specify. The public key is automatically copied into the users authorized_keys and the private key is put in my home directory ready for me to send out... Would encrypting the private key before sending it be a good idea?

---

### Post by mokachoka on 2010-08-25
> **Bachstelze said:**
> They can be world-readable, there's nothing secret in them.  The private key, on the other hand, must of course be chmod 600.  Also, write access should be given only to the owner.

Thinking about what you said here.

If their world readable, would the user potentially not be able to somehow copy this public key to another user account on my system's .ssh folder? and then login to that account using the same private key?

The reason im asking this is because when i created the keys all i did to assign it to a user was drop it into their .ssh folder.

---

### Post by Bachstelze on 2010-08-25
> **mokachoka said:**
> If their world readable, would the user potentially not be able to somehow copy this public key to another user account on my system's .ssh folder? and then login to that account using the same private key?

Readable, not writable.

> The reason im asking this is because when i created the keys all i did to assign it to a user was drop it into their .ssh folder.

It is generally considered rude admin practice to put stuff into users' home directories.  As I said, let the users create their own keys and give you the public key so you can copy it in the right place.

---

### Post by mokachoka on 2010-08-25
Ok, thanks alot for your help and advice.

---

### Post by mokachoka on 2010-08-25
> **Bachstelze said:**
> Readable, not writable.



It is generally considered rude admin practice to put stuff into users' home directories.  As I said, let the users create their own keys and give you the public key so you can copy it in the right place.

Sorry one more question, when the user creates their own keys, can they not just drop the public key off into their own .ssh directory?

---

### Post by Bachstelze on 2010-08-25
Yes, if they have access to it.

---

