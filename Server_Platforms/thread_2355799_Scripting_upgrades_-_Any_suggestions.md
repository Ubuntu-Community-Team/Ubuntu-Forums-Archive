---
title: "Scripting upgrades - Any suggestions?"
date: 2017-03-16
forum: Server Platforms
---

### Post by LHammonds on 2017-03-16
With Ubuntu Server 16.04 LTS, it no longer ships with "aptitude" so I am going to update my scripts to work with what does ship with the OS.  And yes, I know you can install aptitude but I want to work with what it comes with if possible.

The apt command says not to use it in a scripted fashion because of the CLI interface (guess it is geared for human eyes). I get no such warning when using apt-get and it 3 main functions I use in just apt are "update" "upgrade" and "autoremove" which are all available in apt-get.

I do realize auto-upgrading things like PHP can cause application breakage and such but I do have multiple ways to restore files and entire servers or simply reverting packages to prior version numbers.

I've been careful to only handle kernel updates and purging by hand since the disasters in Ubuntu 10.04 but have not seen any issues that might prevent the server from booting since 12.04.

Does anyone see any issues running these commands on production systems in an automated way?

```
apt-get update
apt-get --assume-yes upgrade>> some-log-file 2>&1
apt-get --assume-yes autoremove >> some-log-file 2>&1
apt-get autoclean >> some-log-file 2>&1
apt-get clean >> some-log-file 2>&1
```

Although not necessary for this post, I have included the script below that makes use of the commands above (which was original configured with aptitude using only safe security updates). It can be run from the command line or via root's crontab.

```

#!/bin/bash
#############################################
## Name          : apt-upgrade.sh
## Version       : 1.3
## Date          : 2017-03-16
## Author        : LHammonds
## Purpose       : Keep system updated (rather than use unattended-upgrades)
## Compatibility : Verified on Ubuntu Server 16.04 LTS
## Requirements  : Sendemail, run as root
## Run Frequency : Recommend once per day.
## Parameters    : None
## Exit Codes    :
##    0 = Success
##    1 = ERROR: Lock file detected.
##    2 = ERROR: Not run as root user.
##    4 = ERROR: APT update Error.
##    8 = ERROR: APT upgrade Error.
##   16 = ERROR: APT autoremove Error.
##   32 = ERROR: APT autoclean Error.
##   64 = ERROR: APT clean Error.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-06-01 LTH Created script.
## 2013-01-08 LTH Allow visible status output if run manually.
## 2013-03-11 LTH Added company prefix to log files.
## 2017-03-16 LTH Made compatible with 16.04 LTS
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

## Define local variables.
LogFile="${LogDir}/${Company}-apt-upgrade.log"
LockFile="${TempDir}/${Company}-apt-upgrade.lock"
ErrorFlag=0
ErrorMsg=""
ReturnCode=0
AptCmd="$(which apt)"
AptGetCmd="$(which apt-get)"

#######################################
##            FUNCTIONS              ##
#######################################
function f_cleanup()
{
  if [ -f ${LockFile} ]; then
    ## Remove lock file so subsequent jobs can run.
    rm ${LockFile} 1>/dev/null 2>&1
  fi
  ## Temporarily pause script in case user is watching output.
  sleep 2
  if [ ${ErrorFlag} -gt 0 ]; then
    ## Display error message to user in case being run manually.
    echo "`date +%Y-%m-%d_%H:%M:%S` --- ERROR: ${ErrorMsg}" | tee -a ${LogFile}
    ## Email error notice.
    f_sendmail "ERROR ${ErrorFlag}: Script aborted" "${ErrorMsg}"
  fi
  exit ${ErrorFlag}
}

#######################################
##           MAIN PROGRAM            ##
#######################################
clear
if [ -f ${LockFile} ]; then
  # Lock file detected.  Abort script.
  echo "** Script aborted **"
  echo "This script tried to run but detected the lock file: ${LockFile}"
  echo "Please check to make sure the file does not remain when check space is not actually running."
  ErrorMsg="This script tried to run but detected the lock file: ${LockFile}\n\nPlease check to make sure the file does not remain when check space is not actually running.\n\nIf you find that the script is not running/hung, you can remove it by typing 'rm ${LockFile}'"
  ErrorFlag=1
  f_cleanup
else
  echo "`date +%Y-%m-%d_%H:%M:%S` ${ScriptName}" > ${LockFile}
fi
## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "ERROR: Root user required to run this script.\n"
  ErrorMsg="Root user required to run this script."
  ErrorFlag=2
  f_cleanup
fi
echo "`date +%Y-%m-%d_%H:%M:%S` - Begin script." | tee -a ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Update" | tee -a ${LogFile}
${AptGetCmd} update > /dev/null 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Update return code of ${ReturnCode}"
  ErrorFlag=4
  f_cleanup
fi
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Upgrade" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} --assume-yes upgrade >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Upgrade return code of ${ReturnCode}"
  ErrorFlag=8
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-Get Autoremove" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} --assume-yes autoremove >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Autoremove return code of ${ReturnCode}"
  ErrorFlag=16
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-get Autoclean" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} autoclean >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Autoclean return code of ${ReturnCode}"
  ErrorFlag=32
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` --- Apt-get Clean" | tee -a ${LogFile}
echo "--------------------------------------------------" >> ${LogFile}
${AptGetCmd} clean >> ${LogFile} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorMsg="Apt-Get Clean return code of ${ReturnCode}"
  ErrorFlag=64
  f_cleanup
