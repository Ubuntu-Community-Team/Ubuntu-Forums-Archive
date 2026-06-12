---
title: "whole disk encryption"
date: 2008-09-23
forum: Security
---

### Post by Aleksandr on 2008-09-23
I have just used the alternate cd to make a whole disk encryption and I have some questions if anyone knows.

1)What kind of encryption/which algorithm is used? I could not find any specifications.

2)What are the known vulnerabilities of this specific type of encryption? I mean if someone tries to check my disk, what he will try to exploit?

3)Is this encryption trusworthy/reliable? Is the whole disk/system really encrypted? When I tried to encrypt the whole disk with truecrypt in Windows it took several hours. This encryption, on the contrary was much faster which really makes me wonder about its reliability.

If someones knows any answer to the above questions or can give me some relevant urls, I would be gratefull. I could not find anything on google :(:(:(

Thank you!!! :):):)

---

### Post by hyper_ch on 2008-09-23
> **Aleksandr said:**
> 1)What kind of encryption/which algorithm is used? I could not find any specifications.
The one you chose during installation.

> **Aleksandr said:**
> 2)What are the known vulnerabilities of this specific type of encryption? I mean if someone tries to check my disk, what he will try to exploit?
There are no known vulneberalities

[/QUOTE]3)Is this encryption trusworthy/reliable? Is the whole disk/system really encrypted?[/QUOTE]
Yes

There is one chance to defeat the encryption (applies also for truecrypt) and that's reading out the ramblocks in which the password for unlocking is stored. It has been shown that by freezing the ram modules that the encryption key can be retained for quite some time even after a power cut.

---

### Post by Aleksandr on 2008-09-23
Thank you very much indeed for your response.

I did not choose any algorithm during installation. I wasn't asked for one! Does that mean that the default was used? Which one is that? How can I check it now that I have completed the installation?

Yes, I do know about freezing the memory but I think it's a rather long shot.

Can you please tell me what exactly is

dm-crypt and sda5-crypt??? 

I thought that it was some kind of algorithm like AES...

---

### Post by jerome1232 on 2008-09-24
I believe the default is LUKS.

---

### Post by Aleksandr on 2008-09-24
Thank you but I don't think that LUKS is some kind of algorithm. I think that is an encryption method or something like that.

---

### Post by hyper_ch on 2008-09-24
oh, you did not manually setup the encryption but automatic encryption? I guess then it's AES with sha256...

You can check in my little howto here: [http://ubuntuforums.org/showpost.php?p=5314750&postcount=4](http://ubuntuforums.org/showpost.php?p=5314750&postcount=4) --> those are the default encryption settings when you set it up manually... I guess they will also be default when you to it automatic.

---

