---
title: "Accessing shared folders in Virtualbox"
date: 2011-09-16
forum: Virtualisation
---

### Post by rmcellig on 2011-09-16
I have Virtualbox installed on my Mac and am accessing as guest Ubuntu 11.04. I have the guest additions installed with two shared folders that show up in the Devices/Shared Folders pull down menu. How can I access these folders in Ubuntu?

---

### Post by varunendra on 2011-09-17
"Network" in nautilus?

---

### Post by Morbius1 on 2011-09-17
The shared folders on the Ubuntu guest should be mounted automatically to:
```
/media/sf_share-name
```

---

### Post by rmcellig on 2011-09-17
I can see them but for some reason I can't access them.

---

### Post by Morbius1 on 2011-09-17
Perhaps you didn't automatically get added to the right group.

In the Ubuntu guest:
```
sudo gpasswd -a morbius vboxsf
```
[COLOR=Blue]*Change morbius you your own Ubuntu user name.*[/COLOR]

You will have to logout ( of the guest - not the host ) and login again for the group membership to take affect.

---

### Post by rmcellig on 2011-09-17
home@home-VirtualBox:~$ sudo gpasswd -a home
Usage: gpasswd [option] GROUP

Options:
  -a, --add USER                add USER to GROUP
  -d, --delete USER             remove USER from GROUP
  -h, --help                    display this help message and exit
  -r, --remove-password         remove the GROUP's password
  -R, --restrict                restrict access to GROUP to its members
  -M, --members USER,...        set the list of members of GROUP
  -A, --administrators ADMIN,...
                                set the list of administrators for GROUP
Except for the -A and -M options, the options cannot be combined.
home@home-VirtualBox:~$ 


Does this look right? If so, I restart my gust session to invoke the correct permissions?

---

### Post by Morbius1 on 2011-09-17
The group you need to add yourself to is [COLOR=Blue]vboxsf[/COLOR] so the command is:
```
sudo gpasswd -a home vboxsf
```

---

### Post by haqking on 2011-09-17
See here if you still have problems.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

---

### Post by rmcellig on 2011-09-17
That worked thanks!!!

---

