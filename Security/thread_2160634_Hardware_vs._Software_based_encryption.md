---
title: "Hardware vs. Software based encryption"
date: 2013-07-07
forum: Security
---

### Post by Revolutionary101 on 2013-07-07
Hey everyone. I am a student at the University of Michigan and I am majoring in Computer Science. Currently, I haven't taken any classes related to the fields I am interested in and I am looking to get ahead of the curve.

With that being said, I am wondering what the difference between hardware and software based encryption. What are the pros and cons as far as speed and security wise. Any explanation rather than just simple answers would be most appreciated.

---

### Post by HermanAB on 2013-07-07
Read up on Field Programmable Gate Arrays and VHDL.

---

### Post by Hungry Man on 2013-07-07
Well, basically, with hardware encryption like on a HDD (such as the Samsung 840 PRO) the instructions are built into the hard drive/ at the hardware level, making encryption seamless and incredibly fast - virtually no performance hit (as opposed to 1-15% hit without hardware encryption).

With software encryption the instruction are handled by the CPU, and the reads/writes to the drive are going to be slower. You can have instruction sets like AES-IS on the CPU to speed up the decryption/encryption process, but the reads/writes to the disk will bottleneck.

In terms of encryption in general, some things you'll learn are that when you're using a single password (like for a hard drive) it's symmetric key cryptography - a user chooses a password, generally the password is "stretched"/ hashed (key stretching is just hashing multiple times in a specific way to make bruteforcing slower), and then using that key the encryption algorithm (such as AES) is used to encrypt the data multiple "rounds" (AES can use 12 rounds for 256bit iirc) on each block size.

---

### Post by Revolutionary101 on 2013-07-07
Thank you both for your answers. I will be sure to read up on Field Programmable Gate Arrays and VHDL, HermanAB.

---

### Post by Steve_Decker on 2013-08-27
Software encryption refers to a set of encryption instructions for the  device whereas hardware encryption refers to physical components of the  device (such as a chip).  The most robust encryption solutions utilize  both hardware and software.  Here is an article if you are interested in  reading more:  [http://www.koolspan.com/blog/weekly-word-hardware-software/](http://www.koolspan.com/blog/weekly-word-hardware-software/)

---

