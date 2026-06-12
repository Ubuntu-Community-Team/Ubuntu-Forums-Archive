---
title: "Web Development Server with GUI?"
date: 2007-01-15
forum: Server Platforms
---

### Post by complexprocess on 2007-01-15
Hi folks,
I'm a web developer and am interested in setting up a LAMP development server to keep my source on, because I work from multiple locations.  I've done some linux work before and am pretty familiar with the command line, but I like to have a GUI as an option, in case I want to log on to the server directly and then browse the web for help with configuration.  I'll probably use Firefox, a non-command-line text editor, and a graphical file manager.

My question for you is whether it would make more sense for me to install the desktop version of Ubuntu/Xubuntu and then set up my LAMP environment manually, or if it might be just as easy to install the server version and then install a graphical environment like Xfce and a couple other packages.  I'd prefer to go with the server version and then just add what I need, but if it will be overly complicated for someone with limited experience to do so I'll go with the other option.

Do you see any pitfalls in my future, or do you have any tips that will make the setup easier?

Thanks!
Scott

---

### Post by NumberOne on 2007-01-15
I installed the lamp server then installed my desktop.  It was easy.

After installing the server issue this:

sudo apt-get install ubuntu-desktop

or

sudo apt-get install kubuntu-desktop

or 

sudo apt-get install xfce-desktop

depending on what desktop enviornment you want to use.

Obviously you will need an internet connection and the cd that you used to inst
all the server version.

HTH

---

### Post by complexprocess on 2007-01-15
Well that doesn't seem hard at all.  Thanks.  :)

---

### Post by david_lamp on 2008-01-27
Hi Scott,

I was  just  abourt to  ask  exactly the  same  question.

It  does seem strange that you  have to  choose between the 2. 
I  can see  the  benefit  of  having no GUI  on a  live server, but there must be zillions of people  out there looking to develop LAMP applications before uploading them to live servers.

Were you able to set tings up as required , and was it as straight  forward as suggested ?

Regards
David

---

