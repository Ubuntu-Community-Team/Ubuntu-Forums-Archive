---
title: "[Solved] Some ubuntu.com sites down?"
date: 2016-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-04-12
> Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.I'm seeing this for [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) (for the past few hours) and [http://changelogs.ubuntu.com/changelogs/pool/main/a/apt/apt_1.2.10/](http://changelogs.ubuntu.com/changelogs/pool/main/a/apt/apt_1.2.10/) (since yesterday).

---

### Post by bapoumba on 2016-04-12
Hmm, same here.

---

### Post by Rocky_Bennett on 2016-04-12
Microsoft is now running those sites.

---

### Post by QIII on 2016-04-12
> **Rocky_Bennett said:**
> Microsoft is now running those sites.


Beg pardon?

---

### Post by buzzingrobot on 2016-04-12
Ditto.  Noticed the changelog site yesterday.

Anyone know if Canonical provides the status of its infrastructure someplace? Fedora does, and it's useful sometimes.

(Some Microsoft sites were unavailable for several hours last week. Things happen.)

---

### Post by vasa1 on 2016-04-12
> **buzzingrobot said:**
> Ditto.  Noticed the changelog site yesterday.

Anyone know if Canonical provides the status of its infrastructure someplace? Fedora does, and it's useful sometimes.

(Some Microsoft sites were unavailable for several hours last week. Things happen.)

And [Mozilla had "various" issues]("https://mail.mozilla.org/pipermail/firefox-dev/2016-April/004148.html") that have made them delay the release of Fx 46 by a week.

---

### Post by Habitual on 2016-04-12
500 errors are Server-side.

---

### Post by grahammechanical on 2016-04-12
Down for more than a week.[URL="http://www.isitdownrightnow.com/manpages.ubuntu.com.html"]

http://www.isitdownrightnow.com/manpages.ubuntu.com.html[/URL]

Regards.

---

### Post by vasa1 on 2016-04-12
> **grahammechanical said:**
> Down for more than a week.[URL="http://www.isitdownrightnow.com/manpages.ubuntu.com.html"]

http://www.isitdownrightnow.com/manpages.ubuntu.com.html[/URL]

Regards.
While that's what that site says, I'm not sure it's been that long. Maybe 2-3 days so far. I visit the online man pages quite often.

---

### Post by bapoumba on 2016-04-13
[http://changelogs.ubuntu.com/](http://changelogs.ubuntu.com/) works but not the OP's url.
manpages are still down.
May be a bug report ?

---

### Post by howefield on 2016-04-13
From #canonical-sysadmin

Topic```

"For help highlight: sajoupa || Known issues: {upstart,manpages}.ubuntu.com are down || Although we idle here, please mail requests to rt@ubuntu.com"
```

```
20:27:58      --> | inetpro (~quassel@unaffiliated/hibana) has joined #canonical-sysadmin                                                                                  &#9474; alexlist     
20:28:31  inetpro | hi everyone                                                                                                                                            &#9474; aluria       
20:28:48  inetpro | I am getting a 503 Service Temporarily Unavailable error when doing a changelog request                                                                &#9474; and`         
20:29:46  inetpro | maybe ongoing maintenance causing that?                                                                                                                &#9474; apw          
20:30:09  inetpro | failing URL: http://changelogs.ubuntu.com/changelogs/pool/main/a/apt/apt_1.0.1ubuntu2.5/changelog                                                      &#9474; arosales     
20:30:18   pleia2 | inetpro: I responded in the other channel, they told me yesterday that the server ihad filesystem corruption and they are working on restoring         &#9474; artmello     
20:30:29   pleia2 | "The machine that hosts upstart.ubuntu.com suffered permanent                                                                                          &#9474; axino        
20:30:29   pleia2 | damage to its filesystem today, also affecting changelogs.ubuntu.com                                                                                   &#9474; beisner      
20:30:30   pleia2 | and manpages.ubuntu.com."                                                                                                                              &#9474; benonsoftware
20:30:34  inetpro | pleia2: ah, thanks                                                                                                                                     &#9474; BjornT       
20:30:40     k1l_ | Known issues: {upstart,manpages}.ubuntu.com are down                                                                                                   &#9474; blahdeblah_  
20:30:54   pleia2 | ah, yes, it's in the channel topic too :)                                                                                                              &#9474; bloodearnest 
20:31:09     k1l_ | but http://changelogs.ubuntu.com/ works for me                                                                                                         &#9474; bradm        
20:31:28  inetpro | sad to hear that and hoping that it will be up again soon, thanks       
```

---

### Post by bapoumba on 2016-04-13
Thanks howefield :)

---

### Post by vasa1 on 2016-04-13
> **bapoumba said:**
> Thanks howefield :)
+1.

---

### Post by howefield on 2016-04-13
[http://status.admin.canonical.com/](http://status.admin.canonical.com/) can be a good site to be aware of, except unfortunately it is also down... :(

---

