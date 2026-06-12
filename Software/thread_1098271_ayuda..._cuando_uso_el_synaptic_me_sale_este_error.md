---
title: "ayuda... cuando uso el synaptic me sale este error"
date: 2009-03-16
forum: Software
---

### Post by amomp3 on 2009-03-16
E: Vaya, excedió el número de descripciones que este APT es capaz de manejar.
E: Problem with MergeList /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_main_i18n_Translation-es
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

como no supe borrarlo en ese momento lo edite con:
gksudo gedit /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_main_i18n_Translation-es
y lo vacié

pero ahora me sale esto:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_main_i18n_Translation-es
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_intrepid_partner_binary-i386_Packages)


por toquetear no ?:D

---

### Post by josecuervo86 on 2009-03-16
> **amomp3 said:**
> por toquetear no ?:D

Y a vos que te parece :P

Lo que te aconsejaria es que hicieras un backup del archivo antes de que te agarren las ganas de toquetear. Te lo digo por propia experiencia :(

---

### Post by Hei Ku on 2009-03-16
¿Que sucede si en la terminal pones esto?

sudo apt-get update

---

### Post by amomp3 on 2009-03-16
pasó esto:

Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Des:2 [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release.gpg [189B]               
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid Release.gpg                          
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid Release.gpg                                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/main Translation-es                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/restricted Translation-es            
Des:3 [http://apt.wicd.net](http://apt.wicd.net) intrepid Release.gpg [197B]                          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/universe Translation-es              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/multiverse Translation-es            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security Release.gpg                 
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/main Translation-es                          
Des:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/restricted Translation-es                    
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/universe Translation-es                      
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/multiverse Translation-es                    
Des:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-es                 
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-es             
Des:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates Release.gpg                          
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Translation-es                         
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/main Translation-es                  
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/restricted Translation-es            
Des:7 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]              
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/universe Translation-es              
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/multiverse Translation-es            
Des:8 [http://apt.wicd.net](http://apt.wicd.net) intrepid Release [17,2kB]                            
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-es                        
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security Release.gpg                         
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid Release                                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) intrepid/non-free Translation-es            
Ign [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/main Translation-es                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es        
Des:9 [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release [2093B]                  
Ign [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release                            
Ign [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/restricted Translation-es           
Obj [http://download.virtualbox.org](http://download.virtualbox.org) intrepid/non-free Packages                  
Ign [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/universe Translation-es             
Ign [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/multiverse Translation-es           
Des:10 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                             
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid Release                                      
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Packages                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es          
Obj [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Packages                               
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/main Translation-es         
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates Release                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security Release                             
Des:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]           
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/main Packages                                
Des:12 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-es                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-es               
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/restricted Packages                          
Des:13 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release [1025B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es              
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/main Sources                                 
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty Release.gpg                           
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/restricted Sources                           
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/restricted Translation-es   
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/universe Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-es                         
Des:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-es       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-es                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es        
Des:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58,5kB]              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Translation-es                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/universe Translation-es     
Des:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1105B]    
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/universe Sources                             
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/multiverse Packages                          
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid/multiverse Sources                           
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-es                      
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/restricted Packages                  
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/main Sources                         
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-es               
Obj [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty Release                               
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/restricted Sources                   
Des:17 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11,7kB]                 
Des:18 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11,7kB]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Obj [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Des:19 [http://mirror.noreply.org](http://mirror.noreply.org) intrepid Release.gpg [197B]                   
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/universe Packages                    
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                   
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/multiverse Translation-es   
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/universe Sources                     
Des:20 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates Release.gpg [189B]        
Des:21 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [11,2kB]  
Des:22 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [9913B]      
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/main Translation-es          
Des:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/restricted Translation-es    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/universe Translation-es      
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/multiverse Packages                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/multiverse Translation-es    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed Release.gpg                 
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages                          
Des:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58,5kB]             
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-updates/multiverse Sources                   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/main Translation-es         
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/restricted Translation-es   
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/main Packages                       
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/universe Translation-es     
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/multiverse Translation-es   
Des:25 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports Release.gpg [189B]      
Ign [http://mirror.noreply.org](http://mirror.noreply.org) intrepid/main Translation-es                     
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/restricted Packages                 
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/main Sources                        
Des:26 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [65,6kB]    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-es                      
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/restricted Sources                  
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty/all Packages                          
  404 Not Found
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-es               
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/universe Packages                   
Des:27 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [24,8kB]         
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/universe Sources                    
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/main Translation-es        
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/multiverse Packages                 
Des:28 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [892B]     
Des:29 [http://mirror.noreply.org](http://mirror.noreply.org) intrepid Release [1932B]                      
Obj [http://sft.if.usp.br](http://sft.if.usp.br) intrepid-security/multiverse Sources                  
Ign [http://mirror.noreply.org](http://mirror.noreply.org) intrepid Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Des:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [5212B]   
Des:31 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [144kB]         
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/restricted Translation-es  
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-es                  
Obj [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Obj [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-es                      
Ign [http://mirror.noreply.org](http://mirror.noreply.org) intrepid/main Packages                           
Des:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Des:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [28,2kB] 
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/universe Translation-es    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-es                      
Obj [http://mirror.noreply.org](http://mirror.noreply.org) intrepid/main Packages                           
Des:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/multiverse Translation-es  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid Release                              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security Release                     
Des:35 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates Release [51,2kB]          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-es                      
Des:36 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports Release [44,0kB]        
Des:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/main Packages                        
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/restricted Packages                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/universe Packages                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/multiverse Packages                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/main Sources                         
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/restricted Sources                   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/universe Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-es                      
Des:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]                         
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid/multiverse Sources                   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/main Packages               
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/restricted Packages         
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/universe Packages           
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/multiverse Packages         
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/main Sources                
Des:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46,7kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Des:40 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/restricted Sources [1154B]
Des:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46,7kB]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Des:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27,6kB]                      
Des:43 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/universe Sources [5746B] 
Des:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46,7kB]                      
Des:45 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-security/multiverse Sources [1860B]
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/main Packages                
Des:46 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [7487B]   
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/restricted Packages          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/universe Packages            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/main Sources                 
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/restricted Sources           
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-updates/multiverse Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/multiverse Packages
Des:47 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/main Sources [27,5kB]
Des:48 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/restricted Sources [564B]
Des:49 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/universe Sources [4840B] 
Des:50 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-proposed/multiverse Sources [14B] 
Des:51 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/main Packages [80,0kB]  
Des:52 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Des:53 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/universe Packages [38,0kB]
Des:54 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/multiverse Packages [14B]
Des:55 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/main Sources [15,8kB]   
Des:56 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/restricted Sources [14B]
Des:57 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/universe Sources [12,7kB]
Obj [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                 
Des:58 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27,6kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                 
Des:59 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46,7kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Des:60 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/multiverse Sources [14B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                             
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                          
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                       
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                           
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                           
Des:61 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [1326B]                                                                
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                           
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                           
Descargados 753kB en 8s (92,0kB/s)                                                                                            
W: Error de GPG: [http://apt.wicd.net](http://apt.wicd.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY FEC820F4B8C0755A
W: Error de GPG: [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY DCF9F87B6DFBCBAE
W: Error de GPG: [http://dl.google.com](http://dl.google.com) stable Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY A040830F7FAC5991
W: Error de GPG: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 58403026387EE263
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Error de GPG: [http://mirror.noreply.org](http://mirror.noreply.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY CFF71CB3AFA44BDD
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 4874D3686E80C6B7
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY C5E6A5ED249AD24C
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 28A8205077558DD0
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 02FE5F12ADDE29B2
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 6AF0E1940624A220
W: Imposible obtener [http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz)  404 Not Found

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


despues ejecute synaptic otra vez y me salió el mismo error q postié
(gracias por la ayuda)

---

### Post by ADICTOALMAXIMO on 2009-03-17
Ajja

lo toquetiaste al pinguino

metele nomas asi haiga mas pinguinos

---

### Post by amomp3 on 2009-03-17
me sale q hay actualizaciones disponibles y me sale este error cuando va a cargarlas:


No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_main_i18n_Translation-es, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

---

### Post by Hei Ku on 2009-03-17
Cerra el update-manager, Synaptic, y todo el resto y volve a poner en la consola:

sudo apt-get update

Postea solo las ultimas 10 lineas.

Si eso termina sin error, podes probar de actualizar con este comando:

sudo apt-get dist-upgrade


@AdictoAlMaximo: ya te adverti que no postees si no tenes algo util para decir. Lo tuyo es spam, y esto es un foro de soporte.

---

### Post by amomp3 on 2009-03-17
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid-backports/multiverse Sources                                         
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                            
Descargados 941kB en 13s (70,7kB/s)                                                                            
W: Error de GPG: [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY DCF9F87B6DFBCBAE
W: Error de GPG: [http://apt.wicd.net](http://apt.wicd.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY FEC820F4B8C0755A
W: Error de GPG: [http://dl.google.com](http://dl.google.com) stable Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY A040830F7FAC5991
W: Error de GPG: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 58403026387EE263
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Error de GPG: [http://mirror.noreply.org](http://mirror.noreply.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY CFF71CB3AFA44BDD
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 4874D3686E80C6B7
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY C5E6A5ED249AD24C
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 28A8205077558DD0
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 02FE5F12ADDE29B2
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 6AF0E1940624A220
W: Imposible obtener [http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/harty/all/binary-i386/Packages.gz)  404 Not Found

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.bz2)  La suma MD5 difiere

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2)  La suma MD5 difiere

W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2)  La suma MD5 difiere

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.


disculpá si puse + de 10 pero las 2 primeras es como venia bien sin error y despues estan los errores...

Gracias !

---

### Post by Mauro22 on 2009-03-17
Por lo que veo tenes un monton de sources, que las agregaste y te da error la GPG Key porque son origenes de software no firmados.


Mi consejo es borrar todo el sources.list, poner las direcciones originales, guardar y hacer un update...

No confio en esos origenes... si bien  los nombres son conocidos.

```

...
W: Error de GPG: **[http://apt.wicd.net]("http://apt.wicd.net/") **intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY FEC820F4B8C0755A
W: Error de GPG: **[http://dl.google.com]("http://dl.google.com/")** stable Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY A040830F7FAC5991
W: Error de GPG: **[http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/")** intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 58403026387EE263
....
```

---

### Post by amomp3 on 2009-03-17
el actualizador  de ubuntu me tira esto:

**No se ha podido inicializar la información de los paquetes**

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_main_i18n_Translation-es, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

y synaptic esto:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_main_i18n_Translation-es
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

intenté borrar ese archivo pero  soy el usuario "amo" q no es admin creo
no puedo ser admin o hacer algo para quedar "autorizado" ?

lo q si sé es q con gksudo gedit /etc/apt/sources.list edité la lista como me pidieron asi q tmb edite ese archivo y le borre lo de adentro :twisted: pero sigue dando el mismo error, en serio les juro es el mismo error, es raro...

---

### Post by amomp3 on 2009-03-17
bueno, cumplo con mi deber al anunciar que dentro de Origenes de Software desactivé la casilla universe suponiendo q iba a desactivar todos los universe pero bueno funciono !

ahora la pregunta es... si la vuelvo a activar se va a vovler a c***r ? como arreglo para q no haga más referencia a esa maldita source ?

(E: Problem with MergeList /var/lib/apt/lists/sft.if.usp.br_ubuntu_dists_intrepid_universe_i18n_Translation-es)

si activo la casilla de nuevo no me volvera a  pasar ?

---

### Post by amomp3 on 2009-03-17
si, me vuelve a pasar ...
maldiciooon y quiero encontrar donde esta el error xq no quiero desactivar todo a lo cabezon xq quiero instalar amarok !

---

### Post by josecuervo86 on 2009-03-17
metete en synaptic y anda Configuración -> Repositorios -> Software de terceros y si tenes casillas tildadas desmarcalas y proba a ver si anda

---

### Post by amomp3 on 2009-03-17
si pero eso no soluciona el problema sino que lo pasa por alto ...

xq como digo, quisiera instalar amarok 2 y para eso tengo q habilitar esas fuentes ...

---

### Post by Hei Ku on 2009-03-18
hace un update y un clean, a ver que pasa, y despues volve a probar.

sudo apt-get update

sudo apt-get clean

Y despues de esto volve a habilitar los otros repositorios.

---

### Post by amomp3 on 2009-03-18
los repos de la lista de terceros ni los toco y desactivo (universe) en Software de ubuntu y hice lo q me decis y va bien pero cuando vuelvo a activar universe me aparece esto, por lo menos ahora cambió el error:


E: Vaya, excedió el número de descripciones que este APT es capaz de manejar.
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

---

### Post by Hei Ku on 2009-03-18
Probá lo siguiente. Poné esto en la terminal para arrancar Synaptic:

```

LANG=C; sudo synaptic

```

---

### Post by losoollenos on 2009-06-10
A mi me sale este : 

W: Error de GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5
W: Error de GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5
W: Error de GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

Error similar al que daban los repositrios launchpad que se solucionó con el script que anda por ahi y agradezco. Ya probé con el servidor de Argentina y Brasil y lo mismo, hace una semana más o menos, pueden estar caídos?

Muchas gracias y saludos

---

### Post by Hei Ku on 2009-06-10
Probaste con Synaptic o KPackageKit? Ambos actualizan las claves automaticamente.

---

### Post by losoollenos on 2009-06-10
El mismo error me sale con sinaptic......te parece que pruebe también con KPackageKit ?

---

### Post by Hei Ku on 2009-06-10
No, seguramente va a hacer lo mismo.

Probá esto:

```

gpg --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

```

Si no anda, postea tu archivo /etc/apt/sources.list

---

### Post by losoollenos on 2009-06-11
Lo primero:

ubuntu@ubuntu-desktop:~$ gpg &#8211;recv-keys 40976EAF437D05B5uso: gpg [opciones] [nombre_fichero]
ubuntu@ubuntu-desktop:~$ 

ubuntu@ubuntu-desktop:~$ sudo gpg &#8211;recv-keys 40976EAF437D05B5gpg: AVISO: propiedad insegura del fichero de configuración `/home/ubuntu/.gnupg/gpg.conf'
uso: gpg [opciones] [nombre_fichero]
ubuntu@ubuntu-desktop:~$ 

Sources list:

# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main

Muchas gracias

---

### Post by Hei Ku on 2009-06-11
Fue un error mío al pegar los comandos. Van con doble guion, en vez de simple. 

Fijate que ahí edité el post. Copia los comandos de vuelta y correlos en una terminal.

---

### Post by losoollenos on 2009-06-11
Sale esto:

ubuntu@ubuntu-desktop:~$ gpg --recv-keys 40976EAF437D05B5
gpg: no hay servidores de claves conocidos (use opción --keyserver)
gpg: recepción del servidor de claves fallida: URI incorrecto
ubuntu@ubuntu-desktop:~$ gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
gpg: ATENCIÓN: no se ha exportado nada
[sudo] password for ubuntu: 
gpg: No se han encontrados datos OpenPGP válidos
ubuntu@ubuntu-desktop:~$ 

Saludos

---

### Post by pablo.s on 2009-06-11
Proba cambiando a los
servidores de Estados
Unidos.

---

### Post by Hei Ku on 2009-06-11
Probá con esto. Le agregué el keyserver, porque no lo tomó automaticamente.

```

gpg --recv-keys 40976EAF437D05B5 --keyserver wwwkeys.eu.pgp.net
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

```

---

### Post by losoollenos on 2009-06-11
Hei Ku, 

ubuntu@ubuntu-desktop:~$ gpg --recv-keys 40976EAF437D05B5 --keyserver wwwkeys.eu.pgp.net
gpg: '--keyserver' no es un identificador de clave válido
gpg: 'wwwkeys.eu.pgp.net' no es un identificador de clave válido
gpg: no hay servidores de claves conocidos (use opción --keyserver)
gpg: recepción del servidor de claves fallida: URI incorrecto
ubuntu@ubuntu-desktop:~$ gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
gpg: ATENCIÓN: no se ha exportado nada
[sudo] password for ubuntu: 
gpg: No se han encontrados datos OpenPGP válidos
ubuntu@ubuntu-desktop:~$ 

pablo.s, probé lo que me sugerís pero sale el mísmo error.

Muchas gracias y saludos

---

### Post by Hei Ku on 2009-06-11
ese comando gpg me tiene...

gpg --recv-keys --keyserver wwwkeys.eu.pgp.net 40976EAF437D05B5

Y eso de que el orden de los factores no altera el producto, en este caso, es falso. :p

---

### Post by losoollenos on 2009-06-11
Ahora si !!!
Muchas gracias Hei Ku, y para otra vez, tendré que reemplazar el número largo ese por el que salga, lo demás todo igual?

saludos

---

### Post by Hei Ku on 2009-06-11
Si, todo el resto es igual.

---

### Post by losoollenos on 2009-06-11
Ok ya lo estoy guardando para mis machetes jeje

Muchas gracias y hasta pronto !!!!

---

