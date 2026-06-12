---
title: "Gcalctool 5.28.2"
date: 2012-11-26
forum: The Cafe
---

### Post by ParadoxBlue on 2012-11-26
38 plus 41 divided by 2 equals 58.5? Did I miss a memo? Have mathematic operations changed? Does this program not support chain calculations? I was looking for $4.71 in my checking account. This could be the problem. Anyone had anything like this happen? I ask a lot of questions don't I? Any comments appreciated.

Thanks for any help, 
Robert

---

### Post by Warpnow on 2012-11-27
> **ParadoxBlue said:**
> 38 plus 41 divided by 2 equals 58.5? Did I miss a memo? Have mathematic operations changed? Does this program not support chain calculations? I was looking for $4.71 in my checking account. This could be the problem. Anyone had anything like this happen? I ask a lot of questions don't I? Any comments appreciated.

Thanks for any help, 
Robert

Most math engines and calculators work left to right, not through predetermined order of operations, and rely on you to set it up the right way.

---

### Post by pkadeel on 2012-11-27
> **ParadoxBlue said:**
> 38 plus 41 divided by 2 equals 58.5? Did I miss a memo? Have mathematic operations changed? Does this program not support chain calculations? I was looking for $4.71 in my checking account. This could be the problem. Anyone had anything like this happen? I ask a lot of questions don't I? Any comments appreciated.

Thanks for any help, 
Robert
This is because of operator precedence in mathematics which is then used in programming languages. multiplication and division get precedence over addition and subtraction if no parenthesis are given so in your case
38 + 41 / 2 has become 38 + (41 / 2) which is equal to 58.5

---

### Post by Warpnow on 2012-11-27
> **pkadeel said:**
> This is because of operator precedence in mathematics which is then used in programming languages. multiplication and division get precedence over addition and subtraction if no parenthesis are given so in your case
38 + 41 / 2 has become 38 + (41 / 2) which is equal to 58.5

+1

PEMDAS

Its gcalctool doing it right, and windows calculator (in basic mode) and most basic calculators doing it wrong. If you switch windows calculator to scientific mode it calculates in the same way gcalctool does.

---

### Post by rai4shu2 on 2012-11-27
It's not so much that calculators are normally wrong as much as they normally assume that you're immediately performing some operation. For example, if you punch in 2 + 2, a normal calculator will immediately perform the operation. This is for the convenience of people doing tabulations. It looks as though Gnome Calculator is being developer-ized (that is, redesigned for the convenience of a more developer-oriented approach to doing calculations, as opposed to the way everyone else does it).

---

### Post by ugm6hr on 2012-11-27
> **pkadeel said:**
> This is because of operator precedence in mathematics 

+1
Ask any high school student.

Irrespective of whether programming is involved, mathematics (e.g. as used in algebra etc) has always been this way, even without use of calculators.

---

