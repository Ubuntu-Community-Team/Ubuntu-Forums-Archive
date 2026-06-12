---
title: "I removed VirtualBox but I forgot to remove VirtualBox extensions &amp; guest additions"
date: 2021-06-29
forum: Virtualisation
---

### Post by EngineerStrange on 2021-06-29
I have removed VirtualBox but I forgot to remove the VirtualBox extensions & guest additions before removing the VirtualBox packages. I have deleted the virtual machine and also removed the virtualbox folders inside .cache and .config. Did I left any residue of Virtualbox in my system?

---

### Post by dddman on 2021-06-29
Open your file manager and do a system wide search on "virtualbox".

---

### Post by EngineerStrange on 2021-06-29
No I found nothing except virtualbox.desktop.json which belongs to snap store. Does it mean that I have no residue left? I mean can it contain something with different name?

---

### Post by guiverc on 2021-06-29
Also asked at [https://askubuntu.com/questions/1348898/i-have-removed-virtualbox-but-i-forgot-to-remove-virtualbox-extensions-guest-a](https://askubuntu.com/questions/1348898/i-have-removed-virtualbox-but-i-forgot-to-remove-virtualbox-extensions-guest-a)

---

### Post by dddman on 2021-06-29
> **EngineerStrange said:**
> I mean can it contain something with different name?
also search "vbox"
got to go to work, good luck

---

### Post by MAFoElffen on 2021-06-29
The most important thing (after the next reboot) is to check this:
```
lsmod | grep -i "vbox"
```
To ensure that all the VBox kernel modules are no longer there...

The Guest Additions are in ISO format, seen by the VBox VM Guests, to add extensions to them, to make API calls to VBox to give them extra abilities, between the guest and the Host. That installs nothing to the host system. If you wanted to convert those hosts to use on another Hypervisor, you should have removed the guest additions from the guests, beforehand... then use/convert the VM disks. For example, if you convert the VM disks to raw or qcow, you could use them with KVM.

Still...
```
sudo apt-get install python-is-python3
```
Will reset the aliases that VBox setup to use Pyhton2 as it's default... That will reset those, without causing dependency issues. (You can't just uninstall the previous.)

---

### Post by EngineerStrange on 2021-06-29
I checked the command you've provided in order to check if VBox kernels are no longer in use and received no output. So everything is okay?
Btw I haven't done anything with 3-4 kernel modules that I've signed and neither know what to do with those.

---

### Post by EngineerStrange on 2021-06-29
There are many apearring on search as vbox. But these are components of linux-hwe-5.8-headers and linux-headers. Should I remove these packages?

---

### Post by MAFoElffen on 2021-06-29
The source... since they are no longer used, they are not doing anything, nor causing any harm. They were installed by VBOx as a depency, in order for it to build the kernel modules..

Since they are no longer needed as dependencies:
```
sudo apt clean
sudo autoremove
```
...Should remove them.

---

### Post by EngineerStrange on 2021-06-29
Then I don't have to unsign the modules?

---

### Post by MAFoElffen on 2021-06-29
Before I answer that: What do "you mean" by "unsign the modules" And is there something that bothers you about what is left?

---

### Post by EngineerStrange on 2021-06-30
I just thought that since I signed the modules in order to use those, now I too have to unsign those in order no longer to keep those in use. However I have no idea and it's just a guess and nothing. If you can confirm there's no such processes then I will be sure everything is okay now or not. I am specially talking about the vbox.ko etc.

---

### Post by EngineerStrange on 2021-06-30
Btw do I need all the linux-modules, image versions or having one is sufficient? I have 5.8.0-53, 5.8.0-55 and 5.8.0-59

---

### Post by deadflowr on 2021-06-30
> **EngineerStrange said:**
> Btw do I need all the linux-modules, image versions or having one is sufficient? I have 5.8.0-53, 5.8.0-55 and 5.8.0-59

If you run/ran the autoremove command posted before it would leave you with just 2 (of each of course)

The design is to leave you the current version and an older version as a backup in case issues are found,
you can simply boot back into the older version as a failsafe.

Of course, there is nothing stopping you from clearing all but the current in use versions and only having 1 installed at a time.

---

### Post by EngineerStrange on 2021-06-30
No I frequently use that autoremove command and still I have some packages of 53 version. Also is there any way to correct the system packages in case I have removed anything which I need actually.

---

### Post by deadflowr on 2021-06-30
Where does it show that?

---

### Post by EngineerStrange on 2021-06-30
In synaptic I checked

---

### Post by deadflowr on 2021-07-03
Sorry for the late reply as I assumed you just used synaptic to remove them then.

---

