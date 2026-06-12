---
title: "Keystroke encryption"
date: 2009-03-23
forum: Security
---

### Post by shad0w_crash on 2009-03-23
Heey,

I'm looking for a tool, package for keystroke encryptions. On windows I did use Bluegem, because it's closed source i don't know if it did really encrypted the keystrokes but it sounds usefull.

Is there an alternative for Bluegem, keystroke encryption on Ubuntu? 

Is it an alternative to make lots of calculations (perl script oid) to fill my RAM with? My aim is to make it impossible for a forensic or a hacker using forensic toolkits to extract my truecrypt password (or other passwords) out of my RAM.

---

### Post by Lisa Y on 2009-03-23
Hi there,

Try this site 

[http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)

That might be of some help to you.

---

### Post by shad0w_crash on 2009-03-23
Thanks for the repley, but this is not where i'm looking for. I'm allready running OSSEC (file integrity scanner). And rkhunter to check for rootkits (and double check ossec, but what if rkhunter is rootkitted;)?.

I'm looking for defense against the following situation:

I forgot my laptop somebody quickly inserts an liveCD and makes a full copy of my RAM memory. Passwords are all unencrypted in the RAM. Bluegem claims to have protection against that type of attack by encrypting the keystrokes.

---

### Post by hyper_ch on 2009-03-23
I don't think there's any protection against cold boot attacks.

---

### Post by shad0w_crash on 2009-03-23
Now but it isn't a cold boot attack, it's encrypting the trafic from your keyboard to you RAM.

---

### Post by hyper_ch on 2009-03-23
reading out ram for encryption keys --> cold boot attack

---

### Post by Tubes6al4v on 2009-03-24
I am pretty sure everything on RAM has to be decrypted to be used for processing. There are two ways I can think of to prevent RAM attacks, 
1) Build some kind of barrier around it so it cannot be frozen. You'll probably need some cool cooling setup. 
2) Write some scripts to fill your RAM with random bits. This would take a while I think, but you may be able to have it target the most recently used sectors first, then work back.

Just some thoughts...

---

### Post by shad0w_crash on 2009-03-24
Yes I was also thinkin on that, Of course you got a risk that your secret information is in your swap file.

But if you mounth your truecrypt volume and then run the script the password i typed is gone out of ram.

---

### Post by hyper_ch on 2009-03-24
> **shad0w_crash said:**
> But if you mounth your truecrypt volume and then run the script the password i typed is gone out of ram.

Are you sure of that? I think that won't work.

---

### Post by shad0w_crash on 2009-03-24
No I'm not 100% sure, 
But when you type your password it's in your RAM for sure. I don't know how truecrypt works or Amsn or other applications but i guess they set a flag or create a session when you logged in.

If you make a memory dump you'll get a whole bunch of information. wich is allowed to get overwriten because it's not used anymore. If you overwrite the allowed possitions with just say the letter 'a' there's nothing you can find.

Next saturday if've time to do some testing. This will be my test case:

Entering a string in gedit.
Dumping memory of the specified program and try searching my string.
Trying a perl script to search for prime numbers (ore some like) at least enough to use 756MB of RAM. 
Dumping the memory again and search on the string.

Maby proces memory locations can't be overwritten i don't know yet how the Ubuntu architecture works. But maby it'll work fine.

Anyone having suggestions?

---

### Post by hyper_ch on 2009-03-24
IMHO they key stays clear in memory as tc and dm-crypt do on-the-fly en/decryption.

---

### Post by Tubes6al4v on 2009-03-25
I think hyper is right. Your processer needs the key to decrypt your data. It is always encrypted on the drive, so you need it as long as you are looking at the drive.

As for SWAP, that should be encrypted as well.

---

### Post by shad0w_crash on 2009-03-25
I think he's right to for the fact TC needs the encryption key. But i could still test if the RAM could be cleared after the program is quited isn't?

---

### Post by hyper_ch on 2009-03-25
you can check that :)

---

