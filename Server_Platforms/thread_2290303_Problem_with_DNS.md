---
title: "Problem with DNS"
date: 2015-08-11
forum: Server Platforms
---

### Post by Valery_Maslov on 2015-08-11
I have a DNS server on Ubuntu.
Recently one website youtube.com resolves as 127.0.0.1
Folder bind checked. Nowhere such rules are not spelled out. All the other sites without problems.

[COLOR=#333333][FONT=PT Sans]dns1:~$ nslookup youtube.com[/FONT][/COLOR]
[COLOR=#333333][FONT=PT Sans]Server: 127.0.0.1[/FONT][/COLOR]
[COLOR=#333333][FONT=PT Sans]Address: 127.0.0.1#53[/FONT][/COLOR]

[COLOR=#333333][FONT=PT Sans]Non-authoritative answer:[/FONT][/COLOR]
[COLOR=#333333][FONT=PT Sans]Name: [/FONT][/COLOR][COLOR=#333333][FONT=PT Sans]youtube[/FONT][/COLOR][COLOR=#333333][FONT=PT Sans].com[/FONT][/COLOR]
[COLOR=#333333][FONT=PT Sans]Address: 127.0.0.1[/FONT][/COLOR]


[FONT=arial]@dns1:~$ dig [youtube.com]("http://youtube.com/")[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]; <<>> DiG 9.8.1-P1 <<>> [youtube.com]("http://youtube.com/")[/FONT]
[FONT=arial];; global options: +cmd[/FONT]
[FONT=arial];; Got answer:[/FONT]
[FONT=arial];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36035[/FONT]
[FONT=arial];; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial];; QUESTION SECTION:[/FONT]
[FONT=arial];[youtube.com]("http://youtube.com/").                   IN      A[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial];; ANSWER SECTION:[/FONT]
[FONT=arial][youtube.com]("http://youtube.com/").            25326   IN      A       127.0.0.1[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial];; AUTHORITY SECTION:
[youtube.com]("http://youtube.com/").            25326   IN      NS      [server.yourdomain.com]("http://server.yourdomain.com/").


;; Query time: 5 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Aug 11 13:38:26 2015
;; MSG SIZE  rcvd: 77

@dns1:~$ dig [youtube.com]("http://youtube.com/") +trace


; <<>> DiG 9.8.1-P1 <<>> [youtube.com]("http://youtube.com/") +trace
;; global options: +cmd
.                       4664    IN      NS      [m.root-servers.net]("http://m.root-servers.net/").
.                       4664    IN      NS      [i.root-servers.net]("http://i.root-servers.net/").
.                       4664    IN      NS      [h.root-servers.net]("http://h.root-servers.net/").
.                       4664    IN      NS      [b.root-servers.net]("http://b.root-servers.net/").
.                       4664    IN      NS      [j.root-servers.net]("http://j.root-servers.net/").
.                       4664    IN      NS      [a.root-servers.net]("http://a.root-servers.net/").
.                       4664    IN      NS      [k.root-servers.net]("http://k.root-servers.net/").
.                       4664    IN      NS      [e.root-servers.net]("http://e.root-servers.net/").
.                       4664    IN      NS      [g.root-servers.net]("http://g.root-servers.net/").
.                       4664    IN      NS      [c.root-servers.net]("http://c.root-servers.net/").
.                       4664    IN      NS      [f.root-servers.net]("http://f.root-servers.net/").
.                       4664    IN      NS      [d.root-servers.net]("http://d.root-servers.net/").
.                       4664    IN      NS      [l.root-servers.net]("http://l.root-servers.net/").
;; Received 496 bytes from 127.0.0.1#53(127.0.0.1) in 55 ms


com.                    172800  IN      NS      [c.gtld-servers.net]("http://c.gtld-servers.net/").
com.                    172800  IN      NS      [i.gtld-servers.net]("http://i.gtld-servers.net/").
com.                    172800  IN      NS      [g.gtld-servers.net]("http://g.gtld-servers.net/").
com.                    172800  IN      NS      [l.gtld-servers.net]("http://l.gtld-servers.net/").
com.                    172800  IN      NS      [h.gtld-servers.net]("http://h.gtld-servers.net/").
com.                    172800  IN      NS      [d.gtld-servers.net]("http://d.gtld-servers.net/").
com.                    172800  IN      NS      [k.gtld-servers.net]("http://k.gtld-servers.net/").
com.                    172800  IN      NS      [e.gtld-servers.net]("http://e.gtld-servers.net/").
com.                    172800  IN      NS      [b.gtld-servers.net]("http://b.gtld-servers.net/").
com.                    172800  IN      NS      [j.gtld-servers.net]("http://j.gtld-servers.net/").
com.                    172800  IN      NS      [m.gtld-servers.net]("http://m.gtld-servers.net/").
com.                    172800  IN      NS      [f.gtld-servers.net]("http://f.gtld-servers.net/").
com.                    172800  IN      NS      [a.gtld-servers.net]("http://a.gtld-servers.net/").
;; Received 501 bytes from 192.33.4.12#53(192.33.4.12) in 94 ms


[youtube.com]("http://youtube.com/").            172800  IN      NS      [ns2.google.com]("http://ns2.google.com/").
[youtube.com]("http://youtube.com/").            172800  IN      NS      [ns1.google.com]("http://ns1.google.com/").
[youtube.com]("http://youtube.com/").            172800  IN      NS      [ns3.google.com]("http://ns3.google.com/").
[youtube.com]("http://youtube.com/").            172800  IN      NS      [ns4.google.com]("http://ns4.google.com/").
;; Received 172 bytes from 192.41.162.30#53(192.41.162.30) in 167 ms


[youtube.com]("http://youtube.com/").            300     IN      A       64.233.163.190
[youtube.com]("http://youtube.com/").            300     IN      A       64.233.163.93
[youtube.com]("http://youtube.com/").            300     IN      A       64.233.163.136
[youtube.com]("http://youtube.com/").            300     IN      A       64.233.163.91
;; Received 93 bytes from 216.239.34.10#53(216.239.34.10) in 77 ms



[/FONT]

---

### Post by nerdtron on 2015-08-13
Might be obvious but at least worth a check. Probably you put and entry on the /etc/hosts file?

---

