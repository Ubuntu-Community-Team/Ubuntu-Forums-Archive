---
title: "Vmware install error"
date: 2010-09-24
forum: Virtualisation
---

### Post by greavette on 2010-09-24
Hello,

I'm using the following page to install VMware server 2.0.2 on my Ubuntu Lucid x64 bit (desktop) version.

I've downloaded the tar.gz file from the vmware website and I've downloaded the script to help me install vmware on my system.

[http://www.marcosorfila.com/site/vmware-server-202-on-ubuntu-1004/](http://www.marcosorfila.com/site/vmware-server-202-on-ubuntu-1004/)

Both the tar.gz file and the .sh script are both in a folder on my desktop.  I have not extracted the tar file.

I execute the install using this:
sudo sh vmware-server-2.0*.sh

but this is the errors I receive when I execute this script.  

vmware-server-2.0.x-kernel-2.6.3x-install.sh: 1: cannot open &#65533;r&#65533;&#1554;&#65533;&#65533;z&#65533;O6&#65533;: No such file
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 1: &#65533;: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 2: &#65533;=&#1627;[*!&#65533;&#65533;&#65533;&#65533;&#65533;: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 2: cannot open &#1626;&#65533;Qe
                                                                :&#65533;&#65533;&#1255;&#65533;&#65533;1&#65533;N&#65533;n&#1008;&#65533;3&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
        ^&#65533;b&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?d&#65533;&#65533;l1&#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;&#65533;N&#65533;&#65533;n&#65533;
                                                 &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Lw: No such file
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 2: 3&#65533;&#65533;&#64575;&#65533;&#65533;&#65533;&#65533;l&#65533;9
                                                            g: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 3: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 4: &#914;W&#65533;s&#65533;&#65533;:&#65533;&#1514;e&#65533;&#65533;&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;6&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#12281;&#65533;&#65533;&#65533;N&#65533;=k8: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 5: a: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 5: A&#65533;d^C&#505;Q&#65533;&#65533;d!&#65533;&#65533;: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 5: cannot open &#1467;&#65533;&#65533;g8&#65533;&#65533;: No such file
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 5: &#65533;x+I&#65533;b&#65533;&#65533;&#65533;}&#65533;u&#65533;&#65533;a&#65533;: not found
Y: not foundr-2.0.x-kernel-2.6.3x-install.sh: 5: &#65533;&#65533;1&#65533;&#785;
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 6: &#65533;&#65533;]G&#65533;&#65533;c9C00&#65533;L&#65533;: not found
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 7: Syntax error: "&" unexpected
vmware-server-2.0.x-kernel-2.6.3x-install.sh: 6: 
                                                   &#65533;: not found

Any ideas what I can do to fix these errors.

Thanks,

Charles.

---

### Post by CharlesA on 2010-09-24
Hrm. Try this script that I wrote up, it's based on the ones I came across.

```
#!/bin/bash

###
### Script to install VMware Server on Ubuntu 10.04
### See: http://communities.vmware.com/thread/267682
### See: https://help.ubuntu.com/community/VMware/Server
###

VMWARE=VMware-server-2.0.2-203138.x86_64.tar.gz
VMDIR=vmware-server-distrib
# Color Variables
RED='\E[30;31m'
GREEN='\E[30;32m'
YELLOW='\E[30;33m'
BLUE='\E[30;34m'
MAGENTA='\E[30;35m'
CYAN='\E[30;36m'
WHITE='\E[30;37m'
RESET="tput sgr0"

# Install gcc, which is used for compiling vmware kernel modules
apt-get install gcc --assume-yes || { echo -e $RED"Failed to install gcc"; $RESET; exit; }
# Make the patch script executable, if it isn't already
chmod +x patch-vmware_2.6.3x.sh || { echo -e $RED"Failed to change permissions on patch-vmware_2.6.3x.sh"; $RESET; exit; }
# Extract VMware Server archive, else exit
if [ -f $VMWARE ]
then
  echo -e "Extracting VMware Server archive...\c"&& tar -xf $VMWARE && echo -e $GREEN"\t\t\t\t\tDone!"; $RESET
else
  { echo -e $GREEN"VMware Server archive does not exist!"; $RESET; exit; }
fi
# Run the patch script
./patch-vmware_2.6.3x.sh $VMDIR/lib/modules/source/ > /dev/null && echo -e $GREEN"VMware Server patched successfully!"; $RESET
# Install Vmware Server
./$VMDIR/vmware-install.pl || { echo -e $RED"Install of VMware Server Failed"; $RESET; exit; }
```

Also, follow the instructions on [this]("http://communities.vmware.com/thread/267682") page, to get these files:

```
00-vmware-2.6.32_functional.diff
01-vmware-2.6.32_cosmetic.diff
02-vmnet-include.diff
patch-vmware_2.6.3x.sh
vmware-config.pl.diff

```

---

### Post by greavette on 2010-09-25
Thanks very much for your help with your scripts you've created. 

I've followed the instructions, but I'm confused by the final instruction to do start the install:

" . ./patch-vmware_2.6.3x.sh /path/to/vmware-server-distrib/lib/modules/source"

What does /path/to mean?  I don't have vmware installed so I have no path to any installed modules.  As for the tar.gz file I've downloaded from vmware...that file is in the same location as all your scripts I've downloaded.

Thank you.

---

### Post by dcstar on 2010-09-25
> **greavette said:**
> Thanks very much for your help with your scripts you've created. 

I've followed the instructions, but I'm confused by the final instruction to do start the install:

" . ./patch-vmware_2.6.3x.sh /path/to/vmware-server-distrib/lib/modules/source"

What does /path/to mean?  I don't have vmware installed so I have no path to any installed modules.  As for the tar.gz file I've downloaded from vmware...that file is in the same location as all your scripts I've downloaded.

Thank you.

It means the path where **you **have downloaded the install files.

---

### Post by dcstar on 2010-09-25
> **greavette said:**
> Hello,

I'm using the following page to install VMware server 2.0.2 on my Ubuntu Lucid x64 bit (desktop) version.

I've downloaded the tar.gz file from the vmware website and I've downloaded the script to help me install vmware on my system.

[http://www.marcosorfila.com/site/vmware-server-202-on-ubuntu-1004/](http://www.marcosorfila.com/site/vmware-server-202-on-ubuntu-1004/)

Both the tar.gz file and the .sh script are both in a folder on my desktop.  I have not extracted the tar file.
......

What do the instructions tell** you** to do? (hint: it isn't going to extract itself).

---

### Post by CharlesA on 2010-09-25
> **dcstar said:**
> What do the instructions tell** you** to do? (hint: it isn't going to extract itself).

Mine does. ;)

```
tar -xf $VMWARE
# Run the patch script
./patch-vmware_2.6.3x.sh $VMDIR/lib/modules/source/ > /dev/null
```

@OP: I've attached the files that will allow you to run the patch.

Place them in the same directory as the vmware tar.gz.

---

### Post by greavette on 2010-09-25
Awesome CharlesA...the install now works on my system.

Almost there...now that I've installed VMware 2.02 on my Ubuntu server, I'm seeing a strange error when starting a VM.  Has anyone seen this before?

"Power On Virtual Machine" failed to complete
Failed to initialize monitor device. 

I had installed KVM on this server a 2 years back.  I mention this because I see on the Ubuntu forums others having trouble with VMware after running KVM.  Before upgrading my version of Ubuntu lucid recently I had VMware running successfully on this server.   I found this post that mentions what someone else did to fix VMware after kvm:

[http://ubuntuforums.org/showthread.php?t=1176312&page=2](http://ubuntuforums.org/showthread.php?t=1176312&page=2)

I don't have the kvm running in the background and I've verified that kvm is not installed on my system anymore.  

Any other ideas why I'm getting this failed to initialize monitor device?

Thank you.

---

### Post by greavette on 2010-09-25
I spoke too soon.

I tried the following instruction to stop kvm:

sudo modprobe -r kvm-intel 

and then I restarted my vmware:

sudo /etc/init.d/vmware restart

And now my VM starts without error.

I'm thinking that since I've already checked to make sure kvm was removed previously by doing the following:

sudo rmmod kvm-intel
sudo apt-get remove –purge kvm
and I checked that the following do not exist:
/etc/kvm
/etc/udev/rules.d/45-kvm.rules
/etc/init.d/kvm

That maybe my problem was that I just needed to start vmware.  But I include all the above in case others read this post and need to remove kvm to fix their vmware issues.

Thanks again CharlesA for your modified scripts.  I really appreciate your help.  You got to love this Ubuntu community always trying to learn and help each other.  

I may need to run this vmware restart after each reboot which isn't ideal, but at least my vmware server is back up and running.

Thank you.

---

### Post by greavette on 2010-09-25
Last followup on this post.  I restarted my host server to see what would happen.  VMware again wouldn't start my virtual machine properly.  I'm running an Adito portal in a VM (also on Ubunt lucid Server edition) for our small business so it's quite important that when the server restarts, vmware can automatically start our Adito server without a problem.  Looks like I won't be able to rely on that happening.

It's really too bad that VMware is so much trouble on Ubuntu.  I love using Ubuntu for most of our specialized servers in our office (Citadel mail, iFolder, Adito), but as a host for our VM's, I just can't trust VMware.  Unfortuneately I won't be able to switch to VirtualBox either since this Ubuntu Host Server is one of three servers we use for all our VM's (the other 2 are Windows 2003/8).  Looks like I'll have to use Windows as my Host server and run Ubuntu where I can for our VM's.

Maybe now that VMware has bought SUSE we might see VMware work better on Linux?

---

### Post by CharlesA on 2010-09-25
So, you couldn't start the VM manually after a reboot?

I've not tried setting VMware to start a VM automatically after a reboot.

---

### Post by greavette on 2010-09-25
Nope.  I had it setup to automatically start after reboot for me but that didn't work.  So I tried starting it manually and again it didn't work.  Got stuck at 95%.  I then went to restart vmware:

sudo /etc/init.d/vmware restart

But it failed on stopping some services.  I tried the above instruction again and this time it said I needed to reconfigure VMware.  I tried that and it had me remove vmmon, vmnet, vmci before I could reconfigure.  Once I had removed those, VMware could finally be reconfigured and then my VM would start. 

I then tried rebooting again thinking the above was only a 1 time thing.  Same steps had to be taken before I could start my VM.

I'll for now still run some virtual machines from this server, but they won't be critical to our office.

---

### Post by CharlesA on 2010-09-25
Ugh. I seem to recall getting frustrated with VMware after having some problems (which I cannot seem to duplicate now on the same hardware) and just using VirtualBox.

---

### Post by greavette on 2010-09-25
Yep...I would love to dump VMware, but the rest of our Virtual Host servers run VMware with no problems so I would need a very good case to convince the owner to switch everything to Virtualbox.  And I'm unwilling to have Virtualbox only on this server as the reason I have 3 servers is to vary the load and also in case one server has trouble, we still have two to handle our VM's.

Virtualbox is definetely the way to go...but maybe for another day in our office. ;)

I'm just happy that I can run Ubuntu as much as I do for our specialized servers.

Thanks again for all your help CharlesA.

---

### Post by CharlesA on 2010-09-26
I remember running into that same error when I installed VMware on Ubuntu 10.04. I never found a fix for it, unfortunately.

The annoying thing is that if I test VMware on a VM of Ubuntu, it installs fine and doesn't spit back any errors like that and I did the exact same steps.

Originally, I thought I needed to install X on the server but that wasn't the case on the VM, so I just gave up on it and used VirtualBox.

I'm kind of in the same situation, since my work uses ESXi.

---

