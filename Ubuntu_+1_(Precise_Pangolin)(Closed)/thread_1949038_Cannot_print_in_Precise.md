---
title: "Cannot print in Precise"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ratcheer on 2012-03-29
I have really been looking forward to the release of Precise, but this may be a deal breaker for me. I need to be able to print things because I am home schooling my son.

My printer is a Canon MP620. The driver is the one installed and set up by the script from this web site: [http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer](http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer)

When I try to print something, the Ubuntu print monitor changes status just like things are working just fine, but there is no activity on the printer. It ends up with a status of "Idle - Ready to print", just like the job had completed successfully. But in CUPS, I can see this error message: [I]"/usr/lib/cups/filter/pstocanonij failed"

I have Googled that message and I get hundreds of hits dating back several years to the present. They are for all sorts of problems. I have been unable to link any of them to my problem in order to find a solution. Some of them were accepted as bugs in Launchpad, for which fixes were made years ago.
[/I]
Anyway, this exact same setup prints just fine in Oneiric. I do not know whether it is a printer setup error by me, an incompatibility of the driver with Precise, or a bug. If it is a bug, there are many possible sources: CUPS, Ghostscript, libpng, or who knows what else.

I have been trying to resolve this since yesterday morning. Any help will be much appreciated.

Tim

---

### Post by neu5eeCh on 2012-03-29
First, take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1939744").

Second, has the printer worked in other distributions or Ubuntu versions?

Third, file a bug report. Just do it, even if you're not sure what's causing it. This is the time to do it. Alt+f2 ubuntu-bug cups (or look in your system monitor for a PID).

---

### Post by kurt18947 on 2012-03-29
I second the O.P. s observation that something has changed re printing in Precise.  I have printer setups that have worked very well since at least 10.04 or before.  Printers still work for me (Brothers) but previously a print job started with 5 seconds of hitting 'print'.  Using Precise printing graphics like web pages it takes 45 seconds or longer for the printer to come alive.  I don't see anything funky in dmesg and don't know where else to look for clues.

---

### Post by ratcheer on 2012-03-29
> **VTPoet said:**
> 
Second, has the printer worked in other distributions or Ubuntu versions?



Yes, my original post states that "this exact same setup prints just fine in Oneiric".

Thanks for the pointer to the other thread. I will look into it. Also, if I manage to file a bug, I will post a link to it.

Tim

---

### Post by ratcheer on 2012-03-29
This is from bug 856028, where a user reported the same "pstocanonij failed" message:

                        > This is not a bug in Ubuntu. The problem here is that a manufacturer-supplied  closed-source driver was created for older Linux distributions and does  not work any more with Oneiric as Oneiric ships newer libraries. The  problem can only be solved by Canon, publishing open-source  free-software drivers (so that they can be rebuilt for newer  distributions) or at least publish LSB-based packages which are  distribution-independent.
 Closing ...


Tim

---

### Post by ratcheer on 2012-03-29
I found a CUPS error log. Here is what it says for the last print job I attempted:

