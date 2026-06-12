---
title: "Temporarily suspend CRON action"
date: 2012-08-14
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2012-08-14
Hi all

Have the following code as part of a CRONTAB,  /var/data/bin/zoneedit.sh checking if the external IP address has changed, and, if so, updating Zoneedit.

```
MAILTO=me@mysite.com
*/5 * * * * /var/data/bin/zoneedit.sh
```

This code runs as expected without error.

At midnight, there is a rsync call to a remote server which updates the main server. This operation may take up to 10 minutes.

During this time /var/data/bin/zoneedit.sh also runs but with a reported error, ```
ssmtp: Cannot open smtp.gmail.com:587
```and later runs again without error, even though Zoneedit does not need updating.

What I would like to do is suspend ```
*/5 * * * * /var/data/bin/zoneedit.sh
```from say 23.55 to 00.10, and thus eliminate the error.

Ideas, please?

---

### Post by squaregoldfish on 2012-08-14
What's stopping you from changing the crontab spec for zoneedit so it doesn't run during that period?

---

### Post by ChrisRChamberlain on 2012-08-14
squaregoldfish

Thanks for your reply

> What's stopping you from changing the crontab spec for zoneedit so it doesn't run during that period?

Would appreciate guidance on how to do that.



This code simulates the zoneedit.sh code

```
#!/bin/bash

ipfile='/var/data/bin/ipaddress'

[[ -f "$ipfile" ]] && ipold="$(< "$ipfile" )"
ipnew="$( wget -q -O - checkip.dyndns.org | sed -e 's/.*Current IP Address: //;s/<.*$//' )"

if [[ "$ipold" != "$ipnew" ]]; then
  echo "$ipnew" > "$ipfile"
  /usr/sbin/ssmtp me@mysite.com < /var/data/bin/ipaddress 
  wget -O - --http-user=me --http-passwd=password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mysite.com
fi
```'

Although there may be no change in the external IP address, the script runs within the ten minutes from midnight onwards as previously described.

What should happen is that having determined a 'no change' situation, the script should terminate but it does not.

Any other time of the day it works correctly - if rsync is running it does not. :(

---

### Post by rubylaser on 2012-08-14
You'll need to make two cron entries to accomplish this.  One to cover all of the time from 1:00 - 23:55
```
*/5 1-23 * * * /var/data/bin/zoneedit.sh
```
and a second one that covers from 0:10 - 0:55.
```
10,15,20,25,30,35,40,45,50,55 0 * * * /var/data/bin/zoneedit.sh
```
I think this should do it if I understand you correctly.

---

### Post by ChrisRChamberlain on 2012-08-14
rubylaser

Thank you for your reply.

Have implemented your suggestion, and will report back tomorrow when the CRONTAB has run.

---

### Post by ChrisRChamberlain on 2012-08-15
All ran as hoped for - thanks again to rubylaser for your code.

---

### Post by rubylaser on 2012-08-15
No problem, glad you got it working properly :)

---

### Post by LHammonds on 2012-08-16
I would actually modify the scripts.  If one script must not run when something else is running, you need to have that logic built into the script.

I usually create a scriptname.lock file when a script starts and deletes when finished.

Any script that needs to avoid another simply looks for the existence of that lock file.

This will allow those unfamiliar with the scripts to make schedule changes and they will not cause failures.  Same thing goes for that 10 min script that might start to take longer and longer over time or if it gets stuck.

LHammonds

---

### Post by rubylaser on 2012-08-16
> **LHammonds said:**
> I would actually modify the scripts.  If one script must not run when something else is running, you need to have that logic built into the script.

I usually create a scriptname.lock file when a script starts and deletes when finished.

Any script that needs to avoid another simply looks for the existence of that lock file.

This will allow those unfamiliar with the scripts to make schedule changes and they will not cause failures.  Same thing goes for that 10 min script that might start to take longer and longer over time or if it gets stuck.

LHammonds

