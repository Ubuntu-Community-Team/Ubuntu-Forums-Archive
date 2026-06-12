---
title: "lock up hard drive to make it unusable without password?"
date: 2009-04-26
forum: Security
---

### Post by weeman7007 on 2009-04-26
Hi I was wondering how I could make it so the hard drive in my laptop would be completely useless without a password, i.e. can't format over it or do anything without the password, is this possible? I have already set up a password in my BIOS to not allow it to boot from the hard drive without the password, but then someone could put it in another machine and simply access my data that way, just using a liveCD. I pretty much want to make it totally useless without the passwords. Thanks in advance

---

### Post by iponeverything on 2009-04-26
You can encrypt the whole drive, but with all the drives that I know of there is no way to prevent someone from reformating it. I heard a while back about some of the hard drive vendors working a hardware DRM enforcement mechanism into drives, but I think that if the word got out that a vendor was doing that --- it might hurt their sales.

---

### Post by weeman7007 on 2009-04-26
ahh ok thanks, but the encryption would stop anyone from being able to boot from or mount the drive to view data, yes?

---

### Post by whoop on 2009-04-26
yes

---

### Post by abn91c on 2009-04-26
**No** the FBI and local law enforcement have tools for that, it is how they get child pornographers, the mob, drug dealers and other assorted criminals

---

### Post by OldGreySteve on 2009-04-26
> **weeman7007 said:**
> Hi I was wondering how I could make it so the hard drive in my laptop would be completely useless without a password, i.e. can't format over it or do anything without the password, is this possible? I have already set up a password in my BIOS to not allow it to boot from the hard drive without the password, but then someone could put it in another machine and simply access my data that way, just using a liveCD. I pretty much want to make it totally useless without the passwords. Thanks in advance

I have had a good experience using TrueCrypt.  I keep all my confidential data on a separate partition which is incrypted (I don't care if someone steals my open source applications).  If you multiboot, the same partition can be accessed from Windows.

---

### Post by whoop on 2009-04-26
> **abn91c said:**
> **No** the FBI and local law enforcement have tools for that, it is how they get child pornographers, the mob, drug dealers and other assorted criminals

Well, it's just like security for a vault or your house. There's really nothing stopping an expert to get in, eventually. But with full disk encryption you will stop somebody from booting or mounting the drive to view the data, and decrypting the drive will take a lot of time. Law enforcement actually puts a lot of effort into and has a lot of laws to make the suspect reveal the decryption password. I can go even further and say that these law enforcement methods are so mainly used, that there are encryption schemes that create deny-ability, so if you are tortured you can give a password that will give them some useless data (that might look convincing) while the real data remains encrypted and undetectable (seems like random encrypted garbage)
I certainly hope and think that weeman7007 doesn't want to let his data fall in the hands of any third party but that he does not necessarily want to hide something from the fbi.

I for one can think of a lot of files I don't want my friends to see, but I would be proud and laughing if the FBI forces me to show them :p I also use TrueCrypt for that.

---

### Post by weeman7007 on 2009-04-26
I would prefer for no one (including law enforcement) to see my files but thats just cos I'm slightly paranoid about things... I don't really have anything to hide I just don't think they have the right to search my stuff if I've done nothing wrong, in which case I would demonstrate that as it would be a lot more pleasant than spending a prolonged period of interrogation. I had seen earlier about this deniability thing, sounds kind of cool, how do I do it? I just like maximum security things... Plus the FBI would first have to get me out of the UK I believe...

But I'm innocent.. Well as innocent as anyone really is..

EDIT: could this also be used alongside needing a separate memory stick to boot up? that also sounds rather cool...

---

### Post by whoop on 2009-04-26
> **weeman7007 said:**
> I had seen earlier about this deniability thing, sounds kind of cool, how do I do it? I just like maximum security things... 

[http://www.truecrypt.org/docs/?s=plausible-deniability](http://www.truecrypt.org/docs/?s=plausible-deniability)

---

### Post by weeman7007 on 2009-04-26
cheers for your help :)

---

### Post by ddrichardson on 2009-04-26
> **abn91c said:**
> **No** the FBI and local law enforcement have tools for that, it is how they get child pornographers, the mob, drug dealers and other assorted criminals
You're confusing modern encryption methods with DES where NSA access was a design consideration or the ill fated [clipper chip]("http://en.wikipedia.org/wiki/Clipper_chip"), I'm sure they have the technology to do so but not as easily as you suggest.

Most encryption can be broken with enough time but I'm assuming we're talking about preventing thieves reading sensitive data and full disk encryption is enough of an inconvenience that the drive would be formatted and reinstalled.

Security is a fairly selfish process, if your car is more secure than the one next to it, they'll steal the other one.

---

### Post by whoop on 2009-04-26
> **ddrichardson said:**
> Security is a fairly selfish process, if your car is more secure than the one next to it, they'll steal the other one.

That's a really good point, btw. 
I use that principle on a daily basis. As an example, I have three moderate locks on my bicycle and I like to place my bike next to another one with a single good lock on it :P Am I evil ?

---

### Post by NESFreak on 2009-04-26
> **abn91c said:**
> **No** the FBI and local law enforcement have tools for that, it is how they get child pornographers, the mob, drug dealers and other assorted criminals

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]
[http://xkcd.com/538/](http://xkcd.com/538/)

---

### Post by Steven3k on 2009-04-27
> **weeman7007 said:**
> 
[CUT]

EDIT: could this also be used alongside needing a separate memory stick to boot up? that also sounds rather cool...

See: [http://ubuntuforums.org/showthread.php?t=1137554](http://ubuntuforums.org/showthread.php?t=1137554)

---

### Post by Dave_Connor on 2009-04-27
Can't most disk encryption be broken by the key being stored in the ram and access with a cold boot attack ?

---

### Post by ddrichardson on 2009-04-28
> **Dave_Connor said:**
> Can't most disk encryption be broken by the key being stored in the ram and access with a cold boot attack ?
That's one of the reasons for combining it with a USB boot key and there's a relatively short time window to do it in.

---

### Post by xoros on 2009-04-28
> **weeman7007 said:**
> Hi I was wondering how I could make it so the hard drive in my laptop would be completely useless without a password, i.e. can't format over it 

Well to stop formatting you could flash the firmware with some version that you make, that way most standard hardware interfaces won't know what to do. Or, if it isn't flash-able, physically replace the chips. Granted, you would also have to make the interface to it. 

Good luck with that.

---

### Post by Wydarr on 2009-05-01
As far as I've read (I might be wrong) the only way to lock-up a HDD (i.e. make it unusable unless it is in your laptop, and you input your password) is via a TPM - Trusted Platform Module. 
If I understand correctly, it will effectively lock your HDD to the rig you are using it on via some sort of Hardware - based full disk encryption gizmo stuff. The only problem that I see, is in case your mobo gets toasted it would be... challenging to have access again to the data on the HDD.

For reference:
[http://en.wikipedia.org/wiki/Trusted_Platform_Module](http://en.wikipedia.org/wiki/Trusted_Platform_Module)
[http://en.wikipedia.org/wiki/Secure_cryptoprocessor](http://en.wikipedia.org/wiki/Secure_cryptoprocessor)

I know that I have read somewhere about this in more detail, but my memory tends to be a bit blurry at times. I'll post more details, as soon as I find them.

---

### Post by ddrichardson on 2009-05-01
TPM is also susceptable to removing the memory.

What we use is a combination of encrypted drives and removeable caddies - the drives are removed from the desktops that use them at the end of the day and stored elsewhere.

---

