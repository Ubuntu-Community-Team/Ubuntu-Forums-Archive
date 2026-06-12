---
title: "problem with root folder ?(I make it )"
date: 2011-04-15
forum: Security
---

### Post by bluebird.jeff on 2011-04-15
[CENTER]Hello dear my friends , 

i have a problem with root folder.
[IMG]http://img820.imageshack.us/img820/8064/myproblemwithroot.jpg[/IMG]

  "how" ?
i do this file when i want to extract rpm file !, i try to delete the file 
and cant be deleted so what can i do to delete it ?! 

when i want to delete the file message appear and says : :mad:
" Error while deleting.
the folder "connectors.d" cannot be handled because 
you do not have permissions to read it !!

Note : 1- ( I'm the Administrator )  
       2- im beginner for linux ubuntu 
[/CENTER]

---

### Post by bodhi.zazen on 2011-04-15
Use sudo or gksu

sudo rm /root/file_to_remove

gksu nautilus /root

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bluebird.jeff on 2011-04-16
> **bodhi.zazen said:**
> Use sudo or gksu

sudo rm /root/file_to_remove

gksu nautilus /root

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

okay , 

the file on desktop and his name is KAV so can you give me the sudo code please ?

---

### Post by usatonycuba on 2011-04-17
Open your terminal:

sudo su  << type
(pass for root) << type
nautilus << type

A file manager window will be appear, that is nautilus windows with a root privileges, surf  your computer any where .. main files directory > home > user (name) > Desktop > (right click) -- Delete the file

---

### Post by bluebird.jeff on 2011-04-17
> **usatonycuba said:**
> Open your terminal:

sudo su  << type
(pass for root) << type
nautilus << type

A file manager window will be appear, that is nautilus windows with a root privileges, surf  your computer any where .. main files directory > home > user (name) > Desktop > (right click) -- Delete the file

can you take a look here please : 

[IMG]http://img851.imageshack.us/img851/6571/image005at.jpg[/IMG]

I Cant find any file ! root Desktop ! so what can i do , with note that i make all cods that you say it .

hope someone can help me :), Anyway thank you

---

### Post by usatonycuba on 2011-04-17
> **bluebird.jeff said:**
> can you take a look here please : 

---IMAGE--- ;)

I Cant find any file ! root Desktop ! so what can i do , with note that i make all cods that you say it .

hope someone can help me :), Anyway thank you
That is the ROOT-desktop, click on file system and then the home of your user

--- **CORRECTED** ---

> **usatonycuba said:**
> Open your terminal:


sudo su  << type
(pass for root) << type
nautilus << type

A file manager window will be appear, that is nautilus **File Browser** windows with a root privileges, surf  your computer any where .. main files directory (**FYLE SYSTEM**) > home > user (name) > Desktop > (right click "**select the file and make a right click on it**") -- Delete the file
[IMG]http://ubuntuforums.org/picture.php?albumid=2253&pictureid=7698[/IMG]

--- **EDITED **---

Other way can be: (at your terminal)
```

sudo su      << type
(password)   << type
sudo chmod 777 /home/**ACCOOUNT-USER NAME GOES HERE**/Desktop/**Kav**     << type
sudo chmod 777 /home/**ACCOOUNT-USER NAME GOES HERE**/Desktop/**Kav**/*   << type

```

Then you will see how "the small **lock** in the corner of the **Kav** folder -- IT WILL disappears"... (777 means 'everyone has full access to this file') do what you want with it.

---

### Post by bluebird.jeff on 2011-04-18
Thank you for helping :)

---

### Post by usatonycuba on 2011-04-18
> **bluebird.jeff said:**
> Thank you for helping :)
No problem ..... [SIZE="4"][COLOR="Red"]W[/COLOR]elcome to [COLOR="Sienna"]Ubuntu[/COLOR][/SIZE] :popcorn:

pd: @bluebird.jeff,  you can mark a thread as Solved by going to Thread Tools at the top of the page.. Thanks

---

