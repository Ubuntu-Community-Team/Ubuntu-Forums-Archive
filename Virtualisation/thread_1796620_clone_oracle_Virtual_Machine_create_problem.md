---
title: "clone oracle Virtual Machine create problem"
date: 2011-07-04
forum: Virtualisation
---

### Post by yasir.iqbal1 on 2011-07-04
Dear All,
I am using the oracle Virtual Box 4.0.0 on my ubuntu 10.10 host PC. I am trying to clone one of my VM through clonehd command. When i run the command 
VBoxManage clonehd source.vdi destination.vdi

It create the new vdi file with new UUID. But the problem which i am facing is that when i add this vdi file into a new VM it give me the following error. 

Failed to open the hard disk /Data/SQL-2.vdi.
The medium '/Data/SQL-2.vdi' can't be used as the requested device type.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Medium
Interface: IMedium {9edda847-1279-4b0a-9af7-9d66251ccc18}
Callee: IVirtualBox {d2de270c-1d4b-4c9e-843f-bbb9b47269ff}

I am stuck on this issue from the last 2 weeks. By the way, before running the command clonehd, i release the sourve vdi from virtual manager. Please help me to solve this issue. I know, i am doing something wrong. Otherwise the procedure is very simple and straight forward.

---

### Post by khurtsiya on 2011-10-14
same problem

---

