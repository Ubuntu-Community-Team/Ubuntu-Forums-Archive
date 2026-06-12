---
title: "[SOLVED] virtualbox in ubuntu 8.4?"
date: 2008-04-30
forum: Virtualisation
---

### Post by kamitsukai on 2008-04-30
I tried installing virtualbox from the repositories but afterwards it wouldnt run and then i think iread somwhere that it wont run on ubuntu 8.4?
is this right? also if it will run can someone tell me where i can get a deb package from?

thnx

---

### Post by Dr Small on 2008-04-30
What do you mean "It won't run"?
Execute it from the terminal and give us back the error.

Dr Small

---

### Post by ivze on 2008-04-30
Using virtualbox on HH8.04 on amd64 platform. Works flawlessly.

---

### Post by spec-chum on 2008-04-30
Nope.  I've got virtualbox running fine here on 8.04.

I installed the virtualbox-ose and the virtualbox-ose-modules-2.6.2 24 packages from the Universe repository and I've got a virtual XP machine running fine with that.

---

### Post by ptn107 on 2008-04-30
The version included in Ubuntu's repository works fine .

1) Install virtualbox packages:
```
sudo apt-get install virtualbox-ose virtualbox-ose-modules-2.6.24-16-
generic
```

2) Add your username to the 'vboxusers' group:
```
sudo usermod -a -G vboxusers $USER
```

3) Log out and back in for settings to take effect.

---

### Post by kamitsukai on 2008-04-30
```
dreamsofubuntu@dreamsofubuntu-desktop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

```

---

### Post by ptn107 on 2008-04-30
> **kamitsukai said:**
> ```
dreamsofubuntu@dreamsofubuntu-desktop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

```

You need to install 'virtualbox-ose-modules-2.6.24-16-generic'

---

### Post by kamitsukai on 2008-04-30
lol thankyou i can be such an idiot...

---

### Post by TransplantedCanuck on 2008-05-04
> **kamitsukai said:**
> ```
dreamsofubuntu@dreamsofubuntu-desktop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.

```

I get the exact same error. It was working fine yesterday, and today thats what happens. I tried removing the modules and reinstalling, but no luck. I'M in the vboxusers group...

I'm totally clueless with Linux and the fact that between one boot and the next things will just stop working is frustrating.

Any ideas how I can progress and get it working again?

---

### Post by RowanC on 2008-05-04
Seems to be a number of threads with this problem, I'm new to ubuntu, but there was a kernel version upgrade on Sat/Fri and the virtualbox modules package hasn't kept up with it. I find if I boot into the previous kernel ver (escape at boot to go into grub) it works fine.

Cheers,
RowanC

---

