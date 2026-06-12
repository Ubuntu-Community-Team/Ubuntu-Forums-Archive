---
title: "Linux Host and Network Security"
date: 2008-04-04
forum: Security Discussions
---

### Post by kevross_33 on 2008-04-04
Hey. I want to make people aware of several great solutions for security that are easy to use. First is Ossec ([www.ossec.net](www.ossec.net)) that is easy to install the agent and web interface and can provideo rootkit detection, intrusion prevention, integrity checking and so on. It looks at various logs and assigns risk ratings. This can be for multiple failed SSH or apache logins, brute force, scanning, exploitation etc and can look at the snort /var/log/snort/alert file and then will create a firewall block to detected intrusions. It makes any Linux device capable of defending itself.

Also with agents you can monitor multiple Linux and Windows hosts looking for intrusion patterns before it generates and alert. Almost like cisco security agent.

Second solution is ipcop ([www.ipcop.org](www.ipcop.org)). If you have an old computer install this. Provides plenty and has plenty addons from firewalling, intrusion detection through snort, VPNs etc. 

Also google mhaddons and look at the main site and you will find addons for intrusion prevention (guardian) and rule modification, antivirus and improvements to things such as the web proxy etc. I have used it to protect my homenetwork of both Linux and Windows for a year now and i am very impressed. It is the equivalent to a sonicwall device.

Both are very good solutions to use for security in your network/host and increases visibility of security significantly.

---

### Post by pytheas22 on 2008-04-04
I started testing OSSEC a week ago for use as an IDS on a network of about 100 Windows workstations (plus a couple Linux machines to run the OSSEC server) that I help manage, and I agree that it's great.  We looked at some proprietary solutions (like Tripwire) but have decided that OSSEC is the most straight-forward option, and completely free to boot.  Combined with Snort, arpwatch and the Symantec logs, it makes monitoring the security status of the network and hosts very easy.

The only thing I don't like about OSSEC is that I don't understand how exactly it works, and I would like to before deploying it.  I know what it does--monitors logs and calculates checksums--but the thing that stumps me is how it knows when to recalculate checksums.  I don't notice any extra system resources being used after system files are modified, either on the OSSEC server or Windows agents, and yet it still consistently reports changes I make to files in the \system32 directory.  Can anyone tell me exactly how it knows that it should be recalculating these checksums?  I am thinking maybe it watches disk I/O to detect when a file has been modified, but otherwise, how would it know to check it (besides just recalculating checksums of everything in \system32, which I don't think it's doing because that would take a while and I'd notice it)?

---

### Post by kevross_33 on 2008-04-04
Yeah, and it is a young solution too and already is very impressive, I see it becoming an alternative to Cisco Security Agenet. Pretty much anything which can log  to syslog can be monitored which is great as well as the other features. I like how it can work attacks out just from log patterns. You should also try modsecurity though it is not supported by ubuntu anymore and you have to look online for a guide. Great for protecting apache servers and even an IIS or apache server farm if installed on a reverse proxy.

Syngress has recently written a whole book dedicated to ossec and i will definately be getting that soon so I can learn more about it. I was reading online  and at a defcon an ossec protected server was the only surviving defender. The guy had written a custom active response that whenever you attacked it, it poisoned your arp cache meaning you would end up not even being able to get to the MAC address of the machine and instead will be going somewhere else lol.

---

### Post by pytheas22 on 2008-04-07
I got a chance to take a quick look at the OSSEC book the other day while I was in another office; it's definitely very thorough and looks worth the price (about $50, I think).

In the meantime, I wanted to pose another question: are there any good guides online about configuring OSSEC for Windows agents?  Right now I'm getting a ton of alerts from the two Windows machines that are attached to my OSSEC server.  Most of the alerts are the result of changes to checksums in the Windows registry, parts of which get modified regularly for legitimate reasons.

I copied and pasted part of an ossec.conf that I found online to ignore several registry paths on Windows agents, and it's cut the false-positive alerts down considerably.  However this is not an ideal solution, obviously, as it would be better for me to know that OSSEC is really ignoring only registry keys that deserve to be ignored...so if there were a guide somewhere to configuring OSSEC for monitoring the Windows registry, or if someone were willing to post an ossec.conf that he thinks is well configured for Windows agents, I'd be grateful.

