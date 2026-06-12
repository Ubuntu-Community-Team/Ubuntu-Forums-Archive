---
title: "A couple of networking Qs"
date: 2007-06-14
forum: Server Platforms
---

### Post by Pro_D on 2007-06-14
I have had a problem with bind not talking to my win2k server (which I plan to eventually retire) but rather talking directly to the net when bind is enabled.  Based on the following text finally sinking in then I need to add my win2k server as a root-delegation-only entry (or something along that line)?  By not talking to the win2k server I mean that bind wont ask the win2k server's dns anything (most noticeable when trying to browse the local network).

```
// From the release notes:
//  Because many of our users are uncomfortable receiving undelegated answers
//  from root or top level domains, other than a few for whom that behaviour
//  has been trusted and expected for quite some length of time, we have now
//  introduced the "root-delegations-only" feature which applies delegation-only
//  logic to all top level domains, and to the root domain.  An exception list
//  should be specified, including "MUSEUM" and "DE", and any other top level
//  domains from whom undelegated responses are expected and trusted.
// root-delegation-only exclude { "DE"; "MUSEUM"; };

```

Additionally I seem to be having a problem with something called network manager now that I have moved to kubuntu 7.04.  It's apparently a daemon designed to make networking 'just work' but it seems to be breaking things more than making them work.  It seems to be ignoring the domain name retrieved from my win2k server (assuming it is spitting one out).  Additionally I added
'prepend domain-name "mydomain.com"
to my dhclient.conf file (in case the win2k server is the problem) and this too seems to be outright ignored by network manager (based on what I read in the daemon.log file).

So then this leaves me with:
1> How do I fix network manager without resorting to what has been referred to as kludges of adding a script in various places like /etc/network/if-up.d to add in the missing lines (which will then have to be edited should a major configuration change happen).
2> If my dhcp server (win2k or eventually ubuntu's dhcp3-server) is functioning properly and giving all the right information do I even need network manager running?  The win2k server has pretty much always given the right information for a windows box to get online and accessing shares. For the most part older versions of (k)ubuntu and other linux live disks (knoppix) have gotten online and even accessed shares fine.  This install actually has trouble accessing shares (or at least it's not as easy).  If I don't need network manager (ie dhcp/dns and other server network services are configured properly) how do I go about shutting it off since it came pre-installed.  From reading it seems that taking something that was built in out can be a bit of a pain.

Yes the network manager question is more of a client thing but I have the impression that network manager might interfere with other more server related services running properly.

---

### Post by Mr. C. on 2007-06-15
Its tough for me to understand the big picture here.  You have bind, network manager, and netbios concepts all mixed together.

Can you describe your goals a bit more, and perhaps with more concrete terms.  And lets' try to go through the problems one step at a time.

I can start that process with my take on Network Manger.  It tries to be smart, and setup IP for you.  However, in my experience, it has trouble with more advanced setups.  If you are running a server or services, you likely do not want to use dynamic IP information for that server, and hence have little use for Network Manager.  Configure a static IP setup, and Network Manager will not be an issue for you.

Regarding bind - what is it that you are trying to accomlish?

Regarding Windows shares, I'm reading from your description you are having trouble getting your systems to access Windows shares by name.

Please correct and clarify my understandings.

MrC

---

### Post by Pro_D on 2007-06-15
The problem I was having with network manager wasn't exactly network manager, it was a missing semi colon at the end of a line in dhclient.conf.  I missed putting in that semi colon probably 10 different times and I just happen to come across the error in the logs....

