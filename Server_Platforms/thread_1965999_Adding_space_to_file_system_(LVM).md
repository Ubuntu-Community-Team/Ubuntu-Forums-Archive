---
title: "Adding space to file system (LVM)"
date: 2012-04-26
forum: Server Platforms
---

### Post by LHammonds on 2012-04-26
I have my servers (10.04 LTS, 64bit) setup using LVM where there is extra unused room in the logical volumes ([example]("http://i228.photobucket.com/albums/ee11/Conan_Lon/Linux/LinuxHDPartitionDesign-343.png")).

I was wanting to be able to run a script every hour looking for used space to cross a pre-defined threshold and then automatically increase space in the file system and email the admin.  This would allow us some time to order and install new drives before they are needed.

All the LVM commands allow for increases such as +1G and this would be perfect for a script to simply run something like **resize2fs /dev/LVG/opt +1G**

However, resize2fs is expecting an exact total size and trying to use a plus sign is ignored and thinks you are wanting to resize to a 1 GB file system...which it will obviously fail if there is more than 1GB of data already on the system.

Is there any way to "grow" the file system using a relative number or must I calculate the exact size it is now, add the amount to increase by and then use the combined number to pass it onto resize2fs?

Thanks,
LHammonds

---

### Post by LHammonds on 2012-04-28
Does anyone utilize an automated method to increase space?

---

### Post by darkod on 2012-04-28
I don't have much knowledge about scripting but if I understand LVM correctly, you are looking at two steps.

Growing the Logical Volume, and only then growing the filesystem.

For growing the LV you will need to specify how much you want it to grow, but for growing the filesystem if you want to take all of the LV, which you do, you can use only:
resize2fs /dev/VG/LV

That will take the whole LV.

---

### Post by LHammonds on 2012-04-30
> **darkod said:**
> if you want to take all of the LV, which you do, you can use only:
resize2fs /dev/VG/LV

That will take the whole LV.
No, I do not want to expand the file system to the entire amount of free space in the LV.  Yes, that command (without specifying size) will expand the FS to consume all available space in the LV but I would prefer being able to increment by a certain amount or a percentage.

The reason why is that I want the option to reduce the amount of free space in one volume to give it to another...without any impact on the FS contained in the volume being shrunk (e.g. I do not want to take it offline to shrink an FS).

I am looking to have all unused space split evenly among the volumes I expect will grow.  However, we all know that file systems do not grow that the same pace...which is why I want some buffer room in each volume.

Incremental increases in FS usage will allow me time to purchase more drives if necessary or deallocate free space from another volume that is not growing as fast and give it to the volume that is.

The main point to all of this is that I do not want an FS to expand to the entire amount of space available.  I don't want to be put into a position where I might need to shrink an FS that holds data.  Even though it can be done, I just do not like doing that if it can be avoided.

If I cannot increase space incrementally using resize2fs, I guess I will have to manage the volumes in such a way that they are set to the next incremental size and then keep manipulating the LV to give it more incremental space anytime the FS auto-grows to fill it up.  That would mean all the free space is contained at the LG level.

----------------------------

Since the resize2fs program only accepts an exact total size (or will use the entire LV space if no size is specified), I will attempt to make a script that will look at the current FS size, current LV size and then calculate the exact size of what I want to be incremented by...which can then be fed to the resize2fs program.  (although I hate scripting a solution if there is a more simple approach)

Pseudo-code for the size checking program that would run every hour:
```

fs-name = get parameter 1   (e.g. /dev/LVG/opt)
fs-available-threshold = get parameter 2  (e.g. 2G)
fs-increase-by = get parameter 3  (e.g. 1G)
current-fs-available = get fs available space

if current-fs-available < fs-available-threshold then
  call auto-increment-script, give fs-name and fs-increase-by
  if auto-increment-script successful then
    send email notification to admins
  else
    send email warning to admins
  end if
end if

```Pseudo-code for my auto-increment script idea:
```

fs-name = get parameter 1  (e.g. /dev/LVG/opt)
increment-by = get parameter 2   (e.g. 1G)
current-fs-size = get total size of fs-name   (e.g. 4G)
current-lv-size = get total size of logical volume  (e.g. 10G)

if (current-lv-size - current-fs-size) > increment-by then
  resize fs (current-fs-size + increment-by)
  if return-code is good then
    exit with good code
  else
    exit with failure return-code
  end if
else
  exit with warning
end if

```------------------------

