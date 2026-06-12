---
title: "[SOLVED] Install VMWARE Server console in 8.10"
date: 2008-12-28
forum: Virtualisation
---

### Post by thomasr on 2008-12-28
When I try to install the vmware server console, I get the following error:

In which directory do you want to install the library files? 
[/usr/lib/vmware-server-console] 

The path "/usr/lib/vmware-server-console" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

Unable to get the access rights of source file "./lib".

Execution aborted.

I only want to install the console.

Any help would be most appreciated.

Thanks in advance

---

### Post by Dedoimedo on 2008-12-28
Did you right the script as sudo?
Dedoimedo

---

### Post by thomasr on 2008-12-28
Yes - sudo su in terminal. Finally figured it out. Needed 
sudo ./vmware-install.pl
not
sudo /vmware-install.pl

---

