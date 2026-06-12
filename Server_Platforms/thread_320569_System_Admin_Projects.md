---
title: "System Admin Projects"
date: 2006-12-17
forum: Server Platforms
---

### Post by SuperMike on 2006-12-17
Is there a system administration project being worked on for Ubuntu?

[LIST]
[*]Typing all these command-line params for adding new LDAP users -- that's for the birds. We need some other way.
[*]If they make it web-based, that's great and I'd like to see that too, but not every network permits web interaction to their servers, especially if they're being used for web stuff and are used for application or database tier stuff.
[*]Mom and pop shops that install Ubuntu Server could stand to have the web interface version to make their lives easier, especially if they are slightly technically challenged and are being coached over the phone for some basic system admin tasks.
[/LIST]

---

### Post by ola on 2006-12-17
Hi, have you tried Webmin ([http://www.webmin.com/](http://www.webmin.com/)) for the web based configuration?

I have not used it myself but it's supposed to be quite good.

It might not be quite what you are after, but it might be worth looking at!

Best regards,

Ola

---

### Post by maxamillion on 2006-12-17
[www.ebox-platform.com](www.ebox-platform.com)

you need a debian stable branch installation to use it, but ubuntu is debian so it shouldn't be all too hard. I don't recommend using their installation cd, it seems to fail but installation of their packages from the repos listed on the installation page on an already running debian install seems to work wonders

---

### Post by SuperMike on 2006-12-19
Yeah, I tested with eBox. I see it as having a lot of potential. I noticed awhile back that it needed some improvement in the user admin area. It's unfortunate they chose Python as their development platform. I would have loved to help them but my language of choice is PHP and I only pretend to know Python here or there sometimes.

Maybe I'll just write my own system admin web interface, and eventually, a console admin interface. I mean, I plan to bundle my custom FOSS software in a plug-and-play rackmount PC, and I guess it would help to have an interface for managing other aspects about the host OS for that.

I wasn't impressed with WebMin until I saw the Tiger interface for it. Then it was cool. I need to spend some time to give this a really good evaluation.

---

### Post by elst on 2006-12-19
The Ubuntu Directory Services project is aimed at improving management:

[https://launchpad.net/people/ubuntu-directory](https://launchpad.net/people/ubuntu-directory)

Most of the discussion was about authentication, but LDAP directory are also an essential data store for sharing configuration data, so having one is a prerequisite for doing system administration properly. Most networks today have multiple systems, and virtualization means even more OS instances, so a tool that simply edits the config files on a single system is likely to be a dead-end, development-wise, although it would be useful now.

I would stick my neck out slightly, and say that Python is really useful here. It's a standard part of several distributions, and allows for both desktop and Web interfaces to the same underlying functions/libraries. Implementing the functionality in PHP essentially forces you to install extra software (including a Web server). PHP is also acquiring a bad reputation for security and maintainability which is not undeserved, so a PHP app that modifies system settings would probably not be welcome on many networks. 

FWIW, I've just started learning Python and found that it's a very nice language. The Django and TurboGears frameworks mean that it also has Rails-like facilities available for Web applications.

UPDATE: Having looked at the docs, eBox uses Perl, with Apache to serve the Web interface portion. The datastore for configurations is a GConf database.

---

### Post by SuperMike on 2006-12-20
I had an idea for how a web interface could be built. The idea is just to build the shell of the web interface and make it a snap for PHP developers to add on.

* It has 3 levels. These are Category, Element, and Function. For instance:
Category: Users & Groups  (a category is a grouping of functionality)
Element: LDAP (an element is a grouping of technology)
Function: Add User (a function is a function for using the technology in the category)

* To access these levels, you have a 2 paned interface. On the left you have the Category menu items. When you click one, it refreshes the right pane with icons, a title, and a brief discussion of what the element grouping is all about. When you click an Element menu item in the right pane, it refreshes the right pane to show a list of Function menu items such as Add User, Remove User, etc. You click these Function menu items and the right pane refreshes to show a form for completing the functionality you want.

* The category hierarchy is created dynamically by the folder structure for where the website is hosted. There's a folder called Categories. Inside, it has subfolders for each category. Inside those it has folders for Elements. Inside those it has folders for Functions. These folders are dynamically read and redisplayed in the browser interface. This permits one to simply drop their new Category, Element, or Function folder into the folders and the application immediately recognizes them on a page refresh.

* A simple Page class could be created so that all items drawn on the page can be achieved easily from Page object methods. This allows one to build forms rapidly and keep with the consistent look and feel of the main CSS for the application.

* I don't anticipate a local database being necessary, but if I needed one, then SQLite looks like a good candidate for something so small, and its license is nice.

Well, must run, but if I had the time, I would be building this and sticking it on Ubuntu Projects on their Launchpad for others to collaborate on. Right now I'm working on a CRM built with PHP.

---

### Post by elst on 2006-12-20
It may help to think in terms of "Tasks" rather than "Categories" (I know that the distinction may seem a bit small on the page).

The data store is a big deal here because ideally you need to have something that stores what the settings should be, and then functions that apply those settings to live systems. This model allows you to perform rollbacks in case of error, as well as making it easy to have functions that back up the config, or apply copies of the configuration (for cloning systems). IMO, directly editing config files is slightly dangerous because you can end up with the live copy of the file being damaged/invalid, and then the system stops working...

---

### Post by SuperMike on 2006-12-20
> **elst said:**
> It may help to think in terms of "Tasks" rather than "Categories" (I know that the distinction may seem a bit small on the page).

The data store is a big deal here because ideally you need to have something that stores what the settings should be, and then functions that apply those settings to live systems. This model allows you to perform rollbacks in case of error, as well as making it easy to have functions that back up the config, or apply copies of the configuration (for cloning systems). IMO, directly editing config files is slightly dangerous because you can end up with the live copy of the file being damaged/invalid, and then the system stops working...

All good points. Thanks.

---

### Post by peanut butter on 2006-12-20
has anyone tried ebox on ubuntu? it works great in vmware from their install cd?

---

### Post by SuperMike on 2006-12-21
> **peanut butter said:**
> has anyone tried ebox on ubuntu? it works great in vmware from their install cd?

Yeah, I tried eBox. I filed a change request because I found it wanted to list all the users at once on a page on one particular screen I can no longer remember. I posed the question, "What happens when it's thousands of users and we need to add five more? Do we wait through all that to refresh for each new user?" The developers thought I had a good point and may have fixed that by now, I don't know.

I also knew it was Python based and was more complex under the hood that I had anticipated. That's too bad because I think the whole project could take off if it were easier under the hood. I mean, others could build more modules for it than it already has.

That's why I like the PHP idea. It's got a tremendously huge base. You could build a framework where it's a set of directories with certain page names inside. New modules could be added by creating a new module folder and pasting it in the directory. The web app could dynamically see it and automatically add the proper menu items. Then, if you made the pages easy to compose with a simple but effective object model, you could draw forms in an orderly, consistent, easy way.

---

### Post by dexem on 2006-12-21
> **SuperMike said:**
> Yeah, I tried eBox.

That's great :) You even made a great review on osnews, I think :)

> **SuperMike said:**
> I also knew it was Python based and was more complex under the hood that I had anticipated. That's too bad because I think the whole project could take off if it were easier under the hood. I mean, others could build more modules for it than it already has.

Well, in fact, eBox is written in Perl. This could seem scary at first sight, but it has user and developer documentation and an IRC channel to ask everything to the developers. I think it's no so hard to make an eBox module (I made some video tutorials which are unfinished)...

Anyway, I can't be truly objective because I work for the developer company of eBox, Warp Networks :P

Greetings :)
Dani

---

