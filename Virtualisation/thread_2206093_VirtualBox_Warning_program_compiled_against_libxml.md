---
title: "VirtualBox Warning: program compiled against libxml 209 using older 207"
date: 2014-02-17
forum: Virtualisation
---

### Post by fatih3 on 2014-02-17
I have installed Ubuntu Server 12.04-4 LTS.
  Set to /etc/apt/sources.list
  
[LIST]
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) saucy contrib 
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) raring contrib 
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) quantal contrib 
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib 
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid contrib non-free 
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) wheezy contrib 
[*]deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) squeeze contrib non-free 
[/LIST]
  After that I did
  ```
sudo apt-get update
sudo apt-get install virtualbox-4.3

```  

The Commandline below give me the Error **"Warning: program compiled against libxml 209 using older 207"**
  ```
VBoxManage setproperty websrvauthlibrary null 
```

  Than I downloaded to install the Extension Pack of Linux
  ```
wget [http://download.virtualbox.org/virtualbox/VERSION/Oracle_VM_VirtualBox_Extension_Pack-4.3.6.vbox-extpack](http://download.virtualbox.org/virtualbox/VERSION/Oracle_VM_VirtualBox_Extension_Pack-4.3.6.vbox-extpack)
VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.3.6.vbox-extpack
```
  Got the same error like above with **"Warning: program compiled against libxml 209 using older 207"**

  Can anybody tell what is wrong? What is wrong with libxml?


  **ScreenLog**
  [HTML]VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.3.0.vbox-extpack
Warning: program compiled against libxml 209 using older 207
0%...
Progress state: NS_ERROR_FAILURE
VBoxManage: error: Failed to install "/home/thatsme/Oracle_VM_VirtualBox_Extension_Pack-4.3.0.vbox-extpack"
VBoxManage: error: The installer failed with exit code 127: Warning: program compiled against libxml 209 using older 207
VBoxManage: error: Error creating textual authentication agent: Error opening current controlling terminal for the process (`/dev/tty'): No such device or address
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component ExtPackManager, interface IExtPackManager
VBoxManage: error: Context: "int handleExtPack(HandlerArg*)" at line 1143 of file VBoxManageMisc.cpp[/HTML]

I set usermod too
```
sudo usermod -aG vboxusers <your username>
```

```
VBoxManage -version
Warning: program compiled against libxml 209 using older 207
4.3.0r89960

VBoxManage list extpacks
Warning: program compiled against libxml 209 using older 207
Extension Packs: 0

```

---

### Post by SeijiSensei on 2014-02-17
Did you put all those URLs in sources.list?  You only want to use the one that is identical to your current Ubuntu version, in your case **precise**.  Remove all the others, run "sudo apt-get update" again, and see if you can now run "sudo apt-get install virtualbox-4.3" cleanly.

---

### Post by fatih3 on 2014-02-17
Thanks! 

All is done!!

---

