---
title: "[SOLVED] VMware CPU speed problem"
date: 2008-05-19
forum: Virtualisation
---

### Post by bmwman on 2008-05-19
Hello,
I'm using VMware workstation 6.03 and have XP pro as a guest on Ubuntu 8.04. Everything has been working perfect for a while until today. I started my VM as usual and got the following message:
.............................................................................
This processor may not be powerful enough to run VMware Workstation with good performance.  Your estimated processing speed is 2 Mhz.  Refer to [http://www.vmware.com/info?id=4](http://www.vmware.com/info?id=4) for this product's minimum requirements.
.............................................................................

I have never had any problems before and it just happened. I tried rebooting few times and what not but VM is extremely slow and cannot even boot to XP all the way. My specs are Core 2 Duo 1.86Mhz and 2gb PC2 5300 ram.

Anybody knows how to fix that?

---

### Post by dicecca112 on 2008-05-19
try this

[http://vmblog.com/archive/2007/08/24/help-vmware-fixing-time-keeping-problems-with-the-guest-os.aspx](http://vmblog.com/archive/2007/08/24/help-vmware-fixing-time-keeping-problems-with-the-guest-os.aspx)

---

### Post by bmwman on 2008-05-19
I do have the tyme syncronization checked. Anyway, the issue dissapeared same way like it came up.

Everything works fine again:confused:

---

### Post by Seti on 2008-08-24
@dicecca112  	
Thanks for that link, I just had this same problem and the link had the info needed to fix the issue. In your /etc/vmware/config file, you have to add:

```

host.cpukHz = "X"
host.noTSC = TRUE
ptsc.noTSC = TRUE

```

where "X" is your CPU speed. I have a 2 GHz P4, so mine is 2000000.

:)

---

