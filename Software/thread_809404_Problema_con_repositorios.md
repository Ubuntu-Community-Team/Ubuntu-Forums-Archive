---
title: "Problema con repositorios"
date: 2008-05-27
forum: Software
---

### Post by loopeando on 2008-05-27
Por alguna razon cuando quiero actualizar me aparece esto (ver al final): 

```
loop@loop-laptop:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/web Translation-en_US                      
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Hit http://archive.canonical.com hardy Release                                 
Ign http://wine.budgetdedicated.com hardy Release                              
Ign http://archive.ubuntu.com hardy-updates/web Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Hit http://archive.ubuntu.com hardy-security Release.gpg                       
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US            
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US      
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Ign http://archive.ubuntu.com hardy-security/web Translation-en_US             
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US      
Hit http://archive.ubuntu.com hardy-proposed Release.gpg                       
Ign http://archive.ubuntu.com hardy-proposed/restricted Translation-en_US      
Ign http://archive.ubuntu.com hardy-proposed/main Translation-en_US            
Ign http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_US      
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_US        
Hit http://archive.canonical.com hardy/partner Sources                         
Err http://wine.budgetdedicated.com hardy/main Packages                        
  404 Not Found [IP: 88.159.206.7 80]
Ign http://archive.ubuntu.com hardy-proposed/web Translation-en_US             
Hit http://archive.ubuntu.com hardy-backports Release.gpg       
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/web Translation-en_US
Hit http://archive.ubuntu.com hardy Release                     
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.ubuntu.com hardy-security Release                           
Hit http://archive.ubuntu.com hardy-proposed Release                           
Hit http://archive.ubuntu.com hardy-backports Release                          
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages         
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages 
Hit http://archive.ubuntu.com hardy-security/main Packages      
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages      
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://packages.medibuntu.org hardy/free Sources
Hit http://packages.medibuntu.org hardy/non-free Sources
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz  404 Not Found [IP: 88.159.206.7 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Probe sacando los repositorios manualmente en el sources.list y levantando un backup del mismo archivo y el problema persiste.

Estuve Googleando un poco y este error aparentemente pasa cuando se actualiza de Gutsy a Hardy y quedan repositorios de Gutsy colgados pero yo hice una instalacion limpia de Hardy.

¿Alguna idea de como puedo solucionar esto y poder actualizar?

Gracias!

EDIT: Encontre la solucion aca:[http://ph.ubuntuforums.com/showthread.php?t=692615](http://ph.ubuntuforums.com/showthread.php?t=692615)

---

### Post by AndreaSant on 2008-05-27
> **loopeando said:**
> Por alguna razon cuando quiero actualizar me aparece esto (ver al final): 

```
loop@loop-laptop:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/web Translation-en_US                      
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Hit http://archive.canonical.com hardy Release                                 
Ign http://wine.budgetdedicated.com hardy Release                              
Ign http://archive.ubuntu.com hardy-updates/web Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Hit http://archive.ubuntu.com hardy-security Release.gpg                       
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US            
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US      
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Ign http://archive.ubuntu.com hardy-security/web Translation-en_US             
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US      
Hit http://archive.ubuntu.com hardy-proposed Release.gpg                       
Ign http://archive.ubuntu.com hardy-proposed/restricted Translation-en_US      
Ign http://archive.ubuntu.com hardy-proposed/main Translation-en_US            
Ign http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_US      
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_US        
Hit http://archive.canonical.com hardy/partner Sources                         
Err http://wine.budgetdedicated.com hardy/main Packages                        
  404 Not Found [IP: 88.159.206.7 80]
Ign http://archive.ubuntu.com hardy-proposed/web Translation-en_US             
Hit http://archive.ubuntu.com hardy-backports Release.gpg       
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-backports/web Translation-en_US
Hit http://archive.ubuntu.com hardy Release                     
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.ubuntu.com hardy-security Release                           
Hit http://archive.ubuntu.com hardy-proposed Release                           
Hit http://archive.ubuntu.com hardy-backports Release                          
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages         
Hit http://archive.ubuntu.com hardy-updates/main Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages 
Hit http://archive.ubuntu.com hardy-security/main Packages      
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages      
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://packages.medibuntu.org hardy/free Sources
Hit http://packages.medibuntu.org hardy/non-free Sources
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz  404 Not Found [IP: 88.159.206.7 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Probe sacando los repositorios manualmente en el sources.list y levantando un backup del mismo archivo y el problema persiste.

Estuve Googleando un poco y este error aparentemente pasa cuando se actualiza de Gutsy a Hardy y quedan repositorios de Gutsy colgados pero yo hice una instalacion limpia de Hardy.

¿Alguna idea de como puedo solucionar esto y poder actualizar?

Gracias!

EDIT: Encontre la solucion aca:[http://ph.ubuntuforums.com/showthread.php?t=692615](http://ph.ubuntuforums.com/showthread.php?t=692615)

No sé si es lo mismo porque no entiendo inglés, pero a mí me aparecieron un par de veces los cartelitos de fallo al conectar o error al actualizar y cuando pedí ayuda al foro me dijeron que dejará pasar un rato o al otro día lo intentara,ya que esto se debía a que quizás en ese momento se estaba actualizando el paquete,espero te ayude Andrea

---

### Post by loopeando on 2008-05-28
Pensaba eso en un principio yo tambien pero habia un problema en mis repositorios.

No explican porque se soluciona pero lo que hay que hacer es sacar la opcion "web" de los repositorios.

---

### Post by AndreaSant on 2008-05-28
> **loopeando said:**
> Pensaba eso en un principio yo tambien pero habia un problema en mis repositorios.

No explican porque se soluciona pero lo que hay que hacer es sacar la opcion "web" de los repositorios.

Lamento no haberte sido útil,la próxima vez será.Andrea.

---

