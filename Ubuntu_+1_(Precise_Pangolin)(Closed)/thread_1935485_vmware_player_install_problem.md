---
title: "vmware player install problem"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cwhebert on 2012-03-04
When I try to install vmware player I keep getting this message,
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"
Once installed it tries to compile / load additional modules and fails at network device and goes into an endless loop of wanting me to install the additional modules.  Any ideas?

---

### Post by fjgaude on 2012-03-04
VMware Player doesn't work out-of-the-box with 12.04. See link:

[http://ubuntuforums.org/showthread.php?t=1886604&highlight=vmware+player](http://ubuntuforums.org/showthread.php?t=1886604&highlight=vmware+player)

I used 4.0.1 with the patches. The latest Player, 4.0.2, works with 11.10. You will have to patch as suggested in the link to get 12.04 working with Player. Good luck and happy VMing.

---

### Post by cwhebert on 2012-03-05
> **fjgaude said:**
> VMware Player doesn't work out-of-the-box with 12.04. See link:

[http://ubuntuforums.org/showthread.php?t=1886604&highlight=vmware+player](http://ubuntuforums.org/showthread.php?t=1886604&highlight=vmware+player)

I used 4.0.1 with the patches. The latest Player, 4.0.2, works with 11.10. You will have to patch as suggested in the link to get 12.04 working with Player. Good luck and happy VMing.

Yes, I came across that thread, I guess I was hoping for something a little simpler.  No big deal.  I will try to work with the patch and see how I make out.  Thanks for passing along the information.

---

### Post by fjgaude on 2012-03-05
Go slow, make no typos and you will get there.

effenberg stated twice he was going to make a script to install the patches, but I guess his priorities keep changing. He is a busy fellow. Thanks for the help he provides the forums.

---

### Post by effenberg0x0 on 2012-03-05
> **fjgaude said:**
> Go slow, make no typos and you will get there.

effenberg stated twice he was going to make a script to install the patches, but I guess his priorities keep changing. He is a busy fellow. Thanks for the help he provides the forums.

True, I'm sorry for the delay. I'm actually late on a ton of things. My table is a mess of post-its and piles of paper. Not to mention the unread emails... My current priority is finding the time to go to the bathroom before my kidney fails :) 

The reason is that the IT market is really slow here since January, revenue disappeared, people are sort of panicking. I believe it's cyclical / seasonal, but I had to join the commercial effort. I'm sick of it all. I gotta find a way to quit job #1 and make a living of job #2 (Ubuntu/Linux-related).

I did a script for 4.02 a week or more ago (can't remember), cause the new release wouldn't compile on Kernel 3.2, can't remember who asked me for it at work. It had to download fresh (unpatched sources) and apply different patching. It wouldn't compile because of a macro in linux/kernel_export (THIS_MODULE). I'll check who I sent it to sometime in the early hours and post here if I find it.

Regards,
Effenberg

---

### Post by fjgaude on 2012-03-05
Bless you, man! Thank you again for all you do to assist us poor souls using computers. <smile>

---

### Post by effenberg0x0 on 2012-03-06
Hi, I found it in my email, and took some minutes to make some updates to it. It tests OK in my machine. This is designed for vmware-player 4.0.2 on kernel 3.2.x ok?

Save this file as **vmware-autopatcher.sh** in your "Downloads" directory. 
```

#!/usr/bin/env bash
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
#set -x
#set -v
#Eclipse BASH Template#####################################################START
#
# vmware-autopatcher.sh
#
# A simple script to auto patch vmware-player. It is hardcoded to vmware-player
# 4.02 on kernel 3.2.x so far. Check the "a1" version for testing dynamic
# patching.
#
# USAGE: 
# $ sudo chmod +x vmware-autopatcher.sh
# $ sudo ./vmware-autopatcher.sh
#
# This is a BASH SCRIPT. Please don't ask me how to use it on Windows.
################################################################################
# Alvaro "Effenberg0x0" Leal <Effenberg0x0@Gmail.com> Mar, 2012
#############################################################################END

##ADJUSTABLE GLOBAL VARIABLES

##TEMPLATE GLOBALS
SW_NAME="vmware-autopatcher"
SW_SCRIPT_NAME="vmware-autopatcher.sh"
SW_VERSION="0.1"
SW_AUTHOR="Alvaro \"Effenberg0x0\" Leal"
SW_AUTHOR_WEB="https://launchpad.net/~effenberg0x0"
SW_AUTHOR_EMAIL="effenberg0x0@gmail.com"

#GLOBALS
VMWARE_PLAYER_TARGET_VERSION="4.0.2"
KERNEL_TARGET_VERSION="3.2.0"
PATCH_NAME="vmware_${VMWARE_PLAYER_TARGET_VERSION}_patch_${KERNEL_TARGET_VERSION}.patch"
VMWARE_PLAYER_SOURCES_DIR="/usr/lib/vmware/modules/source"

ensureBash() {
  ## PROVIDED BY: EBS
  # ensureBash()
  # Function keyword omitted for dash compatibility. This will likely be the 
  # first ran function.
  # Makes sure the script is being run by bash and not dash or other
  # interpreter. It uses bash builtins, as the availability of common system
  # tools is unknown.
  # $BASH, $BASHPID and $SHELL are useful bash specifics: $BASH is only
  # exported by bash, and holds the path for bash (e.g. /bin/bash)

  echo -e ""
  echo -e "Checking for BASH as the script interpreter..."
  if [ -z $BASH ]; then
    # Not using bash. Exit gracefully.
    # echo is a safe bash/dash builtin.
    echo -e ""
    echo -e "${SW_NAME} requires bash as its interpreter."
    echo -e "Invoke ${SW_NAME} with \$ sudo bash ${SW_SCRIPT_NAME} or"
    echo -e "#bash ${SW_SCRIPT_NAME} (as root)."
    echo -e "Use the --help option \($ sudo bash ${SW_SCRIPT_NAME} --help\) for"
    echo -e "a list of options."
    echo -e ""
    exit 1
  else
    return 0
  fi
}

function checkRoot() {
  ## PROVIDED-BY: EBS
  # checkRoot()
  # Makes sure that the script is being invoked by root or a suid/sudo user.
  # Avoids using the command 'id' by using builtins like uid/euid
  # Rely exclusively on bash builtins for this function

  echo -e "Checking for root permissions..."
  if [ ${UID} -ne 0 ]; then
    echo -e ""
    echo -e "${SW_NAME} needs root permissions."
    echo -e "Invoke ${SW_NAME} with \$ sudo bash ${SW_SCRIPT_NAME} or"
    echo -e "#bash ${SW_SCRIPT_NAME} (as root)."
    echo -e ""
    exit 1
  else
    return 0
  fi
}

function checkVmwarePids() {
  echo -e ""
  echo -e "Checking for running VMware Processes..."
  vmware_pids=$(ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}' | wc -l)
  if [[ ${vmware_pids} -ne 0 ]]; then
    echo -e ""
    echo -e "There are VMware processed running. Please stop them before proceeding. Exiting..."
    exit 1
  fi  
}
 
function checkVmwarePlayerVersion() {
  vmware_player_installed_version=$(vmplayer --version | awk 'BEGIN {FS=" "} {print $3}')
  if [[ ${vmware_player_installed_version} != ${VMWARE_PLAYER_TARGET_VERSION} ]]; then
    echo -e ""
    echo -e "This patch is designed for vmware-player version ${VMWARE_PLAYER_TARGET_VERSION}. The currently installed version is ${vmware_player_installed_version}. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "vmware-player version match. Proceeding...."
  fi    
}

function checkWorkDir() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}"
  mkdir -p "${patch_dir}"
  if [[ ! -d ${patch_dir} ]]; then
    echo -e ""
    echo -e "Could not create work dir ${patch_dir}. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "Work dir ${patch_dir} succesfully created. Proceeding..."
  fi
}
      
function movePatchAndScript() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}/"
  echo -e ""
  echo -e "Copying script to work dir ${patch_dir}"
  cp ./${SW_SCRIPT_NAME} ${patch_dir}
  if [[ $? -ne 0 ]]; then
    echo -e ""
    echo -e "Could not copy script to work dir ${patch_dir}. Exiting..."
    exit 1   
  else
    echo -e ""
    echo -e "Succesfully copied the script to the work dir ${patch_dir}. Proceeding..."
  fi  
  echo -e ""
  echo -e "Checking for patch file ${PATCH_NAME}..."
  if [[ ! -e ${PATCH_NAME} ]]; then
    echo -e ""
    echo -e "Patch ${PATCH_NAME} not found. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "Patch found. Proceeding..."
  fi
  echo -e "Copying patch to work dir ${patch_dir}"
  cp ./${PATCH_NAME} ${patch_dir}
  if [[ $? -ne 0 ]]; then
    echo -e ""
    echo -e "Could not copy patch to work dir ${patch_dir}. Exiting..."
    exit 1   
  else
    echo -e ""
    echo -e "Succesfully copied the patch to the work dir ${patch_dir}. Proceeding..."
  fi  
}  
  
function checkVmwareSourcesDir() {
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")
  
  if [[ -d ${VMWARE_PLAYER_SOURCES_DIR} ]]; then
    for ((i=0; i<${#sources_tars[@]}; i++)); do
      if [[ ! -e ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} ]]; then
        echo -e ""     
        echo -e "Could not locate vmware-player source tar ${sources_tars[$i]}. Exiting..."
        exit 1
      fi  
    done
      echo -e ""     
      echo -e "All sources tars found. Proceeding..."
  else
    echo -e ""     
    echo -e "Could not locate vmware-player sources directory at a standard location. Exiting..."
    exit 1
  fi  
}

function backupCurrentTars() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}/"
  local timestamp=$(date +%d-%m-%Y_%H:%m:%S)
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")

  echo -e ""
  echo -e "Creating backup diretory at ${patch_dir}${timestamp}..."
  mkdir -p "${patch_dir}/${timestamp}"
  if [[ $? -ne 0 ]]; then
    echo -e "Could not create backup dir ${patch_dir}${timestamp}. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "Backup dir ${patch_dir}${timestamp} succesfully created. Proceeding..."
  fi
  
  echo -e "Making backups of current source tars at ${patch_dir}/${timestamp}..." 
  for ((i=0; i<${#sources_tars[@]}; i++)); do
    cp ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} "${patch_dir}${timestamp}"
    if [[ ! -e "${patch_dir}${timestamp}/${sources_tars[$i]}" ]]; then
      echo -e ""     
      echo -e "Could not backup source tar ${sources_tars[$i]}. Exiting..."
      exit 1
    fi  
  done
  echo -e ""     
  echo -e "Finished making backups at ${patch_dir}${timestamp}. Proceeding..."
}  

function untarSources() {
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")
  
  for ((i=0; i<${#sources_tars[@]}; i++)); do
    if [[ -e ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} ]]; then
      tar -xvf ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} -C ${VMWARE_PLAYER_SOURCES_DIR}
      if [[ $? -ne 0 ]]; then
        echo -e ""
        echo -e "Could not untar source ${sources_tars[$i]}. Exiting..."
        exit 1
      else
        echo -e ""
        echo -e "Source ${sources_tars[$i]} untared. Proceeding..."
      fi         
    else
      echo -e ""
      echo -e "Could not find source ${sources_tars[$i]}. Exiting..."
      exit 1
    fi
  done
}
      
function patchSources() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}/"

  echo -e ""
  echo -e "Applying patches to sources..."
  echo -e "Testing a dry-run first"
  patch --dry-run -p0 -i "${patch_dir}${PATCH_NAME}"
  #if [[ $? -ne 100 ]]; then
   # echo -e ""
   # echo -e "Error applying patches. Exiting..."
   # exit 1
  #else
    echo -e ""
    echo -e "Dry-run succesful. Applying patches to sources..."
    #patch -p0 -i "${patch_dir}${PATCH_NAME}"    
  #fi
}  

function tarSources() {
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")
  declare -a sources_dirs=("vmblock-only" "vmci-only" "vmmon-only" "vmnet-only" "vsock-only")  
  for ((i=0; i<${#sources_dirs[@]}; i++)); do
    if [[ -e ${VMWARE_PLAYER_SOURCES_DIR}/${sources_dirs[$i]} ]]; then
      cd ${VMWARE_PLAYER_SOURCES_DIR}
      tar cf ${sources_tars[$i]} ${sources_dirs[$i]}
      if [[ $? -ne 0 ]]; then
        echo -e ""
        echo -e "Could not tar source dir ${sources_dirs[$i]}. Exiting..."
        exit 1
      else
        echo -e ""
        echo -e "Source dir ${sources_dirs[$i]} tared. Proceeding..."
      fi         
    else
      echo -e ""
      echo -e "Could not find source dir ${sources_dirs[$i]}. Exiting..."
      exit 1
    fi
  done
}

function buildModules() {
  echo -e ""
  echo -e "Building patched kernel modules..."
  vmware-modconfig --console --install-all
  echo -e ""
  echo -e "Start vmware-player now"
}


function main() {
  ensureBash
  checkRoot
  checkVmwarePids
  checkVmwarePlayerVersion
  checkWorkDir
  movePatchAndScript
  checkVmwareSourcesDir
  backupCurrentTars
  untarSources
  patchSources
  tarSources
  buildModules
}


case $1 in 
  *)
  main
  ;;
esac          

```

Save this one as **vmware_4.0.2_patch_3.2.0.patch** in the same directory as the previous one"
```

--- /usr/lib/vmware/modules/source/vmnet-only/filter.c    2012-02-26 13:00:05.000000000 +0100
+++ /usr/lib/vmware/modules/source/vmnet-only/filter.c    2012-02-28 15:11:12.000000000 +0100
@@ -40,6 +40,10 @@
 #include "vnetInt.h"
 #include "vmnetInt.h"
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+#include <linux/export.h>
+#endif
+
 // VNet_FilterLogPacket.action for dropped packets
 #define VNET_FILTER_ACTION_DRP         (1)
 #define VNET_FILTER_ACTION_DRP_SHORT   (2)
--- /usr/lib/vmware/modules/source/vmnet-only/netif.c    2012-02-26 13:02:06.000000000 +0100
+++ /usr/lib/vmware/modules/source/vmnet-only/netif.c    2012-02-28 15:05:11.000000000 +0100
@@ -62,7 +62,9 @@
 static int  VNetNetifStartXmit(struct sk_buff *skb, struct net_device *dev);
 static struct net_device_stats *VNetNetifGetStats(struct net_device *dev);
 static int  VNetNetifSetMAC(struct net_device *dev, void *addr);
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 static void VNetNetifSetMulticast(struct net_device *dev);
+#endif
 #if 0
 static void VNetNetifTxTimeout(struct net_device *dev);
 #endif
@@ -131,7 +133,9 @@
       .ndo_stop = VNetNetifClose,
       .ndo_get_stats = VNetNetifGetStats,
       .ndo_set_mac_address = VNetNetifSetMAC,
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
       .ndo_set_multicast_list = VNetNetifSetMulticast,
+#endif
       /*
        * We cannot stuck... If someone will report problems under
        * low memory conditions or some such, we should enable it.
@@ -611,12 +615,12 @@
  *
  *----------------------------------------------------------------------
  */
-
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 void
 VNetNetifSetMulticast(struct net_device *dev) // IN: unused
 {
 }
-
+#endif
 
 /*
  *----------------------------------------------------------------------
--- /usr/lib/vmware/modules/source/vmnet-only/userif.c    2012-02-26 13:06:09.000000000 +0100
+++ /usr/lib/vmware/modules/source/vmnet-only/userif.c    2012-02-28 15:09:31.000000000 +0100
@@ -517,10 +517,18 @@
      unsigned int tmpCsum;
      const void *vaddr;
 
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) && LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+         vaddr = kmap(skb_frag_page(frag));
+#else
      vaddr = kmap(frag->page);
+#endif
      tmpCsum = csum_and_copy_to_user(vaddr + frag->page_offset,
                      curr, frag->size, 0, &err);
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) && LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+         kunmap(skb_frag_page(frag));
+#else
      kunmap(frag->page);
+#endif
      if (err) {
         return err;
      }

```

Then cd to the directory you saved them (cd ~/Downloads, for example)
Make the script executable:
```
sudo chmod +x vmware-autopatcher.sh
```
And run it with sudo:
```
sudo ./vmware-autopatcher.sh
```

That's it, it doesn't take long. Keep an eye on the screen as it may ask you a thing or two while patching.

Regards,
Effenberg

---

### Post by fjgaude on 2012-03-06
Great! And thank you, Effenberg, once again! I'm sure many are grateful for your work. CWHebert will be happy.

I see only one file has to be patched using 4.0.2. Wonderful!

---

### Post by cwhebert on 2012-03-06
> **fjgaude said:**
> Great! And thank you, Effenberg, once again! I'm sure many are grateful for your work. CWHebert will be happy.

I see only one file has to be patched using 4.0.2. Wonderful!

Happy is not the word, this is fantastic!  I am off to run the script and get my vmware-player up and running.  

I too thank Effenberg.

---

### Post by cwhebert on 2012-03-06
> **effenberg0x0 said:**
> Hi, I found it in my email, and took some minutes to make some updates to it. It tests OK in my machine. This is designed for vmware-player 4.0.2 on kernel 3.2.x ok?

Save this file as **vmware-autopatcher.sh** in your "Downloads" directory. 
```

#!/usr/bin/env bash
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
#set -x
#set -v
#Eclipse BASH Template#####################################################START
#
# vmware-autopatcher.sh
#
# A simple script to auto patch vmware-player. It is hardcoded to vmware-player
# 4.02 on kernel 3.2.x so far. Check the "a1" version for testing dynamic
# patching.
#
# USAGE: 
# $ sudo chmod +x vmware-autopatcher.sh
# $ sudo ./vmware-autopatcher.sh
#
# This is a BASH SCRIPT. Please don't ask me how to use it on Windows.
################################################################################
# Alvaro "Effenberg0x0" Leal <Effenberg0x0@Gmail.com> Mar, 2012
#############################################################################END

##ADJUSTABLE GLOBAL VARIABLES

##TEMPLATE GLOBALS
SW_NAME="vmware-autopatcher"
SW_SCRIPT_NAME="vmware-autopatcher.sh"
SW_VERSION="0.1"
SW_AUTHOR="Alvaro \"Effenberg0x0\" Leal"
SW_AUTHOR_WEB="https://launchpad.net/~effenberg0x0"
SW_AUTHOR_EMAIL="effenberg0x0@gmail.com"

#GLOBALS
VMWARE_PLAYER_TARGET_VERSION="4.0.2"
KERNEL_TARGET_VERSION="3.2.0"
PATCH_NAME="vmware_${VMWARE_PLAYER_TARGET_VERSION}_patch_${KERNEL_TARGET_VERSION}.patch"
VMWARE_PLAYER_SOURCES_DIR="/usr/lib/vmware/modules/source"

ensureBash() {
  ## PROVIDED BY: EBS
  # ensureBash()
  # Function keyword omitted for dash compatibility. This will likely be the 
  # first ran function.
  # Makes sure the script is being run by bash and not dash or other
  # interpreter. It uses bash builtins, as the availability of common system
  # tools is unknown.
  # $BASH, $BASHPID and $SHELL are useful bash specifics: $BASH is only
  # exported by bash, and holds the path for bash (e.g. /bin/bash)

  echo -e ""
  echo -e "Checking for BASH as the script interpreter..."
  if [ -z $BASH ]; then
    # Not using bash. Exit gracefully.
    # echo is a safe bash/dash builtin.
    echo -e ""
    echo -e "${SW_NAME} requires bash as its interpreter."
    echo -e "Invoke ${SW_NAME} with \$ sudo bash ${SW_SCRIPT_NAME} or"
    echo -e "#bash ${SW_SCRIPT_NAME} (as root)."
    echo -e "Use the --help option \($ sudo bash ${SW_SCRIPT_NAME} --help\) for"
    echo -e "a list of options."
    echo -e ""
    exit 1
  else
    return 0
  fi
}

function checkRoot() {
  ## PROVIDED-BY: EBS
  # checkRoot()
  # Makes sure that the script is being invoked by root or a suid/sudo user.
  # Avoids using the command 'id' by using builtins like uid/euid
  # Rely exclusively on bash builtins for this function

  echo -e "Checking for root permissions..."
  if [ ${UID} -ne 0 ]; then
    echo -e ""
    echo -e "${SW_NAME} needs root permissions."
    echo -e "Invoke ${SW_NAME} with \$ sudo bash ${SW_SCRIPT_NAME} or"
    echo -e "#bash ${SW_SCRIPT_NAME} (as root)."
    echo -e ""
    exit 1
  else
    return 0
  fi
}

function checkVmwarePids() {
  echo -e ""
  echo -e "Checking for running VMware Processes..."
  vmware_pids=$(ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}' | wc -l)
  if [[ ${vmware_pids} -ne 0 ]]; then
    echo -e ""
    echo -e "There are VMware processed running. Please stop them before proceeding. Exiting..."
    exit 1
  fi  
}
 
function checkVmwarePlayerVersion() {
  vmware_player_installed_version=$(vmplayer --version | awk 'BEGIN {FS=" "} {print $3}')
  if [[ ${vmware_player_installed_version} != ${VMWARE_PLAYER_TARGET_VERSION} ]]; then
    echo -e ""
    echo -e "This patch is designed for vmware-player version ${VMWARE_PLAYER_TARGET_VERSION}. The currently installed version is ${vmware_player_installed_version}. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "vmware-player version match. Proceeding...."
  fi    
}

function checkWorkDir() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}"
  mkdir -p "${patch_dir}"
  if [[ ! -d ${patch_dir} ]]; then
    echo -e ""
    echo -e "Could not create work dir ${patch_dir}. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "Work dir ${patch_dir} succesfully created. Proceeding..."
  fi
}
      
function movePatchAndScript() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}/"
  echo -e ""
  echo -e "Copying script to work dir ${patch_dir}"
  cp ./${SW_SCRIPT_NAME} ${patch_dir}
  if [[ $? -ne 0 ]]; then
    echo -e ""
    echo -e "Could not copy script to work dir ${patch_dir}. Exiting..."
    exit 1   
  else
    echo -e ""
    echo -e "Succesfully copied the script to the work dir ${patch_dir}. Proceeding..."
  fi  
  echo -e ""
  echo -e "Checking for patch file ${PATCH_NAME}..."
  if [[ ! -e ${PATCH_NAME} ]]; then
    echo -e ""
    echo -e "Patch ${PATCH_NAME} not found. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "Patch found. Proceeding..."
  fi
  echo -e "Copying patch to work dir ${patch_dir}"
  cp ./${PATCH_NAME} ${patch_dir}
  if [[ $? -ne 0 ]]; then
    echo -e ""
    echo -e "Could not copy patch to work dir ${patch_dir}. Exiting..."
    exit 1   
  else
    echo -e ""
    echo -e "Succesfully copied the patch to the work dir ${patch_dir}. Proceeding..."
  fi  
}  
  
function checkVmwareSourcesDir() {
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")
  
  if [[ -d ${VMWARE_PLAYER_SOURCES_DIR} ]]; then
    for ((i=0; i<${#sources_tars[@]}; i++)); do
      if [[ ! -e ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} ]]; then
        echo -e ""     
        echo -e "Could not locate vmware-player source tar ${sources_tars[$i]}. Exiting..."
        exit 1
      fi  
    done
      echo -e ""     
      echo -e "All sources tars found. Proceeding..."
  else
    echo -e ""     
    echo -e "Could not locate vmware-player sources directory at a standard location. Exiting..."
    exit 1
  fi  
}

function backupCurrentTars() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}/"
  local timestamp=$(date +%d-%m-%Y_%H:%m:%S)
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")

  echo -e ""
  echo -e "Creating backup diretory at ${patch_dir}${timestamp}..."
  mkdir -p "${patch_dir}/${timestamp}"
  if [[ $? -ne 0 ]]; then
    echo -e "Could not create backup dir ${patch_dir}${timestamp}. Exiting..."
    exit 1
  else
    echo -e ""
    echo -e "Backup dir ${patch_dir}${timestamp} succesfully created. Proceeding..."
  fi
  
  echo -e "Making backups of current source tars at ${patch_dir}/${timestamp}..." 
  for ((i=0; i<${#sources_tars[@]}; i++)); do
    cp ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} "${patch_dir}${timestamp}"
    if [[ ! -e "${patch_dir}${timestamp}/${sources_tars[$i]}" ]]; then
      echo -e ""     
      echo -e "Could not backup source tar ${sources_tars[$i]}. Exiting..."
      exit 1
    fi  
  done
  echo -e ""     
  echo -e "Finished making backups at ${patch_dir}${timestamp}. Proceeding..."
}  

function untarSources() {
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")
  
  for ((i=0; i<${#sources_tars[@]}; i++)); do
    if [[ -e ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} ]]; then
      tar -xvf ${VMWARE_PLAYER_SOURCES_DIR}/${sources_tars[$i]} -C ${VMWARE_PLAYER_SOURCES_DIR}
      if [[ $? -ne 0 ]]; then
        echo -e ""
        echo -e "Could not untar source ${sources_tars[$i]}. Exiting..."
        exit 1
      else
        echo -e ""
        echo -e "Source ${sources_tars[$i]} untared. Proceeding..."
      fi         
    else
      echo -e ""
      echo -e "Could not find source ${sources_tars[$i]}. Exiting..."
      exit 1
    fi
  done
}
      
function patchSources() {
  local patch_dir="${HOME}/vmware-patch/${VMWARE_PLAYER_TARGET_VERSION}/${KERNEL_TARGET_VERSION}/"

  echo -e ""
  echo -e "Applying patches to sources..."
  echo -e "Testing a dry-run first"
  patch --dry-run -p0 -i "${patch_dir}${PATCH_NAME}"
  #if [[ $? -ne 100 ]]; then
   # echo -e ""
   # echo -e "Error applying patches. Exiting..."
   # exit 1
  #else
    echo -e ""
    echo -e "Dry-run succesful. Applying patches to sources..."
    #patch -p0 -i "${patch_dir}${PATCH_NAME}"    
  #fi
}  

function tarSources() {
  declare -a sources_tars=("vmblock.tar" "vmci.tar" "vmmon.tar" "vmnet.tar" "vsock.tar")
  declare -a sources_dirs=("vmblock-only" "vmci-only" "vmmon-only" "vmnet-only" "vsock-only")  
  for ((i=0; i<${#sources_dirs[@]}; i++)); do
    if [[ -e ${VMWARE_PLAYER_SOURCES_DIR}/${sources_dirs[$i]} ]]; then
      cd ${VMWARE_PLAYER_SOURCES_DIR}
      tar cf ${sources_tars[$i]} ${sources_dirs[$i]}
      if [[ $? -ne 0 ]]; then
        echo -e ""
        echo -e "Could not tar source dir ${sources_dirs[$i]}. Exiting..."
        exit 1
      else
        echo -e ""
        echo -e "Source dir ${sources_dirs[$i]} tared. Proceeding..."
      fi         
    else
      echo -e ""
      echo -e "Could not find source dir ${sources_dirs[$i]}. Exiting..."
      exit 1
    fi
  done
}

function buildModules() {
  echo -e ""
  echo -e "Building patched kernel modules..."
  vmware-modconfig --console --install-all
  echo -e ""
  echo -e "Start vmware-player now"
}


function main() {
  ensureBash
  checkRoot
  checkVmwarePids
  checkVmwarePlayerVersion
  checkWorkDir
  movePatchAndScript
  checkVmwareSourcesDir
  backupCurrentTars
  untarSources
  patchSources
  tarSources
  buildModules
}


case $1 in 
  *)
  main
  ;;
esac          

```

Save this one as **vmware_4.0.2_patch_3.2.0.patch** in the same directory as the previous one"
```

--- /usr/lib/vmware/modules/source/vmnet-only/filter.c    2012-02-26 13:00:05.000000000 +0100
+++ /usr/lib/vmware/modules/source/vmnet-only/filter.c    2012-02-28 15:11:12.000000000 +0100
@@ -40,6 +40,10 @@
 #include "vnetInt.h"
 #include "vmnetInt.h"
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+#include <linux/export.h>
+#endif
+
 // VNet_FilterLogPacket.action for dropped packets
 #define VNET_FILTER_ACTION_DRP         (1)
 #define VNET_FILTER_ACTION_DRP_SHORT   (2)
--- /usr/lib/vmware/modules/source/vmnet-only/netif.c    2012-02-26 13:02:06.000000000 +0100
+++ /usr/lib/vmware/modules/source/vmnet-only/netif.c    2012-02-28 15:05:11.000000000 +0100
@@ -62,7 +62,9 @@
 static int  VNetNetifStartXmit(struct sk_buff *skb, struct net_device *dev);
 static struct net_device_stats *VNetNetifGetStats(struct net_device *dev);
 static int  VNetNetifSetMAC(struct net_device *dev, void *addr);
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 static void VNetNetifSetMulticast(struct net_device *dev);
+#endif
 #if 0
 static void VNetNetifTxTimeout(struct net_device *dev);
 #endif
@@ -131,7 +133,9 @@
       .ndo_stop = VNetNetifClose,
       .ndo_get_stats = VNetNetifGetStats,
       .ndo_set_mac_address = VNetNetifSetMAC,
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
       .ndo_set_multicast_list = VNetNetifSetMulticast,
+#endif
       /*
        * We cannot stuck... If someone will report problems under
        * low memory conditions or some such, we should enable it.
@@ -611,12 +615,12 @@
  *
  *----------------------------------------------------------------------
  */
-
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 void
 VNetNetifSetMulticast(struct net_device *dev) // IN: unused
 {
 }
-
+#endif
 
 /*
  *----------------------------------------------------------------------
--- /usr/lib/vmware/modules/source/vmnet-only/userif.c    2012-02-26 13:06:09.000000000 +0100
+++ /usr/lib/vmware/modules/source/vmnet-only/userif.c    2012-02-28 15:09:31.000000000 +0100
@@ -517,10 +517,18 @@
      unsigned int tmpCsum;
      const void *vaddr;
 
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) && LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+         vaddr = kmap(skb_frag_page(frag));
+#else
      vaddr = kmap(frag->page);
+#endif
      tmpCsum = csum_and_copy_to_user(vaddr + frag->page_offset,
                      curr, frag->size, 0, &err);
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) && LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+         kunmap(skb_frag_page(frag));
+#else
      kunmap(frag->page);
+#endif
      if (err) {
         return err;
      }

```

Then cd to the directory you saved them (cd ~/Downloads, for example)
Make the script executable:
```
sudo chmod +x vmware-autopatcher.sh
```
And run it with sudo:
```
sudo ./vmware-autopatcher.sh
```

That's it, it doesn't take long. Keep an eye on the screen as it may ask you a thing or two while patching.

Regards,
Effenberg

Thank you, thank you, thank you.

---

### Post by cwhebert on 2012-03-06
Effenberg, I followed your instructions, however,when I run the script I get the following message: Checking for BASH as the script interpreter...
Checking for root permissions...

Checking for running VMware Processes...

There are VMware processed running. Please stop them before proceeding. Exiting...

I have tried the script with vmware-player installed and then I uninstalled it and tried the script again.  I am using the command line: sudo ./vmware-autopatcher.sh

Thanks again for your help

---

### Post by fjgaude on 2012-03-06
> **cwhebert said:**
> Effenberg, I followed your instructions, however,when I run the script I get the following message: Checking for BASH as the script interpreter...
Checking for root permissions...

Checking for running VMware Processes...

There are VMware processed running. Please stop them before proceeding. Exiting...

I have tried the script with vmware-player installed and then I uninstalled it and tried the script again.  I am using the command line: sudo ./vmware-autopatcher.sh

Thanks again for your help

Is it all working now?

---

### Post by effenberg0x0 on 2012-03-06
Hi,

vmware-modconfig fails if it finds any vmware process still running. This is something I can't control. 
So, before it fails, my script checks for such processes with:[FONT=monospace]
[/FONT]```
ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}'
```

You can run is manually, just paste it in a terminal. It outputs a list of vmware-related PIDs. If nothing else works, just kill these processes with something like:
```
sudo kill -s KILL (fill in the PIDs)

```
Test again to see if all PIDs were killed:
```
ps ax | grep -i vmware
```

When all are killed, then run the script again from start. 

Regards,
Effenberg

---

### Post by fjgaude on 2012-03-06
Hey, effenberg, I think Hebert must have it working. His last reply seemed ambiguous though. I have no issues here.

He did run the -u uninstall of VMware. So, he's likely good to go.

Thanks again, man!

---

### Post by cwhebert on 2012-03-06
> **fjgaude said:**
> Is it all working now?

No, I need to kill all vmware processes even thought I uninstalled the vmware-player and rebooted.  I will give a go later tonight.  I post my results, however, I am still very thankful for all the help.  I am confident that I will get vmware-player working.

---

### Post by cwhebert on 2012-03-06
> **effenberg0x0 said:**
> Hi,

vmware-modconfig fails if it finds any vmware process still running. This is something I can't control. 
So, before it fails, my script checks for such processes with:[FONT=monospace]
[/FONT]```
ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}'
```

You can run is manually, just paste it in a terminal. It outputs a list of vmware-related PIDs. If nothing else works, just kill these processes with something like:
```
sudo kill -s KILL (fill in the PIDs)

```
Test again to see if all PIDs were killed:
```
ps ax | grep -i vmware
```

When all are killed, then run the script again from start. 

Regards,
Effenberg

When I run: ps ax | grep -i vmware, this is the results I get:  

2376 pts/1    R+     0:00 grep --color=auto -i vmware

How do I kill this process?

Here is what I'm seeing in my terminal window: 

jan@jan-A770M-A:~/Downloads$ ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}'
2391
jan@jan-A770M-A:~/Downloads$ sudo kill -s Kill 2391
kill: No such process
jan@jan-A770M-A:~/Downloads$ ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}'
2396
jan@jan-A770M-A:~/Downloads$ sudo kill -s Kill 2396
kill: No such process

