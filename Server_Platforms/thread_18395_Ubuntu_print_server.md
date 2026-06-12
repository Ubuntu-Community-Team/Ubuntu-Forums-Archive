---
title: "Ubuntu print server"
date: 2005-03-06
forum: Server Platforms
---

### Post by squirrel_chaser on 2005-03-06
I am trying to print from a Debian unstable box to a Ubuntu box with a printer attached.  So far no success.

On the Ubuntu box, browsing is turned on and security in the cupsd.conf file allows network access to cups.

I can ping the Ubuntu box and nmap indicates that port 631 is open on both the Ubuntu box and the Debian unstable box.

Using the ethereal tool to examine network activity, there is no cups broadcast comming from the Ubuntu box. 

Please suggest what I may have misconfigured.  It is probably something simple.

By the way, I have been using Ubuntu for about 6 weeks and really enjoy it.

Thanks for the great forum.

---

### Post by FX on 2005-03-06
At one time I had my machines setup for printing through the network. Since then I had lost it cause of some differents reasons. I can't exactly remember how I got it to work or the configuration I used and after struggling for a while I gave up. I made it easier on myself and bought a Netgear printer server connection deal. It is much easier to setup and you do not have to have a pc running all the time. 

Just plug it into your router and then into your printer. Go throught the printer config tool under "system">adminstration>printing. After you find your ip of the printer server through your routers home page just put that in there. Then for the Queue put in ld. For me works like a charm.

Sorry its not really the answer you are looking for, but all I can say is having a print server makes life alot easier.

---

### Post by flint_ on 2006-02-03
Good posts here, but I am rebuilding my debian print server to be an ubuntu print server, the damn thing will pring locally from the cups test button on the "hostname:631" web site, buit there is not ipp shownin that would allow printing from a remonte machine.  I know I am missing the obvious, but you try reading the cups documentation....

Sometimes I wonder if CUPS stands for:

Completely 
Useless 
Print 
Server

Regards,

Flint

---

### Post by wrtrdood on 2006-02-03
Have you identified the server in the client file on the Debian system?

---

### Post by flint_ on 2006-02-04
Flint[/QUOTE]

Regarding the completely useless print server, I have now worked the problem out.  The end of the deal is the acceptable syntax of the remote share.  The example of correct client syntax is as follows.  Note that this example fixed my problem...

ipp://beta/printers/LaserJet-1300

The secret undocumented syntax to this is as follows. Note that this syntax is very important, and I will break it down below:  

 ipp://beta/printers/LaserJet-1300
  ^     ^     ^          ^
   |     |     |          |
   |     |     |          See Note 1
   |     |     |          
   |     |     This is reserved and must be there          
   |     | 
   |     This is the system name of the server it can 
   |     be a numeric IP octet.
   |     
   This, the colon and the slash syntax are madnatory

Note 1.  This name can be found by ssh'ing to the server 
and typing "sudo lpc status" putting in your password and 
the first returning line is the name of the printer.  Copy
and past this first returning line as the name of the printer.

This all assumes that you have installed the cups server in a sane and functional way.  In the fullness of time, I will be completing an exposition on this matter based upon the work of Mr. David Boyce, a very smart fellow nessled in the rolling hills of Virginia.

Kindest Regards,

Paul Flint

---

### Post by whichpaul on 2006-07-18
Thanks, worked for me :) Though you shouldn't have to search through forums to do something as simple as connecting to a network printer that is running the same OS as your host! How can linux ever conquer the desktop when even experienced users can't perform simple tasks with ease? :(

---

