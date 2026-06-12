---
title: "Gpg newbie - basic questions"
date: 2014-12-14
forum: Security
---

### Post by anon_private on 2014-12-14
[INDENT] 					 					Hi,

I use Kubuntu and have gpg installed as a default program.

First point. What is the difference between pgp and gpg?

I have downloaded a programme from a website and the page talks of using keys to validate the program.

Second point. Am I correct in assuming that the key must be imported  into gpg before a validation can take place. Can validations be done 'on  the fly'?

I am wondering how validations can help.

Is it not possible to put a programme on a website, and place a key  there that will fit, and the user (downloader) will note consistency on  analysis. As for downloading keys, could someone not upload a key to a  server that will show consistence on using gpg when the program itself  may be problematic?

Point three. Should keys be used that are published a website, or only those available via servers?

No doubt, I will be back

Thanks

Ps. Is there a good forum for gpg discussions 				[/INDENT]

---

### Post by kevdog on 2014-12-15
GPG or specifically OpenGPG is the open source version which Werner Koch I believe maintains.  PGP is a closed-source project.  Mostly in linux you are going to utilize GPG.

Yes if a program is publishing their public key on the internet, I believe you need to import this public key onto your keyring first.  This is one source of validation -- mostly a trust validation that the source of the program does not change through a MITM (man in the middle attack).  SHA-1 and md5 checksums are another source of validation to test for file corruption using file hashes

Not sure about the last set up points.

---

### Post by agillator on 2014-12-15
PGP is the original created by Zimmerman, is not open source and is copyrighted. Here's the story as I remember it. Some years ago PGP was only available for purchase/license. The government debated what to do about his encryption system, whether to try to outlaw its use, require users to file their private keys with them, etc., etc., because they were truly worried about not being able to read whatever if they chose to. He responded by making it free to use for personal, non-commercial purposes. For commercial use you still had to pay. Obviously the genie, once out of the bottle, cannot be forced back in. Somewhere along the line Gnu PG (gpg) was developed as an open source system mostly compatible with PGP. Of course it is copyrighted also with the 'copyleft' copyright which allows anyone to use it under certain very liberal conditions. I do not know the current status of PGP, although I think it is still supported and developed. GnuPG is obviously alive and well.

As to 'validation'. The theory behind public key encryption (PGP and/or GPG) is that anything encrypted with one key can ONLY be decrypted by the other key. The keys can also be used to sign files, which means one key is used to calculate a hash of the contents of the file. The other key is the ONLY one that can check that hash against the file to make sure the file has not been changed since it was signed and that it was signed by the person claiming to have signed it.

A person keeps one of the two keys private, very private. The other key can be distributed to the world. In fact, there are public key repositories that many send their public keys to so people can use them. I believe MIT has one of the major repositories. Now the security rests on 'trust'. You only rely on keys you trust. For example your lifelong friend and confidant hands you a disk and says 'Here, this is my public key.' You can be pretty sure it is his public key and he is who he says he is because you personally know him. On the other hand, a man identifying himself as John Doe whom you have never seen before hands you a disk and says 'Here, this is my public key", are you going to believe (trust) him?

In a nutshell that is the system. So, to 'validate' a file which is digitally signed you get the public key of the person and check the signature. Of course there is a problem. How do you know you can trust the key? That is up to you. Many people have other people sign their keys. If someone you know and trust has signed the key, saying I know this person and trust him, you have something to go on. So now you develop a chain of signatures on a key.

There are organizations that issue certificates used to identify people and organizations. Normally those come into play when you use https to view a web site. They are as trustworthy as the organization issuing the certificate and the thoroughness of the identity verification. Again the matter of trust. Some can be trusted, some can't. Which are which? That is up to you. I suppose a certificate could be used to help in the key verification process, but again that is really up to you.

No black and white answers to your questions, I'm afraid. But that is the system. Yes, a nasty person can masquerade as someone else, use their own key to sign or encrypt something and try to fool people. Those who trust him will be fooled, those who don't will not be fooled. You keep the private key private because without that Mr. Nasty cannot appear to be you, he can only hope someone believes him so his public key will work. If he claims to be you but the other person has your REAL public key, the impersonation fails miserably.

Does that help?

---

### Post by sudodus on 2014-12-15
> **anon_private said:**
> ...
[INDENT] Ps. Is there a good forum for gpg discussions                 
[/INDENT]


This Ubuntu Security Forum should be OK :-)

You can probably find more specialized forums via the internet.

You can also find tutorials how to use gpg. And finally, the manual contains a lot ```
man gpg
```

---

