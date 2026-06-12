---
title: "unlimited network connections to ubuntu desktop 16.04 host ? (vm workstation guests)"
date: 2018-03-29
forum: Virtualisation
---

### Post by jon-g-uk on 2018-03-29
I run various websites on my own windows servers and have recently started testing ubuntu 16.04 desktop on a dedicated computer with a view to running my servers as virtual machines on an ubuntu host with vmware.

I have installed vmware on ubuntu 16.04 and that all works fine and my virtual windows servers etc all work fine. However, I can't seem to find any information anywhere about how many network connections that ubuntu desktop can handle.  My virutal webservers in vmware can handle as many connections as can be thrown at them and I need to be sure that ubuntu will not be a restriction in this.  I am using vmware workstation pro and all virtual guest operating systems are using a bridged network connecting through one physical network card with the ubuntu host machines drivers.

So is ubuntu limited in any way like windows desktop machines are, eg will only accept 10 network connections, or can ubuntu dekstop accept unlimited network connections (fingers crossed it is the latter)

thanks in advance

Jon

---

### Post by jon-g-uk on 2018-03-31
Anyone have any views on this ?  All help is very much appreciated

Thank you

Jon

---

### Post by kerry_s on 2018-03-31
i think your okay as long as your connection can handle it.
as far as i know it's made to be able to use in that manner. from what i've read vm's are the new goto thing for running servers instead of physical hardware, it's the cheapest option & easily managed.

---

### Post by jon-g-uk on 2018-03-31
Thanks for your reply. I've been running vmware on a windows host in this manner for many years, but decided to move to ubuntu for the host but I can't find any definitive information anywhere that states how many connections ubuntu desktop can accept.  As it is open source I'm guessing that it's not limited but it would be good to see confirmation of that from an "official" ubuntu document as I don't want to go ahead and then find my guest webservers in vmware are being blocked because ubuntu can't (or won't) accept all the connections.

thanks

Jon

---

### Post by kerry_s on 2018-03-31
there's a limit of 65336 per ip address, is what it says in my linux admin book.

---

### Post by jon-g-uk on 2018-03-31
> **kerry_s said:**
> there's a limit of 65336 per ip address, is what it says in my linux admin book.

That's interesting.  Which admin book is that ?  I'm quite new to Ubuntu so I'm trying to gather as much performance information about it as I can, particularly networking capabilities (connection limitations etc, if any)

Any help in pointing me in the right direction is greatly appreciated.

thanks

Jon

---

### Post by kerry_s on 2018-03-31
it just says admin gnulinux.
i downloaded a bunch of free ebooks from online to a old tablet i turned into a ereader.
sometimes the titles aren't right or it just says untitled in my ereader app, its running like android 4, so i don't expect much from it. lol

i just googled free linux ebooks. you'll find a lot in pdf form.

---

### Post by SeijiSensei on 2018-03-31
> **jon-g-uk said:**
> So is ubuntu limited in any way like windows desktop machines are, eg will only accept 10 network connections, or can ubuntu dekstop accept unlimited network connections (fingers crossed it is the latter)
That limit of ten connections has nothing to do with technology.  It's simply a method used by Microsoft to collect higher fees depending on the size of an organization.  It's a licensing limit, not a technological one.

No such limits ever exist in the open-source world.  They would be unenforceable. 

I highly doubt that you would ever run up against a connection limit in Linux.  

I can't imagine hosting sites on Windows -- what a waste of money.  Consider dumping them in favor of Ubuntu Server VMs with Apache, PHP, MySQL/PostgreSQL, etc.

---

### Post by jon-g-uk on 2018-03-31
Thanks. I will take a look

---

### Post by jon-g-uk on 2018-03-31
> **SeijiSensei said:**
> That limit of ten connections has nothing to do with technology.  It's simply a method used by Microsoft to collect higher fees depending on the size of an organization.  It's a licensing limit, not a technological one.

No such limits ever exist in the open-source world.  They would be unenforceable. 

I highly doubt that you would ever run up against a connection limit in Linux.  

I can't imagine hosting sites on Windows -- what a waste of money.  Consider dumping them in favor of Ubuntu Server VMs with Apache, PHP, MySQL/PostgreSQL, etc.


Yes, I realize that the 10 connection limit in microsoft windows is a licensing issue not a technical one.  The reason why I asked the question re ubuntu is that I cannot find any "official" information anywhere to give me a definitive answer.

I like the idea of running ubuntu desktop as the host and then vmware with our virtual microsoft servers running on top of that, at least it removes one need for the windows host etc.   I can't move the web applications away from microsoft technology, or at least not for sometime without complete re-writing of the code of which there is a lot.  They are not "websites" in the common use of the vernacular, they are hefty dotnet applications that use iis in windows server, so we have a long way to go before we are completely free of microsoft but that is the goal.

---

### Post by SeijiSensei on 2018-04-01
There is no "official" information because the answer is that there are no limits.  Perhaps that's because no one in the open-source world would expect the software to impose any limit.

---

### Post by jon-g-uk on 2018-04-01
> **SeijiSensei said:**
> There is no "official" information because the answer is that there are no limits.  Perhaps that's because no one in the open-source world would expect the software to impose any limit.

Thanks for your replies.  Sounds like this will do the job admirably.  I will be changing the servers over to the vmware on unbuntu host  in the next couple of weeks.

As I mentioned before in this thread, I am very new to ubuntu so I suppose I'm used to being forced into paying loads of money for access to my own computer hardware :)  

By the way, is the only difference between ubuntu server and ubuntu desktop the gui for the desktop or are there other major differences ?

---

