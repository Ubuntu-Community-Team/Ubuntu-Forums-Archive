---
title: "system keeps attempting a partial upgrade, can't install software or upgrade"
date: 2014-10-23
forum: Ubuntu/Debian BASED
---

### Post by lucy3 on 2014-10-23
Hi, I've actually just installed LXLE, but that wasn't in the prefix list. I was installing dropbox and calibre via the software centre when it just suddenly hung there. Restarted the PC, same thing. Tried to update and software said it wanted to do a partial upgrade where it preceded to download dropbox, gets to 100% and hangs at clean up. I have the same errors as this post [http://ubuntuforums.org/showthread.php?t=1858466](http://ubuntuforums.org/showthread.php?t=1858466) but when it talks about entering keys and what the user did to fix it I'm lost. I've just switched from windows. Please take pity and post a step by step. Thanks.

---

### Post by ibjsb4 on 2014-10-23
> Hi, I've actually just installed LXLE, but that wasn't in the prefix list.
Thats because LXLE is not an official ubuntu flavor,  its built on ubuntu.  Should of posted here:
[http://ubuntuforums.org/forumdisplay.php?f=452](http://ubuntuforums.org/forumdisplay.php?f=452)

What version did you install (12.04 or 14.04)?

You say that your getting the same errors as in another old post is not the way to go.  Please post the errors you are getting.  Use code tags if necessary.
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
This way you can get an exact fix to your exact problem.
> Please take pity and post a step by step.
Ok, welcome to the forums :)

---

### Post by lucy3 on 2014-10-24
Hi ibjsb4,

Thanks for replying.

```

What version did you install (12.04 or 14.04)?
```

12.04

Error after trying to run software manager to install dropbox then opening update manager after installation didn't start after root password was entered. 

```
It is impossible to install or remove any software right now. Please use   the package manager "Synaptic" or run "sudo apt-get install -f" in a   terminal to fix this issue first.
```

When I run the above command in a terminal I get ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by ibjsb4 on 2014-10-24
> Unable to lock the administration directory (/var/lib/dpkg/), [COLOR=#ff0000]is another process using it?[/COLOR]
This usually means that you have another package manager open.  Maybe the software center, maybe update manager.  Dpkg can run only one instance in one program so close the others and then run the install -f command.  If you still get the error you can manually unlock dpkg.
```
sudo rm /var/lib/dpkg/lock
```
Lxle is suppose to offer long term support for 12.04, lubuntu 12.04 has already reached end of life.  I do not run lxle and I wonder just how good a job it does with outdated packages.  Please run this command:
```
ubuntu-support-status --show-unsupported
```
No need to post the output, just want to know if it spits out a long list of unsupported packages.

Do post back any errors you get when running the install -f command.

---

### Post by lucy3 on 2014-10-24
```
close the others
```

How do I do this? Already tried through task manager and rebooting the system.

Thanks.

---

### Post by ibjsb4 on 2014-10-24
A reboot should of shut everything down.  Go ahead and try:
```
sudo rm /var/lib/dpkg/lock
```
Followed with:
```
sudo apt-get install -f
```

Edit
I'll check back in after breakfast, maybe someone else will offer to help till then.

---

### Post by lucy3 on 2014-10-24
just rebooted and tried the install-f command and I get```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
``` Ran it and it installs dropbox 100% but then just hangs. Do I remove the lock as above?  I read somewhere that doing so is a last resort.

---

### Post by ibjsb4 on 2014-10-24
Lets back up a bit.
```
sudo apt-get update
```
And post any errors.
If no errors appear:
```
sudo apt-get upgrade
```

[COLOR=#ff0000]Edit[/COLOR]
> Do I remove the lock as above? I read somewhere that doing so is a last resort.
Yes, it should be used as a last resort, but doing so will not kill cats or dogs :)
I am guessing that your looking at the big picture and feel a bit overwhelmed.  Take it one step at a time.  Just reply to this post.

---

### Post by lucy3 on 2014-10-24
To my knowledge no PC or MAC has ever actually killed anyone :lolflag: Not worried I just find research and asking the best way to learn.

same error ```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

Ran ```
sudo dpkg --configure -a
``` same as before downloads 100% but then cursor just flashes in terminal. I can type but no commands register, computer name isn't in command line after running the above.

---

### Post by ian-weisser on 2014-10-24
What output does --configure have before 'downloads 100%'?
What's downloading during the --configure?

---

### Post by lucy3 on 2014-10-24
```
What output does --configure have before 'downloads 100%'?
```

How do I find this out?

```
What's downloading during the --configure? 
```

Dropbox. I was installing calibre and dropbox through the lubuntu software centre and it just suddenly froze when it got to configuring dropbox. No idea why.

---

### Post by ibjsb4 on 2014-10-24
Hay ian-weisser :)

---

### Post by bapoumba on 2014-10-24
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by ibjsb4 on 2014-10-24
> **bapoumba said:**
> *Thread moved to **Ubuntu/Debian BASED**.*
Took ya long enough :p
Got any ideas?

---

### Post by lucy3 on 2014-10-24
```
Took ya long enough :razz:
```

mean't to look into moving it, sorry.

---

### Post by bapoumba on 2014-10-24
> **lucy3 said:**
> ```
Took ya long enough :razz:
```

mean't to look into moving it, sorry.

FYI, you cannot move a thread, Staff has to do it for you. Use the report button to ask for a moving. Just happened to read here :)

---

### Post by lucy3 on 2014-10-24
Really need my files. Is it time to remove the lock or do a fresh install? No clue as to why the software updater froze though is the only thing. :(

---

### Post by lucy3 on 2014-10-24
```
FYI, you cannot move a thread, Staff has to do it for you. Use the  report button to ask for a moving. Just happened to read here :smile:
```

Good to know

---

### Post by bapoumba on 2014-10-24
In the mean time, if you really need files on dropbox, you could use dropbox website in a browser.

Please post the full outputs to 
```
sudo apt-get update
sudo apt-get upgrade
```
All of it.

---

### Post by lucy3 on 2014-10-24
```
 sudo apt-get update
```

```
lucy@lucy-N150P:~$ sudo apt-get update
[sudo] password for lucy: 
Hit http://archive.canonical.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://archive.canonical.com precise Release                          
Hit http://extras.ubuntu.com precise Release                              
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://archive.ubuntu.com precise Release.gpg                         
Get:3 http://archive.ubuntu.com precise-updates Release.gpg [198 B]       
Hit http://archive.ubuntu.com precise-backports Release.gpg               
Get:4 http://archive.ubuntu.com precise-security Release.gpg [198 B]      
Get:5 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]      
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://archive.canonical.com precise/partner i386 Packages            
Hit http://archive.ubuntu.com precise Release                             
Get:6 http://archive.ubuntu.com precise-updates Release [98.7 kB]         
Hit http://ppa.launchpad.net precise Release                              
Get:7 http://ppa.launchpad.net precise Release [12.4 kB]                  
Get:8 http://ppa.launchpad.net precise Release [12.4 kB]                  
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://archive.getdeb.net precise-getdeb Release.gpg                  
Hit http://repo.steampowered.com precise Release.gpg                      
Hit http://archive.canonical.com precise/partner TranslationIndex         
Hit http://extras.ubuntu.com precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise Release                              
Hit http://repo.steampowered.com precise Release                          
Hit http://archive.canonical.com precise/partner Translation-en           
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Translation-en                  
Hit http://archive.getdeb.net precise-getdeb Release                      
Ign http://extras.ubuntu.com precise/main Translation-en_GB               
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Hit http://archive.ubuntu.com precise-backports Release                   
Get:9 http://archive.ubuntu.com precise-security Release [50.7 kB]        
Ign http://extras.ubuntu.com precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Get:10 http://archive.ubuntu.com precise-proposed Release [98.7 kB]       
Hit http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Hit http://ppa.launchpad.net precise/main Translation-en             
Ign http://ppa.launchpad.net precise/main Translation-en             
Hit http://ppa.launchpad.net precise/main Sources                    
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_GB          
Ign http://ppa.launchpad.net precise/main Translation-en            
Hit http://archive.ubuntu.com precise/main Sources                     
Hit http://ppa.launchpad.net precise/main i386 Packages                
Hit http://ppa.launchpad.net precise/main TranslationIndex             
Hit http://ppa.launchpad.net precise/main Translation-en                  
Get:11 http://ppa.launchpad.net precise/main i386 Packages [9,418 B]      
Hit http://archive.ubuntu.com precise/restricted Sources                  
Hit http://archive.ubuntu.com precise/universe Sources                 
Hit http://archive.ubuntu.com precise/multiverse Sources               
Hit http://archive.ubuntu.com precise/main i386 Packages               
Hit http://archive.ubuntu.com precise/restricted i386 Packages         
Get:12 http://ppa.launchpad.net precise/main TranslationIndex [72 B]   
Hit http://archive.ubuntu.com precise/universe i386 Packages              
Hit http://archive.ubuntu.com precise/multiverse i386 Packages            
Hit http://archive.ubuntu.com precise/main TranslationIndex               
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex         
Hit http://archive.ubuntu.com precise/restricted TranslationIndex         
Get:13 http://ppa.launchpad.net precise/main i386 Packages [21.5 kB]      
Get:14 http://ppa.launchpad.net precise/main TranslationIndex [72 B]      
Get:15 http://ppa.launchpad.net precise/main Translation-en [4,331 B]     
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Hit http://archive.ubuntu.com precise/universe TranslationIndex           
Ign http://ppa.launchpad.net precise/main Translation-en                  
Get:16 http://ppa.launchpad.net precise/main Translation-en [6,316 B]     
Hit http://ppa.launchpad.net precise/main Sources                         
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://archive.ubuntu.com precise/main Translation-en_GB              
Hit http://archive.ubuntu.com precise/main Translation-en                 
Hit http://archive.ubuntu.com precise/multiverse Translation-en_GB        
Hit http://archive.ubuntu.com precise/multiverse Translation-en           
Hit http://ppa.launchpad.net precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://archive.ubuntu.com precise/restricted Translation-en_GB        
Hit http://archive.ubuntu.com precise/restricted Translation-en           
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Translation-en                  
Hit http://archive.ubuntu.com precise/universe Translation-en_GB          
Hit http://archive.ubuntu.com precise/universe Translation-en             
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Hit http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en                  
Hit http://ppa.launchpad.net precise/main i386 Packages              
Hit http://ppa.launchpad.net precise/main TranslationIndex           
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Get:17 http://archive.ubuntu.com precise-updates/main Sources [479 kB]    
Ign http://ppa.launchpad.net precise/main Translation-en_GB               
Hit http://archive.getdeb.net precise-getdeb/apps i386 Packages           
Ign http://ppa.launchpad.net precise/main Translation-en                  
Hit http://repo.steampowered.com precise/steam amd64 Packages             
Hit http://archive.getdeb.net precise-getdeb/games i386 Packages          
Hit http://repo.steampowered.com precise/steam i386 Packages              
Ign http://archive.getdeb.net precise-getdeb/apps TranslationIndex        
Ign http://archive.getdeb.net precise-getdeb/games TranslationIndex       
Ign http://repo.steampowered.com precise/steam TranslationIndex           
Get:18 http://archive.ubuntu.com precise-updates/restricted Sources [8,016 B]
Get:19 http://archive.ubuntu.com precise-updates/universe Sources [110 kB]
Get:20 http://archive.ubuntu.com precise-updates/multiverse Sources [8,889 B]
Get:21 http://archive.ubuntu.com precise-updates/main i386 Packages [874 kB]
Get:22 http://archive.ubuntu.com precise-updates/restricted i386 Packages [13.2 kB]
Get:23 http://archive.ubuntu.com precise-updates/universe i386 Packages [256 kB]
Get:24 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex       
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex 
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex 
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex   
Hit http://archive.ubuntu.com precise-backports/main Sources              
Hit http://archive.ubuntu.com precise-backports/restricted Sources        
Hit http://archive.ubuntu.com precise-backports/universe Sources          
Hit http://archive.ubuntu.com precise-backports/multiverse Sources        
Hit http://archive.ubuntu.com precise-backports/main i386 Packages        
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages  
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages    
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages  
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex     
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex 
Get:25 http://archive.ubuntu.com precise-security/main Sources [112 kB]   
Get:26 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:27 http://archive.ubuntu.com precise-security/universe Sources [33.0 kB]
Get:28 http://archive.ubuntu.com precise-security/multiverse Sources [1,780 B]
Get:29 http://archive.ubuntu.com precise-security/main i386 Packages [464 kB]
Ign http://repo.steampowered.com precise/steam Translation-en_GB          
Ign http://archive.getdeb.net precise-getdeb/apps Translation-en_GB       
Ign http://repo.steampowered.com precise/steam Translation-en             
Get:30 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:31 http://archive.ubuntu.com precise-security/universe i386 Packages [106 kB]
Ign http://archive.getdeb.net precise-getdeb/apps Translation-en          
Ign http://archive.getdeb.net precise-getdeb/games Translation-en_GB      
Get:32 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,645 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex      
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex
Ign http://archive.getdeb.net precise-getdeb/games Translation-en   
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex  
Get:33 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [4,249 B]
Get:34 http://archive.ubuntu.com precise-proposed/main i386 Packages [188 kB]
Get:35 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]
Get:36 http://archive.ubuntu.com precise-proposed/universe i386 Packages [19.4 kB]
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex      
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex  
Hit http://archive.ubuntu.com precise-updates/main Translation-en_GB      
Hit http://archive.ubuntu.com precise-updates/main Translation-en         
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en   
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en 
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-security/main Translation-en  
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise-proposed/main Translation-en_GB
Hit http://archive.ubuntu.com precise-proposed/main Translation-en  
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en_GB
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en_GB
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en_GB
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en
Fetched 3,018 kB in 1min 5s (46.1 kB/s)                                   
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
lucy@lucy-N150P:~$ 

