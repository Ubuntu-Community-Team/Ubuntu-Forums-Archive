---
title: "putting passwords in a txt file and encrypting?"
date: 2009-11-12
forum: Security
---

### Post by darrude on 2009-11-12
Hi all,
 
I'm hoping somebody could help me with a really basic encrytpion question.
 
I recently had to re-install my ubuntu, and i've forgotten loads of passwords for different website.  What I was hoping to do was create a txt file with user names / passwords for various sites that I could store on my NAS drive.  The concern I, is that  if i do this, and the file falls into the wrong hands they'd have access to everyting.  
 
Can anyone recommend some software that could password protect / encrypt this file (preferably that would work on window's as well) with a reasonable level of encyption. 
 
My concern is my Nas drive might get pinched then they (the burgalor) would get all my log on details for various sites (and as most website store credit card info etc, it's quite a scary thought).
 
or is there a better way of doing this where I store the passwords somwhere other than the pc.
 
Many Thanks,
 
Darren

---

### Post by tubbygweilo on 2009-11-12
Darren,
A [truecrypt]("http://www.truecrypt.org/docs/") file containing clear text passwords may well meet you needs as it runs with windows and Ubuntu. It is a safe place to store things and you only need one pass phrase to access the stored data, it is **not** an automated master username/password management system like those offered by firefox thunderbird and their  like.

---

### Post by EJeanmaire on 2009-11-12
> **tubbygweilo said:**
> Darren,
A [truecrypt]("http://www.truecrypt.org/docs/") file containing clear text passwords may well meet you needs as it runs with windows and Ubuntu. It is a safe place to store things and you only need one pass phrase to access the stored data, it is **not** an automated master username/password management system like those offered by firefox thunderbird and their  like.

This.  A truecrypt container is exactly what you are looking for.

---

### Post by mr-woof on 2009-11-12
What I've just started to do is encrypt an old pen drive with True Crypt and keep all my user name / passwords on that.

---

### Post by The Cog on 2009-11-12
I use a password protected OpenOffice .ods spreadsheet. I even have separate sheets for home and work passwords. Apart from being easy to use (being a spreadsheet), I don't have to do separate unencrypting/recrypting when I read/update it. Just enter the password when I open it.

---

### Post by FuturePilot on 2009-11-12
Something like KeePassX might be a good solution.

---

### Post by osjak on 2009-11-13
> **The Cog said:**
> I use a password protected OpenOffice .ods spreadsheet. I even have separate sheets for home and work passwords. Apart from being easy to use (being a spreadsheet), I don't have to do separate unencrypting/recrypting when I read/update it. Just enter the password when I open it.
I would strongly advise against this. OpenOffice is not designed to encrypt files. Its password protection is enough to keep one secretary from changing files of another one, yes. But all it does is places the file into a zip archive with a password. If someone who knows what he is doing gets your file, he can use any zip password recovery program to figure out the password. And there are quite a few of those around.
[http://www.linux.com/archive/feature/61635](http://www.linux.com/archive/feature/61635)
[http://www.google.com/search?q=zip+password+recovery](http://www.google.com/search?q=zip+password+recovery)


Keeping your passwords in a TrueCrypt file is one of the ways to do it right. But then you need to keep a backup copy of that file somewhere in case your machine dies. What I ended up doing is installing the [FireGPG]("http://getfiregpg.org/s/home") extension in my browser, and emailing encrypted messages with passwords to my GMail account. One message per website/service. I have a tag "Passwords" to keep them all together easily accessible. And I keep a backup copy of my private key in a TrueCrypt file in a safe place in case my machine goes down :)

---

### Post by Soul-Sing on 2009-11-13
> **futurepilot said:**
> something like keepassx might be a good solution.


+1

> would strongly advise against this. Openoffice is not designed to encrypt files. Its password protection is enough to keep one secretary from changing files of another one,

+1

---

### Post by The Cog on 2009-11-13
> **osjak said:**
> I would strongly advise against this. OpenOffice is not designed to encrypt files. Its password protection is enough to keep one secretary from changing files of another one, yes. But all it does is places the file into a zip archive with a password. If someone who knows what he is doing gets your file, he can use any zip password recovery program to figure out the password. And there are quite a few of those around.
[http://www.linux.com/archive/feature/61635](http://www.linux.com/archive/feature/61635)
[http://www.google.com/search?q=zip+password+recovery](http://www.google.com/search?q=zip+password+recovery)


What do you think the difference is between brute-force attacking an OOo document password and brute-force attacking a truecrypt password? It seems to ne that either way, you need to either run through a dictionary of candidate passwords (as the article you posted says) or just sequentially work through all possible passwords.

If you can convince me there's a material difference then I'll consider changing my ways, but I can't think of a material difference.

---

### Post by XCan on 2009-11-13
The only difference I can think of (unless there's any exploits of course) is that the algorithm is faster for OO and the .zip, and the algorithm is definied. Whereas it may not even be obvious to know which algorithm was used for a Truecrypt volume.

---

### Post by osjak on 2009-11-13
> **The Cog said:**
> What do you think the difference is between brute-force attacking an OOo document password and brute-force attacking a truecrypt password? It seems to ne that either way, you need to either run through a dictionary of candidate passwords (as the article you posted says) or just sequentially work through all possible passwords.

If you can convince me there's a material difference then I'll consider changing my ways, but I can't think of a material difference.
There is a material difference. When you use OpenOffice password, the program uses that password to keep your target file locked up. So all you need to view it is a password. 

When you use the TrueCrypt, it uses a key file to encrypt your target file (practically impossible to brute force that encryption), and then it uses a password to lock down your key file. So if someone gets your encrypted file, a brute force attack would be useless. In order to brute force a file encrypted with  TrueCrypt, one would need that file, the key file and then try to bruteforce the password on the key file. Given that TrueCrypt places no identifiable info in the encrypted file, one would have to know exactly what file you keep your passwords in, and that you use TrueCrypt. Add that TrueCrypt can use any file as a key file (some mp3 file you designate) if you want to make your key file discovery difficult. This is a very different level of hacking, someone would have to really want your data, know your habbits, and have access to your computer with the key file.  

So the bottom line is if you lose your USB drive with an OpenOffice encrypted file, anyone can open it given some effort. If you lose that USB drive with a TrueCrypt file on it, only people knowing what they are doing AND having access to your key file would have a chance in brute forcing it.

Of course things not always go as planned ;)
[http://xkcd.com/538/](http://xkcd.com/538/)

---

### Post by ratcheer on 2009-11-13
I use KeePassX and I keep my database in multiple locations - two PC's, Gmail, and two thumb drives.

Tim

---

### Post by bodhi.zazen on 2009-11-13
> **futurepilot said:**
> something like keepassx might be a good solution.

+1

---

### Post by darrude on 2009-11-14
Hi All,

Thank you so much for your replies.  I had already installed Truecrypt so have managed now to set this up (i thought it was for ecrypting entire drives when i used it initially). 

I like the old thumb drive idea, I now have a encrypted SD card that was sat around doing nothing and a backup container on my main PC.  I will give Keepassx a go as well and see which works best for me.  

I'm actually thinking of storing all personal Document in an Encrypted file now i've found out it relativly easy to do (A friend at work have recently become a victim of Identity theft, it made me start thinking if somebody stole my NAS drive they would easily be able to steal my identity!)

Again, thank you all so much for your replies.  I've only been on linux a few months, but thanks to the help, support and knowledge available on this website I've become a linux convert.  

thanks and regards,

Darren

---

### Post by ratcheer on 2009-11-14
Well, one great thing about KeePassX is that there is also KeePass for Windows, and they can share the same stored databases. So, if you are running it on both platforms, you can make an update on one platform and copy the database to the other platform (or, share the same database on a network) and have immediate access to all changes.

Tim

---

### Post by kevdog on 2009-11-14
I believe the problem with KeePass is with the incompatibilities between version 1.x and 2.x releases.  Kind of a deal breaker for me.

---

### Post by The Cog on 2009-11-14
@osjak:
Nice explanation - thanks.

---

