---
title: "Sendmail or PostFix issues?"
date: 2013-06-19
forum: Server Platforms
---

### Post by smOBudda on 2013-06-19
I've recently moved my machines to a new location. One of the servers that we use for web hosting no longer is able to send reports from sendmail. All websites use Joomla and I've checked to make sure that the issue isn't due to configuration settings via Joomla. None the less I do get a message when trying to restart sendmail using command line though not to sure what it means. 



```

root@smODial3000:~# sudo /etc/init.d/sendmail restart
 * Restarting Mail Transport Agent (MTA) sendmail                               
start-stop-daemon: unable to stat /usr/sbin/sendmail-mta (No such file or directory)
/etc/init.d/sendmail: 296: /etc/init.d/sendmail: /usr/sbin/sendmail-msp: not found
                                                                         [ OK ]
```

The platform of the Ubuntu server is up to date with the most current distro-upgrade. 

Any help or direction you could provide me to resolve this issue would be great. Also if there is any logs I could provide that would assist in this issue please let me know I would be happy to provide them. Thanks for any help you can offer ahead of time.

---

### Post by lisati on 2013-06-19
The error message says to me that you were trying to restart sendmail but it's not installed.

If you have postfix installed, you probably don't need to install sendmail as well, because postfix comes with a [sendmail compatibility interface]("http://www.postfix.org/sendmail.1.html").

---

### Post by smOBudda on 2013-06-19
Is this any help in terms of helping me find a solution for my problem?

I looked into the Mail.log:
```

REMOVED

```

---

### Post by SeijiSensei on 2013-06-19
> (Host or domain name not found. Name service error for name=demolink.org type=MX: Host not found, try again)

Looks to me like the server doesn't have proper name service resolution.  How is the network configured on this machine?  If you are using static addressing, which is the norm on servers, then you need to [add a "dns-nameservers" line]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html") to /etc/network/interfaces to specify the nameserver addresses you are using.

The site "demolink.org" has a properly specified MX record:

```

$ host -t mx demolink.org
demolink.org mail is handled by 10 p.nsm.ctmail.com.

```

The fact that your server cannot find it means that the server has a problem with its DNS setup.

---

### Post by smOBudda on 2013-06-19
> 
The site "demolink.org" has a properly specified MX record:

```

$ host -t mx demolink.org
demolink.org mail is handled by 10 p.nsm.ctmail.com.

```

The fact that your server cannot find it means that the server has a problem with its DNS setup.

I would imagine your correct. I looked using mxtoolbox and when I search my domain it gives me DNS warnings.. I guess the next piece of advice I would ask for is how do I correct the DNS issue?

---

### Post by SeijiSensei on 2013-06-19
Read the page I linked to above.

---

### Post by smOBudda on 2013-06-19
Issue resolved, thank you for taking the time to help me out.

---

### Post by BlinkinCat on 2013-06-19
> **smOBudda said:**
> Issue resolved, thank you for taking the time to help me out.

Hi,

You can mark thread as solved in first post -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

