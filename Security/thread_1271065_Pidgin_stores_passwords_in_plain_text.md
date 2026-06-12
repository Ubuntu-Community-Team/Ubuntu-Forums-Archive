---
title: "Pidgin stores passwords in plain text"
date: 2009-09-20
forum: Security
---

### Post by Sarmacid on 2009-09-20
I just realized today that pidgin stores username/password for accounts in plain text, if you want to see for yourself open up /home/yourusername/.purple/accounts.html

Seems to me like a very big issue, not only because a lot of people can see the passwords, but mostly because I had no idea this was the default behaviour.

Is there any way to change this?

---

### Post by MechaMechanism on 2009-09-20
> **Sarmacid said:**
> I just realized today that pidgin stores username/password for accounts in plain text, if you want to see for yourself open up /home/yourusername/.purple/accounts.html

Seems to me like a very big issue, not only because a lot of people can see the passwords, but mostly because I had no idea this was the default behaviour.

Is there any way to change this?Well I look at it this way in a single user environment.  If someone can read your username/password it's because your computer is either compromised or they have access to the physical machine.  Now in a multi-user environment is where it gets really interesting.  In the case of multiple user accounts each user home directory probably needs to be private.  See here at [[color=red]Ubuntu Profile Security[/color]]("https://help.ubuntu.com/9.04/serverguide/C/user-management.html"). Search for sub heading "User Profile Security".  Now maybe you don't want a private home directory then take a look here at [[color=red]FilePermissions[/color]]("https://help.ubuntu.com/community/FilePermissions") for setting permissions on individual files.

---

### Post by falconindy on 2009-09-20
I understand your concern, but....

If your passwords for your IM accounts are different than other passwords you use, what's the potential harm? Someone impersonates you and tells your friends you enjoy cross dressing on weekends?

It's not as if your bank account or any sensitive personal data is at stake here.

---

### Post by ibuclaw on 2009-09-20
> **falconindy said:**
> I understand your concern, but....

If your passwords for your IM accounts are different than other passwords you use, what's the potential harm? Someone impersonates you and tells your friends you enjoy cross dressing on weekends?

It's not as if your bank account or any sensitive personal data is at stake here.

Actually, his bank account is at stake here...

If he is using MSN Protocol, that means that whoever has his password can also access his Email, look at what he is subscribed to (ie: amazon.com) request a "forgotten password" at the site, to which will be sent to the compromised email, and then the attacker can then go onto "change details" and have access to the details of the card the victim uses.

I agree, this seems like a security issue that pidgin should be taking care of transparently. But equally, if pidgin is to encrypt the password, it must be able to decrypt the password too, and therein lies the major problem. With the source code being open, anyone can decrypt it for their own twisted use.
You do have an onion layer of protection though, as the .purple directory has 600 permissions, which will deny other users the ability to traverse into the directory.

So apart from not allowing people to sign into your profile on ubuntu, your only security is that you must not allow pidgin to remember passwords at all.

Think before you post. ;)

---

### Post by kevdog on 2009-09-20
If the password file only has 600 permissions, then I don't see what the problem is?

---

### Post by rookcifer on 2009-09-20
Why the worry?  All you have to do is use gnome-keyring.

I use Kubuntu, and Kopete automatically uses KWallet, which does the same thing.

---

### Post by falconindy on 2009-09-20
> **tinivole said:**
> Actually, his bank account is at stake here...

If he is using MSN Protocol, that means that whoever has his password can also access his Email, look at what he is subscribed to (ie: amazon.com) request a "forgotten password" at the site, to which will be sent to the compromised email, and then the attacker can then go onto "change details" and have access to the details of the card the victim uses.
Haha, ok... you've got me there. I had considered the whole IM to email effect (would work with yahoo as well) but I would hope that people are smarter than this and have the common sense to separate these things. I have msn and yahoo messenger accounts, and I don't even consider the fact that there are email addresses attached to them. That's what gmail is for!

---

### Post by Sarmacid on 2009-09-21
> **falconindy said:**
> Haha, ok... you've got me there. I had considered the whole IM to email effect (would work with yahoo as well) but I would hope that people are smarter than this and have the common sense to separate these things. I have msn and yahoo messenger accounts, and I don't even consider the fact that there are email addresses attached to them. That's what gmail is for!

Actually I rely the most on googletalk since MSN sucks and never tried Yahoo.

