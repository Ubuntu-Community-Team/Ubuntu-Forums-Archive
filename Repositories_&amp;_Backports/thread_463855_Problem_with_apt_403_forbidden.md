---
title: "Problem with apt: 403 forbidden"
date: 2007-06-04
forum: Repositories &amp; Backports
---

### Post by Rapy on 2007-06-04
Hello, I have a serious problem since 3 days...I cannot use apt because of a 403 forbidden error...I tried to change the conf of sources.list and I tried to update apt but the same error is still there...I think it's a problem of autentication permission of whatever else, but I'm a newbie and I dont know what can be...

---

### Post by dfreer on 2007-06-04
can you post your /etc/apt/sources.list file please? Also, the output of the command:
```
sudo apt-get update
```

---

### Post by Rapy on 2007-06-04
sources.list
> 
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy universe
## deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
## deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Result of apt update:
> Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                   
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty Release.gpg                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-it                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-it             
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Translation-it              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-it                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-it                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-it       
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Translation-it                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-it       
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates Release.gpg                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-it               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-it         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/multiverse Translation-it      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-it         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/universe Translation-it        
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty Release                                
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/multiverse Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/universe Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
  403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Packages                    
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
  403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Packages                      
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
  403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/multiverse Packages            
  403 Forbidden
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
  403 Forbidden
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/universe Packages              
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                              
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources   
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources 
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
  403 Forbidden
Impossibile ottenere [http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.gz)  403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  403 Forbidden
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  403 Forbidden
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  403 Forbidden
Lettura della lista dei pacchetti in corso... Fatto
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.


---

