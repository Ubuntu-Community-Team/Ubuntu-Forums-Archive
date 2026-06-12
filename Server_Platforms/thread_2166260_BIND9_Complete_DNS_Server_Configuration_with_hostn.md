---
title: "BIND9 Complete DNS Server Configuration with hostname step by step"
date: 2013-08-08
forum: Server Platforms
---

### Post by Profark on 2013-08-08
Complete DNS server in ubuntu server 12.

First of all change the ip address of your server form DHCP to STATIC for this use the following command

```
sudo nano /etc/network/interfaces
```

```
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
# dns-nameservers

```
[SIZE=1]****I am leaving dns-nameserver empty and is commented we will come to it later.***[/SIZE]

 
**Restart networking daemons**

```
Sudo /etc/init.d/networking restart

```
Before configuring a DNS server in linux Ubuntu you have to make domain name first and then you will proceed. First you will check your hostname command for this is

```
Sudo nano /etc/hostname
```
My Server has the following name
```
nefitari 
```

(This is my Ubuntu server hostname yours might be different .You can change this according to your need)

Now after hostname, you have to make domain name for your server. Say servername.domain.com it is better practice that whenever you are configuring server for home use or so, do not use .com but .hom or .net or whatever you like. Give the below command

```
Sudo nano /etc/hosts
```

```
127.0.0.1 localhost
192.168.1.5 nefitari.autun.hom nefitari

```
In my file 127.0.0.1 is for localhost and I have changed the second IP address 127.0.1.1 with my server IP that is 192.168.1.5 now I enter my domain name having my hostname **nefitari** first then my domain name **autun.hom** and then alias **nefitari**. You can select of your own, hostname.abc.net or hostname.home.lan etc. but remember changing to this file need to restart your server and then login. Restart is must
**[SIZE=3]Now install BIND9[/SIZE]**

```
Sudo apt-get install bind9
```

After installation just configure the below files step by step

     
[LIST]
[*]Named.conf.options 
[*]Named.conf.local 
[*]Named.conf.resolv.conf 
[/LIST]
 
Now configure file **named.conf.options** This file is use for DNS IPs It mean that your server must connect to some DNS outside. When you buy domain name from ISP’s they normally gives you their own DNS IPs. You can use open DNS IPs of google or so. In my case I am using my own ISP DNS IPs.

```
Sudo nano /etc/bind/named.conf.options
```
```
forwarders {
# Give here your ISP DNS IP’s
192.168.1.1; # gateway or router
182.176.39.23;
182.176.18.13;
68.87.76.178;
};
```

**Save the file and exit using** control x press y and overwrite the file

Now edit the file **named.conf.local** This is the file in which we define forward zones and reverse zones. It means that when we enter domain name it will translate it into IP address and when we enter IP address it will simply convert it into name.

```
Sudo nano /etc/bind/named.conf.local
```
```
# Our forward zone
zone "autun.hom" {
type master;
file "/etc/bind/zones/db.autun.hom";
};

# Our reverse Zone
# Server IP 192.168.1.5
zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/db.192";
};
```

Save the file and exit using control x press y and overwrite the file

Now we will make these two database files **db.autun.hom** and **db.192** in zones folder

First make the directory zones in /etc/bind/

```
Sudo mkdir /etc/bind/zones
```

Before making files let me clear you that I have different devices
                Devices            IPs

    Server itself     192.168.1.5
    Gateway         192.168.1.1
    Win7pc           192.168.1.50


Now in zones directory we will create two files first db.autun.hom. I am just copying the db.local already present in /etc/bind folder to zones folder by changing its name to db.autun.hom. I will put these IP’s in my db.autun.hom file. Let’s start

```
Sudo cp /etc/bind/db.local /etc/bind/zones/db.autun.hom
```

Now use the command below to edit the file

```
Sudo nano /etc/bind/zones/db.autun.hom

```
```
;
; BIND data file for local loopback interface
;
$TTL 604800
@        IN         SOA            nefitari.autun.hom. webuser.autun.hom. (
2 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
autun.hom.            IN          NS           nefitari.autun.hom.
autun.hom.            IN          A             192.168.1.5
;@                       IN          A             127.0.0.1
;@                       IN          AAAA        ::1
nefitari                  IN          A            192.168.1.5
gateway                IN          A            192.168.1.1
win7pc                  IN          A            192.168.1.50
www                     IN         CNAME      autun.hom.
```

