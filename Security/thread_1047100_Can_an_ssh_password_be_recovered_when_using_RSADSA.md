---
title: "Can an ssh password be recovered when using RSA/DSA keys without passphrase?"
date: 2009-01-22
forum: Security
---

### Post by KIAaze on 2009-01-22
Can an ssh password be recovered when using RSA/DSA keys without passphrase?

I configured my system to be able to login into a server using ssh without having to enter the user password by following this tutorial:
[http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html](http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html)

I created the RSA/DSA keys without passphrase.

I understand that if somebody gains access to the files in the .ssh directory, he'll have access to the server.

But will he be able to access the passwords encrypted in those files as well or not? (are the passwords encrypted in there or is it a system similar to /etc/shadow where it only contains some hash?)

edit:
Mmh, after looking at how the whole process works again, it seems like it doesn't require the user password at all... ^^'
But it would be nice if somebody could confirm this for me. ;)

And using a passphrase seems kind of pointless, since it asks for the passphrase all the time then.
Might as well enter my user password everytime...
What's the point of using RSA/DSA with passphrase?
If somebody gains access to the key, can he recover the passphrase from it?

re-edit:
From man ssh-keygen:
> There is no way to recover a lost passphrase.  If the passphrase is lost or forgotten, a new key must be generated and copied to the corresponding public key to other machines.

So the only danger when someone gains access to rsa/dsa files, is that he can connect to the server without a password (if no passphrase is used)?
The user account passwords are safe?

---

### Post by The Cog on 2009-01-22
Password login uses RSA/DSA keys instead of using a users password. The key is accepted by the SSH server as proof of the callers identity. 

The "passphrase" is used to protect the keys from unauthorised users on the calling machine. It has no connection with the login password on the server - it's just the password for the key file.

You are right - if you use a password-less key file, then if you mobile gets hacked then they can use the keys to gain access to the server.

Using key files and pass-phrases is safer for the server than usning standard login passwords though, because brute-force password guessing bots don't really stand a chance. The easiest approach would be two steps - steal somebody's key file and then guess the passphrase.

Once someone has gained access to the server with a stolen key file, they can proceed to either brute-force all the user passwords, or perhaps execute a vulnerability exploit to get root.

---

### Post by KIAaze on 2009-01-22
Thanks.

But I didn't quite understand this part:
> Using key files and pass-phrases is safer for the server than using standard login passwords though, because brute-force password guessing bots don't really stand a chance.


Is it harder to brute-force a key-file passphrase than a login password if the same password string is used for both?
Or is it just harder if a more complex string is used for the passphrase?

Gaining access to ~/.ssh seems easier to me than gaining access to /etc/shadow (ex: pc left unattended while logged into a user account)... O.o

---

### Post by The Cog on 2009-01-22
If someone steals the key file, then brute-force guessing the passphrase probably isn't much harder than guessing user passwords. What I meant was that if you don't have a copy of the key file, brute-force guessing a key itslef (the contents of the key file you don't have) is very hard because the keys are so long - much longer than most users would use in a password.

It means that in practice, an attacker must get hold of a copy of the key file to have any chance at all of hacking in.

---

