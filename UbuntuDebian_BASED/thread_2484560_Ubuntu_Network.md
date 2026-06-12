---
title: "Ubuntu Network"
date: 2023-03-02
forum: Ubuntu/Debian BASED
---

### Post by cybervulcan on 2023-03-02
I have Zorin OS Linux 16.2 running on both my desktop and laptop I have setup a network share on my desktop It is seen on the laptop but when I try to access it I get " Failed to retrieve share list from server Access Denied" any ideas would be appreciated.  I am not sure what the correct sub Forum is please assist

---

### Post by yancek on 2023-03-03
The error means the user on the laptop does not have permission to access files on the desktop so whatever configuration was done on the desktop needs to allow the laptop user permission on the desktopo. How (what software) did you  use to set up the network share?  I've only used nfs (network file system) so don't know that I can help.

---

### Post by cybervulcan on 2023-03-04
I have only auto configured Samba when Zorin auto installed the support files

---

### Post by yancek on 2023-03-05
>  I have only auto configured Samba when Zorin auto installed the support files 		

I don't know what that means in relation to your problem.  Your Desktop is not set to correcxtly allow a user from the laptop access.  As I've never used Samba, I have no idea how or what you would change.

---

