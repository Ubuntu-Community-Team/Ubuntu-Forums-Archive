---
title: "Which command to automatically update packages"
date: 2011-05-11
forum: Server Platforms
---

### Post by Metroshica on 2011-05-11
I'm currently writing a script that will update the software packages on six ubuntu servers so I don't have to go in and update them manually constantly. Problem is, I'm not sure which command I should use to do this the most effective and safe way. Currently, I use sudo apt-get upgrade -y on my own machine, though I can see how this could be dangerous on production servers. I was in the IRC chat and I was told aptitude safe-upgrade is something I may want to look into. Is there a way I can only update security related stuff instead of everything? What do you guys suggest would be the best way going about this?

Another issue I can foresee is certain packages that have an interactive prompt. While apt-get upgrade -y takes care of most of this, MySQL would fail with this as it opens up it's own prompt. Anyway I could make my script skip these types of prompts, so I can go back and update them later manually? Thanks for the help.

---

### Post by arrrghhh on 2011-05-11
There's plenty of reasons why you should never do this.

You're asking for trouble, wouldn't you rather know what's being updated before updating it...?

There is a package, unattended-upgrades.  See the official Ubuntu doc on [Automatic Security Updates](https://help.ubuntu.com/community/AutomaticSecurityUpdates) for more info.

If you have many servers to manage, have a look at [Puppet](http://www.howtoforge.com/installing_puppet_on_ubuntu).

---

