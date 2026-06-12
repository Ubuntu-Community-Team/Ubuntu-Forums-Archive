---
title: "PKCS11 error"
date: 2010-12-27
forum: Security
---

### Post by lz1dsb on 2010-12-27
Has anyone stumbled upon this error:
sec_error_pkcs11_general_error
I get it when I'm trying to acces a web page where I should authenticate with my digital certificate. I renewed my certificate today (actually I issued a new one as it wasn't possible to renew) and now I'm getting this error. 
Otherwise I'm able to read the certificate's data from Firefox and using the opensc-tool. When I try to access the webpage I'm asked about the PIN, then I view the web page's certificate and than, I got the error. 
It strange though that after I do that I'm no longer able to read the card using the opensc-tool command. It's like the card is blocked after that... Any ideas?

Cheers, 
Boyan

---

### Post by lz1dsb on 2010-12-28
For those interested. The error was a bit trivial. I was using the standard Linux driver libccid. Which by the way doesn't support key lenghts more than 1024. And my new digital key is 2048 bits in lenght. It turns out that libccid is the default driver for the majority of Linux distribution. So the solution was to remove the driver and install the driver provided by the vendor. In this case this is: pcsc-omnikey. This driver is available in multiverse.
After that I also changed the following line in the configuration file /etc/opensc/opensc.conf:
# reader_drivers = openct, pcsc, ctapi;
changed to:
reader_drivers = pcsc;
I'll mark this as solved now.

Cheers, 
Boyan

---

### Post by martinpaljak on 2010-12-29
> **lz1dsb said:**
> For those interested. The error was a bit trivial. I was using the standard Linux driver libccid. Which by the way doesn't support key lenghts more than 1024. And my new digital key is 2048 bits in lenght. It turns out that libccid is the default driver for the majority of Linux distribution. So the solution was to remove the driver and install the driver provided by the vendor. In this case this is: pcsc-omnikey. This driver is available in multiverse.
After that I also changed the following line in the configuration file /etc/opensc/opensc.conf:
# reader_drivers = openct, pcsc, ctapi;
changed to:
reader_drivers = pcsc;
I'll mark this as solved now.

Cheers, 
Boyan


Sorry, this does not make any sense. 

The open source CCID driver, libccid, is the default and recommended method for talking to (CCID compliant, of course) smart card readers, which has no problems with 1024, 2048 or 4096 bit keys, if that's your concern. You need of course  to match proper software with the right card and reader. 

If encountering problems, you should follow the procedure at [http://www.opensc-project.org/opensc/wiki/ReportingBugs](http://www.opensc-project.org/opensc/wiki/ReportingBugs) I can't recommend this as an appropriate solution (of course, there's too little information about your original problem and environment as well)

---

