---
title: "Issues printing to Dymo LabelWriter 4XL"
date: 2017-11-06
forum: Server Platforms
---

### Post by netris on 2017-11-06
Hey all, I've been at this for several days now and very frustrated. I tried installing the drivers from the DYMO SDK from their website, but it throws errors that I cannot make any sense of. So I installed 'printer-driver-dymo' and that seems to have all the ppd files for all the dymo printer. This works to install both my DYMO 4XL and DYMO 450Turbo via the cups web GUI. I can then issue a print test page from the web GUI, and it prints just fine. However whenever I try to print to the cups print server from a remote computer that has added those printers via their ipp URL I get either the Message 'stopped "Filter failed"'or the message 'Unable to open raster file - : No such file or directory' under the state for the print job.

Here is the output in the error log, but none of it seems to make any sense either. Googling doesn't seem to turn up anything useful or applicable. I'd appreciate any help anyone can give! (This is also a clean server install)

```
E [06/Nov/2017:20:36:58 -0600] [cups-deviced] PID 16308 (gutenprint52+usb) stopped with status 1!
E [06/Nov/2017:20:37:00 -0600] [Job 35] Unable to open raster file - : No such file or directory
E [06/Nov/2017:20:37:08 -0600] [Job 35] Job stopped due to filter errors; please consult the error_log file for details.
D [06/Nov/2017:20:37:08 -0600] [Job 35] The following messages were recorded from 08:37:00 PM to 08:37:08 PM
D [06/Nov/2017:20:37:08 -0600] [Job 35] Applying default options...
D [06/Nov/2017:20:37:08 -0600] [Job 35] Adding start banner page "none".
D [06/Nov/2017:20:37:08 -0600] [Job 35] Queued on "DYMO_4XL" by "USER1".
D [06/Nov/2017:20:37:08 -0600] [Job 35] File of type application/vnd.cups-raster queued by "USER1".
D [06/Nov/2017:20:37:08 -0600] [Job 35] Adding end banner page "none".
D [06/Nov/2017:20:37:08 -0600] [Job 35] time-at-processing=1510022220
D [06/Nov/2017:20:37:08 -0600] [Job 35] 1 filters for job:
D [06/Nov/2017:20:37:08 -0600] [Job 35] raster2dymolm (application/vnd.cups-raster to printer/DYMO_4XL, cost 0)
D [06/Nov/2017:20:37:08 -0600] [Job 35] job-sheets=none,none
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[0]="DYMO_4XL"
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[1]="35"
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[2]="USER1"
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[3]="Test Page"
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[4]="1"
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[5]="job-uuid=urn:uuid:41988b61-b9b5-371f-723e-f056e2d14bcc job-originating-host-name=192.168.1.5 date-time-at-creation= date-time-at-processing= time-at-creation=1510022220 time-at-processing=1510022220"
D [06/Nov/2017:20:37:08 -0600] [Job 35] argv[6]="/var/spool/cups/d00035-001"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[7]="CUPS_STATEDIR=/run/cups"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[10]="SERVER_ADMIN=root@Server1"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[11]="SOFTWARE=CUPS/2.2.4"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[13]="USER=root"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[14]="CUPS_MAX_MESSAGE=2047"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[15]="CUPS_SERVER=/run/cups/cups.sock"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[17]="IPP_PORT=631"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[18]="CHARSET=utf-8"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[19]="LANG=en_US.UTF-8"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[20]="PPD=/etc/cups/ppd/DYMO_4XL.ppd"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[21]="RIP_MAX_CACHE=128m"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[22]="CONTENT_TYPE=application/vnd.cups-raster"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[23]="DEVICE_URI=usb://DYMO/LabelWriter%204XL?serial=14070210130115"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[24]="PRINTER_INFO=DYMO LabelWriter 4XL"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[25]="PRINTER_LOCATION="
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[26]="PRINTER=DYMO_4XL"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[27]="PRINTER_STATE_REASONS=none"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[28]="CUPS_FILETYPE=document"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[29]="FINAL_CONTENT_TYPE=printer/DYMO_4XL"
D [06/Nov/2017:20:37:08 -0600] [Job 35] envp[30]="AUTH_I****"
D [06/Nov/2017:20:37:08 -0600] [Job 35] Started filter /usr/lib/cups/filter/gziptoany (PID 16332)
D [06/Nov/2017:20:37:08 -0600] [Job 35] Started filter /usr/lib/cups/filter/raster2dymolm (PID 16333)
D [06/Nov/2017:20:37:08 -0600] [Job 35] Started backend /usr/lib/cups/backend/usb (PID 16334)
D [06/Nov/2017:20:37:08 -0600] [Job 35] PID 16332 (/usr/lib/cups/filter/gziptoany) exited with no errors.
D [06/Nov/2017:20:37:08 -0600] [Job 35] PID 16333 (/usr/lib/cups/filter/raster2dymolm) stopped with status 1.
D [06/Nov/2017:20:37:08 -0600] [Job 35] Hint: Try setting the LogLevel to "debug" to find out more.
D [06/Nov/2017:20:37:08 -0600] [Job 35] starting (raster2dymolm)
D [06/Nov/2017:20:37:08 -0600] [Job 35] Loading USB quirks from \"/usr/share/cups/usb\".
D [06/Nov/2017:20:37:08 -0600] [Job 35] Loaded 152 quirks.
D [06/Nov/2017:20:37:08 -0600] [Job 35] Printing on printer with URI: usb://DYMO/LabelWriter%204XL?serial=14070210130115
D [06/Nov/2017:20:37:08 -0600] [Job 35] libusb_get_device_list=7
D [06/Nov/2017:20:37:08 -0600] [Job 35] STATE: +connecting-to-device
D [06/Nov/2017:20:37:08 -0600] [Job 35] STATE: -connecting-to-device
D [06/Nov/2017:20:37:08 -0600] [Job 35] Printer found with device ID: MFG:DYMO;CMD: ;MDL:LabelWriter 450 Turbo;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450 Turbo;SERN:10041918222229; Device URI: usb://DYMO/LabelWriter%20450%20Turbo?serial=10041918222229
D [06/Nov/2017:20:37:08 -0600] [Job 35] STATE: +connecting-to-device
D [06/Nov/2017:20:37:08 -0600] [Job 35] STATE: -connecting-to-device
D [06/Nov/2017:20:37:08 -0600] [Job 35] Printer found with device ID: MFG:DYMO;CMD: ;MDL:LabelWriter 4XL;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 4XL;SERN:14070210130115; Device URI: usb://DYMO/LabelWriter%204XL?serial=14070210130115
D [06/Nov/2017:20:37:08 -0600] [Job 35] Device protocol: 2
D [06/Nov/2017:20:37:08 -0600] [Job 35] Sending data to printer.
D [06/Nov/2017:20:37:08 -0600] [Job 35] Sent 0 bytes...
D [06/Nov/2017:20:37:08 -0600] [Job 35] Waiting for read thread to exit...
D [06/Nov/2017:20:37:08 -0600] [Job 35] Read thread still active, aborting the pending read...
D [06/Nov/2017:20:37:08 -0600] [Job 35] PID 16334 (/usr/lib/cups/backend/usb) exited with no errors.
D [06/Nov/2017:20:37:08 -0600] [Job 35] End of messages
D [06/Nov/2017:20:37:08 -0600] [Job 35] printer-state=3(idle)
D [06/Nov/2017:20:37:08 -0600] [Job 35] printer-state-message="Sending data to printer."
D [06/Nov/2017:20:37:08 -0600] [Job 35] printer-state-reasons=none
W [06/Nov/2017:20:37:20 -0600] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'DYMO_4XL-Gray..\' already exists
E [06/Nov/2017:20:37:41 -0600] [Job 36] Unable to open raster file - : No such file or directory
E [06/Nov/2017:20:37:49 -0600] [Job 36] Job stopped due to filter errors; please consult the error_log file for details.
D [06/Nov/2017:20:37:49 -0600] [Job 36] The following messages were recorded from 08:37:41 PM to 08:37:49 PM
D [06/Nov/2017:20:37:49 -0600] [Job 36] Applying default options...
D [06/Nov/2017:20:37:49 -0600] [Job 36] Adding start banner page "none".
D [06/Nov/2017:20:37:49 -0600] [Job 36] Queued on "DYMO_4XL" by "USER1".
D [06/Nov/2017:20:37:49 -0600] [Job 36] File of type application/vnd.cups-raster queued by "USER1".
D [06/Nov/2017:20:37:49 -0600] [Job 36] Adding end banner page "none".
D [06/Nov/2017:20:37:49 -0600] [Job 36] time-at-processing=1510022261
D [06/Nov/2017:20:37:49 -0600] [Job 36] 1 filters for job:
D [06/Nov/2017:20:37:49 -0600] [Job 36] raster2dymolw (application/vnd.cups-raster to printer/DYMO_4XL, cost 0)
D [06/Nov/2017:20:37:49 -0600] [Job 36] job-sheets=none,none
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[0]="DYMO_4XL"
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[1]="36"
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[2]="USER1"
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[3]="Test Page"
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[4]="1"
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[5]="job-uuid=urn:uuid:9100931d-c567-3ccf-4948-0615b84c1dfe job-originating-host-name=192.168.1.5 date-time-at-creation= date-time-at-processing= time-at-creation=1510022261 time-at-processing=1510022261"
D [06/Nov/2017:20:37:49 -0600] [Job 36] argv[6]="/var/spool/cups/d00036-001"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[7]="CUPS_STATEDIR=/run/cups"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[10]="SERVER_ADMIN=root@Server1"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[11]="SOFTWARE=CUPS/2.2.4"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[13]="USER=root"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[14]="CUPS_MAX_MESSAGE=2047"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[15]="CUPS_SERVER=/run/cups/cups.sock"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[17]="IPP_PORT=631"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[18]="CHARSET=utf-8"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[19]="LANG=en_US.UTF-8"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[20]="PPD=/etc/cups/ppd/DYMO_4XL.ppd"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[21]="RIP_MAX_CACHE=128m"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[22]="CONTENT_TYPE=application/vnd.cups-raster"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[23]="DEVICE_URI=usb://DYMO/LabelWriter%204XL?serial=14070210130115"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[24]="PRINTER_INFO=DYMO LabelWriter 4XL"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[25]="PRINTER_LOCATION="
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[26]="PRINTER=DYMO_4XL"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[27]="PRINTER_STATE_REASONS=none"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[28]="CUPS_FILETYPE=document"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[29]="FINAL_CONTENT_TYPE=printer/DYMO_4XL"
D [06/Nov/2017:20:37:49 -0600] [Job 36] envp[30]="AUTH_I****"
D [06/Nov/2017:20:37:49 -0600] [Job 36] Started filter /usr/lib/cups/filter/gziptoany (PID 16397)
D [06/Nov/2017:20:37:49 -0600] [Job 36] Started filter /usr/lib/cups/filter/raster2dymolw (PID 16398)
D [06/Nov/2017:20:37:49 -0600] [Job 36] Started backend /usr/lib/cups/backend/usb (PID 16399)
D [06/Nov/2017:20:37:49 -0600] [Job 36] PID 16397 (/usr/lib/cups/filter/gziptoany) exited with no errors.
D [06/Nov/2017:20:37:49 -0600] [Job 36] PID 16398 (/usr/lib/cups/filter/raster2dymolw) stopped with status 1.
D [06/Nov/2017:20:37:49 -0600] [Job 36] Hint: Try setting the LogLevel to "debug" to find out more.
D [06/Nov/2017:20:37:49 -0600] [Job 36] starting (raster2dymolw)
D [06/Nov/2017:20:37:49 -0600] [Job 36] Loading USB quirks from \"/usr/share/cups/usb\".
D [06/Nov/2017:20:37:49 -0600] [Job 36] Loaded 152 quirks.
D [06/Nov/2017:20:37:49 -0600] [Job 36] Printing on printer with URI: usb://DYMO/LabelWriter%204XL?serial=14070210130115
D [06/Nov/2017:20:37:49 -0600] [Job 36] libusb_get_device_list=7
D [06/Nov/2017:20:37:49 -0600] [Job 36] STATE: +connecting-to-device
D [06/Nov/2017:20:37:49 -0600] [Job 36] STATE: -connecting-to-device
D [06/Nov/2017:20:37:49 -0600] [Job 36] Printer found with device ID: MFG:DYMO;CMD: ;MDL:LabelWriter 450 Turbo;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 450 Turbo;SERN:10041918222229; Device URI: usb://DYMO/LabelWriter%20450%20Turbo?serial=10041918222229
D [06/Nov/2017:20:37:49 -0600] [Job 36] STATE: +connecting-to-device
D [06/Nov/2017:20:37:49 -0600] [Job 36] STATE: -connecting-to-device
D [06/Nov/2017:20:37:49 -0600] [Job 36] Printer found with device ID: MFG:DYMO;CMD: ;MDL:LabelWriter 4XL;CLASS:PRINTER;DESCRIPTION:DYMO LabelWriter 4XL;SERN:14070210130115; Device URI: usb://DYMO/LabelWriter%204XL?serial=14070210130115
D [06/Nov/2017:20:37:49 -0600] [Job 36] Device protocol: 2
D [06/Nov/2017:20:37:49 -0600] [Job 36] Sending data to printer.
D [06/Nov/2017:20:37:49 -0600] [Job 36] Sent 0 bytes...
D [06/Nov/2017:20:37:49 -0600] [Job 36] Waiting for read thread to exit...
D [06/Nov/2017:20:37:49 -0600] [Job 36] Read thread still active, aborting the pending read...
D [06/Nov/2017:20:37:49 -0600] [Job 36] PID 16399 (/usr/lib/cups/backend/usb) exited with no errors.
D [06/Nov/2017:20:37:49 -0600] [Job 36] End of messages
D [06/Nov/2017:20:37:49 -0600] [Job 36] printer-state=3(idle)
D [06/Nov/2017:20:37:49 -0600] [Job 36] printer-state-message="Sending data to printer."
D [06/Nov/2017:20:37:49 -0600] [Job 36] printer-state-reasons=none

```

