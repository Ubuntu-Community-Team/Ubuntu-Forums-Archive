---
title: "Virtual Interfaces and Apache2"
date: 2009-08-22
forum: Server Platforms
---

### Post by netlynx on 2009-08-22
I am having an odd problem here, that I think might be a network configuration problem, but may also be an issue with Apache2.  Mabye someone could explain this to me.

I have an installation of Apache2 on my development server, and I have 2 nics.  The first nic (eth0) is configured (and connected to) the local network.  The second nic, is configured to have multiple public IP addresses (using virtual interfaces eth1, eth1:0, eth1:1, etc.)

Now the problem I am having is:
I am pointing my domain name to the ip address 72.xx.xx.20, (which is actually virtual interface eth1:2).  When I try to access the domain address from a web browser (remotely), the response time is very slow.

*however*

If I swap addressess of the virtual interfaces, so that 
eth1 = 72.xx.xx.20
eth1:2 = 72.xx.xx.18

Then the response time is lightning quick.

So as far as I can tell, Apache wants to be on a physical interface (eth1), rather than a virtual interface (eth1:2).  This creates a problem for me however when I add multiple domain names and want different virtual hosts configured on different IP addresses (which is part (not all) of the purpose of using virtual interfaces in the first place).

Also to note the default gateway is only set on eth1 (as it should be), so thats not causing any issues afaik.

Any help in this matter would be appreciated.

Thank you

---

### Post by Adina on 2009-08-22
why don't you use name-based virtual hosts instead of ip-based virtual hosts? wouldn't it be simpler? 

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")

---

### Post by windependence on 2009-08-23
What kind of router are you using and how are you connected to the internet (cable, dsl, etc)?

-Tim

---

### Post by netlynx on 2009-08-25
> **Adina said:**
> why don't you use name-based virtual hosts instead of ip-based virtual hosts? wouldn't it be simpler? 

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")

I am using name based virtual hosts for Apache, that is working properly, *however*, I am using the virutal adapters in order to separate the services 'allowed' on each ip.  For example, I only want access to my mail server on a certain IP, and my DNS server should only respond on a separate ip.  Hence why I have separated the adapter into multiple virtual adapters.

As far as Apache, I have it set up using name based virtual hosts (but even Apache only listens on 2 IP addresses out of 5, even using name based configurations)

---

### Post by netlynx on 2009-08-25
> **windependence said:**
> What kind of router are you using and how are you connected to the internet (cable, dsl, etc)?

-Tim

Hey Tim,

   The current setup (yes I realize insecure, working on it...) is that I have a machine that has 2 nics.  One nic is connected to the private LAN, (connected to a Cisco router (home/wireless router)), the other nic is connected directly to the internet (hence the insecurity, however it is firewalled (packet filtered anyhow, which is still not the best solution yet)..  The connection is (similar to cable, connected via a radio network system) direct connection, not sure what routing they have on the ISP end beyond the radio connection.

   I have 5 public IP's mapped to this machine (adapter), eth1, eth1:0, eth1:1, eth1:2, and eth1:3.

   As I mentioned, if I am allowing Apache to listen on eth1 (through the packet filtering rules), allowing HTTP packets through on the IP address mapped to eth1, it works very fast, however if I open up so it allows packets through on another ip address (say the address mapped to eth1:1), there is a few second (up to 10 seconds) delay before the page opens in the browser.

Thanks
Aaron

---

### Post by terazen on 2009-08-26
I don't have a problem with speed on my server and I've got a similar setup except the default gateway is listed each time.  Have you tried it with the gateway?  Possibly you could run wireshark/ethereal and see if the server is doing anything during the delay you are experiencing.

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address x.x.x.5
netmask 255.255.255.0
gateway x.x.x.1

auto eth0:0
iface eth0:0 inet static
address x.x.x.14
netmask 255.255.255.0
gateway x.x.x.1 up

/etc/apache2/sites-available/filename:
<VirtualHost x.x.x.14:80>
...
<VirtualHost x.x.x.14:443>
...

---

### Post by netlynx on 2009-08-26
> **terazen said:**
> I don't have a problem with speed on my server and I've got a similar setup except the default gateway is listed each time.  Have you tried it with the gateway?  Possibly you could run wireshark/ethereal and see if the server is doing anything during the delay you are experiencing.



Considering you are putting the gateway as the same address for each of the adapters I don't see that causing any 'issues', however the *rule* is only 1 gateway per machine (I am in the process of getting my CompTIA Network+ certification right now).  So if you have 2+ adapters (virtual or physical) only 1 of them should have a gateway (default route) configured.  I am sure there are instances where this rule would/could be broken depending on your network layout/configuration, but that would be a very odd setup.

Regardless, since you are using the same default gateway on all adapters that probably wouldn't cause any problems.  What does your 'netstat -nr' look like, does it show multiple default gateways or just one?  I might try that when I get home tonight.  Also I will wireshark the network and see if I can figure out what is happening (I hadn't actually thought of that, great idea!).

