---
title: "AutoCAD on Wine"
date: 2010-07-20
forum: Wine
---

### Post by Iyke on 2010-07-20
I have unsuccessfully tried to install AutoCAD on wine! i need help ASAP!

---

### Post by drs305 on 2010-07-22
Moved to Wine forum.

---

### Post by _h_ on 2010-07-22
Could you maybe provide us with a little more information? Maybe posting on why it was unsuccessful, like error messages etc...?

---

### Post by asdfoo on 2010-07-22
make sure you have wine-1.2, check the AppDB too.

---

### Post by m_A_taha2007 on 2010-08-01
i am so intristed for autocad install in ubuntu 
yesterday i install wine 1.2 on ubuntu 10.04
i try to install autocad 2007
but i can not i have an error massege
SO I TRY TO INSTALL AUTOCAD 2008
BUT I HAVE AN ERROR MASSAGE AGAIN
I INSTALL NET FARME WORK 2
AND RE TRY TO INSTALL AUTOCAD 2008
IT INSTALL TO THE END BUT DO NOT WORK
PLS HELP ME

---

### Post by ronnielsen1 on 2010-08-01
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9306](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9306)
> The problem was always with AutoCAD using the. NET Framework 2.0 to operate, and how language is fairly new, providing such support is not easy, but with the effort of the group have managed to make Wine. NET is installed and running on Linux. 
        
 To install, the program must be downloaded and then using winetricks select dotnet2.0 and MSXML3.                                                                                                                                                  

    Finally, install any other AutoCAD 2008 software.                                                                                                                                                  
    
 wget [www.kegel.com]("http://www.kegel.com") / wine / winetricks                                                                                                                                                  
    
 sh winetricks                                                                                                                                                  
    
 Select dotnet2.0 and MSXML3.                                                                                                                                                  
    
 Install Autocad 2008 ...                                                                                                                                                  
    
 Done! 


There's more directions at that site

---

