---
title: "Which brand of printers should I stick to?"
date: 2020-11-19
forum: The Cafe
---

### Post by Perfect Storm on 2020-11-19
Hello,

I have nothing but pain with HP wireless printers (bugs, bugs, bugs). Can anybody recommend a printer that are a no-brainer.


Thanks.

---

### Post by crip720 on 2020-11-19
I have read that Bother's are decent,  but 20.04 seems to be having a lot of trouble with printers/wireless and a few other things that worked well in earlier versions.  I have a Pantum printer that worked well, but is giving problems now, unknown if printer or Ubuntu.  Would google makes and Linux drivers for best choice.

---

### Post by TheFu on 2020-11-19
Sure - 
Step 1: don't use wifi printers.  
Step 2: Stick with wired ethernet or (USB printers + CUPS.)
Step 3: Look for network printers that support **postscript** and IPP natively.  Then you can print postscript files over the network trouble free from any client. No driver needed. Of course, postscript printers cost more.  More than I'm willing to spend. 

If you need the printer to be somewhere that ethernet doesn't reach, there are MoCa and powerline network extenders. I'd use MoCa 2.5 if there was coax nearby and I planned to put more than just a printer. MoCa is 2-3x more expensive than cheap powerline. OTOH, powerline throughput is often 10% of whatever the box claims. For a printer, that might not matter.  Mine claims 600 Mbps, but delivers only 60 Mbps between different floors of the house.

That's my best advice.

Not really helpful to you, today, but I have 2 old working printers.  A Brother All-in-One and a Samsung laser both from 10-15 yrs ago. Both were under $60 new.

The Samsung model is in the list of supported printers in all the printer setup tools I've seen. For a few years, I had to pick a model that was close, but not exact. Never noticed any issues doing that.  ML-1710 vs ML-1410. Basically, the Samsung only gets used to print about 50 pages in March-April of every year.  This year it was used a few times to print some govt forms that had to be signed and faxed. That reminds me, I need to do that again today.

I don't use the Brother for printing, ever.  Got it for fax and page scanning reasons.  Both devices are USB connected, no networking. I think there are $20 ethernet to printer connection devices.  I worked at a company with 6000+ printers that were spread out over 10,000 sq miles in different company locations. Many of those locations were 2 month rentals, so they'd pop-up, do some sales then move every 2 months.  These tiny "print servers" were important for sales.  

My print server is still running 16.04, so I don't know how well supported newer releases really are. With 16.04 clients, I just run the **system-config-printer** wizard and it showed a list of printers on the network. Picked the CUPS print server hostname and vendor+model from the list. Took under 20 seconds - and I was completely surprised at how easy it was.

Just did this with a 20.04 Ubuntu Mate install (running fvmw WM, not Mate) and it was the same. Bonehead. I think the trick is to have avahi running on both systems - the CUPS server and the desktop.  As much as I dislike avahi, this magically finding printers could be worth it.

