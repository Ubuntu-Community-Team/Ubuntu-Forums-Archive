---
title: "what software developement model ubuntu uses ?"
date: 2009-06-27
forum: The Cafe
---

### Post by medya on 2009-06-27
as you know in software eng. , there are several models for developing a software ,
AGIlE , FDD , XP , Waterfall , CoCoMo...

what model ubuntu developers use ?

I would like to know more about the model that they develop ubuntu with

---

### Post by phrostbyte on 2009-06-27
That's a pretty good question. :) I'd be interested to know too.

---

### Post by 23meg on 2009-06-27
Ubuntu is made of hundreds of components coming from different upstream projects, each of which have their own preferred models, so it wouldn't be a stretch to say that it probably includes code that was written with pretty much every modern development model.

I haven't observed a particular model that's prevalent in the broader Ubuntu development community, though Canonical seems to favor Agile Development (mostly test-driven and integrated with community testing processes) for both Ubuntu components, and other projects such as Bazaar and Launchpad.

You might be interested in the Community-Agile software guidance paper by Ian Clatworthy from Canonical:

[https://launchpad.net/community-agile](https://launchpad.net/community-agile)

---

### Post by medya on 2009-06-27
> **23meg said:**
> Ubuntu is made of hundreds of components coming from different upstream projects, each of which have their own preferred models, so it wouldn't be a stretch to say that it probably includes code that was written with pretty much every modern development model.

I haven't observed a particular model that's prevalent in the broader Ubuntu development community, though Canonical seems to favor Agile Development (mostly test-driven and integrated with community testing processes) for both Ubuntu components, and other projects such as Bazaar and Launchpad.

You might be interested in the Community-Agile software guidance paper by Ian Clatworthy from Canonical:

[https://launchpad.net/community-agile](https://launchpad.net/community-agile)



thats not a reasonable reply ,
there are models which are based on components .
but which one of these models Ubuntu uses .(you cant says ubuntu uses none of them)

---

### Post by 23meg on 2009-06-27
I think it's a reasonable reply, given the fact that the vast majority of the code that makes up Ubuntu is not *written* by Ubuntu developers or Canonical, but is *brought together* and *maintained* by them.

If how that happens is not quite clear to you, [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment) may help.

---

### Post by medya on 2009-06-28
> **23meg said:**
> I think it's a reasonable reply, given the fact that the vast majority of the code that makes up Ubuntu is not *written* by Ubuntu developers or Canonical, but is *brought together* and *maintained* by them.

If how that happens is not quite clear to you, [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment) may help.

but still it has to have a NAME , the model "it is not important that they dont do the coding, in some models of software eng , u dont do the coding "
what is the model of ubuntu?

---

### Post by Tibuda on 2009-06-28
> **medya said:**
> but still it has to have a NAME , the model "it is not important that they dont do the coding, in some models of software eng , u dont do the coding "
what is the model of ubuntu?
I don't think you understand what Ubuntu really is. Ubuntu is a set of different software developped by different people (Kernel, shell, Gnome, the applications...).

If you really want a name, I would choose ["release early, release often" or "given enough eyeballs, all bugs are shallow"]("http://catb.org/esr/writings/cathedral-bazaar/").

---

### Post by 23meg on 2009-06-29
[QUOTE=medya]but still it has to have a NAME , the model "it is not important that they dont do the coding, in some models of software eng , u dont do the coding "[/QUOTE]

Perhaps a tautological description such as "Free software operating system development" is the only possible "name", if you must have one.

---

### Post by ukripper on 2009-06-29
I'd say "AGILE based community collaboration development model"

---

### Post by medya on 2009-07-01
isnt there any official developer or moderator or official member of ubuntu, to tell us what is the exactly model that they use ?

I would like to know,
I have 6 hour courses , in unvirsity, software engineering, and professors keep on telling us, IT DOES MATTER ! IT IS IMPORTANT...
if so , then ubuntu which is an example of successfull software, what kind of model ubuntu uses Offcially ?

---

### Post by RAOF on 2009-07-01
Ubuntu *isn't* an example of successful software.  This is a common mis-understanding of the nature of Ubuntu (and linux distributions in general, really).

*Ubuntu does not develop software*.  Thus, Ubuntu does not follow a software development model.

There are various software development projects which are undertaken by Ubuntu members - these have different strategies.  I know that bazaar and launchpad are somewhere on the test-driven-development spectrum, but not much more.

Also, many open source projects simply *don't* have an explicit model, other than "write the code, and see if the core developers accept it".

---

### Post by medya on 2009-07-02
> **RAOF said:**
> Ubuntu *isn't* an example of successful software.  This is a common mis-understanding of the nature of Ubuntu (and linux distributions in general, really).

*Ubuntu does not develop software*.  Thus, Ubuntu does not follow a software development model.

There are various software development projects which are undertaken by Ubuntu members - these have different strategies.  I know that bazaar and launchpad are somewhere on the test-driven-development spectrum, but not much more.

Also, many open source projects simply *don't* have an explicit model, other than "write the code, and see if the core developers accept it".

thanks this answer satisfies me ,
btw on your profile it says "ubuntu developer" :p

how about softwares like AmaroK or Pidgin, could we tell what model they use ?
or they also dont have a model other than  "write the code, and see if the core developers accept it" ??

---

### Post by RAOF on 2009-07-02
> **medya said:**
> ...
how about softwares like AmaroK or Pidgin, could we tell what model they use ?
or they also dont have a model other than  "write the code, and see if the core developers accept it" ??

In my experience, no project explicitly says "we use the such and such development model".  People really don't think about it all that much :).

---

### Post by medya on 2009-07-05
so you mean all these courses that we study in the university are useless ..ha ?

---

### Post by RAOF on 2009-07-06
> **medya said:**
> so you mean all these courses that we study in the university are useless ..ha ?

Not necessarily useless.  But certainly you won't walk into a development shop and have them say: "Ok, we use the Waterfall methodology exclusively. Go!".

Understanding the strengths and weaknesses of the various models can help you make sense of and (potentially) improve the actual workflows you encounter, though.

---

### Post by ukripper on 2009-07-07
In short - "Right tool for Right job"

---

