---
title: "Something is wrong with firewalld"
date: 2019-11-06
forum: Server Platforms
---

### Post by George_Ntavelis on 2019-11-06
Hello!

I have a question please... i am running Ubuntu server 18.04.3 LTS. All available updates are installed and machine is running Kernel 4.15.0.66.
For some unknown reason when i execute the command **sudo systemctl status firewalld** i get the following error:

[sudo] password for user:
 firewalld.service
 Loaded: masked (/dev/null; bad)
 Active: inactive (dead)

Sorry about my newbie question.

Thank you in advance!

---

### Post by #&amp;thj^% on 2019-11-06
Have you done this yet?
```
sudo systemctl enable firewalld
```

That command configures the system to start the firewall after each server reboot.

---

### Post by deadflowr on 2019-11-06
try to unmask it.
masking creates a link for it to /dev/null, basically forcing it disabled.
from systemctl man page
> mask UNIT...
           Mask one or more units, as specified on the command line. This will
           link these unit files to /dev/null, making it impossible to start
           them. This is a stronger version of disable, since it prohibits all
           kinds of activation of the unit, including enablement and manual
           activation. Use this option with care. This honors the --runtime
           option to only mask temporarily until the next reboot of the
           system. The --now option may be used to ensure that the units are
           also stopped. This command expects valid unit names only, it does
           not accept unit file paths.

       unmask UNIT...
           Unmask one or more unit files, as specified on the command line.
           This will undo the effect of mask. This command expects valid unit
           names only, it does not accept unit file paths.

---

### Post by George_Ntavelis on 2019-11-06
1fallen thank you for your quick reply. Unfortunately when i am trying to run the command i am getting the following:

Synchronizing state of firewalld.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable firewalld
Failed to enable unit: Unit file /etc/systemd/system/firewalld.service is masked.

---

### Post by George_Ntavelis on 2019-11-06
@deadflowr: I am sorry but i dont know how to do it :/

---

### Post by deadflowr on 2019-11-06
Run the same command 1fallen posted but replace enable with unmask.
```
sudo systemctl unmask firewalld
```

Oh, and then run
```
sudo systemctl start firewalld
```

---

### Post by George_Ntavelis on 2019-11-06
Let me try those two :)

---

### Post by #&amp;thj^% on 2019-11-06
Thanks deadflowr, my reply's are becoming more and more vague to newer users.
I was wondering if the service was enabled first then the mask happened. I should have known that "querying" the "status" with out the service running would indeed mask it. ;)
@George_Ntavelis if the unmask hangs use this also:
```
sudo systemctl unmask --now firewalld
```
Then follow deadflowr's advice on starting it.
If all goes well use my first command to enable at Start-up.

---

### Post by #&amp;thj^% on 2019-11-07
A request for some input here....Did we lose you?

---

### Post by George_Ntavelis on 2019-11-07
i run the command sudo systemctl unmask firewalld , the output is '**Removed /etc/systemd/system/firewalld.service.**'
After i run the command: sudo systemctl start firewalld , no output.

Then i say to myself lets check the status (systemctl status firewalld) and i get the following:

 firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/lib/systemd/system/firewalld.service; disabled; vendor preset: enabled)
   Active: active (running) since Thu 2019-11-07 11:05:19 EST; 4min 2s ago
     Docs: man:firewalld(1)
 Main PID: 17977 (firewalld)
    Tasks: 2 (limit: 4679)
   CGroup: /system.slice/firewalld.service
           &#9492;&#9472;17977 /usr/bin/python3 -Es /usr/sbin/firewalld --nofork --nopid



I said to myself that's it? Is it fixed? So i decided to restart the machine... guess what! After the restart when i run sudo systemctl status firewalld i am getting the following:

firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/lib/systemd/system/firewalld.service; disabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:firewalld(1)

Oh man... why it was working before the restart and now it is not?

---

