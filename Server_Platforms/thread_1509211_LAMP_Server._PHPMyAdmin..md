---
title: "LAMP Server. PHPMyAdmin."
date: 2010-06-14
forum: Server Platforms
---

### Post by Roasted on 2010-06-14
This is the first time I'm tinkering with a LAMP server. Basically I asked my buddy what he recommended, which was a LAMP server. I personally just want a way to allow users (friends in particular) to log into my computer from a web based gui and "download" any files I have hosted. The idea came up after we went camping this weekend. 1 camera, tons of pictures, and yet we're all scattered due to where we live, so getting copies of the pictures on CD is kind of a PITA. It'd be nice if I can zip the pictures up and host them for download.

Can LAMP do this? I found a guide online that said it can be done with PHPMyAdmin. The problem is, I have no idea what I'm doing from here on out. Can anybody offer any suggestions?

---

### Post by dapperdanny77 on 2010-06-14
hi,

basically LAMP is the foundation for web based applications - it's not an application itself.

there are myriads of apps which you can install on to of a LAMP installation (forum, wikis, cms, ...) - so this really depends on your needs. 
PHPMyAdmin is a tool to manage MySQL which is a Database. It's not the best idea to store your pictures inside a database.

if you just want to exchange pictures a simple ftp server is sufficient (like proftpd) or you can use apache to serve the files via http

cheers

---

### Post by Roasted on 2010-06-14
> **dapperdanny77 said:**
> hi,

basically LAMP is the foundation for web based applications - it's not an application itself.

there are myriads of apps which you can install on to of a LAMP installation (forum, wikis, cms, ...) - so this really depends on your needs. 
PHPMyAdmin is a tool to manage MySQL which is a Database. It's not the best idea to store your pictures inside a database.

if you just want to exchange pictures a simple ftp server is sufficient (like proftpd) or you can use apache to serve the files via http

cheers

Hmm, okay. This is how it basically went down. I asked a buddy what he recommended to do that, basically to have a web server with items shared out and he suggested apache, which lead to lamp, which lead to phpmyadmin when I did searches on google for what to do.

I do not want to go down the ftp road because every ftp application I use says my router is tainting my connection, despite the forwarded ports. I've upgraded firmware and even had a few IT grad friends remote in to check it out and everybody says everything is set up just fine. Not too sure what that's about, but I'd like to avoid ftp for the previous headaches I experienced.

So if apache is what I need to get this set up, what do you recommend I do exactly? I have apache installed, but uh... I really have no clue what to do from here on out. :P 

Thanks for the response.

---

### Post by dapperdanny77 on 2010-06-14
in ubuntu the apache configs are located in /etc/apache2 dir

the default installation creates some predefined configs.
have a look at this - but it will be hard at the beginning

/etc/apache/sites-enabled/000-default 

is the default vhost configuration of an clean ubuntu apache installation which holds some valuable information which you can use for playing around - but take care that data is accessible from every host/user from outside if you don't have your security measures like Deny,Allow Directives or user authentication

I think it's very important to understand how apache works if you don't want your pictures spread over the internet ;)

---

### Post by Roasted on 2010-06-14
Well my intention was to only host things for limited periods of time to make it easier to send out. For example, several people that were camping with us this weekend live in other states. So when we parted ways, I realized I had the camera with hundreds of pictures and nobody else had anything. I'd just like to set up the pictures on an apache box, host them for a few hours and have the users get back to me when they downloaded the .zip of all of the pictures.

I didn't realize how easy apache was to set up if you were just using a default install. It's just a matter of installing apache2 and whatever you put in /var/www/created-folder is what comes up in the web interface when you hit up your address. One forwarded port later and I'm in business.

So, question - I know basic web design. Is there any way I can create a basic custom template for the default Apache page? It'd be kind of fun to spruce it up a bit. :P

---

### Post by dapperdanny77 on 2010-06-14
just put your html files there - apache will serve this perfectly

---

### Post by kayjaygee_13 on 2010-06-14
Read this guide : [http://woodel.com/](http://woodel.com/)

It covers what you're looking for in detail.

---

### Post by Roasted on 2010-06-14
> **dapperdanny77 said:**
> just put your html files there - apache will serve this perfectly

I did that, but when I do that the index doesn't seem to update. For example, I'll have the layout just like I want it, but if I remove a file in /var/www and hit refresh, it's STILL listed in the index listing even though it's a dead link. Then once I revert back to the default layout, it works fine. Not too sure what is happening here, since all I did was add an image to the background and change the color of the background and font.

Any ideas on how else I can do this? It'd be kind of nice to customize the front page just a little bit, even if I don't use it that often.

---

