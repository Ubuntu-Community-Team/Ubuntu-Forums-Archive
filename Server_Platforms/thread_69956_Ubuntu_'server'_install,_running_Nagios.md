---
title: "Ubuntu 'server' install, running Nagios"
date: 2005-09-28
forum: Server Platforms
---

### Post by tsumi on 2005-09-28
Nagios is a bear to get running properly. I have been messing around with it for quite some time now and just now today got it up, working properly and monitoring.

I was pondering doing a step by step write-up in hopes that it might save someone else the headaches, spitting and cursing that I experienced getting everything to work properly.

Anyone interested?

---

### Post by tsumi on 2005-09-28
I guess this might not be appropriate for this forum as it kind of falls under a "how-to".. Sorry.:?

---

### Post by deuce868 on 2005-09-28
Just do it, if only for your own sake. Put it up and let google find it. You never know who might find it useful one day. 

I setup nagios and know it takes a lot of edits to a lot of files before it's happy. Cool bit of software though.

---

### Post by markrez on 2005-10-07
I would love to see this How-to.  I am very interested in Nagios and any setup procedures you may have.

---

### Post by NixMonk on 2005-10-10
I really like Nagios, the only advice I could offer is with the config files.

I try and make these generic, with no or very little host configuration:

/etc/nagios/
                 cgi.cfg       
                 services.cfg
                 commands.cfg  
                 hosts.cfg       
                 nagios.cfg    
                 timeperiods.cfg
                 contacts.cfg  
                 resource.cfg

Next create a subdirectory named after a group of hosts, IE: linux, ubuntu... Create a file host-template.out. Define what services you want to monitor for generic Linux hosts. Mine looks like this:
```

###############################################################################
# hostname.CFG
#
# Last Modified: XX-XX-2005 BY 
#
###############################################################################

define host{
        host_name               hostname
        alias                   hostname
        address                 
        parents                 
        check_command           check-host-alive
        max_check_attempts      10
        notification_interval   0
        notification_period     24x7
        notification_options    d,r
        contact_groups  admins
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             PING
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notification_interval           0
        notification_period             24x7
        check_command                   check_ping!100.0,20%!500.0,60%
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             Memory
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notifications_enabled           1
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_snmp_memory
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             CPU Load
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notifications_enabled           1
        notification_interval           0
        notification_period             24x7 
        notification_options            c
        check_command                   check_snmp_load
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             Storage
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_snmp_disk
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             Processes
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_snmp_processes
        }define service{
        use                             generic-service
        host_name                       hostname
        service_description             Current Users
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_snmp_users
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             Swap
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_snmp_swap
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             NTP
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              4
        normal_check_interval           5
        retry_check_interval            1
        contact_groups                  admins
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_ntp
        }
define service{
        use                             generic-service
        host_name                       hostname
        service_description             OS Configuration
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              3
        normal_check_interval           10
        retry_check_interval            1
        contact_groups                  admins
        notifications_enabled           1
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_cfengine
        }

define service{
        use                             generic-service
        host_name                       hostname
        service_description             OS Patches
        is_volatile                     0
        check_period                    24x7
        max_check_attempts              3
        normal_check_interval           10
        retry_check_interval            1
        contact_groups                  admins
        notifications_enabled           1
        notification_interval           0
        notification_period             24x7
        notification_options            c
        check_command                   check_yum

```

When you add a new linux host you can just do:
```

cat host-template.out | sed -e 's/address/address       0.0.0.0/g'| sed -e 's/hostname/YOURHOSTNAME/g' >> /etc/nagios/linux/YOURHOSTNAME.cfg

```

Now tell nagios to load any "cfg" it finds in this directory. Add the following line to /etc/nagios/nagios.cfg:
```

cfg_dir=/etc/nagios/linux

```

Now restart nagios, your new host is ready to be monitored. I only use snmp for remote host monitoring, I don't like to install extra software or open more ports SNMP is pretty easy (and fun) to use and widely supported.

Hope that helps some, there are many ways to do this.

---

### Post by Nixed0 on 2005-10-10
I decided to change my account name, this is the old NixMonk. Feeling less monkish these days. Anyways here is a short and simple script to display minimal information. I have users that need this, anymore information than this can cause confusion.

All that should need to be changed is YOURHOST to your nagios httpd server.

```

#!/usr/bin/perl -w
use strict;

my $stateok=0;
my $statecrit=0;
my $line;
my $hostname;
my @hostsok;
my $hostok;
my @hostscrit;
my $hostcrit;
my $colcount=9;

open(DAT, "</var/log/nagios/status.dat") or die("Error opening status file");

while (<DAT>) {
  $line = $_;
  if ($line =~ /host {/) {
    while ($line !~ /}/) {
      $line = <DAT>;
      chomp($line);
      if ($line =~ /host_name=/) {
        $hostname=$line;
        $hostname=~ s/host_name=//;
      } 
      if ($line =~ /current_state=0/) {
        $stateok++;
        @hostsok=(@hostsok,$hostname);
      } elsif ($line =~ /current_state=1/) {
        $statecrit++;
        @hostscrit=(@hostscrit,$hostname);
      }
    }
  }
}
close(DAT);
#sort(@hostsok);
#sort(@hostscrit);

print "Content-type: text/html\n\n";
print "<html><title>System Status</title>\n";
print "<body></body>\n";
print "<center>\n";
print "<table border=1 cellpadding=5 cellspacing=5>\n";
print "<caption><b>$stateok Systems Online</b></caption>\n";
print "<tr>\n";
foreach $hostok(@hostsok){
  chomp($hostok);
  $hostok=~s/\t//;
  if( $colcount < "8" ) {
    print"<td bgcolor=33ff00><a href=http://YOURHOST/nagios/cgi-bin/status.cgi?host=$hostok>$hostok</a></td>\n";
    $colcount++;
  } else {
    print"</tr><tr><td bgcolor=33ff00><a href=http://YOURHOST/nagios/cgi-bin/status.cgi?host=$hostok>$hostok</a></td>\n";
    $colcount=0;
  } 
}
$colcount=9;
print"</tr></table>\n";
print"<hr width=95\% width=5>\n";

if ( @hostscrit) {
  print "<b>Warning $statecrit System Unreachable!</b>\n";
  print "<table border=1 cellpadding=5 cellspacing=5>\n";
  print "<tr>\n";
  foreach $hostcrit(@hostscrit) {
    chomp($hostcrit);
    $hostcrit=~s/\t//;
    if( $colcount < "8" ) {
      print"<td bgcolor=ff0000><a href=http://YOURHOST/nagios/cgi-bin/status.cgi?host=$hostcrit>$hostcrit</a></td>\n";
      $colcount++;
    } else {
      print"</tr><tr><td bgcolor=ff0000>$hostcrit</td>\n";
    }
  }
  $colcount=0;
  print"</tr></table>\n";
} else {
  print"<font color=33ff00><b>All systems OK</b></font>\n";
}

print"</center>\n";
print"</html>\n";

```

Very basic, green box good red box bad. Enjoy:)

---

### Post by markpalinux on 2005-10-25
Another pain in the process is finding out what packages are needed for the config process.

I have tried to compare with the debian packages, if anyone has gotten nagios to config ok, please post your dpkk -l output.

Thanks,
Mark

---

