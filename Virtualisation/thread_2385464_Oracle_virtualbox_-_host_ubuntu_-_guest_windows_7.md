---
title: "Oracle virtualbox - host ubuntu - guest windows 7"
date: 2018-02-20
forum: Virtualisation
---

### Post by AnupamMitra on 2018-02-20
My OS is Ubuntu 16.04 64 bit. Earlier inserted Pen Drive was visible in Guest Windows 7. But at present it is not visible. How to resolve?

---

### Post by QIII on 2018-02-20
Moved to Virtualisation as a more appropriate fit.

---

### Post by ajgreeny on 2018-02-20
What do you mean by "Earlier inserted Pen Drive was visible in Guest Windows 7"?

How long ago was it that the USBs worked and were visible?
What changes have you made?
Have you recently updated the VBox version but not yet also updated the Guest Additions?

---

### Post by AnupamMitra on 2018-02-22
> **ajgreeny said:**
> What do you mean by "Earlier inserted Pen Drive was visible in Guest Windows 7"?

How long ago was it that the USBs worked and were visible?
What changes have you made?
Have you recently updated the VBox version but not yet also updated the Guest Additions?

Thanks for the reply. In the last week of January 2018, VBox version was updated. But on earlier occasions I never updated the Guest Additions at my own. I only opted for update whenever I was asked to do so. However, presently the Virtual Box Version is 5.2.6 r120293 (Qt5.6.1) & Guest Addition version is also same i.e. 5.2.6 r120293.

---

### Post by AnupamMitra on 2018-04-19
Since last two months the above issue was hanging . However it could be solved today by simply adding my[FONT=Liberation Serif][SIZE=3]user name to the 'vboxusers' group with this command: 

[/SIZE][/FONT] [FONT=Times New Roman][SIZE=3][FONT=Liberation Serif]**sudo adduser $USER vboxusers** . 

Thereafter Logout and Login. Interested persons can check the details in the given link. 
[/FONT][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3][[FONT=Liberation Serif]https://help.ubuntu.com/community/VirtualBox/USB[/FONT]]("https://help.ubuntu.com/community/VirtualBox/USB")[/SIZE][/FONT]
  [FONT=Times New Roman][SIZE=3][FONT=Liberation Serif] 
[/FONT][/SIZE][/FONT]

---

### Post by wildmanne39 on 2018-04-19
Thanks for posting your solution as I am sure it will benefit other users.

---

