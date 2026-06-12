---
title: "Problem at login time"
date: 2015-03-06
forum: Ubuntu Studio
---

### Post by massimo7 on 2015-03-06
Hi,
I have installed Ubuntu studio 14.04 (with *Internet available*) on a HP 250 G1, bought a year ago with Ubuntu 12.04 pre-installed.
I can login as Guest, but not as my administrator user: there's a loop that re-presents the login box!

I tried some suggestions found in the network, but nothing!

Then I re-installed Ubuntu studio, but without Internet connection.
I can login as Guest; when I login as my administrator user, an empty desktop is shown, with the wallpaper but without icons on the desktop and without app bar. It is not possible to do anything!
I'm very frustrated! Can anyone help me? Thank you very much, Massimo.

---

### Post by phedup on 2015-03-08
Hi,

When you installed and re-installed 14.4, it gives you choices to 1. log in automatically, 2. log in using password. Did you pick 1. Log in automatically?  If so, then your system should boot and not ask any login questions.  Also, when one installs Ubuntu from a live CD/DVD, it suggests that you be already logged onto the internet before the install.  This is true for Ubuntu Trusty Tar 14.4, and I assume it's true for Ubuntu Studio too, but maybe I'm wrong. 

Also, people usually avoid installing as root unless they are super, super experienced.  But since there are certain times when one needs to make the system think they're root, such as when installing software from the terminal, then they use 'sudo,'  eg: "~$ sudo apt-get"  Sudo makes you a temporary root user, but only in the context of that specific operation.  It's really much safer.

I hope this addresses your problems.

---

### Post by massimo7 on 2015-03-08
I haven-t understood completely your answer, however I choiced to login **with** password.

---

### Post by massimo7 on 2015-03-09
How is possible that tha system allow me enter as Guest and not as my admin account?
So, it's not a driver question!
Perhaps is it a problem in the installation Files? Something wrong in the files permission?

---

### Post by massimo7 on 2015-03-09
The same thing happens if I install Xubuntu 14.04.
But then is XFCE that causing these troubles?

---

### Post by marseille2 on 2015-03-10
Sounds like your desktop is messed up. Do you only have XFCE installed or can you change to another desktop at the login screen? 


If you do have another desktop, login to it and see if everything is there. (This is *NOT* a solution, but a quick way to make sure you do not have an authentication problem, and that it's just a problem with the desktop).


If you find that XFCE is your only desktop, and you can login (even if it's plain wallpaper with no icons or other settings) ... hit [ALT+F1] to see applications OR [ALT+F2] to run only 1 program (see more [hot-keys]("https://help.ubuntu.com/community/KeyboardShortcuts")).


[INDENT=3]To open the terminal in a blank desktop:

[**ALT+F2**] > then type: **xterm**
[/INDENT]
 


If that fails, and you can't do either ... try to read the how-to [manual]("https://wiki.xfce.org/howto") at XFCE, and figure out which file(s) are ruined, *before* you consider reinstalling your desktop ... or installing a different desktop alongside of your old one.


I only say that because I've ruined my desktop many times, and if there's one thing I've learned... Be very careful about installing multiple desktops as a solution. A lot of the times, it's just a case of ruining a configuration file. For XFCE4, check the directory in .config (**/home/userName/.config/xfce4**).


-----

Further Reading: 

[LIST]
[*]How to [purge]("http://askubuntu.com/questions/429148/how-do-i-remove-xfce-from-my-computer") (remove) XFCE4
[*]How to [install]("http://www.enqlu.com/2014/03/how-to-install-xfce-desktop-on-ubuntu-14-04-lts-trusty-tahr.html") XFCE4
[/LIST]

---

### Post by massimo7 on 2015-03-10
Thanks for advice, **marseille2**.
I only have XFCE,
Yesterday I restored Ubuntu to work; next week-end I'll try your advice and then I'll tell you the result.
Thank you very much. Bye.

---

### Post by massimo7 on 2015-03-17
I solved the question with the command:

sudo chown -R $USER:$USER /home/loginname

---

