---
title: "what to use now truecrypt is insecure?"
date: 2016-04-09
forum: Security
---

### Post by jebi on 2016-04-09
hi

I used to use truecrypt, i want to use a similar program, one where i could unmount and require as password to re-mount, preferably not the admin password. i want to encrypt everything, the filesystem, home folders and a non system partition as well.  but i really need a interface GUI i am too slow a typer and noob to linux so a GUI is important to me...

I have heard of LUKs? also aes crypt and dm-crypt are these secure and uncrackable do they have a GUI?

Is there any better programs out there?

Also need like an idiots guide to set them up as well

many thx

freebo

---

### Post by SchnappiJedi on 2016-04-09
Still trust and use TrueCrypt. Audit showed no major issues.

[https://veracrypt.codeplex.com/](https://veracrypt.codeplex.com/) - VeraCrypt (based on TrueCrypt - Not audited)
[https://www.ciphershed.org/](https://www.ciphershed.org/) - CipherShed (rebranded TrueCrypt fixing a few driver permission errors)

---

### Post by mikodo on 2016-04-14
Zulucrypt 

[https://mhogomchungu.github.io/zuluCrypt/](https://mhogomchungu.github.io/zuluCrypt/)

[http://askubuntu.com/questions/483361/how-to-install-zulucrypt-in-ubuntu](http://askubuntu.com/questions/483361/how-to-install-zulucrypt-in-ubuntu)

[https://launchpad.net/~hda-me/+archive/ubuntu/zulucrypt](https://launchpad.net/~hda-me/+archive/ubuntu/zulucrypt)

---

### Post by ptn107 on 2016-04-14
I use veracrypt (good suggestion above).

[https://veracrypt.codeplex.com/](https://veracrypt.codeplex.com/)

directions to compile the source here: [readme]("https://veracrypt.codeplex.com/SourceControl/latest#README.md")

---

### Post by s0urCr34m on 2016-04-16
TrueCrypt still works. The audit(s) didn't bring up anything serious which would affect my Linux/Windows7 usage.

**"Phase 2 of the TrueCrypt Audit FINISHED! No significant cryptographic problems found**

And see why the TrueCrypt spinoffs are violations of the TrueCrypt license." More information and download: [https://www.grc.com/misc/truecrypt/truecrypt.htm](https://www.grc.com/misc/truecrypt/truecrypt.htm) Personally, I don't trust newer spinoffs.

- [https://ubuntuforums.org/showthread.php?t=2313441&p=13450910#post13450910](https://ubuntuforums.org/showthread.php?t=2313441&p=13450910#post13450910)

---

### Post by Habitual on 2016-04-16
```
236db43eb33571e4f5b985e0323b3f8a  /home/jj/Downloads/truecrypt-7.1a-setup-x64
```

and I'm not afraid to use it.

---

### Post by HermanAB on 2016-04-16
LUKS of course.

---

### Post by drm200 on 2016-04-24
I still use truecrypt.  I like it because the files can be opened via ubuntu and windows and because it is very reliable (i've used it for years)  ... IMO the weaknesses found in the audits are not cause for concern for the average user who is just trying to lock up their files to prevent their personal information from identity theft or financial theft ... Sure, the US government might be able to hack it ... but I do not worry about what they will find.  In the eventuality that someone is able to hack into truecrypt, I will worry only after the hack has been posted and is open to exploitation by the masses.

---

### Post by SchnappiJedi on 2016-04-24
Don't think the US government..or any other government can crack Truecrypt. What they can do it brute force it.

Here is one example where they could not get in: [http://www.theregister.co.uk/2010/06/28/brazil_banker_crypto_lock_out/](http://www.theregister.co.uk/2010/06/28/brazil_banker_crypto_lock_out/)
Here is a more recent one when they could get in (but they didn't say how, which makes one think it was just a brute force of a weaker password): [http://www.theregister.co.uk/2015/08/04/truecrypt_decrypted_by_fbi/](http://www.theregister.co.uk/2015/08/04/truecrypt_decrypted_by_fbi/)

It they actually cracked the underlying AES encryption or Truecrypt it would have gotten out...just like it came out how they paid a third party to hack into the iPhone of the Cali scumbags.

---

### Post by Scarbo on 2016-05-07
I downloaded Veracrypt and extracted the four main files.  I figured I wanted to install the gui-setup-x86 file to my new 16.04 system, but can't figure out the next step.  I noted the Ubuntu software center contains no encryption software, which seems careless. Any help would be appreciated.

---

### Post by dan227 on 2016-05-08
> **jebi said:**
> hi  I used to use truecrypt, i want to use a similar program, one where i could unmount and require as password to re-mount, preferably not the admin password. i want to encrypt everything, the filesystem, home folders and a non system partition as well.  but i really need a interface GUI i am too slow a typer and noob to linux so a GUI is important to me...     

Use the Logical Volumn Manager and enable LVM2 "Guided Disk Encryption/Full Disk!"    

> **jebi said:**
>   I have heard of LUKs? also aes crypt and dm-crypt are these secure and uncrackable do they have a GUI?  Is there any better programs out there?  Also need like an idiots guide to set them up as well      

Yes, there are better programs out there, theres also Peter Guttmans Secure File System - SFS for FUSE which works transparently like LUKS and the LVM. As to are they uncrackable, that depends on your definition of good password enforcement and there are always programs for breaking weak one's like "TRUECRACK"   

As to the idiots guide, cat the read me (dot) text file *.txt usually found in INSTALL.TXT or README.TXT and follow what it suggest's, usually its as simple as typing (dot) forwardslash configure followed with (dot) forwardslash make and make install if the build fails it normally tells you why - ie: missing library dependancy which can be fixed with sudo apt-get install name of missing LIB here! 

It's been a while since I explored using either on "Linux!" as I'm having far more fun with EvilOLive - STATIC Linux - and ShellTrumpet! It's not a backdoor, it's just 9P!   Filing system bugs - Mach Kernels / Micro Kernels Oracles "Fuzzy Flop" and goodness me is that every single Linux filing system with a Bug - so it is - Advertising - Astroturfing (never give Google your phone number) and RdRand wholesomeness!

UEFI - an excellent example of bottom burping microsoft bum dust, that is just so friendly for your hardware and accuses everything Nix-like of being a _LEGACY application - a bit like uninventive - anti-encryption spouting operating systems that still want to use WAKE on LAN magic packets with LM_Hash and NTFS!

---

### Post by Habitual on 2016-05-09
> **jebi said:**
> I have heard of LUKs? also aes crypt and dm-crypt are these secure and uncrackable do they have a GUI?
Decide for yourself if what you "heard" is true: [Pwning Past Whole Disk Encryption]("https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/")

---

### Post by SchnappiJedi on 2016-05-09
> **Scarbo said:**
> I downloaded Veracrypt and extracted the four  main files.  I figured I wanted to install the gui-setup-x86 file to my  new 16.04 system, but can't figure out the next step.  I noted the  Ubuntu software center contains no encryption software, which seems  careless. Any help would be appreciated.

Sorry. Have no experience using Veracrypt on Linux. Like Linux for servers and Windows for desktop/ any GUI environment.

---

