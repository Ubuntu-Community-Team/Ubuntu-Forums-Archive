---
title: "LPR not accepting print jobs from cups server"
date: 2016-09-22
forum: Server Platforms
---

### Post by Aphexlog on 2016-09-22
i receive the following error via LPR when trying to run a print job through cups configuration:
```
Caused by: java.io.IOException: error=1 running: '/usr/bin/lpr' '-PWorkCenter5330' '-JJava_Printing_0' '/tmp/tomcat7-tomcat7-tmp/javaprint5068324046451705625.ps'
                lpr: WorkCenter5330: unknown printer
        at sun.print.PSPrinterJob$PrinterSpooler.handleProcessFailure(PSPrinterJob.java:711)
        at sun.print.PSPrinterJob$PrinterSpooler.run(PSPrinterJob.java:734)
        ... 92 common frames omitted

```

my printer name is WorkCenter5330 and my output when running lpoptions is as follows:
```
vmadmin@x4qa-engage01:/etc/cups$ lpoptions
copies=1 device-uri=socket://10.30.30.112 finishings=3 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=1474568699 marker-colors=#000000,none,none,none,none,#000000,none,none,none,none,none,none marker-levels=85,-1,-1,-1,-1,86,-1,-1,-1,-1,-1,-1 marker-names='Black\ Toner\ [K]\ Cartridge;SN4833FE80E0000412,,,,,Black\ Drum\ Cartridge,,,,,,Fuser\ Assembly' marker-types=toner,unknown,unknown,unknown,unknown,opc,unknown,unknown,unknown,unknown,unknown,fuser number-up=1 ppd-timestamp='Thu Sep 22 13:24:34 2016' printer-commands=AutoConfigure,Clean,PrintSelfTestPage printer-info=WorkCenter5330 printer-is-accepting-jobs=true printer-is-colormanaged=true printer-make-and-model='Xerox WorkCentre 5330' printer-state=3 printer-state-change-time=1474568699 printer-state-reasons=none printer-type=10531068 printer-uri-supported=ipp://localhost:631/printers/WorkCenter5330

```
I would also appreciate it if someone could tell me where the LPR config resides.

---

