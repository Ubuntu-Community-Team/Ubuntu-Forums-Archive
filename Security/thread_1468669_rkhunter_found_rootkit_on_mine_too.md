---
title: "rkhunter found rootkit on mine too"
date: 2010-05-01
forum: Security
---

### Post by drreed on 2010-05-01
Solved with Google - Apparently this is a common false positive recently

```

dav@dav-desktop:~/Downloads/rkhunter-1.3.6$ sudo rkhunter -c
[ Rootkit Hunter version 1.3.6 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ Warning ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
   
.. omitted for brevity

 

    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
  
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/w.procps                                        [ OK ]
   
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /usr/sbin/adduser                                        [ Warning ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    
    /usr/local/bin/rkhunter                                  [ OK ]
    /usr/local/etc/rkhunter.conf                             [ OK ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
   
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ Warning ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]


System checks summary
=====================

File properties checks...
    Required commands check failed
    Files checked: 130
    Suspect files: 4

Rootkit checks...
    Rootkits checked : 242
    Possible rootkits: 1
    Rootkit names    : Xzibit Rootkit

Applications checks...
    Applications checked: 2
    Suspect applications: 2

The system checks took: 2 minutes and 4 seconds

All results have been written to the log file (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)


```So I guess I need to change all my passwords and re-install or something right?

lol - I wonder where I picked this up . . .

---

### Post by cariboo on 2010-05-02
This questions gets asked here on a regular basis, at least once a week, it's gets asked so often, that I would almost consider it to be a recurring discussion. Please before asking a question in this or any other sub-forum make sure it hasn't been asked and answered several times over.

---

