---
title: "Cannot change password"
date: 2011-04-13
forum: Security
---

### Post by Paddy Landau on 2011-04-13
I want to change my password to make it more secure.

I go to System > Preferences > About Me > Change Password, and change it there.

However, the screen sticks (see attached screenshot). If I press Close, it closes but the password is not changed. If I wait... well, I waited over 16 minutes and nothing happened.

The odd thing is that about a month ago, I successfully changed the password using this method.

Please help. I'm using 64-bit Lucid 10.04.

---

### Post by SeijiSensei on 2011-04-13
> **Paddy Landau said:**
> I want to change my password to make it more secure.

I do all administrative things like this from a terminal.  It's much faster and easier.

```
sudo passwd paddy
```

You'll be prompted to enter your current password to gain root privileges via sudo, then you'll be prompted to enter the new password twice.

---

### Post by Paddy Landau on 2011-04-13
Thanks for that reply.

I notice that I can avoid using [FONT=Courier New]sudo passwd paddy[/FONT] and use just [FONT=Courier New]passwd[/FONT] on its own.

Do you know if it will also update the encryption? My folder is encrypted and so that needs to change, too. Actually, let me try it and I'll post back whether it works.

---

### Post by Paddy Landau on 2011-04-13
I've tried, and it works a treat, thank you. The encryption password was updated, and so was the keyring.

---

### Post by bodhi.zazen on 2011-04-13
> **Paddy Landau said:**
> Thanks for that reply.

I notice that I can avoid using [FONT=Courier New]sudo passwd paddy[/FONT] and use just [FONT=Courier New]passwd[/FONT] on its own.

Do you know if it will also update the encryption? My folder is encrypted and so that needs to change, too. Actually, let me try it and I'll post back whether it works.

If you are using encryption, then changing your password on the command line will NOT configure ecryptfs (it will use the old password).

You have to re-wrap the ecryptfs password.

I believe the command is:

```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
``` 

You will be prompted for the old passphrase and then the new.

If you already logged out, you will have to mount (decrypt) your home directory first.

Again, in the command line:

```
ecryptfs-mount-private
```

Use your old password. Then cd (to your decrypted home).

Normally the easiest method of changing your password with an encrypted home is with the graphical tools, not sure why you are having a problem with that, perhaps file a bug report ?

---

### Post by SeijiSensei on 2011-04-13
> **Paddy Landau said:**
> I notice that I can avoid using [FONT=Courier New]sudo passwd paddy[/FONT] and use just [FONT=Courier New]passwd[/FONT] on its own.

I forgot you were changing your own password for which you obviously don't need root privileges.  I'm usually creating or managing other accounts on servers, so I use "sudo passwd" all the time. Glad to hear it all worked for you.

---

### Post by Paddy Landau on 2011-04-13
> **bodhi.zazen said:**
> If you are using encryption, then changing your password on the command line will NOT configure ecryptfs (it will use the old password).
Well, this must have been fixed in the latest version (I'm using 10.04). I changed my password using passwd, rebooted to ensure a fresh start, and everything is fine.

---

### Post by Paddy Landau on 2011-04-13
Oh, hang on...

If I use [FONT=Courier New]passwd[/FONT], I need to type my password in first. That obviously allows the system to access my encryption password.

However, if I type [FONT=Courier New]sudo passwd [user][/FONT], then I don't have to type the user's existing password. This means that the encryption cannot be accessed, and the user will have to manually change his password.

I guess there's the difference!

---

### Post by bodhi.zazen on 2011-04-13
glad you got it sorted.

Yes, ecryptfs will prevent root from accessing your encrypted /home by simply changing the password for your user, or at least it did the last time I looked.

If passwd has been patched for your user, fantastic, it was not last I looked.

---

