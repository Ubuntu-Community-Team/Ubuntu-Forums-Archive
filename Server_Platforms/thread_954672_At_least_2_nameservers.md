---
title: "At least 2 nameservers"
date: 2008-10-21
forum: Server Platforms
---

### Post by inadaze on 2008-10-21
Hi,
I have been wrestling with trying to get a dns server working on my Hardy server.  I have bought a domain name and they ask for at least two nameservers.
I made ns1.myDomain.ca and ns2.myDomain.ca but they point to the same IP because I only have one server.  How can I deal with this configuration problem?  I am using bind9 in Hardy.

thanks
Jason

---

### Post by MJN on 2008-10-21
Multiple nameservers (on different routed networks) is not an absolute requirement, although of course often highly desirable and accepted best practice.

Some domain registrars do try and force the listing of multiple servers but if you've only got one, and obtaining another is unnecessary/undesirable/impossible then the usual workaround is to simply do what you've done - give two names which resolve to the same IP address.

Given you've done this, what exactly is the problem you're now having? As you've hidden the domain we can't check the DNS at the parent servers and ensure the glue records are in place. Post your real domain if you want further help.

Mathew

---

### Post by inadaze on 2008-10-21
My domain is foreveragain.ca

The problem is that the company that I got my domain from says I need two nameservers with two different IP addresses.  I got my domain from [www.BudgetNames.ca](www.BudgetNames.ca)

cheers,
Jason

---

### Post by MJN on 2008-10-21
Hi Jason,

They're wrong, at least insofar as them saying you **need** two nameservers with different IP addresses. Sure, it's a good idea but it's not an absolute necessity in order to get a DNS up and running.

I'm not sure what else there is to say.

What problem are you having? Or is just your registrar moaning at you? You're the customer, and it's your domain.

Mathew

---

### Post by david_lynch on 2008-10-21
> **inadaze said:**
> My domain is foreveragain.ca

The problem is that the company that I got my domain from says I need two nameservers with two different IP addresses.  I got my domain from [www.BudgetNames.ca](www.BudgetNames.ca)

cheers,
JasonThat is a pretty standard requirement. Do you have the possibility of getting another IP address? 

If not, perhaps partner with another domain for dns? I do that with a number of domains now - I provide secondary dns server for their domain, and they do the same for me. One hand washes the other.

---

### Post by MJN on 2008-10-21
It's not a necessity though. Best practice, yes. Essential, no.

Jason, I notice the .ca parent servers currently disagree on your domain configuration so presumably you have made changes only recently - this is a very bad time for fault diagnosis given the uncertainty of resolution from cached results on different servers.

Mathew

---

### Post by inadaze on 2008-10-21
My problem is that I cannot hook up my domain name foreveragain.ca to my dns server at home.  I assume that the issue comes from the fact that BugetNames.ca won't let me get away with two nameservers with the same IP.  Everytime I configure the domain name I can never save the configuration because I don't have two different nameservers.  I spoke to the support and that is what they said.  

I will stop playing around with the configuration for a day or so until the root servers update, but in the end, should I look for another domain name service or should I look for a backup nameserver (and if so, how would I find that)?

Thanks
Jason

---

### Post by MJN on 2008-10-21
Sadly, it sounds like a case of 'computer says no'. That is, their online configuration tool is configured to 'help' the customer and stop them making mistakes, but when you want to purposely configure the domain in the way you want it then it falls over itself. Of course, the helpdesk guys running the place are likely reading off scripts written by the authors of the online tool...

Your only option, if you cannot get the registrar to allow you to configure your own domain how you want it configured (fully compliant with the standards etc) then either change registrars or find someone to provide secondary services for you. David...? ;-)

(Depending on why you want to run your own DNS you could always let a 3rd party do it for you - there are numerous free, yet still reliable, services available)

Mathew

P.S. I'm sure at least one of the parent servers was saying foreveragain.ca was delegated to auth1.foreveragain.ca and auth2.foreveragain.ca - and both these names resolved to the same IP.... So, it *was* working... (or my memory is failing me... quite likely!)

---

### Post by inadaze on 2008-10-21
I tried to trick them into letting me have one of my nameservers and one of their default nameservers, but the wouldn't let me.

This is all just a learning experience so I really want to get the domain name working for my dns server.  I know it sounds like a lesson in pain, but I wanted to know more about servers and networking.  

I will try and find a second server or see if I can get my domain name service to let me off with one nameserver (or I'll find another place).

thanks for your help.
Jason

---

### Post by MJN on 2008-10-21
> **inadaze said:**
> This is all just a learning experience so I really want to get the domain name working for my dns server.  I know it sounds like a lesson in pain, but I wanted to know more about servers and networking.  That's why such registrars can be a real pain. Sure, if doing things 'properly' this wouldn't be an issue as you'd be having multiple name servers supporting your domain but given you are doing this to learn about DNS and nothing more then their inflexible processes and procedures are holding you back.

Keep at them. You shouldn't have to convince them (given it is your domain) but if it helps mention that you are well aware of the drawbacks of effectively only have a single nameserver and that such a configuration is far from 'best practice' but that you are doing this purely for educational purposes and only have access to the one server (IP) anyway. Even if they don't understand and still insist it won't work just ask them to do it anyway and you are quite happy to live with the consequences.

It is quite likely that 1st line support will need to send a request back to the guys their system... just get them to escalate it back and hopefully you'll reach someone who is willing to deviate from the scripts...

Mathew

---

