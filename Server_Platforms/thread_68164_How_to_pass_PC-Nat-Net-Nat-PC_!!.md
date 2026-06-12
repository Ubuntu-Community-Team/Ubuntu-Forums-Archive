---
title: "How to pass PC-Nat-Net-Nat-PC !!"
date: 2005-09-22
forum: Server Platforms
---

### Post by patrick295767 on 2005-09-22
Hi 

I have installed my ubuntu server but unfortunatly i have a NAT server which is blocking all the ports but the 80  
as universities are doing most of time.

pc ---- nat:80 ================== internet ===================== nat:80 ------------ pc 

is there a way to do VNC (tight or not)         or any knind of remote desktop assistance
or any kind or console ???


thx a lot 

nota. i have no access to nat config

---

### Post by patrick295767 on 2005-09-23
[QUOTE=patrick295767]Hi 

I have installed my ubuntu server but unfortunatly i have a NAT server which is blocking all the ports but the 80  
as universities are doing most of time.

pc ---- nat:80 ================== internet ===================== nat:80 ------------ pc 

is there a way to do VNC (tight or not)         or any knind of remote desktop assistance
or any kind or console ???


thx a lot 

nota. i have no access to nat config[/QUOTE]





i managed to do so making a program using a special port but i wish to use the 8080 
or maybe using skype do to tunneling ... 
is it possibel ??

---

### Post by patrick295767 on 2005-09-23
i found this very nice web site ... 
[http://www.realvnc.com/pipermail/vnc-list/2004-May/045139.html](http://www.realvnc.com/pipermail/vnc-list/2004-May/045139.html)


and my question is : 

is it possible to do this in case of two nat ??
for instance with two linux machines ssh server1 / ssh server2 
behind nat

pc2 (10.xxxx)- nat - internet - nat -pc1 (192.xxxx)

Tunneling ???

i really dont konw how to pass this ....

Is there a brillant guy in the world ??

Thank you very much

---

### Post by mlomker on 2005-09-23
> is it possible to do this in case of two nat ??
for instance with two linux machines ssh server1 / ssh server2 
behind nat


No.  SSH is designed to be secure/encrypted and it cannot be done through NAT at all.

Are you saying that you can get to a webserver on your PC if you had one running on it?  You could test that by going to **[www.whatismyip.com](www.whatismyip.com)** from your PC to see what the outside world thinks your address is.  Then you can try going from a machine on ther Internet to that address and getting to something on port 80 on your PC.

I doubt you can get inbound access to your PC at all without help from the network administrator.  Schools generally do not want students running servers and prevent this.

---

### Post by patrick295767 on 2005-09-23
[QUOTE=mlomker]No.  SSH is designed to be secure/encrypted and it cannot be done through NAT at all.

Are you saying that you can get to a webserver on your PC if you had one running on it?  You could test that by going to **[www.whatismyip.com](www.whatismyip.com)** from your PC to see what the outside world thinks your address is.  Then you can try going from a machine on ther Internet to that address and getting to something on port 80 on your PC.

I doubt you can get inbound access to your PC at all without help from the network administrator.  Schools generally do not want students running servers and prevent this.[/QUOTE]


Actually, the trick I used to make a server via ftp and http ... rather crazy was a program via visual basic. Actually, this is a remote control program (tooo slow, cmd, and bug with screen stuffs) via NO SSH  and i have to fix some bugs ... but it works ... 
anyhow, that 's not best solution ... cos no encryption
I havent energy to go on programing this progr

When u look at skype ... skype  has file sending and is connecting to the pc of someone NAT with or wihtout any Nat !!!  2 nats or not ... crazy no ?
I dont know how it works. They, i guess, are using a Third PC to enable the connection (with has no nat)
... i really dont know how it works but can pass nat's ....

I dont wish to use my own  program cos i find it unsecured (only a login and password) is not enough... 

... I dont know ...

I am rather sure that we can make great things in informatic, that 's why i think that nothing is impossible !!
That 's why we, human, can make such great things in the world !!!
Egyptians were building Pyramids and hadnt such technology we have now ...
I have always been impressed !!!
Sorry for phylosophy, .... 


I dont know ... as u say no way, nat is the ultimate gate ...

Thank you veyr much for your help !!!!

pat'

(Btw, Holland was very very nice !)

---

### Post by mlomker on 2005-09-23
> I dont know how it works. They, i guess, are using a Third PC to enable the connection (with has no nat)


The Skype server sits in the middle.  Skype doesn't work direct...both people need an outgoing connection to Skype's server.

Things like AOL/Yahoo messenger file transfers (or AOL direct chatting) often fail due to NAT/firewall combos.

---

### Post by patrick295767 on 2005-09-23
[QUOTE=mlomker]The Skype server sits in the middle.  Skype doesn't work direct...both people need an outgoing connection to Skype's server.

Things like AOL/Yahoo messenger file transfers (or AOL direct chatting) often fail due to NAT/firewall combos.[/QUOTE]


Thanks for sharing your knowledge ...

I will think about it ... maybe I can find a way for my applications ... 
It's what I thought from reading and so on about the subject ... third pc .... yeahh

Tired from TRIP... Night is giving advices. Maybe I'll find way with visual basic & great idea. (Or maybe going on with my prg rather not soo secured as a ssh)...

I dont know yet 

Thank you again 

See ya'

Pat'

---

