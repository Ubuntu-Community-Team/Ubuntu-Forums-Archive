---
title: "Problemas con los repositorios Hardy &lt;-&gt; Wine,"
date: 2008-09-30
forum: Software
---

### Post by jm86ar on 2008-09-30
desde hace ya bastante tiempo sigo teniendo errores cada vez que trato de actualizar mi lista de repositorios.

Este es el depurado

 sudo apt-get -f update
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy Release.gpg                                                                          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Translation-es                                                                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Translation-es                                                            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Translation-es                                                            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release.gpg                                                                  
Obj [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es                                                           
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Translation-es                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es                                                
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Translation-es                                               
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-es                                                                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-es                                              
Obj [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                                                          
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Translation-es                                                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports Release.gpg                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es                                                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Translation-es                                                                  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                                                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                                          
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                                                                  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources                                                            
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                                                             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                                                              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                                                           
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                                                            
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/main Translation-es                                                        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-es                      
Des:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages [3094B]                
99% [Esperando las cabeceras] [Esperando las cabeceras] [Esperando las cabeceras]                            
[COLOR="Red"]gzip: stdin: not in gzip format
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                                              
  El subproceso gzip devolvió un código de error (1)
Des:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [/COLOR][27,6kB]                                                
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/restricted Translation-es       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages       
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/universe Translation-es
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-es
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release        
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                      
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Packages   
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/multiverse Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release                      
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports Release                    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Packages                        
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Packages                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Sources    
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/multiverse Sources
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages       
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Packages
Descargados 3095B en 2s (1035B/s)
[COLOR="Red"]W: Imposible obtener [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz)  El subproceso gzip devolvió un código de error (1)[/COLOR]

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.



Me tira esos 2 errores, y desde entonces no puede tener mis actualizaciones al dia, estoy bastante desesperado porque no encuentro info que me ayude.Ya desactive cada repo del archivos sources y probe, pero sigue apareciendo.

 me podrian dar una mano ? desde ya muchas gracias

---

### Post by faktorqm on 2008-10-01
Fijate lo que dice acá, es la pagina oficial de wine para ubuntu/debian.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
salu2!

---

