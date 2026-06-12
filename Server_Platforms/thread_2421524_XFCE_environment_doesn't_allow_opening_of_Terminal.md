---
title: "XFCE environment doesn't allow opening of Terminal Window"
date: 2019-06-23
forum: Server Platforms
---

### Post by ndnd on 2019-06-23
Hello, 
I am fairly new to ubuntu so details (commands) would be helpful. I have installed the following 
> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
Codename:       bionic

Desktop Environment: XFCE4 4.12



I somehow am not able to open the terminal window as well as few other applications. It appears as 'x' as shown in the attached image 
[ATTACH=CONFIG]283482[/ATTACH]
[ATTACH=CONFIG]283483[/ATTACH]

I am not clear if there is an issue with permissions or some package that I need to install. If you require more information from the system can you please let me the commands to get that info as well. 
I have previously worked with xfce4 and it is good in terms of performance so would like to keep it and yes I need desktop environment to install some GUI applications. 

Thanks in advance! :D

---

### Post by again? on 2019-06-23
Try running in terminal (or alt+F2) ...
```
exo-preferred-applications
```

You can navigate to /usr/share/applications/xfce4-terminal if you need.
Settings-manager should also have a "Preferred Applications" module in the personal section.

Being new you may want to install a complete xfce4 environment configured for ubuntu.
```
sudo apt install xubuntu-desktop
```
Then at the login greeter choose the Xubuntu session.

---

### Post by The Cog on 2019-06-23
I would suggest that if you want to use xfce than it would be better to install Xubuntu. That way you don't get all the Ubuntu gnome baggage. But it it's too late to go back to a new install, then as guber2 says, installing xubuntu-desktop should pull in all the supporting bits and pieces to make it work.

---

### Post by ndnd on 2019-06-23
Hi, 
Thanks for the quick reply. The reason for xfce install was to keep it light as I have to access it remotely. In the previous install (I did this 3-4 years ago) I didn't run into any such problems that's the only reason I thought of continuing with xfce.

So here is my question ?

> 
1) Can I uninstall the desktop environment and install it back ? I haven't done any GUI installations yet

> 2) Or should I simply install the xubuntu-desktop. The command would be 

sudo apt-get install xubuntu-desktop  

Right? 


> Would the xubuntu-desktop be clunky? If I do find it so can I uninstall it (how ? ) 

Any other

---

### Post by ndnd on 2019-06-23
Ok I tried to install xbuntu desktop do I need to reset somewhere ? I am still getting the same desktop environment ? 

> sudo apt-get install xubuntu-desktop 
This worked fine. But I tried logging out and logging back in it still goes to the same xfce environment

Do I need to reset/delete/refresh session somewhere. Can anyone show me how ?

Thanks again for your help

---

### Post by again? on 2019-06-23
```

```Did you choose xubuntu at the greeter?
[ATTACH=CONFIG]283486[/ATTACH]
May need to reboot.

FYI: xubuntu-desktop, lubuntu-desktop etc are [**metapackages**]("https://help.ubuntu.com/community/MetaPackages")
ie they are just a list of dependencies. Removing xubuntu-desktop just removes the list not the installed packages.
You need to copy from terminal new packages being installed to file and then you can remove if wanted.

eg if I installed lubuntu-desktop before confirming I would copy the list of new packages to a file.
Best way to do this is highlight with mouse then in another terminal run...
```
echo $(xsel) > lubuntu-packages.txt
```
xsel needs to be installed.
The xsel command copies the packages to a single line.
Then to remove you just run ...
```
sudo apt remove $(cat lubuntu-packages.txt)
```

---

### Post by mastablasta on 2019-06-24
not sure what applications you need, but perhaps a windows manager would be enough for your needs. have you maybe looked into them? e.g. iceWM or Openbox or a tabbed one like i3:
[https://en.wikipedia.org/wiki/Comparison_of_X_window_managers](https://en.wikipedia.org/wiki/Comparison_of_X_window_managers)

windows managers take up a lot less resources than full desktop environments.

---

