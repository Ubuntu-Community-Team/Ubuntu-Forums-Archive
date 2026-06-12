---
title: "Encryption status of Home in 12.04"
date: 2012-05-15
forum: Security
---

### Post by dreamquartz on 2012-05-15
I would like to know if my Home folder is encrypted, but how can I check that.

Dream

---

### Post by OpSecShellshock on 2012-05-16
Shut down completely, then restart the system and log on as a user other than the account with the encrypted home. Navigate to your user account's home directory and see what's in it.

---

### Post by tubbygweilo on 2012-05-16
You could also attempt to read your home directory by booting with a liveCD and examining your home directory - just as a bad guy would.

---

### Post by choppyfireballs on 2012-05-16
Basically you can check by accessing YOUR USERS home folder from another user via live Cd guest, anything that would normally give you access to home without you logging into your user. 

file shares work as well.

---

### Post by dreamquartz on 2012-05-21
Did not like encryption, so re-installed 12.04. Was the easiest way for me to get rid of the encryption.

---

### Post by tubbygweilo on 2012-05-22
dreamquartz, as it seems that you are no longer using an encrypted /home then I would like to ask if you still intend to encrypt data on your machine or have you decided upon another method of keeping data safe?  I myself do not bother with an encrypted home but use full disk encryption and plenty of backups.

---

### Post by Paddy Landau on 2012-05-22
> **dreamquartz said:**
> I would like to know if my Home folder is encrypted, but how can I check that.
Easiest method (using GUI):

[LIST=1]
[*]Open your Home Folder (using Nautilus from the Launcher).
[*]Press Ctrl-H to view hidden files.
[*]Look for a folder called [FONT=Lucida Console].Private[/FONT].
[*]If it exists and it contains many files with strange names beginning with ECRYPTFS, your folder is encrypted.
[/LIST]

---

### Post by dreamquartz on 2012-05-24
> **tubbygweilo said:**
> dreamquartz, as it seems that you are no longer using an encrypted /home then I would like to ask if you still intend to encrypt data on your machine or have you decided upon another method of keeping data safe?  I myself do not bother with an encrypted home but use full disk encryption and plenty of backups.

We are running multiple systems with Ubuntu 12.04. The data created is not stored on the business machines, but on USB 64 GB memory sticks for ease of encryption. The encryption is done via Truecrypt.
We have to use Windows (only one machine; sorry) for some very specific programs that are not and probably never will made available under Linux.

The data is therefore easily transferable from Ubuntu <-> Windows.

Dream

---

### Post by Paddy Landau on 2012-05-25
> **dreamquartz said:**
> The data created is ... stored on ... USB 64 GB memory .... The encryption is done via Truecrypt.
Have you considered putting the data on the network?

If you create a TrueCrypt encrypted file container in a shared folder, and take steps to ensure that only one person ever opens that file container at any given time, it will be easier to back up and to access. It will also last much longer between failures, as a heavily-used USB is prone to sudden fatal failure.

---

### Post by dreamquartz on 2012-05-27
> **Paddy Landau said:**
> Have you considered putting the data on the network?

If you create a TrueCrypt encrypted file container in a shared folder, and take steps to ensure that only one person ever opens that file container at any given time, it will be easier to back up and to access. It will also last much longer between failures, as a heavily-used USB is prone to sudden fatal failure.

Sorry for the mis-understanding. Of course the data is securely stored on the network. There is only no data stored on the Ubuntu computers, which are all netbooks and laptops, by the way.

Dream

---

