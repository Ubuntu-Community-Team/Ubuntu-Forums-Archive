---
title: "Top 25 Most Dangerous Programming Errors"
date: 2010-02-17
forum: The Cafe
---

### Post by Sporkman on 2010-02-17
Don't make these mistakes, beeyatches!

[http://cwe.mitre.org/top25/#Listing](http://cwe.mitre.org/top25/#Listing)

---

### Post by 3rdalbum on 2010-02-17
A pretty dangerous programming error is when programmers believe that the OS' security systems are there to hinder them or to make things more difficult for the end user.

When you make this error, you end off with Mac OS X.

---

### Post by TheOrangePeanut on 2010-02-17
I'm surprised the article doesn't say anything about rounding errors in floating point calculations.  If I remember correctly, a rounding error caused the loss of a million dollar Mars rover a few years ago.  Imagine if that were some kind of auto-pilot software... talk about dangerous!

---

### Post by markbuntu on 2010-02-18
Or not checking what measurement base is used. The Hubble telescope main mirror was built wrong because the specs were assumed to be metric but were in inches or visa versa. OOOPS

The biggest problem in programming is uninitialized variables. This opens doors for much mischeif and many headaches....

---

### Post by Simon17 on 2010-02-18
While round-off errors and unit errors are costly, they aren't security flaws (that's what the list was about).

---

### Post by Firestem4 on 2010-02-18
> **markbuntu said:**
> Or not checking what measurement base is used. The Hubble telescope main mirror was built wrong because the specs were assumed to be metric but were in inches or visa versa. OOOPS

The biggest problem in programming is uninitialized variables. This opens doors for much mischeif and many headaches....

I'm a newbie to programming (currently learning Java). Can you explain how leaving a variable uninitialized can create problems? I can assume but I don't know nearly enough about memory, pointers, et al.

---

### Post by markbuntu on 2010-02-19
If you leave a variable uninitialized someone could put something in there that can create a stack/buffer overflow which can crash the process/system or could even redirect the process to elsewhere. Redirection is a favorite hacker attack used to gain access with java and php/mysql.

This problem generates a lot of security related bug fixes.

---

### Post by Nevon on 2010-02-19
#11- Use of Hard-coded Credentials. 

Seriously. Who would be that stupid?

---

### Post by doas777 on 2010-02-19
> **markbuntu said:**
> Or not checking what measurement base is used. The Hubble telescope main mirror was built wrong because the specs were assumed to be metric but were in inches or visa versa. OOOPS

The biggest problem in programming is uninitialized variables. This opens doors for much mischeif and many headaches....


but remember the ssh key debacle last year. a dev saw an uninitialized var, and assumed it was a flaw, when in fact it was there to use the entrophy of ram as a random seed, iirc. once it was initialized, the randomness became far more psudo than random.

---

### Post by doas777 on 2010-02-19
> **Nevon said:**
> #11- Use of Hard-coded Credentials. 

Seriously. Who would be that stupid?


look into MSs recomendations on storage of database credentials in an asp site. 
[http://weblogs.asp.net/owscott/archive/2005/08/26/Using-connection-strings-from-web.config-in-ASP.NET-v2.0.aspx](http://weblogs.asp.net/owscott/archive/2005/08/26/Using-connection-strings-from-web.config-in-ASP.NET-v2.0.aspx)

---

### Post by lykwydchykyn on 2010-02-19
> **Nevon said:**
> #11- Use of Hard-coded Credentials. 

Seriously. Who would be that stupid?

I wouldn't put it past a few of the local vertical software vendors I've had to work with.  It's bad enough some of them use the same admin password which they haven't changed for decades for all their clients.

---

### Post by kernelhaxor on 2010-02-19
> **doas777 said:**
> look into MSs recomendations on storage of database credentials in an asp site. 
[http://weblogs.asp.net/owscott/archive/2005/08/26/Using-connection-strings-from-web.config-in-ASP.NET-v2.0.aspx](http://weblogs.asp.net/owscott/archive/2005/08/26/Using-connection-strings-from-web.config-in-ASP.NET-v2.0.aspx)

That's a config file .. I don't see anything wrong with storing the credentials there .. where else would you want to put the credentials?

---

### Post by koenn on 2010-02-19
> **lykwydchykyn said:**
> I wouldn't put it past a few of the local vertical software vendors I've had to work with.  It's bad enough some of them use the same admin password which they haven't changed for decades for all their clients.
It's that you're in Tennessee ... 
I could have sworn you were talking about some local vertical software vendors I've to work with ...

---

### Post by doas777 on 2010-02-19
> **kernelhaxor said:**
> That's a config file .. I don't see anything wrong with storing the credentials there .. where else would you want to put the credentials?


well, usually you cannot use integrated authenticatiion outside your domain, so your connection string is going to look like:
```

"Data Source = <server>;Initial Catalog=<db>;User ID=<sql username>; password=<passwd>"

```
the best goal would be to use an auth mechanism like krebros that didn't require passwords, but that is unlikely to happen anytime soon.

---

### Post by matthewbpt on 2010-02-19
> I'm surprised the article doesn't say anything about rounding errors in floating point calculations. If I remember correctly, a rounding error caused the loss of a million dollar Mars rover a few years ago. Imagine if that were some kind of auto-pilot software... talk about dangerous!

I think you mean the accident with the Mars Climate Orbiter, which was lost because of confusion between metric and imperial units. [http://en.wikipedia.org/wiki/Mars_Climate_Orbiter#The_metric.2Fimperial_mix-up](http://en.wikipedia.org/wiki/Mars_Climate_Orbiter#The_metric.2Fimperial_mix-up)

---

### Post by V for Vincent on 2010-02-19
> **doas777 said:**
> but remember the ssh key debacle last year. a dev saw an uninitialized var, and assumed it was a flaw, when in fact it was there to use the entrophy of ram as a random seed, iirc. once it was initialized, the randomness became far more psudo than random.

I kind of wonder why there was no implementation comment there, though...

---

### Post by donkyhotay on 2010-02-19
> **doas777 said:**
> but remember the ssh key debacle last year. a dev saw an uninitialized var, and assumed it was a flaw, when in fact it was there to use the entrophy of ram as a random seed, iirc. once it was initialized, the randomness became far more psudo than random.

> **V for Vincent said:**
> I kind of wonder why there was no implementation comment there, though...

Exactly, if you have something that is intentionally 'wrong' it's important comment it in the code and let later devs now why it's there. I wouldn't blame the dev for changing the var, I would blame the dev who put it there and didn't properly comment/document his code.

---

### Post by doas777 on 2010-02-19
> **V for Vincent said:**
> I kind of wonder why there was no implementation comment there, though...

agreed. I would have added one. 

to comment or not to comment is a thin line to walk. too many comments make the code impossible to read (as a python script i commented for a non-programmer friend to read proved), but too few leads to maintenance mishaps. unfortunately the only way to get the right balance is to know the person that reads it, and their skill/comfort level.
personally i comment blocks of code (methods, etc), but only comment line items if they are truely unintuitive.

---

### Post by Simon17 on 2010-02-19
> **v for vincent said:**
> i kind of wonder why there was no implementation comment there, though...

bwahahaha!

---

### Post by doas777 on 2010-02-19
> **Simon17 said:**
> bwahahaha!
i've known since the breakfast club that you could not be trusted!
;)

---

