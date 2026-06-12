---
title: "Want to make a webhost"
date: 2009-06-26
forum: Server Platforms
---

### Post by Therax on 2009-06-26
[SIZE=2][B]Hi

I am new at this and dont really know how to do this, i have searched but cant find any
sutible help. Maybe a havent lookt at the right place yet but anyway.

I need to make a webserver to host a public website,forum and so on.
I want to make it as a webhosting service becuse i want my users to have
the ability to have a small webhost if they want.
I need a howto or a tutorial on how to do this and if possibly with a gui in the server for me to use,
 i plan on getting a server computer as soon as we can afford one or make one if necesery.
Any help on hoe to do this would be apriciated. 

Thanks in advanced[/B][/SIZE]

---

### Post by wojox on 2009-06-26
Look here

[http://samiux.wordpress.com/2009/06/13/howto-almost-a-perfect-and-secure-ubuntu-9-04-lamp-server/](http://samiux.wordpress.com/2009/06/13/howto-almost-a-perfect-and-secure-ubuntu-9-04-lamp-server/)

---

### Post by R.Bucky on 2009-06-26
do you intend to host other people's domains? or, do you simply want a web server or your own use?

---

### Post by philcamlin on 2009-06-26
install apache

---

### Post by R.Bucky on 2009-06-26
simple enough. There a many tutorials out on the net. [Here is one]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") 
In short, you could use terminal and type in ```
sudo apt-get install apache2
``` That would install the base packages. Your files are located by default in /var/www. Go to [http://localhost](http://localhost) and you will see "It works!"

---

### Post by Therax on 2009-06-26
okay will look.

Yes i intend to host other domains wich is why i wanted to make it like a webhost.

---

### Post by R.Bucky on 2009-06-26
take a look at this
[http://ubuntuforums.org/archive/index.php/t-152207.html]("http://ubuntuforums.org/archive/index.php/t-152207.html")

---

### Post by Therax on 2009-06-26
okay thanks again i think i understand how i have to do it know.
Thanks

---

### Post by Vegan on 2009-06-26
you are far better off installing the full LAMP stack

```
sudo tasksel lamp
```

---

### Post by windependence on 2009-06-27
> **Therax said:**
> okay will look.

Yes i intend to host other domains wich is why i wanted to make it like a webhost.

No offense, but if you are going go host other people's sites, you should have some experience with it first, don't you think?

-Tim

---

### Post by Therax on 2009-06-27
> **windependence said:**
> No offense, but if you are going go host other people's sites, you should have some experience with it first, don't you think?

-Tim


Yeah thats why i am asking so i can get experience. And i learn as i go which is why i want help
and i will firstly run it for me and se if it works. And secondly its going to be basic becuse most of the
time they wont be needing anything else.

---

