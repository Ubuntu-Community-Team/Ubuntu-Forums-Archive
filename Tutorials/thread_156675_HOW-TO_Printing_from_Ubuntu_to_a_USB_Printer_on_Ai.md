---
title: "HOW-TO: Printing from Ubuntu to a USB Printer on Airport Extreme Base Station"
date: 2006-04-07
forum: Tutorials
---

### Post by davygravy on 2006-04-07
[SIZE="4"]**How to print (from a Ubuntu/Linux box) to a USB printer that is connected to an Airport Extreme Base Station**[/SIZE]


*Disclaimer: I assume no responsibility for your tinkering with your computer or your Airport Extreme Base Station.  What I did worked great for me on my AEBS, but I can't assure you of your own success.  Proceed at your own risk.*

When I saw Ubuntu Linux for the first time, I immediately wanted to use it on an older Mac that we had sitting idle.  I installed it and connected it to our already established network, which had an Apple Airport Extreme Base Station (AEBS) as its wireless hub.  Connected directly to the AEBS was our EPSON Stylus Color 740, which we could print to from any Mac in the house, including our laptops (wirelessly).  Getting the Ubuntu box to print to it ***should*** be easy, right?  

Well, one might have hoped so, but this was not the case.  I found hints and tips at various sites and forums, but nothing seemed to work.  After about twenty hours of struggling, I notice a forum entry that mentioned how an AEBS firmware upgrade changed ip ports and printer access.  I found I had to downgrade the AEBS firmware. Once I did that I was printing within a few minutes.

In short, the AEBS doesn't understand IPP or LPD printing protocols when it talks to USB printers connected directly to it.  It uses ip port 9100 or 9101, depending on what version firmware you have installed.  Also, to print to such a printer, it uses the AppSocket/HP JetDirect method.  My original setup would not work with port 9101.  To get mine to work, I had to downgrade the AEBS's firmware to an older version that opened port 9100 on the AEBS (instead of 9101) and then add a printer on the Ubuntu box.

