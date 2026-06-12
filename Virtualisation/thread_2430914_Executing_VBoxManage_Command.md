---
title: "Executing VBoxManage Command"
date: 2019-11-09
forum: Virtualisation
---

### Post by Quarkrad on 2019-11-09
Sorry if this has come up before.  I have a number of virtual machines located in a specific directory and need to execute a number of vboxmanage commands on a particular machine.  If the machine is located in **/media/dad/virtualbox** and the machine is called **test** does one have to cd to **/media/dad/virtualbox**, via the terminal, in order to execute the command on **test**? (Or /media/dad/virtualbox/test - where the .vbox and .vdi files are located?).   Most web pages show vboxmanage commands being executed from the home directory or just show the command itself.

---

### Post by Quarkrad on 2019-11-09
I believe the answer is yes - I have just made the change I need.  I opened a terminal and navigated to the folder containing the vbox file I needed to change. In the example above cd/media/dad/virtualbox/test where there is a number of files including test.vbox.  I then executed the VBoxManage command and the appropriate change was made to the test.vbox file.

---

