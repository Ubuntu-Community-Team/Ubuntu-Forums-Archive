---
title: "Encryption v. temporary files"
date: 2009-10-28
forum: Security
---

### Post by Pro-reason on 2009-10-28
Recently I’ve been reading about encryption and it’s all fascinating stuff.  I’ve read stuff that says that it’s no good encrypting things unless you make sure you shred the decrypted versions.

However, I was wondering whether even that is secure.  I mean, if I open an encrypted e-mail in Thunderbird, it gets decrypted.  Where does that decrypted text go after I close the message?  Does it just vanish from RAM?  Or does Thunderbird store it in an unencrypted temporary file, which an attacker could easily recover?

The same goes for encrypted files of all types.  If an unencrypted version of a file is opened in OpenOffice, AbiWord, GIMP, Evince, Gedit, Audacity, Kino, Totem, Kile, LyX, Rhythmbox, Vim, Emacs, Firefox or Opera, will temporary files be created and insecurely deleted?  Some programs will be more secure than others, I imagine.

Would moving your personal configuration folders (e.g. $HOME/.openoffice.org/) to an encrypted filesystem (e.g. $HOME/.Private/) help at all?

Don’t suggest full-disk encryption.  That’s too obvious.

---

### Post by community nerd on 2009-10-28
When you're setting up it gives you the option to make a seperate home partition wich you can encrypt. Would that do it?

---

### Post by Pro-reason on 2009-10-28
> **community nerd said:**
> When you're setting up it gives you the option to make a seperate home partition wich you can encrypt. Would that do it?
Well, maybe.  It depends.  Do such programs save temporary files only in the user’s directory?  What about /tmp/?  Or somewhere else within the system?

What if I don’t want to slow down my account by having every read and write go through an encryption program?  What if I want to target just OpenOffice, for example?

Does anyone have any specific knowledge about this?

---

### Post by Agent ME on 2009-10-29
When an email gets decrypted, for example in Thunderbird, it doesn't get saved to the hard drive, just held in ram while Thunderbird is open. When a file is decrypted, it doesn't have to be written to the hard drive in plaintext.

The easiest way to manage encryption in Ubuntu is to set up ecryptfs. Open a terminal, and enter "ecryptfs-setup-private". Follow the instructions, and leave settings at their defaults by pressing enter if you don't understand them.
When you're done, it will tell you to log out and log back in. Now you'll have a folder in your home folder called "Private". All files saved in there are automatically encrypted.

The Private folder is only accessible by you while you are logged in, and its files are encrypted by your password. *(Technically encrypted by a private key which is stored in ~/.ecryptfs, and that private key is encrypted by your password. This allows you to change your password and only need to recrypt the private key instead of all your files.)*

---

### Post by Pro-reason on 2009-10-29
> **Agent ME said:**
> When an email gets decrypted, for example in Thunderbird, it doesn't get saved to the hard drive, just held in ram while Thunderbird is open. When a file is decrypted, it doesn't have to be written to the hard drive in plaintext.
It doesn’t have to be, but the question is whether it does.  Do you have the knowledge that Thunderbird/Enigmail in particular makes sure it rights no temporary file?

> **Agent ME said:**
> 
The easiest way to manage encryption in Ubuntu is to set up ecryptfs. Open a terminal, and enter "ecryptfs-setup-private". Follow the instructions, and leave settings at their defaults by pressing enter if you don't understand them.
When you're done, it will tell you to log out and log back in. Now you'll have a folder in your home folder called "Private". All files saved in there are automatically encrypted.

The Private folder is only accessible by you while you are logged in, and its files are encrypted by your password. *(Technically encrypted by a private key which is stored in ~/.ecryptfs, and that private key is encrypted by your password. This allows you to change your password and only need to recrypt the private key instead of all your files.)*
I made reference to ~/Private before, so I know about this.

The point is... well, it’s what I said above.

---

