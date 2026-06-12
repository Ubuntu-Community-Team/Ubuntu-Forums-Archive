---
title: "is anybody else's earth missing from google earth?"
date: 2008-08-21
forum: The Cafe
---

### Post by hardyn on 2008-08-21
My google earth was working just fine a few days ago, today the earth is missing.

is it just me? or are they having server problems?

This feels a little like starwars, and alderan is missing...

---

### Post by ooobuntooo on 2008-08-21
> **hardyn said:**
> My google earth was working just fine a few days ago, today the earth is missing.

is it just me? or are they having server problems?

This feels a little like starwars, and alderan is missing...

I think it does that if you are not connected to the internet!

---

### Post by RiceMonster on 2008-08-21
That happened when I incorrectly installed it before. I accidentally ran it as root and the configuration files had the wrong permissions. It's working just fine for me now though.

---

### Post by hardyn on 2008-08-21
> **ooobuntooo said:**
> I think it does that if you are not connected to the internet!

I was able to leave this post!

---

### Post by swoll1980 on 2008-08-21
You have to run it as root now or it wont work, or check your groups see if there's a google earth group, if there is add your self to it and that should help

---

### Post by RiceMonster on 2008-08-21
> **swoll1980 said:**
> You have to run it as root now or it wont work. check your groups see if there's a google earth group, if there is add your self to it and that should help

No you don't. If you have to run it as root, you accidentally ran it as root when you first installed it and the configuration file permissions are wrong.

Do either of these:
```
sudo chown -R yourusername ~/.config/Google
sudo mv ~/.config/Google ~/.config/Google.bak
```

Yes, sudo is necessary, because root owns it.

---

### Post by Dremora on 2008-08-21
You should stage a protest, Windows users get Earth in Google Earth but Linux users don't.

Clearly Microsoft has removed the entire planet......

---

### Post by hardyn on 2008-08-21
Hahahahahahahaha...





> **dremora said:**
> you should stage a protest, windows users get earth in google earth but linux users don't.

Clearly microsoft has removed the entire planet......

---

### Post by ssam on 2008-08-21
Its been destroyed to make way for a hyperspace bypass.

---

### Post by hardyn on 2008-08-21
It was a permissions problem, as rice suggested.

Maybe i will suggest that google tweak the installer so this does not happen, the permissions this is something that i really should have clued into before posting... oh well.

Thanks for the help.

---

### Post by sydbat on 2008-08-21
42

---

