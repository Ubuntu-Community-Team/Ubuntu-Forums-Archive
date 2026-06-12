---
title: "To virtualize or not?"
date: 2015-04-15
forum: Virtualisation
---

### Post by Tadaen_Sylvermane on 2015-04-15
[COLOR=#000000][FONT=Verdana]I have a small AM1 server I built awhile back. It currently is running Ubuntu 14.04.2 headless in the closet. The install is nothing more than a kvm host, and I have been virtualizing everything I do. This was done for learning as well as I found it easier to have single systems (vms) that do one job as opposed to one system doing multiple jobs.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I am beginning to rethink this though. I can't help but think I am making more work for myself to keep multiple vms updated, performance penalties for vms as opposed to bare metal ( minecraft server comes to mind).[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I guess my question is at what point does virtualization make more sense than single machine for a home server.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]My uses - file server, torrent seedbox, apt-cache-ng proxy, minecraft survival ( 4 players max, lan only ).[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The server is not high powered is another reason I am looking for advice. AM1 Kabini 5350, 8gb memory, 120gb ssd, 1tb hdd.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What is my best option?[/FONT][/COLOR]

---

### Post by redger on 2015-04-15
have you considered LXC ? It's a much more light-weight virtualisation approach (containers based on the host OS) with many of the management and isolation benefits of KVM. Potentially lower security ... particularly for internet facing machines

I use separate LXC VMs for mythtv-backend, browsing and data shipping

I use KVM for high security financial transactions, windows machines and anywhere I need high security .... and can accept the performance overhead.

my machine hardly notices the overhead of the LXC VMs .... whereas KVM machines are definitely noticeable

I mostly deploy "unpriveleged containers" .... see this link   [tps://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/]("tps://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/")

Whilst there's still an operational and management overhead, you still get the flexibility of isolation and much much easier snapshotting (LXC is incredibly easy) for roll-back / forward

---

### Post by Skaperen on 2015-04-15
automate things or script what you want to do manually ... for example i have a script called "upgrade".  this way whether you choose LXC or VMs you can do stuff faster and still be in control.

---

### Post by TheFu on 2015-04-15
If you want to automate patching, but still retain control, use a script that ssh's into each system/VM to do the patching. A simple loop is all it takes, plus setting up ssh-keys, using ssh-agent and setting up sudo to allow your deployment userid to run apt-get update and apt-get dist-upgrade without a password prompt. sudo supports limiting non-passwd commands to specific things.

Or use ansible - takes about 40 min to learn enough to run any command on 1-20,000 systems.
**ansible -i hosts -a "cat /var/run/reboot-required" all** or something similar. Of course, ssh-keys should be setup here too.

Can't talk about whether you should virtualize or not.  I wouldn't on less than a 1st-gen C2D with 4G of RAM - I think your CPU meets that performance.  Most of my home VMs run on a Core i5 w/ 16G. Just replaced an cheap AMD-E350 APU with a Intel G3258 CPU and 8G of RAM - it should perform well as a home KVM server running Plex server, mythtv-backend, and a few network services like DNS, NFS, NTP for the internal network.  I prefer to virtualize services, but not storage.  The VMs only get enough storage to run the apps. If more storage is needed on a box, there's NFS.

Some services need to be on dedicated hardware, IMHO.  I'm old-school that way.  Routers, VPNs, edge firewalls, PBX.

LXC is a great option for systems where you don't need much security. It is just too immature to trust for anything sensitive, IMHO.  Perfect for spinning up a dev container or trying out a new service or for internal-only services.  Containers work on any CPU, no vt-x/amd-v requirement.  I don't have much experience with it beyond playing. 

Came across this:
> You are absolutely deluded, if not stupid, if you think that a worldwide collection of software engineers who can&#8217;t write operating systems or applications without security holes, can then turn around and suddenly write virtualization layers without security holes. [http://marc.info/?l=openbsd-misc&m=119318909016582](http://marc.info/?l=openbsd-misc&m=119318909016582)

---

### Post by redger on 2015-04-16
first off ... what do YOU see as the benefits / costs of virtualisation

secondly, lets not get too carried away with security .... you can easily chase down a rabbit-hole with no material improvement. Linux security posture is very good [http://www.gfi.com/blog/most-vulnerable-operating-systems-and-applications-in-2014/]("http://www.gfi.com/blog/most-vulnerable-operating-systems-and-applications-in-2014/")   [http://en.wikipedia.org/wiki/Security-evaluated_operating_system]("http://en.wikipedia.org/wiki/Security-evaluated_operating_system")
more importantly risk = probability * cost   (actually a statistician would say that is "expectation") .. so ask yourself what the cost of a security failure would be. Frankly I am a whole lot more concerned about my ISP supplied router opening back doors than I am about any of the mutliple linux systems in my environment .... even the windows environments don't worry me that much - partly because I am very careful with browsers and email agents (the major application risk factors).
I'm a bit over spending the last "many" years talking security architects down into pragmatic reality (no offense to other respondents) ... it seems to me that anyone who even considers security issues is already ahead of 95% of the computer using population and a few basic precautions will keep you pretty safe. As exposed in the Snowden papers ... there is no way to secure against a determined state (/well resourced & determined) hacker. The questions are (a) why would they bother (b) what would they gain (c) what is the cost to you (d) how do they do it ie. the "infection" vectors (e) what can you do about it and (f) what would it cost. It seems the major risk vector (probability) for most people is their browser and browsing behaviour (assuming a basically secure modem-router). Control that and a high proportion of your issues go away. Secondly (for risk vectors) look for acceptance of incoming connections eg. FTP server etc - it seems like you have the single torrent seed-box - for which KVM is probably appropriate for it's higher levels of security and isolation.
It's worth noting that the big service providers (IBM, HP, CSC etc)  do not instantly react to all security notifications. Even major ones (like heartbleed) are not necessarily addressed "instantly" and I treat my servers the same way. Patches may be applied every few months - if there is a clear benefit .. otherwise I value stability (and ease of management) over currency.

Thirdly - for maintenance, what do you want to do, how often and why ? Most "service" machines/VMs only need high impact security updates or functional updates offering a high benefit ..... neither of which come along all that often. Remember that any change brings with it the chance of a failure .... and sometimes failures occur in very odd ways and in odd places. Working "service" capabilities are best left alone unless there's a very good reason to change them - to minimise the chance of failure. Required maintenance eg. high impact security updates are quite predictable and can be scripted as discussed above ... if you want to make life easier. For reference there were only 2 situations last year for which I applied "emergency patches" and that was unusually high.

I like virtualisation for -
- Isolation - failures and changes in one environment / service are insulated from other environments (other than the host). I have taken the view that security is also enhanced since I don't know there are any "consumer" exploits targetted at either breaking out of VMs to the host or "jumping" from one VM to another (also if you're using unpriveleged containers exploits are relatively benign since priveleges are all at the user level not admin)
- Reliability - a stable, unchanging, "minimalist" host need not be changed or rebooted for long periods of time which enhanced the stability & reliability of the guest VMs
- Management - I can start and stop a single environment / service without impacting others. Resource allocation can also be ramped up and down easily. The nature of the start-stop also re-initialises resouces like a reboot which is convenient.
- "Testing", or more appropriately "speculative upgrades / changes" - It's much easier to take a snapshot of a VM prior to upgrades (or significant changes), make the change, run it for a while and if necessary revert to the snapshot. This can be done with a physical machine, but it's a whole lot easier with a VM. Yes this is an aspect of operational manageability but I like to list it separately ;)
- Density - I used to run multiple physical machines 24*7 and a others occasionally .... now I'm down to one machine 24*7. That saves a lot of space, electricity and hardware cost (for replacement / upgrades etc)

I won't go into continuity and load balancing / load distribution via VMs because they're a bit advanced (I certainly don't do anything like that in a home environment) and I doubt they're an issue for you.

NET ... in your situation I would go for 
[LIST]
[*]torrent seedbox - KVM Ubuntu guest for isolation & security
[*]file server - If this is really Samba services for LAN clients I would run it on the host or possibly LXC unpriveleged container (assuming you're not using NFS). If it's an FTP server for internet clients run as a KVM machine
[*]apt-cache-ng proxy - Run on the host. If you need isolation use an LXC unpriveleged container. The presence of this service suggests more complexity in your environment i.e. multiple other servers on the LAN
[*]minecraft survival ( 4 players max, lan only ) - LXC unpriveleged container
[/LIST]

Other suggestions ? Discussion ?     it would be interesting to hear other views ... and why

as you may have guessed I have become a big fan of containers .... particularly when run as "unpriveleged" ie. no root access, all operations run as a normal user unless a high level of security or hardware access is required (eg. passthrough)

---

### Post by TheFu on 2015-04-16
I think I agree with everything redger wrote, except tht being aware of security considerations puts you ahead.  Action is necessary.  I've had 2 servers hacked over the years. Once on a government network, the next time here because my bind version was 2 months behind on patches.  The last time was in 2002. Since then, I've been paranoid, yes, that is the word.

We don't patch anything immediately - even emergency patches. Before we deploy any service, we consider the attack vectors and make a decision based on the likelihood of that service being hacked.  For example, we will NOT run any php-based systems directly on the internet. If we need a php-based solution, it can run internally and be accessed only though the VPN.  That decision alone stops most of the widely used attacks from the internet.

Emergency patches often are flawed. By waiting a day or two, we get the "good" patch. We may take mitigation steps at the firewall to prevent the attack vector, but that isn't usually needed. For internet facing services, weekly patching is our goal. The back-end services tied to those may take longer. Just depends on the risk.

We are also religious about daily, versioned, backups.  When trying to figure out what a attacker did, nothing is as useful as being able to compare the running system with a backup from yesterday, last week, last month and perhaps 3 months ago.

We have a design philosophy to control ingress and egress points to the network.  That means front-end servers and reverse proxies are used for web, email, and ssh traffic.  VPN gets a dedicated box. Higher risk items are on physically separate networks from other services, each with a firewall.

You'll not that none of these methods say anything about virtualization or containers.  Those are just tools to be used when appropriate.  We virtualize everything here, except those "key service" items listed above. If there is a failure, I want it to fail-closed, not fail-open.

I'll probably migrate more internal-only servers from KVM to LXC over the next few months.  However, nothing can replace time as a method of proof for any solution's security.  After all, every OS has bugs that were introduced 20 yrs ago and aren't publicly known today, but are likely being used.  The trick is the reduce the vectors available to the "bad guys", so those flaws don't matter AND after they get in, what is the plan to recover the services and ensure data hasn't been corrupted?

1 last example - when I moved to a new company they had a small, public website, just for customers to see we were "real" - nothing of much use on that site at all. Not even hosted on our equipment - fine.  Sad down with the CSO and CEO to explain our plan for what we'd do after it was hacked and defaced.  The CEO started yelling.  If we knew it was going to be defaced, why not just stop that?  We explained it was impossible. A determined hacker would get in and could deface the website.  Our plan was to have a backup website with all the static content available on read-only media and just switch the DNS pointers over to the new website immediately. Then we'd work on solving the real issue with the main website and take appropriate steps to capture data about the intrusion, determine, if possible, who had done it and hopefully discover the whole they had used.  But first job was getting the corporate website back online with next to zero chance of another attack succeeding.  It is hard to hack a read-only NFS mount - just sayin' - though they could being down the data connection f they got into the newly stood-up website.

---

### Post by Tadaen_Sylvermane on 2015-04-17
> [COLOR=#000000]NET ... in your situation I would go for [/COLOR]

[LIST]
[*]torrent seedbox - KVM Ubuntu guest for isolation & security
[*]file server - If this is really Samba services for LAN clients I would run it on the host or possibly LXC unpriveleged container (assuming you're not using NFS). If it's an FTP server for internet clients run as a KVM machine
[*]apt-cache-ng proxy - Run on the host. If you need isolation use an LXC unpriveleged container. The presence of this service suggests more complexity in your environment i.e. multiple other servers on the LAN
[*]minecraft survival ( 4 players max, lan only ) - LXC unpriveleged container
[/LIST]


I couldn't check out the thread for a bit so I went and bare metaled all of the services on the same host. However after reading everything here I have a much clearer understanding of pros and cons. I will likely move the torrent box back into a vm, file server and apt-cache-ng will stay on the host. The reason for the apt-cache-ng server isn't complexity as much as I use *buntu or derivatives for a few desktops / laptops in my house. My internet where I live is quite expensive and terrible, download speeds are horrendous usually so I cache the packages that way I need only download updates once and I have them for all my machines. I will look into containers but for now the minecraft server is running bare metal as well and I have noticed an exponential improvement over its performance as a vm. Before it would lag out quite often with only me playing on it.

---

### Post by TheFu on 2015-04-17
Just a thought for better performance: 
Have you disabled disk buffering in the clientOS settings if you use file-based VM storage?  Only 1 (the hostOS or clientOS) should do disk buffering.

---

