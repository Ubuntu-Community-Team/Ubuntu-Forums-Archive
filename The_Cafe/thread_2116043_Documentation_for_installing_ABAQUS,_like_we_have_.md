---
title: "Documentation for installing ABAQUS, like we have for MATLAB"
date: 2013-02-14
forum: The Cafe
---

### Post by sbnwl on 2013-02-14
I am posting this after having a long time wish for installation support, though unofficially, for some University must have type softwares.

The idea comes right after one visits [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) 

For a newcomer, who migrates to Ubuntu (or say linux),  just goes smoothly with MATLAB in terms of installation and working with MATALB within 15 minutes so easily, like I did after visiting[* MATLAB* - Community *Ubuntu* Documentation]("http://www.google.co.in/url?sa=t&rct=j&q=matlab+ubuntu&source=web&cd=1&cad=rja&ved=0CC4QFjAA&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FMATLAB&ei=HUsdUfeyNcirrAfym4CwCg&usg=AFQjCNEXmXp-ytiwdfvHPUVdmvYSHoke_w&bvm=bv.42452523,d.bmk") recently.

I have successfully installed and used ABAQUS 6.7 and ABAQUS 6.11 (for linux x86_64 platforms) on all the versions of Ubuntu 7.10 to Ubuntu 11.10 (also on FEDORA 8), with all the functionality like:

1. Thread level Parallelization using HP-MPI (Free Available) 
2. User Subroutines (UMAT) using Ubuntu native g77 compiler (Open Source) instead of Intel gFortran compiler (Propitiatory Stuff). You need basically a change in environment file (abaqus_v6.env) file for this effect.
3. Using GNU C compiler (gcc) instead of Intel C++ Compiler.
And one friend of mine even used python scripts in ABAQUS from linux box.

Like wise there may be ANSYS which is also available for linux platforms.

So how about having a community documentation like:

1.[* MATLAB* - Community *Ubuntu* Documentation]("http://www.google.co.in/url?sa=t&rct=j&q=matlab+ubuntu&source=web&cd=1&cad=rja&ved=0CC4QFjAA&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FMATLAB&ei=HUsdUfeyNcirrAfym4CwCg&usg=AFQjCNEXmXp-ytiwdfvHPUVdmvYSHoke_w&bvm=bv.42452523,d.bmk")
2. [I]ABAQUS - Community Ubuntu Documentation
3. ANSYS - Community Ubuntu Documentation

And you people can suggest few more, which could be so useful to set roots in universities.

I would here like to mention my own observations while working with ABAQUS solver, on WINDOWS as well as LINUX (both 64 bit) Platforms on same machine in doul boot, that 
"The same problem was submitted on both platforms and the solution was completed within 36 hours on LINUX as compared to 67 hours on WINDOWS platform"

[/I]I checked with few more contact interaction problems and the result was the same.

So having such Community Ubuntu Documentation pages, in my opinion, will be a great idea for Ubuntu and all open source fans.

---

