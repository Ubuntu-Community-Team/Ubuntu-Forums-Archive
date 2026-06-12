---
title: "Paragon NTFS for Linux 7.0 Public Beta Testing"
date: 2008-09-05
forum: The Cafe
---

### Post by Anatoly_Paragon on 2008-09-05
Dear Forum Visitors, 

For the past year [Paragon]("www.paragon-software.com") has been working on a new version of Paragon NTFS for Linux 7.0. NTFS for Linux 7.0 is a driver allowing Linux users to access (read and **write**) Microsoft NTFS file systems. With the new version, the driver has been significantly improved, and several bugs were fixed.

The product is almost ready for market release and we want to offer you the Public Beta version. This is the first time that we've offered beta testing for this driver. We do it because we want to make Paragon NTFS for Linux a useful tool for every Linux user -- that is why we need your opinion about it.

According to existing feedback, the main issue most users encounter when using our driver is with installation. So, if you choose to test the Beta version with us, please pay attention to the installation stage because it is important for us to make a driver that will support the most Linux distributions as possible.

What we expect from you:
1. Bug reports (though we hope that there won't be many). If you find a bug, describe with details how it can be reproduced by our developers. We need every detail, every step (even if it seems minor). Please specify your Linux distribution and Linux kernel version.

2. Usability issues. We want to make the product as easy to use as possible. Write us with your suggestions on what you think we can improve upon or what should be changed. Make your suggestions both detailed and reasonable so we can understand what your concerns are as well as determine if possible to implement. 

To download the public beta version, please fill out a short [web form]("http://www.paragon-software.com/home/ntfs-linux/betatesting.html").

In addition, you can review the “How to install” readme file [here]("http://www.paragon-software.com/export/sites/paragonsoftware.com/home/ntfs-linux/ReadMe.txt"). 

Our commitment to you:  We will read your feedback in this thread very carefully. Please excuse (in advance) any perceived lack of replies to your posts.  We won’t be able to reply to all of them, but we will do "summary" replies once or twice a week in this thread. 

PS. We value this forum's community members very much. That's why we selected you for our Public beta testing. In exchange for your help, we will be glad to provide the most active beta testers with NTFS for Linux Professional Edition free of charge.

Thank you in advance and best regards, 
Paragon NTFS for Linux team.

---

### Post by Steveway on 2008-09-05
30$ for something that we allready have with a truly free and open-source program? This sounds like Spam. Why should we buy your product and not use ntfs-3g, or even better not use NTFS at all?

---

### Post by Anatoly_Paragon on 2008-09-05
Dear Steveway,

Please note:
1. We are going to provide NTFS for Linux 7.0 Personal Edition for free (for non-commercial use only);
2. Our driver is much faster than NTFS-3g (write performance especially). You can check it.

Best regards,
Anatoly.

---

### Post by Steveway on 2008-09-06
Free in what sense? Free as in beer or free as in freedom?
You know, Software-freedom is a very important thing for most of us, what garuantee do we have that your software does not do anything harmful and will be supported and developed on in the future? We only have your word, and while I don't want to decrease the value of your word, that is not enough.
It's nice that we can have it for "free" and I'm positively suprised by your friendly answer but for people that decided on a free and open-source Operating-system it doen't really make sense to use a closed-source alternative of something that we allready got as a free and open-source variant.
PS: Also, are there any side-by-side comparisions to show the speed improvements of your driver against ntfs-3g backed up by numbers?

---

### Post by pcjunkie on 2008-09-06
Paragon. Why not improve on NTFS -3g? or make a windows ext* read / write?

Alot of people have to duel boot to windows because of games and office compatibility issues (TA M$). Going the other way was more imperative..

I like what you are doing, its just not needed. You can write open source and still sell M$ hacks..

---

### Post by jrusso2 on 2008-09-06
Why hassle the guy he is already offering the program free for non-commercial use. This is why commercial companies won't develop for Linux all they get is grief from the users.

---

### Post by Anatoly_Paragon on 2008-09-08
Dear Steveway,

Thanks for your questions.

Paragon NTFS for Linux 7.0 should be release as a closed-source (library) but free software. We have tested NTFS for Linux for different configurations (kernel versions 2.4.x or 2.6.x), and we can guarantee the absence of any file or volume corruption. We arrange this public beta testing to release bug-free, full-fledged, most-Linux compatible NTFS driver for the Linux community.

> it doen't really make sense to use a closed-source alternative of something that we allready got as a free and open-source variant.
We would like to release our driver with two main advantages: 
1. Easy to install and use driver;
2. High performance and stable driver.

> Also, are there any side-by-side comparisions to show the speed improvements of your driver against ntfs-3g backed up by numbers?
According to Iozone utility (IO Zone Benchmark Program), our write performance is several times higher that NTFS 3G has (2 – 9 times, it depends on file sizes).

Dear Pcjunkie,

> Why not improve on NTFS -3g? or make a windows ext* read / write?
NTFS-3g is a user space driver not a kernel space (as ours). Kernel space drivers have higher performance than user space ones. Please note, Paragon has already EXT2/3 FS drivers for Windows and is going to release for Mac OS X in 2 months.

Looking forward to hearing your feedback.
Thanks in advance.
Best regards,
Anatoly.

---

### Post by bingoUV on 2008-09-08
> **Steveway said:**
> Free in what sense? Free as in beer or free as in freedom?
You know, Software-freedom is a very important thing for most of us, what garuantee do we have that your software does not do anything harmful and will be supported and developed on in the future? 

Steveway,
    Freedom doesn't matter for those who choose to trust their data to an undocumented blob of a filesystem commonly known as NTFS. Nothing against its performance/stability etc. but it is not exactly the choice of freedom lovers.

    Having accepted slavery at the hands of NTFS, additional slavery from Paragon will not hurt much if the promised performance benefits materialize.

    The lack of free choices argument won't help as there are many varied advanced free and Free filesystems for linux/*nix.

---

### Post by szaka on 2008-09-08
Hi,

Evaluation report and comments from the NTFS-3G Team.

Registration was not possible because of an 'Registration failed' error. The parameters were mine: [email]szaka@ntfs-3g.org[/email], Szabolcs, Szakacsits, Hungary, English and accepted the terms. Using different parameters the registration succeeded. The problem is 100% reproducible and anybody is free to test with my provided data above (if it works then I'll get an email). *[UPDATE: Paragon fixed this problem: I started to get the test registration and it works for me too -- Szaka]*

Installation went ok.

When an NTFS volume was mounted with the Paragon driver then the kernel logged this message:
```

kernel: ufsd: module license 'Commertial product' taints kernel.

```
What this means is explained at [http://www.kernel.org/pub/linux/docs/lkml/#s1-18](http://www.kernel.org/pub/linux/docs/lkml/#s1-18) (Btw, Paragon should spell Commertial as Commercial.)

In other words, not only the potential backdoors, spywares, viruses are the real threat when the driver is installed but the softwares bugs which instabilize Ubuntu (system crashes, data corruption, not only on NTFS but Linux file systems as well). Moreover the above also means that whatever problem one will have with the system, **open source developers can not and will not help** the person because the system became "tainted" (unaudited, unchanged, unverified, untested, unreliable) and no reliability can be ensured in such circumstance by open source developers (we have no access to the code which causes the problems, so we can't help).

We tried to run some of our test suites listed at [http://ntfs-3g.org/quality.html#testmethods](http://ntfs-3g.org/quality.html#testmethods) but we have found that the Paragon 7.0 BETA driver is not in a state yet where it could be evaluated. 

For instance compilation of software packages fails with gcc error. Running compilebench randomly halts with "No such file error" (seems to be a race condition or NTFS corruption).

Using an image file, system log gets flooded with the below messages:
```

kernel: Buffer I/O error on device loop0, logical block 31298816
kernel: lost page write due to I/O error on loop0
kernel: Buffer I/O error on device loop0, logical block 31298832
kernel: lost page write due to I/O error on loop0
kernel: Buffer I/O error on device loop0, logical block 31298848
kernel: lost page write due to I/O error on loop0
kernel: Buffer I/O error on device loop0, logical block 31298864
kernel: lost page write due to I/O error on loop0
kernel: Buffer I/O error on device loop0, logical block 31298880
kernel: lost page write due to I/O error on loop0
kernel: Buffer I/O error on device loop0, logical block 31298896

```

Afterwards not even NTFS-3G could work. The most serious is that, the 2.6.26 kernel got so seriously corrupted that the system had to be rebooted. 

This basically could never happen with NTFS-3G because the non-performance critical functionality is executed in a protected memory space and the performance critical parts are shared with other file systems.

NTFS-3G is **open source** and **free for commercial and non-commercial use** both in the sense as beer and freedom. 

We are committed to give away our work, this is what our GPL license means. We can give it away for free because it enjoys the full support of over 200 distributions, like Ubuntu, Red Hat, Novell, Mandriva, Debian, and quite many committed, paid and volunteer open source developers ;-)

> **Anatoly_Paragon said:**
> 
According to Iozone utility (IO Zone Benchmark Program), our write performance is several times higher that NTFS 3G has (2 – 9 times, it depends on file sizes).

Let's compare the speeds when the Paragon driver can run the benchmarks, ok? It's easy to be fast when the driver trashes the system. You are comparing a currently unusable beta driver with a stable one ;-)

Performance is also a much more complex subject. 

Moreover the priority of NTFS-3G was and always will be **reliability** over performance.

[quote=Anatoly_Paragon]
NTFS-3g is a user space driver not a kernel space (as ours).[/b]
[/quote]
No. NTFS-3G is a hybrid space driver. The performance critical work is done purely in the kernel. Only those say the above who don't (want to) understand how FUSE works.
[quote=Anatoly_Paragon]
Kernel space drivers have higher performance than user space ones.
[/quote]
This is absolutely untrue. Performance is a factor of quite many things. Mostly it depends on the file system and implementation design and the quality of the implementation. 

Otherwise how would you explain that the current NTFS-3G driver in development performs much better than all stable kernel drivers (ext3, xfs, reiserfs)? [http://lkml.org/lkml/2008/8/23/51](http://lkml.org/lkml/2008/8/23/51)

Of course Paragon style binary-only kernel drivers have several other disadvantages besides the above ones (losing the support of open source developers, questionable security and reliability, etc), for instance any time Ubuntu updates/upgrades the kernel, the Paragon driver can get broken. It may not function or may start to corrupt data, or even the Linux partitions (kernel corruptions). 

Please also note when these happen you will not get help from open source developers since you're "tainted". On the other hand, Ubuntu and NTFS-3G closely cooperate for almost two years to provide reliable read/write NTFS support to Ubuntu users.

Best regards, Szaka

---

### Post by szaka on 2008-09-08
> **bingoUV said:**
>     Freedom doesn't matter for those who choose to trust their data to an undocumented blob of a filesystem commonly known as NTFS.
The open source Linux community has reverse engineered and documented the NTFS format in the last 13 years. Quite probably this is the reason Paragon could also develop a commercial, closed-source NTFS driver ;-)

If you would like to ask anything about NTFS please feel free to do so, we'll be glad to reply you.

Regards,  Szaka

---

### Post by bingoUV on 2008-09-08
> **szaka said:**
> The open source Linux community has reverse engineered and documented the NTFS format in the last 13 years. Quite probably this is the reason Paragon could also develop a commercial, closed-source NTFS driver ;-)

If you would like to ask anything about NTFS please feel free to do so, we'll be glad to reply you.

Regards,  Szaka

I was wondering in amusement; whether Paragon or Microsoft will ever have their lead developers answer end user questions for free. Instead of a politically correct, lawyer filtered answer to legitimate user concerns; but I digress.

1. Do we support alternate data streams? 

2. In-built compression/encryption? Though I am not sure it is in-built in NTFS or there is a utility in windows that works close to NTFS to achieve these ends.

These are the features I was most interested in when someone described NTFS to me.

Your lkml link was so interesting that I might do a performance test myself,  involving the mount options I typically use.

EDIT: Sorry, I digressed too much. More interesting in this context is the question that:
   Isn't it trivial for microsoft to release a patch to Vista and break ntfs-3g seriously without breaking backward compatibility with XP, and releases of Vista before this patch?

---

### Post by Steveway on 2008-09-09
> **szaka said:**
> Hi,

<snip>

Best regards, Szaka

That was pretty exactly what I wanted to hear. If I would need to use a ntfs-driver to access NTFS-partitions then I would certainly choose ntfs-3g (I'm Linux-only so I don't need one, but my point stays.).
Appereantly it seems to be the more reasonable choice.
BTW: Even though you said that your driver would be free for personal use, your website still says otherwise and wants 30$ for the personal version.

---

### Post by szaka on 2008-09-09
[QUOTE=bingoUV]1. Do we support alternate data streams? 
[/quote]
Yes, NTFS-3G supports streams if the "streams_interface=windows" mount option is used. This will be enabled by default in the future.

[QUOTE=bingoUV]
2. In-built compression/encryption? Though I am not sure it is in-built in NTFS or there is a utility in windows that works close to NTFS to achieve these ends.
[/quote]
NTFS can do transparent/built-in compression/encryption. We know how it works and have code for it. At the moment the stable release includes read-only support for transparent compression, and the other features will be included as well. It wasn't often requested, so it wasn't a high priority for us.

[QUOTE=bingoUV]
Your lkml link was so interesting that I might do a performance test myself,  involving the mount options I typically use.
[/quote]
Your 32/64-bit performance tests were also very instructive! :-)

[QUOTE=bingoUV]
EDIT: Sorry, I digressed too much. More interesting in this context is the question that:
   Isn't it trivial for microsoft to release a patch to Vista and break ntfs-3g seriously without breaking backward compatibility with XP, and releases of Vista before this patch?[/QUOTE]
It's not trivial. The on-disk file system format is bound to an NTFS version number stored on the disk. All incompatible changes modifies the NTFS version number what the NTFS-3G driver would detect and refuse to mount the volume until the open source development community checks the scenario and explicitly adds compatibility support.

---

### Post by Joeb454 on 2008-09-09
Moved to Community Cafe

---

### Post by Polygon on 2008-09-09
im curious on why you even bothered to take the time to code and market a linux ntfs driver when...ntfs-3g has been around for quite a long time. and not to mention from the above posts, ntfs-3g is currently better.....

seriously, your talents and time could be better spent improving ntfs-3g. but that is just my opinion

---

### Post by Scruffynerf on 2008-09-10
> **Anatoly_Paragon said:**
> 
Please note, Paragon has already EXT2/3 FS drivers for Windows


Linky please? Your claims are not being backed up by your website.

---

### Post by gn2 on 2008-09-10
> Beta Test Agreement
between
Paragon Software
15615 Alton Parkway, Suite 450
Irvine, CA 92618
and
You, as user
§ 1 Scope of this Agreement

The Software-Product accompanying this Agreement as a pre-release copy and all affiliated materials, including documentation and information (collectively the "Product"), is copyrighted. Scope of this agreement is the licensing (not selling) of the "Product" to You, as the 'user' (either an individual or an entity).
PARAGON reserves all rights not expressly granted.

§ 2 Extent of Use / User Duties

1. PARAGON grants the User a simple, non-exclusive and temporally restricted right to use the "Product" solely for the purpose of testing. Your rights in the "Product" are limited to those expressly granted in this agreement. In particular, PARAGON reserves all rights of reproduction, distribution and publication.

2. The license is restricted to the respective version acquired, i.e. new versions must be re-licensed. PARAGON is not obligated to provide maintenance, technical support or updates to the User. In no event shall PARAGON be obligated to provide the User a copy of the commercial release version of the "Product"". PARAGON is not obligated to make the "Product"" commercially available.

3. The license is restricted to the object code of the "Product". PARAGON is not obliged to provide the user with the source code. The user may not reverse engineer, decompile, dis- and/or reassemble, or change, alter, modify the "Product"; or create derivative works, enhancements, extensions or add-ons to/of any part of the "Product".

4. This license entitles the user to install and use the "Product" on only one single location (only one computer normally). If this location is part of a multi-user-system, or if the "Product" is to be designed for getting installed on a server centrally (and to be used in a network system), the license is valid for all authorized users of the related system.

5. The "Product" may not be used per data transmission. The transfer in physical form (i.e. stored on portable or other physical media) from one computer to another is only permitted if the "Product" is not used on more than one computer at the same time. If the "product" is to be used in a network system, § 3 cipher 4, S.2 applies accordingly.

6. A transfer of the "Product" or any portion of it to third parties under retention of any usage possibilities is excluded, unless PARAGON permits such a transfer in a written agreement with the user. The user is obliged to prevent unauthorized access to the "Product" by third parties through the implementation of appropriate precautionary measures. The original storage media delivered and any backups are to be stored in a location protected against unauthorized access by a third party. The User is to be obliged to advise potential employees to respect copyright and the terms of this agreement.

7. The User shall not rent, lease, sell, sublicense, assign any portion of the "Product" or the "Product" itself.

8. Duplication of the "Product" is prohibited, provided that the duplication is not necessary for the normal operation of the "Product". Duplication is considered necessary when it occurs during the installation of the "Product" to a hard disk from the accompanying media and when downloading or printing-out data from the running application for exclusively personal use. In addition, the User may create a backup copy when such action is necessary to ensure future use of the "Product" in the contractually implied, exclusively personal manner.

9. Translation of the "Product" is prohibited.

10. Any copy protection system, copyright-notice, or registration-number built into the "Product", or any other characteristics that serve to identify the program, are not to be removed by the User.

11. The User agrees to provide reasonable feedback to PARAGON, particularly to report any and all problems and test results relating to the "Product". All this information may be used by PARAGON for its own purpose. Due to the nature of the development work, PARAGON provides no assurance that any specific errors or discrepancies in the "product" will be corrected.

§ 3 Warranty / Claims for Damages

1. The User is aware of the fact that Software can generally not be produced completely devoid of faults. PARAGON is only liable for defects in the "Product" that decrease significantly it's value or suitability for the contractually intended use. The warranty refers only to material defects of contractual "Product"s delivered by PARAGON. PARAGON is liable without limitation for defects in title.

2. PARAGON is liable for damages arising from the injury of life, body or health that are based on a negligent breach of duty on the part of PARAGON or an intentional or negligent breach of duty by a legal representative or a vicarious agent of PARAGON; as well as for other damages that are based on an intentional or grossly negligent breach of duty on the part of PARAGON or on an intentional or grossly negligent breach of duty by a legal representative or a vicarious agent of PARAGON; yet, PARAGON is fully liable for damages arising from a breach of essential (but only typical, predictable contractual obligations). Further liability for damages is excluded, no matter on which legal grounds claims are based. Liability for damages resulting from a failure to meet explicitly granted quality guarantees or such liability based on the German Product Liability Act remains unaffected.

3. It is up to the User to choose an appropriate usage location for the "Product" and to determine the type of hardware/ computer system to be used. PARAGON offers no guarantees in this matter.

§ 4 Term of Agreement

1. The term of this Agreement shall commence on the date of User's receipt of the Software and will continue for 2 months. A continue of the term may be granted by PARAGON on written request.

2. Aside from the termination of the right of use by reason of time lapse, this Agreement will terminate without notice upon the commercial release of the "Product".

3. Furthermore, the rights conferred to the User under this agreement terminate without notice from PARAGON if the User fails to comply with any term(s) of this agreement.

4. In all cases of termination, the User is obliged to give all media containing "Product" and Documentation back to PARAGON and to remove the "Product" and all files built with it's help from the hard drive in a way that guarantees non-recoverability and, upon demand by PARAGON, to confirm the complete removal through a declaration in lieu of oath.
In either case User shall confirm to PARAGON the deletion of the "Product" in written by ideally using the corresponding form of PARAGON.

§ 5 Additional terms concerning Windows PE

If the "Product" the User has licensed includes Windows PE, the following terms and conditions will accumulative become valid in addition to the other terms:

1. "Windows PE" is Windows "Product" licensed from Microsoft Corporation and/or Microsoft Affiliate(s) and is provided "as is".

2. "Windows PE" contains a security feature that will cause the computer system to reboot without prior notification to the end-user after 24 hours of continuous use.

3. Microsoft or its affiliates are not liable for the "Product" including "Windows PE" licensed by PARAGON. Any support for the "Product" will be provided by PARAGON.

4. To avoid any Misapprehensions, the following is to be clarified:
The license of the "Product" including "Windows PE" is limited to use it as a boot, diagnostic, disaster recovery, setup, restoration, emergency services, installation, test and/ or configuration utilities program, and not for use as a general purpose operating system or as a substitute for a fully functional version of any operating system "Product".

5. Windows® is a registered trademark of Microsoft Corporation.

(6. "Windows PE" is subject to U.S /European Union export jurisdiction.)

§ 6 Confidentiality

The User binds itself not to circulate and to keep severely secret any kind of information, particularly with regard to technical, financial, organisational aspects, of which he or his organs, auxiliary persons, representatives, or other assigned persons get aware in coherence with this contract and/or during collaboration. In case of doubts the User binds itself to confer with PARAGON.

The User is obliged to bind organs, assistants, auxiliary persons, representatives or other persons who could get in contact to information in the same way.

§ 7 Further Terms

1. This agreement may not be modified, varied or altered, unless agreed upon in writing by both contracting parties.

2. This agreement is governed by and interpreted in accordance with the laws of Germany.

3. Concerning contracts with merchants, commercial companies, public legal entities and legal separate estates under public law, as well as in those cases where the customer, who is not a consumer, does not have his/it's general jurisdiction within Germany, the court located in M?llheim, Germany shall have jurisdiction to hear the disputes arising under this agreement.

4. This agreement, together with the general terms and conditions of PARAGON, comprises the entire agreement between PARAGON and the User.

5. If any current or future provision of this agreement is held to be invalid, illegal or unenforceable, the validity, legality and enforceability of the remaining provisions of this agreement will not be affected.

Offeror Identification:
Paragon Software
15615 Alton Parkway, Suite 450
Irvine, CA 92618
Telephone: 1-888-347-5462 (1-888-DISK-IMAGE);
[www.paragon-software.com](www.paragon-software.com)

^No thanks, I'll stick with open source.

But Anatoly_Paragon, if you want me to beta-test your commercial product, PM me so that we can negotiate the fee which I will charge you for my time and effort.

---

### Post by kpkeerthi on 2008-09-10
I will not use this product, I neither have a need for it. But I'm glad that linux gets one more commercial product offering, which is what we all should appreciate.

---

### Post by awakatanka on 2008-09-10
I would say thanks for people that are willing to make commercial applications and drivers for linux. But don't need it because NTFS-3G does everything i need. But i can see a need for this in companies that need more and support. so good work.

---

### Post by Canis familiaris on 2008-09-10
> **gn2 said:**
> 
But Anatoly_Paragon, if you want me to beta-test your commercial product, PM me so that we can negotiate the fee which I will charge you for my time and effort.
lol

---

### Post by mips on 2008-09-10
Everything has a place. The responses here seem out of line and like typical linux zealotry to me.

If the product is in fact better then I can see a market for it, especially in a commercial environment.

Linux users always complain about a lack of commercial apps but when it comes around it is attacked.

Shame on you. We live in a free society, we can all decide what it is we want and don't want. (And what we are willing to pay for.)

---

### Post by NTolerance on 2008-09-10
> **jrusso2 said:**
> Why hassle the guy he is already offering the program free for non-commercial use. This is why commercial companies won't develop for Linux all they get is grief from the users.

Seriously.  The Linux community really needs to back off on the hostility and welcome any and all new software development.  Don't like the license?  Don't buy it but also don't discourage its development.

---

### Post by Polygon on 2008-09-10
> **mips said:**
> Everything has a place. The responses here seem out of line and like typical linux zealotry to me.

If the product is in fact better then I can see a market for it, especially in a commercial environment.

Linux users always complain about a lack of commercial apps but when it comes around it is attacked.

Shame on you. We live in a free society, we can all decide what it is we want and don't want. (And what we are willing to pay for.)

it costs 30 dollars, it doesn't even work, and there is a fully functional (im not aware of any limitations) open source driver, ntfs-3g. Id be happy to pay for commercial programs if there is a niche for them. Like gimp doesnt compare to adobe photoshop, and nexiuz doesnt compare to team fortress 2 (a video game). But expecting people or companies to pay for a program when a free one exists just seems silly to me.

---

### Post by Anatoly_Paragon on 2008-09-11
Dear Szaka,

Thank you for your feedback.

Please find my answers below.

1. The registration procedure was updated. Thanks.

2. The "kernel: ufsd: module license 'Commertial product' taints kernel." message means that you have used a source-closed software. This message will be displayed when using ANY source-closed driver.

3. > (we have no access to the code which causes the problems, so we can't help).
Paragon constantly develops and supports its NTFS drivers. We will be glad to fix any incompatibility or performance issue immediately.

4. Thank you for paying our attention to the "Compilebench" utility. We will fix any issue when testing our driver with this utility before our official release. 

5. We believe NTFS-3G is a great piece of software and we understand its priorities and targets. Paragon just would like to direct all its experience in files system drivers and provide the Linux community with alternative kernel space solution. We believe that we can combine high performance with high stability and release easy-to-install and use NTFS driver for free.


Dear bingoUV,

Paragon supports alternate data streams and compression (full read and write). What do you mean by encryption support? Paragon may copy an encrypted file (from source) to EXT2/3 FS, NTFS, FAT and then copy it back (to source) keeping encryption capabilities intact (use cpntfs utility for this purpose).

Dear Steveway,

We are going to release NTFS for Linux 7.0, after public beta testing, for free. But before releasing we would like to make sure our driver supports the most commonly used Linux distributions without any issues.

Dear Polygon,

Paragon has been developing our Universal File System Technology (UFSD) technology for the last 6 years.  UFSD includes NTFS driver for Linux, Mac OSX, DOS, ... as well as EXT2/3 driver for Windows, Mac OS X,.. Most Paragon products use the UFSD technology that is why we have to constantly improve this technology.

Dear Scruffynerf,

The EXT2/3 FS drivers for Windows are implemented in our backup/restore solutions. If this driver can be interested in the Linux Community we can separate this driver as a single driver/application. 

Dear mips and NTolerance,

Thank you!


Polygon,

> it costs 30 dollars
We will make it free of charge (Personal Edition).

> it doesn't even work
Really? If you find a bug, just let us know and we will fix it immediately.

> But expecting people or companies to pay for a program when a free one exists just seems silly to me
Paragon has a great experience in this field. We provide companies with customization and maintenance services. They are not silly.

Looking forward to hearing your test results.
Best regards,
Anatoly.

---

### Post by bingoUV on 2008-09-11
Thank you Anatoly.

> **Anatoly_Paragon said:**
> 
2. The "kernel: ufsd: module license 'Commertial product' taints kernel." message means that you have used a source-closed software. This message will be displayed when using ANY source-closed driver.


Not if you fix the spelling. It is 'Commercial', not 'Commertial'. Though your name as well as your language in other posts suggests that you are not a native English speaker, nor is this company based in English speaking locality. Correct me if I am wrong. Though it makes no difference to the quality of your software.

NTFS has an in-built encryption support. It is not that you encrypt a file using some other tool, get an encrypted file and store this encrypted file in the file system. With NTFS, you create a file, and ask NTFS to store it in an encrypted form. During mount, maybe it will ask you for the decryption key, I am not sure. But when the user reads the file after mount, it would be presented as non-encrypted file. This is a feature in NTFS, which protects against loss of data through stolen hard disk. I was asking Szaka whether NTFS-3g supports this. Please let us know whether Paragon's driver supports this feature i.e. in windows if I store a file encrypted using this NTFS feature, and if I want to mount this in linux using Paragon's driver; will I be able to read the decrypted file after supplying the key somehow.

Similarly for compression, though a key would not be required.

---

### Post by xchaotic on 2008-09-11
> **bingoUV said:**
> 
1. Do we support alternate data streams? 

2. In-built compression/encryption? Though I am not sure it is in-built in NTFS or there is a utility in windows that works close to NTFS to achieve these ends.

3.   Isn't it trivial for microsoft to release a patch to Vista and break ntfs-3g seriously without breaking backward compatibility with XP, and releases of Vista before this patch?

1. The only popular use of ADS is for rootkits, trojan horses and all sorts of malware. Not exactly very important to keep that.

2. In my view compression doesn't belong at fs level, some files do not compress at all or are compressed already (xvid, mp3), storage is cheap, so why bother? and if you bother, it's best done higher in the layer cake.

3. Microsoft have to support a huge variety of systems on OSes from Win2000 to Vista, they have enough bugfixing already, without introducing problems on purpose.

---

### Post by toupeiro on 2008-09-11
Sounds interesting.  I've never really had any problems, performance or otherwise, with ntfs-3g, but I'm always game to test something new.

If you really want to SELL something, NTFS is probably not your sweetspot.  SMBv2, however......

---

### Post by bingoUV on 2008-09-11
> **xchaotic said:**
> 1. The only popular use of ADS is for rootkits, trojan horses and all sorts of malware. Not exactly very important to keep that.

2. In my view compression doesn't belong at fs level, some files do not compress at all or are compressed already (xvid, mp3), storage is cheap, so why bother? and if you bother, it's best done higher in the layer cake.


Agree totally with point 2. Don't have much experience with windows to comment about point 1, though I heard some popular software depends on alternate data streams.

But let us not kid ourselves. If somebody is using NTFS-3g, it is not for the whizz-bang features of NTFS, incredible stability or any such nonsense. It is plainly because of compatibility with Microsoft's implementation of NTFS. So that you write to the filesystem using windows, mount the same in *nix and read the data correctly. Also, write in *nix, and read in windows.

Which is why, supporting all these features is important. Otherwise, a windows application might compress the data using NTFS's compression mechanism and we are stuck with data unreadable in *nix world. Or it pushes stuff in an ADS and we are unable to find it anyhow in *nix world.

Compatibility with Microsoft's implementation of NTFS is the whole,sole,singular reason for existence of NTFS-3g. Otherwise, there are numerous equally good/better ways of doing filesystems that are not born and brought up in Redmond.

EDIT: Actually, if ADS is used by malware, it is great. Malware will most likely be platform specific, unportable code which will unable to do harm in *nix. NTFS-3g will become a great tool in analysis of malware if it supports ADS (which it does).

---

### Post by zolookas on 2008-09-11
> 
Please note:
1. We are going to provide NTFS for Linux 7.0 Personal Edition for free (for non-commercial use only);
2. Our driver is much faster than NTFS-3g (write performance especially). You can check it.1. ntfs-3g is free in both means, i can use it where i want.
2. ntfs-3g performance is sufficient, i have not experienced any problems with it.

> We would like to release our driver with two main advantages: 
1. Easy to install and use driver;
2. High performance and stable driver.1. ntfs-3g is preinstalled on many distributions including ubuntu
2. According to [szaka]("http://ubuntuforums.org/member.php?u=52867") it is not so stable after all. I have been using paragon ntfs v5 when ntfs-3g was not released and it worked pretty well, except one time one movie disappeared from folder in front of my eyes (i was watching another movie from the same folder at the moment), but after using scandisk, that file was recovered.

Maybe a bit offtopic: Also you can get a free ext2 (works with ext3 since it is backwards compatible) driver for windows at [http://www.fs-driver.org/](http://www.fs-driver.org/) No need to buy any paragon product.

By the way, Paragon, I've just wanted to say that your Partition Manager is the tool that works great when others refuse to.

> **mips said:**
> Everything has a place. The responses here seem out of line and like typical linux zealotry to me.

If the product is in fact better then I can see a market for it, especially in a commercial environment.

Linux users always complain about a lack of commercial apps but when it comes around it is attacked.

Shame on you. We live in a free society, we can all decide what it is we want and don't want. (And what we are willing to pay for.)

Maybe it is better if you want commercial support, but we have even better and free alternative available so it does not make very much sense if any.

---

### Post by Jotnar on 2009-01-10
Lets lay off the Paragon bashing alright?

Paragon was selling reliable NTFS write capabilities for Linux before NTFS-3G even existed.  Your choices at the time were the buggy as hell kernel driver or Paragon's software.  Its dissapointing to see so many people get bent out of shape when a company that has been selling software for Linux longer than most want people to help make their software better.  Seriously, why would any company want to bother with the "Community" when this is the response they get?

I'll give their software a try though I'll probably stick with NTFS-3G.  Isn't it worth an hour or two of your time to test software from a company that has been selling usefull software for Linux for years?

Cheers

---

### Post by Polygon on 2009-01-10
i WOULD (and a lot of people would be too) be interested in a actually FUNCTIONAL ext3 driver for windows, rather then the crappy old ext2 one that is out there. so yes, please split off that ext3 driver thing from your backup program

---

