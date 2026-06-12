---
title: "What is the most secure form of HDD encryption these days?"
date: 2015-07-24
forum: Security
---

### Post by PsychedelicWonders on 2015-07-24
So I've used Truecrypt in the past and clearly it's been compromised and not really an option any more.  I've actaully already had a Truecrypt HDD hacked into (I think that may have been my fault by not have a secure enough password, but either way TC is not safe or supported any more according to the developers.)

Bitlocker surely has back doors and is windows based anyways right?

So I would like an encryption program that is able to be cross platform from Ubuntu to Win7

So what other encryption program is left out there for HDD security?  This is going to be a media HDD, but I still want it completely encrypted. 

I would move to an SSD for my media since it offers hardware encryption via AES password set through bios (when bios able to do this, so far only 1 desktop mobo manufacturer allows this) and supposedly Samsung SSDs have no backdoors since the encryption key & the master key can be regenerated/reset, but the 2TB is $1000 while a WD Black is $125

But from my research hardware encryption is superior these days.  Sucks it's only available on SSDs.  SSDs are also pretty neat how fast they can be securely erased too.

Adding encryption to the drive should still be the first step before transferring media to it don't you think?

---

### Post by TheFu on 2015-07-24
> **PsychedelicWonders said:**
> So I've used Truecrypt in the past and clearly it's been compromised and not really an option any more.  I've actaully already had a Truecrypt HDD hacked into (I think that may have been my fault by not have a secure enough password, but either way TC is not safe or supported any more according to the developers.)

Bitlocker surely has back doors and is windows based anyways right?

So I would like an encryption program that is able to be cross platform from Ubuntu to Win7

So what other encryption program is left out there for HDD security?  This is going to be a media HDD, but I still want it completely encrypted. 

I would move to an SSD for my media since it offers hardware encryption via AES password set through bios (when bios able to do this, so far only 1 desktop mobo manufacturer allows this) and supposedly Samsung SSDs have no backdoors since the encryption key & the master key can be regenerated/reset, but the 2TB is $1000 while a WD Black is $125

But from my research hardware encryption is superior these days.  Sucks it's only available on SSDs.  SSDs are also pretty neat how fast they can be securely erased too.

Adding encryption to the drive should still be the first step before transferring media to it don't you think?

I don't think that anyone knows if/whether truecrypt was cracked or not. We only know that the maintainers decided not to continue. There are many reasons possible for this - UEFI/SecureBoot just for starters.

I don't think we know whether BitLocker is compromised either. Microsoft, for all their flaws, **does** take customer privacy seriously.  I say this as a nearly full-time Linux admin for the last decade and Unix admin prior to that.

