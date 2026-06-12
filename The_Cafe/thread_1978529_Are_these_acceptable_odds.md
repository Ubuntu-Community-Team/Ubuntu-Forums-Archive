---
title: "Are these acceptable odds?"
date: 2012-05-11
forum: The Cafe
---

### Post by ki4jgt on 2012-05-11
Out of the millions of documents created each day are the odds of sha512 acceptable?

SHA512 has a 1/4.01199191 × 10^99 (Calculated 36 ** 64) chance of two documents matching each other. Like I said earlier, with millions of documents created daily what are the chances that some of them don't match?

---

### Post by Bachstelze on 2012-05-11
For starters, the ods are about 1/10^154. Second, the number of atoms in the universe is about 10^80.

One million is 10^6. assuming one million of documents created each day, you would have to wait for 10^148 days. That's more than 10^145 years. The age of the universe is less than 10^10 years.

You don't know what you are talking about.

---

### Post by ki4jgt on 2012-05-11
> **Bachstelze said:**
> For starters, the ods are about 1/10^154. Second, the number of atoms in the universe is about 10^80.

One million is 10^6. assuming one million of documents created each day, you would have to wait for 10^148 days. That's more than 10^145 years. The age of the universe is less than 10^10 years.

You don't know what you are talking about.

That's why I asked the question. I'm not pointing out flaws but asking what are the ranges of acceptable odds. I thought that was pretty obvious. Secondly how did you arrive at 1/10^154? With only 36**64 possible outcomes of the sha512 protocol (assuming it's only alpha-numerical)? That would mean bare minimum every document would have to fall within that range wouldn't it? Lastly, Although I accept your comparisons, I do think you need to reword to the number of atoms in the observable universe.

---

### Post by pqwoerituytrueiwoq on 2012-05-11
> **Bachstelze said:**
> Second, the number of atoms in the universe is about 10^80.
  the infinite universe has a limited number of atom?

---

### Post by JDShu on 2012-05-11
> **ki4jgt said:**
> That's why I asked the question. I'm not pointing out flaws but asking what are the ranges of acceptable odds. I thought that was pretty obvious. Secondly how did you arrive at 1/10^154? With only 36**64 possible outcomes of the sha512 protocol (assuming it's only alpha-numerical)? That would mean bare minimum every document would have to fall within that range wouldn't it? Lastly, Although I accept your comparisons, I do think you need to reword to the number of atoms in the observable universe.

SHA-512 has a digest that is 512 bits long. So there are 2^512 ~= 10^154 possible digests.

---

### Post by papibe on 2012-05-12
> **Bachstelze said:**
> the ods are about 1/10^154.
<joke>

[So you're saying there's a chance]("http://www.youtube.com/watch?v=wGdhc9k07Ms").

</joke>

Respectfully.

---

### Post by ki4jgt on 2012-05-12
> **JDShu said:**
> SHA-512 has a digest that is 512 bits long. So there are 2^512 ~= 10^154 possible digests.

but the bits are limited. Not every bite included in that formula is included in an SHA512 digest. the only bit sequences which would be included would be those which are within the 36 bite range of a-z and 0-9. Unless 256 characters are included the formula doesn't hold out.

---

### Post by JDShu on 2012-05-12
> **ki4jgt said:**
> but the bits are limited. Not every bite included in that formula is included in an SHA512 digest.  

From [wikipedia]("http://en.wikipedia.org/wiki/SHA-2"): "SHA-2 consists of a set of four hash functions with digests that are 224, 256, 384 or 512 bits."

> the only bit sequences which would be included would be those which are within the 36 bite range of a-z and 0-9. Unless 256 characters are included the formula doesn't hold out.What are you talking about? The digest is a series of 512 bits. A bit is either a 1 or a 0.

---

### Post by ki4jgt on 2012-05-12
> **JDShu said:**
> From [wikipedia]("http://en.wikipedia.org/wiki/SHA-2"): "SHA-2 consists of a set of four hash functions with digests that are 224, 256, 384 or 512 bits."

What are you talking about? The digest is a series of 512 bits. A bit is either a 1 or a 0.

There are 8 bits to a character right? So 512/8 = 64 characters. Whenever I hash something I only get the letters a-z or the numbers 0-9 in 64 characters. In total an 8 digit 0/1 sequence can be 1/256 total possibilties however (using the letters I get) a-z and 0-9 are 36 out of those 256 possible bit sequences.

In other words, if you divide the entire bit sequence into 8 bit bytes, (and the bytes are actually 512 bits) you should end up with 64 8 bit byte sequences total. In using every possible sequence of 8 1s and 0s you would have to use all 256 ascii characters. However, since the hash digest only uses a-z and 0-9 you're only using 36 of those 256 total sequences.

---

### Post by JDShu on 2012-05-12
> **ki4jgt said:**
> There are 8 bits to a character right? So 512/8 = 64 characters. Whenever I hash something I only get the letters a-z or the numbers 0-9 in 64 characters. In total an 8 digit 0/1 sequence can be 1/256 total possibilties however (using the letters I get) a-z and 0-9 are 36 out of those 256 possible bit sequences.

In other words, if you divide the entire bit sequence into 8 bit bytes, (and the bytes are actually 512 bits) you should end up with 64 8 bit byte sequences total. In using every possible sequence of 8 1s and 0s you would have to use all 256 ascii characters. However, since the hash digest only uses a-z and 0-9 you're only using 36 of those 256 total sequences.

Why are you arbitrarily interpreting a series of bits as characters? That makes no sense. The point of a hash function is to create a hopefully unique and fixed length bit string, otherwise known as a digest. It is simply a series of 0s and 1s, there is no other meaning.

---

### Post by GeneralZod on 2012-05-12
ki4jgt: Wikipedia has some examples of SHA-512 hashes:

[http://en.wikipedia.org/wiki/Sha512#Examples_of_SHA-2_variants](http://en.wikipedia.org/wiki/Sha512#Examples_of_SHA-2_variants)

e.g.

```

SHA512("The quick brown fox jumps over the lazy dog.")
0x 91ea1245f20d46ae9a037a989f54f1f790f0a47607eeb8a14d12890cea77a1bbc6c7ed9cf205e67b7f2b8fd4c7dfd3a7a8617e45f3c463d481c7e586c39ac1ed

```

As you can see, they are displayed as hex strings (so 16 possible characters, not 36) of 128 characters, so there are

16^128 = (2^4)^128 = 2^512 which is approx 10^154, as Bachstelze and JDShu said.

---

### Post by ki4jgt on 2012-05-12
> **JDShu said:**
> Why are you arbitrarily interpreting a series of bits as characters? That makes no sense. The point of a hash function is to create a hopefully unique and fixed length bit string, otherwise known as a digest. It is simply a series of 0s and 1s, there is no other meaning.

I understand that but when you use a program to get hashes from a file (either md5 or sha) it gives you a series of letters and numbers. I'm assuming it to convert the 1 and 0 bit sequences to legible means. When you visit a Tor address, it's a translation of the hash of the public key of that particular website. When I hash a video on my computer (with Gtkhash) I get 197fe8e6f140ac09dc40a5db75ae71aaf4d73734e90ecf57a82351c5d2ba0b71 I don't get any 1s and 0s. That is with 256 btw. which seems odd. B/c 512 is doing 128 characters. That would be 1024 bits returned. If all you have to judge whether a file is correct or not then you can't include every possible bit sequence and you must convert the 1s and 0s b/c not doing so would make your math inadequate.

---

### Post by JDShu on 2012-05-12
I'll assume you posted before seeing GeneralZod's answer :)

Specifically, those are not characters, those are [hexadecimal]("http://en.wikipedia.org/wiki/Hexadecimal") numbers.

---

### Post by ki4jgt on 2012-05-12
> **GeneralZod said:**
> ki4jgt: Wikipedia has some examples of SHA-512 hashes:

[http://en.wikipedia.org/wiki/Sha512#Examples_of_SHA-2_variants](http://en.wikipedia.org/wiki/Sha512#Examples_of_SHA-2_variants)

e.g.

```

SHA512("The quick brown fox jumps over the lazy dog.")
0x 91ea1245f20d46ae9a037a989f54f1f790f0a47607eeb8a14d12890cea77a1bbc6c7ed9cf205e67b7f2b8fd4c7dfd3a7a8617e45f3c463d481c7e586c39ac1ed

```

As you can see, they are displayed as hex strings (so 16 possible characters, not 36) of 128 characters, so there are

16^128 = (2^4)^128 = 2^512 which is approx 10^154, as Bachstelze and JDShu said.

That actually makes more sense. So 16 of the possible 256 0/1 sequences are used. 0-9 and a-f.

---

