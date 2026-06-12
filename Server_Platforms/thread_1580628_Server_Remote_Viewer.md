---
title: "Server Remote Viewer"
date: 2010-09-23
forum: Server Platforms
---

### Post by De Los Santos on 2010-09-23
okie dokie so... Ive been given the chance to control the server for my highschool.:lolflag: I know (for the most part) what im doing but ive been asked to put a remote desktop viewer on it so we can view anyone on the server(something like dameware mini remote). ive never done this before so id like some help. The machine is running ubuntu 10.04 and has connected thin clients for student access. If you need more info just ask and ill provide. Thanks

---

### Post by arrrghhh on 2010-09-23
Is the server running X?  You want to spy on the thin clients?

---

### Post by De Los Santos on 2010-09-23
Lol no idea about x, im completly new to this system setup. I know ubuntu well but not so much the server side of things. And yes i need to be able to "spy" on the thin clients.

---

### Post by scrooge_74 on 2010-09-23
but what about just checking the logs, or you just want to be able to watch them move the mouse around and type?

---

### Post by arrrghhh on 2010-09-23
Yea, I'm not sure it's possible to spy on the thin clients live... plus it would probably slow down the server&client fairly drastically... depending on your setup, network, etc.

---

### Post by De Los Santos on 2010-09-23
I can check the logs but other less computer literate people (teachers) cant. They also just want to be able to watch over students.

---

### Post by scrooge_74 on 2010-09-23
got it, and I second what arrgh says, you are going to give the server some overhead, it depends how good it is.

Why not just block access to all those sites/programs/functions you dont want students using?

They are using thin clients so is a bit easier :D

Dansguardian is a good option for blocking/managing what they can or can't see

---

### Post by arrrghhh on 2010-09-24
Hrm... I have to say, I know of many ways you could watch over the students real-time (like VNC) but most things like that are not meant for that purpose - so it'll take quite a bit of leg work to setup on your end, and it would probably be very unweildy to manage.

Basically what I'm saying is I'm not aware of any built-in way to monitor what the clients screens are showing...

Plus, it seems like a very archane way to monitor what the students are doing - I agree that a proxy that filters out bad content would be much more useful than something that allows direct spying :P

---

### Post by HermanAB on 2010-09-24
Use webmin and SSH.  VNC is primarily a Windows thing and doesn't work so great with Linux.

---

### Post by De Los Santos on 2010-09-24
I go to a technical school so we have everything from medical and vehicle tech classes, to I.T. A+ and ccna classes. There are a bunch of smart kids (including me) that know ways around proxies and blockers of all sorts because we already have them in place. That being said. there is remote desktop on the server and i created an account for the thin clients. I logged onto a thin client and enabled remote desktop. I then in turn was able to view it from the server. only thing is that i would have to go onto every account and change the setting in it... that would take forever. can i change them all at once?

---

### Post by BkkBonanza on 2010-09-24
[Xnest]("http://en.wikipedia.org/wiki/Xnest") perhaps, or [FreeNX]("https://help.ubuntu.com/community/FreeNX") [shadow sessions]("http://openfacts2.berlios.de/wikien/index.php/BerliosProject:FreeNX_-_HowtoShadow").

---

### Post by De Los Santos on 2010-09-24
Lol just read hermans post. ill keep reading.

---

### Post by De Los Santos on 2010-09-24
by the way. If any of you are wondering/ need the info. The server is an intel based quadcore 3.4ghz x2 with 32 gigs of ram lots of blue lights. lol. All the thin clients have 2 gigs of ram and dual core 2.8ghz... we just got them this summer. i had to put them all together >.<    all in all there pretty fast machines.

---

### Post by arrrghhh on 2010-09-24
> **De Los Santos said:**
> by the way. If any of you are wondering/ need the info. The server is an intel based quadcore 3.4ghz x2 with 32 gigs of ram lots of blue lights. lol. All the thin clients have 2 gigs of ram and dual core 2.8ghz... we just got them this summer. i had to put them all together >.<    all in all there pretty fast machines.

You definitely seem very "technical"...

Anyhoo, with those specs I guess you'd be fine... but I still don't understand how you could possibly watch all the students at the same time...

If you setup your internet connection correctly, the 'smart kids' won't be able to get around the proxy - at my work, if you don't use the proxy, you don't get internet access... simple.

---

### Post by De Los Santos on 2010-09-24
lol well i cant tell if that was a compliment or what. lol. but ill take it as a compliment. but to clear things up i dont want to watch all of them at the same time. I just need to be able to have access to a list of computers, then click the one i choose and see that specific computer. thank you everyone for your help so far.

---

### Post by scrooge_74 on 2010-09-24
Lol

you want to watch what the "smart" ones are doing ...

---

### Post by De Los Santos on 2010-09-24
lol in a sense yes.

---

### Post by scrooge_74 on 2010-09-24
I guess the apps posted higher up should let you see what the "smart" ones are doing, you could also install squid + Dansguardian to keep them out of most places. Also you can use OpenDNS on the server and then use the free account on their website and you can even block more stuff out.

---

### Post by arrrghhh on 2010-09-26
Yes, and with some smart network design, you basically ONLY allow web traffic out if it goes thru the proxy - basically you don't give open access to the web if the client bypasses the proxy.  That's how we do it at work, and it works amazingly well - but it also works really well because our filters do not allow going to any sites that use web proxies either - so it makes it very difficult to back door the filters.

---

### Post by BkkBonanza on 2010-09-26
> **arrrghhh said:**
> That's how we do it at work, and it works amazingly well - but it also works really well because our filters do not allow going to any sites that use web proxies either - so it makes it very difficult to back door the filters.

How do you handle HTTPS ? Block it?

---

### Post by arrrghhh on 2010-09-27
> **BkkBonanza said:**
> How do you handle HTTPS ? Block it?

If it's not piped thru the proxy, it's not allowed out basically.

---

### Post by kevin11951 on 2010-09-27
I can't believe no one has posted this yet:

[http://italc.sourceforge.net/home.php](http://italc.sourceforge.net/home.php)

It's in the Edubuntu docs even!



Anyway, here is a screen shot:

[IMG]http://italc.sourceforge.net/screenshots/italc-1.0.6_1.jpg[/IMG]

---

### Post by kevin11951 on 2010-09-27
Also:

[https://help.ubuntu.com/community/UbuntuLTSP/iTalc](https://help.ubuntu.com/community/UbuntuLTSP/iTalc)

It's meant for Ubuntu 8.04, so if you are using a later version, you should ask here and someone should help out with the details.

---

### Post by arrrghhh on 2010-09-27
Ha, nice.  Never used Edubuntu.  Good find.

---

### Post by scrooge_74 on 2010-09-27
Nice solution no one tough of Edubuntu. 

We either:

1. too old to think of watching school children
2. Our kids are not that "smart" that we need to watch them
3. No kids of our own

---

### Post by BkkBonanza on 2010-09-28
Cool.
I wonder what pc008 is up to... 

... he's probably the "smart" one you want to watch. He makes you think he's powered off but is really firewalled and proxying out on HTTPS.

---

### Post by De Los Santos on 2010-09-28
oh sheesh ya'll! thank again for all the help im glad i got this figured out.

---

