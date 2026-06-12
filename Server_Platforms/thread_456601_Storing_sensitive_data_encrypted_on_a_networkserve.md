---
title: "Storing sensitive data encrypted on a networkserver - possible riscs?"
date: 2007-05-27
forum: Server Platforms
---

### Post by burzum on 2007-05-27
How can i store all data secure (encrypted) on my server but accessing it from other machines without "opening" it with possible holes? I mean there theoreticly bugs in smb/nfs/apache/mysql/openssh that will external users allow to hack into the machine and be able to access the encrypted data as root or at least as a user thats allowed to access some data via the network.

I want to be sure that nobody else then the admin of this machine is able to access the data if the hd or the whole machine is stolen.

Any comments or is just my logic wrong?

---

### Post by eroper on 2007-05-27
There are several risks that come to mind immediately. Encryption is not necessarily a silver bullet as far as data protection goes. A lot of it is determining what acceptable risk levels are. How valuable is the data, who are you protecting it from, and why.

I am not, by any stretch of the imagination, an expert on encryption or data security. I will however attempt to do my best to cover some high level details, with the hopes that someone more knowledgeable corrects me in the event that I am incorrect.

During the time of operation that you are editing, viewing, or otherwise holding the data unencrypted on a machine, a copy of the plain text data is in memory. If the application is not designed appropriately, this memory may be swapped to disk. In this event, it could be stored, on disk, unencrypted, potentially for a long period of time. Applications like gpg will do their best to "lock" the memory they use, thus ensuring that it is never allowed to swap to disk. I believe that gpg will warn if it is unable to do this.

Regardless of whether or not an application uses swap, uid 0 (root) has access to all memory in the system. It would indeed be possible for a knowledgeable party, with appropriate permissions, to peek at the plain-text contents of your encrypted data at any moment that they were unencrypted in memory.

Additionally, if you choose to edit, or otherwise cause the encrypted data to become present on the file-system (even temporarily) in an unencrypted form, it becomes non-trivial to guarantee that the contents are fully erased when you have finished with them. While utilities such as: shred, wipe, srm, etc. exist for the purpose of "securely wiping data from files" they are at the mercy of the underlying operating system and file-system implementations. Again, not being an expert I won't comment on Linux kernel version X with file-system Y.

Even if you are just storing the data on the server, never decrypting it there, remember that with an infinite amount of time and infinite resources, any encryption can be broken, if only by brute force. This means that given enough of the above, a determined attacker could potentially glean useful information from your encrypted source. Encryption, to my knowledge, is based on making it uneconomical both in monetary and chronological terms for an attacker to deem your data worthwhile.

In parting, remember that once a system has been compromised, all of its binaries become suspect. This means that you may not be able to trust the encryption tool binaries themselves. If your data is valuable enough, don't store it on a network attached device, particularly a shared resource which you do not have full control of. Evaluate the value of your data, the risks that it is exposed to, and do your best to make an informed decision.

---

### Post by ruy_lopez on 2007-05-28
The theoretical bugs in the applications are mitigated by keeping the applications up to date. At the moment there's a $16,000 reward for anyone who can find a remote exploit into apache.

Openssh is pretty robust. All the others present data on the network that can be sniffed. If access to your system is physically limited to yourself. And the only way you access from another system is SSH, there's not much to be concerned about.

Unencrypted memory, swap space, all require root access on the system. Put it this way, if someone has root access on your system, you have a problem, data encryption or not.

Everything the above post says it true. 

File system encryption isn't supposed to prevent people seeing data while the system is running. Its purpose is to prevent people accessing your data when your system is powered down, or has been stolen.

You are better off trying to limit root access.

---

### Post by Chayak on 2007-05-28
On encryption...
1. Don't keep your encryption key on the same machine.  If the machine is cracked your data will still be secure as long as the key isn't there.
2. Use strong proven encryption.  AES 128 or 256bit is the standard now though I will always suggest the 256 bit.  Theoretically if every atom on the planet was Deep Blue supercompuer our sun would die before even a fracton of the keyspace was bruteforced.  This isn't to say it's impossible.  If someone really wants your data they'll fall back to what the intelligence community uses the 3B method... Bribery, Burgularly (from keyloggers, tempest, etc), and Blackmail.
3. Be wary of snakeoil, use proven community reviewed (the cryptography community) systems.  Two of the best known are GPG and Truecrypt though refer to #1.  If they can get a copy of your private keys (GPG wise) it makes the job easier as they just have to crack your passphrase which is easier than the full strength keyspace.  Truecrypt wise use a USB flash drive and pick a random file on it as a keyfile.

Other than that you can use the day to day methods I have to use when dealing with encryption at work (Navy)  Two person integrity with the key material, stored in safes within vaults inside of heavily guarded buildings or ships and where no one person knows all the combos or certain things that use two part combos, tamper proof equipment that will zero ( erase its key memory ) if tampred with.  Oh and everyone that even thinks of getting close to it having extensive investigations... something about national security or some such thing ;)

But seriously, use a well known trusted program and get your keys off the system somehow.  It's up to you how severe the measures you want to take to keep your data secure.

Personally all my keys are kept on a Spyrus Hydra Privacy Card 2 that's set to zero itself on certain events, and no I don't keep any backup copies of the key.  If it gets zeroed it's gone for good.

---

