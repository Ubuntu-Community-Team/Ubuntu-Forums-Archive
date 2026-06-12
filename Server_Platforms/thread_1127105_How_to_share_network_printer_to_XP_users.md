---
title: "How to share network printer to XP users"
date: 2009-04-16
forum: Server Platforms
---

### Post by wolfteeth on 2009-04-16
I know this may be archived in the previous articles but I am really unable to find it spending many time, some articles are also described in 2002/2003 which is quite old that can't explain to me.

I need some guide if you experience on below requirments:
my environment: Win2003 AD + Ubuntu8.10 server
I intergrated Ubuntu8.10 into Windows2003 AD domain and already realized the File Server role in Ubuntu through Kerberos authentication with AD domain, but I don't understand how to add new network printer and share to XP users.

It is a network printer, say, HP laserjet 4300, the printer has been setup a Static IP address, and previously it was added to a Win2003 server that XP uses able to use \\FNP01\HP4300 to connect the PQ and download the drive, but how Ubuntu server do?

I found one article talked about the make_printerdef, such as: 
make_printerdef hp212ip6.inf "HP LaserJet 2100 Series PCL 6" > prints.def 

then setup on smb.conf, but I couldn't find the make_printerdef package that caused my clue lost. also found the Samba 3.x version have drop the package out. emm...

I totally lost and need someone expert guide me for how...

many thanks in advance.

  [print$] 

        path = /var/spool/samba/hp2100/ 
        public = yes 
        writable = no 
        browsable = yes 
    
    
  [hplj2100] 
        comment = unc printing server 
        path = /var/spool/samba/lp 
        #/var/spool/samba/lp/
        read only = No 
        printable = Yes 
        printer name = hplj2100 
        printer driver = HP LaserJet 2100 Series PCL 6 
        printer driver file = /var/spool/samba/hp2100/prints.def 
        printer driver location = \\dataserver\print$ 
        print command = lpr -r -h -P %p %s

---

### Post by HermanAB on 2009-04-16
You are on the right track.  The big problem is how to debug things - how to do little tests in order to figure out why it doesn't work.  Maybe see this:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by Thirtysixway on 2009-04-16
I never really got my printers to share over samba.  What I did was I configured it so that CUPS could be accessed by everyone (not just localhost) and then added the printer on XP as

[http://ipaddressofserver:631/printername](http://ipaddressofserver:631/printername)

---

### Post by wolfteeth on 2009-04-16
> **HermanAB said:**
> You are on the right track.  The big problem is how to debug things - how to do little tests in order to figure out why it doesn't work.  Maybe see this:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)


emm.. thanks@HermanAb, however, it is not quite suit my question.
my question exactly is how XP users download Print Driver from shared Ubuntu server via Samba? or via CUPS? how to setup print queue on Ubuntu either on Samba or CUPS.

---

### Post by wolfteeth on 2009-04-16
> **Thirtysixway said:**
> I never really got my printers to share over samba.  What I did was I configured it so that CUPS could be accessed by everyone (not just localhost) and then added the printer on XP as

[http://ipaddressofserver:631/printername](http://ipaddressofserver:631/printername)


thanks @Thirtysixway, however, I couldn't understand how IPP can allow windows Print drive to XP users? or more steps to guide me?

---

### Post by wolfteeth on 2009-04-23
I created a new one post for this case.
[http://ubuntuforums.org/showthread.php?t=1133606](http://ubuntuforums.org/showthread.php?t=1133606)

---