I guess you can tell I'm a bit lost.

---

### Post by effenberg0x0 on 2012-03-06
Ah, please don't shoot me, my mistake guys....
Open my script on gedit, and find this function:
```

function checkVmwarePids() {   
     echo -e ""   
     echo -e "Checking for running VMware Processes..."   
     vmware_pids=$(ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}' | wc -l)   
     if [[ ${vmware_pids} -ne 0 ]]; then     
         echo -e ""     
         echo -e "There are VMware processed running. Please stop them before proceeding. Exiting..."     
         exit 1   
      fi
}   
}
```Replace this line: 
```
if [[ ${vmware_pids} -ne 0 ]]; then

```with this:```
if [[ ${vmware_pids} -gt 1 ]]; then
```
Save the file and run it again.
Tell me if it does get past the VMWare PIDs message. If so I'll edit the code in the original post with this fix.

Thanks,
Effenberg

---

### Post by cwhebert on 2012-03-06
> **effenberg0x0 said:**
> Ah, please don't shoot me, my mistake guys....
Open my script on gedit, and find this function:
```

function checkVmwarePids() {   
     echo -e ""   
     echo -e "Checking for running VMware Processes..."   
     vmware_pids=$(ps ax | grep -i vmware | awk 'BEGIN {FS=" "} {print $1}' | wc -l)   
     if [[ ${vmware_pids} -ne 0 ]]; then     
         echo -e ""     
         echo -e "There are VMware processed running. Please stop them before proceeding. Exiting..."     
         exit 1   
      fi
}   
}
```Replace this line: 
```
if [[ ${vmware_pids} -ne 0 ]]; then

```with this:```
if [[ ${vmware_pids} -gt 1 ]]; then
```
Save the file and run it again.
Tell me if it does get past the VMWare PIDs message. If so I'll edit the code in the original post with this fix.

