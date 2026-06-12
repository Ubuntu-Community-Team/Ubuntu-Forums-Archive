---
title: "Setting User data in cloud init to run &quot;always&quot; through openstack"
date: 2013-11-12
forum: Ubuntu Cloud and Juju
---

### Post by callanankids on 2013-11-12
I submitted the issue to the openstack forum and am interested if I can find anyone here who might know the answer or provide a response that will help...

   the openstack thread: [https://ask.openstack.org/en/question/6895/passing-user-data-python-script-down-and-it-only-runs-until-reboot/](https://ask.openstack.org/en/question/6895/passing-user-data-python-script-down-and-it-only-runs-until-reboot/)

Through the openstack API I build a json object to boot a VM ( ubuntu image). The script gets placed properly in 

      /var/lib/cloud/instance/scripts/part-001

The script runs properly, however, I would like it to run on every reboot. I've found the /etc/init/cloud-final.conf runs all of the modules just once and shall never run them again. If I enter

     /usr/bin/cloud-init-cfg scripts-user always

It will re-run the user data

So my question is this, do I need to edit the **cloud-final.conf** and alter/add the ***script-user always*** option or is there another way... Adding a cron job, or adding it to the /etc/init.d scripts aren't good options for me. They seem to be more of a hack rather than an engineered solution.

thanks for any feedback

---