I don't know of any secure and cross-platform disk encryption. I would go with a hardware-based solution running drives that have encryption firmware. These aren't cheap and they need appropriate BIOS support.  [http://addonics.com/category/encryption.php](http://addonics.com/category/encryption.php) will provide some ideas.

For Linux on cheap hardware, use whole disk encryption and boot from a USB flash drive that you never let out of your possession. Do not boot from the /boot partition on the machine. This will avoid the "evil maid" attack.  There are other methods on the way where both the boot and the running OS cryptographically sign each other to ensure no tampering has happened.

Whatever you do - consider 2-factor authentication.  A flash drive really isn't "something you have" because it can be cloned and used by anyone.  The "something you have" must be unique in the world.

There are many attacks against these things that are not intuitively obvious. I take extra effort around security when traveling, by leaving anything sensitive in a secured location only available through a strong vpn that doesn't depend on DNS.  Sometimes that is an inconvenience when the IPs are blocked by nation-states, but better to be inconvenienced than to allow sensitive corporate data to be leaked by a portable device being stolen.  If it is portable, it must be encrypted - PERIOD.

OTOH, I'm not any expert on this stuff.  Nothing is uncrackable.

---

### Post by jason_gibson2 on 2015-07-24
Is this for work or home use. If home use then I think a safe estimate is that you are taking it to seriously especially if it's a media drive... It just makes me wonder what kind of legal issues you have with your "media", at which point I would be afraid to help or offer suggestions.

---

### Post by TheFu on 2015-07-25
> **jason_gibson2 said:**
> Is this for work or home use. If home use then I think a safe estimate is that you are taking it to seriously especially if it's a media drive... It just makes me wonder what kind of legal issues you have with your "media", at which point I would be afraid to help or offer suggestions.

Jason,

Not every government approves of all content that might exist.  For example, there are sacred Tibetan religious scripts that the Chinese government doesn't want anyone to know about. They don't allow visitation except to a tiny list of Tibetan monks who desperately want to get that knowledge released.  Usually the monks involved have to snap photos of the pages and hide the SD or microSD media to get out of the location. Those texts are taken elsewhere in the world and translated into many different languages.  If caught, the monks will "disappear."

Imagine drafts of the US Constitution **before** the USA had earned independence?  Those documents would have been treasonous. There are oppressive governments around the world. People inside those countries AND outside often work together for change.

My point is that we cannot judge content, just the right to privacy.  Some governments may not agree with the right to privacy, so we use encryption. Either we have the right to privacy or we do not. Encryption is the way that normal people can demand their privacy.  In the USA, I think the 4th amendment assures this. The Supreme Court has said in rulings the fundamental purpose of the (4th) amendment as guaranteeing: 
> "the privacy, dignity and security of persons against certain arbitrary and invasive acts by officers of the Government, without regard to whether the government actor is investigating crime or performing another function."

Whenever discussing computer security, we have to think about OPSEC - operational security. OPSEC is hard, really, really, really, hard. The CIA has been caught doing things in "friendly" nations due to poor opsec. [http://www.youtube.com/watch?v=bM0PmwOlifE](http://www.youtube.com/watch?v=bM0PmwOlifE) while not directly related to disk encryption, is related to poor OPSEC.

Using a bad passphrase is poor OPSEC. Long, random, unguessable is needed. That's why smartcards with GPG keys are a good idea.

---

### Post by jason_gibson2 on 2015-07-25
I didnt think of that I admit. I guess I ultimately said what I wanted to wrong. I am of the belief that if you aren't doing anything illegal then who cares what they do. I don't condone what most goverments do either for the record. That being said I guess my biggest fear with people who want encryption but don't know where to start is that they will turn into the person who posts "encypted my root partition and lost the passkey, HELP ME PLS!" and they lose everything. In this particular case with a media drive it seems double stupid because it takes time to collect media either legally or illegally. Would be one of the last things I can imagine one would risk to encryption. But again to be fair even in the US who invented the internet I'm paying an arm and a leg for a crap connection so maybe I'm not seeing it that way either. Either way I apologize. It isn't up to me to debate legalities of peoples media.

---

### Post by PsychedelicWonders on 2015-07-25
> **TheFu said:**
> I don't think that anyone knows if/whether truecrypt was cracked or not. We only know that the maintainers decided not to continue. There are many reasons possible for this - UEFI/SecureBoot just for starters.

I don't know the reasons like everyone else, but I know that when you open it up to use it says: WARNING: Using Truecrypt is not secure

So I'd like to find other alternatives.  Sad, TC seems to have been in a league of it's own.

> I don't think we know whether BitLocker is compromised either. Microsoft, for all their flaws, **does** take customer privacy seriously.  I say this as a nearly full-time Linux admin for the last decade and Unix admin prior to that.

I do not have the same kind of experience professionally that you do, so I would take your word for that bit of information.  But MS is like the original PRISM lol and in the end if there is an alternative beyond bitlocker, I'd prefer to use it.  Especially since I'm trying to migrate away from Win7 finally and back to Ubuntu.

> I don't know of any secure and cross-platform disk encryption. I would go with a hardware-based solution running drives that have encryption firmware. These aren't cheap and they need appropriate BIOS support.  [http://addonics.com/category/encryption.php](http://addonics.com/category/encryption.php) will provide some ideas.

I'm not familiar with these at all, but they look really interesting.  Is it something you add to an HDD, or the HDD also comes with it?  I literally just bought a new WD Black drive yesterday for my media, was hoping to go with an SSD to utilize Samsungs hardware encryption, but it's just still too expensive right now for me, so had to go with an HDD for now and figure out the most secure form of encryption.  Is this addonics a system that I could add to the WD Black drive just bought?  I ended up with a normal 3.5" internal HDD.

> For Linux on cheap hardware, use whole disk encryption and boot from a USB flash drive that you never let out of your possession. Do not boot from the /boot partition on the machine. This will avoid the "evil maid" attack.  There are other methods on the way where both the boot and the running OS cryptographically sign each other to ensure no tampering has happened.

Not familiar with the evil maid attack, but this sounds like a great solution, just sucks have to physically carry/remember something with you every time you want to use the computer, but I guess that is the state of privacy these days.[/quote]

> Whatever you do - consider 2-factor authentication.  A flash drive really isn't "something you have" because it can be cloned and used by anyone.  The "something you have" must be unique in the world.

Is this the USB master boot key thing you were just referring to?  That's what's nice about the SSDs, they have an encrypted digital key that all you have to remember is  passphrase.

> There are many attacks against these things that are not intuitively obvious. I take extra effort around security when traveling, by leaving anything sensitive in a secured location only available through a strong vpn that doesn't depend on DNS.  Sometimes that is an inconvenience when the IPs are blocked by nation-states, but better to be inconvenienced than to allow sensitive corporate data to be leaked by a portable device being stolen.  If it is portable, it must be encrypted - PERIOD.

OTOH, I'm not any expert on this stuff.  Nothing is uncrackable.

All good advice.  And just for the record, I'm not trying to hide anything illegal, I am on the other hand a private person and since I don't do anything illegal, I shouldn't have to worry about wanting or needing my privacy, nor should I have to explain myself.  But unfortunately I have to both.

---

### Post by TheFu on 2015-07-25
I wouldn't trust any drives with encryption included. 
[http://www.wired.com/2015/02/nsa-firmware-hacking/](http://www.wired.com/2015/02/nsa-firmware-hacking/)

There are lots of reasons to keep media private.  No need to explain to me. For others ... there are perfectly legal adult oriented businesses which may create content for other adults when the kids are off to school.  That content should be encrypted - to protect the children.  See how I turned that around? ;) 
Plus if I'm not doing anything illegal, it isn't any of *their* business what is stored on my disks.  OTOH, most people probably commit 3 felony crimes daily. [http://www.wsj.com/articles/SB10001424052748704471504574438900830760842](http://www.wsj.com/articles/SB10001424052748704471504574438900830760842) because of vague laws.

Just be aware that if you are constantly seen using 2FA to access the computer, someone will figure it out and know exactly what to steal and they will learn whatever it is you enter.

I still don't think the old TC running on a BIOS boot PC was cracked.  I believe the issue was EFI and secureboot - there wasn't any way to ensure TC wasn't hijacked, so rather than produce a version that was "almost" secure if 50 caveats were followed, they decided to stop.
Back in 2010, we know the FBI failed to crack a truecrypt disk. 
[http://www.theregister.co.uk/2010/06/28/brazil_banker_crypto_lock_out/](http://www.theregister.co.uk/2010/06/28/brazil_banker_crypto_lock_out/)
Subsequent reviews of the code didn't find any blatant issues either. 
[https://www.schneier.com/blog/archives/2015/04/truecrypt_secur.html](https://www.schneier.com/blog/archives/2015/04/truecrypt_secur.html)

So ... on my old, BIOS booting, Windows box, I still use truecrypt.  I've never used it on Unix/Linux.

You asked about the addonics stuff - read the webpages, look up anything you don't understand and ask their support people to explain.  I have some non-encryption stuff from Addonics that has been working perfectly for almost a decade.

---

### Post by obake2 on 2015-07-26
I found that one of the best forums where people can talk about security SERIOUSLY is in Trisquel GNU/Linux:

[http://trisquel.info/en/forum](http://trisquel.info/en/forum)

As TheFu said, do not trust hard drives with encryption built in, they always have backdoor built in.

See: [Spying software hidden deep within hard drives made by Western Digital, Seagate, Toshiba and other top manufacturers]("http://trisquel.info/en/forum/spying-software-hidden-deep-within-hard-drives-made-western-digital-seagate-toshiba-and-other-")

And I don't know how much you care about privacy, but if you someday want to wipe your data securely, it is better if you don't use SSD since YOU **NEVER** **KNOW** if it has truly been wiped out. The Operating System simply gets fooled in to thinking that it did wipe out the files, and there is no way to fix it since it is a firmware feature, the way SSD works.

---

### Post by bashiergui on 2015-07-27
> Plus if I'm not doing anything illegal, it isn't any of their business what is stored on my disks. OTOH, most people probably commit 3 felony crimes daily.  [http://www.wsj.com/articles/SB100014...38900830760842](http://www.wsj.com/articles/SB100014...38900830760842) because of vague laws.That is a great article.

---

### Post by TheFu on 2015-07-30
> **TheFu said:**
> I don't think we know whether BitLocker is compromised either. Microsoft, for all their flaws, **does** take customer privacy seriously.  I say this as a nearly full-time Linux admin for the last decade and Unix admin prior to that..

Seems the old MSFT who cared about privacy is gone. [https://edri.org/microsofts-new-small-print-how-your-personal-data-abused/](https://edri.org/microsofts-new-small-print-how-your-personal-data-abused/) has a breakdown of the new privacy policy effective 1 Aug 2015.

The biggies:
* browsing history and favorites are backed up to their cloud
* "We will access, disclose and preserve personal data, including your content (such as the content of your emails, other private communications or files in private folders), when we have a good faith belief that doing so is necessary"
* Forgetaboutit if you used their personal assistant - calendar, contacts, emails and the content of those is shared (which sorta makes sense).
* Data collection on networks you connect with and applications run and any devices that are connected to the Win10 system.
* BitLocker Key recovery is automatically pushed to their cloud servers. So much for whole disk encryption. Good for stopping little brother, but not for free speech.
* Unique ad-network ID for every userid.

All I can say is "nice."

---

### Post by QDR06VV9 on 2015-07-31
This sums it up nicely.
> Privacy? I don't have anything to hide.
Glenn Greenwald: Why privacy matters Over the last 16 months, as I've debated this issue around the world, every single time somebody has said to me, "I don't really worry about invasions of privacy because I don't have anything to hide." I always say the same thing to them. I get out a pen, I write down my email address. I say, "Here's my email address. What I want you to do when you get home is email me the passwords to all of your email accounts, not just the nice, respectable work one in your name, but all of them, because I want to be able to just troll through what it is you're doing online, read what I want to read and publish whatever I find interesting. After all, if you're not a bad person, if you're doing nothing wrong, you should have nothing to hide." Not a single person has taken me up on that offer.

Glenn Greenwald in Why privacy matters - TED Talk

---

### Post by PsychedelicWonders on 2015-08-01
Hmm.  So besides the addonics hardware encrypted HDD system, there isn't anything software wise that is secure any more?  Bitlocker is out.  So is Truecrypt it seems at this point.  These were cross platform encryptions, but is there any encryption methods that are just unique to Ubuntu?  I really want to get away from Windows as much as possible and I really want my personal data encrypted, private, protected & safe.

I've received my new HDD, so I would really like to transfer my data to it ASAP, but I know normally you have to put the encryption layer first before adding media.

---

### Post by TheFu on 2015-08-01
To my knowledge, Ubuntu doesn't do anything proprietary with their encryption so any similarly featured Linux distro would be able to access those volumes with the appropriate knowledge applied to make it so. dm-crypt is dm-crypt, regardless of the linux used.

---

### Post by PsychedelicWonders on 2015-08-01
I wasn't aware of familiar with dm-crypt, I've since done some research since your post and want to go in this direction.  Any good, updated walk-thrus for setting up dm-crypt/LUKS?

---

### Post by zemeckisv1990 on 2015-08-03
this could help you out

[https://www.digitalocean.com/community/tutorials/how-to-use-dm-crypt-to-create-an-encrypted-volume-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-dm-crypt-to-create-an-encrypted-volume-on-an-ubuntu-vps)

---

