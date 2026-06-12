---
title: "Making your VPN more secure"
date: 2012-10-17
forum: Security
---

### Post by yeehi on 2012-10-17
If you are using a VPN, there is a nice test to see whether you have DNS leaks [here]("http://www.dnsleaktest.com/").

There is an interesting article about making your VPN more secure [here]("http://torrentfreak.com/how-to-make-vpns-even-more-secure-120419/").

---

### Post by Stonecold1995 on 2012-10-18
Here's another thing that may help making a VPN more secure.  I'm currently making a bash script that's suppose to be a free alternative to the VPNCheck application in the TorrentFreak link.  I'm still working on it (and it's one of my first scripts) so there are some bugs but so far it's doing pretty well.  I use it constantly and rarely have problems.  The variables you'd want to change are in bold-text.

Here it is if anyone wants it and doesn't want to pay for the official "VPNCheck" product (my script has the same name...  I've got to change that soon).

```
#!/bin/bash

#                ###############################################
#                                   VPNCHECK
#                ###############################################
#
# This is a little script which checks to see if your IP address is hidden so you can
# torrent safely.  It will periodically compare your real IP address with your visible
# IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
# kills you torrent client to prevent it from leaking your IP to the MAFIAA.  I suppose
# it could also be used to secure other programs aside from torrent clients (such as
# DoS tools like SlowLoris and HOIC), but that's not what it's intended for.
#
# This script will NOT protect you if you don't already have some kind of VPN or proxy
# set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
# of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
# open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
# your real IP changes and you don't edit this script it will be pretty much useless
# (e.g. if you have a laptop and you use a different router for any reason, such as going
# to a friend's house, a public cafe, you get a new router, etc).
#
#
# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.
#
#
#  TODO:
#  - If a URL is down, skip it and go on to the next instead of retrying it (IMPORTANT!!1)
#  - Add an option to not compress or archive logs, just let them accumulate
#  - Use the DISPLAY variable to check if X is running instead of searching for the Xorg process (?)
#  - Add support for monitoring multiple clients and IPs at once
#  - Enable passing on arguments to the script to override the below variables
#  - Redirect output messages to stdout and stderr correctly
#  - Log events to syslog (?)

# variables to control the behavior of this script
real_ip="**xxx.xxx.xxx.xxx**"       # this is my "real" external IP address
check_interval=60               # how many seconds to wait before checking again
IFS='|'                         # separator between hosts to probe for current ip
client="**ktorrent**"               # the name of the torrent client's parent process
allow_multiple=0                # whether to allow multiple running instances of not (0=no, 1=yes)
lockfile="/tmp/.vpncheck.lock"  # location of the lock file for this script to use
keep_logs=1                     # whether to log events and activities (0=no, 1=yes)
max_logs=10                     # maximum number of logs to keep at once before compressing and archiving them
archive="archive"               # directory to move old logs to
log_dir=~/".vpncheck"     # directory to put log files in
log_name="vpncheck_log_$(date +%a_%b_%d_%T_%Z_%Y).txt"  # format to name logfiles
hosts="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"  # what sites to use to check the external IP

# command line options
if [ $# -ne 0 ]; then
    if [ "$1" = "--help" -o "$1" = "-h" ]; then
        cat << _EOF

               ###############################################
                                  VPNCHECK
               ###############################################

This is a little script which checks to see if your IP address is hidden so you can
torrent safely.  It will periodically compare your real IP address with your visible
IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
kills you torrent client to prevent it from leaking your IP to the MAFIAA.  I suppose
it could also be used to secure other programs aside from torrent clients (such as
DoS tools like SlowLoris and HOIC), but that's not what it's intended for.

This script will NOT protect you if you don't already have some kind of VPN or proxy
set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
your real IP changes and you don't edit this script it will be pretty much useless
(e.g. if you have a laptop and you use a different router for any reason, such as going
to a friend's house, a public cafe, you get a new router, etc).


Command line options:

      -h, --help    display this help


This script is licensed under the WTFPL, Version 2.
_EOF
        exit 0
    fi
    echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
    exit 1
fi

# if keep_logs is set to 0, don't create log_dir and redirect all logging to /dev/null
log_file="/dev/null"
if [ $keep_logs -eq 1 ]; then
    mkdir -p "$log_dir"
    log_file="$log_dir/$log_name.tmp.$$"
fi

cat << _EOF >> "$log_file"
Script started on $(date) with a process name of $0 (PID $$) by $(id -un) (UID $(id -u)).
Real external IP address ("bad" IP) is set to $real_ip.
Checking external IP address every $check_interval seconds.
Target process is $client.


_EOF

# trap relevant signals so the script can finish up cleanly
function finish_up() {
    echo | tee -a "$log_file"
    log "IP has been successfully validated $(($checks-$failed)) times.  Note that the check failed $failed times."
    log "Script recieved signal and will now terminate.  Removing lockfile if present."
    if [ $keep_logs -eq 1 ]; then
        rename 's/\'.tmp.$$'$//' "$log_file"
        cd "$log_dir"
        # if the number of uncompressed logs exceeds max_logs, compress the oldest and move it to archive
        if [ $(ls -l *.txt | wc -l) -gt $max_logs ]; then
            bzip2 -9 $(ls -1t *.txt | tail -1)
            mkdir -p "$archive"
            mv *.bz2 "$archive"
        fi
    fi
    rm -f "$lockfile"
    exit # use to be exit $?, what should it be now?
}
trap finish_up SIGHUP SIGINT SIGTERM

# append $1 to the current date and tail that to the log
function log() {
    echo -e "<$(date)>     $1" | tee -a "$log_file"
    return 0
}

# prevent opening dialog boxes if X isn't running
function check_x() {
    if [ -z "$(pgrep Xorg)" ]; then # use the DISPLAY variable to detect if X is running instead of the process?
        : "$@"
    else
        "$@"
    fi
    return 0
}

# exit if the lockfile inexplicably vanishes
if [ $allow_multiple -eq 0 ]; then
    function check_lock() {
        if [ ! -e "$lockfile" ]; then
            log "The lockfile has inexplicably vanished.  The script will now exit."
            check_x kdialog --sorry "The lockfile has inexplicably vanished.  The script will now exit."
            finish_up
        fi
    }
fi

# function to log changing states of the client and IP (just log, don't do anything about it)
last_state=0
function log_state() {
    state=$1
    if [ $state -ne $last_state ]; then
        case $state in
            1) log "$client is not running.  IP monitoring will be turned off." ;;
            2) log "$client is running, but IP is hidden.  Current IP address is $current_ip." ;;
            3) log "WARNING: The process $client has been caught running without protection.  SIGTERM has been sent."
               (sleep 3 && log "Sending SIGKILL to $client in case it's still alive.") & ;;
        esac
    fi
    last_state=$state
    check_lock
    return 0
}

# only one instance should run if allow_multiple is set to 0
if [ $allow_multiple -eq 0 ]; then
    if [ -e "$lockfile" ]; then
        log "Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run."
        check_x kdialog --error "Only one instance of the script can be running at a time.  If you believe this is a mistake, remove $lockfile and try again."
        rename 's/\'.tmp.$$'$//' "$log_file"
        exit 1
    fi
    echo -e "$(date)\n$0 (PID $$)\n$(id -un) (UID $(id -u))" > "$lockfile"
    log "allow_multiple is set to 0.  Lockfile has been generated."
else
    if [ -e "$lockfile" ]; then
        log "Another instance of this script appears to be running already, but allow_multiple is set to 1.  This script will continue to run, but please note that this may cause problems."
    fi
    # make sure the script won't remove the lockfile for another instance if allow_multiple is set to 1
    unset lockfile
fi

# STATES:
#  0: state unknown, or no state
#  1: client is not running (IP doesn't matter)
#  2: client is running, and IP is hidden
#  3: client is running, but IP is NOT hidden!
failed=0
checks=0
while true; do
    while true; do
        if [ -n "$(pgrep $client)" ]; then
            # this loop adds redundancy to the check in case one or more of the servers are down
            while true; do
                for check_url in $hosts; do
                    last_ip=$current_ip
                    current_ip=$(curl --max-time 20 -s $check_url)
                    let checks=$checks+1
                    if [ -z "$current_ip" -o -n "$(echo "$current_ip" | grep -E '[[:alpha:]]')" ]; then # check if the server responded with an IP address and not an error page or anything (NOT WORKING!?)
                        let failed=$failed+1
                        break 3
                    fi
                    if [ "$current_ip" = "$real_ip" -a -n "$(pgrep $client)" ]; then
                        # IP address is not hidden, but my torrent client is running (sending SIGTERM to the client)
                        log_state 3
                        pid="$(pidof $client)"
                        killall -q $client
                        sleep 5
                        # send SIGKILL to the client (in case it is still running)
                        killall -qs 9 $client
                        (check_x kdialog --title 'Warning!' --sorry "Your torrent client has been caught running without protection.\nFor your safety, the process $client($pid) has been killed.") &
                        break 2
                    else
                        if [ -z "$(pgrep $client)" ]; then
                            # the torrent client is no longer running, so there is no reason to continue checking my IP 
                            log_state 1
                            break 2
                        fi
                        # the torrent client is running, but my IP address is hidden
                        if [ "$current_ip" != "$last_ip" -a -n "$last_ip" ]; then
                            log "External IP address has changed from $last_ip to $current_ip."
                        fi
                        log_state 2
                        sleep $check_interval
                    fi
                done
            done
        else
            # the torrent client is not running, so it doesn't matter if my IP hidden or not
            log_state 1
        fi
            sleep $check_interval
    done
done

# u don goofed
exit 1

```

This will check your IP using several sites, like whatismyipaddress.com and icanhazip.com, etc, against the "real" IP you put into the script.  If it detects that your IP isn't hidden, it will kill your torrent client (default is KTorrent) and warn you that it had to be killed.  It also keeps logs of events (such as a changing IP address, etc).

This script requires KDE, or at least some KDE utilities like kdialog.

---

### Post by TheArtison on 2012-10-22
Awesome. Thanks.

---

### Post by abexman on 2013-04-20
Cool script. Will this work when your VPN is installed no your router? Seems like it should.

---

### Post by Stonecold1995 on 2013-04-20
> **abexman said:**
> Cool script. Will this work when your VPN is installed no your router? Seems like it should.
Yes it will.  Although if the VPN is on your router I think there's less of a chance of it randomly disconnecting.

Also, any updates I make to the script will be posted [here]("http://ubuntuforums.org/showthread.php?t=2032132") (I already updated it quite a bit, although it's still far from finished).

---