Currently trying to figure out how to translate the pseudo-code into bash script code...

(I just cannot believe I am the only one to want a system that grows like this over time)

---

### Post by darkod on 2012-04-30
I either don't understand how it works, because I don't see a point in what you are asking.

You split the available space in the VG to different LVs. But once a space is inside a LV you can't share FS space between different LVs.

For example, your VG has 100GB. Right now you have three LVs of 10GB each.

You don't want to allocate the remaining 70GB of the VG to only one LV, instead you want the LVs to grow sort of dynamically depending on need. I understand that.

But once a LV has its size, whether after shrink or grow, you don't save anything by not using whole of the LV with a FS.

The FS is not a physical space. Your PV, VG and LVs are the physical space.

How do you plan to expand "same FS" over multiple LVs? Something like that doesn't exist.

---

### Post by LHammonds on 2012-04-30
> **darkod said:**
> 
You split the available space in the VG to different LVs. But once a space is inside a LV you can't share FS space between different LVs.

That is not what I am talking about.  I am just talking about being able to adjust the lines to each LV / FS...kinda like being able to move a slider to adjust how much space each volume can have.

Initially, all available physical space is added to the VG.  I then slice up all the space in the VG to the various LV based on what I "think" will be needed.  I then allocate the FS to just a certain amount of the LV (not 100%) so I can increase any FS that needs more room.  This is the automated part I want.

However, if one of the FS is growing much faster than the others, I can reduce the size of the other LVs to free up space in the VG to be re-allocated to the LV that is growing...thus giving me more time before needing to acquire physical space (hard drives)

If I use all of the VG space for my LVs and each FS in the LV consumes 100% of the LV, I cannot reduce an LV without first reducing the FS...and to my understanding, you cannot reduce an FS while the system is online.

The whole purpose my design is to make the system dynamic and online without any downtime.  That requires the FS to only grow...never shrink.

> **darkod said:**
> 
But once a LV has its size, whether after shrink or grow, you don't save anything by not using whole of the LV with a FS.

Again, FS grow = online or offline, FS shrink = offline only.

Sorry about not being very clear about this.  I'm not good describing systems / processes that I am not 100% familiar with (I am a Linux newbie)

LHammonds

---

### Post by darkod on 2012-04-30
Look, I'm rather new with LVM myself, and I might be wrong. But, no offense, I think you have misunderstood how it works.

Your control ends with the LV size. How much percent of it is the FS makes no difference what so ever.

By configuring the FS to be X% of your LV, you are not gaining anything at all, just losing the (100-X)% of your LV. You can never use more than 100% of the LV for the FS. So, play with the LVs, forget about the FS size. It needs to be 100% of the LV always.

Make this test in virtual box:
You have a VG with 100GB. And two LVs of 30GB each.
Can you make the FS of LV1 to be 40GB without growing LV1 to 40GB first? No.

Lets say you make LV1 70GB with FS of 50GB. That's what you are talking about, right?
Make LV2 30GB with the FS 30GB too.
Now, you have 20GB on LV1 not belonging to the FS. Can you assign 10GB of them to LV2 and grow its FS to 40GB? No. Because LV2 is only 30GB and you can't have a FS of higher size.

Your limit will always be the LV size. And once space is allocated to a LV, it stays assigned to it regardless whether you create FS on it, and how big it is.

