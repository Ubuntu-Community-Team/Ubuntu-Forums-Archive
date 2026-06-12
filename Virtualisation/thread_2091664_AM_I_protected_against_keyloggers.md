---
title: "AM I protected against keyloggers ?"
date: 2012-12-05
forum: Virtualisation
---

### Post by Objectivity on 2012-12-05
Hi Folks,

 I have installed Linux mint on " windows 7 - Vmware " and have some sensitive files on it.

 Just wondering AM I protected against keyloggers ? Can someone access my files ?

 How secure I am in " Virtual environment " ?  :confused:

Yours,
Objectivity

---

### Post by slickymaster on 2012-12-05
Recently VMware release security patches for an ESX server hypervisor source code leak that was published in April and allegedly perpetrated by a hacker from Anonymous. The recent patch repaired critical vulnerabilities that could have enabled an attacker to execute malicious code remotely on the host and leave an end-user's virtualized environment susceptible to a compromising cyber attack.

VMs still run on physical machines. They can be accessed remotely no different from a physical server (RDP, OOB, etc.) so there is still no difference there.

Probably the best approach is to assume and act in a non virtualized environment, regular security  still applies, e.g. secure the individual VMs just like they weren't virtual; secure the host machine as it is a normal server running highly critical workloads (which it is) and treat the virtualization management interface (if you have one) exactly like any "domain admin level" system and secure normally.

---

### Post by Objectivity on 2012-12-05
> **slickymaster said:**
> Recently VMware release security patches for an ESX server hypervisor source code leak that was published in April and allegedly perpetrated by a hacker from Anonymous. The recent patch repaired critical vulnerabilities that could have enabled an attacker to execute malicious code remotely on the host and leave an end-user's virtualized environment susceptible to a compromising cyber attack.

VMs still run on physical machines. They can be accessed remotely no different from a physical server (RDP, OOB, etc.) so there is still no difference there.

Probably the best approach is to assume and act in a non virtualized environment, regular security  still applies, e.g. secure the individual VMs just like they weren't virtual; secure the host machine as it is a normal server running highly critical workloads (which it is) and treat the virtualization management interface (if you have one) exactly like any "domain admin level" system and secure normally.


 SO MUCH THANX ! God bless you.

---

### Post by DuckHook on 2012-12-05
> **slickymaster said:**
> Probably the best approach is to assume and act in a non virtualized environment, regular security  still applies, e.g. secure the individual VMs just like they weren't virtual; secure the host machine as it is a normal server running highly critical workloads (which it is) and treat the virtualization management interface (if you have one) exactly like any "domain admin level" system and secure normally.

+1

You are probably more at risk for keyloggers with the Windows host than with the VM. My comment is based on the assumption that you are downloading more apps, doing your surfing, mail, etc on Windows, and the risk invariably follows the OS that is interacting most aggressively with the outside world. If a keylogger gets installed, it will read whatever you type, whether this be in the host OS or the VM. To bring the discussion down from the heights of paranoia, you are unlikely to get keylogged if you have a full antivirus setup on your Windows host and are properly updated and don't do anything outright foolish on either your host or your Linux VM.

---

### Post by Objectivity on 2012-12-07
> **DuckHook said:**
> +1

You are probably more at risk for keyloggers with the Windows host than with the VM. My comment is based on the assumption that you are downloading more apps, doing your surfing, mail, etc on Windows, and the risk invariably follows the OS that is interacting most aggressively with the outside world. If a keylogger gets installed, it will read whatever you type, whether this be in the host OS or the VM. To bring the discussion down from the heights of paranoia, you are unlikely to get keylogged if you have a full antivirus setup on your Windows host and are properly updated and don't do anything outright foolish on either your host or your Linux VM.

   You wrote :   If a keylogger gets installed, it will read whatever you type !    WOW ! I did not know it can read in VM also ! this is very risky then. Thank you for mentioning this. I probably make another partition and install linux on it alone. This would be much much safer !     Thank you to both of you.

---

### Post by Jason80513 on 2012-12-07
I don't know if the number is correct, but it's been going around the newsgroups lately that something like 1 in 4 Windows machines is infected with malware. Windows is just a tempting target, especially if you are using an older version.

Better to use a simple install of Linux, and lock down the machine as much as possible. 
* Enable the firewall: sudo ufw enable
* Pick a browser and turn off all the plugins.
** Especially the Java plugin. Uninstall the icedtea plugin if you have to.
** Especially the Flash plugin, unless it's Chrome (now unsupported in others).
** You probably don't need the other ones.
* Stick to installing just the applications you need.

You can also use a non-secure account for most things (an account with non-admin rights), and set up permissions on the sensitive files such that the user account you normally use can't see them. And then switch over to the other account when you need to access those files.

Set the hard-drive password (via your bios setup) to prevent someone getting access to the machine if they steal it.

There are some good ways to keep your sensitive data encrypted on disk if you are really paranoid. :)

And don't use a VM for the sensitive data. That just means an attacker has two operating systems to play with. Access to either one exposes your data.

---

### Post by kurt18947 on 2012-12-08
> **Objectivity said:**
> You wrote :   If a keylogger gets installed, it will read whatever you type !    WOW ! I did not know it can read in VM also ! this is very risky then. Thank you for mentioning this. I probably make another partition and install linux on it alone. This would be much much safer !     Thank you to both of you.

That's what I've done.  Create a linux partition for use only in sensitive applications.  Surf the sports sites, tube sites, hobby boards etc. etc. with a separate O.S. on a separate partition.  I've also been able to install a light linux distro e.g. lubuntu or xubuntu on a USB drive formatted to ext2.  That is slow to load but it works and doesn't have java, flash or other security risks.

---

### Post by Objectivity on 2012-12-09
> **Jason80513 said:**
> I don't know if the number is correct, but it's been going around the newsgroups lately that something like 1 in 4 Windows machines is infected with malware. Windows is just a tempting target, especially if you are using an older version.

Better to use a simple install of Linux, and lock down the machine as much as possible. 
* Enable the firewall: sudo ufw enable
* Pick a browser and turn off all the plugins.
** Especially the Java plugin. Uninstall the icedtea plugin if you have to.
** Especially the Flash plugin, unless it's Chrome (now unsupported in others).
** You probably don't need the other ones.
* Stick to installing just the applications you need.

You can also use a non-secure account for most things (an account with non-admin rights), and set up permissions on the sensitive files such that the user account you normally use can't see them. And then switch over to the other account when you need to access those files.

Set the hard-drive password (via your bios setup) to prevent someone getting access to the machine if they steal it.

There are some good ways to keep your sensitive data encrypted on disk if you are really paranoid. :)

And don't use a VM for the sensitive data. That just means an attacker has two operating systems to play with. Access to either one exposes your data.

 I use Truecrypt with keyfile to secure my sensitive files ! Thank you for your help. VERY useful indeed.

---

