---
title: "Business server solution"
date: 2010-06-01
forum: Server Platforms
---

### Post by srivo on 2010-06-01
Hi,

I'm looking to use ubuntu server for a small business. I have a few idea but would like to know what other are doing for business solution.

My first tough is having 2 servers running different VM to serve business need.
Basically what I need is:

[LIST]
[*]DNS server (VM)
[*]Samba server for files and print (VM ?)
[*]email server (VM)
[*]Alfresco community (VM)
[*]KVM for VM
[/LIST]
Would it be a good idea to run ubuntu cloud? How should I slip those different VM among the 2 servers?

Thanks

---

### Post by Vegan on 2010-06-01
One server can handle all of those jobs if its running on bare metal.

My old machine runs a whole boatload of stuff.

---

### Post by v1ad on 2010-06-01
i agree that is a small load for any machine.

---

### Post by spynappels on 2010-06-02
And look at VMWare ESXi as a bare metal Hypervisor. If you want each of those tasks to run in a separate virtual machine, that will work just fine.

I have 5 virtual servers running on a HP ProLiant ML110 with 4 GB of RAM, and one of those is an Alfresco Server and I'm not even slightly maxing out the hardware. Just give the Alfresco VM a bit more RAM for better performance.

---

### Post by HermanAB on 2010-06-02
Howdy,

Two tips:
Always, always, always install a Business server on a Virtual System.  It makes it a whole heckuvalot easier to migrate it to new hardware one day when the inevitable happens.

Rather create separate VMs for complex functions such as DNS, Samba, Web and Email.  Again, the reason is that it makes it easier to migrate any one of these services seamlessly to new hardware.

So, either install ESX or do a minimal install with Virtualbox or VMware Player and then install your server VMs in that.

Yes, it is somewhat less efficient, but in a year or three you will thank me for pointing you this way.

---

### Post by srivo on 2010-06-02
Alright, so what I understand from now is that one good server can handle all of this load. The second server was more redundancy in my first idea. But this is not mission critical at this stage of the company.

Thanks every one

---