```

E [29/Mar/2012:10:52:14 -0500] [Job 13] Job stopped due to filter errors; please consult the error_log file for details. D [29/Mar/2012:10:52:14 -0500] [Job 13] The following messages were recorded from 10:51:59 to 10:52:14 D [29/Mar/2012:10:52:14 -0500] [Job 13] Adding start banner page "none". D [29/Mar/2012:10:52:14 -0500] [Job 13] Queued on "Canon-MP630" by "tim". D [29/Mar/2012:10:52:14 -0500] [Job 13] Auto-typing file... D [29/Mar/2012:10:52:14 -0500] [Job 13] Request file type is application/postscript. D [29/Mar/2012:10:52:14 -0500] [Job 13] File of type application/postscript queued by "tim". D [29/Mar/2012:10:52:14 -0500] [Job 13] Adding end banner page "none". D [29/Mar/2012:10:52:14 -0500] [Job 13] job-sheets=none,none D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[0]="Canon-MP630" D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[1]="13" D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[2]="tim" D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[3]="Tennis_overhead" D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[4]="1" D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[5]="Duplex=None InputSlot=auto PageSize=Letter job-uuid=urn:uuid:b6996587-65a2-3e30-62e4-05942633ed99 job-originating-host-name=localhost time-at-creation=1333036319 time-at-processing=1333036319" D [29/Mar/2012:10:52:14 -0500] [Job 13] argv[6]="/var/spool/cups/d00013-001" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[0]="CUPS_CACHEDIR=/var/cache/cups" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[1]="CUPS_DATADIR=/usr/share/cups" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[4]="CUPS_REQUESTROOT=/var/spool/cups" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[5]="CUPS_SERVERBIN=/usr/lib/cups" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[6]="CUPS_SERVERROOT=/etc/cups" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[7]="CUPS_STATEDIR=/var/run/cups" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[8]="HOME=/var/spool/cups/tmp" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[10]="SERVER_ADMIN=root@tim-Z68A-D3-B3" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[11]="SOFTWARE=CUPS/1.5.2" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[12]="TMPDIR=/var/spool/cups/tmp" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[13]="USER=root" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[15]="CUPS_ENCRYPTION=IfRequested" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[16]="IPP_PORT=631" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[17]="CHARSET=utf-8" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[18]="LANG=en_US.UTF-8" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[19]="PPD=/etc/cups/ppd/Canon-MP630.ppd" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[20]="RIP_MAX_CACHE=128m" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[21]="CONTENT_TYPE=application/postscript" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[22]="DEVICE_URI=bjnp://192.168.1.123:8611" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[23]="PRINTER_INFO=Canon MP630" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[24]="PRINTER_LOCATION=Tommy other driver" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[25]="PRINTER=Canon-MP630" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[26]="PRINTER_STATE_REASONS=none" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[27]="CUPS_FILETYPE=document" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[28]="FINAL_CONTENT_TYPE=printer/Canon-MP630" D [29/Mar/2012:10:52:14 -0500] [Job 13] envp[29]="AUTH_I****" D [29/Mar/2012:10:52:14 -0500] [Job 13] Started filter /usr/lib/cups/filter/pstops (PID 3106) D [29/Mar/2012:10:52:14 -0500] [Job 13] Started filter /usr/lib/cups/filter/pstocanonij (PID 3107) D [29/Mar/2012:10:52:14 -0500] [Job 13] Started backend /usr/lib/cups/backend/bjnp (PID 3108) D [29/Mar/2012:10:52:14 -0500] [Job 13] Canon-MP630: error while loading shared libraries: libpopt.so.0: cannot open shared object file: No such file or directory D [29/Mar/2012:10:52:14 -0500] [Job 13] Page = 612x792; 18,14 to 594,784 D [29/Mar/2012:10:52:14 -0500] [Job 13] slow_collate=0, slow_duplex=0, slow_order=0 D [29/Mar/2012:10:52:14 -0500] [Job 13] Before copy_comments - %!PS-Adobe-3.0 D [29/Mar/2012:10:52:14 -0500] [Job 13] %!PS-Adobe-3.0 D [29/Mar/2012:10:52:14 -0500] [Job 13] %%BoundingBox: (atend) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%Creator: (LibreOffice 3.5) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%For: (tim) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%CreationDate: (2012-03-29 10:51:59 ) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%Title: (Tennis_overhead) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%LanguageLevel: 3 D [29/Mar/2012:10:52:14 -0500] [Job 13] %%DocumentData: Clean7Bit D [29/Mar/2012:10:52:14 -0500] [Job 13] %%Pages: (atend) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%Orientation: (atend) D [29/Mar/2012:10:52:14 -0500] [Job 13] %%PageOrder: Ascend D [29/Mar/2012:10:52:14 -0500] [Job 13] %%EndComments D [29/Mar/2012:10:52:14 -0500] [Job 13] Before copy_prolog - %%BeginProlog D [29/Mar/2012:10:52:14 -0500] [Job 13] Before copy_setup - %%BeginSetup D [29/Mar/2012:10:52:14 -0500] [Job 13] Attempting to connect to host 192.168.1.123 on port 8611 D [29/Mar/2012:10:52:14 -0500] [Job 13] STATE: +connecting-to-device D [29/Mar/2012:10:52:14 -0500] [Job 13] Before page loop - %%Page: 1 1 D [29/Mar/2012:10:52:14 -0500] [Job 13] Copying page 1... D [29/Mar/2012:10:52:14 -0500] [Job 13] pagew = 576.0, pagel = 769.3 D [29/Mar/2012:10:52:14 -0500] [Job 13] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792 D [29/Mar/2012:10:52:14 -0500] [Job 13] PageLeft = 18.1, PageRight = 594.1 D [29/Mar/2012:10:52:14 -0500] [Job 13] PageTop = 783.5, PageBottom = 14.2 D [29/Mar/2012:10:52:14 -0500] [Job 13] PageWidth = 612.0, PageLength = 792.0 D [29/Mar/2012:10:52:14 -0500] [Job 13] Wrote 1 pages... D [29/Mar/2012:10:52:14 -0500] [Job 13] STATE: -connecting-to-device D [29/Mar/2012:10:52:14 -0500] [Job 13] Connected to 192.168.1.123... D [29/Mar/2012:10:52:14 -0500] [Job 13] Connected to 192.168.1.123:8611 (IPv4)... D [29/Mar/2012:10:52:14 -0500] [Job 13] bjnp_backendRunLoop(print_fd=0, device_fd=5 D [29/Mar/2012:10:52:14 -0500] [Job 13] Ready to print. D [29/Mar/2012:10:52:14 -0500] [Job 13] End of messages D [29/Mar/2012:10:52:14 -0500] [Job 13] printer-state=3(idle) D [29/Mar/2012:10:52:14 -0500] [Job 13] printer-state-message="Ready to print." D [29/Mar/2012:10:52:14 -0500] [Job 13] printer-state-reasons=none E [29/Mar/2012:10:52:36 -0500] SSL shutdown failed: Error in the push function. 

```Tim

