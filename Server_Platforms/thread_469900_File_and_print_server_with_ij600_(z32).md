---
title: "File and print server with ij600 (z32)"
date: 2007-06-10
forum: Server Platforms
---

### Post by waltnorth on 2007-06-10
I am setting up a fiesty server for file and print services.  The file server stuff is working fine.  I have an old ij600 (rebranded lexmark z32) that still works just fine (I was using it under Fedora 4 for quite a while until last week).  Now that I'm switching to Ubuntu server I have to go though the headaches of getting it to work again (or get a new printer - but you learn more this way).  I have tried a couple of different ways as shown below.

=============================================
First approach I used were the following steps I found (with some inserted steps to take care of missing links). But I ran into a problem that that foomatic-kitload is missing (used in the install script as "foomatic-kitload -f -k foomatic-db"). Is this not part of the server base and if not where do I get and install it?

>>>>>>>>> Added these steps to create links so the later steps don't complain:

go to /usr/local/lib
ls -l libvdkcompo.so.1
it will show where that is linked to(if it is linked) 
libvdkcompo.so.1->/.../.../libvdk...
go to /usr/lib
do ln -snf /usr/local/lib/libvdk... libvdkcompo.so.1
also do the same for libvdk.so.1
and for libstdc++-libc6.1-1.so.2
ln -s /usr/lib/libstdc++.so.6.0.8 /usr/lib/libstdc++-libc6.1-1.so.2

>>>>>>>>>> Found these steps on the internet

**Downloading driver from lexmark site and install
[http://www.downloaddelivery.com/srfilecache/z32_eng_us-1.0-5.tgz](http://www.downloaddelivery.com/srfilecache/z32_eng_us-1.0-5.tgz)
sudo tar -zxvf z32_eng_us-1.0-5.tgz
cd rpm/z32/english_US
sudo alien -c lexmarkz22-z32-1.0-5.i386.rpm
sudo dpkg -i lexmarkz22-z32_1.0-5_i386.deb
**Downloading and install lexmark-footmatik-kit
gz...
sudo tar -zxvf lexmark-foomatic-kit.tar.gz
cd lexmark-foomatic-kit
sudo sh install

>>>>>>>>>> It breaks here because foomatic-kitload is not found.

sudo pearl lexmarkinstall
...
***Edit ppd file in /etc/cups/ppd
sudo gedit ppdfile.ppd
edit file and change instances of /dev/usb/lp0 , /dev/usb/lp1, /dev/usb/lp2 change to /dev/usblp0, 
/dev/usblp1,/dev/usblp2.
***Add user in printer group
sudo adduser lp
***Add alias in your ~/.bashrc to run the align and clean pages, new commands printalign and printclean for 
lexmark printer.
sudo gedit ~/.bashrc
add lines in end of file
alias printclean='cat /usr/local/lexmark/z32/lxaecln.out > /dev/usblp0'
alias printalign='cat /usr/local/lexmark/z32/lxaealgn.out > /dev/usblp0'
save the file.
reboot your PC

=============================================
Second approach I tried was one I found on Ubuntu forums.

 mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

/etc/rc2.d/S19cupsys restart

cd /usr/lib/cups/backend

./z600

>>>>>>>>>  I ran into these problems:

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

>>>>>>>>>> So I tried creating this link:
$ sudo ln -s /usr/lib/libstdc++.so.6.0.8 /usr/lib/libstdc++.so.5

$ ./z600
./z600: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./z600)
./z600: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./z600)

=====================
At this point I will pick this up again later but for now I have to do some real work.
Thanks for any advice.

---

### Post by waltnorth on 2007-06-10
Well.. I got past the foomatic problem with 
apt-get install foomatic-db-engine

Now to see if I can get webmin to recoginize it.

---

### Post by waltnorth on 2007-06-11
I've got my printer added and it shows up in webmin printers and even seems to be recoginizing the ppd file (after moving it to the correct place as configured in webmin).  But now it refused to enable the printer. I click the YES button and save but it does not enable it.  For that matter it doesn't seem to be saving the print banner option either.

Does any one know where the raw config option is so I can see what it show?

---

### Post by waltnorth on 2007-06-13
I was never able to get webmin to enable the printer but I found the cupsenable command did the trick.

However while I can submit files to print (using lp or with webmin test page) and they do show up in the queue they never print and remain in the queue.  
I've turned on debug in the cupsd.conf file and I can it attempting to  go through the printing process.  

