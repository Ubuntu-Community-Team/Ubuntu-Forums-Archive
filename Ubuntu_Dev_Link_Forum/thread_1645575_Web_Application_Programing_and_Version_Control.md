---
title: "Web Application Programing and Version Control"
date: 2010-12-14
forum: Ubuntu Dev Link Forum
---

### Post by sniper7kills on 2010-12-14
Hello All!

I've been working on a few web applications (all in php) and have decided that I want to get a bit more organized. Currently I'm just uploading and downloading files via FTP and editing them with gedit. I (try to) keep track of all the bugs by memory, and I've been keeping future additions in mind as well, but I'm thinking that its time for a better system.

I'll soon be getting a dedicated server that I'll be setting up to host VM. My plan is to have one VM running Cpanel which will be used to view the application online. And a second VM to hold the project management software (redmine?), and repository (subversion?).

Does anyone know of an easy way to pull this off? Idealy what I'm looking to do is be able to just download the file I need to edit, edit it, and save it automatically uploading it via FTP and committing the change to subversion. Preferably I'd like to not keep a local copy of the applications or SVN on my computer due to the fact I'll be in a Navy Tech school and don't want to risk loosing the data if my computer is lost/stolen/broken.

I'd also like to avoid using any bloated IDE, I mean I've been using gedit just fine after switching to ubuntu from windows XP and dreamweaver.

Hopefully this all makes sense, and someone could give me a bit of insight to what they do for a situation along the lines of mine.

---

### Post by Vorian on 2010-12-30
I would suggest opening your project on launchpad.  Launchpad uses bazaar vcs for raw code, and a ppa for anything you wanted to package up.  For your remote server, just get your keys to launchpad.  You can handle everything via ssh.

Just my $.02

---

