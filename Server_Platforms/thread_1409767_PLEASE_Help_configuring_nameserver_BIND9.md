---
title: "PLEASE Help configuring nameserver BIND9"
date: 2010-02-18
forum: Server Platforms
---

### Post by Oxycodone on 2010-02-18
I have spent over 40 hours over the last two weeks trying to set my nameserver up on ubuntu 9.10 server. I am currently running XAMPP and have confirmed it is currently hosting the temp page I created through my IP ###.###.###.###, however BIND9 is not resolving the domain name.  I think I'm finally going nuts and am seeking assistance.

I purchased the domain "OXYCODONE.ME" through godaddy and created two hosts "NS1" & "NS2" in the domain manager:

[IMG]http://img59.imageshack.us/img59/3568/hosts.jpg[/IMG]

I then changed my domain nameservers to point to my nameserver:

[IMG]http://img203.imageshack.us/img203/1580/nameservers.jpg[/IMG]

I have forwarded port 53 in my router:

[IMG]http://img704.imageshack.us/img704/4821/routert.jpg[/IMG]

**_CONFIGURATION FILES_**


_/etc/resolv.conf_
search oxycodone.me
nameserver 192.168.1.151


_/etc/bind/named.conf.local_
zone "oxycodone.me" {
        type master;
        file "/etc/bind/db.oxycodone.me";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};


_/etc/bind/db.192_
$TTL    604800
@       IN      SOA     ns1.oxycodone.me. hostmaster.oxycodone.me. (
                     2010021710         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

@       IN      NS      ns1.oxycodone.me.

151     IN      PTR     ns1.oxycodone.me.
150     IN      PTR     mail.oxycodone.me.


_/etc/bind/db.oxycodone.me_
$TTL    604800
@       IN      SOA     ns1.oxycodone.me. hostmaster.oxycodone.me. (
                     2010021711         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

@       IN      NS      ns1
@       IN      MX      10 mail.oxycodone.me.

@       IN      A       192.168.1.150
ns1     IN      A       192.168.1.151
mail    IN      A       192.168.1.150
www     IN      CNAME   ns1


_dig oxycodone.me_
; <<>> DiG 9.6.1-P1 <<>> oxycodone.me
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18219
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;oxycodone.me.                  IN      A

;; ANSWER SECTION:
oxycodone.me.           604800  IN      A       192.168.1.150

;; AUTHORITY SECTION:
oxycodone.me.           604800  IN      NS      ns1.oxycodone.me.

;; ADDITIONAL SECTION:
ns1.oxycodone.me.       604800  IN      A       192.168.1.151

;; Query time: 0 msec
;; SERVER: 192.168.1.151#53(192.168.1.151)
;; WHEN: Wed Feb 17 23:09:27 2010
;; MSG SIZE  rcvd: 80


_dig -x 192.168.1.151_
; <<>> DiG 9.6.1-P1 <<>> -x 192.168.1.151
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10141
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;151.1.168.192.in-addr.arpa.    IN      PTR

;; ANSWER SECTION:
151.1.168.192.in-addr.arpa. 604800 IN   PTR     ns1.oxycodone.me.

;; AUTHORITY SECTION:
1.168.192.in-addr.arpa. 604800  IN      NS      ns1.oxycodone.me.

;; ADDITIONAL SECTION:
ns1.oxycodone.me.       604800  IN      A       192.168.1.151

;; Query time: 0 msec
;; SERVER: 192.168.1.151#53(192.168.1.151)
;; WHEN: Wed Feb 17 23:10:03 2010
;; MSG SIZE  rcvd: 104

---

### Post by cariboo on 2010-02-18
I have to ask why you are going to the trouble, when you've already set things up via Godaddy, it takes about 48 hours for all the major dns servers to know that OXYCODONE.ME is located at 24.131.153.132. If the domain name doesn't work after 48 hours, give Godaddy support a call. You paid for the service, you might as well use it.

---

### Post by Oxycodone on 2010-02-18
cariboo907 thanks for the reply.  I configured the  host/nameserver on godaddy over 2 weeks ago.  I actually had it resolving the webpage correctly about a week ago when I had ISPconfig 3 installed.  The HDD running my ubuntu server was very old and crashed, thus needed to set my nameserver again with this new HDD.  ISPConfig 3 uses MyDNS and the setup was done through a gui.  I decided to use bind9 this time around as I have already configured my windows box with XAMPP.

---

### Post by Oxycodone on 2010-02-18
I have changed this domain back to the godaddy nameservers and changed the records through total dns.  I would really like to figure out why my nameserver was not resolving this page.  If someone knows why, please let me know!! Thanks!

---

### Post by mbaas on 2010-02-18
Hello,

You appear to be pointing to your LAN ip adresses (192.168.1.150 and 192.168.1.151). Reserved IP ranges cannot be reached from the internet. Your DNS should be pointing to your WAN ip adress.

---

### Post by Oxycodone on 2010-02-18
I appreciate the response Mbaas.  I suspected the same and changed the settings accordingly however must be missing something... Perhaps you could take the time to modify the configuration files I listed to show me what I am doing wrong?  Thanks either way.

---

### Post by progone on 2011-04-16
dyndns.com might be what you are looking for.  If you own a linksys router, you can create a **webhop** from dyndns to forward to your home server.

Once you get a free or paid account setup with them, go to Synaptic Package manager and type in ddclient and download or type$ sudo apt-get install ddclient
The description: This package provides a client to update dynamic IP addresses with
several dynamic DNS service providers, such as DynDNS.com.

This makes it possible to use a fixed hostname (such as
myhost.dyndns.org) to access a machine with a dynamic IP address.

This client supports both dynamic and (near) static services, as  well as
MX record and alternative name management. It caches the address, and
only attempts the update when it has changed."

Good luck with this.  Depending on your ISP and your router the setup may vary.

---