+1 Very good point.  I was just addressing the original question rather than solving it properly.

---

### Post by ChrisRChamberlain on 2012-08-17
LHammonds

Many thanks for your input.

The script that 'errors' was posted earlier in this thread.

The rsync script is ```
@midnight rsync -e -ssh -varuzP me@remotesite.com:/home/me/Documents/localbackup/ "home/me/Documents/remotebackup" >> /var/data/rsynclog.log
```

So how would you create/modify suitable script, please?

---

### Post by LHammonds on 2012-08-17
I wouldn't call the rsync command directly from the cron schedule.

Create a script file and call the script from cron.

Here is an example of how I would create a script around the rsync command to make it more robust and to send email notifications upon errors as well as nice logging features.

This code is untested but should be pretty-close to a working state.

rsync-docs.sh
```

#!/bin/bash
#############################################
## Name          : rsync-docs.sh
## Version       : 1.0
## Date          : 2012-08-17
## Author        : ChrisRChamberlain
## Purpose       : Backup of me document folders
## Compatibility : Verified on to work on: Ubuntu Server 10.04 LTS - 12.04 LTS
##                 Should not run if /tmp/zoneedit.lock exists.
## Requirements  : rsync, sendemail
## Run Frequency : Once per day after hours or as needed (will not shutdown service)
## Exit Codes    : 
##    0    = success
##    1-35 = rsync error codes
##    98   = Program already running (lock file detected)
##    99   = Incompatible program running (lock file detected)
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-08-17 CRC Created script.
#############################################

LOGFILE="/var/data/rsync-docs.log"
LOCKFILE="/tmp/rsync-docs.lock"
ZONEEDITLOCKFILE="/tmp/zoneedit.lock"
SOURCE="me@remotesite.com:/home/me/Documents/localbackup/"
TARGET="home/me/Documents/remotebackup"
HOSTNAME="$(hostname -s)"
SCRIPTNAME="$0"
ADMINEMAIL="admin@mydomain.com"
REPORTEMAIL="ChrisRChamberlain@mydomain.com"
MAILSERVER="srv-mail"
ERRORFLAG=0

#######################################
##            FUNCTIONS              ##
#######################################
function f_cleanup()
{
  echo "`date +%Y-%m-%d_%H:%M:%S` - Rsync exit code: ${ERRORFLAG}" >> ${LOGFILE}

  if [ -f ${LOCKFILE} ];then
    ## Remove lock file so other backup jobs can run.
    rm ${LOCKFILE} 1>/dev/null 2>&1
  fi
  ## Email the result to the administrator.
  if [ ${ERRORFLAG} -eq 0 ]; then
    f_sendmail "Rsync-Docs Backup Success" "Rsync me docs completed with no errors."
  else
    f_sendmail "Rsync-Docs Backup ERROR" "Rsync me docs failed.  ERRORFLAG = ${ERRORFLAG}"
  fi
}

function f_sendmail()
{
  ## Purpose: Send administrative email message.
  ## Parameter #1 = Subject
  ## Parameter #2 = Body
  sendemail -f "${ADMINEMAIL}" -t "${REPORTEMAIL}" -u "${1}" -m "${2}\n\nServer: ${HOSTNAME}\nProgram: ${SCRIPTNAME}\nLog: ${LOGFILE}" -s ${MAILSERVER}:25 1>/dev/null 2>&1
}

#######################################
##           MAIN PROGRAM            ##
#######################################

## Binaries ##
RSYNC-EXE="$(which rsync)"

if [ -f ${ZONEEDITLOCKFILE} ]; then
  ## Incompatible program is currently running.  Abort script.
  ERRORFLAG=99
  echo "`date +%Y-%m-%d_%H:%M:%S` - Rsync avoiding run.  Exit code: ${ERRORFLAG}" >> ${LOGFILE}
  exit ${ERRORFLAG}
fi

if [ -f ${LOCKFILE} ]; then
  ## Program lock file detected from previous run.  Abort script.
  f_sendmail "Rsync me docs aborted - Lock File" "This script tried to run but detected the lock file: ${LOCKFILE}\n\nPlease check to make sure the file does not remain when this script is not actually running."
  ERRORFLAG=98
  echo "`date +%Y-%m-%d_%H:%M:%S` - Rsync avoiding run.  Exit code: ${ERRORFLAG}" >> ${LOGFILE}
  exit ${ERRORFLAG}
else
  ## Create the lock file to ensure only one script is running at a time.
  echo "`date +%Y-%m-%d_%H:%M:%S` ${SCRIPTNAME}" > ${LOCKFILE}
fi

echo "`date +%Y-%m-%d_%H:%M:%S` - Rsync me docs started." >> ${LOGFILE}

StartTime="$(date +%s)"

## Rsync me documents.
${RSYNC-EXE} -e -ssh -varuzP ${SOURCE} ${TARGET} > ${LOGFILE}
RETURNVALUE=$?
if [ ${RETURNVALUE} -ne 0 ]; then
  ## rsync command failed.  Send warning email.
  f_sendmail "Rsync me docs Failure" "rsync failed with return value of ${RETURNVALUE}"
  ERRORFLAG=${RETURNVALUE}
fi

## Calculate total time for backup.
FinishTime="$(date +%s)"
ElapsedTime="$(expr ${FinishTime} - ${StartTime})"
Hours=$((${ElapsedTime} / 3600))
ElapsedTime=$((${ElapsedTime} - ${Hours} * 3600))
Minutes=$((${ElapsedTime} / 60))
Seconds=$((${ElapsedTime} - ${Minutes} * 60))

echo "`date +%Y-%m-%d_%H:%M:%S` --- Total backup time: ${Hours} hour(s) ${Minutes} minute(s) ${Seconds} second(s)" >> ${LOGFILE}

echo "`date +%Y-%m-%d_%H:%M:%S` - Rsync me docs completed." >> ${LOGFILE}

## Perform cleanup routine.
f_cleanup
## Exit with the combined return code value.
echo "`date +%Y-%m-%d_%H:%M:%S` - Exit code: ${ERRORFLAG}" >> ${LOGFILE}
exit ${ERRORFLAG}

```The script contains a comment block at the beginning giving detailed information about the purpose and how it should run.  It also mentions that it cannot run if a specific incompatible script is running and it lists the various exit codes that can be expected in the case of an error.  The error code will also be added to the log file every time so you can look at the history of the script and see if there is a pattern of aborts.

