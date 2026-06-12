---
title: "Laptop seizure &amp; whole disk encryption?"
date: 2008-08-06
forum: Security
---

### Post by vlovich on 2008-08-06
I'm going to be travelling to the US in about a month and taking my laptop with me.  I'd like a solution where I can pop in a live-CD, encrypt the whole drive with a one-time pad, and then decrypt once I land.

I'm particularly concerned with the stories of laptops being seized indefinitely.  I have banking information and whatnot stored there - rather than go scouring my computer trying to clean data off of my Linux & Windows partitions, it'd be nice to have a solution similar to above.

Does anyone know of a live-CD that does this?  Additionally, a non-ideal, but acceptable solution, would be taking out the laptop drive, hooking it up to a USB port on my desktop, and doing the whole-disk encryption that way.

Acceptable solutions also include ones that only encrypt the contents of each partition separately (i.e. the partition tables remain).

I'm not too familiar with True-crypt, so I can't evaluate whether or not it meets my needs.  Particularly, I'm concerned with whether or not I can remove the True-crypt encryption after I'm done with it (i.e. the drive is no longer encrypted).  Also, it seems to imply it only supports Windows for system encryption - does this mean I have to run the system encryption from Windows, or that it'll only encrypt the Windows partition (i.e. my Linux partition will remain unaffected).

I know this is a long post and kind of ambiguous.  I appreciate any and all suggestions

---

### Post by Nepherte on 2008-08-06
I'm not sure of the necessity to encrypt your disk when they can force you to unlock it.

---

### Post by Dr Small on 2008-08-06
> **Nepherte said:**
> I'm not sure of the necessity to encrypt your disk when they can force you to unlock it.
Remove GRUB, and when they boot it, it will say that there is no OS found. Then when you get across the border, reinstall GRUB from a LiveCD.

---

### Post by Valsodar on 2008-08-06
Hey vlovich, I am also concerned with that laptop search and seizure and I think its very invasive and stupid. If you want to to carry sensitive information I would recommend encrypting it on a usb drive and overwriting it on your harddrive (make sure you have backup copies thou). Also note that encrypting the entire harddrive will be VERY suspicious and they might seize your laptop or might ask you to "Provide Key" in order to let you in. Alternatively you can encrypt the Ubuntu Partitions and reinstall  (so that Windows boots only -> sounds very clever!)

I just hope the border patrol guys in not very clever to figure this out!

Oh yeah, also bring a Live CD to reinstall grub!

Alt. you can remove ubuntu entries from grub (copy menu items and only list windows)

---

### Post by pedja_portugalac on 2008-08-06
I really don't understand you guys! Do you believe, just for second, you can hide something from those who have invented computers? I can understand if you encrypt your laptop hdd just in case it get stolen but you should know right now, if there is any "serious activities" suspicion over you you'll spit out and we are happy about that!

---

### Post by Dr Small on 2008-08-06
> **pedja_portugalac said:**
> I really don't understand you guys! Do you believe, just for second, you can hide something from those who have invented computers? I can understand if you encrypt your laptop hdd just in case it get stolen but you should know right now, if there is any "serious activities" suspicion over you you'll spit out and we are happy about that!
Um, I am pretty sure the lazy border security didn't invent computers. They probably are only "Windows Power Users" (whatever that means), and would have no idea what to do if the system didn't boot.

---

### Post by snowpine on 2008-08-06
"Electronic device, resembles a computer, but doesn't boot--confiscate device, call for backup, detain suspect."

I would imagine that's their protocol. I like the idea of booting to Windows and removing your Linux partition from grub. :)

---

### Post by hyper_ch on 2008-08-06
I'd just put in 10 gb partition another winxp on it.... install a few apps... put a few documents and pictures on their.... replace the background with a family pcitures... and just make sure windows boot manager is installed... I don't think they would know there's more on it (ok, the other windows install would be critical as it will auto-mount it... so unmount that one.

---

### Post by vlovich on 2008-08-06
Let me just clarify.

First, they can't compel me to reveal anything in the original requirements.  Note that I asked for a tool that could encrypt my entire drive (i.e. every single bit including partition tables and whatnot).  The idea is I take the key & transport it on a USB key or just SSH back into my desktop at some later date.

