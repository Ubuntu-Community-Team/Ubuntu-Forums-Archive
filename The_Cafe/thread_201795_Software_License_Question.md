---
title: "Software License Question"
date: 2006-06-22
forum: The Cafe
---

### Post by xtacocorex on 2006-06-22
This might be more suited to the Programming Talk section, but I figured the Cafe' could be a good place for an intense discussion on the topic.

Say I came up with a really novel idea for generating airfoils, so novel in fact that one of my Aerospace professor's who has experience generating airfoils has never seen this method before in his many years of industy and research experience.

Now, I can write a program to generate the airfoils (done in FORTRAN, but currently working on a PyGTK app), perform some basic aerodynamic analysis on them and then do post-processing to get flow visualizations and force output.

What license would I put it under, if the underlying airfoil generation method isn't what anyone has seen before, at least from what research I've done?

I'm not worried about people copying the code, if it had to come down to the GPL I'd use it, but I'm more worried about the intellectual property that I have in the airfoil generation itself. The way the airfoils are shaped, there could be a big market for remote control aircraft pilots and/or people designing aerodynamics for race-cars.

---

### Post by x64Jimbo on 2006-06-22
Four words:
PATENT IT RIGHT NOW.
These days, if you don't patent every little thing that you think of, someone else will, and they will make millions while you just sit and wish that you had patented it when you thought of it. (Or someone else already patented it 40 years ago and they're just waiting for some poor schmuck to come along and make a successful product based on that design so they can sue him for all he's worth)

---

### Post by Gustav on 2006-06-22
That sounds like a patent issue.

edit: beaten again :)

---

### Post by xtacocorex on 2006-06-22
I've thought about patents and since I work with people who deal with intellectual property, one said to do it, but my old professor said that it might be hard to patent a bunch of equations. I sort of agree with my professor, since I did take ideas from two other theories to make my method.

I could do a very restrictive copyright and register it, since that's only 30 USD, whereas with patents, you need lots of money.

---

### Post by bruce89 on 2006-06-22
[QUOTE=xtacocorex]...but my old professor said that it might be hard to patent a bunch of equations.[/QUOTE]
And it's impossible to patent software things such as [double clicking]("http://www.newscientist.com/article.ns?id=dn5072")?  Not to mention they're evil, but I can understand your concerns in this case.  The thing is if it were to be GPLv3, you couldn't have patents on it (I think).

---

### Post by Kvark on 2006-06-22
Think twice before getting into patents. If a huge corporation with an army of lawyers violates your patent then it will be very expensive to sue them and hard to win. And since many companies register thousands of patents per year chances are you violate some of their patents as well which would negate your advantage.

---

### Post by xtacocorex on 2006-06-22
You raise a good point bruce89. I'm going to be pissed if I have to pay someone to let me do double clicking...

I wouldn't want to patent the software, just the means to do the airfoil generation. If I included a flow solver, that'd have to be written from scratch and that couldn't be patented because there are so many out there and they all pretty much do the same thing.

But if you look at the NACA 4 & 5 series airfoils, they aren't patented, at least from what I know.

The only way that I could destroy my method is forcing a company, who has developed this idea before and kept it secret, to release information about it, thereby giving up it's secrecy. And in that case, I'd probably be humbled to know that I wasn't the only one to think it up.

I do have a nice picture of one of the many airfoils the method can create on my google homepage. The link is in my signature.

---

### Post by bruce89 on 2006-06-22
[QUOTE=xtacocorex]You raise a good point bruce89. I'm going to be pissed if I have to pay someone to let me do double clicking...

I wouldn't want to patent the software, just the means to do the airfoil generation. If I included a flow solver, that'd have to be written from scratch and that couldn't be patented because there are so many out there and they all pretty much do the same thing.[/QUOTE]
Yes, that is reasonable then.  I wouldn't worry about the double-click patent unless you implement it on PDA's or something, so don't get drunk about it!  (pissed means drunk here, by the way, we say pissed off.)

---

### Post by xtacocorex on 2006-06-22
I know from reading the Adobe Acrobat spash screen, that the program contains codes that are patented, something like the LZW algorithm. 

I might have to do something like that, were part of the program is patented [the actual generation method] and use the rest of the program as an interface for it.

---

### Post by Virogenesis on 2006-06-22
[QUOTE=x64Jimbo]Four words:
PATENT IT RIGHT NOW.
These days, if you don't patent every little thing that you think of, someone else will, and they will make millions while you just sit and wish that you had patented it when you thought of it. (Or someone else already patented it 40 years ago and they're just waiting for some poor schmuck to come along and make a successful product based on that design so they can sue him for all he's worth)[/QUOTE]
patents are bad end of story.....

---

### Post by bruce89 on 2006-06-22
[QUOTE=xtacocorex]I know from reading the Adobe Acrobat spash screen, that the program contains codes that are patented, something like the LZW algorithm.[/QUOTE]
It seems a bit rediclous having patent info on the splash screen, reminds me of [Microsoft OS/2 1.3]("http://toastytech.com/guis/MOS2Boot.gif")

---

### Post by xtacocorex on 2006-06-22
[quote="Virogenesis"]patents are bad end of story.....[/quote]

Like I said, I wouldn't be patenting the actual software, but a single method that would be used by a program. The method basically consists of two equations and how to put them together in a meaningful way that got the result I wanted. Both of those equations come from other methods.

I also don't have enough money for a patent, at least yet. 

And I might not end up patenting it, just registering for a copyright, that would still protect my idea.

And there could be a decent market in this to make a nice bit of money. If I were to patent it, the money would probably go to paying for the patent.

---

### Post by xtacocorex on 2006-06-22
[QUOTE=bruce89]It seems a bit rediclous having patent info on the splash screen[/QUOTE]

Here is a pic of the Acrobat splash I just took. I didn't bother trying to count the number of patents it's protected under.
[http://robert.wolterman.googlepages.com/acrobatsplash.png](http://robert.wolterman.googlepages.com/acrobatsplash.png)

---

### Post by bruce89 on 2006-06-22
[QUOTE=xtacocorex]Here is a pic of the Acrobat splash I just took. I didn't bother trying to count the number of patents it's protected under.
[http://robert.wolterman.googlepages.com/acrobatsplash.png](http://robert.wolterman.googlepages.com/acrobatsplash.png)[/QUOTE]
Yikes, that's quite a few, I wonder what they are for.  I am fine with patenting certain things, so in this case, that's fine.

---