Here are the details.  If you really want to understand what you are about to do, and what your choices are, read through to the end, including the notes (especially note #I).  You might get by with some short cuts that could save a lot of time.  It is assumed that you already have an established network, an AEBS, and a working USB printer connected to that base station.


==============================================


0.   **Gather the essential information**:

Determine your AEBS's IP address.  It will probably look like 10.0.1.1 or 192.168.1.1, or something like that.  It is preferable to have a static IP for your AEBS since it will make what do later on a lot easier.  

You will also need to know your printer's make (Canon, EPSON, etc.) and model (Stylus Color 740, etc.).



1. ** Find out if you need to open port 9100**:

Port scan your Airport Extreme Base Station to see if port 9100 is open - you will need to tell your port scanning software the ip address of your AEBS.  I used nmapfe (a GUI front end for nmap), but I caution against using the port scan in Gnome's Network Tools (in the Admin menu), as it seemed to be doing only an abbreviated scan and didn't pick up any open ports, though this may have been a problem with Dapper Flight 6.   If port 9100 is open, it should list something like this:

[INDENT]Starting Nmap 3.95 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-04-08 09:58 CDT
Interesting ports on dnm-basestation.local (10.0.1.2):
(The 1668 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
9100/tcp  open  jetdirect
10000/tcp open  snet-sensor-mgmt
MAC Address: 00:03:93:E6:3F:7D (Apple Computer)
Device type: WAP|broadband router
Running: Apple embedded, ARRIS embedded
OS details: Apple Airport Extreme Base Station (WAP) or ARRIS Cadant C3 CMTS Cable Modem
Uptime 1.437 days (since Thu Apr  6 23:29:32 2006)

Nmap finished: 1 IP address (1 host up) scanned in 3.789 seconds[/INDENT]




If your port scan shows 9100 is open, then go to step 3 (you can skip step 2).  

If 9100 is not open but 9101 is open, then you may try step 2.  

If a port scan shows no open ports whatsoever, then check your AEBS's ip 
address to see that it is correct, or try a different port scanning utility.  



2.   **Open port 9100 on your AEBS:** (see disclaimer above at top)  

If port 9100 is not open, you can try downgrading the firmware to Apple's version 5.4 e Airport Extreme Base Station firmware.  For me, this was an fast, easy and painless operation.

I did my downgrade in Tiger, and probably Panther would work, too.  You might be able to do this in Windows using Freebase, a Windows Utility for AEBS.

Google "airport extreme base station 5.4" and you should be led to the Apple site where you can download the firmware update - just download it to your desktop.  Before you tinker with anything, it might be a good idea to save your current AEBS settings so that if something goes haywire, you can restore your setting with the minimum of effort.  

To downgrade your firmware in OS X, start up Airport Admin Utility and select the base station that you want to downgrade the firmware on.  From the menu "Base Station" choose "Upload".  This will downgrade the firmware to 5.4 (or whatever version that you choose).  I lost no functionality when I did this.  I did have to go back to the Macs running 10.3 & 10.4 and use Printer Setup Utility to reestablish the printer, but it was painless since it came up as a Bonjour printer.  YMMV.

Note that from the OS X side, whenever you subsequently open up Airport 
Admin Utility and access your AEBS, you will probably be asked if you want to "upgrade" your firmware.  Choose "no".

Go back to step 1 and see if port 9100 is open.



3.   **Set up your printer connection on your Ubuntu box**: 

Go to your Linux box (probably running Ubuntu Dapper or later) and open a 
browser (like Firefox) window.  In the URL window type in 

localhost:631 

and press enter.  This should take you to the CUPS home page.  Choose 
Printers, and Add a Printer.   

Enter a name for it (keep it simple w/ no strange characters), a location 
(descriptive) and a description (again, descriptive).  Click continue.

From the pull-down menu select 

AppSocket/HP JetDirect

and click Continue.


For the Device URI: field, supply the following:

socket://[your AEBS's ip address]:9100

and press continue.  Mine was "socket://10.0.1.2:9100" , without the quotes.

For the Model/Driver you will have to enter the Make (it was EPSON for me), click Continue, and then the Model (it was EPSON Stylus Color 740 for me, and you can choose different options within this model). (I did not choose Apple LaserWriter - I was told that I had to do this by several well-intending people, but that suggestion was errant.  It would not work at all with the Apple LW driver.) Press Continue again.

If everything goes as it should, you will be told that your "Printer [your 
printer name here] has been added successfully."  You can then click on Printers in the top menu, and you will see your printer listed on the Printer page.  Here you can find a whole set of options for printing a test page (a must), and other printer operations.  

Check the name, description, location and URI for typos.



4.  **Check to see if it works, and maybe reconfigure**:

Print a test page by clicking on Print Test Page.

If your printer prints the test page nicely, then great!  You're done (probably)!  You can set it as your default printer by using the Set As Default option, if you like.

If it prints the test page but the color is out of whack, you can try using a different driver for your model, or configuring your printer with the Configure Printer option.  

If it does not print, then you can either delete the printer with the Delete Printer option and go back to step 3, or try to modify its settings with the Modify Printer option.



5.  **Test it with real-world software you use often, and maybe reconfigure**:

If you were successful in step 4, then try printing from Firefox, OpenOffice Writer and/or a few of your most often used applications.  If you get strange output, you can go back and redo step 4.



6.  **Enjoy**:

Enjoy!

==============================================


Notes:

I.   You can try just printing via AppSocket/HP JetDirect, socket://[your 
AEBS's ip address]:9101 , using the make and model drivers for your USB printer.  Maybe it will work for you right away with port 9101.  It didn't work for me with port 9101, but this may have been because of a bug in CUPS (v1.2 is a release candidate version) or in Ubuntu Dapper Flight 6 (a pre-release development version).

II.  I used the web-based CUPS Printer setup interface because the System-
>Admin->Printers tool seemed to be acting strange sometime in Ubuntu 
Dapper Flight 6.  This was when Dapper was still in development, and more 
than a handful of users were complaining about broken or misbehaving printers.  I saw this in the Ubuntu forums, and also at the CUPS bugs forum < [http://www.cups.org](http://www.cups.org)  > .   This forum thread < [http://www.cups.org/newsgroups?s1655+gcups.bugs+v1660+T0 ](http://www.cups.org/newsgroups?s1655+gcups.bugs+v1660+T0 )  > was quite funny, for me, in retrospect, as it seemed that the thread starter was having the same problem that I was, but the responder (from CUPS publisher ESP) seemed to be pretending that "all was well".  Certainly, it is not funny if you are the one having the printing problem.

III.  I spent about 20 hours researching and trying to get my AEBS to print via AppSocket/HP JetDirect on port 9101.  Apple's AEBS firmware update 5.7 had printing going through port 9101, and try as I might, I was not able to get it to work.  Notably, I could not get it to work with port 9101 with either Linux or OS X Tiger (10.4) via  AppSocket/HP JetDirect.  Of course, in Tiger the printing to the AEBS was autoconfigured with Bonjour (Apple's implementation of Zeroconf, Avahi in Linux) and this didn't use the AppSocket/HP JetDirect protocol, but PAP/APAP protocol instead, which seems to be a proprietary Apple thing.

IV.   If the problem w/ the  AppSocket/HP JetDirect interface is a Ubuntu problem or a CUPS problem, then maybe it will be resolved so that one can print via port 9101 without problems, and without having to downgrade the AEBS firmware.  Since my work was carried out under Dapper Flight 6 (a pre-release development version), one can hardly expect that all the bugs and kinks were worked out already. 

V.   If you have Airport Express, you may find similar situations and 
problems.  I don't know how similar or dissimilar the problems and solutions may be, because I haven't tried this on an Airport Express.

VI.   I had all but given up, and had even tried to buy a US Robotics MaxG Router w/ built-in USB print server to replace the AEBS.  Compusa had a sale on them, but they were sold out.  So I went home and gave it one last try.  

And downgraded the firmware.  Patience (or stuborness) can be a good thing.

VI.   I assume no responsibility for your tinkering with your equipment.  Proceed at your own risk.

---

### Post by dcapitalj on 2006-08-04
Hi. Anybody here willing to help a Mac user?
I got the exact same problem as described in this thread, but no solution yet. The thing is I can't get the Airport Express base station to open port 9100 (or 9101, for that matter). Tried lotsa things I found over the Net, like installing altenative PPD's, like downgrading to firmware 6.1.1, like turning off "IP broadcasting"... nothing worked. Please help. Airport's other functions work 100%.
Config is:
Apple MB pro w/ OS 10.4.7
Airport Express firmware 6.1.1
trying to print to a HP 1125c over the AXBS's USB port. (hard-wiring the printer to the MB works OK)

Thanks in advance

---

### Post by DMHamm on 2006-11-01
I keep getting a "Enter CUPS Username and password" box, and NOTHING I enter seems to work: the box just keeps popping up. If I hit Cancel, I get a "Not authorized" error. This is in 6.06 LTS.

Any ideas what to do?

---

### Post by mbittleston on 2006-11-06
Printing to an HP inkjet printer (deskjet 932c) connected to the airport extreme seems to work fine for the following:
Ubuntu 6.06 LTS Dapper Drake to an airport extreme with firmware v5.7
printer settings are:
Network printer: HP JetDirect printer
host: (ip address of airport)
port: 9101

I did not use the cups interface, just the System->Admin->Printers interface.

---

### Post by jymbob on 2006-11-14
Set up here via System->Admin->Printers:
Laserjet 5L
Network Printer: HP JetDirect
host: 192.168.0.xxx
port: 9101

Ubuntu 6.10 LTS

Seems to be fine.

---

### Post by dare dukes on 2007-11-20
Thanks!  Works like a charm.

---

### Post by motorbikemike on 2008-01-05
Thank you, I was able to make my new install of Ubuntu see and print to my wife's printer on her airport station with this information.  It works well, the test pages printed out very clearly and documents from open office print the way they should.

---

### Post by jamaio on 2008-02-08
> **jymbob said:**
> Set up here via System->Admin->Printers:
Laserjet 5L
Network Printer: HP JetDirect
host: 192.168.0.xxx
port: 9101

Ubuntu 6.10 LTS

Seems to be fine.
This worked Great, 

I used port 9100 with no problems.

I print wirelessly from my laptop and from my wired desktop.

Thanks!!!

---

### Post by renatoborges on 2008-05-25
all you have to do is install the avahi-utils by the synaptic package manager (system/administration/synaptic package manager) and after installation restart your system.

then go to system/administration/print and click the new printer button, your printer or printers, connected to the airport express should appear in the list of printers available for installation.

---

### Post by Varikk on 2008-06-13
Might I just say this post was nice and concise and you saved me 20 hours trying to figure this out myself.  It took me 2 minutes to connect to the printer.  I had been able to connect to it using my macbook and vista machine but have since migrated to ubuntu and was distressed about having to figure this out.  It took me all of 2 forum reads and had yours been the first, well nuff said.  Thanks!

My only input would be a very easy way to find out your Device URI: field is to use Avahi (looks for bonjour style connections on your network).  It can be found in applications/add remove - search field.

Thanks again!

Varikk

---

### Post by tpischke on 2008-07-07
Thanks!  Got me up and printing on my friend's AEBS in about ten minutes.  I was able to use the Print Administration tool in Hardy Heron.  Scanned the AEBS at 10.0.1.1 using nmapfe and found port 9102 open.  Using AppSocket/HP JetDirect, I entered host 10.0.1.1 and port 9102.  Voila!

There was no need to do anything else on either Ubuntu or the Mac/AEBS.

---

### Post by keheikev on 2008-08-03
> **renatoborges said:**
> all you have to do is install the avahi-utils by the synaptic package manager (system/administration/synaptic package manager) and after installation restart your system.

then go to system/administration/print and click the new printer button, your printer or printers, connected to the airport express should appear in the list of printers available for installation.
It worked perfectly I did not have to follow the lead posts using the jet direct method
Thanks!
:kihei:)

