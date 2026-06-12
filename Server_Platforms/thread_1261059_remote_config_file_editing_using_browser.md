---
title: "remote config file editing using browser"
date: 2009-09-08
forum: Server Platforms
---

### Post by gduncan on 2009-09-08
Hi, i'm a long time Ubuntu user, first time poster.

My company produces a certain backup solution that unfortunately only works on some other os....
I am in the interest of remedying that.
All of the programs' configuration is done via ini files. 
What I would like to show my boss right now is something running in a web server that allows remote users to edit said ini files, preferably using html forms.
This way if I cant persuade my boss to shell some cash on programmers to do the porting, I can at least configure the damn thing remotely from my Ubuntu workstation.

I have some modest programming skill so I gave django a go. 
I thought it would fit the bill perfectly, but as it seems it takes too much time for me to learn how to use it competently(mind you this whole thing is a side project).

Is there  any ready made solution for my problem? (preferably a php script that I can just stick into apache :popcorn:)
If not, can someone point me in the right direction?

---

### Post by HermanAB on 2009-09-08
Webmin

---

### Post by gduncan on 2009-09-09
Not exactly what I was looking for.
Webmin is way to big for what I'm doing and doest work as well on Windows as on Linux.

Any other suggestions?

---

### Post by sam-moss on 2009-11-25
GDuncan I've been using Webmin on Linux and it works fine for me. Maybe give it another go.
 
Sam
 
The [fat burning furnace]("http://weightwoo.com/fat-burning-furnace") is actually very good.

---

### Post by spikyjt on 2009-11-25
If I understand the OP correctly, they wish administer a windoze server from a linux client, not administer a linux server, so webmin is not a solution.

There are a number of solutions for this, but a web interface will require significant security considerations. I would respectfully suggest that if you do not have time to learn the software you tried already, you do not have time to do this properly over the web.

You could use rdesktop to log into the win box from your linux box (via TSClient or KRDC). Or you could share the config folder via smb and connect with a suitable samba client on linux. Again there are security concerns.

If you really want a web interface, it will need to be running on a web server on the windoze box. I would suggest this is not the best place for advice on that ;)

---