PS. Just to be more precise. The only situation where the FS size plays a role is before shrinking a LV. You have to shrink the FS first to make sure you lose no data when you shrink the LV later.
But you can not use the space left outside the FS but inside one LV, for another LV. You have to srink one LV, grow another LV, and then grow its FS. Again, the LV size is what you play with.

---

### Post by LHammonds on 2012-04-30
> **darkod said:**
> 
You have a VG with 100GB. And two LVs of 30GB each.
Can you make the FS of LV1 to be 40GB without growing LV1 to 40GB first? No.

Lets say you make LV1 70GB with FS of 50GB. That's what you are talking about, right?
Make LV2 30GB with the FS 30GB too.
Now, you have 20GB on LV1 not belonging to the FS. Can you assign 10GB of them to LV2 and grow its FS to 40GB? No. Because LV2 is only 30GB and you can't have a FS of higher size.

I think this is the point where we disconnect.

If I have 20 GB unused in LV1 and need to reassign 10 GB to LV2 which is currently maxed out, I need to reduce LV1 by 10 GB which then gives the VG 10 extra GB.  At this point, LV1 is now 60 GB, LV1 FS is 50 GB so there is still 10 GB left to grow that particular FS.  Now I would extend LV2 an additional 10 GB so that LV2 is now 40 GB and the LV2 FS is 30 GB.  I can then extend the LV2 FS by 1 GB, 2 GB or all the way up to the 10 GB that LV2 now has to play with.

The commands I would use to do this are:

lvreduce (take 10 GB away from LV1)
lvextend (give 10 GB to LV2)
resize2fs (give up to 10 GB to LV2 FS)

Anytime manipulation of the logical volumes are needed, it will be done manually.  However, a script can safely and automatically increase the FS into unused areas of the logical volume while the system is online and active...which gives the administrator some leeway for growth and time to make LV changes like the above example or add additional drives to increase storage for the entire volume group.

LHammonds

---

### Post by darkod on 2012-04-30
It makes sense, of course. Although my way of thinking is since I have to reduce the LV anyway so that another LV can expand, I would run the FS reduce at the same time.

So, I can have the FS of all LVs maxed out at 100% all the time. At the moment I need to intervene, I can do:
resize2fs (shrink FS)
lvreduce
lvextend
resize2fs (grow FS of the other LV)

---

### Post by LHammonds on 2012-05-01
> **darkod said:**
> 
So, I can have the FS of all LVs maxed out at 100% all the time. At the moment I need to intervene, I can do:
resize2fs (shrink FS)
This is definitely NOT what I want to do.  I run many production servers  and I cannot afford to make such mistakes that would require downtime  (shrinking an FS).

So, I am back to making the scripts I  mentioned in an earlier post unless somebody knows of an easier way to  increment the space allocated to an FS.

Thanks for the conversation and getting me to better explain what I am attempting to do!
LHammonds

---

### Post by LHammonds on 2012-05-01
I have finished the storage check script and ended up using a single script instead of two.

The bulk of the script is error checking and avoiding problems...although I am sure it will not catch 100% of all potential problems but it "should" be sufficient.

I will share the code here but **BE WARNED**, this script will resize your File System under certain circumstances.  Even though it should be safe, you need to make sure you designed your LVM for such a script and you have the correct references for any potential file systems as noted near line 152 that is commented "***Check validity of File System names***."  I chose to use the LV names to keep it short but you can set it to whatever you like.  I did it this way to avoid operator typos that run it manually or set it up wrong in the crontab.  All the important stuff is pre-defined inside the script.

Here is how my system is designed:

**Volume Group** = LVG (Size=342 GB, 0 free)

**Logical Volumes** in LVG:
root (Size=8GB)
opt (Size=75GB)
bak (Size=125GB)
temp (Size=125GB)

**File Systems**:
/dev/mapper/LVG-root (Size=8GB), Mounted on /
/dev/mapper/LVG-opt (Size=50GB), Mounted on /opt
/dev/mapper/LVG-bak (Size=100GB), Mounted on /var/backup
/dev/mapper/LVG-temp (Size=100GB), Mounted on /var/temp

