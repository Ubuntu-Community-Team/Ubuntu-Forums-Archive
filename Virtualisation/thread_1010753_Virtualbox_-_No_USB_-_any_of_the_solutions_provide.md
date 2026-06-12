---
title: "Virtualbox - No USB - any of the solutions provided seems to work for me."
date: 2008-12-14
forum: Virtualisation
---

### Post by talofo on 2008-12-14
Hi all,

I'm getting this:


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}


Here, 

sudo gedit /etc/fstab

I already have added a line to the bottom with this:

none /proc/bus/usb usbfs devgid=1001,devmode=666 0 0


The other solution that I've seen:
sudo gedit /etc/init.d/ mountdevsubfs.sh 

I cannot apply since my file is very different and as not any #magic comment or something.




Can anyone help me put the usb to work on the guest machine?



Thanks in advance,
MEM

---

### Post by Dedoimedo on 2008-12-14
What version are you using?
You need the closed-source PUEL version of VB and not OSE?
Dedoimedo

---

### Post by talofo on 2008-12-14
ow... :( 

So the OpenSource edition does not work?

:s


thanks

Ok. It's free for personal use. How can we install that version then? Should I remove this one?

---

### Post by talofo on 2008-12-14
Yes I need. Well, do I need to change all this just because of a USB? Hmm...

I will search if there is some solutions about ope and usb on guest.


Thanks a lot. I was having no idea that they where two versions of it.


Regards,
MEM

---

### Post by talofo on 2008-12-14
Ups. 

Actually I'm on a PUEL version. :( what should I do?

---

### Post by Dedoimedo on 2008-12-14
Did you install the guest addons in the virtual machine?
Dedoimedo

---

### Post by talofo on 2008-12-14
Yes.

:(

---

