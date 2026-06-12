---
title: "Port 80-No External Access"
date: 2009-02-26
forum: Server Platforms
---

### Post by dlrawlings on 2009-02-26
I know there are lots of post related to Port 80, however, I've not found the solution to my specific problem...yet...  Here's the deal:  I am running Ubuntu Intrepid with a LAMP server.  I am able to access my ip address internally but not able to access it externally.  I have called my ISP who say that Port 80 is open and they can clearly see my computer.  I have even connected the computer directly to the cable modem to eliminate any router issues.  Nevertheless, I'm still not able to access the computer outside of my network.  Apache is running and listening to Port 80, I'm able to open other ports (8000, 22, etc) and access them both internally and externally.  It is just port 80 that I'm having problems.  Any help would be appreciated.

---

### Post by poomalairaj on 2009-02-27
Did you configured your router/modem to forward the port 80?
Also you need to open the port 80 in your firewall...
If you have done the above, please ping your machine from some other computer. i.e., not the computer in which you have installed LAMP or a computer in your local network.
Please refer this link for a guide
[http://chennaigeekspot.blogspot.com/search/label/home%20web%20server]("http://chennaigeekspot.blogspot.com/search/label/home%20web%20server")

---

### Post by sahabcse on 2009-02-27
Hi

Check your port state 

#nmap localhost --------->in your machine

#nmap your system ip ---------->in external machine

eg)sahab@sahab-desktop:~$ nmap 192.168.2.143

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2009-02-27 11:07 PST
Interesting ports on 192.168.2.143:
Not shown: 1713 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
[COLOR="Red"]80/tcp open  http[/COLOR]

Nmap done: 1 IP address (1 host up) scanned in 0.119 seconds
sahab@sahab-desktop:~$ 


Also try telnet yoursystem ip 80 -->in external machine

eg)
sahab@sahab-desktop:~$ telnet 192.168.2.143 80
Trying 192.168.2.143...
Connected to 192.168.2.143.
Escape character is '^]'

If it connect means there is no firewall issue, Check with your router...

---

### Post by dlrawlings on 2009-02-27
Thank you for your help.  Since the webserver is attached directly to the modem there are no firewall issues.  At least none that I am aware of.  I have pinged the computer as Poomalairaj suggested and got the following results:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 16ms, Maximum = 21ms, Average = 18ms

As mentioned before, it is only with port 80 that I have any problems accessing externally, which is very odd.  Is it possible that there could be an issue with the modem?

---

### Post by volkswagner on 2009-02-27
Depending on who you speak with at your ISP, you may get different answers.

If you are not using any software firewall my guess is it is your ISP causing the issue.

Check at [canYouSeeMe]("http://www.canyouseeme.org/") for port 80.

---

### Post by dlrawlings on 2009-02-27
You're definitely correct... I've talked with several folks from my ISP with different responses. Utilizing "canyouseeme.org" it was not able to see me on Port 80.  It's just odd that the ISP tells me that Port 80 is open, I can ping the webserver from an external computer, but it does not access through a web browser, yet I have access to the webserver internally through a web browser.  I can only think that it is either the modem or something with the ISP...  Thoughts?

---

### Post by volkswagner on 2009-02-27
> **dlrawlings said:**
> You're definitely correct... I've talked with several folks from my ISP with different responses. Utilizing "canyouseeme.org" it was not able to see me on Port 80.  It's just odd that the ISP tells me that Port 80 is open, I can ping the webserver from an external computer, but it does not access through a web browser, yet I have access to the webserver internally through a web browser.  I can only think that it is either the modem or something with the ISP...  Thoughts?

If canyouseeme.org reports not being able to connect, you can rest assured that your ISP blocks port 80.  To run a web server with your ISP you will need to run it on a non standard port.

Try other ports such as 8080 at canyouseeme, and change the port in /etc/apache2/ports.conf to reflect the open port.

This is not pretty as you will now need to include the port number in your URL.

---

### Post by dlrawlings on 2009-02-28
Well after much polite haranguing with the tech support folks of my ISP, miraculously I now have Port 80 working.  They claim that it was always open.  I'm not sure what the explanation is, I only know that it now works like a charm.  Just goes to show you that even in a high tech world, prayer may be the only solution.  Thanks for everyone's help!

---