Here is a sample crontab file for checking 3 file systems that I expect will grow over time.  Note that I am not including the root partition since I do not expect it to be growing over time...however, I do have Nagios monitoring it so I will get notified but by a different method.  This process is meant to check AND grow the FS as needed.  When they get within 5 GB of being full, it will try to increment the file system by 1 GB. Click on this link to read about [my thoughts on how to maintain a crontab schedule]("http://ubuntuforums.org/showpost.php?p=11894495&postcount=7").

```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-01 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow command

#
# Get date/time from network time server every hour
#
0 * * * * /etc/network/if-up.d/ntpdate
#
# Daily check for available space on /opt
#
0 1 * * * /var/scripts/prod/check-storage.sh opt 5 1 > /dev/null 2>&1
#
# Daily check for available space on /var/backup
#
0 2 * * * /var/scripts/prod/check-storage.sh bak 5 1 > /dev/null 2>&1
#
# Daily check for available space on /var/temp
#
0 3 * * * /var/scripts/prod/check-storage.sh temp 5 1 > /dev/null 2>&1

```Here is the script.  Notice that the resize2fs command is currently commented out on line 64.  That means this script will operate in a mode that will not affect the system as it is now.  You uncomment the command by removing the pound characters from the beginning to make it actually perform a resize.   Feel free to try it out on the commandline by issuing various threshold values which are below the current available space and above to see how it works without fear of it doing anything to your system.