### Post by #&amp;thj^% on 2019-11-07
We need to enable it for it to start at each boot:
```
sudo systemctl enable firewalld
```
EDIT: You should see something like:
```
me@me-ThinkPad-T430:~$ systemctl enable firewalld
Synchronizing state of firewalld.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable firewalld
==== AUTHENTICATING FOR org.freedesktop.systemd1.reload-daemon ===
Authentication is required to reload the systemd state.
Authenticating as: Me,,, (me)
Password: 
==== AUTHENTICATION COMPLETE ===
==== AUTHENTICATING FOR org.freedesktop.systemd1.reload-daemon ===
Authentication is required to reload the systemd state.
Authenticating as: Me,,, (me)
Password: 
==== AUTHENTICATION COMPLETE ===
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-unit-files ===
Authentication is required to manage system service or unit files.
Authenticating as: Me,,, (me)
Password: 
==== AUTHENTICATION COMPLETE ===

```

---

### Post by deadflowr on 2019-11-07
systemctl start just starts it.
It won't output anything unless there is a problem.
I posted to run it so you can see off the bat if anything is wrong.
Now you know it can load properly.

As posted by 1fallen enabling it should set it to persistently start at bootup.

> i run the command sudo systemctl unmask firewalld , the output is 'Removed /etc/systemd/system/firewalld.service.'
Fwiw, this service file was the link to /dev/null, so removing it stop it from loading it from that abyss.
Running the enable should create a new link to the proper /lib directory file.
(It should show that in the output)

---

### Post by George_Ntavelis on 2019-11-07
Thank you very much for your help guys!

Now its working :) I have one last question please, lets say that i need to temporary stop the firewalld for some time to do something the command will be 'sudo systemctl stop firewalld' am i correct?
If i execute sudo systemctl disable firewalld the firewalld will be disabled on the next boot ... correct?

Thank you for your time and effort :)

---

