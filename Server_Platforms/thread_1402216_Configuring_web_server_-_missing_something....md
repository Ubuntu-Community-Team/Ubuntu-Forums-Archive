---
title: "Configuring web server - missing something..."
date: 2010-02-08
forum: Server Platforms
---

### Post by esauer on 2010-02-08
Ok, I have done this several times in the past, but this time, I think I am just forgetting something. I am trying to set up apache in ubuntu 8.10 server to work on a subdomain, xxx.example.com, of my live website, which is hosted by a company. I have the cname record properly set on the host. I know this because I can access my router's configuration page when I set its domain name. I have port forwarding set up on the router to point traffic on port 80 to my server's local ip address (currently 192.168.1.100). When I enter the local IP in a browser, I get the default index page. When I enter the domain name, after unsetting it on the router, I get server not found errors. 

Can anyone think of something I missed? It must be some problem with the router configuration? Please advise.

Thanks.

---

### Post by esauer on 2010-02-11
Can anybody advise on this?

---

### Post by Sporkman on 2010-02-11
I'm not sure if I understand correctly - are you on the same local network as the server?

One thing I can attest to - I am on the same LAN as my server, but I cannot get to the server by entering the domain name because my router (which is the portal to the outside) always intercepts it & serves up a "page not found 404" error.

You can try entering your domain name in a proxy service like [http://www.hidemyass.com/](http://www.hidemyass.com/) , which will indeed route your query out then back in - works for me...

---

### Post by esauer on 2010-02-11
Hi, just checked that. Does not work from outside my LAN either.

---

### Post by esauer on 2010-02-11
Just to clarify, my router is a Linksys 4 port Wireless with dd-wrt operating system installed (server is plugged in, not on wireless).

---

### Post by Ronca_Lapor on 2010-02-11
i think your problem might be that you haven't configured DNS

that's what i have spend quite some time on; i installed Alfresco community Edition, and then everyone in my network can access it thru the address "10.10.1.23/share".

but we thought that an IP address is rather difficult to memorize, especially because some people using the online document repository do not understand much about network

so what i did was, i downloaded bind9 and configured it so that people can now have access to Alfresco thru "http://alfresco.mydomain/share" much simpler to remember
here is a really good howto on bind9: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
though in my case, the system is compleatelly internal; what i said might make no sense at all

---

### Post by Porter200el on 2010-02-12
> **esauer said:**
> Ok, I have done this several times in the past, but this time, I think I am just forgetting something. I am trying to set up apache in ubuntu 8.10 server to work on a subdomain, xxx.example.com, of my live website, which is hosted by a company. I have the cname record properly set on the host. I know this because I can access my router's configuration page when I set its domain name. I have port forwarding set up on the router to point traffic on port 80 to my server's local ip address (currently 192.168.1.100). When I enter the local IP in a browser, I get the default index page. When I enter the domain name, after unsetting it on the router, I get server not found errors. 

Can anyone think of something I missed? It must be some problem with the router configuration? Please advise.

Thanks.

You need to set a cname record on your domain controller to point to your sub domain locally.  A public DNS record cannot point to a 192.168.XXX.XXX address, it will point to your public IP then your DC can redirect the request to the proper local box.  If you don't have a domain controller, I believe that DD-WRT has an option to set a dynamic dns records, but your router would need to be acting as the domain controller/Default Gateway (basically the device serving up the IPs) for that to work.

---

### Post by esauer on 2010-02-12
The actual domain name is hosted externally by a web host company. I have created a cname record on their system pointing to my router's external IP. Then from there I have a port forward record from port 80 to the local IP of the box that I would like serving webpages.

---

### Post by esauer on 2010-02-12
Also, as I said before, I can set a domain name on my router, and it shows up fine. The problem has to be communication between my router and the local box. I just can't figure out where the communication breakdown is.

---

### Post by Porter200el on 2010-02-12
> **esauer said:**
> Also, as I said before, I can set a domain name on my router, and it shows up fine. The problem has to be communication between my router and the local box. I just can't figure out where the communication breakdown is.

Then you need to edit the host file on your web server. You need to add in the cname record and the ip, if there is not DC, then that is the only way this box is going to know that it is: subomain.domain.com.  Let me know if you need more help with this.

---

