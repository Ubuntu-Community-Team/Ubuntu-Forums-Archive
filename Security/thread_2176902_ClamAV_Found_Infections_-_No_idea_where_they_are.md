---
title: "ClamAV Found Infections - No idea where they are"
date: 2013-09-26
forum: Security
---

### Post by arkan01d on 2013-09-26
I loaded up Chrome today and it tells me there is a sync error and I have to sign in again. I type my email and password 5 times and it just keeps saying there's a sync error. However gmail, google+, and youtube says I'm signed in. Then I tried to load Capsized game from Steam. The program window pops up for a few seconds then closes. Steam will not close now because it says I have Capsized still running. I opened System Monitor and closed the Capsized process, but Steam persists in saying it can not close until Capsized is closed.

I decided to run a clamav to check. I ran```
(arkan01d) $ sudo freshclam[sudo] password for arkan01d: 
ClamAV update process started at Thu Sep 26 12:23:43 2013
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.97.8 Recommended version: 0.98
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cld is up to date (version: 55, sigs: 2424225, f-level: 60, builder: neo)
daily.cld is up to date (version: 17901, sigs: 378613, f-level: 63, builder: neo)
bytecode.cld is up to date (version: 226, sigs: 43, f-level: 63, builder: neo)
```

Apparently it needs to be updated, which I thought freshclam was supposed to do. I read all over [http://www.clamav.net](http://www.clamav.net) and search the forums on the web. They all say just run that command. "[I]OKAY, so I guess it's as updated as it's supposed to be then."
[/I]
Then I run```
 SUDO (arkan01dclamscan -r /home

``` and get ```
----------- SCAN SUMMARY -----------
Known viruses: 2797577
Engine version: 0.97.8
Scanned directories: 7650
Scanned files: 144914
Infected files: 6
Data scanned: 28470.53 MB
Data read: 98082.58 MB (ratio 0.29:1)
Time: 1849.252 sec (30 m 49 s)
```

So where are these infected files? I can not find documentation telling me where to find them. 'clamscan --help' doesn't help me. I tried 'man clamscan' which just tells you that you could get an infected result, but not what or how to handle it. Even the site does not say what to do if you actually get a virus. I could use the remove flag, but I don't want to delete things if they are not actually viruses. How do I know what files are infected? How can I tell if they are false positives?

---

### Post by unspawn on 2013-09-26
man clamscan tells you to add the "--verbose --infected --stdout" switches?

---

### Post by arkan01d on 2013-09-26
I did see that. I just didn't want to take another hour doing another scan. Especially since freshclam isn't updating already.

---

### Post by unspawn on 2013-09-26
> **arkan01d said:**
> I did see that. I just didn't want to take another hour doing another scan. 
It's your choice to make informed decisions and use your system to its full potential. 
Or not.


> **arkan01d said:**
> Especially since freshclam isn't updating already.
Set it as a cron job in /etc/cron.daily/ if it wasn't set up that way already.

---

### Post by arkan01d on 2013-09-26
> **unspawn said:**
> It's your choice to make informed decisions and use your system to its full potential. 
Or not.
Ouch... I'm less than a month into using Ubuntu. Sorry if my ignorance offends. I didn't think my decision was totally uninformed. I followed a few guides, even the one on ClamAV's site says to do what I did. I was supposing there must have been some sort of output file somewhere. Seems strange to do a scan of a directory and then just tell you, "Yup, you got a bug," without any real information. There isn't even a guide that I can find as to what to do when you have a virus, other than using the delete when they are found scan option. After spending the better part of 4 hours working on this alone I thought I would reach out for assistance.  The only way to know if you are using your system to it's full potential is to seek the knowledge and once that fails you ask somebody ;)

---

### Post by unspawn on 2013-09-27
...right. And that's why I said "go use these --flags to find out", to which you basically responded "no, I won't do that". See what I mean?

---

### Post by SeijiSensei on 2013-09-27
Do you have a mounted Windows partition?  I'd guess the infected files are in there.  You can limit clamscan to specific directories, so try scanning just the Windows partition with verbose settings and see how many infections it picks up there.

---

