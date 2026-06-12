---
title: "Encryption, smartcards, tokens and GPG options"
date: 2010-02-09
forum: Security
---

### Post by ushills on 2010-02-09
I would like to secure my hard drive and user access with some sort of encryption.

I have a multiuser PC in our house that is used by all the family, what I would like to do is encrypt the 

/home folder of the users either globally or individually.

I would also like to discuss the posibilities of the following within Ubuntu.

1.  Decryption of entire /home provided a USB key with a valid GPG key is inserted at boot, drive remains 

encrypted if key is not present.

2.  Decryption of entire /home provided a GPG smartcard with a valid GPG key is inserted at boot, drive 

remains encrypted if key is not present.  What options are available if the smartcard fails.

3.  Use of time based security token as password for each user, (one token per user) to decrypt users home 

directory and login.  Sudo should be able to access all accounts and reset token and add new tokens using 

password.


What time based tokens are suitable for use with Ubuntu and where can you get them in the UK.

Ultimately I want to secure my PC's data should it be stolen, I would also like it to be fairly secure 

when I the main user am away from the machine (i.e individual authentication tokens) but easy for other 

users to have secure passwords that are easy to remember/enter (i.e. time based security token/GPG 

smartcards).

Is there any discussion of these options or can we start this here.

Finally, I currently back-up all my data to a encrypted hard-drive that is held off site using 

rdiff-backup, if the individual /home folders are encrypted how can I do this.  Would global encryption of 

/home be a better option or just encryption of sensitive /home accounts with a removable encryption key.

---

### Post by ushills on 2010-02-09
Having read about pam_usb this would seem to fulfil many of my requirements, however, a question.

Would one USB key be able to unlock all user accounts or just selectively the ones with sensitive information, I understand that pam_usb is for authentication only however would this work with cryptfs for encryption of /home unlocked with USB key and PIN.

---

### Post by cariboo on 2010-02-09
Is there a reason to encrypt the home folders? If you change home directory permissions to 700, the only people that can access the directory are root and the owner.

---

### Post by ushills on 2010-02-10
I want to use encryption in the event of hard drive / pc theft, thereby securing my information.

---

### Post by tubbygweilo on 2010-02-10
> Is there a reason to encrypt the home folders? If you change home directory permissions to 700, the only people that can access the directory are root and the owner. 
If you change the permission then it may well be possible to still extract information from the /home directory via a live cd whereas when I tried to do the same on an encrypted /home all I could extract and examine were encrypted file names containing what may well have been encrypted data.

---

### Post by ushills on 2010-02-11
pam_usb seems to work in this situation, I have tried pam_usb coupled with the necessity to enter the a user password and this seems to work.

I am however having issues with ecryptfs and /home and will raise this as a seperate thread.

---