Save it and exit

    **Webuser.autun.hom.** is the email who will access name server. You can write any name instead webuser like admin, root or host master etc.
    **Autun.hom.** is my NS means name server
    **Autun.hom.**changing to IP 192.168.1.5

   ** @ IN A 127.0.0.1 and AAAA ::1 **can be comment out you should not need it because db.local is already present in /etc/bind it is just a copy of that file. So no need you can delete it

    Changing** Nefitari** to IP 192.168.1.5

    **Gateway **to IP 192.168.1.1

    **Win7pc** you can name your windows PCs or Linux Clients to any name but remember IP of that client must correctly be inserted into file. In my case I gave IP of windows PC 192.168.1.50

    Last, I am using **CNAME** means canonical name it is just an alias to nefitari. Means that you can access your server by entering [www.autun.hom]("http://www.autun.hom") instead nefitari.autun.hom . You can omit this or comment it. It is just up to you.


**Now create reverse lookup zone file**

```
Sudo cp /etc/bind/db.127 /etc/bind/zones/db.192
```

Now use the command below to edit the file

```
Sudo nano /etc/bind/zones/db.192
```
```
;
; BIND reverse data file for local loopback interface
;
$TTL 604800
@                IN             SOA               nefitari.autun.hom. webuser.autun.hom. (
2 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
                 IN               NS            nefitari.
1                IN              PTR           gateway.autun.hom.
5                IN              PTR           nefitari.autun.hom.
50             IN               PTR            win7pc.autun.hom.
```

**Save it and exit**

Now when you are done with your zone file you have to check it whether it is working correctly or not by entering the command below for forward zone file

```
named-checkzone autun.hom /etc/bind/zones/db.autun.hom
```
Output
```
zone autun.hom /IN: loaded serial 2
Ok
```

**Now check the reverse zone file**

```
named-checkzone autun.hom /etc/bind/zones/db.192
```
Output
```
zone autun.hom /IN: loaded serial 2
Ok 
```

If the output of your named-checkzone is same as above then it is working fine otherwise you made some mistake in file.

**Now edit the file resolv.conf**

```
Sudo nano /etc/resolv.conf
```

```
Nameserver 192.168.1.5
domain autun.hom
search autun.hom
```

Enter the following lines into to your resolv.conf file and save it

Now come to** dns-nameservers** (/etc/networking/interfaces) *[SIZE=1]check start of the this post[/SIZE]
you will now add the following code to** /etc/networking/interfaces**
```
dns-nameservers 192.168.1.5
```
reason for this is that whenever you restart server** /etc/resolv.conf** file wash its contents
[B][SIZE=2]Restart the bind
[/SIZE][/B]
```
sudo /etc/init.d/bind9 restart
```

After bind start check your setting in log file

```
tail -f /var/log/syslog
```

it must not have any error in the log
**[SIZE=3]Checking forward zones[/SIZE]**

```
host –l autun.hom
```

Output should like this

```
autun.hom name server nefitari.autun.hom.
autun.hom has address 192.168.1.5
gateway.autun.hom has address 192.168.1.1
nefitari.autun.hom has address 192.168.1.5
win7pc.autun.hom has address 192.168.1.50
```

Now use** NSLOOKUP**

```
nslookup autun.hom
```

OUTPUT

```
Server: 192.168.1.5
Address: 192.168.1.5#53

Name: autun.hom
Address: 192.168.1.5

```
Use **DIG**

```
Dig gateway.autun.hom
```

```
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 35612
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;gateway.autun.hom IN A

;; ANSWER SECTION:
gateway.autun.hom 604800 IN A 192.168.1.1

;; AUTHORITY SECTION:
Autun.hom. 604800 IN NS nefitari.autun.hom.

;; ADDITIONAL SECTION:
Nefitari.autun.hom. 604800 IN A 192.168.1.5

;; Query time: 12 msec
;; SERVER: 192.168.1.5#53(192.168.1.5)
;; WHEN: Thu Aug 8 01:56:25 2013
;; MSG SIZE rcvd: 90
```

Output should similar to the above, check **status: NOERROR** means it is resolving check **ANSWER SECTION:** gateway.autun.hom is resolved into 192.168.1.1
[B][SIZE=3]Checking reverse zone
[/SIZE][/B]
```
host 192.168.1.1
```

Output

```
1.1.168.192.in-addr.arpa domain name pointer gateway.autun.hom

```
If it gives you an error like below

```
host 1.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)

```
This means that you made some mistake in **/etc/bind/named.conf.local** file in reverse zone If your server IP is 192.168.1.5 then your reverse zone looks like this

zone "**1.168.192**.in-addr.arpa" {
correct ip reversing
};

Sometime people made mistake in reversing the ip like (just an example)

zone "**0.168.192**.in-addr.arpa" {
incorrect ip reversing
};

Use **NSLOOKUP**

```
nslookup 192.168.1.1
```

