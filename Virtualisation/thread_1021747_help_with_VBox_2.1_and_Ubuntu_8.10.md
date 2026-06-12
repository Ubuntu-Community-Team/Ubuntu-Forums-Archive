---
title: "help with VBox 2.1 and Ubuntu 8.10"
date: 2008-12-25
forum: Virtualisation
---

### Post by Bigfoot009 on 2008-12-25
I'm running Ubuntu 8.1 and Virtualbox 2.1 and I wanted to know if it's possible to access my external hard drive on my VM. I also got an error 


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {f39438d7-abfd-409b-bc80-5f5291d92897}
Callee: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}


any help would be greatly appreciated.

---

### Post by albinootje on 2008-12-25
> **Bigfoot009 said:**
> I'm running Ubuntu 8.1 and Virtualbox 2.1 and I wanted to know if it's possible to access my external hard drive on my VM. I also got an error 

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


You can solve that annoying problem as following,
read the section about USB all the way down at this page :
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

And a perhaps easier solution that I'm using at work, is to make the /media folder from Ubuntu visible through "shared folders" in the guest OS.

---

### Post by bodhi.zazen on 2008-12-26
Or you can use shared folders or a network protocol such as Samba.

---

