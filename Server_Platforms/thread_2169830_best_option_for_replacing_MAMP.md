---
title: "best option for replacing MAMP?"
date: 2013-08-23
forum: Server Platforms
---

### Post by baker-quin on 2013-08-23
Hey,

I've been working on learning HTML through [http://www.w3schools.com/](http://www.w3schools.com/) and some PHP through [http://www.codecademy.com/](http://www.codecademy.com/). I'm just beginning so I really don't know very much at all but my friend does it professionally and he recommended MAMP for being able to load things I might mess around with in .php files. He's obviously a Mac user so I'm wondering which method would be best for a linux operation. I'm running 12.04. I've been looking on google and I've noticed two which I think (with no experience) may do the job well. LAMP seems to be popular but I'm not understanding how it works... 

I found this tutorial [http://community.linuxmint.com/tutorial/view/486](http://community.linuxmint.com/tutorial/view/486) and in this they are installing each element separately... I'm always hesitant to use the terminal because half the time I do it I have no idea what just happened or where it went. I'm quite new to linux but figuring it out slowly. My question here is if I do it this way, then can I save files with the extension .php and they will show up in my browser like .html files do? I'm using google chrome as my web browser and when I save files as .php currently they go on the downloads bar when I open the file it opens gedit and shows the code. 

From what I understand MAMP acts as a local server where you can use PHP, MySQL and APACHE and it'll show what you just did. Anyway, I'll try to learn those later but being able to interact with the php and see what is happening will be a huge benefit to me as I learn more. I've also heard of XAMPP and I havent yet done much research on it yet but thought I'd ask the Linux community what works well as some of this is confusing me when I'm trying to google it out. 

Also, to note, I'm using sublime text 3 beta.

---

### Post by houstonbofh on 2013-08-23
You are asking a little more than you know here...

1) The easiest way to install a LAMP in Ubuntu is to run "tasksel" a command line program.  Go into a shell and tupe "sudo tasksel" and it is fairly easy to understand.  You can install more than just LAMP as well.  Since most Linux servers do not have a GUI, most server tools will be command line or web based...

2) To make a php web page do something it has to be run in a web server with php enabled.  Also, the directory the file is in has to allow exec on files.  This can be donw globally for the entire server, but that can be a security risk.

---

