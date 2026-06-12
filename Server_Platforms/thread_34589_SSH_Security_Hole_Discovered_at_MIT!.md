---
title: "SSH Security Hole Discovered at MIT!"
date: 2005-05-15
forum: Server Platforms
---

### Post by s0c0 on 2005-05-15
New research into security weaknesses in a popular secure remote access technology highlights the vulnerability of large-scale computing environments such as grids and supercomputing clusters to a potentially crippling form of attack.

The SSH (Secure Shell) technology is used by security administrators and other technical users to connect to remote machines via a secure, encrypted tunnel. 

The system is used widely in university and research networks, and security researchers at the Massachusetts Institute of Technology last week published a paper showing how a simple worm could grab SSH user credentials from one machine and move rapidly among any number of connected systems, causing what's known as a "cascade failure."

Read More at [http://www.eweek.com/article2/0,1759,1815795,00.asp](http://www.eweek.com/article2/0,1759,1815795,00.asp)

-Hopefully they get a patch out for this!

---

### Post by JonahRowley on 2005-05-15
> -Hopefully they get a patch out for this!

You generally cannot simply patch design flaws.  Sadly, this can't really be defended against, if it really is a "vuln" anyway.

> The researchers, from MIT's Computer Science and Artificial Intelligence Lab and Lincoln Laboratory, found that malicious hackers could use an SSH file called "known_hosts" to gather lists of remote systems visited by other users via SSH.

This file is *vital* to SSH, it holds the public keys of machines you've connected to in the past.  Encrypting this is a possibility, but makes ssh a pain to use since you'll have to enter a symmetric cipher password every time you use it.  A system similar to ssh-agent could be used to protect your **known_hosts** file for people who use ssh often, and would work smoothly.

Though I agree that this is a weakness, the chances of a pre-auth vulnerability in OpenSSH, which is highly-audited, is not likely.  Also, worms do not work well in varied envrironments.  Remember the Apache SSL worm?  It didn't work, too many people were running different versions and configurations of Apache, the same is true for SSH.

Other than automated attacks, this poses a bigger threat for people who use the same password for all attacks.  If your password is compromised, this could be used as an index of all your other ssh accounts.  If you use public key auth, then this isn't a problem though, since your password will not be compromised (it's never transmitted) and your private key is symmetrically encrypted.  Then again, if they get that symmetric key, they have an index of all your accounts to play with..

Overall, I don't see this as a large problem.  If you don't use the same password, and don't let your private key fall into the wrong hands, known_hosts doesn't give an attacker much more information than he could get by other means.  It's something to keep in mind though.

What about **~/.bash_history**?  It can be used just as easily to find hosts you ssh to.  **known_hosts** doesn't hold info you can't get by other means anyway, it just allows an attacker to get them faster.

---

### Post by LordHunter317 on 2005-05-15
This isn't a security vulnerability in anyway.

Unless someone finds a way to derive the entire hostkey from the key fingerprint (which is extermely unlikely), the known_hosts file tells you exactly two things: Jack and Shit. And if someone found a way to derive the key from the fingerprint, they wouldn't need the known_hosts file to pretend to be a host anyway. They could just get the fingerprint and derive the key directly from the host.

Here's a better idea: If you read it in eweek, it's probably either old security news or just plain wrong. This is a clear case of the latter.

---

### Post by word_virus on 2005-05-16
[QUOTE=s0c0]-Hopefully they get a patch out for this![/QUOTE]

The solution is to use hashes of host names in known_hosts.  This is available in OpenSSH 4.0 by setting /etc/ssh/ssh_config HashKnownHosts line to "yes".  
Ubuntu currently uses OpenSSH 3.9.  Below are instructions for patching manually for the curious/security conscious:

