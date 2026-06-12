---
title: "md5sum.txt  xubuntu 13.10 32bit (or) (&amp;) ubuntu 13.10 32bit"
date: 2014-04-26
forum: Security
---

### Post by ali17 on 2014-04-26
Hi

please upload  "md5sum.txt "

The original version :   xubuntu 13.10 32bit (or) (&) ubuntu 13.10 32bit

Thank you

---

### Post by Bashing-om on 2014-04-26
ali17; Hi ! Welcome to the forum .


This ?
[http://releases.ubuntu.com/13.10/MD5SUMS](http://releases.ubuntu.com/13.10/MD5SUMS)
What you are seeking ?

Else, how about this :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[INDENT]My litle bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ali17 on 2014-04-26
> **Bashing-om said:**
> ali17; Hi ! Welcome to the forum .

Else, how about this :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)[INDENT]My litle bit[INDENT][INDENT][INDENT]to try and help
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


[SIZE=3]**Section :**[/SIZE]**Check the files on the CD**


[B]My File  (  "md5sum.txt" )  is incomplete
[/B]
** This File (  "md5sum.txt" )  will contain the following :**
----------------------------------------------------------------------------------------------
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg

3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
dc720c5427dbcf23016af4127509191b  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
af086195f98ccb1280542b039e3c8f63  ./preseed/xubuntu.seed
e46c8d65bf15e284a187ef2fb46521e0  ./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20110321-9_i386.deb
25b1f78d0a25fc231bb5ca2bf85bab38  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_i386.deb


5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm

------------------------------------------------------------------------------------------------

** please upload  "md5sum.txt "[COLOR=#ff0000] .[/COLOR]** (xubuntu desctop 13.10 32bit    or    ubuntu desctop 13.10  32bit)

---

### Post by Bashing-om on 2014-04-26
ali17; Hello, once more;

Does not appear I can do much to help.

> 
Section :Check the files on the CD -> My File ( "md5sum.txt" ) is incomplete

 I am at a loss if
a) you verified the .iso integrity
b) you "check disk for defects" in the liveDVD's boot options menu

As then the dvd is "complete".
Can you place into context what you are doing and what the end goal is ?
 I do not have access to the images (32 bit) and thus can not break out the requested files and do not know how to obtain said file without having that liveDVD to extract the file.

