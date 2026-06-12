---
title: "Full disk encryption benefiters and risks"
date: 2008-12-12
forum: Security
---

### Post by shqip on 2008-12-12
Full disk encryption benefits and risks. 
I have been wondering about the full disk or hard drive encryption. What are the benefits of full disk encryption? 
 
Are there any ricks and what are they? 
 
Would your date be safe and secure on a server that would be 24/7 on-line? 
 
What is the main purpose of encrypting or having a full disk encrypted? 
 
Is there a way to also encrypt MBR or do you have to leave that part of the disk, unencrypted? 
 
I have also read that now even an encrypted disk is not safe?

---

### Post by DieB on 2008-12-12
first there are certain countries that got laws to force u to give free your password (even us and eu - as if they were not evil;) ).

second fulldisk-encryption might prevent u if your system is down against certain vulnerabilities, like someone just goes in and installs something, but it does not keep u safe from exploits through running apps.

Plus it will result in higher cpu-usage, plus u need /boot unecrypted (but for that simply use a usb-disk).

thats how much i know -  in short

p.s.: the usb-disk might only be a real opportunity if you can physicly get their.

For your purpose i would recommend intrusion-detection, there are some in the repositories - but that is a big hack.

---

### Post by bodhi.zazen on 2008-12-12
What are you trying to accomplish with encryption ?

When your data is encrypted you will not be able to access it. When you decrypt it it is accessible.

One risk would be if you lost the password or key, you would not be able to recover your data.

If the entire hard drive and swap partition are encrypted, you can not boot or access the data on the hard drive without the password and/or key.

Once the partition is booted, however, the data is accessible.

So again, what are you trying to accomplish ?

---

### Post by cdenley on 2008-12-12
Encryption only protects from physical access. Even then, if you leave it running 24/7, it is possible someone could reboot your computer to a livecd or something and find your encryption key in memory. Any time an encrypted filesystem is mounted, the key is in memory. So, in your case, it would be a deterrent for someone with physical access and dead-set on stealing your data, and a protection from someone who steals your drive/server but powers down or unplugs the server in the process. Also, it only protects you from data recovery, not data destruction. It does nothing for threats coming from the internet, or a local user.

---

### Post by shqip on 2008-12-12
> **bodhi.zazen said:**
> What are you trying to accomplish with encryption ?

When your data is encrypted you will not be able to access it. When you decrypt it it is accessible.

One risk would be if you lost the password or key, you would not be able to recover your data.

If the entire hard drive and swap partition are encrypted, you can not boot or access the data on the hard drive without the password and/or key.

Once the partition is booted, however, the data is accessible.

So again, what are you trying to accomplish ?
Well I thought that if you encrypt hard drive fully, that would prevent hackers and unwanted visitors from being able to read and write and install programs etc.  

I am more concerned with the on-line security rather the physical one. 
We are exposed to the insecure internet that sometimes I think, the only way to be safe and secure is not to use the internet at all, but how can you live without using the internet, where you find so much information and to me is like a big library you can access it from the comfort of your home. 

I am not trying to accomplish anything.  It just that I want to protect sensitive information and creative data/ideas not from physical theft. Plus as you are aware we do get visitors from time to time sniffing out, which I don&#8217;t mind as long as they don&#8217;t still my ideas and mess up with my computer/laptop/server? 
They are welcome to help though. 

It does not matter much if you are behind a firewall or not.

---

### Post by Dr Small on 2008-12-12
> **shqip said:**
> Well I thought that if you encrypt hard drive fully, that would prevent hackers and unwanted visitors from being able to read and write and install programs etc.  

I am more concerned with the on-line security rather the physical one. 
We are exposed to the insecure internet that sometimes I think, the only way to be safe and secure is not to use the internet at all, but how can you live without using the internet, where you find so much information and to me is like a big library you can access it from the comfort of your home. 

I am not trying to accomplish anything.  It just that I want to protect sensitive information and creative data/ideas not from physical theft. Plus as you are aware we do get visitors from time to time sniffing out, which I don&#8217;t mind as long as they don&#8217;t still my ideas and mess up with my computer/laptop/server? 
They are welcome to help though. 

It does not matter much if you are behind a firewall or not.
Well, then full disc encryption is not for you, since it only protects you against physical theft and cold boot attacks, as once the system has been unlocked, it runs decrypted as normal.

---

