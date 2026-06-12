---
title: "Issue with adding KVM Images to UEC."
date: 2010-10-18
forum: Ubuntu Cloud and Juju
---

### Post by hariv on 2010-10-18
Hi,
 
We are facing issue with adding a KVM images (.qcow2 file) to the UEC. Is it possible ?
 
 
 
We are also receiving an error message on slecting the image store Tab.
 
"Error 7: Could not connect to host"
 
Our setup has 2 machines of which one is acting as a CC and other as node controller.
 
Please help :(

---

### Post by kim0 on 2010-10-18
Perhaps read the "Registering with Eucalyptus" section of
[http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-4-%E2%80%93-image%C2%A0management/](http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-4-%E2%80%93-image%C2%A0management/)

For your second problem, I think your CC needs to have Internet access, does it ?

---

### Post by hariv on 2010-10-18
Thanks for the update. Will try that and let you know.
 
Thanks,
Hari

---

### Post by Rusty au Lait on 2010-10-18
hariv,
I am curious. Why do you want to create an instance with a virtual layer built into it? My interest started with system administrator. I have not created an instance for myself yet and adding other virtual constructs seems to be an added burden.

kim0,
I believe the CLC is the only aC (NC, CC, WC, etC. hehe :)) that needs access to the outside by an instance user or admin.

---

