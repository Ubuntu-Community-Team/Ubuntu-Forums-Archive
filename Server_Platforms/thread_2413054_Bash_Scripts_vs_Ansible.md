---
title: "Bash Scripts vs Ansible"
date: 2019-02-20
forum: Server Platforms
---

### Post by branau on 2019-02-20
I'm getting a little tired of running the same old commands over and over again for setting up new servers, or migrating software between servers, and I'd like to make the process a little more automatic. I don't tend to do this often, but for my home infrastructure I do a fresh install of the latest Ubuntu every time there's a new LTS and I have a few services running on VPSs that I upgrade every so often as well. At the moment I've also got all of my home services running on a single server, but I'd like to split them up onto multiple different servers as I can't really afford to scale up the server but I can certainly scale out with a few raspberry pis to share the load. I've been debating between just writing a few shell scripts to do the setup process for various services for me or taking the time to learning something like Ansible which as I understand is specifically built for this. I'm not a sysadmin by trade, but I am a dev and could potentially see myself switching over to more sysadmin work at some point in the future. A few of the services I manage for myself are for example my Nextcloud instance, a git server, a Jenkins instance, an airsonic instance, an IRC bouncer, and a Mastodon instance, to name a few (I've got plenty more though and seem to be adding more constantly). Would Ansible be overkill for these things, or would it be more sensible than a collection of bash scripts?

---

### Post by QIII on 2019-02-20
Hello!

I use Ansible for this sort of thing.

If you are administering 10 or fewer machines, you can use the personal-use version of Ansible Tower.

It's always good to learn new tools to have in your hip pocket.

You could also use SaltStack, Puppet, Chef, etc, but I don't think any of them have a free-to-use version.

---

### Post by LHammonds on 2019-02-22
Bash is part of the system and has no extra cost.  That is why I use it.  If you would like to see some of the scripts I use to automate my servers so I don't have to touch them or do very little when I do need to touch them, take a look at my sig.

LHammonds

---

