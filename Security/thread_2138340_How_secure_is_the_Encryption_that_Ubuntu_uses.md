---
title: "How secure is the Encryption that Ubuntu uses?"
date: 2013-04-23
forum: Security
---

### Post by Juniorr on 2013-04-23
I have a couple of questions:

1 - How secure is the Encryption that Ubuntu uses? Can a normal user by-pass it? FBI? Someone? (w/o the passwd, of course)

2 - How to restrict access to a specific folder? Let's say a friend comes to use my computer and I don't want him to see a folder. How to do that? And how to put a password to use, let's say, Chromium?

3 - I don't use a swap partition so no trace there, let's say, of a bank acc password. What are the other possible places that files may be when/after writing/accessing?

---

### Post by Cheesemill on 2013-04-23
Which encryption are you talking about?

There are two methods of encryption available to you when installing Ubuntu, either whole drive encryption or home folder encryption.

---

### Post by Juniorr on 2013-04-23
The home folder one, I didn't have time to learn how to encryp the whole disk AND have W7 installed as well.

---

### Post by slickymaster on 2013-04-23
> **Juniorr said:**
> 1 - How secure is the Encryption that Ubuntu uses? Can a normal user by-pass it? FBI? Someone? (w/o the passwd, of course)
I think Ubuntu uses AES-256 to encrypt the disk volume and has a cypher feedback to help protect it from frequency attacks and others attacks that target statically encrypted data. With it your computer is reasonably safe unless you are subject to serious organised cyber crime or Government investigation!
> **Juniorr said:**
> 2 - How to restrict access to a specific folder? Let's say a friend comes to use my computer and I don't want him to see a folder. How to do that? And how to put a password to use, let's say, Chromium?
You can change the permission of the folder```
sudo chmod 700 -R /home/user/my_folder
```

---

### Post by Juniorr on 2013-04-23
> **slickymaster said:**
> You can change the permission of the folder```
sudo chmod 700 -R /home/user/my_folder
```
And after that what do I need to do to access the folder? Is it reversible?

---

### Post by CharlesA on 2013-04-23
> **Juniorr said:**
> And after that what do I need to do to access the folder? Is it reversible?

You just made it readable and writable by your user only. If you want to put it back to the way it was you would just run this:

```
sudo chmod 755 -R /home/user/my_folder
```

---

### Post by Juniorr on 2013-04-23
> **CharlesA said:**
> You just made it readable and writable by your user only. If you want to put it back to the way it was you would just run this:

```
sudo chmod 755 -R /home/user/my_folder
```
I thought encryption enough to prevent other users to access it from other accounts.

What I want is like: When I click on the folder I need (ON MY ONLY ACCOUNT, there will be no other accounts) to type a password, is there such thing?

---

### Post by CharlesA on 2013-04-23
> **Juniorr said:**
> I thought encryption enough to prevent other users to access it from other accounts.

What I want is like: When I click on the folder I need (ON MY ONLY ACCOUNT, there will be no other accounts) to type a password, is there such thing?

It is. I don't know if you can password protect certain folders, though.

---

### Post by Irihapeti on 2013-04-23
You can do something of the kind using encfs.

When not mounted, the files are on the disk, but in a hidden folder and the names are also encrypted.

However, if someone discovered them and wanted to annoy you, they could just delete them. If that's likely to happen, keep a backup (a good idea anyway).

---

### Post by alphaamanitin on 2013-04-24
A better idea to protect files (not the entire system) is to use something like TrueCrypt to create a folder of X mb that looks like a file.  Decrypt it only as needed, and immediately encrypt when done.  

As for your first question about how secure vs the different groups, that depends on what you are willing to take as a loss.  Basically, you want to not have physical access when things are in their decrypted state and soon enough after it that a cold boot RAM dump is not feasible.

Here is what I would say on the issue:
You can hide files and change the permissions so that only the superuser can read/write etc.  You should have a guest account for friends so that they simply cannot access the area where the folder is stored.  In terms of defeating attacks you have to make a choice.  Create backups (which an organized attack like the FBI would probably find) or minimize the risk by minimizing the targets an attacker has.  I think you basically have to just accept that if some one (or group) get's physical acess to your computer or convinces you to run something on your computer, and you know it, than it is a total wash.  I would take a purge aproach in this case.  Everything associated with that computer is a total lose.  An important note here is that we are talking about a group that will obey the laws and doesn't have a reasonable suspicion that the data is on a computer, even with hidden encrypted volumes.

If you don't know about acess, well, you are screwed.  Game over, at some point no matter what you do, you will be compromised because you don't even know some part of your security, the most fundamental part, has been overcame.  

Scary though: it is a group like Russian mop that wants what is on your computer.  Consider your entire lifestyle a loss and get the hell out of dodge.  Cause for sure, if the Russian mob (or maybe even the CIA in one of my governments fun Hilton Torture Inn that we franshize to fun places) get a hold of you they arent not going to bother with cold boot attacks etc....You just became a real life example of the [xkcd joke on encryption]("https://xkcd.com/538/").    


Oh, you might find it interesting that the FBI doesn't even need direct physical access.  Methods used include analyzing the variation of the acoustics of each key, the EM radiation differences by key, differences in micro sugers of voltage in your power lines in your house.

Id

---

