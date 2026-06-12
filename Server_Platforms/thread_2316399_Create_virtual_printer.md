---
title: "Create virtual printer?"
date: 2016-03-07
forum: Server Platforms
---

### Post by garlicsalt2 on 2016-03-07
Ok, so I'm intimately familiar with command-line Ubuntu. A friend of mine has a Vinyl cutter. I haven't found an actual printer driver for it. It acts as a plotter as far as a computer is concerned. Interfaces via a USB cable, which is internally connected to USB to Serial circuitry.

The problem is, In order to use it, I'm told that I need to pay $70 per month to use the proprietary software that goes with it. I have come to understand that if I have a printer driver, it can be used directly from any graphics program, as long as I am careful as to what commands are sent to the Vinyl Cutter.

If I can get the cutter to work/interface with a Linux Box, what would be involved in creating a virtual printer that:

1. Accepts print jobs via Samba from a Windows computer via the Network.
2. Runs the print job through a ps2edit script.
3. And finally sends the modified job to the Plotter/Cutter.

Notes:
I don't think I need help setting up Samba, I've done this before. I just need help getting something that Samba will recognize.
If Samba isn't an option or won't work as expected, I could probably do IPP if needed.
I don't necessarily need somebody to hold my hand - I can probably figure out how to fill in the gaps. I could use some help getting started. I am naturally technically inclined, just a bit out of my league for the moment.

---

### Post by SeijiSensei on 2016-03-08
Off the top of my head....

It looks like you can [set up CUPS to print to a file]("https://wiki.linuxfoundation.org/en/OpenPrinting/Database/CupsFAQ#How_do_I_print_to_a_file.3F").  You could pipe the result to ps2edit then write it directly to the cutter over the USB connection.   If you run "lsusb" do you see the cutter?  If so, try disconnecting it, then running
```
sudo tail -f /var/log/syslog
```
Now reconnect the cutter and see what the log reports.  Does it get assigned to a device like /dev/usb/something?  If so, then try piping the results of ps2edit directly to that device and see what happens.

If all that works, you can use IPP from the Windows client.

If you can't pipe directly from CUPS to ps2edit, then you could write the result to a file in a queue directory.  Then write a script to run every minute from cron, check the queue for files, run any it finds through ps2edit, write the results to the cutter, then archive the file.  Not as elegant, but it probably wouldn't matter from a production standpoint, and it has the virtue of letting you archive all the files.

---

### Post by garlicsalt2 on 2016-03-18
Ok. I've been busy at work. I have looked into the info above, and believe it is definitely possible to do what I had hoped. I hope to figure it out eventually. Meanwhile, the Boss is using a cracked version of the software that is normally used to drive the vinyl cutter. I understand that paying $70 per month to use a piece of hardware for which he's already paid is outrageous, but I still don't condone piracy. Sigh. I am trying to work on the completely legal Linux version, but the boss and his graphics designer are always using the other machine. I can't plug in a USB cable into tow different computers at once.

To sum up, progress is moving forward, but slowly. I have a virtual cups printer setup and shared over via Samba server, and saves to a postscript file. I have printed a test page via CUPS web interface, then manually run it through pstoedit and then through the distiller program I found. I have not tried sending any output to the cutter. I kind of want to put some plain paper in the machine first. Vinyl is an expensive commodity with which to be experimenting. It's now 11 PM local time. Good night everybody.

---

