---
title: "error installing cups printer (ubuntu server 9.04)"
date: 2009-09-06
forum: Server Platforms
---

### Post by vk7krj on 2009-09-06
I have just finished installing & setting up my web server & nas box using ubuntu server 9.04, and have thoroughly enjoyed the learning process (I am a complete beginner with linux).
However, getting the cups printer stuff working is driving me to distraction- I keep running up against the error

"Unable to copy interface script - No such file or directory!"

when it gets to the stage of copying the PPD file.
I have tried it with the file in it's own directory on my windows machine, in the root of the windows drive, and in its own shared directory on the ubuntu box, all produce the same error.

I have checked the permissions of the file, it is read, write and execute by anyone, I have tried it using the cups web interface, and I have tried it from the ubuntu box using links2. The cups web admin pages fill in some of the boxes for me with the correct name of the printer, so I assume it "sees" it ok.

I have googled and searched the forums for this, but nothing- any help on it would be greatly appreciated.

Thanks, Ken
[www.vk7krj.com](www.vk7krj.com)

---

### Post by vk7krj on 2009-09-08
[SIZE=3][FONT=Arial]bump[/FONT][/SIZE]

---

### Post by vk7krj on 2009-09-08
Still badly needing help on this one- I am just going round in circles now.  If it's any help, here is the error log from my last attempt to install this printer- I begin to think it is actually missing some file/files somewhere, what other files/ directories does cups expect to find during the printer install process?

D [09/Sep/2009:11:46:13 +1000] cupsdNetIFUpdate: "lo" = localhost:631
D [09/Sep/2009:11:46:13 +1000] cupsdNetIFUpdate: "eth0" = 192.168.9.3:631
D [09/Sep/2009:11:46:13 +1000] cupsdNetIFUpdate: "lo" = localhost:631
D [09/Sep/2009:11:46:13 +1000] cupsdNetIFUpdate: "eth0" = fe80::240:63ff:fefa:7dca%eth0:631
D [09/Sep/2009:11:46:13 +1000] Report: clients=1
D [09/Sep/2009:11:46:13 +1000] Report: jobs=0
D [09/Sep/2009:11:46:13 +1000] Report: jobs-active=0
D [09/Sep/2009:11:46:13 +1000] Report: printers=1
D [09/Sep/2009:11:46:13 +1000] Report: printers-implicit=0
D [09/Sep/2009:11:46:13 +1000] Report: stringpool-string-count=198
D [09/Sep/2009:11:46:13 +1000] Report: stringpool-alloc-bytes=5376
D [09/Sep/2009:11:46:13 +1000] Report: stringpool-total-bytes=4304
D [09/Sep/2009:11:46:13 +1000] update_cups_browse: Refused 120 bytes from 192.168.9.3
D [09/Sep/2009:11:46:30 +1000] cupsdReadClient: 7 POST /admin HTTP/1.1
D [09/Sep/2009:11:46:31 +1000] cupsdAuthorize: Authorized as root using Basic
D [09/Sep/2009:11:46:31 +1000] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 6318
I [09/Sep/2009:11:46:31 +1000] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6318)
D [09/Sep/2009:11:46:31 +1000] cupsdSendCommand: 7 file=21
D [09/Sep/2009:11:46:31 +1000] cupsdAcceptClient: 20 from localhost:631 (IPv6)
D [09/Sep/2009:11:46:31 +1000] [CGI] admin.cgi started...
D [09/Sep/2009:11:46:31 +1000] [CGI] http=0xb92d3a30
D [09/Sep/2009:11:46:31 +1000] [CGI] op="add-printer"...
D [09/Sep/2009:11:46:31 +1000] [CGI] do_am_printer: DEVICE_URI="parallel:/dev/lp0"
D [09/Sep/2009:11:46:31 +1000] [CGI] file->tempfile=/var/spool/cups/tmp/4aa708f72c5de
D [09/Sep/2009:11:46:31 +1000] [CGI] file->name=PPD_FILE
D [09/Sep/2009:11:46:31 +1000] [CGI] file->filename=FP203A.PPD
D [09/Sep/2009:11:46:31 +1000] [CGI] file->mimetype=text/plain; charset=us-ascii
D [09/Sep/2009:11:46:31 +1000] cupsdReadClient: 20 POST /admin/ HTTP/1.1
D [09/Sep/2009:11:46:31 +1000] cupsdAuthorize: No authentication data provided.
D [09/Sep/2009:11:46:31 +1000] CUPS-Add-Modify-Printer ipp://localhost/printers/FX_DocuPrint_203A_LPT_1
E [09/Sep/2009:11:46:31 +1000] CUPS-Add-Modify-Printer: Unauthorized
D [09/Sep/2009:11:46:31 +1000] cupsdSendError: 20 code=401 (Unauthorized)
D [09/Sep/2009:11:46:31 +1000] cupsdCloseClient: 20
D [09/Sep/2009:11:46:31 +1000] cupsdAcceptClient: 20 from localhost:631 (IPv6)
D [09/Sep/2009:11:46:31 +1000] cupsdReadClient: 20 POST /admin/ HTTP/1.1
D [09/Sep/2009:11:46:31 +1000] cupsdAuthorize: Authorized as root using Local
D [09/Sep/2009:11:46:31 +1000] CUPS-Add-Modify-Printer ipp://localhost/printers/FX_DocuPrint_203A_LPT_1
D [09/Sep/2009:11:46:31 +1000] cupsdIsAuthorized: username="root"
I [09/Sep/2009:11:46:31 +1000] Setting FX_DocuPrint_203A_LPT_1 device-uri to "parallel:/dev/lp0" (was "parallel:/dev/lp0".)
I [09/Sep/2009:11:46:31 +1000] Setting FX_DocuPrint_203A_LPT_1 printer-is-accepting-jobs to 1 (was 1.)
I [09/Sep/2009:11:46:31 +1000] Setting FX_DocuPrint_203A_LPT_1 printer-state to 3 (was 3.)
D [09/Sep/2009:11:46:31 +1000] CUPS-Add-Modify-Printer server-error-internal-error: Unable to copy interface script - No such file or directory!
D [09/Sep/2009:11:46:31 +1000] cupsdProcessIPPRequest: 20 status_code=500 (server-error-internal-error)
D [09/Sep/2009:11:46:31 +1000] [CGI] lang="en.UTF8", locale="/en"...
D [09/Sep/2009:11:46:31 +1000] cupsdCloseClient: 20
D [09/Sep/2009:11:46:31 +1000] PID 6318 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [09/Sep/2009:11:46:31 +1000] [CGI] lang="en.UTF8", locale="/en"...
D [09/Sep/2009:11:46:31 +1000] [CGI] lang="en.UTF8", locale="/en"...
D [09/Sep/2009:11:46:44 +1000] update_cups_browse: Refused 121 bytes from 192.168.9.3
D [09/Sep/2009:11:46:53 +1000] cupsdAcceptClient: 20 from 192.168.9.2:631 (IPv4)
D [09/Sep/2009:11:46:53 +1000] cupsdReadClient: 20 GET /admin/log/error_log HTTP/1.1
D [09/Sep/2009:11:46:53 +1000] cupsdAuthorize: No authentication data provided.

Thanks, Ken
[www.vk7krj.com]("http://www.vk7krj.com")

---

