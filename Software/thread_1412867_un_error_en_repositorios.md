---
title: "un error en repositorios"
date: 2010-02-21
forum: Software
---

### Post by zhelo on 2010-02-21
que es lo que sale al final(lo de rojo?
> 
zhelo@zhelo-laptop:~$ sudo aptitude update
[sudo] password for zhelo: 
Escribiendo información de estado extendido... Hecho
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic Release.gpg
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/main Translation-es                     
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/restricted Translation-es               
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-es              
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/universe Translation-es                 
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/multiverse Translation-es               
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-es                  
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates Release.gpg                     
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-es        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-es          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-es        
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                          
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/main Translation-es             
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/restricted Translation-es       
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/universe Translation-es         
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                 
Des:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-es                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-es              
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/multiverse Translation-es       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                               
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic Release                                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                    
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates Release                         
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                        
Des:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11,7kB]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                              
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/main Packages                           
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                         
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/restricted Packages                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                     
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources               
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/restricted Sources                      
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                         
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                        
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/main Sources                            
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/multiverse Sources                      
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages              
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/universe Sources                        
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                    
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/universe Packages                       
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic/multiverse Packages
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/main Packages
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/restricted Packages
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/restricted Sources
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/main Sources
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/multiverse Sources
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/universe Sources
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/universe Packages
Obj [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) karmic-updates/multiverse Packages
Descargados 198B en 2s (90B/s).                         
Leyendo lista de paquetes... Hecho                   
[COLOR=Red]W: Error de GPG: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2EBC26B60C5A2783[/COLOR]

---

### Post by x_jefesin_x on 2010-02-21
Supongo que agregaste un repositorio ( de medibuntu para ser mas esacto ) sin agregar su llave pública...

Si es asi corre en consola esto

> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783 

Saludos:)

---

### Post by radixs on 2010-02-22
yo la se de otra forma

UPS, perdón lo estaba haciendo de otra forma, que en si era lo mismo

Apoyo lo de x_jefesin_x[COLOR=Black] [/COLOR]+1

---

### Post by zhelo on 2010-02-22
gracias funciono :D

---

