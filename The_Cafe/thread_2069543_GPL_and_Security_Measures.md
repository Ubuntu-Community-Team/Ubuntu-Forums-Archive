---
title: "GPL and Security Measures"
date: 2012-10-11
forum: The Cafe
---

### Post by ki4jgt on 2012-10-11
If you develop a security measure for a GPLd program you've written which involves a secret variable, do you have to release said variable with the source code of said program when requested to do so?

---

### Post by Dave_L on 2012-10-11
What is a "secret variable"? How does it differ from other variables?

The GPL requires that the complete source code be provided. The intent is that anyone who receives a copy of the program is fully able to use it, study it, modify it and redistribute it.

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

---

### Post by GeneralZod on 2012-10-11
> **ki4jgt said:**
> If you develop a security measure for a GPLd program you've written which involves a secret variable, do you have to release said variable with the source code of said program when requested to do so?

If *you've* written it by yourself and are the sole copyright holder, you can distribute whatever portions of the source you want.

---

### Post by JDShu on 2012-10-11
Why would you have a "secret variable" in your security program? That makes no sense.

---

### Post by Grenage on 2012-10-11
Security through obscurity is a fallacy.  If you have written the code, then you can obviously set the licence terms; you don't have to apply the GPL to an entire application, do you?

---

### Post by Dave_L on 2012-10-11
> **Grenage said:**
> Security through obscurity is a fallacy.  If you have written the code, then you can obviously set the licence terms; you don't have to apply the GPL to an entire application, do you?

If an essential component of the application is not licensed as GPL, then could the application be considered GPL? I suppose we can't discuss this properly until we find out what "secret variable" means. :)

---

### Post by ki4jgt on 2012-10-11
> **Grenage said:**
> Security through obscurity is a fallacy.  If you have written the code, then you can obviously set the licence terms; you don't have to apply the GPL to an entire application, do you?

Which is why we have public and private GPG keys.

> **Dave_L said:**
> If an essential component of the application is not licensed as GPL, then could the application be considered GPL? I suppose we can't discuss this properly until we find out what "secret variable" means. :)

I have an application which upon execution reports to a server (in concept b/c I haven't coded it yet). It combines a code word (the variable) and the current time and then hashes them together, to prove that it is the program and not someone trying to hack the system. The question now, is if I don't include the variable in the program, can I still distribute it under the GPL?

---

### Post by Grenage on 2012-10-11
> **ki4jgt said:**
> Which is why we have public and private GPG keys.

That's not quite the same thing. ;)

While that sounds like a system that could be cracked in under five minutes, why not just make the variable.. variable?  If it can be assigned by the user, then the code base can be open; I'm sure you have a reason for not doing so.

The application can't be considered GPL if you've got closed source, but could be if the closed source was a bolt-on.  You could of course use another licence, but you already know that. ^^

---

### Post by ki4jgt on 2012-10-11
> **Grenage said:**
> That's not quite the same thing. ;)

While that sounds like a system that could be cracked in under five minutes, why not just make the variable.. variable?  If it can be assigned by the user, then the code base can be open; I'm sure you have a reason for not doing so.

The application can't be considered GPL if you've got closed source, but could be if the closed source was a bolt-on.  You could of course use another licence, but you already know that. ^^

Well, I need a way to verify that the program is the actual thing sending me the message of completion (and not a bot). I'm trying to prevent automated bots from reporting multiple times that the task has been completed. It has to do with file downloading. Basically the program will allow webmasters to embed files within their sites. Then when a user downloads the file, the program will fetch an ad to display (it's written in JAVA). The site owner will get half of the profit for every ad shown. Have any other suggestions for a way to do this?

---

### Post by ssam on 2012-10-12
> **ki4jgt said:**
> Well, I need a way to verify that the program is the actual thing sending me the message of completion (and not a bot). I'm trying to prevent automated bots from reporting multiple times that the task has been completed. It has to do with file downloading. Basically the program will allow webmasters to embed files within their sites. Then when a user downloads the file, the program will fetch an ad to display (it's written in JAVA). The site owner will get half of the profit for every ad shown. Have any other suggestions for a way to do this?

The most fundamental freedom of free software is that the user can modify the programs behaviour. so for example i might want to modify your program to not display the adverts, because i consider seeing adverts to be a distracting anti-feature.

You seem to want to make piece of software that the user can't modify, (or at least that you can spot and reject modified versions).

But, it sounds like you are also interested in offering your source code to the community (as long you can do so without compromising your main goal). That is admirable, and i think possible. There are a few ways you might be able to do this.

* You could write the software, and release it as an opensource (GPL) project. Then, because you still own the copyright to the code (you wrote it all), you could make a slight modified version, with your secret extra code, and release that only as a binary. You will need to make sure that you have not used anyone else's GPL code in your program, and that all the libraries you make use of allow linking into a closed program (eg LGPL)

* You could split your program into bits and release some of them as LGPL or BSD/Apache licence. Then you could write a closed source program, that makes use of those libraries. 

Not being able to hide secrets in source code, is not directly related to security. Look at openssh, openssl, gpg, firefox etc. The are all opensource, and they all implement industry leading secure communication and authentication. There are closed source programs that do similar, and they are not in general any more secure.

So suppose your program has a secret number in it. and it sends a message to your server using that secret number. what is to stop an attacker listening to your network traffic? what stops them decompiling your binary? just keeping the source secret, does not solve much.

---

### Post by ki4jgt on 2012-10-12
> **ssam said:**
> The most fundamental freedom of free software is that the user can modify the programs behaviour. so for example i might want to modify your program to not display the adverts, because i consider seeing adverts to be a distracting anti-feature.

You seem to want to make piece of software that the user can't modify, (or at least that you can spot and reject modified versions).

But, it sounds like you are also interested in offering your source code to the community (as long you can do so without compromising your main goal). That is admirable, and i think possible. There are a few ways you might be able to do this.

* You could write the software, and release it as an opensource (GPL) project. Then, because you still own the copyright to the code (you wrote it all), you could make a slight modified version, with your secret extra code, and release that only as a binary. You will need to make sure that you have not used anyone else's GPL code in your program, and that all the libraries you make use of allow linking into a closed program (eg LGPL)

* You could split your program into bits and release some of them as LGPL or BSD/Apache licence. Then you could write a closed source program, that makes use of those libraries. 

Not being able to hide secrets in source code, is not directly related to security. Look at openssh, openssl, gpg, firefox etc. The are all opensource, and they all implement industry leading secure communication and authentication. There are closed source programs that do similar, and they are not in general any more secure.

So suppose your program has a secret number in it. and it sends a message to your server using that secret number. what is to stop an attacker listening to your network traffic? what stops them decompiling your binary? just keeping the source secret, does not solve much.

I was going under the concept that hashing the secret + the current time together using sha256 would enable me to authenticate said program but I have been informed that by using a java decompiler, one may indeed obtain something as trivial as a single variable. . . My problem arises in that I can't trust users to be honest about download hits. Money is a POWERFUL motivator to cheat the system. This is sad in and of itself, but I am open to other suggestions as well which would keep my program completely open sourced. I just haven't been able to come up with a concept as simple as a secret yet.

---

