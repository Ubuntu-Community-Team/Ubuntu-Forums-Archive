---
title: "webmin, CUPS"
date: 2009-01-27
forum: Server Platforms
---

### Post by waspinator on 2009-01-27
Hi,

I'm new to Ubuntu Server and I'm trying to install a printer on the server. Since the server has no GUI so I'm doing everything through CLI or webmin. 

The first thing I tried was to get CUPS web interface to work. 
Initially poiting my browser to port 631 on my server did nothing. I then changed localhost:631 to just 631 in the cups config file and my browser connected but all I got was 403 Forbidden. It works through the links2 text browser on the server itself though. 

I then tried to configure my printer through Webmin. When I click on Hardware -> Printer Administration -> Add a new printer I don't see any CUPS drivers. I have attached a screenshot of what I see.

Can anyone help me get my printer to work either though CUPS web interface, or more preferably since it's all in one place, webmin?

Thanks

Operating system 	Ubuntu Linux 8.10
Webmin version   	1.441

---

### Post by cariboo on 2009-01-27
The first thing to do is to make sure your printer is supported check the [Openprinting Database]("http://www.openprinting.org/printer_list.cgi").

Install elinks, it is in the repositories, then at the prompt type:

```
elinks http://localhost:631
```

Elinks is a text based web browser, use it to access the cups web interface to setup and share your printer. You have to use the arrow keys for naviagation.

If you are accessing your server remotely you can ssh in and start elinks from the console. I would suggest using the terminal in full screen mode.

Jim

---

### Post by ibutho on 2009-01-28
Take a look at part of my /etc/cups/cupsd.conf and make sure that yours is similar. In the example below 192.168.1.111 is the ip address of my server (the one where cups is running)

```
# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
#Listen localhost:631
Listen 192.168.1.111:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow @LOCAL
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL
</Location>


```

---

### Post by waspinator on 2009-01-28
> **cariboo907 said:**
> The first thing to do is to make sure your printer is supported check the [Openprinting Database]("http://www.openprinting.org/printer_list.cgi").

Install elinks, it is in the repositories, then at the prompt type:

```
elinks http://localhost:631
```

Elinks is a text based web browser, use it to access the cups web interface to setup and share your printer. You have to use the arrow keys for naviagation.

If you are accessing your server remotely you can ssh in and start elinks from the console. I would suggest using the terminal in full screen mode.

Jim

I actually already tried something similar using another browser called links2. What I'm actually trying to do though is access that page from another computer. When I try to do that I get 403 Forbidden Even though I set the cups config file from Listen localhost:631 to just Listen 631

---

### Post by waspinator on 2009-01-28
@ibutho

My file looks pretty similar although I listen to connections from anywhere on port 631. I'm trying to access the CUPS page from another computer. Are you able to do that with your configuration?

---

### Post by waspinator on 2009-01-29
I seem to have solved it. 

For reference if anyone else has a problem with CUPS here is what I did.

1. copied the default config
sudo cp cupsd.conf.default cupsd.conf

2. Added "Port 631" under #allow remote access

3. Added "Allow from All" under all the other sections

---

### Post by ibutho on 2009-01-29
> **waspinator said:**
> @ibutho

My file looks pretty similar although I listen to connections from anywhere on port 631. I'm trying to access the CUPS page from another computer. Are you able to do that with your configuration?

Yes, I am able to access the cups admin page from another computer (on the same network). Anyway, it appears that you managed to resolve your problem which is cool. ;)

---