### Post by anon_private on 2014-12-15
> **agillator said:**
> PGP is the original created by Zimmerman, is not open source and is copyrighted. Here's the story as I remember it. Some years ago PGP was only available for purchase/license. The government debated what to do about his encryption system, whether to try to outlaw its use, require users to file their private keys with them, etc., etc., because they were truly worried about not being able to read whatever if they chose to. He responded by making it free to use for personal, non-commercial purposes. For commercial use you still had to pay. Obviously the genie, once out of the bottle, cannot be forced back in. Somewhere along the line Gnu PG (gpg) was developed as an open source system mostly compatible with PGP. Of course it is copyrighted also with the 'copyleft' copyright which allows anyone to use it under certain very liberal conditions. I do not know the current status of PGP, although I think it is still supported and developed. GnuPG is obviously alive and well.

As to 'validation'. The theory behind public key encryption (PGP and/or GPG) is that anything encrypted with one key can ONLY be decrypted by the other key. The keys can also be used to sign files, which means one key is used to calculate a hash of the contents of the file. The other key is the ONLY one that can check that hash against the file to make sure the file has not been changed since it was signed and that it was signed by the person claiming to have signed it.

A person keeps one of the two keys private, very private. The other key can be distributed to the world. In fact, there are public key repositories that many send their public keys to so people can use them. I believe MIT has one of the major repositories. Now the security rests on 'trust'. You only rely on keys you trust. For example your lifelong friend and confidant hands you a disk and says 'Here, this is my public key.' You can be pretty sure it is his public key and he is who he says he is because you personally know him. On the other hand, a man identifying himself as John Doe whom you have never seen before hands you a disk and says 'Here, this is my public key", are you going to believe (trust) him?

In a nutshell that is the system. So, to 'validate' a file which is digitally signed you get the public key of the person and check the signature. Of course there is a problem. How do you know you can trust the key? That is up to you. Many people have other people sign their keys. If someone you know and trust has signed the key, saying I know this person and trust him, you have something to go on. So now you develop a chain of signatures on a key.

There are organizations that issue certificates used to identify people and organizations. Normally those come into play when you use https to view a web site. They are as trustworthy as the organization issuing the certificate and the thoroughness of the identity verification. Again the matter of trust. Some can be trusted, some can't. Which are which? That is up to you. I suppose a certificate could be used to help in the key verification process, but again that is really up to you.

No black and white answers to your questions, I'm afraid. But that is the system. Yes, a nasty person can masquerade as someone else, use their own key to sign or encrypt something and try to fool people. Those who trust him will be fooled, those who don't will not be fooled. You keep the private key private because without that Mr. Nasty cannot appear to be you, he can only hope someone believes him so his public key will work. If he claims to be you but the other person has your REAL public key, the impersonation fails miserably.

Does that help?

Thank you for the very detailed answer, yes, it does help. The system is certainly not fool proof, but it helps.

I am looking at a site at the moment where hashes are given for programs (different versions of the same programme). This site gives SHA256, SHA1, MD5 (evidently not secure), a finger print for the programme, and a pgp signature.

My question: Why give a number of hashes. Is one preferred? When he states md5 is not secure, what does that mean.

Thanks again

> **kevdog said:**
> GPG or specifically OpenGPG is the open source version which Werner Koch I believe maintains.  PGP is a closed-source project.  Mostly in linux you are going to utilize GPG.

Yes if a program is publishing their public key on the internet, I believe you need to import this public key onto your keyring first.  This is one source of validation -- mostly a trust validation that the source of the program does not change through a MITM (man in the middle attack).  SHA-1 and md5 checksums are another source of validation to test for file corruption using file hashes

Not sure about the last set up points.

Thank you

> **sudodus said:**
> This Ubuntu Security Forum should be OK :-)

You can probably find more specialized forums via the internet.

You can also find tutorials how to use gpg. And finally, the manual contains a lot ```
man gpg
```

Thank you

Couple of points not covered.

Second point. Am I correct in assuming that the key must be imported   into gpg before a validation can take place. Can validations be done 'on   the fly'?


Point three. Should keys be used that are published on a website, or only those available via servers?

---

### Post by sudodus on 2014-12-15
The main purpose of md5sum is to check that the download was good, that an iso file is transferred correctly (that there was no error in the transfer via the internet). This is enough for most people and purposes. But it does not provide a strong signature that there is no manupulatation of the content. Longer checksum strings provide higher security.

The security level of gpg signature is higher than that of standard checksums, so for example Tails provides gpg for you to check that the download was correct (and not tampered with by a man-in-the-middle attack). See this link

[https://tails.boum.org/download/index.en.html](https://tails.boum.org/download/index.en.html)

> **anon_private said:**
> Couple of points not covered.

Second point. Am I correct in assuming that the key must be imported   into gpg before a validation can take place. Can validations be done 'on   the fly'?


Some systems do these things automatically (the public key will be used to check the signature), for example when you update and upgrade the Ubuntu flavour operating systems.
> 
Point three. Should keys be used that are published on a website, or only those available via servers?

It is all about trust. Do you trust the website, server, the people running the service? (The intent of those people and also their skill to keep attackers out of their systems.)

---

