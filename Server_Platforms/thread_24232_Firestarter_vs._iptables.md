---
title: "Firestarter vs. iptables"
date: 2005-04-06
forum: Server Platforms
---

### Post by mario8723 on 2005-04-06
I'm new to security and hopefully would like to make a career out of it. With that said, here's my question:

Is it better to "custom" write your own iptables rules or run a "pre-configured" firewall like Firestarter.

Currently, I am running Firestarter, but am wondering if there are any advantages to running my own iptables script. Is there anything to be gained from doing this outside of understanding iptables more?

Thanks in advance for your responses...

---

### Post by NemoTheLobster on 2005-04-06
I'd say learn how to use iptables directly even if it's just so you can use the GUI tools more effectively.  You can also learn a lot just from looking at the ruleset that these scripts generate and figuring out how and why they do things the way they do.  

I stick with doing iptables directly, because my rulesets are simple enough that a GUI would be overkill.  I just migrated the Gentoo iptables scripts over to make it easier to manage.

It's especially frustrating when I know exactly what rule I'd put in, but I can't figure out how to do it with the GUI.  Or the GUI makes it a lot harder than it needs to be.  I haven't used Firestarter in a very long time though, so I'm not commenting on that one.

---

### Post by trash-can on 2005-04-06
There is no good answer to your question, but one thing is for sure, it surely will be better if you try and write your own firewall script and UNDERSTAND what you wrote and what every single line does! Then you can decide wheather you go witch a custom written script or some gui tool.

I chose to go with a custom script. Well, I tried couple of gui tools/programs which were ment to make running firewall seamless, but I found that I'm more comfortable with my own. Ok, maybe I was too lazy to spend more time and get more familiar with each of these tools, but at that moment I didn't actually care to waste my time, I needed something that worked well (my good old firewall script).

I suspect that for complicated firewall it would be more productive approach to choose some gui tool, but not on simple Desktop machine, IMHO.

---

### Post by p!=f on 2005-04-06
If you want to get some knowledge about iptables, write your own script. There're tons of tutorials around the web, just google a bit. :) Man pages are also very good start, simply said there's enough documentation to walk you through.
On the other hand, there're some issues you might not like. First, writing your own script will probably mean you will combine binaries with datas. Even it's not that big deal, we paranoids never know. :)
Second, if your script becomes huge, with plenty of rulesets, you may lose the sense for orientation. :) If you have more machines with different rulesets it may become true pain to administer it effectively.
I won't make any recommandation since setting up your firewall is very personal bussiness but if you ask me what I use, I'm the happy Shorewall user. Take a look at [http://www.shorewall.net](http://www.shorewall.net) for more informations if you're interested. No GUI required compared to Firestarter which may sound uncomfortable but it's practical if you run server. :)
Setting shorewall up is trivial task, same stands for adding rules which may not be case when you write your own script. 

Taken from shorewall.net site, section about
> 
The Shoreline Firewall, more commonly known as "Shorewall", is a high-level tool for configuring Netfilter. You describe your firewall/gateway requirements using entries in a set of configuration files. Shorewall reads those configuration files and with the help of the iptables utility, Shorewall configures Netfilter to match your requirements. Shorewall can be used on a dedicated firewall system, a multi-function gateway/router/server or on a standalone GNU/Linux system. Shorewall does not use Netfilter's ipchains compatibility mode and can thus take advantage of Netfilter's connection state tracking capabilities.

Shorewall is not a daemon. Once Shorewall has configured Netfilter, it's job is complete. After that, there is no Shorewall code running although the /sbin/shorewall program can be used at any time to monitor the Netfilter firewall.

On the other hand someone could tell you running Shorewall is not that "cool" as running your own script. :)
Make your choice. ;)

---

### Post by sinbad782 on 2005-04-10
guarddog has an ability to export scripts for use on other machines - might be worth a look. I think firewall-builder also has similar uses.

---

