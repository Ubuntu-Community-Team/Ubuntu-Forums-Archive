---
title: "I hate synaptic!"
date: 2009-04-28
forum: The Cafe
---

### Post by =^,^= on 2009-04-28
Why does search not work properly in synaptic! 

Its **SO** annoying!

---

### Post by Tibuda on 2009-04-28
How it should work?
I always find what I want.

---

### Post by Namtabmai on 2009-04-28
Perhaps because it searches descriptions as well as names?

---

### Post by speedwell68 on 2009-04-28
> **=^,^= said:**
> Why does search not work properly in synaptic! 

Its **SO** annoying!

Works fine here.  What are you searching for exactly?

---

### Post by MikeTheC on 2009-04-28
Yeah, no problems on my system.

Heck, I did a search for "dopewars" and the game and it's associated data file came right up.

---

### Post by Skripka on 2009-04-28
> **=^,^= said:**
> Why does search not work properly in synaptic! 

Its **SO** annoying!

Back in my *buntu days it worked great-especially in comparison to the jokes that were KPackageKit and Adept.

---

### Post by RiceMonster on 2009-04-28
I didn't have this problem either.

Can't you do
```
apt-cache search <pkg>
```
as well? (sorry, haven't used apt in  while) Maybe that will yield better results?

---

### Post by =^,^= on 2009-04-28
> **speedwell68 said:**
> Works fine here.  What are you searching for exactly?

Libstdc++5

---

### Post by Namtabmai on 2009-04-28
Edit menu -> Search, select name drop down, type libstdc++5. One result.

The quick search probably searches everything, including dependences. Which to be frank is a stupid default for a quick search.

---

### Post by =^,^= on 2009-04-28
> **Namtabmai said:**
> Edit menu -> Search, select name drop down, type libstdc++5. One result.

The quick search probably searches everything, including dependences. Which to be frank is a stupid default for a quick search.

Thanks that worked great! :D

---

### Post by jacob01 on 2009-04-28
I also had trouble finding a package. I installed a .deb that i downloaded online and it took me a while to find it i guess the search was case sensitive. To me this kinda defeats the purpose of a search, but besides that i can usually find what I'm looking for.

---

### Post by ssam on 2009-04-28
the search box in the tool bar just filters what is currently displayed.

---

### Post by swoll1980 on 2009-04-28
> **RiceMonster said:**
> I didn't have this problem either.

Can't you do
```
apt-cache search <pkg>
```
as well? (sorry, haven't used apt in  while) Maybe that will yield better results?

+1 using apt-cache search, and apt-get install/remove is way faster, and easier, than opening up all that GUI goodness in synaptic.

---

### Post by Bart_D on 2009-04-28
I love synaptic!

---

### Post by dragos240 on 2009-04-28
> **Bart_D said:**
> I love synaptic!

+1, but you have to love the terminal. Fixes all your problems.

---

### Post by gnomeuser on 2009-04-28
If you continue to find synaptic a bit cumbersome and overly complex might I suggest that you take a look at the PackageKit alternative in the packagekit-gnome package. I find it very pleasant to work with, somewhere in between add/remove programs and synaptic in terms of complexity.

---

### Post by Xbehave on 2009-04-28
I've not used it in a while, but when i started with ubuntu it was soo much better than adept that i even used it on kubuntu, it was however pretty slow on full description searches. IMHO it should do an apt-cache search <word> style search on just names+short descriptions, then load additional results underneath. 

Howver i found the cli, is much better than a gui package manager if you know what you want. Essentially your interacting with just text anyway, its a hard thing to sell to new users, but the cli is great for package management (you might still want to use synaptic to search for vague stuff like games/web browsers/etc, but i just use the web plus cli anyway)

---

### Post by drawkcab on 2009-04-28
The add/remove applications front end is what drives me nuts.  Super buggy.

---

### Post by myusername on 2009-04-28
i hate packagekit.

---

### Post by Bart_D on 2009-04-29
> **drawkcab said:**
> The add/remove applications front end is what drives me nuts.  Super buggy.

+1

I hate add/remove applications.

---

### Post by drawkcab on 2009-04-29
> **Bart_D said:**
> +1

I hate add/remove applications.

It is a very helpful thing for new users because it groups and documents various useful applications--provided that it works correctly.  Unfortunately it doesn't.

---

### Post by Excedio on 2009-04-29
That's funny...i searched for Libstdc++5 and it was the first and only thing that was found.

Maybe I have a special version that uses magic for searching. \\:D/

---

