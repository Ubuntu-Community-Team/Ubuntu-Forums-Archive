---
title: "work on a Gourmet recipe collection"
date: 2009-01-02
forum: The Cafe
---

### Post by ndefontenay on 2009-01-02
Hi everyone,

I was looking for a gourmet recipe collection and found that instead:

[http://brainstorm.ubuntu.com/idea/14521/](http://brainstorm.ubuntu.com/idea/14521/)

On that thread, there's a link to wikipedia cookbook.
So I thought that if instead of discussing, we could insert the wikipedia cookbook in gourmet and then export it and put all of them in a tgz file ready to import :)

I've look at the list and if we are just 4-6 people working on it, we could complete the job in a week (working hard).

So this is the idea. What I'm not sure about is:

1) How to organize the job say if there's newcomers?
2) Where to store the collection?
3) How to easily allow for people to add there recipes to the collection in the future?

This could easily be a one shot job which I could do myself for 3-4 months and provide, but I want it to be more than that. We are a great community and I'm sure we can bring openess to the food community! After all, there is already an open beer and an open cola ^^

--
This could be for the future of the tool if it gets popular and used enough:

4) See with the guys from the project if it would be possible to get grading informations from everyone, make an average rating to input to the next version of the recipe collection.

Bring your ideas in about how to organize that guys. 
Mailing list, blog, forum?

Get wild here. We will filter the good ideas after.

---

