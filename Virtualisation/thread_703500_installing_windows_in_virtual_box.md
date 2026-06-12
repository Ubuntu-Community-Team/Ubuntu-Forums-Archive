---
title: "installing windows in virtual box"
date: 2008-02-21
forum: Virtualisation
---

### Post by kxr1der on 2008-02-21
Could somebody explain how to install windows XP in virtual box for me in detail. Im currently dual booting but i only do this for itunes, cuz i have an iphone and i dont want to jailbreak it... anyway i want to run windows and itunes in a virtual machine but i dont know anything about stuff like that. Also i was wondering if programs (itunes) installed in the virtual machine will stay installed when i run it again, and if i test this out and dont like it can i reallocate the hard drive space i used for the VM to ubuntu.

---

### Post by dje on 2008-02-21
First of all i need to know which version of virtualbox you are using
Did you install virtualbox from the repos ie. 
```
sudo apt-get install virtualbox-ose
```
or did you download it from the virtualbox site?

When you set up a vm all its "hard drive" is just one file on your ubuntu partition, if you don't want it anymore you just delete that file and it's all gone!

dje

---

### Post by dixonstalbert on 2008-02-21
try

[https://help.ubuntu.com/community/VirtualBox?highlight=%28virtualbox%29](https://help.ubuntu.com/community/VirtualBox?highlight=%28virtualbox%29)

---

### Post by dje on 2008-02-21
There is a very [easy guide here]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") to install virtualbox with USB support which is what you will need (you need to scroll down to the 'Personal Use & Evaluation License Version' section)

dje

---

### Post by kxr1der on 2008-02-21
I have the closed source version downloaded from the website

---

### Post by dje on 2008-02-21
Have you configured virtualbox for usb support? Look through the guide [here]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") to ensure that you have configured usb support (scroll down to 'Personal Use & Evaluation License Version')
As dixonstalbert posted there is a good walkthrough of creating a new virtual machine [here]("https://help.ubuntu.com/community/VirtualBox?highlight=%28virtualbox%29")

After you have created a new virtual machine insert your xp disk and click start. Then ensure you mount the host cd drive when prompted by the wizard and then it is a normal windows installation from then on

dje

---

### Post by kxr1der on 2008-02-21
last question: I don't actually have a windows install cd it is an hp recovery cd, which installs windows and drivers for the pc... Will this work?

---

### Post by dje on 2008-02-21
Well there's only one way to find out!! Give it a go, it can't hose your system. It may or may not work. Hope i was of some help.

EDIT: I think that it will most likely work

dje

---

### Post by kxr1der on 2008-02-21
im getting this error on enableing USB 


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

there isnt eve a tab for USB settings like there should be

---

### Post by kxr1der on 2008-02-21
nvr mind fixed it

---

