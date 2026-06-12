---
title: "Recommendations for an Ubuntu tower server set-up for a small business of 20 people"
date: 2015-05-28
forum: Server Platforms
---

### Post by Stephen_White on 2015-05-28
This is my very first post so forgive me in advance if I'm asking in the wrong place or asking the wrong kinds of questions.

I've joined a start-up audio/video company and as the only programmer hired so far the others are looking to me to set up our network.  The company is in Redmond, Washington literally in the heart of Microsoft-ville so there is some bias towards setting up a Windows server, but I've used Unix and Linux in the past and appreciate the flexibility and configurability of those systems.  If I'm going to have to learn to be the network administrator for the time being I'd really prefer to use Linux.  It's been several years since I've worked extensively in Linux (Red Hat & Debian) so I've been investigating current Linux distros and it seems like ubuntu would be the best fit for me.

The company will grow to ~20 employees in a year (currently there are 3).  We will be developing using Mac OS X, Windows and Linux machines.  In the first year we don't need things like a mail server or public website.  We really only need a few things:  firewall protection, a file server, Samba, raid, a way to do back-ups and Apache to host git (and maybe an internal wiki).  The owner is tempted to just go buy a NAS and call that good enough, but those are too simplistic and inflexible.  I think a tower server would be a better first step to set up something more flexible without being too expensive.

I've finished reading _The Official Ubuntu Server Book_ and am currently reading _Linux Administration A Beginners Guide_ as well as scouring the Internet for information on setting up a small business network.  I've got the gist of what software packages I need, but I'm not sure if everything I need can or should be done on a single tower server.  Our first and foremost need is a file server with ~5 TiB usable storage, with Samba, raid 1 and a way to do back-ups, so it seems like that should all go on the tower server.  Our second most pressing need is to use Apache to host git for source code control, which would imply to me I need a LAMP set-up.  Can Apache et all go on the tower server as well or do I need to set up a second machine?  I'm trying to keep initial costs low (i.e.,  < $4,000 USD) so I'm hoping we're still talking the one tower machine here.  And lastly I'm not sure what I need to do about a firewall.  Can that also run on the tower server or should I have an additional PC?  We aren't currently setting up email or a web-site visible to the Internet so I'm hoping that there won't be much to do with regards to a firewall.  I'm hoping our ISP will provide a gateway and I'll just be connecting the hosts and the tower server to the network switches, configure the appropriate packages for the tower server for our needs and be off and running.  Again forgive me if I'm being hopelessly naive, this is still very new to me.

Any advice on equipment needed or on any other subject is GREATLY APPRECIATED.  We're only talking about a year here with mostly file sharing and git for working on source code as fundamental needs.  After a year we can expand to something fancier and more expensive.

Thanks!

- Stephen White

---

### Post by Stephen_White on 2015-05-29
After some research I purchased a Lenovo TS440 70AQ000YUX.  I think I'm going to start out with it set up just as a file server, and I'm going to swipe my daughter's very outdated PC to use as a LAMP server for the web support to host our git repository for now.  I'd rather just use the Lenovo for the LAMP server, but several things I've read recommend segregating the servers, minimally through virtualization, and as a total newbie I'd rather not add the complexity of virtualization into the mix.

If anyone believes I should just go ahead and use Apache to host a git repository on the Lenovo along with the file serving please let me know.

Thanks!

---

### Post by cariboo on 2015-05-29
You asked a question about servers, the best place for this type of question is server platforms

---

### Post by SeijiSensei on 2015-05-29
First of all, Linux like all *nix system, was designed from the ground up to be multi-tasking and multi-user.  Any decent server could handle all the things you mention without breaking a sweat.  There's no reason not to run Apache on the server.  That way you can access the shared directories in any of a variety of ways.

I've not supported Macs, but *nix machines work best with NFS for file service.  Since OS X also runs on a Unix platform, I'd use Samba for Windows machines and NFS for everything else.  You can have both services running in parallel.

You might also want to run isc-dhcp-server and bind on the server unless you're letting your router provide DNS services. You can [configure the two packages]("http://askubuntu.com/questions/162265/how-to-setup-dhcp-server-and-dynamic-dns-with-bind") so the DHCP server notifies the DNS server, bind9, each time it allocates an address to a client workstation.  Then you'll be able to reference the machines by hostnames and add other records to the DNS server for shared servers, printers, etc.  This is a bit complicated to get working at first, but once you get the filesharing part up and running, I'd turn to name service next.

Have you registered a domain?  Does your provider offer email and web hosting services?

---

### Post by volkswagner on 2015-05-29
Virtualize, virtualize, virtualize!

Learning to setup a KVM host will not take much time, compared to the benefit. If you are a development group, having the ability to spin up an instance of Windows or other for testing can be invaluable. The ability to scale and segregate with VM's is great.

If you decide to move web and mail severs to the cloud you can simply ditch the VM(s) after migration. It's nice to be able to clone VM's and create snapshots.

For example it's recommend to keep SAMBA Active Directory separate from file server. This can be done with one machine using virtualization.

For router or firewall get a decent embedded router capable of running OpenWRT plus a quality managed switch. OpenWRT can run OpenVPN for your road warriors or those late night ah ha moments.

---

### Post by Stephen_White on 2015-05-29
Thank you all so much for the advice and info!  I REALLY appreciate it!

