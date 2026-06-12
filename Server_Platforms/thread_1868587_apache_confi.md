---
title: "apache confi"
date: 2011-10-24
forum: Server Platforms
---

### Post by sinista on 2011-10-24
Hi Peeps!

I need some help with my vps, i have apachce, php etc installed which works fine and i have some vhosts which route to the correct folders when I enter the correct URL,

however when i eneter the actual IP  address (33.22.324 etc..) of the server im directed to first folder it meets i.e. a.com or b.com (its alphabetical)

instead of this i want it to go to an index or error page of my creation.  

so my question is how do i do this or even, what file do i need to edit to do this.

Many Thanks.

---

### Post by volkswagner on 2011-10-24
Since you have noticed the importance of alphaNaming, make your vhost file come first.
Create a vhost file with name like 00000aaasite and point it to your index.  This way any other sites you create will come after this "default".

You can name your vhost file anything you want.  It is just important when using a2ensite to have the correct file name.

---

### Post by sinista on 2011-10-24
thanks dude,

this was my initial thought though it almost seemed a bit hacky, but if thats the way its done fair play.


can anyone recomend a good mail server type thingy that i can install.

:)

---

### Post by volkswagner on 2011-10-24
[Citadel]("http://www.citadel.org") is dead easy with a lot of features.  It does prefer to have it's own server but you can easily setup reverse proxy so it can live along side your web server (Apache2)

Or you can roll your own:

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