fi
echo "--------------------------------------------------" >> ${LogFile}
echo "`date +%Y-%m-%d_%H:%M:%S` - End script." | tee -a ${LogFile}

## Perform cleanup routine.
f_cleanup

```

---

### Post by TheFu on 2017-03-20
Have you considered using a devops tool, so you can leverage all the solutions pre-built and shared on github for each sub-system?

Of course, there are downsides to all those tools and some of them cause more issues than they solve. ;)  Spent a few hrs today fighting through an ansible 1.9-->2.1 upgrade that broke many of my roles and playbooks.  Sometimes we gotta wonder why they change stupid things (sudo/become ???).  Seems just to make things break.

As for the scripting - fully specify all paths to all programs (date/tee/rm/ etc). echo supports multi-line.
Might want to capture some signals to cntl-c gets caught and stuff gets cleaned up correctly.  There's a "Belts and Suspenders for Bash" presentation with lots more ideas. I've seen the presentation a few times, but can't find it online. Sorry.

---

### Post by ian-weisser on 2017-03-21
Why run autoclean, then clean?

---

### Post by Habitual on 2017-03-21
I've been known to run
```
apt-get autoremove -y && apt-get update && apt-get dist-upgrade -y
``` on occasion.

---

### Post by TheFu on 2017-03-21
ooops. Saw the wrong things. My eyes tricked me. ;)

---

### Post by LHammonds on 2017-04-10
> **TheFu said:**
> Have you considered using a devops tool?No.

> **TheFu said:**
> As for the scripting - fully specify all paths to all programs (date/tee/rm/ etc).As I understand it, that is primarily a security recommendation to prevent modification to the path for the purpose of calling malicious programs.  Would it be better to just set a PATH variable at the beginning to avoid the problem of executables being moved/upgraded to different locations or ability for the script to run as is on different systems?

> **TheFu said:**
> Might want to capture some signals to cntl-c gets caught and stuff gets  cleaned up correctly.Even though the script can be run via command-line directly, its primary use will be via crontab.  It would be good to include interrupt code so I'll look into that.

> **ian-weisser said:**
> Why run autoclean, then clean?The way I understand it is this:  Autoclean clears out packages in the cache that cannot be downloaded anymore.  Clean removes all packages in your cache.  It might be pointless to run autoclean but I do it cause its there and I like double-coverage. ;-)

LHammonds

---

### Post by SeijiSensei on 2017-04-10
The usual reason for using full paths in crontabs is that cron runs in a stripped-down environment.  As you say, you can define a PATH at the top of the file to resolve this problem.  Or just use /usr/bin/apt.

---

### Post by LHammonds on 2017-04-11
> **SeijiSensei said:**
> The usual reason for using full paths in crontabs is that cron runs in a stripped-down environment.  As you say, you can define a PATH at the top of the file to resolve this problem.  Or just use /usr/bin/apt.
What I currently do is add the path to the crontab.

Example:
```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-20 - LTH - Created schedule
########################################
 
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
 
# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Daily software upgrade check
#
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1

```

The main thing I'm trying to find out is if anyone else automates their patches like this or if there is something wrong with doing these in a scripted fashion:

```

apt-get update
apt-get --assume-yes upgrade>> some-log-file 2>&1
apt-get --assume-yes autoremove >> some-log-file 2>&1
apt-get autoclean >> some-log-file 2>&1
apt-get clean >> some-log-file 2>&1

```

The next item on my checklist to tackle after this will be the business of not needing to reboot after patching.  I have read articles in the past about how to update the kernel without rebooting but have not had time to dedicate working on that solution.

I didn't care to automate reboots after patches due to various kernel and grub issues with my initial experiences with Ubuntu 10.04.  But since 12.04 and on, I have not had the show-stoppers like the ones I experiences back in the 10.04 days.  Didn't want to come in to work to find that every Linux server that rebooted failed to start up and have to troubleshoot all of them at once.  ;-)   That is still a risk but not nearly as much of a promise as it used to be.

LHammonds

---

