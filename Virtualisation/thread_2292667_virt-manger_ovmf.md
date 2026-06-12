---
title: "virt-manger ovmf"
date: 2015-08-30
forum: Virtualisation
---

### Post by darthrevan13 on 2015-08-30
I want to configure a VirtuaI Machine graphically and the virt-manager, qemu packages offered by Ubuntu are a tad too old for my taste so I used the virtualization PPA for Ubuntu (ppa:jacob/virtualisation) to get the latest qemu and libvirt without getting into the headache of compiling them. After that I used

```
apt-get install ovmf
```

to get the OVMF option in libvirt and virt-manager but virt-manger threw this warning > Libvirt did not detect any UEFI/OVMF firmware image installed on the hostAfter some searching I found out that the OVMF image supplied with Ubuntu is quite old so I [found]("https://packages.debian.org/sid/ovmf") a fairly recent one in the unstable packages of Debian 8. After I downloaded it I installed and restarted libvirt-bin using:

```
dpkg -i ovmf_0~20150106.5c2d456b-1_all.deb
systemctl restart libvirt-bin
```

But still virt-manager would not see OVMF. After some more searching I found [this]("https://www.redhat.com/archives/virt-tools-list/2014-September/msg00163.html") page that explains when virt-manger displays the warning:

> 1) libvirt supports the necessary domcapabilities bits, 
2) it detects that qemu supports the necessary command line options, and 
3) libvirt detects a UEFI binary on the host that maps to a known template via qemu.conf

After reading that I realized that the 3rd option was surely the problem, meaning that when I installed OVMF (either from the Ubuntu PPA or the deb package) it did not create the necessary links in /etc/libvirt/qemu.conf. Opening it I found at the bottom of the file that I have to list the OVMF images in this format:

```
nvram = [
   "/usr/share/OVMF/OVMF_CODE.fd:/usr/share/OVMF/OVMF_VARS.fd"
]
```

Here is where I hit a wall. I don't know what or how to make an OVMF_VARS file. I only have one image in /usr/share/ovmf/ and I don't understand how I can split it or what is the syntax for the qemu.conf file to put just the unified image.

PS: I'm a noob when it comes to Linux & Visualization so I'm sorry if my question seems easy or stupid.

---

### Post by KillerKelvUK on 2015-08-31
There aren't any packages with up-to-date ovmf builds in them so you need to work around...Gerd Hoffman runs a daily OVMF build site, you can grab is files here ([https://www.kraxel.org/repos/jenkins/edk2/](https://www.kraxel.org/repos/jenkins/edk2/)).  You need to grab the one with 'ovmf-x64' in the file name...within the .rpm archive find 2 files named 'OVMF-pure-efi.fd' and 'OVMF_VARS-pure-efi.fd', extract these and put them in /usr/share/qemu/, then change into the same directory and create a symbolic link using 'sudo ln -s OVMF-pure-efi.fd OVMF.fd'.  Re-edit /etc/libvirt/qemu.conf and update the nvram link you noted in your post to reflect the new path i.e. /usr/share/qemu/.

As you're using Jacob's PPA for updated virt tools then virt-manager should now work fine when you select OVMF from the drop list when creating a new vm.

---

### Post by GizmoChicken on 2015-09-17
> **KillerKelvUK said:**
> There aren't any packages with up-to-date ovmf builds in them so you need to work around...Gerd Hoffman runs a daily OVMF build site, you can grab is files here ([https://www.kraxel.org/repos/jenkins/edk2/](https://www.kraxel.org/repos/jenkins/edk2/)).  You need to grab the one with 'ovmf-x64' in the file name...within the .rpm archive find 2 files named 'OVMF-pure-efi.fd' and 'OVMF_VARS-pure-efi.fd', extract these and put them in /usr/share/qemu/, then change into the same directory and create a symbolic link using 'sudo ln -s OVMF-pure-efi.fd OVMF.fd'.  Re-edit /etc/libvirt/qemu.conf and update the nvram link you noted in your post to reflect the new path i.e. /usr/share/qemu/.

As you're using Jacob's PPA for updated virt tools then virt-manager should now work fine when you select OVMF from the drop list when creating a new vm.


