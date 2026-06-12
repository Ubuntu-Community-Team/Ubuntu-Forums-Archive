---
title: "why not an graphic aptitude?"
date: 2006-09-17
forum: The Cafe
---

### Post by sargate on 2006-09-17
Hello everyone, i am just curious, if aptitude is "better" than apt-get, why do not create an gtk version of aptitude just like synaptic but with aptitude (gaptitude)
Sorry for my bad english

Thanx

---

### Post by nalmeth on 2006-09-17
Well, this might be useful for some. At least something to make it less confusing than when you type:
aptitude
on it's own in the terminal.. Perhaps in time synaptic will allow you to use aptitude instead of apt-get, rather than making yet another package manager.

I've yet to be converted to aptitude though.. I always find packages mysteriously not being installed, and packages being removed that I *don't* want removed.

A lot of it is sticking what I'm used to, of course, but aptitude hasn't wowed me over apt-get. Even if I have to do a little more work to get the job done, I want to know that I'm getting what I asked for.
Yes, I understand you can change aptitude's behavior, but information is a bit lacking, and I'm still happy with apt-get.

Also, I've always wondered if my problems arise from using both apt-get and aptitude. I haven't found anything definate or convincing either way.

---

### Post by PriceChild on 2006-09-17
Well if you type sudo aptitude, you get a sort of gui in the terminal...

Not really a gui... but you can still click the mouse button on menus and options!

pricey

---

### Post by aysiu on 2006-09-17
This is what that GUI looks like, by the way.

---

### Post by [h2o] on 2006-09-17
What in aptitude is not available in synaptic?

---

### Post by Shay Stephens on 2006-09-17
> **'[h2o] said:**
> What in aptitude is not available in synaptic?
That's what I was wondering.  Synaptic has a nice gui.

---

### Post by Bloodfen Razormaw on 2006-09-17
Aptitude's killer feature is that it tracks which packages are installed manually and which are automatically installed by dependencies.  It can remove any package which is installed automatically if, after the next operation, all packages which depend on it (or optionally, which recommend it) will be gone.  So if you install package A which depends on B, removing A automatically removes B, unless some package C is installed which still depends on B.  It is a reliable way of handling dependencies when removing packages to ensure the system stays clean.

---

### Post by mostwanted on 2006-09-17
Synaptic doesn't use apt-get, it uses the same low-level library that apt-get and aptitude uses, not the shell script commands.

---

### Post by sargate on 2006-09-17
> **Bloodfen Razormaw said:**
> Aptitude's killer feature is that it tracks which packages are installed manually and which are automatically installed by dependencies.  It can remove any package which is installed automatically if, after the next operation, all packages which depend on it (or optionally, which recommend it) will be gone.  So if you install package A which depends on B, removing A automatically removes B, unless some package C is installed which still depends on B.  It is a reliable way of handling dependencies when removing packages to ensure the system stays clean.

That is exactly what i mean, i always use aptitude, synaptic is nice, i never use it, but new people does, so maybe use aptitude instead of apt-get will solve dependencies problems.

---

### Post by TheMono on 2006-09-17
I believe that Edgy will have the SMART package manager which does track dependencies in aptitude-style.

---

### Post by croak77 on 2006-09-17
It's already been said but;

ncurses = gui

---

### Post by Wolki on 2006-09-17
apt-get/synaptic in edgy mark dependencies and offer to remove them once they're not needed, too. Aptitude will use the same mechanism. Smart will not be default in edgy (or it would already be, we're way past feature freeze).

Personally I'm not sure autoremoving dependencies is a good idea since it could potentially break stuff. The people who would be affected by this should know enough to carefully check the autoremove list though... At least I hope :)

---

### Post by gorilla on 2006-09-17
aptitude is nice; I use it as well, but it is no good standard package tool for Ubuntu, since it complicates life when dealing with meta-packages.
There are some circumstances where one has to delete a meta-packages and aptitude would remove all relates packages, if the user dosn't go through the list and checks to keep each to-be-removed packaged

---

