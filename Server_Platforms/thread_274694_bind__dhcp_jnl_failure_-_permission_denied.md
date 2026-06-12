---
title: "bind / dhcp jnl failure - permission denied"
date: 2006-10-10
forum: Server Platforms
---

### Post by twistedtwig on 2006-10-10
Hi all,

I thought i had bind working correctly but seems i dont fully.

i want to have a static ip that is given out from the dhcp server. That is working but it doesnt seem to be able to create the jnl file.

> 
Oct 10 12:05:06 localhost named[3726]: journal file /etc/bind/db.10.168.192.jnl does not exist, creating it
Oct 10 12:05:06 localhost named[3726]: /etc/bind/db.10.168.192.jnl: create: permission denied
Oct 10 12:05:06 localhost dhcpd: unable to add reverse map from 100.10.168.192.in-addr.arpa. to bobby.ponywarshome.local: timed out

my permissions are as follows:

> 
-rwxrwxr-x 1 bind bind 237 2006-08-30 19:21 db.0
-rwxrwxr-x 1 bind bind 368 2006-08-30 19:21 db.10.168.192
-rwxrwxr-x 1 bind bind 271 2006-08-30 19:21 db.127
-rwxrwxr-x 1 bind bind 237 2006-08-30 19:21 db.255
-rwxrwxr-x 1 bind bind 353 2006-08-30 19:21 db.empty
-rwxrwxr-x 1 bind bind 256 2006-08-30 19:21 db.local
-rwxrwxr-x 1 bind bind 279 2006-08-30 19:21 db.ponywars
-rwxrwxr-x 1 bind bind 12442 2006-10-10 08:28 db.ponywars.jnl
-rwxrwxr-x 1 bind bind 1507 2006-08-30 19:21 db.root
-rwxrwxr-x 1 bind bind 388 2006-08-30 19:21 logging.conf
-rwxrwxr-x 1 bind bind 2383 2006-08-30 20:13 named.conf
-rwxrwxr-x 1 bind bind 412 2006-08-30 20:11 named.conf.local
-rwxrwxr-x 1 bind bind 685 2006-08-30 19:21 named.conf.options
-rwxrwxr-x 1 bind bind 77 2006-08-30 19:21 rndc.key
-rwxrwxr-x 1 bind bind 1317 2006-08-30 19:21 zones.rfc1918

not sure what else i shoudl be posting to be honest. any and all help MORE than welcome. rather confused to be honest.

Cheers

Twiggy

(i reposted from networking thread as i feel i miss posted really)

---

### Post by Iowan on 2006-10-10
Naive question perhaps, but...
Is **named** in the **bind** group?

---

### Post by twistedtwig on 2006-10-10
not naive at all, because i dont know how to check it let alone do it.

to be completely honest permissions and groups confuse me at the moment and i do think thats where the problem may lay.

any advice or pointers on where to look / read up on it please.

Thx :)

---

### Post by Endwin on 2006-10-10
Did you set the directory it is in to be owned by bind?

---

### Post by twiggy on 2006-10-10
this is what i am not sure about.  i have posted the ls -l of /etc/bind

Here is the ls -l of /etc grep'd for bind

> 
drwxrwxr-x   2 root   root      4096 2006-10-09 09:37 bind
drwxr-xr-x   2 root   root      4096 2006-08-30 08:17 bindBackupDDNS
drwxr-xr-x   2 root   root      4096 2006-08-30 08:18 bindOriginal


i dont have confidence with my understanding of what i have set and how to set / change things

Twiggy

---

### Post by Iowan on 2006-10-10
How many usernames do you have/need?

---

### Post by twistedtwig on 2006-10-11
must have been an old one i forgot.  will try and remove it, at least get rid of cookie for it


Could anyone point me in the right direction to understanding, checking and fixing the permissions / ownership issues please?

cheers

Twiggy

---

### Post by Endwin on 2006-10-11
Depending on how screwed up your permissions are a reinstall may be warented.

[http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions]("http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions")
is a link to a site describing file permissions, owners, group and how to change them.

I take it you are just trying to set up a local DNS server for a LAN?

---

### Post by twistedtwig on 2006-10-11
yep its just a local network for a computers at home.  did some reading around and found some answers.  think i got it sorted. with chmod 775 and chwown root:bind to give bind the group.

Think it works.  The reason i actually noticed was i have setup an old computer with a trail version of sbs2003 premium and the dns wasnt working for it.  it wasnt adding the reverse mapping or forward mapping.  when i changed the settings it did the reverse but not the forward (although i dont remember seeing an error for it).

I think this has to do with the windows domain controller and need to play with this for a while to understand what is happening ( or not happening so to speak).

when i added one of my computers to the domain (taking it out of the workgroup) it also buggered up its mapping.  I have a copy of my old bind settings after having a bit of a play with no success.

thank you everyone for your help and guidence.  it really helped me think about what i hadnt done and look to what i needed to do.

Cheers

Twiggy

---

### Post by Endwin on 2006-10-11
Not sure how relevent to you this would be at the moment but I did write a guide about DHCP/DNS and the like. You can extract from that the DNS and try and get it to work for you.

[http://ubuntuforums.org/showthread.php?t=267974]("http://ubuntuforums.org/showthread.php?t=267974")

---

### Post by twistedtwig on 2006-10-11
wicked, thank you.  will have a good read of that tonight :)

---

### Post by twistedtwig on 2006-10-11
> home.linux.lan.moo.cow.milk ;)

thats gotta be my new domain name

---

### Post by Endwin on 2006-10-11
heh, just keep in mind that is only for your local LAN. If you want a domain name for the net you need to buy one, and I don't think there is a .milk extension yet =)

---

### Post by twistedtwig on 2006-10-12
Hi guys,

Just wanted to say thank you for all your help.  Got bind working again last night with computers on a domain rather than workgroup.  only thing i have noticed at work this morning is i dont seem to be able to ping them when i vpn in. before i would do:

ping computername.localdomain

and that woudl resolve but it doesnt seem to be working at this point.  Will have to have another look at that, but felt good to get it working last night.  Through the guide given and advice i understood what i didnt get before hand.

THANKS people.. u rock!!!! :D

Twiggy

---

### Post by twistedtwig on 2006-10-12
Oh dear, i spoke too soon.  it all seems broken again this morning.  I used putty to get into the server and cant ping anything and have this error:

> 
localhost dhcpd: Can't update forward map dalecomputer.ponywarshome.local to 192.168.10.196: no such RRset


/cry

I dont understand what the RRset bit is, never seen this before.

any suggestions please?

---

### Post by twistedtwig on 2006-10-12
ok, so i have come home to have a look at this.

from a local machine i can ping all the computers, ie ping wiggly and get a response.  But if i am puttied into the ubuntu server it can not resolve the name.  I am not even sure how that is possible to be honest.  I thought they all sent the request to the ubuntu server to resolve the name.

the windows server isnt running as a dhcp or dns server.

oh my god this is confusing me.

i had a look at the daemog.log file again and can see that it is not entering a forward map.  it adds the reverse but not the forward, here is the output when i did a release and renew from the laptop (felix).

> Oct 12 12:37:55 localhost dhcpd: removed reverse map on 194.10.168.192.in-addr.arpa.
Oct 12 12:37:55 localhost dhcpd: DHCPRELEASE of 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1 (found)
Oct 12 12:38:07 localhost dhcpd: DHCPDISCOVER from 00:d0:59:34:17:7c via eth1
Oct 12 12:38:08 localhost dhcpd: DHCPOFFER on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 12 12:38:08 localhost dhcpd: added reverse map from 194.10.168.192.in-addr.arpa. to felix.ponywarshome.local
Oct 12 12:38:08 localhost dhcpd: DHCPREQUEST for 192.168.10.194 (192.168.10.1) from 00:d0:59:34:17:7c (felix) via eth1
Oct 12 12:38:08 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1


any thoughts please guys?

---

### Post by Endwin on 2006-10-12
On the server with bind you need to **EXPLICITLY** tell it to search itself for domain information. How are you geting your IP for your DNS server? Through DHCP or is it static? Is this machine also the gateway/router for your lan? 

If this is through DHCP you need to modify **/etc/dhcp3/dhclient.conf**
and uncomment

```

#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;

```

Replace Fuge.com home.vix.com with whatever your domain for the local LAN is. 

