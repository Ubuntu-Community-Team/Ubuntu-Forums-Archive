---
title: "HOW TO: Brother 32/64-bit Printer Drivers (and AirPrint!)"
date: 2012-06-01
forum: Tutorials
---

### Post by BonjourPrinter on 2012-06-01
Brother's official instructions are horrible, awfully laid out, and are wrong in so many places, such as suggesting that you edit /etc/printcap which is an auto-generated file that you CANNOT edit because any changes will automatically be replaced (herp derp), along with many other plain errors; Brother's Linux people seem to be on a salary of peanuts and the instructions appear to be a hobbled-together mess of ancient, outdated misinformation.

Other people have tried to fill these horrible documentation flaws by figuring out how to do things and have made a few guides, but all of those guides have been very messy and full of useless or plain wrong steps and with vital details left out, mostly due to being based on the horribly wrong instructions by Brother.

I've spent SEVEN hours digging deep into the internals of Brother's drivers and the AirPrint and mDNS protocols and have a very good understanding of how everything works, so here I present to you a complete, perfect guide for installing Brother printer drivers and even getting AirPrint to work, covering all required steps (over 50% of which are never even covered by Brother), while avoiding all the junk/plain wrong misinformation! If you look at the official instructions you'll see LOADS of things that are not covered here, and vice versa; rest assured that you have ZERO reason to read the official instructions and will in fact just be causing yourself HARM by doing so. Take my word for it and AVOID Brother's "help" pages completely!

The guide refers to the HL-2270DW in many places (since it's an excellent, best-selling printer and I needed something for the example commands), but just substitute it for your own model number if you have a different model!

The steps have been marked as either "32/64 bit", "32-bit only" or "64-bit only". Do the ones appropriate for your system!

Finally, these instructions are written for all versions of Ubuntu and Linux Mint, but other distros should work as well (either as-is or with minor changes; most notably you might need the RPMs rather than the DEB installers). I only provide full guarantees of success for Ubuntu and Linux Mint.

(64-bit only) Install the pre-requisite package:
**# sudo apt-get install ia32-libs**

(32/64 bit) Download both driver deb files here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW)

(64-bit only) Download the 64-bit patch file here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00098](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00098)

(64-bit only) Rename the patch file to **brdpkgdeldep.sh** and make it executable.

(64-bit only) Navigate to the folder that contains your two package files and the patch and run these commands:
# **./brdpkgdeldep.sh hl2270dwlpr-2.1.0-1.i386.deb**
# **./brdpkgdeldep.sh cupswrapperHL2270DW-2.0.4-2.i386.deb**

(64-bit only) Install the patched drivers (note the "a" after the version numbers, indicating 64 bit versions):
# **sudo dpkg -i --force-all hl2270dwlpr-2.1.0-1a.i386.deb**
# **sudo dpkg -i --force-all cupswrapperHL2270DW-2.0.4-2a.i386.deb**
(the force flag means force installation despite 32 vs 64 bit package mismatch)

(32-bit only) Install the regular drivers (note the lack of "a" after the version numbers):
# **sudo dpkg -i --force-all hl2270dwlpr-2.1.0-1.i386.deb**
# **sudo dpkg -i --force-all cupswrapperHL2270DW-2.0.4-2.i386.deb**

(32/64 bit) Configure CUPS for your printer connection (it's pre-set to USB but you might want to change it to Networked, so that's what I'll describe here):
* Go to [http://localhost:631/](http://localhost:631/) in a browser and go to the Printers tab and select the HL2270DW.
* It defaults to "Connection: usb:/dev/usb/lp0", so if you've connected it over USB, you can proceed to printing a test page right away, otherwise read on to switch it to a networked connection.
* From the Administration submenu, select "Modify Printer" and log in with your linux administrator account, then wait a while for it to discover networked printers via Bonjour/mDNS.
* You should see four duplicates of the HL-2270DW under "Discovered Network Printers", and you won't know what protocol each is without selecting it. Just select a random one and hit Continue. (Would have been nice if CUPS' web interface showed the protocol in parenthesis after each one to make this step easier)
* If the "Connection" path says "dnssd://Brother%20HL-2270DW%20series._pdl-datastream._tcp.local/" then you've got the right one; if not, hit Back and try another until you find this one (the key part is the "pdl-datastream" protocol, which is REQUIRED for networking printing; IPP will NOT work).
* If you want others on the network to be able to print to this printer via your machine, check the "Share This Printer" box and then hit Continue.
* It now asks you to choose a model/PPD, etc. Since you're modifying the properly installed printer driver, you should simply leave these values as they are and confirm by clicking "Modify Printer". (However, if you're re-adding the printer after having deleted it and need to re-configure the printer from the ground up, you might appreciate knowing that the necessary PPD is located at "/usr/share/cups/model/HL2270DW.ppd")
* Now click "Print Test Page" under the Maintenance menu and verify that it prints properly.

