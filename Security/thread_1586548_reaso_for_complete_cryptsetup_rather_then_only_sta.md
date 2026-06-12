---
title: "reaso for complete cryptsetup rather then only standard home crypting?"
date: 2010-10-02
forum: Security
---

### Post by nico23 on 2010-10-02
i mean when my home is crypted and i will make my linux to del my swap on shutdown why should i need the whole drive encrypted?

i meam linux is legal and open source and if somebody could see withc programms and configs i have does it matter?

most of the personal configs and in /home right?

what do you think about that? i have all the other stuff on truecrypt partitions anyway so why would i need to crypt my linux partition?

---

### Post by envygeeks on 2010-10-02
> **nico23 said:**
> i mean when my home is crypted and i will make my linux to del my swap on shutdown why should i need the whole drive encrypted?

Encrypting the entire drive is mostly for Enterprise and development environments, but still flawed by application.

> **nico23 said:**
> 
i meam linux is legal and open source and if somebody could see withc programms and configs i have does it matter?


Again, enterprise and development security.  Home users don't care about anything more than home folder encryption.

> **nico23 said:**
> 
most of the personal configs and in /home right?


It depends on what you mean by "personal configs" if by "personal configs" you mean stuff like passwords, SSH keys, PGP keys and configuration information for thunderbird, pidgin then your answer is yes.

> **nico23 said:**
> 
what do you think about that? i have all the other stuff on truecrypt partitions anyway so why would i need to crypt my linux partition?

Truecrypt is only useful if your processor can handle it and if you actually need it, for simple encryption with no plausible deniablility (multiple passwords) then it's much more viable to go and buy and AES encrypted drive that uses hardware chips to do it, such as Western Digital Passports.  That is because at that point you obviously don't care about your information security /that much/ because you don't give your self the room to wiggle out with plausible deniability, not that Linux gives you that ability anyways, and most people often assume that Linux encryption is just utterly safe, when by theory it's flawed by application because of the deniability factor.

You don't need to encrypt your entire Linux install, again, this is mostly for the enterprise, developers and other people that might handle data that needs some form of /basic/ protection. Home folder encryption is more than enough to keep your data from the prying eyes and mostly came about because of those so called "personal configs", a good example is pidgin which stores user information in plain text in your home folder.  with home folder encryption John can't view your personal files from his username because your home folder is encrypted. So, John can't go and hijack your AOL username and password easily.


Here is my personal spin:

The way Linux handles encryption right now by default is rather weak in applicaiton.  They /redhat at first/ brought it about as 'enterprise security' but for /true/ enterprise security it's worthless.  When we think about protecting our data, our number one enemy happens to be the people around us, they know we encrypt the data.  Our second enemy happens to be people who might try to exploit us, extortionists. In both cases they know that we encrypt the data.  In normal situations on Linux you don't have plausible deniability, as a matter of fact, you have none. They know you encrypt it.  I've (along with plenty of others) suggested to Ubuntu ( multiple times) and redhat (multiple times) that for the encryption to be truly usable it should involve some form of deniability, meaning, if you come to me and know I have encryption, I need to have a /second/ key that I can give you, and it needs to wrap in a way (much like Truecrypt hidden volumes /which I mentioned earlier/) that nobody could ever tell that there is actually two encryptions there and you would never know if I gave you the right or wrong key because you decrypted something, just the wrong something, and you could never tell here was something else there.

---

### Post by OpSecShellshock on 2010-10-02
To add to the above: full disk encryption is really only necessary when it's arbitrarily required in order to "comply" with some industry information systems standard. I say arbitrarily because a sensible encryption policy would take into consideration the data itself and the specific risks involved in its storage. In most cases, even at the enterprise level, not having it there in the first place is a much better option than encrypting the whole disk. This is especially true considering that encryption only applies in "at-rest" circumstances--while there's an active session and the disk is in use, it's not encrypted. If users don't power down while the device is unattended, then they're not really getting anything out of it. And of course they aren't powering down.

Also, the greatest risk to information systems is posed by those who have legitimate access. Whether they breach by accident or intentionally, they still breach more often than any intruder ever could. Encryption does not and cannot solve that problem. It's not meant to.

Having said all that, I'll just admit that it's easier to check the box and be compliant than it is to argue.

