---
title: "Private Directory"
date: 2009-06-24
forum: Security
---

### Post by ftabor on 2009-06-24
I've just installed ecryptfs-utils and all went well.  My question is, if physical access can be gained to the computer, and your login password is compromised, then the files in the Private folder can be accessed.  Correct?  

Is it possible to use a different pass phrase to mount Private, different from your login password?  The purpose of the encrypted folder is defeated if someone can get your login.

I suppose, as a single user, I need to encrypt the whole computer.

---

### Post by HermanAB on 2009-06-25
Howdy,

The standard way to encrypt file systems is LUKS with AES256.  The more things you encrypt, the better.  However, even the defence force doesn't encrypt everything.  You have to assess the risk and then apply an appropriate solution.

If your threat is your little kid sister, then you only need a good password.  That should be fine till she turns twelve.

If your threat is your dorm room buddies, then you should encrypt your /home partition with LUKS.

If your threat is the government, then you should emigrate to a friendlier country.

If you cannot emigrate, then you should encrypt as much of the machine as possible (/, /swap, /home), cross your fingers and say six Hail Ma-rys every day (or pay suitable homage to the god favoured by the majority).

Hope that helps!

---

### Post by bodhi.zazen on 2009-06-25
> **ftabor said:**
> I've just installed ecryptfs-utils and all went well.  My question is, if physical access can be gained to the computer, and your login password is compromised, then the files in the Private folder can be accessed.  Correct?  

Is it possible to use a different pass phrase to mount Private, different from your login password?  The purpose of the encrypted folder is defeated if someone can get your login.

I suppose, as a single user, I need to encrypt the whole computer.

Yes that is correct. 

You can use ecryptfs to encrypt a separate directory if you wish, I have an overvie here :

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

Otherwise, as HermanAB suggested, re-install w/ LUKS (ubuntu use the alternate CD).

---

### Post by ftabor on 2009-06-25
> **HermanAB said:**
> Howdy,

The standard way to encrypt file systems is LUKS with AES256.  The more things you encrypt, the better.  However, even the defence force doesn't encrypt everything.  You have to assess the risk and then apply an appropriate solution.

If your threat is your little kid sister, then you only need a good password.  That should be fine till she turns twelve.

If your threat is your dorm room buddies, then you should encrypt your /home partition with LUKS.

If your threat is the government, then you should emigrate to a friendlier country.

If you cannot emigrate, then you should encrypt as much of the machine as possible (/, /swap, /home), cross your fingers and say six Hail Ma-rys every day (or pay suitable homage to the god favoured by the majority).

Hope that helps!

Wife and a lawyer.  I've removed to separate external storage what documents and files I need to safeguard, and it's in a secure place.

What I really need to protect is stuff like the passwords stored in Firefox, and another file I have with my many numerous passwords that are impossible to remember.  That is an obscurely named file that's hidden deep in a directory tree in root.  You would really have to know what to look for to find it, but, you never know.

I have sacrificed a goat, we'll just have to wait and see.

---

### Post by ftabor on 2009-06-25
> **bodhi.zazen said:**
> Yes that is correct. 

You can use ecryptfs to encrypt a separate directory if you wish, I have an overvie here :

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

Otherwise, as HermanAB suggested, re-install w/ LUKS (ubuntu use the alternate CD).


I think I can make Ecryptfs work.  If I make the encrypted directory, yada yada, then change my password, then I have to supply the original password to mount the private directory.  That should work.  A little extra work maybe, but since I rarely shut down, it won't be that much of a problem.

Since this is a laptop we're talking about, that stays with me most of the time, I'll have time to do a restart or a shut down, unless they send a big ******* to collect it.

Thanks, I'll work on this.  I'd hate to have to reinstall.  I have my home on a separate partition, but it's taken me 2 months to get this thing to where it is, I'd hate to have to start over.

---

### Post by Divider on 2009-06-25
Simplest way to never worry about encryption, use a live cd and a encrypted 16gb flash drive with AES256 or higher (ironkey) :popcorn:

---

### Post by Agent ME on 2009-06-25
> **ftabor said:**
> My question is, if physical access can be gained to the computer, and your login password is compromised, then the files in the Private folder can be accessed.  Correct?  
...

I suppose, as a single user, I need to encrypt the whole computer.
If someone finds out your encryption password, then your encryption is broken. Same thing if you encrypt your whole computer.

---

### Post by ftabor on 2009-06-25
Using TrueCrypt, your encryption password is a whole lot harder to break with a brute force cracker.

---

