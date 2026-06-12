---
title: "Entropy"
date: 2014-05-31
forum: Security
---

### Post by borgward on 2014-05-31
I ran dd if=/dev/random bs=1 count=32 2>/dev/null | base64 -w 0 | rev | cut -b 2- | rev to create secure password. 

jdLtcA0QawkgrYWDWkMEhAy9JCPX0hCwU/H0emcTew7QuTowMLax1tzKiqsFWhh


While writing it down I noticed elements that could qualify as dictionary words: awk, ME, JCP, emc, Tow, Lax.

cat /proc/sys/kernel/random/entropy_avail

3968

How much entropy do I need to produce a strong password for critical use? What are the factors that determine the amount of entropy in a system.

---

### Post by Chayak on 2014-05-31
You're reading too much into it.  That kind of password even if there are elements that could be words is perfectly secure.
Check [https://www.grc.com/haystack.htm]("https://www.grc.com/haystack.htm")

---

### Post by borgward on 2014-06-01
I previously checked out haystack. I also found a lot of disagreement about their conclusions, especially for critically important stuff. I would appreciate an answer that addresses my questions:

How much entropy do I need to produce a strong password for critical use?

What are the factors that determine the amount of entropy in a system.

---

### Post by bashiergui on 2014-06-01
Just because there happen to be a few 3-letter combinations that spell a word does not make it less random. You can often find what you percieve to be patterns in chaos. 

Use /dev/urandom instead of /dev/random.  Here's a good discussion elaborating on that and your question. [http://security.stackexchange.com/questions/89/feeding-dev-random-entropy-pool](http://security.stackexchange.com/questions/89/feeding-dev-random-entropy-pool)

---

### Post by HiImTye on 2014-06-02
that password is perfectly secure, you should be looking more at the crypt() function than entropy

---

### Post by donsy on 2014-06-02
You generated a 64-character password comprising upper and lower case letters and numbers for a total of 62 possibilities in each character location. The entropy per character for that is log2(62) =  5.954.  The entropy for your generated 64-character password is 5.954*64 = 381.069 bits, which should be more than sufficient over your lifetime.

If you're worried about embedded words check out pwgen to generate your passwords. For example:
```
pwgen -v 64
```
will generate 64 character passwords with no vowels.

---

### Post by tgalati4 on 2014-06-02
There are a few tools that you can use to increase the default entropy provided by linux systems:

[http://manpages.ubuntu.com/manpages/trusty/man3/Data::Entropy::RawSource::CryptCounter.3pm.html](http://manpages.ubuntu.com/manpages/trusty/man3/Data::Entropy::RawSource::CryptCounter.3pm.html)

[http://manpages.ubuntu.com/manpages/trusty/en/man8/rngd.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/rngd.8.html)

You could write a script that takes the current entropy and adds entropy to it (presumably increasing entropy by some random amount), then use that for your security purposes.

---

