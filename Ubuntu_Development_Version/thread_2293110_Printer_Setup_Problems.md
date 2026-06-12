---
title: "Printer Setup Problems"
date: 2015-09-02
forum: Ubuntu Development Version
---

### Post by sgage on 2015-09-02
As has been the case for, I think, years now, I can not set up a printer from the 'Printers' feature in the Control Center. It seems to get hung up on downloading drivers or something. 'system-config-printer' works perfectly and quickly, as it always has. Printer is an Epson Stylus C86.

Anyone else see this? Like I said, it hasn't worked for me for a long, long time.

---

### Post by QDR06VV9 on 2015-09-02
All Hp's here with no issues at all over wifi && lan.
Mine takes about 30 to 40 Seconds to DL the drivers needed.
It installed before I finished typing my reply.

---

### Post by sgage on 2015-09-02
> **runrickus said:**
> All Hp's here with no issues at all over wifi && lan.
Mine takes about 30 to 40 Seconds to DL the drivers needed.
It installed before I finished typing my reply.

Lucky you! When I try it, it correctly identifies the printer, says 'searching for drivers', and it just gets stuck there. It has done this for a very long time. I posted a bug on this a while ago, but nothing ever came of it. Oh well.

---

### Post by ventrical on 2015-09-03
> **runrickus said:**
> All Hp's here with no issues at all over wifi && lan.
Mine takes about 30 to 40 Seconds to DL the drivers needed.
It installed before I finished typing my reply.

I have had nothing but success with a variety of printers. Ubuntu takes 'dead' printers and brings them back to life. LaserJet HPs work exceptionally well. Time and money saved.! 

The format has changed through the last few cycles. Now you have to specify in the dialog box <usb Printer> or <Parallel printer> othwise it will just spin.
Regards..

---

### Post by sgage on 2015-09-03
> **ventrical said:**
> I have had nothing but success with a variety of printers. Ubuntu takes 'dead' printers and brings them back to life. LaserJet HPs work exceptionally well. Time and money saved.! 

The format has changed through the last few cycles. Now you have to specify in the dialog box <usb Printer> or <Parallel printer> othwise it will just spin.
Regards..

I see no such dialog box, but I suspect it's different for different printers. The install goes as follows for me, using the control center printer routine:

I fire it up, it detects 'Epson Stylus 86 USB'. The only option at this point is to select it and click 'add'. The installer sort of grays out, and a message box comes up saying 'searching for driver'. After a few seconds, a notification is put up by something called Scp-dbus-service-py saying 'Download Driver is ready', as if it wants my go-ahead, but no dialog box is presented to allow me to do so. Another minute and a dialog box comes up saying "Download Printer Driver” is not responding, do I want to force-quit or wait. If I quit, and then quit the main Printer dialog, a box pops up saying 'searching for drivers' again. When I quit that, sometimes (maybe one in 4), the standard Gnome box comes up that asks for your password. In the end, no printer is installed. This is how it has worked for me through several releases.

In other words, it's all messed up, and the various components of the process don't seem to be communicating properly, or to be state aware. 

Incidentally, using the Control Center Print installer in Fedora works fine - same printer and everything.

As I mentioned in my OP, manually running system-config-printer works perfectly and very quickly. The printer then functions just fine, all the options are available, etc., etc.  I don't have another printer here to test the routine with - maybe it's just the 'recipe' for the Epson that's messed up.

---

### Post by cariboo on 2015-09-03
I've got two printers here, a Brother HL-5250DN and an Epson R-340, both are networked, the laser printer via a network cable and the Epson connected to my file/whatever server, both were installed on wily in a matter of minutes, way easier than in Windows.

---

### Post by sgage on 2015-09-03
> **cariboo said:**
> I've got two printers here, a Brother HL-5250DN and an Epson R-340, both are networked, the laser printer via a network cable and the Epson connected to my file/whatever server, both were installed on wily in a matter of minutes, way easier than in Windows.

That's nice. :KS  Must just be my printer. As I have said, it installs perfectly and quickly with system-config-printer. The script for the control center item is broken for me.

---

### Post by flocculant on 2015-09-04
I had similar a version or two back with an HP printer. Turned out to be something someone had done. 

Had a quick look in the changelog for system-config-printer but nothing jumped out at me.

I'd report it.

---

### Post by sgage on 2015-09-04
> **flocculant said:**
> I had similar a version or two back with an HP printer. Turned out to be something someone had done. 

Had a quick look in the changelog for system-config-printer but nothing jumped out at me.

I'd report it.

I reported it some time ago, I'm pretty sure. Maybe I'll look for it and give it a bump, or just post a new version...

---

### Post by ventrical on 2015-09-04
> **cariboo said:**
> I've got two printers here, a Brother HL-5250DN and an Epson R-340, both are networked, the laser printer via a network cable and the Epson connected to my file/whatever server, both were installed on wily in a matter of minutes, way easier than in Windows.

Epson Artisan 730  ink-jet .. a throw-away surplus came with pile of hardware and pcs.  I hooked in wily (USB) and it prints awesomely beautiful colors. All from a printer that was ready for the brick pile.

**an important point I think**  There is a lot of mis-information going around about printers that just seem to die or have sit for a while and then it is assumed that the ink-jets dry up and will not work! Not so with Ubuntu. Ubuntu has proven to me time and time again that  this  dis-information is not true. All of the printers I work with  come from obsoleted Windows machines that have been bricked by obsolescence or are fubared by malware. Ubuntu more or less behaves like an anti-malware in many of these instances.

Regards..

---

### Post by ventrical on 2015-09-04
> **sgage said:**
> I see no such dialog box, but I suspect it's different for different printers. The install goes as follows for me, using the control center printer routine:

I fire it up, it detects 'Epson Stylus 86 USB'. The only option at this point is to select it and click 'add'. 

Uh... what version are you using because it is the otherway around. Open printer control center, then , click  add. After that a sort of dialog box comes up with options. Then you select the suggested printer. A dialog box opens. At the bottom of that box will either be USB or parallel printer. You have to ignore the other verbose options.

Regards..

---

### Post by sgage on 2015-09-04
> **ventrical said:**
> Epson Artisan 730  ink-jet .. a throw-away surplus came with pile of hardware and pcs.  I hooked in wily (USB) and it prints awesomely beautiful colors. All from a printer that was ready for the brick pile.

**an important point I think**  There is a lot of mis-information going around about printers that just seem to die or have sit for a while and then it is assumed that the ink-jets dry up and will not work! Not so with Ubuntu. Ubuntu has proven to me time and time again that  this  dis-information is not true. All of the printers I work with  come from obsoleted Windows machines that have been bricked by obsolescence or are fubared by malware. Ubuntu more or less behaves like an anti-malware in many of these instances.

Regards..

My printer works perfectly with Ubuntu - that isn't the issue. I just can't install it with the Contol Center Printer module. Manually running system-config-printer, it installs quickly and without incident, and subsequently runs just fine - better than under Windows, in fact.

---

