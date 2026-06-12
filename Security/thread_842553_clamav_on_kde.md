---
title: "clamav on kde"
date: 2008-06-27
forum: Security
---

### Post by MisterP on 2008-06-27
I am using clamav on kde, so I have been using klamav.  I must admit, I don't particularly like klamav.  I have been wondering if I could get rid of klamav and just use the clamav front end instead.  I haven't tried to do anything yet.  I was wondering if anyone had any thoughts.

Alternatively, what does anyone think about avast?  Is it any good?  Does it scan emails?

---

### Post by sydbat on 2008-06-27
I use Avast. No, it does not scan emails (at least in the 64bit version). But I scan my email folder a couple of times a week to make sure my Windows friends don't get something from me.

---

### Post by Pjotr123 on 2008-06-27
Tip:read this about security in Ubuntu:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by perspectoff on 2010-09-25
> **Pjotr123 said:**
> Tip:read this about security in Ubuntu:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

These pages have a lot of disinformation. I disagree with many of the recommendations there.

Although hosted on Googlepages, they are not affiliated with Google in any way. They are the private pages of a Dutch individual.

---

### Post by SeijiSensei on 2010-09-25
You can run clamscan from the command prompt:

sudo clamscan /path/to/target/directory

You'll need to use sudo so clamscan will be able to scan all the directories in the target regardless of ownerships or permissions.  Depending on how many files and directories are involved, this report can be pretty large.  Using the command

sudo clamscan /path/to/target/directory | grep FOUND

will only display the lines corresponding to found viruses.

If you want to automate this process, I recommend the following approach.  Create a file with an editor like this:

sudo nano /usr/local/sbin/clamscanner

Then enter the following text into the file, replacing "/path/to/target/directory" with the one you want to scan (e.g., "/" or "/home") and you@example.com with an email address to which the reports will be sent.

```

#!/bin/sh
TARGET=/path/to/target/directory
NOTIFY=you@example.com

clamscan $TARGET 2>&1 | grep FOUND | mail -s "Clamscan report for $TARGET" $NOTIFY

```

Save the file, then type the following commands
sudo chmod u+x /usr/local/sbin/clamscanner
sudo cd /etc/cron.daily
sudo ln -s /usr/local/sbin/clamscanner

These make the script executable by the root user and set it up to run automatically every night.  After it scans TARGET, it will mail a report listing any viruses found to the NOTIFY address.

You'll probably need to install "bsd-mailx" to enable the command-line mail client; "sudo apt-get install bsd-mailx" should do the trick.

If you want to test this and make sure it's working properly, you should download the "eicar.com" file from [here](http://www.eicar.org/download/eicar.com).  This is a dummy virus file that all scanners recognize for testing purposes.  Put it in the target directory, and you should see a line like this when you run clamscan:

/tmp/eicar.com: Eicar-Test-Signature FOUND

---

### Post by uRock on 2010-09-25
Moved to Security Discussions sub-forum.

---

### Post by beew on 2010-09-25
ClamAV  is a sorry excuse for an AV , it is slow and uses up a lot of your CPU resources and has absymal detection rate, I would  either forget about the idea of installing an AV all together,--which many do,--or get a real one like bitdefender for Linux (google bitdefender for Unice) or Avast. 

[http://en.wikipedia.org/wiki/Clam_AntiVirus](http://en.wikipedia.org/wiki/Clam_AntiVirus)

---

### Post by OpSecShellshock on 2010-09-25
> **beew said:**
> ClamAV  is a sorry excuse for an AV , it is slow and uses up a lot of your CPU resources and has absymal detection rate, I would  either forget about the idea of installing an AV all together,--which many do,--or get a real one like bitdefender for Linux (google bitdefender for Unice) or Avast. 

[http://en.wikipedia.org/wiki/Clam_AntiVirus](http://en.wikipedia.org/wiki/Clam_AntiVirus)


In my experience, the same is true of all AV scanners. In any case, they're just scanning for Windows malware for the most part. If you want to run a scan, there's probably little need to scan anything outside of the home directory.

---

