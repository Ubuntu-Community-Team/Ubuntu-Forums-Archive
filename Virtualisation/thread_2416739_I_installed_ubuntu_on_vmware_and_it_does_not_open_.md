---
title: "I installed ubuntu on vmware and it does not open in full screen"
date: 2019-04-14
forum: Virtualisation
---

### Post by aviramof on 2019-04-14
i installed ubuntu on vmware and it does not open in full screen mode when i choose it.it is most likely ubuntu problem not vmware.thanks in advance for the help.

---

### Post by wildmanne39 on 2019-04-14
Thread moved to virtualisation.

---

### Post by TheFu on 2019-04-15
> **aviramof said:**
> i installed ubuntu on vmware and it does not open in full screen mode when i choose it.it is most likely ubuntu problem not vmware.thanks in advance for the help.

VMware makes 6 virtualization products, so each probably has slightly different defaults.

If you want full screen, that would be a VMware setting, definitely. Depending on the specific VMware variant and the GPU it is emulating for the guest, there might be "[guest additions]("https://kb.vmware.com/s/article/1022525")" which should be loaded. Sometimes these are called *VMware Tools*.

Stating the exact version of which VMware hypervisor is being used would be helpful too.
As would the exact variant of Ubuntu and the release - those would be helpful as well.

Have you contacted VMware support?  
[https://pubs.vmware.com/ws65_ace25/ws_user/special.19.13.html](https://pubs.vmware.com/ws65_ace25/ws_user/special.19.13.html) provides a startup option for their "Workstation" hypervisor.
[https://www.virtuallypeculiar.com/2016/12/vsphere-client-console-does-not-display.html](https://www.virtuallypeculiar.com/2016/12/vsphere-client-console-does-not-display.html) is for vsphere.


Or perhaps the wording above isn't clear for what your expectations to getting a guest into full screen mode might be?

---

### Post by aviramof on 2019-04-16
i already tried to reinstall vmware tools according to a guide they gave me on vmware forums and it didn't work.i am using vmware workstation and latest ubuntu 18.10 i think.

i must mention that at first when i install ubuntu it does work in fullscreen but stops later i don't know why.

---

### Post by TheFu on 2019-04-16
18.10 isn't in the VMware Workstation support list here: [https://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&details=1&partner=271&productNames=3&osFamily=2&page=1&display_interval=100&sortColumn=Partner&sortOrder=Asc&testConfig=16](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&details=1&partner=271&productNames=3&osFamily=2&page=1&display_interval=100&sortColumn=Partner&sortOrder=Asc&testConfig=16)

Nor here: [https://partnerweb.vmware.com/GOSIG/home.html](https://partnerweb.vmware.com/GOSIG/home.html)

I did see something about Vmware Fusion having systemd startup order issues with 18.10 in the VMware forums. It was causing Mac Retina displays some issues.

---

### Post by aviramof on 2019-04-18
i'll try downloading 18.04

---

### Post by aviramof on 2019-04-19
i installed 18.04 and it works in full screen mode for now at least.

---

### Post by aviramof on 2019-04-19
the problem now is that 18.04 don't let me change the interface to hebrew.

---

