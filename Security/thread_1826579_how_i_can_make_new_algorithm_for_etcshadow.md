---
title: "how i can make new algorithm for /etc/shadow"
date: 2011-08-16
forum: Security
---

### Post by mr.new on 2011-08-16
[CENTER]
-------------------------------------------------------------
Hello , :D

i have one Question , i use [COLOR=Red]SHA-512[COLOR=Black] algorithm[/COLOR][/COLOR] in the[COLOR=Red] /etc/shadow[/COLOR] File
But i Want to use my[COLOR=Black] lgorithm[/COLOR] ..

[COLOR=Black]how i can remove the sha-512 and use my algoritm ? , [/COLOR]
this is good idea , Because no one can des encrypt it !! He Not Know the algorithm method

and thanks..
[/CENTER]

---

### Post by Thewhistlingwind on 2011-08-16
Maybe, but do you trust your (presumably) untested algorithm versus the trial-by-fire seasoned sha family of algorithms?

Security by design is usually considered superior to security though obscurity.

Regardless, wikipedia is always useful. ([https://secure.wikimedia.org/wikipedia/en/wiki/Shadow_password](https://secure.wikimedia.org/wikipedia/en/wiki/Shadow_password))

I myself however, don't know how to do this.

---

### Post by mr.new on 2011-08-16
thanks my friend for help , i will see it ..
But I was I think is as easy,, ?

---

### Post by scorp123 on 2011-08-17
> **mr.new said:**
>  this is good idea , Because no one can des encrypt it !! He Not Know the algorithm method "Security by obscurity" has been proven time and time again to _NOT_ work. And thus: **Bad idea.**

---

### Post by tubbygweilo on 2011-08-18
Mr New, I may well be wrong but the idea of "rolling your own crypto" seems to be a step too far. 

I feel that the skill, rigour and peer review required of such a project may well be restrictyed to a small self selecting group of people already employed by organisations known by their three letter acronyms. 

When you have completed your project will you be publishing the results of uyour work in this forum?

---

### Post by xenomuta on 2011-08-19
There are many approaches you can take. However, this task requires nice C programming skills and in dept knowledge of how Linux security works.

You could download the shadow package and patch it to support your own crypto algorithm.
OR
You could make your own PAM module to read your algorithm hashes from some other file wile disabling passwords on /etc/shadow

I would recommend you to read the Shadow Password Howto as well:
[http://tldp.org/HOWTO/Shadow-Password-HOWTO.html](http://tldp.org/HOWTO/Shadow-Password-HOWTO.html)
:guitar:
rock on

---

### Post by SeijiSensei on 2011-08-19
I don't really see the point of this.  Remember that the entries in /etc/shadow are hashes.  They can't be decrypted to reveal the passwords.  They can only be brute-forced with a rainbow table.  I doubt that you can roll your own hash algorithm that would be anywhere close to SHA512 in terms of professionalism and extensive testing.

Your efforts would be better spent on making sure you and your users have strong passwords.

---

### Post by mr.new on 2011-08-20
> 
When you have completed your project will you be publishing the results of uyour work in this forum? 	

:rolleyes:

xenomuta

THANKS ,, for this infromation.


> Your efforts would be better spent on making sure you and your users have strong passwords. 	

any hash can be cracked , md5 with good cpu can crack any hash and SHA-*

see this video i cracked SHA-512 hash for other user on my system .

[http://www.mediafire.com/?yr5kz28hj4duc3t](http://www.mediafire.com/?yr5kz28hj4duc3t)

need to good cpu to crack any hash for any strong password for that i want to create new algorithm  .

---

