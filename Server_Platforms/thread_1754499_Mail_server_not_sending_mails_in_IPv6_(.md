---
title: "Mail server not sending mails in IPv6 :("
date: 2011-05-10
forum: Server Platforms
---

### Post by THOR123 on 2011-05-10
Hi i am new to server platform.  I have set up a mail server using postfix as MTA and IMAP as MUA for the first time.  I want to send the mails both on IPv4 and Ipv6 networks. Though the mail gets delivered but only on ipv4:(. 

here is my main.cf file


[IMG]http://dl.dropbox.com/u/6356889/Main.cf_2.png[/IMG]
The output iam getting  after checking mail.log is 

[IMG]http://dl.dropbox.com/u/6356889/Untitled.png[/IMG]

I really need to get it fixed :(
Any suggestions or hint ! 
Thanks in advance

---

### Post by lemming465 on 2011-05-10
Could we see the output of ```
ip address show; ip -6 route show; ip -4 route show
```
What happens if you run *ping -6 ipv6.google.com*

---

### Post by elico on 2011-05-10
it depends on other things then just IPV6...
such as the recipient host usage of IPV6 and some other settings.
if it's a close environment with couple of servers you can setup specific settings for them.

---

### Post by hawkmage on 2011-05-11
What hapens if you run "nslookup -type=AAAA MXServer" Where MXServer is the name of the mail server.  You need to be able to resolve the mail server name to its IPv6 address to be able to send via IPv6.

---

### Post by THOR123 on 2011-05-16
> **lemming465 said:**
> Could we see the output of ```
ip address show; ip -6 route show; ip -4 route show
```
What happens if you run *ping -6 ipv6.google.com*

Hi 

here is the output of the code```
ip address show; ip -6 route show; ip -4 route show
```
[IMG]http://dl.dropbox.com/u/6356889/abc.jpg[/IMG]

when i run the cmd ping -6 ipv6.google.com 

it says network rechable !

What i have figured out is iam missing a default route for ipv6 here. U reckon it may be one of the reasons ?

---

### Post by THOR123 on 2011-05-16
> **hawkmage said:**
> What hapens if you run "nslookup -type=AAAA MXServer" Where MXServer is the name of the mail server.  You need to be able to resolve the mail server name to its IPv6 address to be able to send via IPv6.

hi
when i 
run "nslookup -type=AAAA mail.epic.inn650"

output says
Server:  2402:ec00:ffe1:1::3
Address: 2402:ec00:ffe1:1::3#53

mail.epic.inn650  has AAAA address 2402:ec00:ffe1:1::3

---

### Post by THOR123 on 2011-05-17
dammit i had a missing default route ! that was it :P

thanks guys ! problem fixed :)

---

