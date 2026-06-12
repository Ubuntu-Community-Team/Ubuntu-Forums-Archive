---
title: "Managing Iptables with Fwbuilder"
date: 2017-01-05
forum: Security
---

### Post by afastars on 2017-01-05
Hi Expert's,

i got problem managing iptables, problem explanation as follows:


i generate iptables rules by using fwbuilder once the policies has succesfully applied
i'm not be able to ping other machine that has different subnet.


then i reset all iptable rules and tried to make the firewall rule manually and the result is
i able to ping other machine that has different subnet.

I've also check the **ip_forward** is set to **1** for ping and etc to be work correctly.


**Note : the rules created in fwbuilder and manually create directly from iptables is exactly
the same rule.

I've no idea where to adjust the settings. Please help.

---

### Post by TheFu on 2017-01-05
Welcome to the forums.

2013-07-03 is the last update for fwbuilder.  Seems the project is dead. Perhaps using a dead project for security needs might not be the best choice?

If you want help, please post facts. That means the rules. Also, please use "code tags." Avoid images.

---

### Post by Doug S on 2017-01-05
> **TheFu said:**
> Welcome to the forums.

2013-07-03 is the last update for fwbuilder.  Seems the project is dead.Hmmm... we still refer to fwbuilder in [the Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/firewall.html#other-firewall-tools"). Perhaps we should delete the reference. I'll enter a bug report so that I don't forget.

@afastars: to be able to help, and as TheFu mentioned, we would have to see your entire iptables rule set, both your fwbuilder generated one and your manual one. Myself, I prefer the output from "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L".

---

### Post by afastars on 2017-01-05
Hi expert thanks for replied my message, below is the command generated from fwbuilder :


```

#!/bin/sh 
#
#  This is automatically generated file. DO NOT MODIFY !
#
#  Firewall Builder  fwb_ipt v5.1.0.3599
#
#  Generated Thu Dec 29 08:33:58 2016 PST by root
#
# files: * fw.fw /etc/fw.fw
#
# Compiled for iptables 1.4.4
#




FWBDEBUG=""

PATH="/sbin:/usr/sbin:/bin:/usr/bin:${PATH}"
export PATH



LSMOD="/sbin/lsmod"
MODPROBE="/sbin/modprobe"
IPTABLES="/sbin/iptables"
IP6TABLES="/sbin/ip6tables"
IPTABLES_RESTORE="/sbin/iptables-restore"
IP6TABLES_RESTORE="/sbin/ip6tables-restore"
IP="/sbin/ip"
IFCONFIG="/sbin/ifconfig"
VCONFIG="/sbin/vconfig"
BRCTL="/sbin/brctl"
IFENSLAVE="/sbin/ifenslave"
IPSET="/usr/sbin/ipset"
LOGGER="/usr/bin/logger"

log() {
    echo "$1"
    which "$LOGGER" >/dev/null 2>&1 && $LOGGER -p info "$1"
}

getInterfaceVarName() {
    echo $1 | sed 's/\./_/'
}

getaddr_internal() {
    dev=$1
    name=$2
    af=$3
    L=$($IP $af addr show dev $dev |  sed -n '/inet/{s!.*inet6* !!;s!/.*!!p}' | sed 's/peer.*//')
    test -z "$L" && { 
        eval "$name=''"
        return
    }
    eval "${name}_list=\"$L\"" 
}

getnet_internal() {
    dev=$1
    name=$2
    af=$3
    L=$($IP route list proto kernel | grep $dev | grep -v default |  sed 's! .*$!!')
    test -z "$L" && { 
        eval "$name=''"
        return
    }
    eval "${name}_list=\"$L\"" 
}


getaddr() {
    getaddr_internal $1 $2 "-4"
}

getaddr6() {
    getaddr_internal $1 $2 "-6"
}

getnet() {
    getnet_internal $1 $2 "-4"
}

getnet6() {
    getnet_internal $1 $2 "-6"
}

# function getinterfaces is used to process wildcard interfaces
getinterfaces() {
    NAME=$1
    $IP link show | grep ": $NAME" | while read L; do
        OIFS=$IFS
        IFS=" :"
        set $L
        IFS=$OIFS
        echo $2
    done
}

diff_intf() {
    func=$1
    list1=$2
    list2=$3
    cmd=$4
    for intf in $list1
    do
        echo $list2 | grep -q $intf || {
        # $vlan is absent in list 2
            $func $intf $cmd
        }
    done
}

find_program() {
  PGM=$1
  which $PGM >/dev/null 2>&1 || {
    echo "\"$PGM\" not found"
    exit 1
  }
}
check_tools() {
  find_program which
  find_program $IPTABLES 
  find_program $IPTABLES_RESTORE
  find_program $MODPROBE 
  find_program $IP 
}
reset_iptables_v4() {
  $IPTABLES -P OUTPUT  DROP
  $IPTABLES -P INPUT   DROP
  $IPTABLES -P FORWARD DROP

cat /proc/net/ip_tables_names | while read table; do
  $IPTABLES -t $table -L -n | while read c chain rest; do
      if test "X$c" = "XChain" ; then
        $IPTABLES -t $table -F $chain
      fi
  done
  $IPTABLES -t $table -X
done
}

reset_iptables_v6() {
  $IP6TABLES -P OUTPUT  DROP
  $IP6TABLES -P INPUT   DROP
  $IP6TABLES -P FORWARD DROP

cat /proc/net/ip6_tables_names | while read table; do
  $IP6TABLES -t $table -L -n | while read c chain rest; do
      if test "X$c" = "XChain" ; then
        $IP6TABLES -t $table -F $chain
      fi
  done
  $IP6TABLES -t $table -X
done
}


P2P_INTERFACE_WARNING=""

missing_address() {
    address=$1
    cmd=$2

    oldIFS=$IFS
    IFS="@"
    set $address
    addr=$1
    interface=$2
    IFS=$oldIFS



    $IP addr show dev $interface | grep -q POINTOPOINT && {
        test -z "$P2P_INTERFACE_WARNING" && echo "Warning: Can not update address of interface $interface. fwbuilder can not manage addresses of point-to-point interfaces yet"
        P2P_INTERFACE_WARNING="yes"
        return
    }

    test "$cmd" = "add" && {
      echo "# Adding ip address: $interface $addr"
      echo $addr | grep -q ':' && {
          $FWBDEBUG $IP addr $cmd $addr dev $interface
      } || {
          $FWBDEBUG $IP addr $cmd $addr broadcast + dev $interface
      }
    }

    test "$cmd" = "del" && {
      echo "# Removing ip address: $interface $addr"
      $FWBDEBUG $IP addr $cmd $addr dev $interface || exit 1
    }

    $FWBDEBUG $IP link set $interface up
}

list_addresses_by_scope() {
    interface=$1
    scope=$2
    ignore_list=$3
    $IP addr ls dev $interface | \
      awk -v IGNORED="$ignore_list" -v SCOPE="$scope" \
        'BEGIN {
           split(IGNORED,ignored_arr);
           for (a in ignored_arr) {ignored_dict[ignored_arr[a]]=1;}
         }
         (/inet |inet6 / && $0 ~ SCOPE && !($2 in ignored_dict)) {print $2;}' | \
        while read addr; do
          echo "${addr}@$interface"
    done | sort
}


update_addresses_of_interface() {
    ignore_list=$2
    set $1 
    interface=$1 
    shift

    FWB_ADDRS=$(
      for addr in $*; do
        echo "${addr}@$interface"
      done | sort
    )

    CURRENT_ADDRS_ALL_SCOPES=""
    CURRENT_ADDRS_GLOBAL_SCOPE=""

    $IP link show dev $interface >/dev/null 2>&1 && {
      CURRENT_ADDRS_ALL_SCOPES=$(list_addresses_by_scope $interface 'scope .*' "$ignore_list")
      CURRENT_ADDRS_GLOBAL_SCOPE=$(list_addresses_by_scope $interface 'scope global' "$ignore_list")
    } || {
      echo "# Interface $interface does not exist"
      # Stop the script if we are not in test mode
      test -z "$FWBDEBUG" && exit 1
    }

    diff_intf missing_address "$FWB_ADDRS" "$CURRENT_ADDRS_ALL_SCOPES" add
    diff_intf missing_address "$CURRENT_ADDRS_GLOBAL_SCOPE" "$FWB_ADDRS" del
}

clear_addresses_except_known_interfaces() {
    $IP link show | sed 's/://g' | awk -v IGNORED="$*" \
        'BEGIN {
           split(IGNORED,ignored_arr);
           for (a in ignored_arr) {ignored_dict[ignored_arr[a]]=1;}
         }
         (/state/ && !($2 in ignored_dict)) {print $2;}' | \
         while read intf; do
            echo "# Removing addresses not configured in fwbuilder from interface $intf"
            $FWBDEBUG $IP addr flush dev $intf scope global
            $FWBDEBUG $IP link set $intf down
         done
}

check_file() {
    test -r "$2" || {
        echo "Can not find file $2 referenced by address table object $1"
        exit 1
    }
}

check_run_time_address_table_files() {
    :
    
}

load_modules() {
    :
    OPTS=$1
    MODULES_DIR="/lib/modules/`uname -r`/kernel/net/"
    MODULES=$(find $MODULES_DIR -name '*conntrack*' \! -name '*ipv6*'|sed  -e 's/^.*\///' -e 's/\([^\.]\)\..*/\1/')
    echo $OPTS | grep -q nat && {
        MODULES="$MODULES $(find $MODULES_DIR -name '*nat*'|sed  -e 's/^.*\///' -e 's/\([^\.]\)\..*/\1/')"
    }
    echo $OPTS | grep -q ipv6 && {
        MODULES="$MODULES $(find $MODULES_DIR -name nf_conntrack_ipv6|sed  -e 's/^.*\///' -e 's/\([^\.]\)\..*/\1/')"
    }
    for module in $MODULES; do 
        if $LSMOD | grep ${module} >/dev/null; then continue; fi
        $MODPROBE ${module} ||  exit 1 
    done
}

verify_interfaces() {
    :
    echo "Verifying interfaces: eth0 eth1 eth2 lo"
    for i in eth0 eth1 eth2 lo ; do
        $IP link show "$i" > /dev/null 2>&1 || {
            log "Interface $i does not exist"
            exit 1
        }
    done
}

prolog_commands() {
    echo "Running prolog script"
    
}

epilog_commands() {
    echo "Running epilog script"
    
}

run_epilog_and_exit() {
    epilog_commands
    exit $1
}

configure_interfaces() {
    :
    # Configure interfaces
    update_addresses_of_interface "eth0 10.34.109.61/24" ""
    update_addresses_of_interface "eth1 192.168.2.0/24" ""
    update_addresses_of_interface "eth2 192.168.3.0/24" ""
    update_addresses_of_interface "lo 127.0.0.1/24" ""
}

script_body() {
    # ================ IPv4



    (

    echo '*filter'
    # ================ Table 'filter', automatic rules
    echo :INPUT DROP [0:0]
    echo :FORWARD DROP [0:0]
    echo :OUTPUT DROP [0:0]
    # accept established sessions
    echo "-A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT "
    echo "-A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT "
    echo "-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT "
    # backup ssh access
    echo "-A INPUT  -p tcp -m tcp  -s 127.0.0.1/255.255.255.255  --dport 22  -m state --state NEW,ESTABLISHED -j  ACCEPT "
    echo "-A OUTPUT  -p tcp -m tcp  -d 127.0.0.1/255.255.255.255  --sport 22  -m state --state ESTABLISHED,RELATED -j ACCEPT "
    # ================ Table 'filter', rule set Policy
    # 
    # Rule  0 (lo)
    echo "-A INPUT -i lo   -s 127.0.0.1   -m state --state NEW  -j ACCEPT "
    echo ":Cid2890X8568.0 - [0:0]"
    echo "-A OUTPUT -o lo   -s 127.0.0.1   -m state --state NEW  -j Cid2890X8568.0 "
    echo "-A Cid2890X8568.0  -d 10.34.109.61   -j ACCEPT "
    echo "-A Cid2890X8568.0  -d 127.0.0.1   -j ACCEPT "
    echo "-A Cid2890X8568.0  -d 192.168.2.0   -j ACCEPT "
    echo "-A Cid2890X8568.0  -d 192.168.3.0   -j ACCEPT "
    echo ":Cid2890X8568.1 - [0:0]"
    echo "-A OUTPUT -o lo   -s 127.0.0.1   -m state --state NEW  -j Cid2890X8568.1 "
    echo "-A Cid2890X8568.1  -d 10.34.109.61   -j ACCEPT "
    echo "-A Cid2890X8568.1  -d 127.0.0.1   -j ACCEPT "
    echo "-A Cid2890X8568.1  -d 192.168.2.0   -j ACCEPT "
    echo "-A Cid2890X8568.1  -d 192.168.3.0   -j ACCEPT "
    # 
    # Rule  1 (eth0)
    echo "-A INPUT -i eth0   -s 10.34.109.61   -m state --state NEW  -j ACCEPT "
    echo "-A FORWARD -i eth0   -s 10.34.109.61   -m state --state NEW  -j ACCEPT "
    echo "-A OUTPUT -o eth0   -s 10.34.109.61   -m state --state NEW  -j ACCEPT "
    # 
    # Rule  2 (global)
    echo ":RULE_2 - [0:0]"
    echo "-A INPUT  -s 192.168.3.0/24   -m state --state NEW  -j RULE_2 "
    echo "-A RULE_2  -j LOG  --log-level info --log-prefix \"RULE 2 -- ACCEPT \""
    echo "-A RULE_2  -j ACCEPT "
    #
    echo COMMIT



    echo '*nat'
    # ================ Table 'nat',  rule set NAT
    echo :PREROUTING ACCEPT [0:0]
    echo :POSTROUTING ACCEPT [0:0]
    echo :OUTPUT ACCEPT [0:0]
    # 
    # Rule  0 (NAT)
    echo "-A POSTROUTING -o eth0   -s 192.168.2.0/24  -j SNAT --to-source 10.34.109.61 "
    #
    echo COMMIT


    ) | $IPTABLES_RESTORE; IPTABLES_RESTORE_RES=$?
    test $IPTABLES_RESTORE_RES != 0 && run_epilog_and_exit $IPTABLES_RESTORE_RES
}

ip_forward() {
    :
    echo 1 > /proc/sys/net/ipv4/ip_forward
}

reset_all() {
    :
    reset_iptables_v4
}

block_action() {
    reset_all
    # backup ssh access
    $IPTABLES -A INPUT  -p tcp -m tcp  -s 127.0.0.1/255.255.255.255  --dport 22  -m state --state NEW,ESTABLISHED -j  ACCEPT
    $IPTABLES -A OUTPUT  -p tcp -m tcp  -d 127.0.0.1/255.255.255.255  --sport 22  -m state --state ESTABLISHED,RELATED -j ACCEPT
}

stop_action() {
    reset_all
    $IPTABLES -P OUTPUT  ACCEPT
    $IPTABLES -P INPUT   ACCEPT
    $IPTABLES -P FORWARD ACCEPT
}

check_iptables() {
    IP_TABLES="$1"
    [ ! -e $IP_TABLES ] && return 151
    NF_TABLES=$(cat $IP_TABLES 2>/dev/null)
    [ -z "$NF_TABLES" ] && return 152
    return 0
}
status_action() {
    check_iptables "/proc/net/ip_tables_names"
    ret_ipv4=$?
    check_iptables "/proc/net/ip6_tables_names"
    ret_ipv6=$?
    [ $ret_ipv4 -eq 0 -o $ret_ipv6 -eq 0 ] && return 0
    [ $ret_ipv4 -eq 151 -o $ret_ipv6 -eq 151 ] && {
        echo "iptables modules are not loaded"
    }
    [ $ret_ipv4 -eq 152 -o $ret_ipv6 -eq 152 ] && {
        echo "Firewall is not configured"
    }
    exit 3
}

# See how we were called.
# For backwards compatibility missing argument is equivalent to 'start'

cmd=$1
test -z "$cmd" && {
    cmd="start"
}

case "$cmd" in
    start)
        log "Activating firewall script generated Thu Dec 29 08:33:58 2016 by root"
        check_tools
         prolog_commands 
        check_run_time_address_table_files
        
        load_modules "nat "
        configure_interfaces
        verify_interfaces
        
        
        
        script_body
        ip_forward
        epilog_commands
        RETVAL=$?
        ;;

    stop)
        stop_action
        RETVAL=$?
        ;;

    status)
        status_action
        RETVAL=$?
        ;;

    block)
        block_action
        RETVAL=$?
        ;;

    reload)
        $0 stop
        $0 start
        RETVAL=$?
        ;;

    interfaces)
        configure_interfaces
        RETVAL=$?
        ;;

    test_interfaces)
        FWBDEBUG="echo"
        configure_interfaces
        RETVAL=$?
        ;;



    *)
        echo "Usage $0 [start|stop|status|block|reload|interfaces|test_interfaces]"
        ;;

esac

exit $RETVAL


```



Below is the command i manually type directly to iptables

```

#ADD ROUTE
route add -net 192.168.3.0 netmask 255.255.255.0 gw 10.34.109.61
route add -net 192.168.2.0 netmask 255.255.255.0 gw 10.34.109.61


#ENABLE IPV4 FORWDING ON THE FLY
sysctl -w net.ipv4.ip_forward=1

#NAT - ALLOW TO ACCESS INTERNET BY USING FIREWALL IP ADDRESS
iptables -t nat -A POSTROUTING -o eth0 -s 192.168.2.0/24  -j SNAT --to-source 10.34.109.61

```

result from the command above as follows :
```

root@firewall:~# iptables -v -x -n -L
Chain INPUT (policy ACCEPT 240747 packets, 20318228 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 1613 packets, 96843 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2820 packets, 521031 bytes)
    pkts      bytes target     prot opt in     out     source               destination   



root@firewall:~# iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 347 packets, 58034 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 237 packets, 37734 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 204 packets, 13820 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 204 packets, 13820 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       2      117 SNAT       all  --  *      eth0    192.168.2.0/24       0.0.0.0/0            to:10.34.109.61


```
i'm waiting your response and hope we able to resolve this problem. Do you know what third party tools able to used by me to manage iptables besides shorewall and fwbuilder..?

thanks

---

### Post by Doug S on 2017-01-05
> **afastars said:**
> Do you know what third party tools able to used by me to manage iptables besides shorewall and fwbuilder..?A lot of people use ufw (or gufw with a GUI). I have never used either, as I only use iptables directly.

O.K. so your manual iptables is basically empty, except for the SNAT rule. (EDIT: While I was writing this reply, I see you edited your post to basically say that.)

Myself, I do not want to see the complicated script from fwbuilder, but rather I want to see the resulting iptables rule set. i.e. I want to see the output from those same commands I gave earlier and that you used to show us the manual stuff.

EDIT 2: It seems to have some IPV6 stuff. I can not help with that.

---

### Post by TheFu on 2017-01-05
**code tags** please.
Please don't use different fonts.

---

