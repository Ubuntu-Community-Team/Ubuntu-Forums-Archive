---
title: "Multipurpose Home Server: Use virtual servers?"
date: 2013-06-03
forum: Server Platforms
---

### Post by abyrne on 2013-06-03
Hi all,

I'm fairly thrifty when it comes to electronics, so I've been getting by with using a decent-spec (2.4GHz Intel Dual Core w/ 2GB RAM) tower running Ubuntu Server 12.04 as my multi-purpose home server. Right now, its main duties consist of hosting a handful of low traffic websites (2 WordPress and 1 PHP-driven specialized site. Collectively, they never get more than 120 views per day), BitTorrent box, and general-purpose file server. I'm thinking about eventually adding backup server and media server to that list. It's been chugging along quite nicely with those jobs for quite a few months, and I've yet to have any major problems. But lately I've been thinking about security, and I've figured that there may be some security risks when it comes to hosting multiple servers on a single system, especially when the files contained on that server are rather private (family photos, documents, etc).

So my question to you today is: _It it a good strategy to rebuild the server from scratch, separating the software into Xen-based virtual servers?_ 
I would probably end up giving Apache and any other WAN-facing software its own virtual server (and I'm thinking about installing an Ethernet card that would give that virtual server its own port), and then making another virtual server for LAN backup, media server, etc. My security reasoning behind this is simple isolation: if the hacker gets into the virtual server running Apache, then he's isolated from the rest of the servers and the rest of my LAN. Plus, I can experiment with any other services I want to use in the future without having to worry about messing up the rest of the system.

I've played around with Linux and servers for a while now, but I've yet to deal with virtualization like Xen or OpenVZ. I feel like the virtual isolation (combined with firewalling and other good security practices) should keep me relatively solid. And my processor does support hardware virtualization, so I'm guessing the performance hit shouldn't be too bad. If you have any suggestions as to a better way to go about this (virtualization or otherwise), I would sincerely appreciate them.

Thanks!

---

### Post by abyrne on 2013-06-04
Bump. Would this be better in a different section of the forum?

---

### Post by matt_symes on 2013-06-04
Thread moved to **server platforms**.

---

### Post by SeijiSensei on 2013-06-05
I think you're being a bit too paranoid.  Apache has been hardened over two decades and is not a likely target for successful exploits.  Also unless you have online enemies, the chance that your machine would be a target is trivially small.

Nevertheless if you'd like to try virtualization, I suggest VirtualBox.  It's quite easy to install and use.  Follow the [installation instructions]("https://www.virtualbox.org/wiki/Linux_Downloads") on the VB site for "Debian-based" distributions.

---

### Post by abyrne on 2013-06-05
> **SeijiSensei said:**
> I think you're being a bit too paranoid.  Apache has been hardened over two decades and is not a likely target for successful exploits.  Also unless you have online enemies, the chance that your machine would be a target is trivially small.
Thanks for your response! I was just using Apache as an example for any web-facing service, but you're probably right about me being paranoid. The more I think about it, the more I feel like virtualization may be a bit overkill. 

Does anyone else have an opinion on this?

---

### Post by trundlenut on 2013-06-05
I like using virtual machines like you describe more to avoid conflicts and to save me from myself.

If you mess up one thing then it won't take everything else with it.

If you go down the VM route it would probably be worth adding some more memory to the physical machine.

---

### Post by sandyd on 2013-06-05
If your not very bored, and dont want to deal with the commandline, but still want to try virtulization, try Vmware ESXi or Citrix XenServer (both free, but only with windows clients). Also, neither officially support software RAID, and support a limited set of RAID cards. Otherwise, for KVM, use Proxmox, which has a web interface with java-based consoles for VMs. Its based on debian, so anything that can be done on debian can be done on the host.

---

### Post by abyrne on 2013-06-06
> **trundlenut said:**
> I like using virtual machines like you describe more to avoid conflicts and to save me from myself.

If you mess up one thing then it won't take everything else with it.

If you go down the VM route it would probably be worth adding some more memory to the physical machine.

This is another benefit that I have been thinking about. What's your setup like? Do you just have a "Production" VM and an "Experimental" VM? 
 Also, how's the performance hit? I know RAM might be a bit tight, but how does the CPU usage fare in your situation?

[QUOTE=sandyd][COLOR=#000000]If your not very bored, and dont want to deal with the commandline, but still want to try virtulization, try Vmware ESXi or Citrix XenServer (both free, but only with windows clients). Also, neither officially support software RAID, and support a limited set of RAID cards. Otherwise, for KVM, use Proxmox, which has a web interface with java-based consoles for VMs. Its based on debian, so anything that can be done on debian can be done on the host.[/COLOR][/QUOTE]
I don't mind the command line at all, and I'd prefer not to use Windows on a server platform. After a brief glance at their website, Proxmox looks pretty promising. Is there any reason to use KVM over Xen?

---

### Post by sandyd on 2013-06-06
> **abyrne said:**
> This is another benefit that I have been thinking about. What's your setup like? Do you just have a "Production" VM and an "Experimental" VM? 
 Also, how's the performance hit? I know RAM might be a bit tight, but how does the CPU usage fare in your situation?


I don't mind the command line at all, and I'd prefer not to use Windows on a server platform. After a brief glance at their website, Proxmox looks pretty promising. Is there any reason to use KVM over Xen?

You dont really use windows on a server platform - you see the interface that controls the server is windows-based. The server itself runs on a modifed verison of linux.

Generally, all virtulization platforms have their own advantages and disadvantages. Ive never used Xen itself because KVM has always been stable, and Proxmox provided a nice web interface that supports clustering.

Some benchmarks (KVM vs Xen): [http://www.phoronix.com/scan.php?page=article&item=ubuntu1210_xenkvm_preview&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu1210_xenkvm_preview&num=2)

---

### Post by abyrne on 2013-06-06
> **sandyd said:**
> You dont really use windows on a server platform - you see the interface that controls the server is windows-based. The server itself runs on a modifed verison of linux.

Generally, all virtulization platforms have their own advantages and disadvantages. Ive never used Xen itself because KVM has always been stable, and Proxmox provided a nice web interface that supports clustering.

Some benchmarks (KVM vs Xen): [http://www.phoronix.com/scan.php?page=article&item=ubuntu1210_xenkvm_preview&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu1210_xenkvm_preview&num=2)
Oh yes, thank you for clearing that up. I think I'll look into Proxmox a bit more. And thank you for the link as well!

---

### Post by CharlesA on 2013-06-06
> **sandyd said:**
> If your not very bored, and dont want to deal with the commandline, but still want to try virtulization, try Vmware ESXi or Citrix XenServer (both free, but only with windows clients). Also, neither officially support software RAID, and support a limited set of RAID cards. Otherwise, for KVM, use Proxmox, which has a web interface with java-based consoles for VMs. Its based on debian, so anything that can be done on debian can be done on the host.

+1 to proxmox. If I ever reinstall my server, I'll be running that on the host.

Separation of services is handy, but sometimes it is overkill.

---

### Post by tgalati4 on 2013-06-06
You might be better off just setting up a single server (perhaps using a Long Term Release) and running all of your services from that.  If you want to play around, there are a lot of cloud services that have free or low-cost sandboxes that you can play in.  If you like the service then you can either install it on your server or continue to use the cloud version.  That way you always have a stable, running server with your services running 24/7 and cloud services  when you want to experiment.

VM's require a lot of RAM and more maintanence than a single bare metal server.  I would only install one if you wanted to learn about VM's (say learning Xen) and then run your stable server as Dom1 and your sandboxes as Dom2, Dom3, etc.

As far as security, I don't think it really makes a difference. VM's were a handy way of separating services so you could bring down your mail server without killing your print server.  Security and jailing of the VM's is not as well developed as the separation of physical resources on a machine.  So, I would not rely on VM's for security.  If one VM got compromised, I would be concerned about the enire server being compromised. 

You could make backup snapshots of your websites to additional VM's or to Cloud services.  So if a website breaks, you have a quick remedy to switch over.  This doesn't improve security, only uptime if such a mishap occurs.

There are lots of server hardening tutorials.  I would go through those before relying on VM's for hardening.

---

### Post by trundlenut on 2013-06-07
> **abyrne said:**
> This is another benefit that I have been thinking about. What's your setup like? Do you just have a "Production" VM and an "Experimental" VM? 
 Also, how's the performance hit? I know RAM might be a bit tight, but how does the CPU usage fare in your situation?


I setup a "base" VM which I clone when I want to start something new.  Once I have a VM that is ready for production I use snapshots or clone it completely before trying upgrades or tinkering with it.  A couple of times I have been a little too experimental and borked one, but it doesn't really matter as I can roll it back or just delete it.

Generally once I have a working VM on my laptop I copy it to the host it will live on, I only really run the experimental or test ones on the laptop.  The first thing I did when I got this laptop was bump up the ram to 4gb, the cpu is a dual core Turion 64, not the fastest but to be honest most of things I have played with are not very processor intensive so it's been fine.

I changed jobs recently and I haven't needed to do so much computer stuff as I used too.

---

### Post by mr-woof on 2013-06-07
Personally, I love ESXI for this type of thing. My home lab is running on an older quad intel chip with 8gb of ram, I can have quite a few windows servers and clients running without too many problems, it just takes a little while to get going from boot up. :-)  You can also have multiple network cards on different networks with say a smoothwall/ipcop in front

---

### Post by Porcini M. on 2013-06-23
I'm a big fan of separating services into multiple dedicated VMs atop a stable base system. I like to use Virtualbox Headless.

Here are some scripts if you're interested:

vmutil.sh, to see the status of a running machine + load/eject a "dvd":

```
#!/bin/bash

TRUE=1
FALSE=0

VBOXEXE="/usr/bin/VBoxManage"


#DVDCTLNM="idectl"
DVDCTLNM="IDE Controller"

#IDEPORT=0
IDEPORT=1

rptres ()
{
   if [ $1 -eq 0 ]; then
      echo "Ok."
   else
      echo "Failed."
   fi
}

vm_info ()
{
   VMNAME="$1"

   if [ "$VMNAME" != "" ]; then
      $VBOXEXE showvminfo "$VMNAME"
      rptres $?
   else
      echo ""
      echo "Usage:"
      echo ""
      echo "   vm_info <machine name>"
      echo ""
   fi
}

vm_dvd ()
{
   VMNAME="$1"
   CMD="$2"
   ISONAME="$3"

   if [ $CMD = "load" ]; then
      $VBOXEXE storageattach "$VMNAME" --storagectl "$DVDCTLNM" --port $IDEPORT --device 0 --type dvddrive --medium "$ISONAME"
      rptres $?
   elif [ $CMD = "eject" ]; then
      $VBOXEXE storageattach "$VMNAME" --storagectl "$DVDCTLNM" --port $IDEPORT --device 0 --type dvddrive --medium none
      rptres $?
   else
      echo ""
      echo "Usage:"
      echo ""
      echo "   vm_dvd <machine name> load <iso file>"
      echo "   vm_dvd <machine name> eject"
      echo ""
   fi
}

```


Set up a new VM (with running RDP to install the OS):

```
#!/bin/bash -u

TRUE=1
FALSE=0

INSTALL_ISO_NAME="${1}"

VBOXEXE="/usr/bin/VBoxManage"

VMNAME="myMachine"

VMDIR="/home/vbox"

HOST_CPU_IS_INTEL=$TRUE

VHD_SIZE_MB=6000
RAM_SIZE_MB=96
NUM_CPUS=1
HOST_ETH_IFACE="eth0"

if [ $HOST_CPU_IS_INTEL -eq $TRUE ]; then
   INTEL_ONLY_ON="on"
else
   INTEL_ONLY_ON="off"
fi

RDP_PORT=3002



msg ()
{
   echo "[vmbld] ${@}"
}

errmsg ()
{
   msg "${@}"
   exit 1
}

chkres ()
{
   if [ $1 -ne 0 ]; then
      errmsg "Error encountered - aborting."
   fi
}

cmd ()
{
   echo "[vmbld> ${@}"
   ${@}
   chkres $?
}

vbmcmd ()
{
   cmd $VBOXEXE ${@}
}


if [ ! -e $VBOXEXE ]; then
   errmsg "Error - vbox needs installed"
fi

if [ ! -e $VMDIR] || [ ! -d $VMDIR ]; then
   errmsg "Error - vbox directory need set up"
fi

if [ -e "${VMDIR}/${VMNAME}" ]; then
   errmsg "Error - machine dir already exists"
fi

if [ ! -e $INSTALL_ISO_NAME ]; then
   errmsg "Error - ISO image doesn't exist"
fi

vbmcmd createvm --name "$VMNAME" --basefolder "${VMDIR}" --ostype Ubuntu_64 --register

vbmcmd createhd --filename "${VMDIR}/${VMNAME}/${VMNAME}.vdi" --size $VHD_SIZE_MB

vbmcmd storagectl "$VMNAME" --name satactl --add sata --hostiocache off
vbmcmd storagectl "$VMNAME" --name idectl --add ide

vbmcmd storageattach "$VMNAME" --storagectl satactl --port 0 --device 0 --type hdd --medium "${VMDIR}/${VMNAME}/${VMNAME}.vdi"
vbmcmd storageattach "$VMNAME" --storagectl idectl --port 0 --device 0 --type dvddrive --medium "$INSTALL_ISO_NAME"

vbmcmd modifyvm "$VMNAME" --cpus $NUM_CPUS \
                          --memory $RAM_SIZE_MB \
                          --acpi on \
                          --ioapic on \
                          --pae on \
                          --hwvirtex on \
                          --nestedpaging on \
                          --rtcuseutc on \
                          --hwvirtexexcl on \
                          --largepages $INTEL_ONLY_ON \
                          --vtxvpid $INTEL_ONLY_ON \
                          --nic1 bridged \
                          --nictype1 virtio \
                          --bridgeadapter1 $HOST_ETH_IFACE \
                          --audio none \
                          --vrde on \
                          --vrdeport $RDP_PORT \
                          --vrdeauthtype null \
                          --vrdemulticon off


```


Example /etc/init.d script to start VMs as services:

```
#!/bin/bash

### BEGIN INIT INFO
# Provides:          virtual_machines
# Required-Start:    vboxautostart-service vboxweb-service vboxdrv
# Required-Stop:     vboxautostart-service vboxweb-service vboxdrv
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start VMs
# Description:       Start virtual machines
### END INIT INFO


RETVAL=0

start()
{
   echo "[virtual_machines] Starting myMachine..."
   /home/vbox/bin/myMachine.sh
   if [ $? -ne 0 ]; then
      RETVAL=1
   fi
}

stop()
{
   echo "[virtual_machines] Stopping myMachine..."
   /usr/bin/vboxmanage controlvm myMachine poweroff
   if [ $? -ne 0 ]; then
      RETVAL=1
   fi
}

case $1 in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart)
    stop
    start
    ;;
  status)
    echo "[virtual_machines] myMachine ========================================"
    vboxmanage showvminfo myMachine
    RETVAL=0
    ;;
  *)
    echo "Usage: virtual_machines {start|stop|restart|status}"
    RETVAL=1
esac

exit $RETVAL


```

---

