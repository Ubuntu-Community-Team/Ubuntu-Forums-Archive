---
title: "Helpful scripts - discover/register virtualbox VMs and register ISOs in Media Manager"
date: 2020-06-25
forum: Virtualisation
---

### Post by kneutron on 2020-06-25
--This has come in handy for me when booting multiple distros on the same hardware, and changing ZFS pool names/datasets so I wanted to share -- HTH

--I created some scripts to populate Virtualbox on a freshly installed distro.  Modify script to cd to where your "Default Machine Folder" would be in Virtualbox Preferences, and it will find and register existing VMs and ISOs.  Works on Ubuntu 18.04, 20.04 and OSX High Sierra with Virtualbox 6.1.10.

BEGIN vbox-populate.sh # don't forget to chmod +x it

```

#!/bin/bash


# Discover existing virtualbox vms and add them to the GUI
# If GUI is already running, they should populate in realtime


# REF: https://www.virtualbox.org/manual/ch08.html#vboxmanage-general




#source ~/bin/failexit.mrg

# failexit.mrg
function failexit () {
  echo '! Something failed! Code: '"$1 $2" # code # (and optional description)
  exit $1
}


vbm=`which VBoxManage`


function discregis () {
  find .  -name *.vbox -type f -exec $vbm registervm "$PWD/{}" \;
}

# TODO editme
cd /zsgtera4/virtbox-virtmachines || failexit 101 "! Cannot cd to VM dir"
discregis

# Uncomment/duplicate if you have VMs in more than one location
#cd /zdell500/virtbox-virtmachines || failexit 102 "! Cannot cd to VM dir"
#discregis


VBoxManage list vms

# Populate Media Manager with existing ISOs


# create dummy VM and attach known ISOs to it to populate media manager
# REF: http://www.allgoodbits.org/articles/view/54
# REF: https://superuser.com/questions/741734/virtualbox-how-can-i-add-mount-a-iso-image-file-from-command-line


vmname=dummyisofinder


VBoxManage createvm --name "$vmname" --ostype 'Linux_64' --basefolder "$HOME" --register
VBoxManage modifyvm "$vmname" --description "NOTE this is just a temp VM used to conveniently register ISOs with vbox media manager - it was created with $0"


VBoxManage storagectl $vmname --name IDE --add ide --controller piix3 --portcount 2 --bootable on


#VBoxManage showvminfo "$vmname"


function registeriso () {
  for this in *.iso; do
    echo $PWD/${this}
    VBoxManage storageattach "$vmname" --storagectl IDE --port 0 --device 0 --type dvddrive --medium $PWD/${this}
#  VBoxManage modifyvm $vmname --dvd $PWD/${this}
  done
}

# TODO editme - point this to where you keep your ISOs
#cd /Volumes/zsgtera4/shrcompr-zsgt2B/ISO
cd /zsgtera4/shrcompr/ISO
registeriso

# if this shows up as mounted in df (useful for network shares), use it too
if [ $(df |grep /mnt/imac5 |wc -l) -gt 0 ]; then
  cd /mnt/imac5/ISO
  registeriso
fi


# eject
VBoxManage storageattach "$vmname" --storagectl IDE --port 0 --device 0 --type dvddrive --medium emptydrive 

```

---

