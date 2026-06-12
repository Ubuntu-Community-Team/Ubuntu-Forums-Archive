---
title: "ransomeware, browser hijack"
date: 2014-12-26
forum: Security
---

### Post by crip720 on 2014-12-26
This morning I was hit with ransomeware on the chromium browser, private window.  I am not certain which ransomeware it was, but it seem to be a browser hijack since it happen on a reloading of the page.  I restarted the ubuntu 14.04 OS, and it seems to be okay.  I shutdown and am now on another Ubuntu partition.  Question; how can I tell if the system is clean, do have Bitdefender on it, can install rootkit finder on it.  Can install clamvirus program on the clean Ubuntu partition, or try installing Bitdefender which would take longer to get working.  Ubuntu 14.04 64bit is up to date.  Any sugustions would be apprecated.  Thank you.  Colin.

---

### Post by westie457 on 2014-12-26
The only time I had a ransomware page appear the easiest way to remove it is to empty the cache. This can be done either in the settings page of chromium or look inside the hidden cache folder in the file-browser.

---

### Post by crip720 on 2014-12-26
I am more interested in making sure it is not on the OS.  I think by restrarting, it clear out, but want to make sure it did leave anything behind.  Will clear cache when I start the OS again.  I was not root at the time.

---

### Post by westie457 on 2014-12-26
Provided you were not running as root the chances of anything being written outside of your /Home folder are slim, you would need to give your password for anything to be written.
Have never used Bitdefender so cannot comment on its effectiveness at finding malware.
Clamav will only find threats aimed at Windows OSes.
A rootkit finder - eg rkhunter will throw up a lot of false positives, very nearly all of them will be normal system files and processes.

Feel free to try a rootkit finder and post the results here so we can check.

---

### Post by sammiev on 2014-12-26
I scan once a week or every other week with Bitdefender and have found malware in the past. 

Scans usually take just a min or two.

---

### Post by nomenkultur on 2014-12-27
those ransomeware sites tend to work by dropping scripts or executables, and they only work in windows...

 windows and android that is, in android it's a pain

---

### Post by crip720 on 2014-12-27
Hi, system seems to fine.  Ran a full scan with Bitdefender and it did seem to find a couple of nasties. It name them; Gen: Variant.Kazy.268129, and Gen: Variant.Symmi.40340. Quarantine both of them.  It might be possible it found them in the Windows partition since I had it scan the file system, but I did a scan of Windows from Ubuntu a few weeks ago and it only found a couple of trojans.  I had Bitdefender quarantine them at the time but they did show up again this time in the Bitfender quarantine file.  I can supply a snapshot of the Bitdefender summary if you need it.  Thanks, Colin.

---

### Post by sammiev on 2014-12-28
> **crip720 said:**
> Hi, system seems to fine.  Ran a full scan with Bitdefender and it did seem to find a couple of nasties. It name them; Gen: Variant.Kazy.268129, and Gen: Variant.Symmi.40340. Quarantine both of them.  It might be possible it found them in the Windows partition since I had it scan the file system, but I did a scan of Windows from Ubuntu a few weeks ago and it only found a couple of trojans.  I had Bitdefender quarantine them at the time but they did show up again this time in the Bitfender quarantine file.  I can supply a snapshot of the Bitdefender summary if you need it.  Thanks, Colin.

I do not have Widows on my computer so anything it finds is usually in FF or any other browser.

---

### Post by fugu2 on 2015-01-07
FYI, it has been my experience that many AV's simply don't work as well as we would like them too.  As an example I did a web search for "keylogger" and found some old c code that had a functioning keylogger for a windows computer, compiled it with mingw, made sure that it worked and then tested to see if several AV's could detect it and to my surprise and had a harder time getting the AV's to detect it then to not detect it. That c code was VERY old too. So be very careful and don't run untrusted code on your computer.

---

