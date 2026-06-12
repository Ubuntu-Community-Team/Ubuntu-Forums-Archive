---
title: "firestarter blocks ldp (cups) printer"
date: 2005-04-10
forum: Server Platforms
---

### Post by bennettg on 2005-04-10
Hello....nOOb here.  3 months on suse linux and 3 days on ubuntu.  I Love it and am so close from getting away from M$, BUT......

I have a samsung ml1430 printer attached to a linksys wireless print server.  I use a laptop that connects wirelessly.  No problem printing in xp.  

in ubuntu, I went to system, administration, printing and configured my printer via lpd at abc.def.g.hij where the abc's are my local ip address for the print server.  I could print in suse 9.2 without problems (including with the firewall on).  In ubuntu, I can ply print with the firewall (firestarter gui) off.  

I searched the ubuntu forums and linuxquestions.org for hours without success.  I know I need to set rules (policy) in firestarter, but I havent had any success.

Please help this nOOb!

---

### Post by gheorghe_pop on 2005-04-11
Do you have a network or just one computer? If you have a network can you view your network with the firewall on?

 I have an isue with firestarter.For me SAMBA doesent work with firestarter maybe it's the same problem for you too.

---

### Post by bennettg on 2005-04-11
i don't have a network per se.  I have a wireless router that i use with wireless print servers.  the print servers all have static ip addresses.  i cannot see them when firestarter/firewall is on.  any ideas?

---

### Post by gheorghe_pop on 2005-04-11
try to allow all for the print server ip in firestarter and see if that is working

---

### Post by bennettg on 2005-04-11
i am sorry i am such a noob.  could you suggest a step by step process to accomplish this?

---

### Post by gheorghe_pop on 2005-04-12
well it's very simple
you have to open firestarter GUI and in ther you go the policy tab.
now add a new rule,tou will see the button on the topleft corner.
there you enter the ip addres of the print server.
I think you'll have to enter the addres to inbound traffic an to the outbound trafic also.

hope this works

edit:
of course you could check the firestarter doc page
[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

---

### Post by bennettg on 2005-04-12
no luck.  i had previously review the firestarter documentation without success as well.

anyone else having problems?

---

### Post by bennettg on 2005-04-12
this is the error i get in the events tab:

Time: Apr 12 07:16:09 Source: 192.168.1.101 Destination: 64.233.161.99 In IF:  Out IF: eth1 Port: 80 Length: 40 ToS: 0x00 Protocol: TCP Service: HTTP

---

### Post by Maximus_ARNP on 2006-07-12
Error Noted :

Connection to CUPS server failed. Check that the CUPS server is correctly installed and running."

Well I had same problem. I had to allow Ipp as follows:

1/. Start Firestarter
2/. Click on Policy tab.
3/. Select "Inbound Traffic Policy"
4/. In "allow service" pan right click to "Add Rule".
5/. Enter as follows (Hint : You will HAVE TO TYPE "IPP" as a Name):

Name : IPP
Port : 631
IP, Host or Network : 127.0.0.1
Comment : CUPS Print

6/. Click "ADD".

Done with setting rule. Now, check if your CUPS is working.
Go to [http://localhost:631](http://localhost:631)
You should be able to see CUPS Home where you should be able to configure Printer.

If you don't have FireStarter Firewall, then, there might be some other firewall that would be blocking CUPS server. In that case, you will have to find out the way to add policy for that Firewall to allow CUPS Server.

Good Luck.

Rick Detroja.

P. S. : I am aware that original question was posted in 2005. But I am still including a solution just in case if there is any newbee (like myself) still encountering that trouble every now and then!

---