---

### Post by paradigm2 on 2009-09-27
It adds another potential issue.  If yet another file is written with a cleartext password and the computer is ever stolen then that means the thief has yet another password.

Sure encryption and good physical security would prevent this but security should be layered as much as possible not relying on prevention at a mere single point.

Pidgin should ideally NOT be storing a cleartext password.

---

### Post by zeroseven0183 on 2010-01-08
So what now? Is there a way to sort of prevent or change how Pidgin works in storing (or not storing) passwords?

---

### Post by BkkBonanza on 2010-01-08
See here, (amazing what google can find for you in <1 minute)

[http://www.cyber-knowledge.net/blog/?p=216](http://www.cyber-knowledge.net/blog/?p=216)

Cases like this make me glad I use an encrypted home directory,

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

---

### Post by Sarmacid on 2010-01-08
Thanks for the links BkkBonaza.

---

### Post by nodiscc on 2011-01-18
Hello,
sorry to resurrect an old thread, but this is still a problem in pidgin 2.7.3 (which is the default in debian squeeze), and newest 2.7.9 from the pidgin PPA looks affected too:
passwords are still stored in _clear text_ in the accounts.xml file.

I found this: [http://code.google.com/p/pidgin-gnome-keyring/](http://code.google.com/p/pidgin-gnome-keyring/)

but I don't know if I can trust the code... (no C skills). I reported it on pidgin's trac but still no answer. Maybe someone could check if that's legit? (at least I tried and it DOES store passwords in the keyring).

Thanks !

---

### Post by DodgeV83 on 2011-01-18
People have complained about this many many many times.  People have also complained about similar issues in Ubuntu many many many times.

[http://www.omgubuntu.co.uk/2009/10/did-you-know-gnome-lets-anyone-see-your-keyring-passwords-msn-wifi-twitter-etc-without-needing-a-password/](http://www.omgubuntu.co.uk/2009/10/did-you-know-gnome-lets-anyone-see-your-keyring-passwords-msn-wifi-twitter-etc-without-needing-a-password/)

[http://ubuntuforums.org/showthread.php?t=1302342&page=1](http://ubuntuforums.org/showthread.php?t=1302342&page=1)

They know the passwords are stored in plain text.  They will probably never change it.  "If someone has physical access to your machine they can already extract all of your password" is the common response.  I would think you'd want to make it as hard as possible (the story I linked above shows you can click "System -> Preferences -> Password" and see all the saved passwords in plaintext), but the devs disagree.

They are trying to perpetuate the idea that no one should ever be using your computer while you are logged in.  I would prefer that turning around for 10 seconds without locking my computer wouldn't allow someone with 0 technical knowledge to see all my password, but that's the way it is :-({|=

---

### Post by DZ* on 2011-01-19
Pidgin devs argue that securing passwords is not an issue that pidgin as a particular application needs to deal with.

For unencrypted accounts I solve this by symlinking .purple to an encrypted folder which I mount when needed.

> **rookcifer said:**
> Why the worry?  All you have to do is use gnome-keyring.

gnome-keyring won't currently help encrypting pidgin passwords

[http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)


> **rookcifer said:**
> I use Kubuntu, and Kopete automatically uses KWallet, which does the same thing.

I use Pidgin under Kubuntu :-)

---

### Post by nodiscc on 2011-01-21
Hi all and thanks for your answers. I'd like to add some precisions:

> gnome-keyring won't currently help encrypting pidgin passwords

How that? It alreday does for, eg, wireless keys, and would be a good way to integrate pidgin's password encryption in the several desktop environments.

> [**http://developer.pidgin.im/wiki/PlainTextPasswords**]("http://developer.pidgin.im/wiki/PlainTextPasswords")
No. The Pidgin developers are generally open to, and would encourage integration with keyrings

But my question was about [http://code.google.com/p/pidgin-gnome-keyring/](http://code.google.com/p/pidgin-gnome-keyring/) . I tested that by copying the plugin to /usr/lib/pidgin/, and when i logged on some random account, it actually saved my password to the keyring (gnome-keyring). And no more traces of it in ~/.purple/accounts.xml. Looks nice. I'm asking for someone with more C skills to look look a bit inside it, and let us know if it's clean.

It could be a great improvement. I can use the symlink method, but it isn't something I would recommend to newbs.

Thanks

---