Volkswagner, I will read more about virtualization since I totally can see the benefits of going that route, I'm just nervous that as a newbie and as an accidental administrator (only coder current in the company so the hat landed on my head) that throwing virtualization into the mix is additional complication that might trip me up.  I will research it more, maybe snag my daughter's old PC and experiment with trying to set up a machine using virtualization.

Seijispnsei, yeah the server tower we purchased seems like total overkill if all it ends up doing is running as a file server.  It seems like it should easily be able to handle more than just file serving.  I understand that with virtualization you can make it seem like there are multiple PCs on the same PC and thus better utilize the hardware while still keeping things modular (i.e., your web server can't take down your file server), but as I mentioned to volkswagner I've been nervous to go down that route due to the added complexity.

So it sounds like I **should** virtualize but **could** not bother and just run everything without virtualizing.  Thank you both for the advice!!!

And my apologies cariboo for posting to the wrong place. Rookie mistake.

Thanks all,

- Stephen

---

### Post by SeijiSensei on 2015-05-30
Personally I think virtualization is oversold, but that's probably because I've been running servers offering multiple services for two decades now.  Most machines I have built for clients run Apache, bind DNS, an SQL server (usually PostgreSQL but sometimes MySQL as well), and often SMTP and POP/IMAP email with spam/virus checking via MailScanner, just for starters.  Never had much of a problem with them either.  I have a couple of machines that run SphinxSearch as well.

---

### Post by mastablasta on 2015-05-31
you could get Zentyal business/pro version and get some additional support along with a nice GUI.

i wanted to mention one of the small business servers out there, but you already went with overkill machine. anyway now that you have it put it to good use and who knwos maybe business takes off and it won't be an overkill PC in the end.

what was described here doesn't really need that much power. 

for file sharng and colaboraiton - well MS has Sharepoint, while here you might be interested to look at Owncloud. can run alongside, samba, apache etc. you also mentioned this is audio/video company. no tsure what you do but maybe some galeries will come in handy to share material such as Piwigo for example.

anyway if there is a lot of suers it is better to keep things on separate machines, but for a smaller amount of users that actually don't do all their stuff on server - well it can all run on one PC. make sure UPS is there and OS as well as file backups are made regulary and versioned (RAID is not a backup).

Openmedia vault is another nice GUI that runs on Debian - it's ment for NAS but the numebr of official and unofficial modules make it easy to install mayn other things.
Another good admin GUI is Ajenti work on various platforms. Makes it really easy to set up all things you want to setup (well git would porbably have to be done manually).

Two more good servers with UI but Red Hat based are Nethserver & ClearOS (also has a version for companies). just saying it might be easier to maintain if you dont' have to fix every text file individually.

---

### Post by Stephen_White on 2015-06-01
Thanks again SijiSensei.  I probably will just start out running everything on the one machine.  The simplest set-up seems better for me as I'm learning.

---

### Post by Stephen_White on 2015-06-01
Thanks for the great info mastablasta!  I will investigate those things.  Thanks!!!

---

### Post by TheFu on 2015-06-01
IMHO .... 

You don't need/want apache for git.  Git works over ssh.  Get the ProGIT free ebook and setup the shared git repo.

We virtualize everything to abstract HW from the OS and drivers. For almost all uses, a virtual server can be treated just like a physical server after it is setup.

Keep the firewall on a different physical box. A $120 Atom running pfsense is what my security friends suggest. pfsense is used at home and at medium-sized universities as an edge router. 

Of course there are many different opinions about all this stuff.  It is hard to replace experience with book-reading, I'm sorry to say. This is especially true for security parts.  
* [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) - Setting up a new server?
* [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - Learning Linux
* [http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) - System Maintenance for Ubuntu Systems

Volkswagner and SeijiSensei are giving good advice (even when they conflict).  With UNIX/Linux, there is seldom 1 best answer. That flexibility is the greatest strength of the OS family.

I segregate services into different VMs based on security risks, network location and load.  However, if you do virtualize, avoid running **anything** on the hostOS (also called hypervisor or Dom0).

Just because you **can** do something, that doesn't make it the smart thing to do for your situation or that it won't impact overall security.

If you will have remote workers, setup and FORCE openVPN to be used. If your people are technical, use ssh/sftp with keys. Do not allow password-based authentication. There are nice **sftp** clients for every OS that has a network. For non-technical people, it is best to just force that to be used everywhere - even inside the company.

IMHO.

---

### Post by Stephen_White on 2015-06-02
Thanks TheFu!  I've purchased the Pro Git book by Scott Chacon and Ben Straub (yes, I know it is free online but I find it easier to have an actual book).  I'll look into getting an Atom. I've never heard of it.  I'll also read those blogs.  Thanks so much for the help and advice!

- Stephen

---

### Post by TheFu on 2015-06-02
> **Stephen_White said:**
> Thanks TheFu!  I've purchased the Pro Git book by Scott Chacon and Ben Straub (yes, I know it is free online but I find it easier to have an actual book).  I'll look into getting an Atom. I've never heard of it.  I'll also read those blogs.  Thanks so much for the help and advice!

- Stephen

Glad it helps.  "Atom" is a low-power x86/x64 CPU type from Intel. These are "APUs" - that used to mean "CPU soldered onto MB with integrated GPU", basically and all-in-one PC. 15W for the APU+MB+GPU. Just add a case, PSU, RAM and plug it in.

There are many other options on the low end from Via, AMD, etc. The point is to find a cheap x86 CPU that uses low power, but can run Linux or BSD (pfsense).

---

