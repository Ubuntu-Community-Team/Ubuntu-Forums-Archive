---
title: "VMware / Windows Domain Controller"
date: 2009-07-27
forum: Virtualisation
---

### Post by TheGameAh on 2009-07-27
Hey all.  Not sure how many Windows guys I'll find here, but figured I'd ask.

Have two domain controllers.  I've gone with a practice I read about years ago, suggesting to keep one domain controller real (this is the PDC emulator, FSMO holder).

A few years later, and I'm wondering if this is still best practice. I've also read that as long as your NTP setup is very solid, (no time drifts to kill your DCs), you should be able to virtualize every domain controller.  Anyone have some practice here?

---

### Post by jocampo on 2009-07-27
Hi

MCSA here and Ubuntu newbie. In a production or real environment, you should NOT virtualize a DC. If your organization depends of that and the host went down or something happen to your VM software, you're "dead".

Trust me! ... play all you want but do not virtualize your DCs

---

### Post by toddi1973 on 2009-07-27
What flavor of VMWare are you using ?
Are you referring to the VMWare Server/Workstation/Parallels product line, or are you talking about ESX(i) ?
If you talk about ESX(i) and vSphere 4.0, I can give my 2 cents on this.
We have sucessfully deployed multiple DCs in multiple sites inside of VMs.
As long as you pay close attention to your redundancy setup, it is much more likely that a physical DC goes down then your vSphere cluster (redundant hosts, redundant network, redundant SANs).

However, having said that... There have been issues with Kerberos authentication due to the timelag in VMs. So our current MO is to have one DC physical at every AD site and have 2 more DCs for that site running inside VMs. One at head-office, one at the site.

 Toddi1973

---

