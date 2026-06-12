---
title: "Wierd!"
date: 2008-06-03
forum: Virtualisation
---

### Post by Elcid247 on 2008-06-03
i set up VMware, wanted to run my existing copy of windows xp.

neway i found the methods and done every step. but when i press power on, all it does is go to the console window, then after a couple of secs it turns the thing off.

any ideas?

[IMG]http://i32.tinypic.com/s1hh5w.png[/IMG]

---

### Post by Vadi on 2008-06-03
If it doesn't matter much, try installing it in VirtualBox? There's a guide on how to do that in the tips & tutorials on this forum.

---

### Post by fjgaude on 2008-06-03
Where did the existing VM of Windows come from, what hardware?

---

### Post by Elcid247 on 2008-06-03
> **fjgaude said:**
> Where did the existing VM of Windows come from, what hardware?

i got the instructions from here, followed it step by step.

[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)

idk but, i think the answer to ur question is my pc. the windows is set-up on my comp, im using multiboot.


could it be something in the settings of the virtual machine? i see an X on each of the floppy and the cd-rom no matter wht settings i use.


im thinking about reinstalling VMware but the only problem is tht idk how to uninstall it :-P

---

### Post by fjgaude on 2008-06-04
I can't say if what you have done works or not. Sure is complex. <smile>

The easiest way to re-install vmware server is to delete or rename the directory /etc/vmware.

```
sudo mv /etc/vmware /etc/vmwarebak
```

When you start the re-install the /vmware directory will be recreated. If you are successful you can then deleter the /vmwarebak one.

Let us know how you are doing.

---

### Post by Elcid247 on 2008-06-05
ok 1st thank u!

2nd when i tried to reinstall the vmware, i keep getting this error


```
dsktop@Pcv:~/src/VMWare$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found

```

im using the same instructions i used 1st time which i got from here

[http://ubuntuforums.org/showthread.php?t=779934]("http://ubuntuforums.org/showthread.php?t=779934")

last time it worked like a charm but now it doesnt

---

### Post by lswest on 2008-06-05
try ```
chmod a+x vmware-install.pl
sudo perl vmware-install.pl
```

---

### Post by Elcid247 on 2008-06-05
got this
```

dsktop@Pcv:~/src/VMWare$ chmod a+x vmware-install.pl
chmod: cannot access `vmware-install.pl': No such file or directory
dsktop@Pcv:~/src/VMWare$ sudo perl vmware-install.pl
Can't open perl script "vmware-install.pl": No such file or directory
dsktop@Pcv:~/src/VMWare$
``` 

i copied the vmserver and the vm-any-any-update into the directory and extracted them,

it solved the install.pl, but keeps prompting me to overwrite every file.

PS: i actually did not extract em the 1st time or even put them in the directory!!

---

### Post by lswest on 2008-06-05
well, if it's working now then never mind, but if it isn't make sure that the file is called that by running ```
ls
```

---

### Post by Elcid247 on 2008-06-05
actually its not :(

after answering a bazillion prompts, and in the middle of installing the update, it said operation aborted!!


seriousely idk wht to do.

---

### Post by Elcid247 on 2008-06-05
ok im in deep water right now :oops:

```

root@Pcv:/home/dsktop/src/VMWare/vmware-server-distrib# sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Unable to find the answer INITSCRIPTSDIR in the installer database 
(/etc/vmware/locations). You may want to re-install VMware Server.

Execution aborted.

Failure

Execution aborted.

```

any ideas? :lolflag:

im seriousely thiking of reinstalling ubuntu and start over!

---

### Post by fjgaude on 2008-06-05
Have you tried doing what #5 of this thread suggests? And then doing a re-install?

---

### Post by Elcid247 on 2008-06-05
> **fjgaude said:**
> Have you tried doing what #5 of this thread suggests? And then doing a re-install?

actually i did.

but again it said execution aborted(after a bazillion overwrite)

but when i tried again without doing #5, it said

```

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Server 1.0.5 build-80187 for Linux completed 
successfully. Thank you for having tried this software.

```

:lolflag:

and no overwrites this time :D

but i did get this error at the end

```
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

any ideas how i can fix this module thing? cause the webpages gave me nothing lol!

---

### Post by Elcid247 on 2008-06-05
ok solved!! finally!!!

hope the dam thing works this time!!

---

### Post by Elcid247 on 2008-06-05
back to point zero  :-x:-x   :cry::cry::cry:

---

### Post by fjgaude on 2008-06-06
What was done to fix the issue?

---

### Post by Elcid247 on 2008-06-06
the 1st time, this didnt appear

> Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes] 

or maybe it did but i accepted.

anyway the 2nd time didnt have any module issues whatsoever, or any problems.


but im back to point zero, the thing starts then shutsdown after couple of secs.

---

### Post by fjgaude on 2008-06-06
By "shuts down" you mean that the console goes away? unloads?

Or you mean the VM can't be seen or powered on?

---

### Post by Elcid247 on 2008-06-07
> **fjgaude said:**
> By "shuts down" you mean that the console goes away? unloads?

Or you mean the VM can't be seen or powered on?

well it starts, all i see in the console is a black screen, then after couple of secs it goes back to the "Summary" tab.

---

