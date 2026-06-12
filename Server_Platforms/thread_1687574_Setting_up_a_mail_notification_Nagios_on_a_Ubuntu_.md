---
title: "Setting up a mail notification Nagios on a Ubuntu machine"
date: 2011-02-14
forum: Server Platforms
---

### Post by Sturme on 2011-02-14
Hi,

I I'm currently working on Nagios Core 3.2.2, and I'm trying to set up a mail notification.

I already install postfix and mailx. And I'm able to send a mail via Ubuntu. I checked this with the command: echo "mail test" | mailx -s "test subject" *mail address*. 


My configuration for sending alerts are:

> ###############################################################################
#
# SAMPLE NOTIFICATION COMMANDS
#
# These are some example notification commands. They may or may not work on
# your system without modification. As an example, some systems will require
# you to use "/usr/bin/mailx" instead of "/usr/bin/mail" in the commands below.
#
################################################################################


# 'host-notify-by-email' command definition
define command{
command_name host-notify-by-email
command_line /usr/bin/printf "%b" "***** Nagios 2.9 *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /bin/mail -s "Host $HOSTSTATE$ alert for $HOSTNAME$!" $CONTACTEMAIL$
}


# 'host-notify-by-epager' command definition
define command{
command_name host-notify-by-epager
command_line /usr/bin/printf "%b" "Host '$HOSTALIAS$' is $HOSTSTATE$\nInfo: $HOSTOUTPUT$\nTime: $LONGDATETIME$" | /bin/mail -s "$NOTIFICATIONTYPE$ alert - Host $HOSTNAME$ is $HOSTSTATE$" $CONTACTPAGER$
}

# 'notify-by-email' command definition
define command{
command_name notify-by-email
command_line /usr/bin/printf "%b" "***** Nagios 2.9 *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | /bin/mail -s "** $NOTIFICATIONTYPE$ alert - $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$
}


# 'notify-by-epager' command definition
define command{
command_name notify-by-epager
command_line /usr/bin/printf "%b" "Service: $SERVICEDESC$\nHost: $HOSTNAME$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\nInfo: $SERVICEOUTPUT$\nDate: $LONGDATETIME$" | /bin/mail -s "$NOTIFICATIONTYPE$: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$" $CONTACTPAGER$
}

###############################################################################
###############################################################################
#
# TIME PERIODS
#
###############################################################################
###############################################################################

# This defines a timeperiod where all times are valid for checks, 
# notifications, etc.  The classic "24x7" support nightmare. :-)

define timeperiod{
        timeperiod_name 24x7
        alias           24 Hours A Day, 7 Days A Week
        sunday          00:00-24:00
        monday          00:00-24:00
        tuesday         00:00-24:00
        wednesday       00:00-24:00
        thursday        00:00-24:00
        friday          00:00-24:00
        saturday        00:00-24:00
        }> define contact{
contact_name Nagios
alias Nagiosadmin
service_notification_period 24x7
host_notification_period 24x7
service_notification_options w,u,c,r
host_notification_options d,r
service_notification_commands notify-by-email
host_notification_commands host-notify-by-email
email *mailaddress*
}> define contactgroup{
        contactgroup_name       admins
        alias                   admins
        members                 Nagios        
}> define service{
    use                     generic-service
    host_name               svr-monitoring.penthese-dmn.local
    service_description     ssh_check load 
    check_command           ssh_load2!5.0,4.0,3.0!10.0,6.0,4.0
    contact_groups          admins
}I get a error when I update and restart Nagios: 
> Error: Template 'generic-service' specified in service definition could not be not found (config file '/etc/nagios/conf.d/services.cfg', starting on line 1)
And I don't know if all the other configurations, shown above, are correct.

Can anyone please help me,

Cheers

---

