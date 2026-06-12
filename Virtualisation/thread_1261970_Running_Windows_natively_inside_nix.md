---
title: "Running Windows natively inside *nix"
date: 2009-09-09
forum: Virtualisation
---

### Post by anystupidname1 on 2009-09-09
For the sake of discussion / argument, what would it take to be able to run windows natively inside linux similar to how andLinux / coLinux run inside Winders? Would Microsoft have to go open source? Please enlighten me.

---

### Post by mrfelker on 2009-09-09
> **anystupidname1 said:**
> For the sake of discussion / argument, what would it take to be able to run windows natively inside linux similar to how andLinux / coLinux run inside Winders? Would Microsoft have to go open source? Please enlighten me.
Not sure what you mean by "natively".  

1)  You can run Windows Applications (not the OS) directly from a Linux desktop using Wine or Crissiver Linux (try wine-doors also).  

2)  I guess the closest thing to running Windows "natively" on  Linux is to use Xen virtualization.  This I haven't tried yet because it is a new concept for me.  

This is a great site for many aspects of virtualization.

[http://www.virtuatopia.com/index.php/Main_Page](http://www.virtuatopia.com/index.php/Main_Page)

Other desktop and server virtualization solution are from VMwaer.  Like some others heremyself am trying to setup Unbutu on Hyper-V (with sysnthetic drivers_ but this is another thread.

3)  I guess the easiste way to run Windows on Linux is to use a dual boot setup.  So why do want to virtualize Windows??

<artu

---

### Post by anystupidname1 on 2009-09-09
> **mrfelker said:**
> Not sure what you mean by "natively".  

1)  You can run Windows Applications (not the OS) directly from a Linux desktop using Wine or Crissiver Linux (try wine-doors also).  

2)  I guess the closest thing to running Windows "natively" on  Linux is to use Xen virtualization.  This I haven't tried yet because it is a new concept for me.  

This is a great site for many aspects of virtualization.

[http://www.virtuatopia.com/index.php/Main_Page](http://www.virtuatopia.com/index.php/Main_Page)

Other desktop and server virtualization solution are from VMwaer.  Like some others heremyself am trying to setup Unbutu on Hyper-V (with sysnthetic drivers_ but this is another thread.

3)  I guess the easiste way to run Windows on Linux is to use a dual boot setup.  So why do want to virtualize Windows??

<artu

1) yes, this is useful for running Internet Explorer and stuff.
2) I specifically said "natively" because running Windows virtually isn't what I am asking about.
3) I usually run a dual boot box with the ability to run the Windows partition virtually within the *nix host. The point of this question was to find out what OTHER possibilities exist. Since Vista and Win7 don't have manual hardware profiles anymore, this option may no longer be an option until something finds a way to do it as well...

---

### Post by dcstar on 2009-09-10
> **anystupidname1 said:**
> 1) yes, this is useful for running Internet Explorer and stuff.
2) I specifically said "natively" because running Windows virtually isn't what I am asking about.
3) I usually run a dual boot box with the ability to run the Windows partition virtually within the *nix host. The point of this question was to find out what OTHER possibilities exist. Since Vista and Win7 don't have manual hardware profiles anymore, this option may no longer be an option until something finds a way to do it as well...

PC hardware will only run one OS at a time because all resources must be controlled by a single OS to ensure correct operation.

You then use additional software to emulate another OS or provide a virtual hardware environment(s) for another OS.

---

