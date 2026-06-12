---
title: "Virtual Box - Failed to access the USB subsystem."
date: 2011-11-30
forum: Virtualisation
---

### Post by marer13 on 2011-11-30
Hello everyone,

I'm having troubles accessing USB on my Virtual Box.

Here's the message I'm getting:


 p, li { white-space: pre-wrap; }  *Failed to access the USB subsystem.*
*VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a more detailed explanatio*n.


Any help would be appreciated.

---

### Post by BC59 on 2011-11-30
Here it's explained with pictures:

[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---

### Post by marer13 on 2011-11-30
Thank you for your willingness to help, but this article shows how to deal with it on Ubuntu, and I'm on Kubuntu. It's different. 

I can't follow the steps. When I go to User Groups, there is no [B][I]"Click the "Unlock" button..."

[/I][/B]I'm attaching a screenshot.[B][I]
[/I][/B]

---

### Post by haqking on 2011-11-30
from terminal

```
sudo usermod -a -G vboxusers username
``` 

where username is your username then logout and back in

---

### Post by marer13 on 2011-11-30
That worked!

Thank you very much!

---

### Post by haqking on 2011-11-30
> **marer13 said:**
> That worked!

Thank you very much!

Of course it worked ;-)

You are welcome.

Cheers

---

### Post by geek.de.nz on 2012-11-12
```
sudo usermod -a -G vboxusers username
```

didn't work for me. Is it possible that the group is not allowed to access my USB devices??

```
sudo groups myuser
myuser : myuser adm cdrom sudo dip plugdev lpadmin sambashare vboxusers

```

Weird it doesn't work for me...

---

### Post by cwsnyder on 2012-11-12
You really should have opened a thread to ask your question.  VirtualBox has changed since the tutorial was written, requiring Oracle VirtualBox (non-free) and the VirtualBox Extension Pack installed on the Host computer, as well as the user being part of the vboxusers group.

---

### Post by pkadeel on 2012-11-13
> **geek.de.nz said:**
> ```
sudo usermod -a -G vboxusers username
```didn't work for me. Is it possible that the group is not allowed to access my USB devices??

```
sudo groups myuser
myuser : myuser adm cdrom sudo dip plugdev lpadmin sambashare vboxusers

```Weird it doesn't work for me...
Are you sure you have also installed the guest additions extention pack and have enabled USB access in virtualbox Preference

---

### Post by wildmanne39 on 2012-11-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

