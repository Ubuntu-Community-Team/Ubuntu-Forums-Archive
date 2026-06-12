---
title: "Clear passwords visible in 8.10"
date: 2009-04-02
forum: Security
---

### Post by grunge09 on 2009-04-02
I was using terminal to run a sudo command and when it asks for a password when you type it in incorrectly and press enter and IF you are quick and retype it BEFORE the command prompt comes up what you type (i.e. your password) is clearly visible.  Bad if someone is looking over your shoulder huh.  

Once the password prompt comes up it is not visible until you again mistype and press enter then quickly retype before the password prompt comes back up.

Normally one would wait until the prompt comes up to retype but for those of us that are impatient our passwords can be compromised.

---

### Post by albinootje on 2009-04-02
> **grunge09 said:**
> I was using terminal to run a sudo command and when it asks for a password when you type it in incorrectly and press enter and IF you are quick and retype it BEFORE the command prompt comes up what you type (i.e. your password) is clearly visible.  Bad if someone is looking over your shoulder huh.  


Doesn't seem to be in the bug list for sudo :
[https://bugs.launchpad.net/ubuntu/+source/sudo](https://bugs.launchpad.net/ubuntu/+source/sudo)

But it sounds more like an user problem to me.
Typing in the password fast is one thing which I can understand, but being fast enough to see that you have to wait for the prompt again is also important imho.

---

### Post by bodhi.zazen on 2009-04-02
While you may report is as a bug if you wish, I am not sure it is a bug in sudo.

I would imagine it is a function of your shell as once you hit the enter key sudo is finished reading. Your key input is appearing while the shell is processing your command.

you are talking wither very fast typing, a very slow computer, or a very CPU intense command as I assume you have to type

sudo -> enter password -> see the password failed -> enter password -> see the password failed -> enter password -> see the password failed -> 

(3 password attempts)

now re-enter sudo command and your password all in the blink of an eye, between the time when sudo exits and you get your prompt back ?

I am not sure I buy you can in fact type that fast.

I am betting you are typing after you entered your password a second time while you are waiting for the terminal to process your password without paying attention to what you are doing.

I suggest you chill out (no offense intended). You really need to pay attention to what you are doing.

If you type your password at the prompt it is there for all to see as well. Is this a bug in bash ? I think not. 

So, IMO, sudo works just fine, and the problem is you are typing your password indiscriminately, without paying attention to what you are doing.

:popcorn:

---

### Post by kpatz on 2009-04-02
Next time just wait for the prompt to appear before typing your password.

If you jump the gun, and someone sees you type it, just change your password afterward.  Problem solved. ;)

It's not just sudo either.  Any password prompt can do the same thing.  The login password prompt can do this as well, if you type too soon.  Or if you miss the enter key and start typing your password at the login prompt.

Not really a bug, just a "user" issue...

---

