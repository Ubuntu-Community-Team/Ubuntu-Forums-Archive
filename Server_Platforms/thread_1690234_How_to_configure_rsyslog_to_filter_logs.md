---
title: "How to configure rsyslog to filter logs?"
date: 2011-02-18
forum: Server Platforms
---

### Post by mrwooster on 2011-02-18
I am having a look at loggly, and want to set up rsyslog to send my apache logs to one port and all other logs to a different port.

My rsyslog.conf looks like this:

```
# Access logs for apache                                                        
$ModLoad imfile                                                                 
$InputFileName /path/to/apache/logs.log                                     
$InputFileTag apache-access:                                                      
$InputFileStateFile stat-apache-access                                            
$InputFileSeverity info                                                         
$InputRunFileMonitor                                                            
                                                                                
$InputFilePollInterval 10                                                       
                                                                                
*.* @@logs.loggly.com:<port_number>                                                     
& ~                          
```


What I would like to do is, send all apache access logs to:

@@logs.loggly.com:<a_different_port_number>

and send all other logs that come through rsyslog to 

@@logs.loggly.com:<port_number>

I have tried something along the lines of

if $programname === ... but I cant seem to get the syntax right

Ty

---

### Post by macmonac on 2011-12-19
Hy,

I have the same problem, have you find a solution ?
My version of rsyslog is this of lucid :
rsyslogd 4.2.0, compiled with:
	FEATURE_REGEXP:				Yes
	FEATURE_LARGEFILE:			Yes
	FEATURE_NETZIP (message compression):	Yes
	GSSAPI Kerberos 5 support:		Yes
	FEATURE_DEBUG (debug build, slow code):	No
	Atomic operations supported:		Yes
	Runtime Instrumentation (slow code):	No

Regards

---

### Post by hearno on 2012-05-02
Here's what you do to fix it guys:

First in the standard rsyslog.conf file for monitoring files the user syslog needs to be the group owner of the file.........something that apache2 doesn't do by default so change the "$PrivDropToGroup syslog" to -> "$PrivDropToGroup adm" this should help monitoring files that can be read by the admin group



$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup **adm**


#
#
# Check out the apachelog forwarder in the apache.conf which is in rsyslog.d/ directory
#
# Apache access file



# Forward to Loggly

*.*    @@logs.loggly.com:<port>
#

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf




Just for organizations sake I added my file monitors in a separate .conf file saving it in the /etc/rsyslog.d/ directory here's what that apache.conf looks like

$ModLoad imfile
$InputFileName /var/log/apache2/access.log
$InputFileTag apache-access:
$InputFileStateFile stat-apache-access
$InputFileSeverity info
$InputRunFileMonitor


$ModLoad imfile
$InputFileName /var/log/apache2/error.log
$InputFileTag apache-errors:
$InputFileStateFile stat-apache-error
$InputFileSeverity error
$InputRunFileMonitor

$InputFilePollInterval 10

if $programname == 'apache-access' then @@logs.loggly.com:<port>
& ~
if $programname == 'apache-errors' then @@logs.loggly.com:<port>
& ~  


***Then sudo service rsyslog restart

check out: sudo netstat -tapn and three rsyslogd connections to the ports should be there.

****NOTE that the $InputFileTag is the same as the value that $programname is looking for.  just change the path to the file and you should be good to go on monitoring other files as well.


Hope this helps


It's suggested that you place the apache.conf contents back into the main rsyslog.conf and that it precedes the main drain...the whole config file would look something like:




#  /etc/rsyslog.conf    Configuration file for rsyslog.
#
#                       For more information see
#                       /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html
#
#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf


#################
#### MODULES ####
#################

$ModLoad imuxsock # provides support for local system logging
$ModLoad imklog   # provides kernel logging support (previously done by rklogd)
#$ModLoad immark  # provides --MARK-- message capability

# provides UDP syslog reception
#$ModLoad imudp
#$UDPServerRun 514

# provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514

###########################
#### GLOBAL DIRECTIVES ####
###########################

#
# Use traditional timestamp format.
# To enable high precision timestamps, comment out the following line.
#
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# Filter duplicated messages
$RepeatedMsgReduction on

#
# Set the default permissions for all log files.
#

$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup adm


#
#
#
# Apache access file:

$ModLoad imfile
$InputFileName /var/log/apache2/access.log
$InputFileTag apache-access:
$InputFileStateFile stat-apache-access
$InputFileSeverity info
$InputRunFileMonitor

#Apache Error file:

$ModLoad imfile
$InputFileName /var/log/apache2/error.log
$InputFileTag apache-errors:
$InputFileStateFile stat-apache-error
$InputFileSeverity error
$InputRunFileMonitor

$InputFilePollInterval 10

if $programname == 'apache-access' then @@logs.loggly.com:<port>
& ~
if $programname == 'apache-errors' then @@logs.loggly.com:<port>
& ~  

# Forward syslog messages to Loggly

*.*    @@logs.loggly.com:<port>

#

#
# Include all config files in /etc/rsyslog.d/
#
$IncludeConfig /etc/rsyslog.d/*.conf

---

