---
title: "Random password generators?"
date: 2011-02-02
forum: Security
---

### Post by meow9th on 2011-02-02
I'm looking for a high quality, offline, random password generator with options for varying complexity (ie, allow/disallow user-specified characters or character classes). On Windows, I use the open-source program [PWGen]("http://pwgen-win.sourceforge.net/index.html"). The author really seems to know his cryptography, and the options available are really handy. The [user manual (pdf)]("http://pwgen-win.sourceforge.net/manual.pdf") includes technical details.

Does anyone know of a comparable Linux application?

---

### Post by anomie on 2011-02-02
At a glance, not sure whether one is a port of the other (or whether they're unrelated), but there's of course pwgen for GNU/Linux: 

[http://sourceforge.net/projects/pwgen/](http://sourceforge.net/projects/pwgen/)

---

### Post by Klump on 2011-02-02
I know only one: KeePassX. It's a password manager and has a strong built-in password generator. Might give that a try :)

---

### Post by rookcifer on 2011-02-02
OP,

I wrote a password generator with a GUI for Linux.  It's got its own PPA.  To install it, just type this into the terminal

```
sudo add-apt-repository ppa:rookcifer/pypass && sudo apt-get update && sudo apt-get install pypass
```

Then you can find it in Applications---> Accessories

I am aware of PWgen, as you seem to like.  The main difference I see in it and Pypass is that it includes its own entropy gatherer.  However, I don't think that's necessary as /dev/urandom itself is considered cryptographically secure by most experts (my password generator uses /dev/urandom).  Including one's own entropy gatherer (which I've thought about doing) is really sort of pointless, which is why I didn't.

---

### Post by walt.smith1960 on 2011-03-04
Here's one.  Good luck memorizing 'em though.

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

---

### Post by DZ* on 2011-03-04
tr -cd [:alnum:] < /dev/urandom | head -c 12; echo ""
for 12 character strings made of letters and digits or
tr -cd [:graph:] < /dev/urandom | head -c 12; echo ""
to also include printable characters

---

### Post by Jimtheplanner on 2011-03-05
Try Revelation- it's in the repos and works well with Ubuntu....

---

### Post by Megaptera on 2011-03-05
Something a bit different but useful:
" PasswordCard is a credit card-sized card you keep in your wallet, which lets you pick very secure passwords for all your websites, without having to remember them! You just keep them with you, and even if your wallet does get stolen, the thief will still not know your actual passwords."

[http://www.passwordcard.org/en](http://www.passwordcard.org/en)

I use it at work where I have to change several system p/w monthly. Random but easy to remember.

---

