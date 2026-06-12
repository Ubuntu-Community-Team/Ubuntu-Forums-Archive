---
title: "DNS configuration problem in ubuntu serv. 8.04.4 lts."
date: 2012-06-27
forum: Server Platforms
---

### Post by paramvirsinh on 2012-06-27
Dear Friends,

I have problem with DNS configuration in ubuntu server 8.04 lts.

I am using zimbra 6.0.16.

The scenario is described as below.

Steps:

1). First of all i have changed /etc/bind/named.conf. file with 
    
    [B]forwarders {
                <ip addresses of pc>
           };[/B]


2). Then restarted the DNS server.

sudo /etc/init.d/bind9 restart

it reflects no error in both steps.

3). Checked the /etc/resolv.conf file

nameserver xxx.xxx.xxx.xxx


4). Then configured BIND9 with my FQDN. 

In /etc/bind/named.conf.local file

[B]zone "******" {
    type master;
        file "/etc/bind/db.******";
};[/B]


5). Then created the template with this command.

**sudo cp /etc/bind/db.local /etc/bind/db.example.com**

6). Then edited the new zone file with below changes.

[B];
; BIND data file for mydomain.com
;
$TTL    604800
@       IN           SOA     mail.mydomain.com. admin.mydomain.com. (
                                                                         6         ;               Serial
                                                          604800         ;               Refresh
                                   86400         ;               Retry
                                                       2419200         ;               Expire
                                 604800 )       ;             Negative Cache TTL
;
@               IN               NS                 mail
                      IN                 MX                10 mail
                      IN                A             xxx.xxx.xxx.xxx
mail         IN          A                     xxx.xxx.xxx.xxx
[/B] 

7). Then /**etc/init.d/bind9** restart

8). Edited reverce zone file  /etc/bind/named.conf.local with

[B]zone "*.***.***.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};[/B]


9). sudo **cp /etc/bind/db.127 /etc/bind/db.192**


10). created a PTR record in /etc/bind/db.192. 


[B];
; BIND reverse data file for local loopback interface
;
$TTL    604800
@         IN         SOA         ns.******.    root.******. (
                                                                           3         ;    Serial
                             604800         ;   Refresh
                                                            86400         ;   Retry
                                                     2419200        ;   Expire
                                                         604800  )     ;  Negative Cache TTL
;
@            IN         NS         ns.
10         IN        PTR       ns.******.[/B]

11). sudo /etc/init.d/bind9 restart


Then I have fired the dig command


**dig @<ipaddress of name server> <hostname><domain name>**


But it reflects the error like

[B]global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: [/B][B]SERVFAIL, id: 6672
[/B] 
Any help will be appreciated.

---

### Post by SeijiSensei on 2012-06-27
If the forwarders are defined globally, then I don't think the server will pay attention to the local zone files.  [Generally speaking]("http://ubuntuforums.org/showthread.php?t=2008326") you don't need to use forwarders; just let your server talk directly the root nameservers.

---

