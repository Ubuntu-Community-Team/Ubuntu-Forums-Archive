---
title: "Cant ssh to ubuntu 12.04 at AWS instance"
date: 2014-02-23
forum: Server Platforms
---

### Post by roman8 on 2014-02-23
[COLOR=#000000][FONT=Arial]i'm no new to amazon, using it for almost 3 years, centOS only so far.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm trying to create Ubuntu server 12.04 instance from the marketplace (on m1.small):
[https://aws.amazon.com/marketplace/pp/B007Z5YWX4/ref=srh_res_product_title?ie=UTF8&sr=0-2&qid=1393104126186](https://aws.amazon.com/marketplace/pp/B007Z5YWX4/ref=srh_res_product_title?ie=UTF8&sr=0-2&qid=1393104126186)
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]using same *.pem key i'm usuing for my other servers, when i'm trying to connect i got the error: Permission denied (publickey).[/FONT][/COLOR]

[LIST]
[*]yes, my pem key has chmod 400.
[*]i tried using those username: ubuntu, root, ec2-user.
[*]port 22 open in the security group.
[/LIST]
[COLOR=#000000][FONT=Arial]i used ssh ubuntu@public-ec2-dns and ssh -i my.pem ubuntu@public...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]i'm using a mac.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]does anyone got an idea why i cant connect?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]thanks.[/FONT][/COLOR]

---

### Post by roman8 on 2014-02-23
something was wrong with the keypair, even that i use it to connect to another server and it works.
i created new keypair and it works great.

---

