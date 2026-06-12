---
title: "ubuntu server problem"
date: 2009-07-05
forum: Server Platforms
---

### Post by aago1254 on 2009-07-05
Okay i have a hard drive problem okay here is the lay out  
 
i have the main drive that has the ubuntu server 9.04 os on it. and works fine able to file share with my local computers.   
 
but when it comes to my the 2nd drive i have it mounted and able to see it but im not able to write to it or have premission to do so. 
 
everything looks right i dont know if is should sudo chmod 777 the harddrive i think i tried but i dont know what to do at this point any help would be ahh great

---

### Post by aago1254 on 2009-07-07
cheers i got it thank you for the help here 
 
 
sudo chmod -R 777 media/store    was the only thing i needed i didnt need to set users and groups because its just a house file server.. hope this helps ya guys 
 
:guitar:

---

