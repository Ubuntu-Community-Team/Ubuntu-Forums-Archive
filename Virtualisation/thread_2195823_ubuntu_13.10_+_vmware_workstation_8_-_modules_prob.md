---
title: "ubuntu 13.10 + vmware workstation 8 - modules problem"
date: 2013-12-26
forum: Virtualisation
---

### Post by linux.girl on 2013-12-26
Hello everyone. I upgraded from ubuntu 13.04 to 13.10. Now my VM workstation 8 can no longer be launched. See the problem + the solution that I had for the** [COLOR=#ff0000]13.04[/COLOR]. Now none of this is working for [COLOR=#ff0000]13.10[/COLOR] and I cant use my VMs :-( Does anyone know of a solution to ubuntu 13.10 and vm 8?**

Problem:

(the problem is in a screenshot that appears below under the word Thanks, click on it to enlarge and see the problem)

Solution for 13.04:

apt-get install build-essential
ln -s  /usr/src/linux-headers-$(uname  -r)/include/generated/uapi/linux/version.h  /usr/src/linux-headers-$(uname -r)/include/linux/version.h
cd /usr/lib/vmware/modules/source
ll
tar xvf vmblock.tar ; tar xvf vmci.tar; tar xvf vmmon.tar ; tar xvf vmnet.tar ; tar xvf vsock.tar
wget [http://communities.vmware.com/servlet/JiveServlet/download/2234875-108182/vmci.linux-3-8.patch](http://communities.vmware.com/servlet/JiveServlet/download/2234875-108182/vmci.linux-3-8.patch)
ll
patch -p0 < vmci.linux-3-8.patch.2
vi module_together 
for file in *-only
 
do
 
  tar cvf `basename $file -only`.tar $file
 
done
 
rm -rf *-only
chmod 755 module_together 
./module_together 
rm -rf * -only
rm -rf *-only
vmware-modconfig --console --install-all
 
This  didnt permanently solve the problem as after reboot I got the  /dev/vmmon and vmci errors, which I fixed with this script given in  another forum:
 
#!/bin/bash
if [[ $UID != 0 ]]; then
    echo "Please run this script with sudo:"
    echo "sudo $0 $*"
    exit 1
fi
 
sudo  ln -s /usr/src/linux-headers-$(uname  -r)/include/generated/uapi/linux/version.h  /usr/src/linux-headers-$(uname -r)/include/linux/version.h
 
cd /usr/lib/vmware/modules/source
sudo cp vmci.orig.tar vmci.tar
sudo cp -n vmci.tar vmci.orig.tar
 
sudo tar -xf vmci.tar
cd vmci-only/linux/
 
sudo sed '127s/.*/   .remove = vmci_remove_device,/' driver.c > driver.c.tmp
mv driver.c.tmp driver.c
sudo sed '1744s/.*/static int/' driver.c > driver.c.tmp
mv driver.c.tmp driver.c
sudo sed '1972s/.*/static void/' driver.c > driver.c.tmp
mv driver.c.tmp driver.c
cd ../..
sudo tar -cf vmci.tar vmci-only/
 
sudo rm vmci-only/ -Rf
sudo vmware-modconfig --console --install-all
sudo rm /usr/src/linux-headers-$(uname -r)/include/linux/version.h
echo "Done"


 
 
[B]Now that I upgraded to ubuntu 13.10 this no longer works. Can anyone help please?


Thanks!!![/B]
**[ATTACH=CONFIG]248917[/ATTACH]**

---

### Post by linux.girl on 2014-01-07
Help please...anyone?

---

### Post by jcottier on 2014-03-04
Hi, I have not tried workstation, but I know that vmplayer v5 and v6 works ok in 13.10. Since you upgraded, I would guess that its got the wrong (previous) linux headers are left installed. I think I would use synaptic to check which headers and kernel source are still installed and remove any old ones.

---

