---
title: "Login Security in Karmic"
date: 2009-11-16
forum: Security
---

### Post by Logan1985 on 2009-11-16
I have Ubuntu 9.10 running on my work laptop. I also use this laptop for personal stuff like mail in Thunderbird, etc.

My concern surrounds the possibility of the laptop being stolen.

When I installed Ubuntu I *didn't* select the option that mentioned home folder encryption..I took the first option (I can't remembe the wording of it).

Now..will it be easy for someone to boot into single user mode and then reset my password?

What I had wanted to do is use Truecrypyt and set up pre-boot authentication, but I see that this is not available in the Linux version, which I am quite surpirsed at (I'm sure there is a perfectly good reason).

Anyway, if anybody can give me pointers as to what I should encrypt and by what means, it would be most appreciated.

Thanks

---

### Post by Trebaruna on 2009-11-16
Yes, it will be quite easy for someone to access your stuff.

Using the alternate CD you can choose full disk encryption during the installation process. This should set everything up for you. I believe there's an easy checkbox to select that version on the main Ubuntu website.

Encrypting your home folder should also work, methinks. Even if someone did change your password they'd need the old one to decrypt the relevant files, so you're pretty safe with this option, too.

EDIT: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Logan1985 on 2009-11-16
Many thanks.

I've read about the alternate installer...why is it necessary to use this rather than the usual one?

Also, will I need to re-install to achieve what you have suggested? Or can I do this to my existing setup?

With full disk encryption set up using this method, does that prevent someone easily resetting my password via single user mode? Or is it a case of they can reset it, but cannot decrypt anything without the original password like you already mentioned?

Thanks again

---

### Post by Trebaruna on 2009-11-16
> **Logan1985 said:**
> 
I've read about the alternate installer...why is it necessary to use this rather than the usual one?

Because the "normal" installer does not include the option to encrypt the entire harddrive, unfortunately. If you're happy just encrypting your home folder then the normal ISO will do fine.

> **Logan1985 said:**
> 
Also, will I need to re-install to achieve what you have suggested? Or can I do this to my existing setup?

Yes, I'm afraid a new install is required, as far as I know.

> **Logan1985 said:**
> 
With full disk encryption set up using this method, does that prevent someone easily resetting my password via single user mode? Or is it a case of they can reset it, but cannot decrypt anything without the original password like you already mentioned?

I'm not entirely certain about the details here, but I believe it works like this:
-Ubuntu begins loading up, and detects an encrypted system
-It asks for your passphrase which it uses as the key to decrypt the system
-It continues to load until it reaches the login screen where you type your account password.

So there's a passphrase and an account pass. The former doesn't need to be stored anywhere I think --if decryption works it was the right passphrase, otherwise not--, and the latter sits in the encrypted part of the system so it cannot be accessed without knowing the former.

If you only encrypt the home folder someone could change your password and perhaps even login, I don't know. They could not, however, get to any of your files or settings (like your browser and email client and their stored passwords) because the original password would've been used as the key.

---

### Post by Sesshomurai on 2009-11-16
The other major problem with login security in Karmic is the poor decision to show the usernames on the login screen.

It should not be possible to see what valid user account names are.

---

### Post by Logan1985 on 2009-11-16
> **Trebaruna said:**
> Because the "normal" installer does not include the option to encrypt the entire harddrive, unfortunately. If you're happy just encrypting your home folder then the normal ISO will do fine.

Yes, I'm afraid a new install is required, as far as I know.

I'm not entirely certain about the details here, but I believe it works like this:
-Ubuntu begins loading up, and detects an encrypted system
-It asks for your passphrase which it uses as the key to decrypt the system
-It continues to load until it reaches the login screen where you type your account password.

So there's a passphrase and an account pass. The former doesn't need to be stored anywhere I think --if decryption works it was the right passphrase, otherwise not--, and the latter sits in the encrypted part of the system so it cannot be accessed without knowing the former.

If you only encrypt the home folder someone could change your password and perhaps even login, I don't know. They could not, however, get to any of your files or settings (like your browser and email client and their stored passwords) because the original password would've been used as the key.

Thanks for the additional explaination. Unfortunately I have spent too much time setting up this system to even consider starting again. The reason I didn't select the option to encrypt the home folder was that I had planned to use full disk encryption with TrueCrypt and enable pre-boot authentication. At the time I didn't realize that this isn't actually available in the Linux version :(

Sesshomurai - I agree with you on that point. That should be optional at least! Or maybe it is and I just don't know it :p

So..any suggestions as how best to secure/encrypt my laptop *without *a reinstall?

---

### Post by cdenley on 2009-11-16
Full disk encryption will result in a significant decrease in system performance. Encrypting only your home directory is usually a good compromise, since it should contain all your sensitive data (except your system user password hash).

---

### Post by hictio on 2009-11-16
> **cdenley said:**
> Full disk encryption will result in a significant decrease in system performance. Encrypting only your home directory is usually a good compromise, since it should contain all your sensitive data (except your system user password hash).

Sorry to hijack, but, regarding this performance issue:
How would one leave outside of the "full home" encrypting the media files? For instance the music and video files? Placing them on the ~/Public directory is enough? Or those file should be placed completely outside the user's home?

---

### Post by Logan1985 on 2009-11-16
I found this guide: [http://www.linux-mag.com/id/7568/2/](http://www.linux-mag.com/id/7568/2/)

I got as far as the rsync which completed, but it gave some errors..but I have no idea what the issues were. Anybody know what I can check? Is there some kind of log for rsync?

It *seems* that I can safely complete this procedure because /home get's backed up (unencrypted) as part of it...am I missing something here...or can I just restore that folder if something goes wrong?

If not I think I actually may just bite the bullet and start from scratch....urgh.

EDIT: Is there a way I can back up all settings eg custom menus, software packages, etc etc and restore, then copy contents of old home to new?

---

