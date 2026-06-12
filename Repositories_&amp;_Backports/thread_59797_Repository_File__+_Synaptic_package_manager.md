---
title: "Repository File  + Synaptic package manager"
date: 2005-08-25
forum: Repositories &amp; Backports
---

### Post by explosive on 2005-08-25
Hi,

I'm new here (just installed ubuntu today :)). I followed a guide here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)  and changed my sources.list file. After doing this there were far more program patches. (Is this normal?) Also it said that some of the file were not from a trusted site and a malicous user could exploit this, (or words to that effect). So I chickened out and put my sources.list back to the original.  Is this actually a problem, or am I just being silly?

Additionaly when I run 'Synaptic Package Manager' I get this error message:

"W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050129) unstable/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20i386%20Binary-1%20(20050129)_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050129) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20i386%20Binary-1%20(20050129)_dists_unstable_restricted_binary-i386_Packages) - stat (2 No such file or directory)"

It continues to load afterwards, but i'd like to know why it does it.

I hope I posted this in the correct place.

I'd just like to say that overall I am very impressed with ubuntu, I have used Fedora Core 3 in the past, and had all sorts of problems, but ubuntu installed with no problems, it even detected my wirless card and 1280x800 screen res without having to sort it out manually!

---

### Post by Lambert on 2005-08-25
Yes it is. Depending on your sources you have to watch what you upgrade as it break a program. Stick with the ubuntu repositories and you shouldn't have a problem. These are tested by other users. It still gives that warning though if it's outside the official repositories (like universe or back ports)



Read this wiki page on repositories.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)




One of your sources set in your sources.list is the cd/rom drive and you currently don't have your disk in there. You need to go in to your sources.list and # out the lines pointing to your cd drive. 

It just gives that error stating nothing read on the cd drive then moves on to the next source.

---

### Post by explosive on 2005-08-25
[QUOTE=Lambert]Yes it is. Depending on your sources you have to watch what you upgrade as it break a program. Stick with the ubuntu repositories and you shouldn't have a problem. These are tested by other users. It still gives that warning though if it's outside the official repositories (like universe or back ports)



Read this wiki page on repositories.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)




One of your sources set in your sources.list is the cd/rom drive and you currently don't have your disk in there. You need to go in to your sources.list and # out the lines pointing to your cd drive. 

It just gives that error stating nothing read on the cd drive then moves on to the next source.[/QUOTE]
 Thank you for your help :)

BTW, I can't view the link you gave me I get an XML parsing error appear in a pop-up window  :???:

---

### Post by explosive on 2005-08-25
[QUOTE=explosive]Thank you for your help :)

BTW, I can't view the link you gave me I get an XML parsing error appear in a pop-up window  :???:[/QUOTE]
 The xml problem appears to have gone after restarting x-server.

I now get this error message when I run 'Ubuntu Update Manager'.

> "It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.

The following packages are not upgraded:
gaim
gimp
mozilla-firefox
mozilla-firefox-gnome-support
smbclient"

Any idea how to fix it?

I tried 'apt-get dist-upgrade' but nothing was installed and the error remains...

---

### Post by explosive on 2005-08-26
Anyone got any ideas?

I have attached the error message.

---