[INDENT]If I could I would
[INDENT][INDENT][INDENT]as I can not I wont [/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ali17 on 2014-04-27
Do you have access to [COLOR=#ff0000]"[/COLOR]xubuntu-13.10-desktop-i386.iso[COLOR=#ff0000]"[/COLOR] or [COLOR=#ff0000]"[/COLOR]ubuntu-13.10-desktop-i386.iso[COLOR=#ff0000]"[/COLOR] file [COLOR=#a52a2a]?[/COLOR]

Who has access ?

---

### Post by sudodus on 2014-04-29
The idea with the md5sums is to check that files are downloaded, copied, burned correctly. You find the md5sums of the iso files at

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

The two files you ask about have the following md5sums

```

99fddea7d86b29059c854968e3be38c3  xubuntu-13.10-desktop-i386.iso
d0508f909c2c71d96aeac5efb0329b33  ubuntu-13.10-desktop-i386.iso

```

Start a terminal window and run the command

```
md5sum xubuntu-13.10-desktop-i386.iso
```
and it should produce the output
```
99fddea7d86b29059c854968e3be38c3
```

and 
```

md5sum ubuntu-13.10-desktop-i386.iso
```
should produce the output
```
d0508f909c2c71d96aeac5efb0329b33
```

If the md5sums match, your download was good. The only way to change the md5sum is to download again (until it matches the entry in UbuntuHashes).

But maybe you have problems with something else? If the download was good and the install DVD/USB drive is corrupted, you need to burn or flash it again (burning with the slowest speed possible is a good idea). Often it is easier to succeed with a USB pendrive (compared to burning a CD or DVD). I think that those iso files are too big for CD.

I'm guessing now:

[FONT=courier new]**ubuntu-13.10-desktop-i386.iso**[/FONT] contains the following file [FONT=courier new]**md5sum.txt**[/FONT] at the root (viewed with ***file-roller***), so I guess you are looking for

```
/md5sum.txt
```

and I add it as an ***attached file*** with its own md5sum

```
5765805c23215de23f7775d84a79e140  md5sum.txt
```

---

### Post by ali17 on 2014-04-29
I have an iso file  ( 8015b79bda4f16a3c04d66ca8effa6)

 How can I change MD5 : OF 8015b79bda4f16a3c04d66ca8effa6   TO  8f731443c6a5166216adcd47bc5c82a6

---

### Post by Lars Noodén on 2014-04-29
The MD5 checksum is (nearly) unique to any given file.  To change the checksum, change the file.  It is virtually impossible to compute backwards from an existing checksum to make a matching file on normal hardware.  However, since it is becoming possible on advanced hardware, SHA256 is being recommended.  

What are you trying to do?

---

### Post by thnewguy on 2014-04-29
If you have an ISO file and the checksum is wrong, then the file is corrupted and you need to download it again. You will not be able to change the existing file to make the checksum match.

---

### Post by sudodus on 2014-04-29
Threads merged.

Please do not start more than one thread about the same problem, because it may cause double work for us who try to help!

---

### Post by ali17 on 2014-04-30
> **sudodus said:**
> Threads merged.

Please do not start more than one thread about the same problem, because it may cause double work for us who try to help!

Ok ;)

---

### Post by sudodus on 2014-04-30
*@ali17*,

Please tell us what you want to do, why you wanted this md5sum.txt, and why you haven't checked the one I uploaded (there are 0 views).

Are our replies telling you what you wanted to know?

---

### Post by ali17 on 2014-04-30
i have an "ubuntu 13.10 32bit.iso"(d0508f909c2c71d96aeac5efb0329b33) and "xubuntu 13.10 32bit.iso"(99fddea7d86b29059c854968e3be38c3)  (Original)

I would like to know :

is It  possible be infected Contents Ubuntu 13.10 i386.iso file (eg: .deb or... .)  by virus / trojan/keylogeer/... .
(md5  certainly will change. Eg : of 99fddea7d86b29059c854968e3be38c3 to 8f731443c6a5166216adcd47bc5c82a6 )&#1567; 

In this case: for Cheat :

A hacker can change the md5 file OF 8f731443c6a5166216adcd47bc5c82a6 TO 99fddea7d86b29059c854968e3be38c3 (While there are still infected file )

Is it possible to be infected file, but md5 is 99fddea7d86b29059c854968e3be38c3 &#1567;

---

### Post by sudodus on 2014-04-30
I see. I must reply yes, md5sum is primarily a checksum to make sure that the download was correct. But as pointed out by *Lars Noodén* in post #8, it is *possible* (but difficult) to 'fix' the md5sum. But if you download the iso file from a reliable web site, for example that of Canonical (Ubuntu's main web site)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

it is extremely unlikely that it is hacked.

If you need an extra secure linux distro, look at ***Tails***

[https://tails.boum.org/](https://tails.boum.org/)

which has an elevated security check for the download

[https://tails.boum.org/download/index.en.html#verify](https://tails.boum.org/download/index.en.html#verify)

---

### Post by sudodus on 2014-04-30
[http://askubuntu.com/questions/172947/what-are-the-differences-between-md5sum-and-sha256sum](http://askubuntu.com/questions/172947/what-are-the-differences-between-md5sum-and-sha256sum)

There is a brief explanation above, why sha256sum is better than md5sum. I can compute the ***sha256sum*** for you, and you will get the increased security with a 256-bit hash.

```

$ [COLOR=#0000ff]md5sum ubuntu-13.10-desktop-i386.iso[/COLOR]
d0508f909c2c71d96aeac5efb0329b33  ubuntu-13.10-desktop-i386.iso
$ [COLOR=#0000ff]sha256sum ubuntu-13.10-desktop-i386.iso[/COLOR]
a7f7fcb03e5323a3619b84218c935dd9e54a348ee6ebd55748d81886a3272171  ubuntu-13.10-desktop-i386.iso
$
```

But still, if security is important, consider using ***Tails***

---

### Post by ali17 on 2014-04-30
I have three demands :

[COLOR=#ff0000]**&#1777;)**[/COLOR]

How about SHA256&#1567; 
Impossible to change&#1567;

 SHA256 Stronger than MD5&#1567; 

&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;
[B][COLOR=#ff0000]&#1778;) [/COLOR]
[/B]
Please put out the following statement:


ls -l ubuntu-13.10-desktop-i386.iso 
ls -l xbuntu-13.10-desktop-i386.iso

i want to Check the CD

&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;
[COLOR=#ff0000]**&#1779;)**[/COLOR]

Now I use the ubuntu-13.10-desktop-i386 (i do not know my OS infected or not) 
I installed in  the flash 

  If my system(ubuntu-13.10) is infected and 

I download from the link [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso)

How can I ensure that my OS does not damage This file(ubuntu 14.4)

Because I want to install it(ubuntu 14.4) and be sure it is not infected

---

### Post by sudodus on 2014-04-30
> **ali17 said:**
> I have three demands :

[COLOR=#ff0000]**&#1777;)**[/COLOR]

How about SHA256&#1567; 
Impossible to change&#1567;

 SHA256 Stronger than MD5&#1567; 

SHA256 is much stronger than MD5 (not impossible, but there are easier methods to get information, see the attached cartoon)
> 
&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;
[B][COLOR=#ff0000]&#1778;) [/COLOR]
[/B]
Please put out the following statement:


ls -l ubuntu-13.10-desktop-i386.iso 
ls -l xbuntu-13.10-desktop-i386.iso

I have only the Ubuntu iso file:
```
$ ls -l ubuntu-13.10-desktop-i386.iso
-rw------- 1 sudodus sudodus 938475520 jan  2 19:28 ubuntu-13.10-desktop-i386.iso
```
> 
i want to Check the CD

&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;&#8722;
[COLOR=#ff0000]**&#1779;)**[/COLOR]

Now I use the ubuntu-13.10-desktop-i386 (i do not know my OS infected or not) 
I installed in  the flash 

  If my system(ubuntu-13.10) is infected and 

I download from the link [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso)

How can I ensure that my OS does not damage This file(ubuntu 14.4)

Because I want to install it(ubuntu 14.4) and be sure it is not infected

0. If your current system is infected, it is probably trying to send information about you to those who infected the system. I do not think that it will try to damage a downloaded iso file.

1. Use the md5sum from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) to check it

2. I have not downloaded Ubuntu 14.04 LTS, so I cannot easily get the sha256sum of it.

3. If you really need something more secure, again I would recommend ***Tails***

---

### Post by cariboo on 2014-04-30
I'd like to know what makes you think your system is infected, just because you installed flash?

---

