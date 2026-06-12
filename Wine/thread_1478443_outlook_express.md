---
title: "outlook express"
date: 2010-05-09
forum: Wine
---

### Post by ian_king2 on 2010-05-09
I know it seems like a daft idea, but I'd like to get Outlook Express working in Wine. (all the other machines on our network are using it and we share a common mailbox)

Has anyone managed this?

I'm running 9.10 on a 64 bit machine
version of wine is 1.1.42 (I needed this version to get Dreamweaver to work)

I can run IE6 using ies4linux to no avail.

I've copied across all the DLLs which Outlook Wxpress claims to need 

This is as far as I've got:

err:service:validate_service_config Service L"Mxdsvbgrs" is Win32 but has no image path set
err:service:scmdatabase_load_services Invalid configuration of service L"Mxdsvbgrs" - skipping
fixme:shell:MLLoadLibraryA ("acctres.dll",0x68810000,0) semi-stub!
fixme:shell:MLLoadLibraryA ("msoeres.dll",0x60330000,0) semi-stub!

anyone got a suggestion (other than dumping Outlook Express of course)

Ian

---

### Post by cogadh on 2010-05-09
Unfortunately, dumping OE may be your only option. In Wine testing, it only works as far as receiving mail, it doesn't work for sending mail at all. Thunderbird can work with a common mailbox and might be much easier to deal with.

---