At this point I'm not sure if this questions still belongs in the server forum or if I should move over to the general forum.  In any case I will attach some debug output in case anyone has any ideas.

Individual lines from the log seem like possible culprits:
============
D [12/Jun/2007:14:57:38 -0700] [Job 8] sh: cannot create /dev/lp0: Device or resource busy

D [12/Jun/2007:14:57:41 -0700] [Job 8] Warning: the map file cidfmap was not found.

E [12/Jun/2007:14:57:48 -0700] [Job 8] /ioerror in --.outputpage--
D [12/Jun/2007:14:57:48 -0700] [Job 8] Operand stack:
D [12/Jun/2007:14:57:48 -0700] [Job 8] 1   true
D [12/Jun/2007:14:57:48 -0700] [Job 8] Execution stack:
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:48 -0700] Discarding unused printer-state-changed event...
D [12/Jun/2007:14:57:48 -0700] [Job 8] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   0   3   %oparray_pop   --nostringval--   --nostringval--
D [12/Jun/2007:14:57:48 -0700] [Job 8] Dictionary stack:
D [12/Jun/2007:14:57:48 -0700] [Job 8] --dict:1126/1686(ro)(G)--   --dict:0/20(G)--   --dict:103/200(L)--
D [12/Jun/2007:14:57:48 -0700] [Job 8] Current allocation mode is local
D [12/Jun/2007:14:57:48 -0700] [Job 8] Last OS error: 32
D [12/Jun/2007:14:57:48 -0700] [Job 8] ESP Ghostscript 815.04: Unrecoverable error, exit code 1
D [12/Jun/2007:14:57:48 -0700] [Job 8] error closing printing command line.
D [12/Jun/2007:14:57:48 -0700] [Job 8] renderer return value: 2
D [12/Jun/2007:14:57:48 -0700] [Job 8] renderer received signal: 2
D [12/Jun/2007:14:57:48 -0700] [Job 8] tail process done writing data to STDOUT
D [12/Jun/2007:14:57:48 -0700] [Job 8] KID4 finished
D [12/Jun/2007:14:57:48 -0700] [Job 8] Process dying with "The renderer command line returned an unrecognized error code 2.", exit stat: 1
D [12/Jun/2007:14:57:48 -0700] [Job 8] error: Illegal seek (29)
D [12/Jun/2007:14:57:48 -0700] [Job 8] The renderer command line returned an unrecognized error code 2.
D [12/Jun/2007:14:57:49 -0700] [Job 8] KID4 exited with status 0
D [12/Jun/2007:14:57:49 -0700] [Job 8] KID3 exited with status 1
D [12/Jun/2007:14:57:49 -0700] [Job 8] Renderer exit stat: 1
D [12/Jun/2007:14:57:49 -0700] [Job 8] Renderer process finished
D [12/Jun/2007:14:57:49 -0700] [Job 8] Killing process 4856 (KID3)




