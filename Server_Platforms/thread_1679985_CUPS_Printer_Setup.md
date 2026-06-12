---
title: "CUPS Printer Setup"
date: 2011-02-01
forum: Server Platforms
---

### Post by mvastola on 2011-02-01
Hi guys,
So I have a printer set up on one server and I'm trying to print to it from another, and I'm having trouble getting things to print on the latter.

I believe I successfully added the printer, but when I go to print a test file, I get the following in the CUPS Error Log.

```
E [01/Feb/2011:19:37:59 -0500] [Job 9] Empty print file!
E [01/Feb/2011:19:37:59 -0500] PID 24374 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 11!
D [01/Feb/2011:19:37:59 -0500] [Job 9] The following messages were recorded from 19:37:58 to 19:37:59
D [01/Feb/2011:19:37:59 -0500] [Job 9] Queued on "Bedlam" by "root".
D [01/Feb/2011:19:37:59 -0500] [Job 9] Auto-typing file...
D [01/Feb/2011:19:37:59 -0500] [Job 9] Request file type is application/postscript.
D [01/Feb/2011:19:37:59 -0500] [Job 9] File of type application/postscript queued by "root".
D [01/Feb/2011:19:37:59 -0500] [Job 9] No job-sheets attribute.
D [01/Feb/2011:19:37:59 -0500] [Job 9] ... but someone added one without setting job_sheets!
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[0]="Bedlam"
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[1]="9"
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[2]="root"
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[3]="ticket.ps"
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[4]="1"
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[5]="job-originating-user-name=root finishings=3 job-priority=50 job-sheets=none,none number-up=1 job-uuid=urn:uuid:f5e41937-547a-31a0-6b70-ceb76fd19da5 job-originating-host-name=localhost job-id=9 job-state=5 job-media-sheets-completed=0 job-k-octets=28"
D [01/Feb/2011:19:37:59 -0500] [Job 9] argv[6]="/var/spool/cups/d00009-001"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[8]="HOME=/var/spool/cups/tmp"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[10]="SERVER_ADMIN=root@tumult.domain.com"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[11]="SOFTWARE=CUPS/1.4.4"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[13]="USER=root"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[16]="IPP_PORT=631"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[17]="CHARSET=utf-8"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[18]="LANG=en_US.UTF-8"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[19]="PPD=/etc/cups/ppd/Bedlam.ppd"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[20]="RIP_MAX_CACHE=auto"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[21]="CONTENT_TYPE=application/postscript"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[22]="DEVICE_URI=ipp://bedlam.domain.com/printers/BrotherMFC"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[23]="PRINTER_INFO=Bedlam"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[24]="PRINTER_LOCATION="
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[25]="PRINTER=Bedlam"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[26]="CUPS_FILETYPE=document"
D [01/Feb/2011:19:37:59 -0500] [Job 9] envp[27]="FINAL_CONTENT_TYPE=printer/Bedlam"
D [01/Feb/2011:19:37:59 -0500] [Job 9] Started filter /usr/lib/cups/filter/pstopdf (PID 24372)
D [01/Feb/2011:19:37:59 -0500] [Job 9] Started filter /usr/lib/cups/filter/pdftopdf (PID 24373)
D [01/Feb/2011:19:37:59 -0500] [Job 9] Started filter /usr/lib/cups/filter/foomatic-rip (PID 24374)
D [01/Feb/2011:19:37:59 -0500] [Job 9] Started backend /usr/lib/cups/backend/ipp (PID 24375)
D [01/Feb/2011:19:37:59 -0500] [Job 9] pstopdf 6 args: 9 root ticket.ps 1 job-originating-user-name=root finishings=3 job-pri
ority=50 job-sheets=none,none number-up=1 job-uuid=urn:uuid:f5e41937-547a-31a0-6b70-ceb76fd19da5 job-originating-host-name=localhost job-id=9 job-state=5 job-media-sheets-completed=0 job-k-octets=28 /var/spool/cups/d00009-001
D [01/Feb/2011:19:37:59 -0500] [Job 9] PPD: /etc/cups/ppd/Bedlam.ppd
D [01/Feb/2011:19:37:59 -0500] [Job 9] Getting input from file
D [01/Feb/2011:19:37:59 -0500] [Job 9] foomatic-rip version 4.0.5.223 running...
D [01/Feb/2011:19:37:59 -0500] [Job 9] Parsing PPD file ...
D [01/Feb/2011:19:37:59 -0500] [Job 9] CUPS page accounting disabled by driver.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Added option PageSize
D [01/Feb/2011:19:37:59 -0500] [Job 9] STATE: +connecting-to-device
D [01/Feb/2011:19:37:59 -0500] [Job 9] Looking up "bedlam.domain.com"...
D [01/Feb/2011:19:37:59 -0500] [Job 9] Copying print data...
D [01/Feb/2011:19:37:59 -0500] [Job 9] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0xb8ab7c7c, use_bc=0, side_cb=0xb775b2a0)
D [01/Feb/2011:19:37:59 -0500] [Job 9] Added option ImageableArea
D [01/Feb/2011:19:37:59 -0500] [Job 9] Added option PaperDimension
D [01/Feb/2011:19:37:59 -0500] [Job 9] Added option Duplex
D [01/Feb/2011:19:37:59 -0500] [Job 9] Added option Resolution
D [01/Feb/2011:19:37:59 -0500] [Job 9] Added option Font
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] Parameter Summary
D [01/Feb/2011:19:37:59 -0500] [Job 9] -----------------
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] Spooler: cups
D [01/Feb/2011:19:37:59 -0500] [Job 9] Printer: Bedlam
D [01/Feb/2011:19:37:59 -0500] [Job 9] Shell: /bin/bash
D [01/Feb/2011:19:37:59 -0500] [Job 9] PPD file: /etc/cups/ppd/Bedlam.ppd
D [01/Feb/2011:19:37:59 -0500] [Job 9] ATTR file:
D [01/Feb/2011:19:37:59 -0500] [Job 9] Printer model: Brother MFC-7820N Foomatic/Postscript
D [01/Feb/2011:19:37:59 -0500] [Job 9] Job title: ticket.ps
D [01/Feb/2011:19:37:59 -0500] [Job 9] File(s) to be printed:
D [01/Feb/2011:19:37:59 -0500] [Job 9] <STDIN>
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [01/Feb/2011:19:37:59 -0500] [Job 9] Printing system options:
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-originating-user-name=root'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-originating-user-name=root.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'finishings=3'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option finishings=3.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-priority=50'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-priority=50.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-sheets=none'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-sheets=none.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'none'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'number-up=1'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option number-up=1.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-uuid=urn:uuid:f5e41937-547a-31a0-6b70-ceb76fd19da5'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-uuid=urn:uuid:f5e41937-547a-31a0-6b70-ceb76fd19da5.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-originating-host-name=localhost'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-originating-host-name=localhost.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-id=9'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-id=9.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-state=5'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-state=5.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-media-sheets-completed=0'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-media-sheets-completed=0.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Pondering option 'job-k-octets=28'
D [01/Feb/2011:19:37:59 -0500] [Job 9] Unknown option job-k-octets=28.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Options from the PPD file:
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] ================================================
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] File: <STDIN>
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] ================================================
D [01/Feb/2011:19:37:59 -0500] [Job 9]
D [01/Feb/2011:19:37:59 -0500] [Job 9] Resolution: 600x600
D [01/Feb/2011:19:37:59 -0500] [Job 9] Page size: Letter
D [01/Feb/2011:19:37:59 -0500] [Job 9] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [01/Feb/2011:19:37:59 -0500] [Job 9] Relative margins: 18, 36, 18, 36
D [01/Feb/2011:19:37:59 -0500] [Job 9] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [01/Feb/2011:19:37:59 -0500] [Job 9] PostScript to be injected:
D [01/Feb/2011:19:37:59 -0500] [Job 9] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [01/Feb/2011:19:37:59 -0500] [Job 9] Filetype: PDF
D [01/Feb/2011:19:37:59 -0500] [Job 9] Driver does not understand PDF input, converting to PostScript
D [01/Feb/2011:19:37:59 -0500] [Job 9] Storing temporary files in /var/spool/cups/tmp
D [01/Feb/2011:19:37:59 -0500] [Job 9] Starting process "pdf-to-ps" (generation 1)
D [01/Feb/2011:19:37:59 -0500] [Job 9] Filetype: PostScript
D [01/Feb/2011:19:37:59 -0500] [Job 9] Reading PostScript input ...
D [01/Feb/2011:19:37:59 -0500] [Job 9] --> This document is DSC-conforming!
D [01/Feb/2011:19:37:59 -0500] [Job 9] Job claims to be DSC-conforming, but "%%BeginProlog" was missing before first line with another"%%BeginProlog" comment (is this a TeX/LaTeX/dvips-generated PostScript file?). Assuming start of "Prolog" here.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Inserting option code into "Prolog" section.
D [01/Feb/2011:19:37:59 -0500] [Job 9] Set job-printer-state-message to "Empty print file!", current level=ERROR
D [01/Feb/2011:19:37:59 -0500] [Job 9] Backend returned status 1 (failed)
D [01/Feb/2011:19:37:59 -0500] [Job 9] End of messages
D [01/Feb/2011:19:37:59 -0500] [Job 9] printer-state=3(idle)
D [01/Feb/2011:19:37:59 -0500] [Job 9] printer-state-message="Empty print file!"
D [01/Feb/2011:19:37:59 -0500] [Job 9] printer-state-reasons=none

```

The first thing in the log and most obvious issue here is that /usr/lib/cups/filter/foomatic-rip is segfaulting. But I have no idea how to invoke that command to reproduce the segfault so I can report it. (The invocation is not in the log.)  Furthermore, I don't know if that's the root cause of the problem.

Any help would be greatly appreciated.

---

