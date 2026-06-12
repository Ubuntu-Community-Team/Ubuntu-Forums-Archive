---
title: "Encryption tools other than Truecrypt"
date: 2012-12-11
forum: Security
---

### Post by Hungry Man on 2012-12-11
I'm wondering if there are tools similar to Truecrypt for file encryption.

---

### Post by Soul-Sing on 2012-12-12
> **Hungry Man said:**
> I'm wondering if there are tools similar to Truecrypt for file encryption.

-cryptkeeper
- is it an option to .zip or.tar the file securing it with a pass?

---

### Post by tubbygweilo on 2012-12-12
Hungry Man, which functions, processes used by Truecrypt do you not wish to use or see in this product you are seeking?

---

### Post by Hungry Man on 2012-12-12
It's nothing against Truecrypt. I'm just curious about other programs. What I'm looking for is an encryption tool for encrypting files in a cryptographically secure way.

@Soul-Sing,

.zip password encryption is very weak. I'm not sure about .tar.

---

### Post by DanR01 on 2012-12-12
If you just want to encrypt individual files what about gpg or gpa?

I've also played around with scrypt and bcrypt. The latter uses blowfish encryption. These are in the repos. scrypt claims to be more secure against hardware based attacks.

---

### Post by Hungry Man on 2012-12-12
Isn't Scrypt for key derivation? Can I use it to encrypt files? I'll have a look ASAP, thanks.

---

### Post by DuckHook on 2012-12-13
Depending on what you want to use it for, consider ecryptfs. Tightly knit into Ubuntu. I believe it is the tool used for encryption of /home and entire disk when this option is chosen at install. Sort of like KVM in the VM world--already part of the kernel. Brief Wikipedia description [here]("http://en.wikipedia.org/wiki/ECryptfs"). Advantage for me is, because encryption metadata is in the file itself, the encrypted file is self-contained. This has advantages for sensitive files that you want to store/transfer to the cloud. I've used it for accounting records that I upload to Ubuntu One/Dropbox. Disadvantage: no gui, which is a big drawback for me because I'm not that familiar with its CLI yet. Also see its *man* page. If encrypting individual files and directories, need to do:

```
sudo apt-get install ecryptfs-utils
```

---

### Post by Hungry Man on 2012-12-13
Thanks DuckHook. I much prefer GUI programs, unfortunately. It's a shame it doesn't have one.

---

### Post by sahabcse on 2012-12-13
Try LUKS – The Linux Unified Key Setup – and dm-crypt.

I think GUI not available for this

---

### Post by DuckHook on 2012-12-13
> **Hungry Man said:**
> ...I much prefer GUI programs...

As do I. Am getting better with the command line all the time, but my main concern with Truecrypt actually is that it isn't an Ubuntu-sanctioned app and is not in the repositories. As an ultra-paranoid, I don't like loading anything from outside the repositories. Seems kinda contradictory to enhance security by going to some outside site that isn't sanctioned. However, lots of people do with apparently good results, so you may be okay with it.

---

### Post by Hungry Man on 2012-12-13
It's due to licensing issues. Truecrypt has very strange licenses I believe.

---

### Post by Dave_L on 2012-12-13
> **Hungry Man said:**
> It's due to licensing issues. Truecrypt has very strange licenses I believe.

