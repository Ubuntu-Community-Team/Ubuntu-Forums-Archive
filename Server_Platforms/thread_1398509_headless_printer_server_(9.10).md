---
title: "headless printer server (9.10)"
date: 2010-02-04
forum: Server Platforms
---

### Post by rdema19403 on 2010-02-04
I have a server it is running ubuntu 9.10 server i wanted to hook my printer up to the server and be able to print from my ubuntu desktop computer.how should i go about doing that the server has cups on it?
I am new to this so any help would be ok .
I can access the server from a terminal using ssh i also have webmin installed on the server.
Thanks in advance
Ralph

---

### Post by Demented ZA on 2010-02-04
Well you could try [here]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html"), as well as going to the Cups [homepage]("http://www.cups.org/"). Look on the left for the faq's.

It doesn't seem too difficult :-) hope that helps.

Edit: It mainly boils down to editing /etc/cups/cups.d/ports.conf and making sure the Cups daemon listens on the interface you need (probably your local network in your case). then issuing a restart command to cups and connecting to it from your desktop.

Please let me know where you need help :-)

---

### Post by rdema19403 on 2010-02-07
when i ssh into the terminal because  i have a headless server what is the command to get to this file (/etc/cups/cups.d/ports.conf )
Thanks in advance

---

### Post by Queue29 on 2010-02-07
> **rdema19403 said:**
> when i ssh into the terminal because  i have a headless server what is the command to get to this file (/etc/cups/cups.d/ports.conf )
Thanks in advance

This isn't as easy to [set up]("http://bozosort.com/content/?p=19") as you might think it should be.

There is no such thing as /etc/cups/cups.d/ports.conf
The file you want to edit is /etc/cups/cupsd.conf which also deals with information about the port number.

---

