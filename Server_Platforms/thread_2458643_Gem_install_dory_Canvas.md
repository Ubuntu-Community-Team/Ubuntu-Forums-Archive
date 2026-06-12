---
title: "Gem install dory Canvas"
date: 2021-03-01
forum: Server Platforms
---

### Post by dotto95 on 2021-03-01
Hello, I'm trying to install Canvas LMS on my ubuntu server.
It required dory package.

I installed it:
```
gem install dory

``````


Successfully installed dory-1.1.0
Parsing documentation for dory-1.1.0
Done installing documentation for dory after 0 seconds
1 gem installed



```

But when I run Canva's installer:

```


  ________  ________  ________   ___      ___ ________  ________
|\   ____\|\   __  \|\   ___  \|\  \    /  /|\   __  \|\   ____\
\ \  \___|\ \  \|\  \ \  \\ \  \ \  \  /  / | \  \|\  \ \  \___|_
 \ \  \    \ \   __  \ \  \\ \  \ \  \/  / / \ \   __  \ \_____  \
  \ \  \____\ \  \ \  \ \  \\ \  \ \    / /   \ \  \ \  \|____|\  \
   \ \_______\ \__\ \__\ \__\\ \__\ \__/ /     \ \__\ \__\____\_\  \
    \|_______|\|__|\|__|\|__| \|__|\|__|/       \|__|\|__|\_________\
                                                         \|_________|


Welcome! This script will guide you through the process of setting up a
Canvas development environment with docker and dinghy/dory.


When you git pull new changes, you can run ./scripts/docker_dev_update.sh
to bring everything up to date.


> Some additional dependencies need to be installed for your OS.
	Canvas recommends using dory for a reverse proxy allowing you to
	access canvas at http://canvas.docker. Detailed instructions
	are available at https://github.com/FreedomBen/dory.
	If you want to install it, run 'gem install dory' then rerun this script.



```

Can you help me?
Thank you

---

### Post by TheFu on 2021-03-01
gems are for ruby devs.
The expertise you need is a ruby dev who also uses docker.  When I was programming in Ruby around 2011, most ruby setups used rvm and bundler to handle dependencies. I got frustrated trying to keep up with all the huge changes in the Ruby language every other year and all the huge changes in the different ruby frameworks every other year.  Basically, re-porting the same code 3 times in 6 years just got boring, so I moved back to perl.

Sorry, but that is the extent of the help I can offer.

---

### Post by dotto95 on 2021-03-02
Thanks for the reply! I solved it by downgrading my Ubuntu from 20.04 to 18.04 LTS.

---

