---
title: "Does apparmor by default protect transmission?"
date: 2010-01-18
forum: Security
---

### Post by dogdo on 2010-01-18
Hi 

Im using ubuntu 9.10 with the default apparmor profiles- some of the profiles that are enforced by default have weird names- is one of these a transmission profile?

---

### Post by FuturePilot on 2010-01-18
No

---

### Post by bodhi.zazen on 2010-01-18
By default all apparmor profiles are in complain mode.

You have to change them to enforce.

There is no profile for transmission, so you need to write one, or you can modify mine if you wish :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.bin.transmission](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.bin.transmission)

---

### Post by dogdo on 2010-01-21
Ok when i try to make my own profile for transmission with 'sudo genprof transmission' i do the normal actions with tranmission, deny/accept the logs but then it tells me to add a new user and password? im the only user on this pc so i dont know what this means.

---

### Post by rookcifer on 2010-01-21
> **dogdo said:**
> Ok when i try to make my own profile for transmission with 'sudo genprof transmission' i do the normal actions with tranmission, deny/accept the logs but then it tells me to add a new user and password? im the only user on this pc so i dont know what this means.

```
#include <tunables/global>                                 

/usr/bin/transmission {
  #include <abstractions/X>
  #include <abstractions/base>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/private-files>
  #include <abstractions/private-files-strict>


  owner /home/*/ r,
  owner /home/*/** rwk,
  owner /proc/*/cmdline r,
  owner /proc/*/fd/ r,
  /proc/*/net/route r,
  /proc/filesystems r,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/lib*so* mr,
  /usr/share/fonts/ r,

}
```

Start with this and go from there.  This wont be complete because I use KDE, so it will have to have minor tweaks for Gnome.

---

### Post by dogdo on 2010-01-21
Thats one of the reasons i wanted to make my own profile. Even though there is a sticky thread posted in the security forums first page which has instructions for this, i cant seem to access the transmission profile directly. I always get a error saying that 

'shinji@shinji-laptop:~$ /etc/apparmor.d
bash: /etc/apparmor.d: is a directory'

God i hope 10.04 has better default profiles set to enforce...

---

### Post by FuturePilot on 2010-01-21
> **dogdo said:**
> Thats one of the reasons i wanted to make my own profile. Even though there is a sticky thread posted in the security forums first page which has instructions for this, i cant seem to access the transmission profile directly. I always get a error saying that 

'shinji@shinji-laptop:~$ /etc/apparmor.d
bash: /etc/apparmor.d: is a directory'

God i hope 10.04 has better default profiles set to enforce...

That's because /etc/apparmor.d is a directory. Just throwing a directory into the terminal will give you that error. If you're trying to edit a profile you need to specify a program like

```
gksudo gedit /etc/apparmor.d/profilename
```

where profilename is the name of the profile.

---

### Post by dogdo on 2010-01-21
Ok i did that sudo command for the transmission profile and this is what i got 

[http://img706.imageshack.us/img706/2078/screenshotch.png](http://img706.imageshack.us/img706/2078/screenshotch.png)

So do i just fill this page up with text? im thinking of copying and pasting one off the apparmor tutorial page-is this recommended?

---

### Post by bodhi.zazen on 2010-01-21
> **dogdo said:**
> Ok i did that sudo command for the transmission profile and this is what i got 

[http://img706.imageshack.us/img706/2078/screenshotch.png](http://img706.imageshack.us/img706/2078/screenshotch.png)

So do i just fill this page up with text? im thinking of copying and pasting one off the apparmor tutorial page-is this recommended?

No offence intended, but it seems you do not understand the basics of editing files or which files apparmor is using.

I suggest you look at a few links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In terms of editors, you can use gedit or nano

gksu gedit /path/to/file_to_edit
sudo nano /path/to/file_to_edit

In terms of apparmor, first you need to understand the naming convention of profiles. Profiles are stored in a directory , /etc/apparmor.d

They are named for the full path of the application, dropping the first / and converting the remaining / to a .

```
bodhi@entropy:~$ which transmission                           01/21/10  7:05 PM
/usr/bin/transmission
```

so the profile for transmission is NOT called transmission, it is called 

usr.bin.transmission

and it is located at 

/etc/apparmor.d/usr.bin.transmission

In addition, I would advise you, in order to write your open profile you need to understand the linux tree, where applications are located, and how to read the logs apparmor generates in /var/log/messages

The "tools" such as aa-logprof will only get you in the ball park, they will not write the profile for you, they need to be fine tuned.

I strongly suggest you go back to the apparmor sticky and read it again.

With that said, do not get discouraged, you are well on your way, better then some.

---

### Post by FuturePilot on 2010-01-21
.

---