Anyway here is how you get a search "mydomain.com" line into your resolv.conf while running network manager and for whatever reason your server isn't giving it to you via dhcp.
Open up dhclient.conf in your favorite editor.
Add in a new line: prepend domain-name "mydomain.com";
-alternately you can use the word supersede instead of prepend which should replace whatever you get (or didn't get) from a server with whatever is in the quotes. dhcp info seems a bit hard for me to come by...
save the file.
restart networking (sudo /etc/init.d/networking restart)
wait....
check your resolv.conf file and the search line should be there.

Of course if the windows server was handing out a domain name with dhcp I suppose this wouldn't have been an issue...

I am now looking at the dns problem again to see if my idea pans out or I get any new ones worth a shot.  I have edited the original bind details to be a bit more specific while removing most of the network manager references:

[mostly original message]
Some details:

eth0 is the nic (wired) connected to the main lan.  Retrieving information via dhcp from win2k server.  This is preferable to a static configuration, when the kubuntu machine retires the win2k system.  As the lan domain isn't public systems on the other end of this wire shouldn't be able to get dhcp or dns information for kubuntu system.  I am fairly confident this is configured properly (based on many howtos and some documentation pages for dhcp3 and bind9).

eth1 is the nic (wired) connected to the mini subnetwork (3 computers including the Kubuntu machine). Static configuration.  This is meant to be the access point through which clients gain access to kubuntu's services, including NAT eventually, but *just* dhcp3-server and bind9 for now.

eth0 and eth1 are on separate subnets, 192.168.1.x and 192.168.2.1 respectively (mask for both: 255.255.255.0).  Currently I am trying to (slowly) simulate if the kubuntu machine was connected to the internet via eth0 but I need to not break communication with the rest of the main lan (through eth0) at the moment.  

> **Mr. C. said:**
> Can you describe your goals a bit more, and perhaps with more concrete terms. And lets' try to go through the problems one step at a time.

My overall goal is to learn about, setup, and test various components on kubuntu trying to setup a machine that will replace the win2k system, without taking the win2k off the network before I and the kubuntu machine are fairly ready (minimize downtime of the network from days/weeks to hours).  The win2k hardware is old and I also don't really want another copy of windows acting as our server anymore having read what I have read about vulnerabilities inherent in pretty much any copy of windows...  Plus, I see now, the lack of deep control left us with a badly setup server.

atm I am trying to get basic network server functions going and the most basic would be dhcp-server and dns (bind) services.  I have most of the desired functionality going with some small amount of confidence that I am not transmitting details out of the eth0 line and so not risking breaking something outside of the eth1 lan.

> **Mr. C. said:**
> Regarding bind - what is it that you are trying to accomlish?

When bind is off and network settings point to the windows server for dns the kubuntu system can ping any computer on the main (eth0) lan.

When bind is on I can no longer ping computers on the eth0 lan from the kubuntu system.  Everything else on eth1 works properly (since bind is the dns server for eth1 attached systems). Internet still works too but it's somewhat slow on first lookups.

Based on some reading it seems that bind isn't even bothering to ask the win2k computer dns questions and since the lan domain is private the internet dns servers don't have an answer either.

I think what is actually going on is that either bind isn't forwarding any questions to the 2k computer or that bind isn't trusting the response from it.  I think that the problem is most likely that it's a trust issue given the quoted text in my first post.  I have a forwarders section naming the 2k computer by IP address...  Of course I may have the concept for forwarders wrong.  I think forwarders are servers that bind should forward a question to if it doesn't have an answer - like for domains it isn't authoritative for like say the internet and in this case the eth0 lan.

Overall I am looking to have bind9/dhcp-server configured to be authoritative for the eth1 domain while caching internet lookups and have dynamic host names added via dhcp3-server (and a key for security), without having all the vulnerabilities inherent in windows.  Granted for the moment I am trying to add some of those vulnerabilities but it will significantly increase the speed of getting this system ready since I am testing as I go...  Besides the possible better understanding.

> **Mr. C. said:**
> Regarding Windows shares, I'm reading from your description you are having trouble getting your systems to access Windows shares by name.

Windows shares - Dumb mistakes on my part (not on kubuntu) and a little lack of knowledge (on kubuntu) (fixed).
Related (I thought) to shares - remote desktop wasn't working, didn't have the all the software - rdesktop package (fixed).

---

### Post by Mr. C. on 2007-06-15
Hmmm, I feel like I'm drinking from a firehose.

I'm sorry, but I just can't follow you, as from my read, components seem to be moving from one net to the next.  I'm not going to try to respond line-by-line, but instead will give you this general guideline:

1) You can setup and test a DNS server on your Ubuntu systems without causing any harm or impacting your existing Win2K or other other systems.  No system will use that DNS server until you configure systems to use it for name resolution.

2) Your DNS server will not cause ping to fail.  You may have intended to say causing host name lookups to fail, as in the command ping myhost.com.

3) You do not need to use a forwarder configuration in your DNS server to resolve some local queries, and forward the rest to Win2k.  This makes no sense, and your guessing at what might be failing is not necessary.  You can configure your Ubuntu DNS server to a) be authoritative for the domains you use, and b) recursively resolve all other queries on its own.  Asking it to forward queries to Win2k, esp. when you are going to retire Win2k is pointless, and needlessly complex.  Simple configure bind to a) answer its own domain's queries, and it will recursively resolve all others.  Only systems which have the IP address of the system which is running bind listed as thier name servers will attempt to use your bind setup.  So configure and test the system as you want it to work, and cut over once it works.  Test your bind server using dig, to be sure your results are what you expect.

4) I will say once again, if you are going to run bind, dhcp, etc. on your Ubuntu system, it must configure it with a static IP to be reliable.  Using a dynamic IP address for such a server is like playing whack-a-mole.  You do not want the IP address of this system changing, as this will affect other systems which are configured to use its services.

5) Prevening one subnet from being able to retrieve DHCP information, or query bind, is a simple configuration variable in each service's config file.  Just configure them to *not* listen on a particular interface.  Your perimeter firewall prevents WAN users from using bind, and DHCP doesn't cross subnets (unless you've configured a DHCP helper).

Specific questions about a configuration or how things work will yield more specific responses.

Best of luck.
MrC

---

