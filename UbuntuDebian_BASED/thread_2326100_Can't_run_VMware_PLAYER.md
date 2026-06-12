---
title: "Can't run VMware PLAYER"
date: 2016-05-28
forum: Ubuntu/Debian BASED
---

### Post by dallase1 on 2016-05-28
After having to reinstall VMware Player Workstation when I try to run it for the first time to install an Operating System I get a message saying 

"Before you can run VMware Player, Several several modules must be compiled and loaded into the running kernel.

[B]Kernel Headers 3.2.0-103-generic-pae

[/B]Kernel headers for version 3.2.0-103-generic-pae were not found. If you installed them in a non-deafult path you can specify the path below. Otherwise refer to your distribution's documentation for installation instructions and click Refresh to search in default locations[B]"

[/B]When I click browse I see a list of folders and one of them matches the 3.2.0-103-generic-pae name exactly but when I click Install it  says 
 
"C header files matching your running kernel were not found. Refer to your distribution's documentation for installation instructions"

So where do I find these files it is looking for ?

[B]
Thanks 


[/B]

---

### Post by QDR06VV9 on 2016-05-28
Moved to Virtualisation
Have you run this yet
```
 sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by izznogooood on 2016-05-28
You might also need to install the kernel source codes:

```
sudo apt-get source linux-image-`uname -r`
```

On another note.... Why dont you use "Virtualbox" ? <-- this will also keep up to date automatically...

---

### Post by ajgreeny on 2016-05-28
I assume you are still running 12.04 from that kernel version, or perhaps another ubuntu version after upgrading, but still using that kernel for some reason.

I do not know vmware-player at all (I use VBox) but I just wonder if that old kernel version is the cause of your problem.

---

### Post by QDR06VV9 on 2016-05-28
> **ajgreeny said:**
> _**I assume you are still running 12.04 from that kernel version**_, or perhaps another ubuntu version after upgrading, but still using that kernel for some reason.

I do not know vmware-player at all (I use VBox) but I just wonder if that old kernel version is the cause of your problem.

Yep he is... from one of his other posts
> I have Cylon Linux Release 12.04 LTS (precise) 32-bit Kernel Linux 3.2.0-102-generic-pae GNOME 3.4.2

---

### Post by ajgreeny on 2016-05-28
OK, so humour me, what is Cylon Linux Release?

I have searched and found nothing useful, other than a link with precise in some way.

Thread moved to Ubuntu/Debian Based OSs.

---

### Post by QDR06VV9 on 2016-05-28
> **ajgreeny said:**
> OK, so humour me, what is Cylon Linux Release?

I have searched and found nothing useful, other than a link with precise in some way.

Thread moved to Ubuntu/Debian Based OSs.

[http://cylonlinux.weebly.com/](http://cylonlinux.weebly.com/)  :D

Forum: [http://cylonlinux.weebly.com/help--support.html](http://cylonlinux.weebly.com/help--support.html)

---

### Post by ajgreeny on 2016-05-28
> **runrickus said:**
> [http://cylonlinux.weebly.com/](http://cylonlinux.weebly.com/)  :D

Forum: [http://cylonlinux.weebly.com/help--support.html](http://cylonlinux.weebly.com/help--support.html)
Sorry not to have mentioned, but I did find that and therefore moved the thread to the *U/D Based* section.

My bad!  I meant to say so in an edit after moving the thread but got involved in doing something else.

---

### Post by dallase1 on 2016-05-28
Non of these solved the problem 
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo apt-get source linux-image-`uname -r`

and when I ran the second command it asked for Zorin OS 9 32 bit but I have Cylon Linux 12.04 and don't have Zorin OS 9 installed on any of my partitions. 
I don't know if it has anything to do with it but when I try to up my system because update manager says I have 6 updates available it asks me to insert the 
Orin OS 9 DVD and when I do it still fails to update and it 's stuck on not being able to complete the update.

---

### Post by QDR06VV9 on 2016-05-31
> Before you can run VMware Player, Several several modules must be compiled and loaded into the running kernel.
now lets try this
```
sudo vmware-modconfig --console --install-all
```
I have also seen where kernel 3.8.0-21-generic fixed the vmware issue.
But just try the above one at a time.

---