**Enabling network sharing (if you wanted it):**
* Simply having checked the "Share This Printer" checkbox is not enough; doing so just enables that printer for sharing, but it doesn't turn on actual printer sharing itself in CUPS. So, you'll want to go to the "Administration" tab of the web interface and ensure that "Share printers connected to this system" is enabled.
* Click "Change Settings" to confirm. What this does is that it tells CUPS to start broadcasting a list of printers over the network using Bonjour/mDNS, allowing other Mac/Unix/Linux machines to detect them.
* Note that this does NOT broadcast over Samba/NetBIOS (Windows technology for sharing printers); you'll want to look up "CUPS over Samba" on Google for setting that up, if you want Windows clients to be able to print to it.

**Bonus: AirPrint!? The holy grail?!**
* The Bonjour/mDNS network sharing technology in CUPS actually broadcasts the capability information for your CUPS server running on the Linux machine, and NOT for the printer itself. Any jobs sent over the network therefore go to your Linux CUPS server, which translates them to a format the printer understands and forwards the job. This means that your Linux machine MUST always be running when you want to print to the CUPS server.
* The upside of course is that the CUPS server supports a heck of a lot more features than a direct connection to a printer would; to be precise, the CUPS server has no problem accepting PDF or PNG/JPG input, rather than just plain PostScript (which is the only format that most printers understand natively).
* You see, the requirements for AirPrint capability is that the receiving printer/machine can accept PDF and PNG/JPG, and that the printer/machine broadcasts a normal "_ipp._tcp" service over mDNS, BUT with a few special fields. To be precise, it also needs a subtype of "_universal._sub._ipp._tcp", and its list of pdl's must include application/pdf and image/jpg and image/png (if it does not include support for PDF or image formats, then AirPrint on your iOS device will still see the printer but will not be able to print to it), and finally it must have a text-record called "URF=none" (not used by AirPrint but must be there or the printer won't show up).
* Luckily, CUPS supports ALL of the required formats, AND has supported those extra mDNS fields since CUPS 1.4.6, SO if you are on that version or higher (update CUPS if you're on an older version), your printer sharing will actually AUTOMATICALLY be AirPrint-compatible. Go ahead, pick up your iOS device, go to Safari, go to Print Page and it will find your CUPS daemon running on the Linux machine.
* You can now print from iOS devices as long as both your printer and Linux machine are running! Give it a test print!
* Note for curious experts that want to know more: *If your printer had native support for rasterizing PDF, PNG and JPG (which the Brother printers do not), then it would actually have been possible to simply do service-announcement via AVAHI (or mDNSResponder), filling in the capabilities and the proper fields, and AirPrint devices would find the printer and be able to send PDF/JPG/PNG data directly to it without the need for a CUPS server in-between. However, I don't know of ANY printers that supports those formats that isn't *ALSO* natively AirPrint-enabled, since there is NO reason for a printer to natively understand those formats unless it needs to support AirPrint.*

**Bonus: Removing printers you don't want to share.**
* You can do that via the web interface and the "Modify Printer" option, going through the configuration steps (without changing anything) and unchecking "Share This Printer" for each printer you don't want to share.
* However, that method doesn't work for the "Print to PDF" virtual printer, as it cannot be configured via the web interface (the final model/ppd step cannot be completed).
* So, for that one, you should either directly edit /etc/cups/printers.conf and set "Shared No" for that printer and re-start the CUPS daemon, OR you can use the Printer control panel GUI to view printer properties and disable sharing without manually touching any config files. In fact, you could have done all of the web interface steps above using the control panel instead, but I wrote the web steps because they're more universal.

**Bonus: What exactly is contained in the Brother drivers?**
* The mystery packages actually perform three things:
* 1) They install a PPD to /usr/share/cups/model/HL2270DW.ppd, which is a file that describes the capabilities of the printer, such as onboard fonts, paper dimensions, features, you name it.
* 2) They install a CUPS filter program; this filter is used by the PPD (via the cupsFilter line), and what it does is that it takes any print jobs you send to CUPS, and converts them to the vendor-specific language that the Brother printer speaks, before transmitting them over the wire to the actual printer. Without this program filtering the output, your printer would receive troublesome data and will hate you (for instance, it might print the job and then print blank pages until it runs out of paper). In other words: You NEED the filter. The reason I elaborated on what the filter does is that some people have pondered *why* you even need anything more than a PPD file. Now you know why! Your printer will not work properly AT ALL without the filter program!
* 3) Finally, they install a default USB configuration for your printer and then re-starts the CUPS server.
* You need all three things in order for your printer to work.


**I place this material in the public domain and anyone is free to re-mix the instructions for other distros / post the instructions as-is or modified on their own blogs / or anything else you might want to do with them. No attribution is needed!**

Enjoy!

---

