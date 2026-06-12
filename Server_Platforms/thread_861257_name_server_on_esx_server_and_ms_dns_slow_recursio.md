---
title: "name server on esx server and ms dns slow recursion"
date: 2008-07-16
forum: Server Platforms
---

### Post by trmentry on 2008-07-16
I have a very complex issue and I'm needing some help.

Due to the DNS poison cache thing, we need to update our 4 dns servers.  They are currently on SLES 10 and 9.  3 are VMs in ESX enviroment. 1 is a physical box (ns1).  

Our subscription to Novell has expired and we figured why not tech refresh to Ubuntu and save the $$.  So I built a Ubuntu x64_86 VM on our dev enviroment.  It worked great.

I migrated it out over time to become NS2, 3, 4.  I then switched the physical box off and made it a VM as well.  I was told that they had originally had NS1 as a VM but had issues with haivng slow recursion lookups.  So they moved it to physical and it was fine then.  NS1 being the master obvously.  Anyway... didn't seem to have that issue here with Ubuntu.

About 2 hours later after the bring up of the new VMs, we started to get user complaints of 'slow internet'.  Digging into it, looked like DNS was slow to resolve.  

The way our network works, is the following.

Users will send query to a local Microsoft DNS server which will forward to the root MS DNS server for the domain which will forward to the Ubuntu boxen.   The forward between the MS root servers and the Ubuntu boxen was where it was slow.  Queries taking 2-4 seconds to return.  

If we took users and pointed to the Ubuntu boxes themselves, they were fine.  

I backed out and shut down all my VMs and brought the physical NS1 and the old VMs back online and the users were happy.

I honestly can't see this being an Ubuntu issue or a VM issue.  But I suspect something with the 9.4.2-P1 version of bind and MS DNS.  We're only doing around 300 queries/sec.  No where near the 10k saying that there are issues on isc's site.


I've Googled around and not gotten much back.  I'm hoping someone may have some ideas as to what is the cause or if someone has seen this before b/c I feel like I'm loosing my mind.

Thanks in advance.

---

### Post by RealPSL on 2008-07-16
Do you have IPV6 (tunneling) enabled or disabled on the Ubuntu hosts?

---

### Post by trmentry on 2008-07-21
> **RealPSL said:**
> Do you have IPV6 (tunneling) enabled or disabled on the Ubuntu hosts?

um... not sure.  this is a generic install of hardy server and selecting dns server and openssh server during install.

so whatever the default is I'm guessing.   how can I check?

thanks

---

### Post by windependence on 2008-07-21
Why so many M$ DNS servers? One internal and one exteral should be sufficient and they don't at all have to be M$. Windoze won't know the difference.

There have been known cases where M$ stuff was intentionally coded not to work well with other platforms.

-Tim

---

### Post by trmentry on 2008-07-21
> **windependence said:**
> Why so many M$ DNS servers? One internal and one exteral should be sufficient and they don't at all have to be M$. Windoze won't know the difference.

There have been known cases where M$ stuff was intentionally coded not to work well with other platforms.

-Tim


I'm inheriting this mess.  The 4 Linux NS servers are primary for external requests for things like.. [www.company.com](www.company.com) etc.  

The company is a windows show and highly into AD stuff.  MS DNS does work better (IMO) for the AD stuff.  I've seen MS tear up a zone file with all the SRV and what not records.

Anyway... we have offices all over the globe.  Each office has it's own GC server to auth to which is the local dns server for that office.  

I'm highly suspecting this is a MS issue, but can't nail it down.  

I'm trying to see someone else has seen this behaviour and/or has a work around.

Thanks

---

