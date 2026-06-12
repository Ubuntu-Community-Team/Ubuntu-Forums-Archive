---
title: "can Ubuntu ONE be used to sync settings/programs across PCs?"
date: 2013-03-28
forum: Ubuntu One (CLOSED)
---

### Post by kyalami321 on 2013-03-28
Ubuntu One is a great feature, but can it be used to sync settings/programs between Ubuntu PCs? it'd be nice to have the same wallpaper and desktop settings (amongst others) to sync across my two PCs without my having to change them. same thing with apps; consider the iPhone's ability to sync a list of apps between devices and then having each device download the app. with Ubuntu's software center looking and behaving like an app store, such thoughts follow.

---

### Post by Frogs Hair on 2013-03-31
I don't think this can be done because system configurations are located in different folders and some require root access. Copying and saving a user profile or preferred application settings  is possible if you can locate them, but simply moving it to the correct folder doesn't remove the existing one. As you know many web browser have a sync option, but don't require special permissions to use like the Ubuntu root directory. In the case of identical folder names you would have to replace each folder because identical names can't be placed in the same directory. I think manually configuring would be faster and safer than trying to sync configuration files which are setup during installation.

---

### Post by Isamu715 on 2013-04-02
It's possible to sync some user-specific app settings with Ubuntu One on individual basis. The app-downloading thing is possible with some tinkering. An apps configuration is usually loacated in *.appname* folder in your home directory, for ex. *~/.openshot* for the OpenShot Video Editor. If you sync these folders using Ubuntu One your app settings should be the same across synced computers. Settings like wallpaper, etc. are found in *~/.gconf*. Note that the path to the selected wallpaper needs to be the same on all systems so it's recommended that you put the wallpaper in a synced folder before changing it.

---

### Post by roly33 on 2013-04-11
> **kyalami321 said:**
> Ubuntu One is a great feature, but can it be used to sync settings/programs between Ubuntu PCs? it'd be nice to have the same wallpaper and desktop settings (amongst others) to sync across my two PCs without my having to change them. same thing with apps; consider the iPhone's ability to sync a list of apps between devices and then having each device download the app. with Ubuntu's software center looking and behaving like an app store, such thoughts follow.

It might be simpler using something like Samba 4 on an old unused laptop as an Active Directory Server as your user profile could be kept on the server and pulled to whichever machine you are logged into (depending if it'll work on Ubuntu clients or not, I know it works with Windows clients).

As my only current machines are My Toshiba Satellite C660-15R Notebook running Ubuntu & Advent Netbook running Windows 7 Ultimate I cant really test it out.
Will have to get a HDD for my old Fujitsu Siemens or HP Compaq Notebooks and stick Ubuntu on and give it a go one day.

so if anyone with Networking experience can help it would help?

But I don't think Ubuntu One will be really suitable in the long run as it's intended use is for cloud storage & not something that is suited to Active Directory type jobs IMHO.

Roland

---

### Post by JamesTait on 2013-04-12
You might want to give OneConf a try. It integrates into Ubuntu Software Centre and is available via the Installed button - you get a list of hosts and can sync installed packages between them. I'm not sure if it does everything you're asking, but it might be a start.

---

