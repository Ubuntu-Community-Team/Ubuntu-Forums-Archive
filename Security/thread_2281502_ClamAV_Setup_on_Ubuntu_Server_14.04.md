---
title: "ClamAV Setup on Ubuntu Server 14.04"
date: 2015-06-07
forum: Security
---

### Post by stressed on 2015-06-07
Hello...

I would like to install ClamAV on my Ubuntu 14.04 server and set it up to download updates and run scans automagically.  I've done quite a bit of searching, read much, and can't seem to locate any good examples on how to accomplish this.

This is what I would like ClamAV to do:
1)  Let's say at some defined time, maybe 12:00am, download the latest definition updates and install.
2)  After the definition updates are downloaded and installed, run a scan against my entire server.
3)  If there is anything found, report it and maybe quarantine it.

Does this sound like something that can be done?  I'm not a Linux guru by any means.  I can get around the OS but I would need some instructions on how to accomplish this if doable.

Any suggestions would be very helpful.  Thank you!

---

### Post by SeijiSensei on 2015-06-08
First, unless your system has a Windows partition that you write to from Windows, it is very unlikely ClamAV will ever detect any malware on your system.  It's probably worth a few minutes of your time reading this: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).  I've used Linux for two decades and never had a piece of malware on my machines.  I use ClamAV in conjunction with [MailScanner]("http://www.mailscanner.info/") to scan incoming mail for viruses on both my own mail servers and those of my clients.  All the malware it detects target Windows users.

If you still want to use ClamAV, install it with "sudo apt-get install clamav".  The main scanner program is called "clamscan" while the database updater is called "freshclam".  After installation, run freshclam from the prompt with "sudo freshclam".  It will report downloading the virus definition files.  To scan a directory on your system use
```
sudo clamscan -r /path/to/directory
```
I suggest starting with /home or with any Windows partitions on your drive.  Since most files will be clean, you can limit the output to unusual cases with 
```
sudo clamscan -r /home | grep -v OK
```
which will report only lines that don't include the "OK" entry at the end.  Probably all or nearly all of those will be benign reports of "Symbolic link" and "Empty file".

I scanned my /home directory just now and got these results:
```

----------- SCAN SUMMARY -----------
Known viruses: 3832462
Engine version: 0.98.7
Scanned directories: 1248
Scanned files: 14376
Infected files: 0
Data scanned: 1732.46 MB
Data read: 85787.17 MB (ratio 0.02:1)
Time: 146.366 sec (2 m 26 s)

```

If you want to automate this process, you'll need to run it from cron.  Read [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) for details.

---

### Post by stressed on 2015-06-08
Hi SeijiSensei...

Thank you for the reply.  I appreciate your time.  The biggest reason that I wanted to automate ClamAV is because I was going to setup an instance of ownCloud for my family.  I would prefer to set it and forget it until it needs upgraded.  Of course my family isn't as conscious about security as I am.  Worst case scenario, one of my family members uploads a file that is infected and has unintended consequences on my server.  In the past, I've seen malware that had the same effect on Linux as it did on Windows; must have been written for both.  Anyway, my thoughts were to have ClamAV running in the background, in memory, at all times scanning incoming files as well as what I originally posted.  I was just hoping that I wasn't asking for something that couldn't be done.  

I've never worked with Cron before.  If it's easy, I should be ok, however, if there is an elevated level of effort with it, I may be posting back.

Thank you.

---