[http://www.truecrypt.org/legal/license](http://www.truecrypt.org/legal/license)

I've read the TrueCrypt license before, and didn't see anything strange about it. Maybe I'm missing something.

---

### Post by Hungry Man on 2012-12-13
[https://bugs.launchpad.net/ubuntu/+bug/109701](https://bugs.launchpad.net/ubuntu/+bug/109701)

---

### Post by DuckHook on 2012-12-13
...which is unfortuante because [this]("http://www.linuxuser.co.uk/reviews/the-best-file-encryption-software-in-open-source") says Truecrypt is faster than just about anything else out there, including ecryptfs.

---

### Post by rjbl on 2012-12-15
> **DuckHook said:**
> As do I. Am getting better with the command line all the time, but my main concern with Truecrypt actually is that it isn't an Ubuntu-sanctioned app and is not in the repositories. As an ultra-paranoid, I don't like loading anything from outside the repositories. Seems kinda contradictory to enhance security by going to some outside site that isn't sanctioned. However, lots of people do with apparently good results, so you may be okay with it.

I'd  not be too concerned that Truecrypt isn't 'an Ubuntu-sanctioned app  and  is not in the repositories'. The system is distributed direct from  the  developers as a PGP signed .tar.gz package and is tightly  authenticated.

The  Truecrypt system is highly reputable and, as an openly published  source  code it has been heavily scrutinized and is widely believed to  be  robust, well-engineered and fit for purpose. It's a competent  product  and well-regarded as a protector of personal privacy. Whether  some  sinister acronymic agency, somewhere in this wide world, has found  a way  of breaking into it is, and will remain, unknowable. It wasn't  designed  to withstand unlimited-resource attacks by guys with clusters  of  super-computers at their fingertips. Theoreticaly it remains  doubtful  that they can succeed, practically it is unlikely that they'd  throw  gazillions at breaking *our*  crypto. Nothing the average  guy does  is interesting enough to justify spending that sort of time  and money  puzzling out what he's doing.

However, the weakness of all crypto  systems is the guy who uses it. He  will insist on writing his password  down somewhere - in case he forgets  it. He may be a bit cryptic with his  notes; but quite a lot of the  sinister three-letter men are now getting  quite good at guessing. 

The principal crypto systems (except  microsofts EFS) are pretty good at  NOT keeping copies of users crypto  tucked away in caches or temporary  system files. The risk to us regular  guys, just wishing that no  stranger should be able poke around in our  private lives, is that some  dude dumps a key-logger onto our machine.  Well, it takes two to tango.  Some sort of action by the victim is needed  to get a key-logger into  the target. The Ubuntu software accreditation  and installation schema  gives good assurance here and provided we, the  users, are quite  cautious about installing novelty softwares from  outside the Repos then  we are much, much safer than yer average Windows /  iPhone / iPad user.  Reputable linux apps have a rather good record for  cleaniness. After  years of development in full sight of a critical user  base most linux  apps are pretty well-engineered and trustworthy.

'Course,  in today's world the real risk to the individuals privacy is  the whole  social media thing. I cannot understand why so many of us  delight in  spreading our orivate lives over facebook, twitter, flickr  and the like.  Its a free gift for the Nosey Ones.

Hope this helps

rjbl

---

### Post by regency on 2012-12-30
> **rjbl said:**
> The  Truecrypt system is highly reputable and, as an openly published  source  code it has been heavily scrutinized and is widely believed to  be  robust, well-engineered and fit for purpose. l

@ rjbl

You might wish to read the following article:

"Still putting your crypto-protected PC in hibernate? $300 app can hack it - Attacking strong crypto may soon become a script kiddie exercise."

The link is: [http://arstechnica.com/security/2012/12/cheap-app-cracks-pgp/](http://arstechnica.com/security/2012/12/cheap-app-cracks-pgp/)

---

### Post by Welly Wu on 2012-12-31
This is the reason why I don't use TrueCrypt any longer. If you stick with the crypto tools in Ubuntu, then you will be better off because it's integrated. Elcomsoft and Passware target Microsoft Windows, Apple OS X, and TrueCrypt. Nothing that I am aware of targets ecryptfs, dm-crypt, LUKS, or GnuPG.

---

### Post by bazmonkey on 2013-01-06
Having just put this scheme into effect on my laptop, and having given it considerable thought, I thought I'd share.

I have lots of different kinds of data on my computer.  Most of it is media, both commercial and personal (pictures), and some of it is personal data and work.  I also utilize dropbox to keep some of it (basically everything minus movies and music) over several devices, including ones that can't handle any encryption scheme I utilize on my computer (phone).

I also am using pam-usb as a *required* module for two-factor auth.  Because a laptop isn't a physically locked-down machine, it's only really going to stop snoopers at work while I'm afk.  Plus, pamusb-agent can unlock the screen without a password (even though it's required to log in or sudo, etc.), so popping out the key gives me a simple way to train myself to lock the screen.

The reason I mention it is because it forces me to keep a USB key on me religiously.  It has to stay separate from the laptop when possible but on me any time I'd have the laptop.  So it's on my keys.

I use encfs and cryptkeeper.  Cryptkeeper likes to do things it's own way with encfs, so I let it set up an encrypted volume whose encrypted data sits in the dropbox directory, and decrypted mount point is outside.  Then I moved the .encfs6.xml key (the passphrase-protected encryption key for the volume) to the USB key.  Finally, I wrote a wrapper script that sets an environment variable specifying where the .encfs6.xml file is, and then calls cryptkeeper (cryptkeeper can't do this itself).  This script gets started up each session.

Advantages (for me):

* encfs keeps encrypted files, not a big encrypted virtual volume.  The advantage to the bad guy knowing how many files I have hidden and their relative sizes is negligible in my case.  He can know that.  What makes this an advantage to me is that dropbox can keep my files in the cloud along with the rest of my day-to-day stuff.  I can deploy this on my desktop at home and get the same encrypted data.  Rather than having to sync up one huge file containing all my encrypted data, it can sync it file-by-file.

* The master password to my encrypted data isn't tied to my login password like it is with Ubuntu's built-in home encryption scheme.  My user login password (on a laptop) doesn't need to be nearly as strong as my data's master password.  If bad guy has my laptop, my login password doesn't stop him from doing anything.  It's more to stop snoopers at work.

* Unlike home-directory encryption of any kind, my encrypted data need only be accessible when I need it.  I can hibernate and suspend like normal.

* Rather than storing passwords for convenience within web browsers and other applications, I can keep a password manager whose data is in the encrypted section.

* THE ENCRYPTION KEY IS SEPERATE FROM THE ENCRYPTED DATA!  It's effectively two-factor now: it requires a passphrase I know to decrypt a key I have.  It increases the chances that an attacker or theif will have the data and the key.  Without the key my encrypted data is essentially secure against any reasonable attack.  In most encryption schemes a typical theft scenario would leave only your master password in the way because the key resides with/near the data.  This way, there's a good chance the much, much larger encryption key will be stopping the attacker.

Hope that's useful to someone.  I think it strikes a balance between convenience and security that other encryption schemes don't.  Once set up it's controlled graphically, and it allows you to keep the same encrypted data synced on multiple machines seamlessly without exposing the data to the cloud or ever keeping the key and data together when you're not there.  It takes advantage of the fact that you already go through the trouble of transporting something physically to every machine you use: yourself.  Might as well carry the key!

---

### Post by rjbl on 2013-01-06
> **regency said:**
> @ rjbl

You might wish to read the following article:

"Still putting your crypto-protected PC in hibernate? $300 app can hack it - Attacking strong crypto may soon become a script kiddie exercise."

The link is: [http://arstechnica.com/security/2012/12/cheap-app-cracks-pgp/](http://arstechnica.com/security/2012/12/cheap-app-cracks-pgp/)

The risk of reading crypto keys out of cache has been long known, over the years many researchers have produced tools to do just this, in all operating systems. It's a risk to be managed, just like any other,

Personally I rarely, maybe never, hibernate a PC with encrypted volumes open. (Actually, I can't think over any occasion, in decades, that I've ever allowed any machine to go into hibernation - basically 'You're using the box or it's switched off') Like I said (OP) almost all of the risk in in using any encryption system (excl. Microsoft EFS) is in the Secure Computing Environment (SCE).

Hope this clarifies my earlier post a bit.

rjbl

---

### Post by tubbygweilo on 2013-01-06
> basically 'You're using the box or it's switched off'

Sound advice indeed.

Bruce Schneier has been exploring the world of the Evil Maid for quite some [time]("http://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html") so it comes down to a layered defense with consideration given to attack vectors and then defending against those you can.

---

### Post by rjbl on 2013-01-08
> **tubbygweilo said:**
> Sound advice indeed.

Bruce Schneier has been exploring the world of the Evil Maid for quite some [time]("http://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html") so it comes down to a layered defense with consideration given to attack vectors and then defending against those you can.

D'accord. Of course, you must retain physical control of your kit at all times, else all bets are off.

Personally I don't use whole disk encryption that much - bad experiences in the early days of the concept.

If you feel a need to protect the sanctity of you private life then measure the risks - almost invariably they will be close at hand, rather than sinister government agencies; the Feds etc. 

Actually EcryptFS gives pretty good protection against casual attack by the average crim who's nicked your laptop and is curious about its contents.

Whole disk encryption will stop him dead but he'll just take the disk out and sell the box on, probably for peanuts.

Hope this helps
rjbl

---

### Post by mhogomchungu on 2013-05-18
> **sahabcse said:**
> Try LUKS – The Linux Unified Key Setup – and dm-crypt.

I think GUI not available for this

cryptsetup now has a desktop environment/file manager independent GUI front end called "zuluCrypt".

The project is hosted at: [http://code.google.com/p/zulucrypt/](http://code.google.com/p/zulucrypt/)

disclaimer:
I am the founder and current maintainer of the project and just joined this forum to raise awareness of my project.

---

### Post by cariboo on 2013-05-18
> **mhogomchungu said:**
> cryptsetup now has a desktop environment/file manager independent GUI front end called "zuluCrypt".

The project is hosted at: [http://code.google.com/p/zulucrypt/](http://code.google.com/p/zulucrypt/)

disclaimer:
I am the founder and current maintainer of the project and just joined this forum to raise awareness of my project.

Welcome, hopefully your project is embraced by the community.

---

### Post by mhogomchungu on 2013-05-19
> **cariboo907 said:**
> Welcome, hopefully your project is embraced by the community.

thank you,i hope so too.

background of why i started the project.I wanted to manage cryptsetup plain type encrypted volumes that reside in files using a GUI solution and there was no solution to use.I then started the project to solve my problem and decided to expand it and release it to the community in a a hope that it will be useful to others too.

---

