---
title: "Ubuntu Server unreachable by hostname, desktop resolves fine"
date: 2011-01-03
forum: Server Platforms
---

### Post by Hideaki on 2011-01-03
Hello,

I have a home server running Ubuntu Server 10.10, it is running Samba for file sharing with a mix of Windows and Linux boxes in my house. My main problem is that the server is only accessible by IP or by using hostname.local, but it is not possible to connect to it by just typing the hostname. Further more, it is not being automatically discovered and listed by Windows or Linux clients.

What's really odd is that I also have an Ubuntu Desktop 10.10 install on a separate computer, and that computer is accessible using just the hostname and is automatically being discovered and listed by other computers.

What is missing on the server? What is responsible for resolving just hostname, avahi seems to only deal with hostname.local and that is working fine. I also compared the samba config of the desktop and server Ubuntu installs but wasn't able to find any setting that would be influencing this. Is there some package I'm missing on the server?

Thanks for any help!

---

### Post by woodman231 on 2011-01-03
Does your router detect it without the .local part?

Meaning if you were to go to your router's home page and view your router's DHCP list do you see this Ubuntu server there?

Is Ubuntu running in a VM or is it a physical machine?  If it's a VM be sure it's not NAT'd and ensure that it is bridged.

Thanks,
Sean W.

---

### Post by Hideaki on 2011-01-03
> **woodman231 said:**
> Does your router detect it without the .local part?

Meaning if you were to go to your router's home page and view your router's DHCP list do you see this Ubuntu server there?

Is Ubuntu running in a VM or is it a physical machine?  If it's a VM be sure it's not NAT'd and ensure that it is bridged.

Thanks,
Sean W.

All the systems I described are physical, none of them are virtual machines.

I checked my router's DHCP list and it does just list the hostname, not appending the .local.

---

### Post by cipherboy_loc on 2011-01-03
You could always add it to /etc/hosts. Add a line like what follows:

```
192.168.0.123            ubuntu-server
```

or whatever you want to name it. The first thing is an IP address for the machine, the second is the desired hostname.


Cipherboy

> **Hideaki said:**
> All the systems I described are physical, none of them are virtual machines.

I checked my router's DHP list and it does just list the hostname, not appending the .local.

---

### Post by Hideaki on 2011-01-03
> **cipherboy_loc said:**
> You could always add it to /etc/hosts. Add a line like what follows:

```
192.168.0.123            ubuntu-server
```

or whatever you want to name it. The first thing is an IP address for the machine, the second is the desired hostname.


Cipherboy

I know that's always an option, but I have a large number of computers in my home network, I'd really rather not have to add an entry to every single one of their host files.

---

### Post by kevinthecomputerguy on 2011-01-03
I have had alot of luck with these two steps.
 
1.) If you have given your linux server a static IP address
 
then edit  /etc/hosts         (replace 127.0.1.1  with your Linux boxes static IP address) 
 
*not to be confused with 127.0.0.1, you want to edit\replace 127.0.1.1
 
Here's a printscreen (also shows how to use .localhost and localhost.localdomain properly)
[http://woodel.com/page2_files/image026.jpg](http://woodel.com/page2_files/image026.jpg)
 
2.) Make sure your firewall is allowing ports 137,138,139, and 445.
You probably only need the last two, but as trouble-shooting try all, then narrow it down to just 139 and 445

---

### Post by samosamo on 2011-01-04
I disagree with the poster above me to open ports on your firewall. That is a ridiculous suggestion.

Please provide more information about your DNS server as well as your DHCP server.  Most home office setups have a simple "wireless router" doing all that dirty work so I will assume you can access it via the web config, go to DNS, and add a new record for all your network devices to see?

---

### Post by kevinthecomputerguy on 2011-01-04
Wow
You can disagree til your blue in the face. But you may want to know what your talking about first.
 
Those ports represent samba \ file and printer sharing.
 
He would like to "discover" them by name. Workgroup sharing, Which is a netbios brodcast. Which Will never work if the server he is trying to discover is blocking port 139 and 445.

---

### Post by samosamo on 2011-01-04
> **kevinthecomputerguy said:**
> Wow
You can disagree til your blue in the face. But you may want to know what your talking about first.
 
Those ports represent samba \ file and printer sharing.
 
He would like to "discover" them by name. Workgroup sharing, Which is a netbios brodcast. Which Will never work if the server he is trying to discover is blocking port 139 and 445.

OK Kevin, "the computer guy," you're telling this guy to open insecure ports on his firewall. That's like breaking rule number one. Besides that, the guy just said he is accessing his server via some type of unicast traffic (.local address) so do you REALLY think there is a firewall between his clients and server?

---

### Post by kevinthecomputerguy on 2011-01-04
You&#8217;re a real piece of work &#8220;samosamo&#8221;. It&#8217;s hard to follow your ramblings.

