---
title: "Creating passwords with pwgen"
date: 2012-08-27
forum: Security
---

### Post by DanR01 on 2012-08-27
I've been playing around with pwgen to create strong passwords. I've created a file using the command 

```
pwgen -scnyC 64 40000 > passwordfile
```To create a text file containing 40,000 lines of 64 characters

The output looks like this:

```
mE'4PMM1(lS[Mz5ZCH*`M0D:i.g{BW3C)?F@UK/W.FaC<cWx*a/r4cq+[2>2'{w5
2}oWKK7<G3-==&10:a?VS_ih^nd//J/+~kBx"cI/|m@\{~s2<-8P"+Y6>->uphl#
O'O3b_9\uHOWKjdI^[~MyL2$d%2"\Cy5]lL9WU.8;v=xF6|c|8F*ujqR41SG7>[q
```I would then pick a line eg 34,124 and a start point eg character 13 and select sequential data of 30-64 characters and use this as a password. I would only have to remember the start point and the password length.

Are there any downsides to using this approach? How large would the initial file have to be to have sufficient entropy to withstand attacks if the file was recovered by someone with an interest in recovering the password?

---

### Post by Ms. Daisy on 2012-08-27
Seems reasonable.  In fact there's a public version of your approach that seemed decent as well: 
[http://www.passwordcard.org/en](http://www.passwordcard.org/en)

Downsides: You would need backups of the 40000 character file. I would print it out as well as digitally back it up in a few locations.

Calculate the possible passwords from your40000 character file- if the attacker doesn't know the length of your password then the number of guesses he'd have to make increase enormously.

---

### Post by DanR01 on 2012-08-27
Thanks for the link Ms Daisy.

The file is actually 40,00 x 64 characters so 2,560,000 in total.

I did try and calculate the number of possibilities but gave up as I didn't know how to account for strings of letters that were likely to be repeated in the file which would decrease the entropy. 

Ars Techica has an interesting article which is what got me thinking about it

[http://arstechnica.com/security/2012/08/passwords-under-assault/](http://arstechnica.com/security/2012/08/passwords-under-assault/)

---

### Post by rookcifer on 2012-08-27
> **DanR01 said:**
> Are there any downsides to using this approach? How large would the initial file have to be to have sufficient entropy to withstand attacks if the file was recovered by someone with an interest in recovering the password?

No downsides.  You don't even need pwgen to create passwords.  You can simply use /dev/urandom to do that.  For instance:

```
cat /dev/urandom| tr -dc 'a-zA-Z0-9' | fold -w 10| head -n 4
```

Change the fold -w 10 to whatever length of password you want.  Change the "head -n 4" to generate however many passwords you need.

This technique uses the built in PRNG /dev/urandom, which is cryptographically strong.  

I wrote a password generator with a GUI a while back.  It's on Launchpad in the PPA's but I haven't updated the package for 12.04 or 11.10.

---

### Post by Hungry Man on 2012-08-27
Your password doesn't have to by cryptographically secure. Entropy is largely irrelevant to cracking.

You're either on a dictionary or you aren't. It's **** easy to not be on one and still have a reasonably easy to remember password.

I suggest instead of dealing with 40 character passwords that can't be remembered you try dealing with basic algorithms on your own to create one ex:

padding + Sitename+a friends birthday + 2 random symbols + padding

<UbuntuForums12092()>

Easy to remember and really strong.

Alternatively (and more secure) you can replace the site name with a favorite song.

-PachebelCannon71890$%-

This likely has much less 'entropy' than a random string of its size but it doesn't matter. You won't find a dictionary with that on it and hackers don't get points for getting close. It's still ridiculously long/ impossible to bruteforce.

---

