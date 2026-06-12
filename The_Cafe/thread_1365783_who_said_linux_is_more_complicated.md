---
title: "who said linux is more complicated?"
date: 2009-12-27
forum: The Cafe
---

### Post by mamamia88 on 2009-12-27
I am trying to make myself into a restricted user on windows 7 much like a root user on linux. I am absolutely at a loss on how to do so.  I asked on my digital life but they said that I have an administrator account but i am not "THE ADMINISTRATOR"  what the heck does this even mean.  does anyone know how to do what i want in windows 7?

---

### Post by nmccrina on 2009-12-27
The first thing I did after installing Windows 7 was to create a new "standard user" account. At install, I had named the default account 'admin' to save my user name for the new one.

Then I just used the admin account to install stuff, and did everything else in my other one.

---

### Post by pwnst*r on 2009-12-27
> **mamamia88 said:**
> I am trying to make myself into a restricted user on windows 7 much like a root user on linux. I am absolutely at a loss on how to do so.  I asked on my digital life but they said that I have an administrator account but i am not "THE ADMINISTRATOR"  what the heck does this even mean.  does anyone know how to do what i want in windows 7?

it's not hard.

---

### Post by mamamia88 on 2009-12-27
so i have too make a second account just to do this?

---

### Post by pwnst*r on 2009-12-27
sounds like you already have an admin account.  just add a standard user account now.

---

### Post by mamamia88 on 2009-12-27
ah ok went ahead and did it thanks this makes me feel alot more comfortable using windows.  i would install ubuntu on this but i really don't feel like struggling with wireless drivers right now

---

### Post by pwnst*r on 2009-12-27
what kind of laptop/desktop do you have?

---

### Post by mamamia88 on 2009-12-27
i am using a samsung n130 i just got for christmas.  it uses a realtek wireless card i believe.  i already tried the live cd and it didn't connect to wireless

---

### Post by pwnst*r on 2009-12-27
damn, that sucks :/

---

### Post by lisati on 2009-12-27
> **mamamia88 said:**
> i am using a samsung n130 i just got for christmas.  it uses a [COLOR="Red"]realtek wireless card[/COLOR] i believe.  i already tried the live cd and it didn't connect to wireless

Some Realtek cards seem to be supported, others seem to need a little tweaking. Do you know which one? The following at the terminal might be able to tell you:
```
lspci | grep Realtek
```
(I'll have to defer to the wisdom of others if its one that doesn't work without help)

---

### Post by pwnst*r on 2009-12-27
yeah, i was googling and saw that some have gotten them to work with Realtek drivers.  

[http://ubuntuforums.org/showthread.php?t=1321340](http://ubuntuforums.org/showthread.php?t=1321340)

---

### Post by mamamia88 on 2009-12-27
cool man thanks doesn't look that bad might give it a try can you install ndiswrapper from live cd?

---

### Post by pwnst*r on 2009-12-27
hm.. that's a good question and one i not have an answer for.  hopefully someone will chime in that knows.

---

### Post by mamamia88 on 2009-12-27
yeah hopefully i want to make sure it works before installing it.

---

### Post by handy on 2009-12-27
> **mamamia88 said:**
> so i have too make a second account just to do this?

Just like in most distros, you have a root account & your normal user account.

Same thing really.

---

### Post by Frak on 2009-12-27
> **handy said:**
> Just like in most distros, you have a root account & your normal user account.

Same thing really.
Yep.

---

### Post by RiceMonster on 2009-12-27
uhhh....

I just installed windows 7 yesterday. All I did was add another account, and it defaulted to a limited account. Then, when you go to do anything that requires admin privalges, UAC will automatically ask you for the password of your admin account.

Not hard to figure out.

---

