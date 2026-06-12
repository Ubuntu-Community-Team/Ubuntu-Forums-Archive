---
title: "ClamAV / KlamAV"
date: 2008-10-31
forum: Security
---

### Post by GNUway Tech on 2008-10-31
I've been using ClamAV with the KlamAV frontend for quite some time now, and I've always been satisfied. For some reason, since I switched to Kubuntu, I find that it doesn't operate like it used to.

For starters, it doesn't give me the option to update the database from the update screen. It just always says it is updating. On Hardy Heron, though, it still gave me a list of files. But, now that I've updated to 8.10, it won't even give me that in KlamAV.

Is there something I'm not doing right, or is there a better alternative for AntiVirus software?????

---

### Post by nubdora on 2008-10-31
Nevermind.

---

### Post by GNUway Tech on 2008-10-31
It's been doing this to me for the last few months now, telling me it's constantly updating itself. I just switched to 8.10 within the last 24 hours, and now it's not even loading a database.

---

### Post by cariboo on 2008-11-01
Have you tried updating in a terminal by using:

```
sudo freshclam
```

I don't believe in using a windows anti-virus program in linux, as it is really just a waste of time.

Jim

---

### Post by GNUway Tech on 2008-11-01
I just tried the command.

It said the list was up to date, but it still won't give me a list in the virus browser in Klamav.

---

### Post by GNUway Tech on 2008-11-02
Now, I'm not even seeing ClamAV or KlamAV in Adept. All I'm seeing is ClamTk. Is Ubuntu not supporting ClamAV anymore??????? If not, are there any other free alternatives for AntiVirus software???????

---

### Post by GNUway Tech on 2008-11-12
Okay, so I finally installed ClamTk just to see if I could get it to work for me. As soon as I first opened it, I got a message that said some distros don't automatically configure freshclam for updates, and I should do that myself. I know freshclam is installed, because it installed with ClamTk. How do I configure it????????

---

### Post by GNUway Tech on 2008-12-03
With all the recent Adept updates for ClamAv, I figured it might be safe to give KlamAv another try. I installed it and tried to update the virus database from it. I got an error message that said "Config file error."

Does anybody have any idea how to correct this so it will work???? I really don't see how I should have to learn to use ClamAv from the command line if there is a GUI alternative available, especially one as simplified and easy to use as KlamAv. I already tried ClamTk, but I can't get it to work either, and I would rather use KlamAv.

If there's just no way to make either of these work, is there another free open source anti-virus software that I can use??????

---

### Post by cariboo on 2008-12-03
You can get AVG here:

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

and Avast from here:

[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Jim

---

