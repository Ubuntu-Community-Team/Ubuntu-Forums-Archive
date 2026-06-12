---
title: "k9 web protection linux port"
date: 2008-05-25
forum: Ubuntu Christian Edition
---

### Post by eric.duveau on 2008-05-25
Dear all, I would like to encourage project to port [_k9 web protection_]("http://www.k9webprotection.com") for Linux.

To sumerize K9 is a proxy redirector **freely** available on mswindows connected to a powerful commercial filtering database. The filtering is very accurate (very little overblocking no very little underblocking as the database is very accurate)

We need your support:  :D
Here is the URL:[_micropledge.com/projects/k9-webfilter-for-linux_]("http://micropledge.com/projects/k9-webfilter-for-linux")

---

### Post by macdogdaddy on 2008-11-26
Yes, I enthusiastically second this request.  I have used this program on my nephew's Windows box for couple years and it has been very useful.  Especially after he got his browser infected.  

Each time he ran his browser (any browser) it opened endless pop-ups to shady sites.  This didn't stop the pop-ups, but it wouldn't let the shady sites load.  

Now that I'm reloading his OS (destroyed by virus) I thought of cutting his teeth on Ubuntu. As a recent windows convert myself, having this program available would make the switch much easier.  And as mentioned above, it works very very good.

---

### Post by jonathonblake on 2008-11-26
> **eric.duveau said:**
> _k9 web protection_[/URL] for Linux.

What does k9 offer that DansGuardian does not offer?

jonathon

---

### Post by eric.duveau on 2008-11-27
k9 web protection and Dansguardian do not have the same filter philosophy. 

Dansguardian as it configured on CE ubuntu analyzes the pages strings before displaying to the web browser. 

K9 compared the browsed URL to a huge professional URL categorized database. 


I have found that the K9 categorization is very accurate. Whereas dansguardian is less (I have often seen good sites being blocked).

I hope that my answer is clear.

---

### Post by eric.duveau on 2008-11-27
[http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&st=0&sk=t&sd=a&hilit=linux](http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&st=0&sk=t&sd=a&hilit=linux) if you want to know more about this port project.

---

### Post by jonathonblake on 2008-11-27
> **eric.duveau said:**
> 

K9 compared the browsed URL to a huge professional URL categorized database. 


In reading the site, that isn't the understanding I came away with. (Which is why I asked the question --- both K9 and DansGuardian claim to have the same design philosophy, albeit implemented in slightly different ways.)

jonathon

---

### Post by Shwefty on 2008-11-27
+1 for K9, I used it on Windows.  It was a little intrusive there, but if you're looking for protection it is fantastic!

---

### Post by lawmanuk on 2008-11-28
you could always change your dns server to:

[www.opendns.com](www.opendns.com) or
[www.scrubit.com](www.scrubit.com)

both of these are free and have built in web filtering, with opendns providing customisation options.

---

### Post by eric.duveau on 2008-11-28
> **lawmanuk said:**
> you could always change your dns server to:

[www.opendns.com](www.opendns.com) or
[www.scrubit.com](www.scrubit.com)

both of these are free and have built in web filtering, with opendns providing customisation options.

Yes but as far as I have understood, opendns.com is easy to tune only if you have a fix IP public address. I have tested  [www.scrubit.com](www.scrubit.com) but it seems that the reliablility is not very good. 

In my case, I have a dynamic public IP address. So opendns is not a good choice.

Besides K9 is not easy to remove even it you are the administrator of your PC. So I would like to use K9 and be root at the same time !

---

### Post by KIAaze on 2008-12-03
Found this while googling for opendns+k9 for use on a windows machine. :)

> **eric.duveau said:**
> I have found that the K9 categorization is very accurate. Whereas dansguardian is less (I have often seen good sites being blocked).


Use [http://urlblacklist.com/](http://urlblacklist.com/) ;)

Also, it's useful to comment out "japanese pornography" in the weightedphraselist, as well as whitelist all webmail sites in the "exceptionsitelist".

/etc/dansguardian/lists/exceptionsitelist:
```

...
.Include</etc/dansguardian/lists/blacklists/mail/domains>
...

```
/etc/dansguardian/lists/weightedphraselist:
```

...
##.Include</etc/dansguardian/lists/phraselists/pornography/weighted_japanese> #ALPHA#
...

```

More info and GUI:
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)
(still needs a lot of work, so any help is welcome!)

---

### Post by jamorod on 2010-03-15
Do you know if there has been any progress on this? I shifted to Ubuntu a couple of months ago, and would like to install K9. 

Which is the best alternative availble if it isn't ready yet?

Thanks!

---

### Post by KIAaze on 2010-03-15
These are the only possibilities I know of for the moment:
-dansguardian
-openDNS
-Firefox plugins (but you might need to find out how to lock the plugin settings and it's obviously restricted to Firefox or other mozilla-based browsers)

dansguardian GUI: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
Check the list of alternatives here too: [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

---

### Post by ElQanah on 2010-05-17
I just want to say that K9 Blue Coat is a great tool for us parents.  I do home computers support and recommend this to every family and every parent.  Now, I also enjoy providing linux and support for it to homes, and such a tool as this is needed.  Linux community offers some other alternatives, but not close to the excellence of K9.

Congrats for such a great work.  I add my self to the wish and waiting list.   :P

---

### Post by pizza-is-good on 2010-11-09
Any updates on this project? I am waiting for K9 for Ubuntu. I have used it on windows and it is superb.

---

### Post by jadonchristensen on 2011-09-19
If you want to use OpenDNS, but with less setup and just want to block porn, use their FamilyShield. No need to worry about Dynamic IPs.

[http://www.opendns.com/landings/familyshield](http://www.opendns.com/landings/familyshield)

P.S. I would like to see K9 for Linux, since it is very customizable.

---