I originally had a similar issue as that presented by darthrevan13.  In my case, when attempting to create a VM using Virt-Manager 1.2.1 (from Jacob's PPA) with KVM on an Ubuntu 15.10 host, the pull down menu in Virt-Manager for selecting UEFI reported "UEFI not found" on the system.

After following the steps that you provided, the pull down menu in Virt-Manager now allows me to select OVMF.  So that's a big step forward.  Thanks!

However, I now get a new error message when I attempt to create a VM with OVMF.  (I'll just note that I don't get any errors when using Virt-Manager 1.2.1 to create VMs that don't use OVMF.)

Here's an example of the error that I get when I try to use my installation of Virt-Manager 1.2.1 (from Jacob's PPA) on Ubuntu 15.04 and 15.10 to create create a VM with OVMF:[INDENT]
Unable to complete install: 'internal error: cannot load AppArmor profile 'libvirt-e1318c23-8e80-4f2a-b3f9-9dfe9414da54''

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1873, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 414, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 478, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3497, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: cannot load AppArmor profile 'libvirt-e1318c23-8e80-4f2a-b3f9-9dfe9414da54
[/INDENT]

  Care to share any thoughts on how to overcome the "cannot load AppArmor profile" error?

---

### Post by KillerKelvUK on 2015-09-20
> **GizmoChicken said:**
> I originally had a similar issue as that presented by darthrevan13.  In my case, when attempting to create a VM using Virt-Manager 1.2.1 (from Jacob's PPA) with KVM on an Ubuntu 15.10 host, the pull down menu in Virt-Manager for selecting UEFI reported "UEFI not found" on the system.

After following the steps that you provided, the pull down menu in Virt-Manager now allows me to select OVMF.  So that's a big step forward.  Thanks!

However, I now get a new error message when I attempt to create a VM with OVMF.  (I'll just note that I don't get any errors when using Virt-Manager 1.2.1 to create VMs that don't use OVMF.)

Here's an example of the error that I get when I try to use my installation of Virt-Manager 1.2.1 (from Jacob's PPA) on Ubuntu 15.04 and 15.10 to create create a VM with OVMF:[INDENT]
Unable to complete install: 'internal error: cannot load AppArmor profile 'libvirt-e1318c23-8e80-4f2a-b3f9-9dfe9414da54''

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 89, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 1873, in do_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 414, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 478, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3497, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: cannot load AppArmor profile 'libvirt-e1318c23-8e80-4f2a-b3f9-9dfe9414da54
[/INDENT]

  Care to share any thoughts on how to overcome the "cannot load AppArmor profile" error?

Sure...

```

sudo apt-get purge apparmor  (semi joke here so don't just copy/paste unless you know what you're doing!)

```

Depends on whether you want to keep AppArmor or not, I'm sure the mods and other AppArmor supporters will be able to help narrow the problem and offer support but my personal solution was the above command, I don't run AppArmor on my VM host.  If you were to google around to find out how to edit AppArmor profiles you will be able to locate the config file for the complaining profile, its likely a file permissions issue to do with libvirt trying to access the new OVMF file/folder...from this you could attempt to update the AppArmor permissions allowed for libvirt.  My personal experience is poor with AA however I prob haven't given it enough due attention.

If I recall you will get more detailed AA output in dmesg and you can also set AA to complain mode so that it will prompt you if/when it denies access.  These I think will confirm specifically what AA has a problem with, that will give you good input for some googling around.

Sorry I can't be of more help on this one...unless your happy to live without AA then I think my first answer is your ticket :lolflag:

---

### Post by GizmoChicken on 2015-09-21
> **KillerKelvUK said:**
> Sure...

```

sudo apt-get purge apparmor  (semi joke here so don't just copy/paste unless you know what you're doing!)

```

Depends on whether you want to keep AppArmor or not, I'm sure the mods and other AppArmor supporters will be able to help narrow the problem and offer support but my personal solution was the above command, I don't run AppArmor on my VM host.  If you were to google around to find out how to edit AppArmor profiles you will be able to locate the config file for the complaining profile, its likely a file permissions issue to do with libvirt trying to access the new OVMF file/folder...from this you could attempt to update the AppArmor permissions allowed for libvirt.  My personal experience is poor with AA however I prob haven't given it enough due attention.

If I recall you will get more detailed AA output in dmesg and you can also set AA to complain mode so that it will prompt you if/when it denies access.  These I think will confirm specifically what AA has a problem with, that will give you good input for some googling around.

Sorry I can't be of more help on this one...unless your happy to live without AA then I think my first answer is your ticket :lolflag:

Thanks for the reply.  Much appreciated!

Just to confirm, you also experienced the "cannot load AppArmor profile"  error when attempting to create a VM with OVMF?  And to get past that  error, you purged AppArmor?

Well, I'm not quite ready to the employ the "sudo apt-get purge apparmor" nuclear option just yet.  And while I'm not opposed to editing AppArmor profiles, I had hoped that I could overcome the problem otherwise, such as by editing permissions on some files, which, as you speculate, is the likely culprit.  When/if I get a chance, I'll do some more digging.  I may even try again using the QEMU command line in an attempt to rule in/out libvirt's participation in the error.

By the way, I did ask for support on the virt-tools-list a few weeks ago, but so far, no answer.  See [https://www.redhat.com/archives/virt-tools-list/2015-August/msg00064.html](https://www.redhat.com/archives/virt-tools-list/2015-August/msg00064.html)

---

### Post by redger on 2015-09-21
did you install the standard Ubuntu ovmf package first ? I installed this before anything else in order to ensure the correct links permissions etc were in place ... then installed the latest from Gerds repository over the top ... and didn't experience any problems

fwiw I had a number of issues with AppArmor interfering with virtualisation & passthrough, not this one tho. I recall having to work my way thru all the logs and even went so far as to create my own AppArmor entries in /etc/apparmor.d/libvirt/ ..... unnecessarily as it happens :(
then after more tinkering I found I could operate successfully using my own (non admin) logon if I made the following changes to  /etc/apparmor.d/abstractions/libvirt-qemu
```
# WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /{dev,run}/shm r,
 # ================ START Changes ================ #
  /{dev,run}/shm/pulse-shm* rw,
  @{HOME}/.config/puls** rwk,
  @{HOME}/** r,
  # Only necessary if running as root, which we no longer are
  #/root/.config/puls** rwk,
  #/root/.asoundrc r,
  /dev/vfio/* rw,
  /dev/hugepages/libvirt** rw,
  # ================ END Changes ================ #
  /{dev,run}/shmpulse-shm* r,
  /{dev,run}/shmpulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
```
I'm not suggesting you need the same ... but it suggests some useful entries

you may need to add a line to provide read write access to the vars files along the lines of 
```
/usr/share/qemu/OVMF** rwk,
```

good luck :)

---

### Post by GizmoChicken on 2015-09-28
> **redger said:**
> did you install the standard Ubuntu ovmf package first ? I installed this before anything else in order to ensure the correct links permissions etc were in place ... then installed the latest from Gerds repository over the top ... and didn't experience any problems

fwiw I had a number of issues with AppArmor interfering with virtualisation & passthrough, not this one tho. I recall having to work my way thru all the logs and even went so far as to create my own AppArmor entries in /etc/apparmor.d/libvirt/ ..... unnecessarily as it happens :(
then after more tinkering I found I could operate successfully using my own (non admin) logon if I made the following changes to  /etc/apparmor.d/abstractions/libvirt-qemu
```
# WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /{dev,run}/shm r,
 # ================ START Changes ================ #
  /{dev,run}/shm/pulse-shm* rw,
  @{HOME}/.config/puls** rwk,
  @{HOME}/** r,
  # Only necessary if running as root, which we no longer are
  #/root/.config/puls** rwk,
  #/root/.asoundrc r,
  /dev/vfio/* rw,
  /dev/hugepages/libvirt** rw,
  # ================ END Changes ================ #
  /{dev,run}/shmpulse-shm* r,
  /{dev,run}/shmpulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
```
I'm not suggesting you need the same ... but it suggests some useful entries

you may need to add a line to provide read write access to the vars files along the lines of 
```
/usr/share/qemu/OVMF** rwk,
```

good luck :)


Hi redger,

Thanks much for the suggestions.  Much appreciated.  Unfortunately, none of those AppArmor edits, at least in my hands, seems to have overcome the error.

Just for kicks, I tried KillerKelvUK's (semi-joking) suggestion to purge AppArmor.  Sure enough, after purging AppArmor, I can create and run VMs using OVMF with virt-manager.  For me, that's not a long-term option.  But it's good to know that the error truly does result from some aberrant interaction with AppArmor.

I've been testing on Ubuntu 15.10 pre-release.  After the official release, I'll try again with a clean install.  Maybe something will have been cleared up by then.

GizmoChicken

---

### Post by redger on 2015-09-29
I also added comments similar to above apparmor entries into /etc/libvirt/qemu.conf

```
# ============= Start Change ============== #
cgroup_device_acl = [
    "/dev/null", "/dev/full", "/dev/zero",
    "/dev/random", "/dev/urandom",
    "/dev/ptmx", "/dev/kvm", "/dev/kqemu",
    "/dev/rtc","/dev/hpet", "/dev/vfio/vfio",
    "/dev/vfio/1", "/dev/vfio/14", "/dev/vfio/15", "/dev/vfio/16", "/dev/vfio/17",
    "/dev/shm", "/root/.config/pulse", "/dev/snd",
]
# ============= Start Change ============== #

```

Plus some other possibilities
```
# Notes: The DAC security driver is always enabled; as a result, the
# value of security_driver cannot contain "dac".  The value "none" is
# a special value; security_driver can be set to that value in
# isolation, but it cannot appear in a list of drivers.
#
#security_driver = "selinux"
# ============= Start Change ============== #
# Setting to None Didn't help me - might help you (I set mine back to apparmor)
#security_driver = "apparmor"
security_driver = "none"
# ============= End Change ============== #
```
```
# If set to non-zero, then attempts to create unconfined
# guests will be blocked. Defaults to 0.
# ============= Start Change ============== #
security_require_confined = 0
#security_require_confined = 1
# ============= End Change ============== #
```

If you're passing hardware through, this may also help
```
relaxed_acs_check = 1
```

Also in /etc/libvirt/qemu.conf you could set libvirt to run as root (not recommended, but you an do it - I have commented these out in my copy)
```
# ============= Start Change ============== #
user = "root"

# The group for QEMU processes run by the system instance. It can be
# specified in a similar way to user.
group = "root"
# ============= End Change ============== #
```

plus one or 2 other possibilities in the same file (you may not need all these, but I'll document them anyway
```
hugetlbfs_mount = "/dev/hugepages"
```
```
clear_emulator_capabilities = 1
```
```
vnc_allow_host_audio = 1
```
```
nographics_allow_host_audio = 1
```

once again .. good luck

---

### Post by xsnake_ on 2015-10-18
With regards to the AppArmor profile issue noted above by GizmoChicken, I have noticed that adding:
```
security_driver = "none"
```
to /etc/libvirt/qemu.conf seems to resolve the issue (don't forget to systemctl restart libvirt-bin.service).

---

### Post by fredwntr1 on 2015-10-18
download the ovmf deb package from debians website make sure its the newer unstable version. migrate to downloads via terminal and use command sudo dpkg -i ovmf.........
after sudo virsh edit (your vm name)  add this in the os section of your xml file


 <os>
    
    <loader readonly='yes' type='rom'>/usr/share/ovmf/OVMF.fd</loader>      <------------------------------------- this 
   
  </os>

---

### Post by darthrevan13 on 2015-10-26
@fredwntr1
> 
download the ovmf deb package from debians website make sure its the newer unstable version. migrate to downloads via terminal and use command sudo dpkg -i ovmf.........
after sudo virsh edit (your vm name) add this in the os section of your xml file


<os>

<loader readonly='yes' type='rom'>/usr/share/ovmf/OVMF.fd</loader> <------------------------------------- this 

</os>


That's what ended up doing to get it to work. It really is a bummer that i have to manually edit this because someone forgot to make a profile in AppArmor for Virt Manager and OVMF.

@redger
> 
Also in /etc/libvirt/qemu.conf you could set libvirt to run as root (not recommended, but you an do it - I have commented these out in my copy)
Code:
# ============= Start Change ============== #
user = "root"

# The group for QEMU processes run by the system instance. It can be
# specified in a similar way to user.
group = "root"
# ============= End Change ============== #
plus one or 2 other possibilities in the same file (you may not need all these, but I'll document them anyway
Code:
hugetlbfs_mount = "/dev/hugepages"
Code:
clear_emulator_capabilities = 1
Code:
vnc_allow_host_audio = 1
Code:
nographics_allow_host_audio = 1
once again .. good luck


I know it's off topic but I found the options for hugepages and host audio on another thread, tried them and failed miserably. Hugepages was unusable for me, because again AppArmor (I did not want to deactivate or purge it, looking into making profiles that work for what I need is on my TO DO list), and the  audio options sent crackling noise back so the only solution I found was to do Steam In-home streaming from the VM to the host which, worked well albeit at some performance cost that I don't quite like. I was thinking of getting a KVM switch just to get rid of this head ache.

Would you be so kind as to point me in the direction where I could find some documentation about the qemu options you just mentioned?

PS: Also, would it be worth it to ditch AppArmor and go with SELinux? I have a bit of expierence with it and it seems easier to me, or is it just a pain to set it up on Ubuntu?

---

### Post by redger on 2015-11-08
for a detailed set of instructions, try this .... [http://ubuntuforums.org/showthread.php?t=2266916&highlight=uefi]("http://ubuntuforums.org/showthread.php?t=2266916&highlight=uefi")

first you need to install the hugepages package
```
sudo apt-get install hugepages
```

add the following lines to /etc/sysctl.conf
```
# Set hugetables / hugepages for KVM single guest needing 6GB RAM
vm.nr_hugepages = 3200
```

The above figures are set for my system where, hugepages are 2MB each. On my system, the Windows VM which needs this facility the most is allocated 6GB of ram, so we need 6144 MB which => 6144 / 2 = 3072 … plus add some extra for overhead (about 2% ie. 61 additional pages), so I have overachieved 

Create a new directory for hugepages, we'll use this later (to improve VM performance)
```
sudo mkdir /dev/hugepages
```

update the libvirt qemu configuration at /etc/libvirt/qemu.conf -
```
hugetlbfs_mount = "/dev/hugepages"
```

Update apparmor to allow libvirt to allocate hugepages, use VFIO and sound. Add the following to the apparmor definition in /etc/apparmor.d/abstractions/libvirt-qemu
```
# WARNING: this gives the guest direct access to host hardware and specific
  # portions of shared memory. This is required for sound using ALSA with kvm,
  # but may constitute a security risk. If your environment does not require
  # the use of sound in your VMs, feel free to comment out or prepend 'deny' to
  # the rules for files in /dev.
  /{dev,run}/shm r,
 # ================ START Changes ================ #
  /{dev,run}/shm/pulse-shm* rw,
  @{HOME}/.config/puls** rwk,
  @{HOME}/** r,
  # Only necessary if running as root, which we no longer are
  #/root/.config/puls** rwk,
  #/root/.asoundrc r,
  /dev/vfio/* rw,
  /dev/hugepages/libvirt** rw,
  # ================ END Changes ================ #
  /{dev,run}/shmpulse-shm* r,
  /{dev,run}/shmpulse-shm* rwk,
  /dev/snd/* rw,
  capability ipc_lock,
```
Then reload the apparmor defintiions so the changes take effect
```
sudo invoke-rc.d apparmor reload
```
Then restart libvirt (just to be sure)
```
sudo service libvirt-bin stop
sudo service libvirt-bin start
```


then in the XML for your VM
```
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
```

hopefully that will work


As for sound, I tried using both Pulse and Alsa. Alsa worked best but both have their problems ... so I bought a cheap PCIe USB card which is assigned to the VM and the attached a cheap USB sound card to that - works nicely, no lag, no crackling, all good. 

The qemu program will print detailed help for audio (I piped it into a text file), see the manual







From time to time I had some trouble with Hugepages, particularly if something went wrong with Qemu (prior to using Libvirt) so I would use this script to recover the Hugepages space (scrappy, but it works for me)
```
#!/bin/sh
# ==============  Try to use Hugepages if possible ============== ##
# cat /proc/meminfo |grep HugePage     will print all the relevant info on Hugepages
echo "Allocating Hugepages (hopefully)"
# Set the amount we want
MEM=6144
#MEM=12144  # Used for testing max only
# Set the Hugepages PageSize factor
FACTOR=2
# Set the amount of total system memory to reserve
RESERVE=6144
# Set the parameter text for qemu
HUGE="-mem-path /dev/hugepages"
# Swapsize (in hugepages) used by hugeadm to consolidate existing pages into contingious area
SWAPSIZE=1000
# Calculate required number of pages assuming each page = 2048kB
NEED=$(( $MEM / $FACTOR ))
# Calculate the amount we want (allowing for management overhead)
# WANT=$(( $TOTAL + $NEED ))
WANT=$(( $NEED + (( $MEM / 100 * 2 )) ))
# Find the total system memory
MEMTOTAL=$(grep MemTotal /proc/meminfo | awk '{print $2}')
# Find current total Hugepages memory
TOTAL=$(grep HugePages_Total /proc/meminfo | awk '{print $NF}')
# Find the number of HugePages available
AVAIL=$(grep HugePages_Free /proc/meminfo | awk '{print $NF}')
# Is there enought for us ?
NEWTOTAL_RAM=$MEMTOTAL
# How much do we need to capture ?
NEWTOTAL_PAGES=$(( $TOTAL + $WANT - $AVAIL ))
# First use the admin command which will consolidate any existing pages
#    to maximise the number of contiguous pages
if [ $AVAIL -lt $WANT ]; then
#   Try to allocate an additional amount
    echo "Re-establishing and defragmenting hugepages NEWTOTAL_PAGES " $NEWTOTAL_PAGES " SWAPSIZE " $SWAPSIZE
    echo "COMMAND = hugeadm --pool-pages-min=DEFAULT:$NEWTOTAL_PAGES --add-temp-swap=$SWAPSIZE"
# sysctl -p
    kdesudo "hugeadm --pool-pages-min=DEFAULT:$NEWTOTAL_PAGES --add-temp-swap=$SWAPSIZE"
#    kdesudo "hugeadm --pool-pages-min=DEFAULT:3194 --add-temp-swap=1000"
fi
# Find the updated number of HugePages available
AVAIL=$(grep HugePages_Free /proc/meminfo | awk '{print $NF}')
# If the admin command didn't work, try brute force (unlikely to succeed, but you never know)
if [ $AVAIL -lt $WANT ]; then
#   First try to allocate an additional amount
    NEWTOTAL=$(( $WANT - $AVAIL + $TOTAL ))
    NEWTOTAL_RAM=$(( (( (( $NEWTOTAL * $FACTOR )) + $RESERVE )) * 1024 ))
    if [ $NEWTOTAL_RAM -lt $MEMTOTAL ]; then
        echo $NEWTOTAL > /proc/sys/vm/nr_hugepages
    else
        echo 0 > /proc/sys/vm/nr_hugepages
        TOTALUPD=$(grep HugePages_Total /proc/meminfo | awk '{print $NF}')
        AVAILUPD=$(grep HugePages_Free /proc/meminfo | awk '{print $NF}')
        NEWTOTALUPD=$(( $WANT - $AVAILUPD + $TOTALUPD ))
        NEWTOTAL_RAMUPD=$(( (( (( $NEWTOTALUPD * $FACTOR )) + $RESERVE )) * 1024 ))
        if [ $NEWTOTAL_RAMUPD -lt $MEMTOTAL ]; then
            echo $NEWTOTALUPD > /proc/sys/vm/nr_hugepages
        else
            echo 'Insufficient space for Hugepages --> ' $TOTAL ' > ' /proc/sys/vm/nr_hugepages
            HUGE=
        fi
    fi
#   echo $WANT > /proc/sys/vm/nr_hugepages
fi

AVAILUPD=$(grep HugePages_Free /proc/meminfo | awk '{print $NF}')
if [ $AVAILUPD -lt $WANT ]; then
    echo 'Insufficient space for Hugepages --> ' $TOTAL ' > ' /proc/sys/vm/nr_hugepages
    HUGE=
fi
#  Debugging
if [ "$1" = "debug" ]; then
    echo "reserve " $RESERVE
    echo "need " $NEED
    echo "want " $WANT
    echo "total " $TOTAL
    echo "avail " $AVAIL
    echo "memtotal " $MEMTOTAL
    echo "newtotal " $NEWTOTAL
    echo "NEWTOTAL_RAM " $NEWTOTAL_RAM
    echo "NEWTOTAL_PAGES " $NEWTOTAL_PAGES
    echo "memtotal " $MEMTOTAL
    echo "avail upd " $AVAILUPD
    echo "total upd " $TOTALUPD
    echo "newtotal upd " $NEWTOTALUPD
    echo "NEWTOTAL_RAM upd " $NEWTOTAL_RAMUPD
    echo "HUGE = " $HUGE
    echo
    cat /proc/meminfo |grep HugePage
fi
#exit
```

---

