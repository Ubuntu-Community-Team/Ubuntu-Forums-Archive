---
title: "Creating a Web Browser Logger"
date: 2011-11-09
forum: Security
---

### Post by SparTacux on 2011-11-09
I've just posted a tutorial for creating a web browser logger using GUFW/UFW  to intercept Web Browser traffic. I thought I'd post a copy here for you guys to test out while it's going through the process of being accepted/declined by the Forum moderators.

The mods can delete this thread if the tutorial is accepted.

PS: I had problems pasting the UFW config file in the message window so I had to make some changes to it - I haven't tested this amended version. Let me know if it works or not.

Ta

---

### Post by SparTacux on 2011-11-09
CREATING A PERMANENT LOG OF YOUR INTERNET BROWSING ACTIVITIES.


Since I've been a member of the Ubuntu forum I've come across quite a few people requesting some sort of utility or program for observing traffic when using a browser on the internet. It was my aim to provide such a 'utility' and the following tutorial describes how to do this.

Ubuntu supplies the program UFW ( Uncomplicated Firewall ) for managing a Firewall. UFW also logs all Firewall activity on your computer. GUFW is a GUI front end for UFW which many people use on Ubuntu and Linux Mint for configuring their Firewall.

All UFW log data is written to the file /var/log/ufw.log file which can be viewed with Ubuntu's Log File Viewer. The log level details in UFW can be set to various levels ( from low - full ) by setting the log level preferences in GUFW. The downside is that UFW writes it's Firewall logs to syslog, kern, messages as well as ufw.log.

If you adjust the log levels to high you will see ufw.log provide Firewall data for all traffic on your computer. This would include HTTP, HTTPS, FTP, DNS , MDNS, IPP, ICMP, POP, SMTP, IPP, DHCP and a whole lot more depending on what services you are using. Going through the ufw.logs can be a nightmare as it shows all blocked traffic, all allowed traffic and also shows audit data before making a decision to allow or block traffic.

To make it easier to find your web browser traffic in the Firewall logs we need to intercept the browser log data being written to ufw.log. Then copy the data to a separate file. I also wanted to stop firewall data filling up syslog, kern and messages logs so that we can increase the UFW log level from low to high to get a more detailed view of traffic on your computer. In addition to this I needed a separate file for logging blocked traffic so I didn't have to scroll through the ufw.log ( using Ubuntu Log File Viewer ) to find it.

UFW has a special configuration file called 20-ufw.conf which can be found in the etc/rsyslog.d folder. This config file causes UFW to write it's logs to the file ufw.log. We need to modify this file to create the browser logger. Backup the original 20-ufw.conf file using sudo Nautilus and select copy ( or whatever method you prefer ) Open 20-ufw.conf and delete it's contents and copy and paste the file below. Save the new 20-ufw.conf file. Then to apply the changes either restart your computer or run terminal and type:

sudo restart rsyslog

Two new log files will be created in the /var/log folder... One called "ufwbrowser.log" and the other "ufwblocks.log" You can view these logs by running Ubuntu's Log File Viewer and select File on the main menu and then select open. Scroll down the list of log files and open both "ufwblocks.log" and "ufwbrowser.log" Click on the ufwbrowser.log ( in Log File Viewer ) to open the log file contents. Fire up Firefox or whatever browser you use and watch the http and https traffic in your log viewer in real time.

Job Done !!!


FINAL NOTES ( PLEASE READ )

If you have never used GUFW or UFW before then I recommend you learn how to use it to configure your Firewall before making changes to your 20-ufw.conf file. It is not my intention to provide information on how to use GUFW or provide information on how to set up Firewalls. There are many threads on this topic which can be found in the Security section of the Ubuntu Forums.

If you are familiar with GUFW....

Run GUFW and set the log levels to high or full( GUFW Edit>preferences ) so that UFW sends all firewall activity to the Firewall logs. If you add your own firewall rules using GUFW then make sure you tick the "show extended actions" box and select Log. This makes sure UFW logs your new rule.

The two new log files which have been created can grow to quite a size - especially the browserlog. They can reach many megabytes in size and will eventually cause the Log File Viewer to become sluggish and unresponsive if they get too big. The ufw.log file is automatically rotated by the system so this is not a problem. The ufwbrowser.log and ufwblocks.log need to be backed up and deleted from time to time. You could apply some sort of log rotation scheme to these two files but you will lose a permanent record of your internet activities if you select this method. The choice is up to you.

At the moment only HTTP and HTTPS traffic is sent to your ufwbrowser log. You could easily modify the file below to add FTP ( 21 ) traffic , etc.

The ufw.log still captures ALL traffic on your system as it did before including the Browser traffic and Blocked traffic - so no changes here except AUDIT data is removed.

I have NOT used this 'utility' without using GUFW as a GUI front end for UFW. It 'should' work with UFW alone ( for those of you who don't use GUFW ). Maybe some of the guys on the Forum will test it out and give me feedback on the subject.

Enjoy
SPARTACUX

COPY AND PASTE THE FOLLOWING INTO 20-ufw.conf:


#********************************************************
# WEB BROWSER LOGGER USING GUFW/UFW
#
#  ALSO STOPS UFW LOGS GOING TO SYSLOG, MESSAGES AND
#  KERNAL LOGS. IT CREATES ANOTHER LOG FILE FOR
#  VIEWING BLOCKED TRAFFIC AND IGNORES UFW AUDIT DATA 
#
# CREATED BY SPARTACUX NOV 2011
#
# The Author accepts no liability for this file and
# users use it at their own risk
#**********************************************************

# LOG UFW BLOCKED TRAFFIC TO SEPARATE LOG FILE #
:msg ,contains, "UFW BLOCK" /var/log/ufwblocks.log

# LOG HTTP and HTTPS TO SEPARATE BROWSER LOG #
:msg, regex, "UFW ALLOW.*DPT=80" /var/log/ufwbrowser.log
:msg, regex, "UFW ALLOW.*DPT=443" /var/log/ufwbrowser.log


# DON'T WRITE AUDIT DATA TO UFW LOGS #
:msg ,contains, "UFW AUDIT" ~
&~

# KEEP UFW DATA TO UFW LOGS ONLY #
:msg ,contains, "[UFW" /var/log/ufw.log
&~

#************************************************************
# NOTES:
#
# This file replaces /etc/rsyslog.d/20-ufw.conf
# and handles all UFW data.
#
#I F USING GUFW TO ADD YOUR OWN FIREWALL RULES THEN
# MAKE SURE YOU SET EACH RULE TO LOG ITS OUTPUT BY
# SELECTING THE ADVANCED RULE OPTIONS AND SELECTING
# SHOW EXTENDED ACTIONS.
#
# ALSO SET GUFW LOG LEVELS TO HIGH OR FULL ( GUFW
# PREFERENCES ) TO GET THE BEST OUT OF THIS UFW
# UTILITY. YOU CAN OPEN "ufwbrowser.log" AND
#" ufwblocks.log" WITH UBUNTU'S LOG FILE VIEWER.
#**************************************************************

---

