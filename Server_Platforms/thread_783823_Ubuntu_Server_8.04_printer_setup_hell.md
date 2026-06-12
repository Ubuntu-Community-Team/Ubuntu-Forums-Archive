---
title: "Ubuntu Server 8.04 printer setup hell"
date: 2008-05-06
forum: Server Platforms
---

### Post by Gooorn on 2008-05-06
Hello.

I'm unable to set up my USB printer on server for sharing.
I have Ubuntu Server 8.04 LAMP clean installation and no gui.

a) from shell (sudo printconf), I have a problem with foomatic-db as it was not installed properly but apt-get has no errors and reports foomatic-db as installed

b) when using [http://xxx.xxx.xxx.xxx:631](http://xxx.xxx.xxx.xxx:631) for cups administration everything is fine (printer and model can be discovered) but the last button to set up printer, the one where choosing the right driver for the printer, is resulting in new window asking username and password and after that the server is refusing my connection until "sudo /etc/init.d/cupsys restart".

This is so frustrating since the b) option finds bleeding foomatic-db but rejects all my attempts to provide username and password and a) version has problems with the same foomatic-db.:confused:

Please, can someone help me....

Thanx,

Sinisa Perovic

---

### Post by SumnerBoy on 2008-05-06
I am in the same boat. I can find and select my printer + driver but when I hit the final 'Add Button' CUPS crashes with an authorisation error (in the log).

The first time I tried this I was prompted for a username and password. I entered my username and password (which is an admin user) but since then I am not even prompted.

Any help?!

---

### Post by inportb on 2008-05-06
That's interesting. What printers are you installing?

Because I just plug my printer in and wait for it to be automatically configured.

---

### Post by SumnerBoy on 2008-05-06
Mine is a Canon MP530. I don't think it is anything to do with the printer itself - I believe it is some sort of permissions issue.

I get the following in the error log when trying to add the printer, after which I have to restart CUPS;

```
CUPS-Add-Modify-Printer: Unauthorized
```

---

### Post by SumnerBoy on 2008-05-06
Is it something to do with CUPS failing to authorise and then refusing to accept any further attempts until some timeout expires? 

I say this because I tried this last night, and the first time I attempted I was prompted for a username and password. I entered my login but it failed. Then each subsequent attempt I wasn't prompted for any login credentials.

However this evening I tried again and was prompted for a login again. I tried the root login but again no luck. And now any subsequent attempts are again met with no login prompt.

This is really starting to frustrate me!

---

### Post by SumnerBoy on 2008-05-06
And yet more...

I tried updating my cupds.conf file from;

```
DefaultAuthType Basic
```

to;

```
DefaultAuthType None
```

When I repeated the process I was this time shown a page with the following;

```
401 Unauthorized
Enter your username and password or the root username and password to access this page. If you are using Kerberos authentication, make sure you have a valid Kerberos ticket.

```

This is instead of a blank 404 page and the CUPS server shutting down if the auth type is Basic.

Does this help?

---

### Post by bdk6m2007 on 2008-05-06
FWIW, I've got this same problem with 07.10.

---

### Post by SumnerBoy on 2008-05-06
The frustrating thing is I was able to setup my printer previously (in 7.10). I then decided to upgrade to 8.04 by doing a fresh install, and since then I have been unable to get it to work.

I actually still have the old config files, and by copying them over I can get the printer to work, but I really want to know why this isn't working normally.

Someone must have some idea about this?

---

### Post by nquinnathome1 on 2008-05-09
I have the same problem; every time I get to the authorisation box and enter my servers username/pass, it returns a page load error and my cupsys is no longer running.

EDIT: I seem to have fixed it for my machine. I'll walk you all through what I did.

First of all, we need to modify AppArmor so that CUPSD complains to it:
```
sudo aa-complain cupsd
```

Next, make some changes to your cupsd.conf configuration file (it's located at /etc/cups/cupsd.conf). Make sure the following sections are set as follows (changes highlighted in bold):

```

# Administrator user group...
SystemGroup lpadmin
[B]
#Set default encryption - 'Never' = not over SSL, which would need HTTPS
DefaultEncryption Never[/B]

# Only listen for connections from the local machine.
Listen localhost:631
**Listen 192.168.1.254:631** #set this to <your_server_IP:631>
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
**Browsing On**
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
[B]  Allow localhost
  Allow @LOCAL[/B]
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
[B]  Allow localhost
  Allow @LOCAL[/B]
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
[B]  Allow localhost
  Allow @LOCAL[/B]
</Location>

```

Now restart cups:
```
sudo /etc/init.d/cupsys restart
```

---

### Post by Laz_K on 2008-05-10
I had a similar problem, which I solved by changing cupsd.conf authentication to the following:

DefaultAuthType BasicDigest

---

### Post by Gooorn on 2008-05-12
Thanx a million nquinnathome1 for your help. it works.=D>

---

