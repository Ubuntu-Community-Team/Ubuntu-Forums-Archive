---
title: "Watson jr."
date: 2014-04-27
forum: Ubuntu Cloud and Juju
---

### Post by knud-g on 2014-04-27
Hi 

I read the following article about setting up a jr. Watson
and think it could be fun to try it out on top of open stack.
See [https://www.ibm.com/developerworks/community/blogs/InsideSystemStorage/entry/ibm_watson_how_to_build_your_own_watson_jr_in_your_basement7?lang=en](https://www.ibm.com/developerworks/community/blogs/InsideSystemStorage/entry/ibm_watson_how_to_build_your_own_watson_jr_in_your_basement7?lang=en)

Have anyone already tried to make a juju bundle for Watson jr. or juju charms 
for any of the components  [OpenNLP, OpenCyc, UIMA] ?

---

### Post by bhima-pandava on 2014-05-30
I've been trying off & on to build something vaguely similar to Watson jr. for a few years.  My take on this is that there are huge amounts of work in between the gaps between the various components needed (OpenNLP, OpenCyc, UIMA are just the large ones) needed to produce a minimally functioning proof of concept which the author of the article waves this away with the amusing "simple matter of programming". Moreover, having these 3 projects already installed wouldn't be as helpful as it might seem because for one such an installation wouldn't actually do anything and besides there's a lot to be learned about each of these projects in the misery of getting them built, installed, and configured.

It's a shame really because I suspect that there would be a lot of interest in a sort of personal Watson/private Siri and we're so tantalizingly close...

---