If the next LTS doesn't support my printers, I'll just setup an LXD container with 16.04 or 20.04, do a little USB passthru for the printer and forget about it for 5 yrs. [https://ubuntu.com/blog/usb-hotplug-with-lxd-containers](https://ubuntu.com/blog/usb-hotplug-with-lxd-containers)

---

### Post by iamjiwjr on 2020-11-19
My Brother HL-L2390DW does not work on any Ubuntu-based distro I've tried. It worked partially for a short term, but by the second or third boot it has been doa consistently. The scanner graphics are a mess and don't work.

However, the Brother works great on non-Ubuntu-based-Debian distros I 've tried. LMDE, Debian, Deepin, for instance, work great. Solus, Manjaro, Fedora, and especially openSUSE (the champ) work fine.

I am of the opinion that Ubuntu has a significant printer issue that needs to go to the top of their priority list. Something they're doing is screwing up a lot of printers.

I don't know how they are now, but my past experience with HP printers has been fine with pretty much all distros.

---

### Post by oldfred on 2020-11-19
My brother printer has been working just fine, with Kubuntu.
It is immediately recognized with Live installer and installs what it seems to need automatically.
But it seems to set up 3 printers and only one really works. And other works for scanning?

I got frustrated with my HP, both not printing and cost of ink cartridges.
The HP also had multiple printers set up and sometimes one worked and sometimes another worked.
Something about the new ipp printing that is supposed to be automatic, is not fully fixed for all printers.

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  lpstat -e [/COLOR]
Brother_HL_L2390DW


[/FONT]

---

### Post by TheFu on 2020-11-20
> **oldfred said:**
> My brother printer has been working just fine, with Kubuntu.
It is immediately recognized with Live installer and installs what it seems to need automatically. 


Is it a wifi printer?

---

### Post by zebra2 on 2020-11-20
I use a HL-2270DW Brother Laser printer using wifi on all of my Lenovo laptops.  Using 20.04, 20.10 and 21.04 perfect install on all three.  The trick is to install the linux drivers from Brothers support site and then install using **system-config-printer.** The newer printer install script won't install the printer correctly or at all.  The wifi works fine on both of my printers with the newer versions of Ubuntu.  I also have a cheap $20 Canon MG2920 printer/scanner that I have never used as a printer because I don't want to buy the ink but it does a first class scan. The Box said "Windows Only" but i bought it anyway and found linux drivers on the Canon.uk site. There wasn't drivers on the Canon.us site. I've had this printer/scanner for years and I install the Canon Drivers and use **system-config-printer **to install. I couldn't get to a setup on the Canon printer that would allow a static IP to be set but I was able to use the wifi pairing button on my router with wifi in pairing mode on the printer. It was easy once I figured it all out.  These things can work in linux, you just need to have a little know how, a lot of persistence, and **system-config-printer **installed.  
PS: just in case you missed it. sudo apt-get install system-config-printer.








2

---

### Post by oldfred on 2020-11-20
Printer is both USB & Wireless.

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  lpstat -l -e [/COLOR]
Brother_HL_L2390DW network none ipp://Brother%20HL-L2390DW._ipp._tcp.local/ 
HL_L2390DW network none ipp://HL-L2390DW._ipp._tcp.local/ 
HL_L2390DW@localhost permanent ipp://localhost/printers/HL_L2390DW@localhost implicitclass://HL_L2390DW%40localhost/


My wife has printed from her iPad.
But I believe my default is the USB connected connection.

I already added Wi-Fi before I tried scanning, so not sure if this issue applied or not.
But it works. :)

WiFi Brother Print
[https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux](https://help.brother-usa.com/app/answers/detail/a_id/166020/~/connect-to-a-wireless-network---linux)
scan issues 2395
[https://ubuntuforums.org/showthread.php?t=2443188](https://ubuntuforums.org/showthread.php?t=2443188)

This is Brother printer:
[FONT=monospace][COLOR=#000000]Nmap scan report for 192.168.1.21 [/COLOR]
Host is up (0.053s latency). 
MAC Address: xx:xx:xx:xx:xx:xx (Chongqing Fugui Electronics)


[/FONT]

[/FONT]

---

### Post by VMC on 2020-11-20
I have Brother HL2320D. I use to have to run that brother script, and then reorient the pdd file. Not anymore.
Since 20.04 I just plugged in my usb cable turned on Brother, and within 15 seconds it was ID'ed and ran a test page!

---

### Post by Perfect Storm on 2020-11-20
Thanks for the input.

---

### Post by SeijiSensei on 2020-11-21
I have a Brother HL-3170CDW.  Only modification I needed to make was to set the printer into Postscript emulation to get it to print envelopes correctly.

The printer is directly wired with Ethernet into my router. You can still print from wifi devices this way without using the wifi features of the printer itself. Brother has a useful app for Android devices that will detect the printer. DK about iOS devices, but I'd imagine they'd have an app for them, too.

---

### Post by Raffles727 on 2020-11-21
By all accounts, and my personal experience, Brother.

---

### Post by kurt18947 on 2020-11-21
I've had good success with Brother using their installer script. Older inkjet MFD, MFC-6490CW and HL-3170xxx. They're both wired networked and have static network addresses. I use system-config-printer to configure the connection using socket, e.g. socket://printer. IP. address:9100.  We also have a Samsung monochrome laser that is recognized "out of the box" but prints well with some apps e.g. Libre Office but with other apps e.g. Firefox it'll print a line or two of gibberish per page and will keep printing until it runs out of paper.  I found Samsung linux drivers on HP's support site (HP bought Samsung's printer business a few years ago), those work as expected.

---

### Post by ycooreman on 2020-11-25
I use a Brother MFC-J5330DW, wirelessly. 
The printer is automatically detected and works without issues for printing and scanning

---