If your machine has one nic, with a static IP or a gateway with a public static IP (IE the server doesn't get a DHCP IP) then you need to manually edit /etc/resolv.conf

```

search YOUR.DOMAIN.HERE
nameserver IP_OF_MACHINE HERE

```

The DNS Server by default dosn't include itself in the searching of name lookups, which is why you need to do the above.

---

### Post by twistedtwig on 2006-10-12
Thanks for the reply.  Ok so i have ubuntu running as my dhcp and dns server.  This is connected to the net and gets its external IP through dhcp.  it has two network cards, the external being dynamic and internal static (192.168.10.1).

So all computers in the network at dynamic using dhcp (windows server is dynamic but i use the mac address to keep it sudo static from within dhcpd.conf).

does the
> 
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1

tell it to search it self? i am a little confused what that does?

Thank you for your help :)

Twiggy

EDIT: just thought, could have this completely wrong though.... without it adding the forward mapping will it not be able to resolve the ip?  I "think" it isnt doing this, as i said in last post i couldnt see it in the daemon.log file but i am so not confident with this yet.

---

### Post by twistedtwig on 2006-10-12
should there not be 2 jnl files in the bind folder? one for reverse  db.10.168.192.jnl and db.ponywarshome.jnl for forward mapipng? again could be wrong, but either way i only have one at the moment.

/stressed Twiggy

---

### Post by Endwin on 2006-10-12
OK, I think you should have 2 JNL files one for the domain and one for the IP related to said domain for the reverse lookups. The idea behind uncommenting those two lines is to tell DHCP that 'HEY I want these items added to my resolv.conf so that when you overwrite it I can still use this information'. Whenever dhclient goes and gets an IP for the machine it gets information from the DHCP server such as the IP, gateway, and DNS information it then creates a resolv.conf fine with this information so that the system can get on-line. By uncommenting those lines in /etc/dhcp3/dhclient.conf you tell it to add this information before the information it gets from DHCP.


#supersede domain-name "fugue.com home.vix.com"; <= This adds search DOMAIN to resolv.conf
#prepend domain-name-servers 127.0.0.1 <= This adds nameserver IP_ADDRESS to resolv.conf

Since the Ubuntu server is the DHCP and DNS server for your lan, the machines that connect to it are getting the proper DNS information yes? (trying to make sure DHCP is set up right to pass along the proper DNS server to the machines on your lan)

---

### Post by twistedtwig on 2006-10-12
They seem to be getting all the right info.  only thing i am not sure about is the "DNS Suffix Search List".  my laptop seems to have ponywarshome.local twice and the other computer was still having ponywars.com (the old one).  cant remember if that changed this morning.

The computers definetly gets the gateway of 192.168.10.1 (which is the static ip on the ubuntu server).  They can get the net and work fine and ping other computers by name.

---

### Post by twistedtwig on 2006-10-12
i thought it might help to post my bind files incase there is some still error in here:

db.10.168.192
> 
$ORIGIN .
$TTL 86400      ; 1 day
10.168.192.in-addr.arpa IN SOA  betty.ponywarshome.local. jon.betty.ponywarshome.local.10.168.192.in-addr.arpa. (
                                10         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywarshome.local.
$ORIGIN 10.168.192.in-addr.arpa.
$TTL 21600      ; 6 hours
100                     PTR     bobby.ponywarshome.local.
194                     PTR     felix.ponywarshome.local.
198                     PTR     wiggly.ponywarshome.local.



db.ponywarshome
> 
$ORIGIN .
$TTL 86400      ; 1 day
ponywarshome.local      IN SOA  betty.ponywarshome.local. jon.betty.ponywarshome.local. (
                                63         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywarshome.local.
                        MX      10 betty.ponywarshome.local.
$ORIGIN ponywarshome.local.
$TTL 21600      ; 6 hours
dalecomputer            TXT     "31a988dc539aa14c240d875a61117897ea"



named.conf
> 
include "/etc/bind/named.conf.options";
logging {

        channel update_debug {
                file "/var/log/update-debug.log";
                severity debug 3;
                print-category yes;
                print-severity yes;
                print-time     yes;
        };

        channel security_info {
                file "/var/log/named-auth.info";
                severity info;
                print-category yes;
                print-severity yes;
                print-time     yes;
        };

        category update { update_debug; };
        category security { security_info; };
};

// setting up the ddns
key "rndc-key" {
        algorithm hmac-md5;
        secret "KEYYYY/JNVahw==";
};

controls {
        inet 127.0.0.1 allow { 127.0.0.1; } keys { "rndc-key"; };
};

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};



named.conf.local
> 
zone "ponywarshome.local" {
        type master;
        file "/etc/bind/db.ponywarshome";
        notify yes;
        allow-update { key rndc-key; };
};

zone "10.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.10.168.192";
        notify yes;
        allow-update { key rndc-key; };
};


dhcpd.conf
> authoritative;

ddns-updates on;
ddns-rev-domainname "in-addr.arpa.";
ddns-update-style interim;
allow client-updates;

max-lease-time 600;######################172800;
default-lease-time 500; #################43200;
one-lease-per-client on;

subnet 192.168.10.0 netmask 255.255.255.0 {
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.10.255;

option domain-name "ponywarshome.local";
option domain-name-servers 192.168.10.1;
option routers 192.168.10.1;

range 192.168.10.101 192.168.10.200;
}

key "rndc-key" {
        algorithm hmac-md5;
        secret "nHNvhlt1nQ0bg0k/JNVahw==";
};

zone ponywarshome.local. {
        primary 127.0.0.1;
        key rndc-key;
}

zone 10.168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key rndc-key;
}

host BOBBY {
        hardware ethernet 00:08:54:44:75:10;
        fixed-address 192.168.10.100;
}


Twiggy

---

### Post by Endwin on 2006-10-12
Odd that it is in there twice, but should not be a a biggie. What search DOMAIN_NAME_HERE in resolv.conf does is make refrencing machines easier. For example say you have the domain moocow.com and you have the machines routerman, clientperson, and cookiemonster. In the DNS they would be respectively routerman.moocow.com, clientperson.moocow.com, and cookiemonster.moocow.com. Instead of always typing routerman.moocow.com whenever you want to acess routerman. The search moocow.com in resolv.conf searches the domain for that name so that you can just type routerman whenever you are connected to that DNS server. 

The supersede domain-name "moocow.com"; directive would make sure that no matter what search moocow.com would always be in resolv.conf.

From the sound of it your clients are fine and it is just the DNS/DHCP/router that has a few problems, Set those directives, and then restart networking and you should be good. (or just release/renew the DHCP address for the internet). Be careful not to kill your connection home =).

---

### Post by twistedtwig on 2006-10-12
cool bananas.. i do LOVE your naming structure! :D

will try that when i get home so i can release and refresh the IPs at home and check results easily and safely.

fingers crossed i can come back and say YAY!

i SO owe u a beer or 3 ;)

thank you.  will let you know how it goes in a couple of hours.. darn work!

---

### Post by Endwin on 2006-10-12
Heh, well my example names are usally wierd. My home stuff is named thus:

guardian <- router
nani <- main machine
lain <- laptop
cantlin <- web server
sylvaria <- file server

with the domain alefgard.com so in everyday life I don't use strange names, but for my examples I do so that it is clear that hey maybe I should change this. I have read too many examples where the bit you need to rename or modify is not clearly stated I make a point of doing so in mine (hence the strange names). Who heard of a command or option named moocowmilk?:p 

If you are feeling brave and have acess to the machine from work you can do ```
sudo /etc/init.d/networking restart
``` in order to refresh the network or just manually reboot the machine.

---

### Post by twistedtwig on 2006-10-12
/cry

restarted ALL computers and still no joy

> Oct 12 17:44:21 localhost dhcpd: added reverse map from 100.10.168.192.in-addr.arpa. to bobby.ponywarshome.local
Oct 12 17:44:21 localhost dhcpd: DHCPREQUEST for 192.168.10.100 from 00:08:54:44:75:10 via eth1
Oct 12 17:44:21 localhost dhcpd: DHCPACK on 192.168.10.100 to 00:08:54:44:75:10 via eth1


that is what the daemon.log file says when the server came back up.  there is still no forward mapping.  but the computers can still ping each other.