```
Server: 192.168.1.5
Address: 192.168.1.5#53

1.1.168.192.in-addr.arpa name=gateway.autun.hom
```

**[SIZE=2]If you get NXDOMAIN or SERVFAIL like errors it means that one of your zone file is not working correctly[/SIZE]**

**[SIZE=3]Test Your Server to Outside World[/SIZE]**
Now you can** ping ubuntu.com **or **dig ubuntu.com **for the first time it will take **several miliseconds** to resolve the name ubuntu.com but when you run it **second** time, it will take **form 1 to 10 mili seconds, **its normal time and it means that your DNS is working properly
**[SIZE=3]Configuring clients[/SIZE]**

**windows side**

    open** network connections**
    select **change adapter settings**
    select **properties**
    select **internet protocol version IPv4**


and here give the IP address (in my case it is 192.168.1.50 have you remember win7pc)

    **IP address** 192.168.1.50
    **Subnet Mask **255.255.255.0
   ** Default Gateway **192.168.1.1
   ** primary DNS** 192.168.1.5 (my new BIND DNS server ip)
    select **Advance **(in the same window)
    select **DNS** tab
    Type in the text box below here In **DNS Suffix for this connection:autun.hom**
    click **ok**
    click on **validate setting upon exit**
    click **ok**


and you are done with it open **CMD**

```
ping gateway
```

it must gives you some replies

similarly

```
ping 192.168.1.1 or 5
```

it must gives you some replies
you can use** NSLOOKUP**
```
nslooup gateway
```
**[SIZE=3]LINUX CLIENTS[/SIZE]**

```
sudo nano /etc/network/interfaces
```
type the following lines
```
auto eth0
iface eth0 inet dhcp
```
Now restart Network Deamons
```
Sudo /etc/init.d/networking restart
```
to force client renew IP command
```
sudo dhclient -r
```
Now obtain fresh IP:
```
sudo dhclient
```

*[SIZE=2]If you are running DHCP server on your system then enter the domain name and name server in dhcpd.conf file for example I have DNS server named nefitari.autun.hom and IP address is 192.168.1.5 like as under[/SIZE]*

```
option domain-name “nefitari.autun.hom”;
option domain-name-server  192.168.1.5; 
```
**[SIZE=3]How to enable query logging in BIND[/SIZE]**
To enable query logging execute rndc querylog command:
```
Sudo rndc querylog
```
Check out query logging status by executing command:
```
Sudo rndc status
```
Now you can view queries:
```
tail -f /var/log/syslog
```
To disable it execute command again. 
```
Sudo rndc querylog
```

**[SIZE=3]Our own Query Logging in BIND[/SIZE]**

```
Sudo nano /etc/bind/named.conf.local
```
Add the following lines at the bottom of the file. You can use any channel to produce log file. You can use more than one channel as well. 
```
logging {
    channel mylog_default {
        file "/var/log/mylogs/mylog.log" versions 3 size 12m;
        severity dynamic;
        print-time yes;
    };
category default { mylog_default; };
};

```
After saving the file go to /var/log/ and make a mylogs folder and give it bind permission so that bind can write to it.
```
Sudo mkdir /var/log/mylogs
```
```
sudo chown bind:bind /var/log/mylogs
```
Now after this you can make file mylog.log by using sudo nano mylog.log and save it in the directory mylogs or when you edit Apparmor it create the file automatically after restarting the bind, **But at this time when you restart the bind it will not start and show fail**. Because before named daemon can write to the new log file the AppArmor profile must be updated. First, edit 
```
Sudo nano /etc/apparmor.d/usr.sbin.named 
```
And add: 
```
/var/log/mylogs/mylog.log w,
```
Next, reload the profile: 
```
sudo cat /etc/apparmor.d/usr.sbin.named | sudo apparmor_parser -r
```
It may give you some warnings 
**Now restart bind**
```
Sudo /etc/init.d/bind9 restart
```
To check logs 
```
Tail –f /var/log/mylogs/mylog.log
```

---

### Post by Cheesemill on 2013-08-08
A couple of remarks.

First of all you shouldn't ever edit /etc/resolv.conf as it gets created fresh every time you restart the machine. Instead you should add DNS information in the /etc/networking/interfaces file like this...
```
dns-nameservers     192.168.1.5
```
(notice that it's dns-nameservers not dns-nameserver as you've written)

Also unless you need the advanced features of bind such as MX records then all of this can be done by just installing the dnsmasq package and adding your hosts to the /etc/hosts file.

---

### Post by Profark on 2013-08-08
Thanks, i think its just for the beginners i will advance it slowly and gradually. yes /etc/resolv.conf wipe out after restart because it is normally controlled by network manager. you can add dns-nameservers to /etc/networking/interfaces this correct.

---

