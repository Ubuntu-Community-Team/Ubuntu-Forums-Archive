---
title: "nvu and web page publishing"
date: 2006-10-22
forum: Server Platforms
---

### Post by bubbleblabs on 2006-10-22
I have set up my pc as an ubuntu lamp server, i have also installed nvu and created a web page to access records from my database.  In nvu it only lets me publish a webpage to the internet, i dont want to buy a domain name, i just want to send my page to my localhost on my pc.  Is there anyway i can do this with nvu, and if not does anyone no how to do this as my web page skills are very basic......????? Please help???

---

### Post by meng on 2006-10-22
You can *save* the webpage wherever you like within your filesystem.

---

### Post by bubbleblabs on 2006-10-22
> **meng said:**
> You can *save* the webpage wherever you like within your filesystem.

I have done this already but i dont know how to access it from my web browser, I was previously able to access it from my browser by going to [http://local](http://local) host, but when i did that i wasnt able to go to my phpadmin page to use my database, i am very new to all this so any help is appreciated,

---

### Post by meng on 2006-10-22
Here are some tips on getting help:
1) Describe your problem in detail, and give an accurate title: your problem is not with nvu, but with how you are accessing the page through localhost.
2) Don't double post: pick the most appropriate subforum and be patient.
EDIT: oh and howdy to a fellow Brisbanite (I'm working overseas right now though, have been since mid-2004)

---

### Post by bubbleblabs on 2006-10-22
Thanks,for your tips,:D

---

### Post by testcees on 2006-10-22
> **meng said:**
> You can *save* the webpage wherever you like within your filesystem.
Default the lamp server looks for webpages in /var/www/.

---

### Post by airtonix on 2006-10-25
Dont bother with nvu, its a piece of &^%&...

I cant stress how important it is that you get familar with editing the source code instead of using pretty wysiyg.....because they are very rarely wsyiwyg......and more often than not they implement bloated code into your pages whilst rewriting your efficient code backinto bloated code.

Im pretty sure this is something that wysiwygs are fundamentally afflicted with....

I recommend experimenting with these editors in the following order : 

**gedit**
has an awesome snippet system and will soon support remote filesystems, has code colouring,  block indenting, tabbed documents, css, php, cod reference

**bluefish**
pretty damn cool, same as gedit but it supports remote filesystems, and saves the editing session into project files. And although it is not as cool as gedit in my opinion it has this sytem of closing the opending tag you write......wierd as i bashed gedit in my early days in defence of leafpad and bluefish, but now its the other way round....

[B]quantsPlus
[/B]A kde based app, which means if you install it....a whole bunch of kde libraries will be installed along with it....not really an issue for me now since this aspect is cleaner than it was before, and this is proly the only editor that has wysiwyg support that i would (cringe) recommend.

**Leafpad**
this one is like notepad on windoze, cept it also has line numbering. just lightweight editor...opens up fast.

---

