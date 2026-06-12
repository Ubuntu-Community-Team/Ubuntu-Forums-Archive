---
title: "Open Remote Console / Access VMWare Server 2.0.2 on Ubuntu Linux 10.04 Lucid"
date: 2010-05-01
forum: Virtualisation
---

### Post by bastafidli on 2010-05-01
Hello,

Using fresh install of Ubuntu Linux 10.04 Lucid Lynx you cannot by default access VMWare Server 2.0.2 running on different machine. I was able to solve this by combining several tips I have found around Internet but since I have not seen it all at one place, I have decided to document it here.

Lets assume your VMWare 2.0.2 server runs on different machine with IP address 10.20.30.40. By default if you try to open URL

[https://10.20.30.40:8333](https://10.20.30.40:8333)

Firefox 3.6 will not be able to open it. To fix this type about:config in the Firefox address bar, hit Enter and click button to promise to be carefull.
In the Filter box type security and hit Enter.
Change security.enable_ssl2 to true.

Go back to [https://10.20.30.40:8333](https://10.20.30.40:8333) and this time it should open the Login page and allows you to login. Login and click on your running virtual machine in the left pane (if it is not running, then start it). Then click on the Console tab. You will get an option to install the plugin. Install it and restart Firefox. If you try to go back to the console tab, you will see that the plugin is installed, but you cannot invoke it. You will get an error. It seems that integration between Firefox 3.6 and the plugin is broken. But since the plugin was installed properly it will still allow you to start it with command line.

Try to execute following command in the terminal

~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc -h "10.20.30.40:8333" -M "YOURVMID"

YOURPROFILE is the name of your Firefox profile. Find it just by going to the above directory.
YOURVMID is ID assigned by VMWare to your VM. There are several places on the Internet which describe how to find it so I won't duplicate it here.

 If you try to run the command, you will get some errors and nothing will run. It is because the permissions are incorrect.

Run the following in the terminal 

chmod 755  ~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmware.com/plugins/*

chmod 755  ~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmware.com/plugins/bin/*

chmod -r 755  ~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmware.com/plugins/lib/*

 After this you can simply run

~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc -h "10.20.30.40:8333" -M "YOURVMID" 

and the Remote Console  and you can login to your server

 To make it smoother, create file VM.desktop on your desktop, open in in text editor and enter the following text

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=VM
Type=Application
GenericName=VMware Remote Console
Comment=Enables remote interaction with virtual machines.
Icon=~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmwar
e.com/plugins/share/icons/hicolor/48x48/apps/vmware-vmrc.png
TryExec=~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vm
ware.com/plugins/vmware-vmrc
Exec=~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmwar
e.com/plugins/vmware-vmrc -h "10.20.30.40:8333" -M "YOURVMID"
GenericName[en_US]=VMware Remote Console

Save the file, change the permissions to make it executable and now you can connect to your server just by double clicking on it.

Update 5/7/2010

In order to solve issue when VMWare Remote Console doesn't grab the mouse, please edit file 

~/.mozilla/firefox/YOURPROFILE.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc

and as a first line after the comments enter

export VMWARE_USE_SHIPPED_GTK=yes

In order to solve issue when the arrow and other extended keys are not working in VMWare Remote Console, please edit (or create) file

~/.vmware/config

and add there line

xkeymap.nokeycodeMap = true

---

### Post by ben_l on 2010-05-03
How can I find what my value should be for "YOURVMID"? Googling really doesn't turn up anything.

---

### Post by Jerome Warnier on 2010-05-04
> **ben_l said:**
> How can I find what my value should be for "YOURVMID"? Googling really doesn't turn up anything.

You'll find a good example here: [http://www.systhread.net/texts/200910gsxwrap.php](http://www.systhread.net/texts/200910gsxwrap.php)

---

### Post by bastafidli on 2010-05-04
> **ben_l said:**
> How can I find what my value should be for "YOURVMID"? Googling really doesn't turn up anything.

Here is another way

[http://planetvm.net/blog/?p=1316](http://planetvm.net/blog/?p=1316)

"Search for a file named “vmInventory.xml” on your VMserver2 host and look inside for <objID>XXX</objID>"

---

### Post by occ4m on 2010-05-17
thanks for collecting this info, it was very useful.

However, I did have to use the full path in the ".desktop" file; the "~" expansion does not work there. (at least for me).

---

### Post by Noe Rodriguez on 2010-05-20
God day.
 
A error with line => export VMWARE_USE_SHIPPED_GTK=yes, when execute ./vmware-vmrc -h.........
 
Gtk-Message: Failed to load module "canberra-gtk-module": libcaberra-gtk-module.so: cannot open shared object file: No such file or directory.
 
Thanks.

---

### Post by rulez on 2010-05-26
Same issue here !

When using export VMWARE_USE_SHIPPED_GTK=yes got :

Gtk-Message: Failed to load module "canberra-gtk-module": libcaberra-gtk-module.so: cannot open shared object file: No such file or directory.

Weird !

If i'm not using this env parameter my mouse doesnt grab the vm window !

---

### Post by rulez on 2010-05-26
Launching vmware-vmrc with sudo fix my problem...

---

### Post by z-itou16 on 2010-07-30
I won't recommend remove the env parameter as it will tell vmware what GUI lib to use.

I have the same problem with canberra-gtk-module, however if it does not cause my virtual experience any problem at all.

Regards!

---

### Post by danielrve on 2010-12-16
Hi..

I have this problem...


[email]user@user-laptop:~/.mozilla/firefox/e50mubam.default/extensions/VMwareVMRC@vmware.com[/email]/plugins$ ls
bin  libconf                         open_source_licenses.txt  vmware-desktop-entry-creator  vmware-vmrc-daemon  xkeymap
lib  np-vmware-vmrc-2.5.0-122581.so  share                     vmware-vmrc                   vmware-vmrc-legacy


user@user-laptop:~$ sudo /home/user/.mozilla/firefox/e50mubam.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc -h localhost:8333 -M 16
sudo: /home/user/.mozilla/firefox/e50mubam.default/extensions/VMwareVMRC@vmware.com/plugins/vmware-vmrc: command not found

when execute vmware-vmrc say command not found...

What can i do???

Thanks

---

