---
title: "nagios3 pnp4nagios"
date: 2013-05-24
forum: Server Platforms
---

### Post by dozycat on 2013-05-24
I am installing a new server ubuntu 12.04 to replace an existing 10.04 server.
I have a working nagios with pnp4nagios from oficial repository with ubuntu 10.04.
I am tryng to do the same with ubuntu server 12.04 to replace the old server, I did an update with a copy of the server and tried to update,  it did not boot up.


So I am installing a new server to replace the old.

I found that pnp4nagios is now located in /etc/pnp4nagios in 12.04 and the links of pnp4nagios in nagios.cfg must be changed, but the link:

localhost/pnp4nagios

gives error: perfdata directory "/var/lib/pnp4nagios/perfdata/" is empty.

What is strange is that I used in nagios.cfg:

host_perfdata_file=/tmp/host-perfdata
service_perfdata=/tmp/service_perfdata.


And I checked, and the folder is there and the permissions are ok.
 
Has anyone used pnp4nagios from the repositories?

---

### Post by dozycat on 2013-05-28
I give up on pnpt4nagios from repositories, so desinstalled pnp4nagios, desinstalled nagios.
Installed nagios, repair it so it worked well alone.
Aand triednagiosgrapher, the pipe never got data. So I went back to PNP4NAGIOS but installed from:

[http://docs.pnp4nagios.org/pnp-0.6/install](http://docs.pnp4nagios.org/pnp-0.6/install)

It worked.

---

### Post by 3angle-o on 2013-12-28
I know this may be old, but for future admins:

apt-get install nagios3 pnp4nagios #from repos
get nagios working with atleast one host and service before proceeding.
##it should work out of the box, but test it.
home folders are now /etc/nagios3 /etc/pnp4nagios
besure to make adjustments to nagios.cfg as follows:
process_performance_data=1
host_perfdata_file=/var/lib/pnp4nagios/host-perfdata
service_perfdata_file=/var/lib/pnp4nagios/service-perfdata
host_perfdata_file_template=[HOSTPERFDATA]\t$TIMET$\t$HOSTNAME$\t$HOSTEXECUTIONTIME$\t$HOSTOUTPUT$\t$HOSTPERFDATA$
service_perfdata_file_template=[SERVICEPERFDATA]\t$TIMET$\t$HOSTNAME$\t$SERVICEDESC$\t$SERVICEEXECUTIONTIME$\t$SERVICELATENCY$\t$SERVICEOUTPUT$\t$SERVICEPERFDATA$
host_perfdata_file_mode=a
service_perfdata_file_mode=a
host_perfdata_file_processing_interval=0
service_perfdata_file_processing_interval=0
host_perfdata_file_processing_command=process-host-perfdata-file
service_perfdata_file_processing_command=process-service-perfdata-file

now commands.cfg adding:
define command{
        command_name    process-host-perfdata-file
        command_line    /usr/bin/perl /usr/lib/pnp4nagios/libexec/process_perfdata.pl
}
define command{
        command_name    process-service-perfdata-file
        command_line    /usr/bin/perl /usr/lib/pnp4nagios/libexec/process_perfdata.pl
}

Finally add the pnp4nagios links to hosts and services... generic-host_nagios2.cfg generic-service_nagios2.cfg (to apply to all by default)
within define host{...} add:
         action_url      /pnp4nagios/index.php/graph?host=$HOSTNAME$&srv=_HOST_
and again for service within define service{...}
        action_url      /pnp4nagios/index.php/graph?host=$HOSTNAME$&srv=$SERVICEDESC$

 Some troubleshooting tips:
Turn on debuging for both nagios3 and pnp4nagios within their respenctive configs...
monitor their log files while using services: tail -F /var/log/pnp4nagios/perfdata.log /var/log/nagios3/nagios.log
test out pnp4nagios via [http://localhost/pnp4nagios/](http://localhost/pnp4nagios/)

---

