---
title: "About creating UbuntuCE"
date: 2006-10-03
forum: Ubuntu Christian Edition
---

### Post by slimdog360 on 2006-10-03
Im not Christian nor do I Run UbuntuCE so I hope this is cool, but I have a question related to how it was created. So I suppose its directed the the person behind it, Jeremy? from memory. 
I want to create my own Ubuntu for myself, live cd and all. I want to change the Desktop environment and add in great detail my own packages etc.
So the question is, how was CE built? Was it made with anything special? All that sort of thing.

Ive seen reconstructor (haven't used it) but from what I can tell it only really give the ability to change the default wallpaper and some colours.

Thanks

---

### Post by mhancoc7 on 2006-10-03
Hi slimdog360,

Yes it is absolutely cool for you to inquire about how Ubuntu CE is developed.

I mainly use the [Ubuntu Customization Kit (UCK)]("http://uck.sourceforge.net/") to build it. [UCK]("http://uck.sourceforge.net/") is primarily designed to create localized LiveCDs in your own language, but with some of the extra scripts you can do some really cool stuff. The documentation is not that great for [UCK]("http://uck.sourceforge.net/"), but after you get the hang of it you can do some neat stuff.

I just started using [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") with Ubuntu CE v1.3. I only use it to replace the Usplash since it does it so easily. You can do a lot of neat stuff with [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") as well, including add and remove programs. It also makes changing the themes much easier than [UCK]("http://uck.sourceforge.net/"). [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") v2.0 is in the works which is going to implement a module component which looks promising as well.

All in all, I like [UCK]("http://uck.sourceforge.net/") the best since I can do stuff like preconfigure Dansguardian. I also like to work directly with the scripts from the command line. I think [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") in its current release is the best option for those wanting to make basic changes like themes and adding/removing programs.

I hope that helps.

Jereme

---

### Post by Raphink on 2006-10-03
Using scripts and tools such as Reconstructor or UCK is a way to do it indeed. However, some old customized Ubuntu projects have contacted us lately to learn how to do it the metapackage way, because it is stronger on the long run. 

It is a fact that using scripts and Reconstructor/UCK allows you to customize Ubuntu in a few hours, but it is not sustainable: you have to do it again with each new version, and you distribute unpackaged contents.

If all you want is to release a live CD for a particular need and don't plan to maintain it in the future, it is perfectly fine to use scripts. If you plan to still be around in 6 months or 1 year and to keep releasing new versions and build a community of users, then you rather not.

I strongly encourage every new derivative to contact the Ubuntu team and try to integrate in Ubuntu, using metapackages.


Raphaël

---

### Post by mhancoc7 on 2006-10-03
@ Raphaël

Well, I believe slimdog360 said that he wanted to make a LiveCD for himself. So UCK or Reconstructor are perfect solutions.

As for your comments about using UCK or Reconstructor to create a derivative, I do not completely agree. I am growing weary of some of your posts that seem to be aimed at undermining what we are doing with the Ubuntu CE project. I mean, why don't you wait and see if the Ubuntu CE Team are able to "sustain" our project before you pass judgement on it.

Yes, the Ubuntu CE project is going in a direction that you and probably many Ubuntu developers do not agree with. However, the Ubuntu CE Team are working tirelessly to make sure that Ubuntu CE will continue to grow and give Christian computers what they want in their OS.

I respect your experience with your initial attempt with Ichthux. I have watched your project from a distance with admiration. You have mentioned numerous times that you did not want me to make the same mistakes that you made early on. I appreciate your concerns and I take your thoughts into consideration more than you probably think.

So in short I would just like to ask you to please stop subtlely undermining our project. I think it is clear what your opinion is so I don't think it is necessary to take every opportunity to remind us. 

I hope you understand that I am not trying to be rude. I will continue to support your project with links and mentioning it when appropriate. I just wished you would not try to tarnish what we are doing with your opinions. I mean how would you feel if I joined the Ichthux forum and began saying stuff like, "Yeah, Ichthux is cool, but Ubuntu CE is better."?

God Bless, Jereme

---

### Post by slimdog360 on 2006-10-03
thanks

---

### Post by mhancoc7 on 2006-10-03
> **slimdog360 said:**
> thanks

No problem. If you ever have any questions please feel free to PM me.

Sorry for the rant in my previous post. I did not mean to hijack the thread, I just need to voice my thoughts.

Jereme

---

