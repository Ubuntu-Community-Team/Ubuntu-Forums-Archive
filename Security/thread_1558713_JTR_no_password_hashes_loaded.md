---
title: "JTR no password hashes loaded?"
date: 2010-08-22
forum: Security
---

### Post by II Luis II on 2010-08-22
Well after reading up about it I thought I would give it ago and see if it was actually any good. So I've tried and havent had any success. This is getting a bit annoying now and im hoping youll have the answer. 

The problem: No password hashes loaded

This is what im typing in to the terminal: john -wordfile:password.lst crackme.txt
So, im trying to use a word list. The crackme.txt is just a file with the following: "User:alphabet"

in the wordlist, the word alphabet is quite high up on the list but not at the top so I could see if this really got the password but without it taking too long. 

Can anyone help me? Am I doing it wrong? 

Cant remeber what I did but when writing up this new thread I changed something so now I get this back:

luis@ubuntu:~$ john -wordlist:password.lst crackme.txt
stat: crackme.txt: No such file or directory

So, do I need to move the file somewhere else? 

Thank you very much.

EDIT: When I drag and drop the file from my documents to the terminal I get the no password hashes loaded.

---

### Post by cariboo on 2010-08-22
Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1495033&highlight=john"), it should answer your questions.

---

### Post by II Luis II on 2010-08-22
Hmm Im assuming Ubuntu software centre does most of the installing and stuff for me?

but i got stuck on this:

Run the cracker
On Ubuntu, the actual password is /etc/shadow rather  than /etc/passwd. This file is not readable to normal users. So you have  to copy it and change the read permission. Remember, don't crack a  password file on its own machine. If someone else stole your password  file, or compromised JtR sent out your password file, you still have a  layer of protection because others don't know which computer these  passwords are for.

Not sure what Im changing and stuff. I guess I shouldnt really be doing stuff like this without learning the basics of linux but Im curious and now ive started ill finish, whats the run directory, step five on the tut im confused with could you explain or just slap me and send me on my way.

---

### Post by cariboo on 2010-08-23
What that thread states is that john is broken.

---

### Post by justanothergreysky on 2010-08-23
> **II Luis II said:**
> 
The problem: No password hashes loaded

So, im trying to use a word list. The crackme.txt is just a file with the following: "User:alphabet"



The password file is supposed to be..

user:MD5hash

For example:

root:$1$.QKDPc5E$SWlkjRWexrXYgc98F.

You can't just stick a word in there an expect John to "crack" it.  It should be an actual password MD5 hash.

---

### Post by II Luis II on 2010-08-23
Hmm not sure about john being broken. But I thought I could run a wordlist against the file and it would pick up the word? Fail on my behalf?

---

### Post by n~kf)}BW% on 2010-09-21
John never worked for me with ubuntu... It's a shame :(

I've had no problems with other tools. Even if your specify the right format, john doesn't load hashes! I had a list with raw MD5 hashes and i provided the format but it still didn't work?

---

### Post by bodhi.zazen on 2010-09-21
JTR works as described.

There are many tutorials on how to use it

[http://www.osix.net/modules/article/?id=455](http://www.osix.net/modules/article/?id=455)

The "problem" is that JTR does not work out of the box with all hashes.

See the link cariboo907 gave (post #2)

---

