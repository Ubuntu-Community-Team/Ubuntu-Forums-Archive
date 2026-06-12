---
title: "Rainbow Table Algorithm"
date: 2008-10-15
forum: Security
---

### Post by era86 on 2008-10-15
Greetings.

I have been researching the use of rainbow tables among "black hat" hackers and I was wondering how these look-up tables work.  I've done a lot of googling and wiki-ing, but I am still having a hard time grasping the algorithm.

From my understanding, it basically:

-takes a password hash
-reduces the hash to plaintext
-if plaintext isn't found, it hashes the plaintext and loops?

Someone please correct this.

Also, what is the protocol behind reading the data in a rainbow table?  Is there some open documentation on how the data is stored?

Any help is appreciated, thank you!:guitar:

---

### Post by cdenley on 2008-10-15
I believe the concept of rainbow tables is they compute hashes for commonly used passwords and store the hash with the plaintext password. Then, when they have a hash they want to crack, instead of guessing the password, hashing, then comparing, they simply compare the hashes they already computed.

I don't think this works well in linux, since md5 passwords use an 8 character salt. I think I did the math, and determined that creating rainbow tables using my password dictionary would require over 100TB of storage for MD5 passwords. Intrepid will use SHA512 passwords, so I don't think rainbow tables will be feasible for ubuntu anytime soon.

What type of password hash are you trying to crack?

---

### Post by era86 on 2008-10-15
I was just going to try and crack weak LM Windows passwords.  I want to design a tool that would be like a password recovery kit.  I'll keep looking around I guess and see what similar projects have done.

---

### Post by hyper_ch on 2008-10-16
As far as I understand it they just work for a string that gets encrypted to the same hash.

As the length of the hash is normally limited, there are a certain amount of possible hashes and hence multiple different strings will result in the same hash.

What is normally done to verify whether the entered string is identical to the encrypted one is to compare the hashes.

So people have just started to generate the hash of every possible input string and then, when you have the hash, you'll see if you can find a collission and if you do, you have then a string that encrypts to the same hash.

A bit simplified is the use of digit sums:

you use a string that is 1510151 --> this results in a digit sum of 13

Now you have a database that that started at 1 and just calculates all those digit sums.
1 -> 1
2 -> 2
...
11 -> 2
13 -> 4
...
49 -> 13

So when you have now the hash sum you look it up in the db, you will find "13" there which corresponds to a string of "49" and you have then a collission.

---

