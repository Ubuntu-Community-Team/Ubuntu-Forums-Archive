---
title: "Network settings for VM"
date: 2023-02-22
forum: Virtualisation
---

### Post by rjtt64 on 2023-02-22
Hello

Just installed ubutunto 22.04, on a vm hosted on windows server 2012. The install is set to dhcp.  Ive installed the gui via install ubuntu desktop

I want to set a static ip address, and change the dns server. 

So 
1. I go to settings, network, but all it shows is vpn and proxy, there isnt a list of the interfaces there
2. I go etc\netplan from files, but the file there is readonly to root
3. I try to edit etc/network/interfaces but there is no such file there (which is odd)
4. if I do ifconfig, i can see my ip4 interface there

Any ideas how I can change it, it seems like the gui isnt properly set, its odd that there seem no interfaces


Many thanks for any help you can give

---

### Post by QIII on 2023-02-22
Moved to Virtualisation

---

### Post by MAFoElffen on 2023-02-23
Is this 22.04 VM a Desktop or Server? Desktop networking renders with Network Manager, and Server edition renders with networkd... So different instructions for each...

---

### Post by rjtt64 on 2023-02-23
Ah sorry, its the LTS version from here [https://ubuntu.com/download/server](https://ubuntu.com/download/server) 20.04.1, which is running on Windows server 2012. I didnt realise, if I understand you correclty there is a different flavour for ubuntu desktop\server.

I would add I installed this iso on a physical box too and had the same problem (ie network settings not showing the interfaces), so any advice helpful, I guess its more important to understand how to do it for the physical box. 

Feels quite uncomfortable not even being able to set a fixed ip on a box!!

Thanks for your help

---

### Post by TheFu on 2023-02-23
Networking can be setup as either a system service or something end-users control, at least on desktop installs. On a server, it is expected that the network will come up as part of the OS booting.

If the systems aren't changing subnets and you've setup a VM (I've never seen or used hyper-v), then both the VM host and the guests should be setup by you with static IPs.  In 20.04+ Ubuntu Server, that is handled by netplan YAML files. Here's an example:
$ more 01-eth0-static.yaml  # that's in /etc/netplan/  The name just needs to end in .yaml to be active.
```
network:
  version: 2
  renderer: networkd 
  ethernets:
     eth0:
       addresses:
          - 172.22.22.33/24
       dhcp4: false
       dhcp6: false
       nameservers:
         addresses: [ "172.22.22.80", "172.22.22.81"]
       routes:
         - to: default
           via: 172.22.22.1

```
yaml is extremely indentation sensitive. Use spaces, not tabs.
You'll need to change the ethernet device, IPs, subnets and router/gateway for your needs.  Then run 
```
sudo netplan generate
sudo netplan apply --debug
```
That should move the guest to whatever new IP you've selected. Be certain it is outside the DHCP range.

Use **sudoedit** to edit system files.

It should be obvious that if your VM host configures the VM into a NAT or host-only connection, then it will be stuck.  Most of the time, I use a "bridged" connection for guest VMs, but only you know your needs.

If you are running Ubuntu Server, then there isn't any GUI.  If you've added a GUI, then it is a bastardized system and will never behave like you want, at least regarding networking.  It is a server at the core. There are a few other subsystems that are different between a desktop install and a server install. You picked that, so best not to blame the distro for your choice.  If you want a desktop version with a GUI interface, then download and install a desktop ISO. You'll be happier.

But if you want to learn the CLI methods, forget the GUI now.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a basic text on Linux command line tools.  Because different distros handle package management and a few other subsystems differently, I don't know if that book is current related to Ubuntu Server network config files.  Canonical went their own way around 2018.  This was forced on all Linux distros because the software that was previously used by all distros lost support in 2011 and the replacement tools aren't the same.

While netplan can be used on desktops, most people would use network-manager.  There are lots of different methods, since NM has plenty of different interfaces.  There's an 'app' that can be seen in the DE dock, next to the volume and login/logout controls, there's a full GUI in the system settings, there's **nmcli** which is generally used by scripts and there are the network-manager config files.  I haven't used network-manager in over a decade since it was initially confused by my network setup. It was easier to rip it out and use the same method that servers use (depending on the specific release).  I seldom use wifi, so that wasn't a problem. Most people use wifi and want a GUI to make the connections.

---

### Post by rjtt64 on 2023-02-24
Thanks @thefu for your kindness and very full reply,  theres many basic things I dont know about Ubuntu\linux and its world so thanks for that. The CLI guidebook being a very useful pointer. 

So what I am trying to do is to replace a windows 2012 server which is operating as a DC on my windows + linux NAS network.

Can I check this approach isnt erm flawed. 

So I will set up CLI adminstered hyper V ubuntu server on a VM, with a Samba DC within my windows domain to learn the installation mechanism and prove the concept, before doing the same install onto a physical box and replacing the windows DC. 

Again if you have any pointers for best place to learn how to set up DNS, DHCP, and Samba DC that woudl be appreciated, Im assuming on the ubuntu\Samba websites woudl be the one

---

### Post by MAFoElffen on 2023-02-24
Do you plan to have your Hyper-V VM on the same network as your host? Or test it on another network, so you can test in isolation? If on the same network, setup a bridged network switch in Hyper-V...

What I usually do is use the default NAT switch so that it's on a different network that the host network, and while testing dhcp broadcasts, it doesn't affect the existing machines on the host network.

Based on what I have done with converting 2012, 2012R2, 2016, 2019 and 2022 Win Server DC's to Linux Hosts... What I would do is setup a main Linux Server as a VM, with KVM to install nested VM's... This piece is optional, but help in spinning up new machines for primary / secondary DNS, etc... 

Then about replacing a DC (and making it a replacement for a Windows Server DC / SSSD compliant, think in layers): SAMBA ([https://ubuntu.com/server/docs/samba-introduction](https://ubuntu.com/server/docs/samba-introduction)), Bind9 (DNS) ([https://ubuntu.com/server/docs/service-domain-name-service-dns](https://ubuntu.com/server/docs/service-domain-name-service-dns)), isc-dhcp-server ([https://ubuntu.com/server/docs/network-dhcp](https://ubuntu.com/server/docs/network-dhcp)), Kerberos ([https://ubuntu.com/server/docs/kerberos-introduction](https://ubuntu.com/server/docs/kerberos-introduction)), OpenLDAP ([https://ubuntu.com/server/docs/service-ldap-introduction](https://ubuntu.com/server/docs/service-ldap-introduction))...

Installing Ubuntu server as a Domain Controller: [URL="https://adamtheautomator.com/domain-controller-on-linux/"]https://adamtheautomator.com/domain-controller-on-linux/
[/URL]

Keeping to SSSD compliance, then you can join both Windows and Linux clients to the Domain in a seamless manner...

Overview of SSSD Integration: [https://www.redhat.com/en/blog/overview-direct-integration-options](https://www.redhat.com/en/blog/overview-direct-integration-options)

---

### Post by TheFu on 2023-02-24
OT:
I haven't seen a "Domain Controller" since 2008. Sigh.  Life was so much easier when NIS was used. Too bad that was/is a security failure and NIS+ servers only run on Solaris. NIS+ is considered secure with clients for pretty much every OS.  Nobody should be using NIS since the late 1990s and even then, the security flaws were known.

What I find a little embarrassing is that Canonical doesn't have all local user accounts setup in an LDAP DB with the normal GUI user interfaces available to manage users.  If any network has more than 1 Ubuntu system, they should automatically find each other, have the LDAP servers exchange keys for replication, and ask the admin which will be the master.  Then PAM would be easier and MS-AD wouldn't be the primary LDAP used by Linux systems.  Expecting organizations to use LDIF files as the management technique for LDAP is crazy. So is expecting an organization to download a 3rd party php webapp or java program.  User account management for LDAP needs to be built-into the OS, with C/C++ code.

RedHat has/had a solution for this, FreeIPA, but it is a dumpster fire of 50 F/LOSS projects put together for "Identity Management".  If you want to run bloated software that requires 50 different languages. There are clients for all systems, but the server software port to Debian/Ubuntu from RHEL seems to last about 1 yr before the divergent systems break it.  It hasn't worked since 2018. Sigh.

Downright embarrassing, IMHO.  Especially when in 20.04 Canonical made hooking up Ubuntu Desktop to MS-AD trivial at install time. I actually don't mind that. More flexibility is good and MSFT is the 900 lb gorilla in desktop access controls. Not having a solution for small and large Ubuntu deployments really is embarrassing.  There are a number of small businesses who don't want to run **any** MSFT software, but don't have the technical expertise to follow 10 guides to make their Linux desktops have centralized user account management.

Perhaps **Cockpit** can make all of this easy?  IDK, but it is worth a try.

---

### Post by MAFoElffen on 2023-02-24
I agree that it is not easy. There are a lot of pieces that you have to install and configure to work together. There are no GUI tools to do it remotely like Windows RSAT...

Once implemented, a Windows RSAT workstation can connect to it, but it assumes that it is "Windows Like"... So you can't really make changes "from it". Windows always seems to assume the it is the only player...

My niche, professionally, was getting Windows and Linux to play nice together in the same infrastructure. It is so much easier if all is Windows or all is Linux.

You can use the same server service methodologies in Linux, for Domain, and single sign-on, file sharing, peripheral sharing, etc, and not have it have to connect to Windows Clients in a Windows type manner.

You do not need Domain to connect to NAS.

---

### Post by rjtt64 on 2023-02-25
Thanks again @MaFoElffen and @theFu, for your kindness in taking the time to post these replies. They are very helpful and I am working on your thoughts currently. Just for background my "use case" is I have a windows 12 server and windows network in my home, now windows 12 comes to EOL and I am no longer a developer (Im a psychotherapist now) I dont have free licenses and I face £800 or so for 3 years until windows server 2022 becomes EOL for not very much as its a server that only gives dhcp, dns, file security and radius logins. So I then thought a move to Ubuntu would be cheaper, and also give me some more tech to learn as frankly whilst I do love being a therapist I do miss tech..

---

### Post by TheFu on 2023-02-25
If you haven't been running Linux enough to know the difference between a "Server" and a "Desktop" install, you are really new to Linux.

If you don't really know Linux, the learning curve for what you hope to accomplish will be very steep.  The great thing about Unix systems is their flexibility. The terrible thing for noobs with Unix systems is there is usually 50-500 different ways to accomplish the same thing, with lots of small, but important, choices along the way.

Used to be there were all-in-one distros, like ClarkConnect that tried to be similar to MS-SBS.  Most of those have died out for a number of reasons.  Mainly because Unix people tend to put different network services into different systems, since they are all separate projects with different software stacks.  

In the 1990s, we would load up 10 systems onto the same OS and that lead to "dependency hell" on the system.  Each project team moved forward at different rates, so the underlying libraries needed for each would diverge.  At the time, we'd setup environment variables to access the different libraries only for the specific programs needed. It was a manual hassle.  

These days, flatpaks, snaps, and appimage packaging are all the rage because each addresses that same need, but without the end-users really needing to know. Flatpaks are only for desktop programs, not server stuff.  AppImages tend to be for GUI programs only, so not for servers either.  Snaps are being pushed as the solution to everything, but they come with some constraints/sandboxing that isn't within the control of the local admin.  When you have simple needs, a snap package that does exactly what you need is a good thing.  If your needs to even slightly more than the snap packaging team thinks you need, forgetaboutit. You're screwed.  Also, nearly all how-to guides on the internet don't apply to the snap-package-version of anything.  So instead of 1000 how-to guides, you'll find 2 which probably don't clearly address your needs.  I've found snap guides to be lacking.  They put things in odd places, don't have access to the standard, expected, documented, locations and commands.

Anyways, file security is handled by Unix permissions.  That's the core for all Unix security, so learn that stuff ASAP. Don't avoid it.  For DHCP and DNS, you don't need to use the enterprise software.  You can use a light solution that also provides internet filters for bad domains or advertising - check out a pihole.  I run a pihole setup inside a Linux container and it provides local DNS, but not DHCP.  Another option is to run a LAN router, say opnsense, which provides DNS, DHCP, VPN and Radius.  As long as you don't make it your WAN gateway, shouldn't be too risky.  Definitely have your WAN router only do routing and firewalling. Don't go crazy with "kitchen sink" addons like DNS, DHCP, VPN, RADIUS, and the 50 other things that router software projects have added to their systems - at least not on the WAN router.  

It is really unfortunate that the term "domain" is used, since there have been 20 different types of "domains" in computing for decades and a "domain controller" usually only handles 3.   Sigh.

---

### Post by MAFoElffen on 2023-02-25
> **rjtt64 said:**
> <EDITTED>
I have a windows 12 server and windows network in my home
<EDITED>
its a server that only gives dhcp, dns, file security and radius logins.

It sounds like you do not actually need anything that fully covers SSSD and an integrated enterprise type solutions, but rather a few "server services"... dhcp, dns, filesharing and OpenRadius. The later being optional, because it could just be tightening up your basic home wireless network security. 

It's just in a home-office solution, correct?

I have CISCO experience, so networking to me is just "Networking." It is a layer in the overall infrastructure. The go-to for Linux and Windows file sharing is Samba. DNS and DHCP services can be handled as Linux Server services... It doesn't need to be that complicated.

In the past, for small business solutions, I used to recommend "Zentyal Server" ([https://zentyal.com/community/](https://zentyal.com/community/))... Which is a small business server type of distro, based on Ubuntu, with an HTTPS GUI Desktop. Lots of scripting to make Linux Server services simpler for non-technical users. They have a community edition that is free. That may fit what you are trying to do, and make things much simpler, with a shorter learning period.

You could test it for free to see if it fits what you want to do. Info on migration from Windows Server: [https://zentyal.com/migration-from-windows-server-to-zentyal/](https://zentyal.com/migration-from-windows-server-to-zentyal/) ...Then look into whether you need a commercial license for your business.

EDIT: Don't overlook backups and disaster recovery... Important to "all".

---

### Post by rjtt64 on 2023-02-26
Thanks again @MaFoEllen. Yes Its a home office network, and youre right a simple solution is all thats needed, I use AD very little. I guess in terms of solutions having all the network services in one place, is one important aspect. Thanks for the pointer to Zentyal, I had original tried univention in the same space, but I couldnt get a windows client to be added to the domain, inspite of a fair amount of work.  I think now Im involved with Ubuntu, I might see if I can get this solution working, although like someone said before there is much learnign to be done!

---

### Post by rjtt64 on 2023-02-26
Could I ask what a good way to test a DHCP server, the environment is the ubuntu dhcp server Ive just set up is in the same subnet as 2 other dhcp servers, Ive used nmap but it is giving the results from anotehr server  (ive turned the other servers off and confirmed this to be the case

Output  and configs below

```
~$ vim /etc/dhcp/dhcpd.conf
ddns-update-style standard;
authoritative;
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.150 192.168.1.200;
  option domain-name-servers dc1-server.robhome.com;
  option domain-name "robhome.com";
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}


rob@dc1-server-ubuntu:~$ sudo nmap --script broadcast-dhcp-discover -e eth0
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2023-02-26 15:00 UTC
Pre-scan script results:
| broadcast-dhcp-discover:
|   Response 1 of 1:
|     IP Offered: 192.168.1.99
|     DHCP Message Type: DHCPOFFER
|     Subnet Mask: 255.255.255.0
|     Renewal Time Value: 30m00s
|     Rebinding Time Value: 52m30s
|     IP Address Lease Time: 1h00m00s
|     Server Identifier: 192.168.1.23
|     Router: 192.168.1.1
|     Domain Name Server: 192.168.1.23, 192.168.1.29
|     Hostname: robhome.com\x00
|_    Domain Name: RobHome.com\x00
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.45 seconds
```

---

### Post by TheFu on 2023-02-26
When posting terminal output here, please use the forum's 'code tags'  That's in the advanced Reply ... or just use 'quote tags' and change the beginning and ending "QUOTE" to "CODE" - these are case insensitive.  Code tags preserve whitespace, so columns line up correctly, just like in a terminal.

That **nmap ** command and output seems to have the wrong hostname and the trailing hex'00' in the hostname/domainname isn't what I'm seeing here from my DHCP server.  

Also, 1 hour seems much too short of a lease for a home network.  I use 1 day, since I limit the number of guest devices on that subnet to 10.  

Using DHCP reservations to manage static IPs may seem like a good idea, but it is prone to failures that can really suck. With longer lease times, that risk can be mitigated, but if you configure the static IPs locally on the system, as God intended, DHCP issues won't happen.  I've seen entire office buildings with 2K people lose networking because of DHCP issues. That company was 50% MSFT and 50% Unix, but the DNS/DHCP was 100% MSFT.  Remember that DHCP and DNS are 2 separate network services on Unix systems. they aren't tightly coupled like MSFT does it.

And of course, ensure that any static or DHCP reserved IPs used are outside the dynamic DHCP address ranges for guest devices.  I only use DHCP reservations for devices where setting static IPs is impossible or very hard, but I want every device to effectively have a known IP so internal firewall filtering can be performed.

---

### Post by rjtt64 on 2023-03-01
Hi 

I dont suppose anyone could help with this, I cant ping my domainname against these settings so > ping daniellandrob.com  doesnt return the correct ip address. I would add a standard ping bbc.com does return the correct address so at least I know the forwarders are working

```

this coming from /etc/bind/db.daniellaandrob.com

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     daniellaandrob.com. dns.daniellaandrob.co.uk. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      daniellaandrob.com.
@       IN      A       192.168.1.21
@       IN      AAAA    ::1
ns      IN      A       192.168.1.21

```


Many thanks

---

### Post by TheFu on 2023-03-01
perhaps I'm missing something, but don't you need a hostname before the domain for DNS to work?  Typical DNS aliases for hostnames are www, mail, smtp, gopher, ns, www2, www3.

The expected FQDN is {hostname}.{domainname} ... so [www.daniellaandrob.com](www.daniellaandrob.com).

I haven't used bind in a few decades.  O'Reily makes a book about it, which was excellent last time I needed it.  I rate books excellent when I'm able to find the information I need in less than 15 minutes, solve the issue, and never need to see it again. ;)

There are other DNS options, BTW.  Bind is the Fortune 10 version.  Maybe you want the small-business version instead, which dnsmasq can do using a file very similar to the /etc/hosts file.

---

### Post by rjtt64 on 2023-03-01
Thanks @TheFu, Im used to (Msoft) DNS servers returning ips for domainnames, hence I tried it on linux. Thanks for the book recommendation and I like your strategy of 15 min books! I would add I do love the ubuntu documentation really clear. I will have a look at dnsmaq too as I have 2 users ! Many thanks

---