At home, on your own stuff, you probably have a better idea of what risks there are regarding where your data is stored and who can physically access the devices that it sits on. Just encrypt accordingly and you're good.

---

### Post by rookcifer on 2010-10-02
> **envygeeks said:**
> 
Again, enterprise and development security.  Home users don't care about anything more than home folder encryption.


I disagree.  Encrypting the whole drive is best since there would be no way to find any residual data associated with encrypted data in the / partition or in /tmp or in swap, etc.


> Truecrypt is only useful if your processor can handle it and if you actually need it, for simple encryption with no plausible deniablility (multiple passwords) then it's much more viable to go and buy and AES encrypted drive that uses hardware chips to do it, such as Western Digital Passports. 

I wouldn't trust hard drive hardware crypto.  In at least [one case]("http://www.sophos.com/blogs/gc/g/2010/01/05/flash-drive-manufacturers-warn-hackers-decrypt-secure-usb-sticks/"), it was shown that the hard drive maker made a boneheaded mistake that allowed the drive to be decrypted by an attacker (granted these were flash drives, but the same concerns occur in spin drives).  Indeed, if the code isn't available for public review, the crypto should not be trusted.  This is especially true in this era of governments mandating that they have backdoors into hardware and software crypto.  If the government asks for it you can rest assured Seagate, WD and other makers WILL comply.


 > That is because at that point you obviously don't care about your information security /that much/ because you don't give your self the room to wiggle out with plausible deniability, not that Linux gives you that ability anyways, and most people often assume that Linux encryption is just utterly safe, when by theory it's flawed by application because of the deniability factor.


If you're talking about Truecrypt's hidden volumes, they are not bullet proof either as shown by Bruce Schneier and his research team.


Here is my personal spin:

> The way Linux handles encryption right now by default is rather weak in applicaiton.  They /redhat at first/ brought it about as 'enterprise security' but for /true/ enterprise security it's worthless.  When we think about protecting our data, our number one enemy happens to be the people around us, they know we encrypt the data.

If an adversary knows you encrypt data, that does no good in helping them decrypt it.  If you're talking about rubber hose cryptanalysis here, that's beyond the scope of what ANY software or hardware can protect against.  That's a strictly human element.  In reality most people don't have to fear being tortured.

 >  Our second enemy happens to be people who might try to exploit us, extortionists. In both cases they know that we encrypt the data.  In normal situations on Linux you don't have plausible deniability, as a matter of fact, you have none. They know you encrypt it.  I've (along with plenty of others) suggested to Ubuntu ( multiple times) and redhat (multiple times) that for the encryption to be truly usable it should involve some form of deniability, meaning, if you come to me and know I have encryption, I need to have a /second/ key that I can give you, and it needs to wrap in a way (much like Truecrypt hidden volumes /which I mentioned earlier/) that nobody could ever tell that there is actually two encryptions there and you would never know if I gave you the right or wrong key because you decrypted something, just the wrong something, and you could never tell here was something else there.

