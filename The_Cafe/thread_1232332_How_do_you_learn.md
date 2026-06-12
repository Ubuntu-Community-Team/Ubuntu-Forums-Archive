---
title: "How do you learn?"
date: 2009-08-05
forum: The Cafe
---

### Post by Jago6060 on 2009-08-05
I've seen a lot of really in depth topics on the forums and was just wondering, how do you learn all of this stuff?  Do you learn by necessity?  Learn because you want to?  Schedule time to learn?  I'm just kind of looking for opinions on the best way to go about immersing myself in Ubuntu so I can learn more.

---

### Post by Viva on 2009-08-05
Learn by accident

---

### Post by ibuclaw on 2009-08-05
I learn by giving support.

You quickly learn how to resolve recurring issues people have with software you are using/learning to use, and if you run in a similar problem, you can work around it yourself. :)

Classic example is Dual NViDIA cards setup in Ubuntu.

Before you restart X into the nvidia drivers.
```
lspci | grep VGA
```
and get one of the PCI locations, ie: 04:00.00

And put that inside the xorg.conf file under 'Section "Device"' in the following format:
```
BUSID    "PCI:4:0:0"
```
It's the small steps that make a big difference.

---

### Post by SuperSonic4 on 2009-08-05
I've a visual learner - I learn by seeing :)

---

### Post by Ian dewhurst on 2009-08-05
Its not absorbing as most people think.

About a year ago I screwed up my XP partition and had to use linux (no XP install CD)
So you just pick things up as you go along start with basics installing software, changing themes and fonts installing flash etc.
And then when you feel you are ready to learn more there are thousands of tutorials on what you wish to learn if anything at all.
I think most people are put off by the terminal to be honest.

But some people forget to mention that there are programs that skip the terminal (envy, ubuntu tweak etc) when people are more happier using a GUI wizard.
Its all about what you want at the end of it all and remember apart from this forum Google is your friend:D

---

### Post by MikeTheC on 2009-08-05
Oh, you mean about Linux. Well, I learned the basics of Linux itself by conversations with a friend who is hyper-knowlegeable and does coding for a living. After getting the "skeleton", if you will, it has all been about hanging the muscles and tendons and other stuff in the right places.

In a sense, that's kind of the way I learn anything.

---

### Post by cmay on 2009-08-05
all of the above to some extent .
 but the most important is learning by doing. i cant read something and then remember it if it does not get put to use. i also need to see things as examples sometimes.

 but that depends on what it is i learn. stuff like computers i learn most by reading a whole lot in forums adn books . and then find the examples around that fits the best approach and from there adapt to my own needs.  

i quit school very very early because i hate learning stuff from books i cant use right away. on the other hand if i just see how others do and dont know enough about it to find a better way myself then i dont feel right about it eihter.

---

### Post by XubuRoxMySox on 2009-08-05
I have to actually *do* it to learn it. That goes for Linux as well as dance and even history class at school. I can't travel through time (yet), but I go to "living history" events when I can and participate when I can. I even got to play the part of a Confederate cannonier in the War Between the States! Wore a uniform, took the training, worked on a cannon crew (shooting blanks of course, but very LOUD ones!).

---

### Post by lisati on 2009-08-05
I voted "All of the above" but can relate to the "lean by doing" option: there have been questions on the forums from time to time where I'm sure there's an answer (perhaps I've seen something similar mentioned in another thread) but I hesitate to answer because I haven't actually done it myself...

---

### Post by NovaAesa on 2009-08-05
I learn by all bar hearing. I best learn when I have to explain the knowledge to someone less knowledgeable than me! That really puts the heat on to make sure you know what you're on about!

---

### Post by OutOfReach on 2009-08-05
I'm more of a kinesthetic/visual learner. I get absolutely bored when I read/hear lessons/lectures etc and I get easily distracted.

EDIT: Oh, this thread is regarding ubuntu, well my above points still stay, but sometimes the reading does become less of a burden.

---

### Post by ibuclaw on 2009-08-05
Oh, and I Learn by [Learning to Learning]("http://www.amazon.co.uk/Study-Skills-Handbook-Cottrell/dp/0230573053/ref=sr_1_1?ie=UTF8&qid=1249511860&sr=8-1").

At least, in the most effective way possible. ;)