### Post by clearski on 2013-04-25
Create a TruyCrypt file container (which, as alhaamanitin said, looks like an ordinary file) and then copy it to your /home/username folder. Make sure you place a dot in front of filename (like .myfile). This way it will be invisible both in terminal and Nautilus, as long as the preferences are not set to "Show hidden files" for the second. Pick up a nice name like ".gksu_enviro" for the file container, so it will look like a file that the system is using, because there are others .gksu* files there. Make sure you're not using a name which exists. When you need to acces the file just delete the dot and the file will be visible and it will be easy to open it with TrueCrypt. And last, but not least, make sure you don't forget your key to TrueCrypt, because your files will be lost forever.

Of course, if you''ll have a 50 Gb file container named .gksu_enviro, someone searching for something will realize that something's wrong with that file in your /home/username (that is someone who has direct access to your computer and is really looking for some files into it).
However, that person won't probably be able to open the file.

Or you could just use both the Encrypt home folder of Ubuntu and the TrueCrypt. Or it could be more, but at least you could try these and decide if they are enough or you need extra layers of security. :)

---

### Post by Stonecold1995 on 2013-05-04
> **alphaamanitin said:**
> Oh, you might find it interesting that the FBI doesn't even need direct physical access.  Methods used include analyzing the variation of the acoustics of each key, the EM radiation differences by key, differences in micro sugers of voltage in your power lines in your house.
Without trying to accuse you of spreading FUD, I just have to point out that power analysis (and most other side-channel) attacks are nowhere near practical yet.  True, there have been tests that can get some information about the internal state of the CPU (and thus information about the encryption key) by monitoring voltage spikes, but this is also in extremely controlled conditions with the sensors DIRECTLY connected to the CPU, much less outside an entire house.  Currently there is no documented way to gather ANY information about the state of the CPU from outside your house (or even between your computer and the outlet as far as I am aware).

It IS true though that you can pick up on unique acoustics of each key being pressed, but that requires a sensitive microphone to be placed and active WHEN you enter the password.  Other side channel attacks don't need your interaction, they only need a computer actively encrypting/decrypting information.

[https://en.wikipedia.org/wiki/Side_channel_attack](https://en.wikipedia.org/wiki/Side_channel_attack)

Lots of people have already answered OP's questions, but while I'm here I'll throw in something too.

1) The encryption is very secure.  It uses AES256 (you can set it to the more powerful but slower Serpent) with a strong SHA512 (I think) hash.  If your password is sufficiently long and random, no, a normal user can't get in.  The FBI also will not be able to (again, assuming you've chosen a strong password, say, 30 characters mostly random), even with years of time to brute force/dictionary attack.  An massively funded and highly secret (and untrustworthy) organization like the NSA *might* be able to, given sufficient time and assuming the technology they possess is sufficiently more powerful than what is currently available (quantum computing, etc).  That's assuming they only try to break in through technical means though.  If they use for more conventional and effective techniques, they *will* be able to break through.  I don't know of any encryption algorithm that remains secure after a waterboarding session on the password owner!

2) You can protect specific folder by changing the permissions.  What I do (although it may be a more clunky or unsafe way, but it works for me), is run 
```
sudo chown -R root:root private_folder
sudo chmod -R a-rw private_folder
sudo chattr -R +i private_folder
```
To unlock it I use
```
sudo chattr -R -i private_folder
sudo chmod -R a+rw private_folder
sudo chown -R yourname:yourname private_folder
```

This way a user will need your user password to access the folder.  If you want a more secure method, just put the files in a TrueCrypt container and encrypt it with a long password.

3) Your password is only stored in RAM, and only for a very short time as you are entering it.  It is not stored in any temporary files.  Your user password's hash is stored in /etc/shadow as a very strong salted SHA512 hash.  While the hash is stored in plaintext (unless your whole disk is encrypted of course), if the password is long enough it will be nearly impossible to crack the hash and get the original password out of it.

---

### Post by Leslie Dorner on 2013-05-11
eCryptfs uses SHA-1 for the hash algorithm. Password shadowing uses SHA-512. LUKS uses SHA-1 as well. Encfs uses SHA-1 as well.

Rubber hose cryptanalysis is going to break you to give up your password nowadays especially if you live outside the USA.

---

### Post by Stonecold1995 on 2013-05-11
> **Leslie Dorner said:**
> eCryptfs uses SHA-1 for the hash algorithm. Password shadowing uses SHA-512. LUKS uses SHA-1 as well. Encfs uses SHA-1 as well.

Rubber hose cryptanalysis is going to break you to give up your password nowadays especially if you live outside the USA.
LUKS can be set to use other hash algorithms as well.  I'm using LUKS with Whirlpool.

Alsok, rubber hose cryptanalysis may be more common outside the USA, but if you are high profile, don't expect the CIA to play nice.

---

### Post by jamvaru on 2013-07-15
just use a usb for the real important stuff; and unmount/eject it often; i suppose you can do some encryption on it, too
there are intrusion distros, isn't there a non-intrusion distro? one that specializes in security?
probably just a bunch of packages anyways
it is all about increasing the size of your black hat relative to the size of your white hat; there is a balance there somewhere

---

### Post by tubbygweilo on 2013-07-15
> **jamvaru said:**
> . . . it is all about increasing the size of your black hat relative to the size of your white hat; there is a balance there somewhere

I would like to add that one should also consider what you are protecting and whom is after. I may well be wrong but not too many on this forum may be genuinely targeted or indeed penetrated by shady three letter acronym organisations, but may well be target of interest to a disgruntled partner, co-worker or a run of the mill criminal intent on parting a fool from their money.

Physical access is root access so keep hold of your kit and work outwards from there.

Know your enemy and plan accordingly.

---