Thanks
Aaron

---

### Post by terazen on 2009-08-26
Here is my netstat -nr:
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
x.x.x.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         x.x.x.1   0.0.0.0         UG        0 0          0 eth0

---

### Post by netlynx on 2009-08-26
> **terazen said:**
> Here is my netstat -nr:
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
x.x.x.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         x.x.x.1   0.0.0.0         UG        0 0          0 eth0

Ok, so yeah, it is smart enough to only put in one entry as a default gateway.  That's what I thought.  Ok, I will give that a try when I get home tonight then as well and see if that helps.  It is strange why other server services such as mail and ftp are reacting quickly to requests, but Apache seems to be the only one having a problem when it is on a virtual interface.  I will try your suggestions and let you know how it goes.

Thanks
Aaron

---

### Post by netlynx on 2009-08-27
> **terazen said:**
> I don't have a problem with speed on my server and I've got a similar setup except the default gateway is listed each time.  Have you tried it with the gateway?  Possibly you could run wireshark/ethereal and see if the server is doing anything during the delay you are experiencing.

...

Hey Terazen,

Ok I tried putting the gateway in all virtual interfaces and it had no effect, and netstat -nr came back with one entry as expected (which is good).  Either way, I have been searching through the logs and I can not find anything that would give any indication of problems.  I have not tried wireshark/ethreal yet, I will try that tonight and see if I can find anything that looks wrong.  Any other thoughts?

Thanks
Aaron

---

### Post by terazen on 2009-08-28
If wireshark doesn't show anything and nothing is in the logs then maybe you could test other applications like ping or ssh to see if the problem is specific to apache or not.

What is in your site configuration file in /etc/apache2/sites-available?

---

### Post by netlynx on 2009-08-28
> **terazen said:**
> If wireshark doesn't show anything and nothing is in the logs then maybe you could test other applications like ping or ssh to see if the problem is specific to apache or not.

What is in your site configuration file in /etc/apache2/sites-available?

Will post my sites-available config file tonight.  As far as other apps, FTP, SSH, Ping, and IMAP/POP3 (postfix/etc), all respond quickly, Apache is the only one that is lagging (and by lagging, I mean 3-4 seconds, not really even a big deal for a test/dev machine, but more irritating.)  I will go back to the config file (and post it for you).  One thing to note though is even the 'standard' sites-available/default is having the same issue (I did not change that one).

On a side note, the sites-available/<config> is just a stripped down version of the default config (set to separate log files and directories).

Thanks
Aaron

---

### Post by netlynx on 2009-08-28
> **terazen said:**
> If wireshark doesn't show anything and nothing is in the logs then maybe you could test other applications like ping or ssh to see if the problem is specific to apache or not.

What is in your site configuration file in /etc/apache2/sites-available?

Well, now I have a little egg on my face, *APPARENTLY* back to the drawing board with my DNS server.  I just did some tests with wireshark and it appears that my DNS is the lag point, not the HTTP server.  I am running two DNS servers, one windows based Active Directory (for my internal lan/domain including dhcp), which will be going away soon anyhow, and then a public DNS server for my development server machine.  Well, it is the windows server that is timing out when it is responding to my laptop.  I changed my dns to the public IP of the development server (instead of using the local domain DNS server), and everything comes up quick.  Another good reason to dump the AD server as I really have no desire to figure out why *THAT* is happening, decomm time.

Anyhow, problem appears to be solved, and never had a thing to do with the development server in the first place.  I wish I had whipped out wireshark earlier in this conversation.

Thanks
Aaron

[side note: that may not exactly be the problem I described above, because now that I think about it, if the AD server was the cause, then I would be having lag issues with all internet addresses.  Hmmm.  Either way, the AD server is going to be decommed this weekend and another Ubuntu server replacing it anyhow (along with other services being moved around), so will see what happens this weekend and I will update you.]

---

