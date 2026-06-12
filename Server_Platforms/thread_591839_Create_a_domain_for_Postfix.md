---
title: "Create a domain for Postfix"
date: 2007-10-25
forum: Server Platforms
---

### Post by petersfreeman on 2007-10-25
My goal is to create an email server for our community of about ten families. 

I live in a remote area with ten families and we have a single link from the internet connected to a router which runs DHCP and issues IP addresses in the 192.188.1.100 to 192.168.1.149 range.  

I have a LAMP server with a fixed IP address of 192.168.1.31 which I set up using Ubunto 7.04 Server (LAMP option)

I have installed Postfix and gave it a domain called muskrat.net, testing shows it to be working correctly by typing:  [FONT="Courier New"]telnet 192.168.1.31 25[/FONT], however if I try typing [FONT="Courier New"]telnet mail.muskrat.net 25[/FONT] it goes of to a 206.x.x.x address and times out

When I go to a Windows XP box, load up MS Outlook, add a mail account and enter the incoming and outgoing servers as 192.168.1.31, testing from MS Outlook shows that it finds the server, finds the incoming server, finds the outgoing server but when it tries to log on to the outgoing server (SMTP) it fails.  The error message is to check SSL authentication etc...

I have tried a number of times in  setting SSL on and off in combination with a number of other settings with no success.

As I want to create a number of users with email addresses in the format of [email]firstname.lastname@muskrat.net[/email], I suspect the problem is I have no domain.  Here are my questions:

1.  If in fact I need to create a domain, how do I create one called muskrat.net?

2.  Can I create this domain locally only (members of our remote community can send each other mail, but not to people outside in other towns and cities)?

3.  To be able to send and receive emails from outside, do I need to register this domain?  If so, can I register it for free or will I need to pay a fee?

4.  How do I create the domain?

5.  Do I need to make my server a DNS server?

Thank you,

Peter Freeman

---

### Post by whit on 2007-10-27
You can register a domain for $15 a year or less. I've had good luck with the service at domaindirect.com - it would be a "parked domain" you'd want from their choices as compared to one of the options where they host services for you for more bucks. You can host your own DNS, and point to it from your domain registration. Some registrars also provide free DNS you can point to your address (can't recall with domaindirect - I run a DNS). You'll have to find a domain name that's not already registered, though. 

Alternately, if you don't want people outside to be able to email in, you could set up a local DNS, and have your users configure to use it, that would allow you to internally pretend to be any domain you want. But as soon as someone configures their system to use public DNS instead of your private one, that stops working right.

---

