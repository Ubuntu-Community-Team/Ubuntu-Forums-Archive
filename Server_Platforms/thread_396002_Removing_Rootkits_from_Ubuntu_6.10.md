---
title: "Removing Rootkits from Ubuntu 6.10"
date: 2007-03-28
forum: Server Platforms
---

### Post by sbowne on 2007-03-28
Hello:

I am teaching an "Ethical Hacking and Network Defense" class and I discovered a security issue with Ubuntu 6.10.  I don't know if this is something new, or something other people already know about.

I am using Ubuntu 6.10 in VMware on a host operating system of Windows XP Professional.

I downloaded and installed the "Fuckit" rootkit (sorry for the undignified name) from egocrew.de/download-category-4.html.  This rootkit works on Ubuntu 6.10 even with current patches installed, allowing a user to log in with elevated privileges, and to hide connections to remote ports.  It has other features as well, but those did not seem to work correctly when I tried to use them.  The rootkit also wrecks Ubuntu so that it won't restart, not even in recovery mode.  It runs OK until you shut it down, however.

The "rkhunter" rootkit hunter finds the rootkit, but does not remove it, or tell you how to remove it.

I wanted to repair the rootkitted Ubuntu machine.  I am primarily a Windows user, so my first instinct was to look for a Windows XP-style "System Restore", but I could not find such a feature in Ubuntu.  So I wrote a script which calculated the MD5 hash of all the files on a healthy Ubuntu machine (well, almost all of them) and stored the results in a big file.  I then ran the same script on the infected machine, and used the "diff" command to compare the results.  That gave me a short list of changed files (about 30) which I could easily filter down to the ten files that mattered.  Copying those ten files from the clean machine to the rootkitted machine fixed it.

I would appreciate comments on these issues:

1. This technique seems to me to be a powerful way to fix rootkitted machines, and machines with other problems as well.  Is this something new?  Is there already some Ubuntu feature or add-on that solves this problem better?

2. Shouldn't the security patches protect Ubuntu from this rootkit?  Should I report this as a bug?

3. If there is no System Restore for Ubuntu, is it worth developing one?  Perhaps the hashes for system files could be calculated and saved on some regular basis, such as every day, and a handy tool created to list what files were changed between any two days.  That would make it easier to diagnose and fix problems caused by malware or just human error.  Are there already log files that do that?

