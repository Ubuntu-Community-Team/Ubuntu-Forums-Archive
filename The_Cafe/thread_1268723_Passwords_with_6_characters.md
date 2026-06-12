---
title: "Passwords with 6 characters?"
date: 2009-09-17
forum: The Cafe
---

### Post by carlosgs91 on 2009-09-17
.

---

### Post by Skripka on 2009-09-17
Assuming we are limiting ourselves to alphanumeric passwords-no symbols, and case-sesative:

There would be 10 numbers, and 26x2 letters (for upper and lower case).  So you'd have 62^6 possiblities.

---

### Post by Bachstelze on 2009-09-17
You can also count symbols like &#@!, etc.. So yes, assuming the password has been generated randomly (with e.g. [font=monospace]makepasswd[/font], six characters is a perfectly fine length for non-critical purposes.

---

### Post by wojox on 2009-09-17
If the password can be made up of upper and lower case letters (52 in all), plus the ten digits 0-9? Now there are 62^6 six character passwords (about fifty seven thousand million.)

---

### Post by carlosgs91 on 2009-09-17
.

---

### Post by Mornedhel on 2009-09-17
Most password brute force attacks are based on password dictionaries though, so they don't have as large a search space as every possible combination of 6 characters. It's simple : users don't want to have to remember a random combination, they want to remember a word or at best, a jumbled word.

---

### Post by carlosgs91 on 2009-09-17
.

---

### Post by Mornedhel on 2009-09-17
Password dictionaries are not language dictionaries (though they include them). For instance, a common password used to be "gandalf". A not so subtle variation would be "g4nd4lf" (or "mellon").

---

### Post by MaxIBoy on 2009-09-17
Also, I imagine password dictionaries contain auto-generated variants for each word (swapping @ for A, 1 for I, vowels removed, a word with the number 1 at the end, etc.) 


Finally, there are things like rainbow tables which make it more feasible to crack passwords.

---

### Post by scragar on 2009-09-17
> **Mornedhel said:**
> Password dictionaries are not language dictionaries (though they include them). For instance, a common password used to be "gandalf". A not so subtle variation would be "g4nd4lf" (or "mellon").

I went through a phase of using "f14dn49" :p (gandalf in 1337 backwards), I considered it quite secure at the time.

---

### Post by MaxIBoy on 2009-09-18
You can check your password easily using Ophcrack, a rainbow-table based password cracking tool. 

[http://www.codinghorror.com/blog/archives/000949.html](http://www.codinghorror.com/blog/archives/000949.html)

Apparently it cracked the password Fgpyyih804423 in 160 seconds flat.



UNIX passwords are immune to this because they "salt" the hash.

---

