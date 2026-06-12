---
title: "vmware workstation reinstall"
date: 2008-04-06
forum: Virtualisation
---

### Post by Matt26 on 2008-04-06
i'm trying to re-install vmware workstation 6 (same versions that i had installed previously) based on this article i found when i first installed it:

[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

since part 1 and part 3 (part 2 doesn't apply to me) under the tarball installation have already been completed from my first installation (nothing was changed since that time) i would assume that running the install script from part 4 should run smoothly. but instead i get an error message in the terminal window stating no such file or directory- even if i try executing the script directly from the folder... and the syntax i am using is correct since i am copying/pasting directly from the instructions.  i have even tried deleting the vmware-distrib folder to Trash and extracting the folder again but i still get the same message about no such file or directory... it was suggested in another post that when workstation was uninstalled before that it may not have been completely removed and there may still be traces of the install left behind- either way, i'm stuck and i can't figure out how to reinstall workstation at this point...

any suggestions would be greatly appreciated.

---

### Post by fjgaude on 2008-04-06
The only experience I've had with this is trying to install the Server after having installed the Player and then removing it. I had to completely removed everything associated with Player before I could and did install Server.

I used Synaptic to do the final removing, searched for vmware, and then clicked on Mark for Complete Removal. That permitted me to install Server.

Workstation may be different, but likely not.

Let us know how you are doing.

---

### Post by Matt26 on 2008-04-06
thanks i will keep searching... any idea what the file gcc-3.4 would represent?  i noticed that this file is included in the command for executing the vmware-install.pl command in part 4 of the instructions- do you know what the command 'export CC=/usr/bin/gcc-3.4' does?  i see that the file still exists in the /usr/bin directory and i am wondering if i should try deleting the file to see if this will allow workstation to install, but i don't know if i will make things worse by doing this.

---

### Post by fjgaude on 2008-04-06
I don't know what EXPORT does but you do not want to remove the gcc, for that is the compiler, very much needed.

Just use Synaptic to do as I suggested.

---

### Post by Matt26 on 2008-04-06
good to know thanks.. i tried using synaptic but the only listings it has are for vmware server, none of which are checked to indicate that they  can be removed, so i'm not sure what i can do there...

---

### Post by fjgaude on 2008-04-06
Okay, I get it... Synaptic doesn't know Workstation was even installed.

I don't know what to suggest other than do a Google and keep your fingers crossed.

---

