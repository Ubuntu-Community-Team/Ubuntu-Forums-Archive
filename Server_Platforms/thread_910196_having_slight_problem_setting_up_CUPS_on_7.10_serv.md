---
title: "having slight problem setting up CUPS on 7.10 server"
date: 2008-09-04
forum: Server Platforms
---

### Post by bluepowder7 on 2008-09-04
i'm going through the 7.10 server guide ([https://help.ubuntu.com/7.10/server/C/cups.html](https://help.ubuntu.com/7.10/server/C/cups.html)), and i'm quickly stuck.  first, my /etc/cups/cupsd.conf configuration file never had a ServerAdmin line, so i just manually entered it.  hopefully that's ok.  second, i don't have the /etc/cups/cups.d/ports.conf file or directory structure which supposedly holds my configuration for the CUPS server (going by the guide, i need to edit or set up the LISTEN parts).

i DID find a "listen" line in cupsd.conf, which has

```

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

```

but i'm not certain that this is where i should make the edit.

if i DO need to make it here, how should i structure the listen line so that it listens to stuff over the network and then funnels it to the old-fashioned laser printer that's connected to the server box's parallel port?  and then, how do i set up the the printer stuff on my desktop machine to properly route the job to the server box?

i'm just a wee bit lost when it comes to this stuff...  back when i set up my network inkjet printer, it was a day full of frustration and guides that skip over stuff or don't explain it adequately to newbies like myself (i did get it working eventually)

---

### Post by bluepowder7 on 2008-09-05
little bit of help, please?

---

### Post by lucho64 on 2008-09-06
I got 7.10 too. I don't have the ports.conf file. I got rid of the Listen lines on my config and replaced them with:
```

Port 631
Browsing On
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow all
</Location>

```
I'm behind a firewall, so I figured I could have it allowing everybody in.

I can print from other computers (also running linux) From windows machines I can also print, but for that I also need to have samba properly configured. Can you browse your network with samba?

---

### Post by windependence on 2008-09-06
Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(Dapper: /etc/cups/cups.d/ports.conf; Edgy: /etc/cups/cupsd.conf)

```
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
```

Restart the cups daemon:

```
sudo /etc/init.d/cupsys restart
```

On the Windows boxes:

Start the Add Printer wizard 
Click Next 
Select A network printer, or a printer attached to another computer 
Select Connect to a printer on the Internet or on a home or office network 

Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the URL box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. Don't forget the port number! 
Click Next and run through the driver installation to complete

**NOTE:**

You can't use the web admin interface because root is disabled. If you want to configure cups so that you can use web admin w/o enabling the root account follow the instructions here: [https://help.ubuntu.com/community/Pr...psWebInterface](https://help.ubuntu.com/community/Pr...psWebInterface)

-Tim

---

