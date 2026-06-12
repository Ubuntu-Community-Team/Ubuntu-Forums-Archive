---
title: "Python authentication to OpenSSH"
date: 2006-06-05
forum: Server Platforms
---

### Post by Tortanick on 2006-06-05
I was wandering if/how you could some how have OpenSSH make users imput a password to a Python script, if the password is correct the python script will pass the user to the normal username/password you get when logging into OpenSSH.

---

### Post by LordHunter317 on 2006-06-05
Why would you ever want to do this?  I'm not aware of any easy way to do this, and it's a terribly bad and likely dangerous idea anyway.

---

### Post by Tortanick on 2006-06-06
I created my own password system designed to give me a hint that I could use to deduce a new password every time I log in. 

I can't see whats so bad or dangerous about it though?

---

### Post by LordHunter317 on 2006-06-07
Because if you're not careful, you'll compromise your system.

You probably want to look at S/KEY, which already does what oyu likely want.

---

### Post by Tortanick on 2006-06-07
S/Key creates a list of one use passwords, my system creates a new password for every attempt and I figure out the new password when I want to log on and type that. Quite a big diffrence.

As for being carefull:

The python script's only user imput is a string. (raw_input)
I plan to keep the traditional user/password as a failsafe

The only risk is I make a mistake while implementing the python authentication, and thats what I asked for help with,

---

### Post by LordHunter317 on 2006-06-07
Yes, but what's to stop me from making the guess and getting in instead?

Anyway, the only way to inject it into the OpenSSH auth stack is to recompile OpenSSH.

If you really want to do this, create a PAM module.  But I'm positive you really don't want to do this.

---