PS - Sorry, the code tags are not handling that output very well.

---

### Post by ratcheer on 2012-03-29
This looks like a solid clue. It came from the above CUPS error log output:

```
Canon-MP630: error while loading shared libraries: libpopt.so.0: cannot open shared object file: No such file or directory
```
Tim

---

### Post by ratcheer on 2012-03-29
Here is another clue from 2009:

[http://ubuntuforums.org/showthread.php?t=1204298](http://ubuntuforums.org/showthread.php?t=1204298)

I definitely have ia32-libs-multiarch installed, but something must be wrong with the installation.

Tim

---

### Post by ratcheer on 2012-03-29
**NEVER MIND**

This thread is moot because I gave up and reinstalled Precise to get rid of all the mess I installed to try to get the printer working. I guess I will just keep Oneiric for printing.

Tim

---

### Post by Baldrick_NZ on 2012-03-29
I hear your frustration Tim.

However, once you have re-installed precise, I would suggest checking out the Canon website itself for the drivers of your particular printer. Canon, from my understanding, are quite Linux friendly. Download the file, double click on it and it should bring up software centre to install. Install it, then restart your puter and it should then be there when you configure (set up) your printer.

For years I haven't been able to get my Brother to work, but it does now after following the above. Hopefully it'll work for you too.

---

### Post by PapaGary on 2012-03-29
Did you try [this]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")?

---

### Post by ratcheer on 2012-03-29
Thanks, @Baldrick_NZ. I do have the driver direct from Canon, but it is the same driver the script I referred to in the top post installs. But the script also finds and installs the many prerequisites for the driver, which is fairly old. It is a 32-bit driver and it requires a specific version of libpng, plus who knows what all else. I really don't want all that mess cluttering up my newly installed system, again.

But I do appreciate your tip.

Tim

---

### Post by ratcheer on 2012-03-29
I have seen that, @PapaGary, but I haven't tried it. Thank you for the tip.

Tim

---

### Post by PapaGary on 2012-03-29
> **ratcheer said:**
> I have seen that, @PapaGary, but I haven't tried it. Thank you for the tip.

Tim
Hey, you're welcome. It worked for me.

---

### Post by cmccauley on 2012-03-30
> **kurt18947 said:**
>  I have printer setups that have worked very well since at least 10.04 or before.  Printers still work for me (Brothers) but previously a print job started with 5 seconds of hitting 'print'.  Using Precise printing graphics like web pages it takes 45 seconds or longer for the printer to come alive.

I'm seeing the exact same thing with an old reliable HP printer. Works fine for the folks using 11.10, Windows 7 and Vista but for me, I need to go off and make a cup of tea to print a 3 page simple doc.


Chris

---

### Post by ratcheer on 2012-03-30
Here is what I got after I added that repository:

```
W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
tim@tim-Z68A-D3-B3:~$ sudo apt-get install cnijfilter-mp630series
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cnijfilter-mp630series
```

Tim

---

### Post by kurt18947 on 2012-03-30
> **cmccauley said:**
> I'm seeing the exact same thing with an old reliable HP printer. Works fine for the folks using 11.10, Windows 7 and Vista but for me, I need to go off and make a cup of tea to print a 3 page simple doc.


Chris

Chris, thank you for that.  I was wondering if it was a Precise problem or a Brother problem seeing as I only have Brother printers.  If you're seeing it with HP as well that points toward Precise.  I've alerted Brother to the problem but didn't ask for help because I feel it impractical to ask someone to support a moving target like Precise has been.  Now that beta 2 is out maybe printer manufacturers will take a look.

---

### Post by Flywaver on 2012-04-03
> **ratcheer said:**
> Here is what I got after I added that repository:

```
W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
tim@tim-Z68A-D3-B3:~$ sudo apt-get install cnijfilter-mp630series
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cnijfilter-mp630series
```

Tim

Same here!!

---

### Post by cariboo on 2012-04-03
> **kurt18947 said:**
> Chris, thank you for that.  I was wondering if it was a Precise problem or a Brother problem seeing as I only have Brother printers.  If you're seeing it with HP as well that points toward Precise.  I've alerted Brother to the problem but didn't ask for help because I feel it impractical to ask someone to support a moving target like Precise has been.  Now that beta 2 is out maybe printer manufacturers will take a look.

I've got a Brother HL-5250DN, networked laser printer and an Epson R340, that's connected to a WinXP system. I don't have any problems printing to either printer.

---

### Post by kurt18947 on 2012-04-04
Well, my situation is consistent anyway.  I have three Brother MFDs.

[LIST=1]
[*]MFC-7820N connected via wired network
[*]MFC-6490CW connected via USB
[*]MFC-J430W connected via USB
[/LIST]

Printing from FireFox 12 although 11 performs the same.  If I print a blank page, the printer comes alive within 5-10 seconds and spits out a blank page.  If I try to print 1 page from [www.weatherunderground.com]("http://www.weatherunderground.com"), it takes 40-50 seconds for the printer to come alive.  Thinking perhaps there's something about that particular web page, I did a search on Amazon and printed one page.  Same story, it took about 45 seconds to 'come alive' then printing was fine.  Once the printer comes alive,  printing is rapid as expected.  This behavior is pretty uniform regardless of model or connection.  Printer #1 takes perhaps 5 seconds longer, probably due to the network connection.  Wondering if it was a FireFox problem, I printed the same page to .pdf then opened the .pdf file and printed that.  Same story, printer came alive after about 40-45 seconds.  I tried printing to #3 a mostly text .docx file in Libre Office.  The printer came alive almost instantly and printed correctly.  I created 2 lines of text in Libre Office, saved as .html, opened in FireFox and printed it.  Speed was as I would expect.  There's something going on  with graphics though the weatherunderground page had very simple graphics and not many of those.

Printer 3 is connected to a machine that has Meerkat installed as well.  There are no printing issues with any apps so I'm thinking *something* is going on with Precise.  I have Mint12 on a laptop, I should see how that behaves.  Worth filing a bug?  I hesitate to blame Precise if it's a Brother issue.

---

### Post by cariboo on 2012-04-04
> **kurt18947 said:**
> Well, my situation is consistent anyway.  I have three Brother MFDs.

[LIST=1]
[*]MFC-7820N connected via wired network
[*]MFC-6490CW connected via USB
[*]MFC-J430W connected via USB
[/LIST]

Printing from FireFox 12 although 11 performs the same.  If I print a blank page, the printer comes alive within 5-10 seconds and spits out a blank page.  If I try to print 1 page from [www.weatherunderground.com]("http://www.weatherunderground.com"), it takes 40-50 seconds for the printer to come alive.  Thinking perhaps there's something about that particular web page, I did a search on Amazon and printed one page.  Same story, it took about 45 seconds to 'come alive' then printing was fine.  Once the printer comes alive,  printing is rapid as expected.  This behavior is pretty uniform regardless of model or connection.  Printer #1 takes perhaps 5 seconds longer, probably due to the network connection.  Wondering if it was a FireFox problem, I printed the same page to .pdf then opened the .pdf file and printed that.  Same story, printer came alive after about 40-45 seconds.  I tried printing to #3 a mostly text .docx file in Libre Office.  The printer came alive almost instantly and printed correctly.  I created 2 lines of text in Libre Office, saved as .html, opened in FireFox and printed it.  Speed was as I would expect.  There's something going on  with graphics though the weatherunderground page had very simple graphics and not many of those.

Printer 3 is connected to a machine that has Meerkat installed as well.  There are no printing issues with any apps so I'm thinking *something* is going on with Precise.  I have Mint12 on a laptop, I should see how that behaves.  Worth filing a bug?  I hesitate to blame Precise if it's a Brother issue.

How do your printers work when printing a pdf or an .odt document? I'm asking, as if it is only web pages that take a long time to print, then it may be a caching problem.

---

### Post by kurt18947 on 2012-04-05
> **cariboo907 said:**
> How do your printers work when printing a pdf or an .odt document? I'm asking, as if it is only web pages that take a long time to print, then it may be a caching problem.

It may have something to do with caching or spooling.  I notice intermittent disk activity while the machine "thinks about it".  Here might be some relevant info from dmesg:

```
[  345.815399] usblp0: removed
[  420.613551] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01F3
[  542.144755] usblp0: removed
[  618.944744] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01F3

```I have no clue what the above means.  Simple text files always print quickly, even .html files viewed in FireFox so I don't think it's a FireFox specific issue.  I did install the MFC-J430W in Mint12 and there were no printing issues either from USB or WiFi.  If I print to file a slow printing web page and print from a .pdf viewer,  printing is slow to start there as well.

---

### Post by pete04 on 2012-04-05
I was having the same issue since upgrading to 12.04, but I isolated it to printing directly from the browser (both Chrome Beta and Firefox). For  whatever reason, my print jobs were held up because of a lack of toner, even thought the printer had fresh toner cartridges. I uninstalled and reinstalled the printer and drivers a couple times, which worked temporarily.

Last night, Canonical pushed out a huge update (I noticed cups was among the 250+ packages). Printer works great. No problems printing from anything. I'd run those updates and see if it helps.

---

### Post by ratcheer on 2012-04-05
The new CUPS sounded promising, so I tried to add my Canon printer, again. It gave: CUPS server error: There was an error during the CUPS operation: 'client-error-not-possible'.

So, I am still lost.

Tim

---

### Post by ratcheer on 2012-04-05
I tried it again using ipp:// instead of bjnp://. This time, it successfully installed the driver and added the printer.

The bad news is that it still will not print. No activity whatsoever on the printer. The status message in CUPS is, "The printer is busy."

Tim

---

### Post by philinux on 2012-04-05
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/856028](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/856028)

