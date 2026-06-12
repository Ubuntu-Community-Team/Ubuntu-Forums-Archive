---
title: "Vmware error message while opening any guest OSs !"
date: 2009-09-07
forum: Virtualisation
---

### Post by Wanas on 2009-09-07
When I try to open any Guest OS I got this message 
> Unable to change virtual machine power state: Cannot find a valid peer process to connect to.

I have tried to create a new guest OS but the same message appear :(

In the same day I have this message from VMware, Firefox & songbird is so slow in starting, starting in more than a full minute :( 

Is there a way to fix this two problems ?  

I am using ubuntu 9.04 
Vmware Workstation 6.5.2 build-156735 
Firefox 3.5.2 from the daily mozilla builds from the launchpad.com
Songbird the latest

---

### Post by darco on 2009-09-08
Try running this command to see if you have any instances of vmware running:

```
vmrun list
```

If you do have vm running the use the vmrun stop command to kill the vm.
Then retry vmware....

darco

---

### Post by Wanas on 2009-09-08
I got it solved
The problem was in installing Avira anti virus
After uninstalling the Avira Guard every thing came back to normal  
thanks darco for trying to Help me

---

