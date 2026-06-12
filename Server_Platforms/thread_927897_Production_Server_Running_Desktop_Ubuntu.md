---
title: "Production Server Running Desktop Ubuntu"
date: 2008-09-23
forum: Server Platforms
---

### Post by steve_c on 2008-09-23
I installed Ubuntu Desktop 7.10 on a server because I needed it to have the xlibs necessary to do X-fowarding and the Restricted nVidia driver for hardware 3D acceleration. At the time I didn't realize there really was a linux-restricted-modules-server that just didn't come installed on Ubuntu Server.

Since then I've upgraded the server to Ubuntu Desktop 8.04 LTS, for the LTS aspect.

Between the upgrading and the fact this is has and is running a bunch of extra crap for the desktop, I'm really tempted to put the server down for a weekend and reinstall 8.04 server fresh.

That said my friend who is much more experienced than I has always harped on me with the "if it ain't broke don't fix it" mantra. So I know the other alternative would be to disable X/Gnome from auto starting, and use aptitude to install the Ubuntu Server kernel. That would essentially make it Ubuntu Server, but with a bunch of extra, mostly unused crap on it, which would be fairly harmless other than taking up a small amount of disk space and cluttering the directory structure just a bit.

While this server is not mission-critical and I can put it down for a weekend with no great loss, it's being used fairly regularly by the researchers in my group--I know I'd have to back up roughly a half terabyte of data and try to make sure I get all the packages they need reinstalled (there's got to be a log somewhere--/var/log/dpkg or /var/log/aptitude maybe?).

So could any experienced sysadmins give me their advice/opinions/alternative suggestions? I don't want to do something that's going to accidentally scrooge myself, but at the same time I want to try to make this server run as best as it possibly can.

Thanks for any help.

---

### Post by HermanAB on 2008-09-23
Simple, just switch to runlevel 3:
$ sudo init 3

and to get the GUI again:
$ sudo init 5

That is what runlevels are for.

Cheers,

Herman

---

### Post by cdenley on 2008-09-23
> **HermanAB said:**
> Simple, just switch to runlevel 3:
$ sudo init 3

and to get the GUI again:
$ sudo init 5

That is what runlevels are for.

Cheers,

Herman

Not on debian-based systems. I think it would work like that if you run
```

sudo rm /etc/rc3.d/*gdm

```

Or you could just use the gdm init script to switch back and forth
```

sudo update-rc.d -f gdm remove

```
then, to start GUI
```

sudo /etc/init.d/gdm start

```
and to stop it
```

sudo /etc/init.d/gdm stop

```

---

### Post by lmno745 on 2008-09-23
What is World of Warcraft?Players from across the globe can leave the real world behind and undertake grand quests and heroic exploits in a land of fantastic adventure and [yoga mats]("http://www.yoga-mats.cn/") . Do you want to [China Travel guide]("http://www.china-travel-guide.cn/") yourself?So please let us do this task for you, one of our World Of Warcraft powerlevelers work for you as a full- time job other than part-time.s a massively multiplayer online game, World of Warcraft enables thousands of players to come together online and battle against the world and each other. As we know, When you first start a game of World of Warcraft, you will be taken to your race's starting area. All the races except trolls and gnomes begin in a unique location.So it takes a long time to powerlevel a powerful character for many players, for the player's energy and time are limited. [http://www.yogawww.com](http://www.yogawww.com), [http://www.chinatravelvip.com](http://www.chinatravelvip.com), WOW Power Leveling is our primary service, we offer [wow gold]("http://www.wowchina.us/") & [wow gold]("http://www.wowgoldsell.com/") service,and is on sale now for a limited time! You can purchase our power leveling service at a much lower price than any of our competitors. We don't use any Bots or Macros to power level your character.All of our employees are skilled World of Warcraft players, who personally powerleveling your character, to provide even more safety to your account.  We will complete the wow power leveling in a very short time, and you can play the character at your desired level. During the progress of World of Warcraft powerleveling, you can get all information about your World of Warcraft powerleveling status anytime.We use real players (WOW Power Leveler) to level your character, ALL HAND MADE. Your account will be safe and secure,GUARANTEED.Our goal is to make sure all our customers are satisfied with their wow powerleveling & [cheap wow gold]("http://www.howtogold.com/") orders. We upgrade your characters levels, skills and more.safety to your account.[http://www.yogawww.com](http://www.yogawww.com), [http://www.chinatravelvip.com](http://www.chinatravelvip.com), [www.wowchina.usOur](www.wowchina.usOur) team consists of veteran players with over 1 years of playing experience, they offer quality and professional service to all our customers. No risk is ever involved during this process.Our staff will not chat to anyone during this progress, so don't afraid about your character.Our service is standing by 24/7 to serve you.

---

