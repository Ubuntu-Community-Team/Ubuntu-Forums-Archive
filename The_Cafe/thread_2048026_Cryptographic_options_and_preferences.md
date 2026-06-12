---
title: "Cryptographic options and preferences?"
date: 2012-08-26
forum: The Cafe
---

### Post by Welly Wu on 2012-08-26
I have a System76 Lemur Ultra Thin (lemu4) and I use Ubuntu 12.04.1 64 bit Long Term Service as my default and primary operating system of choice. I have 9.70 terabytes of total storage capacity as I outline here:

Seagate GoFlex FreeAgent Desk 3.00 terabyte Super Speed USB 3.0 (2 drives)
Seagate FreeAgent Desk 1.50 terabyte USB High Speed 2.0 (1 drive)
Western Digital My Passport 2.00 terabyte Super Speed USB 3.0 Portable (1 drive)
Kingston DataTraveler HyperX 128.00 gigabyte Super Speed USB 3.0 thumb (1 drive)
Crucial M4 2.5" SATA-III 6 GB/s MLC NAND FLASH 128.00 gigabyte Solid State Drive (1 drive)

Previously, I used TrueCrypt 7.1a for my external Seagate, Kingston, and Western Digital storage devices and it worked fine. I decided to use the Linux Unified Key System (LUKS) to encrypt my /home and /swap partitions when I installed Ubuntu 12.04 64 bit LTS bare metal. I use a variety of ciphers including Advanced Encryption Standard in Cipher Block Chaining Encrypted Salted Sector Initialization Vector Secure Hash Algorithm 256 bits mode of operation at 256 bits 14 rounds cipher strength and Secure Hash Algorithm 512 bits hash algorithm for TrueCrypt 7.1a and LUKS, Blowfish in Cipher Block Chaining mode of operation at both 256 bits and 448 bits 16 rounds cipher strength for WiTopia personal VPN Pro SSL and CrashPlan+ data backup software application respectively, and Gnu Privacy Guard using RSA 4096 bits asymmetric public key and CAST5 128 bits 16 rounds symmetric block cipher. I decided to migrate my data to the default built-in LUKS. TrueCrypt is a good software application, but the problem is that CrashPlan+ does not support it because it is run in the user space rather than the system level. My favorite cipher is AES CBC ESSIV:SHA-256 at 256 bits and SHA-512 hash algorithm because my Intel Core i5-3210M supports Advanced Encryption Standard - New Instructions for up to 4X hardware acceleration for encryption and 10X hardware acceleration for parallel decryption operations.

I have found that LUKS just plain old works properly. It gives me consistent results. I no longer have to worry about which slot to mount my external encrypted storage devices within TrueCrypt at all. I also do not need to worry about downloading or installing a software application such as CrashPlan+ that does not offer support for TrueCrypt because LUKS is a system level cryptographic feature. I have found that LUKS is much faster than TrueCrypt 7.1a. Copying several hundreds of gigabytes worth of mixed data using Super Speed USB 3.0 technology is reasonably fast. I also like the fact that LUKS encrypted partitions are readily mounted on virtually any modern GNU/Linux or BSD UNIX operating system. Microsoft Windows users can mount LUKS encrypted partitions using FreeOFTE software application as well. LUKS makes cryptography very simple and easy to use. I can backup my partition headers and save them within an encrypted 7-zip file for added safety. Though I do not plan to use this feature, I can also create up to 8 LUKS key slots for each LUKS encrypted partition. TrueCrypt 7.1a does not offer this feature. I can even specify that an additional authentication method be used in order to mount a LUKS partition. Finally, I am not limited in the number of LUKS partitions that I can choose to create in the future. This affords me flexibility and I can create custom partitions within volumes.

TrueCrypt 7.1a is still useful if you need to plausibly deny attackers access to your hidden volumes. It allows for multiple cipher and hash algorithm cascades which is a unique feature at the cost of decreased speed and performance. It also allows you to encrypt a Microsoft Windows system drive which is a great alternative to Microsoft BitLocker and BitLocker to Go features found in Ultimate and Enterprise editions for Windows 7 or Microsoft Windows 8 Pro 64 bit version.

GnuPG is quite useful for encrypting individual files. However, I think that it is easier and better to use 7-Zip to create encrypted compressed files that contain a multitude of folders and files inside. 7-Zip uses AES CBC 256 bits. I typically do not encrypt data that I plan to share with someone else so GnuPG is becoming less preferable for my needs. I find that using both GnuPG to encrypt individual files and 7-Zip to create encrypted compressed files provides robust security. This is what I typically do for extremely confidential and sensitive data.

Canonical makes Ubuntu so easy to use for just about anyone interested in GNU/Linux especially if they need publicly available strong software cryptography at no additional charge. The level of granular control and the sheer number of available choices and flexibility are unmatched in GNU/Linux. I don't have to worry about vendor lock-in using proprietary cryptographic software products which means that my data is liberated. The best thing about the implementation of software cryptography in Ubuntu is that you do not need to be a subject matter expert in order to be able to use it effectively. If you have brand new and modern PC hardware to power the current version of Ubuntu, then you are good to go.

My recommendation is to stick with the default built-in LUKS and GnuPG to meet your needs for confidentiality and integrity. TrueCrypt is useful in very narrow and specific purposes for a niche audience, but it is not fully supported by some hardware and software vendors in specific applications.

I hope that this is helpful and useful to those that are new to cryptography and Ubuntu that are looking for advice and best practices.

---

