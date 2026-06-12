---
title: "Anything around for Monitor GUI?"
date: 2009-12-12
forum: Server Platforms
---

### Post by Xiuh on 2009-12-12
I like to look at a web based monitoring GUI now and again and decided to setup one up after a LAMP setup. I'm far from familiar with most of the packages that work out well on Ubuntu. Off the top of my head, I had decided to setup Webmin. It's worked out alright, but the Ubuntu community's lack of interest in it and the fact I spent quite a bit of time trying to trick it out with minimal levels of satisfaction has got me looking for something else. Anyone have a suggestion on something like this that fits in well on Ubuntu server systems?

---

### Post by shairozan on 2009-12-12
Hey there

I highly recommend Opsview, as I have been using it for over a year now. It's basically running Nagios on the bottom, but they developed a really nice PHP front end for it. You can take a look at it at their website.

 [http://www.opsera.com]("http://www.opsera.com")

They have a repository that you can install the actual application from (using apt-get. Thankfully no need to compile) and they have very concise FAQs on how to get it setup. 

I monitor 5 sites across the United States with it. It's a solid piece of software.

---

### Post by Queue29 on 2009-12-12
What do you mean, "trick it out"? Webmin does precisely what it was made to do, and it does it well. What more do you want?

---

### Post by Xiuh on 2009-12-12
Thanks for the heads up shairozan. I looked it over for a bit, I think I'll give it a spin.

So far as "tricking out" my Webmin, that process would probably involve adjusting the configuration settings, module and log organization, locating additional libs to recompile for improved modular support, etc. Anyways, I have nothing negative to stay about this package, just wasn't my cup of tea and I was interested in trying something new. No crime in that.

---

