---
title: "HowTo:Install&amp;secure wireless connection using D-link DIR-615 router in ubuntu Hardy"
date: 2008-07-21
forum: Tutorials
---

### Post by grobar on 2008-07-21
If you're in windows VISTA/XP/Whatever right now and you've somehow arrived to this page using google then welcome, cause these steps 1-4 are exactly the same in vista/XP!

1. Log in via [http://192.168.0.1](http://192.168.0.1) (default "username: Admin and no pass")
2. Go to setup tab ----> internet ----> internet connection wizard
[LIST]
[*]2.1 CHANGE PASSWORD ! click next
[*]2.2 chose time zone (you know where you are)
[*]2.3  Configure your Internet Connection
DHCP Connection (Dynamic IP Address)
Choose this if your Internet connection automatically provides you with an IP Address. Most Cable Modems use this type of connection.
[*]2.4. press "clone your computer's MAC address" ; hostname: 'your computer name in ubuntu' ( mine is "grobar" yours is ..... )
[/LIST]

3. Go to setup tab ----> wireless settings ----> Wireless Network Setup Wizard (after this we're gonna do manual settings)
3.1 give your network a name= SSID (e.g. 'grobar')
3.2.Automatically assign a network key (Recommended) and chose WAP or WAP2
3.3 Write down the network key!!! Or do printscr and save this page.

Right here you're pretty much set but please do step 4 as well!!! 

4. Go to setup tab ----> wireless settings ---->Manual Wireless Network Setup
4.1 

Wireless Network Settings
[LIST]
[*]Enable Wireless : ALWAYS

[*]Wireless Network Name : (Also called the SSID) the name you gave in 3.1

[*]802.11 Mode : chose "mixed 802.11n,g and b" 

[*]Enable Auto Channel Scan : YES

[*]Wireless Channel : AUTO

[*]Transmission Rate : BEST (Mbit/s)

[*]Channel Width : AUTO 20/40 MHz

[*]Visibility Status : !!!Invisible!!! (so that no outsiders know your SSID except you)
[/LIST]


4.2
Wireless Security Mode : WPA-Personal

4.3 
WPA mode: WPA2 only
Cipher type: AES
Group key update interval : 3600 seconds

4.4
Pre-Shared Key : the one that you generated (and wrote down somewhere) in 3.2. , you can change this key if you want but I suggest to leave it as is...


OK, now you're all set but if you did step 4, you can't see your network cause its status is set to invisible. So go to the upper right corner on your ubuntu desktop: click on the computer icon, click enable networking,click enable wireless and the click connect to other network.
Now you enter:
your SSID name that you entered in 3.1
wireless security: WPA2 personal
type: AES
enter password that you've generated in 3.2 (or 4.4)
ENJOY wireless in ubuntu hardy...

---

### Post by zoward on 2008-08-10
I just replaced my aging Belkin router with a DIR-615, and while I got it up and running immediately, I can't access the web interface through Firefox 3.0.1 under Ubuntu - it gives me a message that "The network appears to be down", even though I can freely access the internet via both ethernet and wireless..  I am connected to the router via ethernet on this box (ie, I'm not trying this wirelessly).  I was able to configure the router using my wife's Vista-based laptop, but it's a pain to have to do that every time I need to access the router.  

Any ideas?

BTW, Thanks for this guide.  Fortunately, the router's disc includes a PDF of the manual.  Unfortunately, the troubleshooting section does not mention the error I got at all.

Thanks,
zoward

---

### Post by zoward on 2008-09-09
Through experimentation, I found the answer to my own question.  I'm posting it here for the benefit of anyone else who searches for this.  The D-Link DIR-615 includes a firewall, which does ALG (application level gateay) configuration.  This needs to be shut off for PPTP for Ubuntu to be able to connect to a Microsoft VPN though this router.

1) Log onto the DIR-615's web page at [http://192.168.0.1](http://192.168.0.1).  Enter your password if necessary.

2) Choose "Advanced" from the bar across to top of the page.

3) Choose "Firewall Settings" from the menu on the left hand side of the page.

4) Scroll down the page until you see a section called ALG - Application Level Gateway.

5) Uncheck the "PPTP" option.

6) Go back to the top of the page, and choose "Save Settings".  Choose to reboot the router after saving.

You should now be able to connect.

---

### Post by zoward on 2008-09-09
Oops.  The above was a separate problem I was having (connecting to a Microsoft VPN under Ubuntu Linux using the DLink DIR-615).  I also solved the problem of connecting to the webapge for hte DIR-615 under Ubuntu Linux in a different way.  Instead of using Firefox, I downloaded Epiphany, which uses Webkit instead of Gecko as a rendering engine, and for some reason the Epiphany liked the javascipt of the web page better than Firefox did, and I was able to connect.

$sudo apt-get install epiphany-browser epiphany-extensions
$epiphany [http://192.168.0.1](http://192.168.0.1)

Enjoy!

---

### Post by NimoTh on 2009-02-25
Great Tutorial! I followed the instructions closely step by step. Some menu items were a bit different but my router is German anyway. Never thought WPA would work so smoothly.

Thanks a bunch grobar.

Cheers,
Martin

---

### Post by sethlbrown on 2010-03-06
Thanks for an excellent tutorial. I run both Windows XP, & an Ubuntu Dell with Hardy installed. One question, out of curiousity, does it matter what the hostname is? If I stick with the default of "DIR-615" are there any drawbacks?

Regards --slb

---

### Post by djqbert on 2011-03-16
Hey, thanks for the help.Before I couldn't use my wireless but was using with cable.After I followed your instruction now im ablet to use wireless but not the cable.It gives the error 691.My password and username does match.I want to use wireless for my laptop and the cable connection for the desktop.How can i solve this problem ? Thanks in advice.

---

### Post by apurvachitte on 2011-10-28
hi,

I have installed ubuntu 10.04.03 , how do i install d-link dir-615 router on that? is the process same? or different?

---

