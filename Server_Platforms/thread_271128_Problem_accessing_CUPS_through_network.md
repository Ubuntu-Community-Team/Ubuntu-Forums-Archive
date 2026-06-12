---
title: "Problem accessing CUPS through network"
date: 2006-10-04
forum: Server Platforms
---

### Post by secici on 2006-10-04
Hi;

What I've learned as I searched documentation about ubuntu and network printing through the day is I have to install samba with a truely configured cupsd.

Installed version of ubuntu is 5.10 CUPS version 1.1.23.10ubuntu4

I cannot reach CUPS at the ubuntu on the network form windows machines typing [http://192.168.1.99:631](http://192.168.1.99:631) which is IP number of our ubuntu machine.

CUPS locally serving well when we call [http://localhost:631](http://localhost:631) we can observe everything goes well. A test page comes out from our dot-matrix printer correctly.

In cupsd.conf we added the line like the following:

Location/
...
Allow From 192.168.*.*
...
/Location

Restarted with:

sudo /etc/init.d/cupsys restart

But nothing changes...

Even our ubuntu system allows connection to its own web server by typing from Firefox both [http://localhost](http://localhost) and [http://192.168.1.99](http://192.168.1.99) very well but when we type [http://localhost:631](http://localhost:631) CUPS responds but [http://192.168.1.99:631](http://192.168.1.99:631) an error apppears of CONNECTION ERROR.

SAMBA also works well we can reach ubuntu form a windows machine...

I don't know why cupsd behave like not recognizing the changes that have been made in /etc/cups/cupsd.conf .

Any Ideas?

Thank you all for your interest.

---

### Post by bristleburger on 2006-10-07
Hi Secici

Have you tried switching "Browsing on" in /etc/cups/cups.d/browse.conf?

---

### Post by secici on 2006-10-09
Yes it is on by default. And I didn't change it.

And finally I upgraded to 6.06 LTS and my system is up-to-date.

Let me explain you a summary of the final situation.

At this ubuntu system, locally, I start Firefox, the address: 

[http://localhost](http://localhost)

responds by showing me the default web page. Because Apache is installed and working.

[http://localhost:631](http://localhost:631)

responds by showing me CUPS configuration web interface.

[http://192.168.1.X](http://192.168.1.X) 
(This is the system's IP number)

also responds by showing the default web page...

BUT FINALLY

[http://192.168.1.X:631](http://192.168.1.X:631)

returns me an error telling me a connection problem.

I suspect there is a restriction about some of the Ports not to service outside on my Ubuntu system. Maybe port 631 is one of that ports. 

How can I test that? Or what may be the problem?

Thanks for all the help...

---

### Post by bristleburger on 2006-10-10
Hi Secici

I've just tried the following URL in firefox, and it works fine:

[http://192.168.1.2:631](http://192.168.1.2:631)

192.168.1.2 is the IP address of my dapper cups server.

It's possible that your cups configuration files were not upgraded when you upgraded from ubuntu  5.10 to 6.06 so I have attached my own files so that you can check.

By the way, I notice that the standard /etc/cups/cupsd.conf contains this:

<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

Presumably “Allow @LOCAL” allows access by hosts on the local network.

---

### Post by Pamir on 2006-10-13
Hi

By changing " Allow localhost" to "Allow ALL" you should be able to acces from any machine in the network

---

### Post by ArgentSilver on 2006-11-19
> **secici said:**
> Hi;

What I've learned as I searched documentation about ubuntu and network printing through the day is I have to install samba with a truely configured cupsd.

Installed version of ubuntu is 5.10 CUPS version 1.1.23.10ubuntu4

I cannot reach CUPS at the ubuntu on the network form windows machines typing [http://192.168.1.99:631](http://192.168.1.99:631) which is IP number of our ubuntu machine.

CUPS locally serving well when we call [http://localhost:631](http://localhost:631) we can observe everything goes well. A test page comes out from our dot-matrix printer correctly.

In cupsd.conf we added the line like the following:

Location/
...
Allow From 192.168.*.*
...
/Location

Restarted with:

sudo /etc/init.d/cupsys restart

But nothing changes...

Even our ubuntu system allows connection to its own web server by typing from Firefox both [http://localhost](http://localhost) and [http://192.168.1.99](http://192.168.1.99) very well but when we type [http://localhost:631](http://localhost:631) CUPS responds but [http://192.168.1.99:631](http://192.168.1.99:631) an error apppears of CONNECTION ERROR.

SAMBA also works well we can reach ubuntu form a windows machine...

I don't know why cupsd behave like not recognizing the changes that have been made in /etc/cups/cupsd.conf .

Any Ideas?

Thank you all for your interest.

From my WinXP machines I have to use this form in the URL box: [http://192.168.1.x:631/printers/yourprintername](http://192.168.1.x:631/printers/yourprintername)

I'm using Edgy with whatever version of Cups comes with it, but I think that's the convention that Cups requires.

---

