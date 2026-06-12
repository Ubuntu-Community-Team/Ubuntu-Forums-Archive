---
title: "Does ubuntu use salts in Password Hashing?"
date: 2009-07-28
forum: Security
---

### Post by oomar on 2009-07-28
I recently got into rainbow tables and the like and cracked several windows computers in an average of under 5 minutes. Now im curious as to the extent you can use rainbow tables to crack. I started reading and i read about the use of salts in hashing the password. Does ubuntu use a salt when making a password hash? Cause i would feel a hell of a lot safer if it did lol

also to what extent can you use rainbnow tables to crack things? is it ONLY for hashed passwords?

---

### Post by cdenley on 2009-07-28
Yes, ubuntu/linux uses salts to store passwords. If you want to see your password hash:
```

sudo getent shadow $USER|cut -d : -f 2

```
**DON'T POST THAT OUTPUT**

If you want to generate a SHA-512 password hash:
```

mkpasswd -m SHA-512

```
or MD5:
```

mkpasswd -m md5

```

You will see something like this:
```

$6$[COLOR="Red"]E3G2M9ETLCseq7zT[/COLOR]$[COLOR="Blue"]sx9/ZqPRFJG2mePE532hqwmFKecp1OXRHx2k5uOGey8dLp7y9JhlkDU.Q1CnQv0I2ZKGw388wD3HkeHVrUnY/.[/COLOR]

```

$6$ means SHA-512.
$1$ means MD5, what ubuntu used to use, I think prior to 8.04.

The red portion is the salt. The blue portion is the actual hashed data. All the different parts are seperated by "$".

And yes, rainbow tables are only used to crack hashed data, as far as I know.

---

### Post by shaggy999 on 2009-07-28
Here's what I don't get. If the salt is delimited by the $ signs then what use is it? All you have to do is ignore those sections of the password when using your rainbow tables to figure out the password.

I was always under the impression that when someone enters a password it does something like 'hash(salt+password)'

That way when somebody gets the password file they won't be able to figure out what the password was because a match from the rainbow tables will produce 'salt+password' but when you type 'salt+password' into the password box it doesn't work.

---

### Post by oomar on 2009-07-28
well the whole idea of rainbow tables is that you pre compute all possible hashes. Even just using the hashes its a lot of space used. Now with salts you now have to precompute ALL of the possible salt combinations which REALLY increases the time of a crack. basically you would have to bruteforce it to find the (salt+password) and once you find that you have to brute force THAT to just find the salt and remove that. from what ive heard it pretty much makes it unreasonable to rainbow crack it and are just better off with a normal brute force. idk i think thats a halfway decent explanation

---

### Post by shaggy999 on 2009-07-28
> **oomar said:**
> well the whole idea of rainbow tables is that you pre compute all possible hashes. Even just using the hashes its a lot of space used. Now with salts you now have to precompute ALL of the possible salt combinations which REALLY increases the time of a crack. basically you would have to bruteforce it to find the (salt+password) and once you find that you have to brute force THAT to just find the salt and remove that. from what ive heard it pretty much makes it unreasonable to rainbow crack it and are just better off with a normal brute force. idk i think thats a halfway decent explanation

I understand the theory. It's the implementation I don't understand.

> Now with salts you now have to precompute ALL of the possible salt combinations

No, you don't. Not with the way it's implemented as I see it. The salt is very specifically set aside from the password. For example:

```
$6$E3G2M9ETLCseq7zT$sx9/ZqPRFJG2mePE532hqwmFKecp1OXRHx2k5uOGey8dLp7y9JhlkDU.Q1CnQv0I2ZKGw388wD3HkeHVrUnY/.
```

Clearly the salt is E3G2M9ETLCseq7zT and you want to perform the rainbow tables crack on: sx9/ZqPRFJG2mePE532hqwmFKecp1OXRHx2k5uOGey8dLp7y9JhlkDU.Q1CnQv0I2ZKGw388wD3HkeHVrUnY/.

This is why I'm confused. The salt is not adding any security as I see it.

---

### Post by Mister.Vash on 2009-07-28
The salt changes the hash, as an example, using salt0000 and salt0001 as the salt, you can see the hash changes for the password examplepassword

So basically, for the rainbow tables to be useful, you would need to know what the salt was to have it correlate as different salts are going to give you different hashes

mkpasswd --hash=MD5 -S salt0000 examplepassword
$1$salt0000$dfkWDoA.ln2yWeNY2RNPx.

mkpasswd --hash=MD5 -S salt0001 examplepassword
$1$salt0001$qAhvW6XuDLCU.K4Av7ZiW0

---

### Post by cdenley on 2009-07-29
> **Mister.Vash said:**
> 
So basically, for the rainbow tables to be useful, you would need to know what the salt was to have it correlate as different salts are going to give you different hashes

You would need to know the salt before generating the rainbow tables, unless you have a rainbow table for every possible salt. As explained, the hash at the end was generated with something like hash(password+salt). The rainbow table would have to match up the resulting hash found in /etc/shadow with password+salt.

The salt must also be available in order to check passwords given during authentication so the login module can do a hash(password+salt) then compare with the value stored in /etc/shadow. However, even though the attacker knows the salt if they know the hash, it still prevents them from using pre-computed hashes, so their only option is to do a hash(password+salt) with every password they guess, which takes a lot longer.

---

### Post by shaggy999 on 2009-07-29
That makes sense. Now I understand. Thanks. :)

---

### Post by J V on 2010-03-30
I beleive in letting dead threads lie but, I presume the salt is random generated?

---

### Post by cdenley on 2010-03-30
> **J V said:**
> I beleive in letting dead threads lie but, I presume the salt is random generated?

Yes.

---

### Post by rookcifer on 2010-03-30
> **oomar said:**
> I recently got into rainbow tables and the like and cracked several windows computers in an average of under 5 minutes. 

It must have been an XP box since XP has a very weak password hash with no salting.  This has been fixed with Vista/7 (passwords are now salted).

Linux has been using salted password hashes for a long time.  Those rainbow tables ain't gonna work over here.

---

### Post by cdenley on 2010-03-31
> **rookcifer said:**
> It must have been an XP box since XP has a very weak password hash with no salting.  This has been fixed with Vista/7 (passwords are now salted).

Linux has been using salted password hashes for a long time.  Those rainbow tables ain't gonna work over here.

I'm pretty sure Vista (and probably windows 7) password hashes are still easily cracked with rainbow tables. They dropped LM hashes which I think were for backwards compatibility with Windows 98, and only use NTLM which are stronger, but still don't use a random salt. I cracked some vista password hashes quite quickly a while ago. I haven't tried Windows 7, yet.

---

