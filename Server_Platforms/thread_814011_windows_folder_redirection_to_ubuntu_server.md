---
title: "windows folder redirection to ubuntu server"
date: 2008-05-31
forum: Server Platforms
---

### Post by fouadk on 2008-05-31
hi everyone...

i was wondering if anyone has tried before to redirect folder from a windows active directory to an linux based server...

i am trying to do this but it fails when windows asks for a password....the username and password dont work even though i have created a samba user....

i have followed this guide [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
 to join my ubuntu server to the Active Directory...

i just cant authenticate from windows to linux...

please help...

thanks in advance

---

### Post by windependence on 2008-05-31
The user must exist on the Linux box and the passwords must be the same. Also, samba sharing must be turned on on the linux box. If you have a GUI, you should be able to right click on the folder on the Linux box and set up sharing.

-Tim

---

### Post by fouadk on 2008-06-01
thanks for your reply....

they should be smaba users ??? or regular users ?????

i have created smaba users.....

does the steps i followed in the tutorial(mentioned in my first post) affect anything ????

should i supply(in windows) the username as WORKGROUP\USERNAME or just USERNAME??? none of them work...

---

