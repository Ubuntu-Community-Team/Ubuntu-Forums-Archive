---
title: "Virtual box error"
date: 2015-10-04
forum: Virtualisation
---

### Post by gari2 on 2015-10-04
Hi,

I'm sorry to post this but I haven't found any solution to my problem.

I have installed VirtualBox on Ubuntu 14.04 and when I try to run Windows 7, this window appears.

Fallo al abrir una sesión para la máquina virtual Windows 7.

The virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1.

Código Resultado: NS_ERROR_FAILURE (0x80004005)
Componente: Machine
Interfaz: IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}


 Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.



I've tried to do everything I read but I couldn't run it.

Thank you

---

### Post by flocculant on 2015-10-04
did you run that command as root ?

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by howefield on 2015-10-04
> **gari2 said:**
> I've tried to do everything I read but I couldn't run it.

What happened after you ran..

```
 sudo /etc/init.d/vboxdrv setup
```

---

### Post by gari2 on 2015-10-04
When I run 
 sudo /etc/init.d/vboxdrv setup

This message appears:

sudo: /etc/init.d/vboxdrv: command not found

---

### Post by gari2 on 2015-10-04
Hi!

Finally I could solve it. I had to install "aptitude", then I removed VirtualBox packages and I installed the one from the VirtualBox web.

Thank you!

---

### Post by cristina.rivera.ba on 2016-04-23
No me funcionaba Virtualbox, arrancaba pero no podía ejecutar ninguna de las máquinas. La solución que encontré fue:
[FONT=courier new]sudo apt-get install virtualbox-dkms[/FONT]
y después:
[FONT=courier new]sudo modprobe vboxdrv[/FONT]

---

### Post by MAFoElffen on 2016-04-23
> **cristina.rivera.ba said:**
> No me funcionaba Virtualbox, arrancaba pero no podía ejecutar ninguna de las máquinas. La solución que encontré fue:
[FONT=courier new]```
sudo apt-get install virtualbox-dkms
```[/FONT]
y después:
```

[FONT=courier new]sudo modprobe vboxdrv
```[/FONT]
<translation of last post...>
> 
I did not work Virtualbox , but could not run tore none of the machines . The solution I found was :
```

sudo apt- get install virtualbox- dkms

```
and then:
```

sudo modprobe vboxdrv

```


---

