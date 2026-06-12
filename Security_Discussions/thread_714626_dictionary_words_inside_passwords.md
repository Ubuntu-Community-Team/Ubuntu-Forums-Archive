---
title: "dictionary words inside passwords"
date: 2008-03-04
forum: Security Discussions
---

### Post by pytheas22 on 2008-03-04
This is not explicitly Ubuntu-related, but I'm sure that someone here can provide a good answer.  Anyway, passwords are a subject that everyone should be familiar with, on Linux or not.

My email provider recently began forcing users to create new passwords that fulfill a variety of criteria.  Most of it makes sense: enforce minimum password length, include non-alphanumeric characters and both cases, et cetera.  One of the requirements of the new policy, however, is that the password can't contain a dictionary word, even if it's embedded inside other random strings.  In other words, passwords like  %8F9woRd^ß ! would not be accepted because they contain strings like "woRd."

I'm wondering why they have this requirement.  I understand why it's bad to make a password that's a dictionary word, because it can be cracked easily by going through a wordlist, but I've never heard of a cracker that can look for dictionary words *inside* a password.  Do they exist, or would plain bruteforcing be the only way to crack %8F9woRd^ß ! ?

---

### Post by erginemr on 2008-03-04
None that I know, the cracker should still do a brute force attack even if a part of the password is a known dictrionary word.

You can dupe the e-mail provider's password checker by inserting a number into the word that can be easily remembered such as *"...w1ord...."*

---

### Post by koenn on 2008-03-04
password crack tools that use dictonaries / wordlists these days are aware that it's common for users to take an existing word or a person's name and do some additions to it, such as add a few numbers at the end (Love123), in front (666Mike), use random caps (LoVe) or 'leet translations (l0ve, m1ke), or some other variations such as reversing a word (evol), or any combination of those, which give a resemblence of strong passwords, but are still quite easy to crack becauser the crack tool has subroutines to check for such common variation schemes to each word in its dictionary.

Your ISP probably wants to prevent the use of these resonably weak passwords by simply checking if there is a dictionary word in your password.
You're right that the occurence of a dictionary word in a random string can be in fact quite strong (as the examle you show), but probably it's to complicated / time consuming for the ISP password checker to take that into account - testing on the mere presense of a dictionary word without paying attention to what else it is wrapped in, is easier/faster/ ...

---

### Post by bodhi.zazen on 2008-03-04
Umm ... The fact that they can detect the string "word" shows the weakness you are questioning, no ?

I suggest a password using your SS# or birthdays ...

J/K :lolflag:

---

### Post by pytheas22 on 2008-03-04
Thanks for the replies.

> Your ISP probably wants to prevent the use of these resonably weak passwords by simply checking if there is a dictionary word in your password.

This is true, and I admit that I hadn't thought of using variations on user names or common words as a consideration of the ISP.  But on the other hand, I'm not sure it's a very competent rule, as it would be perfectly fine, by my ISP's rules, to embed reversed words in passwords.  So *eVol478! would pass the test, even though a good cracker might realize that it's just 'love' reversed with a case change and some extra characters.

Also, by not allowing dictionary words inside passwords, I think that the ISP encourages people to keep passwords shorter.  I've always been told that password length is the single most important factor, and like to make long passwords by using sentences or fake email addresses, like 'this Is good@fake passwords.com'  But that password, which would take a huge amount of time to brute force simply because it's long, would not be permitted; *eVol478! , which is short enough to make bruteforcing a possibility, would.  And the useful suggestion above of substituting letters in for numbers is also against the ISP's rules, as it checks for strings like '3lit3' inside the password and rejects them if found.

Anyway, none of this is that important, but it was interesting and I wanted to make sure that there are indeed no crackers that can look for a word inside a password.  Thanks again for the information.

---

