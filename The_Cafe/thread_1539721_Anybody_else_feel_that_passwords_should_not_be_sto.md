---
title: "Anybody else feel that passwords should not be stored plaintext in chrome?"
date: 2010-07-26
forum: The Cafe
---

### Post by josephellengar on 2010-07-26
I hope that this is not considered tech support, but I was wondering if it bothered anybody else that chrome stores passwords in plaintext?  I know it is possible to use lastpass and roboform, but I don't trust those any more than I trust someone who happens to have access to my computer.  I mean, anybody who I lend the computer to can open up a chrome window and look at my password list.  Even IE doesn't do that!  It just feels wrong.  And I need some sort of password manager ... all of my passwords (except for forums and games sites) are 20+ characters and none are the same.

---

### Post by RiceMonster on 2010-07-26
Pidgin does this too, and to be honest, it does bother me.

---

### Post by RevengeOfTheToxicRodent on 2010-07-26
> **rossholley said:**
> I hope that this is not considered tech support, but I was wondering if it bothered anybody else that chrome stores passwords in plaintext?  I know it is possible to use lastpass and roboform, but I don't trust those any more than I trust someone who happens to have access to my computer.  I mean, anybody who I lend the computer to can open up a chrome window and look at my password list.  Even IE doesn't do that!  It just feels wrong.  And I need some sort of password manager ... all of my passwords (except for forums and games sites) are 20+ characters and none are the same.

I think it would bother me more if I was using Chrome on Windows. 
Still, it's kind of bizarre when you consider the lengths Google went to to make Chrome as secure as possible.

---

### Post by Bachstelze on 2010-07-26
> **RiceMonster said:**
> Pidgin does this too, and to be honest, it does bother me.

FileZilla does it too, and a lot of others.  Doesn't really bother me, especially now when we have easy-as-pie encrypted home directories.

---

### Post by rg4w on 2010-07-26
It seems a bit rudimentary to always use encrypted files to store passwords.  Disappointing to see any modern software doing otherwise.

---

### Post by josephellengar on 2010-07-27
> **rg4w said:**
> It seems a bit rudimentary to always use encrypted files to store passwords.  Disappointing to see any modern software doing otherwise.

Yeah.  I want to see an encrypted file used to store the passwords and a master password required to reveal/edit them.  I looked on the extensions website but there was no extension to do this.

---

### Post by jerenept on 2010-07-27
> **rossholley said:**
> I hope that this is not considered tech support, but I was wondering if it bothered anybody else that chrome stores passwords in plaintext?  I know it is possible to use lastpass and roboform, but I don't trust those any more than I trust someone who happens to have access to my computer.  I mean, anybody who I lend the computer to can open up a chrome window and look at my password list.  Even IE doesn't do that!  It just feels wrong.  And I need some sort of password manager ... all of my passwords (except for forums and games sites) are 20+ characters and none are the same.

 Let me suggest a fix: Don't store your passwords in Chrome. (Maybe Keepassx or something.)

---

### Post by josephellengar on 2010-07-27
> **jerenept said:**
> Let me suggest a fix: Don't store your passwords in Chrome. (Maybe Keepassx or something.)

Oh, good idea.

---

### Post by earthpigg on 2010-07-27
it doesn't bother me, nor does pidgin doing this. on my netbook, /home folder is encrypted in case of theft. 

firefox may not store passwords in plain text, but anyone copying your ~/.mozilla folder can just copy that folder into their own ubuntu install, start firefox, and edit -> preferences -> security -> saved passwords -> there's all your saved passwords in plain text.

if someone has a way of looking at your chrome config files, they can surely copy them. if they can do that, they can surely copy ~/.mozilla too. so, plain text or not... as long as chrome/firefox knows how to open the data, it may as well be plain text.

saving them ***not*** as plaintext and calling it a 'security feature'.... only creates a false sense of security. 

remember when Win98 had login passwords, but all you had to do to bypass it was click through some help files and you could login without entering a password? same thing with fancy-schmancy obfuscated file formats, essentially.

if someone has access to your home folder and nothing is encrypted, they have access to any and all saved passwords and data. period. that applies to firefox, chrome, pidgin, empathy, et cetera. anything else is silly as a security feature if all the bad guy has to do is copy a few dotfiles and start the same software on the same operating system. If you can back up some dotfiles, restore them, and immediately gain access to all your saved skype/pidgin/chrome/firefox/etc passwords... why can't the bad guy?

he can. encrypt or bust.

another option, short of encrypting your ***entire*** home folder, is to encrypt just ~/.config/chromium or ~/.mozilla if that is your browser of choice using truecrypt or whatever you wish. 

