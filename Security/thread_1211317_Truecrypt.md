---
title: "Truecrypt"
date: 2009-07-12
forum: Security
---

### Post by RedSingularity on 2009-07-12
I am currently working with truecrypt on my USB sticks.  I noticed that when i encrypt a stick i cannot mount it unless i use the truecrypt software to do so.  Is there any way around this?  I mean i dont want to have to install truecrypt on every computer i use my USB drive on.  That is a hassle and in some cases, such as at my university, i cannot install software myself.

---

### Post by HermanAB on 2009-07-12
Well, you could use LUKS and then install LUKS or FreeOTFE on every computer you work on, or you can install GPG on every computer you work on...

---

### Post by RedSingularity on 2009-07-12
But what if i cannot install software on a computer.  At my university i cannot install software due to administration privileges needed.  By the way they are running Winblows XP not linux.

---

### Post by mdebusk on 2009-07-12
> **Shadow121 said:**
> when i encrypt a stick i cannot mount it unless i use the truecrypt software to do so.  Is there any way around this?

[Read this and see if it gives you what you need.]("http://www.truecrypt.org/docs/administrator-privileges")

---

### Post by juancarlospaco on 2009-07-12
*BTW Truecrypt its easy to hack nowadays...*

---

### Post by RedSingularity on 2009-07-12
> **mdebusk said:**
> [Read this and see if it gives you what you need.]("http://www.truecrypt.org/docs/administrator-privileges")


Thanks...that got me on the right track.

---

### Post by tubbygweilo on 2009-07-13
> **juancarlospaco said:**
> *BTW Truecrypt its easy to hack nowadays...*

Can you please point me to a research paper, exploit in the wild or something along those lines that supports your posting as I and MrGoogle are having a hard time finding this news.

Those I support make quite a bit of use of Truecrypt and any news about exploits would be most welcome.

Many thanks.

---

### Post by XCan on 2009-07-13
> **juancarlospaco said:**
> *BTW Truecrypt its easy to hack nowadays...*

The only 'hack' I've read about are those dump-key-to-storage-media-fast-as-heck-before-ram-clears-after-hard-boot thingies, are you referring to a new exploit in Truecrypt?

---

### Post by Lucky. on 2009-07-13
> **tubbygweilo said:**
> Can you please point me to a research paper, exploit in the wild or something along those lines that supports your posting as I and MrGoogle are having a hard time finding this news.

Those I support make quite a bit of use of Truecrypt and any news about exploits would be most welcome.

Many thanks.

Ditto, I want to see this too.

---

### Post by doas777 on 2009-07-13
agreed, I've never seen a serious complaint about truecrypt, except that it's components are under like 12 different licenses (though none are really encumbering).

---

### Post by shad0w_crash on 2009-07-14
Never heard of an attack on TrueCrypt. Maby it's an algoritm that is broken? I checked AES and the most they get is a XSL attack [http://en.wikipedia.org/wiki/XSL_attack](http://en.wikipedia.org/wiki/XSL_attack)

Anyone more information?

---

### Post by pauna on 2009-07-14
Just because of these admin issues, I've stopped using Truecrypt on my USB sticks. Instead, I've just gotten a HW encrypting USB disk ([http://www.h-online.com/security/A-secure-USB-disk-from-Lenovo--/features/113192](http://www.h-online.com/security/A-secure-USB-disk-from-Lenovo--/features/113192)).

Sure it's bigger than an USB stick and expensive, but works in all kinds of situations and setups. No software or drivers required.

And I'm still running Truecrypt for some other needs, just not USB sticks.

---

### Post by theevilhamster on 2009-07-14
Please reply with the security issue! I'm terrified about my sensitive information being leaked, and if i cannot protect against the issue, i'll destroy my drive!

---

### Post by pauna on 2009-07-14
> **theevilhamster said:**
> Please reply with the security issue! I'm terrified about my sensitive information being leaked, and if i cannot protect against the issue, i'll destroy my drive!

I don't think there are real security issues with the current version of Truecrypt. The only problems I know are well documented on the Truecrypt web page (for example bootloader infection).

There have been issues in previous versions of Truecrypt (for example version 5.1 had a vulnerability with the deniable file system), but version 6.0 fixed that.

---

### Post by doas777 on 2009-07-14
I do know that there are theoretical means to determine if there is a stenographic (hidden) volume, and that an algorithmic attack was released last week that reduces the number of operations to bruteforce an AES256 cipher tosomthing like 2^111 from the previous 2^120. I can't say I'm losing sleep over either of those.

---

### Post by theevilhamster on 2009-07-16
> **pauna said:**
> I don't think there are real security issues with the current version of Truecrypt. The only problems I know are well documented on the Truecrypt web page (for example bootloader infection).

There have been issues in previous versions of Truecrypt (for example version 5.1 had a vulnerability with the deniable file system), but version 6.0 fixed that.

Thanks, im a little too OTT with the whole security thing, i hope i can trust AES and T/C a little longer.

---

### Post by paddymurphy on 2009-07-21
> **mdebusk said:**
> [Read this and see if it gives you what you need.]("http://www.truecrypt.org/docs/administrator-privileges")
 
 
Hello all
 
I've only just installed ubuntu so please forgive if I appear very ignorant.
 
I have Ubuntu and Windows at home, and windows at work. I want to move files around the 3 computers on a USB stick, but keep sensitive files secure.
 
I started looking around and thought that Trucrypt might be the way to do it - but from what I read now on this page of the forum, it seems it is only possible if the powers that be at my workplace agree to instal Truecrypt (which just ain't going to happen).
 
I'd be grateful if someone could confirm that my understanding is correct.
 
If so, does anyone have another method that would work?
 
Many thanks everybody.

---

### Post by Rob_H on 2009-07-21
> **paddymurphy said:**
> I started looking around and thought that Trucrypt might be the way to do it - but from what I read now on this page of the forum, it seems it is only possible if the powers that be at my workplace agree to instal Truecrypt (which just ain't going to happen).

You can run TrueCrypt without installing it by putting a copy on a USB stick or other removable media. See the documentation for [Traveler Mode]("http://www.truecrypt.org/docs/?s=truecrypt-portable"). You will, however, need administrative privileges on the machines, since TrueCrypt uses a device driver.

> **juancarlospaco said:**
> *BTW Truecrypt its easy to hack nowadays...*

Spreading this kind of FUD without evidence is not helpful. If you have proof, post a link. But I suspect you're just trolling.

---

### Post by paddymurphy on 2009-07-21
> **Rob_H said:**
> You can run TrueCrypt without installing it by putting a copy on a USB stick or other removable media. See the documentation for [Traveler Mode]("http://www.truecrypt.org/docs/?s=truecrypt-portable"). You will, however, need administrative privileges on the machines, since TrueCrypt uses a device driver.



Spreading this kind of FUD without evidence is not helpful. If you have proof, post a link. But I suspect you're just trolling.


Many thanks for your reply. I think it boils down to the same thing though - without the active co-operation of my boss (which I won't get) then Truecrypt really isn't portable.

Thanks again.

---

### Post by RedSingularity on 2009-07-21
Here, follow [this](http://riosec.com/files/TrueCryptTraveler.swf) link.  You will need a windows computer but I did it and it works great.  Even on computers without admin rights.

---

### Post by paddymurphy on 2009-07-21
Ah! If you don't need Administrator rights then that looks like it's doable after all.

Many thanks indeed - I shall try it out!

---

