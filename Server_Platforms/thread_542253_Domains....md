---
title: "Domains..."
date: 2007-09-03
forum: Server Platforms
---

### Post by hockey97 on 2007-09-03
HI is thier any tutorials on  having my own domain named website.

I have apache 2 installed and also bind9 

I have bought a registerd domain name.

I also have a mail server.

Now what Ip address do I need to have the domain name when user request my [www.example.com](www.example.com)  it will take them to my apache2 server and grab the website files ect??

I know my external ip and internal ip, and the ip address of my domain name.

just don't know what to do to make my apache server reply to my domain name for the request.

I have been trying the whole day can't get it to work.

I don't know how to find name servers, i have an idea to do nslookup or ding,  I have found an ns server but I think it's only for my domain name.

Can someone please help me out on doing this or at least a good tutorial that would explain each step on doing this?

Thanks

---

### Post by K.Mandla on 2007-09-05
Moved to Servers & Security. ;)

---

### Post by KCPokes on 2007-09-05
I'll see if I can help a bit...

The short path is, using godaddy as an example, to go into the control panel at godaddy, choose the complete DNS control, and set your A record to be the value of your public IP address.  This is not going to work well if you do not have a static IP address, or have a DHCP address that changes a lot.  If you are planning on using your mailserver, you will need to set the MX record to point to your A record as well, thus it all rolls up to a single A record.  This is the typical setup, although you can have HTTP traffic go to a location different then mail traffic, thus your MX record would be set to its own value.  

Clear as mud?  

You mentioned that you have Bind running, but honestly I find it just complicates the situation.  If you utilize your registrar to handle the DNS propagation, there isnt really a call to run your own DNS server, other then internal resolution and/or to speed up name resolution for your traffic.  

Once you have set up DNS, in your registrar, you need to ensure that your router/firewall is set up to allow port specific traffic in.  You'll need to open port 25 (SMTP), port 110 (POP3), and port 80, at the very least, and configure them to point to the appropriate server IPs.  

Hopefully this didnt add to the confusion.  The steps are pretty straightforward, although takes a bit the first time.

---

### Post by hockey97 on 2007-09-05
I got my domain name up and also got the site up.

but failing at the mail server end.

I got the mx records. I made them,  but I don't know what the send to address thing??

I made mine like mail.mydomainname.com  

now I got my mail name

I tested it by doing  [email]mailnameuser@mydomain.com[/email]

is that right??

or would it be like [email]mailnameuser@mail.mydomain.com[/email]

the first one I done I tested I got a mail daemon, saying it faild to send mail, I used aol e-mail service to test this.

any good website that has tutorials or somthing??

---

### Post by az on 2007-09-05
You mentioned your external and internal addresses.  You need to have a static ip on the outside (from your ISP) and you need to have your router send requests for port 80 to your box that is running apache.

Have you done this?

---

