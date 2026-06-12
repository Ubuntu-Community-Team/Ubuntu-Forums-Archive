---
title: "Convertion issues"
date: 2009-10-16
forum: Ubuntu Christian Edition
---

### Post by johnathanamber on 2009-10-16
Hey everyone!

> OK so I did the following as instructed byt the convertion.htm page:
wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg](http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg) -O- | sudo apt-key add - && wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc](http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc) -O- | sudo apt-key add - && sudo wget [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list) -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

And it doesn't finish...
```
OK
OK
--2009-10-16 11:59:37--  http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list
Resolving ubuntuce.com... 66.40.7.42
Connecting to ubuntuce.com|66.40.7.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 417 [text/plain]
Saving to: `/etc/apt/sources.list.d/ubuntuce.list'

100%[======================================>] 417         --.-K/s   in 0.001s  

2009-10-16 11:59:38 (674 KB/s) - `/etc/apt/sources.list.d/ubuntuce.list' saved [417/417]

Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/restricted Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty Release
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/restricted Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/restricted Packages
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1) jaunty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://ubuntuce.com jaunty_amd/ Release.gpg                                
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Get:1 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://ubuntuce.com jaunty_amd/ Translation-en_US                          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US              
Hit http://archive.canonical.com jaunty Release                                
Hit http://wine.budgetdedicated.com jaunty Release                             
Hit http://archive.canonical.com jaunty/partner Packages                       
Ign http://ubuntuce.com jaunty_amd/ Release                                    
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://ubuntuce.com jaunty_amd/ Packages                                   
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://us.archive.ubuntu.com jaunty/main Sources                           
Hit http://us.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://us.archive.ubuntu.com jaunty/universe Packages                      
Hit http://us.archive.ubuntu.com jaunty/universe Sources                       
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages                  
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages  
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources         
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources   
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages    
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources     
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages  
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources   
Ign http://ppa.launchpad.net jaunty/main Translation-en_US           
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Get:2 http://ppa.launchpad.net jaunty Release [52.9kB]
Ign http://ppa.launchpad.net jaunty Release                           
Hit http://security.ubuntu.com jaunty-security/main Packages          
Hit http://ppa.launchpad.net jaunty Release    
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://ppa.launchpad.net jaunty Release                         
Hit http://security.ubuntu.com jaunty-security/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages                   
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Fetched 308B in 2min 4s (2B/s)
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D86553DB9220067F
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Is this just a matter of removing the offending repositories from the Synaptic Package Manager?

God bless and thank you,
Johnathan

PS: I was amazed that this existed... which is awesome!

---

### Post by rippin on 2009-10-16
> **johnathanamber said:**
> Hey everyone!



And it doesn't finish...
```
OK
OK
--2009-10-16 11:59:37--  http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d

<snip>

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D86553DB9220067F
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)/dists/jaunty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
```Is this just a matter of removing the offending repositories from the Synaptic Package Manager?

God bless and thank you,
Johnathan

PS: I was amazed that this existed... which is awesome!

Try it again with CD in the drive, plus maybe the server was too busy at the time for the GPG key and it might get it. Or edit out the CD, do sudo apt-get update. Try again. The key from the link provided exists.

---

### Post by johnathanamber on 2009-10-16
@rippin,

Thank you for the advice... I did insert the CD and tried again...

Since that didn't work, I went ahead and downloaded the ISO... I'll just reinstall with the UFC CD...

See y'all in a bit!

God bless and thank you,
Johnathan

---

