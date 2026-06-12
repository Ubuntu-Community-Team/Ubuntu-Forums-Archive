---
title: "I am not able to stop DHCP server"
date: 2015-10-06
forum: Server Platforms
---

### Post by Bhanu_Prasad on 2015-10-06
I have installed DHCP server but when I am trying to stop using "stop isc-dhcp-server" it is throwing message saying "stop: unknown instance". I have tried to stop using other commands as well but no luck.

---

### Post by Lars Noodén on 2015-10-06
It should be something like this:

```

sudo service isc-dhcp-server stop

```

However, if it is saying "stop: unknown instance", then there is  most likely no [dhcpd](http://manpages.ubuntu.com/manpages/trusty/en/man8/dhcpd.8.html) running.  

Check /var/log/syslog for the relevant error messages or try *sudo dhcpd -d* to see them up front.

---

### Post by SeijiSensei on 2015-10-06
That error might mean nothing is running with the name "stop".

Check to see if the program is running with the command "ps ax | grep dhcp".  If it is, you can "kill" it using its process ID, the first number at the beginning of the entry returned by the ps command.
```
sudo kill -15 12345
```
replacing "12345" with the correct PID.  That tells the process to close down "gracefully." Now run the "ps ax | grep dhcp" command again.  If the process is still running, use "kill -9" rather than "kill -15" to force it to shutdown.

However you should always use "sudo service isc-dhcp-server start|stop|restart" to manage the daemon.

---

### Post by Bhanu_Prasad on 2015-10-07
> **Lars Noodén said:**
> It should be something like this:

```

sudo service isc-dhcp-server stop

```

However, if it is saying "stop: unknown instance", then there is  most likely no [dhcpd]("http://manpages.ubuntu.com/manpages/trusty/en/man8/dhcpd.8.html") running.  

Check /var/log/syslog for the relevant error messages or try *sudo dhcpd -d* to see them up front.

I have run command sudo dhcpd -d

here is what i have got:
[COLOR=#000000][FONT=Calibri]Internet Systems Consortium DHCP Server 4.1-ESV-R4[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Copyright 2004-2011 Internet Systems Consortium.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]All rights reserved.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Wrote 0 leases to leases file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]No subnet declaration for wlan2 (192.168.1.2).[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]** Ignoring requests on wlan2.  If this is not what[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]   you want, please write a subnet declaration[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]   in your dhcpd.conf file for the network segment[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]   to which interface wlan2 is attached. **[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Not configured to listen on any interfaces!&#8203;

Is it saying it is not configures at all? Could you please help....[/FONT][/COLOR]

---

### Post by Bhanu_Prasad on 2015-10-07
@SeijiSensei

I have run ps ax | grep dhcp on terminal it doesnt show that dhcp server is running it shows only dhcp client. I think server is not at all running. Thanks for the reply

---

### Post by Lars Noodén on 2015-10-07
Ok.  Those errors show that you have not configured dhcpd yet.  It won't run until you have a configuration that is valid for your setup.  

The ISC DHCP server has a lot of options.  What is your general goal with DHCP?

Which interface to you plan to run it on?  That interface needs to already have its own **static** ip address.

---

