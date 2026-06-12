---
title: "pstoraster failed with HP Officejet 6500"
date: 2010-01-27
forum: Server Platforms
---

### Post by ichneumon on 2010-01-27
I'm having problems with network printing from all clients via cups to a networked HP OfficeJet 6500. The server is running Hardy with kernel 2.6.24-26-server, and is fully up to date. I've installed hplip-3.9.12 as the 6500 isn't supported in v2.8.2, and the printer is connected across the local ethernet network. Local printing from the server works fine, but when I try to print from client PCs, each print job works, in that it prints the document successfully, but terminates after printing with a "/usr/lib/cups/filter/pstoraster failed" error. This means that the print job remains in the queue with a State of "stopped". This happens when printing from XP, Vista and Ubuntu 9.10, and also whether printing through either ipp or samba.

The relevant section of the cups error log with debug enabled appears to be:

```

D [27/Jan/2010:17:42:30 +0100] [Job 586] %%[Page: 1]%%
D [27/Jan/2010:17:42:30 +0100] [Job 586] Putting.
D [27/Jan/2010:17:42:30 +0100] [595.0 842.0]
D [27/Jan/2010:17:42:30 +0100] [Job 586] /.MediaSize
D [27/Jan/2010:17:42:30 +0100] [Job 586] false
D [27/Jan/2010:17:42:30 +0100] [Job 586] /.IgnoreNumCopies
D [27/Jan/2010:17:42:30 +0100] [Job 586] false
D [27/Jan/2010:17:42:30 +0100] [Job 586] /ManualFeed
D [27/Jan/2010:17:42:30 +0100] [Job 586] 0.0
E [27/Jan/2010:17:42:30 +0100] PID 4562 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
D [27/Jan/2010:17:42:30 +0100] [Job 586] /K^G
D [27/Jan/2010:17:42:30 +0100] [Job 586] lingFactor
D [27/Jan/2010:17:42:30 +0100] [Job 586] 0
D [27/Jan/2010:17:42:30 +0100] [Job 586] /K^G
D [27/Jan/2010:17:42:30 +0100] [Job 586] Setting cupsRowCount to 0...
D [27/Jan/2010:17:42:30 +0100] [Job 586] Setting cupsRowFeed to 0...
D [27/Jan/2010:17:42:30 +0100] [Job 586] Setting cupsRowStep to 0...
D [27/Jan/2010:17:42:30 +0100] [Job 586] Setting cupsInteger0 to 26...
D [27/Jan/2010:17:42:30 +0100] [Job 586] cupsEncodeLUT[0] = 0
D [27/Jan/2010:17:42:30 +0100] [Job 586] cupsEncodeLUT[65535] = 255
D [27/Jan/2010:17:42:30 +0100] [Job 586] num_components = 4, depth = 32
D [27/Jan/2010:17:42:30 +0100] [Job 586] cupsColorSpace = 17, cupsColorOrder = 0
D [27/Jan/2010:17:42:30 +0100] [Job 586] cupsBitsPerPixel = 32, cupsBitsPerColor = 8
D [27/Jan/2010:17:42:30 +0100] [Job 586] max_gray = 255, dither_grays = 256
D [27/Jan/2010:17:42:30 +0100] [Job 586] max_color = 255, dither_colors = 256
D [27/Jan/2010:17:42:30 +0100] [Job 586] Result of putting.
D [27/Jan/2010:17:42:30 +0100] [Job 586] /undefined
D [27/Jan/2010:17:42:30 +0100] [Job 586] /      =
D [27/Jan/2010:17:42:30 +0100] [Job 586] ined
D [27/Jan/2010:17:42:30 +0100] PID 4564 (/usr/lib/cups/filter/hpcups) exited with no errors.

```As /usr/lib/cups/filter/pstoraster appears to be a wrapper for passing the print job through gs, I also tried upgrading ghostscript to v8.70; this gives exactly the same results.

Although the current workaround of adding "MaxJobs 0" to /etc/cups/cupsd.conf prevents the queue filling up, I would prefer this printer to work correctly, as it was bought with the express purpose of avoiding the nightmare I ran into with the previous Lexmark. Has anyone else run into this problem, or found a solution to this error? If any more information is required, I'll provide it.

---

### Post by mraisky on 2010-09-12
Same problem, same hardware, same software...

---