```

```
 sudo apt-get upgrade
```

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

```
sudo dpkg --configure -a'
```

I get ```
> 
``` with a flashing cursor and nothing else happens.

---

### Post by deadflowr on 2014-10-24
The ' symbol is leaving the command unfinished.
Try it without the ' at the end.
(ctrl +C to get back to a prompt)

Edit:
```
sudo dpkg --configure -a
```

Also, try using the quote tag bubble when quoting, instead of the code tags#.

---

### Post by bapoumba on 2014-10-24
Hmm..

Just for my information, please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by lucy3 on 2014-10-24
> The ' symbol is leaving the command unfinished.
Try it without the ' at the end.

```
[lucy@lucy-N150P:~$ sudo dpkg --configure -a
[sudo] password for lucy: 
Setting up nautilus-dropbox (0.7.1-2) ...

Downloading Dropbox... 100% o share and store your files online. Want to learn more? Head to http://www.dropbox.com/
``` it just sits there.

> Just for my information, please post the outputs to :
 	Code:
 	cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*

```
lucy@lucy-N150P:~$ cat -n /etc/apt/sources.list
     1	
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	deb http://archive.ubuntu.com/ubuntu precise main restricted
     5	deb-src http://archive.ubuntu.com/ubuntu precise main restricted
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
    10	deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
    11	
    12	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13	## team. Also, please note that software in universe WILL NOT receive any
    14	## review or updates from the Ubuntu security team.
    15	deb http://archive.ubuntu.com/ubuntu precise universe
    16	deb-src http://archive.ubuntu.com/ubuntu precise universe
    17	deb http://archive.ubuntu.com/ubuntu precise-updates universe
    18	deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb http://archive.ubuntu.com/ubuntu precise multiverse
    26	deb-src http://archive.ubuntu.com/ubuntu precise multiverse
    27	deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
    28	deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
    29	
    30	## N.B. software from this repository may not have been tested as
    31	## extensively as that contained in the main release, although it includes
    32	## newer versions of some applications which may provide useful features.
    33	## Also, please note that software in backports WILL NOT receive any review
    34	## or updates from the Ubuntu security team.
    35	deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    36	deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    37	
    38	deb http://archive.ubuntu.com/ubuntu precise-security main restricted
    39	deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
    40	deb http://archive.ubuntu.com/ubuntu precise-security universe
    41	deb-src http://archive.ubuntu.com/ubuntu precise-security universe
    42	deb http://archive.ubuntu.com/ubuntu precise-security multiverse
    43	deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse
    44	
    45	## Uncomment the following two lines to add software from Canonical's
    46	## 'partner' repository.
    47	## This software is not part of Ubuntu, but is offered by Canonical and the
    48	## respective vendors as a service to Ubuntu users.
    49	deb http://archive.canonical.com/ubuntu precise partner
    50	# deb-src http://archive.canonical.com/ubuntu precise partner
    51	
    52	## This software is not part of Ubuntu, but is offered by third-party
    53	## developers who want to ship their latest software.
    54	deb http://extras.ubuntu.com/ubuntu precise main
    55	# deb-src http://extras.ubuntu.com/ubuntu precise main
    56	deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
lucy@lucy-N150P:~$ ls -la /etc/apt/sources.list.d
total 292
drwxr-xr-x 2 root root 4096 Oct 17 17:06 .
drwxr-xr-x 6 root root 4096 Oct 23 21:50 ..
-rw-r--r-- 1 root root  144 Oct 17 17:06 anonbeat-guayadeque-precise.list
-rw-r--r-- 1 root root  144 Oct 17 17:06 anonbeat-guayadeque-precise.list.save
-rw-r--r-- 1 root root  164 Oct 17 17:06 catfish-search-catfish-stable-precise.list
-rw-r--r-- 1 root root  164 Oct 17 17:06 catfish-search-catfish-stable-precise.list.save
-rw-r--r-- 1 root root  134 Oct 17 17:06 claws-mail-ppa-precise.list
-rw-r--r-- 1 root root  134 Oct 17 17:06 claws-mail-ppa-precise.list.save
-rw-r--r-- 1 root root   75 Oct 29  2012 cooperjona-stormcloud-precise.list.save
-rw-r--r-- 1 root root    0 Mar 23  2013 deluge-team-ppa-precise.list
-rw-r--r-- 1 root root   69 Mar 23  2013 deluge-team-ppa-precise.list.save
-rw-r--r-- 1 root root    0 Jun  1 09:35 ehoover-compholio-precise.list
-rw-r--r-- 1 root root   73 Jun  1 09:35 ehoover-compholio-precise.list.save
-rw-r--r-- 1 root root   57 Oct 17 17:06 getdeb.list
-rw-r--r-- 1 root root   57 Oct 17 17:06 getdeb.list.save
-rw-r--r-- 1 root root  136 Oct 17 17:06 h-realh-roxterm-precise.list
-rw-r--r-- 1 root root  136 Oct 17 17:06 h-realh-roxterm-precise.list.save
-rw-r--r-- 1 root root  156 Oct 17 17:06 kevin-mehall-pithos-daily-precise.list
-rw-r--r-- 1 root root  156 Oct 17 17:06 kevin-mehall-pithos-daily-precise.list.save
-rw-r--r-- 1 root root  148 Oct 17 17:06 kubuntu-ppa-backports-precise.list
-rw-r--r-- 1 root root  148 Oct 17 17:06 kubuntu-ppa-backports-precise.list.save
-rw-r--r-- 1 root root  144 Oct 17 17:06 landronimirc-clamtk-precise.list
-rw-r--r-- 1 root root  144 Oct 17 17:06 landronimirc-clamtk-precise.list.save
-rw-r--r-- 1 root root    0 Aug 19  2013 landronimirc-skippy-xd-daily-precise.list
-rw-r--r-- 1 root root   82 Aug 19  2013 landronimirc-skippy-xd-daily-precise.list.save
-rw-r--r-- 1 root root  136 Oct 17 17:06 libreoffice-ppa-precise.list
-rw-r--r-- 1 root root  136 Oct 17 17:06 libreoffice-ppa-precise.list.save
-rw-r--r-- 1 root root  138 Oct 17 17:06 linphone-release-precise.list
-rw-r--r-- 1 root root  138 Oct 17 17:06 linphone-release-precise.list.save
-rw-r--r-- 1 root root  132 Oct 17 17:06 linrunner-tlp-precise.list
-rw-r--r-- 1 root root  132 Oct 17 17:06 linrunner-tlp-precise.list.save
-rw-r--r-- 1 root root    0 Nov 15  2013 lubuntu-desktop-ppa-precise.list
-rw-r--r-- 1 root root   75 Nov 15  2013 lubuntu-desktop-ppa-precise.list.save
-rw-r--r-- 1 root root  154 May 28 08:21 lubuntu-dev-lubuntu-daily-precise.list.save
-rw-r--r-- 1 root root    0 May 23  2013 lubuntu-dev-non-official-apps-precise.list
-rw-r--r-- 1 root root   85 May 23  2013 lubuntu-dev-non-official-apps-precise.list.save
-rw-r--r-- 1 root root  142 May 28 08:21 lubuntu-dev-staging-precise.list.save
-rw-r--r-- 1 root root  128 Oct 17 17:06 lxle-stable-precise.list
-rw-r--r-- 1 root root  128 Oct 17 17:06 lxle-stable-precise.list.save
-rw-r--r-- 1 root root    0 Nov 22  2013 lxle-updates-precise.list
-rw-r--r-- 1 root root   68 Nov 22  2013 lxle-updates-precise.list.save
-rw-r--r-- 1 root root   66 Oct 17 17:06 medibuntu.list
-rw-r--r-- 1 root root   66 Oct 17 17:06 medibuntu.list.save
-rw-r--r-- 1 root root  134 Oct 17 17:06 nemh-systemback-precise.list
-rw-r--r-- 1 root root  134 Oct 17 17:06 nemh-systemback-precise.list.save
-rw-r--r-- 1 root root  146 Oct 17 17:06 nilarimogard-webupd8-precise.list
-rw-r--r-- 1 root root  146 Oct 17 17:06 nilarimogard-webupd8-precise.list.save
-rw-r--r-- 1 root root    0 Nov 15  2013 noobslab-deepin-sc-precise.list
-rw-r--r-- 1 root root   74 Nov 15  2013 noobslab-deepin-sc-precise.list.save
-rw-r--r-- 1 root root  134 Oct 17 17:06 noobslab-icons-precise.list
-rw-r--r-- 1 root root  134 Oct 17 17:06 noobslab-icons-precise.list.save
-rw-r--r-- 1 root root  136 Oct 17 17:06 noobslab-themes-precise.list
-rw-r--r-- 1 root root  136 Oct 17 17:06 noobslab-themes-precise.list.save
-rw-r--r-- 1 root root  134 Oct 17 17:06 nowrep-qupzilla-precise.list
-rw-r--r-- 1 root root  152 Oct 17 17:06 openshot_developers-ppa-precise.list
-rw-r--r-- 1 root root  152 Oct 17 17:06 openshot_developers-ppa-precise.list.save
-rw-r--r-- 1 root root  152 Oct 17 17:06 otto-kesselgulasch-gimp-precise.list
-rw-r--r-- 1 root root  152 Oct 17 17:06 otto-kesselgulasch-gimp-precise.list.save
-rw-r--r-- 1 root root   58 Oct 17 17:06 playdeb.list
-rw-r--r-- 1 root root   58 Oct 17 17:06 playdeb.list.save
-rw-r--r-- 1 root root  140 May 27 08:46 richardgv-compton-precise.list.save
-rw-r--r-- 1 root root   72 Aug 24  2012 shimmerproject-ppa-precise.list.save
-rw-r--r-- 1 root root    0 Jan  7  2013 shnatsel-zram-precise.list
-rw-r--r-- 1 root root   67 Jan  7  2013 shnatsel-zram-precise.list.save
-rw-r--r-- 1 root root  150 Oct 17 17:06 steam.list
-rw-r--r-- 1 root root  114 May 27 09:02 steam.list.dpkg-old
-rw-r--r-- 1 root root  150 Oct 17 17:06 steam.list.save
-rw-r--r-- 1 root root  136 Oct 17 17:06 tuxpoldo-btsync-precise.list
-rw-r--r-- 1 root root  136 Oct 17 17:06 tuxpoldo-btsync-precise.list.save
-rw-r--r-- 1 root root   69 Oct 29  2012 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root    0 Jun  1 09:34 upubuntu-com-chat-precise.list
-rw-r--r-- 1 root root   73 Jun  1 09:34 upubuntu-com-chat-precise.list.save
-rw-r--r-- 1 root root    0 Jun  1 09:37 videolan-master-daily-precise.list
-rw-r--r-- 1 root root   77 Jun  1 09:37 videolan-master-daily-precise.list.save
-rw-r--r-- 1 root root  148 Oct 17 17:06 videolan-stable-daily-precise.list
-rw-r--r-- 1 root root  148 Oct 17 17:06 videolan-stable-daily-precise.list.save
-rw-r--r-- 1 root root  156 Oct 17 17:06 vokoscreen-dev-vokoscreen-precise.list
-rw-r--r-- 1 root root  156 Oct 17 17:06 vokoscreen-dev-vokoscreen-precise.list.save
-rw-r--r-- 1 root root  156 Oct 17 17:06 webupd8team-y-ppa-manager-precise.list
-rw-r--r-- 1 root root  156 Oct 17 17:06 webupd8team-y-ppa-manager-precise.list.save
-rw-r--r-- 1 root root    0 Sep 25 03:54 yannubuntu-boot-repair-precise.list
-rw-r--r-- 1 root root   76 Sep 25 03:54 yannubuntu-boot-repair-precise.list.save
-rw-r--r-- 1 root root  138 Oct 17 17:06 ytvwld-syncthing-precise.list
-rw-r--r-- 1 root root  138 Oct 17 17:06 ytvwld-syncthing-precise.list.save
lucy@lucy-N150P:~$ tail -v -n +1 /etc/apt/sources.list.d/*

```

Does this mean that updates are not forthcoming? Website says this version has been revisited so includes version 14.04 important upgrades. They do have a 14.04 version but only for 64 bit hence the revisited attached to this version.

---

### Post by bapoumba on 2014-10-24
That is quite a bit of other repos you have here..
Please post the output to the last command :
```
tail -v -n +1 /etc/apt/sources.list.d/*
```

Now for dropbox, you may want to purge it and try to install it again :
```
sudo apt-get purge nautilus-dropbox
sudo apt-get install nautilus-dropbox
```

---

### Post by lucy3 on 2014-10-24
> That is quite a bit of other repos you have here..
Please post the output to the last command :
     Code:
     tail -v -n +1 /etc/apt/sources.list.d/*

```
lucy@lucy-N150P:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/anonbeat-guayadeque-precise.list <==
deb http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu precise main
# deb-src http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu precise main

==> /etc/apt/sources.list.d/anonbeat-guayadeque-precise.list.save <==
deb http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu precise main
# deb-src http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu precise main

==> /etc/apt/sources.list.d/catfish-search-catfish-stable-precise.list <==
deb http://ppa.launchpad.net/catfish-search/catfish-stable/ubuntu precise main
# deb-src http://ppa.launchpad.net/catfish-search/catfish-stable/ubuntu precise main

==> /etc/apt/sources.list.d/catfish-search-catfish-stable-precise.list.save <==
deb http://ppa.launchpad.net/catfish-search/catfish-stable/ubuntu precise main
# deb-src http://ppa.launchpad.net/catfish-search/catfish-stable/ubuntu precise main

==> /etc/apt/sources.list.d/claws-mail-ppa-precise.list <==
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/claws-mail/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/claws-mail-ppa-precise.list.save <==
deb http://ppa.launchpad.net/claws-mail/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/claws-mail/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/cooperjona-stormcloud-precise.list.save <==
deb-src http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu precise main

==> /etc/apt/sources.list.d/deluge-team-ppa-precise.list <==

==> /etc/apt/sources.list.d/deluge-team-ppa-precise.list.save <==
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/ehoover-compholio-precise.list <==

==> /etc/apt/sources.list.d/ehoover-compholio-precise.list.save <==
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main

==> /etc/apt/sources.list.d/getdeb.list <==
deb http://archive.getdeb.net/ubuntu precise-getdeb apps

==> /etc/apt/sources.list.d/getdeb.list.save <==
deb http://archive.getdeb.net/ubuntu precise-getdeb apps

==> /etc/apt/sources.list.d/h-realh-roxterm-precise.list <==
deb http://ppa.launchpad.net/h-realh/roxterm/ubuntu precise main
# deb-src http://ppa.launchpad.net/h-realh/roxterm/ubuntu precise main

==> /etc/apt/sources.list.d/h-realh-roxterm-precise.list.save <==
deb http://ppa.launchpad.net/h-realh/roxterm/ubuntu precise main
# deb-src http://ppa.launchpad.net/h-realh/roxterm/ubuntu precise main

==> /etc/apt/sources.list.d/kevin-mehall-pithos-daily-precise.list <==
deb http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu precise main
# deb-src http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu precise main

==> /etc/apt/sources.list.d/kevin-mehall-pithos-daily-precise.list.save <==
deb http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu precise main
# deb-src http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu precise main

==> /etc/apt/sources.list.d/kubuntu-ppa-backports-precise.list <==
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main

==> /etc/apt/sources.list.d/kubuntu-ppa-backports-precise.list.save <==
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main

==> /etc/apt/sources.list.d/landronimirc-clamtk-precise.list <==
deb http://ppa.launchpad.net/landronimirc/clamtk/ubuntu precise main
# deb-src http://ppa.launchpad.net/landronimirc/clamtk/ubuntu precise main

==> /etc/apt/sources.list.d/landronimirc-clamtk-precise.list.save <==
deb http://ppa.launchpad.net/landronimirc/clamtk/ubuntu precise main
# deb-src http://ppa.launchpad.net/landronimirc/clamtk/ubuntu precise main

==> /etc/apt/sources.list.d/landronimirc-skippy-xd-daily-precise.list <==

==> /etc/apt/sources.list.d/landronimirc-skippy-xd-daily-precise.list.save <==
deb-src http://ppa.launchpad.net/landronimirc/skippy-xd-daily/ubuntu precise main

==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list.save <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/linphone-release-precise.list <==
deb http://ppa.launchpad.net/linphone/release/ubuntu precise main
# deb-src http://ppa.launchpad.net/linphone/release/ubuntu precise main

==> /etc/apt/sources.list.d/linphone-release-precise.list.save <==
deb http://ppa.launchpad.net/linphone/release/ubuntu precise main
# deb-src http://ppa.launchpad.net/linphone/release/ubuntu precise main

==> /etc/apt/sources.list.d/linrunner-tlp-precise.list <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu precise main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu precise main

==> /etc/apt/sources.list.d/linrunner-tlp-precise.list.save <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu precise main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu precise main

==> /etc/apt/sources.list.d/lubuntu-desktop-ppa-precise.list <==

==> /etc/apt/sources.list.d/lubuntu-desktop-ppa-precise.list.save <==
# deb-src http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/lubuntu-dev-lubuntu-daily-precise.list.save <==
deb http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu precise main
deb-src http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu precise main

==> /etc/apt/sources.list.d/lubuntu-dev-non-official-apps-precise.list <==

==> /etc/apt/sources.list.d/lubuntu-dev-non-official-apps-precise.list.save <==
# deb-src http://ppa.launchpad.net/lubuntu-dev/non-official-apps/ubuntu precise main

==> /etc/apt/sources.list.d/lubuntu-dev-staging-precise.list.save <==
deb http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu precise main
deb-src http://ppa.launchpad.net/lubuntu-dev/staging/ubuntu precise main

==> /etc/apt/sources.list.d/lxle-stable-precise.list <==
deb http://ppa.launchpad.net/lxle/stable/ubuntu precise main
# deb-src http://ppa.launchpad.net/lxle/stable/ubuntu precise main

==> /etc/apt/sources.list.d/lxle-stable-precise.list.save <==
deb http://ppa.launchpad.net/lxle/stable/ubuntu precise main
# deb-src http://ppa.launchpad.net/lxle/stable/ubuntu precise main

==> /etc/apt/sources.list.d/lxle-updates-precise.list <==

==> /etc/apt/sources.list.d/lxle-updates-precise.list.save <==
# deb-src http://ppa.launchpad.net/lxle/updates/ubuntu precise main

==> /etc/apt/sources.list.d/medibuntu.list <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/

==> /etc/apt/sources.list.d/medibuntu.list.save <==
## Please report any bug on https://bugs.launchpad.net/medibuntu/

==> /etc/apt/sources.list.d/nemh-systemback-precise.list <==
deb http://ppa.launchpad.net/nemh/systemback/ubuntu precise main
deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu precise main

==> /etc/apt/sources.list.d/nemh-systemback-precise.list.save <==
deb http://ppa.launchpad.net/nemh/systemback/ubuntu precise main
deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu precise main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-precise.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.save <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main

==> /etc/apt/sources.list.d/noobslab-deepin-sc-precise.list <==

==> /etc/apt/sources.list.d/noobslab-deepin-sc-precise.list.save <==
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu precise main

==> /etc/apt/sources.list.d/noobslab-icons-precise.list <==
deb http://ppa.launchpad.net/noobslab/icons/ubuntu precise main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu precise main

==> /etc/apt/sources.list.d/noobslab-icons-precise.list.save <==
deb http://ppa.launchpad.net/noobslab/icons/ubuntu precise main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu precise main

==> /etc/apt/sources.list.d/noobslab-themes-precise.list <==
deb http://ppa.launchpad.net/noobslab/themes/ubuntu precise main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu precise main

==> /etc/apt/sources.list.d/noobslab-themes-precise.list.save <==
deb http://ppa.launchpad.net/noobslab/themes/ubuntu precise main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu precise main

==> /etc/apt/sources.list.d/nowrep-qupzilla-precise.list <==
deb http://ppa.launchpad.net/nowrep/qupzilla/ubuntu precise main
deb-src http://ppa.launchpad.net/nowrep/qupzilla/ubuntu precise main

==> /etc/apt/sources.list.d/openshot_developers-ppa-precise.list <==
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/openshot_developers-ppa-precise.list.save <==
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main
# deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list <==
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main

==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save <==
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main

==> /etc/apt/sources.list.d/playdeb.list <==
deb http://archive.getdeb.net/ubuntu precise-getdeb games

==> /etc/apt/sources.list.d/playdeb.list.save <==
deb http://archive.getdeb.net/ubuntu precise-getdeb games

==> /etc/apt/sources.list.d/richardgv-compton-precise.list.save <==
deb http://ppa.launchpad.net/richardgv/compton/ubuntu precise main
# deb-src http://ppa.launchpad.net/richardgv/compton/ubuntu precise main

==> /etc/apt/sources.list.d/shimmerproject-ppa-precise.list.save <==
deb-src http://ppa.launchpad.net/shimmerproject/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/shnatsel-zram-precise.list <==

==> /etc/apt/sources.list.d/shnatsel-zram-precise.list.save <==
deb-src http://ppa.launchpad.net/shnatsel/zram/ubuntu precise main

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.dpkg-old <==
deb http://repo.steampowered.com/steam/ precise steam
# deb-src http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/tuxpoldo-btsync-precise.list <==
deb http://ppa.launchpad.net/tuxpoldo/btsync/ubuntu precise main
# deb-src http://ppa.launchpad.net/tuxpoldo/btsync/ubuntu precise main

==> /etc/apt/sources.list.d/tuxpoldo-btsync-precise.list.save <==
deb http://ppa.launchpad.net/tuxpoldo/btsync/ubuntu precise main
# deb-src http://ppa.launchpad.net/tuxpoldo/btsync/ubuntu precise main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save <==
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/upubuntu-com-chat-precise.list <==

==> /etc/apt/sources.list.d/upubuntu-com-chat-precise.list.save <==
# deb-src http://ppa.launchpad.net/upubuntu-com/chat/ubuntu precise main

==> /etc/apt/sources.list.d/videolan-master-daily-precise.list <==

==> /etc/apt/sources.list.d/videolan-master-daily-precise.list.save <==
# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu precise main

==> /etc/apt/sources.list.d/videolan-stable-daily-precise.list <==
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main

==> /etc/apt/sources.list.d/videolan-stable-daily-precise.list.save <==
deb http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main
# deb-src http://ppa.launchpad.net/videolan/stable-daily/ubuntu precise main

==> /etc/apt/sources.list.d/vokoscreen-dev-vokoscreen-precise.list <==
deb http://ppa.launchpad.net/vokoscreen-dev/vokoscreen/ubuntu precise main
# deb-src http://ppa.launchpad.net/vokoscreen-dev/vokoscreen/ubuntu precise main

==> /etc/apt/sources.list.d/vokoscreen-dev-vokoscreen-precise.list.save <==
deb http://ppa.launchpad.net/vokoscreen-dev/vokoscreen/ubuntu precise main
# deb-src http://ppa.launchpad.net/vokoscreen-dev/vokoscreen/ubuntu precise main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu precise main
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu precise main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list.save <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu precise main
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu precise main

==> /etc/apt/sources.list.d/yannubuntu-boot-repair-precise.list <==

==> /etc/apt/sources.list.d/yannubuntu-boot-repair-precise.list.save <==
deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu precise main

==> /etc/apt/sources.list.d/ytvwld-syncthing-precise.list <==
deb http://ppa.launchpad.net/ytvwld/syncthing/ubuntu precise main
# deb-src http://ppa.launchpad.net/ytvwld/syncthing/ubuntu precise main

==> /etc/apt/sources.list.d/ytvwld-syncthing-precise.list.save <==
deb http://ppa.launchpad.net/ytvwld/syncthing/ubuntu precise main
# deb-src http://ppa.launchpad.net/ytvwld/syncthing/ubuntu precise main
lucy@lucy-N150P:~$ 

```

What does this mean for using the distro? Haven't tried many but this seems to be the fastest so far, including lubuntu.

UPDATE: error when I type the purge command ```
lucy@lucy-N150P:~$ sudo apt-get purge nautilus-dropbox
[sudo] password for lucy: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by bapoumba on 2014-10-24
> **lucy3 said:**
> 
What does this mean for using the distro? Haven't tried many but this seems to be the fastest so far, including lubuntu.
Well, it may mean nothing to your current problem. I just know that very often, when dealing with packages and package managers, it is useful to have a complete picture of all the repositories used on a system. Now you have what I would call a lot of repositories :)

Back to dropbox, which version matches Precise 12.04, so it is not coming from somewhere else, have you tried to purge/install again ?
Please do it from a terminal and post the full outputs.

---

### Post by lucy3 on 2014-10-24
```
lucy@lucy-N150P:~$ sudo apt-get purge nautilus-dropbox
[sudo] password for lucy: 
Sorry, try again.
[sudo] password for lucy: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
lucy@lucy-N150P:~$ sudo apt-get install nautilus-dropbox
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

I didn't mistype my password, restarted the terminal three times before pasting the results. Same every time 'try again' and then accepted.

Appreciate the time your spending on this. :D

---

### Post by ian-weisser on 2014-10-24
> **lucy3 said:**
> Tried to update and software said it wanted to do a partial upgrade

Considering how many PPAs seem to be installed, I wouldn't try to update to another version of Ubuntu.
Updates work best when PPAs and other non-Ubuntu software have been uninstalled.

---

### Post by bapoumba on 2014-10-25
I'd be curious to know if dpkg broke with installing nautilus-dropbox or was previously broken. You can have a look at logs : /var/lib/dpkg/status & /var/backups for older log files.

---

### Post by lucy3 on 2014-10-25
I've solved it. :) bampou[**[COLOR=#990303][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805")ma you beat me to the posting. Dropbox was the culprit, just that particular package. A search of lxle lead me to a post where someone had the exact problem. For anyone else tearing their hair out over this:

1) Boot into recovery mode
2) Select the repair option within recovery, recovery will say dropbox is installed
3) Boot into 'normal' mode
4) Despite what your system said, dropbox won't run. Delete it using the software manager and reinstall, using terminal, package manager, or direct from the dropbox website.

Don't know if it's a bug with this particular distro or if that package is dodgy. Software centre seems fine with everything else but nice to know about the repair option. 

Thanks to everyone who gave up their time to help me out. :D

---

### Post by bapoumba on 2014-10-25
Glad to see you fixed it. Please mark your thread as solved (under Thread tools), thanks.
I am interested by the link where you found that, do you still have it around ? A broken dpkg output is a broken dpkg output, unless I am missing something about recovery mode, which I very will may :)

---

### Post by lucy3 on 2014-10-26
> Glad to see you fixed it. Please mark your thread as solved (under Thread tools), thanks.

Already done, may be a NOOB but that's just good manners :P

> [I am interested by the link where you found that, do you still have it  around ? A broken dpkg output is a broken dpkg output, unless I am  missing something about recovery mode, which I very will may :smile:

See below, don't know enough to tell you what exactly the repair function does.

[HTML]http://lxle.net/forum/#/discussion/522/dropbox-wont-install/p1[/HTML]

---

