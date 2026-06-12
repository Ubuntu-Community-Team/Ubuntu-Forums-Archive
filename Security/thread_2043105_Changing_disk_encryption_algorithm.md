---
title: "Changing disk encryption algorithm"
date: 2012-08-15
forum: Security
---

### Post by Stonecold1995 on 2012-08-15
When I installed Kubuntu, I used the alternate installer so I could encrypted the disk, and I ended up encrypting it with AES.  However, I now regret that and want to use Serpent instead (it's a lot stronger if I'm right, and I can be really paranoid about computer security).  So is there a way to re-encrypt the disk or somehow change the encryption method from AES to Serpent without re-installing?

Also, I know Serpent is stronger than AES but AES is faster, but how big are the differences?  I want to change from AES to Serpent because I know AES is susceptible to a timing attack (and is weaker in general), but my TrueCrypt benchmarks place the speed differences far apart.  I get 2.6 GB/s with AES and 241 MB/s with Serpent, according to TrueCrypt (encrypting and decrypting 1 GB of random data in RAM).  Is the difference really that big in practice?  If I encrypt my computer with Serpent would the disk really be more than 10 times slower?

---

### Post by Hungry Man on 2012-08-15
Serpent isn't stronger. Both Serpend and Rijndael (now referred to as AES) were in competition to become the Advanced Encryption Standard - Rijndael won and that's why it's called AES.

Timing attacks aren't exactly easy to pull off and I don't know why Serpent would be more immune than Rijndael.

And yes, disk actions could be 10x slower.

---

### Post by Stonecold1995 on 2012-08-15
> **Hungry Man said:**
> Serpent isn't stronger. Both Serpend and Rijndael (now referred to as AES) were in competition to become the Advanced Encryption Standard - Rijndael won and that's why it's called AES.

Timing attacks aren't exactly easy to pull off and I don't know why Serpent would be more immune than Rijndael.

And yes, disk actions could be 10x slower.

Oh, OK.  I just thought Serpent only lost to AES because AES was so much faster.  Is Serpent actually weaker, and is it so slow because there isn't hardware acceleration (AES-NI, I think) or just because it's a more complex cipher?

---

### Post by Hungry Man on 2012-08-15
Everyone in the competition put their own encryption method first and put Rijndael second (except for the developers of Rijndael who put it first, of course) so it was pretty widely accepted by the members of the competition that it was great.

The speed doesn't have to do with hardware acceleration. That doesn't make too big a difference, the speed is almost entirely determined by the algorithm and disk speed.

I don't think any of them are cryptographically insecure.

---

### Post by rookcifer on 2012-08-16
> **Stonecold1995 said:**
> When I installed Kubuntu, I used the alternate installer so I could encrypted the disk, and I ended up encrypting it with AES.  However, I now regret that and want to use Serpent instead (it's a lot stronger if I'm right, and I can be really paranoid about computer security). 

Saying Serpent is stronger than AES is like saying swimming across the Atlantic is "easier" than swimming across the Pacific.  Both are unattainable.

 > So is there a way to re-encrypt the disk or somehow change the encryption method from AES to Serpent without re-installing?

Probably not.

> Also, I know Serpent is stronger than AES but AES is faster, but how big are the differences?  I want to change from AES to Serpent because I know AES is susceptible to a timing attack (and is weaker in general)

All block ciphers are susceptible to side-channel attacks.  AES is not really alone here.  Besides those types of attacks require the attacker to already have control over your machine, and if he has that it's game over anyway.  It would be easier for him to simply install a hardware keylogger or a bootloader than use a timing or cache attack.  So no matter what crypto solution you use, if an attacker gets a hold of the machine without your knowledge, it's game over.  The cipher is the least of your worries.  All of them (AES, Serpent, Twofish, Camellia, RC6, CAST5) are so strong that an attacker would undoubtedly take a short-cut and attack you some other way.

> but my TrueCrypt benchmarks place the speed differences far apart.  I get 2.6 GB/s with AES and 241 MB/s with Serpent, according to TrueCrypt (encrypting and decrypting 1 GB of random data in RAM).  Is the difference really that big in practice?  If I encrypt my computer with Serpent would the disk really be more than 10 times slower?

You are getting those AES speeds because modern Intel processors come with a special AES instruction set which speeds it up dramatically.  Without that CPU instruction you wouldn't see anywhere near 2.6 Gb/s.  But even without that instruction set AES would still outperform Serpent.

It also depends on how the code was compiled and optimized.  So you can't really compare Truecrypt's implementation of AES with other software.  There will be a little variance.

---