Thanks,
Effenberg

I made the change, however, I still getting vmware process running: 


jan@jan-A770M-A:~/Downloads$ sudo chmod +x vmware-autopatcher.sh
jan@jan-A770M-A:~/Downloads$ sudo ./vmware-autopatcher.sh

Checking for BASH as the script interpreter...
Checking for root permissions...

Checking for running VMware Processes...

There are VMware processed running. Please stop them before proceeding. Exiting...
jan@jan-A770M-A:~/Downloads$ sudo chmod +x vmware-autopatcher.sh
jan@jan-A770M-A:~/Downloads$ sudo ./vmware-autopatcher.sh

Checking for BASH as the script interpreter...
Checking for root permissions...

Checking for running VMware Processes...

There are VMware processed running. Please stop them before proceeding. Exiting...

I've attached the edited patch so you can verify I put the change in the right place.  I currently have vmware-player uninstalled.  Thanks again for your time and help.

---

### Post by mjbright on 2012-03-08
Hi, I think the problem is that ps is detecting the vmware-autopatcher itself.

I changed the ps line to be:

     vmware_pids=$(ps ax | grep -i vmware | grep -v vmware-autopatcher | grep -v grep | awk 'BEGIN {FS=" "} {print $1}' | wc -l)


... now I have the problem that it refuses to patch my non-4.0.2 version ... let's have a look.

