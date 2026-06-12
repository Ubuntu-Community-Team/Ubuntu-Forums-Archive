---
title: "Looking for software virtualization application (Not Wine, Not VM)"
date: 2008-11-16
forum: Virtualisation
---

### Post by lovinglinux on 2008-11-16
As the title says, I'm not looking for compatibility layer applications like Wine or virtual machine applications like VMWare or VirtualBox. I'm looking for a software virtualization application for Linux, like Altiris SVS for Windows.

I guess some explanation is necessary.

When you install a new software using Altiris interface it captures all file and registry operations during install and put them on virtual layer. These files are physically stored in a special folder outside the system folders. Every time you activate the application layer, Altiris temporarily add those files and modifications to the system paths, fooling Windows to believe that the software is actually installed. It relies on virtual links to the physical paths, like Windows Vista does with some files. So I guess they are similar to simlynks.

Any file or registry operations performed while running the virtualized software are kept inside the virtual layer and are deleted if you remove the layer. Once the layer is removed, no traces of the virtualized software is left behind. So basically, Altiris is a Sandbox that can prevent dll incompatibilities, prevent malware infections and also provide the ability to run different versions of the same application on a single machine without messing with system files.

For example, if I want to try Firefox 3 without modifying the current installation which is Firefox 2, I have to create a layer for the Firefox 3 installation executable. Then when I activate Firefox 3 layer and open Firefox installation folder under "C:\Program Files\" all files related to Firefox 3 will be there. Those files that are common between the two versions will appear to be overwritten by Firefox 3 files. But when deactivate the layer, all files related to Firefox 3 disappear and the ones related to Firefox 2 will be displayed. If I do this while browsing the Firefox installation folder I can actually see files being added/replaced and disappearing while I activate/deactivate the layer.

Continuing from the example above, If I download a file while using the Firefox 3 layer and save it for example under "My Documents", this file will also be physically stored outside "C:\Documents and Settings\" but it will appear to be there. When I deactivate the layer, this file will also disappear from "My Documents" folder. If I want to keep files downloaded by Firefox 3 I must create an exception for a specific folder or drive. For example, if I store all my downloads under "C:\Downloads" I can add this path to the exception list, so all files saved there will be physically saved there and will not disappear when I deactivate or delete the Firefox 3 layer.

Altiris also has the ability to use a snapshot like VirtualBox. For example, let's assume that I decided to install a Firefox update that completely screwed with my Firefox 3 installation. All I have to do is reset the layer, so it will revert all changes made after the installation with the fresh install state. 

But let's assume that I want to keep my bookmarks that I added after installation.

Altiris SVS can also make some changes in the layer permanent. When you install a software layer it creates two types of layers, one unwritable and other writable. The first one is the fresh install snapshot and the other is where it will save all modifications and files downloaded after the installation of the software. So, if I want to make for example my Firefox profile to be permanently incorporated into the main layer, I can move the files from the writable layer into the unwritable layer (using Altiris manager), so whenever I reset the application layer, my profile won't be deleted.

If I want to have a backup of the current state (snapshot), all I have to do is export the layer to a svs package, which is basically a compressed file containing all the application files and registry modifications. This package acts like a snapshot. If I want to restore it, all I have to do is remove (delete) the current layer and import the svs package to a new layer. If I need to format my drive e re-install Windows, then all I have to do to get Firefox 3 running again with all my settings is importing this svs package.

So, Altiris SVS is called a **S**oftware **V**irtualization **S**ystem. It can be used to test software from untrusted sources, to test new versions of softwares without overwriting or conflicting with the current installed version, to restore a software to a fresh install state, to distribute software that can be easily deployed on several machines (with customizations included or not), to restore applications with customizations already included and to avoid system wide infections.

Well, I used Altiris on Windows and I simply loved it. So I'm wondering if I could find a similar application for Linux?

---