### Post by lensman3 on 2008-12-12
I run 3 of my 4 disks encrypted with truecrypt.  I encrypted the disk and THEN added a file system.  If someone steals the disk or I loose a disk between here and work, nobody can read it.  If someone does at Linux "dd" command on the drive, the info looks like noise.

Truecrypt even has a plausible denyability mode.  United States Homeland Security (oxymoron) has been confiscating HD's.  As a company that might have sensitive competitive info on the disk, you can tell TSA to keep the disk and walk away from the laptop.  You can be sure that even the NSA can't read it (if you have a good pass phrase).

I think that if I was transporting sensitive data around, I would require my employees to have the data under some kind of encryption.  Truecrypt makes a  little program the can even run off a flash memory stick, so whatever computer the stick is  plugged into you can decrypt it.  If you loose the stick nobody can read its contents.

---

### Post by shqip on 2008-12-13
> **Dr Small said:**
> Well, then full disc encryption is not for you, since it only protects you against physical theft and cold boot attacks, as once the system has been unlocked, it runs decrypted as normal.


What do you sugest the solution would be for me and for so many others out there?

---

### Post by shqip on 2008-12-13
> **lensman3 said:**
> I run 3 of my 4 disks encrypted with truecrypt.  I encrypted the disk and THEN added a file system.  If someone steals the disk or I loose a disk between here and work, nobody can read it.  If someone does at Linux &quot;dd&quot; command on the drive, the info looks like noise.

Truecrypt even has a plausible denyability mode.  United States Homeland Security (oxymoron) has been confiscating HD's.  As a company that might have sensitive competitive info on the disk, you can tell TSA to keep the disk and walk away from the laptop.  You can be sure that even the NSA can't read it (if you have a good pass phrase).

I think that if I was transporting sensitive data around, I would require my employees to have the data under some kind of encryption.  Truecrypt makes a  little program the can even run off a flash memory stick, so whatever computer the stick is  plugged into you can decrypt it.  If you loose the stick nobody can read its contents.

 I think that they should in the interest of all of us and to stop terrorism.   I am not against that as long as they do not do anything with peoples private and other sensitive data and as long as they keep it secure and secret, I don't see any problem with that.    I am not so sure about the encryption security though. It used to be good, but that's the past.

---

### Post by bodhi.zazen on 2008-12-13
Encryption is still solid :)

What and how are you trying to protect what exactly ?

First, look at hardening your OS. Use strong passwords.

If you are running a server , learn to secure it.

Next take a look at Apparmor or SELinux.

Also look at NIDS and HIDS (snort and OSSEC).

That should give you at least a start :twisted;

---

### Post by ItsJweed on 2008-12-14
> **bodhi.zazen said:**
> Encryption is still solid :)

On this topic, I'm currently in the process of wiping my HD after which I will be reinstalling Ubuntu from the alternate CD with full drive encryption. 

I've heard that it is better to fill the drive with random data before doing this to make cryptanalysis attacks more difficult and I've heard plaintext attacks are possible by attacking the headers. (Which are to some extent known.)

My question is this, if I put one large LVM encrypted partition on my HD with my /boot partition on a flash drive and use a random 50 character password with special characters and all to encrypt, is there any chance of the encryption on the drive being broken within my lifetime assuming an attacker gained access to the drive immediately after I was done installing? Lets assume they have massive computing resources.

---

### Post by NSAJEFF on 2008-12-14
The biggest issue I noticed when using tools such as TrueCrypt was massive slowdowns. These apps are system hogs. YMMV of course.

---

### Post by bodhi.zazen on 2008-12-14
I think it would take a long, long time to crack ;)

---

### Post by hyper_ch on 2008-12-15
and don't forgot: If you use encryption you also need backups.

If the initializing vector becomes corrupt of an encrypted drive or partition, you'll probably never get your data back.

---

### Post by ItsJweed on 2008-12-15
> **hyper_ch said:**
> and don't forgot: If you use encryption you also need backups.

If the initializing vector becomes corrupt of an encrypted drive or partition, you'll probably never get your data back.

Is the "initialization vector" stored on /boot or is it part of the LVM file system?

---

### Post by hyper_ch on 2008-12-16
it's part of the enrypted partition/harddisk... lvm is something else... /boot can't be encrypted...

---

### Post by ItsJweed on 2008-12-16
> **hyper_ch said:**
> it's part of the enrypted partition/harddisk... lvm is something else... /boot can't be encrypted...