In one sentence you say it&#8217;s not a good idea to open those ports, and then in the next sentence assume there is no firewall. Which would mean ALL ports are open.

Anyway, it&#8217;s hard to have a conversation with you, as you obviously have no idea what you&#8217;re talking about. Do I believe there is a firewall between the client and server&#8230; I hope so, I would firewall my T.V. if I could.

You must have missed a few sentences, or maybe English is not your first language.  I get the impression you think im talking about making changes to the router??? If so, re-read. And maybe educate yourself on Samba and File Shares and Local Area Networking.

This guy&#8230; talking about unicasts on non-routable traffic. A good laugh on a Tuesday morning.
Anyway, hopefully the original poster will not be discouraged by your uneducated ramblings.

---

### Post by cariboo on 2011-01-04
A default server install doesn't have any ports listening, until you start the services. A firewall has nothing to do with opening or closing ports that is the job of the server. All the firewall does is allow/disallow access to ports already opened.

I have to agree with samosamo, the op is behind a router, and the server is running on his internal network, there really is no need for firewalls on systems behind a router, especially if there aren't any ports forwarded to the router.

Please keep this thread civil, as we are all volunteers here.

---

### Post by kevinthecomputerguy on 2011-01-04
No need for a firewall behind a router? 
Ports arent listening unless you install a service?
 
Maybe i need a soda break, but the user already said Samba, so we know port 139 or 445 is needed.
 
And no firewall on your server? really? so he is to trust everyone on his network. He is never going to get a network worm, wow.
 
You guys must not do very many small buisness LAN setups. No disrespect Cariboo907, but i still feel neither one read the original posters question. Your comment about no ports being open on a default install is a strange one, the default install has no services, just a pretty black screen to stare at.

---

### Post by samosamo on 2011-01-04
kevinthecomputerguy, I understand your frustration, please keep in mind this is a highly technical forum and should be treated as such.  You heard the moderator's opinion now please let's get back on the topic.

So like I was saying, I suggest for the OP to configure DNS on his network if it's not already and add a record for this server so other clients may be able to access it by name.  I don't know how firewalls and networking came into the picture??  Oh wait, yes I do...

---

### Post by kevinthecomputerguy on 2011-01-04
Lets see if i can get away with quoting samosamo
 
"That is a ridiculous suggestion."
 
What do i know, i only support 5,000 linux boxes.

---

### Post by cariboo on 2011-01-04
Just so we are all on the right page, from the op:

> I have a home server running Ubuntu Server 10.10, it is running Samba for file sharing with a mix of Windows and Linux boxes in my house. 

In a business setting, things are different then for home use. I wouldn't advise the same thing as I did if this was a business.

---

### Post by samosamo on 2011-01-04
> **kevinthecomputerguy said:**
> Lets see if i can get away with quoting samosamo
 
"That is a ridiculous suggestion."
 
What do i know, i only support 5,000 linux boxes.

What are you trying to prove by telling us that?  You support 5,000 linux boxes but you can't answer the OP's question about just a lonely single one so what are you trying to say?  That you know what you're doing?

I hope you're better at supporting 5,000 linux boxes than you are at fighting with strangers on the internet

---

### Post by Hideaki on 2011-01-04
Woah, I didn't expect this to get so heated >_<

So, there is no firewall running on the server, it's behind a router and only very specific ports are forwarded to the internet.

My router handles DNS in the network, and it is working perfectly fine, as I stated, 2 Ubuntu Desktop boxes(running 10.10) and several Windows ones are all accessible by just using their hostname.
My question is why the Ubuntu Server box is not behaving the same way.
Editing the hosts file on the server with the server's internal static IP did nothing to resolve the issue.

---

### Post by samosamo on 2011-01-04
> **Hideaki said:**
> Woah, I didn't expect this to get so heated >_<

So, there is no firewall running on the server, it's behind a router and only very specific ports are forwarded to the internet.

My router handles DNS in the network, and it is working perfectly fine, as I stated, 2 Ubuntu Desktop boxes(running 10.10) and several Windows ones are all accessible by just using their hostname.
My question is why the Ubuntu Server box is not behaving the same way.
Editing the hosts file on the server with the server's internal static IP did nothing to resolve the issue.

Its not heated really

Output of "hostname" command on your server?  It needs to be configured correctly in order for your router's DHCP to assist DNS, assuming its running dnsmasq or something similar
Adding a DNS record is still an option...

---

### Post by arrrghhh on 2011-01-04
Folks, it sounds like the server just needs to be running avahi...

To the OP, are you running avahi?  It's the automatic "zeroconf" discovery like bonjour.

Otherwise, you'll have to modify hosts files on the clients, as was mentioned earlier.

---

### Post by Hideaki on 2011-01-04
hideaki@Saber:~$ hostname
Saber

smb://saber/ is what I'd like to be able to do, or //saber in the case of windows computers.
It's really not that big of an issue, it's just annoying and inconsistent having most computers on this network resolve to just their hostname but for some odd an inexplicable reason the server needs to have .local appended to the end.

