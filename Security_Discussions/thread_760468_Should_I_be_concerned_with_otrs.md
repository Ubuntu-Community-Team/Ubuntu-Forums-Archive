---
title: "Should I be concerned with otrs?"
date: 2008-04-20
forum: Security Discussions
---

### Post by shane2peru on 2008-04-20
Ok, I didn't install or setup OTRS to my knowledge.  However it shows up quite often in my logs.  I have a Ubuntu 7.10 LAMP server install.  Here is a logwatch part with otrs:
```

Commands Run:
    User otrs:
       [ -x $HOME/bin/otrs.cleanup ] && $HOME/bin/otrs.cleanup > /dev/null: 1 Time(s)
       test -x $HOME/bin/DeleteSessionIDs.pl && $HOME/bin/DeleteSessionIDs.pl --expired > /dev/null: 12 Time(s)
       test -x $HOME/bin/GenericAgent.pl && $HOME/bin/GenericAgent.pl -c db > /dev/null: 144 Time(s)
       test -x $HOME/bin/GenericAgent.pl && $HOME/bin/GenericAgent.pl > /dev/null: 72 Time(s)
       test -x $HOME/bin/PendingJobs.pl && $HOME/bin/PendingJobs.pl > /dev/null: 12 Time(s)
       test -x $HOME/bin/PostMasterPOP3.pl && $HOME/bin/PostMasterPOP3.pl > /dev/null: 144 Time(s)
       test -x $HOME/bin/RebuildTicketIndex.pl && $HOME/bin/RebuildTicketIndex.pl > /dev/null: 1 Time(s)
       test -x $HOME/bin/UnlockTickets.pl && $HOME/bin/UnlockTickets.pl --timeout > /dev/null: 24 Time(s)
```  That is a lot of access for something that I didn't install and is not running on my machine.  Here is the aptitude remove results: ```
sudo aptitude remove otrs2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done    
```

one more slocate:
```

 slocate otrs
/usr/share/otrs
/usr/share/otrs/Kernel
/usr/share/otrs/Kernel/Config
/usr/share/otrs/Kernel/Config/Files
/usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm
/var/mail/otrs
/var/lib/dpkg/info/otrs2.postrm
/var/lib/dpkg/info/otrs2.list
/var/lib/ucf/cache/:etc:otrs:maintainance.html
/var/lib/ucf/cache/:etc:otrs:cron
/var/lib/ucf/cache/:etc:otrs:Kernel:Config:GenericAgent.pm
/var/lib/ucf/cache/:etc:otrs:fetchmailrc
/var/lib/ucf/cache/:etc:apache2:conf.d:otrs2
/var/lib/ucf/cache/:etc:otrs:Kernel:Config.pm
/var/lib/otrs
/var/lib/otrs/log
/var/lib/otrs/log/TicketCounter.log
/var/lib/otrs/httpd
/var/lib/otrs/httpd/htdocs
/var/lib/otrs/tmp
/var/lib/otrs/tmp/SysConfig-Cache_Kernel_Config_Files_Ticket.xml-70c9f5dd45ac453d1609a300e8ee356f.pm
/var/lib/otrs/tmp/SysConfig-Cache_Kernel_Config_Files_Framework.xml-a9be39813932c27ec1032591414fe04a.pm
/var/cache/apt/archives/otrs2_2.1.7-2_all.deb

```

I also opened synaptics to make sure I didn't mess something up with aptitude and it still showed that otrs2 was not installed.  This is slightly disconcerting.  If anyone has any ideas I  would appreciate the help.  This is my first server install.  I have a firewall with only port 80 open to the www coming in (at least I think I do)  I have ssh blocked with denyhosts and set to paranoid with only internal LAN address allowed into it.  So I figure I'm pretty secure, however don't understand this otrs business.  Thanks.

Shane

---

### Post by shane2peru on 2008-04-21
ok, it is only 3 days before the Hardy release, and I do plan on upgrading so I'm not overly concerned by this situation.  However I would like a little feedback on this.  Even if it is just speculation, I would love to hear some thoughts about this.  It really boggles my mind, aptitude, synaptics says it isn't installed on my system, and yet it has cronjobs setup and running, and has directories.  :confused::confused::confused:

Shane

---

### Post by cbobb@alinean.com on 2008-04-21
It appears that OTRS was however installed at one time and is still executing quite a few of its scripts that are intricate to its operation.  I use OTRS, for my inhouse change control / ticketsystem.  Check the cronjobs and see where they are executing from, as the perl scripts still appear to be either running or trying to run.  check /opt/otrs for that is its default install directory from source . .as it might have been installed outside of apt and there for would not show up on an apt remove.  

cb

---

### Post by shane2peru on 2008-04-21
> **cbobb@alinean.com said:**
> It appears that OTRS was however installed at one time and is still executing quite a few of its scripts that are intricate to its operation.  I use OTRS, for my inhouse change control / ticketsystem.  Check the cronjobs and see where they are executing from, as the perl scripts still appear to be either running or trying to run.  check /opt/otrs for that is its default install directory from source . .as it might have been installed outside of apt and there for would not show up on an apt remove.  

cb

Ahh, now that you say that, I know I didn't install it outside of apt, however I did download and tried a few applications, sugarcrm, and vtiger, is it possible that one of them automagically installed that program outside of apt?  Or perhaps webmin installed it for me?  That would make more sense if something like that installed it, because I certainly didn't, and was quite concerned that it shows up on my system, and in my logs. :D  The odd thing is that it doesn't show up in the ```
crontab -l 
```  or ```
sudo crontab -l
```  That is what is odd.  Apparently something set it to run elsewhere.  That is also what boggles my mind.  Thanks for the thoughts.

Shane

---