So using something like dd to backup the first (insert some number of GB) of space on the drive is what I should do?

---

### Post by hyper_ch on 2008-12-16
you should always have backups, regardless of what you do... so you will just make encrypted backups in that case.

---

### Post by Vantrax on 2008-12-17
> **ItsJweed said:**
> On this topic, I'm currently in the process of wiping my HD after which I will be reinstalling Ubuntu from the alternate CD with full drive encryption. 

I've heard that it is better to fill the drive with random data before doing this to make cryptanalysis attacks more difficult and I've heard plaintext attacks are possible by attacking the headers. (Which are to some extent known.)

My question is this, if I put one large LVM encrypted partition on my HD with my /boot partition on a flash drive and use a random 50 character password with special characters and all to encrypt, is there any chance of the encryption on the drive being broken within my lifetime assuming an attacker gained access to the drive immediately after I was done installing? Lets assume they have massive computing resources.

About 6 months ago there was some fuss in the security community about a variety of FDE solutions that were easily crackable because they stored the access key in ram. They found that there was a ghost of the key still sitting in the ram and that they could extract it if they took the laptop. Thats a gross oversimplification of the issue (and im a little fuzzy on it) but if they just had the HDD that attack would be impossible. The other limitation is you would need to know that it was encrypted before you boot so you can take the imprint of the ram.

Don't remember what became of it as I was busy working on other stuff at the time.

---

### Post by hyper_ch on 2008-12-18
vantrax: google for "Cold boot attack". It's a pdf to be found at harvard I think.

---

### Post by ljwobker on 2009-01-07
> **ItsJweed said:**
> 
My question is this, if I put one large LVM encrypted partition on my HD with my /boot partition on a flash drive and use a random 50 character password with special characters and all to encrypt, is there any chance of the encryption on the drive being broken within my lifetime assuming an attacker gained access to the drive immediately after I was done installing? Lets assume they have massive computing resources.

Nothing is impossible, but it's certainly very very unlikely.  Once they get your drive, they copy it into a VERY fast memory store somewhere, and start running brute-force attacks on it.   Basically, they're trying passwords one at a time -- and each time after "decrypting" the data they have to look at it and decide whether or not they got the key "right".  If they got it right, the data will look like files, folders, and data.  If they got it wrong, it just looks like random data.

Ultimately it's just a matter of time and computing cycles.  But anyone who has enough of both to crack a really strong password with a really good cipher would also need a really good reason to come after YOUR data... which they probably don't have, right?  

Then again, if they have these kinds of resources, they can probably just follow you around and watch you type in your password one day, and then you're fooked.

---

### Post by hyper_ch on 2009-01-07
hacking such a passwords will take a very long time - even with millions of computers...

20 characters from a pool of 100 easly available different characters on your keyboard (a-zA-Z0-9 --> 58 plus special chars) gives you 100^20 possible combinations.

On average such a key would be broken after (100^20)/2 tries.

--> 5000000000000000000000000000000000000000

So, having a very fast computer that can, let's say, try 1 mio combinations pre second this will result in:

--> 5000000000000000000000000000000000 seconds.

Let's say you have 1 million computers at your disposal that call try 1 mio combinations per second then it "only" requires:

--> 5000000000000000000000000000 seconds.

That would be 1388888888888888888888888 hours

or

57870370370370370370370 days

or

158'440'439'070'144'751'185 years

assuming you have 1 mio computers at your disposal that can check 1 mio combinations per second.

So having a secure password with a strong key that has no weakness will protect you from brute-forcing.

But then, who knows what will be in 10 years or if a weakness is found in the encryption method.

---

### Post by Biochem on 2009-01-07
> **hyper_ch said:**
> hacking such a passwords will take a very long time - even with millions of computers...

20 characters from a pool of 100 easly available different characters on your keyboard (a-zA-Z0-9 --> 58 plus special chars) gives you **100^20 possible combinations**.



But that is _only if they know_ that your passphase is 20 characters long. If they have no clue it will be more like:

100^1+100^2+100^3+100^4...100^19+100^20

Which will take significantly longer to crack.
and also why it's stupid to have a rigid password maximum length (like my university's password which must absolutely be 8 characters long, 9 is not good enought.
They also force us to change it every freaking month!

---

### Post by hyper_ch on 2009-01-07
the others won't make it much longer, it will by about 1/99th more combinations....

---

