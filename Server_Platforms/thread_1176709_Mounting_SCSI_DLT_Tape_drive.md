---
title: "Mounting SCSI DLT Tape drive"
date: 2009-06-02
forum: Server Platforms
---

### Post by fosheezy on 2009-06-02
Hello,
I am running Ubuntu 8.04 server in Vmware ESXi.  I have a DLT Tape drive plugged it, it shows up on the physical server, and after a > $ cat /proc/scsi/scsi
I get :


> 
Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: VMware   Model: Virtual disk     Rev: 1.0 
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: NECVMWar Model: VMware IDE CDR00 Rev: 1.00
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: QUANTUM  Model: DLT VS160        Rev: 2500
  Type:   Sequential-Access                ANSI  SCSI revision: 02


I cannot seem to find a definitive answer as to how to confgure the /etc/stinit.def file.  I've looked through the examples in the example file, put them into the file, done an stinit but still get 
> $ stinit
Initialized 0 tape devices.
  

I have never delt with tape drives at all, and am trying to get this to work to avoid purchasing Windows server (2008 doesn't even support backing up to tape drives anyway, I'd be stuck with 2003 which I don't want to use if I were forced into it).  Can someone help me out here?  I'd really like to save $900 for my company. I need to backup about 113 GB of data to this tape drive. I have 5 tapes. The server is a Dell PE 2800, and used to have 2003 SBS on it, but SBS doesnt like not being the domain controller on our new 2003 server's domain.  The tape drive is plugged into a pci slot on the back, so it is a separate SCSI device.  ESXi is working wonderfully, I just need this to work to seal the deal.  I've looked around online and in my "ubuntu, Unleashed" book, but came up with nothing.  Any help with that file is appreciated.  

Thanks!

Let me know if I left out any info someone might need to help me.

---

### Post by alastair on 2009-06-02
The Quantum "Installation guide for Linux" seems to talk about creating/checking device nodes :

[http://www.quantum.com/ServiceandSupport/SoftwareandDocumentationDownloads/DLTVS160/index.aspx](http://www.quantum.com/ServiceandSupport/SoftwareandDocumentationDownloads/DLTVS160/index.aspx)

Do you have them?

This s/w might be Redhat oriented, so YMMV.

---

### Post by Vegan on 2009-06-02
Tape is so passe, go get a hard disk or another storage server and use it for backups. Tape is very last year's tech.

Disks are cheaper than ever.

---

### Post by fosheezy on 2009-06-02
> **alastair said:**
> The Quantum "Installation guide for Linux" seems to talk about creating/checking device nodes :

[http://www.quantum.com/ServiceandSupport/SoftwareandDocumentationDownloads/DLTVS160/index.aspx](http://www.quantum.com/ServiceandSupport/SoftwareandDocumentationDownloads/DLTVS160/index.aspx)

Do you have them?

This s/w might be Redhat oriented, so YMMV.

Thanks for this, I had not found it on the site.  I'll try it out tomorrow at work.

To the reply about using hard drives - I'd love to, trust me.  The server is a file server (for testing videos - have to keep them for a few years for compliance) and it will be at a remote location.  Our headquarters uses a dedicated backup server that pushes the backups offsite twice a day.  If I can get the price down for HDD backup, I'll put it out there. But for now I'd like to get the tape drive working, because I just bought an IBM x3650M2 and had to buy some microsoft licensing for it, so I spent about $7000.  Not sure some more hard drives are going to be approved to purchase.

Thanks for the help, I'll let you know how it goes.

---

### Post by johnnyb0y on 2010-03-31
> **Vegan said:**
> Tape is so passe, go get a hard disk or another storage server and use it for backups. Tape is very last year's tech.

Disks are cheaper than ever.

Tapes are used the world over for backup so I think it's very much still current!

I've had 5 HDDs go bad on me over the years, and my Quantum DLT7000 has yet to let me down.

Just my two penneth...

---

