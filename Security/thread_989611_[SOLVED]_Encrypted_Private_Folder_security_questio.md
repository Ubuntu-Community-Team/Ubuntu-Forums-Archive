---
title: "[SOLVED] Encrypted Private Folder security question"
date: 2008-11-21
forum: Security
---

### Post by FictionPimp on 2008-11-21
I am very interested in using the encrypted private folder feature in 8.10 on my notebook. Currently this notebook is running windows XP and using truecrypt to encrypt a folder that I use to store all important documents. Each time I need to use the encrypted folder I mount it and supply the password. I have truecrypt set to unmount automatically if idle and I also unmount when I am finished with the folder.

It looks like this private folder will meet these needs but I have a question. From reading the docs it says the folder can be auto-mounted when you login and unmounted when you log out. This sounds very nice and I like it. However, what would stop a theif who steals my notebook from booting up in single user mode, changing my account password and then logging in to get my files?

For that matter, it looks like it is possible to recover the passwords if you have sudo access? If that is the case, again this seems like it is not as secure as it first looks.

I could be very wrong about this, but this is why I am checking. I am thinking about going the full disk encryption route (My work notebook already does this), but I would rather not if this is truly secure.

---

### Post by teddks on 2008-11-21
If I remember correctly, single user mode requires the root password. However, FDE is a bit more secure, and is pretty much invisible except for the extra password. With Ubuntu, it's incredibly simple to set up, as well. I highly recommend it.

---

### Post by Dr Small on 2008-11-21
> **teddks said:**
> If I remember correctly, single user mode requires the root password. However, FDE is a bit more secure, and is pretty much invisible except for the extra password. With Ubuntu, it's incredibly simple to set up, as well. I highly recommend it.
Unless the user sets a root password (not default, not supported, and of course, not documented), then single user mode does not prompt for a password.

---

### Post by teddks on 2008-11-21
(Is that so? It always seems that I need a password for the single-user mode shell. I could just be misremembering, though.)

How is the ecryptfs implemented? If it's a pam module (like pam_encfs), then changing your user password won't change the encryption password, and it follows that your files would be safe.

I'm not sure -- if you need to have the crypto passphrase be the same as your login, then it's probably done in that manner, though.

---

### Post by cariboo on 2008-11-22
I'm not really sure if you should be using the private directory, as all the files are linked to a hidden directory called .Private. You can access the directory, without having your private directory mounted. see the screenshot.

edit: see bug #264977:

Jims

---

### Post by hyper_ch on 2008-11-22
I would take the "easy" route and use full disk encryption... that way everything gets encrypted and I don't accidentally leave anything important unencrypted...

One thing: **make sure to have regular backups!!!**

while you should have regular backups anyway (because hardware might fail) it is even more so important on fully encrypted devices. If the sector with the stored passwords gets corrupted you can't access any data anymore.

---

### Post by teddks on 2008-11-22
> **cariboo907 said:**
> I'm not really sure if you should be using the private directory, as all the files are linked to a hidden directory called .Private. You can access the directory, without having your private directory mounted. see the screenshot.

edit: see bug #264977:

Jims

Yes, but all that would be revealed are the filenames.

I've never really understood why they used ecryptfs over encfs; encfs has some sort of filename dealing-with.

Also, I can confirm that changing a login password would not compromise the encryption in any way.

---

### Post by FictionPimp on 2008-11-22
Thanks for the information. I decided to go with full disk encryption. I am well aware of the risks. I was in charge of setting up the policy at my work for our current notebooks with full disk encryption. They use a network folder to place any 'can't lose' files and information. And that folder gets backed up.


Here at home I plan to use my existing method of weekly USB hard drive and a script that copies my home folder to it. That hard drive is then kept in my bedroom fireproof safe.

---

### Post by Hadraniel on 2008-11-26
> **teddks said:**
> I've never really understood why they used ecryptfs over encfs; encfs has some sort of filename dealing-with
ecryptfs is *much* faster, by using a kernel module.

---

### Post by teddks on 2008-11-26
> **Hadraniel said:**
> ecryptfs is *much* faster, by using a kernel module.

Makes sense. I used to have my entire home directory encrypted with encfs and it was slow as ****.

---

