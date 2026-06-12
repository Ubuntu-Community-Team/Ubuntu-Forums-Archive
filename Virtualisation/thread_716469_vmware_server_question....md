---
title: "vmware server question..."
date: 2008-03-05
forum: Virtualisation
---

### Post by niko123 on 2008-03-05
hi...agian... 

im installying vmware server..... and i just did the following commands...

# cd /tmp/vmware-server 
# sudo ./vmware-install.pl

now that i almost finished...my terminal prompts me with this...

In which directory do you want to install the binary files?
[/usr] 

and im scared to answer it...can anyone help...??

please!

Thanks!

---

### Post by niko123 on 2008-03-05
if i wanted it to be defult....what would i type in... /usr???

---

### Post by HermanAB on 2008-03-06
If you want the default, then don't type anything, just [Enter].

---

### Post by niko123 on 2008-03-06
great thanks....

can you help me with this...i tired installing the VMware management interface...and received the following error...

root@xtwoface:/tmp/vmware-mui-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

root@xtwoface:/tmp/vmware-mui-distrib#  

how...would i remove the previous installation of VMware software....


And how come when i go to my Applications>system tools?VMware console...
and i click to open the vmware console a error pops up saying...
Could not launch menu item. Failed to execute child process "vmware"

---

### Post by niko123 on 2008-03-06
bump...pls help

---

### Post by niko123 on 2008-03-06
bump...:(

---

### Post by fjgaude on 2008-03-06
I believe you have to completely remove the old installation before you can re-install.

Try this:

```
sudo /usr/bin/vmware-uninstall.pl
```

Then reinstall using all the defaults.

---

### Post by niko123 on 2008-03-06
this is what i got back from that command...

xtwoface@xtwoface:~$ sudo /usr/vmware-uninstall.pl
Uninstalling the tar installation of VMware Server.

Unable to find the tar installer database file (/etc/vmware/locations)

Execution aborted.

---

### Post by fjgaude on 2008-03-07
Okay, things are not as we would expect.

Do this: Open Synaptic, then do a Search for vmware. When you find anything that has vmware in it click Mark for Complete Removal. Then Apply, Apply.

Then click on Status bar, and see if there is anything there that needs to be delected, things not being used.

---

### Post by niko123 on 2008-03-07
OK....i removed teh xserver-xorg-video-vmware...it was the only file there to remove

---

### Post by fjgaude on 2008-03-07
A question which you might have already answered: Did you try to intsll the vmware server from their web site: vmware.com? Or from the Ubuntu repositories?

---