wget [ftp://ftp.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-3.9p1.tar.gz](ftp://ftp.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-3.9p1.tar.gz)
wget [http://nms.lcs.mit.edu/projects/ssh/openssh-3.9p1-hashed-hosts-NOCOLLECT-20050214.patch.gz](http://nms.lcs.mit.edu/projects/ssh/openssh-3.9p1-hashed-hosts-NOCOLLECT-20050214.patch.gz)
tar zxf openssh-3.9p1.tar.gz
gunzip openssh-3.9p1-hashed-hosts-NOCOLLECT-20050214.patch.gz
patch -p0 < openssh-3.9p1-hashed-hosts-NOCOLLECT-20050214.patch
cd openssh-3.9p1
./configure --prefix=/usr
make 
sudo make install
sudo perl convert_known_hosts.pl

This will replace your current OpenSSH binaries, patch them, and convert all the host names currently stored in your known_hosts files to the hash format.

When is Ubuntu getting OpenSSH 4.0, by the way?

---

### Post by JonahRowley on 2005-05-16
[QUOTE=word_virus]When is Ubuntu getting OpenSSH 4.0, by the way?[/QUOTE]

I have no idea, but at the earliest, Breezy, due out in October.

---

### Post by LordHunter317 on 2005-05-16
First, I should apologise.  Whenever I said "fingerprint" in my previous post, it should really be "public key".  My apologies for speaking incorrectly.

[QUOTE=word_virus]The solution is to use hashes of host names in known_hosts. This is available in OpenSSH 4.0 by setting /etc/ssh/ssh_config HashKnownHosts line to "yes". [/quote]The security value of this is debatable at best.  I'd argue that if someone can compromise your known_hosts file anyway, they're also likely to be able to figure out the hashed hostname extremely quickly (or have really good guesses), via other means.

There is no flaw here guys.  known_hosts only contains publically available information anyway.  I have no clue why this hashing was added as it really makes no sense whatsoever.

---

### Post by JonahRowley on 2005-05-16
[QUOTE=LordHunter317]There is no flaw here guys.  known_hosts only contains publically available information anyway.  I have no clue why this hashing was added as it really makes no sense whatsoever.[/QUOTE]

There is no flaw directly, no.  But how many people do you know that use the same password for all accounts?  Or even worse, use the same password on their private key as they do on other accounts?  One compromise could quickly become many.  Having a directory of other hosts this user has an account on just sitting there is probably not a good idea.

And yes, the information can be gathered by other means.  But sniffing, scanning, etc takes time and isn't perfect.  I think the danger they're referring to is automated attacks, which probably wouldn't be smart enough to glean the information from other sources, but could easily parse the known_hosts file and cause the "cascade failure" as they called it.  There's no reason for it to be in the clear, hashing it is a good thing.

On a side note, **~/.ssh/config** presents the same vulnerability, but is not so easily solved.  I have many accounts all over the Internet, on different hosts, different ports and different usernames and I use the ssh config file as an address book of sorts.  An automated program could just as easily use this file, if many other people use it as I do.

Edit:  This is a lot more than just SSH as well.  Imagine I'm a sysadmin and I manage 50 Apache servers.  I use virtually the same configuration on each, and I manage those configs over SSH.  If my system is compromised by an Apache vuln, following known_hosts, 50 more could be in a very short period of time.  That would be a "Bad Thing."

BTW, eweek was probably not the proper link for this, get it from the horse's mouth:

[http://nms.csail.mit.edu/projects/ssh/](http://nms.csail.mit.edu/projects/ssh/)

---

### Post by LordHunter317 on 2005-05-16
[QUOTE=JonahRowley]There is no flaw directly, no. But how many people do you know that use the same password for all accounts? Or even worse, use the same password on their private key as they do on other accounts? One compromise could quickly become many.[/quote]Yes, but these weakness are social ones, and exist **regardless** of any flaws in SSH.  

Meaning they're part of your security baseline in reality.  Any attacker who compromises one account via password who's not doing automated assaults is going to try the password everywhere he can, as the hit rate for it is likely to be high.


> Having a directory of other hosts this user has an account on just sitting there is probably not a good idea.Yeah, but it doesn't store account names, or other necessarily useful information, just that they shelled there.  Sure, it gives an attacker less work, but I don't think it's really that much less work these days.  

People grossly underestimate the amount of time it takes to do an automated attack.  By the time I've fed all the hostnames in the file into my botnet, it could have easily just scanned and tried the password on every SSH using host on the subnet.  

> And yes, the information can be gathered by other means. But sniffing, scanning, etc takes time and isn't perfect. I think the danger they're referring to is automated attacks,This is just the thing.   All the information contained in a known_hosts file will be gleamed by an automated network.  As soon as the automated attack connects to a host listed in the known_hosts file, they have the exact same information.

And the reality of it is that it's easier to just brute-force your ways through these things then try to write a "smart" automated attacker. 

> but could easily parse the known_hosts file and cause the "cascade failure" as they called it. Or they could just attack every host in your netblock and get just as high of a hitrate.

It's not like there's a lack of targets running SSH or anything.  And automated attacks don't care what hosts they compromise, just that they manage to get in and compromise a host.

> There's no reason for it to be in the clear, hashing it is a good thing.Why?  I don't see what it gains you.  It's like taking the house number on your mailbox and putting a piece of tape over it.  I can just as easily find it out in a million other different ways.

>  If my system is compromised by an Apache vuln, following known_hosts, 50 more could be in a very short period of time. And how many of those 50 hosts are in teh same netblocks?  Like 25 in one block and 25 in your redundant center, right?  

An automated attack, worm, or whatever, is just going to hit them all at once.  Screw known_hosts.  You can infest faster just by attacking everyone.

You'll note all the massive Windows worms (the non e-mail ones, e.g., code red) didn't need to look anything up to spread.  They just attacked everyone and infested the machines they could.

That is the model you have to be prepared against.   

The other is an actual human running the attack.  In which case, the known_Hosts information **might** be useful.  But there's still so many other ways to get the information, you'd have to take many more drastic steps to even call yourself safe.  Steps that generally aren't worth the cost.

Think the attack scenarios through for a second and you realize it's rather silly to obscure plainly public information.

The long and the short of it is that address harvesting is pointless for IP-based automated attacks.  I can scan an entire netblock in the time it takes me to parse the file containing the information I want.

Even if I only hit one host in that entire netblock, it's still a less waste of time than parsing the files.  

And it's not like bandwidth or machines to launch the attacks from are valuable resources.  If they were, then this might have some merit.  But that's just not the way things work on the Internet today.

---

### Post by ChM on 2005-06-13
Hello,

our security officer has blocked internet access to my Ubuntu PC because it doesn't run openSSH 4.1.  :-# I have installed Hoary and would prefer to stick with it. Shouldn't there be a security update for this ? Do we have to wait for Breezy ? 

How is this package managed ? Who could I contact to know more about the planes to release the latest openSSH version ? Can I help on this ?

---

### Post by Jussi Kukkonen on 2005-06-13
[QUOTE=ChM]
our security officer has blocked internet access to my Ubuntu PC because it doesn't run openSSH 4.1.  :-# I have installed Hoary and would prefer to stick with it. Shouldn't there be a security update for this ? Do we have to wait for Breezy ? 

How is this package managed ? Who could I contact to know more about the planes to release the latest openSSH version ? Can I help on this ?[/QUOTE]

Hello ChM,

first, I'd like to point out that it's a little rude to hijack a thread that's discussing something else...

If you can negotiate with your 'security officer', you can show him the [list of bugs](http://bugzilla.mindrot.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=Portable+OpenSSH&version=3.9p1&version=4.0p1&long_desc_type=allwordssubstr&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&keywords_type=allwords&keywords=&resolution=FIXED&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&votes=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=)  in 3.9 and 4.0 that were fixed. If you ask me, there's nothing there that warrants blocking you... You could also show him the Debian package lists (even Sarge, the fresh release, has 3.8). 

If he's stubborn, you'll have to [build 4.1](ftp://ftp.ca.openbsd.org/pub/OpenBSD/OpenSSH/portable/INSTALL) . Nothing to worry about, it's not rocket science.

---

### Post by nocturn on 2005-06-13
[QUOTE=ChM]Hello,

our security officer has blocked internet access to my Ubuntu PC because it doesn't run openSSH 4.1.  :-# I have installed Hoary and would prefer to stick with it. Shouldn't there be a security update for this ? Do we have to wait for Breezy ? 

How is this package managed ? Who could I contact to know more about the planes to release the latest openSSH version ? Can I help on this ?[/QUOTE]

Ouch, that is though (the blocking).  

You could download the OpenSSH 4 sources, deinstall the debs and compile your own as an interim solution.  
Or ask Jdong for a backport.

---

### Post by ChM on 2005-06-14
Thank you nocturn, jdong saved my life  :smile: 

Sorry Jussi ! I naively thought 4.1 was a response to the security hole. I should have checked it previously.

---