Edit:

> **arrrghhh said:**
> Folks, it sounds like the server just needs to be running avahi...

To the OP, are you running avahi?  It's the automatic "zeroconf" discovery like bonjour.

Otherwise, you'll have to modify hosts files on the clients, as was mentioned earlier.

Yes, Avahi is running and it is resolving to hostname.local instead of just hostname. I think that's the way avahi does things though.

```

hideaki@Saber:~$ ps -ef | grep -i avahi
avahi     1141     1  0 09:50 ?        00:00:00 avahi-daemon: running [Saber.local]
avahi     1142  1141  0 09:50 ?        00:00:00 avahi-daemon: chroot helper
hideaki   3374  3328  0 18:37 pts/0    00:00:00 grep --color=auto -i avahi

```

My desktop gives similar output:
```

hideaki@Yurippe:~$ ps -ef | grep -i avahi
avahi      954     1  0 Jan02 ?        00:00:00 avahi-daemon: running [Yurippe.local]
avahi      955   954  0 Jan02 ?        00:00:00 avahi-daemon: chroot helper
hideaki  24988 24969  0 18:37 pts/3    00:00:00 grep --color=auto -i avahi

```

Yet my desktop is accessible by yurippe, yurippe.local, and its local IP. My server is only accessible by saber.local, and by its IP.

---

### Post by arrrghhh on 2011-01-04
> **Hideaki said:**
> Yes, Avahi is running and it is resolving to hostname.local instead of just hostname. I think that's the way avahi does things though.

Yet my desktop is accessible by yurippe, yurippe.local, and its local IP. My server is only accessible by saber.local, and by its IP.

Interesting.  Well... brute-force (sloppy) fix would be hosts file modifications on all the clients.

As to why it only resolves to saber.local, and the desktop version does not... That's interesting.  I don't have a good explanation, hopefully someone more knowledgeable chimes in ;)

---

### Post by samosamo on 2011-01-05
Avahi is running and that is the reason .local works in the first place.

The hostname looks good.  My next question is, does the server have a static IP set?  If it does you need to set it to DHCP.  If you need the IP to be static then you need to reserve it in your DHCP configuration.

Bottom line is: this is not a problem with your server

---

### Post by FloM on 2011-01-05
Hello,

I don't know if it will work for you but for me worked just fine.
As you, i have a local network on Ubuntu 10.10 with samba shares and windows stations...

My problem was almost the same. I only could access the server via IP address like this \\192.168.0.1 and the server was not listed in my networks.
I have discover that in the new ubuntu 10.10 this line from smb.conf doesn't exist:
```

# netbios name is the name you will see in "Network Neighborhood",
# but defaults to your hostname
   netbios name = UBUNTUSERVER

```  

For me adding that line to smb.conf worked. Now i can access the server via "\\ubuntuserver" or "\\192.168.0.1" and now the server is listed "Network Neighborhood"

Hope it will help you
Good luck
Flo

---

### Post by Hideaki on 2011-01-05
> **samosamo said:**
> Avahi is running and that is the reason .local works in the first place.

The hostname looks good.  My next question is, does the server have a static IP set?  If it does you need to set it to DHCP.  If you need the IP to be static then you need to reserve it in your DHCP configuration.

Bottom line is: this is not a problem with your server

IP is mac address assigned inside the router.


> **FloM said:**
> Hello,

I don't know if it will work for you but for me worked just fine.
As you, i have a local network on Ubuntu 10.10 with samba shares and windows stations...

My problem was almost the same. I only could access the server via IP address like this \\192.168.0.1 and the server was not listed in my networks.
I have discover that in the new ubuntu 10.10 this line from smb.conf doesn't exist:
```

# netbios name is the name you will see in "Network Neighborhood",
# but defaults to your hostname
   netbios name = UBUNTUSERVER

```  

For me adding that line to smb.conf worked. Now i can access the server via "\\ubuntuserver" or "\\192.168.0.1" and now the server is listed "Network Neighborhood"

Hope it will help you
Good luck
Flo

That seems to be exactly what I needed. It's working now. I still can't comprehend why the server needed that but my desktop works without that line...

---

### Post by FloM on 2011-01-05
Glad i could help...

Regarding the other matter...honestly it beats me....maybe because your desktop and your server have the same protocols...

Cheers,
Flo

---

### Post by kevinthecomputerguy on 2011-01-05
Shizzam!
 
netbios brodcast :- ) not DNS
 
*Great work FloM, thats a gem!
 
Too bad there was no firewall, i would be batting a thousand today.
 
I wonder if one setup is Samba version 3, and one is Samba version 4.

---

### Post by habibalex on 2011-11-15
thanks so much, i am a total newbie and this solved my problem.  

I had to install samba first:
sudo apt-get install samba

and then my configuration file was location in /etc/samba/smb.conf

---