---

### Post by davygravy on 2008-08-19
Woohoo... after I went to a x86 machine w/ Gutsy (I needed it for some light dev work I'm doing), I could no longer get my own tutorial to work for me...:confused:

Hmmm...

About 4 weeks ago I upgraded to Hardy and now it works again... not sure what was up, but I'm glad to have printing back...

---

### Post by flapane on 2009-03-03
Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-03-03 21:10 CET
Interesting ports on 10.0.0.1:
PORT     STATE  SERVICE
9100/tcp closed jetdirect
9101/tcp closed jetdirect
9102/tcp closed jetdirect
9103/tcp closed jetdirect
9104/tcp closed jetdirect
9105/tcp closed jetdirect
9106/tcp closed jetdirect
9107/tcp closed jetdirect
9108/tcp closed unknown
9109/tcp closed unknown
9110/tcp closed unknown

how to open them from linux

---

### Post by herculea8n1982 on 2009-04-25
Awesome guide thanks worked a treat. I didn't even know there was a web interface like that for CUPS!

---

### Post by ronmihu on 2009-07-21
I read these posts and they where very helpful.  I am using the currently latest production release of 9.10.  I approached this from a different angle however.  I went to System->Administration->Printing and clicked on the New button.  It searched for my printers, but did not find it.  So I clicked on the Network Printer expansion and looked at the options.  I selected AppSocket/HP JetDirect and entered in my Airport Extreme IP address of 10.0.1.1 and left the default port at 9100.  Now click the Forward button at the bottom of the dialogue window.  The next window asks you to select your printer from the database.  Click Forward again.  I selected my PhotoSmart C3100 series from the selection of HP printers and clicked Forward again.  Enter in the printer description information if you don't like the defaults, then click Apply.  

That's all there was to it.  It found my printer and I printed the test page.  Perfect!

Thanks everyone!

---

### Post by Zookalicious on 2010-10-23
> **ronmihu said:**
> I read these posts and they where very helpful.  I am using the currently latest production release of 9.10.  I approached this from a different angle however.  I went to System->Administration->Printing and clicked on the New button.  It searched for my printers, but did not find it.  So I clicked on the Network Printer expansion and looked at the options.  I selected AppSocket/HP JetDirect and entered in my Airport Extreme IP address of 10.0.1.1 and left the default port at 9100.  Now click the Forward button at the bottom of the dialogue window.  The next window asks you to select your printer from the database.  Click Forward again.  I selected my PhotoSmart C3100 series from the selection of HP printers and clicked Forward again.  Enter in the printer description information if you don't like the defaults, then click Apply.  

That's all there was to it.  It found my printer and I printed the test page.  Perfect!

Thanks everyone!

It's so beautiful when something actually works on the first try :,D

Sorry to bump a dead thread.

---

### Post by xubuntu84 on 2010-12-29
Thanks for the support.  Had no idea that you could access CUPS via an internet browser.  Easy setup, good tutorial!

---

### Post by blackappy on 2012-08-24
Thanks for the HOW-TO.

---

