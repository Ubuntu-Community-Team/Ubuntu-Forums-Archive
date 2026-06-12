---
title: "Are you supposed to removed cloud-init"
date: 2019-09-16
forum: Ubuntu Cloud and Juju
---

### Post by crusty1337 on 2019-09-16
As far as i understand it, cloud-init handles early initialization of a cloud instance.
Ive been using it to help build KVM VMs and it works really well.

One aspect of cloud-init I dont understand is what happens once its done the initial creation of the instance.

Does it automatically disable itself so it never runs again?
Can it execute again under certain circumstances? (I'm pretty sure I got it to re-run by running ```
sudo rm -rf  /var/lib/cloud/*
```)
Should I be uninstalling cloud-init once my instance has been built and its gone into production?

---

### Post by digikin on 2020-01-19
Technically you could remove them and it wont cause an issue but those files are used for troubleshooting.  
Here is a snipit from the cloudinit docs.

 [h=2]Where are the data files?[/h] Inside the /var/lib/cloud/ directory there are two important subdirectories:
  [h=3]instance[/h] The /var/lib/cloud/instance directory is a symbolic link that points to the most recenlty used instance-id directory. This folder contains the information cloud-init received from datasources, including vendor and user data. This can be helpful to review to ensure the correct data was passed.
 It also contains the datasource file that containers the full information about what datasource was identified and used to setup the system.
 Finally, the boot-finished file is the last thing that cloud-init does.
 
  [h=3]data[/h] The /var/lib/cloud/data directory contain information related to the previous boot:
 
[LIST]
[*]instance-id: id of the instance as discovered by cloud-init. Changing this file has no effect.
[*]result.json: json file will show both the datasource used to setup the instance, and if any errors occured
[*]status.json: json file shows the datasource used and a break down of all four modules if any errors occured and the start and stop times.
[/LIST]

---

### Post by TheFu on 2020-01-19
I've removed cloud-init from my KVM servers, but Canonical's dependencies (or more likely "install-recommended" options for APT keep reinstalling it.
I don't do "cloudy" things, but I definitely do lots of virtualization.  Big proponent of self-hosting everything possible here.

---

