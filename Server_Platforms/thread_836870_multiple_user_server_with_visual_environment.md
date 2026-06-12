---
title: "multiple user server with visual environment"
date: 2008-06-21
forum: Server Platforms
---

### Post by oodlesOfmoodles on 2008-06-21
I'm not sure if a server is what I am looking for but is it possible to have an Ubuntu box that has I can make user accounts for and then people login into it in a visual environment(X11) and then use applications?

Something like multiple users SSHing into a server but with a login screen and regular Ubuntu apps.

The reason it has to be visual/application oriented is because I want to set up something like this in my school and 99% of the student body isn't computer proficient enough to use the (Linux) command line.

Thanks guys!

---

### Post by werries on 2008-06-21
wouldn't it be easier to have ubuntu installed on the PC, and then have their home folders all on the server?

---

### Post by zeronothing on 2008-06-22
you should check out "nomachine". go to their website [[COLOR="Blue"]here[/COLOR]]("http://www.nomachine.com/"), and you can download the software to create your environment. The software comes in .deb for a double click install. make sure you have openssh server install because its a prerequiste for the software. then all you have to do is create accounts on that machine using the "users and Groups" function under system -> administration. then the users you want to connect to that machine would need to download the free client program from the website to connect to the server you want to setup. they make the client program for windows, linux, and mac. check it out, I use it for remote purposes.

---

### Post by oodlesOfmoodles on 2008-06-22
wow cool!

thanks man.

---

### Post by zeronothing on 2008-06-22
the application is really cool, if you need help setting it up or configuring it, give me a shout. you probably won't but if you do message me here on the forums.

---

### Post by oodlesOfmoodles on 2008-06-22
thanks!
Im gonna give this a try in the next few days (after i get back from this vacation).

---

