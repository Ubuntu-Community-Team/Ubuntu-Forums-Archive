---
title: "shadow file"
date: 2008-07-04
forum: Security
---

### Post by Red-Shield on 2008-07-04
I AM NOT A HACKER can any one tell me if there is a real way to read the shadow file in an unencrypted text i have a bet with my linux teacher he says there wont be someone here who will know how to unencrypted it i am not looking to be malicious just looking to learn can any one help me with this ...

---

### Post by Dr Small on 2008-07-04
The /etc/shadow file is unencrypted. I can read it, and so can you. The passwords are encrypted though.

---

### Post by Red-Shield on 2008-07-04
well that is what i am talking about is there help my bet will cost me 100 dollars american

---

### Post by Dr Small on 2008-07-04
If the passwords are simple, the hashes can be cracked with John the Ripper. But if not, it could take you weeks (even years, or never) to crack the passwords. So inevitably, you have lost the bet from the git-go.

---

### Post by kevdog on 2008-07-04
Yes those passwords are hashed -- there is no way you are going to find the real password from the hash.  Sorry you lost the bet.

---

### Post by Red-Shield on 2008-07-05
well what he said was if i could tell him his password for the account he created on my lap top i would get a hundred dollars i have been using ubuntu and unix for about 2-1/2 years he said it is possable just that there was no one that would help me with it but i will try john the ripper never heard of it will search for it what does hashed mean????

---

### Post by hyper_ch on 2008-07-05
you need rainbow tables and compare the hashes to it... the rainbow tables will give you a password that will then be hashed to that string....

---

### Post by Gamma746 on 2008-07-05
If you want to run John the Ripper, install it with ```
sudo aptitude install john
```Then you can run it with ```
john /path/to/file
```You'll need to prefix that with "sudo" if you don't have read access to the file.

> what does hashed mean????
[http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)

---

### Post by Dr Small on 2008-07-05
> **Gamma746 said:**
> If you want to run John the Ripper, install it with ```
sudo aptitude install john
```Then you can run it with ```
john /path/to/file
```You'll need to prefix that with "sudo" if you don't have read access to the file.


[http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function)
Or, an easier way would be to copy the line where the teacher has his account (in /etc/shadow), paste it in a new file, and then run john against it. Saves time, incase there is other users on the system.

---

### Post by kevdog on 2008-07-05
Id be interested to know if that works .. my bet ... no!  What hash is used in the shadow file anyway.  If its md5 you might find the password in a few weeks, sha1 -- forget about it.

---

### Post by Dr Small on 2008-07-05
Generally most passwords in the shadow file are MD5 hashes, unless you changed it. I generate my own MD5 hashes with grub to run against john to test the strength of it.
```
grub-md5-crypt
```

My current password:
```
guesses: 0  time: 20:00:55:02 (3)  c/s: 4217  trying: We422m
```

---

### Post by kevdog on 2008-07-05
Where would or could you change the hash -- md5 isn't all that great.  Id prefer higher than SHA1 however would settle on SHA1 or even RIPEMD160.  Anyway to do this?

---

### Post by Dr Small on 2008-07-06
I am having a hard time finding anything on it, yet I know it must be possible, since john himself will detect what type of hash it is, to begin cracking it. This was the only refference I could find on it, of all places..., Wikipedia:
> The contents of the file is usually modified by the passwd program, which in turn is largely dependent on PAM. For example, the type of hash used is dictated by the configuration of the pam_unix.so module. By default the MD5 hash is used, while the newer pam_unix2.so module is also capable of stronger hashes such as blowfish.

Perhaps I am searching around with the wrong search terms, too. So that doesn't help any.

---

### Post by The Cog on 2008-07-06
What hasn't been specifically stated, perhaps because those that know it assume it is obvious, is that a hash is intended to be a one-way function. There is not supposed to be any way to retrieve the original from the hash. The way hashes work is that when the user inputs the password, the user input is put through the same hash algorithm and the result is compared against the stored hash.

---

### Post by kevdog on 2008-07-06
Cracking a hash isn't so much breaking the algorithm, its either guessing the same password and comparing the result, or creating a collision -- which means guessing another word the results in the same hash.  The ability to generate collisions is much more probable with md5 than other well known hashes.

Blowfish to the best of my knowledge is not a hash function, but an encryption algorithm.  Well accepted hashes (via the gnupg project) are the SHA family, md5.  Whirlpool is a different type of hash that is in consideration in the gnupg standard.  Currently there is an ongoing competition that should be complete by 2001 sponsored by the NSA that will define the next American Hash Standard.  The American Encryption Standard was set in 2006 -- and this was the Rajindel encryption algorithm.  AES really isn't an algorithm per se, simply a designation.

---

### Post by Red-Shield on 2008-07-06
well thank all of you people who helped i am sorry that i did not print the progress but it took about 15 minutes to tell me the password was "letmein" my teacher said it was a weak password but still owes the hundred i took the advise and isolated the string in a seperate file it was faster thank i love linux..........

---

### Post by Dr Small on 2008-07-06
> **Red-Shield said:**
> well thank all of you people who helped i am sorry that i did not print the progress but it took about 15 minutes to tell me the password was "letmein" my teacher said it was a weak password but still owes the hundred i took the advise and isolated the string in a seperate file it was faster thank i love linux..........
So, did you win the bet?

---

### Post by Red-Shield on 2008-07-06
yes !!! but if the passwd was harder then will john just keep running until it cracks or will it quit it did not crack my password and i let it run half the day so can i leave it running it uses 100% of my processor while trying to crack i have 2 intel quad core and 4GB of ram can it run for a month and is that bad for my hardware?????

---

