---
title: "How to move my &quot;virtual machines&quot; folder (Ubuntu) to my 2nd internal HD"
date: 2023-02-11
forum: Virtualisation
---

### Post by swarup on 2023-02-11
I am running out of space on my main internal hard drive, the one that houses my OS (MS Windows 11), and would like to move the "virtual machines" folder containing my Ubuntu OS to my 2nd internal HD which has a lot of space on it. Is this ok to do, and if so are there particular steps that need to be taken? Or can I simply copy the folder and the paste it onto my other internal HD and run it from there? I am using VM Ware (Workstation 16). Both my internal hard drives are solid state drives (SSD).

---

### Post by TheFu on 2023-02-11
This is a Windows and VMware Workstation question, not really related to Linux.

No clue how to do it on MS-Windows as the host.  I'd be surprised if there wasn't an "Export VM" option in the GUI for VMware Workstation.  [https://docs.vmware.com/en/VMware-Workstation-Pro/17/com.vmware.ws.using.doc/GUID-D1FEBF81-D0AA-469B-87C3-D8E8C45E4ED9.html](https://docs.vmware.com/en/VMware-Workstation-Pro/17/com.vmware.ws.using.doc/GUID-D1FEBF81-D0AA-469B-87C3-D8E8C45E4ED9.html) is the link a web search found. It is empty when I click it, but that's normal with my browser settings.

---

### Post by swarup on 2023-02-11
Ubuntu users are quite savvy about issues like this, and over the years I have found that I could get the best guidance here on our Ubuntu forum. Someone here on the forum is going to know exactly how this is done.

---

### Post by howefield on 2023-02-11
Thread moved to the "*Virtualisation*" forum.

---

### Post by swarup on 2023-02-11
I was able to manage the move-- it was a simple copy and paste. Then VMW asked me when I tried to open the new one whether I'd moved it or copied it, and I selected "moved". That was it. All done.

---

### Post by TheFu on 2023-02-11
The OVF format includes a VM UUID, so I suspect that's where the hint came from.  This is normal, industry-wide, but usually it is a problem, not helpful when doing things like this. 

Glad it worked for you.

---

