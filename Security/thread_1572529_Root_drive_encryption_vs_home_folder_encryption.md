---
title: "Root drive encryption vs home folder encryption"
date: 2010-09-11
forum: Security
---

### Post by tornadof3 on 2010-09-11
Hello all

I'm currently running 10.04, installed as an upgrade via the software centre. The original install on my laptop was from the alternate CD of a 9.04 installation.

For the 10.10 release of ubuntu, I'm planning to do a clean re-install. I am a fan of using encryption, and was wondering what opinions there were regarding doing a 'root system' encryption that runs using lvm and encrypts the entire filesystem (with a password on boot) or simply installing as normal and then using the feature in ubuntu to encrypt the user's home files which are unlocked on login. Is there a difference in speed of execution for apps?

My machine is in no way "slow", (it's a decent AMD X2 Athlon with 4GB RAM) but I do think/wonder whether having the root drive encryption makes it a little sluggish compared to what it might be like without?? Would the same overhead exist with home user drive encryption?

---

### Post by rookcifer on 2010-09-11
You're looking at about a 5% slow down on average.  Phoronix has done some benchmarks concerning this and they can be found with a Google search.

I recommend using 128 bit AES (since larger keys cause even more overhead).  AES is the fastest.  If you use Serpent, you can expect even more of a slow down.  If you insist on 256 bit keys (which is completely unnecessary) then Twofish slightly out-performs AES in most of the benchmarks I have seen.  At 128 bit keys, however, AES is the fastest.

---

### Post by BkkBonanza on 2010-09-11
From what I've read it only cuts about a few percent off disk speed.

As far as root vs. home encryption I opted for home - anything even remotely valuable should be in your home anyway. And why bother encrypting system binaries and stuff. I'm sure there are user scenarios where they would want logs and system config private but for me there is really only a very limited amount of private material. Also, this way I have a choice to put stuff in or out of my "safe" area.

You can add encrypted home now without re-installing and it is an option during the install process as well on newer releases. The goto tutorial for adding it after is here: 

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

One convenient thing about encrypted home is it is tied into your regular password so you won't have to enter two passwwords to boot. It also supports two factor auth. by allowing the key to be on a flash stick and you needing both password and key. It's been working well for me through two release upgrades now.

I don't even notice I have it turned on.

---

### Post by bodhi.zazen on 2010-09-12
I perform full system encryption using LUKS + LVM on laptops / netbooks and honestly do not notice any major performance hit. It depends on how much you write to disk I suppose.

---

### Post by HermanAB on 2010-09-12
Howdy,

I agree that there is no noticeable performance hit when using software encryption on a system.  

Basically, you only need to encrypt your data.  Encrypting the whole OS is not useful at all, since there is nothing secret in it, but it does make it slightly more difficult for someone to compromise a portable machine.

Note that there must always be some small part of the disk that is in clear, otherwise the machine cannot boot, so there is always a way to compromise a machine even if it uses so called 'whole disk' encryption, but the smaller you make that clear piece, the harder it is to mess with it.

---

### Post by Bachstelze on 2010-09-12
> **HermanAB said:**
> 
Basically, you only need to encrypt your data.  Encrypting the whole OS is not useful at all, since there is nothing secret in it, 

As I said in another thread, there is a lot of information outside your home directory, especially if you are the only user of the system. For example, an attacker could read your logs, or see which packages you have installed. It is not hard to imagine why you would want to protect that information.

As for the uselessness of 256-bit keys, I'm not no sure. In *Practical Cryptography*, Niels Ferguson and Bruce Schneier argue that a n-bit key cipher only provides n/2 bits of security due to collision attacks, meaning that a 256-bit key cipher is necessary to get 128 bits of security.

---

### Post by BkkBonanza on 2010-09-12
> For example, an attacker could read your logs, or see which packages you have installed.

I'm not sure of the usefulness of that info but regardless if worried it would make sense to change permissions to be non-readable by "other". If an attacker has access to root or the user's account then they already have full access to the encrypted home.

---

### Post by Bachstelze on 2010-09-12
> **BkkBonaza said:**
> I'm not sure of the usefulness of that info

Think harder.

> **BkkBonaza said:**
> If an attacker has access to root or the user's account then they already have full access to the encrypted home.

You're totally missong the point of encryption... The point is that an attacker is not able to access the data even if they have physical access to the machine.

---

### Post by wacky_sung on 2010-09-12
Actually i do agree that encryption on home directory does slow down my system during boot up on my low end pc hardware.Beside that,using cryptkeeper help me to secure my files in an encrypted folder which is secure enough to prevent any break in.

---

### Post by rookcifer on 2010-09-12
> **Bachstelze said:**
> As for the uselessness of 256-bit keys, I'm not no sure. In *Practical Cryptography*, Niels Ferguson and Bruce Schneier argue that a n-bit key cipher only provides n/2 bits of security due to collision attacks, meaning that a 256-bit key cipher is necessary to get 128 bits of security.

That's only true for hash functions, not ciphers (or at least not single key ciphers.  TripleDES is susceptible because the plaintext is encrypted with more than one key).  In the case of TripleDES the attack is called a meet-in-the-middle attack and in the case of hash functions it is known as the birthday attack.  These attacks *do not* affect modern ciphers like AES, Twofish, Serpent, et al.

However, for hash functions it is a different story.  Because of the birthday attack, it is imperative to use a hash function with twice the keylength of the cipher.  So if you're using 128 bit AES, you will want to use SHA-256 since SHA-256 only has a complexity of 128 bits.

Now, it has been shown that Grover's algorithm (for use with quantum computing) can reduce the complexity of a typical block cipher by half (n^n/2).  This is why NIST wanted the AES candidates to offer 256 bit keys, so that if quantum computers ever became a reality, 256 bit keys will still provide 128 bit security (which is not breakable by brute force). AES was intended to be used for decades (if not longer) so NIST planned ahead.

So the bottom line is unless you are protecting your data from quantum computers, there's no need for anything other than 128 bit keys.

---

### Post by bodhi.zazen on 2010-09-12
> **wacky_sung said:**
> Actually i do agree that encryption on home directory does slow down my system during boot up on my low end pc hardware.Beside that,using cryptkeeper help me to secure my files in an encrypted folder which is secure enough to prevent any break in.

Yes, you will notice a performance hit on older hardware. If a task takes 0.1 seconds on modern hardware and 1 second on old hardware, you will not likely notice the task taking 0.15 seconds, but you would notice it taking 1.5 seconds.

---

### Post by tornadof3 on 2010-09-13
This topic has had lots of very interesting replies - thank you for all contributions. I remember making extensive use of *Practical Cryptography* (as mentioned by Bachstelze) in my 3rd year project during my degree and found it a very useful resource then.

---

### Post by mathgeek2000 on 2010-09-13
I have an hp business laptop, and personally prefer home folder/file encryption:

Pros:
  -- Can back up my PC w/ CloneZilla w/o needing an entire 160GB  free on the 
      Backup HDD.
  -- Can still adjust sizes if I need to, using GParted on CD.
  -- Only need one password at login, not one for bootup, second for login.
       (UBUNTU could do both folder, and LVM Encryption)

If you're 'really concerned' with security Dual-Factor Authentication is possible: -
   will need: USB Jump Drive, and Password to log in:
  --

---

### Post by radiobuzzer on 2013-01-08
(a) encrypting home folder does not protect you if somebody steals your computer. This is because your passphrase is stored in the unencrypted part of the hard disk. So one has to 
[LIST]
boot up the computer with the Ubuntu recovery menu or with a Live CD/USB, 
mount your / as root user and then su to your username
then this person will have full access to your password and keyphrase, for changing it and decrypting the data
[/LIST]

So if you are looking for real protection, encrypting home directory is not enough. I have managed to recover my lost passphrase very easily, just by using the recovery boot meny of Ubuntu 12.10

(b) Concerning performance, I am concerned about the fact that everything is encrypted and is seen by your filesystem as one file. This leads eventually into a huge file, which may be slow to handle and get easily fragmented. I have noticed that after using a constantly growing encrypted partition for two years

---

### Post by howefield on 2013-01-08
Old thread closed.

---