You would also need to modify the zoneedit.sh to include a creation of a /tmp/zoneedit.lock file when the script starts and then ensure the file is deleted whenever the script exits (either from an error or clean exit).

The cron schedule can then be modified to call the script as often as you need without worry about incompatible program running at the same time because they will now avoid the situation.

If the zoneedit must also not start if your rsync is running, be sure to add the lockfile check at the beginning to see if the rsync job is running.

Here are [my notes on how to manage crontab schedules]("www.hammondslegacy.com/forum/viewtopic.php?p=261#p261") in case you'd like further info.

crontab.root
```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-08-17 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow command

#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# zoneedit every 5 minutes
#
*/5 * * * * /var/scripts/prod/zoneedit.sh > /dev/null 2>&1
#
# rsync me docs a few times per day
#
0 8,12,17 * * /var/scripts/prod/rsync-docs.sh > /dev/null 2>&1

```LHammonds

---

### Post by ChrisRChamberlain on 2012-08-19
LHammonds

Many thanks for the code and the effort put in - will work through it this coming week and advise the outcome.

---

### Post by ChrisRChamberlain on 2012-08-28
A much belated second vote of thanks to LHammonds for your contribution. 

Hope this thread helps another as much as it has helped me.

---

### Post by LHammonds on 2012-08-29
You're welcome.  I am glad to pay back to a community that has helped me.  Be sure to pay it forward.  ;)

---

