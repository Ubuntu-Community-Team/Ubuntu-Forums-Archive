---
title: "auto start virtual machine workstation on ubuntu startup"
date: 2012-03-24
forum: Virtualisation
---

### Post by mohamed_en on 2012-03-24
I have vmplayer installed on ubuntu 11.10 and I have created vm.vmx and I want it be started automatically when ubuntu startup 
I am new in linux world and I need to that urgent
I used to use vmrun command in windows command prompt but I can not use the same in ubuntu :p

---

### Post by nd456 on 2012-03-24
You can try putting it under the "startup applications" if you haven't already. That will just execute the file on startup without showing up in the terminal...
I also found this witch may be of assistance...
[www.vmware.com/pdf/vix160_](www.vmware.com/pdf/vix160_)**vmrun**_command.pdf
Sorry if this didn't answer your question

---

### Post by mohamed_en on 2012-03-24
Thanks for your reply
I tried to use startup applications I browsed for the vm.vmx file but it does not start could you tell me what I am missing or doing wrong

---

### Post by erind on 2012-03-24
In case you missed it, you need to add a new entry in the "Startup Applications". Place the below command in the "Command" section of that entry:

```
/usr/bin/vmrun start /full/path/to/VM.vmx

```Then save it and reboot.

---

### Post by dcstar on 2012-03-25
> **erind said:**
> In case you missed it, you need to add a new entry in the "Startup Applications". Place the below command in the "Command" section of that entry:

```
/usr/bin/vmrun start /full/path/to/VM.vmx

```Then save it and **reboot**.

There is no need to **reboot** for something that happens every time you **Log In**.

---

### Post by mohamed_en on 2012-03-25
Thank you all for replying to my question 
I found the solution in startup applications I add a new entry  with the command that starts the vm 
command ```
vmplayer /usr/home/me/vmware/vm.vmx
```
and it works perfect
Thank you all again:p

---

