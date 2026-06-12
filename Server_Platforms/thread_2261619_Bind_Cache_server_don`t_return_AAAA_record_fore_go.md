---
title: "Bind Cache server don`t return AAAA record fore google.de"
date: 2015-01-20
forum: Server Platforms
---

### Post by eheimwbn on 2015-01-20
Hi,
im running two identical configured bind9 servers. The first one without an 'public' ipv6 address, the second one has an ipv6 address. Since this morning the first one still returns a aaaa record for dig @localhost google.de aaaa


[INDENT][SIZE=1]; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> @localhost google.de aaaa[/SIZE][/INDENT]
[INDENT][SIZE=1]; (2 servers found)[/SIZE][/INDENT]
[INDENT][SIZE=1];; global options: +cmd[/SIZE][/INDENT]
[INDENT][SIZE=1];; Got answer:[/SIZE][/INDENT]
[INDENT][SIZE=1];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18342[/SIZE][/INDENT]
[INDENT][SIZE=1];; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 5[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; OPT PSEUDOSECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1]; EDNS: version: 0, flags:; udp: 4096[/SIZE][/INDENT]
[INDENT][SIZE=1];; QUESTION SECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1];google.de.                     IN      AAAA[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; ANSWER SECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1]google.de.              300     IN      AAAA    2a00:1450:4001:80d::100f[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; AUTHORITY SECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1]google.de.              83107   IN      NS      ns4.google.com.[/SIZE][/INDENT]
[INDENT][SIZE=1]google.de.              83107   IN      NS      ns1.google.com.[/SIZE][/INDENT]
[INDENT][SIZE=1]google.de.              83107   IN      NS      ns3.google.com.[/SIZE][/INDENT]
[INDENT][SIZE=1]google.de.              83107   IN      NS      ns2.google.com.[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; ADDITIONAL SECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1]ns1.google.com.         342327  IN      A       216.239.32.10[/SIZE][/INDENT]
[INDENT][SIZE=1]ns2.google.com.         342327  IN      A       216.239.34.10[/SIZE][/INDENT]
[INDENT][SIZE=1]ns3.google.com.         342327  IN      A       216.239.36.10[/SIZE][/INDENT]
[INDENT][SIZE=1]ns4.google.com.         342327  IN      A       216.239.38.10[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; Query time: 14 msec[/SIZE][/INDENT]
[INDENT][SIZE=1];; SERVER: ::1#53(::1)[/SIZE][/INDENT]
[INDENT][SIZE=1];; WHEN: Tue Jan 20 10:16:14 CET 2015[/SIZE][/INDENT]
[INDENT][SIZE=1];; MSG SIZE  rcvd: 212[/SIZE][/INDENT]


The second one, since this morning, doesn’t.  


[INDENT][SIZE=1]; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> @::1 google.de AAAA[/SIZE][/INDENT]
[INDENT][SIZE=1]; (1 server found)[/SIZE][/INDENT]
[INDENT][SIZE=1];; global options: +cmd[/SIZE][/INDENT]
[INDENT][SIZE=1];; Got answer:[/SIZE][/INDENT]
[INDENT][SIZE=1];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19599[/SIZE][/INDENT]
[INDENT][SIZE=1];; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; OPT PSEUDOSECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1]; EDNS: version: 0, flags:; udp: 4096[/SIZE][/INDENT]
[INDENT][SIZE=1];; QUESTION SECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1];google.de.                     IN      AAAA[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; AUTHORITY SECTION:[/SIZE][/INDENT]
[INDENT][SIZE=1]google.de.              359     IN      SOA     ns4.google.com. dns-admin.google.com. 1579719 900 900 1800 60[/SIZE][/INDENT]
[INDENT][SIZE=1]
[/SIZE][/INDENT]
[INDENT][SIZE=1];; Query time: 0 msec[/SIZE][/INDENT]
[INDENT][SIZE=1];; SERVER: ::1#53(::1)[/SIZE][/INDENT]
[INDENT][SIZE=1];; WHEN: Tue Jan 20 10:54:05 CET 2015[/SIZE][/INDENT]
[INDENT][SIZE=1];; MSG SIZE  rcvd: 98[/SIZE][/INDENT]





He returns one fore facebook or heise but not for google.de or youtube … 
The returned SOA serial number is for both answer’s the same.

---

