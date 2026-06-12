---
title: "Home Server Possible?"
date: 2009-06-05
forum: Server Platforms
---

### Post by SykoFerret on 2009-06-05
I was wondering if this set up is even possible. I'm new to linux and netwroking., but I'm a quick learner. 
I was wondering if it is possible to set up a server that basically runs my entire network. I would like the setup to be Modem-->ubuntu-server-->Netgear wireless N router-->windows clients (also bridge to linksys wrt54g ver2 using dd-wrt). I would like to have the dhcp, dns (with individual user/group login/pass for filesharing, but the machine will not host files.), also as a jabber im server(LOCAL only) and a nice freeware firewall. any ideas for a beginner where to start? I have successfully installed webmin after a few hours. and that's where I'm at. any advice would be greatly appreciated.
 
**Overwhelmed**

---

### Post by uberlube on 2009-06-05
Sure its possible. Of course u have to choose your flavour. Check into openSSH, might be a good start for you.

---

### Post by SykoFerret on 2009-06-05
I have successfully logged into webmin using ssh but i dont have a second NIC yet for the server so 
i'm just using dhcp on the router.
webmin looks more confusing than command line. lol.

---

### Post by uberlube on 2009-06-05
why do u need a second NIC?

---

### Post by SykoFerret on 2009-06-05
right now the server is plugged into the router. It would make more sense to have it in between the modem and the router, due to the need for a firewall. or is that unnecessary?

---

### Post by uberlube on 2009-06-05
Yes and no. IMO i would leave it where it is seeing as how it is just a home server. If this were an enterprise server then sure. Im not really an expert on the subject but if u just have a few trusted machines connecting from within your internal network then theres no real need to go all out.

---

### Post by SykoFerret on 2009-06-06
well. atm it is only a server fo 8 machines and 3 phones. but in the next couple months my network will cover the whole block. I'm estimating 50-70 machines. And there are some specific machines I want to share files with via active directory and I dont want others to just be able to run a network setup wizard and access those files. And the added security will prevent any harmful files bollixing up my networked machines.
I could always add a hardware firewall in the future though.

---

### Post by uberlube on 2009-06-06
K forgive me but i need more info to try to understand what u are doing.
1)The whole block? u get around dont u lol.
2)3 phones? how are these being used by your network. Are they dialup modems?

---

### Post by SykoFerret on 2009-06-06
The phones are WiFi enabled. And basically the vision in the long run is to have the server run a domain, and dhcp, as well as a firewall, and possibly later down the road TOR and peerguardian for some users who prefer "anonymity". but for now just a domain a few static ip's and a firewall. with room to expand. and of course password protected filesharing between clients, without hosting files on teh server.
and i'll be using dd-wrt on a bunch of linksys wrt54g routers to basically lay a mesh over the area.

---

### Post by uberlube on 2009-06-06
Ah i c. I dont even know why WIFI phones didnt come to mind, lol. Well you are on the right track. All u really need to do from here is keep trying out which type of server u like best and do what u can to make it secure. Here is some sites and reading material that u may find interesting:

[http://www.dyndns.org]("http://www.dyndns.org")
With ISP's randomly chaging your IP address, this is a must to run a server.

[https://help.ubuntu.com/7.04/server/C/openssh-server.html]("https://help.ubuntu.com/7.04/server/C/openssh-server.html")
openSSH documentation from Ubuntu

[http://www.pureftpd.org/project/pure-ftpd]("http://www.pureftpd.org/project/pure-ftpd")
If u wish to go with an ftp server this is great for beginners. Also has a nice GUI for the admin to set up accounts and maintain the server(pureadmin).

---

### Post by uberlube on 2009-06-06
[http://ubuntuforums.org/showthread.php?t=1046738]("http://ubuntuforums.org/showthread.php?t=1046738")

Another good post from a guy that has all the answers.

---

### Post by SykoFerret on 2009-06-06
awesome thx 4 the linx. Definately appreciated.

---

### Post by SykoFerret on 2009-06-06
ok. now I have a dyndns registered. how do i set it up in th dhcp and dns in webmin )or command line)

---

### Post by uberlube on 2009-06-06
you have to log into your router (192.168.1.1) and point it to your DNS. After that the people that access your network will just have to enter the domain name that u chose in dyndns (as well as their password). The nice this about this as well is that it gives u an extra layer of security, you wont have your actual IP address floating around all over the place.

---

### Post by SykoFerret on 2009-06-06
ok my router support dyndns so i punched in my info and that's working. I disabled the dhcp on my router and tried to join the domain on a windows machine and i get the error the domain controller doesnt exist.

---

### Post by uberlube on 2009-06-06
is this windows machine on your internal network?

---

### Post by SykoFerret on 2009-06-06
yes. and I haven't configured dhcp on the server yet I think the pcs are still using dynamically assigned addy's from the router.

---

### Post by uberlube on 2009-06-06
ya that was going to be my suggestion was to log into the server from the address assigned from the router. The dyndns address is for outsiders from your network. Have u tried this yet?

---

### Post by SykoFerret on 2009-06-06
atm i dont have a way to test from outside the network so i will asume it's working. now for the local dhcp, i need to create a subnet or shared network? or i guess a host?

---

### Post by uberlube on 2009-06-06
"While it is strongly recommended that DHCP be used wherever possible, running a local DHCP is generally not recommended except in the case of remote sites or when a special DHCP server is needed, e,g, rembo. The rationale is:

    * the computers in an org-unit should receive static ip-addresses, ie dynamic pools are either small pools to support visitor computers, or for environments when when any computer can be plugged-in (e.g. wireless or the MBBS learning rooms)
    * unless an org-unit is running it's own DNS in cooperation with Central DNS, there seems little point in computers having to be entered both in WebDNS and in the configuration of the local DHCP server

When a local DHCP server is running, it doesn't need to directly interact with Central DHCP but hosts receiving static ip-addresses need to be correspondingly registered in WebDNS."

I just found this while looking up what you are trying to do. Im still a little confused. What type of server are u running, is it an ssh?

---

### Post by SykoFerret on 2009-06-06
i dont need it to be except for local. I'll be using a 3rd party program on a filtered port to do any remote managment. I could remote to this machine and just run webmin from this machine to make any mobile changes. I don't know much about networking but figured dns is synonymous with active directory. it would be preferable to auto deny all clients except those I add via MAC addy.

---

### Post by uberlube on 2009-06-06
I think you might be going about this the wrong way. especially with webmin. All you should really have to do is add users as explained in the documentation and manage what they can and cant access through there. To make any changes from anywhere u sould really only have to log in as the servers superuser. Or am i off the mark? Again what type of server are u running?

---

### Post by SykoFerret on 2009-06-06
I want it to manage usernames and passwords for network file access, and assign static IPs by MAC, and have a local jabber IM server so I can IM other network users. I can set up another server to manage the firewall and external dns at a later date. so basically I want to run filesharing, and use the server for acces management to the local pc's files. and have the server assign the same local ip to individual users everytime they connect. And Have an IM client to connect with users for support, and local remote acces to users. webmin is really only to avoid the command line.

---

### Post by SykoFerret on 2009-06-06
for example: user at MAC 1 is assigned ip 1 and wants a file from MAC 2 at IP 2 he has access to folder 1 and 2. but user at MAC 3 at IP 3 has access to only folder 1.
where each user uses their personal login name and password to access the files.

---

### Post by uberlube on 2009-06-06
OK thats more specific.

"I want it to manage usernames and passwords for network file access, and assign static IPs by MAC"

Ok im sure its a great tool for doing all that once u learn how to use it, although i dont believe its necessary to assign people static IP's and such. Just assign them usernames and passwords and have them log in through that.

"and have a local jabber IM server so I can IM other network users."

[Instructions]("http://linuxgazette.net/112/tomar.html") on how to do so.

Am i correct to assume that u want the jabber server to run within your server? If so i dont believe that this is possible. It is a separate entity altogether.

"I can set up another server to manage the firewall and external dns at a later date."

You should really only need to have 1 server running to accomplish all you are trying to do(except the jabber server). Plus a server doesnt manage a firewall at all.

"so basically I want to run filesharing, and use the server for acces management to the local pc's files. and have the server assign the same local ip to individual users everytime they connect. And Have an IM client to connect with users for support, and local remote acces to users. webmin is really only to avoid the command line."

All of this can be managed by having just 1 server(filesharing). Again outsiders from your home network have to connect externally, i dont believe you can have outsiders log in as if they are within your internal network. Plus if u can it would make your network way more vulnerable.



Ill look into running this jabber server within a regular server and see if its possible.

---

### Post by SykoFerret on 2009-06-06
ok. now I know with windows a file server hosts the files. i dont want the server to host the files. it only has a 15GB hdd. i just want the server to just host a list of shared files with access rights. an old friend of mine had a red hat box exactly like the one i want without the im server. but i haven't the slightest clue how to set it up. he was running smoothwall for firewall. and i definately don't want anyone to have external access.

---

### Post by uberlube on 2009-06-06
so you have 1 machine acting as a dedicated server and the files that are being shared are housed on another machine?

---

### Post by SykoFerret on 2009-06-06
right. except the files will be hosted on multiple machines. i want to avoid setting up password protected sharing on a bunch of machines by restricting access. basically have the pps table in one central location. or active directory in windows. the only need for dns would be to resolve internal hosts.

---

### Post by uberlube on 2009-06-06
Ok. In a normal scenario the server would be hosting the files but i think in this case what u would have to do is make what is called a "group" for the users u want to have gain access to those files. The group holds the permissions for those users as to what they can and cant access. All you would then have to do is allow the group access to the folder housing the files on your network.

---

### Post by SykoFerret on 2009-06-06
ok. so how do i go about setting that up? and i just share the file on th windows machine and users in the groups with access will have access to the files? will i even need dhcp or dns? the server is behind the router with a static ip. if you have some links that would be appreciated. it's late so i'm going to call it a night and try to get some more done tomorrow. thanks again for all your help.

---

### Post by uberlube on 2009-06-06
i believe that u can forget about dhcp but dns is still necessary for people to access your network. Ive been thinking about this a bit more and im not quite sure if u can host files on your server from another cpu that is logged in as a guest. I guess thats the whole point of the server itself is to be the host. U may want to consider dedicating some more space to the server to host the files on. Or if u are limited to that amount of space go get an external HD and hook it up to the server and just use that. As for setting it all up u have to check the documentation from the type of server you are running. It will explain how to create groups and assign privileges and all that. Anyways gnight and GL.

---

