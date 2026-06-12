---
title: "Undetected DVD disc"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Son Of Nova on 2012-04-13
I've just realized I've put this in the wrong forum :/

Hi, I want oto back up my files to clean install ubuntu, but ubuntu isn't recognising my blank DVD+RW. It recognises and plays back DVD movies. I know there compatibility issues across different DVD technologies, but I'm not sure how it would work with this drive.

Here is the terminal output for it;

    *-cdrom:1
                description: DVD-RAM writer
                product: DVDRAM GSA-4082B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: A206
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc


Should ubuntu be able to write to the disc?

---

### Post by dino99 on 2012-04-13
is the reader detected correctly ?

sudo lshw > hardware.txt

or is it a software issue ?

Look at logs : .xsession-errors (inside /home, ctrl+h to unhide it) & /var/log/

---

