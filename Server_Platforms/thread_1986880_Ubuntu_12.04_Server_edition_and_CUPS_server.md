---
title: "Ubuntu 12.04 Server edition and CUPS server"
date: 2012-05-25
forum: Server Platforms
---

### Post by ranger12 on 2012-05-25
This is not a question or an issue but just comments on the 12.04 server edition and cups. I bought an Epson Workforce 545 All-in-One printer and I already had the CUPS server software up and running on the server box. All I had to do was just plug it into the server box via usb and then I booted up my workstation which is running 12.04 Desktop. First of all I opened up nautilus and under Network I saw the printer listed there. I then fired up the Printer utility and then clicked Add and expanded the Network Printer list in the left pane and bam - there is was listed. I clicked it and then clicked Install or Add - don't remember the exact caption on the button but anyhow. It found and installed the driver and I clicked the Print Test Page button and wham - out came a test page. Probably the most work I did was in the printer settings to configure it for my wireless router so I can print from my iPad. That is just way too slick!! I have also tested out Simple Scan with it and that also works great. I have not tried the copier or fax yet but that is coming. I could have plugged the puppy into the router but I wanted to test out the cups server running on my server box. I thin I will leave it that way too. :) I hope y'all had as easy of a go at as I did. The home network is shaping up nicely now.

---

### Post by LHammonds on 2012-05-25
Wait a sec...you got an iPad that printed through Ubuntu to a non-apple printer?  Wow...I never thought about that.  Ever since I first saw the info about being able to print from an iPad/iPhone, I completely dismissed the option since it required very specific printing hardware which we were never going to purchase.

I guess I need to re-evaluate.  Oh, almost forgot to mention. I have a virtual server running Zentyal 2.2.7 (Ubuntu 10.04) with a handful of printers defined on it for testing purposes.

Thanks,
LHammonds

---

### Post by ranger12 on 2012-05-25
Sorry for the ambiguity. I meant to say that I configured the wireless printer settings on the printer itself so I could print to the printer directly from the iPad. It is not going through Ubuntu. My desktop workstation is going through the server box for printing since the printer is hooked up to the server not the workstation. It was all painless.

According to the Apple printer page there are quite a few printers now that support printing from iOS devices using the AirPrint system. It works pretty well. I wanted a printer that would be supported by my iPad and Ubuntu and not just Windows. This one fits the bill quite nicely.

---

### Post by ranger12 on 2012-05-28
Boy do I feel stupid. I guess I did have to do a little more configuration on the cupsd.conf on the file server. Turns out I had set up the printer to do dns-sd through the router and using a driver on the workstation and not the cups server on the server box but I straightened  that out and now have it actually going through cups on the server box. It still wasn't that big of a deal though. This printer has several ways of putting it on a network.

---

