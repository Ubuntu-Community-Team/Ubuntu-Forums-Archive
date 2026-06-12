---
title: "err:module:map_image please help"
date: 2009-12-14
forum: Wine
---

### Post by asmith20002 on 2009-12-14
Hi, 
 
I've been searching for this and I couldn't find a solution.  
 
I have Ubuntu Hardy and I've installed wine with:  
sudo aptitude install wine 
 
During installation I received a notice about userspace suspend support and I have to reconfigure my kernel to set it and recompile kernel after that. 
 
I ignored that and did nothing about it and my wine seems to be working fine.  
I have this program, CMP image converter that I'm trying to use wine on it. 
Command is like this:  
 
wine converter.exe pathToImage 
 
When the program tries to convert I get this 4 times: 
       
               
>  err:module:map_image Could not map section .text, file probably truncated      
 
I never added any libraries to the wine. I simply used the install command and that was all. ( I'm noob on wine and Linux, so I don't know how to install any add-ons for wine) 
 
How can I get pass this error? 
Thanks for your time

---

