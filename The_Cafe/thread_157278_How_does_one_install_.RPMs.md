---
title: "How does one install .RPMs?"
date: 2006-04-08
forum: The Cafe
---

### Post by Swiss on 2006-04-08
How does one install .RPMs? ](*,)

---

### Post by dabear on 2006-04-08
[QUOTE=Swiss]How does one install .RPMs? ](*,)[/QUOTE]
install «alien»
```
sudo apt-get install alien
```
Convert the rpm to a deb

If you downloaded the rpm to the desktop:
```

cd ~/Desktop
sudo alien YOUR_FILE_NAME.rpm

```
install the deb:
```

sudo dpkg -i THE_NEWLY_CREATED_DEB.deb

```

---

### Post by John.Michael.Kane on 2006-04-08
You have to use a program called alien [http://www.newlinuxuser.com/howto-install-an-rpm-package-on-a-debian-box/](http://www.newlinuxuser.com/howto-install-an-rpm-package-on-a-debian-box/)

---

### Post by ComplexNumber on 2006-04-08
another program of use is checkinstall

---

### Post by dabear on 2006-04-08
[QUOTE=ComplexNumber]in most systems, just double click on it and the package manager will ask if you want to install it or not. on the command line, just type 'rpm -Uvh <package name>'[/QUOTE]
Wrong, do not do this for ubuntu!

Installing the rpm with the rpm command will bypass debians package system. Convert to a deb, and installthat instead

---

### Post by aysiu on 2006-04-08
[QUOTE=dabear]install «alien»
```
sudo apt-get install alien
```
Convert the rpm to a deb

If you downloaded the rpm to the desktop:
```

cd ~/Desktop
sudo alien YOUR_FILE_NAME.rpm

```
install the deb:
```

sudo dpkg -i THE_NEWLY_CREATED_DEB.deb

```[/QUOTE] dabear, do you know if there's a difference between the procedure you're outlining and this procedure? ```
cd ~/Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i *.rpm
```

---

### Post by ComplexNumber on 2006-04-08
eas[quote=dabear]Wrong, do not do this for ubuntu!

Installing the rpm with the rpm command will bypass debians package system. Convert to a deb, and installthat instead[/quote]
at least wait until i've edited my post :D.

---

### Post by dabear on 2006-04-08
[QUOTE=aysiu]dabear, do you know if there's a difference between the procedure you're outlining and this procedure? ```
cd ~/Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i *.rpm
```[/QUOTE]
Ah, I didn't know alien had an -i/--install parameter. Except for that, those two methods are mainly the same. But I dunno if it's such a wise thine to include the asterix instead of the file name,though.. I mean, if there's multiple rpms in the Desktop directory, those too will be installed

---

### Post by NeghVar on 2006-04-08
> Except for that, those two methods are mainly the same. But I dunno if it's such a wise thine to include the asterix though.. I mean, if there's multiple rpms in the Desktop directory, those too will be installed

I believe the * was included in place of 'FILE TITLE HERE'

---

### Post by 3rdalbum on 2006-04-09
I thought I read recently that there are risks associated with using RPMs on a Debian-based system. Is that just for using the rpm command, or does it also apply to using Alien to convert to a deb?

---

### Post by majikstreet on 2006-04-10
I don't think so ^^

at Swiss, on Ubuntu/Debian or on RedHat/Fedora/Etc?

I thought it was rpm -i but I don't think I've ever really done that!

---

### Post by Swiss on 2006-04-10
U/d :)

---

### Post by dabear on 2006-04-10
It should be safe to install the deb package after its alienized ( 8) ), but if it screws up, you can just uninstall it. From my earlier fedora time, I believe I installed an rpm by issuing the command "rpm -Uvh package.rpm", but I am uncertain if the -v and -h flags needs to be there. 

If you really want to, you can install the rpm directly in ubuntu (and thus bypassing the debian system) by issuing the above command, but you would then have to install the rpm package first. **DONT DO THIS!**

---

### Post by Swiss on 2006-04-10
Actually, before I knew what I was doing, I used that command. It said that "Command not reconized" (sp?) :)

---