---

### Post by Nburnes on 2009-08-05
I learn by all of the above.

The site is especially helpful for any of my Ubuntu needs, which other users on this site make me manually use the Terminal and try to figure things out on my own.

---

### Post by jrusso2 on 2009-08-05
After 13 years of using Linux as my operating system you tend to pick things up.  But when I first started I did buy some books and read them to learn commands.  

Now of course most of that stuff is online so you don't need to buy books.  

The most important thing to learn is how to search.  Chances are someone already had your problem and has had the same issue and something is posted about it.

---

### Post by spupy on 2009-08-05
> **OutOfReach said:**
> I'm more of a visual learner, and I really love I'm more of a kinesthetic/visual learner. I get absolutely bored when I read/hear lessons/lectures etc and I get easily distracted.

This for me as well. I even rarely go to lectures because I get bored to sleep in there.

---

### Post by TBOL3 on 2009-08-05
Here type in the following command:

sudo apt-get install elearn elearn-now

No, you learn by life experiences, by seeing, hearing, doing, and needing.  What I find to be really important though, and one of the hardest things to do, is to realize that you don't know everything about a topic, and even though you may think you do, you still need to continue to learn.

---

### Post by mamamia88 on 2009-08-05
i usually learn by making mistakes

---

### Post by Jago6060 on 2009-08-06
> **TBOL3 said:**
> Here type in the following command:
sudo apt-get install elearn elearn-now


If only it were that easy :popcorn:

---

### Post by nothingspecial on 2009-08-06
> **MikeTheC said:**
>  Well, I learned the basics of Linux itself by conversations with a friend who is hyper-knowlegeable and does coding for a living.

Me too, and it`s brilliant sometimes when he phones me!? to ask how to do something.

---

### Post by RED Lemming on 2009-08-06
Necessity.... I need to do something (or want to) and I try to do it. 

Along the way knowledge kind of settles like intellectual dandruff....  some gets brushed off, but the rest sticks.


Thinking of it actually I seem to remember being asked this question in quite a serious way by an old lecturer, I think my reply was "Osmosis."

EDIT: And no I don't have dandruff.

---

### Post by harry2006 on 2009-08-06
i learn by doing and reading

---

### Post by epsolon77 on 2009-08-06
When I was still in school I had a psych/intelligence test done as part of a class to look at what ways you learn best vs brain dominance.  It was really interesting, and of course I forgot the main thrust of the research that was done.  Anyway, they found that my brain has an abnormal amount of connections between hemispheres, which makes me technically ambidextrous (this just means my handwriting sucks just as bad from both hands), and that I do not favor a learning style.  I think I was a little better at tactile learning, but it was not by much.

---

### Post by Tipped OuT on 2009-08-06
I learn by seeing, then doing.

---

### Post by magmon on 2009-08-06
My mind is like a sponge. If I put any time into reading/watching/doing anything, I will remember it forever.

---

### Post by ibuclaw on 2009-08-07
> **magmon said:**
> My mind is like a sponge. If I put any time into reading/watching/doing anything, I will remember it forever.

Ah, but sponges only retain 20% of what they take in. (Put a sponge under water and watch how much water it looses once you take it out ;))

My mind is like a sheet of Bounty Kitchen Roll :)

---

### Post by SuperSonic4 on 2009-08-07
> **tinivole said:**
> Ah, but sponges only retain 20% of what they take in. (Put a sponge under water and watch how much water it looses once you take it out ;))

My mind is like a sheet of Bounty Kitchen Roll :)

As in it doesn't exist any more? ;)

[http://www.plenty.co.uk/home.html](http://www.plenty.co.uk/home.html)

---

### Post by fatkidwithastick on 2009-08-07
> **tinivole said:**
> Ah, but sponges only retain 20% of what they take in. (Put a sponge under water and watch how much water it looses once you take it out ;))

My mind is like a sheet of Bounty Kitchen Roll :)


mine is a sham-wow, lol :D

---

