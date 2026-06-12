---
title: "A libgtk-3-0 problem in Gnome3 Staging PPA"
date: 2013-02-02
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-02-02
The libgtk-3-0 package (in Gnome3 Staging PP) depends on libxkbcommon0 (0.2.0-0ubuntu1).
However, in RR repos we have now libxkbcommon0 (0.2.0-0ubuntu3), which cannot be installed due to the dependency problem.

So, Gnome3 Staging PPA GTK3 packages should be rebuilt against newer libxkbcommon0.

---

### Post by ricotz on 2013-02-02
A rebuild will be published shortly.

---

### Post by zika on 2013-02-02
Is this it? Marked red...
```
:~$ UPALL
[sudo] password for zika: 
Ign http://extras.ubuntu.com raring InRelease
Ign http://archive.canonical.com raring InRelease                             
Ign http://archive.ubuntu.com raring InRelease                                
Ign http://ppa.launchpad.net quantal InRelease                                
Hit http://extras.ubuntu.com raring Release.gpg                               
Hit http://archive.canonical.com raring Release.gpg                           
Ign http://archive.ubuntu.com raring-updates InRelease                        
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://extras.ubuntu.com raring Release                                   
Ign http://archive.ubuntu.com raring-security InRelease                       
Hit http://archive.canonical.com raring Release                               
Ign http://ppa.launchpad.net quantal InRelease                                
Ign http://archive.ubuntu.com raring-backports InRelease                      
Ign http://ppa.launchpad.net raring InRelease                                 
Ign http://ppa.launchpad.net raring InRelease                                 
Get:1 http://archive.ubuntu.com raring Release.gpg [933 B]                    
Hit http://packages.medibuntu.org raring InRelease                            
Hit http://archive.ubuntu.com raring-updates Release.gpg                      
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://extras.ubuntu.com raring/main amd64 Packages                       
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://archive.ubuntu.com raring-security Release.gpg                     
Hit http://archive.canonical.com raring/partner amd64 Packages                
Hit http://extras.ubuntu.com raring/main i386 Packages                        
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://archive.ubuntu.com raring-backports Release.gpg                    
Hit http://archive.canonical.com raring/partner i386 Packages                 
Hit http://packages.medibuntu.org raring/free amd64 Packages                  
Ign http://ppa.launchpad.net raring InRelease                                 
Get:2 http://archive.ubuntu.com raring Release [40.8 kB]                      
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://liquorix.net sid InRelease                                         
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://packages.medibuntu.org raring/non-free amd64 Packages              
Hit http://archive.ubuntu.com raring-updates Release                          
Get:3 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Hit http://archive.ubuntu.com raring-security Release                         
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://archive.ubuntu.com raring-backports Release                        
Hit http://packages.medibuntu.org raring/free i386 Packages                   
Hit http://ppa.launchpad.net quantal Release.gpg                              
Get:4 http://archive.ubuntu.com raring/main amd64 Packages [1,163 kB]         
Hit http://ppa.launchpad.net raring Release.gpg                               
Ign http://extras.ubuntu.com raring/main Translation-en_US                    
Get:5 http://ppa.launchpad.net raring Release.gpg [316 B]                     
Hit http://packages.medibuntu.org raring/non-free i386 Packages               
Hit http://liquorix.net sid/main amd64 Packages                               
Hit http://ppa.launchpad.net raring Release.gpg                               
Ign http://extras.ubuntu.com raring/main Translation-en                       
Ign http://archive.canonical.com raring/partner Translation-en_US             
Hit http://ppa.launchpad.net raring Release.gpg                               
Ign http://archive.canonical.com raring/partner Translation-en                
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://liquorix.net sid/future amd64 Packages                             
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://ppa.launchpad.net raring Release.gpg                               
Get:6 http://ppa.launchpad.net quantal Release [11.9 kB]                      
Get:7 http://archive.ubuntu.com raring/restricted amd64 Packages [10.2 kB]    
Hit http://liquorix.net sid/main i386 Packages                                
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net quantal Release                                  
Get:8 http://archive.ubuntu.com raring/universe amd64 Packages [5,380 kB]     
Hit http://ppa.launchpad.net raring Release                                   
Get:9 http://ppa.launchpad.net raring Release [9,752 B]                       
Hit http://liquorix.net sid/future i386 Packages                              
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Get:10 http://ppa.launchpad.net quantal/main amd64 Packages [2,140 B]         
Get:11 http://ppa.launchpad.net quantal/main i386 Packages [2,136 B]          
Hit http://ppa.launchpad.net raring/main amd64 Packages                       
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main amd64 Packages                      
Hit http://ppa.launchpad.net quantal/main i386 Packages                       
Hit http://ppa.launchpad.net raring/main Sources                              
Hit http://ppa.launchpad.net raring/main amd64 Packages                       
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Ign http://packages.medibuntu.org raring/free Translation-en_US               
Get:12 http://ppa.launchpad.net raring/main Sources [25.9 kB]                 
Ign http://packages.medibuntu.org raring/free Translation-en                  
Ign http://packages.medibuntu.org raring/non-free Translation-en_US           
Get:13 http://ppa.launchpad.net raring/main amd64 Packages [40.8 kB]          
Ign http://packages.medibuntu.org raring/non-free Translation-en              
Get:14 http://ppa.launchpad.net raring/main i386 Packages [40.8 kB]           
Hit http://ppa.launchpad.net raring/main amd64 Packages                       
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Hit http://ppa.launchpad.net raring/main Sources            
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main Sources            
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Ign http://liquorix.net sid/future Translation-en_US                          
Ign http://liquorix.net sid/future Translation-en                             
Get:15 http://archive.ubuntu.com raring/multiverse amd64 Packages [130 kB]    
Get:16 http://archive.ubuntu.com raring/main i386 Packages [1,162 kB]         
Ign http://liquorix.net sid/main Translation-en_US                            
Ign http://liquorix.net sid/main Translation-en                               
Ign http://ppa.launchpad.net quantal/main Translation-en_US                   
Ign http://ppa.launchpad.net quantal/main Translation-en                      
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                   
Ign http://ppa.launchpad.net quantal/main Translation-en                      
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Get:17 http://archive.ubuntu.com raring/restricted i386 Packages [10.1 kB]    
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Get:18 http://archive.ubuntu.com raring/universe i386 Packages [5,389 kB]     
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Get:19 http://archive.ubuntu.com raring/multiverse i386 Packages [132 kB]     
Hit http://archive.ubuntu.com raring/main Translation-en                      
Hit http://archive.ubuntu.com raring/multiverse Translation-en                
Hit http://archive.ubuntu.com raring/restricted Translation-en                
Get:20 http://archive.ubuntu.com raring/universe Translation-en [3,720 kB]    
Hit http://archive.ubuntu.com raring-updates/main amd64 Packages              
Hit http://archive.ubuntu.com raring-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com raring-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com raring-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com raring-updates/main i386 Packages               
Hit http://archive.ubuntu.com raring-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com raring-updates/universe i386 Packages           
Hit http://archive.ubuntu.com raring-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com raring-updates/main Translation-en              
Hit http://archive.ubuntu.com raring-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-updates/restricted Translation-en        
Hit http://archive.ubuntu.com raring-updates/universe Translation-en          
Hit http://archive.ubuntu.com raring-security/main amd64 Packages             
Hit http://archive.ubuntu.com raring-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com raring-security/universe amd64 Packages         
Hit http://archive.ubuntu.com raring-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com raring-security/main i386 Packages              
Hit http://archive.ubuntu.com raring-security/restricted i386 Packages        
Hit http://archive.ubuntu.com raring-security/universe i386 Packages          
Hit http://archive.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com raring-security/main Translation-en             
Hit http://archive.ubuntu.com raring-security/multiverse Translation-en       
Hit http://archive.ubuntu.com raring-security/restricted Translation-en       
Hit http://archive.ubuntu.com raring-security/universe Translation-en         
Hit http://archive.ubuntu.com raring-backports/main amd64 Packages            
Hit http://archive.ubuntu.com raring-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com raring-backports/universe amd64 Packages        
Hit http://archive.ubuntu.com raring-backports/multiverse amd64 Packages      
Hit http://archive.ubuntu.com raring-backports/main i386 Packages             
Hit http://archive.ubuntu.com raring-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com raring-backports/universe i386 Packages         
Hit http://archive.ubuntu.com raring-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com raring-backports/main Translation-en            
Hit http://archive.ubuntu.com raring-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com raring-backports/restricted Translation-en      
Hit http://archive.ubuntu.com raring-backports/universe Translation-en        
Ign http://archive.ubuntu.com raring/main Translation-en_US                   
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US             
Ign http://archive.ubuntu.com raring/restricted Translation-en_US             
Ign http://archive.ubuntu.com raring/universe Translation-en_US               
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US           
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US       
Ign http://archive.ubuntu.com raring-security/main Translation-en_US          
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US    
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US      
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US         
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US   
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US   
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US     
Fetched 17.3 MB in 20s (837 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  empathy empathy-common mcp-account-manager-uoa nautilus-sendto-empathy
The following packages will be upgraded:
  evince evince-common gir1.2-gtk-3.0 libevdocument3-4 libevview3-3
  libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common nautilus
10 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 12.2 MB of archives.
After this operation, 28.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtk-3-bin amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [71.9 kB]
Get:2 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgail-3-0 amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [74.3 kB]
Get:3 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtk-3-0 amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [2,014 kB]
Get:4 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtk-3-common all 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [2,762 kB]
Get:5 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main evince amd64 3.7.4-0ubuntu1~raring1 [660 kB]
Get:6 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libevdocument3-4 amd64 3.7.4-0ubuntu1~raring1 [683 kB]
Get:7 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libevview3-3 amd64 3.7.4-0ubuntu1~raring1 [598 kB]
Get:8 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main evince-common all 3.7.4-0ubuntu1~raring1 [2,136 kB]
Get:9 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gtk-3.0 amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [222 kB]
Get:10 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main nautilus amd64 1:3.7.4-0ubuntu1~raring1 [2,996 kB]
Fetched 12.2 MB in 9s (1,247 kB/s)                                            
(Reading database ... 313155 files and directories currently installed.)
Preparing to replace libgtk-3-bin 3.6.4-0ubuntu5 (using .../libgtk-3-bin_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
[COLOR=Red]Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'[/COLOR]
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0:amd64 3.6.4-0ubuntu5 (using .../libgail-3-0_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgail-3-0:amd64 ...
Preparing to replace libgtk-3-0:amd64 3.6.4-0ubuntu5 (using .../libgtk-3-0_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgtk-3-0:amd64 ...
Preparing to replace libgtk-3-common 3.6.4-0ubuntu5 (using .../libgtk-3-common_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace evince 3.6.1-1ubuntu2 (using .../evince_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement evince ...
Preparing to replace libevdocument3-4 3.6.1-1ubuntu2 (using .../libevdocument3-4_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libevdocument3-4 ...
Preparing to replace libevview3-3 3.6.1-1ubuntu2 (using .../libevview3-3_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libevview3-3 ...
Preparing to replace evince-common 3.6.1-1ubuntu2 (using .../evince-common_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement evince-common ...
Preparing to replace gir1.2-gtk-3.0 3.6.4-0ubuntu5 (using .../gir1.2-gtk-3.0_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace nautilus 1:3.7.2-0ubuntu1~13.04~ricotz0 (using .../nautilus_1%3a3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement nautilus ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for menu ...
Processing triggers for mime-support ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Setting up libgtk-3-common (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libgtk-3-0:amd64 (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libgtk-3-bin (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libgail-3-0:amd64 (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libevdocument3-4 (3.7.4-0ubuntu1~raring1) ...
Setting up libevview3-3 (3.7.4-0ubuntu1~raring1) ...
Setting up evince-common (3.7.4-0ubuntu1~raring1) ...
Setting up evince (3.7.4-0ubuntu1~raring1) ...
Setting up gir1.2-gtk-3.0 (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up nautilus (1:3.7.4-0ubuntu1~raring1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```It seems that I've lost (again) those nice menus when in awesome... ;) Never mind, gnome-tweak-tool will start working again some of these days... Or I'll get Appearance in gnome-control-center... Till then I'll have to go to dgong-editor to dig...

