---
title: "Problem configuring Wine Audio to run Spotify"
date: 2012-06-06
forum: Virtualisation
---

### Post by mimicatastrophe on 2012-06-06
Anyone running Spotify on current ubuntu/wine releases? 

Spotify specifies to configure wine audio tab and i am unable to as there are no other options in the menus besides "default"

I cant live without Spotify anymore lol this and In Design seem to be my only problems with switching to linux from windows. 

Anyway I found another site to try to direct me on the Spoty issue and this is what ended up happening. ```
mimi@Isis:~$ sudo gedit /etc/apt/sources.list.d/spotify.list
[sudo] password

(gedit:22497): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VJV2EW': No such file or directory

(gedit:22497): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:22497): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

mimi@Isis:~$ sudo apt-get update
Ign http://repostitory.spotify.com precise InRelease
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://archive.canonical.com precise InRelease                             
Get:3 http://repository.spotify.com stable InRelease [2,009 B]                 
Get:4 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:5 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:6 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Err http://repostitory.spotify.com precise Release.gpg                         
  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)
Ign http://repostitory.spotify.com precise Release                             
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]                   
Get:8 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:9 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Get:10 http://repository.spotify.com stable/non-free i386 Packages [894 B]     
Get:11 http://archive.canonical.com precise Release [7,078 B]                  
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Get:12 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:13 http://security.ubuntu.com precise-security/main Sources [14.9 kB]      
Get:14 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:15 http://archive.canonical.com precise/partner Sources [3,417 B]          
Get:16 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Get:17 http://archive.canonical.com precise/partner i386 Packages [4,999 B]    
Get:18 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:19 http://security.ubuntu.com precise-security/universe Sources [4,935 B]  
Get:20 http://security.ubuntu.com precise-security/multiverse Sources [696 B]  
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [49.4 kB]
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [11.6 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://repostitory.spotify.com precise/main TranslationIndex               
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Err http://repostitory.spotify.com precise/main Sources                   
  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)
Err http://repostitory.spotify.com precise/main i386 Packages             
  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)
Get:25 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:26 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Err http://repostitory.spotify.com precise/main Translation-en_US              
  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)
Err http://repostitory.spotify.com precise/main Translation-en                 
  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)
Get:27 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:28 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:29 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:30 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:31 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:32 http://us.archive.ubuntu.com precise-updates/main Sources [98.4 kB]     
Get:33 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:34 http://us.archive.ubuntu.com precise-updates/universe Sources [19.6 kB] 
Get:35 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,053 B]
Get:36 http://us.archive.ubuntu.com precise-updates/main i386 Packages [236 kB]
Get:37 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:38 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [59.0 kB]
Get:39 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,046 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:40 http://us.archive.ubuntu.com precise-backports/main Sources [700 B]     
Get:41 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:42 http://us.archive.ubuntu.com precise-backports/universe Sources [6,109 B]
Get:43 http://us.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:44 http://us.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:45 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:46 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [5,227 B]
Get:47 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 13.0 MB in 2min 22s (91.7 kB/s)                                        
W: Failed to fetch http://repostitory.spotify.com/dists/precise/Release.gpg  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repostitory.spotify.com/dists/precise/main/source/Sources  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repostitory.spotify.com/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repostitory.spotify.com/dists/precise/main/i18n/Translation-en_US  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repostitory.spotify.com/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'repostitory.spotify.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
mimi@Isis:~$ sudo gedit /etc/apt/sources.list

```

so the spotify document i was told to make placed a line in sources.list but claims spotify is precise which it is not correct? would this solve anything? 

spotify installs and opens but audio is a loud higher tone dense static.

---