### Post by Mr. Picklesworth on 2009-01-02
Oh, I wasn't expecting this to happen :)
(That's my Brainstorm page!)

I would happily port over some recipes from Wikipedia Cookbook. Alas, Gourmet doesn't permit photographic directions which are used very often in there. You can only have one image for each recipe. Shouldn't be too tricky to allow multiple images, though.

A little Launchpad project would be a nice way (hosted in a Bzr repository) since that way people can contribute in an easy, distributed way. I also definitely don't think this should be proprietary to Ubuntu; push the starter collection upstream. (Although some downstream goodies never hurt anyone).

---

### Post by smartboyathome on 2009-01-02
What about the Ubuntu Forum's Cookbook? How would this be different? :)

---

### Post by gnomeuser on 2009-01-02
For inspiration Linux Kernel Hacker Robert Love' [Food Tastes Good](http://food.rlove.org/) blog.

---

### Post by laceration on 2009-01-02
Sorry, but I disagree with brainstorm idea.  I think the recipe manager should be empty.  I don't use the Gourmet Recipe Manager--didn't even know about it-- but use a little db program I wrote myself.  I'll do a search for what I want to make and put together my own recipes from I find.  An idea here, an idea there.  Following one narrow little collection is a limit we don't have to follow since we left the book era for the www era.

...and OP, what do you need recipes for?  You are from Thailand, what a great cuisine your county has!  Couldn't you ask your Mother anything you need to know?:)

---

### Post by ndefontenay on 2009-01-04
Hi laceration,

Hi Mr Picklesworth.

Happy new year!


I'm sorry for the delay in replying... New year etc...

The idea is not to force feed (if I may say so x) people with recipes when installing Gourmet but to build a library and make it available. People are free to take it for a basis... Or not. 

There's a lot more in cooking than the recipes we like. If you take it seriously and if you start, there's a bunch of sauce, pastries, broath which are basis for other food. Also, since I'm so excited with this idea, I'm even planning to contact a few great Chefs I know to ask them if I can use their recipes or if they could give me a recipe they like etc...

There's a lot of directions we can go. For now, I want to have an available platform and start building a community and have gourmet and the library known through cooking blog, special hosts recipes etc... Basically make it lively.

For where I'm from: I'm from [Mauritius]("http://maps.google.com/?ie=UTF8&ll=-24.287027,63.720703&spn=26.956507,39.550781&z=5") otherwise. I just live in Thailand. Let's just say I like hot countries :) My food culture is a mix of french, indian, chinese, creole food.

It takes a few motivated people to build something great. If you are with me on this, let's make this happen right now. For people reading the thread, if you guys are interested in jumping in the boat, send me a message or write in this thread.

When we know who's ready to spend some time on it, I'll contact the Gourmet guys to let them know of what we are doing in order to exchange link and so on.

cheers

Nico

---

### Post by ndefontenay on 2009-01-04
[https://launchpad.net/recipes](https://launchpad.net/recipes)

---

### Post by Ripfox on 2009-01-04
Um I just installed gourmet with aptitude and it removed some linux headers?

---

### Post by Ripfox on 2009-01-04
Anybody? That was weird to me but maybe I never experienced it before?

---

### Post by ndefontenay on 2009-01-04
Hi.

I encountered the same behavior when I was installing nfs. So it might not be related to just gourmet after all.

I didn't ask much question about it though because everything seem to be working fine anyway...

Try to post the question in the general help area. You might have more answer.

Nico

---

### Post by laceration on 2009-01-04
> there's a bunch of sauce, pastries, broath which are basis for other food
That is a good idea.  There are almost unlimited www food resources available, but this, as far as I know, is unique.  The French mother sauces for instance.  Count me in on that!

I like cold countries (it's 16 degs here now--that's well below 0 on the C scale) but hot food:).  My food culture, The USA, is one where the art has been removed and replaced with an industrial process, where the consumer is just a part:P. But that is just one(bad) aspect of it, there are also the many influences of the many types of people here.  Most notably, imho, Mexican.

---

### Post by Mr. Picklesworth on 2009-01-04
> **ndefontenay said:**
> [https://launchpad.net/recipes](https://launchpad.net/recipes)

Yay! You should also create a [Team]("https://edge.launchpad.net/people/+newteam") for this, too, and link it to the project. That way we can stay in touch / organize things a bit better.
(A team gets its own PPA, for example, which could really help).

There are some minor grammar errors in that project description, and I must say the line "biggest recipe library available" made me a bit worried; I don't think that is a great goal, given a few things:
Google (or maybe Cuil) is the biggest recipe library ever. Biggest does not mean Best. Your other goal is a bit more important; to make things look nice and package the data for certain applications to improve the user experience.

No pressure intended, though. Of course, you just put that up, and I usually don't even *have* project descriptions.
Thanks for taking the initiative!

Now all we need is some support in Gourmet for multiple recipe databases and a default database in a system directory. Oh, and some recipes. And nice photographs.

Good idea to put sauces in there. It would be neat if we could make this somewhat educational. Not "Teach yourself to cook!", but at least understandable to those very new to cooking with lots of explanations. I believe Gourmet has room for that kind of stuff. I keep getting a desire for Ubuntu to be sort of a land of exploration and discovery, and lightly educational tools could help that a great deal. They seem like the perfect thing to go with the free software ethos.

I guess I could write a nice letter to Vikram Vij begging him for some Creative Commons curry recipes :P

As for the license, could I recommend Creative Commons? GPL is really targeted at code, whereas CC is aimed at *content* like recipes and writing. Most free recipes you find on the web will be Creative Commons, because it's more relevant to the field and *really easy* to organize rights.

---

### Post by ndefontenay on 2009-01-04
I'm probably going a bit ahead of myself but that's how I keep myself motivated x)

I go create the team. I'll let you check the grammar and tone down the description.

---

### Post by yabbadabbadont on 2009-01-04
I've never tasted "Gourmet" before... does it taste like chicken?  :twisted:


(It looks like a good idea to me)

---

### Post by yabbadabbadont on 2009-01-04
Edit: Stupid forum software... first it tells me that I have to wait 20 seconds between posts (when it has been a couple of minutes already...) then it double posts my submission.  (now we know why the delay notice was issued)

---

### Post by ndefontenay on 2009-01-04
The team is created and open.

I haven't found the license you were talking about so I kept it as is for now. If you are allowed to change it, feel free to do so.

I like your ideas of doing something educational.

My idea of having a recipe DB started with my needs:

I want to do some recipe, I don't know how to do a pastry for a Quiche Lorraine. I go online and google it... Problem is, google is getting biased by commercial web sites implementing their web design for highest ranking on a LOT of keywords. It gets harder to find what you want on a first shot (found out this is getting really true for bread recipes on google France for which all keywords tend to go to one web site selling a "bread cooking machine" and for whom all recipes requires the said machine)...

Also, it is good to keep in mind that the less developed countries have an internet which is not as smooth as it is in the US, Canada and Europe. I got ADSL in Thailand but it's not as fast as when I was living in Paris last year... That is true in pretty much all of Asia (except maybe Singapore and Japan is not counted in), the African continent (except maybe South Africa) and pretty much all the islands you can think of.

The addition of these 2 factors had me looking 1) For a recipe storage program 2) A library of recipes. It's just too much time searching otherwise.