---

### Post by Harry33 on 2013-02-02
> **zika said:**
> Is this it? Marked red...
```
:~$ UPALL
[sudo] password for zika: 
Ign http://extras.ubuntu.com raring InRelease
Ign http://archive.canonical.com raring InRelease                             
Ign http://archive.ubuntu.com raring InRelease                                
Ign http://ppa.launchpad.net quantal InRelease                                
Hit http://extras.ubuntu.com raring Release.gpg                               
Hit http://archive.canonical.com raring Release.gpg                           
Ign http://archive.ubuntu.com raring-updates InRelease                        
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://extras.ubuntu.com raring Release                                   
Ign http://archive.ubuntu.com raring-security InRelease                       
Hit http://archive.canonical.com raring Release                               
Ign http://ppa.launchpad.net quantal InRelease                                
Ign http://archive.ubuntu.com raring-backports InRelease                      
Ign http://ppa.launchpad.net raring InRelease                                 
Ign http://ppa.launchpad.net raring InRelease                                 
Get:1 http://archive.ubuntu.com raring Release.gpg [933 B]                    
Hit http://packages.medibuntu.org raring InRelease                            
Hit http://archive.ubuntu.com raring-updates Release.gpg                      
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://extras.ubuntu.com raring/main amd64 Packages                       
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://archive.ubuntu.com raring-security Release.gpg                     
Hit http://archive.canonical.com raring/partner amd64 Packages                
Hit http://extras.ubuntu.com raring/main i386 Packages                        
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://archive.ubuntu.com raring-backports Release.gpg                    
Hit http://archive.canonical.com raring/partner i386 Packages                 
Hit http://packages.medibuntu.org raring/free amd64 Packages                  
Ign http://ppa.launchpad.net raring InRelease                                 
Get:2 http://archive.ubuntu.com raring Release [40.8 kB]                      
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://liquorix.net sid InRelease                                         
Ign http://ppa.launchpad.net raring InRelease                                 
Hit http://packages.medibuntu.org raring/non-free amd64 Packages              
Hit http://archive.ubuntu.com raring-updates Release                          
Get:3 http://ppa.launchpad.net quantal Release.gpg [316 B]                    
Hit http://archive.ubuntu.com raring-security Release                         
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://archive.ubuntu.com raring-backports Release                        
Hit http://packages.medibuntu.org raring/free i386 Packages                   
Hit http://ppa.launchpad.net quantal Release.gpg                              
Get:4 http://archive.ubuntu.com raring/main amd64 Packages [1,163 kB]         
Hit http://ppa.launchpad.net raring Release.gpg                               
Ign http://extras.ubuntu.com raring/main Translation-en_US                    
Get:5 http://ppa.launchpad.net raring Release.gpg [316 B]                     
Hit http://packages.medibuntu.org raring/non-free i386 Packages               
Hit http://liquorix.net sid/main amd64 Packages                               
Hit http://ppa.launchpad.net raring Release.gpg                               
Ign http://extras.ubuntu.com raring/main Translation-en                       
Ign http://archive.canonical.com raring/partner Translation-en_US             
Hit http://ppa.launchpad.net raring Release.gpg                               
Ign http://archive.canonical.com raring/partner Translation-en                
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://liquorix.net sid/future amd64 Packages                             
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://ppa.launchpad.net raring Release.gpg                               
Hit http://ppa.launchpad.net raring Release.gpg                               
Get:6 http://ppa.launchpad.net quantal Release [11.9 kB]                      
Get:7 http://archive.ubuntu.com raring/restricted amd64 Packages [10.2 kB]    
Hit http://liquorix.net sid/main i386 Packages                                
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net quantal Release                                  
Get:8 http://archive.ubuntu.com raring/universe amd64 Packages [5,380 kB]     
Hit http://ppa.launchpad.net raring Release                                   
Get:9 http://ppa.launchpad.net raring Release [9,752 B]                       
Hit http://liquorix.net sid/future i386 Packages                              
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Hit http://ppa.launchpad.net raring Release                                   
Get:10 http://ppa.launchpad.net quantal/main amd64 Packages [2,140 B]         
Get:11 http://ppa.launchpad.net quantal/main i386 Packages [2,136 B]          
Hit http://ppa.launchpad.net raring/main amd64 Packages                       
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main amd64 Packages                      
Hit http://ppa.launchpad.net quantal/main i386 Packages                       
Hit http://ppa.launchpad.net raring/main Sources                              
Hit http://ppa.launchpad.net raring/main amd64 Packages                       
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Ign http://packages.medibuntu.org raring/free Translation-en_US               
Get:12 http://ppa.launchpad.net raring/main Sources [25.9 kB]                 
Ign http://packages.medibuntu.org raring/free Translation-en                  
Ign http://packages.medibuntu.org raring/non-free Translation-en_US           
Get:13 http://ppa.launchpad.net raring/main amd64 Packages [40.8 kB]          
Ign http://packages.medibuntu.org raring/non-free Translation-en              
Get:14 http://ppa.launchpad.net raring/main i386 Packages [40.8 kB]           
Hit http://ppa.launchpad.net raring/main amd64 Packages                       
Hit http://ppa.launchpad.net raring/main i386 Packages                        
Hit http://ppa.launchpad.net raring/main Sources            
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main Sources            
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Hit http://ppa.launchpad.net raring/main amd64 Packages     
Hit http://ppa.launchpad.net raring/main i386 Packages      
Ign http://liquorix.net sid/future Translation-en_US                          
Ign http://liquorix.net sid/future Translation-en                             
Get:15 http://archive.ubuntu.com raring/multiverse amd64 Packages [130 kB]    
Get:16 http://archive.ubuntu.com raring/main i386 Packages [1,162 kB]         
Ign http://liquorix.net sid/main Translation-en_US                            
Ign http://liquorix.net sid/main Translation-en                               
Ign http://ppa.launchpad.net quantal/main Translation-en_US                   
Ign http://ppa.launchpad.net quantal/main Translation-en                      
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                   
Ign http://ppa.launchpad.net quantal/main Translation-en                      
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Get:17 http://archive.ubuntu.com raring/restricted i386 Packages [10.1 kB]    
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Get:18 http://archive.ubuntu.com raring/universe i386 Packages [5,389 kB]     
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                    
Ign http://ppa.launchpad.net raring/main Translation-en                       
Get:19 http://archive.ubuntu.com raring/multiverse i386 Packages [132 kB]     
Hit http://archive.ubuntu.com raring/main Translation-en                      
Hit http://archive.ubuntu.com raring/multiverse Translation-en                
Hit http://archive.ubuntu.com raring/restricted Translation-en                
Get:20 http://archive.ubuntu.com raring/universe Translation-en [3,720 kB]    
Hit http://archive.ubuntu.com raring-updates/main amd64 Packages              
Hit http://archive.ubuntu.com raring-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com raring-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com raring-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com raring-updates/main i386 Packages               
Hit http://archive.ubuntu.com raring-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com raring-updates/universe i386 Packages           
Hit http://archive.ubuntu.com raring-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com raring-updates/main Translation-en              
Hit http://archive.ubuntu.com raring-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-updates/restricted Translation-en        
Hit http://archive.ubuntu.com raring-updates/universe Translation-en          
Hit http://archive.ubuntu.com raring-security/main amd64 Packages             
Hit http://archive.ubuntu.com raring-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com raring-security/universe amd64 Packages         
Hit http://archive.ubuntu.com raring-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com raring-security/main i386 Packages              
Hit http://archive.ubuntu.com raring-security/restricted i386 Packages        
Hit http://archive.ubuntu.com raring-security/universe i386 Packages          
Hit http://archive.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com raring-security/main Translation-en             
Hit http://archive.ubuntu.com raring-security/multiverse Translation-en       
Hit http://archive.ubuntu.com raring-security/restricted Translation-en       
Hit http://archive.ubuntu.com raring-security/universe Translation-en         
Hit http://archive.ubuntu.com raring-backports/main amd64 Packages            
Hit http://archive.ubuntu.com raring-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com raring-backports/universe amd64 Packages        
Hit http://archive.ubuntu.com raring-backports/multiverse amd64 Packages      
Hit http://archive.ubuntu.com raring-backports/main i386 Packages             
Hit http://archive.ubuntu.com raring-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com raring-backports/universe i386 Packages         
Hit http://archive.ubuntu.com raring-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com raring-backports/main Translation-en            
Hit http://archive.ubuntu.com raring-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com raring-backports/restricted Translation-en      
Hit http://archive.ubuntu.com raring-backports/universe Translation-en        
Ign http://archive.ubuntu.com raring/main Translation-en_US                   
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US             
Ign http://archive.ubuntu.com raring/restricted Translation-en_US             
Ign http://archive.ubuntu.com raring/universe Translation-en_US               
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US           
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US       
Ign http://archive.ubuntu.com raring-security/main Translation-en_US          
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US    
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US      
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US         
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US   
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US   
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US     
Fetched 17.3 MB in 20s (837 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  empathy empathy-common mcp-account-manager-uoa nautilus-sendto-empathy
The following packages will be upgraded:
  evince evince-common gir1.2-gtk-3.0 libevdocument3-4 libevview3-3
  libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common nautilus
10 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 12.2 MB of archives.
After this operation, 28.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtk-3-bin amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [71.9 kB]
Get:2 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgail-3-0 amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [74.3 kB]
Get:3 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtk-3-0 amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [2,014 kB]
Get:4 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtk-3-common all 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [2,762 kB]
Get:5 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main evince amd64 3.7.4-0ubuntu1~raring1 [660 kB]
Get:6 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libevdocument3-4 amd64 3.7.4-0ubuntu1~raring1 [683 kB]
Get:7 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libevview3-3 amd64 3.7.4-0ubuntu1~raring1 [598 kB]
Get:8 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main evince-common all 3.7.4-0ubuntu1~raring1 [2,136 kB]
Get:9 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gtk-3.0 amd64 3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1 [222 kB]
Get:10 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main nautilus amd64 1:3.7.4-0ubuntu1~raring1 [2,996 kB]
Fetched 12.2 MB in 9s (1,247 kB/s)                                            
(Reading database ... 313155 files and directories currently installed.)
Preparing to replace libgtk-3-bin 3.6.4-0ubuntu5 (using .../libgtk-3-bin_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
[COLOR=Red]Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'[/COLOR]
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0:amd64 3.6.4-0ubuntu5 (using .../libgail-3-0_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgail-3-0:amd64 ...
Preparing to replace libgtk-3-0:amd64 3.6.4-0ubuntu5 (using .../libgtk-3-0_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgtk-3-0:amd64 ...
Preparing to replace libgtk-3-common 3.6.4-0ubuntu5 (using .../libgtk-3-common_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace evince 3.6.1-1ubuntu2 (using .../evince_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement evince ...
Preparing to replace libevdocument3-4 3.6.1-1ubuntu2 (using .../libevdocument3-4_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libevdocument3-4 ...
Preparing to replace libevview3-3 3.6.1-1ubuntu2 (using .../libevview3-3_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libevview3-3 ...
Preparing to replace evince-common 3.6.1-1ubuntu2 (using .../evince-common_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement evince-common ...
Preparing to replace gir1.2-gtk-3.0 3.6.4-0ubuntu5 (using .../gir1.2-gtk-3.0_3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace nautilus 1:3.7.2-0ubuntu1~13.04~ricotz0 (using .../nautilus_1%3a3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement nautilus ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for menu ...
Processing triggers for mime-support ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Setting up libgtk-3-common (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libgtk-3-0:amd64 (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libgtk-3-bin (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libgail-3-0:amd64 (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up libevdocument3-4 (3.7.4-0ubuntu1~raring1) ...
Setting up libevview3-3 (3.7.4-0ubuntu1~raring1) ...
Setting up evince-common (3.7.4-0ubuntu1~raring1) ...
Setting up evince (3.7.4-0ubuntu1~raring1) ...
Setting up gir1.2-gtk-3.0 (3.7.7+git20130127.r1.22bad6a2-0ubuntu1~raring1) ...
Setting up nautilus (1:3.7.4-0ubuntu1~raring1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```It seems that I've lost (again) those nice menus when in awesome... ;) Never mind, gnome-tweak-tool will start working again some of these days... Or I'll get Appearance in gnome-control-center... Till then I'll have to go to dgong-editor to dig...

Yes that is the one.
Now you got the right and working GTK3 installed.

---

### Post by Harry33 on 2013-02-02
> **ricotz said:**
> A rebuild will be published shortly.

Thank you, now all is well again with the GTK3.

The only issue left now is the missing F2 function. There is input microphone function instead. But that is an upstream issue and another story (gnome-settings-daemon).

---

### Post by ricotz on 2013-02-03
> **Harry33 said:**
> Thank you, now all is well again with the GTK3.

The only issue left now is the missing F2 function. There is input microphone function instead. But that is an upstream issue and another story (gnome-settings-daemon).

Should be fixed now in gnome3-team/gnome3-staging

---

### Post by Harry33 on 2013-02-03
> **ricotz said:**
> Should be fixed now in gnome3-team/gnome3-staging

Thanks again,
definitely fixed now.

---

