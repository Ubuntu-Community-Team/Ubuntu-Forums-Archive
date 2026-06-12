---
title: "Not completely serious, but...  Emacs based distro?"
date: 2010-08-04
forum: The Cafe
---

### Post by Zorgoth on 2010-08-04
I just read a post by someone looking to install Linux on a computer with 64 MB of RAM. 

I know that I can get Xubuntu going (badly) on 128 from experience, but 64, no way.  

So what I am wondering is, purely out of curiosity, could one design a lightweight distribution with graphical functionality based entirely on emacs (presumably on top of a skeleton X so you have cursor and real graphics)?  I know emacs has a web browser capable of more than text, although I believe that if you want a full-featured web browser you would need more X-based packages hiding in the background.

Obviously implementing all the GUI-frontends in emacs lisp would take a lot of work, but is is possible? :D

---

### Post by phrostbyte on 2010-08-05
Could someone? Of course they can. You can if you wanted to. Ubuntu Emacs Remix? :p

---

### Post by spupy on 2010-08-05
Isn't Emacs a distro? You just need to throw in a good text editor (like ed) and you're good to go!




(Sorry, let's get the emacs jokes out first :)

---

### Post by Dustin2128 on 2010-08-05
try SliTaz, fluxbuntu or lubuntu. As for emacs, I'm pretty sure its GNU HURD in disguise...
>.>
<.<

---

### Post by Shining Arcanine on 2010-08-05
> **Zorgoth said:**
> I just read a post by someone looking to install Linux on a computer with 64 MB of RAM. 

I know that I can get Xubuntu going (badly) on 128 from experience, but 64, no way.  

So what I am wondering is, purely out of curiosity, could one design a lightweight distribution with graphical functionality based entirely on emacs (presumably on top of a skeleton X so you have cursor and real graphics)?  I know emacs has a web browser capable of more than text, although I believe that if you want a full-featured web browser you would need more X-based packages hiding in the background.

Obviously implementing all the GUI-frontends in emacs lisp would take a lot of work, but is is possible? :D

You should try Gentoo Linux or one of its derivatives. They can be configured to use very little in terms of resources. 64MB of RAM is more than enough to get a graphical environment working with Gentoo Linux, although compilation would likely need to be done with the aid of distcc.

---

### Post by Cuddles McKitten on 2010-08-05
> **spupy said:**
> You just need to throw in a good text editor (like ed) and you're good to go!

That's a very strange way to spell "vi."

---

### Post by lisati on 2010-08-05
<side note>
I have Ubuntu 6.06 on a machine with only 64Mb RAM. It doesn't have a GUI (it choked when I tried to install one), but since I use it mainly as a backup for my server, that's no big deal. Puppy works on that machine, if a bit slowly for my liking.
</side note>

---

### Post by Xianath on 2010-08-06
I used to have Linux running on 4MB for quite a long time. All it takes is the right distro, the right kernel and the fact that 4MB cost just over $200 at the time.

EMACS, if statically compiled, could theoretically run an entire text-based distro on its own. I'm afraid though that a fully statically compiled EMACS would be larger than the kernel itself ;)

---

