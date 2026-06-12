---
title: "Synaptic Segmentation fault"
date: 2004-12-16
forum: Repositories &amp; Backports
---

### Post by ibs on 2004-12-16
I get this Segmentation fault error when i try to run Synaptic or apt-get. I tried to restart but the problem is still there.

---

### Post by ibs on 2004-12-16
I think the problem is solved :) I had wrong repositories in the config file.

---

### Post by Huzudra on 2008-01-05
i'm having the same error now, can you outline what you did to fix it?

---

### Post by warmotor on 2008-09-02
I ran 

sudo apt-get update

from the terminal and it fixed this problem

---

### Post by Huzudra on 2008-09-03
> **warmotor said:**
> I ran 

sudo apt-get update

from the terminal and it fixed this problem

thanks, i'll keep that in mind should it happen again.

i think my original problem was bad ram or bad hardware, i havent had the same problem since and i'm using different ram and a different cpu i think.

---

### Post by artistgay on 2008-09-10
yesterday it still worked today, deluge and synaptics as well as some other programs dont work anymore. Itried:
#tom@tom-desktop:~$ sudo apt-get update
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release.gpg
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Translation-de       
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-de  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Translation-de  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Translation-de    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Translation-de  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release.gpg        
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Translation-de 
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Translation-de
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Translation-de
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-de
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-de
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release             
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release                    
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release                        
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                   
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Packages              
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Packages        
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Sources               
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Sources         
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Packages          
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources        
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Sources           
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Packages        
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Sources         
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Packages      
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Sources       
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Sources 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages   
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources    
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Packages  
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Sources
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Packages
OK   [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Sources
Paketlisten werden gelesen... Fertig

But the problem persists

---

