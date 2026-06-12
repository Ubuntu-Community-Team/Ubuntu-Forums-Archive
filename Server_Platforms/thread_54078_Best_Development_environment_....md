---
title: "Best Development environment ... ?"
date: 2005-08-03
forum: Server Platforms
---

### Post by Elijah on 2005-08-03
I was tasked to create a development environment for a team of 4 web developers, we all had pc's & a central server. They're not networked yet, but soon will be ... Also the number of developers & pc's could rise. Some pc's could use windows in the future so we might use samba ... 

I thought of using CVS and have it installed & configured for the central server as the source repository but I was wondering if that was the best solution ... ? I had NFS installed and setup ... I dunno what else could work. 

Should thin-clients work? I could remove the hd's from the desktops & setup the server for it ... it'll be easier to administer the whole network ... 

Erm, what else I haven't talked about? other options?

---

### Post by John Nilsson on 2005-08-03
I would consider using Subversion instead of CVS. As it is designed to superseed it. TortoiseSVN is a great explorer extension for windows machines. If the dev's are goind to work on laptops without connectivity to the server I would consider a distributed system instead though.

Have a look at [this](http://zooko.com/revision_control_quick_ref.html)  for alternatives.

Try to keep everything related to development in the repository so that setting up a new dev-machine is a simple matter of checkout.

For a cross platform IDE you should try Eclipse (there are plugins for subversion). I use eithe Eclipse or GVim for my development, depending on mood ;-)

---

### Post by Elijah on 2005-08-03
[QUOTE=John Nilsson]I would consider using Subversion instead of CVS. As it is designed to superseed it. TortoiseSVN is a great explorer extension for windows machines. If the dev's are goind to work on laptops without connectivity to the server I would consider a distributed system instead though.

Have a look at [this](http://zooko.com/revision_control_quick_ref.html)  for alternatives.

Try to keep everything related to development in the repository so that setting up a new dev-machine is a simple matter of checkout.

For a cross platform IDE you should try Eclipse (there are plugins for subversion). I use eithe Eclipse or GVim for my development, depending on mood ;-)[/QUOTE]
 Thanks =) I didn't know about that subversion in linux, I've only tried the TortoiseSVN. 

I'll check out eclipse too.

---

### Post by adeh on 2005-08-03
We use CVS on a central server (now chugging along beautifully thanks to this forum) to host the code. Using CVS or SVN is a must. Simply using NFS or Samba to "share" the codebase will only result in tears one day when the new guy nukes the codebase. 

On the dev machine, we use Eclipse, which behaves exactly the same on Win and Lin, and has plugins for SVN and CVS. Also, you can develop J2EE, JSP, PH P... depending on what you guys are using, Eclipse most likely has a plugin. I'm not sure but ubuntu should have apt-gettable eclipse which makes set-up a breeze.

I would not recommend thin clients. Each developer should have his own server running locally on his desktop/laptop, with access to his own DB schema, so that he can develop and test without messing with anyone else. Then, he commits his code on the server and the others can update to get the new code. When it comes time to deploy, you can then treat the server just like a development machine, checkout and go.

If you have not decided on a development framework yet, you might want to look into Ruby on Rails (although you can't use Eclipse for that)
Good luck.

---

### Post by Elijah on 2005-08-06
[QUOTE=adeh]We use CVS on a central server (now chugging along beautifully thanks to this forum) to host the code. Using CVS or SVN is a must. Simply using NFS or Samba to "share" the codebase will only result in tears one day when the new guy nukes the codebase. 

On the dev machine, we use Eclipse, which behaves exactly the same on Win and Lin, and has plugins for SVN and CVS. Also, you can develop J2EE, JSP, PH P... depending on what you guys are using, Eclipse most likely has a plugin. I'm not sure but ubuntu should have apt-gettable eclipse which makes set-up a breeze.

I would not recommend thin clients. Each developer should have his own server running locally on his desktop/laptop, with access to his own DB schema, so that he can develop and test without messing with anyone else. Then, he commits his code on the server and the others can update to get the new code. When it comes time to deploy, you can then treat the server just like a development machine, checkout and go.

If you have not decided on a development framework yet, you might want to look into Ruby on Rails (although you can't use Eclipse for that)
Good luck.[/QUOTE]
 Thanks for the advice, I'll cancel the thin client idea and go on with SVN and Eclipse :-) 

I dunno about Ruby, never tried the language ...

---

### Post by jwenting on 2005-08-09
[QUOTE=Elijah]Thanks for the advice, I'll cancel the thin client idea and go on with SVN and Eclipse :-) 

I dunno about Ruby, never tried the language ...[/QUOTE]
 when evaluating svn I encountered quite a bit of problems with tool support.
svn is still too much in a state of flux to be considered stable (for example, if your client supports svn 1.1 most likely it won't be able to talk to a 1.2 server).
That's why I decided to go with cvs for the projects I'm setting up. 

It certainly looks promising, but not yet quite stable enough for me.

---

### Post by fekimoki on 2005-08-11
[QUOTE=Elijah]I was tasked to create a development environment for a team of 4 web developers, we all had pc's & a central server. They're not networked yet, but soon will be ... Also the number of developers & pc's could rise. Some pc's could use windows in the future so we might use samba ... 

I thought of using CVS and have it installed & configured for the central server as the source repository but I was wondering if that was the best solution ... ? I had NFS installed and setup ... I dunno what else could work. 

Should thin-clients work? I could remove the hd's from the desktops & setup the server for it ... it'll be easier to administer the whole network ... 

Erm, what else I haven't talked about? other options?[/QUOTE]
 hi, im really interested using cvs and stuff, but i dont know where to begin and i really dont know whats that all about. is there any url link about this?
i have a PHP programmer team (2-3 persons) and really having trouble synchronizing codes.. do we need to use cvs ?

---

### Post by John Nilsson on 2005-08-26
[QUOTE=fekimoki]hi, im really interested using cvs and stuff, but i dont know where to begin and i really dont know whats that all about. is there any url link about this?
i have a PHP programmer team (2-3 persons) and really having trouble synchronizing codes.. do we need to use cvs ?[/QUOTE]
 Just read [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

---

