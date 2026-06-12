---
title: "close terminal windows from within the bash script....how ???"
date: 2017-05-18
forum: Ubuntu/Debian BASED
---

### Post by gmcn on 2017-05-18
hi all, :) 

so i am new to the linux world and have been learning through scratch and by hit and miss scenarios from the resources available on the internet and youtube.. and i am trying to write a simple bash script....i searched the answer for this question and cannot seem to find a simple answer but only complicated technical arguments which are not helpful at all ..!!!

so my question is i am trying to write a bash script to update the system. 2 questions here..

1. how can i make a .sh bash script auto execute at the startup of the system ???

and now my script is 

#!/bin/sh
sudo apt-get update -y && apt-get dist-upgrade -y 
exit 

so when i do the "./update.sh" command the system updates and upgrades itself but the terminal window itself doesn't close....so my second question is what do i add to the above code to make it close the terminal window after the execution of the window...i even looked into the settings of the terminal where it says close the terminal after successful completion of the code..its no help... and i am on kali linux on vmware.

---

### Post by HermanAB on 2017-05-18
Put the script in rc.local

---

### Post by deadflowr on 2017-05-18
Thread moved to *Ubuntu/Debian Based*

---

### Post by gmcn on 2017-05-18
okay will look into researh what rc.local is and how to use it....thnk you!!!! any idea how to close the window after execution..??

---

