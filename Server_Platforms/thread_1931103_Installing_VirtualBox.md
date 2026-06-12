---
title: "Installing VirtualBox"
date: 2012-02-24
forum: Server Platforms
---

### Post by brent1975 on 2012-02-24
Hello. I am looking at installing VirtualBox on my ubuntu 10.04 Server. Anyone have any step by step instruction on how to achieve this task? 

Here is what I am looking for:

The installation of the host it self all the way to loading the first operating system on the first virtual machine.

Any help would be greatly appreciated.

---

### Post by SeijiSensei on 2012-02-25
Follow the instructions for "Debian-based" systems midway down the page at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) to add the VB repository to your server.  Then run "sudo apt-get install virtualbox-4.1" to install it.  Launch the VM manager; on my Kubuntu machine it's in the System area of the menus.  Click on the icon to create a new machine and just follow the dialog boxes.  You'll need a bootable image of the OS you want to install.  You can use a CD/DVD or boot from a .iso file on your hard drive.

Once you got a working machine up and running, follow the instructions [here](https://www.virtualbox.org/manual/ch01.html#intro-installing) to install the extension pack.  

The wizards are very helpful and very complete.  There's more help at virtualbox.org.

---

### Post by Porcini M. on 2012-02-25
I was running some headless virtualbox machines off of Ubuntu Server for a while.. Here's a couple of scripts you can use as a reference:


Show VM info, load & eject ISO:

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


Create & add a new VM:

```
#!/bin/bash -u

TRUE=1
FALSE=0

INSTALL_ISO_NAME="${1}"

VBOXEXE="/usr/bin/VBoxManage"

VMNAME="subsonic"

VMDIR="/home/vbox"

HOST_CPU_IS_INTEL=$TRUE

VHD_SIZE_MB=12000
RAM_SIZE_MB=256
NUM_CPUS=1
HOST_ETH_IFACE="eth0"

if [ $HOST_CPU_IS_INTEL -eq $TRUE ]; then
   INTEL_ONLY_ON="on"
else
   INTEL_ONLY_ON="off"
fi

RDP_PORT=3000



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
                          

#vboxmanage showvminfo subsonic
#vboxmanage storageattach subsonic --storagectl idectl --port 0 --device 0 --type dvddrive --medium none

```


Vbox service script, for starting/stopping VMs (goes in /etc/init.d, then run:
sudo update-rc.d <filename> defaults
):

```
#!/bin/bash

RETVAL=0

start()
{
   echo "[virtual_machines] Starting subsonic..."
   /home/vbox/bin/subsonic.sh
   sleep 2
   echo "[virtual_machines] Starting gateway..."
   /home/vbox/bin/gateway.sh
   if [ $? -ne 0 ]; then
      RETVAL=1
   fi
}

stop()
{
   echo "[virtual_machines] Stopping gateway..."
   /usr/bin/vboxmanage controlvm gateway poweroff
   echo "[virtual_machines] Stopping subsonic..."
   /usr/bin/vboxmanage controlvm subsonic poweroff
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
    echo "[virtual_machines] subsonic =========================================="
    vboxmanage showvminfo subsonic
    echo "[virtual_machines] gateway ==========================================="
    vboxmanage showvminfo gateway
    RETVAL=0
    ;;
  *)
    echo "Usage: virtual_machines {start|stop|restart|status}"
    RETVAL=1
esac

exit

```

Hope that helps!

---

