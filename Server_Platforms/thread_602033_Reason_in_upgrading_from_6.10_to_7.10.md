---
title: "Reason in upgrading from 6.10 to 7.10?"
date: 2007-11-03
forum: Server Platforms
---

### Post by frodemt on 2007-11-03
Hi.

Is there any point in upgrading from 6.10 server to 7.10 server?

Has 7.10 server bether security than 6.10?

Regard from Frode,

---

### Post by frodemt on 2007-11-12
So noone has any oponion about this? :confused:

---

### Post by reckless2k2 on 2007-11-12
only real reason is at the end of life cycle to be honest if everything is working fine for you. if you've got everything tweaked out well and to your liking with no issues, don't upgrade until end of life cycle. servers in general don't need much upkeep unless major issues. you probably should consider off loading once 8.04 LTS comes around. you will be approaching end of life cycle for 6.10. you will need to upgrade then. even still, that should be a clean install. the upgrade paths are usually rocky. you're better off backing up and clean install when 8.04 comes around. LTS will have a much longer life cycle so incremental version updates are irrelevant.

---

### Post by frodemt on 2007-11-12
Thank you for the answer reckless2k2.

Do you know when 8.04 LTS will be around?

---

### Post by rsambuca on 2007-11-12
8.04 -> April 2008!!

---

### Post by p_quarles on 2007-11-12
Ubuntu version numbers work like so:
year.month

So, 8.04 = April 2008. That's when it will be available, unless it gets delayed for some reason;.

And like reckless2k2 said, there's no reason to upgrade before the end-of-life. 6.10 is still getting all security updates. Personally, I use Debian Stable for my home server, A very long support cycle, and the "Stable" part is no joke.

EDIT: rsambuca beat me to it

---

### Post by reckless2k2 on 2007-11-13
p_quarles is right that debian is more stable and a much longer life cycle than anything ubuntu. debian proper is "harder" though to admin. not terribly by any means but ubuntu does do a lot of the work for you. hence the reason ubuntu is born. "easy debian"...hahahaha. 

if you are using ubuntu, it's probably because you like the support forums along with the VAST documentation. i personally use centos for my servers but have been playing with ubuntu and debian server models lately. i'm sure i won't offload anytime soon though. 

long and short, if you want long support cycle, use debian proper or an ubuntu LTS like 8.04. then you don't have to worry about 18 month force upgrade cycle. LTS is 5 years. 

i'm using centos 4 and it's supported until 2010 or 2012. can't remember which one. NOW THAT'S LONG.

---

### Post by Sporkman on 2007-11-15
> **reckless2k2 said:**
> i personally use centos for my servers but have been playing with ubuntu and debian server models lately.

How different is CentOS from Ubuntu in terms of filesystem structure re log files, config files ,etc, as well as package management & general admin? Particularly in a LAMP context?

I've noticed many web hosting cos have CentOS as their linux offering, so I've been thinking about learning CentOS...

---

### Post by reckless2k2 on 2007-11-18
sporkman,
centos is a red hat enterprise linux (RHEL) clone. it's basically "free" red hat enterprise. not to be confused with fedora core. fedora core is s development distro and the life cycle is short and packaging leads to MUCH instability in the distro. although fedora is the testing ground for RHEL, red hat looks a few fedora cycles back for any useful items. 

there are great "how to" setups for centos on sourceforge that do hand holding on the setup. more or less it's all the same under any linux distro. the difference is more so to how the distro is maintained or updated. ubuntu uses deb packaging while centos uses rpm packaging. a lot of times i test an install on ubuntu prior to moving to a stable centos. while the install is more times more difficult in centos, the maintenance there after is pretty much the same. most files are in the same places. if you admin ubuntu, there's a small learning curve going to centos but not drastic. if you admin debian, you shouldn't have much issue because you will know and or understand linux in general so centos admin won't be difficult. only reall difference i find is that centos packaging is older for stability and some files in /etc might not have a directory or the directory name is different (ie. apache2 in ubuntu but it's httpd in centos). it's nothing major though. 

i like centos because it's a setup and then you don't have to bother after that. i barely touch the box and i don't have to worry about end of life cycle any time in the near future. 
good luck.

---

### Post by Sporkman on 2007-11-18
Thanks for the good explanation reckless2k2.

---

