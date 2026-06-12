---
title: "Unable to add Universe and Multiverse"
date: 2005-11-19
forum: Repositories &amp; Backports
---

### Post by Il_Tuo_Nome on 2005-11-19
Upon trying to add Universe and Multiverse as per [http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-whatis]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#synaptic-whatis")
I was unsuccessful due to not being able *[COLOR="DarkRed"]Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe)  and Non-free (Multiverse)[/COLOR]*. 'Offiially Supported and Restricted Copyright are already check, the checkmarks I added would not stay. Nor did all repositories become check marked as suggested by #6. of that section.

[B]2.3.	

How do I add Universe and Multiverse?
	

By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

[/B]   [B]1.Start Synaptic by selecting System->Administration->Synaptic Package Manager from the desktop menu system.
   2.In Synaptic choose Settings-> Repositories.
   3.Click the Settings button.
   4.Tick Show disabled software sources, then click Close.
   5.On the Repositories dialog box click Add. There are three separate repositories; Breezy Badger, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes.
   6.You should now see checkboxes next to each repository, scroll through the list and ensure they are all checked. 

[/B]





thank you

---

### Post by geniium on 2005-11-19
have you tried to edit directly /etc/apt/sources.list ? read the forum on, you have many subject about how to do this. and it should work.

---

### Post by aysiu on 2005-11-19
Read my sig.

---

### Post by rjwood on 2005-11-19
just do the following from a terminal
```
sudo gedit /etc/apt/sources.list
``` it will ask for your password-then a file will pop up--make it look like this by editing yours or you can copy and paste mine over yours
```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted  
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") breezy-extras main restricted universe multiverse
```

then
```
sudo apt-get update
``` ```
sudo apt-get upgrade
``` good luck:)

---

### Post by Il_Tuo_Nome on 2005-11-19
Thank you guys :). By doing that, am I right to assume I don't need to go in to *[COLOR="SeaGreen"]System>Administration>Synaptic Package Manager[/COLOR]* to do it the way I was? Or is that still necessary?

Thanks again fpr the help :)

---

### Post by aysiu on 2005-11-19
Synaptic Package Manager is just a graphical version of apt-get.

---

### Post by Il_Tuo_Nome on 2005-11-19
understood,

thanks again for the help :)

---

