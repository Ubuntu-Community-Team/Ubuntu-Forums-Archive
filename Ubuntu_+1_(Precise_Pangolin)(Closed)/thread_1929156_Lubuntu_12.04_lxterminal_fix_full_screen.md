---
title: "Lubuntu 12.04 lxterminal fix full screen"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nm_geo on 2012-02-21
For those of you that have asked for the lxterminal to not open in full screen.
Julien Lavergne has provided a solution. 
 
> I already reverted it. If you still have it by default, remove in your
configuration file (~/.config/openbox/lubuntu-rc.xml) the lines below :
 
<!-- Option to maximize all normal window when launched-->
<application type="normal">
<maximized>true</maximized>
</application>
 

 
I saved a backup of my lubuntu-rc.xml before making the changes just in case. Good news the lxterminal opened right in the center and much smaller window. I have not made a new/fresh install since I made the changes, but it is probably fixed in the current dailys too. Will see about a new install later today.
 
:)

---

### Post by paul_in_london on 2012-02-21
> **nm_geo said:**
> For those of you that have asked for the lxterminal to not open in full screen.
Julien Lavergne has provided a solution. 
 

 
I saved a backup of my lubuntu-rc.xml before making the changes just in case. Good news the lxterminal opened right in the center and much smaller window. I have not made a new/fresh install since I made the changes, but it is probably fixed in the current dailys too. Will see about a new install later today.
 
:)

This did the trick. Thanks very much. :)

---

### Post by nm_geo on 2012-02-21
> **paul_in_london said:**
> This did the trick. Thanks very much. :)

Fresh install today has the lxterminal starting in smaller window now. One more down.. :D

---