Again, I question the worthiness of plausible deniability.  If one wants plausible deniability they can just as easily say "I forgot my pass phrase" or "that random spot on my hard drive is just where I wiped the drive, it isn't an encrypted volume."  And that says nothing about the technical limitations of it (it probably isn't deniable at all, as Schneier and company pointed out in a [research paper]("http://www.darkreading.com/security/encryption/showArticle.jhtml?articleID=211201156")).

---

### Post by envygeeks on 2010-10-02
> **rookcifer said:**
> I disagree.  Encrypting the whole drive is best since there would be no way to find any residual data associated with encrypted data in the / partition or in /tmp or in swap, etc.

So you're saying the Kernel developers lied when they said that SWAP files are as fast as swap partitions. So you obviously can't create a swap file for each user in their home folder? And you surely can't create a temp folder for each user in their home folder. Some of us don't even have SWAPs too, modern servers don't carry swaps because they cause I/O issues, and people like me don't even have swaps on our personal computers.

> **rookcifer said:**
> 
I wouldn't trust hard drive hardware crypto.  In at least [one case]("http://www.sophos.com/blogs/gc/g/2010/01/05/flash-drive-manufacturers-warn-hackers-decrypt-secure-usb-sticks/"), it was shown that the hard drive maker made a boneheaded mistake that allowed the drive to be decrypted by an attacker (granted these were flash drives, but the same concerns occur in spin drives).  Indeed, if the code isn't available for public review, the crypto should not be trusted.  This is especially true in this era of governments mandating that they have backdoors into hardware and software crypto.  If the government asks for it you can rest assured Seagate, WD and other makers WILL comply.


Because every drive is a spin drive? Everybody knows that relying on WD to make crypto isn't safe, that is why, I implied /reading would have caught that implication/ you should use them because quote "you obviously don't care about your information security /that much/" while part of the rational was plausible deniability that is not the entire rational.

 

> **rookcifer said:**
> 
If you're talking about Truecrypt's hidden volumes, they are not bullet proof either as shown by Bruce Schneier and his research team.


And he admitted shortly after that v6.0 of Truecrypt fixed those problems because they received the white paper from his "research team", quote from his entry: "So we cannot break the deniability feature in TrueCrypt 6.0."

> **rookcifer said:**
> 
If an adversary knows you encrypt data, that does no good in helping them decrypt it.  If you're talking about rubber hose cryptanalysis here, that's beyond the scope of what ANY software or hardware can protect against.  That's a strictly human element.  In reality most people don't have to fear being tortured.


Nobody said it does help them decrypt it, it was implied it gives them motivation to try and decrypt it.  And false, in reality, most people respond to torture.  If they didn't there wouldn't be so many forced information leaks in the world, right?  This is why the CIA, NSA and Special Forces train their people not to respond to torture.


> **rookcifer said:**
> 
Again, I question the worthiness of plausible deniability.  If one wants plausible deniability they can just as easily say "I forgot my pass phrase" or "that random spot on my hard drive is just where I wiped the drive, it isn't an encrypted volume."  And that says nothing about the technical limitations of it (it probably isn't deniable at all, as Schneier and company pointed out in a [research paper]("http://www.darkreading.com/security/encryption/showArticle.jhtml?articleID=211201156")).

The first point will only work in some cases, the second point will not always if /ever/ work because they can tell that it is encryption.  They just can't tell if it's multiple encryptions if it's designed right.  They can tell that it's not data from wiping the drive, they cannot tell what data it is though.  The link to the actual white paper: [http://www.schneier.com/paper-truecrypt-dfs.pdf](http://www.schneier.com/paper-truecrypt-dfs.pdf)

---

### Post by bodhi.zazen on 2010-10-02
> **nico23 said:**
> i mean when my home is crypted and i will make my linux to del my swap on shutdown why should i need the whole drive encrypted?

i meam linux is legal and open source and if somebody could see withc programms and configs i have does it matter?

most of the personal configs and in /home right?

what do you think about that? i have all the other stuff on truecrypt partitions anyway so why would i need to crypt my linux partition?

Encrypt what you want. On mobile devices, laptops / netbooks I personally encrypt the entire install, /root swap and /home

Honestly, for what i do, that satisfies my personal paranoia.

If you prefer no encryption or encrypt only your data or only your home, well nothing wrong with that either.

The vast majority of the people on these forums probably do not need encryption at all.

---

### Post by HermanAB on 2010-10-03
Hmm, note that encryption only protects data at rest.  That means, it only protects your data when your machine is switched *off*.

The main reason to use encryption is to protect a machine when it has been stolen, or when you are afraid that someone can subvert it at night when no-one is around.

In general, the more of the disk drive you encrypt, the more difficult it is for someone to mess with it without your knowing when it was switched off.  For normal users, it should be sufficient to encrypt /home only.  For paranoid folks (including government users) it is best to do 'full disk encryption' (there is always some small part that is not encrypted to allow the machine to boot).

However, while the machine is running, the data is transparently decrypted, so it doesn't help with security of a running system.

---

### Post by jwhendy on 2010-10-04
Perhaps a related question... I'm just recently looking into encryption for my computer and have been wondering similar things. One question is this: what information "spills over" into other directories when using one's computer?

For example, say only  /home is encrypted. When log files are written, I'm moving around various files, opening spreadsheets, on the web... what is recorded elsewhere?

Is there anything in /var or elsewhere, for example, that would show that my user profile opened some file called "Bank_Records_2010" in Moneydance or something?

Is that a concern at all? To leave no trace of file names and other "metadata" outside of the encrypted partition. Would this be compromised at all with the use of only an encrypted /home partition or can anyone here verify that something like I've described doesn't happen?

---

