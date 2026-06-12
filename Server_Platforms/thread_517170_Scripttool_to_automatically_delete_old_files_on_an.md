---
title: "Script/tool to automatically delete old files on an FTP server?"
date: 2007-08-04
forum: Server Platforms
---

### Post by MJN on 2007-08-04
I use the ZoneMinder CCTV system to automatically detect, and capture, motion when I'm away from my home. In case of a burglary the server itself is obviously at risk and hence I have it configured to automatically upload recorded events to an off-site FTP server (to which I only have FTP access to, no low-level access available).

Whilst I have the configuration set to only upload events greater than 5 seconds in length there are still occasions when I get false alarms uploaded and so my account gradually gets full (it's limited to 1GB).

I am therefore interested in finding a solution to this, perhaps in the form of a script that can log in to my FTP account, check the available space, and delete old files if a certain threshold is exceeded. Alternatively, it could obtain a list of files and delete any older than a specific date (age).

Sadly my scripting skills are somewhat limited and feel this task, particularly the automated FTP sessions, would be too steep a learning curve for me to feasibly climb.

Hence, has anyone written such a script/tool or perhaps is aware of something that works along these lines? 

Mathew

P.S. Thinking outside the box, is anyone aware of any low-cost storage services that allow rsync access? This way I could perform the date matching/processing locally and simply sync the offsite storage to it.

---

### Post by koenn on 2007-08-04
the ftp command in ms-dos/windows had an -s option to run an automated ftp session from a script. Basically, you'd add, line by line, everyting you'd type in during an interactive session (including username and password). 
although you can delete multiple files that way, checking for disk free space or comparing dates would be quite hard, ftp servers apparently don't provide for that. 

What you could try is mount your space on the ftp server to your local filesystem. 
check this : 
[http://ftpfs.sourceforge.net/usage.html](http://ftpfs.sourceforge.net/usage.html)

Chances are you could just work directly on the mount point, with any shell command or control structure available  to do your processing. Or you could rsync it agains a model directory.

---

### Post by MJN on 2007-08-04
The semi-automated interactive -s function sounds like what I'd otherwise need. My concern was that my rudimentary scripting skills would not cover error conditions and semi-intelligent 'what ifs' whereas I was hoping someone else's might! Furthermore, it still requires the parsing of a directory listing and other functional bits which I don't feel confident learning all at once!

Mounting an FTP source sounds interesting though - I could probably cope with that! I can understand why that page regularly caveats the bandwidth issue! I'll give it a go and see if it holds up.

If anyone else has any ideas or pointers please do keep them coming.

I'm surprised a solution doesn't already exist, or at least one that's easy to find - I thought perhaps this might be a common potential requirement for anyone that backs up over FTP.

Mathew

---

### Post by nix4me on 2007-08-04
lftp can probably do that.  Try looking through the man pages for lftp.

nix4me

---

### Post by MJN on 2007-08-04
Thank you both for your ideas... they've been really helpful.

I tried the ftpfs mounting (via LUFS) and seemed to have some success... I built the module, installed it, and all seemed hunkydory and working quite well despite my limited upload bandwidth. Then I got a Segmentation Fault and whole machine went down... that'll teach me to experiement in a live environment!

So, I've removed it now and will continue with some higher-level approaches.

LFTP looks interesting... I'll experiment further. One handy function I've already found is that its rm command can remove empty directories and use wildcards - this in itself is quite useful as that was holding me back in FTP.

Thanks again,

Mathew

---

