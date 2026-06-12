---
title: "DynDNS iptables auto update script"
date: 2010-12-29
forum: Security
---

### Post by wltj on 2010-12-29
This script creates iptables rules and cron jobs for dynamic hosts  (dyndns.com, no-ip.com, etc). The cron job runs the script at regular  intervals (every 15 minutes by default) checking to see if each host&#8217;s IP  has changed. If so, it updates iptables to allow access from the host&#8217;s new IP, replacing the old rule, and logs changes to /var/log/dyn-iptables.log

```
#! /bin/bash
# http://www.jrepo.org/wp/dyndns-iptables-auto-update-script/
# leave a comment for fixes
# uses: iptables, cron, perl, dig, netfilter multiport support in kernel. see command vars below.
#
#################################### variables #########################################

# commands used in script
rm=$(which rm)
cat=$(which cat)
grep=$(which grep)
perl=$(which perl)

cut=$(which cut)
tail=$(which tail)
dig=$(which dig)
mkdir=$(which mkdir)
chmod=$(which chmod)
crontab=$(which crontab)
dirname=$(which dirname)
basename=$(which basename)
hostname=$(which hostname)
date=$(which date)
sleep=$(which sleep)
iptables=$(which iptables)
iptablessave=$(which iptables-save)
if [ $? -eq 1 ]; then
  inits="/etc/init.d"
  [[ ! -d "$inits" ]] && read -p "Enter your init script directory: " inits
  if [ -f "$inits"/iptables ]; then
  iptablessave="/etc/init.d/iptables save"   # make sure that "save" is a valid function in the iptables init script..
  else
    echo "Problem setting iptablessave command, check lines 26-36 in "$0"."
    exit 1;
  fi
fi

unset PATH # avoid accidental use of $PATH

# lock variables, so cron doesn't run more than one instance of this script at a time.
TMP_LOCKDIR="/tmp/dyn-iptables.lock"
checkcount="1" # start count for lockcheck()
checksleep="2" # wait this many seconds before attempting to run script again.
checkthresh="15" # give up lockcheck()ing after running this many times.

# default options
CRONMINUTES="15" # default minute interval for cron to wait before checking for HOST IP change. Set with -M switch.
CONFDIR="/root/.dyn-iptables" # where files used by script are saved. if you change, do not add trailing /
CHAIN="INPUT"  # change this to whatever iptables chain you want.
TMP_CRONFILE="/tmp/crontmp" # tmp file, makes no difference as long as it doesn't already exist.

# keep these options for a log format consistent with /var/log/messages
LOGDIR="/var/log"
LOGFILE="dyn-iptables.log"
RUNDATE=$( $date +%b\ %d\ %T )
MYHOSTNAME=$( $hostname )
SCRIPTF=$( $basename "$0" ) # ('proc' field in log)

#################################### usage #########################################

usage() {
echo "
Usage: "$0" [-H hostname] [-M minutes] [-TP tcp_ports] [-UP udp_ports]

-h (help)
  Show this help.

-H (host) 
  Dynamic host for which to create/replace firewall rule.

-M (minutes)
  The interval which cron will wait before re-running the script to check for changed IP addresses. Default is 15.

-TP (tcp_ports)
  Port number(s) to open for HOST.
  For non-consecutive ports, use comma separated values with no spaces (-TP 22,80,443).
  For consecutive ports, you can use range syntax (-TP 21:23 for ports 21-23).

-UP (udp_ports)
  Same format as -TP.

Examples:
---------
# opens tcp ports 80, 443 and 3333-3337 for myhost.dyndns.org, will run cron job every 120 minutes.
dyn-iptables.sh -H myhost.dyndns.org -TP 80,443,3333:3337 -M 120

# opens udp port 177 for myhost.dyndns.org
dyn-iptables.sh -H myhost.dyndns.org -UP 177
"
$rm -rf "$TMP_LOCKDIR" && exit 0;
}

############################# cron checks #############################

addcronjob() {
# search cron file for line containing current host and protocol
GREPCRON=$( $grep "$HOST" "$TMP_CRONFILE" | $grep "$P_OPT" )

if [ "$GREPCRON" ]; then
  # if found, replace ports and cron's minute interval
  $perl -pi -e "s!^\*/(\d+)!\*/"$CRONMINUTES"! if m!(^.+$HOST.+$P_OPT(.+)?$)|(^.+$P_OPT.+$HOST(.+)?$)!" "$TMP_CRONFILE"
  $perl -pi -e "s!(-M (\S+) )!-M "$CRONMINUTES" ! if m!(^.+$HOST.+$P_OPT(.+)?$)|(^.+$P_OPT.+$HOST(.+)?$)!" "$TMP_CRONFILE"
  $perl -pi -e "s!($P_OPT (\S+) )!"$P_OPT" "$PORTS" ! if m!(^.+$HOST.+$P_OPT(.+)?$)|(^.+$P_OPT.+$HOST(.+)?$)!" "$TMP_CRONFILE"
else
  # set cron string
  CRONJOB="*/"$CRONMINUTES"\t*\t*\t*\t*\t/bin/bash "$SCRIPTD"/"$SCRIPTF" "$ARGS2" > /dev/null 2>&1"
  # append new job to crontab.
  echo -e "$CRONJOB" >> "$TMP_CRONFILE"
fi
return
}

#############################  log #############################

writetolog() {
LOGLINE=""$RUNDATE" "$MYHOSTNAME" "$SCRIPTF" "$LOGMSG""
echo "$LOGLINE" >> "$LOGDIR"/"$LOGFILE"
return
}

############################# update firewall #############################

buildfirewall() {
[ ! -d "$CONFDIR" ] && $mkdir -p "$CONFDIR" && $chmod 700 "$CONFDIR"

HOSTIP_FILE="$CONFDIR/ipaddr_"$HOST""

# lookup IP of HOST from DNS servers using dig command.
echo "DIGGING $HOST"
NEWIP=$( $dig +short "$HOST" | $tail -n 1 )
echo "$NEWIP" | $grep -qi "timed out"

if [[ $? -eq 0 ]] || [[ ! "$NEWIP" ]]; then
  echo "Error: couldn't lookup hostname/ip for "$HOST""
  $rm -rf "$TMP_LOCKDIR"
  exit 1;
fi
[ ! "$NEWIP" ] && echo "Error: couldn't lookup hostname/ip for "$HOST"" && $rm -rf "$TMP_LOCKDIR" && exit 1;

# look for existing iptables rules for NEWIP
NEWIP_RULENUM=$( $iptables -L "$CHAIN" -n --line-numbers | $perl -ane "print @F[0] if /(^.+$PROTOCOL.+$NEWIP(.+)$)/" )

if [ -f $HOSTIP_FILE ]; then
  # if host ip file exists, assign OLDIP the ip address inside the file.
    OLDIP=$( $cat "$HOSTIP_FILE" )
    # look for existing iptables rule for OLDIP / Protocol
  OLDIP_RULENUM=$( $iptables -L "$CHAIN" -n --line-numbers | $perl -ane "print @F[0] if /(^.+$PROTOCOL.+$OLDIP(.+)$)/" )
fi

# Now that OLDIP, OLDIP_RULENUM, NEWIP, and NEWIP_RULENUM are defined,
# start checking iptables rules...

if [ "$OLDIP_RULENUM" != "" -a "$NEWIP_RULENUM" != "" ]; then  # if both rules exist...
  if [ "$OLDIP_RULENUM" != "$NEWIP_RULENUM" ]; then # and they are not the same rule...
    $iptables -D "$CHAIN" "$OLDIP_RULENUM" # then delete rule for OLDIP
    # write to log
    LOGMSG="[ "$HOST": "$OLDIP" Old IP deleted from "$CHAIN" chain. (New IP matches already existing rule.) ]"
    writetolog "$LOGMSG"
    # and update/replace existing rule for NEWIP.
    if [ "$MULTIPORT" = "true" ]; then
      $iptables -R "$CHAIN" "$NEWIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" -m multiport --dports "$PORTS" -j ACCEPT
    else
      $iptables -R "$CHAIN" "$NEWIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" --dport "$PORTS" -j ACCEPT
    fi
    # save new ip to file and save rules.
      echo "$NEWIP" > "$HOSTIP_FILE"
    $iptablessave
    return
  else 
    # if OLDIP_RULENUM and NEWIP_RULENUM are the same rule, replace/update it.
    if [ "$MULTIPORT" = "true" ]; then
      $iptables -R "$CHAIN" "$NEWIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" -m multiport --dports "$PORTS" -j ACCEPT
    else
      $iptables -R "$CHAIN" "$NEWIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" --dport "$PORTS" -j ACCEPT
    fi
    # save new ip to file and save rules.
      echo "$NEWIP" > "$HOSTIP_FILE"
    $iptablessave
    return
  fi
elif [ "$OLDIP_RULENUM" != "" -a "$NEWIP_RULENUM" = "" ]; then  # replace OLDIP rule with NEWIP rule.
  if [ "$MULTIPORT" = "true" ]; then
    $iptables -R "$CHAIN" "$OLDIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" -m multiport --dports "$PORTS" -j ACCEPT
    LOGMSG="[ "$HOST": "$OLDIP" -> "$NEWIP" IP changed. Replaced "$CHAIN" rule #"$OLDIP_RULENUM". ]"
    writetolog "$LOGMSG"
  else
    $iptables -R "$CHAIN" "$OLDIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" --dport "$PORTS" -j ACCEPT
    LOGMSG="[ "$HOST": "$OLDIP" -> "$NEWIP" IP changed. Replaced "$CHAIN" rule #"$OLDIP_RULENUM". ]"
    writetolog "$LOGMSG"
  fi
  # save new ip to file and save rules.
    echo "$NEWIP" > "$HOSTIP_FILE"
  $iptablessave
  return
elif [ "$OLDIP_RULENUM" = "" -a "$NEWIP_RULENUM" != "" ]; then  # if rule exists for NEWIP but not OLDIP, update it.
  if [ "$MULTIPORT" = "true" ]; then
    $iptables -R "$CHAIN" "$NEWIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" -m multiport --dports "$PORTS" -j ACCEPT
  else
    $iptables -R "$CHAIN" "$NEWIP_RULENUM" -s "$NEWIP"/32 -p "$PROTOCOL" --dport "$PORTS" -j ACCEPT
  fi
  # save new ip to file and save rules.
    echo "$NEWIP" > "$HOSTIP_FILE"
  $iptablessave
  return
else # Neither rule exists so append new rule for NEWIP
  if [ "$MULTIPORT" = "true" ]; then
    $iptables -A "$CHAIN" -s "$NEWIP"/32 -p "$PROTOCOL" -m multiport --dports "$PORTS" -j ACCEPT
    LOGMSG="[ "$HOST": "$NEWIP" New rule appended to "$CHAIN" chain. ]"
    writetolog "$LOGMSG"
  else
    $iptables -A "$CHAIN" -s "$NEWIP"/32 -p "$PROTOCOL" --dport "$PORTS" -j ACCEPT
    LOGMSG="[ "$HOST": "$NEWIP" New rule appended to "$CHAIN" chain. ]"
    writetolog "$LOGMSG"
  fi
  # save new ip to file and save rules.
    echo "$NEWIP" > "$HOSTIP_FILE"
  $iptablessave
  return
fi
}

############################# set port options #############################

portopts() {
# port is numeric check
echo "$PORTS" | $grep -E '[^0-9,:]' > /dev/null
if [ $? -eq 0 ]; then
  echo -e "\nInvalid port format.\n"
  $rm -rf "$TMP_LOCKDIR"
  exit 1;
fi
# Do we need to use iptables multiport module?
GREPPORTS=$( echo "$PORTS" | $grep -E ',|:' )
[ "$GREPPORTS" ] && MULTIPORT=true || MULTIPORT=false
return
}

############################# start checking args #############################

main() {
# check if root
[[ "$UID" -ne 0 ]] && echo -e "\nOnly root can run this script.\n" && $rm -rf "$TMP_LOCKDIR" && exit 1;

# if no args given or arg is -h, show usage
[ "${#ARGS[@]}" -lt 1 -o "${ARGS[0]}" = "-h" -o "${ARGS[0]}" = "--help" ] && usage

# if TCP and UDP are set at same time
if echo "$ARGS2" | $grep -E "\-TP" | $grep -E "\-UP" > /dev/null
  then
  echo -e "\nPlease select one protocol or the other (-TP or -UP)\n" && $rm -rf "$TMP_LOCKDIR" && exit 1;
fi

#get absolute path to script
SCRIPTD="$( cd "$( "$dirname" "$0" )" && pwd )"

while [ "${ARGS[0]}" ]; do
  # make sure that ARGS array has second element (the value for element 0, which is the flag)..
  [ -z "${ARGS[1]}" ] && echo -e "\nYou must specifiy a value for parameter: "${ARGS[0]}"\n" && $rm -rf "$TMP_LOCKDIR" && exit 1;

  case "${ARGS[0]}" in
  -H )
    HOST="${ARGS[1]}"
    unset ARGS[0] ARGS[1]
    ARGS=( "${ARGS[@]}" )
    ;;
  -M )
    CRONMINUTES="${ARGS[1]}";
    unset ARGS[0] ARGS[1]
    ARGS=( "${ARGS[@]}" )
    ;;
  -TP )
    PROTOCOL="tcp"
    P_OPT="\-TP" # used in croncheck
    PORTS="${ARGS[1]}"
    portopts $PORTS $TMP_LOCKDIR
    unset ARGS[0] ARGS[1]
    ARGS=( "${ARGS[@]}" )
    ;;
  -UP )
    PROTOCOL="udp"
    P_OPT="\-UP" # used in croncheck
    PORTS="${ARGS[1]}"
    portopts $PORTS $TMP_LOCKDIR
    unset ARGS[0] ARGS[1]
    ARGS=( "${ARGS[@]}" )
    ;;
  * )
    usage
    esac
done

if [[ "$PORTS" ]] && [[ "$HOST" ]]; then
  # write current root crontab to temp file
  $crontab -u root -l > "$TMP_CRONFILE"

  # set -M minute interval (for the croncheck) if it wasn't specified
  echo "$ARGS2" | $grep -q "\-M"
  [[ $? -eq 1 ]] && ARGS2=$( echo ""$ARGS2" -M 15" ) # add default -M 15
  buildfirewall
  addcronjob

  # finish up
  $perl -pi -e 's/^\n//g' "$TMP_CRONFILE" # remove any empty lines in cronfile
  echo -e "\n" >> "$TMP_CRONFILE" # add trailing newline
  $crontab -u root "$TMP_CRONFILE" # write to root's crontab
  if [ "$iptablessave" = "/sbin/iptablessave" ]; then
    $iptablessave > "$RULES_FILE" # save separate copy of rules
  fi
  $rm -rf "$TMP_LOCKDIR" "$TMP_CRONFILE"
  exit 0
else # ports are not set
  echo -e "\nPlease specify a host (-H) and allowed ports to access.\n"
  $rm -rf "$TMP_LOCKDIR"
  exit 1
fi
}

lockcheck() {
if [ "$checkcount" -le "$checkthresh"  ]; then
  if ! $mkdir "$TMP_LOCKDIR" > /dev/null 2>&1
  then
    $sleep "$checksleep"
    ((checkcount++))
    lockcheck
  else
    main # start checking args.
  fi
else
  # Script won't run because $TMP_LOCKDIR still exists.
  LOGLINE=""$RUNDATE" "$MYHOSTNAME" "$SCRIPTF" [ Oops, script didn't run because "$TMP_LOCKDIR" still exists from previous instance. ]"
  echo "$LOGLINE" >> "$LOGDIR"/"$LOGFILE"
  exit 1;
fi
}

ARGS=( $* ) # store script input arguments to an array to be chopped up in 'main'
ARGS2="${ARGS[*]}" # ARGS2 used in CRONJOB variable in 'addcronjob'
lockcheck # start script.

```crontab entries, log entries, and iptables output


