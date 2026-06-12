---
title: "ASP BullSh*t"
date: 2006-02-22
forum: The Cafe
---

### Post by soop on 2006-02-22
Ok, so here's the situation, we had a guy doing all our web crap. He's not the keenest of individuals and well he chose to do everything in Visual Studio for some inane reason, so now I have a bunch of stm and asp files. What I'd like to know is if anyone is aware of a conversion tool? Or am I going to have to port this all by hand?

Thanks

---

### Post by ssam on 2006-02-22
will it run in mono?

---

### Post by Stormy Eyes on 2006-02-22
[QUOTE=soop] What I'd like to know is if anyone is aware of a conversion tool? Or am I going to have to port this all by hand?[/QUOTE]

I think you're screwed. Is there any reason you can't just take one for the boss, get an ASP manual, and learn to maintain the existing code? I suspect your boss would prefer that to having it reimplemented, but I could be wrong.

---

### Post by jimjawn on 2006-02-22
[http://modules.apache.org/search](http://modules.apache.org/search) <--Search for "ASP"

I've never done this, but you can run asp pages in apache with modvb.  Additionally, there is xsp which is the asp.net server that comes with mone (already mentioned)

Additionally, there are some asp to php tools that you can use.  

[http://asp2php.naken.cc/](http://asp2php.naken.cc/) <-- is one

Is just one google "convert asp to php".  

If you're using asp you're probably using access and will have to probably rewrite some of your mysql code.  I'm willing to bet its not that hard.

And for what its worth, IMHO visual studio is an EXCELLENT ide for programming.  Especially if you're doing asp.

---

### Post by briancurtin on 2006-02-22
rewrite it, ASP sucks in the first place

(note, i did not say ASP.NET)

---

### Post by kelsey23 on 2006-02-22
C# isnt a bad language but VB just plain sucks.....anyway regular ASP pages feel like writing a web site in JavaScipt (JScript or VBScript is supported)...which just feels wrong...

---

### Post by LordHunter317 on 2006-02-22
Are we talking ASP or ASP.NET?

They're two completely different APIs with two completely different solutions.

If it's the former, it's possible to maybe get it running on Mono.  More details are required. 

However, the best solution would likely to be to run that application on Windows, or just rewrite it.

---

### Post by LordHunter317 on 2006-02-22
[QUOTE=jimjawn]If you're using asp you're probably using access and will have to probably rewrite some of your mysql code.  I'm willing to bet its not that hard.[/quote]Depending on teh application it ranges from easy to near impossible (date times are well, unique, in Access).

But I wouldn't migrate to MySQL.

---

