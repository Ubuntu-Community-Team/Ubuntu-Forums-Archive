---
title: "Trouble with QQ and remote printers"
date: 2012-08-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-20
I'm seeing a new bug with network printers. I have an HP P1005 Laser USB printer connected to a PP server that is running cups service and has no firewall restrictions to IPs in the LAN. All QQ machines stopped being able to send documents to this printer. Printing locally works normally.

Example: When I open any PDF document on Document Viewer in the client machines and go to File/Print, the print dialog is stalled in "Getting printer information" status. It doesn't change and I can't print.

[ATTACH]222948[/ATTACH]

But when I go to Dash -> Print Settings, double click on the same printer and click on "Print Test Page" button, the remote printer starts immediately and prints normally.

[ATTACH]222949[/ATTACH] [ATTACH]222950[/ATTACH]
Notice that the printer status is Print Settings is displayed as normal ("idle").

Sending documents to this remote printer using up-to-date PP machines works normally.

Anyone else seeing this?

Regards,
Effenberg

---

### Post by VinDSL on 2012-08-20
> **effenberg0x0 said:**
> I'm seeing a new bug with network printers.[...]

Anyone else seeing this?
Not exactly the same setup, but...

My network printer is still working.



[INDENT][IMG]http://vindsl.com/images/vindsl-desktop-20-aug-2012-1.png[/IMG][/INDENT]


As you can see, I have my remote printer setup as a LPD/LPR device.

I've got everything in this house (that prints) connected to a single printer, over my LAN, via a print server.

You've probably already tried this, but...  With CUPS, I've noticed that sometimes the config gets janky, and the only thing that fixes it is deleting the printer profile and starting from scratch.  This would be the functional equivalent of re-installing a program with Synaptic, or making a new profile in Firefox.

Have you tried deleting the printer profile from your setup, and making a new profile?

---

### Post by 67GTA on 2012-08-20
I have had trouble with this also, but was able to manually set up ipp printing. When I check the server settings, the "Show printers shared by other systems" option is greyed out, so that might be keeping it from broadcasting the printer. I have no idea why that is happening. There are no errors in the cups logs.

---

### Post by effenberg0x0 on 2012-08-20
> **67GTA said:**
> I have had trouble with this also, but was able to manually set up ipp printing. When I check the server settings, the "Show printers shared by other systems" option is greyed out, so that might be keeping it from broadcasting the printer. I have no idea why that is happening. There are no errors in the cups logs.

Yeah, you're right about the grayed option, it isn't like that in PP.

Here's how I have it in QQ:
[ATTACH]222959[/ATTACH]
I'll look into IPP as an option. 

VinDSL: I'll look into LPR, thanks for the tip.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-20
You were both correct: LPD/LPR and IPP work out of the box, while "Remote CUPS via DNS-SD" does not...

I think it qualifies for a bug report.

Regards,
Effenberg

---

### Post by VinDSL on 2012-08-20
> **effenberg0x0 said:**
> You were both correct: LPD/LPR and IPP work out of the box...
It's a testimony to the versatility of CUPS!  :D

Just did a search on DuckDuckGo, for my vintage HP DeskJet 895Cxi printer.

[INDENT][PC Mag Editor's Choice, November 3, 1998]("http://people.virginia.edu/~cavcomp2/printers/hp/895cxi/HP%20DeskJet%20895Cxi%20Data%20Sheet.htm")[/INDENT]

And, my NetGear PS110NA print server, hearkening back to the turn of the century.

CUPS still supports them!  Amazing!

---

### Post by 67GTA on 2012-08-20
I agree. I hoped one of the many cups updates we have been getting would magically fix it. LOL If I use the cups web interface, the shared printer option is "checked".  It must be something local in one of the cups packages. I will do some more digging tomorrow.

---

### Post by 67GTA on 2012-08-21
Still not sure what the problem is. All cups config files look fine. Reinstalled all cups packages. Deleted the printer and started over. My desktop is broadcasting the printer without the share option checked. My laptop automatically finds it if I give the printer setup dialog a couple of minutes. Maybe a bug or some crazy Gnome 3 setting.

---

