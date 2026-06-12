---
title: "[SOLVED] Odd printer problem"
date: 2008-12-01
forum: System76 Support
---

### Post by ewg on 2008-12-01
System 76 Sable
Canon Pixma ip4200 printer
Ubuntu 8.10

I've never had any printing problems 'till now. Job is sent, no error messages, no jobs left in queue, cups reports job is completed, but nothing happens. Odd part is 2 wireless networked printers (1 XP, 1 Vista) do print to the canon hooked up to the Ubuntu desktop with no problem.

It worked fine after upgrade to 8.10 but there have been some updates since. Any suggestion?

Thanks,

---

### Post by thomasaaron on 2008-12-01
Are you sure you're selecting the printer and not "print to file"?

---

### Post by ewg on 2008-12-01
Yes. I'm positive. I'm doing the same actions I've done since I first hooked it up a year ago.

---

### Post by thomasaaron on 2008-12-01
Try un-installing the printer and then re-installing it. I had a similar problem on my Epson at home, and this fixed it.

---

### Post by ewg on 2008-12-01
Delete and re-install did not work. Now I'm struggling with the finding it on the network.

---

### Post by ewg on 2008-12-01
OK, I did get the networked printers working, I'd changed the name on the re-install. Printer still won't work from Ubuntu desktop though. All signs are that it is working but nothing happens. 

Thanks for any help. I really do need this to be fixed.

---

### Post by thomasaaron on 2008-12-01
Sorry, I'm a little murky on your set-up, even after re-reading the previous posts.

Did you ever uninstall and re-install the printer? Can you please clarify your set-up?

---

### Post by ewg on 2008-12-01
Sorry for confusion:
I have a System 76 Sable with Ubuntu 8.10. I print with a Canon Pixma iP4200. That has been working fine for over a year. It has worked through all the Ubuntu upgrades & updates through 8.10. Then just 2 days ago, it stopped printing. I can't print any document or even a test page from the Cups manager. I get no error messages, the print manager says the print job is completed and there are no jobs left in the queue. Also, it DOES print from my wireless networked laptops (1 on Vista, 1 on XP). There were several updates last week. Could 1 of those changed something? Why does it still work fine from the networked laptops? I did uninstall & reinstall the printer using the recommended drivers.

As always, thank you.

---

### Post by thomasaaron on 2008-12-01
Yes, some of those updates were cups updates. I just downloaded them, and they didn't hose my printing (network or otherwise). But that doesn't mean they didn't hose yours.

There are some logs that might help us figure it out. After a failed print, run these commands and post the output, and I'll have a look:

cat /var/log/cups/access_log
cat /var/log/cups/error_log
cat /var/log/cups/page_log

---

### Post by ewg on 2008-12-01
Thomas, file was too big to attach. I'll send it in an Open Office Doc to your sys 76 support address.

Thanks,

---

### Post by ewg on 2008-12-02
I did send you the logs you requested via the Sys 76 email support.
I also have this:
ewg@ubuntu:~$ lpq
iP4200-Ver.2.60-1 is ready
no entries
ewg@ubuntu:~$ sudo cat /etc/cups/printers.conf 
[sudo] password for ewg: 
# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2008-12-02 06:27
<DefaultPrinter iP4200-Ver.2.60-1>
Info Canon iP4200
Location Local Printer
DeviceURI usb://Canon/iP4200
State Idle
StateTime 1228217238
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
ewg@ubuntu:~$ service cups restart
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 5043: Operation not permitted
cupsd: Child exited with status 1!
                                                                         [fail]

---

### Post by thomasaaron on 2008-12-02
Everything looks great in your logs until you get to the very end...

E [01/Dec/2008:17:39:59 -0500] Pause-Printer: Unauthorized 
I [01/Dec/2008:17:39:59 -0500] Saving subscriptions.conf... 
I [01/Dec/2008:17:39:59 -0500] Saving printers.conf... 
I [01/Dec/2008:17:39:59 -0500] Printer "iP4200-Ver.2.60-1" stopped by "root". 

I think HAL (the hardware abstraction layer) is shutting down the job at the last minute. 

Try this...

sudo apt-get --purge-remove hal-cups-utils

...and then reboot. 

Then uninstall and re-install the printer and try again.

If this gives you any problems, just re-install hal's interface to cups...

sudo apt-get install hal-cups-utils

Did that work?

---

### Post by ewg on 2008-12-02
Got an error:

ewg@ubuntu:~$ sudo apt-get --purge-remove hal-cups-utils
E: Sense purge is not understood, try true or false.
ewg@ubuntu:~$

---

### Post by thomasaaron on 2008-12-02
Sorry...

sudo apt-get --purge remove hal-cups-utils

---

### Post by ewg on 2008-12-02
Sorry Thomas. It did not work. I know this is taking too much of your time.
It's very weird, and fortunate for me, that the networked laptops still print fine.

Anything else I can try?

---

### Post by thomasaaron on 2008-12-02
Will THAT printer work with another computer?

---

### Post by ewg on 2008-12-02
It is the only printer we have and it is the one that is printing fine from the laptops I have networked through my Ubuntu desktop. That is my biggest puzzle: Why does the network print to it with no trouble?

---

### Post by thomasaaron on 2008-12-02
I see. Your networked printers are XP and Vista and they work. But it will not work from you Ubuntu computer that is connected to it via USB running Intrepid.

That actually sounds more like a driver problem. I know under Dapper, there was a specialized procedure for installing the drivers for the ip4200...

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

And under Intrepid, there is still a special procedure for the ip4300...
[http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

What drivers are you using? Have you tried installing Canon's drivers?

---

### Post by ewg on 2008-12-02
Yes, I went through the driver process under Dapper and those are the drivers I'm using. Do you think I should go through that whole process again?
Not sure if I should try the 4300 with my 4200 but I will if you think it will help.

---

### Post by ewg on 2008-12-02
HOORAY!!!! I followed the link re: intrepid/iP4300 and changed all 4300 references to 4200 and it worked! I'll be careful to check for new drivers more frequently.

Thank you sir!

---

### Post by thomasaaron on 2008-12-02
Any time. Sorry that took so long. Yesterday was slammed, and today I've not had my coffee yet (...and it's 2PM!).

---

