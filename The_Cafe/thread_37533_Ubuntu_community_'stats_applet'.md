---
title: "Ubuntu community 'stats applet'"
date: 2005-05-27
forum: The Cafe
---

### Post by trash on 2005-05-27
I think the idea of 'collecting' stats has come up before as a feature for the forum to display the numbers of users/locations/ and what not, but today I thought it would be kind cool to have an applet that sat on the desktop(show/hide) that displayed a worldwide count of people using Ubuntu.. online users anyway.
to display something simple like:

Total
Users onlne = ##
Countries = ##
Languages = ##
Downloads = ##
more??

I guess there might be issues about running the applet/daemon by default to keep the stats acurate but it could give a general up to date count.
Of course i don't have a clue how to write a program so I'm just putting the thought out there.

---

### Post by sapo on 2005-05-27
very good ideia!

I think that it isnt very dificult to do.. we need a server to update the users online and "ping" the machines... and sent the stats do eveyone that is online  ;-) 

I know that there is a lot of programers here that could do it in a few days  :grin:

---

### Post by trash on 2005-05-27
Sweet! I doubt that this would be heavy usage on a server, could it be tied in with something that already exsisted like the new update manager which obviously(maybe) functions similarly?

---

### Post by sapo on 2005-05-27
[QUOTE=trash]Sweet! I doubt that this would be heavy usage on a server, could it be tied in with something that already exsisted like the new update manager which obviously(maybe) functions similarly?[/QUOTE]

its impossible to have a heavy usage with just this kind of statistic...

The only thing that the "app" should do is send a packet to the server saying "i m alive" and the server would count how many people is online....

About the location it could be based on the ip..

The app could send kernel version and some more detailed statistics too... like if the cliente is a x86, ppc or amd64.. if the cliente is using gnome, kde or another window manager...

We just need somebody to make the app and the gui.. i can help with the statistics page using php.. like making graphs and all that stuff  :grin:

---

### Post by weekend warrior on 2005-05-27
[GeoShell](http://www.geoshell.org/index.asp) for windows has a small plugin like  this called [GeoUsers](http://www.geoshell.org/plugins/zoom.asp?id=245). It's worth a look for the idea and layout. GeoShell uses bars loading and unloading plugins like Gnome panels. 

HTH

---

### Post by sapo on 2005-05-27
We can make a dinamic signature to forums too.. a image showing the current status of the ubuntu comunity, and linking to download ubuntu...

something like it:

[img]http://sigx.yuriy.net/images/demooutput.png[/img]

It could be an applet to make a signature and at same time send statistics to a global ubuntu usage  :grin:

---

### Post by totalshredder on 2005-05-27
[QUOTE=sapo]We can make a dinamic signature to forums too.. a image showing the current status of the ubuntu comunity, and linking to download ubuntu...

something like it:

[img]http://sigx.yuriy.net/images/demooutput.png[/img]

It could be an applet to make a signature and at same time send statistics to a global ubuntu usage  :grin:[/QUOTE]
These are good ideas, and it'd be real fun to use them. We just got to find a Grade A coder :-D

---

### Post by trash on 2005-05-27
Wow i like where this is going!

Basic requirements:
transparent background
configurable text/color/size, options on/off for sent stats/forum?
gDesklet like functionality
gnome startup option

I can't wait!!

---

### Post by sapo on 2005-05-28
[QUOTE=trash]Wow i like where this is going!

Basic requirements:
transparent background
configurable text/color/size, options on/off for sent stats/forum?
gDesklet like functionality
gnome startup option

I can't wait!![/QUOTE]

 [-X 

I think this should be fully customizable.. or otherwise nobody will use...

if you make a simple app with a lot of "useless" stuff, its going to slow down in old machines.. so we will NOT have an perfect comunity status... i think that it should be a simple app that show some basic stats and when clicked open a webpage with more accurated status and, graphics and some more options...

It should not use processing or bandwidth.. it just send like from 5 to 5 minutes a "heartbeat" to the server...

like [www.no-ip.com](www.no-ip.com) does... i m using it... and it runs in background and just send a hearthbeat...

---

### Post by trash on 2005-05-28
[QUOTE=sapo][-X 

I think this should be fully customizable.. or otherwise nobody will use...

if you make a simple app with a lot of "useless" stuff, its going to slow down in old machines.. so we will NOT have an perfect comunity status... i think that it should be a simple app that show some basic stats and when clicked open a webpage with more accurated status and, graphics and some more options...

It should not use processing or bandwidth.. it just send like from 5 to 5 minutes a "heartbeat" to the server...

like [www.no-ip.com](www.no-ip.com) does... i m using it... and it runs in background and just send a hearthbeat...[/QUOTE]

fully customizable would be awesome, i was thinking simlicity but what I would like to see/not to see on my desktop hehe... whoever writes it will ultimately decide, then we can hound him/her for more/less features.
Since i'm also running a older PII I'm all for minimalist apps/anything.

---

