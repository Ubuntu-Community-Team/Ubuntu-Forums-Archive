---
title: "virtualbox broken after update"
date: 2009-06-01
forum: Virtualisation
---

### Post by ayu on 2009-06-01
Hi,

Virtualbox breaks every time after updating to a new release. After "upgrading" from 8.10 to 9.04, Virtualbox console starts up fine, but when I try to start a virtual machine there is an error:

```
The VirtualBox Linux kernel driver (vboxdrv) is either
not loaded or there is a permission problem with /dev/vboxdrv. 
Re-setup the kernel module by executing
'/etc/init.d/vboxdrv setup'

```

Vboxdrv doesnt exist for me, so I'm not sure what to do. After the 8.04 to 8.10 upgrade, I uninstalled virtualbox and installed virtualbox-ose from the repos. I recall there being a vboxdrv error to for 7.04->7.10 and for 7.10->8.04, but those were easily fixed. I couldn't do the same thing for 8.10 though, so I had to install ose instead. But 9.04 breaks it again. :(

Can somebody please help? Thanks in advance!
~Ayu

---

### Post by madverb on 2009-06-01
/etc/init.d/vboxdrv setup
?

---

### Post by ayu on 2009-06-02
> **ayu said:**
> 
... Vboxdrv doesnt exist for me, so I'm not sure what to do ...

> **madverb said:**
> /etc/init.d/vboxdrv setup
?

??

---

### Post by Elfy on 2009-06-02
Run the command as given by virtualbox - almost ;) You'll need to add sudo 

```
sudo /etc/init.d/vboxdrv setup
```

If you read the whole of the error message you can see that it tells you what you need to do - which is great if you understand :)

> Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup'

Anytime that you need to do anythinng like this outside of your home you will need to use sudo.

---

### Post by ayu on 2009-06-02
> **forestpixie said:**
> Run the command as given by virtualbox - almost ;) You'll need to add sudo 

```
sudo /etc/init.d/vboxdrv setup
```

If you read the whole of the error message you can see that it tells you what you need to do - which is great if you understand :)



Anytime that you need to do anythinng like this outside of your home you will need to use sudo.

Thanks, but I don't think permissions are the problem here.

```
ayu@ubuntu:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
```

Like I said, vboxdrv is missing, and I don't know how to get it back.

Best regards,
Ayu

---

### Post by Therion on 2009-06-02
Did you install Virtual Box from the Repo -- using Add/Remove or Synaptic?  Judging from the error messages you're getting, I'm betting you did.

If so, I'll bet you dollars to donuts the "problem" is the new kernel you're now running.  The option of recompiling the kernel module is not part the OSE version of Virtual Box (the version you get from the repo) so it's not really a problem * per se* (it's a feature!) but by the same token, it's the source of the error message.

---

### Post by ayu on 2009-06-02
> **Therion said:**
> Did you install Virtual Box from the Repo -- using Add/Remove or Synaptic?  Judging from the error messages you're getting, I'm betting you did.

If so, I'll bet you dollars to donuts the "problem" is the new kernel you're now running.  The option of recompiling the kernel module is not part the OSE version of Virtual Box (the version you get from the repo) so it's not really a problem * per se* (it's a feature!) but by the same token, it's the source of the error message.

Yes I installed OSE from the repo after being unable to fix the non-ose version (also from repos) after my upgrade to 8.10. Does this mean OSE from the repos doesn't work in 9.04?  So..., any suggestions? Uninstall everything and install the deb from virtualbox? Does this mean I have to reinstall everytime I do an upgrade?

---

### Post by Elfy on 2009-06-03
I use the puel version and have the repo added to my sources, nothad any issues with it as yet. The repo information is on the downloads page - [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


IF you do install the puel version remove the ose version first.

---

### Post by ayu on 2009-06-09
Not really solved, but uninstalling and installing the deb from virtualbox.org works. Guess I'll just have to do that after every release.

---