be sure not to forget that one password, and you now have a place that you can securely store all the passwords you want in plaintext. even literally, just a regular OpenOffice or plaintext document with a list of all your usernames and passwords, sitting in ~/.config/chromium.

---

### Post by josephellengar on 2010-07-27
> **earthpigg said:**
> it doesn't bother me, nor does pidgin doing this. on my netbook, /home folder is encrypted in case of theft. 

firefox may not store passwords in plain text, but anyone copying your ~/.mozilla folder can just copy that folder into their own ubuntu install, start firefox, and edit -> preferences -> security -> saved passwords -> there's all your saved passwords in plain text.

if someone has a way of looking at your chrome config files, they can surely copy them. if they can do that, they can surely copy ~/.mozilla too. so, plain text or not... as long as chrome/firefox knows how to open the data, it may as well be plain text.

saving them ***not*** as plaintext only creates a false sense of security.

another option, short of encrypting your ***entire*** home folder, is to encrypt just ~/.config/chromium or ~/.mozilla if that is your browser of choice using truecrypt or whatever you wish.

be sure not to forget that one password, and you now have a place that you can securely store all the passwords you want in plaintext. even literally, just a regular text document with a list of all your usernames and passwords, sitting in ~/.config/chromium.

Point taken.  But I don't think that any browsers should do this.  They should all encrypt the passwords, and all require a password to see the stored passwords.

---

### Post by endotherm on 2010-07-27
given my druthers, nothing would be stored in plaintext, but especially credentials. seeing it always makes me cringe. sabnzbd does the same thing.

---

### Post by aysiu on 2010-07-27
> **earthpigg said:**
> 
firefox may not store passwords in plain text, but anyone copying your ~/.mozilla folder can just copy that folder into their own ubuntu install, start firefox, and edit -> preferences -> security -> saved passwords -> there's all your saved passwords in plain text. Not if you create a master password.

---

### Post by FuturePilot on 2010-07-27
> **earthpigg said:**
> it doesn't bother me, nor does pidgin doing this. on my netbook, /home folder is encrypted in case of theft. 
Pidgin most certainly does. Look in ~/.purple/accounts.xml

> firefox may not store passwords in plain text, but anyone copying your ~/.mozilla folder can just copy that folder into their own ubuntu install, start firefox, and edit -> preferences -> security -> saved passwords -> there's all your saved passwords in plain text.
Unless you use a master password in which case they are indeed encrypted.

---

### Post by endotherm on 2010-07-27
> **earthpigg said:**
> it doesn't bother me, nor does pidgin doing this. on my netbook, /home folder is encrypted in case of theft. 

firefox may not store passwords in plain text, but anyone copying your ~/.mozilla folder can just copy that folder into their own ubuntu install, start firefox, and edit -> preferences -> security -> saved passwords -> there's all your saved passwords in plain text.

if someone has a way of looking at your chrome config files, they can surely copy them. if they can do that, they can surely copy ~/.mozilla too. so, plain text or not... as long as chrome/firefox knows how to open the data, it may as well be plain text.

saving them ***not*** as plaintext only creates a false sense of security. 

if someone has access to your home folder and nothing is encrypted, they have access to any and all saved passwords and data. period. encryption or plaintext, imo, anything else is silly as a security feature. 

another option, short of encrypting your ***entire*** home folder, is to encrypt just ~/.config/chromium or ~/.mozilla if that is your browser of choice using truecrypt or whatever you wish.

be sure not to forget that one password, and you now have a place that you can securely store all the passwords you want in plaintext. even literally, just a regular OpenOffice or plaintext document with a list of all your usernames and passwords, sitting in ~/.config/chromium.
there are definitely ways to make the passwords non-portable if they wanted to. just salt the hash based on a characteristic of the mobo (cpu id for instance) that would fail on a new box.  a better solution would be to use whatever platforms secure credentials storage (seahorse i believe in ubuntu) to store them in a ciphertext.

storing the file in plaintext is problematic because it is being stored in a predictable location by a common application, that also happens to have access to that password and receives and processes commands from the web. that means that a good attack on chrome could conceivably retrieve your passwords remotely, even though the attacker does not have access to the local disk.

---

### Post by earthpigg on 2010-07-27
> **aysiu said:**
> Not if you create a master password.

> Unless you use a master password in which case they are indeed encrypted. 

i thought chrome had this feature. my mistake. that false assumption of mine invalidates a lot of my above post, then.

i guess the DIY fix is to use truecrypt or something similar to encrypt ~/.config/chromium and use that to achieve identical (but less user-friendly) functionality to firefox's master password.

one would have to make sure they decrypt that folder *before* starting chrome/chromium.

yes/no?

---

