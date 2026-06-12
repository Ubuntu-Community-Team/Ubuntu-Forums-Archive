---
title: "systemd news"
date: 2020-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by kc1di on 2020-04-30
Some interesting changes coming to systemd. read about it[ here. ]("https://www.techrepublic.com/article/linux-home-directory-management-is-about-to-undergo-major-change/")

---

### Post by webaake on 2020-04-30
I wish for a Ubuntu version WITHOUT systemd. Is that PC?

---

### Post by VMC on 2020-04-30
That's very Homey :)

---

### Post by Tadaen_Sylvermane on 2020-04-30
> **webaake said:**
> I wish for a Ubuntu version WITHOUT systemd. Is that PC?

Gonna be the devil's advocate

I wish people would get over it and let it go.

No offense :)

---

### Post by CatKiller on 2020-04-30
> **webaake said:**
> I wish for a Ubuntu version WITHOUT systemd.

There will never be a version of Ubuntu without systemd until a better successor comes along. It's not going to go back to 1983's init scripts. Ubuntu already created something that was better than those, and systemd was still better.

Feel free to move to devuan.

---

### Post by andrew.46 on 2020-05-01
> **webaake said:**
> I wish for a Ubuntu version WITHOUT systemd. Is that PC?

My daily computing is done on Slackware which does not use systemd nor does it suffer from this omission...

---

### Post by QIII on 2020-05-01
Automobiles are noisy and smelly.  I will stick to my horse and buggy, thank you very much.  :)

---

### Post by andrew.46 on 2020-05-01
> **QIII said:**
> Automobiles are noisy and smelly.  I will stick to my horse and buggy, thank you very much.  :)

Actually I have just come back from mucking out the stables :)

---

### Post by Artim on 2020-05-01
It sounds like it makes /home portable between computers, which is kinda cool.  I wonder if it would decrease the odds of a mess-up when upgrading the OS while preserving the /home partition.

---

### Post by webaake on 2020-05-01
Well, I'm already running Devuan and Obarun on other machines with good results. And thanks for the tip about Slackware!

I only wish that this forum would be more influnced by critical thinking. Over the years I've seen some of Canonicals ideas be like "The Emperors New Clothes". I see the OMG Ubuntu site only discuss themes, icons and wallpapers - superficial. 

Slackware here we go.... :) :)

---

### Post by QIII on 2020-05-01
What sort of critical thinking is absent?

---

### Post by andrew.46 on 2020-05-01
> **webaake said:**
> Slackware here we go.... :) :)

My best advice is to avoid Slackware 14.2 which is very long in the tooth, there will be a 15.0 release soon enough. Perhaps the safest course would be to run a recent snapshot of -current in VM before committing (or not!) when the release version comes to light. And: Have Fun!!!

---

### Post by webaake on 2020-05-01
When searching on this forum on "systemd future" and scrolling back to 2014, only one thread remotely discussing meta perspective can be found. This: [https://ubuntuforums.org/showthread.php?t=2200186&highlight=systemd+future](https://ubuntuforums.org/showthread.php?t=2200186&highlight=systemd+future)
it is from January 2014. Six years ago.

I would be glad if someone could point me to other threads here, discussing systemd and it's implications and future.

---

### Post by Tadaen_Sylvermane on 2020-05-01
Maybe because people have beat that horse to death everywhere else? No one here see's the point of endless debate about something already done and mostly set in stone. You can talk about it all day long. Won't change anything. I'd say that shows a bit more critical thinking, not less. Keep moving and adapt, or get left behind. Simple reality in the world.

---

### Post by QIII on 2020-05-01
systemd was introduced about 10 years ago and I have been using it with Fedora, the first adopter, since.  That means I probably encountered it long before those who use only Ubuntu.

As with anything else, there is a learning curve.  As with everything else there are problems.

I have three systems and three adjectives for you to associate, if you are able:

systems:  init, upstart, systemd

adjectives:  asynchronous, parallel, serial.

systemd has a couple of downsides:  it could represent a bottleneck and it is not posix compliant.

What bottlenecks does serial initialization present?

Is Posix compliance a sacrosanct, dogmatic requirement for, as you said, "the future"?

As said, systemd is 10 years old.  We are now ***in*** systemd's "future".  It has been adopted by virtually all of the major enterprise Linux distributions.

Just some bones to critically chew on ...  

Cheers!

---

### Post by Artim on 2020-05-02
If you're gonna try Slackware, I suggest [SalixOS]("http://salixos.org").  It will "feel familiar" to Ubuntu and Debian users because it's package manager is so similar to Synaptic.  It's completely compatible with Slackware, so the repositories are vast with software.  It has some very cool unique tools for simplifying things, very GUI-oriented.  So much so that it is referred to as an OS "for lazy Slackers."

---

### Post by webaake on 2020-05-02
I went for PCLinuxOS. Seems ok. I can recommend it. 

I started with Ubuntu 7.04 and I've run them all up until 18.04. I've also run Arch for a long time. I have several machines with different distros.
Right now I'm evaluating the best distro WITHOUT systemd. Fore some years I didn't have the time to dig deep in Ubuntu. Now I have and I don't like what I see. If I'd like to beat the dead horse I'd do it.

---

### Post by DuckHook on 2020-05-02
I'm *really* excited about:

[list=1]
[*]Portable $HOME
[*]$HOME encrypted by default
[*]Easily resize $HOME
[/list]
I'm *really* worried about:

[list=1]
[*]Portable $HOME
[*]$HOME encrypted by default
[*]Easily resize $HOME
[/list]
SSH has always been a problem with fully encrypted $HOME but there are standard workarounds. I doubt it will be too hard for them to figure out a solution. The bigger problem to my mind would be newbies who auto login, then forget their passwords, or who don't backup and LUKS gets corrupted, and end up being locked out of their $HOME.

I can already see the frantic forum posts begging for help.

---

