---
title: "Why are apt-get update/upgrade separate?"
date: 2008-09-13
forum: The Cafe
---

### Post by mrsteveman1 on 2008-09-13
As far as i can tell, they are always executed one after the other. Doing upgrade doesn't mean much if you haven't updated, and updating serves little if any purpose if you aren't immediately going to upgrade packages.

So why are they separate, and why can't apt-get upgrade perform the update at the same time?

---

### Post by SunnyRabbiera on 2008-09-13
the two preform seperate functions, apt-get update refreshes the repository and upgrade typically looks for newer packages.

---

### Post by smartboyathome on 2008-09-13
> **SunnyRabbiera said:**
> the two preform seperate functions, apt-get update refreshes the repository **cache** and upgrade typically looks for newer packages.

There you go, fixed. The reason they're separate is because, of example, if you use a repository to get a specific program, but don't need to upgrade anything, then you can just update the repository cache and install the program.

---

### Post by mrsteveman1 on 2008-09-13
That's a good point, there are reasons to run update alone, which is why it can be done separately. So that's one out of my two confusions taken care of :D

However, why does upgrade not automatically run update as part of its process? I can't think of any situation where one would want to run upgrade without updating the cache first.

---

### Post by smartboyathome on 2008-09-13
> **mrsteveman1 said:**
> That's a good point, there are reasons to run update alone, which is why it can be done separately. So that's one out of my two confusions taken care of :D

However, why does upgrade not automatically run update as part of its process? I can't think of any situation where one would want to run upgrade without updating the cache first.

Perhaps you don't want all the updates, only the ones from your cache? Or if an update breaks the first time and you need to run it again to fix it, you don't want to refresh your cache again, do you? Take up the extra time it takes?

---

### Post by jward3010 on 2009-06-19
The extra time in writing out "sudo apt-get upgrade" after "sudo apt-get update" is whats annoying me, even "sudo apt-get update && sudo apt-get upgrade" is long enough, simply because it's a constant task and Linux is about increasing productivity and reducing workload by clever automation. There could easily be a combined command that would do the two. It's one of the most talked about commands on the Ubuntu forums and it's an action thats done by thousands of Ubuntu users everyday - there should be a way to simplify it and increase it's efficiency.

Sorry for digging this one up from the dark.

---

### Post by &#32 Greg on 2009-06-19
If it bothers you, then why not alias it?

---

### Post by Sef on 2009-06-19
> whats annoying me, even "sudo apt-get update && sudo apt-get upgrade"

So save that command in a word document and simply cut and paste it when you want to use it.

---

### Post by FuturePilot on 2009-06-19
I've never done the two right after one another. I see no reason to. update-manager executes an update every 24 hours so there's really no reason to run apt-get update again.

---

### Post by RiceMonster on 2009-06-19
> **Sef said:**
> So save that command in a word document and simply cut and paste it when you want to use it.

or even simpler, make it an alias as "update" or something like that.

edit: Greg already pointed that out

---

### Post by solitaire on 2009-06-19
do what I do...

In terminal press the up arrow key till the command pops up then press enter!

You've typed it in once so it's remembered! so if you don't use terminal a lot it would only take 3 or 4 presses of the up arrow to get to the command!


Simples!!

---

### Post by MaxIBoy on 2009-06-20
> **mrsteveman1 said:**
> That's a good point, there are reasons to run update alone, which is why it can be done separately. So that's one out of my two confusions taken care of :D

However, why does upgrade not automatically run update as part of its process? I can't think of any situation where one would want to run upgrade without updating the cache first.I encounter this all the time. It's more useful if you're on the bleeding edge, but a lot of the time there are upgrades which I specifically know will break my system. I like to update my cache and peruse the list of updates before I actually upgrade anything. I need to do this on my laptop because it has the Debian experimental repositories enabled. So for example, some library could receive an update, which causes other packages to break. Obviously, issues like this get ironed out before the packages is allowed to go into the more stable repositories. Meanwhile, I learned to disable automatic updates after some nasty breakage, and in return for my trouble, I get the latest and greatest software! (In theory, anyway.)

---

### Post by HappyFeet on 2009-06-20
> **jward3010 said:**
> there should be a way to simplify it and increase it's efficiency.


There is a way. Just write some code and come up with something. It shouldn't be that hard to do. ):P

We users are part of the community, and as such, instead of waiting for other people to write everything for them, should take it upon themselves to contribute and write code. [I]But I do realize that not everybody is inclined to do the aforementioned coding. 
[/I]
"If you want it done right, do it yourself."  ;)

---

### Post by MaxIBoy on 2009-06-20
> **HappyFeet said:**
> There is a way. Just write some code and come up with something. It shouldn't be that hard to do. ):P
```
alias update='sudo apt-get update && sudo apt-get upgrade'
```
Put that in your ~/.bashrc.

---

### Post by ericab on 2009-06-20
do what Greg said and alias it.

assign "sudo apt-get update && apt-get upgrade" to something like "sudo apt new"

badda-bing! back in business

---

