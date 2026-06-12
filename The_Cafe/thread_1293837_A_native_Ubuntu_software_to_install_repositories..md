---
title: "A native Ubuntu software to install repositories."
date: 2009-10-17
forum: The Cafe
---

### Post by donniezazen on 2009-10-17
Greetings,

Every 6 month we get a new version of Ubuntu(Yay!!:guitar:). It is easy to add a single repositories but if you have like 8-10 repositories added, its mess to add all of them at a time. So, a software which will come with pre-installed repositories will make things easy for us. Developer can add their repositories and keys to this software. A warning can be added to this software that it may mess their system.

What do you think guys?

Thanks,
SK

---

### Post by NoaHall on 2009-10-17
Ehm. You do know you can edit the file easily just with gedit? :)

Copy the repos
Then do 
gksudo gedit /etc/apt/sources.list

then paste the repos 

Easy enough.
Edit -
Oh and for the keys, there's a new thing in karmic for easily installing keys.

---

### Post by donniezazen on 2009-10-17
> **NoaHall said:**
> Ehm. You do know you can edit the file easily just with gedit? :)

Copy the repos
Then do 
gksudo gedit /etc/apt/sources.list

then paste the repos 

Easy enough.

What about keys?

A lot of people want to try beta software but they don't . This software will open a pool of beta testers. For example VLC in Jaunty came with a separate video screen. But the beta version fixed this problem. Also this is going to be a comprehensive software for repos not just for a single repo.

---

### Post by NoaHall on 2009-10-17
I don't get it.

There's going to be a new thing for adding keys and repos easier in karmic, anyway.

---

### Post by Frak on 2009-10-17
> **NoaHall said:**
> Ehm. You do know you can edit the file easily just with gedit? :)

Copy the repos
Then do 
gksudo gedit /etc/apt/sources.list

then paste the repos 

Easy enough.
Edit -
Oh and for the keys, there's a new thing in karmic for easily installing keys.
Do you expect Mrs. Smith and her grandkid to know how to do that? Let's say they understand what it says, are they confident enough to do that?

---

### Post by misfitpierce on 2009-10-17
Ubuntu Tweak comes pre-installed with repos and you can just activate them for tons of apps and software. Try out newest Ubuntu Tweak version and check out the repos in there... Everything from TV style apps to theme repos to empathy repos and firefox nightly repos and more. Talking about something like that?

---

### Post by NoaHall on 2009-10-17
I'm pretty sure Mrs Smith and her grandchild don't want to get lots of repos at once ;)

---

### Post by donniezazen on 2009-10-17
Its all about making things accessible. You can do everything by command line but general users need GUI.

---

### Post by zekopeko on 2009-10-17
In Karmic there a simplified system for installing ppa's and their keys.
Simply paste the line (not the **deb [http://.](http://.)..** but something like this **ppa:gnome-do**, check a random ppa for example) from the ppa page into the software sources dialog and click add. That's it.
In the future they are planning an apt-url like system where you simply click a link and it prompts you to add the ppa.

---

### Post by donniezazen on 2009-10-17
> **zekopeko said:**
> In Karmic there a simplified system for installing ppa's and their keys.
Simply paste the line (not the **deb [http://.](http://.)..** but something like this **ppa:gnome-do**, check a random ppa for example) from the ppa page into the software sources dialog and click add. That's it.
In the future they are planning an apt-url like system where you simply click a link and it prompts you to add the ppa.

Sounds cool. But i am talking about a single place to check out all new and beta softwares by independent developers.

---

### Post by sandyd on 2009-10-17
i asked this earlier - its going to be part of ubuntu software center.
[https://wiki.ubuntu.com/SoftwareCenter](https://wiki.ubuntu.com/SoftwareCenter)

---

### Post by zekopeko on 2009-10-17
> **soham_1207 said:**
> Sounds cool. But i am talking about a single place to check out all new and beta softwares by independent developers.

Well the system as planned will allow app developers to have a simple button on the webpage that will add the ppa and install the app.

---

