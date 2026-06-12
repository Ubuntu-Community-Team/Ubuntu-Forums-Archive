---
title: "CUPS Server Won't Print PDF"
date: 2008-08-19
forum: Server Platforms
---

### Post by Luft on 2008-08-19
I'm running Ubuntu 8.04 with the Kubuntu desktop and using it as a cups server.

I can print Open Office documents but not PDF documents.

---

### Post by Cheesehead on 2008-08-19
How, exactly, are you telling the computer to print the PDF files?
What programs are you using, and what commands are you clicking on?
If the using the command line, what commands are you using?

---

### Post by Luft on 2008-08-19
> **Cheesehead said:**
> How, exactly, are you telling the computer to print the PDF files?
What programs are you using, and what commands are you clicking on?
If the using the command line, what commands are you using?

I just bring up the document using kpdf and click on the File Print menu option.  (This is on the server itself.)

If I use the web administration utility: **[http://localhost:631](http://localhost:631)** and look I see the print job listed as completed:
**completed at Tue 19 Aug 2008 03:18:15 PM PDT** but nothing prints out.  I am able to print Open Office documents and a test page.  I'm beginning to think that it's a problem with KPDF but I don't have a clue as to how to track the problem down or correct it.

---

### Post by Cheesehead on 2008-08-20
If you (1) click 'print' in an app, and (2) cups picks up the job (because it claimed to print it), then it's not the app's fault. The app did what it was supposed to do - send it to cups. 

To test the app-to-cups link, print the file to a PDF or another printer. If the PDF gets created properly, then your app is just fine.



Three possibilities:

1) Printer communication problem - unlikely since you can print from OpenOffice.

2) Printer is actually receiving the file, and then quietly choking on a Postscript or memory error - possible with older printers, like my Apple LaserWriter 4/600. Since it's the printer's problem, it would happen when (almost) anyone on your network sends the PDF file, from any app, or any OS. So you can reproduce it fairly easily. Try sending the print job from the command line,

3) The cups filter that converts PDF print jobs into Postscript for printing is not installed, misconfigured, or broken - possible.

What kind of printer is it?

---

### Post by edmicman on 2008-09-12
I'm having this exact same problem with my setup.  Did you ever find any resolution?  I'm printing to a Brother HL2040 via IPP through a Linksys WPS54G print server.  Printing works fine in Firefox and OpenOffice, but printing a PDF through the default "document viewer" breaks.  The job shows it completed on the CUPS server, but it hoses up the printer and nothing ever comes out.

Can you tell me more info about this "cups filter that converts PDF to Postscript" thing?  How can I tell if that is not installed or broken somehow?

Thanks!

---

### Post by windependence on 2008-09-13
He is talking about the driver. Here is some information I dug up on which driver it should be using: 

> Printer:        Brother HL-2040 
Driver file:    hl1250.ppd 
 

Works 100% with Foomatic ppd. Setup is automatic with Edgy-Gutsy. Detected as "Brother HL-2040 series" and default driver is "Brother HL-2060 Foomatic/hl1250" 

In CUPS, most drivers will work just fine for most standard print functions no matter what the printer actuall is. Where they differ is on the small features like this. I think you have the wrong driver file selected in CUPS.

Can you post your /var/log/cups/error_log file?

Let's also look at your /etc/cups/cupsd.conf 

-Tim

---

### Post by edmicman on 2008-09-13
Thanks for the info!  I've attached a zip file of my cupsd.conf as well as cups-pdf.conf, if that helps.  The /var/log/cups/error_log file is actually empty - zero bytes.  The funny thing is, this morning I opened a PDF using the document viewer, and it actually printed just fine!  Weird....it was doing this exact problem from this thread last time I tried.

I'll look into the driver thing.  I thought I got the one I'm using from the Brother website for the HL2040.  I have it set up in the CUPS/Printing preferences as "ipp://192.168.1.98:631/ipp/P1".  I got that somewhere on these forums I think for setting up the printer.  I'm wondering if I run into problems because I'm not only using the (possibly?) wrong driver, but also because it's going through the print server?

Thanks for all the help - I'll see if I can mess with the driver, but first maybe I'll test printing some PDFs a couple more times and see if it is still broken.  Thanks again!

---

