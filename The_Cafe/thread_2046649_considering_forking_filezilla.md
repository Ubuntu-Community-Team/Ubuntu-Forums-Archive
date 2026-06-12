---
title: "considering forking filezilla"
date: 2012-08-23
forum: The Cafe
---

### Post by Primefalcon on 2012-08-23
Here's the deal, filezilla stores all usernames and passwords saved in plaintext files..... developer is completely opposed to volunteers even adding this as an option feature.....

I am considering forking filezilla to use GPG with a master password to encrypt these files....

and I am wondering if:

1. Anyone else has done this (hence no need to do this)
2. I would be able to handle the Linux version myself... however a windows version would require someone more familiar with Windows Development
3. also general feedback/opinions (positive and negative) would be welcome

---

### Post by Dave_L on 2012-08-23
This is filezilla client-side?

Did the developer provide a reason for opposing it as an option, even if someone else does the programming?

Would it be compatible with Seahorse?

---

### Post by hakermania on 2012-08-23
+1 we don't want our passwords as plain text!

---

### Post by Mmmbopdowedop on 2012-08-23
> **hakermania said:**
> +1 we don't want our passwords as plain text!

Whilst I can understand not wanting your passwords stored in plain text, I can't help but wonder why would you go to the effort to persue this over a minor problem?

There's (probably) hundreds of various FTP clients that work the same, gFTP for example, looks the same, works the same, I usually use sshfs myself, which mounts the sFTP folder as a drive, works great!

It's a bit silly to go out of your way to try and correct something in a great program, that will probably mean nothing to the masses.

Nobody is going to flock to your fork, I know i'd sure as hell trust a Filezilla product over yours.

---

### Post by ojdon on 2012-08-23
Like what everyone else is stating, forking is just wasting your time. Look for an alternative client instead.

---

### Post by mr john on 2012-08-23
Thats terrible security. When I was at university they blocked people from installing msn messenger in the labs. Everybody started using Trillian instead, but nobody realized it stored the passwords in text files. Needless to say a list of peoples usernames and passwords started to float around.

If the developer refuses to embrace security with SFTP then I see no why anyone would trust that product. The whole point of SFTP over FTP is increased security, so having passwords unencrypted seems a bit silly to me. 

I for one will not be using that product after reading this. I use other clients anyway though, because I've always felt that the GUI of filezilla clients were inferior to the likes of WinSCP and Nautilus.

---

### Post by Mmmbopdowedop on 2012-08-23
> **mr john said:**
> Thats terrible security. When I was at university they blocked people from installing msn messenger in the labs. Everybody started using Trillian instead, but nobody realized it stored the passwords in text files. Needless to say a list of peoples usernames and passwords started to float around.

If the developer refuses to embrace security with SFTP then I see no why anyone would trust that product. The whole point of SFTP over FTP is increased security, so having passwords unencrypted seems a bit silly to me. 

I for one will not be using that product after reading this. I use other clients anyway though, because I've always felt that the GUI of filezilla clients were inferior to the likes of WinSCP and Nautilus.

If you're refusing to use Filezilla because of this, then i'd question your state of mind. You've either left your computer open to the world, or you're imcompetent with it and don't know what you're doing, installing from various repositories and have no idea what's going on.

If you think i'm incorrect, then there's really no reason to stop using it.

It's a great program with a lot of features.

---

### Post by synaptix on 2012-08-23
Been using FileZilla for quite a long time now, never had a security issues whether it was on Windows or Linux.

---

### Post by Primefalcon on 2012-08-23
> **synaptix said:**
> Been using FileZilla for quite a long time now, never had a security issues whether it was on Windows or Linux.
The guys reasoning when asked is encryption is just a waste of time and only provides a false sense of security... so why bother... 

BTW this is a direct quote from the guy...
> If your system is secure, you can use nuclear missile launch codes as desktop background.

Links to forum posts on filezilla forums where he is discussing it:
[http://forum.filezilla-project.org/viewtopic.php?f=3&t=17932](http://forum.filezilla-project.org/viewtopic.php?f=3&t=17932)
and
[http://forum.filezilla-project.org/viewtopic.php?f=1&t=23736](http://forum.filezilla-project.org/viewtopic.php?f=1&t=23736)

My advice is if your going to use it, is either don't save the password or use key based logins..

and the reason I am thinking of ding this, is the fact that apart from this issue Filezilla is the best gui program out there...

---

### Post by forrestcupp on 2012-08-23
> **Primefalcon said:**
> The guys reasoning when asked is encryption is just a waste of time and only provides a false sense of security... so why bother... 

Sounds exactly like the GnuCash devs' ridiculous reasoning for why they don't have any password capability at all in their financial software.

I say go for it, and if people don't want to use it, it's their loss.

---

### Post by wojox on 2012-08-23
> **forrestcupp said:**
> 
I say go for it, and if people don't want to use it, it's their loss.

+1 :p

---

### Post by Paqman on 2012-08-24
I've never bothered with a seperate FTP client on Linux. Between Nautilus and SSH I can get anything I want done on my VPS.

---

### Post by Lars Noodén on 2012-08-24
> **Primefalcon said:**
> ...
My advice is if your going to use it, is either don't save the password or use key based logins...


One problem is that if you enter your password in Filezilla, it gets saved in plain text whether you want it to or not:

[http://trac.filezilla-project.org/ticket/4507](http://trac.filezilla-project.org/ticket/4507)

---

### Post by zombifier25 on 2012-08-24
> **forrestcupp said:**
> Sounds exactly like the GnuCash devs' ridiculous reasoning for why they don't have any password capability at all in their financial software.

I say go for it, and if people don't want to use it, it's their loss.

Indeed. It's also the same reason Pidgin used plain text passwords. They assumed that all Pidgin users are experts in IT and if the file is in plain text then the users will treat it with more care, and if the file was obfuscated it would create a false sense of security.

I don't know if it should be forked though.

---

### Post by Primefalcon on 2012-08-24
Ok I'll start setting things :-). I probably would of forked it anyhow so to speak even if just for personal use

---

### Post by Primefalcon on 2012-08-24
feel free to shoot some name idea's and even maybe an icon for it :-), otherwise I'll might end up calling it something kinda silly like primezilla lol

---

