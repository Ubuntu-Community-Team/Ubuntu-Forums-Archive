---
title: "Security of this alternative to /dev/urandom"
date: 2014-11-03
forum: Security
---

### Post by GigabyteProduction on 2014-11-03
Using data from /dev/urandom is known to be cryptographically secure, but it's slow. I found on [http://serverfault.com/a/415962/198839](http://serverfault.com/a/415962/198839) this alternative to using data from /dev/urandom:
```
openssl enc -aes-256-ctr -pass pass:"$(dd if=/dev/urandom bs=128 count=1 2>/dev/null | base64)" -nosalt < /dev/zero
```

This produces random data at a much faster rate. I used 6 instances (1 for each core of my CPU, as this appears to be single-threaded) of this command, all piping into dd so I could wipe areas of my hard drive that I was about to create an LUKS encrypted partition at. When I was testing the speed of the command before I wrote to my hard drive, I found that using my entire CPU, it generated at 1 GB/s, which is significantly faster than the 15 MB/s I was getting with /dev/urandom (not to mention I've exhasted /dev/urandom before and it slowed down to 1 MB/s after 15 minutes of copying).

I would think that it is cryptographically secure, since disk encryption utilities like TrueCrypt or CipherShed makes data that is indistinguishable from cryptographically secure random data, which also uses AES (though, often with other encryption algorithms used on top of each other).

Is this any less or maybe any more secure than using /dev/urandom?

---

### Post by bashiergui on 2014-11-08
[FONT=arial][/FONT]If this is for wiping clusters then it's probably sufficient. All you really need to do is write over the existing space with 0s once, writing random data is unnecessary. Once data is overwritten with anything it's gone.

---

### Post by GigabyteProduction on 2014-11-08
Oh, no it's not **just** for wiping data. The reason why I did this is because I encrypted my system with LUKS. If I only wiped with 0s, an attacker would know what parts of my disk have stuff in them, and how much stuff there is. By filling the space with random data, an attacker looking at the drive won't know what's encrypted and what's not. Also, an attacker trying to attack AES by brute force, rather than attacking the passphrase by brute force wouldn't know if a given portion of data was actually encrypted or if it was just random data (which won't decrypt to anything useful). **For both of the reasons stated to work, the random data used needs to be cryptographically secure**, meaning it's seemingly impossible for someone to replicate (normal random number generators may use something like time as the seed of the generator, or may have patters that don't exist in the encrypted data) otherwise an attacker would be able to use a tool to find what's encrypted and what's not, and that's what I'm trying to prevent.

Also, wiping with 0s isn't always sufficient, depending on what your threat model is. I think there are tools that can find imprints of data that's left on hard drives when wiped with 0s. I'm not anticipating someone with these tools stealing my hard drive; I'm just doing this for the sake of correctness and completedness, but it defeats the purpose if my command isn't actually as secure as it should be.

---

### Post by bashiergui on 2014-11-09
> **GigabyteProduction said:**
> If I only wiped with 0s, an attacker would know what parts of my disk have stuff in them, and how much stuff there is. By filling the space with random data, an attacker looking at the drive won't know what's encrypted and what's not.  You're wrong, and you're also kind of right but not in the way you think. I hate myself enough to try and explain why.

I follow your logic but that's not how it works.  Data written in unallocated space is going to be marked as unallocated regardless of how random it is.  So your technique will only confuse an attacker that doesn't know what he's doing.> **GigabyteProduction said:**
> Also, an attacker trying to attack AES by brute force, rather than attacking the passphrase by brute force wouldn't know if a given portion of data was actually encrypted or if it was just random data (which won't decrypt to anything useful).  Again I follow the logic but an attacker is not going to attack AES 256. It hasn't been cracked yet, and I'm willing to bet a sizeable amount of cash that your computer will not be the first one. An attacker won't go the most difficult path. They'll exploit the easier stuff, like looking in memory for the keys. And if they're able to get the keys then it doesn't matter how you wrote over the unallocated space. [Here]("https://www.schneier.com/blog/archives/2012/03/can_the_nsa_bre.html")'s an article that explains that the attacker will probably "**exploit bad random number generators** or sloppy password creation habits". So in that sense your technique is actually useful and will probably work quite well. You'll remove one of the easier attack paths. Use a strong password and you'll eliminate another.> **GigabyteProduction said:**
> Also, wiping with 0s isn't always sufficient, depending on what your threat model is. I think there are tools that can find imprints of data that's left on hard drives when wiped with 0s. I'm not anticipating someone with these tools stealing my hard drive; I'm just doing this for the sake of correctness and completedness, but it defeats the purpose if my command isn't actually as secure as it should be.You can use all 0s or you can use random writes if you like, but one pass is sufficient. Even if you're Snowden. [Here]("http://www.howtogeek.com/115573/htg-explains-why-you-only-have-to-wipe-a-disk-once-to-erase-it/") are the facts on that.

---

