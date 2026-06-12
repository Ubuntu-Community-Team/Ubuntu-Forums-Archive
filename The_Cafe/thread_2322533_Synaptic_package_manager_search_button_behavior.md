---
title: "Synaptic package manager search button behavior"
date: 2016-04-28
forum: The Cafe
---

### Post by user1397 on 2016-04-28
Decided to post this here as it's not really a support question, as no functionality is missing really.

I've just been wondering why the search button in synaptic seems to behave in two different ways, and randomly at that.  The default way, which I have always seen right after installing synaptic, is just a plain button that you click on and a search field pop up appears where you can type anything, and then your search terms are displayed on the left side and your results on the right.

But for some reason, sometimes the search button stops being a button and becomes a field itself, where as soon as you start typing, results appear.  I have noticed that almost always, on every Ubuntu version up until now, this "behavior" appears randomly, and usually only the second time after opening synaptic for the first time after installing it.  I find this behavior way more convenient and useful, as you can search faster and you can still see the status of the packages on the left side while searching.

Anyone else ever thought this was weird?  I don't know why I suddenly bring it up now, should've asked years ago.  I tried googling but didn't find much.

After a fresh install of 16.04 I noticed behavior #2 never showed up, which is kinda annoying cause that's the behavior I preferred.

And no, I've looked, and there's nothing in preferences to switch between the two.

---

### Post by QDR06VV9 on 2016-04-28
I know this is not a help request... but this was talked about in the Development cycle of Xenial
If you want** (notice the if you want) **the search function back.
```
sudo apt-get install apt-xapian-index
sudo update-apt-xapian-index -vf
```

---

### Post by user1397 on 2016-04-28
> **runrickus said:**
> I know this is not a help request... but this was talked about in the Development cycle of Xenial
If you want** (notice the if you want) **the search function back.
```
sudo apt-get install apt-xapian-index
sudo update-apt-xapian-index -vf
```
Oh wow, well that explains that then. Any idea why they decided against including it by default?

Thanks!

---

### Post by vasa1 on 2016-04-28
> **ubuntuman001 said:**
> Oh wow, well that explains that then. Any idea why they decided against including it by default?

Thanks!apt-xapian-index? Not sure, but there's a bug filed against it: [https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/655831](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/655831)

Also, it seems it builds a database that grows ...

I know that Lubuntu, which includes Synaptic as a default package, hasn't been including apt-xapian-index as a default for as long as I can remember.

---

### Post by mc4man on 2016-04-28
> **ubuntuman001 said:**
> Oh wow, well that explains that then. Any idea why they decided against including it by default?

Thanks! 
It wasn't specifically included previously,   apt-xapian-index  was pulled in by  a dep  or recommend of software-center. 
So when s-c was dropped it was no longer required/recommended  by any default package so no quick search in synaptic  as synaptic doesn't require or recommend it.

---

