---
title: "Really strange McAfee problem"
date: 2012-02-01
forum: Security
---

### Post by Danny*` on 2012-02-01
Hi everybody, 

some really weird problem started yesterday. When I try to open certain websites (even Facebook) they are blocked by McAfee firewall. The weird part is I never installed McAfee and I cant find it anywhere in my software center or my "home". 

Does anyone have a clue what to do? I`m pretty new to Linux and I don't and would appreciate any help.

Danny

---

### Post by Paddy Landau on 2012-02-01
This is ultra weird, as McAfee is for Windows, not Linux.

Did you install WUBI or is this a native installation?
Which version of Ubuntu did you install?
How do you know that McAfee is blocking it -- what error message do you get, and where do you see the error message?

---

### Post by Dangertux on 2012-02-01
Is it actually McAfee? Can you provide a screenshot of the behavior you're witnessing.

Also : McAfee does have a Linux version for those who don't know.

---

### Post by uRock on 2012-02-01
Are you on a home network or a corporate/college network.

---

### Post by emiller12345 on 2012-02-01
> **uRock said:**
> Are you on a home network or a corporate/college network.
+1 
I think this sounds very much like a networking problem
you might want to grab some info about how your computer is currently configured (not necessarily post this info though)
This will grab the address request protocol info (MAC addresses) of the computers on your local segment that your computer is talking with
```
$ arp -van
```
This will grab the routing tables and gateway info of your computer
```
$ route -n
```
This will grab your ip
```
$ ifconfig -a
```

---

### Post by deonis on 2012-02-01
try proxy server of any kind ... if it works then everything is fine with your PC. If not - you are not using Linux :)

---

### Post by CharlesA on 2012-02-02
> **deonis said:**
> try proxy server of any kind ... if it works then everything is fine with your PC. If not - you are not using Linux :)
I would advise against this if they are on a corporate or school network.

---

### Post by Danny*` on 2012-02-05
Okay, it seems to be a browser-related issue, since other browsers are working fine.

A little info on my system:
Dedicated Linux machine (custom built for Linux, never had any Win version on it) using Ubuntu 11.10. 
Using a wire connection on my private router. I`m the admin and the only one using the router and computer (at least to my knowledge). 
I can`t use proxies since everything "seedy" and then some is being blocked
(other browsers do work). And I (as the administrator) sure as hell didn't put anything on any block list. 

@emiller12345

As a total noob I`m gonna have to look into that. I will reply once I have done so.

---

### Post by Dangertux on 2012-02-05
> **Danny*` said:**
> Okay, it seems to be a browser-related issue, since other browsers are working fine.

A little info on my system:
Dedicated Linux machine (custom built for Linux, never had any Win version on it) using Ubuntu 11.10. 
Using a wire connection on my private router. I`m the admin and the only one using the router and computer (at least to my knowledge). 
I can`t use proxies since everything "seedy" and then some is being blocked
(other browsers do work). And I (as the administrator) sure as hell didn't put anything on any block list. 

@emiller12345

As a total noob I`m gonna have to look into that. I will reply once I have done so.

That screenshot is from McAfee web gateway. This is a server side product that is usually used on proxy servers. There is a good chance that your other browser is set to use some proxy, again is this router attached to a school or corporate network?

Because that is where this is coming from (some larger network.)

Hope this helps.

---

### Post by emiller12345 on 2012-02-05
> **Danny*` said:**
> 
As a total noob I`m gonna have to look into that. I will reply once I have done so.
If your sure theres no problem with other browsers on the same computer then those commands will not help you.  If its just FF, you could check your Preferences >> Advanced >> Network >> Settings... and look to see if your settings have been altered. I think the default is to `Use system proxy settings'. Or it might be a strange plug-in that is altering the proxy settings.

---

### Post by Danny*` on 2012-02-05
And the solution is... 

> your other browser is set to use some proxy> `Use system proxy settings'You got it! It happened a couple days back I installed Proxtube, a Firefox Add-On... I gave it a quick thought that these might be related (because problems started about the time of installation as I recalled) but somehow forgot about it. 

Proxtube let`s you watch Youtube Videos that have been blocked for German users by the fine GEMA (copyright management mafia). I didn`t want to go through the trouble using "normal" proxy everytime, so this seemed convenient. Guess I`ll have to find another solution. Epiphany works fine, so I can use FF for YT only. 

>  There is a good chance that your other browser is set to use some  proxy, again is this router attached to a school or corporate network?
No, I live in my own appartment (not in a dorm, etc.) with my own phone connection and all... It`s as private as it gets. No network. This seems strange... why would hidemyass.com for example or file sharings sites (not that I would go there or anything, god forbid) block people using proxies (I guess that is what "server sided" means, right?)?

Anyway, I disabled Proxtube, didn´t work, I deinstalled PT and it still didn`t work until I 
used emillier's advice and changed used system proxy settings. It works!!
 
So thanks everybody for the advice, I learned something new (that includes making a screenshot :D). 

The only thing I need to know now is how to put a "solved" in front of the thread title for future generations. EDIT: Solved.

---

