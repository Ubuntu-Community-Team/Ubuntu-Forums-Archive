---
title: "How to test truecrypt security?"
date: 2010-11-03
forum: Security
---

### Post by dogdo on 2010-11-03
Ive made a simple encrypted external hard drive with truecrypt but i want to see how secure the encryption is. 

First off how do i know that the data is encrypted or not? granted for me to see the data i have to give the right password but what if someone tried to get at the data without the password-what would they see-complete gibberish? 

Secondly is it easy to run software on ubuntu to carry brute force dictionary attacks?

---

### Post by wilee-nilee on 2010-11-04
Boot a Live Cd and you will be in I suspect, maybe not, I'm not really sure. I suspect you can from live cd crtl-f2 gksudo nautilus and have root access, though.

Thats all I'm saying not really knowing your true intentions.

---

### Post by HermanAB on 2010-11-04
Howdy,

There is one simple test that will give you some confidence.  Compress the encrypted data with gzip.  If it compresses, then the data is not random and therefore not encrypted.  If it doesn't compress, then it is probably OK.

Another test is to calculate a histogram of the encrypted data.  It should be a flat line - there should be roughly equal numbers of all values.

A third test is to look for repeating patterns.  You can do that with grep.  You should not find any repeating patterns.  If you do, then the encryption is flawed due to a programming bug.

A fourth simple test is to run the data through the program 'strings'.  It should not find any legible ASCII strings in the data.

A fifth test that you can try is the chi-square test, which is a kind of statistical histogram.

Hope that helps!

---

### Post by noway2 on 2010-11-04
In addition to the above, which you can use to test that your data is encrypted, you might also be interested to know that the FBI confiscated some computers where it had been used and could not decrypt it.  Time to resort to the the $5 wrench.  Google truecrypt and FBI if you are interested.

As an aside, I do wonder if this is at least partially what is behind the recent articles I have seen about the US govt wanting back-doors to encryption software.

---

### Post by dogdo on 2010-11-04
While on the topic what is the best way to store/remember truecrypt passwords? at the moment im using a separate encrypted usb key to store this data.

---

### Post by artie_effim on 2010-11-04
> **dogdo said:**
> Ive made a simple encrypted external hard drive with truecrypt but i want to see how secure the encryption is. 

First off how do i know that the data is encrypted or not? granted for me to see the data i have to give the right password but what if someone tried to get at the data without the password-what would they see-complete gibberish? 

Secondly is it easy to run software on ubuntu to carry brute force dictionary attacks?

Ok, first off TrueCrypt has not undergone any formal certification and accreditation analysis.  From a real security point of view it is TOTALLY UNTRUSTED.  Meaning that a [Common Criteria]("http://en.wikipedia.org/wiki/Common_Criteria") approved lab has not analyzed the product.  The assumption that interdependent security analysis has done the same job as a full C&A effort is false.  The real questions is - do you as a consumer of this product _trust_ that the developers correctly implemented the security requirements.  Having no formal evaluation, you cannot be sure.  (not to turn this into a debate on the CC, it is what we have now and it is the best solution in place at the moment.)

Secondly - it is trivial to run a brute force attack against the product if the attacker has system access and the correct permissions.

---

### Post by jkounis on 2010-11-05
> **artie_effim said:**
> 
Secondly - it is trivial to run a brute force attack against the product if the attacker has system access and the correct permissions.

Yes it is completely trivial. You just need basic programming knowledge, an understanding of the algorithms involved, and a lot of patience. Oh and perhaps a source of heat to keep warm after the Sun extinguishes in about 5 billion years or so and you haven't made much headway testing all the possible keys. (Assuming you have a strong, 50+character password, and we don't develop quantum computers or blow ourselves up in the meantime.)

---