### Post by Mr. Picklesworth on 2010-07-27
The latest dev builds of Chromium (around 6.0.472, r53024) can store your passwords in the keyring appropriate to your operating system. So, the Linux version will store your passwords to gnome-keyring or kwallet, which are both nice and secure by encrypting your stored passwords via another password you enter at login.

Right now it's opt-in by launching Chromium with chromium-browser --password-store=detect

Once the feature is hardened, it will be default :)


If you need it *_now_*, Epiphany (the Gnome web browser) uses gnome-keyring already.


Basically any software that stores passwords but doesn't use a session keyring daemon like gnome-keyring (or a master password) is storing your password in something as good as plain text. It's definitely a problem, and I have been slowly weeding them out as well.

Come to think of it, with Empathy, Chromium and Nautilus for all my sftp stuff, that may finally be done!

---

### Post by earthpigg on 2010-07-27
> **Mr. Picklesworth said:**
> 
Come to think of it, with Empathy, Chromium and Nautilus for all my sftp stuff, that may finally be done!

If/when that is finally done, do you think it would be redundant to encrypt /home folders by default?



And, slightly off topic because I have never tried it and maybe someone else has:

If I backup /home/foo (where foo is an account I do not know the password to and has an encrypted ~), move to a fresh install, what would I need to do in order for the user foo to be able to login and have all of their settings and files and whatnot back? Assume Mr. Foo will not tell me his password.

---

### Post by endotherm on 2010-07-28
/home encryption is for a completely different usecase than we're talking about here. when you login your key is saved for access by all processes you spawn, including firefox, and the encryption is transparent, so ff just asks for the file, and the underlying system automatically decrypts it and loads it in ram. 

/home encryption is for protection against physical compromise, like a lost laptop or multi-user considerations. it doesn't protect anyone from anything as long as the user is logged in. it is only when the user is NOT logged in that disk encryption becomes useful.

---

### Post by aeiah on 2010-07-28
passwords that matter are only saved in a truecrypt image file, and no passwords at all (besides wireless access points) are saved on my netbook. 

i dont bother encrypting my netbook home partition either. why should i encourage the thief to reinstall an operating system when they can use mine, and get keylogged and have their photo taken? 8-)

---

### Post by endotherm on 2010-07-28
> **aeiah said:**
> passwords that matter are only saved in a truecrypt image file, and no passwords at all (besides wireless access points) are saved on my netbook. 

i dont bother encrypting my netbook home partition either. why should i encourage the thief to reinstall an operating system when they can use mine, and get keylogged and have their photo taken? 8-)
thats generally my approach, but I do use the keyring for samba/daap/sab/ etc. i don;t like automounting encryption for several reasons, but primarilly because if an attacker tries to boot my laptop while I am still there, then they'll just beat the password out of me. if they don;'t notice an archive deep in the filesystem though, then AES 256 will provide sufficient protection from technical attacks.

---

### Post by FuturePilot on 2010-07-28
> **earthpigg said:**
> If/when that is finally done, do you think it would be redundant to encrypt /home folders by default?
No. People store other sensitive data besides passwords.

> And, slightly off topic because I have never tried it and maybe someone else has:

If I backup /home/foo (where foo is an account I do not know the password to and has an encrypted ~), move to a fresh install, what would I need to do in order for the user foo to be able to login and have all of their settings and files and whatnot back? Assume Mr. Foo will not tell me his password.

Backup /home/.ecryptfs/foo, make sure foo uses the same login password on the new install and place the data in the same location on the new install.

---

### Post by NCLI on 2010-07-28
> **rossholley said:**
> I hope that this is not considered tech support, but I was wondering if it bothered anybody else that chrome stores passwords in plaintext?  I know it is possible to use lastpass and roboform, but I don't trust those any more than I trust someone who happens to have access to my computer.  I mean, anybody who I lend the computer to can open up a chrome window and look at my password list.  Even IE doesn't do that!  It just feels wrong.  And I need some sort of password manager ... all of my passwords (except for forums and games sites) are 20+ characters and none are the same.[URL="http://blog.tinisles.com/2010/01/should-you-trust-lastpass-com/"]
You can trust LastPass[/URL].

---

### Post by Paqman on 2010-07-28
> **aeiah said:**
> no passwords at all (besides wireless access points) are saved on my netbook. 


So you type them in repeatedly? You're now vulnerable to keylogging. Damned if you do, damned if you don't.

---

### Post by earthpigg on 2010-07-28
> **Paqman said:**
> So you type them in repeatedly? You're now vulnerable to keylogging. Damned if you do, damned if you don't.

he can copy/paste, and be sure to randomly copy something else as soon as he pastes the password :P

---

