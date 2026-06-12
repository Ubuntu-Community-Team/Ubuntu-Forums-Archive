---
title: "No-Swap Secure Bash Variables"
date: 2008-04-30
forum: Security
---

### Post by psych787 on 2008-04-30
I'm thinking of using TrueCrypt on my storage disks. However, I want to mount my TrueCrypt volumes securely by script. Specifically, I don't want my password paged out into swap somehow. Is there a way to:

1) Pass TrueCrypt my password as something other than a command line option?
2) Instruct bash that certain variables (my passwords) are NEVER to be paged out?

Thanks!

---

### Post by lemming465 on 2008-04-30
> I want to mount my TrueCrypt volumes securely by script
This is basically an impossible dream.  If the goal is a non-interactive script, there has to be non-interactive access to the key, meaning it's either stored on disk, or not encrypted, or has a null passphrase protecting it, or something equivalently icky.
If you can have interaction, e.g. insert & remove USB key, or type a password when prompted, you can do better.

---

### Post by psych787 on 2008-04-30
The interaction is typing the password. My concerns are that:
1) If the password is sent through command line, it will be part of the process list, and its name may end up in swap space or a log file somehow.
2) The variable itself may be swapped out or stored.

---

### Post by lemming465 on 2008-05-01
> **psych787 said:**
> The interaction is typing the password. My concerns are ///


Actually, it's worse than that: attackers with physical access the machine can use the Princeton [Cold Boot Attack]("http://citp.princeton.edu/memory/") to recover the key from RAM.  Truecrypt, Bitlocker, FileVault - everything is vulnerable to this, because the keys have to be in RAM to run the decryption.  The next generation of paranoid operating systems is going to be a lot pickier about sanitizing RAM during shutdown and about interactions between hibernation and disk encryption.  However, this is not a major risk for powered off laptops; it's more of a mission impossible movie plot threat for server rooms.

> 
1) If the password is sent through command line, it will be part of the process list 
Quite true, and the only possible answer is *don't do that*.  Programs which want passphrases should prompt interactively for them with keyboard echo turned off; things like passwd, su, sudo, gksu and so on do this already.  And not be run under *script*.
> its name may end up in swap space or a log file somehow.
I'm not sure I entirely understand you here.  Your concern is valid; an obvious file to worry about is ~/.bash_history.

I haven't read the code, but the Truecrypt technical documentation makes it seem like it flags its password memory as non-swappable, which should help mitigate things there.  Bash is not that paranoid, so if the script is going to be interactive, it would be best to code it without storing passwords in variables.  Writing a C helper program which marked its storage as non-swappable, used a random initialization vector to xor with the password, and erased it before exit, could help mitigate that if you have to have repeated access to the password.

In general, if you are doing encryption at all, the weakest point is probably something else.  It also makes a difference whether your threat model is most concerned with physical or network attacks, or both. E.g. certificate authorities are usually off-line and used only via sneakernet to eliminate network attacks, and use special hardware storage modules for the private keys to avoid disk risks, and so on.

An excellent (if somewhat academic) book on overall security design is Ross Anderson's _Security Engineering_, if you want somewhere to read up on this stuff.


Good luck with it!

---

### Post by psych787 on 2008-05-01
1) I am aware of the cold boot RAM issue. However, due to its fast read/write speed, its not that hard to wipe ram, and there are tools to do so. TrueCrypt itself knows to to this unless you pull the plug. Actually, if someone got physically close to the machine while its turned on there are a lot of cheaper and more effective side channel attacks that have yet to be dealt with (obfusticated) properly.
2) So you're telling me I would have to enter the password interactively? Ok, great. Now every time I boot up, I'm going to have to enter my 10+ digit password 4 times? Or can TrueCrypt mount multiple containers at once?
3) Actually I don't even have a bash_history. I chmodded it so no one can write into it. My concern is some file that somehow logs activity related to the password (including memory dumps). Obviously this is not as much of an issue on Linux as Windoze, but it is still a spot of concern if I'm doing password sensitive stuff outside TrueCrypt, which is already secure about that.
4) Its a little beyond my skills to make a C+ helper program, and I don't see how that would solve the problem. One way or another, TrueCrypt would be getting the password where it would show up in the process list.
5) There aren't other weak points. Network access is guarded by a Linux router, which is always behind another router, and only accessible in special cryptographic ways which I will not describe here. Physical access is the primary concern, and the ideal goal is make the data inaccessible when the machine is turned off.

---