### Post by SeijiSensei on 2015-06-08
Take a look at [http://www.webhostingtalk.com/showthread.php?t=1228322](http://www.webhostingtalk.com/showthread.php?t=1228322)

This shows how to set up a cron job that checks a directory for new files every five minutes, hands them to clamscan, and automatically deletes any infected files. You'll notice that method uses clam**d**scan.  There is a "daemonized" version of ClamAV that includes a daemon called [clamd]("http://linux.die.net/man/8/clamd") and a client called clamdscan.  Clamd is often used by hosting providers especially if they are also scanning mail.  In your case I'd just replace "clamdscan" with "clamscan" in the command.

Of course, the better solution is for your family members to have antivirus programs installed on their machines so the files never reach your server at all.

The only kinds of malware I've seen that runs on both Windows and Linux are browser exploits.  The last one I encountered was "Antivirus 2010" which was surreptitiously introduced into an advertisement at the New York Times site some years back.  It invoked a Javascript when you closed your browser that downloaded a page and made it look like Windows was scanning your hard drive for viruses and finding dozens of them.  The intent was to trick the mark into buying a phony antivirus solution.  As a Linux user, I could only laugh when it claimed to be scanning my C: drive and finding infected .dll files!  This wasn't a virus, though, and it wouldn't have been detected by ClamAV.  

After that I expanded my anti-advertising tools by adding Ghostery to Firefox to control third-party scripts.  NoScript is a possibility as well, though I found it too intrusive.  Of course, I've been running the AdBlock extension for Firefox for years (now using AdBlock Edge).

---

### Post by stressed on 2015-06-08
Thanks for the reply again.  I'll get to digging in to see what I can come up with.

By the way, should I create the cron job in root or my user account?  If so, how would I do that?

---

### Post by SeijiSensei on 2015-06-09
You want to create a root crontab.  You can use the crontab command or edit the files directly as root with sudo.  If you use crontab, you can select an editor when you run the command like this:
```
sudo crontab -e
```
On my 14.04 machine it will offer a menu of editing options depending on what is installed.
```

sudo] password for seiji: 
no crontab for root - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/jed
  4. /usr/bin/vim.tiny

Choose 1-4 [2]:

```
I use [jed]("http://www.jedsoft.org/jed"), an Emacs clone, so having installed it, it appears in my list.

---

### Post by stressed on 2015-06-09
Seeing that I can't find a way to have ClamAV running all the time, basically running so that when someone drops a file on the server that file gets scanned automatically right then, and if infected, that file will get removed immediately, I've come to this:

1)  Update ClamAV at 12:30am, 7 days a week, quietly.
2)  Scan every 2 hours, 7 days a week, recurse the entire drive, remove infected files and print only infected files to an email and send with "ownCloud Antivirus Report" as the subject line.

Does the below look correct for this?

sudo crontab -e

30  00  *  *  0-6  freshclam --quiet
*  /2  *  *  0-6  clamscan -r --remove -i / 2>/dev/null | sendmail [EMAIL="my@email.com"]my@email.com[/EMAIL] "ownCloud Antivirus Report"

Of course I'm sure I'll have to setup sendmail beforehand as well.  Seems I'm going to have to figure out a way to get sendmail to work with gmail.
If I do it this way, do I have to do anything with the clamav-daemon?[EMAIL="my@email.com"]

[/EMAIL]

---

### Post by SeijiSensei on 2015-06-09
No, you don't need the daemon if you just run clamscan.

I would run freshclam without the --quiet option and send the result to a log:
```
30 00 * * 0-6 freshclam > /var/log/freshclam 2>&1
```

Also there should not be a space between the star and the slash in "*/2".

You might not need to do anything special to get sendmail to send to your address.  It depends on where this server is located.  ISPs often block outbound mail on residential connections, but if this is a server located directly on the Internet, sendmail will use DNS to locate the server that handles mail for "email.com" and send the mail there.  I'd make sure that your server has consistent forward and reverse DNS lookups because some mail providers will reject mail if the the host=>IP and IP=>host records do not match.  If you have a domain, give the server an A record in your DNS, then ask your provider to configure the reverse entry to match.

---

### Post by stressed on 2015-06-10
I'm just wondering why you might send the freshclam update to a log?  Is it because you want to see what definitions have been updated or that an update actually occurred?

Thanks for pointing out no space between the * and the /2; it does seem kind of odd to me that there would not be a space there though.  I'm just wondering, how many spaces are you supposed to put between the numbers/stars?  Is one space fine or should there be two spaces?  It doesn't look as though a tab is used.

I appreciate all your help so far.  I've actually learned quite a bit, more than what I expected.

---

### Post by SeijiSensei on 2015-06-11
The "*/2" construct is no different than a single number or a single star.  It represents "minutes divisible by two."

There can be an arbitrary amount of space between fields in nearly all configuration files.  A tab character (^Q^I) is treated as a space.

Yes, I would log freshclam to make sure it's working properly.  You may also see warnings there about needing to update ClamAV to a more recent version. Ubuntu doesn't always keep up because the ClamAV binary is sometimes modified to handle new forms of malware.

Basically I log everything that is automated just in case.

---

### Post by Habitual on 2015-06-11
> **SeijiSensei said:**
> 
```
sudo clamscan -r /home | grep -v OK
```
which will report only lines that don't include the "OK" entry at the end. 

I always use:
```
clamscan -ir /path/to/scan
```
for just the summary at the end.

Have a Great Day!

---

### Post by SeijiSensei on 2015-06-11
> **Habitual said:**
> I always use:
```
clamscan -ir /path/to/scan
```
for just the summary at the end.

Does that list the infected files, too?  Or do you have to run clamscan again to list them?

---

### Post by stressed on 2015-06-11
Oooops, I think my clamscan construct should be like this then, correct?  I'll begin logging like you instead of email:
*  */12  *  *  *  clamscan -r --remove -i / > /var/log/clamscan 2>&1

---

