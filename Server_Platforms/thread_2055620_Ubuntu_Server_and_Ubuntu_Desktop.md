---
title: "Ubuntu Server and Ubuntu Desktop"
date: 2012-09-09
forum: Server Platforms
---

### Post by hank22077 on 2012-09-09
In the Official Documentation under the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/index.html") , Preparing to Install, Server and Desktop Differences it states: 'it('s) just as easy to install a server      application on the Desktop Edition'.

I have searched everywhere, having no luck at figuring out how this is done.

First, I'd like to create an hosting company.
Second, would it be best to use a separate Server install; or install a server application on my existing desktop install.

 If the 2nd, how do I 'install a server      application on the Desktop Edition'?

Thanks

---

### Post by papibe on 2012-09-09
Hi hank22077.

A few thoughts.
[LIST]
[*]When it says "it's easier", it makes reference to the use of GUI installation applications like USC or Synaptic.
[*]On a server you would have to use either apt-get or tasksel.
[*]IMHO, it doesn't make sense to use the Desktop version as your platform for a hosting company. For one machine it makes no difference, but in a scale economy you'll be spending more resources (disk and RAM) on your servers.
[/LIST]Regards.

---

### Post by hank22077 on 2012-09-10
Thank you, that is more clear.

BTW, another STUPID question: Does a computer need to remain ON continuously for an hosting company to give access to servers, if the server is set to an IP address? :-k

---

### Post by Wim Sturkenboom on 2012-09-10
> 
Does a computer need to remain ON continuously for an hosting company to give access to servers, if the server is set to an IP address?

Please elaborate. Which computer? As you might expect, the server(s) need to be on 24/7. Talking about another computer? If so, what's its task?

---

### Post by SeijiSensei on 2012-09-10
To be honest, if you're asking these questions, I'm not sure you are ready to be running a "hosting company."

If you still think you are up to the task, I'd start off by renting a virtual machine from some place like [Linode]("http://www.linode.com/").  For $20/month you can get a machine with 512 MB of memory, a decent chunk of disk storage, a huge pipe to the Internet, and important things like backup power from honking big generators in an air-conditioned locked-down hosting facility.

---

### Post by hank22077 on 2012-09-10
> **Wim Sturkenboom said:**
> Please elaborate. Which computer? As you  might expect, the server(s) need to be on 24/7. Talking about another  computer? If so, what's its task?

> **SeijiSensei said:**
> To be honest, if you're asking these questions, I'm not sure you are ready to be running a "hosting company."

If you still think you are up to the task, I'd start off by renting a virtual machine from some place like [Linode]("http://www.linode.com/").  For $20/month you can get a machine with 512 MB of memory, a decent chunk of disk storage, a huge pipe to the Internet, and important things like backup power from honking big generators in an air-conditioned locked-down hosting facility.

Yes, this is what I mean; I have a virtual space which my computer can connect to.
I can either use my console, or the one they provide. 
So, my question, I geuss is that their virtual space keeps things going even while my machine is off, correct?

---

### Post by SeijiSensei on 2012-09-10
> **hank22077 said:**
> So, my question, I geuss is that their virtual space keeps things going even while my machine is off, correct?

Yes, of course.  The Internet is global so servers must work 24/7.  Does you provider not offer you a management console where you can see graphs of the system's performance over time like the attached?

It's not really clear what you mean by a "virtual space." A hosting account is simply a directory on someone's server where you can put a website, and some tools like editors to manage it.  A "virtual machine" is the equivalent of entire computer residing in a hosting facility.  In the past people like me would either place our own hardware in the facility or rent a physical machine from the provider.  Nowadays I use Linode and get the equivalent of a physical computer but it is really just one of dozens of server instances running on Linode's big servers.

---

### Post by hank22077 on 2012-09-10
Yes, I have a VPS console, which shows me the usage; only not an expensive one.

---

### Post by hank22077 on 2012-09-11
Well, it appears as though I should now mark this as solved.

Many thanks SeijiSensei!

Before I go, I should add that I have 'dabbled' in reseller hosting, I must admit that my original post was somewhat half-assed, appologies; and, that whilst I understand running a server directly from my computer would require it to be left on, I meant to ask if it would need left on while using the VPS service, because their console is connected to mine.

I have the option of using ssh from my computer, or in my account on their site; therefore with my lack of knowledge in the server area, I wasn't quite sure if I needed the same setup on my computer as I have with the VPS provider or not.

Anyway. 
Thanks for the responses.

---

