---
title: "aircrack ng, good number dictionary"
date: 2008-10-01
forum: Security
---

### Post by cosine352 on 2008-10-01
Hi friends,
I was having fun cracking my wireless key. It was real easy when it was WEP. Now I have changed it to WPA. I got the .cap file with WPA handshake data. Now I am having problem cracking it.
The problem is with the dictionary I think. I know my passphrase is only numbers. But the dictionary I have is for words. Do anyone know about some good dictionary for numbers. It will be cool.

Thanks

---

### Post by pytheas22 on 2008-10-02
If your passphrase is longer than seven or eight characters and is composed exclusively of numbers, I don't think there will be any dictionaries that will include it.  Generally WPA is only crackable if the passphrases are short or dictionary words.  If you add your passphrase to your dictionary file, aircrack should find it, but I don't know of any pre-existing dictionaries that would be likely to contain your passphrase.

You can also always write your own dictionary file.  They're usually just plain text files.  If you want a list of numbers, it would be trivial to get the computer to spit out all values within a certain range into a text file.

---

### Post by cosine352 on 2008-10-03
So I am safe.:guitar::popcorn::D

---

### Post by pytheas22 on 2008-10-03
Yes, WPA1/2 can't be cracked as long as your passphrase is sufficiently long (8 or so characters minimum, the more the better) and is not a word or phrase that would conceivably appear in any word list.  Otherwise, the only way to crack WPA is through brute-forcing, which takes way too long ([~15 billion years on a 31-character passphrase]("http://newsgroups.derkeiler.com/Archive/Alt/alt.internet.wireless/2006-03/msg00636.html")) as long as your passphrase is not too short.

Of course, it's possible that some day, someone will discover a vulnerability in the WPA protocol that makes it susceptible to cryptographic attacks, but for the time being you should be pretty safe. (This is what happened to WEP, whose algorithm was discovered to contain vulnerabilities that made it possible to statistically predict the key by taking advantage of other fundamental flaws in the way that the protocol worked...but WEP was a joke from the outset; the WPA people knew what they were doing.  The sad thing is that a majority of households still use WEP.)

Of course, if your passphrase is just a number, you may want to throw in some letters.  It's conceivable that someone could create a dictionary file of numbers in order to crack your passphrase in a reasonable amount of time, even if the number were quite high.  If you throw in some random letters or other characters somewhere, you rule out this possibility.

---