### Post by #&amp;thj^% on 2019-11-07
Yes Sir!
```
FIREWALLD(1)                       firewalld                      FIREWALLD(1)

NAME
       firewalld - Dynamic Firewall Manager

SYNOPSIS
       firewalld [OPTIONS...]

DESCRIPTION
       firewalld provides a dynamically managed firewall with support for
       network/firewall zones to define the trust level of network connections
       or interfaces. It has support for IPv4, IPv6 firewall settings and for
       ethernet bridges and has a separation of runtime and permanent
       configuration options. It also supports an interface for services or
       applications to add firewall rules directly.

OPTIONS
       These are the command line options of firewalld:

       -h, --help
           Prints a short help text and exists.

       --default-config
           Path to firewalld default configuration. This usually defaults to
           /usr/lib/firewalld.

       --debug[=level]
           Set the debug level for firewalld to level. The range of the debug
           level is 1 (lowest level) to 10 (highest level). The debug output
           will be written to the firewalld log file /var/log/firewalld.

       --debug-gc
           Print garbage collector leak information. The collector runs every
           10 seconds and if there are leaks, it prints information about the
           leaks.

       --nofork
           Turn off daemon forking. Force firewalld to run as a foreground
           process instead of as a daemon in the background.

       --nopid
           Disable writing pid file. By default the program will write a pid
           file. If the program is invoked with this option it will not check
           for an existing server process.

       --system-config
           Path to firewalld system (user) configuration. This usually
           defaults to /etc/firewalld.

CONCEPTS
       firewalld has a D-Bus interface for firewall configuration of services
       and applications. It also has a command line client for the user.
       Services or applications already using D-Bus can request changes to the
       firewall with the D-Bus interface directly. For more information on the
       firewalld D-Bus interface, please have a look at firewalld.dbus(5).

       firewalld provides support for zones, predefined services and ICMP
       types and has a separation of runtime and permanent configuration
       options. Permanent configuration is loaded from XML files in
       /usr/lib/firewalld (--default-config) or /etc/firewalld
       (--system-config) (see the section called &#8220;DIRECTORIES&#8221;).

       If NetworkManager is not in use and firewalld gets started after the
       network is already up, the connections and manually created interfaces
       are not bound to the zone specified in the ifcfg file. The interfaces
       will automatically be handled by the default zone. firewalld will also
       not get notified about network device renames. All this also applies to
       interfaces that are not controlled by NetworkManager if
       NM_CONTROLLED=no is set.

       You can add these interfaces to a zone with firewall-cmd [--permanent]
       --zone=zone --add-interface=interface. If there is a
       /etc/sysconfig/network-scripts/ifcfg-interface file, firewalld tries to
       change the ZONE=zone setting in this file.

       If firewalld gets reloaded, it will restore the interface bindings that
       were in place before reloading to keep interface bindings stable in the
       case of NetworkManager uncontrolled interfaces. This mechanism is not
       possible in the case of a firewalld service restart.

       It is essential to keep the ZONE= setting in the ifcfg file consistent
       to the binding in firewalld in the case of NetworkManager uncontrolled
       interfaces.

   Zones
       A network or firewall zone defines the trust level of the interface
       used for a connection. There are several pre-defined zones provided by
       firewalld. Zone configuration options and generic information about
       zones are described in firewalld.zone(5)

   Services
       A service can be a list of local ports, protocols and destinations and
       additionally also a list of firewall helper modules automatically
       loaded if a service is enabled. Service configuration options and
       generic information about services are described in
       firewalld.service(5). The use of predefined services makes it easier
       for the user to enable and disable access to a service.

   ICMP types
       The Internet Control Message Protocol (ICMP) is used to exchange
       information and also error messages in the Internet Protocol (IP). ICMP
       types can be used in firewalld to limit the exchange of these messages.
       For more information, please have a look at firewalld.icmptype(5).

   Runtime configuration
       Runtime configuration is the actual active configuration and is not
       permanent. After reload/restart of the service or a system reboot,
       runtime settings will be gone if they haven't been also in permanent
       configuration.

   Permanent configuration
       The permanent configuration is stored in config files and will be
       loaded and become new runtime configuration with every machine boot or
       service reload/restart.

   Direct interface
       The direct interface is mainly used by services or applications to add
       specific firewall rules. It requires basic knowledge of ip(6)tables
       concepts (tables, chains, commands, parameters, targets).

DIRECTORIES
       firewalld supports two configuration directories:

   Default/Fallback configuration in /usr/lib/firewalld (--default-config)
       This directory contains the default and fallback configuration provided
       by firewalld for icmptypes, services and zones. The files provided with
       the firewalld package should not get changed and the changes are gone
       with an update of the firewalld package. Additional icmptypes, services
       and zones can be provided with packages or by creating files.

   System configuration settings in /etc/firewalld (--system-config)
       The system or user configuration stored here is either created by the
       system administrator or by customization with the configuration
       interface of firewalld or by hand. The files will overload the default
       configuration files.

       To manually change settings of pre-defined icmptypes, zones or
       services, copy the file from the default configuration directory to the
       corresponding directory in the system configuration directory and
       change it accordingly.

       For more information on icmptypes, please have a look at the
       firewalld.icmptype(5) man page, for services at firewalld.service(5)
       and for zones at firewalld.zone(5).

SIGNALS
       Currently only SIGHUP is supported.

   SIGHUP
       Reloads the complete firewall configuration. You can also use
       firewall-cmd --reload. All runtime configuration settings will be
       restored. Permanent configuration will change according to options
       defined in the configuration files.

SEE ALSO
       firewall-applet(1), firewalld(1), firewall-cmd(1), firewall-config(1),
       firewalld.conf(5), firewalld.direct(5), firewalld.dbus(5),
       firewalld.icmptype(5), firewalld.lockdown-whitelist(5), firewall-
       offline-cmd(1), firewalld.richlanguage(5), firewalld.service(5),
       firewalld.zone(5), firewalld.zones(5), firewalld.ipset(5),
       firewalld.helper(5)

NOTES
       firewalld home page:
           http://firewalld.org

       More documentation with examples:
           http://fedoraproject.org/wiki/FirewallD

AUTHORS
       Thomas Woerner <twoerner@redhat.com>
           Developer

       Jiri Popelka <jpopelka@redhat.com>
           Developer

firewalld 0.7.2                                                   FIREWALLD(1)
```

---

### Post by George_Ntavelis on 2019-11-07
1fallen and deadflowr Thank you so much for your help! :)

---