Nepherte:  They can't force me to unlock anything - there's no password prompt.  Just a no-os message since the disk doesn't contain any useful data.

Dr Small: Worthless solution, since if they seize it, they still have access to my banking information.

Valsodar: My sensitive information is generally in the form of Firefox saved passwords and whatnot.  However, the whole point of this encryption is so that I don't have to figure out where my sensitive data is, and then have to backup/restore this.  I want a one-shot solution.

pedja_portugalac: First, the border security guards did not event computers.  Second, yes.  The whole point of encryption is that no matter how smart your opponent is, your data is still safe.  I think you need a crash course in encryption (read-up on RSA as a starter)

snowpine: That's fine.  I can at least argue that I haven't had the time to install an OS.  Their seizure of the laptop doesn't gain them anything and I'm secure in the knowledge they don't have my banking info.  Additionally, I could just put a live-cd in there - they won't know the difference between it booting off the CD & off a hard drive.

hyper_ch:  Again.  I'm not trying to fool the border guards.  I don't care if they find the laptop suspicious.  I want to make sure that all the data I have on the laptop is secure.

Please, don't suggest to me to install a hidden Windows partition.  I already have 3 primary partitions & a logical partition, and I don't believe that Windows can install into a logical partition anyways.

Please read my requirements: I'm looking for a solution where I can pop in a CD and have my entire drive encrypted/decrypted withsome (a)symmetric key encryption.

---

### Post by Dr Small on 2008-08-06
To encrypt your hard drive, everything has to be erased, so that already foils your plans.

---

### Post by pedja_portugalac on 2008-08-06
> **hyper_ch said:**
> I'd just put in 10 gb partition another winxp on it.... install a few apps... put a few documents and pictures on their.... replace the background with a family pcitures... and just make sure windows boot manager is installed... I don't think they would know there's more on it (ok, the other windows install would be critical as it will auto-mount it... so unmount that one.
You are smart guy but believe me if they suspect you of criminal activities they'll find time and people to discover your deepest secrets. Maybe you'll wait all that time in a cell of 2 x 2 meters or on a famous "tropical island"! I don't understand what someone would want to hide so badly if it's not in connection with terrorist activities or child pornography? That's why I presume some of those guys are involved in such stories!!!

---

### Post by vlovich on 2008-08-06
> **pedja_portugalac said:**
> You are smart guy but believe me if they suspect you of criminal activities they'll find time and people to discover your deepest secrets. Maybe you'll wait all that time in a cell of 2 x 2 meters or on a famous "tropical island"! I don't understand what someone would want to hide so badly if it's not in connection with terrorist activities or child pornography? That's why I presume some of those guys are involved in such stories!!!

Just 1 google <a href="http://www.google.ca/search?q=laptop+stolen+identity&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a">search</a> answers your questions.  Essentially, I would have no problem with them inspecting my laptop in front of me and as long as it never leaves me.  However, them being seized indefinitely is a huge problem.

Do you really trust someone who is getting paid about minimum wage and having to deal with all sorts of people going through customs (i.e. constant stress) with all the personal information on your laptop (i.e. banking?).  This is wide-scale identity fraud waiting to happen.  Don't believe me about the intelligence of customs agents (at least in parts of the US) - just look at [this]("http://http://www.michaelnygard.com/blog/2008/03/steve_jobs_made_me_miss_my_fli.html") and [this]("http://www.tsa.gov/blog/2008/03/update-bob-screens-apple-macbook-air.html").

I've already been a victim of some minor identity fraud (I suspect a camera was placed over one the ATMs I used).  It was no fun replacing my card and filing reports to get my money back.  Thankfully, it wasn't anywhere near the complete ID theft that could occur if someone stole my laptop.

As for the "if you've got nothing to hide argument", you need some education, not fear-mongering.