I hope this explanation answer the question of why would we have a recipe DB when we got the internet. If we can get the whole in one shot while people sleep (when it's fast) it's so much easier to browse it locally...

I think that a lot of people who got a fast ADSL would also find it useful to have their recipes "at home".

---

### Post by ndefontenay on 2009-01-04
As per laceration note: 

It is quite true and we might as well start with that.

---

### Post by Ripfox on 2009-01-05
> **ndefontenay said:**
> As per laceration note: 

It is quite true and we might as well start with that.

What about starting with the fact that when you install Gourmet from the repos it removes several Linux Headers?

---

### Post by Mr. Picklesworth on 2009-01-05
> **Ripfox said:**
> What about starting with the fact that when you install Gourmet from the repos it removes several Linux Headers?

```
Package: gourmet
Priority: optional
Section: universe/gnome
Installed-Size: 7424
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Rolf Leggewie <foss@rolf.leggewie.biz>
Architecture: all
Version: 0.14.0-1ubuntu2
Depends: python (>= 2.3), python-central (>= 0.6.7), python-imaging, python-glade2, python-gtk2 (>= 2.3.92), python-pysqlite2 | python (>= 2.5) | python-sqlite3, python-reportlab, python-sqlalchemy
Recommends: python-gnome2
Suggests: libmetakit-python, python-pyrtf
Filename: pool/universe/g/gourmet/gourmet_0.14.0-1ubuntu2_all.deb
Size: 1635072
```

Not Gourmet's problem, or the Gourmet packager's problem. If you're sure it isn't your system or a misinterpretation, then the bug is with one of those cute, harmless looking dependencies.

Keep in mind that Debian keeps track of dependencies for a good reason; it isn't just to make people crazy. If killing a certain linux-headers package isn't wiping out anything else, it's probably safe to do. Sometimes this is done for cleanup, although I don't think apt does that kind of stuff automatically so it depends on how this is happening. Actually removing the Linux kernel would cause apt to uninstall every package on your system that depends on there being a kernel. Granted, if something is installed that needs those headers *outside* of the Debian package system, you can consider yourself doomed :P

---

### Post by Ripfox on 2009-01-06
> **Mr. Picklesworth said:**
> ```
Package: gourmet
Priority: optional
Section: universe/gnome
Installed-Size: 7424
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Rolf Leggewie <foss@rolf.leggewie.biz>
Architecture: all
Version: 0.14.0-1ubuntu2
Depends: python (>= 2.3), python-central (>= 0.6.7), python-imaging, python-glade2, python-gtk2 (>= 2.3.92), python-pysqlite2 | python (>= 2.5) | python-sqlite3, python-reportlab, python-sqlalchemy
Recommends: python-gnome2
Suggests: libmetakit-python, python-pyrtf
Filename: pool/universe/g/gourmet/gourmet_0.14.0-1ubuntu2_all.deb
Size: 1635072
```

Not Gourmet's problem, or the Gourmet packager's problem. If you're sure it isn't your system or a misinterpretation, then the bug is with one of those cute, harmless looking dependencies.

Keep in mind that Debian keeps track of dependencies for a good reason; it isn't just to make people crazy. If killing a certain linux-headers package isn't wiping out anything else, it's probably safe to do. Sometimes this is done for cleanup, although I don't think apt does that kind of stuff automatically so it depends on how this is happening. Actually removing the Linux kernel would cause apt to uninstall every package on your system that depends on there being a kernel. Granted, if something is installed that needs those headers *outside* of the Debian package system, you can consider yourself doomed :P

There's alot of maybes and probablys in that statement...:D

---