/var/scripts/prod/check-storage.sh
```

#!/bin/bash
#############################################
## Name          : check-storage.sh
## Version       : 1.2
## Date          : 2012-05-01
## Author        : LHammonds
## Purpose       : Check available space for a file system and expand if necessary.
## Compatibility : Verified on Ubuntu Server 10.04.4 LTS
## Requirements  : None
## Run Frequency : Recommend once per day for each FS to monitor.
## Parameters    :
##    1 = (Required) File System name (e.g. opt)
##    2 = (Required) File System Threshold (e.g. 2G)
##    3 = (Required) Amount to increase File System (e.g. 1G)
## Exit Codes    :
##    0 = Success (either nothing was done or FS expanded without error)
##    1 = ERROR: Missing or incorrect parameter(s)
##    2 = ERROR: Invalid parameter value(s)
##    4 = ERROR: Lock file detected
##    8 = ERROR: Resize2fs error
##   16 = SEVERE: No room to expand
##   32 = ERROR: Script not run by root user
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-05-01 LTH Created script.
## 2012-05-02 LTH Improved log messages.
## 2012-05-02 LTH Improved email messages.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LOGFILE="${TEMPDIR}/check-storage.log"
LOCKFILE="${TEMPDIR}/check-storage.lock"
ErrorFlag=0
ReturnCode=0

#######################################
##            FUNCTIONS              ##
#######################################

function f_cleanup()
{
  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other check space jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  exit ${ErrorFlag}
}

function f_showhelp()
{
  echo -e "\nUsage : ${SCRIPTNAME} FileSystemName ThresholdSizeInGB AmountToIncreaseByInGB\n"
  echo -e "\nExample: ${SCRIPTNAME} opt 2 1\n"
}

function f_auto-increment()
{
  let RoomInLV=${LVSize}-${FSSize}
  if [[ ${RoomInLV} -gt ${FSIncreaseBy} ]]; then
    ## There is room in the LV to increase space to the FS.
    #resize2fs ${FSVol} ${NewFSSize}G
    ReturnCode=$?
    echo "`date +%Y-%m-%d_%H:%M:%S` --- resize2fs ${FSVol} ${NewFSSize}G, ReturnCode=${ReturnCode}" | tee -a ${LOGFILE}
    if [[ ${ReturnCode} -ne 0 ]]; then
      ## There was an error in resize2fs.
      return ${ReturnCode}
    fi
  else
    ## There is not enough room in the LV to increase space in the FS.
    return 50
  fi
  return 0
}

#######################################
##           MAIN PROGRAM            ##
#######################################

if [ -f ${LOCKFILE} ]; then
  # Lock file detected.  Abort script.
  echo "Check space script aborted"
  echo "This script tried to run but detected the lock file: ${LOCKFILE}"
  echo "Please check to make sure the file does not remain when check space is not actually running."
  f_sendmail "ERROR: check storage script aborted" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when check space is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LOCKFILE}'"
  ErrorFlag=4
  f_cleanup
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo "ERROR: Root user required to run this script."
  echo ""
  ErrorFlag=32
  f_cleanup
fi

## Check existance of required command-line parameters.
case "$1" in
  "")
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  --help|-h|-?)
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  *)
    FSName=$1
    ;;
esac
case "$2" in
  "")
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  --help|-h|-?)
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  *)
    FSThreshold=$2
    ;;
esac
case "$3" in
  "")
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  --help|-h|-?)
    f_showhelp
    ErrorFlag=1
    f_cleanup
    ;;
  *)
    FSIncreaseBy=$3
    ;;
esac

## Check validity of File System name.
case "${FSName}" in
  "opt")
    FSVol="/dev/LVG/opt"
    FSMap="/dev/mapper/LVG-opt"
    ;;
  "bak")
    FSVol="/dev/LVG/bak"
    FSMap="/dev/mapper/LVG-bak"
    ;;
  "temp")
    FSVol="/dev/LVG/temp"
    FSMap="/dev/mapper/LVG-temp"
    ;;
  *)
    echo "ERROR: ${FSName} does not match a known file system defined in this script."
    f_showhelp
    ErrorFlag=2
    f_cleanup
    ;;
esac

## Check validity of threshold value.
test ${FSThreshold} -eq 0 1>/dev/null 2>&1
if [[ $? -eq 2 ]]; then
  ## Threshold parameter is not an integer.
  echo "ERROR: ${FSThreshold} is not an integer."
  f_showhelp
  ErrorFlag=2
  f_cleanup
fi

## Check validity of increment value.
test ${FSIncreaseBy} -eq 0 1>/dev/null 2>&1
if [[ $? -eq 2 ]]; then
  ## FSIncreaseBy parameter is not an integer.
  echo "ERROR: ${FSIncreaseBy} is not an integer."
  f_showhelp
  ErrorFlag=2
  f_cleanup
fi

## Get available space for the file system.
FSAvailable="`df --block-size=g ${FSMap} | awk '{ print $4 }' | tail -n 1 | sed 's/G//'`"

## Get the current size of the File System.
FSSize="`df --block-size=g ${FSMap} | awk '{ print $2 }' | tail -n 1 | sed 's/G//'`"

## Get the current size of the Logical Volume for the File System
LVSize="`lvs --noheadings --nosuffix --units=g ${FSMap} | awk '{ print $4}' | sed 's/[.].*//'`"

## Calculate the new size of the FS in case we need it.
let NewFSSize=${FSSize}+${FSIncreaseBy}

if [[ ${FSAvailable} -lt ${FSThreshold} ]]; then
  echo "`date +%Y-%m-%d_%H:%M:%S` - Starting expansion of ${FSVol}" | tee -a ${LOGFILE}
  echo "`date +%Y-%m-%d_%H:%M:%S` --- LVSize=${LVSize}GB, FSSize=${FSSize}GB, FSAvail=${FSAvailable}GB, FSThreshold=${FSThreshold}GB, FSIncreaseBy=${FSIncreaseBy}GB" | tee -a ${LOGFILE}
  ## Run the auto-expansion function.
  f_auto-increment
  ReturnCode=$?
  case ${ReturnCode} in
  0)
    f_sendmail "NOTICE: File System Expanded" "${FSVol} was expanded because it was nearing max capacity.  Please review disk space usage and plan appropriately. LVSize=${LVSize}GB, FSSize=${FSSize}GB, FSAvailable=${FSAvailable}GB, FSThreshold=${FSThreshold}GB, FSIncreaseBy=${FSIncreaseBy}GB"
    ;;
  50)
    echo "`date +%Y-%m-%d_%H:%M:%S` - SEVERE: No room to expand ${FSVol}" | tee -a ${LOGFILE}
    ErrorFlag=16
    f_sendmail "SEVERE: No room to expand ${FSVol}" "There is not enough room in the Logical Volume to expand the ${FSVol} File System.  Immediate action is required.  Make sure there is free space in the Volume Group 'LVG' and then expand the Logical Volume...then expand the File System.\n\nLVSize=${LVSize}GB, FSSize=${FSSize}GB, FSAvailable=${FSAvailable}GB, FSThreshold=${FSThreshold}GB, FSIncreaseBy=${FSIncreaseBy}GB.\n\nType 'vgs' to see if there is any free space in the Volume Group which can be given to the Logical Volume.\n\nType 'lvs' to see the current sizes of the LVs.\n\nType 'lvdisplay' to see a list of Logical Volumes so you can get the LV Name which is used in the lvextend and resize2fs commands.\n\nType 'lvextend -L+1G /dev/LVG/opt' if you want to extend the opt Logical Volume by 1 gigabyte (assuming there is 1GB available in the Volume Group).\n\nType 'df --block-size=g' to see a list of file systems and their associated size and available space.\n\nType 'resize2fs /dev/LVG/opt ${NewFSSize}G' to set the size of opt to ${NewFSSize} gigabytes. Make sure you set the size to the desired end-result which should be LARGER than the current FS size so you do not lose data."
    ;;
  *)
    echo "`date +%Y-%m-%d_%H:%M:%S` - ERROR: Expansion failure for ${FSVol}" | tee -a ${LOGFILE}
    ErrorFlag=8
    f_sendmail "ERROR: File System Expansion Failed" "${FSVol} Expansion failed with return code of ${ReturnCode}.  LVSize=${LVSize}GB, FSSize=${FSSize}GB, FSAvailable=${FSAvailable}GB, FSThreshold=${FSThreshold}GB, FSIncreaseBy=${FSIncreaseBy}GB"
    ;;
  esac
  echo "`date +%Y-%m-%d_%H:%M:%S` - Finished expansion of ${FSVol}" | tee -a ${LOGFILE}
else
  echo "`date +%Y-%m-%d_%H:%M:%S` - ${FSVol} ${FSAvailable}G>${FSThreshold}G No action required." | tee -a ${LOGFILE}
fi

## Perform cleanup routine.
f_cleanup

```Oh, one last thing...my code uses functions and variable I have pulled out into a common-use file which are specific to my environment (you need to change to suit your environment).  Here are the pertinent bits:

/var/scripts/common/standard.conf
```

## Global Variables ##
TEMPDIR="/var/temp"
MYDOMAIN="example.com"
ADMINEMAIL="admin@${MYDOMAIN}"
REPORTEMAIL="lhammonds@${MYDOMAIN}"
HOSTNAME=$(hostname -s)
SCRIPTNAME=$0
MAILFILE="${TEMPDIR}/mailfile.$$"

## Global Functions ##

function f_sendmail()
{
  ## Purpose: Send email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  echo "From: ${ADMINEMAIL}" > ${MAILFILE}
  echo "To: ${REPORTEMAIL}" >> ${MAILFILE}
  echo "Subject: ${1}" >> ${MAILFILE}
  echo "" >> ${MAILFILE}
  echo -e ${2} >> ${MAILFILE}
  echo "" >> ${MAILFILE}
  echo -e "\n\nServer: ${HOSTNAME}\nProgram: ${SCRIPTNAME}\nLog: ${LOGFILE}" >> ${MAILFILE}
  sendmail -t < ${MAILFILE}
  rm ${MAILFILE}
}

```Here is the typical output when it does not have to increase the FS:

/var/temp/check-storage.log
```

2012-05-01_01:00:00 - /dev/LVG/opt 44G>2G No action required.
2012-05-01_02:00:00 - /dev/LVG/bak 91G>2G No action required.
2012-05-01_03:00:00 - /dev/LVG/temp 93G>2G No action required.
2012-05-02_01:00:00 - /dev/LVG/opt 44G>2G No action required.
2012-05-02_02:00:00 - /dev/LVG/bak 91G>2G No action required.
2012-05-02_03:00:00 - /dev/LVG/temp 93G>2G No action required.
2012-05-03_01:00:00 - /dev/LVG/opt 44G>2G No action required.
2012-05-03_02:00:00 - /dev/LVG/bak 91G>2G No action required.
2012-05-03_03:00:00 - /dev/LVG/temp 93G>2G No action required.

```Here is a sample of what the log will look like when it perform increases...notice how I had to increase the threshold in order for it to fire off the increase (but it still just issued a single gigabyte increase):

