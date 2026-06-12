---
title: "[SOLVED] Installing VMWare in Hardy - Help"
date: 2008-05-08
forum: Virtualisation
---

### Post by UnknownFear on 2008-05-08
I am trying to follow [this]("http://ubuntuforums.org/showthread.php?t=779934") tutorial and, instead of putting in the install code, I just open a terminal and drag and drop the "install.pl" file into the terminal to install VMware Server, but it wont install.

```
dan@dan-desktop:~$ sudo '/home/dan/src/vmware-server-distrib/vmware-install.pl' 
A previous installation of VMware software has been detected.

Failure

Execution aborted.

dan@dan-desktop:~$
```

Any help with this? I have also tried installing vmware-server from the synaptic manager, but I got this error:

[I]vmware-server:

Package vmware-server has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/I]

Any help? I'd really like to get VMWare Server installed.

---

### Post by glennric on 2008-05-08
Follow the directions on
[Installing VMWare Server in Hardy]("http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29")

---

### Post by glennric on 2008-05-08
vmware-server is no longer available in the repositories.

---

### Post by UnknownFear on 2008-05-08
> **glennric said:**
> Follow the directions on
[Installing VMWare Server in Hardy]("http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29")

I am following your tutorial. I got to the installing part, but this came up:

```
dan@dan-desktop:~$ cd vmware-server-distrib
dan@dan-desktop:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

dan@dan-desktop:~/vmware-server-distrib$
```

---

### Post by bodhi.zazen on 2008-05-08
Please see this thread :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

Basically you need the so called any-any update, there are instructions and links in the above thread.

---

### Post by UnknownFear on 2008-05-09
I have tried the update, but I get this:

```
dan@dan-desktop:~/src/VMWare/vmware-any-any-update116$ sudo ./runme.pl
Can't exec "/etc/vmware/installer.sh": No such file or directory at ./runme.pl
	line 819 (#1)
    (W exec) A system(), exec(), or piped open call could not execute the
    named program for the indicated reason.  Typical reasons include: the
    permissions were wrong on the file, the file wasn't found in
    $ENV{PATH}, the executable in question was compiled for another
    architecture, or the #! line in a script points to an interpreter that
    can't be run for similar reasons.  (Or maybe your system doesn't support
    #! at all.)
    
Unknown VMware version ? is installed. This installer supports only version 2 
and 3.

Execution aborted.

dan@dan-desktop:~/src/VMWare/vmware-any-any-update116$
```

And also, I went into the Synaptic Package Manager and I COMPLETELY removed vmware-server and the vmware-kernel, than tried to install it via Terminal from ~/src/VMWare/..., but I got this:

```
dan@dan-desktop:~$ cd ~/src/VMWare/vmware-server-distrib
dan@dan-desktop:~/src/VMWare/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

dan@dan-desktop:~/src/VMWare/vmware-server-distrib$
```

I am really confused as to why it still detects an installation of vmware-server when I completley removed it. Any more help on this will be greatly appreciated.

---

### Post by UnknownFear on 2008-05-09
Can anyone help me out? It still says it detects a previous installation, yet I uninstalled it and removed it completely from the synaptic manager.

---

### Post by Kokopelli on 2008-05-09
This has been a problem for a few people including myself.  See if you still have a /etc/vmware folder.  If you do try moving it somewhere else and re-running the install.  Failing that try
```
sudo find / -name vmware
```
and clear out the hits.

---

### Post by UnknownFear on 2008-05-09
There is a vmware folder in the /etc folder, but I can't delete it. In the folder there is a file called locations, and this is what is in it:

[I]directory /etc/vmware
file /etc/vmware/locations
answer BINDIR /usr/bin
answer INITDIR /etc
answer INITSCRIPTSDIR /etc/init.d[/I]

Any suggestions?

---

### Post by raidensix on 2008-05-09
try: sudo rm -rf /etc/vmware

---

