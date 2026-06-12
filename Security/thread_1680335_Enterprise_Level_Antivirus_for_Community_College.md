---
title: "Enterprise Level Antivirus for Community College"
date: 2011-02-02
forum: Security
---

### Post by jeepfreak2002 on 2011-02-02
I know that this is a linux forum, but I need to tap the brains of folks that have experience in this filed.  My wife is the assistent IT director of a large community college in Pittsburgh, PA.

They are running 4000-5000 client PC's. between the labs a nd faculty, across multiple campuses.  They are rolling out Win 7 64 bit across all machines.  They have 1/2 the PC's on Forefront and 1/2 on TrendMicro.  They want to re-evaluate the AV solution, and are unable to find any decent review or tests for Enterprise level AV/spyware/malware solutions.

Can anyone suggest a product and offer any input for how to make an informed decision as to which product to choose.

Thanks,
jeepfreak2002

---

### Post by bodhi.zazen on 2011-02-02
> **jeepfreak2002 said:**
> I know that this is a linux forum, but I need to tap the brains of folks that have experience in this filed.  My wife is the assistent IT director of a large community college in Pittsburgh, PA.

They are running 4000-5000 client PC's. between the labs a nd faculty, across multiple campuses.  They are rolling out Win 7 64 bit across all machines.  They have 1/2 the PC's on Forefront and 1/2 on TrendMicro.  They want to re-evaluate the AV solution, and are unable to find any decent review or tests for Enterprise level AV/spyware/malware solutions.

Can anyone suggest a product and offer any input for how to make an informed decision as to which product to choose.

Thanks,
jeepfreak2002

You can monitor your network with Linux, and you can run antivirus on mail or samba servers, but you can not "protect" windows clients from a central Linux server.

What is it you want Linux to do for this large network exactly ?

---

### Post by tgm4883 on 2011-02-02
> **bodhi.zazen said:**
> You can monitor your network with Linux, and you can run antivirus on mail or samba servers, but you can not "protect" windows clients from a central Linux server.

What is it you want Linux to do for this large network exactly ?

The way I read it, it's not a linux question at all. He is looking for a Windows AV solution.

I say Symantec Endpoint Protection (SEP). [http://www.symantec.com/business/endpoint-protection](http://www.symantec.com/business/endpoint-protection)  There is a trial available for testing, although you can't go from trial -> licensed in the SEP 11.0 product so if you do test, do it small scale as you will have to reinstall the full product should you decide go with SEP. SEP 12.1 should be out sometime this year around Q2 and have a lot of new features/enhancements. 

Full disclosure: I work for Symantec.

---