i am so lost :(

---

### Post by twistedtwig on 2006-10-12
I thought it could have been the dns on the windows server (sbs2003) but it isnt, i uninstalled it, restarted everything again but still the same issue.

and oddly the "DNS Suffex Search List" is still ponywars.com when it should be ponywarshome.local on one of my computers.

I am so confused to what isnt working now.... grrr thought i was getting the hang of this last night /sulk

---

### Post by Endwin on 2006-10-12
Ok let us go over what IS and IS NOT working...

What I understand:

DHCP and DNS work Clients get IPs and can ping/connect to each other by DNS name.

The DHCP/DNS server cannot ping by the DNS names, however it can by normal IPs.

Is this correct?

---

### Post by twistedtwig on 2006-10-12
perfect round up of the situation

sorry for delay in reply family issues arrose.

---

### Post by Endwin on 2006-10-12
Ok in that case what are the contents of **/etc/resolv.conf** ?

---

### Post by twistedtwig on 2006-10-12
resolv.conf

> 
domain ponywarshome.local
search ponywarshome.local
nameserver 127.0.0.1
nameserver 194.74.65.69


---

### Post by Endwin on 2006-10-12
Ok let's remove the domain line and try it, and if it still doesn't try adding nameserver IP_OF_LOCAL_MACHINE in place of 127.0.0.1

Also it may help to try dig MACHINE.ponywarshome.local

where MACHINE is one of the machines on your lan.

---

### Post by twistedtwig on 2006-10-12
ok so here is the dig:

> ; <<>> DiG 9.3.2 <<>> wiggly.ponywarshome.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 47116
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;wiggly.ponywarshome.local.     IN      A

;; AUTHORITY SECTION:
ponywarshome.local.     86400   IN      SOA     betty.ponywarshome.local. jon.betty.ponywarshome.local. 63 604800 86400 2419200 86400

;; Query time: 4 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu Oct 12 20:47:56 2006
;; MSG SIZE  rcvd: 89


---

### Post by Endwin on 2006-10-12
I take it removing the domain and changing the IP disn't work...


ok, how about restart the DNS and DHCP servers in that order then post the tail -n 30 of /var/log/daemon.log /var/log/messages and /var/log/syslog

---

### Post by twistedtwig on 2006-10-12
nope it had no affect :( here are the logs

daemon.log
> 
Oct 12 21:01:50 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:01:50 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seconds.
Oct 12 21:02:19 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:02:19 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:02:19 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seconds.
Oct 12 21:02:48 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:02:48 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:02:48 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.
Oct 12 21:03:15 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:03:15 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:03:15 localhost dhclient: bound to 86.139.30.251 -- renewal in 25 seconds.
Oct 12 21:03:18 localhost dhcpd: DHCPREQUEST for 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:03:18 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:03:40 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:03:40 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:03:40 localhost dhclient: bound to 86.139.30.251 -- renewal in 30 seconds.
Oct 12 21:04:10 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:04:10 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:04:10 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seconds.
Oct 12 21:04:27 localhost dhcpd: added reverse map from 100.10.168.192.in-addr.arpa. to bobby.ponywarshome.local
Oct 12 21:04:27 localhost dhcpd: DHCPREQUEST for 192.168.10.100 from 00:08:54:44:75:10 via eth1
Oct 12 21:04:27 localhost dhcpd: DHCPACK on 192.168.10.100 to 00:08:54:44:75:10 via eth1
Oct 12 21:04:39 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:04:39 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:04:39 localhost dhclient: bound to 86.139.30.251 -- renewal in 26 seconds.
Oct 12 21:04:43 localhost dhcpd: DHCPREQUEST for 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1
Oct 12 21:04:43 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 12 21:05:05 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:05:05 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:05:05 localhost dhclient: bound to 86.139.30.251 -- renewal in 32 seconds.


messages
> 
Oct 12 18:00:08 localhost kernel: [   62.720128] Bluetooth: HCI device and connection manager initialized
Oct 12 18:00:08 localhost kernel: [   62.720183] Bluetooth: HCI socket layer initialized
Oct 12 18:00:08 localhost kernel: [   62.778227] Bluetooth: L2CAP ver 2.8
Oct 12 18:00:08 localhost kernel: [   62.778248] Bluetooth: L2CAP socket layer initialized
Oct 12 18:00:08 localhost kernel: [   62.790766] Bluetooth: RFCOMM socket layer initialized
Oct 12 18:00:08 localhost kernel: [   62.790821] Bluetooth: RFCOMM TTY layer initialized
Oct 12 18:00:08 localhost kernel: [   62.790832] Bluetooth: RFCOMM ver 1.7
Oct 12 18:00:08 localhost squid[5257]: Squid Parent: child process 5261 started
Oct 12 18:19:42 localhost -- MARK --
Oct 12 18:39:42 localhost -- MARK --
Oct 12 18:59:43 localhost -- MARK --
Oct 12 19:19:43 localhost -- MARK --
Oct 12 19:39:43 localhost -- MARK --
Oct 12 19:59:43 localhost -- MARK --
Oct 12 20:19:44 localhost -- MARK --
Oct 12 20:39:44 localhost -- MARK --
Oct 12 20:47:26 localhost kernel: [10093.823292] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Oct 12 20:47:27 localhost kernel: [10094.832465] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 12 20:47:27 localhost kernel: [10094.964976] TLAN: eth0: Starting autonegotiation.
Oct 12 20:47:29 localhost kernel: [10096.966075] TLAN: eth0: Autonegotiation complete.
Oct 12 20:47:30 localhost kernel: [10097.072814] TLAN: eth0: Link active with AutoNegotiation enabled, at 100Mbps Full-Duplex
Oct 12 20:47:30 localhost kernel: [10097.072832] TLAN: Partner capability: 10BaseT-HD 10BaseT-FD 100baseTx-HD 100baseTx-FD
Oct 12 20:47:30 localhost kernel: [10097.091032] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 12 20:58:25 localhost kernel: [10752.484968] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Oct 12 20:58:26 localhost kernel: [10753.430024] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 12 20:58:27 localhost kernel: [10753.558893] TLAN: eth0: Starting autonegotiation.
Oct 12 20:58:29 localhost kernel: [10755.559997] TLAN: eth0: Autonegotiation complete.
Oct 12 20:58:29 localhost kernel: [10755.666722] TLAN: eth0: Link active with AutoNegotiation enabled, at 100Mbps Full-Duplex
Oct 12 20:58:29 localhost kernel: [10755.666740] TLAN: Partner capability: 10BaseT-HD 10BaseT-FD 100baseTx-HD 100baseTx-FD
Oct 12 20:58:29 localhost kernel: [10755.685992] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


syslog
> 
Oct 12 21:00:11 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 21:00:11 localhost dhcpd: All rights reserved.
Oct 12 21:00:11 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 21:00:13 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 21:00:13 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 21:00:13 localhost dhcpd: All rights reserved.
Oct 12 21:00:13 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 21:00:13 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 12 21:00:13 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 12 21:00:13 localhost dhcpd: Wrote 9 leases to leases file.
Oct 12 21:00:17 localhost dhcpd: added reverse map from 100.10.168.192.in-addr.arpa. to bobby.ponywarshome.local
Oct 12 21:00:17 localhost dhcpd: DHCPREQUEST for 192.168.10.100 from 00:08:54:44:75:10 via eth1
Oct 12 21:00:17 localhost dhcpd: DHCPACK on 192.168.10.100 to 00:08:54:44:75:10 via eth1
Oct 12 21:00:28 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:00:28 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:00:28 localhost dhclient: bound to 86.139.30.251 -- renewal in 25 seconds.
Oct 12 21:00:32 localhost dhcpd: DHCPREQUEST for 192.168.10.194 from 00:d0:59:34:17:7c (felix) via eth1
Oct 12 21:00:32 localhost dhcpd: DHCPACK on 192.168.10.194 to 00:d0:59:34:17:7c (felix) via eth1
Oct 12 21:00:53 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:00:53 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:00:53 localhost dhclient: bound to 86.139.30.251 -- renewal in 30 seconds.
Oct 12 21:01:23 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:01:23 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:01:23 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.
Oct 12 21:01:50 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:01:50 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:01:50 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seconds.
Oct 12 21:02:19 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:02:19 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:02:19 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seconds.


---

### Post by Endwin on 2006-10-12
Ok the db.0.168.192.in-addr.arpa file there is no refrence to resolve the DNS server =)

I presume the address is 192.168.10.1

You will want to add 

```
1     PTR    betty

```
just before the other enteries (just bellow the DNS entry and above the ones already in there.

restart dns and post the logs again we want to make sure the file loaded correctly.

---

### Post by twistedtwig on 2006-10-12
so db.10.168.192 file:

> 
$ORIGIN .
$TTL 86400      ; 1 day
10.168.192.in-addr.arpa IN SOA  betty.ponywarshome.local. jon.betty.ponywarshome.local.10.168.192.in-addr.arpa. (
                                17         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywarshome.local.
$ORIGIN 10.168.192.in-addr.arpa.
$TTL 250        ; 4 minutes 10 seconds
1                       PTR     betty
100                     PTR     bobby.ponywarshome.local.
194                     PTR     felix.ponywarshome.local.
198                     PTR     wiggly.ponywarshome.local.


daemon.log
> 
Oct 12 21:17:54 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.
Oct 12 21:18:21 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:18:21 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:18:21 localhost dhclient: bound to 86.139.30.251 -- renewal in 25 seconds.
Oct 12 21:18:46 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:18:46 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:18:46 localhost dhclient: bound to 86.139.30.251 -- renewal in 31 seconds.
Oct 12 21:19:17 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:19:17 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:19:17 localhost dhclient: bound to 86.139.30.251 -- renewal in 32 seconds.
Oct 12 21:19:32 localhost named[11865]: shutting down: flushing changes
Oct 12 21:19:32 localhost named[11865]: stopping command channel on 127.0.0.1#953
Oct 12 21:19:32 localhost named[11865]: no longer listening on 127.0.0.1#53
Oct 12 21:19:32 localhost named[11865]: no longer listening on 86.139.30.251#53
Oct 12 21:19:32 localhost named[11865]: no longer listening on 192.168.10.1#53
Oct 12 21:19:32 localhost named[11865]: exiting
Oct 12 21:19:35 localhost named[12598]: starting BIND 9.3.2 -u bind
Oct 12 21:19:35 localhost named[12598]: found 4 CPUs, using 4 worker threads
Oct 12 21:19:35 localhost named[12598]: loading configuration from '/etc/bind/named.conf'
Oct 12 21:19:35 localhost named[12598]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 12 21:19:35 localhost named[12598]: listening on IPv4 interface eth0, 86.139.30.251#53
Oct 12 21:19:35 localhost named[12598]: listening on IPv4 interface eth1, 192.168.10.1#53
Oct 12 21:19:35 localhost named[12598]: command channel listening on 127.0.0.1#953
Oct 12 21:19:35 localhost named[12598]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: zone 10.168.192.in-addr.arpa/IN: loaded serial 17
Oct 12 21:19:35 localhost named[12598]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: zone ponywarshome.local/IN: loaded serial 63
Oct 12 21:19:35 localhost named[12598]: zone localhost/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: running


messages
> 
Oct 12 18:00:08 localhost kernel: [   62.720183] Bluetooth: HCI socket layer initialized
Oct 12 18:00:08 localhost kernel: [   62.778227] Bluetooth: L2CAP ver 2.8
Oct 12 18:00:08 localhost kernel: [   62.778248] Bluetooth: L2CAP socket layer initialized
Oct 12 18:00:08 localhost kernel: [   62.790766] Bluetooth: RFCOMM socket layer initialized
Oct 12 18:00:08 localhost kernel: [   62.790821] Bluetooth: RFCOMM TTY layer initialized
Oct 12 18:00:08 localhost kernel: [   62.790832] Bluetooth: RFCOMM ver 1.7
Oct 12 18:00:08 localhost squid[5257]: Squid Parent: child process 5261 started
Oct 12 18:19:42 localhost -- MARK --
Oct 12 18:39:42 localhost -- MARK --
Oct 12 18:59:43 localhost -- MARK --
Oct 12 19:19:43 localhost -- MARK --
Oct 12 19:39:43 localhost -- MARK --
Oct 12 19:59:43 localhost -- MARK --
Oct 12 20:19:44 localhost -- MARK --
Oct 12 20:39:44 localhost -- MARK --
Oct 12 20:47:26 localhost kernel: [10093.823292] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Oct 12 20:47:27 localhost kernel: [10094.832465] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 12 20:47:27 localhost kernel: [10094.964976] TLAN: eth0: Starting autonegotiation.
Oct 12 20:47:29 localhost kernel: [10096.966075] TLAN: eth0: Autonegotiation complete.
Oct 12 20:47:30 localhost kernel: [10097.072814] TLAN: eth0: Link active with AutoNegotiation enabled, at 100Mbps Full-Duplex
Oct 12 20:47:30 localhost kernel: [10097.072832] TLAN: Partner capability: 10BaseT-HD 10BaseT-FD 100baseTx-HD 100baseTx-FD
Oct 12 20:47:30 localhost kernel: [10097.091032] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 12 20:58:25 localhost kernel: [10752.484968] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Oct 12 20:58:26 localhost kernel: [10753.430024] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 12 20:58:27 localhost kernel: [10753.558893] TLAN: eth0: Starting autonegotiation.
Oct 12 20:58:29 localhost kernel: [10755.559997] TLAN: eth0: Autonegotiation complete.
Oct 12 20:58:29 localhost kernel: [10755.666722] TLAN: eth0: Link active with AutoNegotiation enabled, at 100Mbps Full-Duplex
Oct 12 20:58:29 localhost kernel: [10755.666740] TLAN: Partner capability: 10BaseT-HD 10BaseT-FD 100baseTx-HD 100baseTx-FD
Oct 12 20:58:29 localhost kernel: [10755.685992] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 12 21:19:44 localhost -- MARK --


syslog
> 
Oct 12 21:19:17 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:19:17 localhost dhclient: bound to 86.139.30.251 -- renewal in 32 seconds.
Oct 12 21:19:32 localhost named[11865]: shutting down: flushing changes
Oct 12 21:19:32 localhost named[11865]: stopping command channel on 127.0.0.1#953
Oct 12 21:19:32 localhost named[11865]: no longer listening on 127.0.0.1#53
Oct 12 21:19:32 localhost named[11865]: no longer listening on 86.139.30.251#53
Oct 12 21:19:32 localhost named[11865]: no longer listening on 192.168.10.1#53
Oct 12 21:19:32 localhost named[11865]: exiting
Oct 12 21:19:35 localhost named[12598]: starting BIND 9.3.2 -u bind
Oct 12 21:19:35 localhost named[12598]: found 4 CPUs, using 4 worker threads
Oct 12 21:19:35 localhost named[12598]: loading configuration from '/etc/bind/named.conf'
Oct 12 21:19:35 localhost named[12598]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 12 21:19:35 localhost named[12598]: listening on IPv4 interface eth0, 86.139.30.251#53
Oct 12 21:19:35 localhost named[12598]: listening on IPv4 interface eth1, 192.168.10.1#53
Oct 12 21:19:35 localhost named[12598]: command channel listening on 127.0.0.1#953
Oct 12 21:19:35 localhost named[12598]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: zone 10.168.192.in-addr.arpa/IN: loaded serial 17
Oct 12 21:19:35 localhost named[12598]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: zone ponywarshome.local/IN: loaded serial 63
Oct 12 21:19:35 localhost named[12598]: zone localhost/IN: loaded serial 1
Oct 12 21:19:35 localhost named[12598]: running
Oct 12 21:19:49 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:19:49 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:19:49 localhost dhclient: bound to 86.139.30.251 -- renewal in 25 seconds.
Oct 12 21:19:58 localhost dhcpd: DHCPREQUEST for 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:19:58 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:20:14 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:20:14 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:20:14 localhost dhclient: bound to 86.139.30.251 -- renewal in 32 seconds.


---

### Post by Endwin on 2006-10-12
That should do it, it is loading now, look in the directory do you see a corresponding .jnl file for it? Try using the names for pinging now the full name and the short one and see if it works.

---

### Post by twistedtwig on 2006-10-12
nope :( still no extra jnl file, restarted networking, bind and dhcp-server

> 
jon@betty:/etc/bind$ ls -l
total 64
-rwxr-xr-x 1 root bind  237 2006-10-11 20:47 db.0
-rw-r--r-- 1 bind bind  524 2006-10-12 21:31 db.10.168.192
-rw-r--r-- 1 bind bind 6334 2006-10-12 21:31 db.10.168.192.jnl
-rwxr-xr-x 1 root bind  271 2006-10-11 20:47 db.127
-rwxr-xr-x 1 root bind  237 2006-10-11 20:47 db.255
-rwxr-xr-x 1 root bind  353 2006-10-11 20:47 db.empty
-rwxr-xr-x 1 root bind  256 2006-10-11 20:47 db.local
-rw-r--r-- 1 root bind  446 2006-10-12 15:03 db.ponywarshome
-rwxr-xr-x 1 root bind 1507 2006-10-11 20:47 db.root
-rwxr-xr-x 1 root bind  388 2006-10-11 20:47 logging.conf
-rwxr-xr-x 1 root bind 2373 2006-10-11 20:54 named.conf
-rwxr-xr-x 1 root bind  422 2006-10-12 15:05 named.conf.local
-rwxr-xr-x 1 root bind  685 2006-10-11 20:47 named.conf.options
-rwxr-xr-x 1 root bind   77 2006-10-11 20:47 rndc.key
-rwxr-xr-x 1 root bind 1317 2006-10-11 20:47 zones.rfc1918


here is the daemon.log
> 
Oct 12 21:31:15 localhost named[13210]: zone ponywarshome.local/IN: loaded serial 63
Oct 12 21:31:15 localhost named[13210]: zone localhost/IN: loaded serial 1
Oct 12 21:31:15 localhost named[13210]: running
Oct 12 21:31:20 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 21:31:20 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 21:31:20 localhost dhcpd: All rights reserved.
Oct 12 21:31:20 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 21:31:22 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 21:31:22 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 21:31:22 localhost dhcpd: All rights reserved.
Oct 12 21:31:22 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 21:31:22 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 12 21:31:22 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 12 21:31:22 localhost dhcpd: Wrote 9 leases to leases file.
Oct 12 21:31:29 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:31:29 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:31:29 localhost dhclient: bound to 86.139.30.251 -- renewal in 28 seconds.
Oct 12 21:31:31 localhost dhcpd: removed reverse map on 198.10.168.192.in-addr.arpa.
Oct 12 21:31:31 localhost dhcpd: DHCPRELEASE of 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1 (found)
Oct 12 21:31:36 localhost dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Oct 12 21:31:37 localhost dhcpd: DHCPOFFER on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:31:37 localhost dhcpd: added reverse map from 198.10.168.192.in-addr.arpa. to wiggly.ponywarshome.local
Oct 12 21:31:37 localhost dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:31:37 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:31:57 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:31:57 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:31:57 localhost dhclient: bound to 86.139.30.251 -- renewal in 28 seconds.
Oct 12 21:32:25 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:32:25 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:32:25 localhost dhclient: bound to 86.139.30.251 -- renewal in 28 seconds.


it still doesnt look like its adding a forward backing bit?

---

### Post by Endwin on 2006-10-12
AH,

db.ponywarshome

is also missing a refrence to itself (it is also the one without a jnl file extension). 

Just bellow the mx betty one should be...


```
betty      A    1

```

That way it it can lookup itself.

**EDIT** and restart bind after adding that.

---

### Post by twistedtwig on 2006-10-12
so db.ponywarshome shoudl look like

> 
$ORIGIN .
$TTL 86400      ; 1 day
ponywarshome.local      IN SOA  betty.ponywarshome.local. jon.betty.ponywarshome.local. (
                                63         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywarshome.local.
                        MX      10 betty.ponywarshome.local.
                        betty   A 1
$ORIGIN ponywarshome.local.
$TTL 21600      ; 6 hours
dalecomputer            TXT     "31a988dc539aa14c240d875a61117897ea"


restarted bind but no forward mapping or pinging

Oct 12 21:42:33 localhost dhcpd: removed reverse map on 198.10.168.192.in-addr.arpa.
Oct 12 21:42:33 localhost dhcpd: DHCPRELEASE of 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1 (found)
Oct 12 21:42:39 localhost dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Oct 12 21:42:40 localhost dhcpd: DHCPOFFER on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:42:40 localhost dhcpd: added reverse map from 198.10.168.192.in-addr.arpa. to wiggly.ponywarshome.local
Oct 12 21:42:40 localhost dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:42:40 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1

---

### Post by Endwin on 2006-10-12
bah I lied.

```

$ORIGIN .
$TTL 86400 ; 1 day
ponywarshome.local IN SOA betty.ponywarshome.local. jon.betty.ponywarshome.local. (
63 ; serial
604800 ; refresh (1 week)
86400 ; retry (1 day)
2419200 ; expire (4 weeks)
86400 ; minimum (1 day)
)
NS betty.ponywarshome.local.
MX 10 betty.ponywarshome.local.
betty A 192.168.10.1
$ORIGIN ponywarshome.local.
$TTL 21600 ; 6 hours
dalecomputer TXT "31a988dc539aa14c240d875a61117897ea"

```

You need to put the full IP of the local machine (bran fart)

---

### Post by twistedtwig on 2006-10-12
hehe, but still no joy:

daemon.log
> 
Oct 12 21:54:58 localhost named[14408]: command channel listening on 127.0.0.1#953
Oct 12 21:54:58 localhost named[14408]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 12 21:54:58 localhost named[14408]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 12 21:54:58 localhost named[14408]: zone 10.168.192.in-addr.arpa/IN: loaded serial 25
Oct 12 21:54:58 localhost named[14408]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 12 21:54:58 localhost named[14408]: /etc/bind/db.ponywarshome:12: unknown RR type 'betty'
Oct 12 21:54:58 localhost named[14408]: zone ponywarshome.local/IN: loading master file /etc/bind/db.ponywarshome: unknown class/type
Oct 12 21:54:58 localhost named[14408]: zone localhost/IN: loaded serial 1
Oct 12 21:54:58 localhost named[14408]: running
Oct 12 21:55:04 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 21:55:04 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 21:55:04 localhost dhcpd: All rights reserved.
Oct 12 21:55:04 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 21:55:06 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 21:55:06 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 21:55:06 localhost dhcpd: All rights reserved.
Oct 12 21:55:06 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 21:55:06 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 12 21:55:06 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 12 21:55:06 localhost dhcpd: Wrote 9 leases to leases file.
Oct 12 21:55:13 localhost dhcpd: removed reverse map on 198.10.168.192.in-addr.arpa.
Oct 12 21:55:13 localhost dhcpd: DHCPRELEASE of 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1 (found)
Oct 12 21:55:14 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 21:55:14 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 21:55:14 localhost dhclient: bound to 86.139.30.251 -- renewal in 26 seconds.
Oct 12 21:55:18 localhost dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Oct 12 21:55:19 localhost dhcpd: DHCPOFFER on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:55:19 localhost dhcpd: added reverse map from 198.10.168.192.in-addr.arpa. to wiggly.ponywarshome.local
Oct 12 21:55:19 localhost dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 21:55:19 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1


db.ponywarshome
> 
$ORIGIN .
$TTL 86400      ; 1 day
ponywarshome.local      IN SOA  betty.ponywarshome.local. jon.betty.ponywarshome.local. (
                                63         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywarshome.local.
                        MX      10 betty.ponywarshome.local.
                        betty   A 192.168.10.1
$ORIGIN ponywarshome.local.
$TTL 21600      ; 6 hours
dalecomputer            TXT     "31a988dc539aa14c240d875a61117897ea"


---

### Post by Endwin on 2006-10-12
hrmm.. I know there is some silly misconfigured thing the problem is finding it... 

What is in resolv.conf now? contents of /etc/dhcp3/dhclient.conf?

I take it that still did not make a  db.ponywarshose.jnl file...

I am runing out of ideas, it may be an idea to wipe the DHCP and DNS and redo... Sometimes a restart from scratch with knowledge of what is doable can sole the problem with that one file with the misplaced .

---

### Post by twistedtwig on 2006-10-12
okie dokie

resolve
> 
search ponywarshome.local
nameserver 127.0.0.1
nameserver 194.74.65.69


dhclient
> 
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "ponywarshome.local";
#prepend domain-name-servers 127.0.0.1;
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


and nope, no jnl file

---

### Post by Endwin on 2006-10-12
Ok... release/renew on one of the clients and then see if you can see it, and it makes the jnl file....

**EDIT** Probably should do this after each change so the DHCP server will update the DNS leases.

---

### Post by twistedtwig on 2006-10-12
nope pinging wiggly doesnt do anything after network, bind and dhcp restarting (in that order) and then release renewing wiggly

jon@betty:~$ ping wiggly
ping: unknown host wiggly

> 
root@betty:/home/jon# tail -n 30 /var/log/daemon.log
Oct 12 22:33:09 localhost named[15915]: zone ponywarshome.local/IN: loading master file /etc/bind/db.ponywarshome: unknown class/type
Oct 12 22:33:09 localhost named[15915]: zone localhost/IN: loaded serial 1
Oct 12 22:33:09 localhost named[15915]: running
Oct 12 22:33:13 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 22:33:13 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 22:33:13 localhost dhcpd: All rights reserved.
Oct 12 22:33:13 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 22:33:15 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Oct 12 22:33:15 localhost dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Oct 12 22:33:15 localhost dhcpd: All rights reserved.
Oct 12 22:33:15 localhost dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 12 22:33:15 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 12 22:33:15 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 12 22:33:15 localhost dhcpd: Wrote 9 leases to leases file.
Oct 12 22:33:22 localhost dhcpd: removed reverse map on 198.10.168.192.in-addr.arpa.
Oct 12 22:33:22 localhost dhcpd: DHCPRELEASE of 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1 (found)
Oct 12 22:33:26 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:33:26 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:33:26 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.
Oct 12 22:33:30 localhost dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Oct 12 22:33:31 localhost dhcpd: DHCPOFFER on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 22:33:31 localhost dhcpd: added reverse map from 198.10.168.192.in-addr.arpa. to wiggly.ponywarshome.local
Oct 12 22:33:31 localhost dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 22:33:31 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 22:33:53 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:33:53 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:33:53 localhost dhclient: bound to 86.139.30.251 -- renewal in 25 seconds.
Oct 12 22:34:18 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:34:18 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:34:18 localhost dhclient: bound to 86.139.30.251 -- renewal in 28 seconds.


---

### Post by Endwin on 2006-10-12
OS of wiggly? If it is linux is dhclient.conf sending the hostname?

---

### Post by twistedtwig on 2006-10-12
wiggly and felix are xp pro bobby sbs2003.. only linux is betty (server)

---

### Post by Endwin on 2006-10-12
/etc/bind/db.ponywarshome:12: unknown RR type 'betty'
Oct 12 21:54:58 localhost named[14408]: zone ponywarshome.local/IN: loading master file /etc/bind/db.ponywarshome: unknown class/type 

This is interesting what is the current stuff in the file?

---

### Post by twistedtwig on 2006-10-12
db.ponywarshome = 

> 
root@betty:/home/jon# cat /etc/bind/db.ponywarshome
$ORIGIN .
$TTL 86400      ; 1 day
ponywarshome.local      IN SOA  betty.ponywarshome.local. jon.betty.ponywarshome.local. (
                                63         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                86400      ; minimum (1 day)
                                )
                        NS      betty.ponywarshome.local.
                        MX      10 betty.ponywarshome.local.
                        betty   A 192.168.10.1
$ORIGIN ponywarshome.local.
$TTL 21600      ; 6 hours
dalecomputer            TXT     "31a988dc539aa14c240d875a61117897ea"


---

### Post by Endwin on 2006-10-12
Replace it with this and then restart bind and post the daemon.log.

```
$ORIGIN .
$TTL 86400 ; 1 day
ponywarshome.local IN SOA betty.ponywarshome.local. jon.betty.ponywarshome.local. (
63 ; serial
604800 ; refresh (1 week)
86400 ; retry (1 day)
2419200 ; expire (4 weeks)
86400 ; minimum (1 day)
)
NS betty.ponywarshome.local.
MX 10 betty.ponywarshome.local.

$ORIGIN ponywarshome.local.
$TTL 21600 ; 6 hours
betty A 192.168.10.1
```

If you note it loads the file fine, release renew on the client and check the file.

---

### Post by twistedtwig on 2006-10-12
ok new file daemon after restart:

> 
root@betty:/home/jon# tail -n 30 /var/log/daemon.log
Oct 12 22:57:47 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:57:47 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seconds.
Oct 12 22:58:16 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:58:16 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:58:16 localhost dhclient: bound to 86.139.30.251 -- renewal in 26 seconds.
Oct 12 22:58:31 localhost dhcpd: DHCPREQUEST for 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 22:58:31 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 22:58:42 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:58:42 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:58:42 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.
Oct 12 22:58:47 localhost named[15915]: shutting down: flushing changes
Oct 12 22:58:47 localhost named[15915]: stopping command channel on 127.0.0.1#953
Oct 12 22:58:47 localhost named[15915]: no longer listening on 127.0.0.1#53
Oct 12 22:58:47 localhost named[15915]: no longer listening on 86.139.30.251#53
Oct 12 22:58:47 localhost named[15915]: no longer listening on 192.168.10.1#53
Oct 12 22:58:47 localhost named[15915]: exiting
Oct 12 22:58:49 localhost named[16860]: starting BIND 9.3.2 -u bind
Oct 12 22:58:49 localhost named[16860]: found 4 CPUs, using 4 worker threads
Oct 12 22:58:49 localhost named[16860]: loading configuration from '/etc/bind/named.conf'
Oct 12 22:58:49 localhost named[16860]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 12 22:58:49 localhost named[16860]: listening on IPv4 interface eth0, 86.139.30.251#53
Oct 12 22:58:49 localhost named[16860]: listening on IPv4 interface eth1, 192.168.10.1#53
Oct 12 22:58:49 localhost named[16860]: command channel listening on 127.0.0.1#953
Oct 12 22:58:49 localhost named[16860]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 12 22:58:49 localhost named[16860]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 12 22:58:49 localhost named[16860]: zone 10.168.192.in-addr.arpa/IN: loaded serial 29
Oct 12 22:58:49 localhost named[16860]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 12 22:58:49 localhost named[16860]: zone ponywarshome.local/IN: loaded serial 63
Oct 12 22:58:49 localhost named[16860]: zone localhost/IN: loaded serial 1
Oct 12 22:58:49 localhost named[16860]: running


after release renew:
> 
Oct 12 22:58:49 localhost named[16860]: starting BIND 9.3.2 -u bind
Oct 12 22:58:49 localhost named[16860]: found 4 CPUs, using 4 worker threads
Oct 12 22:58:49 localhost named[16860]: loading configuration from '/etc/bind/na                                             med.conf'
Oct 12 22:58:49 localhost named[16860]: listening on IPv4 interface lo, 127.0.0.                                             1#53
Oct 12 22:58:49 localhost named[16860]: listening on IPv4 interface eth0, 86.139                                             .30.251#53
Oct 12 22:58:49 localhost named[16860]: listening on IPv4 interface eth1, 192.16                                             8.10.1#53
Oct 12 22:58:49 localhost named[16860]: command channel listening on 127.0.0.1#9                                             53
Oct 12 22:58:49 localhost named[16860]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 12 22:58:49 localhost named[16860]: zone 127.in-addr.arpa/IN: loaded serial                                              1
Oct 12 22:58:49 localhost named[16860]: zone 10.168.192.in-addr.arpa/IN: loaded                                              serial 29
Oct 12 22:58:49 localhost named[16860]: zone 255.in-addr.arpa/IN: loaded serial                                              1
Oct 12 22:58:49 localhost named[16860]: zone ponywarshome.local/IN: loaded seria                                             l 63
Oct 12 22:58:49 localhost named[16860]: zone localhost/IN: loaded serial 1
Oct 12 22:58:49 localhost named[16860]: running
Oct 12 22:59:09 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:59:09 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:59:09 localhost dhclient: bound to 86.139.30.251 -- renewal in 29 seco                                             nds.
Oct 12 22:59:38 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 22:59:38 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 22:59:38 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seco                                             nds.
Oct 12 22:59:39 localhost dhcpd: removed reverse map on 198.10.168.192.in-addr.a                                             rpa.
Oct 12 22:59:39 localhost dhcpd: DHCPRELEASE of 192.168.10.198 from 00:09:5b:06:                                             0f:30 (wiggly) via eth1 (found)
Oct 12 22:59:44 localhost dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Oct 12 22:59:45 localhost dhcpd: DHCPOFFER on 192.168.10.198 to 00:09:5b:06:0f:3                                             0 (wiggly) via eth1
Oct 12 22:59:45 localhost dhcpd: added reverse map from 198.10.168.192.in-addr.a                                             rpa. to wiggly.ponywarshome.local
Oct 12 22:59:45 localhost dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) f                                             rom 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 22:59:45 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30                                              (wiggly) via eth1
Oct 12 22:59:47 localhost named[16860]: client 192.168.10.198#2106: update 'pony                                             warshome.local/IN' denied
Oct 12 23:00:05 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 23:00:05 localhost dhclient: DHCPACK from 192.168.1.1


no change to file

---

### Post by twistedtwig on 2006-10-12
looking at the output when wiggly requests a new ip it shoudl create a forward map.  but it doesnt seem to try... my this is confusing

---

### Post by Endwin on 2006-10-12
Oct 12 22:59:47 localhost named[16860]: client 192.168.10.198#2106: update 'pony warshome.local/IN' denied

Note the **pony warshome.local/IN** we have a space there that is bad, its trying to update the wrong zone....

Somewhere in either dhcpd.conf or named.conf.local you have a space that should not be there. Take a look through carefully and try and find it. 

I will be back in about an hour and 1/2 to help some more. The main idea is to check the logs look for strange things or problems with the files and resolve in inconsistancies.

---

### Post by twistedtwig on 2006-10-12
cool. thanks man.. cant see it anywhere, could be an odd character in it so going to retype all the ponywarshome.local 's to make sure.

ur a STAR btw :D:D:D

---

### Post by twistedtwig on 2006-10-12
ok so got rid of the space.  didnt see it anywhere but retyping them all seems to have got rid of it but the denied is still there.

> 
Oct 12 23:24:01 localhost named[17879]: no longer listening on 192.168.10.1#53
Oct 12 23:24:01 localhost named[17879]: exiting
Oct 12 23:24:03 localhost named[18089]: starting BIND 9.3.2 -u bind
Oct 12 23:24:03 localhost named[18089]: found 4 CPUs, using 4 worker threads
Oct 12 23:24:03 localhost named[18089]: loading configuration from '/etc/bind/named.conf'
Oct 12 23:24:03 localhost named[18089]: listening on IPv4 interface lo, 127.0.0.1#53
Oct 12 23:24:03 localhost named[18089]: listening on IPv4 interface eth0, 86.139.30.251#53
Oct 12 23:24:03 localhost named[18089]: listening on IPv4 interface eth1, 192.168.10.1#53
Oct 12 23:24:03 localhost named[18089]: command channel listening on 127.0.0.1#953
Oct 12 23:24:03 localhost named[18089]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 12 23:24:03 localhost named[18089]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 12 23:24:03 localhost named[18089]: zone 10.168.192.in-addr.arpa/IN: loaded serial 33
Oct 12 23:24:03 localhost named[18089]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 12 23:24:03 localhost named[18089]: zone ponywarshome.local/IN: loaded serial 63
Oct 12 23:24:03 localhost named[18089]: zone localhost/IN: loaded serial 1
Oct 12 23:24:03 localhost named[18089]: running
Oct 12 23:24:13 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 23:24:13 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 23:24:13 localhost dhclient: bound to 86.139.30.251 -- renewal in 31 seconds.
Oct 12 23:24:14 localhost dhcpd: removed reverse map on 198.10.168.192.in-addr.arpa.
Oct 12 23:24:14 localhost dhcpd: DHCPRELEASE of 192.168.10.198 from 00:09:5b:06:0f:30 (wiggly) via eth1 (found)
Oct 12 23:24:20 localhost dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Oct 12 23:24:21 localhost dhcpd: DHCPOFFER on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 23:24:21 localhost dhcpd: added reverse map from 198.10.168.192.in-addr.arpa. to wiggly.ponywarshome.local
Oct 12 23:24:21 localhost dhcpd: DHCPREQUEST for 192.168.10.198 (192.168.10.1) from 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 23:24:21 localhost dhcpd: DHCPACK on 192.168.10.198 to 00:09:5b:06:0f:30 (wiggly) via eth1
Oct 12 23:24:23 localhost named[18089]: client 192.168.10.198#2362: update 'ponywarshome.local/IN' denied
Oct 12 23:24:44 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 12 23:24:44 localhost dhclient: DHCPACK from 192.168.1.1
Oct 12 23:24:44 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.


the named process (if thats what it is, think i am reading that correctly) seems to be able to update things fine.  although db.ponywars had less rights than the others (775) so i changed it so it also had 775.

but as u can see it still doesnt like updating ponywarshome.local bit.

i am afraid i am going to have to hit the sack now (11:30pm) i have a job interview at 10am so must get a bit of sleep.  

THANK YOU SO MUCH FOR YOUR HELP SO FAR... i do get it more now and understand a little better about how to de bug things.  Fingers crossed I / we can solve it tomorrow.. its SOOO frustrating.

Cheers

Twiggy

---

### Post by twistedtwig on 2006-10-13
dont know if this means much but when i did a release renew from bobby (sbs2003 server) i get this:

> Oct 13 08:45:35 localhost dhcpd: DHCPRELEASE of 192.168.10.100 from 00:08:54:44:75:10 via eth1 (not found)
Oct 13 08:45:41 localhost dhcpd: DHCPDISCOVER from 00:08:54:44:75:10 via eth1
Oct 13 08:45:41 localhost dhcpd: DHCPOFFER on 192.168.10.100 to 00:08:54:44:75:10 via eth1
Oct 13 08:45:41 localhost dhcpd: added reverse map from 100.10.168.192.in-addr.arpa. to bobby.ponywarshome.local
Oct 13 08:45:41 localhost dhcpd: DHCPREQUEST for 192.168.10.100 (192.168.10.1) from 00:08:54:44:75:10 via eth1
Oct 13 08:45:41 localhost dhcpd: DHCPACK on 192.168.10.100 to 00:08:54:44:75:10 via eth1
Oct 13 08:45:43 localhost named[2733]: client 192.168.10.100#1043: update 'ponywarshome.local/IN' denied
Oct 13 08:45:43 localhost named[2733]: client 192.168.10.100#1043: update 'ponywarshome.local/IN' denied
Oct 13 08:45:46 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct 13 08:45:46 localhost dhclient: DHCPACK from 192.168.1.1
Oct 13 08:45:46 localhost dhclient: bound to 86.139.30.251 -- renewal in 27 seconds.


i get denied twice.  There is only one network card in there.. but odd that.

i am getting to the point of thinking i should retype ALL the files to ensure there are no ODD characters in there that i cant see

should there be the speak marks ' around ponywarshome.local/IN?  cant see it doing that anywhere else in the whole process?

---

### Post by Endwin on 2006-10-13
It might be a a good idea to retype the stuff from the looks of it it is happy and working the DHCP server just can't update the DNS  for that reccord because it can't authenticate itself. 

One thing to try is to add 192.168.10.1 to the list of things that can update the DNS in /etc/bind/named.conf it may be trying to update on that interface as opposed to the loopback one.

If that fails it looks like retyping would be a good idea. 


Namely you want to change...

```
controls {
inet 127.0.0.1 allow { 127.0.0.1; } keys { "rndc-key"; };
};

```

to...
```

controls {
inet 127.0.0.1 allow { 127.0.0.1; 192.168.10.1; } keys { "rndc-key"; };
};
```


To have an idea of what it should look like in daemon.log this is what my log looks like.

```
Oct 12 21:35:46 guardian named[11901]: client 10.10.0.1#33654: updating zone '0.10.10.in-addr.arpa/IN': deleting rrset at '249.0.10.10.in-addr.arpa' PTR
Oct 12 21:35:47 guardian named[11901]: client 10.10.0.1#33654: updating zone 'alefgard.com/IN': adding an RR at 'Margaritaville.alefgard.com' A
Oct 12 21:35:47 guardian named[11901]: client 10.10.0.1#33654: updating zone 'alefgard.com/IN': adding an RR at 'Margaritaville.alefgard.com' TXT
Oct 12 21:35:47 guardian named[11901]: client 10.10.0.1#33654: updating zone '0.10.10.in-addr.arpa/IN': deleting rrset at '249.0.10.10.in-addr.arpa' PTR
Oct 12 21:35:47 guardian named[11901]: client 10.10.0.1#33654: updating zone '0.10.10.in-addr.arpa/IN': adding an RR at '249.0.10.10.in-addr.arpa' PTR

```

---

### Post by twistedtwig on 2006-10-13
just noticed something VERY odd.

> 
Oct 13 15:14:36 localhost dhcpd: DHCPOFFER on 192.168.10.196 to 00:0d:88:93:3f:bd (dalecomputer) via eth1
Oct 13 15:14:36 localhost named[2733]: journal file /etc/bind/db.ponywarshome.jnl does not exist, creating it
Oct 13 15:14:36 localhost dhcpd: Added new forward map from dalecomputer.ponywarshome.local to 192.168.10.196
Oct 13 15:14:36 localhost named[2733]: journal file /etc/bind/db.10.168.192.jnl does not exist, creating it
Oct 13 15:14:36 localhost dhcpd: added reverse map from 196.10.168.192.in-addr.arpa. to dalecomputer.ponywarshome.local
Oct 13 15:14:36 localhost dhcpd: DHCPREQUEST for 192.168.10.196 (192.168.10.1) from 00:0d:88:93:3f:bd (dalecomputer) via eth1
Oct 13 15:14:36 localhost dhcpd: DHCPACK on 192.168.10.196 to 00:0d:88:93:3f:bd (dalecomputer) via eth1


doing an update on boys computers (which are NOT on the windows domain yet, so still on the work group) and they got added properly to the db.ponywarshome.local

they are on wireless but cant think thats it.  i think its the fact that they havent joined the domain

---

### Post by Endwin on 2006-10-13
Your runing a windows domain? That could be part of our problem right there. The wondows domain is handling some of the DNS stuff and that is why it is conflicting with the other things....

---

### Post by twistedtwig on 2006-10-13
I uninstalled the acutal DNS server from the windows server (sbs2003) thinking that might have been it yesterday but obviously it didnt work.

dont suppose u have any ideas from this point?  only built the sbs2003 machine this week as a test to see what it does and get used to using one.

---

### Post by twistedtwig on 2006-10-13
so yep its deffently the windows domain controller (or something on bobby / sbs2003) that is causing the issue.  changed felix back to workgroup and it worked fine when i did a release and renew

but i honestly cant see what would be causing this really.  i have removed the dns server, EVERYTHING gets its dns records from betty (ubuntu server)............ but.. if it is in the domain maybe it requests everything from sbs2003 then that requests it from ubuntu server.....

still dont get why that would mean ubuntu server couldnt update the  jnl file though

---

### Post by Endwin on 2006-10-13
It would take some research into how windows domains work. From what I know (which isn't a whole lot) they do a lot of the network setup for you on machines that join. One thing you could try is adding the windows domain to the list of comps allowed to update the DNS and see what that does. However I am not sure as to the cause without some research. 

At lease we found out WHY it was messing up. All we need to do now is figure out how to get your domain server and the DHCP/DNS server to play nicely together.

---

### Post by twistedtwig on 2006-10-13
a REALLY bad work around could be a use dhcp but set static IP's for any computers i know i will want to terminal into but still allowing people to join the network easily enough.. but that is SUCH a bodge


EDIT: thats worth a try.. hehe.. and yep it feel REALLY good to at least know why its doing what its doing

Cheers

---

### Post by twistedtwig on 2006-10-13
looking at the logging it is saying there is a prerequisite not satisified

> 13-Oct-2006 19:24:26.581 update: info: client 127.0.0.1#32771: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '99.10.168.192.in-addr.arpa' PTR
13-Oct-2006 19:24:26.581 update: info: client 127.0.0.1#32771: updating zone '10.168.192.in-addr.arpa/IN': adding an RR at '99.10.168.192.in-addr.arpa' PTR
13-Oct-2006 19:24:26.602 update: info: client 192.168.10.99#1402: updating zone 'ponywarshome.local/IN': update unsuccessful: wiggly.ponywarshome.local/A: 'RRset exists (value dependent)' prerequisite not satisfied (NXRRSET)



found this:

> Q: I keep getting log messages like the following.  Why?

   Dec  4 23:47:59 client 10.0.0.1#1355: updating zone 'example.com/IN':
   update failed: 'RRset exists (value dependent)' prerequisite not
   satisfied (NXRRSET)

A: DNS updates allow the update request to test to see if certain
conditions are met prior to proceeding with the update.  The message
above is saying that conditions were not met and the update is not
proceeding.  See doc/rfc/rfc2136.txt for more details on prerequisites.

will keep looking into it :)

cant locate that file on my computer but searching online

[http://www.faqs.org/rfcs/rfc2136.html](http://www.faqs.org/rfcs/rfc2136.html)
> 2.4.2 - RRset Exists (Value Dependent)

   A set of RRs with a specified NAME and TYPE exists and has the same
   members with the same RDATAs as the RRset specified here in this
   section.  While RRset ordering is undefined and therefore not
   significant to this comparison, the sets be identical in their
   extent.

   For this prerequisite, a requestor adds to the section an entire
   RRset whose preexistence is required.  NAME and TYPE are that of the
   RRset being denoted.  CLASS is that of the zone.  TTL must be
   specified as zero (0) and is ignored when comparing RRsets for
   identity.


not fully sure what that means to be honest but hoping someeone else might, i think it maybe important

>     NXRRSET     8       Some RRset that ought to exist,
                        does not exist.


---

### Post by Endwin on 2006-10-13
Could it be that the domain nedds to BE ponywarshome.lan on the windows domain for this to work? Windows may not even allow a .lan extension and only one of the stock domain name extensions.

---

### Post by twistedtwig on 2006-10-19
interestingly i found this error:

> 
root@betty:/home/jon# /etc/init.d/bind9 restart
 * Stopping domain name service...                                                                                            rndc: connect failed: connection refused
                                                                                                                       [ ok ]
 * Starting domain name service...                                                                                     [ ok ]
root@betty:/home/jon# named -g -p 53
19-Oct-2006 10:33:05.651 starting BIND 9.3.2 -g -p 53
19-Oct-2006 10:33:05.652 found 4 CPUs, using 4 worker threads
19-Oct-2006 10:33:05.665 loading configuration from '/etc/bind/named.conf'
19-Oct-2006 10:33:05.670 listening on IPv4 interface lo, 127.0.0.1#53
19-Oct-2006 10:33:05.671 binding TCP socket: address in use
19-Oct-2006 10:33:05.671 listening on IPv4 interface eth0, 86.132.250.153#53
19-Oct-2006 10:33:05.672 binding TCP socket: address in use
19-Oct-2006 10:33:05.672 listening on IPv4 interface eth1, 192.168.10.1#53
19-Oct-2006 10:33:05.673 binding TCP socket: address in use
19-Oct-2006 10:33:05.683 /etc/bind/named.conf:41: couldn't add command channel 127.0.0.1#953: address in use
19-Oct-2006 10:33:05.683 ignoring config file logging statement due to -g option
19-Oct-2006 10:33:05.686 zone 0.in-addr.arpa/IN: loaded serial 1
19-Oct-2006 10:33:05.688 zone 127.in-addr.arpa/IN: loaded serial 1
19-Oct-2006 10:33:05.690 zone 10.168.192.in-addr.arpa/IN: loaded serial 103
19-Oct-2006 10:33:05.692 zone 255.in-addr.arpa/IN: loaded serial 1
19-Oct-2006 10:33:05.693 /etc/bind/db.ponywarshome:10: unknown RR type 'ponywarshome.local.'
19-Oct-2006 10:33:05.693 zone ponywarshome.local/IN: loading master file /etc/bind/db.ponywarshome: unknown class/type
19-Oct-2006 10:33:05.695 zone localhost/IN: loaded serial 1
19-Oct-2006 10:33:05.697 running


not that i know what an RR type is yet :P
will look into this further :)

---

### Post by twistedtwig on 2006-10-19
found this link

[http://www.daniweb.com/techtalkforums/thread19915.html](http://www.daniweb.com/techtalkforums/thread19915.html)

that talks about permissions being the issue and named needs to own the group for a couple of files.  so i tried the command chown root:named rndc.key but get the following error

chown: `root:named': invalid group

any ideas please?

---

### Post by Endwin on 2006-10-19
The group that controls DNS is bind not named. My entire /etc/bind dir is set to (including the directory itself) to be owned by bind and owned by the group bind. That way I know bind would have no problems with it.

---

### Post by twistedtwig on 2006-10-19
ok,..... so the error would seem to lay within this RR type thingy then.  right time to investigate some more

---

### Post by djdvant on 2008-04-24
After much hair pulling over several months I finally got to the problem.  My DNS and DHCP files were OK and always had been.

I finally tracked down an kernel audit message


kernel:  audit(1209076817.081:16): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/etc/bind/xxxxx.com.hosts.jnl" pid=16561 profile="/usr/sbin/named" namespace="default"

So I had a look in:
/etc/apparmor.d/usr.sbin.named

and changed this line:
  /etc/bind/** r,

to this:
  /etc/bind/** rw,

End of problems

---

### Post by qhartman on 2008-04-26
thanks for posting your solutions, but consider also moving your zone info to /var/lib/bind, where apparmor is expecting it to be. That might be a considered a "better" solution.

---