Complete set of lines from the log file.
============
I [12/Jun/2007:14:57:37 -0700] Job 8 queued on "NorthPrinter" by "root".
D [12/Jun/2007:14:57:37 -0700] Job 8 hold_until = 0
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:37 -0700] Discarding unused printer-state-changed event...
D [12/Jun/2007:14:57:37 -0700] job-sheets=none,none
D [12/Jun/2007:14:57:37 -0700] banner_page = 0
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[0]="NorthPrinter"
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[1]="8"
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[2]="root"
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[3]="bw.ps"
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[4]="1"
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[5]="job-uuid=urn:uuid:3c6dc89b-d8d0-3191-7c37-d1ef8d5d5076"
D [12/Jun/2007:14:57:37 -0700] [Job 8] argv[6]="/var/spool/cups/d00008-001"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[9]="SERVER_ADMIN=root@NorthServer.NorthFamily"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[10]="SOFTWARE=CUPS/1.2.8"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[12]="TZ=US/Pacific"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[13]="USER=root"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[16]="CHARSET=utf-8"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[17]="LANG=en_US"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[18]="PPD=/etc/cups/ppd/NorthPrinter.ppd"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[19]="RIP_MAX_CACHE=8m"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[20]="CONTENT_TYPE=application/postscript"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[21]="DEVICE_URI=parallel:/dev/lp0"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[22]="PRINTER=NorthPrinter"
D [12/Jun/2007:14:57:37 -0700] [Job 8] envp[23]="FINAL_CONTENT_TYPE=printer/NorthPrinter"
I [12/Jun/2007:14:57:37 -0700] Started filter /usr/lib/cups/filter/pstops (PID 4844) for job 8.
I [12/Jun/2007:14:57:37 -0700] Started filter /usr/lib/cups/filter/foomatic-rip (PID 4845) for job 8.
I [12/Jun/2007:14:57:37 -0700] Started backend /usr/lib/cups/backend/parallel (PID 4846) for job 8.
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:37 -0700] Discarding unused job-state event...
D [12/Jun/2007:14:57:37 -0700] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:37 -0700] PID 4844 (/usr/lib/cups/filter/pstops) exited with no errors.
D [12/Jun/2007:14:57:37 -0700] [Job 8] Page = 612x792; 0,0 to 612,792
D [12/Jun/2007:14:57:37 -0700] [Job 8] slow_collate=0, slow_duplex=0, slow_order=0
D [12/Jun/2007:14:57:37 -0700] [Job 8] Before copy_comments - %!PS-Adobe-2.0
D [12/Jun/2007:14:57:37 -0700] [Job 8] %!PS-Adobe-2.0
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%Title: bw.ps
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%Creator: fig2dev Version 3.2 Patchlevel 1
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%CreationDate: Mon Dec  4 16:12:32 2000
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%For: [email]jcameron@vaio.home[/email] (Jamie Cameron)
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%Orientation: Portrait
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%BoundingBox: 49 32 568 799
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%Pages: 1
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%BeginSetup
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%IncludeFeature: *PageSize A4
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%EndSetup
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%Magnification: 1.0000
D [12/Jun/2007:14:57:37 -0700] [Job 8] %%EndComments
D [12/Jun/2007:14:57:37 -0700] [Job 8] Before copy_prolog - /$F2psDict 200 dict def
D [12/Jun/2007:14:57:37 -0700] [Job 8] Before copy_setup - %%Page: 1 1
D [12/Jun/2007:14:57:37 -0700] [Job 8] Before page loop - %%Page: 1 1
D [12/Jun/2007:14:57:37 -0700] [Job 8] Copying page 1...
D [12/Jun/2007:14:57:37 -0700] [Job 8] pagew = 612.0, pagel = 792.0
D [12/Jun/2007:14:57:37 -0700] [Job 8] bboxw = 612, bboxl = 792
D [12/Jun/2007:14:57:37 -0700] [Job 8] PageLeft = 0.0, PageRight = 612.0
D [12/Jun/2007:14:57:37 -0700] [Job 8] PageTop = 792.0, PageBottom = 0.0
D [12/Jun/2007:14:57:37 -0700] [Job 8] PageWidth = 612.0, PageLength = 792.0
D [12/Jun/2007:14:57:37 -0700] [Job 8] Wrote 1 pages...
D [12/Jun/2007:14:57:37 -0700] [Job 8] perl: warning: Setting locale failed.
D [12/Jun/2007:14:57:37 -0700] [Job 8] perl: warning: Please check that your locale settings:
D [12/Jun/2007:14:57:37 -0700] [Job 8] LANGUAGE = (unset),
D [12/Jun/2007:14:57:37 -0700] [Job 8] LC_ALL = (unset),
D [12/Jun/2007:14:57:37 -0700] [Job 8] LANG = "en_US"
D [12/Jun/2007:14:57:37 -0700] [Job 8] are supported and installed on your system.
D [12/Jun/2007:14:57:37 -0700] [Job 8] perl: warning: Falling back to the standard locale ("C").
D [12/Jun/2007:14:57:37 -0700] cupsdCloseClient: 19
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:37 -0700] Discarding unused printer-state-changed event...
D [12/Jun/2007:14:57:37 -0700] [Job 8] backendRunLoop(print_fd=0, device_fd=4, use_bc=0)
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:37 -0700] Discarding unused printer-state-changed event...
D [12/Jun/2007:14:57:38 -0700] [Job 8] foomatic-rip version $Revision$ running...
D [12/Jun/2007:14:57:38 -0700] [Job 8] Parsing PPD file ...
D [12/Jun/2007:14:57:38 -0700] [Job 8] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option ColorSpace
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option PageSize
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option PageRegion
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option ImageableArea
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option PaperDimension
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option Resolution
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option MediaType
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option Mode
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option Model
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option ImageType
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option Dither
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option Port
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option AlignA
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option AlignB
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option AlignC
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option AlignD
D [12/Jun/2007:14:57:38 -0700] [Job 8] Added option Font
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Parameter Summary
D [12/Jun/2007:14:57:38 -0700] [Job 8] -----------------
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Spooler: cups
D [12/Jun/2007:14:57:38 -0700] [Job 8] Printer: NorthPrinter
D [12/Jun/2007:14:57:38 -0700] [Job 8] Shell: /bin/bash
D [12/Jun/2007:14:57:38 -0700] [Job 8] PPD file: /etc/cups/ppd/NorthPrinter.ppd
D [12/Jun/2007:14:57:38 -0700] [Job 8] ATTR file: 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Printer model: Lexmark Z32 Foomatic/lexmarkinkjet
D [12/Jun/2007:14:57:38 -0700] [Job 8] Job title: bw.ps
D [12/Jun/2007:14:57:38 -0700] [Job 8] File(s) to be printed: 
D [12/Jun/2007:14:57:38 -0700] [Job 8] <STDIN>
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [12/Jun/2007:14:57:38 -0700] [Job 8] Pondering option 'job-uuid=urn:uuid:3c6dc89b-d8d0-3191-7c37-d1ef8d5d5076'
D [12/Jun/2007:14:57:38 -0700] [Job 8] Unknown option job-uuid=urn:uuid:3c6dc89b-d8d0-3191-7c37-d1ef8d5d5076.
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] ================================================
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] File: <STDIN>
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] ================================================
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Reading PostScript input ...
D [12/Jun/2007:14:57:38 -0700] [Job 8] --> This document is DSC-conforming!
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] -----------
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginSetup
D [12/Jun/2007:14:57:38 -0700] [Job 8] "Prolog" section is missing, inserting it.
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%EndSetup
D [12/Jun/2007:14:57:38 -0700] [Job 8] Inserting PostScript code for CUPS' page accounting
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%EndProlog
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] -----------
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginProlog
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%EndProlog
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] -----------
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginSetup
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *PageSize Letter
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: PageSize=Letter --> Option will be set by PostScript interpreter
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *Resolution 600
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Resolution=600 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: Resolution=600
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Resolution=600 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *MediaType Plain
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: MediaType=Plain --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: MediaType=Plain
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: MediaType=Plain --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *Mode Colour
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Mode=Colour --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: Mode=Colour
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Mode=Colour --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *ImageType Business
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: ImageType=Business --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: ImageType=Business
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: ImageType=Business --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *Dither Auto
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Dither=Auto --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: Dither=Auto
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Dither=Auto --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *Port ParPort1
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Port=ParPort1 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: Port=ParPort1
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: Port=ParPort1 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *AlignA 16
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignA=16 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: AlignA=16
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignA=16 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *AlignB 8
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignB=8 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: AlignB=8
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignB=8 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *AlignC 16
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignC=16 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: AlignC=16
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignC=16 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginFeature: *AlignD 16
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignD=16 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %% FoomaticRIPOptionSetting: AlignD=16
D [12/Jun/2007:14:57:38 -0700] [Job 8] Option: AlignD=16 --> Setting option
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%EndSetup
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] -----------
D [12/Jun/2007:14:57:38 -0700] [Job 8] New page:  1 1
D [12/Jun/2007:14:57:38 -0700] [Job 8] Inserting option code into "PageSetup" section.
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%BeginPageSetup
D [12/Jun/2007:14:57:38 -0700] [Job 8] Found: %%EndPageSetup
D [12/Jun/2007:14:57:38 -0700] [Job 8] End of page header
D [12/Jun/2007:14:57:38 -0700] [Job 8] Flushing FIFO.
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Starting renderer
D [12/Jun/2007:14:57:38 -0700] [Job 8] JCL: <job data> 
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] renderer PID kid4=4857
D [12/Jun/2007:14:57:38 -0700] [Job 8] renderer command: lexmarkwrapper -r 600 -t 0 -c CMYK -m z32 -i business -d 5 -p /dev/lp0 -A 16 -B 8 -C 16 -D 16 > /dev/null
D [12/Jun/2007:14:57:38 -0700] [Job 8] 
D [12/Jun/2007:14:57:38 -0700] [Job 8] Closing renderer
D [12/Jun/2007:14:57:38 -0700] [Job 8] perl: warning: Setting locale failed.
D [12/Jun/2007:14:57:38 -0700] [Job 8] perl: warning: Please check that your locale settings:
D [12/Jun/2007:14:57:38 -0700] [Job 8] LANGUAGE = (unset),
D [12/Jun/2007:14:57:38 -0700] [Job 8] LC_ALL = (unset),
D [12/Jun/2007:14:57:38 -0700] [Job 8] LANG = "en_US"
D [12/Jun/2007:14:57:38 -0700] [Job 8] are supported and installed on your system.
D [12/Jun/2007:14:57:38 -0700] [Job 8] perl: warning: Falling back to the standard locale ("C").
D [12/Jun/2007:14:57:38 -0700] [Job 8] perl: warning: Setting locale failed.
D [12/Jun/2007:14:57:38 -0700] [Job 8] perl: warning: Please check that your locale settings:
D [12/Jun/2007:14:57:38 -0700] [Job 8] LANGUAGE = (unset),
D [12/Jun/2007:14:57:38 -0700] [Job 8] LC_ALL = (unset),
D [12/Jun/2007:14:57:38 -0700] [Job 8] LANG = "en_US"
D [12/Jun/2007:14:57:38 -0700] [Job 8] are supported and installed on your system.
D [12/Jun/2007:14:57:38 -0700] [Job 8] perl: warning: Falling back to the standard locale ("C").
D [12/Jun/2007:14:57:38 -0700] [Job 8] sh: cannot create /dev/lp0: Device or resource busy
D [12/Jun/2007:14:57:39 -0700] [Job 8] foomatic-gswrapper: gs '-sstdout=%stderr' '-dBATCH' '-dNOPAUSE' '-dSAFER' '-r600' '-sDEVICE=ppmraw' '-sOutputFile=%stdout' '-'
D [12/Jun/2007:14:57:39 -0700] [Job 8] ESP Ghostscript 815.04 (2007-03-14)
D [12/Jun/2007:14:57:39 -0700] [Job 8] Copyright (C) 2004 artofcode LLC, Benicia, CA.  All rights reserved.
D [12/Jun/2007:14:57:39 -0700] [Job 8] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [12/Jun/2007:14:57:41 -0700] [Job 8] Warning: the map file cidfmap was not found.
D [12/Jun/2007:14:57:41 -0700] [Job 8] Loading NimbusRomNo9L-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n021003l.pfb... 2472720 1166871 2340708 635928 3 done.
D [12/Jun/2007:14:57:48 -0700] cupsdAcceptClient: 25 from localhost (Domain)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Classes
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Default
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdCloseClient: 25
D [12/Jun/2007:14:57:48 -0700] cupsdAcceptClient: 25 from localhost (Domain)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Classes
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Default
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] Get-Jobs ipp://localhost/printers/NorthPrinter
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdCloseClient: 25
D [12/Jun/2007:14:57:48 -0700] cupsdAcceptClient: 25 from localhost (Domain)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Classes
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Default
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [12/Jun/2007:14:57:48 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:48 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:48 -0700] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:48 -0700] cupsdCloseClient: 25
E [12/Jun/2007:14:57:48 -0700] [Job 8] /ioerror in --.outputpage--
D [12/Jun/2007:14:57:48 -0700] [Job 8] Operand stack:
D [12/Jun/2007:14:57:48 -0700] [Job 8] 1   true
D [12/Jun/2007:14:57:48 -0700] [Job 8] Execution stack:
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:48 -0700] Discarding unused printer-state-changed event...
D [12/Jun/2007:14:57:48 -0700] [Job 8] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   0   3   %oparray_pop   --nostringval--   --nostringval--
D [12/Jun/2007:14:57:48 -0700] [Job 8] Dictionary stack:
D [12/Jun/2007:14:57:48 -0700] [Job 8] --dict:1126/1686(ro)(G)--   --dict:0/20(G)--   --dict:103/200(L)--
D [12/Jun/2007:14:57:48 -0700] [Job 8] Current allocation mode is local
D [12/Jun/2007:14:57:48 -0700] [Job 8] Last OS error: 32
D [12/Jun/2007:14:57:48 -0700] [Job 8] ESP Ghostscript 815.04: Unrecoverable error, exit code 1
D [12/Jun/2007:14:57:48 -0700] [Job 8] error closing printing command line.
D [12/Jun/2007:14:57:48 -0700] [Job 8] renderer return value: 2
D [12/Jun/2007:14:57:48 -0700] [Job 8] renderer received signal: 2
D [12/Jun/2007:14:57:48 -0700] [Job 8] tail process done writing data to STDOUT
D [12/Jun/2007:14:57:48 -0700] [Job 8] KID4 finished
D [12/Jun/2007:14:57:48 -0700] [Job 8] Process dying with "The renderer command line returned an unrecognized error code 2.", exit stat: 1
D [12/Jun/2007:14:57:48 -0700] [Job 8] error: Illegal seek (29)
D [12/Jun/2007:14:57:48 -0700] [Job 8] The renderer command line returned an unrecognized error code 2.
D [12/Jun/2007:14:57:49 -0700] [Job 8] KID4 exited with status 0
D [12/Jun/2007:14:57:49 -0700] [Job 8] KID3 exited with status 1
D [12/Jun/2007:14:57:49 -0700] [Job 8] Renderer exit stat: 1
D [12/Jun/2007:14:57:49 -0700] [Job 8] Renderer process finished
D [12/Jun/2007:14:57:49 -0700] [Job 8] Killing process 4856 (KID3)
D [12/Jun/2007:14:57:49 -0700] [Job 8] Process dying with "Error closing renderer", exit stat: 1
D [12/Jun/2007:14:57:49 -0700] [Job 8] error: Bad file descriptor (9)
D [12/Jun/2007:14:57:49 -0700] [Job 8] Error closing renderer
E [12/Jun/2007:14:57:49 -0700] PID 4845 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
D [12/Jun/2007:14:57:49 -0700] PID 4846 (/usr/lib/cups/backend/parallel) exited with no errors.
D [12/Jun/2007:14:57:49 -0700] [Job 8] File 0 is complete.
process 3850: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
D [12/Jun/2007:14:57:49 -0700] Discarding unused printer-state-changed event...
D [12/Jun/2007:14:57:49 -0700] Discarding unused job-stopped event...
D [12/Jun/2007:14:57:49 -0700] cupsdAcceptClient: 26 from localhost (Domain)
D [12/Jun/2007:14:57:49 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:49 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:49 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:49 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:49 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:49 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:49 -0700] CUPS-Get-Classes
D [12/Jun/2007:14:57:49 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:49 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:49 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:49 -0700] CUPS-Get-Default
D [12/Jun/2007:14:57:49 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:49 -0700] cupsdCloseClient: 26
D [12/Jun/2007:14:57:50 -0700] Unloading job 8...
D [12/Jun/2007:14:57:52 -0700] cupsdAcceptClient: 26 from localhost (Domain)
D [12/Jun/2007:14:57:52 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:52 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:52 -0700] CUPS-Get-Printers
D [12/Jun/2007:14:57:52 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:52 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:52 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:52 -0700] CUPS-Get-Classes
D [12/Jun/2007:14:57:52 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:52 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:52 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:52 -0700] CUPS-Get-Default
D [12/Jun/2007:14:57:52 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:52 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:52 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:52 -0700] Get-Printer-Attributes ipp://localhost/printers/NorthPrinter
D [12/Jun/2007:14:57:52 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:52 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:14:57:52 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:14:57:52 -0700] Get-Jobs ipp://localhost/printers/NorthPrinter
D [12/Jun/2007:14:57:52 -0700] Loading attributes for job 8...
D [12/Jun/2007:14:57:52 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:14:57:52 -0700] cupsdCloseClient: 26
D [12/Jun/2007:15:03:41 -0700] Unloading job 8...
D [12/Jun/2007:15:03:41 -0700] cupsdAcceptClient: 26 from localhost (Domain)
D [12/Jun/2007:15:03:41 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:15:03:41 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:15:03:41 -0700] CUPS-Get-Printers
D [12/Jun/2007:15:03:41 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:15:03:41 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:15:03:41 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:15:03:41 -0700] CUPS-Get-Classes
D [12/Jun/2007:15:03:41 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:15:03:41 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:15:03:41 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:15:03:41 -0700] CUPS-Get-Default
D [12/Jun/2007:15:03:41 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:15:03:41 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:15:03:41 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:15:03:41 -0700] Get-Printer-Attributes ipp://localhost/printers/NorthPrinter
D [12/Jun/2007:15:03:41 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:15:03:41 -0700] cupsdReadClient: 26 POST / HTTP/1.1
D [12/Jun/2007:15:03:41 -0700] cupsdAuthorize: No authentication data provided.
D [12/Jun/2007:15:03:41 -0700] Get-Jobs ipp://localhost/printers/NorthPrinter
D [12/Jun/2007:15:03:41 -0700] Loading attributes for job 8...
D [12/Jun/2007:15:03:41 -0700] cupsdProcessIPPRequest: 26 status_code=0 (successful-ok)
D [12/Jun/2007:15:03:41 -0700] cupsdCloseClient: 26

---

