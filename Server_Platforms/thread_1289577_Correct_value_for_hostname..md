---
title: "Correct value for hostname."
date: 2009-10-12
forum: Server Platforms
---

### Post by rnodal on 2009-10-12
Hello all,

I have searched the Internet and I'm getting contradicting information.
What should be the correct value for the hostname?

I had it as: hostname.example.com 
but logically I feel that it should be: hostname

Any input would be appreciated. Thank you! 

-r

---

### Post by scorp123 on 2009-10-12
```
man hostname
```
> 
" ... THE FQDN
       You can&#8217;t change the FQDN (as returned by hostname --fqdn) or the DNS domain name (as returned by dnsdomainname) with this command. The FQDN of the system is  the  name
       that the resolver(3) returns for the host name.

       Technically: The FQDN is the name gethostbyname(2) returns for the host name returned by gethostname(2).  The DNS domain name is the part after the first dot.

       Therefore  it  depends on the configuration (usually in /etc/host.conf) how you can change it. Usually (if the hosts file is parsed before DNS or NIS) you can change it
       in /etc/hosts. .... "

EDIT .... I hit "save" too soon. The rest of my text got cut off. Sorry for that.

Back to topic:

So what this means:  If you only have the short host name in /etc/hostname then you should have the long form at least in /etc/hosts ... But yes, it seems both ways are possible. If I remember correctly RHEL and Fedora put the FQDN into /etc/hostname whereas SUSE, Debian and Ubuntu just use the short name there.

---

### Post by rnodal on 2009-10-12
> **scorp123 said:**
> ```
man hostname
```


EDIT .... I hit "save" too soon. The rest of my text got cut off. Sorry for that.

Back to topic:

So what this means:  If you only have the short host name in /etc/hostname then you should have the long form at least in /etc/hosts ... But yes, it seems both ways are possible. If I remember correctly RHEL and Fedora put the FQDN into /etc/hostname whereas SUSE, Debian and Ubuntu just use the short name there.

Thank you for your great answer.

You are right about the redhat using the FQDN. 

I think I will go short host name for now. Thank you,

-r

---

### Post by bab1 on 2009-10-12
Regardless of where you enter it, the host name is the name of the host.  The FQDN is the host name and the domain name.  This would be hostname.domainname.whatever.  If you have a host named earth and a domain named planets.com then the FQDN is earth.planets.com.  The host name mercury would have the FQDN mercury.planets.com.

---

### Post by scorp123 on 2009-10-13
> **bab1 said:**
> Regardless of where you enter it, the host name is the name of the host.  The FQDN is the host name and the domain name ....  I don't mean to be inpolite ... but that stuff is kinda obvious? And obviously we know all that? The only question was where to put it ... :D

---

### Post by bab1 on 2009-10-13
> **scorp123 said:**
> I don't mean to be inpolite ... but that stuff is kinda obvious? And obviously we know all that? The only question was where to put it ... :D

Hmmmmm,  I read what the OP asked> What should be the correct value for the hostname?


My take on that is *what is a **hostname***.  not where do you store it.

But even this must be taken in context.  As further born out in the OP's example e.g. > I had it as: hostname.example.com
but logically I feel that it should be: hostname


It sure sounds like the question involving the concept of hostname vs. FQDN.

On the other hand, who are you to state> ... but that stuff is kinda obvious? And obviously we know all that?

The OP doesn't state his level of competency, rather he asks for any and all information on the subject e.g. > Any input would be appreciated. Thank you!


---

### Post by rnodal on 2009-10-13
> **bab1 said:**
> Hmmmmm,  I read what the OP asked

My take on that is *what is a **hostname***.  not where do you store it.

But even this must be taken in context.  As further born out in the OP's example e.g. 

It sure sounds like the question involving the concept of hostname vs. FQDN.

On the other hand, who are you to state

The OP doesn't state his level of competency, rather he asks for any and all information on the subject e.g.

Sorry for creating all this mess. 
I should have explained myself better or worded my question better.

My question should have been:
> What should I put in /etc/hostname? The hostname or the FQDN?
 

Like scorp123 mentioned, both are possible. I just wanted to make sure that my decision to put just the hostname was not going to comeback and hunt me later.

Thank you both for helping. Both of you gave me clear and helpful answers that would help others.

Once again, thank you and sorry for the confussion.

-r

---

### Post by ldillon on 2010-01-11
The command "hostname -f" should return the fqdn, if you've properly set up your local DNS, but it never seems to.

There are a few ways to silence the apache error, some are listed above, but I believe that this problem resolves around Ubuntu having a bug in setting the fully qualified domain name.
Redhat never had this problem if all of your DNS-related settings were correct.

I read somewhere that this is an old bug that no one wants to fix.  I wish I had a link to substantiate this.

If I'm wrong on this, someone please squash this rumor.

---

