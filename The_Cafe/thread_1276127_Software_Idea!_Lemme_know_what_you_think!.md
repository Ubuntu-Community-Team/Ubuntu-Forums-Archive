---
title: "Software Idea! Lemme know what you think!"
date: 2009-09-26
forum: The Cafe
---

### Post by Vert on 2009-09-26
I've been trying to think of a program that would help me learn Python3 and PyQT/PyGTK. I think I have an idea which hasn't been done yet in the FOSS world. I just wanted to throw this idea out there and see if the community would benefit and use this program.
  My wife and I sometimes have trouble deciding what we're going to have for lunch and/or dinner. So I thought I'd make a program which would choose a recipe at random which would be invoked from the command line. For instance you type in: recipe.py taco. And it pulls recipes about tacos from a set of recipes sites. If no argument is given then it is randomly picked. Then this idea extended to a GUI, what if I made it in QT (as I use KDE these days) and GTK (so it fits in with my wife's Gnome)? It could be used to search for a random recipe or it could save a found recipe (like a favorite's feature) or just visit the recipe's web page where you could bookmark it in your browser.
  Would people like to see this done? Or has it been done already and I was just unaware? I've been looking around online and I've only found proprietary software which has features even close to this. Thank you everyone for any and all feedback towards this idea!

P.S. Please forgive the rushed nature of this post. Busy day!

---

### Post by Frak on 2009-09-26
You could, and it's a good idea. The way I read it is that you want to screen-scrape the web page for ideas (?) In that case, be aware of the rights and conditions given by the page. Certain information on pages are kept as sole ownership of the creator. Even just distributing this stuff onto a users personal computer can be illegal.

If you're not distributing it, that's fine, but if you are, be sure to pass it by the site-owners first to get the OK on it before you delve into anything that could result in legal consequences. You are technically using their resources by requesting the information.

Your "take it to the page" idea would be a fool-proof way to get pass this restriction.

---

### Post by Vert on 2009-09-26
Thank you for reminding me about the possible legal consequences if I reformatted information! I completely forgot about this and got caught up in features and whatnot. I thought the URL link was going to be a secondary feature, suppose it'll have to be a main one :p

---

### Post by Tibuda on 2009-09-26
I think this would be a good website instead of a desktop application. A cooking social network for people to share and search recipes.

---

### Post by Vert on 2009-09-26
To be honest Daniel, this crossed my mind. I figured there has to be an OSS recipe sharing wiki-type site or something out there. So I was thinking I could add some functionality in there to save your own recipes and/or publish it on that wiki. And if it doesn't exist then I could outsource to the community and work with someone who would know how to do that. As it is though, this could take me a while to build (the client side app, I mean). I'm just learning Python and I've never really done a project that's been this big (all the features, plus a GUI in a language relatively unknown to me).

---

### Post by Frak on 2009-09-26
> **Vert said:**
> To be honest Daniel, this crossed my mind. I figured there has to be an OSS recipe sharing wiki-type site or something out there. So I was thinking I could add some functionality in there to save your own recipes and/or publish it on that wiki. And if it doesn't exist then I could outsource to the community and work with someone who would know how to do that. As it is though, this could take me a while to build (the client side app, I mean). I'm just learning Python and I've never really done a project that's been this big (all the features, plus a GUI in a language relatively unknown to me).
Cookipedia written in Django?

---

### Post by otetiani on 2009-09-26
Great idea! I'm big into cooking and often use different websites to come up with ideas.

An added feature I use sometimes is to be able to search by ingredients.

Further, if you could add a rating system for the recipes by the users to help sort.

---

### Post by Vert on 2009-09-26
Outstanding!!! When I feel as though I have the software in a usable state, I'll be sure to contact them about integrating some functionality! Thank you very much for making me aware of them!

---

### Post by -grubby on 2009-09-26
As far as I know, Django is not out for Python 3 yet. Neither is PyQt. Or PyGTK. Besides, most of learning Python 3 is figuring out what's different than Python 2.x

---

### Post by Vert on 2009-09-26
Otet: I'll put serious consideration into if and how a rating system would work. It's an excellent idea, I'm just not sure if it could be implemented in a universal way (for instance, what about sites that don't support ranking?). It could definitely be implemented for locally kept recipes though!

---

### Post by Vert on 2009-09-26
PyQT works with Python 3, Django is in the process of being ported, and the status of PyGTK is unknown. As for the learning, well... I never knew Python 2.x to begin with, so I'm starting from a blank slate and would rather future proof my lessons as opposed to learning a syntax and having to relearn 6-12 months from now (or however long it's gonna take for Python 3 to become de facto over 2.x).

---

