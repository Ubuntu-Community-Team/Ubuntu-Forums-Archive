---
title: "MAAS CentOS deployment issues"
date: 2015-10-14
forum: Server Platforms
---

### Post by sa-shukla on 2015-10-14
I  am running MAAS 1.8.2 version, and was able to fetch the CentOS image from the daily repository. Now when I try to deploy a  node using this CentOS image, deployment fails giving following error  message in regiond.log file:

 2015-10-04 10:43:30 [maasserver] ERROR: Unable to identify boot image for (centos/amd64/generic/centos7/commissioning): cluster 'maas' does not have matching boot image.

 Also bootup of node fails with following error message at the boot prompt: unable to find metadata boot-kernel

 This is what my centos image folder looks like:

 # ls /var/lib/maas/boot-resources/current/centos/amd64/generic/centos7/generated/
root-tgz

 Seems the image upload is broken or image deployment. Was unable to figure out with limited error logging messages.



Following is my curtin_userdata_centos file which looks little wierd:
# cat curtin_userdata_centos
#cloud-config
debconf_selections:
 maas: |
  {{for line in str(curtin_preseed).splitlines()}}
  {{line}}
  {{endfor}}
 late_commands:
  maas: [wget, '--no-proxy', '{{node_disable_pxe_url}}', '--post-data', '{{node_disable_pxe_data}}', '-O', '/dev/null']
 power_state:
  mode: reboot

Did anyone try deploying CentOS image through MAAS and also running into same issues? Not sure why it is taking network instead of cluster server IP address.

[ATTACH=CONFIG]264947[/ATTACH]

---

