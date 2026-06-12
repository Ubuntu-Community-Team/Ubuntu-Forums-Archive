---
title: "activate snmp trap cpu and disk monitoring"
date: 2009-11-17
forum: Server Platforms
---

### Post by MatsB on 2009-11-17
Hi,

Could anyone point me in the right direction when it comes to snmpd.conf configuration? I would like to setup my servers so that they send a trap to our managment station when the cpu and disk goes over a certain threshold value.

I know I can define threshold values with disk and load comands but how can I make the server send traps?

This is my snmpd.conf file
NET-SNMP version:  5.4.1

```

###########################################################################
#
# snmpd.conf
#
#   - created by the snmpconf configuration program
#
###########################################################################
# SECTION: System Information Setup
#
#   This section defines some of the information reported in
#   the "system" mib group in the mibII tree.

# syslocation: The [typically physical] location of the system.
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysLocation.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  location_string

syslocation  *remove for privacy issue*

# syscontact: The contact information for the administrator
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysContact.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  contact_string

syscontact  *remove for privacy issue*



###########################################################################
# SECTION: Agent Operating Mode
#
#   This section defines how the agent will operate when it
#   is running.

# master: Should the agent operate as a master agent or not.
#   Currently, the only supported master agent type for this token
#   is "agentx".
#   
#   arguments: (on|yes|agentx|all|off|no)

# master  agentx



###########################################################################
# SECTION: Trap Destinations
#
#   Here we define who the agent will send traps to.

# trap2sink: A SNMPv2c trap receiver
#   arguments: host [community] [portnum]

trap2sink  *remove for privacy issue*

# authtrapenable: Should we send traps when authentication failures occur
#   arguments: 1 | 2   (1 = yes, 2 = no)

authtrapenable  1



###########################################################################
# SECTION: Monitor Various Aspects of the Running Host
#
#   The following check up on various aspects of a host.

# proc: Check for processes that should be running.
#     proc NAME [MAX=0] [MIN=0]
#   
#     NAME:  the name of the process to check for.  It must match
#            exactly (ie, http will not find httpd processes).
#     MAX:   the maximum number allowed to be running.  Defaults to 0.
#     MIN:   the minimum number to be running.  Defaults to 0.
#   
#   The results are reported in the prTable section of the UCD-SNMP-MIB tree
#   Special Case:  When the min and max numbers are both 0, it assumes
#   you want a max of infinity and a min of 1.

proc  ntpd 1 1

# disk: Check for disk space usage of a partition.
#   The agent can check the amount of available disk space, and make
#   sure it is above a set limit.  
#   
#    disk PATH [MIN=100000]
#   
#    PATH:  mount path to the disk in question.
#    MIN:   Disks with space below this value will have the Mib's errorFlag set.
#           Can be a raw byte value or a percentage followed by the %
#           symbol.  Default value = 100000.
#   
#   The results are reported in the dskTable section of the UCD-SNMP-MIB tree

disk  / 10%

# load: Check for unreasonable load average values.
#   Watch the load average levels on the machine.
#   
#    load [1MAX=12.0] [5MAX=12.0] [15MAX=12.0]
#   
#    1MAX:   If the 1 minute load average is above this limit at query
#            time, the errorFlag will be set.
#    5MAX:   Similar, but for 5 min average.
#    15MAX:  Similar, but for 15 min average.
#   
#   The results are reported in the laTable section of the UCD-SNMP-MIB tree

load  5 3 3



###########################################################################
# SECTION: Access Control Setup
#
#   This section defines who is allowed to talk to your running
#   snmp agent.

# rocommunity: a SNMPv1/SNMPv2c read-only access community name
#   arguments:  community [default|hostname|network/bits] [oid]

rocommunity  *remove for privacy issue*

```

---

### Post by Hafsa Ansari on 2011-02-04
Hi MatsB,
Just read your post. I also have the same problem. I want my ubuntu machine to automatically generate a trap message when apache service gets down. I searched net alot for it but no result :(. Can you please help me.
Thanks in advance 

Regards,
Hafsa

---

### Post by creatureofthedark on 2012-02-02
hey guys im trying to work out the exact same thing!!!! the only snmp trap i seem to be able to receive from ubuntu is uptime.... the only thing  I can manage to work is polling using snmpget....

---

