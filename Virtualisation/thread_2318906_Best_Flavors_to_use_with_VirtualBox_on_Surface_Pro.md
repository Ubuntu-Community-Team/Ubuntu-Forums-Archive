---
title: "Best Flavors to use with VirtualBox on Surface Pro 3"
date: 2016-03-30
forum: Virtualisation
---

### Post by wackzingo on 2016-03-30
I haven't used Ubuntu Desktop since version 12. I am starting my **C for System Programming** class and it is recommended that we use VirtualBox 5.0.* and Ubuntu 14.0.* or newer. I am using a Surface Pro 3 with I-5/4GB/128GB model so I am an worried that I might not have enough resources to run Ubuntu 15.0.* in a VM. I am strictly using this for the programming projects. I basically need to be able to run one of the decent editors and compile what should be fairly simple C projects. 

Will Ubuntu run fine with 1-2 GB of ram on my Surface Pro 3 for this purpose?
Should I go with a different flavor like Kubuntu or Xubuntu?

Again, this is primarily just for writing code in one of the editors like gedit and compiling fairly simple C programs. 

Thanks.

---

### Post by slickymaster on 2016-03-30
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by sudodus on 2016-03-30
I would suggest that you use ***Lubuntu***. It has the lightest desktop environment of the Ubuntu flavours, and it is needs the least amount of RAM.

---

### Post by MAFoElffen on 2016-03-31
Rule of thumb for running Virtual's is that you want to keep your VM allocated memory to less than half your Host's memory. (this is only a rule of thumb) Full-blown Ubuntu requires 1 GB, but will fly in 2 GB. Running gedit, gnome terminal and the compiler is not going to add much to your base system. Since you have 4 GB, you are fine to run any flavor of Ubuntu as a VM. When you build your VM, initially allocate 1 GB (with dynamic memory). After, edit your settings, to edit the upper end of your dynamic allocation to 2 GB.

> **wackzingo said:**
> Again, this is primarily just for writing code in one of the editors like gedit and compiling fairly simple C programs. 

As just my own curiosity. I have been a programmer who is back in school documenting my past experience ... I have a few questions for you:


Questions:
 - What version of Windows is on your Surface Pro? Win 10 Professional? (Can run Hyper-V as a feature, which would be less overhead than running VirtualBox)
 - A College course? (If DreamSpark is available to you... Which would give you access to "Win 10 Educational", which would also allow you to run Hyper-V...)
 - Pure C or C++?
 - Why in Linux?

Because the only reason I can think of off the top of my head, that a college would recommend that is for C++ and the GNU C++ compiler, and the basic experience of compiling via commandline (and follow-ons for Python). That is how I started with C and Assembler, but now-a-days...

---

### Post by wackzingo on 2016-03-31
> **MAFoElffen said:**
> 

As just my own curiosity. I have been a programmer who is back in school documenting my past experience ... I have a few questions for you:


Questions:
 - What version of Windows is on your Surface Pro? Win 10 Professional? (Can run Hyper-V as a feature, which would be less overhead than running VirtualBox)
 - A College course? (If DreamSpark is available to you... Which would give you access to "Win 10 Educational", which would also allow you to run Hyper-V...)
 - Pure C or C++?
 - Why in Linux?

Because the only reason I can think of off the top of my head, that a college would recommend that is for C++ and the GNU C++ compiler, and the basic experience of compiling via commandline (and follow-ons for Python). That is how I started with C and Assembler, but now-a-days...

Thanks for the info, it's much appreciated.

- I am using Windows 10 Professional. It came with it, so it wasn't an upgrade. I could run Hyper-V but I always fear something may run on my machine but not my professor so I try to use what they recommend. Maybe that fear is unfounded though.

- We have Dreamspark subscriptions available to us so I have access to all that.

- Pure C not C++

- I believe the professor said the primary reason is the open source nature of Linux we can look at code on the system. Not knowing what's ahead 
(only had class once so far) yet I'm not sure why that's important.

This is from the Syllabus:

**Programming Concepts Design and Tool Usage**
- Bit representations for numeric types, including two's complement and floating point format
- Arrays and Strings
- Pointers & Structures
- Input / Output: streams, pipes, files, devices
- System Calls
- Libraries
- Use of scripting languages (if time permits)

**Design and Tool usage**
- Virtual Machine
- Program organization using source and header files
- Common Unix shell commands
- gcc
- gdb
- Unix Text Editors

---

### Post by MAFoElffen on 2016-03-31
I've been working as a Student Tutor and now as a T.A. for the Computer Science courses since I started... Been fun. Funny how Professors ask me how things really work... LOL. I love C. But now busiest with C++, C# and Python. Just heped an instrructor rewrite his OOP Courses from Java into Python.

*** Whatever you do (whichever hypervisor you use to run your VM), there will be one common pre-cursor = Before anything, ensure that IOMMU vt-x is turned on in your BIOS. If you right-click your taskbar (<Cntrl><Alt<Del>) and open up the Task Manager. Click on Performance Tab and you should see that vitualization is already enabled (Should be on by default on Surface Pro's). If not, then turn it on in your BIOS Setup. Needs to be on to be able to install and run a 64-bit VM OS.

Yes, you could turn on Hyper-V (just by going to windows features and turning it on.) Yes, there may be slight differences in the instructions from your instructor. Very slight. I just converted a whole Networking class'es lab's from VirtualBox to Hyper-V... One note-- if you trun on Hyper-V, then Hyper-v takes over the IOMMU features of that machine... Meaning if hyper-V is turned on, then VirtualBox will say that the machine does not have IOMMU. If you turn it off,  then VitrualBox will magically see that same machine as IOMMU capable.

Hyper-V runs Ubuntu just fine. But so does VirtualBox. Your choice.

Source editing tip for gedit: On gedit-- good basic editor. once you name (Save As) your code file with program specific file extension,* then* it will context sensitive color-code your code. Pay attention to the colors and how they change. You will get used to what should be which color. If it does not change color as expected, trace it back to where the color codes are normal, then move down and look  for a syntax error.

Sounds like it's gong to be a good class.

---