My other option is to manually sort through all of the OSSEC alerts from the Windows machines and figure out which registry keys to ignore, but this will take a really long time, since the Windows registry is so convoluted.  And the whole point of open source is not to waste time doing what others have already done, right?

```

~$ cat ossec.conf 
<ossec_config>
  <global>
    ...
  </global>

  <rules>
    <include>rules_config.xml</include>
    <include>pam_rules.xml</include>
    <include>sshd_rules.xml</include>
    <include>telnetd_rules.xml</include>
    <include>syslog_rules.xml</include>
    <include>arpwatch_rules.xml</include>
    <include>symantec-av_rules.xml</include>
    <include>symantec-ws_rules.xml</include>
    <include>pix_rules.xml</include>
    <include>named_rules.xml</include>
    <include>smbd_rules.xml</include>
    <include>vsftpd_rules.xml</include>
    <include>pure-ftpd_rules.xml</include>
    <include>proftpd_rules.xml</include>
    <include>ms_ftpd_rules.xml</include>
    <include>hordeimp_rules.xml</include>
    <include>vpopmail_rules.xml</include>
    <include>courier_rules.xml</include>
    <include>web_rules.xml</include>
    <include>apache_rules.xml</include>
    <include>mysql_rules.xml</include>
    <include>postgresql_rules.xml</include>
    <include>ids_rules.xml</include>
    <include>squid_rules.xml</include>
    <include>firewall_rules.xml</include>
    <include>cisco-ios_rules.xml</include>
    <include>netscreenfw_rules.xml</include>
    <include>sonicwall_rules.xml</include>
    <include>postfix_rules.xml</include>
    <include>sendmail_rules.xml</include>
    <include>imapd_rules.xml</include>
    <include>mailscanner_rules.xml</include>
    <include>ms-exchange_rules.xml</include>
    <include>racoon_rules.xml</include>
    <include>vpn_concentrator_rules.xml</include>
    <include>spamd_rules.xml</include>
    <include>msauth_rules.xml</include>
    <!-- <include>policy_rules.xml</include> -->
    <include>attack_rules.xml</include>
    <include>zeus_rules.xml</include>
    <include>ossec_rules.xml</include>
    <include>local_rules.xml</include>
  </rules>  

  <syscheck>
    <!-- Frequency in seconds that syscheck is executed - default to every 6 hours -->
    <frequency>900</frequency>
    
    <!-- Directories to check  (perform all possible verifications) -->
    <directories check_all="yes">/etc,/usr/bin,/usr/sbin</directories>
    <directories check_all="yes">/bin,/sbin</directories>

    <!-- Files/directories to ignore -->
    <ignore>/etc/mtab</ignore>
    <ignore>/etc/mnttab</ignore>
    <ignore>/etc/hosts.deny</ignore>
    <ignore>/etc/mail/statistics</ignore>
    <ignore>/etc/random-seed</ignore>
    <ignore>/etc/adjtime</ignore>
    <ignore>/etc/httpd/logs</ignore>
    <ignore>/etc/utmpx</ignore>
    <ignore>/etc/wtmpx</ignore>
    <ignore>/etc/cups/certs</ignore>
    <ignore>/etc/dumpdates</ignore>
    <ignore>/etc/svc/volatile</ignore>

    <!-- Windows files to ignore -->
    <ignore>C:\WINDOWS/System32/LogFiles</ignore>
    <ignore>C:\WINDOWS/Debug</ignore>
    <ignore>C:\WINDOWS/WindowsUpdate.log</ignore>
    <ignore>C:\WINDOWS/iis6.log</ignore>
    <ignore>C:\WINDOWS/system32/wbem/Logs</ignore>
    <ignore>C:\WINDOWS/system32/wbem/Repository</ignore>
    <ignore>C:\WINDOWS/Prefetch</ignore>
    <ignore>C:\WINDOWS/PCHEALTH/HELPCTR/DataColl</ignore>
    <ignore>C:\WINDOWS/SoftwareDistribution</ignore>
    <ignore>C:\WINDOWS/Temp</ignore>
    <ignore>C:\WINDOWS/system32/config</ignore>
    <ignore>C:\WINDOWS/system32/spool</ignore>
    <ignore>C:\WINDOWS/system32/CatRoot</ignore>

    <!--Windows registry keys to ignore ... copied and pasted from http://www.ossec.net/ossec-list/2007-March/msg00107.html...changed 4 April 2008-->

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Installer\UserData</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Group
Policy\State</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\WindowsUpdate</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Internet
Settings\Cache</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\RNG</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\PCHealth\PchSvc</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Dfrg</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\WBEM</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Rpc</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\DirectDraw</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Direct3D</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\COM3</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows
NT\CurrentVersion\ProfileList</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows
NT\CurrentVersion\Prefetcher</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Classes\Interface</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Classes\TypeLib</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Classes\MIME</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Classes\Software</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Software\Classes\CLSID</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Security\Policy\Secrets</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\Security\SAM\Domains\Account\Users</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\DeviceClasses</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Watchdog</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\MediaCategories</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Windows</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\hivelist</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ServiceCurrent</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Print</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session
Manager</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Eventlog</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\RemoteAccess\Performance</registry_ignore>

<registry_ignore>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W32Time\TimeProviders\NtpClient</registry_ignore>
<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\SMS</registry_ignore>
<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows
NT\CurrentVersion\Winlogon\GPExtensions</registry_ignore>
<registry_ignore>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Group
Policy</registry_ignore>

  </syscheck>

  <rootcheck>
    <rootkit_files>/var/ossec/etc/shared/rootkit_files.txt</rootkit_files>
    <rootkit_trojans>/var/ossec/etc/shared/rootkit_trojans.txt</rootkit_trojans>
  </rootcheck>

  <global>
    <white_list>127.0.0.1</white_list>
    <white_list>^localhost.localdomain$</white_list>
    <white_list>132.236.56.250</white_list>
    <white_list>128.253.180.2</white_list>
    <white_list>192.35.82.50</white_list>
  </global>

  <remote>
    <connection>syslog</connection>
  </remote>

  <remote>
    <connection>secure</connection>
  </remote>

  <alerts>
    <log_alert_level>1</log_alert_level>
    <email_alert_level>7</email_alert_level>
  </alerts>

  <command>
    <name>host-deny</name>
    <executable>host-deny.sh</executable>
    <expect>srcip</expect>
    <timeout_allowed>yes</timeout_allowed>
  </command>  

  <command>
    <name>firewall-drop</name>
    <executable>firewall-drop.sh</executable>
    <expect>srcip</expect>
    <timeout_allowed>yes</timeout_allowed>
  </command>  

  <command>
    <name>disable-account</name>
    <executable>disable-account.sh</executable>
    <expect>user</expect>
    <timeout_allowed>yes</timeout_allowed>
  </command>  

  <command>
    <name>route-null</name>
    <executable>route-null.sh</executable>
    <expect>srcip</expect>
    <timeout_allowed>yes</timeout_allowed>
  </command>


  <!-- Active Response Config -->
  <active-response>
    <!-- This response is going to execute the host-deny
       - command for every event that fires a rule with
       - level (severity) >= 6.
       - The IP is going to be blocked for  600 seconds.
      -->
    <command>host-deny</command>
    <location>local</location>
    <level>6</level>
    <timeout>600</timeout>
  </active-response>

  <active-response>
    <!-- Firewall Drop response. Block the IP for
       - 600 seconds on the firewall (iptables,
       - ipfilter, etc).
      -->
    <command>firewall-drop</command>
    <location>local</location>
    <level>6</level>
    <timeout>600</timeout>    
  </active-response>  

  <!-- Files to monitor (localfiles) -->

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/messages</location>
  </localfile>

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/auth.log</location>
  </localfile>

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/syslog</location>
  </localfile>

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/mail.info</location>
  </localfile>

  <localfile>
    <log_format>syslog</log_format>
    <location>/var/log/snort/alert</location>
  </localfile>
</ossec_config>
```

---

### Post by jba6511 on 2008-04-07
if you have newer hardware which ipcop may have difficult with since it is designed for older pc's, endian firewall is a good alternative. Has all of the features of ipcop and support for new hardware.

---

