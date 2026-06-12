---
title: "XP in 7.10 with VMware?"
date: 2007-10-30
forum: Virtualisation
---

### Post by Apex-jb on 2007-10-30
Is there a guide anywhere that will show me how to install XP pro on Gutsy Gibbon with VMware? All of the guides I have been able to find so far are for older versions of Ubuntu.

---

### Post by evlutn on 2007-10-30
I was just looking for the same thing.  I found the following link and it worked:

[http://ubuntuforums.org/showthread.php?t=592636&highlight=ubuntu+gutsy+install+vmware]("http://ubuntuforums.org/showthread.php?t=592636&highlight=ubuntu+gutsy+install+vmware")

---

### Post by trmentry on 2007-10-31
I followed this
[http://ubuntuforums.org/showthread.php?p=3632767#post3632767](http://ubuntuforums.org/showthread.php?p=3632767#post3632767)

and it worked fine for me.  I'm installed on a headless system.

---

### Post by Delvien on 2007-11-01
Its very easy. 

If you want to install VMware workstation, go to the vmware website, download the RPM then:

```
 sudo apt-get install alien build-essential 
```

then

```
 sudo alien /PATH/VMWARE RPM 
```

(of course replace PATH with the path, and VMWARE RPM with the rpm's name)

then simple enough:

```
 sudo dpkg -i /PATH/NEWVMWARE.deb
```

(again replace path and deb with the path and file name.)

Then.. (should be last step if you have GCC compiler installed.)

```
 sudo /usr/bin/vmware-config.pl 
```

(might be vm-config.pl, im doing this from memory so...)

---

### Post by Delvien on 2007-11-01
but if you are asking to install XP pro, pop in the CD, make a new VM, its all guided, and simple enough.

---

### Post by Apex-jb on 2007-11-04
> **Delvien said:**
> Its very easy. 

If you want to install VMware workstation, go to the vmware website, download the RPM then:

```
 sudo apt-get install alien build-essential 
```

then

```
 sudo alien /PATH/VMWARE RPM 
```

(of course replace PATH with the path, and VMWARE RPM with the rpm's name)

then simple enough:

```
 sudo dpkg -i /PATH/NEWVMWARE.deb
```

(again replace path and deb with the path and file name.)

Then.. (should be last step if you have GCC compiler installed.)

```
 sudo /usr/bin/vmware-config.pl 
```

(might be vm-config.pl, im doing this from memory so...)
Is it the same with VMware Player? I dont have a license for workstation. Also with this step,
```
 sudo dpkg -i /PATH/NEWVMWARE.deb
```
is NEWVMWARE.deb the rpm files name?

---

### Post by Delvien on 2007-11-05
> **Apex-jb said:**
> Is it the same with VMware Player? I dont have a license for workstation. Also with this step,
```
 sudo dpkg -i /PATH/NEWVMWARE.deb
```
is NEWVMWARE.deb the rpm files name?


(again replace path and deb with the path and file name.)


Im not sure on Vmware player, i personally find VMware player very limited, therefore i dont use it. I have a license for VMware workstation so....

Check out VirtualBox OSE ( in the repos ) its easier to install, and ALOT faster.

---

