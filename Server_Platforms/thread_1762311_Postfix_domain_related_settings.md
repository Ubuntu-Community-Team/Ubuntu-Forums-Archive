---
title: "Postfix domain related settings"
date: 2011-05-19
forum: Server Platforms
---

### Post by jplozza on 2011-05-19
Hi All,
 
I have set up[ a postfix / dovecote email server and all is working well. Ok near enough.
 
I have two things that i can work out the first being what to set the following parameters to.
 
[LIST]
[*]myhostname = mail.company.net.au
[*]mydomain = company.net.au
[*]myorigin = /etc/mailname
[*]mydestination = "This is just blank i.e. whitespace"
[/LIST]The computer name was set to "Server01" during install.
 
The second issue i will keep working through until i cant take it any further
 
My setup is a server box behind a firewall/router that connects to an ADSL internet connection. every thing ethernet.
 
I can send and receive emails from outlook 2010 from both inside and outside my local network and I have postfix relay my outgoing emails via an external relay because of the fact I have a dynamic address and some servers take isssues with my IP address.
 
I have MX and A records setup with a dynamic service provider and an alias to the A record of mail.company.net.au
 
my first MX points to company.net.au my second to a thirdparty backup server.
 
As I have said every thing works well.
 
My confusion is what to set the above parameters to given the following.
 
I own my own company and this server is firstly for my company emails for the domain company.net.au (oviouslly this isnt the real domain). I also have several private domains such as "private.com.au"
 
I have set up all domains as virtual domains with virtual users and aliasses. I dont need to have email accounts for the linux account users except for perhaps root and admin but this isn critical just nice
 
I have read every thing I can and it isn clear what are sensible settings for above.
 
Could some one sugest what the would set the parameters to and why why/not.
 
Thanks

---

