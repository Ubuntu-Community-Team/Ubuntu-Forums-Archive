---
title: "New to Servers"
date: 2013-08-26
forum: Server Platforms
---

### Post by Arunomi on 2013-08-26
Hi 

Im thinking of making my own server
and i have a thougt.

Im thinking of runing ubuntu server edition and then xen to make virtual servers.
for starters on file server, one gateway and on user server.

Is my hardware to week.

Asus A7N8x-e Delux
Athlon xp +3200
3gb ram

AN is it to much work to set up virtual servers so i 
should go for just servers and no virtual.

Best regards Sean

---

### Post by kpothi on 2013-08-26
You may need more hardware depending on the your actual requirement in the future. For a start, this should do.

---

### Post by Arunomi on 2013-08-26
I will upgrade my hardware in the future 
but if i can use what i have I can save money
now to spend it later =)

---

### Post by nerdtron on 2013-08-26
For a file server, your hardware can handle it. But for virtualisation, I'd say no. 3GB RAM is small and your processor is weak. You should consider using at least a dual core (or quad core) processor when running a virtualize system.

---

### Post by SeijiSensei on 2013-08-27
You don't really need to use virtual servers just to provide an array of Internet services.  I have machines that simultaneously run mail, web, DNS and an SQL db and hardly break a sweat.  Unix was designed from the start as a multiuser, multiprocess operating system, and Linux carries on that tradition.  You'd be much better off running all the services you need on this one machine rather than slicing up your memory into separate VMs.

---

### Post by Arunomi on 2013-08-31
When is it a good ide to work with virtual servers?

---

### Post by nerdtron on 2013-08-31
> **Arunomi said:**
> When is it a good ide to work with virtual servers?

I say always, if not, as often as possible.
Easy to deploy (and clone), easy to migrate (to another machine), can be disposable (for testing). Plus you can always run 4 or 5 VMs if your hardware can do it.
I'd say it's worth it than configuring multiple services on a single physical install of ubuntu server.

---

### Post by Arunomi on 2013-08-31
So with my Hardware is it even worth trying to set up a virtual server?
For now it would bee three virtual servers.

File server
User Server
Gateway/router

Later I want to upgrade to something like a i5 or i7 intel cpu
and maby 8gb in ram

---

### Post by nerdtron on 2013-08-31
> **Arunomi said:**
> So with my Hardware is it even worth trying to set up a virtual server?
For now it would bee three virtual servers.

File server
User Server
Gateway/router

Later I want to upgrade to something like a i5 or i7 intel cpu
and maby 8gb in ram

I dont' think you need virtual servers in your setup. Virtualization really excels when for example you run a web server, then on another VM a DNS server, another VM mail server. Instead of taking hours mixing them all on a single physical install, just create VM for each and they would be happy.

File server can be easily implemeted via samba or nfs share.
What is a User server? I mean how do you define it?
Gateway/router - I think it can be done via IPtables (i may be wrong)

---

### Post by SeijiSensei on 2013-08-31
> Instead of taking hours mixing them all on a single physical install, just create VM for each and they would be happy.

Taking hours???  If I want to install Apache I run "sudo apt-get install apache2".  If I want to install PostgreSQL I run "sudo apt-get install postgresql".  Setting up an individual VM for each server and getting them all to work together takes a *lot* more time and effort that simply installing multiple packages on a single server.  You'll have to configure those servers the same way whether they are on one machine or many.

There's the "security" argument, that an attack on one service won't bring the whole machine down, just the individual VM.  As I say, I've been running servers for over fifteen years and have been exploited just once, some ten years ago, when I failed to upgrade Apache.  And I run some of the more famously vulnerable software like BIND and sendmail, too.  Modern versions of these are not especially insecure, and making sure you update when security patches are released is the front line of defense.

---

### Post by trundlenut on 2013-08-31
I find the best thing about VMs is being able to create multpile copies and snapshots of specific VMs so that I can experiment and then roll back if (or more likely when) I hose one.  Also by running separate VMs for different tasks you can keep different tasks separate.

At the OP your hardware isn't going to cut it, I have a dual core laptop with 4gb of RAM and it will run desktop Ubuntu + 2 VMs with 1gb of RAM each, but that is it really and your machine probably won't even handle that.

---

### Post by Arunomi on 2013-09-04
If where to upgrade what should I buy?

Whould it do with a intel i5 cpu or do i need a i7?

Or is Amd better?

---

### Post by SeijiSensei on 2013-09-04
> **trundlenut said:**
> I find the best thing about VMs is being able to create multpile copies and snapshots of specific VMs so that I can experiment and then roll back if (or more likely when) I hose one.

I can understand experimenting on a machine that is not in production, and using VMs in that situation makes sense.  But if you're running a production server that needs to be available 24x7, experimenting on that machine creates undue risk.  Hosing a server that is hosting a client's web site or email can result in angry phone calls that I'd just as soon avoid.  In those cases I just want the machine to be reliable and highly available and, once configured, doing its thing without my needing to pay attention to it.  I'm happiest when I don't need to touch a server in production.

---

### Post by CharlesA on 2013-09-04
> **SeijiSensei said:**
> I can understand experimenting on a machine that is not in production, and using VMs in that situation makes sense.  But if you're running a production server that needs to be available 24x7, experimenting on that machine creates undue risk.  Hosing a server that is hosting a client's web site or email can result in angry phone calls that I'd just as soon avoid.  In those cases I just want the machine to be reliable and highly available and, once configured, doing its thing without my needing to pay attention to it.  I'm happiest when I don't need to touch a server in production.

I have to echo Seiji's thoughts. I will be an idiot and play around on one of my VPSes if I am testing things and don't have my other VMs accessible, but it's a bad habit to get into.

Now I test on a VM before pushing changes to production. So far it has saved me a ton of headaches.

---

### Post by SeijiSensei on 2013-09-04
There's a big difference between running servers for yourself and running them for others who are paying for your services.  Here's a currently relevant example for me.

I'm working with a client as we move them from one ISP to another.  I built and maintain a rather complex gateway server that provides a variety of services for the organization, one of which is to forward an Internet-facing port back to the Exchange server inside the client's network.  We could tolerate some downtime for a couple of services like the web site, but the port forward to Exchange has to be rock solid throughout the process.  Why?  Because the CEO likes to read his mail with his iPhone whenever he wants. If that gets interrupted, my colleague at the client's site will hear no end of complaints for days to come. 

That's what life is like in the real world of server administration, and why I prefer to be the outside consultant!

---

### Post by CharlesA on 2013-09-04
I've heard horror stories of things going down after doing updates at work and the CEO getting on the IT guy's butt about it.

Which reminds me that I need to do some updates on our wiki server.

---

### Post by trundlenut on 2013-09-05
> **SeijiSensei said:**
> I can understand experimenting on a machine that is not in production, and using VMs in that situation makes sense.  But if you're running a production server that needs to be available 24x7, experimenting on that machine creates undue risk.  Hosing a server that is hosting a client's web site or email can result in angry phone calls that I'd just as soon avoid.  In those cases I just want the machine to be reliable and highly available and, once configured, doing its thing without my needing to pay attention to it.  I'm happiest when I don't need to touch a server in production.

I agree, I normally setup a new server as a VM on my test machine, making good notes of the setup/configuration, then once I am happy setup the live server.  Also being able to clone a production VM in order to try out upgrades has also saved my bacon in the past.

The OP was talking about setting up his own server(s) and he is going to need to go up the learning curve and VMs offer a relatively safe way to do it.

---