Looks like it's jumped one version to precise now.

---

### Post by pete04 on 2012-04-05
I spoke too soon above. Printing issues from Chrome popped up again. Opera has the same issue -- printer is coming up as out of toner.

Firefox, though, works. Other direct printing operations seem fine (LibreOffice). It's weird.

---

### Post by dino99 on 2012-04-05
the latest updates push that one on my side:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/974329](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/974329)

---

### Post by akgrant on 2012-04-13
> **ratcheer said:**
> Here is what I got after I added that repository:

```
W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
tim@tim-Z68A-D3-B3:~$ sudo apt-get install cnijfilter-mp630series
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cnijfilter-mp630series
```

Tim

Ditto re the [http://ppa.launchpad.net/michael-gruz/canon](http://ppa.launchpad.net/michael-gruz/canon) packages (attempting to use a Canon iP4200).

Alistair

---

### Post by akgrant on 2012-04-14
> **akgrant said:**
> Ditto re the [http://ppa.launchpad.net/michael-gruz/canon](http://ppa.launchpad.net/michael-gruz/canon) packages (attempting to use a Canon iP4200).

Alistair

I installed the latest updates this morning, followed the excellent instructions at [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) (for reporting a problem), thought I'd better check to see if the printer was recognised before pressing the Send button, and my Canon iP4200 is now there.

Hopefully this update will help others as well.

Cheers,
Alistair

---

### Post by ratcheer on 2012-04-14
OT, but I am having a moderate war with this printer on Sabayon 8 Linux. I finally got the printer recognized and a print job actually makes it spin its machinery, some, but I still can't get anything to actually print.

Back to the regularly scheduled programming...

Tim

PS - LATER - I finally got the MP620 working in Sabayon. The final hurdle was to disable ufw, add the printer, and re-enable ufw. I came back to Precise and tried the same thing, but it still will not print.

---

### Post by ratcheer on 2012-04-24
I searched harder, this morning. There are tons of bugs that seem to be identical in Launchpad, but no solutions other than the generic suggestion of "contact Canon, get a better driver".

Do I just need to break down and buy an HP printer? This Canon printer is really very nice, and I really cannot afford a new printer. But, IMHO, Canon's support for Linux is terrible, although many seem to say the opposite.

My main question remains: **Why does it work in Oneiric but not in Precise?**

Tim

---

### Post by dino99 on 2012-04-24
maybe try this howto:

[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://doc.ubuntu-fr.org/imprimante_canon_pixma_mp_620](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://doc.ubuntu-fr.org/imprimante_canon_pixma_mp_620)

or this one:

[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://www.le-libriste.fr/ubuntu/gestion-des-imprimantes-canon-sous-ubuntu/](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://www.le-libriste.fr/ubuntu/gestion-des-imprimantes-canon-sous-ubuntu/)

---

### Post by Flywaver on 2012-04-24
> **dino99 said:**
> 
[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://www.le-libriste.fr/ubuntu/gestion-des-imprimantes-canon-sous-ubuntu/](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://www.le-libriste.fr/ubuntu/gestion-des-imprimantes-canon-sous-ubuntu/)

Thanks but unfortunately his PPA doesn't support precise :(

---

### Post by dino99 on 2012-04-24
> **Flywaver said:**
> Thanks but unfortunately his PPA doesn't support precise :(

its not mandatory, you still can try it (simply choose its highest release distro)

this one should do the trick:  ppa:michael-gruz/canon-2012

---

### Post by Flywaver on 2012-04-24
> **dino99 said:**
> its not mandatory, you still can try it (simply choose its highest release distro)

this one should do the trick:  ppa:michael-gruz/canon-2012

same issue with this PPA: > W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon-2012/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon-2012/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found


:(

---

### Post by ratcheer on 2012-04-24
@dino99 - Your first suggestion about using script mp620-630univ is what I have used several times. It is completely successful on Oneiric (and Natty before that) and it seems to be successful on Precise. The printer is installed, but when I try to actually print to it, it fails with message "pstocanonij failed". This is the error I can find many bug reports for on Launchpad. But, so far, I have not found a fix.

It will take me some time to investigate your second suggestion but I will try it.

Thank you for your advice.

Tim

---

### Post by codingman on 2012-04-24
There is a big update for Precise and it got some new printer things so I suggest doing the update in ubuntu update manager, they also got new wallpapers for Precise

---

### Post by ratcheer on 2012-04-24
Thanks, @codingman

Tim

---

### Post by ray field on 2012-04-26
this is driving me nuts! about two-thirds of a document will print, then just stops.

the Linux drivers for this MP530 have never been particularly good but at least they basically worked -- I guess it's a good thing I kept the old Lucid installation around, because that works fine.

I would switch to another inkjet as well, except I bought two cartridge packs for this thing, which of course is practically what a new one would cost. 

I don't really like to think about it, but in all my years of computing I've probably had to buy twice as many printers as desktops, and I shudder to think how much I've spent on ink & toner.

---

### Post by ratcheer on 2012-04-26
> **ray field said:**
> ... and I shudder to think how much I've spent on ink & toner.

You got that right!

Tim

---

### Post by SPK201 on 2012-04-26
Ok, easy fix:

skip if you already added the repo:```
[FONT=&quot]sudo add-apt-repository ppa:michael-gruz/canon[/FONT]

```Now, go to synaptic/muon and edit software repositories,

edit the two repos and change "precise" to "oneiric".

After that
```
sudo apt-get update
sudo apt-get install *canondriver*
```That did it for me.

---

