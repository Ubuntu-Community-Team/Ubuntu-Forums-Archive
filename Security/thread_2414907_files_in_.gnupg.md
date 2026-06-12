---
title: "files in .gnupg"
date: 2019-03-17
forum: Security
---

### Post by mcyber4 on 2019-03-17
Hi
Why I have after 30min or so, even with booting from live cd, two additional files in the .gnupg folder?
I had that on my old hacked pc, but on a 2 days old new laptop?
Thanks

---

### Post by mcyber4 on 2019-05-29
Anyone could confirm that? What is that? Thanks

---

### Post by Rubi1200 on 2019-05-29
Hi,

You're not exactly giving us much to go on.

What files? 

Show us the output please for

```
ls -l
```

And what do you mean by > [COLOR=#000000]even with booting from live cd[/COLOR]

What exactly does that mean?

Oh, and it would also help if we knew what version of Ubuntu you are using.

Thanks.

---

### Post by mcyber4 on 2019-05-30
Hi
on my new pc I've not yet installed a harddisk nor network. Selected "try ubuntu without installing". Ubuntu 19.04. If it's not readable I could try another screenshot. Are those used for encrypted downloads?
Many thanks

---

### Post by Rubi1200 on 2019-05-30
Hi,

Ah, okay now it is clear.

Not exactly encrypted downloads but it is encryption:
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
[https://packages.ubuntu.com/search?keywords=gnupg](https://packages.ubuntu.com/search?keywords=gnupg)

Be aware that during both live testing and installation many temp files are created and then later deleted during the cleanup phases.

I do not think there is something to be concerned about but if you have other questions feel free to ask.

---

### Post by mcyber4 on 2019-05-30
Thanks, I feel better&#8230; although on any clean system that I've heard those do not appear.
Can I get info about that? I've tried to open those files in some apps without success. If I delete them, they're back in a while.

---

### Post by Rubi1200 on 2019-05-30
Still not clear to me which files you are referring to and why you need to delete them.

---

### Post by mcyber4 on 2019-05-31
So that's normal on a fresh ubuntu? Anyone else has those?
[http://de.tinypic.com/r/ws9uzb/9](http://de.tinypic.com/r/ws9uzb/9)
seems weird that some app uses encryption.

---

### Post by Rubi1200 on 2019-05-31
I'm unable to confirm because I use a different setup when installing, meaning I use the minimal install which only adds a browser and core utilities needed for functionality.

But, Thunderbird email client would likely use GPG so in that case I guess those files are normal.

And there are probably also other applications that use GPG for example GNOME keyring which is used for logins etc.

Again, personally I do not see an issue with those files but there may be others with different experiences.

---

### Post by DuckHook on 2019-05-31
gnupg is the Gnome implementation of pgp. It is a very good security feature if used properly and is associated with GPG2. Those files are harmless and in fact necessary for GPG2 to function properly:

[https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration.html](https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration.html)

However, unless GPG2 has been invoked for some other use, it is unusual to see these files created. Given the OP's concern with security, it would not be surprising to have these files inadvertantly created by a process that he/she may have initiated but think was unrelated. GPG2 is used at a low level to support many app functions or extensions: for example, Enigmail in Thunderbird, many VPN implementations, etc. Too many to list.

[LIST]
[*]pubring.kbx is the public keyring keybox which is used to store generated public keys.
[*]trustdb.gpg is the file containing the trust database
[*]Everyone with a typical install has the private-keys-vl1.d which is the directory containing our private gpg keys. Even if we have no keys, the directory is generated.
[/LIST]
Fooling around with these files/directories will almost certainly break some app functionalities that depend on them. However, they are admittedly obscure and difficult to parse.

@OP

Encryption is used all the time and, in fact, should be used more, not less. All HTTPS web pages are encrypted. The best e-mail protocols use encryption. A popular one is gmail in which all data streams are encrypted until they reach their endpoints. While your typical update download is not encrypted, it uses a signing and verification scheme that is inseparably tied to modern encryption methodology. It's just that these apps use a self-contained encryption container instead of GPG.

---

### Post by Rubi1200 on 2019-05-31
> **DuckHook said:**
> gnupg is the Gnome implementation of pgp. It is a very good security feature if used properly and is associated with GPG2. Those files are harmless and in fact necessary for GPG2 to function properly:

[https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration.html](https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration.html)

However, unless GPG2 has been invoked for some other use, it is unusual to see these files created. Given the OP's concern with security, it would not be surprising to have these files inadvertantly created by a process that he/she may have initiated but think was unrelated. GPG2 is used at a low level to support many app functions or extensions: for example, Enigmail in Thunderbird, many VPN implementations, etc. Too many to list.

[LIST]
[*]pubring.kbx is the public keyring keybox which is used to store generated public keys.
[*]trustdb.gpg is the file containing the trust database
[*]Everyone with a typical install has the private-keys-vl1.d which is the directory containing our private gpg keys. Even if we have no keys, the directory is generated.
[/LIST]
Fooling around with these files/directories will almost certainly break some app functionalities that depend on them. However, they are admittedly obscure and difficult to parse.

I checked again and on my minimal Ubuntu MATE 19.04 install I do in fact have the private-keys-vl1.d directory, no surprise as DuckHook mentions.

I do not have the other files but also no surprise for me since I have been busy testing processes that likely would not need encryption.

I understand your concern about security but you have all the documentation and also support here so unless you want to try and backtrack and figure out which applications may have created those other files I would just leave it alone.

Just my opinion on the matter.

---

