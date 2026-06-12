---
title: "Server directory syncronisation with offline mode?"
date: 2006-03-13
forum: Server Platforms
---

### Post by puddpunk on 2006-03-13
Hey guys!

I have a rather unique problem. I have a server in my house and everybody in my family has a desktop and a laptop. Some computers run Linux, the rest run windows XP pro.

Everybody has a samba share on the server with their personal documents in it - theres also a shared directory but I'm not concerned about that.

Now this works great for the permanently network-enabled desktops they just mount  the server share to their filesystem either by network drives (Windows) or smbfs (Linux). The problem is that the laptops are not permanently connected to the network. I take mine to work and uni and would like to have access and be able to modify my files from there. Also when I come home I would like it to syncronise any changes to the server or vice versa. While the laptop is connected to the network I would like it to work in "Live mode" i.e. instantly show any changes to my share without having to "re-sync".

I had a brief look at iFolder and it looks very interesting but I don't feel it intergrates into gnome well enough (like vfs). Where possible I would like to avoid gnome-vfs as a few apps I want to use don't support it.

My first thought was to have two folders in my home folder. Share-live and Share-offline. When I login/out I would have a script that would check if share-live is mounted and use rsync or unison to syncronise the files between them. Functional and flexable but slow and a bit of a hack :)

So basically I want to be able to sync a remote directory automatically (i.e. without having to run a script or anything) to a local directory preferably without polling and I need offline access to it. I really don't want to recompile any kernels but if it's a good solution I probably would.

Anybody have any ideas, comments or suggestions?

---

### Post by lewmnik on 2006-04-14
[QUOTE=puddpunk]

I had a brief look at iFolder and it looks very interesting but I don't feel it intergrates into gnome well enough (like vfs). Where possible I would like to avoid gnome-vfs as a few apps I want to use don't support it.

Anybody have any ideas, comments or suggestions?[/QUOTE]

Well did you really read the iFolder page through? Chick it out and you'll will bi amazed, it really is the thing you want 

[http://www.ifolder.com/files/7/7e/NLD-fullscreen.jpg](http://www.ifolder.com/files/7/7e/NLD-fullscreen.jpg) 

:p

---