/var/temp/check-storage.log
```

2012-05-02_01:00:00 - Starting expansion of /dev/LVG/opt
2012-05-02_01:00:00 --- LVSize=75GB, FSSize=50GB, FSAvail=44GB, FSThreshold=50GB, IncreaseBy=1GB
2012-05-02_01:00:00 --- resize2fs /dev/LVG/opt 51, ReturnCode=0
2012-05-02_01:00:00 - Finished expansion of /dev/LVG/opt
2012-05-02_02:00:00 - Starting expansion of /dev/LVG/bak
2012-05-02_02:00:00 --- LVSize=125GB, FSSize=99GB, FSAvail=91GB, FSThreshold=100GB, IncreaseBy=1GB
2012-05-02_02:00:00 --- resize2fs /dev/LVG/bak 100, ReturnCode=0
2012-05-02_02:00:00 - Finished expansion of /dev/LVG/bak
2012-05-02_03:00:00 - Starting expansion of /dev/LVG/temp
2012-05-02_03:00:00 --- LVSize=125GB, FSSize=99GB, FSAvail=93GB, FSThreshold=100GB, IncreaseBy=1GB
2012-05-02_03:00:00 --- resize2fs /dev/LVG/temp 100, ReturnCode=0
2012-05-02_03:00:00 - Finished expansion of /dev/LVG/temp
```**EDIT #1:** The log file output is not all that great in 1.0.  I spruced it up with more info in version 1.1.  Have fun!

**EDIT #2:** Updated to version 1.2, improved email notifications and other minor changes.

Here is a sample email for the situation where there is not enough room available in the LV to extend the FS:
```

From: admin@example.com
To: dirkdiggler@example.com
Sent: Wednesday, May 2, 2012 2:47:17 PM
Subject: SEVERE: No room to expand /dev/LVG/opt

There is not enough room in the Logical Volume to expand the /dev/LVG/opt File System. Immediate action is required. Make sure there is free space in the Volume Group 'LVG' and then expand the Logical Volume...then expand the File System.

LVSize=75GB, FSSize=50GB, FSAvailable=44GB, FSThreshold=55GB, FSIncreaseBy=55GB.

Type 'vgs' to see if there is any free space in the Volume Group which can be given to the Logical Volume.

Type 'lvs' to see the current sizes of the LVs.

Type 'lvdisplay' to see a list of Logical Volumes so you can get the LV Name which is used in the lvextend and resize2fs commands.

Type 'lvextend -L+1G /dev/LVG/opt' if you want to extend the opt Logical Volume by 1 gigabyte (assuming there is 1GB available in the Volume Group).

Type 'df --block-size=g' to see a list of file systems and their associated size and available space.

Type 'resize2fs /dev/LVG/opt 105G' to set the size of opt to 105 gigabytes. Make sure you set the size to the desired end-result which should be LARGER than the current FS size so you do not lose data.

Server: mail
Program: ./check-storage.sh
Log: /var/temp/check-storage.log
```

---

