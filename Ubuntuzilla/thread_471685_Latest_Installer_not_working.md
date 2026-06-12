---
title: "Latest Installer not working"
date: 2007-06-12
forum: Ubuntuzilla
---

### Post by Rich_li_ny on 2007-06-12
I already had SeaMonkey 1.1.2 installed (Per Manual Install Instructions on this forum) but didnt have it listed under Applications > Internet.   It worked fine with a launched I created on desktop.

So to try out this script I did this: "bash /home/richie/installseamonkey.sh -remove"

Ok SeaMonkey was removed .. except for the desktop launcher. No biggie. 

I then did this to reinstall it hoping that it woudl be reinstalled and would have an icon in the application menu. "bash /home/richie/installseamonkey.sh -install"

this is what I got: 

"...The most recent release of SeaMonkey is detected to be 1.1.2. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/projects/seamonkey/](http://www.mozilla.org/projects/seamonkey/)) Is it correct [y/n]? "

So I selected Y ( I know that the latest version and the one I just uninstalled and am attempting to reinstall. 
The system runs through the following routine but nothing is ever installed.....:


Updating repositories list

Password:
Ign cdrom://Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_ZA
Ign cdrom://Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_ZA
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]           
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                     
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_ZA         
Get:5 [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release.gpg [189B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_ZA                   
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_ZA                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_ZA     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_ZA     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages       
Ign [http://www.claws-mail.org](http://www.claws-mail.org) ./ Translation-en_ZA                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_ZA        
Hit [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_ZA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_ZA   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_ZA             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Hit [http://www.claws-mail.org](http://www.claws-mail.org) ./ Packages                                   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [42.6kB]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_ZA           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [17.8kB]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_ZA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_ZA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_ZA     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_ZA         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_ZA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_ZA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_ZA   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_ZA    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_ZA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_ZA    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_ZA          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                   
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Sources [17.8kB]        
Fetched 78.3kB in 26s (2943B/s)                                             
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2)  MD5Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

OK .. So is this a bug or am I doing something wrong?

Rich

---

### Post by nanotube on 2007-06-12
> **Rich_li_ny said:**
> I already had SeaMonkey 1.1.2 installed (Per Manual Install Instructions on this forum) but didnt have it listed under Applications > Internet.   It worked fine with a launched I created on desktop.

So to try out this script I did this: "bash /home/richie/installseamonkey.sh -remove"

Ok SeaMonkey was removed .. except for the desktop launcher. No biggie. 

I then did this to reinstall it hoping that it woudl be reinstalled and would have an icon in the application menu. "bash /home/richie/installseamonkey.sh -install"

this is what I got: 

"...The most recent release of SeaMonkey is detected to be 1.1.2. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/projects/seamonkey/](http://www.mozilla.org/projects/seamonkey/)) Is it correct [y/n]? "

<snip>

OK .. So is this a bug or am I doing something wrong?

Rich

Hi 
yes, this is a bug indeed! 
the thing is, you are using an older release (i know this, because as of a few releases back, we are no longer a shell script, but a python script. :)
this bug has been fixed in the newer releases (the bug is that when apt-get update fails due to some repositories being down, the script exits, because it likes everything to complete successfully. however, it is not really necessary for this step).

so please go to our homepage ([http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)), read the instructions for usage (we use python rather than bash now) and get the newest released version (4.0.2), and it will let you bypass the incomplete apt-get update error and proceed.

please report back on how that worked. :)

edit: and by the way, i'm curious, where did you get that old seamonkey install script, and what made you think it was the 'latest' version?

---

