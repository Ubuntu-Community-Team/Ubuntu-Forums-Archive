---
title: "Need know good internet filter / link"
date: 2010-04-04
forum: Security
---

### Post by grimmson on 2010-04-04
Had a bad weekend and I need some help. After my sons 10th birthday I checked his browser history, needless to say social networking has educational benefits. So far I've spent 8 - 9 hours doing clean installs of 9.10 with dansguardian and squid with negative results. I think steps are assumed or left out of the directions because it ultimately leads to failure. Documentation can be found about the squid dating back to the year 2000. Basically I need an up to date filter for his pc running 9.10 with good install / setup directions. The quicker the set up the better, I just ran out of weekend.

p.s. the link to set up dansguardian on the homepage failed. it's dated March 19, 2006. [http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)
If you give me something that  works I'll let Dan know.

---

### Post by xpod on 2010-04-05
Mabey your trying too hard, with the wrong methods.;)
I find just using [OpenDNS`s](http://www.opendns.com/) filtering abilities stops anything i wouldn`t want our younger girls seeing from popping up on their screens. That`s as far as the porn and tasteless stuff is concerned anyway. I dont actively block any of the Social Networking type sites because we also have Teenagers, who do use Facebook etc. I could lock down the individual machines, and indeed have done in the past, but, i`ve found education(for us all), discussion & involvement works best. The younger girls do have MSN accounts for chatting to family & friends via whatever messenger app they use but they`re not allowed Facebook & Bebo type accounts....not at that age.

I only sat down at a computer myself some 4 years ago because of the sheer dread i felt at the prospect of our girls being let loose on the big bad Internet and me knowing absolutely nothing about it. Irrational & unfounded most of that dread turned out to be for sure but you only have to pick a newspaper up to hear about some other wee girl who`s been groomed & ultimately murdered by some animal to know it`s not all smilies & lol`s.

---

### Post by lisati on 2010-04-05
Some routers have filtering capabilities. My Netgear router has fairly basic filtering, which can be set to block certain sites. My main router/modem (a Thomson Speedtouch model) has the ability to block sites, and also has the ability to redirect specified sites to others that you might be more comfortable with.

---

### Post by grimmson on 2010-04-05
Thank you both. I'll try these options ans see what happens. My kid is young enough where a totally unrestricted Internet just won't work. Might request this be addressed with edubuntu so parents have a slick option that's a little quicker than go fish on the net and hope for the best. Something in the repos would be great.

---

### Post by xpod on 2010-04-05
> **lisati said:**
> Some routers have filtering capabilities. My Netgear router has fairly basic filtering, which can be set to block certain sites. My main router/modem (a Thomson Speedtouch model) has the ability to block sites, and also has the ability to redirect specified sites to others that you might be more comfortable with.

Redirecting individual sites you dont want your kids on means the little mites are still trying to get on the sites in question. I`d end up just killing their connection full stop if i was constantly being disobeyed like that. ....Ours all have virtually unrestricted access to the net to start with(XXX etc asides) and only by their own actions can they lose it.

That`s not to say you cant be an annoying parent just for the fun of it with they type of tactics in questions.:-\"

EDIT: That possibly made me sound like some Victorian dad, which is in fact far from the truth. The lack of any Facebook type accounts for our Primary School children is not even an issue. They dont actually care(...yet) and none of them have ever lost their Internet access when they eventually got their own machines.

---

### Post by grimmson on 2010-04-05
I got ya xpod. I'd say your right most of the time. This is a new development that I wasn't ready for. I'm positive when a friend came over he taught lessons I didn't assume my son would have access to. From here teaching why not to click links, follow pop ups, talk to strangers when your not really prepared or positive who it is,etc... That is why I wanted to turn to a highly restrictive net nanny and follow up with browser history. When he would ask can't I go here or why is this disabled it would give me the chance to engage him on things I might not think of up front (like why it's not good to ask for a $10,000 loan). I've got a good kid, but the Internet is too vast  for me to cover every why and what if. There are a lot of things I don't want him to stumble on (like megaporn.com) and me not catch it until it's too late.

---

### Post by bodhi.zazen on 2010-04-06
> **grimmson said:**
> Had a bad weekend and I need some help. After my sons 10th birthday I checked his browser history, needless to say social networking has educational benefits. So far I've spent 8 - 9 hours doing clean installs of 9.10 with dansguardian and squid with negative results. I think steps are assumed or left out of the directions because it ultimately leads to failure. Documentation can be found about the squid dating back to the year 2000. Basically I need an up to date filter for his pc running 9.10 with good install / setup directions. The quicker the set up the better, I just ran out of weekend.

p.s. the link to set up dansguardian on the homepage failed. it's dated March 19, 2006. [http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)
If you give me something that  works I'll let Dan know.

My advice is for you to set up a proxy server.

Squid / Dansguardian are the "gold standard" , but not so easy to configure as you can see.

An alternate might be privoxy.

[http://www.macos.utah.edu/documentation/servers/privoxy.html](http://www.macos.utah.edu/documentation/servers/privoxy.html)

It might be easier for you to learn the syntax of privoxy.

Alternately you can block everything and then white list allowed sites.

What how-to are you following with Dansguardian ?

---

### Post by bodhi.zazen on 2010-04-06
Update: Dansguardian is very very easy to install.

[https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian)

```
sudo apt-get install tinyproxy dansguardian
```

Edit the dansguardian config file:

```
gksu gedit /etc/dansguardian/dansguardian.conf
```

Comment (add a # in the front) out the line near the top UNCONFIGURED

> # UNCONFIGURED - Please remove this line agter configuration

now search for the line "proxyport" and change to to 8888

```
proxyport 8888
```

Save and exit.

start the services

```
sudo service tinyproxy start
sudo service dansguardian start
```

Open Firefox, 

Edit -> Preferances -> Advanced tab -> Network tab -> Settings button

use localhost 8080 for all connections

This page has some general screen shots :

[http://www.hsl.virginia.edu/services/computing/FirefoxProxySetUp.cfm](http://www.hsl.virginia.edu/services/computing/FirefoxProxySetUp.cfm)

That's it,

---

### Post by bodhi.zazen on 2010-04-06
ARggg !!! 

dansguardian has a bug :

[https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475](https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475)

I installed squid and dansguardian is working.

```
sudo apt-get purge tinyproxy
sudo apt-get install squid
```

Re-edit /etc/dansguardian/dansguardian.conf

Change the port back to squid

```
proxyport 3128
```

Keep firefox using port 8080

---

### Post by yeleek on 2010-04-06
If you've a spare machine and want something which is easy to manage why not try one of the many, many free browser based content proxy servers such as:


[http://www.untangle.com/Product-Overview](http://www.untangle.com/Product-Overview)
[http://www.smoothwall.org/about/express-feature-list/](http://www.smoothwall.org/about/express-feature-list/)

also monowall, pfsense, etc etc

Thing is - and I'm aware of this for my own child - its not just url filtering we need to be aware of now.  And whilst I don't think i'd ever block IM completetly, I'd make sure my child knew i had the ability to monitor them.

---

### Post by bodhi.zazen on 2010-04-06
I took me a hile to get it all sorted, but I would use dansguardian + privoxy

See : [http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by grimmson on 2010-04-18
Troopers you guys are. Thanks for all the advice and big thanks to bodhi.zazen for chasing the dans bug to conclusion and offering an alternitive method. I am glad someone like you is on the dev team.

---

