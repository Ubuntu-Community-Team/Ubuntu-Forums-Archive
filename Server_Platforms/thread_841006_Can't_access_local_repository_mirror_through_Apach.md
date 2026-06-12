---
title: "Can't access local repository mirror through Apache"
date: 2008-06-26
forum: Server Platforms
---

### Post by nbotticelli on 2008-06-26
Hello,

I am trying to create a local network repository mirror for Ubuntu.

I have all repositories downloaded already along with apache2 being installed.

Right now I am just trying to get a fresh ubuntu install to get all the updates etc off of the repository mirror but it keeps coming up and saying that it can't get the files...


The mirror is ubuntu server 8.04 and so is the fresh install. For now I set both machines with static IP's running just through a switch and they can ping each other, 

I can even go on the fresh install machine and using firefox go to the ip of the server machine and it brings me to the default "It Works" index.html file of apache....But when I manually type in the web address to where the repositorties should be located it comes up with 404 error access denied stuff...

How do I open up access? Apparently it's a permissions issue but I've never done this before and don't know how to open it up.

Any help is greatly appreciated!

-Nicco

---

### Post by nbotticelli on 2008-06-26
Ok, I was able to get some repositories to work from the client machine but it still comes up saying that it can't access many of them....I'll have to look at everything again later on actually post what some more of the settings are.

I think where I am becoming confused is when I have to set up the link between the apt-mirror files and the apache/www folder for outside access.

---