[http://papers.ssrn.com/sol3/papers.cfm?abstract_id=998565](http://papers.ssrn.com/sol3/papers.cfm?abstract_id=998565)
[http://www.guardian.co.uk/commentisfree/2007/nov/21/comment.politics2](http://www.guardian.co.uk/commentisfree/2007/nov/21/comment.politics2)

My counter-argument is this: if the customs agents, police, etc, have no reason to suspect me, why are they searching me?  Are they trying to plant evidence, steal my possessions, perform ID theft?  The argument works both ways, and neither is correct.

Another thing is that in Canada (at least for the time being), it's perfectly legal to download music (it's been upheld by the Supreme Court).  In the States, I could run in to all sorts of legal issues if some border security guard decided I had "illegal" content on it.  

I think this is the third time I'm saying this.  I'm just not too keen on having some stranger having potential access to particularly sensitive financial information.

And how did terrorism and child pornography come up?  You should look up how to form a coherent, rational argument, rather than one based upon fear and emotional response.  If you believe that terrorists and child pornographers are trying to smuggle things in laptops on airplanes, I think you need a reality check.  It's far easier to just put the content on a USB key and encrypt that.  Or send it over e-mail using PGP.  Or even use OTR to transfer the file in an IM program.  Or use TOR.

I can maybe buy that child pornographers are using technology to commit their crimes; even then - laptop seizures at the airport are not effective at all since it's targeting the wrong communication channel (hint, it's not Usenet either).  [Terrorists]("http://www.brookings.edu/articles/2007/0506terrorism_byman.aspx") on the other hand, prefer employing [low-tech]("http://www.washingtonpost.com/wp-dyn/content/article/2008/01/04/AR2008010403573.html?hpid=topnews") solutions because it is less likely to interception and there's no complicated set up needed to ensure privacy and security.

---

### Post by vlovich on 2008-08-06
> **Dr Small said:**
> To encrypt your hard drive, everything has to be erased, so that already foils your plans.

I'm pretty sure that's not a given.  For instance, Truecrypt can even encrypt a running system in a transactional manner.  So I don't think it's out of the realm of possibility for a solution to exist that does the whole disk in an offline manner.

Just to show that it is possible, here's a theoretical solution.

Assuming you have 10 MB + some extra for bookkeeping free.
Read in the first 10 MB of the partition.
Encrypt it
Write out the 10 MB in the free space
Update your book-keeping to indicate which 10 MB has that encrypted information and which 10 MB is free now.
Rinse & repeat until drive is completely encrypted.
Bonus points for defragmenting the partition before hand so that free space is at the end for better performance and less bookkeeping needed.

To do the whole drive, hook the drive into a USB enclosure with write-caching off.  Do the above steps again, except you don't need any bookkeeping (i.e. bookkeeping is stored on some other storage medium), and you overwrite the old data instead of placing it somewhere at the end.

