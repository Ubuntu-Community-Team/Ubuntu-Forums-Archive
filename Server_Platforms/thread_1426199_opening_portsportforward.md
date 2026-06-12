---
title: "opening ports/portforward"
date: 2010-03-10
forum: Server Platforms
---

### Post by zander1013 on 2010-03-10
hi,

i am trying to add another server with a static ip address to my wlan behind a debian etch server setup as firewall/router/server for my wlan.

wan <---> debian server/firewall/router <---> <new server>

subsequently i believe that i must configure debian server/firewall/router for portforwarding to make the server behind the debian server/router/firewall accessible to the web.

the new server (oznola) is ubuntu server 9.10 and seems to be working correctly. i can access oznola's web page by entering [http://oznola.localdomain](http://oznola.localdomain) on other machines in my wlan.

i want to assign oznola a static ip address and have debian server/router/firewall portforward or open a public port for it.

is this a sound plan?

if yes how do i configure the debian server/router/firewall to portforward to oznola?

i have five variables that i am working with "source ip" , "public port", "private port", "private ip" and protocol

my plan is to set...
"source ip" == "all" (default)
"public port" == ??? (i don't know what "public port" should be)
"private port" == ??? (i don't know what "private port" should be)
"private ip" == ??? (but i think it should be the static ip for the server behind the firewall)
"protocol" == tcp (default)

does anyone know what ports should be used?

can someone tell me how to set the static ip on the ubuntu server?

i have been looking at [http://portforward.com](http://portforward.com) for help but they don't give an explanation on configuring a linux software router/firewall/server that i can find. i can only find docs there on hardware routers.

please advise

---

### Post by iponeverything on 2010-03-10
> 
source ip" == "all" (default)
"public port" == ??? (i don't know what "public port" should be)
"private port" == ??? (i don't know what "private port" should be)
"private ip" == ??? (but i think it should be the static ip for the server behind the firewall)
"protocol" == tcp (default)


"public port" == 1234 (choose anything between 1024 and 65535)
"private port" == 80  (the default)
"private ip"  == It is the static ip that you choose

> can someone tell me how to set the static ip on the ubuntu server?

```
nano /etc/network/interfaces

```

Add something like this depending what static works for your internal network:

```

iface eth0 inet static
  address 192.168.1.44
  netmask 255.255.255.0
  gateway 192.168.1.1

auto eth0 


```

After the portwarding on external box is setup you should be to access the the internal server with something like:

[http://external.ip:1234](http://external.ip:1234)

---

### Post by spynappels on 2010-03-10
If you want the webserver to be publicly accessible, and port 80 is not blocked by your ISP, you can set the public port to 80 as well. This means that all web requests are automatically forwarded to your new server.

---

### Post by zander1013 on 2010-03-10
> **spynappels said:**
> If you want the webserver to be publicly accessible, and port 80 is not blocked by your ISP, you can set the public port to 80 as well. This means that all web requests are automatically forwarded to your new server.

indeed i do want it to be publicly accessible as you described.

right now the debian server/router/firewall is serving [http://alonzofretwell.com](http://alonzofretwell.com) i want the new server to serve [http://temporalmills.com](http://temporalmills.com) from ~behind~ [http://alonzofretwell.com](http://alonzofretwell.com) from the new server.

www from wan is already coming through port 80/443 on the server/router/firewall( [http://alonzofretwell.com](http://alonzofretwell.com) ).

www <> server/router/firewall <> new server

i am using a web gui interface to set up my ports on the debian server/router/firewall. in the section where i can manage "open port/add portforward" there is a two button, radio button where i can select "portforward" or "open public port" it grays out "private port" and "private ip" when i select "open public port".

btw this is the first time i have tried to do this so thank you for your patience.

should i select "open public port", set public port to 80, leave source ip to "all" and then click "update"?

will this effect service from [http://alonzofretwell.com](http://alonzofretwell.com) since it is already using port 80/433?

thank you so much for your help.

---

### Post by zander1013 on 2010-03-10
also i am using a wireless network adapter between the new server and the server/router/firewall. does that effect what i add to the /etc/network/interfaces file?

Code:
iface eth0 inet static
  address 192.168.1.44
  netmask 255.255.255.0
  gateway 192.168.1.1

auto eth0

the "iface eth0" and "auto eth0" in particular are what i am concerned with. should i replace eth0 with something else since it is wireless?

MY BAD: this is done on the server/router/firewall not the server behind it. eth0 should work fine.

---

### Post by zander1013 on 2010-03-10
okay,

i got this thing working as iponeverything suggested [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) is served from the new server and [http://alonzofretwell.com](http://alonzofretwell.com) is served as before.

thank you ip!:)


is there anyway for me to set things up so that [http://temporalmills.com](http://temporalmills.com) will point to [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) instead?

thank you again!:)

---

### Post by spynappels on 2010-03-10
That is easy, you get the Domain Name Company where you got the temporalmills.com to point to alonzofretwell.com:1234 in their DNS records.

I didn't realize you had another site running on the firewall box, my earlier suggestion would only allow you to have one or the other, not both. Sorry.

---

### Post by zander1013 on 2010-03-11
hi,

can i add more servers similarly?

i can see that to add another server i should add another public port but can i still use port 80 for the private port?

please advise.

thank you.

---

