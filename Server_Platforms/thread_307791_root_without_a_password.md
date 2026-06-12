---
title: "root without a password?"
date: 2006-11-27
forum: Server Platforms
---

### Post by camilluk on 2006-11-27
My pc has kubuntu edgy.

While trying to adjust my screen resolution, I installed the operating system several times. Every time, I would install kubuntu on partition 1 and mount '/home' on partition 2, where I have all the data. Being '/home', partition 2 also is the home of the default non-root user ('joe') that I typically create at every installation, always with the same password.

Here's the disturbing fact I realised: if I boot in failsafe mode I get a 'root' prompt without being asked a for a password. From there I am in total control of the machine. I can even
```
startx
```and log in kubuntu as 'root' (always with no password), which is otherwise impossible to do.

I can then see all the content of '/home' and do whatever I want with it!!!

How do I prevent that from happening?

I don't want anybody to get hold of my pc and start in failsafe mode or just make a fresh installation in order to be able to see all my files. However, 
I don't want to find myself in a situation where after a fresh installation, I can't access my '/home' folder because it's protected and therefore unreadable. How do I reconcile these two apparently conflicting needs?

Thank you!
Cam

---

### Post by marekdef on 2006-11-27
Try securing your grub with:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_disable_all_interactive_editing_control_for_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_disable_all_interactive_editing_control_for_GRUB_menu)

---

### Post by camilluk on 2006-11-27
I will try that, and that should prevent someone from getting the root's prompt without a password. But what if I reinstall over the present installation? Grub is replaced at each new installation, right? In that case the system is still vulnerable, isn't it?

---

### Post by MJN on 2006-11-27
The bottom line is that if someone can get physical access to your machine then you can't stop them getting at your files. Forget passwords, locked down Grub etc - they just could quite easily boot with a LiveCD and mounted your partitions, put your disk in another machine and mount them etc etc.
 
Of course, encrypted hard disks can mitigate this....
 
Mathew

---

### Post by camilluk on 2006-11-27
> **MJN said:**
> The bottom line is that if someone can get physical access to your machine then you can't stop them getting at your files. Forget passwords, locked down Grub etc - they just could quite easily boot with a LiveCD and mounted your partitions, put your disk in another machine and mount them etc etc.
 
Of course, encrypted hard disks can mitigate this....
 
Mathew

I am reluctant to confute your argument, because I have seen with my own eyes that what you're saying is true... There must be a way to prevent that though. I mean, forget my personal pictures and my home finance spreadsheets... let's say I'm the HR director of a large company, and I have the personnel data on a linux pc (ok, it's not too big a company...:)). If what you're saying is true, the cleaning lady comes in the office at 4AM, boots from a live cd, installs over my existing OS, screws up my personnel files and also cuts a €10000 cheque for herself in the process!!! This can't be right...[-(

---

### Post by piers on 2006-11-27
Without trying to sound facetious, that's why they put locks on the doors and didn't let the cleaning lady in unsupervised at the company I used to work for!

You could always password protect your BIOS, but then you could always open the PC and reset the BIOS again! Maybe remove the CD-ROM drive and fill the IDE socket with glue? Put the computer locked in cabinet with nice long cables? It goes on...

---

### Post by camilluk on 2006-11-27
> **piers said:**
> Without trying to sound facetious, that's why they put locks on the doors and didn't let the cleaning lady in unsupervised at the company I used to work for!

You could always password protect your BIOS, but then you could always open the PC and reset the BIOS again! Maybe remove the CD-ROM drive and fill the IDE socket with glue? Put the computer locked in cabinet with nice long cables? It goes on...

I know you're just kidding, but I think this is a serious issue, and I still think there must be a way to prevent that. I don't expect my pc to be thief-proof, but at least I hope the thief won't be able to access the data. (S)He can reformat the HD and get a brand new system going, but not my data. We use an AS400 for the company data, and if you steal it you can't do much with it unless you know the security officer's password... Surely the same security can be applied to a linux system...

And btw, I worked at several large companies, and I am now working with a not-so-large but still large-ish company... I've never seen the cleaners while I was around, and yet every morning my desktop is clean and tidy! :-D I guess all the tons of papers that IT managers sign off to certify the security of the data they manage are a load of toilet paper then!

---

### Post by yota on 2006-11-27
Without physical security there's no real security, but in real life we all have to accept a trade-off between security and functionality.
I think that luks ( [http://luks.endorphin.org/](http://luks.endorphin.org/) ) and truecrypt ( [http://www.truecrypt.org/](http://www.truecrypt.org/) ) are great enhancements that can satisfy the OP needs.

Luks is available in ubuntu in the package "cryptsetup", it's very nicely integrated with the os and I'm quite happy using it.
Sure, if someone really wants you data at any cost the shutdown-pc-in-a-closed-chest is a still a safer solution ;) but IMHO encryption should be enough for occasional thiefs such as cleaning ladies.

Just my 2 cents, hoping to help!

---

### Post by glent on 2006-11-27
I had the same security problem. What is the point in constantly entering a password to make some small system changes while not logged as root, when it is easier to login as root without any password!!!

---

### Post by Kurt` on 2006-11-27
> **glent said:**
> I had the same security problem. What is the point in constantly entering a password to make some small system changes while not logged as root, when it is easier to login as root without any password!!!

As was stated earlier in this thread, physical access to a machine bypasses all "protection" mechanisms except for disk encryption.

Why do you think datacenters have 24/7 armed guards and surveillance cameras? :-)

Also, the reason you have to explicitly type a command (sudo) to run a command as root is to prevent YOU from accidentally harming your system. If you were always logged in as root, a mistyped command could destroy your entire system.

---

### Post by HackProof on 2006-11-27
u wont how easy it is to physically abuse a virgin ubuntu box!

sick and tired of doing sudo each time editing the xorg.conf file i tried this trick

$ sudo passwd root
password:
Enter UNIX password:
Conform UNIX password:

$su
password:

#

whats it!!!!!!! you dont even have to boot to fail safe/ recover mode!

---

### Post by Phantom784 on 2007-01-05
When I want to work as root without having to keep typing sudo, i just use "sudo su".  That way, you won't have to create a password for root.

---