All the details of what I did are in this Microsoft Word document: [http://samsclass.info/123/proj/RootkittingUbuntu.doc](http://samsclass.info/123/proj/RootkittingUbuntu.doc)

I would be grateful for any opinions or guidance, especially from more experienced Linux users.

Thanks,

Sam Bowne

---

### Post by kidders on 2007-03-28
Hi there,

This post is intriguing!

> **sbowne said:**
> 1. This technique seems to me to be a powerful way to fix rootkitted machines, and machines with other problems as well.  Is this something new?  Is there already some Ubuntu feature or add-on that solves this problem better?There are a few intrusion detection applications around that use file hashes to *detect* unexplained changes, but I'm not aware of one that offers to undo the damage for you.

> **sbowne said:**
> 2. Shouldn't the security patches protect Ubuntu from this rootkit?  Should I report this as a bug?I'm not completely sure that they should. To protect yourself reliably from rootkits, a virus scanner is called for imo. If you have the time, it's at least worth reporting what you've done as a bug ... the worst they could do is close it!

> **sbowne said:**
> 3. If there is no System Restore for Ubuntu, is it worth developing one?  Perhaps the hashes for system files could be calculated and saved on some regular basis, such as every day, and a handy tool created to list what files were changed between any two days.  That would make it easier to diagnose and fix problems caused by malware or just human error.  Are there already log files that do that?Something like that would be extremely helpful to many people, if you ask me. Perhaps another poster will have seen something like this before, but I haven't. Apple is about to bring out something similar that they claim will be able to arbitrarily reverse changes to files.

---

### Post by Frosty Cold Drink on 2007-03-28
> **sbowne said:**
> 1. This technique seems to me to be a powerful way to fix rootkitted machines, and machines with other problems as well.  Is this something new?  Is there already some Ubuntu feature or add-on that solves this problem better?
Tripwire was one of the first. What you can do is wipe out bad files and reinstall the providing package. Of course this doesn't help if your apt is compromised.

> 2. Shouldn't the security patches protect Ubuntu from this rootkit?  Should I report this as a bug?
No. Maybe (didn't read your details). There are too many threats out there, and new ones can be created on a whim. Its impractical to try and protect against them in anything but a generic way. Even anti virus is only mildly useful in many situations. File permissions and mount options, combined with user accounts and groups should get you half way to "secure". Proper configuratiaon of everything else should get you most of the rest of the way.

> 3. If there is no System Restore for Ubuntu, is it worth developing one?  Perhaps the hashes for system files could be calculated and saved on some regular basis, such as every day, and a handy tool created to list what files were changed between any two days.  That would make it easier to diagnose and fix problems caused by malware or just human error.  Are there already log files that do that?
Knowing is better than nothing. That said, using some sort of version control like SVN, CVS, or arch would make it fairly easy to keep multiple versions of everything, and pick your point to restore. The problem with stuff like this is that if the machine is compromised, you have to assume the on-system diagnosis and repair tools are as well. The only way to get 100% safe, accurate shots is to take the system off line, run your tools, build your images, and then bootstrap it again. 99% of the time its cheaper to just back up your key files and reinstall if you have to.

---

### Post by pppetter on 2007-03-29
Dude, for a rootkit to work it needs to be run with full privileges on the computer, so the person installing must have forgotten to check the source of the file. But this person might as well edit some weird configuration file, thus messing up the system entirely - or just delete everything...and so on.

My point is that it's impossible to build a system that protects itself from a superuser(admin).

---

### Post by Mr. C. on 2007-03-29
The premise that "the person installing must have forgotten to check the source of the file" is faulty.  There are, and have always been, plenty of exploits in *all* computer operating systems.  

Sometimes through no fault of even the most astute, aware, sensible, and learned admin, a system is compromised.  It takes just one sufficient exploit found in a single daemon to gain control of a system.

An intelligent rootkit can hide from the likes of tripwire, and all other detection software, as once compromised, the system may return any results desired to hide itself.

That said, the best one can do is try to be as vigilant as possible, staying as close to the head of the malware pack as cost and circumstances allow.

Once compromised, attempts to delouse a system are essentially futile and counterproductive.

MrC

---

### Post by _tms on 2007-03-29
> **kidders said:**
> 
I'm not completely sure that they should. To protect yourself reliably from rootkits, a virus scanner is called for imo. If you have the time, it's at least worth reporting what you've done as a bug ... the worst they could do is close it!

There seems to be some misunderstanding in this thread. The OS can't protect itself from root, but if a "regular" user of a ubuntu system can log in, run this rootkit and gain root privileges, there is a security flaw within the system and must be fixed A.S.A.P. 

I suggest you submit this as a bug/security issue,
If you have not figured out how exactly this program is gaining root access, provide exact step-by-step instructions of what needs to be done to run it.

---

### Post by GoBieN on 2007-03-29
If you are deeply concerned about security holes and exploits and in your applications that would allow rootkits or other malware to gain entrance, you should install Debian stable, and not Ubuntu. Ubuntu is more aimed at user friendliness and functionality, and is based on the unstable branch of Debian i believe. Whilst Debian Stable is thoroughly tested and usually is a half year behind on releasing new packages or upgrades. 
That said, even in stable a new exploit can be found, but its less likely. 

On my Ubuntu server, I run chkrootkit periodically in the hope that if a rootkit gets in, it will be found.

None the less, the only way in on my system is trough apache/php or webmin, since everything is  shut by a NAT router with firewall. Imo one should always have a decent firewall protect vital equipment. SSH is forwarded to, but not on the standard port, so brute force attack scripts have never found me. Even apache is on a different port (not deliberately, 80 is blocked by ISP) but that doesn't help much since the site is listed in search engines.

---

### Post by Mr. C. on 2007-03-29
> **_tms said:**
> There seems to be some misunderstanding in this thread. The OS can't protect itself from root, but if a "regular" user of a ubuntu system can log in, run this rootkit and gain root privileges, there is a security flaw within the system and must be fixed A.S.A.P. 


Where did the OP say he ran the kit as a non-privileged user?  Where did it say that the OP ran as a non-privileged user, who had not recent ran sudo in the past couple of minutes?

MrC

---

### Post by ice60 on 2007-03-29
i made these notes for configuring aide on my suse box. if you keep the database it creates on a separate media it should help find the presents of some rootkits i suppose. 

in a root shell run this -
# aide --init

that will create the database.

then move that new database and make it the default database -
cd /var/lib/aide/
 mv aide.db.new aide.db

the rules governing what and how things are checked are kept here -
/etc/aide.conf

to re-run and check for any changes run this from a root shell -
# aide --check -V2

---

### Post by Mr. C. on 2007-03-29
> **ice60 said:**
>  it creates on a separate media it should help find the presents of some rootkits i suppose. 

in a root shell run this -
# aide --init

Now what makes you think if I was the kernel and hacked OS, and recognized you running the "aide" program, that I could not return whatever results I wanted?  The kernel loads the program, the kernel starts the program running, the kernel can replace modified code instead of your code.

If the system is running, and has been hacked, one cannot trust the results of standard anti-intrusion kits.

MrC

---

### Post by ice60 on 2007-03-29
> **Mr. C. said:**
> Now what makes you think if I was the kernel and hacked OS, and recognized you running the "aide" program, that I could not return whatever results I wanted?
?? 

what makes you think i think that :confused: i don't think that at all!

---

### Post by ice60 on 2007-03-29
i just re-read my post and it's 100% correct. i said this -

> if you keep the database it creates on a separate media it should help find the presents of some rootkits i suppose. i'll leave it there, i'm too lazy for this :lolflag:

---

### Post by Mr. C. on 2007-03-29
If you give advice such as :

"if you keep the database it creates on a separate media it should help find the presents of some rootkits i suppose"

but don't quantify "should" and "I suppose", the advice is not very useful to the OP.  My question was not meant for you in particular, it was meant to bring home the point that results can't be trusted on compromised systems.

MrC

---

### Post by ice60 on 2007-03-29
> **Mr. C. said:**
> If you give advice such as :

"if you keep the database it creates on a separate media it should help find the presents of some rootkits i suppose"

but don't quantify "should" and "I suppose", the advice is not very useful to the OP.  My question was not meant for you in particular, it was meant to bring home the point that results can't be trusted on compromised systems.

MrC

grow up. 

OP if you are struggling with the words "should" and "i" and "suppose" please let either me, or MR C know and we'll fill you in.

---

### Post by ice60 on 2007-03-29
ok, then run aide from another computer, that way a rootkit that's aide aware has no way of hiding its presents

---

### Post by Frosty Cold Drink on 2007-03-29
> **ice60 said:**
> ok, then run aide from another computer, that way a rootkit that's aide aware has no way of hiding its presents

But what if it was one of those kits that hides its files from other processes :shock:

---

### Post by ice60 on 2007-03-29
> **Frosty Cold Drink said:**
> But what if it was one of those kits that hides its files from other processes :shock:

i'm sorry i really don't know what you're talking about. i admit i haven't followed security as closely as i did when i just ran windows, but are there now rootkits that can hide themselves from computer b when it's on computer a?

---

### Post by Frosty Cold Drink on 2007-03-29
> **ice60 said:**
> i'm sorry i really don't know what you're talking about. i admit i haven't followed security as closely as i did when i just ran windows, but are there now rootkits that can hide themselves from computer b when it's on computer a?

Not explicitly. If computer b is looking around on computer a, it has to ask computer a something. If computer a is rootkited, its responses can't be trusted.

The only 100% reliable way to detect a rootkit, assuming you have a siguature for it, is to bring the rootkited system offline, and look for it without relying on any part of the rootkited system.

In not-so-generic terms, shut the sucker down, put its hard drive(s) in another machine, mount them ro+noexec and start looking.

Edit: Infamous Cold Drink metaphor: If you were brainwashed, you wouldn't know you were brainwashed. If I asked you if you were brainwashed, you wouldn't be able to tell me you are brainwashed. If I asked you indirect questions relating to your brainwashing, I *might* be able to infer you were brainwashed, but since any response could be effected by the brainwashing, I still probably wouldn't be able to tell.

---

### Post by ice60 on 2007-03-30
are you two some kind of double act or something? you both might think you are being funny, but a security forum is not a place to joke around, please try and remember that. thank you.

---

### Post by pppetter on 2007-03-30
> **_tms said:**
> There seems to be some misunderstanding in this thread. The OS can't protect itself from root, but if a "regular" user of a ubuntu system can log in, run this rootkit and gain root privileges, there is a security flaw within the system and must be fixed A.S.A.P. 

I suggest you submit this as a bug/security issue,
If you have not figured out how exactly this program is gaining root access, provide exact step-by-step instructions of what needs to be done to run it.

You missed my point in the previus post.... In step 15 in this .doc file it says:
> 15.In the terminal window, enter this command, then press the Enter key:
sudo ./install 

In this How-to install a rootkit. So, the rootkit has to be _given_ root permissions to work, it doesn't "gain" it some weird way.

---

### Post by _tms on 2007-03-30
> **pppetter said:**
> You missed my point in the previus post.... In step 15 in this .doc file it says:


In this How-to install a rootkit. So, the rootkit has to be _given_ root permissions to work, it doesn't "gain" it some weird way.
Bah, busted! I only skimmed through the .doc file.

---

### Post by Frosty Cold Drink on 2007-03-30
> **ice60 said:**
> are you two some kind of double act or something? you both might think you are being funny, but a security forum is not a place to joke around, please try and remember that. thank you.

Is a valid analogy.

---

### Post by sbowne on 2007-03-30
Thanks to you all!  I appreciate the information.  After reading all the responses, my conclusions are:

1. I really need to look into Tripwire, because it seems to do what I did better

2. I don't think this is a bug to be patched in the OS.  If the OS starts having features just to stop individual exploits, it will soon be a complete mess like Windows.   It's better to put only directly useful stuff in the OS and leave malware protection in optional applications, so admins can easily choose what type of protection to use (if any).

I think this is now clear to all, but in case it isn't, the rootkit does not elevate privileges.  You must install it as a superuser.

Thanks again!

--Sam

---

