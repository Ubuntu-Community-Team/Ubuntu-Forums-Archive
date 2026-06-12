---
title: "ClamAV question"
date: 2017-02-22
forum: Security
---

### Post by ferfykins on 2017-02-22
How to scan entire hard-drive with clamav? and does that automatically remove the malware? if not, how do i remove the malware?

---

### Post by RobGoss on 2017-02-22
I'm not a regular user for** Clamav** but I do have it installed, from what I know about this program you can pick and choose which part of your system you want to scan, If you choose your **Home** directory it would be the best way in my option for a full system scan, seeing this is were just about all your files are stored

If the scan detects anything on your machine you can **Quarantine** it for removel

---

### Post by Perfect Storm on 2017-02-22
But be aware of false positives before meddling with them.

And clamAV is slow as bananabread

---

### Post by ubunticus on 2017-02-22
You can find some useful info and command lines at:[https://www.unixmen.com/installing-scanning-clamav-ubuntu-14-04-linux/](https://www.unixmen.com/installing-scanning-clamav-ubuntu-14-04-linux/)

---

### Post by SeijiSensei on 2017-02-22
You can scan the entire drive with
```
sudo clamscan -r -i /
```
That will produce a list of only those files ClamAV thinks are infected.  I'd be wary about removing anything that isn't obviously Windows malware.  The probability of the Linux files on your machine having malware in them is close to zero, especially if everything installed came from the Ubuntu repositories.

---

### Post by cariboo on 2017-02-22
Moved to Security.

---

### Post by ferfykins on 2017-02-22
----------- SCAN SUMMARY -----------
Known viruses: 5870797
Engine version: 0.99.2
Scanned directories: 70613
Scanned files: 258382
Infected files: 4
Total errors: 27129
Data scanned: 10278.91 MB
Data read: 10299.28 MB (ratio 1.00:1)
Time: 1532.564 sec (25 m 32 s)




result from using : [COLOR=#000000][FONT=&quot]sudo clamscan -r -i /


i take it, it doesn't automatically remove the malware?[/FONT][/COLOR]

---

### Post by cariboo on 2017-02-23
How do you know the files are infected, and not just false positives?

---

### Post by ferfykins on 2017-02-23
> **cariboo said:**
> How do you know the files are infected, and not just false positives? 


I don't lol, i'm nub at linux

---

### Post by Perfect Storm on 2017-02-23
Can you post which files it says is infected.

---

### Post by ferfykins on 2017-02-23
> **Artificial Intelligence said:**
> Can you post which files it says is infected.

 I posted all the output it showed, idk how to check which files is infected....

---

### Post by Perfect Storm on 2017-02-23
```
sudo clamscan -r -i --log=clamlogfile.txt /
```

---

### Post by RobGoss on 2017-02-23
> **ferfykins said:**
> I don't lol, i'm nub at linux

It seems far fetched to worry about something you're not to sure of. Linux is pretty safe and as long as I've been using it I never had any viruses what so ever, I'm not saying it's not possible just that it is unlikely

---

### Post by SeijiSensei on 2017-02-23
According to the [man page for clamscan]("https://linux.die.net/man/1/clamscan"), 
> -i, --infected
Only print infected files.

The summary you posted showed four infected files.  Are you sure it didn't list those four files, too?  

Did you try this method from our "Antique" moderator which tells clamscan to write a log file?
> **Artificial Intelligence said:**
> ```
sudo clamscan -r -i --log=clamlogfile.txt /
```
Then examine clamlogfile.txt for the flagged files.

> **RobGoss said:**
> It seems far fetched to worry about something you're not to sure of. Linux is pretty safe and as long gone as I've been using it never had and viruses what so ever
That's my experience as well, and I've been using desktop flavors of Linux for decades.

---

### Post by lisati on 2017-02-23
> **RobGoss said:**
> It seems far fetched to worry about something you're not to sure of. Linux is pretty safe and as long as I've been using it I never had any viruses what so ever, I'm not saying it's not possible just that it is unlikely

Agreed. As others have found, most of the problems I've experienced with Ubuntu have been because of carelessness or not fully understanding what I've been doing. In the 9 years I've been using some flavour of Ubuntu, I don't recall encountering a problem with my setup that was directly attributable to something nasty I'd picked up somewhere.

---

### Post by Habitual on 2017-02-23
Don't forget to scan the nut behind the keyboard.

---

