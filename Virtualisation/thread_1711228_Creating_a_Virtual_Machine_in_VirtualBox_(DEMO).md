---
title: "Creating a Virtual Machine in VirtualBox (DEMO)"
date: 2011-03-21
forum: Virtualisation
---

### Post by varunendra on 2011-03-21
============================================================
This is a simple demo for those who are interested in, but have no experience of virtualization.

For a more detailed info, use "Virtualization Megathread" instead: [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)
============================================================


A couple of weeks ago (before returning to this forum after a long gap), I composed an email to my friends demonstrating how to create a virtual machine in virtualbox. The original target was to emulate a three-machine network scenario on a relatively low configuration hardware to solve the purpose of practicing networking configurations + related commands on a single, low configuration laptop / PC.

I chose Linux Mint (lxde) as host, and DSL + Win Server 2003 as two different guests on an old Compaq Presario 2100 laptop (P4 2GHz, 512 MB RAM, 30 GB HDD).

**_WHY DSL in this Demo_?**
Running a live CD or installing an OS on any virtual machine consists of similar steps upto the loading of the OS or startup of installation. Beyond that, the steps would be same as they are on a physical machine. However, being a minimal desktop OS, DSL experienced some trouble with pointer after being loaded. The solution involved turning off a default feature. So I thought I should share that.


**_Before we start_ :**
This demo was performed on Win XP (to make it look familiar to my 'linux-scared' friends), however, the final implementation on Linux Mint went exactly same way. So don't mind the XP looks in some of the screenshots.


**_So here we go_:**

First, install Virtualbox (preferably PUEL edition, as it has the advantage of being able to use USB devices) from either repositories (default ubuntu repository contains only OSE version, not PUEL), or from here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


Now, assuming you already have VirtualBox installed, here's how to create a  minimal Virtual machine to try (or to permanently install) DSL upon.

1) Open VirtualBox, and click "New":
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx1.jpg[/IMG]


2) In the subsequent windows, just click "Next" > "Next" until you get this window :-
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx3.jpg[/IMG]


3) As displayed above, give a name of your choice to the Virtual Machine you are creating.
4) In "Operating System", select "Linux"
5) In "Version", select "Other Linux"
6) Click "Next"


7)  In the next window, select the amount of RAM you want to dedicate to  this Virtual Machine (use the slider or type in the box) :-
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx4.jpg[/IMG]
(note that even 16MB of memory is sufficient for DSL, however, at least 64 MB is recommended for maximum performance)

8.) Click "Next"


9) In the next three windows, it is okay to accept the default options. So just click next,
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx5.jpg[/IMG]


10) Next
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx6.jpg[/IMG]


11) Next
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx7.jpg[/IMG]


12) In the "Virtual Disk Location and Size" window, choose the size of Virtual hard disk (it will actually be a "**.vdi**" file on your hard disk, seen by the virtual machine as a Hard disk.)

Note that since you have selected "Dynamically expanding storage" in the  above step, the initial size of this file (i.e., hard disk - for the  Virtual Machine) would be "ZERO". It will expand in size as you start  copying files to it, and the max. size would be as much as you define in  this step :-
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx8.jpg[/IMG]


13) Click Next,
14) Click "Finish".
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx9.jpg[/IMG]

(continued in next post due to no. of image restrictions....)

---

### Post by varunendra on 2011-03-21
15) Click "Finish" once more to finish creating the virtual Machine.


16) Now your newly created Virtual machine will show up in the  Virtual  Machine's list in the left pane of VirtualBox Manager window. At  this  stage, this Virtual Machine is like a computer which has all the   hardware, but no OS yet. So let us provide OS to it, which is the Live   DSL CD image in this case.

In the right hand pane, all the "virtual" hardware of this machine is listed. Locate "Storage" link and click it.
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx10.jpg[/IMG]


17) Click the CD icon (shown as single disk)
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx11.jpg[/IMG]

18.) Click on "Browse" icon

19) Select "Choose a virtual CD/DVD disk file...."


20) Browse to the downloaded "iso" image of DSL ("DSL-4.4.10.iso" in this case), select it, click "Open"
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx12.jpg[/IMG]



21) Click "Ok" in the next window.

22) Now the selected image should appear in the "Storage" list of the selected VM (virtual Machine) :-
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx13.jpg[/IMG]


23) While the machine is selected, click on "Start" button as shown above.


24) The forthcoming window would appear something like this :-
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx14.jpg[/IMG]


25) If you don't want to wait for timeout before the auto booting   starts, simply click inside the running OS window and hit "Enter"
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx15.jpg[/IMG]

In the meanwhile, since you are running a Virtual Machine for the first   time, VirtualBox will show up several annoying messages providing   various info. Just read the info (for your own good!) and close them.   You have the option to check a check-box in all these messages that says  something like  - "Do not show this message again".


26) DSL loading screen :
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx16.jpg[/IMG]


27) Final Screen:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx17.jpg[/IMG]

(continued in next post due to no. of image restrictions....)

---

### Post by varunendra on 2011-03-21
28.)  Now, since DSL is a Non-standard (as for VirtualBox) distribution of   Linux, a very good feature "Mouse Integration" will actually cause some   trouble here. That is, the Virtual Window will be unable to capture   your mouse so that you can't use your mouse to control the pointer   "inside" the virtual window.
  
  Fortunately, the solution is quite simple. Just follow the following snap :-
  [IMG]http://i621.photobucket.com/albums/tt292/varunjnp/VBx18.jpg[/IMG]
  
  
  As stated above, your mouse will now be "captured" by the virtual window   as soon as you click inside it. It means, you will now be able to   control the pointer appearing inside, but can not move it outside to   return to your "host" system (the actual one running in the background,   on which, the VirtualBox itself is running).
  
  In order to release the mouse, you will have to press "Right Ctrl" key. So simple !
  
  If  you want to enjoy the full-screen experience, just press "Right Ctrl  +  F" keys simultaneously. Press the same combination again to return  from  full-screen mode.
  
  [B][U]
This is The End of this guide[/U].[/B]
  
  If you wish to install a full-fledged OS in a virtual machine, the steps  would be similar from steps-1 to 22, only the OS-specific settings  would be changed (type, version selection, amount of RAM, HDD size,....  etc.)
  
  Hope this helps those who want to try virtualbox, but are hesitating for  some reason. Please notify me of any errors I may have made during  creation of this post.
  
  Thank you.

---