[IMG]http://www.jrepo.org/im/dyn-iptables.png[/IMG]
[IMG]http://jrepo.org/im/dyn-iptables.gif[/IMG]

---

### Post by primski on 2012-10-02
Hello,

I'm using this script and it works ok. I have iptables in place and I need a certain dyndns host to be allowed to access server on some of the ports. Thats great and this script adds the rule to the INPUT chain at the end.

But, I have a itpables.test.rules where I have all my rules defined and have them put in effect on nic up/down, works great.

My last rule in INPUT chain is REJECT everything, like it should be, right?

But then this script adds the allow rule below this REJECT ALL rule and of course doesn't work.

Either modify the script to insert rule at certain position, adding another argument would work, or i need to rewrite my rules a little, but since I don't know much about all this, I don't know how should my rules be defined.

Here are my rules:

> 
*filter

#  Allows all loopback (lo0) traffic and drop all traffic to 127/8 that doesn't use lo0
-A INPUT -i lo -j ACCEPT
-A INPUT -i lo -d 127.0.0.0/8 -j REJECT

#  Accepts all established inbound connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#  Allows all outbound traffic
#  You can modify this to only allow certain traffic
-A OUTPUT -j ACCEPT

# Allow local traffic
-A INPUT -p tcp -s 127.0.0.1/8 -j ACCEPT
-A INPUT -p tcp -s SERVER_PUBLIC_IP/32 -j ACCEPT

# Allows ALL traffic from Location 1
-A INPUT -p tcp -s SOME_PUBLIC_IP/32 -j ACCEPT

# Allow All from Location 2
-A INPUT -p tcp -s SOME_PUBLIC_IP/32 -j ACCEPT

# Allow ping
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT

# Allow Zimbra Ports
-A INPUT -p tcp --dport 25 -j ACCEPT
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 110 -j ACCEPT
-A INPUT -p tcp --dport 143 -j ACCEPT

-A INPUT -p tcp --dport 443 -j ACCEPT
-A INPUT -p tcp --dport 465 -j ACCEPT
-A INPUT -p tcp --dport 993 -j ACCEPT
-A INPUT -p tcp --dport 995 -j ACCEPT

# log iptables denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7

# Reject all other inbound - default deny unless explicitly allowed policy
-A INPUT -j REJECT
-A FORWARD -j REJECT

COMMIT

any help greatly appreciated,

thanks a lot

bye.


edit: problem seems fixed - i modified the script a little so it deletes the REJECT all rule before inserting new rule and adding REJECT all rule back after it adds dyndns hosts ip, so it ensures that REJECT all rule is in fact at the end of chain.

---

