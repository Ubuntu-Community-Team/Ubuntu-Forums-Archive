---
title: "Cloud-init 'init' phase doesn't fire after clean"
date: 2022-05-13
forum: Ubuntu Cloud and Juju
---

### Post by jbartlett0 on 2022-05-13
We make a vSphere template from Ubuntu 22.04.4 using cloud-init and autoinstall. Works great, we get a proper template (unique machine-id, unique sshd keys, etc). One of our use cases requires us to provision the server using cloud-init a second time; for that template, we remove /etc/cloud/cloud.cfg.d/99-installer.cfg (user-data from first run dumped by autoinstaller) and run 'cloud-init clean --logs' before converting to template. When we provision that template, it does receive the new cloud-config data which is placed at /dev/sr0, but it seems the 'init' phase is not kicked off. The VM sits there with no new configuration. When I log into the console, there is nothing in /var/lib/cloud/instance. If I manually trigger init with 'cloud-init init', the new cloud-config is processed successfully. A reboot completes the config and the VM now works as expected (part of the cloud-config writes a script out, then executes it to retrieve the IP Pool info through vmtools).

Am I missing a step to re-arm cloud-init? Why won't the init phase fire again unless manually triggered? I checked the datasources, and nocloud is first in line, so that should be fine. If I leave 99-installer.cfg in place, it is processed the second time, so I know /etc/cloud/cloud.cfg.d is being parsed. Any tips to get this workng? If I use the pre-built Ubuntu 22.04 cloud image, I can make some changes to it, run 'cloud-init clean' and then convert to template and cloud-init fires as expected. What would block init from running a second time in our template?

---