---

### Post by effenberg0x0 on 2012-03-08
Hi mjbright,

Yea, that's one of the problems. The thing is, no matter if you stop vmware "stoppable" services, you always have at least two services running. Dependinh on which vmware products are installed, you might have more. And these running services won't let you use vmware-modconfig. vmware-installer practically uninstall and reinstall al products every time, which is not an alternative...

So, essentially, you always have to kill vmware processes, which is not very safe in terms of machine stability. But anyway, regarding exclusively the script and remaining PIDs issue, disregarding risks and etc, I was working in something like this:

```

function checkVmwarePids() {
  func_arg=$1
  vmware_pids=$(ps ax | grep -i vmware | grep -v 'grep' | awk 'BEGIN {FS=" "} {print $1" "$5}' | grep -i 'vmware' | awk 'BEGIN {FS=" "} {print $1}' | tr "\n" " ")
  vmware_pid_count=$(ps ax | grep -i vmware | grep -v 'grep' | awk 'BEGIN {FS=" "} {print $1" "$5}' | grep -i 'vmware' | awk 'BEGIN {FS=" "} {print $1}' | tr "\n" " " | wc -w)

  if [[ "${func_arg}" == "force-proceed" ]]; then
    force_proceed="true"
    echo -e "force-proceed activated"
  else
    force_proceed="false"
    echo -e "force-proceed not activated"
  fi
          
  echo -e ""
  echo -e "Checking for running VMware Processes..."
  if [[ ${vmware_pid_count} -gt 0 ]]; then
    echo -e ""
    echo -e "There are VMware processes running."
    if [[ "${force_proceed}" == "false" ]]; then
      echo -e "Kill them before proceeding. Exiting..."
      exit 1
    else
      echo -e "force-proceed activated. We will initially attempt to gracefully stop all VMware processes..."      
      max_stop_attempts=3
      stop_attempts=1
      while [[ ${vmware_pid_count} -ne 0 && ${stop_attempts} -le ${max_stop_attempts} ]]; do
        echo -e "Attempt ${stop_attempts} of ${max_stop_attempts}"
        /etc/init.d/vmware stop
        echo -e "Now waiting 5 seconds"        
        sleep 5s
        let stop_attempts++
        vmware_pid_count=$(ps ax | grep -i vmware | grep -v 'grep' | awk 'BEGIN {FS=" "} {print $1" "$5}' | grep -i 'vmware' | awk 'BEGIN {FS=" "} {print $1}' | tr "\n" " " | wc -w)
      done
      if [[ ${vmware_pid_count} -ne 0 ]]; then
        echo -e ""
        echo -e "We have tried being nice. Now lets go berserk."
        max_kill_attempts=5
        kill_attempts=0
        while [[ ${vmware_pid_count} -ne 0 && ${kill_attempts} -le ${max_kill_attempts} ]]; do 
          echo -e "Attempt ${kill_attempts} of ${max_kill_attempts}."
          kill -s KILL ${vmware_pids}
          echo -e "Now waiting 5 seconds"
          sleep 5s
          vmware_pid_count=$(ps ax | grep -i vmware | grep -v 'grep' | awk 'BEGIN {FS=" "} {print $1" "$5}' | grep -i 'vmware' | awk 'BEGIN {FS=" "} {print $1}' | tr "\n" " " | wc -w)
          let kill_attempts++
        done        
        echo -e ""
        if [[ ${vmware_pid_count} -gt 1 ]]; then
          echo -e "Well, there are active VMware PIDs. But force-proceed is activated, so lets try to proceed anyway..."
        else
          echo -e "There are no more VMware processes running. Proceeding..."
        fi
      fi    
    fi
  else
    echo -e "There are no VMware processes running. Proceeding..."
  fi 
}

```But another more important issue, which is what I am really focusing on, is that every time a patch is needed, we can't be sure if the end-user is running:
a) An unpatched set or kernel modules sources (and their versions).
b) A patched set of kernel modules sources (and their version)
b1) If so, what was patched (version and/or files) and which patch was used.
c) A set of kernel module sources with mixed versions.
 