And just in case it's any consolation... this is the error I get when I tried to make the DYMO SDK files:

```

user1@Server1:~/dymo-cups-drivers-1.4.0.5$ sudo make
Making all in src
make[1]: Entering directory '/home/user1/dymo-cups-drivers-1.4.0.5/src'
make  all-recursive
make[2]: Entering directory '/home/user1/dymo-cups-drivers-1.4.0.5/src'
Making all in lw
make[3]: Entering directory '/home/user1/dymo-cups-drivers-1.4.0.5/src/lw'
Making all in tests
make[4]: Entering directory '/home/user1/dymo-cups-drivers-1.4.0.5/src/lw/tests'
make[4]: Nothing to be user1e for 'all'.
make[4]: Leaving directory '/home/user1/dymo-cups-drivers-1.4.0.5/src/lw/tests'
make[4]: Entering directory '/home/user1/dymo-cups-drivers-1.4.0.5/src/lw'
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT raster2dymolw.o -MD -MP -MF .deps/raster2dymolw.Tpo -c -o raster2dymolw.o raster2dymolw.cpp
In file included from raster2dymolw.cpp:37:0:
../common/CupsFilter.h: In member function &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**)&#8217;:
../common/CupsFilter.h:135:10: warning: &#8216;template<class> class std::auto_ptr&#8217; is deprecated [-Wdeprecated-declarations]
     std::auto_ptr<CHalftoneFilter> H;
          ^~~~~~~~
In file included from /usr/include/c++/7/memory:80:0,
                 from raster2dymolw.cpp:28:
/usr/include/c++/7/bits/unique_ptr.h:51:28: note: declared here
   template<typename> class auto_ptr;
                            ^~~~~~~~
In file included from raster2dymolw.cpp:37:0:
../common/CupsFilter.h: In member function &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*)&#8217;:
../common/CupsFilter.h:218:3: error: &#8216;ppd_file_t&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
   ^~~~~~~~~~
../common/CupsFilter.h:218:3: note: suggested alternative: &#8216;cups_file_t&#8217;
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
   ^~~~~~~~~~
   cups_file_t
../common/CupsFilter.h:218:15: error: &#8216;ppd&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
               ^~~
../common/CupsFilter.h:218:21: error: there are no arguments to &#8216;ppdOpenFile&#8217; that depend on a template parameter, so a declaration of &#8216;ppdOpenFile&#8217; must be available [-fpermissive]
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ^~~~~~~~~~~
../common/CupsFilter.h:218:21: note: (if you use &#8216;-fpermissive&#8217;, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
../common/CupsFilter.h:228:3: error: there are no arguments to &#8216;ppdMarkDefaults&#8217; that depend on a template parameter, so a declaration of &#8216;ppdMarkDefaults&#8217; must be available [-fpermissive]
   ppdMarkDefaults(ppd);
   ^~~~~~~~~~~~~~~
../common/CupsFilter.h:234:7: error: there are no arguments to &#8216;ppdMarkOption&#8217; that depend on a template parameter, so a declaration of &#8216;ppdMarkOption&#8217; must be available [-fpermissive]
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ^~~~~~~~~~~~~
../common/CupsFilter.h:238:3: error: there are no arguments to &#8216;cupsMarkOptions&#8217; that depend on a template parameter, so a declaration of &#8216;cupsMarkOptions&#8217; must be available [-fpermissive]
   cupsMarkOptions(ppd, OptionCount, Options);
   ^~~~~~~~~~~~~~~
../common/CupsFilter.h:243:3: error: &#8216;ppd_choice_t&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
   ^~~~~~~~~~~~
../common/CupsFilter.h:243:3: note: suggested alternative: &#8216;cups_cspace_t&#8217;
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
   ^~~~~~~~~~~~
   cups_cspace_t
../common/CupsFilter.h:243:17: error: &#8216;choice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                 ^~~~~~
../common/CupsFilter.h:243:17: note: suggested alternative: &#8216;clone&#8217;
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                 ^~~~~~
                 clone
../common/CupsFilter.h:243:26: error: there are no arguments to &#8216;ppdFindMarkedChoice&#8217; that depend on a template parameter, so a declaration of &#8216;ppdFindMarkedChoice&#8217; must be available [-fpermissive]
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ^~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:3: error: there are no arguments to &#8216;ppdClose&#8217; that depend on a template parameter, so a declaration of &#8216;ppdClose&#8217; must be available [-fpermissive]
   ppdClose(ppd);
   ^~~~~~~~
In file included from raster2dymolw.cpp:38:0:
CupsFilterLabelWriter.h: At global scope:
CupsFilterLabelWriter.h:36:89: error: &#8216;ppd_file_t&#8217; has not been declared
   static void ProcessPPDOptions (CLabelWriterDriver& Driver, CDummyLanguageMonitor& LM, ppd_file_t* ppd);
                                                                                         ^~~~~~~~~~
CupsFilterLabelWriter.h:43:98: error: &#8216;ppd_file_t&#8217; has not been declared
   static void ProcessPPDOptions (CLabelWriterDriverTwinTurbo& Driver, CDummyLanguageMonitor& LM, ppd_file_t* ppd);
                                                                                                  ^~~~~~~~~~
In file included from raster2dymolw.cpp:38:0:
CupsFilterLabelWriter.h:50:95: error: &#8216;ppd_file_t&#8217; has not been declared
   static void ProcessPPDOptions (CLabelWriterDriver& Driver, CLabelWriterLanguageMonitor& LM, ppd_file_t* ppd);
                                                                                               ^~~~~~~~~~
CupsFilterLabelWriter.h:58:104: error: &#8216;ppd_file_t&#8217; has not been declared
   static void ProcessPPDOptions (CLabelWriterDriverTwinTurbo& Driver, CLabelWriterLanguageMonitor& LM, ppd_file_t* ppd);
                                                                                                        ^~~~~~~~~~
raster2dymolw.cpp: In function &#8216;int main(int, char**)&#8217;:
raster2dymolw.cpp:60:3: error: &#8216;ppd_file_t&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
   ^~~~~~~~~~
raster2dymolw.cpp:60:3: note: suggested alternative: &#8216;cups_file_t&#8217;
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
   ^~~~~~~~~~
   cups_file_t
raster2dymolw.cpp:60:15: error: &#8216;ppd&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
               ^~~
raster2dymolw.cpp:60:21: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ^~~~~~~~~~~
In file included from raster2dymolw.cpp:37:0:
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]&#8217;:
../common/CupsFilter.h:99:15:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]&#8217;
raster2dymolw.cpp:68:35:   required from here
../common/CupsFilter.h:218:32: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
../common/CupsFilter.h:228:18: error: &#8216;ppdMarkDefaults&#8217; was not declared in this scope
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
../common/CupsFilter.h:228:18: note: suggested alternative: &#8216;cupsLangDefault&#8217;
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
   cupsLangDefault
../common/CupsFilter.h:234:20: error: &#8216;ppdMarkOption&#8217; was not declared in this scope
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:234:20: note: suggested alternative: &#8216;cupsParseOptions&#8217;
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       cupsParseOptions
../common/CupsFilter.h:238:18: error: &#8216;cupsMarkOptions&#8217; was not declared in this scope
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:238:18: note: suggested alternative: &#8216;cupsParseOptions&#8217;
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
   cupsParseOptions
../common/CupsFilter.h:243:45: error: &#8216;ppdFindMarkedChoice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:11: error: &#8216;ppdClose&#8217; was not declared in this scope
   ppdClose(ppd);
   ~~~~~~~~^~~~~
../common/CupsFilter.h:248:11: note: suggested alternative: &#8216;pclose&#8217;
   ppdClose(ppd);
   ~~~~~~~~^~~~~
   pclose
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;:
../common/CupsFilter.h:99:15:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;
raster2dymolw.cpp:73:35:   required from here
../common/CupsFilter.h:218:32: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
../common/CupsFilter.h:228:18: error: &#8216;ppdMarkDefaults&#8217; was not declared in this scope
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
../common/CupsFilter.h:228:18: note: suggested alternative: &#8216;cupsLangDefault&#8217;
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
   cupsLangDefault
../common/CupsFilter.h:234:20: error: &#8216;ppdMarkOption&#8217; was not declared in this scope
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:234:20: note: suggested alternative: &#8216;cupsParseOptions&#8217;
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       cupsParseOptions
../common/CupsFilter.h:238:18: error: &#8216;cupsMarkOptions&#8217; was not declared in this scope
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:238:18: note: suggested alternative: &#8216;cupsParseOptions&#8217;
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
   cupsParseOptions
../common/CupsFilter.h:243:45: error: &#8216;ppdFindMarkedChoice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:11: error: &#8216;ppdClose&#8217; was not declared in this scope
   ppdClose(ppd);
   ~~~~~~~~^~~~~
../common/CupsFilter.h:248:11: note: suggested alternative: &#8216;pclose&#8217;
   ppdClose(ppd);
   ~~~~~~~~^~~~~
   pclose
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurboWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]&#8217;:
../common/CupsFilter.h:99:15:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurboWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]&#8217;
raster2dymolw.cpp:84:37:   required from here
../common/CupsFilter.h:218:32: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
../common/CupsFilter.h:228:18: error: &#8216;ppdMarkDefaults&#8217; was not declared in this scope
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
../common/CupsFilter.h:228:18: note: suggested alternative: &#8216;cupsLangDefault&#8217;
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
   cupsLangDefault
../common/CupsFilter.h:234:20: error: &#8216;ppdMarkOption&#8217; was not declared in this scope
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:234:20: note: suggested alternative: &#8216;cupsParseOptions&#8217;
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       cupsParseOptions
../common/CupsFilter.h:238:18: error: &#8216;cupsMarkOptions&#8217; was not declared in this scope
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:238:18: note: suggested alternative: &#8216;cupsParseOptions&#8217;
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
   cupsParseOptions
../common/CupsFilter.h:243:45: error: &#8216;ppdFindMarkedChoice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:11: error: &#8216;ppdClose&#8217; was not declared in this scope
   ppdClose(ppd);
   ~~~~~~~~^~~~~
../common/CupsFilter.h:248:11: note: suggested alternative: &#8216;pclose&#8217;
   ppdClose(ppd);
   ~~~~~~~~^~~~~
   pclose
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurbo; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;:
../common/CupsFilter.h:99:15:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurbo; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;
raster2dymolw.cpp:89:37:   required from here
../common/CupsFilter.h:218:32: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
../common/CupsFilter.h:228:18: error: &#8216;ppdMarkDefaults&#8217; was not declared in this scope
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
../common/CupsFilter.h:228:18: note: suggested alternative: &#8216;cupsLangDefault&#8217;
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
   cupsLangDefault
../common/CupsFilter.h:234:20: error: &#8216;ppdMarkOption&#8217; was not declared in this scope
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:234:20: note: suggested alternative: &#8216;cupsParseOptions&#8217;
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       cupsParseOptions
../common/CupsFilter.h:238:18: error: &#8216;cupsMarkOptions&#8217; was not declared in this scope
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:238:18: note: suggested alternative: &#8216;cupsParseOptions&#8217;
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
   cupsParseOptions
../common/CupsFilter.h:243:45: error: &#8216;ppdFindMarkedChoice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:11: error: &#8216;ppdClose&#8217; was not declared in this scope
   ppdClose(ppd);
   ~~~~~~~~^~~~~
../common/CupsFilter.h:248:11: note: suggested alternative: &#8216;pclose&#8217;
   ppdClose(ppd);
   ~~~~~~~~^~~~~
   pclose
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]&#8217;:
../common/CupsFilter.h:99:15:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]&#8217;
raster2dymolw.cpp:103:37:   required from here
../common/CupsFilter.h:218:32: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
../common/CupsFilter.h:228:18: error: &#8216;ppdMarkDefaults&#8217; was not declared in this scope
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
../common/CupsFilter.h:228:18: note: suggested alternative: &#8216;cupsLangDefault&#8217;
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
   cupsLangDefault
../common/CupsFilter.h:234:20: error: &#8216;ppdMarkOption&#8217; was not declared in this scope
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:234:20: note: suggested alternative: &#8216;cupsParseOptions&#8217;
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       cupsParseOptions
../common/CupsFilter.h:238:18: error: &#8216;cupsMarkOptions&#8217; was not declared in this scope
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:238:18: note: suggested alternative: &#8216;cupsParseOptions&#8217;
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
   cupsParseOptions
../common/CupsFilter.h:243:45: error: &#8216;ppdFindMarkedChoice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:11: error: &#8216;ppdClose&#8217; was not declared in this scope
   ppdClose(ppd);
   ~~~~~~~~^~~~~
../common/CupsFilter.h:248:11: note: suggested alternative: &#8216;pclose&#8217;
   ppdClose(ppd);
   ~~~~~~~~^~~~~
   pclose
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;:
../common/CupsFilter.h:99:15:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;
raster2dymolw.cpp:108:37:   required from here
../common/CupsFilter.h:218:32: error: &#8216;ppdOpenFile&#8217; was not declared in this scope
   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
../common/CupsFilter.h:228:18: error: &#8216;ppdMarkDefaults&#8217; was not declared in this scope
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
../common/CupsFilter.h:228:18: note: suggested alternative: &#8216;cupsLangDefault&#8217;
   ppdMarkDefaults(ppd);
   ~~~~~~~~~~~~~~~^~~~~
   cupsLangDefault
../common/CupsFilter.h:234:20: error: &#8216;ppdMarkOption&#8217; was not declared in this scope
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:234:20: note: suggested alternative: &#8216;cupsParseOptions&#8217;
       ppdMarkOption(ppd, Options[i].name, Options[i].value);
       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       cupsParseOptions
../common/CupsFilter.h:238:18: error: &#8216;cupsMarkOptions&#8217; was not declared in this scope
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:238:18: note: suggested alternative: &#8216;cupsParseOptions&#8217;
   cupsMarkOptions(ppd, OptionCount, Options);
   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
   cupsParseOptions
../common/CupsFilter.h:243:45: error: &#8216;ppdFindMarkedChoice&#8217; was not declared in this scope
   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:248:11: error: &#8216;ppdClose&#8217; was not declared in this scope
   ppdClose(ppd);
   ~~~~~~~~^~~~~
../common/CupsFilter.h:248:11: note: suggested alternative: &#8216;pclose&#8217;
   ppdClose(ppd);
   ~~~~~~~~^~~~~
   pclose
Makefile:345: recipe for target 'raster2dymolw.o' failed
make[4]: *** [raster2dymolw.o] Error 1
make[4]: Leaving directory '/home/user1/dymo-cups-drivers-1.4.0.5/src/lw'
Makefile:435: recipe for target 'all-recursive' failed
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory '/home/user1/dymo-cups-drivers-1.4.0.5/src/lw'
Makefile:262: recipe for target 'all-recursive' failed
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/user1/dymo-cups-drivers-1.4.0.5/src'
Makefile:204: recipe for target 'all' failed
make[1]: *** [all] Error 2
make[1]: Leaving directory '/home/user1/dymo-cups-drivers-1.4.0.5/src'
Makefile:263: recipe for target 'all-recursive' failed
make: *** [all-recursive] Error 1

```

---

### Post by gpecke on 2017-12-23
I have found the same bug. In my case it did not occur immediately, but after a period remote printing failed with the message you described. Local printing on the machine with the Dymo connected continues to function correctly.

I tried reinstalling the printer to no avail.

---

### Post by mmdeveloper2 on 2018-04-11
Okay I thought I was doing something wrong, I can't get the driver to "make" either

---

### Post by soloarielruiz on 2018-09-05
Hi, looking for all places i found this patch.
 git clone [https://aur.archlinux.org/dymo-cups-drivers.git](https://aur.archlinux.org/dymo-cups-drivers.git)

Then copy that files inside the folder of driver, and finally:
* patch -Np1 -i cups-ppd-header.patch
* ./configure
* make
* sudo make install 

I hope you serve them.

---

### Post by jamie-2 on 2018-11-06
Just wanted to say a big thank you for adding this patch man :D

---

### Post by pereclies on 2019-02-14
Super grateful for the patch as well. If anyone's looking for a quick fix, I made the change and put it up in a repo on my GitHub.

You just need to download and build it:
[https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux](https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux)

---

