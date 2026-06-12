---
title: "Doubt about security"
date: 2014-04-06
forum: Security
---

### Post by Phuwin on 2014-04-06
I just wondering which of the following needs no security? Why?
A server that carries a large amount of traffic.
A server that carries a low amount of traffic.
A home machine.
A server behind a firewall.

Thanks

---

### Post by OrangeCrate on 2014-04-06
This will get you started in finding answers to your question(s):

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Iowan on 2014-04-06
Perhaps you could rephrase your question so it doesn't seem so much like a homework question.
From the  [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

---

### Post by pfeiffep on 2014-04-06
> **Phuwin said:**
> I just wondering which of the following needs no security? Why?
A server that carries a large amount of traffic.
A server that carries a low amount of traffic.
A home machine.
A server behind a firewall.

Thanks

IMO all computing devices require some form of security. Even those not connected to the internet require some form of physical security.
The only totally safe device is one not connected to a power source;)

---

### Post by ant2ne on 2014-04-07
> Perhaps you could rephrase your question so it doesn't seem so much like a homework question.LOL
> I just wondering which of the following needs no security? Why?This is obviously a trick question. All devices require security. Apparently even [your DVR]("http://arstechnica.com/security/2014/04/how-new-malware-is-making-the-internet-of-things-the-windows-xp-of-2014/").

---

### Post by bashiergui on 2014-04-07
> **Phuwin said:**
> I just wondering which of the following needs no security? Why?
A server that carries a large amount of traffic.
A server that carries a low amount of traffic.
A home machine.
A server behind a firewall.

Thanks
The one you don't want to control anymore.

---

### Post by CharlesA on 2014-04-07
> **bashiergui said:**
> The one you don't want to control anymore.

/thread.

Everything needs security.

---

### Post by ant2ne on 2014-04-08
> The one you don't want to control anymore. 
^^ LOL that!

---

### Post by Xentime on 2014-04-11
> **CharlesA said:**
> Everything needs security.

Too true. Fun to think how far technology has come when security wasn't even considered so long ago.

---

### Post by SeijiSensei on 2014-04-11
&#8220;Heartbleed is further evidence that we don&#8217;t have our house in order when it comes to Internet security,&#8221; said Edward Felten, a computer security expert at Princeton University.

&#8220;There&#8217;s a level of care in designing systems and sweating the details of their operations that&#8217;s missing in the culture of software development,&#8221; Mr. Felten said. &#8220;We don&#8217;t have the kind of safety culture that is common in fields such as aviation.&#8221;

[http://www.nytimes.com/2014/04/10/technology/users-stark-reminder-as-web-grows-it-grows-less-secure.html](http://www.nytimes.com/2014/04/10/technology/users-stark-reminder-as-web-grows-it-grows-less-secure.html)

I'd trust Felten's judgement over most other observers except perhaps Bruce Schneier.  The "[Freedom to Tinker](https://freedom-to-tinker.com/)" blog Felten founded is an excellent resource as is [Schneier on Security]("https://www.schneier.com/").

---

### Post by bashiergui on 2014-04-12
> &#8220;There&#8217;s a level of care in designing systems and sweating the details of their operations that&#8217;s missing in the culture of software development,&#8221; Mr. Felten said. &#8220;We don&#8217;t have the kind of safety culture that is common in fields such as aviation.&#8221;People die due to faulty jet engines. Therefore safe design matters and there's a financial incentive to prevent deaths (killing people is expensive)

No one died as a result of heartbleed. It costs a lot and it's hard to build security into the development process. As long as there is no/little financial incentive to design safely, we won't.

---

### Post by buzzingrobot on 2014-04-13
> **bashiergui said:**
>  It costs a lot and it's hard to build security into the development process. As long as there is no/little financial incentive to design safely, we won't.

Very true.  Businesses find it is much cheaper to absorb the costs of dealing with a breach.  As consumers, we do not punish businesses by simply boycotting their products or services. We still buy Microsoft.  We still shop at Target.

More bugs would be caught if the will and the resources were available to audit all networking code on all platforms, and to do it over and over and over as new code comes online, including fixes to the bugs the auditing discovered. 

That seems unlikely.  But, a more organized and disciplined approach would be useful, rather than waiting on some random researcher to examine some random piece of software and write about the bugs that were found.

---

### Post by open2reason on 2014-04-13
> **buzzingrobot said:**
> Very true.  Businesses find it is much cheaper to absorb the costs of dealing with a breach.  As consumers, we do not punish businesses by simply boycotting their products or services. We still buy Microsoft.  We still shop at Target.

More bugs would be caught if the will and the resources were available to audit all networking code on all platforms, and to do it over and over and over as new code comes online, including fixes to the bugs the auditing discovered. 

That seems unlikely.  But, a more organized and disciplined approach would be useful, rather than waiting on some random researcher to examine some random piece of software and write about the bugs that were found.

True, just think back a few months to Apple's *gotofail *problems [http://www.forbes.com/sites/andygreenberg/2014/02/23/apples-gotofail-security-mess-extends-to-mail-twitter-imessage-facetime-and-more/](http://www.forbes.com/sites/andygreenberg/2014/02/23/apples-gotofail-security-mess-extends-to-mail-twitter-imessage-facetime-and-more/) but I don't think all that many customers revolted by boycotting Apple products and hitting their bottom line. You can be a big player like Apple or a small group like openssl [https://www.openssl.org/about/](https://www.openssl.org/about/) and bad things happen, is the customer / end user worried or indeed bothered?

I think finance and funding can have a lot to do with getting things right and wonder how many commercial companies relied upon openssl code (or any other open sourced code) for their daily use, their business model yet failed to support the project's work with cash, kit or time?

---

