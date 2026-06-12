---
title: "No more printing from HP Officejet 8600 Plus on 17.10"
date: 2017-09-19
forum: Ubuntu Development Version
---

### Post by Jacobonbuntu on 2017-09-19
Since last update on 17.10, including the new Gnome-control-center, my Officejet 8600 Plus stopped working. I removed the non-working printer from the printer settings window and added it again in several ways, hplip GUI, the settings panel, the web setup, no avail. It is a network attached setup, but it seems irrelevant; I also tried usb connection with the same result. By default, the printer appears as "printer without driver", but the model HP 8600 shows correctly.
The symptoms: The print job seems to start immediately, but almost immediately "Printjob stopped" appears in the notification. The job then stays forever in queue. Another interesting part is that the "search for preferred drivers" gives no result. Manually setting the driver that *should* work gives the same result.

Since both the cups driver and hplip/toolbox are the same version as 17.04 (where it worked fine) I kind of suspect the new Gnome-control-center, which shows more exciting issues on my system, but since printing isn't my major subject, I am not sure.

Ubuntu Budgie 17.10 Beta1 / cups 2.2.4/7, hplip 3.17.22

---

### Post by jsjpandey on 2017-09-20
Take a look at syslog with following command while printing and post the output
*tail -f /var/log/syslog*

---

### Post by Jacobonbuntu on 2017-09-20
Thanks! unfortunately only a few lines that I can directly connect to some testing I am doing. Not a single line about printing.

To be concrete:

    ```
Sep 20 08:41:58 jacob-System-Product-Name budgie-panel.desktop[1899]: X Error of failed request:  BadWindow (invalid Window parameter)
    Sep 20 08:41:58 jacob-System-Product-Name budgie-panel.desktop[1899]:   Major opcode of failed request:  21 (X_ListProperties)
    Sep 20 08:41:58 jacob-System-Product-Name budgie-panel.desktop[1899]:   Resource id in failed request:  0x4e1466e
    Sep 20 08:41:58 jacob-System-Product-Name budgie-panel.desktop[1899]:   Serial number of failed request:  12
    Sep 20 08:41:58 jacob-System-Product-Name budgie-panel.desktop[1899]:   Current serial number in output stream:  12
```

---

### Post by jsjpandey on 2017-09-20
Can you give the log of printer while giving print command from the following commands
[I]tail -f /var/log/cups/error_log
tail -f /var/log/syslog[/I]

---

### Post by Jacobonbuntu on 2017-09-20
Interesting, pasted the output, it sais I don' t have permission...
Wait, going to pastebin...

Quite a story: [https://pastebin.com/bHnpa7pe](https://pastebin.com/bHnpa7pe)

---

### Post by Jacobonbuntu on 2017-09-20
...And the output of *tail -f /var/log/syslog is no different from what I posted in #3*

---

### Post by slickymaster on 2017-09-20
See [bug 1718215]("https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1718215")

---

### Post by jsjpandey on 2017-09-20
See [bug 1718215]("https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1718215") is perfect solutiion

---

### Post by Jacobonbuntu on 2017-09-20
Awesome, that must be it. Thanks a lot!

---

### Post by wgarcia on 2017-09-20
I was also hit by this bug in all my 17.10 systems and it was driving me crazy.

---

