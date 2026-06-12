---
title: "VmWare Workstation problem typing License number"
date: 2013-03-25
forum: Ubuntu Development Version
---

### Post by dcialdella on 2013-03-25
RESOLVED 

In ubuntu 13.04, i can NOT open the window to type the license (original) of my Workstation.
in Ubu 12.10 when I click a botton open another windows to type it.

---

### Post by dino99 on 2013-03-25
and what the logs say ?

---

### Post by dcialdella on 2013-03-25
The log?
where I could find it ?
    folder /home/user/.vmware ?

---

### Post by dcialdella on 2013-03-25
<?xml version="1.0"?>
<VMwareUserExperienceProgram version="1.0">
  <HostUUID>52 25 05 13 fe 85 e8 ce-c5 6a 5e e5 8a 7e 66 46</HostUUID>
  <VMwareProductName>VMware Workstation</VMwareProductName>
  <VMwareProductVersion>9.0.2</VMwareProductVersion>
  <VMwareProductBuild>1031769</VMwareProductBuild>
  <HostOS>Linux</HostOS>
  <HostArch>x86_64</HostArch>
  <HostVersion>Linux 3.8.0-13-generic Ubuntu Raring Ringtail (development branch)</HostVersion>
  <HostLocale>en_US.UTF-8</HostLocale>
</VMwareUserExperienceProgram>

---

### Post by dcialdella on 2013-03-25
I read this

   [http://communities.vmware.com/message/2026697#2026697](http://communities.vmware.com/message/2026697#2026697)

"
I finally found the license directory in the */usr/lib/vmware/licenses/site* folder.
In  that folder you will find 3 different types of licenses, ws, ws.vl,  ws.eval; which I can only assume are the different types of licenses  available for purchase.  After running a 'cat license-ws-90-e*-201202' I  noticed that the license type for each file was different. Since e.x.p  is available free to the general public, the Serial Number for the  license can be found on the website where you can download VMW-TP, I  assumed that it was a full version of the product. There are also 2  different versions of license files in that folder, what looks to be the  version for 8.0.2, and the version for e.x.p.  I copied the  license-ws-90-e1-201202 file to the /etc/vmware/ directory, since that  correlates to the type of license I needed.  Then after running another  cat on the original license file, I merely just edited the new license  file with "Serial = 'XXXXX-XXXXX-XXXXX-XXXXX-XXXXX'", saved and  restarted the VMware service. Tada!! You should now be able to start the  VM, but may have a new issue, an error about the Kernel version being  different than what is found.  I simply rebooted the machine, and reran  VMW, and it started to work.
"

YES, IT WAS RESOLVED !!!!

    cp */usr/lib/vmware/licenses/*license-ws-90-e1-201202     /etc/vmware/license-ws-90-e1-201202

    vi /etc/vmware/license-ws-90-e1-201202

    add the line 
    Serial = "xxx-xxx-xxxx-xxx-xxx"

    restart the VM services and VOILA !!!!!

the problem is related to the APP when I have to type de license number,

---

### Post by neurobashing on 2013-04-10
This work too:

$ sudo /usr/lib/vmware/bin/vmware-vmx --new-sn xxxx-xxxx-xxxx-xxxx-xxxx

---