Additionally, for extra reliability, when updating the bookkeeping, you can write out the (encrypted or unencrypted - doesn't matter) 10 MB into the same place as the bookkeeping.  That way, if you have a failure, you can recover because you'll have written the previous 10 MB, so you'll know if you successfully managed to complete your last operation.

So there you go - it is possible to do an in-place encryption.  My question is if anyone has done so.  I guess the answer is no.

---

### Post by vlovich on 2008-08-06
> **pedja_portugalac said:**
> You are smart guy but believe me if they suspect you of criminal activities they'll find time and people to discover your deepest secrets. Maybe you'll wait all that time in a cell of 2 x 2 meters or on a famous "tropical island"! I don't understand what someone would want to hide so badly if it's not in connection with terrorist activities or child pornography? That's why I presume some of those guys are involved in such stories!!!

Also, just wanted to add (from Wikipedia, but you can look this up from the primary sources as well if you want):

> Search and seizure is a legal procedure used in many common law countries whereby police or other authorities and their agents, who suspect that a crime has been committed, do a search of a person's property and confiscate any relevant evidence to the crime. Certain countries, such as the United States and Canada, have provisions in their constitutions that provide the public with the right against "unreasonable" search and seizure. This right is generally based on the premise that everyone is entitled to a reasonable right to privacy.

So what the TSA is doing is potentially unconstitutional (breaking the law).

Additionally, you may want to lookup [criticisms]("http://en.wikipedia.org/wiki/Transportation_Security_Administration#Criticisms") and [scandals]("http://en.wikipedia.org/wiki/Transportation_Security_Administration#Scandals") surrounding the TSA.  Essentially, they're an incompetent organization at best, focusing on measures that simply inconvenience normal passengers, rather than actual criminals.

First, let the TSA convince me that they are competent (i.e. they don't lose & destroy my property randomly) and have fixed all the real threats (they can properly screen [bombs and guns]("http://community.seattletimes.nwsource.com/archive/?date=20061028&slug=screeners28")).  Even then, they still don't have a right to invade my privacy.

---

### Post by Dr Small on 2008-08-07
> **vlovich said:**
> So what the TSA is doing is potentially unconstitutional (breaking the law).


Yes, I am pretty sure we all realize this. The Constitution is about to be abolished.

---

### Post by snowpine on 2008-08-07
Patriot Act.

---

### Post by vlovich on 2008-08-07
From what I understand of the US constitution, it trumps any law made by Congress.  The only way Congress can override the Constitution is by amending it, which requires 2/3rds of both houses.  AFAIK, the Patriot Act was never proposed as a constitutional amendment.

However, this is getting off topic.  I'm still looking for the encryption solution.

---

### Post by PadreSol on 2008-08-07
Put all your data, encrypted, on the net somewhere.
Remove all your data from laptop.
Leave laptop as-is.
When you get where you're going download it and go.


For fun, create a directory with 1024 dirs with each one containing 1024 dirs and each one containing 1024 files text files 
Then when they do the search it will spin in there.
NB: Could cause delays.

Create a fifo and write a program to write to it when it's read from.
Have the writer write a stream of poetry to the fifo.
NB: They may flag the poetry as subversive.

---

### Post by PadreSol on 2008-08-07
> **pedja_portugalac said:**
> You are smart guy but believe me if they suspect you of criminal activities they'll find time and people to discover your deepest secrets. Maybe you'll wait all that time in a cell of 2 x 2 meters or on a famous "tropical island"! I don't understand what someone would want to hide so badly if it's not in connection with terrorist activities or child pornography? That's why I presume some of those guys are involved in such stories!!!

If you have nothing to hide then please post your home address and all your personal information including accounts, etc. so we can all see it.

If not then what are you trying to hide?

---

### Post by pedja_portugalac on 2008-08-07
> **PadreSol said:**
> If you have nothing to hide then please post your home address and all your personal information including accounts, etc. so we can all see it.

If not then what are you trying to hide?

Mr pedja_portugalac
Central Intelligence Agency
Office of Public Affairs
Washington, D.C. 20505
USA

Phone: (703) 482-0623

---

### Post by vlovich on 2008-08-07
> **PadreSol said:**
> Put all your data, encrypted, on the net somewhere.
Remove all your data from laptop.
Leave laptop as-is.
When you get where you're going download it and go.


For fun, create a directory with 1024 dirs with each one containing 1024 dirs and each one containing 1024 files text files 
Then when they do the search it will spin in there.
NB: Could cause delays.

Create a fifo and write a program to write to it when it's read from.
Have the writer write a stream of poetry to the fifo.
NB: They may flag the poetry as subversive.

That is not a practical solution.  The hard-drive is big, so imaging it and downloading the image over the net is pointless.  If I'm just doing it for the information itself, that's pointless - I can just encrypt it onto my iPod or my camera's SD card.  However, this ignores my requirement of not having to scour my drive for what constitutes sensitive data - the whole point is minimal effort + maximal reward.  It seems like there's no solution out there for the moment.

Oh, and the FIFO is a cool idea.

---

### Post by insane_alien on 2008-08-10
set up an ssh server at home to use pgp encryption, put key on usb stick, fresh install laptop, when across border ssh into your server and access all your data. before recrossing copy all data to server, delete traces on laptop, corss border, job done.

---

### Post by scorp123 on 2008-08-10
> **vlovich said:**
> I'm going to be travelling to the US in about a month and taking my laptop with me. We use thin-client laptops.

* NO local harddisk at all
* NO data they could "inspect" (= copy & steal)
* even if they keep the laptop ... without knowing how to get to the server which is here in Europe it's just a pile of dead plastic ...

And even with the laptop gone I could still easily get to all my data and even my desktop: we use "Sun Secure Global Desktop", all I need is a web browser with a Java VM. That's it.

Example of such a laptop: "Comet 15"

Details:
[http://www.tadpole.com/products/notebooks/comet15.asp](http://www.tadpole.com/products/notebooks/comet15.asp)
[http://www.rugged-systems.com/p/MobileSunSolaris/0078.htm](http://www.rugged-systems.com/p/MobileSunSolaris/0078.htm)

Sun Secure Global Desktop:
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

Sun Ray Thin-Client Server:
[http://www.sun.com/software/sunray/index.jsp](http://www.sun.com/software/sunray/index.jsp)


Yes... that software isn't free. But it's worth the money. And if you are a customer of Sun anyway (e.g. you buy servers from them) it should be easy to get a juicy rebate on the software.

I really travel a lot ... and those SUN solutions really are worth their money.

---

### Post by PadreSol on 2008-08-10
...just so you don't feel as if you're the only one....

[http://www.eff.org/deeplinks/2008/08/public-pressure-mounts-against-invasive-border-sea](http://www.eff.org/deeplinks/2008/08/public-pressure-mounts-against-invasive-border-sea)

Of course it still leaves us all wondering what happened to our elected officials, but it's still good that the public's outraged.

---

### Post by misterfixit on 2008-08-25
> **snowpine said:**
> "Electronic device, resembles a computer, but doesn't boot--confiscate device, call for backup, detain suspect."

I would imagine that's their protocol. I like the idea of booting to Windows and removing your Linux partition from grub. :)

--

You left out a couple of steps:

confiscate device, call for backup, detain suspect, perform anal probe cavity search without lube; transfer to Rendition Facility, Waterboard until key is coughed up, send home, say it was all an unfortunate error.
:lolflag:

---

### Post by panhandle on 2008-08-25
I guess another option, though less satisfactory, is to have (2) hard drives.

One is a clean, new disk with a clean, new install and some basic software.

The other is your working HD, which you can ship to and fro a destination.

Thus, there is never a problem with physical access to a hard drive. 

However, the a couple other options here (thin client) seem like significantly less hassle. 

As long as there is nothing illegal on your working HD, then shipping it should present no problem.

---

### Post by sighk on 2008-08-25
What you could do, create small partition with no boot loaders, make sure it isn't in fstab or mtab. Your system will fully boot, your other drive wouldn't show up without alot of digging, ie sudo vi /etc/fstab and adding your device and mount point.

So

Computer boots
if they quickly look at it, everything looks correct.
end of story

---

### Post by sternkanz on 2008-08-27
Hello. I read this topic due to the original question, and I'm looking for a slightly different solution. I have already made the effort of wiping all personal data from my laptop, and I would like to zero all the free space. I know its not "secure" in any way, but I would like to do it all the same.

If you know how I can do this, please let me know. I am using Hardy.

Thanks,

Stern

---

### Post by panhandle on 2008-08-27
@stern:

use shred.

---

### Post by adamogardner on 2008-10-18
> **pedja_portugalac said:**
> Mr pedja_portugalac
Central Intelligence Agency
Office of Public Affairs
Washington, D.C. 20505
USA

Phone: (703) 482-0623

Dude, one of the best rebuttals I ever did see.  

So what I'm getting from this thread is that there is no easy way to encrypt my laptop.  There is no program that simply encrypts all your stuff??!!  Why?  I don't want the world here, I just want my computer to be cryptic on demand.  I don't get the whole cryptology thing; don't you unencrypt it with a password?  whats all this talk about seperate disks and thumbdrives?

---

### Post by hyper_ch on 2008-10-19
there is an easy way to encrypt: Full disk encryption upon installation.

---

### Post by u-slayer on 2008-10-19
It's simple really: you have two goals in defeating border guards:

1. Don't attract suspicion.
2. Have all of your data encrypted.

Partition your hard drive as such:
<10 GB of Windows NTFS><8 GB for Linux><The Rest for your encrypted /home>

For the first goal, I would overwrite the MBR (back it up first) and install windows on the first 10GB of your laptop. So when your friendly TSA official boots the laptop they will see nothing but a friendly windows desktop with family pictures and boring stuff. Windows will not see the other partitions because they are in linux AND you overwrote the partition table so windows can't find them. As far as windows is concerned you only have a 10GB hard drive. Quite pathetic, but not unheard of. 

When you land in the states, revert the MBR and you can boot back into linux like nothing happened.

To satisfy goal two, use something like Truecrypt to encrypt the /home directory of your Linux install or go all the way and just encrypt the whole damn Filesystem if you want to bother with it.

---

### Post by bcn17 on 2008-12-29
You could make a .tar file of your entire filesystem with something like partimage live cd

 Encrypt it with truecrypt. 

Keep the key on a usb drive and the encrypted/compressed filesystem on dvd's or an external harddrive.

 delete your original hard drive. 

Travel to USA.

un-encrypt

 uncompress the entire filesystem onto the harddisk with partimage live cd. 

Good luck-

---

### Post by nitrogensixteen on 2008-12-30
Why not bypass the issue altogether and ship the hard disk to yourself? Backup your critical data prior to departure.
If you are really concerned about private data, encrypt your firefox data folder in your home, or encrypt your whole home. Log in as a different user if they ask you to boot. If you have more sensitive data than your banking information, you are taking an unnecessary risk by delivering it to customs at all. Encrypt it and upload it to rapidshare(or whatever you like). If you arouse their suspicion and they feel like doing it, they will pressure you to unlock any encrypted information they find or just keep your computer. Don't risk your computer by standing up for your "right" to privacy.

---

### Post by Kinstonian on 2008-12-30
I'd recommend you put your hard drive in your luggage, and keep a LiveCD ready in case they tell you to turn on your laptop.  However, I'm not 100% sure if data on your hard drive would be safe from their X-ray machines or not.  I remember reading that someone put a hard drive through an X-ray machine at the airport many times (I believe 50 or more) and it didn't change a single bit.  If you don't want to risk it, I suggest you mail it.

Edit: nitrogensixteen beat me to it :)

---

### Post by Tubes6al4v on 2008-12-31
In reality the only way to get this to a satisfactory level of security is (as has been suggested) to encrypt from the bottom up. I would back up my entire linux partition to a tar or bzip file, and do the same for the windows side (though I have not done this), and copy the backups to an external drive. Now that you have the backups, you can set about building a more secure system.

- Whipe the drives
- Overwrite with random data
- Create 4 or more partitions (1 windows, 1 hidden windows, 1 Linux, 1 Shared and/or /home)
- Install windows to the first partition. 
- Use Truecrypt to create a hidden OS on the second partition.
- Restore windows backup to hidden OS
- Place family photos, bs documents, etc, on encrypted, but not hidden OS.
- Install encrypted linux to third partition, possibly with /home encrypted on the 4th (or just use the 4th as shared encrypted space via Truecrypt).


This would be even more sound if we could create a hidden linux OS too. I know you said you didn't want to do the hidden OS thing, but it is really the only way to have deniability and to be able to give them a key that satisfies them and does not put you at risk. Plus this will not be an issue further trips.

---

### Post by RansomStark on 2009-01-02
> **panhandle said:**
> @stern:

use shred.

Not a good idea.... Taken from the MAN page for shred.

CAUTION: Note that shred relies on a very important assumption: that the file system overwrites data in place. This is the traditional way todo things, but many modern file system designs do not satisfy this assumption. The following are examples of file systems on which shred is not effective, or is not guaranteed to be effective in all file sys-tem modes:

* log-structured or journaled file systems, such as those supplied with AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)
* file systems that write redundant data and carry on even if some writes fail, such as RAID-based file systems
* file systems that make snapshots, suchasNetworkAppliance's NFS server
* file systems that cache in temporary locations, such as NFS version 3 clients
* compressed file systems

A better option is the DBAN ([http://www.dban.org/](http://www.dban.org/)) or the secure-delete packaeg ([http://www.thefreecountry.com/security/securedelete.shtml](http://www.thefreecountry.com/security/securedelete.shtml))

---

