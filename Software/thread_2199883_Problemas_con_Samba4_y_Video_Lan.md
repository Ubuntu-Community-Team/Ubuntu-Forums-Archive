---
title: "Problemas con Samba4 y Video Lan"
date: 2014-01-16
forum: Software
---

### Post by Vero1 on 2014-01-16
Buenos Días,

Cada vez que actualizo me sale el siguiente error. Aparte, la navegación se hizo muy lenta y de vez en cuando se freeza.
Uso Ubuntu 12.04

Ésto me sale al actualizar, tanto por el Administrador de Actualizaciones como por Terminal:


Des:1 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise Release.gpg [198 B]
Des:2 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates Release.gpg [198 B]                
Des:3 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports Release.gpg [198 B]              
Des:4 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security Release.gpg [198 B]               
Des:5 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise Release [49,6 kB]                          
Des:6 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates Release [49,6 kB]                  
Des:7 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports Release [49,6 kB]                
Des:8 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security Release [49,6 kB]                 
Des:9 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main Sources [934 kB]                      
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Obj [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Obj [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Obj [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Des:10 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted Sources [5.470 B]              
Des:11 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe Sources [5.019 kB]               
Des:12 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release.gpg [287 B]                           
Obj [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release                                          
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release                                          
Des:13 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages/DiffIndex                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-es_ES                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-es_ES                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-es_ES             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-es                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-es                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-es                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages/DiffIndex                               
Des:14 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Des:15 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse Sources [155 kB]               
Des:16 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main i386 Packages [1.274 kB]             
Des:17 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted i386 Packages [8.431 B]        
Des:18 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe i386 Packages [4.796 kB]   
Des:19 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                       
Des:20 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:21 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse i386 Packages [121 kB]         
Des:22 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main TranslationIndex [3.706 B]           
Des:23 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse TranslationIndex [2.676 B]     
Des:24 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted TranslationIndex [2.596 B]     
Des:25 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe TranslationIndex [2.922 B]       
Des:26 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main Sources [447 kB]             
Obj [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages                                         
Des:27 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted Sources [7.039 B]      
Des:28 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe Sources [101 kB]         
Des:29 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse Sources [8.486 B]
Des:30 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main i386 Packages [765 kB]
Des:31 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                    
Des:32 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted i386 Packages [11,5 kB]
Des:33 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe i386 Packages [234 kB]
Des:34 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse i386 Packages [14,4 kB]
Des:35 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main TranslationIndex [3.564 B]
Des:36 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse TranslationIndex [2.605 B]
Des:37 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted TranslationIndex [2.461 B]
Des:38 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe TranslationIndex [2.850 B]
Des:39 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main Sources [4.225 B]          
Des:40 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted Sources [14 B]
Des:41 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Des:42 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe Sources [36,4 kB]      
Des:43 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse Sources [5.311 B]    
Des:44 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main i386 Packages [4.809 B]    
Des:45 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted i386 Packages [14 B] 
Des:46 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe i386 Packages [37,7 kB]
Des:47 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse i386 Packages [5.178 B]
Des:48 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main TranslationIndex [72 B]    
Des:49 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse TranslationIndex [72 B]
Des:50 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted TranslationIndex [70 B]
Des:51 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe TranslationIndex [73 B]
Des:52 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main Sources [95,7 kB]          
Des:53 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted Sources [2.494 B]     
Des:54 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe Sources [30,5 kB]       
Des:55 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse Sources [1.797 B]     
Des:56 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main i386 Packages [375 kB]      
Des:57 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted i386 Packages [4.620 B]
Des:58 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe i386 Packages [92,5 kB] 
Des:59 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse i386 Packages [2.650 B]
Des:60 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main TranslationIndex [74 B]     
Des:61 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse TranslationIndex [72 B]
Des:62 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted TranslationIndex [72 B]
Des:63 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe TranslationIndex [73 B] 
Des:64 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main Translation-es [652 kB]              
Des:65 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:66 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main Translation-en [726 kB]              
Des:67 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Des:68 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse Translation-es [101 kB]        
Des:69 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse Translation-en [93,4 kB]       
Des:70 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted Translation-es [2.691 B]       
Des:71 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted Translation-en [2.395 B]       
Des:72 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe Translation-es [1.284 kB]        
Des:73 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Des:74 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe Translation-en [3.341 kB]        
Des:75 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:76 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main Translation-es [652 kB]      
Des:77 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Des:78 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main Translation-en [333 kB]      
Des:79 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse Translation-es [101 kB]
Des:80 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse Translation-en [8.293 B]
Des:81 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted Translation-es [2.691 B]
Des:82 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted Translation-en [2.663 B]
Des:83 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe Translation-es [1.284 kB]
Des:84 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Des:85 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe Translation-en [134 kB]  
Des:86 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main Translation-en [4.235 B]   
Des:87 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse Translation-en [4.610 B]
Des:88 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted Translation-en [14 B]
Des:89 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe Translation-en [27,7 kB]
Des:90 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:91 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main Translation-en [167 kB]     
Des:92 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse Translation-en [1.299 B]
Des:93 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted Translation-en [1.253 B]
Des:94 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe Translation-en [55,3 kB]
Des:95 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                                
Des:96 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                   
Des:97 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                   
Descargados 23,8 MB en 49seg. (478 kB/s)                                       
Leyendo lista de paquetes... Hecho
W: Error de GPG: [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 6BCA5E4DB84288D9

-System-Product-Name:~$ samba
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[2014/01/16 11:48:23,  0] ../lib/util/debug.c:578(reopen_logs_internal)
  Unable to open new log file '/var/log/samba/log.%m': No such file or directory
[2014/01/16 11:48:23,  0] ../source4/smbd/server.c:366(binary_smbd_main)
  samba version 4.0.0alpha18 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2012


Por favor lo mas urgente posible una solución ya que hace tiempo que tengo este problema y a pesar del cartel que me sale de enviar informe, hasta ahora no se arregló el problema.

Gracias de antemano.

---

### Post by Vero1 on 2014-01-24
> **Vero1 said:**
> Buenos Días,

Cada vez que actualizo me sale el siguiente error. Aparte, la navegación se hizo muy lenta y de vez en cuando se freeza.
Uso Ubuntu 12.04

Ésto me sale al actualizar, tanto por el Administrador de Actualizaciones como por Terminal:


Des:1 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise Release.gpg [198 B]
Des:2 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates Release.gpg [198 B]                
Des:3 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports Release.gpg [198 B]              
Des:4 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security Release.gpg [198 B]               
Des:5 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise Release [49,6 kB]                          
Des:6 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates Release [49,6 kB]                  
Des:7 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports Release [49,6 kB]                
Des:8 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security Release [49,6 kB]                 
Des:9 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main Sources [934 kB]                      
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Obj [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Obj [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Obj [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Des:10 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted Sources [5.470 B]              
Des:11 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe Sources [5.019 kB]               
Des:12 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release.gpg [287 B]                           
Obj [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release                                          
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release                                          
Des:13 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages/DiffIndex                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-es_ES                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-es_ES                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-es_ES             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-es                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-es                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-es                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages/DiffIndex                               
Des:14 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Des:15 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse Sources [155 kB]               
Des:16 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main i386 Packages [1.274 kB]             
Des:17 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted i386 Packages [8.431 B]        
Des:18 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe i386 Packages [4.796 kB]   
Des:19 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                       
Des:20 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:21 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse i386 Packages [121 kB]         
Des:22 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main TranslationIndex [3.706 B]           
Des:23 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse TranslationIndex [2.676 B]     
Des:24 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted TranslationIndex [2.596 B]     
Des:25 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe TranslationIndex [2.922 B]       
Des:26 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main Sources [447 kB]             
Obj [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages                                         
Des:27 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted Sources [7.039 B]      
Des:28 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe Sources [101 kB]         
Des:29 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse Sources [8.486 B]
Des:30 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main i386 Packages [765 kB]
Des:31 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                    
Des:32 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted i386 Packages [11,5 kB]
Des:33 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe i386 Packages [234 kB]
Des:34 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse i386 Packages [14,4 kB]
Des:35 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main TranslationIndex [3.564 B]
Des:36 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse TranslationIndex [2.605 B]
Des:37 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted TranslationIndex [2.461 B]
Des:38 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe TranslationIndex [2.850 B]
Des:39 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main Sources [4.225 B]          
Des:40 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted Sources [14 B]
Des:41 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Des:42 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe Sources [36,4 kB]      
Des:43 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse Sources [5.311 B]    
Des:44 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main i386 Packages [4.809 B]    
Des:45 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted i386 Packages [14 B] 
Des:46 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe i386 Packages [37,7 kB]
Des:47 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse i386 Packages [5.178 B]
Des:48 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main TranslationIndex [72 B]    
Des:49 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse TranslationIndex [72 B]
Des:50 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted TranslationIndex [70 B]
Des:51 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe TranslationIndex [73 B]
Des:52 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main Sources [95,7 kB]          
Des:53 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted Sources [2.494 B]     
Des:54 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe Sources [30,5 kB]       
Des:55 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse Sources [1.797 B]     
Des:56 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main i386 Packages [375 kB]      
Des:57 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted i386 Packages [4.620 B]
Des:58 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe i386 Packages [92,5 kB] 
Des:59 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse i386 Packages [2.650 B]
Des:60 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main TranslationIndex [74 B]     
Des:61 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse TranslationIndex [72 B]
Des:62 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted TranslationIndex [72 B]
Des:63 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe TranslationIndex [73 B] 
Des:64 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main Translation-es [652 kB]              
Des:65 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:66 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/main Translation-en [726 kB]              
Des:67 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Des:68 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse Translation-es [101 kB]        
Des:69 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/multiverse Translation-en [93,4 kB]       
Des:70 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted Translation-es [2.691 B]       
Des:71 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/restricted Translation-en [2.395 B]       
Des:72 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe Translation-es [1.284 kB]        
Des:73 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Des:74 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise/universe Translation-en [3.341 kB]        
Des:75 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:76 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main Translation-es [652 kB]      
Des:77 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Des:78 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/main Translation-en [333 kB]      
Des:79 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse Translation-es [101 kB]
Des:80 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/multiverse Translation-en [8.293 B]
Des:81 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted Translation-es [2.691 B]
Des:82 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/restricted Translation-en [2.663 B]
Des:83 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe Translation-es [1.284 kB]
Des:84 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Des:85 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-updates/universe Translation-en [134 kB]  
Des:86 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/main Translation-en [4.235 B]   
Des:87 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/multiverse Translation-en [4.610 B]
Des:88 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/restricted Translation-en [14 B]
Des:89 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-backports/universe Translation-en [27,7 kB]
Des:90 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Des:91 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/main Translation-en [167 kB]     
Des:92 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/multiverse Translation-en [1.299 B]
Des:93 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/restricted Translation-en [1.253 B]
Des:94 [http://ftp.ccc.uba.ar](http://ftp.ccc.uba.ar) precise-security/universe Translation-en [55,3 kB]
Des:95 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                             
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es_ES                                
Des:96 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-es                                   
Des:97 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                   
Descargados 23,8 MB en 49seg. (478 kB/s)                                       
Leyendo lista de paquetes... Hecho
W: Error de GPG: [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 6BCA5E4DB84288D9

-System-Product-Name:~$ samba
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[2014/01/16 11:48:23,  0] ../lib/util/debug.c:578(reopen_logs_internal)
  Unable to open new log file '/var/log/samba/log.%m': No such file or directory
[2014/01/16 11:48:23,  0] ../source4/smbd/server.c:366(binary_smbd_main)
  samba version 4.0.0alpha18 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2012


Por favor lo mas urgente posible una solución ya que hace tiempo que tengo este problema y a pesar del cartel que me sale de enviar informe, hasta ahora no se arregló el problema.

Gracias de antemano.

Por favor, necesito urgentemente que se arregle el problema de Samba4 ya que provoca problemas con la navegación. Aparte cada vez que se actualiza informa que hubo problemas para configurar Samba4, aparte de que la navegación es lenta y a veces se freeza. Tambien suele aparecer un aviso de un script y pregunta si continúa o no. URGENTE SOLUCION POR FAVOR. Gracias.

---

### Post by gmunioz on 2014-01-25
Estas usando una versión alpha:

samba version 4.0.0alpha18 started.

Esto implica que solo es para pruebas, y que tendrá infinitos errores.
Mi sugerencia es que desinstales esa versión e instales la estable.

---

### Post by gmunioz on 2014-01-25
La versión estable es samba a secas, no samba4.
En cuanto al error del repositorio, no es importante y te indica que no ha sido validado, 
deberías validarlo introduciendo su clave gpg para que no siga informando ese error.

---

