---
title: "viurs, how bad?"
date: 2005-12-06
forum: Server Platforms
---

### Post by [pl]ice on 2005-12-06
hey my mate just told me that his boxes have been infected with wirus/trojan :/
  u guys watch it... that was last night
[http://www.viruslist.com/en/news?id=48308](http://www.viruslist.com/en/news?id=48308)

---

### Post by Perfect Storm on 2005-12-07
That's why people shouldn't login as root.

---

### Post by nocturn on 2005-12-07
[QUOTE='[pl]ice']hey my mate just told me that his boxes have been infected with wirus/trojan :/
  u guys watch it... that was last night
[http://www.viruslist.com/en/news?id=48308](http://www.viruslist.com/en/news?id=48308)[/QUOTE]

How did the infection enter his machine?  
Did it infect it as root?  If not, cleanup is relatively easy.
Does he have an external firewall protecting his box? (this would close the backdoor).

He can try clamav to detect and possibly clean the virus.

---

### Post by nocturn on 2005-12-07
The virus information page was kinda vague.  It lists how the payload works but it does not explain the propagation method (what would make it a virus)...

Any info on this?

---

### Post by nocturn on 2005-12-07
Ok, as far as I can gather, it propagates like this.

You download already infected binaries, execute them and then it drops it's payload.  In the early phase, it spread in some infected tar.gz files on the net.

If you do not run as root, only binaries in your own directory are infected, so cleaning should be easy.

I'm now wandering how he got this virus, it is pretty old (2002).

---

### Post by [pl]ice on 2005-12-08
eh, that was an old one :)  i got up too early... ;)

yeh, these guys got dedicated server and a client uploaded a package, got infected; it's all kool :)  
   sorry for the chicken skin :smile:

---

### Post by az on 2005-12-08
[QUOTE='[pl]ice']eh, that was an old one :)  i got up too early... ;)

yeh, these guys got dedicated server and a client uploaded a package, got infected; it's all kool :)  
   sorry for the chicken skin :smile:[/QUOTE]
I do not understand what you mean.

Anyway, this is an old (ancient) virus.  Does it even still work?

---

### Post by [pl]ice on 2005-12-08
hhee, sorry, i meant that my mate send me info that he got infectet ~7 am, and  i haven't checked it well ..
  yeh, the virus still works ok :D 
totally client's fault :) (as the client is the admin of his box)

---

