---
title: "Security of various password stores"
date: 2008-06-28
forum: Security
---

### Post by torben2 on 2008-06-28
Hello everybody,

I am using Hardy with encrypted /home and swap, which works fine. To make things easier I use the same (fairly complex) password for both Samba, console login, SSH key passphrase and DM-Crypt (LUKS). At least synchronization between console and LUKS are necessary for pam_mount to work.

Plus, the LUKS header contains severall (fairly strong) passwords since we have multiple users who must be able to mount /home on login.


To my knowledge, 

- /etc/shadow is a MD5 hash of the password plus a "salt"
- smbpasswd is an "encrypted" version of the password (how?)
- LUKS stores the password in some sector of the harddisk, encrypted (how?)
- the SSH key passphrases are also (fairly securely) encrypted.

How secure is this? Given total access to the harddisk, which is least secure?

Is it possible/feasible/... to recover my password from the shadow or smbpasswd databases?

Thanks for any thoughts and insight!

---

### Post by hyper_ch on 2008-06-28
if anybody has physical access to your machine and gets luks key from ram, what do you care about the rest of the data?

---

### Post by tubbygweilo on 2008-06-28
> if anybody has physical access to your machine
Sounds about right to me. 

What about adding a simple bios password? I think make booting via a LiveCD just that little bit harder but alas will not stop having your hard disk removed and mounted on another machine.

---

### Post by torben2 on 2008-06-28
Sorry, you both missed my point ...

A) This is a PPC machine. No "bios", no bios password.
B) I don't care about hackers while the thing is running. I care about thieves who steal the whole computer while it is OFF, and then access it from a different system, and try to find the encryption key for /home.

So: is it possible to recover the shadow, or smb passwords out of the respective databases on disk, by ay other practicable method other than brute-force?

Thanks!

---

### Post by hyper_ch on 2008-06-28
if machine is not booted, hence password not in ram, how many years shall they have time to get the data within?

---

### Post by torben2 on 2008-06-28
If you think you need a number to answer my question (which you don't):
One year.

If you still think you cannot answer, let me rephrase:
What hashing/encryption methods are used in shadow, and smbpasswd databases, and are they symmetric or asymmetric?

---

### Post by hyper_ch on 2008-06-28
if it's a fully encrypted system you don't have all that data ;) you can only brute-force it...

---

