---
title: "How to create a vbox launcer on AWN dock that automatically loads a specified vm?"
date: 2009-03-22
forum: Virtualisation
---

### Post by benhur99ph on 2009-03-22
Hi everyone,

Sorry if this has been posted before, I have run a search a couple of times and didn't find anything. So here goes.

As the title suggests, I am looking for a way to create a launcher on my AWN dock that starts Virtualbox and loads a specific virtual machine at the same time. So I wouldn't have to select it from the list and click on "start". This is because I only have one virtual machine setup, a Windows XP guest which I use for an application that is designed for Windows only.

Is there a way to do this? 

Thanks,
Ben

---

### Post by Dedoimedo on 2009-03-22
Create a shortcut and:
VBoxManage startvm <your virtual machine name>

Dedoimedo

---