So diff-based patches are always much more likely to fail, even when they are correct, consistently. The alternatives would be:

a) To not use diff-based patches and, instead, search replace sources lines using some tool like sed. But it would be very hard to sort of predict what was written in the any possible patch applied by the end-user (also, he might have manually edited the sources); 

b) Or, what I consider to be more doable: 
- Always create diff patches based in fresh / unpatched kernel modules sources from VMWare (done).
- The script would always download the correct VMWare bundle (version, architecture) and extract the kernel modules sources from the binary bundle files (done).
- Always backup previous sources and write the new (unpatched) ones. 
- Only then, apply the patch.

I'm working on a generic patcher that takes any patch file as a first argument and performs these steps.

Also, I'd like to keep working vmware-player deb packages in my PPA and try to get them in repos, but I'm not sure licensing issues would allow me to. That would be much easier. I'll check vmware licensing and probably email them as soon as I have the time to do it.

BTW: The attached patch works for 4.0.2 unmodified kernel modules sources on kernel 3.2.x (It's different from the patch I posted previously). 

Regards,
Effenberg

---

### Post by mjbright on 2012-03-08
Thanks a lot effenberg0x0.

I had to make minor modifs to your script (uncomment the real patching, and change the test on the "100" return code of the dry patching) and then I had vmware player working.

This was on Precise Pangolin (Ubuntu 12.04) Beta 1, with Ubuntu's 3.2.0-18-generic kernel ... just fyi for anyone else blocked on this.

Thanks again !!  :D:D

---

