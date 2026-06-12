---
title: "please help about vmware workstation 7"
date: 2010-05-01
forum: Virtualisation
---

### Post by pleasehelpme90 on 2010-05-01
hello all , thanks for reading and taking time to help me 

my problem is so weird and not common .i had downloaded vmware workstation 7 from there site 
i dont understand how to install it .the format is bundle and it's in the folder of download 
please tell me step by step 

i will tell you what i did
first i had open the terminal then i type dir / Download then it came with ...

Downloads:

VMware-Workstation-Full-7.0.1-227600.i386.bundle

ok now i did this 
sudo: ./VMware-Workstation-Full-7.0.1-227600.i386.bundle

then he want from me the password and i typed it 

what happen here is he told me : sudo: ./VMware-Workstation-Full-7.0.1-227600.i386.bundle: command not found
??? why 

thanks

---

### Post by dcstar on 2010-05-02
> **pleasehelpme90 said:**
> 
.........
what happen here is he told me : sudo: ./VMware-Workstation-Full-7.0.1-227600.i386.bundle: command not found
??? why 

thanks

Either the file is not executable or you have a 32-bit file and a 64-bit system.

---

### Post by josephinesbed on 2010-05-02
I was having the same issue until I used the following code:

sudo ./VMware-Workstation-Full-7.0.1-227600.i386.bundle

After that, it worked perfectly. So, try removing the : after *sudo* and see if it works for you also.    Hope this helps.

---

### Post by fjgaude on 2010-05-02
Say, make sure you are in the folder when the .bundle file is.

---

