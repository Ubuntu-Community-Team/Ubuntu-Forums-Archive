---
title: "Puppet Puppetmaster"
date: 2009-07-13
forum: Server Platforms
---

### Post by awreneau on 2009-07-13
We are beginning to roll out a few Ubuntu desktops at our company and I've been tasked w/ providing a management system for the systems.  

I've looked at Landscape, have a trial running at present.
I'm trying Puppet but it's giving me a little trouble.
Planning on trying cfengine as well.

I've googled puppet(puppetmaster) and ubuntu and numerous other combinations only to come up short.

Can anybody point me to a good tutorial, thats up to date, on cfengine and puppet for ubuntu?  The reductive labs instructions are more geared towards the tarball install or so it seemed to me.

Would appreciate the help.

---

### Post by Silver Knight on 2009-08-15
> **awreneau said:**
> Can anybody point me to a good tutorial, thats up to date, on cfengine and puppet for ubuntu?

Personally, I have not used cfengine in rather a long while, and have long since lost all the information I had collected regarding it, so I can not be of much help with that one; ***however***, I just happen to have some articles bookmarked regarding Puppet which struck me as potentially useful during my own research into this topic.  If I've done it right, the article titles *(enclosed in quotes)* in the following paragraph **should** be clickable links to the articles themselves, but just in case something goes awry, I will also post the addresses of the articles as a list at the end of my post for copy and paste purposes.

While it's not exactly up-to-date *(actually a couple of years out of date to be accurate)* the howto at howtoforge titled "[Configuration Automation & Centralized Management With Puppet on Ubuntu]("http://www.howtoforge.com/installing_puppet_on_ubuntu")" may contain enough mostly accurate information to help you get started with Puppet.  There is also an article titled "[Managing Ubuntu instances with Puppet]("http://theshadowaspect.com/posts/managing-ubuntu-with-puppet.html")" which takes a more manual approach to the process (installing from source, etc), an article titled "[Ideal Linux (Debian/Ubuntu) Deployment]("http://waldemar.schlackow.de/node/7")" which appears to be about unattended installation and configuration of Ubuntu using Puppet, and a more recent article titled "[Puppet: Server Configuration Made Easy]("http://muffinresearch.co.uk/archives/2009/01/18/puppet-server-configuration-made-easy/")" which may be helpful.

 These are just a few of the articles I have currently in my reading queue at the moment as I embark on my adventure of learning the differences between Mandriva Linux (my distro of choice for the past 7+ years) and Ubuntu Linux (the distro I am currently exploring at this very moment).   Hopefully one or all of these articles are/will be at least somewhat useful to you [I](although, I do notice that this post is marked as being 4 weeks old at the time I came across it, so I do sincerely hope that I'm not posting too late to be helpful here.)
[/I]---
~{ Silver Knight }~
---
*(Articles mentioned in my post are listed below in the order that I mention them above.)*

[LIST]
[*][http://www.howtoforge.com/installing_puppet_on_ubuntu](http://www.howtoforge.com/installing_puppet_on_ubuntu)
[*][http://theshadowaspect.com/posts/managing-ubuntu-with-puppet.html](http://theshadowaspect.com/posts/managing-ubuntu-with-puppet.html)
[*][http://waldemar.schlackow.de/node/7](http://waldemar.schlackow.de/node/7)
[*][http://muffinresearch.co.uk/archives/2009/01/18/puppet-server-configuration-made-easy/](http://muffinresearch.co.uk/archives/2009/01/18/puppet-server-configuration-made-easy/)
[/LIST]

---

### Post by EmmEff on 2009-08-15
If you're following the Reductive Puppet [Installation Guide](http://reductivelabs.com/trac/puppet/wiki/InstallationGuide), simply skip the "Install Puppet" step.  Everything after that is topical, whether it be a tarball or Ubuntu deb installation.  This is how I learned Puppet.

---

