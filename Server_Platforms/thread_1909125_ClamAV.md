---
title: "ClamAV"
date: 2012-01-14
forum: Server Platforms
---

### Post by DanHorniblow on 2012-01-14
Hi, I recently setup my VPS with [this tutorial]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3").

But ISPconfig is telling me that ClamAV is outdated!?
```

Sat Jan 14 17:00:33 2012 -> ClamAV update process started at Sat Jan 14 17:00:33 2012
Sat Jan 14 17:00:33 2012 -> WARNING: Your ClamAV installation is OUTDATED!
Sat Jan 14 17:00:33 2012 -> WARNING: Local version: 0.96.5 Recommended version: 0.97.3
Sat Jan 14 17:00:33 2012 -> DON'T PANIC! Read http://www.clamav.net/support/faq
Sat Jan 14 17:00:33 2012 -> main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
Sat Jan 14 17:00:33 2012 -> daily.cld is up to date (version: 14308, sigs: 73235, f-level: 63, builder: guitar)
Sat Jan 14 17:00:33 2012 -> bytecode.cld is up to date (version: 161, sigs: 39, f-level: 63, builder: edwin)
```

How do I update ClamAV?

Cheers Dan

---

### Post by ajgreeny on 2012-01-14
Don't bother; it is more trouble that it's worth.

What is important is that the virus signatures are up to date, and they will be if freshclam is running as it should.

---

### Post by DanHorniblow on 2012-01-14
Ok then, how would I check if my virus signatures are up to date?

---

### Post by ajgreeny on 2012-01-15
If you installed clamav the usual way with apt-get, synaptic or software-centre, **freshclam** will have been installed as well, and will run every time you boot up, I think, to make sure the signatures are up to date.  Check that freshclam is installed, and maybe also that it is running, though I am not certain if it keeps running after it has done the update.

My memories of clamav are too old to be certain about this sort of detail, and I don't bother with any virus checker any more as I don't have windows to worry about.

---

### Post by melc_sokat on 2012-01-15
Originally Posted by Pidster  
Had the same problem.. the daemon was running in processes.

had to ---> sudo /etc/init.d/clamav-freshclam stop

then sudo freshclam -v

and it worked for me.

then restart the daemon with

sudo /etc/init.d/clamav-freshclam start

after it was restarted i was able to run the freshclam -v command with no more porblems. thinking it might have been locked up..??

---

### Post by Vegan on 2012-01-15
For those who do not use security, do not be too smug.

Malware frequently is found hiding on Linux servers

---

