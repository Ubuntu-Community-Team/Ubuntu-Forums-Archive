---
title: "Need help starting."
date: 2016-04-29
forum: Server Platforms
---

### Post by Spud37 on 2016-04-29
I want to set up my laptop to run as a server/NAS would this be easier done by installing ubuntu server or regular desktop ubuntu. I would like to be able to still run a few programs on it. 


<OLD POST; Edited to better phrase>
Okay so first let me say my goal is to use a laptop that has some hard drives connected via USB as a NAS as well as a media server if possible. I am really wondering would it be better to just use ubuntu server, or go with desktop and install something to allow me to make a NAS? I am hoping to still using the laptop to just run small things if needed but mostly act as a NAS that other ubuntu, and windows machines can access. Bonus if it could with mac, and somehow get Google Drive to work with it. Is there any way to get google drive to sync? Really if anyone has a notion or an idea of what I want and knows more about this area if you give me a nudge with some links that would be amazing. Yes I did google and search ubuntuforums but i found so many threads and so many different opinions and most are not for the latest ubuntu but past releases.

Thanks.

---

### Post by DuckHook on 2016-04-29
My first and overriding piece of advice would be to break your questions down into separate bite-sized pieces and post them in their respective forums. Your paragraph of disparate questions above will generate too much noise and might just confuse you further.

I suggest editing your post and starting with just the laptop-as-server question first. You will have plenty of opportunity to start further threads on the rest. We're a patient and helpful community. ;)

---

### Post by Spud37 on 2016-04-29
I am not sure about what the correct forums where for some, such  as NAS, if that was networking or if that was media. Since I would like to also use it as a media server with ps3. 

Also hard to break it up into smaller questions because to me, they are all one big question

Thanks.

---

### Post by Bucky Ball on 2016-04-29
*Thread moved to **Server Platforms**.*

[QUOTE=Spud37]I want to set up my laptop to run as a server/NAS ...[/QUOTE]

Server/NAS (network-attached storage) goes here.

---

### Post by DuckHook on 2016-04-29
I remember things looking that way to me when I first started too.

My suggestion was made only to help you generate better replies. The forum help areas tend to attract experts who focus on their expertise. Example: network gurus don't visit *General Help* as often as they do *Networking & Wireless*.

**EDIT**

Ninja'd by Bucky Ball.

Hopefully, you can find your answers here.

---

### Post by mastablasta on 2016-04-29
Laptop as server is not the best idea out there, but i guess you have limited resources like me.

> **Spud37 said:**
> I would like to be able to still run a few programs on it. 
what kind of programs?
> 
<OLD POST; Edited to better phrase>
Okay so first let me say my goal is to use a laptop that has some hard drives connected via USB as a NAS as well as a media server if possible. I am really wondering would it be better to just use ubuntu server, or go with desktop and install something to allow me to make a NAS? I am hoping to still using the laptop to just run small things if needed but mostly act as a NAS that other ubuntu, and windows machines can access. Bonus if it could with mac, and somehow get Google Drive to work with it. Is there any way to get google drive to sync? Really if anyone has a notion or an idea of what I want and knows more about this area if you give me a nudge with some links that would be amazing. Yes I did google and search ubuntuforums but i found so many threads and so many different opinions and most are not for the latest ubuntu but past releases.


will it be only LAN server or accessed from outside of LAN?

have a look at Openmediavault - it is super easy to install and once you are up and have web access to it it is easy to add various plugins. it is based on Debian stable. Debian has good documentation if you need it and Openmediavault also has good community support.

If you plan to install desktop, then install a lighter one. Generally servers do not have deskotp as they are another attack vector. Plus, imagine someone needing access to server and everything going slow for them while you are doing "something" on it. but if you plan to have it only in LAN i guess this shouldn't be an issue. Just use something like Lubuntu so it doesn't consume the resoruces unnecessarilly. if you need a web interface to the server have a look at Ajenti. very light and plenty of options.

are you planning to install Plex server or will this be just a file server?

You mentioned Google drive. I believe there are some things one can do to connect to google drive:
[http://dothisbest.com/how-to/install-google-drive-grive2-on-ubuntu/](http://dothisbest.com/how-to/install-google-drive-grive2-on-ubuntu/)
[http://www.howtogeek.com/196635/an-official-google-drive-for-linux-is-here-sort-of-maybe-this-is-all-well-ever-get/?PageSpeed=noscript](http://www.howtogeek.com/196635/an-official-google-drive-for-linux-is-here-sort-of-maybe-this-is-all-well-ever-get/?PageSpeed=noscript)

but why not make a step forward and install your own cloud since you plan to have a server setup and running anyway?: [https://owncloud.org/](https://owncloud.org/)

explore the options, make a plan of what you want and how it will be setup, and then ask your questions (preferably not in a wall of text). :D

---

