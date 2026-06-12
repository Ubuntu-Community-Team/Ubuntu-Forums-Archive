---
title: "Mozilla Firefox 1.5.0.4 Released.Jus"
date: 2006-06-01
forum: The Cafe
---

### Post by Rackerz on 2006-06-01
Just thought I'd let you guys know ;).

---

### Post by BWF89 on 2006-06-03
Firefox's automatic updater notified me yesterday. That thing sure saves alot of time. Althuogh I hate it that the people that make Statusbar Clock extension never update their MAXVERSION line of code forcing me uninstall the extension and reinstall while having the override max version compatibility check box checked. MR Tech's Local Install extension sure comes in handy for that. Before I heard of that I had to manually openup the extension file archive with 7-Zip and change the MAXVERSION piece of code myself.

---

### Post by greggh on 2006-06-03
When will I be able to get it for xubuntu? :confused:

---

### Post by jdong on 2006-06-03
A Launchpad bug ([https://launchpad.net/distros/ubuntu/+source/firefox/+bug/48043](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/48043)) has already been filed for the inclusion of Firefox 1.5.0.4. Since it's a security update, Dapper will probably receive this version (or the relevant security patches applied to the Dapper version) as soon as it passes quality inspection.

So, patience, and it will be in Ubuntu repositories :)

---

### Post by greggh on 2006-06-03
I'm new to (x)ubuntu and Linux in general so I'm sorry if this is a dumb question. When the new FireFox package is made available will it be good for all the versions of ubuntu (kubuntu and xubuntu as well)? Or are there seperate repositories and packages that show up in Synaptic depending on the particular flavor of ubuntu you're using?

---

### Post by John.Michael.Kane on 2006-06-03
greggh patches/security update are applied across the board for (K)(X)Ubuntu.

---

### Post by jdong on 2006-06-03
All the Ubuntu/Kubuntu/Xubuntu all use the same set of repostories, just a different set of packages and default settings (artwork, themes, etc) are installed by default. The Firefox update will apply to all editions of Ubuntu that use Firefox.

---

### Post by John.Michael.Kane on 2006-06-03
jdong guess the way i said was not good?

---

### Post by greggh on 2006-06-03
[QUOTE=SD-Plissken]jdong guess the way i said was not good?[/QUOTE]

I think you said it fine. But jdong added some more info. From what I understand from what he said that although they all use the same repositories, depending on what flavor of ubuntu you are using you are going to see different packages available to you in Synaptic? Do I have that right or am I still confused?

---

### Post by John.Michael.Kane on 2006-06-03
greggh no your not confused your right.

---

### Post by jdong on 2006-06-03
[QUOTE=SD-Plissken]jdong guess the way i said was not good?[/QUOTE]

No, no, you answered his question wonderfully. I just wanted to take the opportunity to go on a little *buntu rant.


Too often I hear people trying to refer to KUbuntu as a different distribution than Ubuntu, etc. In reality, they are **all the same distribution**. For example, here's how you do each install manually:

Start with the Ubuntu "minimal" base install from the Server CD, which just installs the textmode portion of the OS.

For Ubuntu, install the "ubuntu-desktop" package
For KUbuntu, install the "kubuntu-desktop" package
For Xubuntu, install the "xubuntu-desktop" package.


In other words, all three are the same exact distribution, just with a different set of software pre-installed by default. Ubuntu pre-installs GNOME while KUbuntu pre-installs KDE and XUbuntu pre-installs XFCE.

They all work off the same repository, as in you see the **same set of packages** in Synaptic in all three. You can turn Ubuntu into KUbuntu just by installing kubuntu-desktop, or do a "Ubuntu Ultimate Edition" install by installing all three packages.


Many other Linux distributions have setup programs that allow you to customize what gets installed by default. We find that to be unnecessarily cumbersome, time-consuming, and utterly confusing for new users, so we offer these three default configurations so you can get a system up and running ASAP. Later on, there's a world of possibilities (often much more than the 5-CD distributions offer) in the Ubuntu repositories.


So, Ubuntu, XUbuntu, and KUbuntu are all the same distribution that use the same repostories. The difference is in what packages the setup program automatically installs for you.

---

### Post by John.Michael.Kane on 2006-06-03
jdong I get where you going with it now. the only thing that that diffrent is the Desktop environment other wise the underlying code is the same for all. just wanted to make sure i had answer the question correctly.

---

### Post by n2diy on 2006-06-03
My Firefox hasn't updated, and I haven't received any notifications. I manually ran the Update Manager, and I'm told Breezy is up to date? Is there something I need to configure?

Darryl

---

### Post by aysiu on 2006-06-03
[QUOTE=n2diy]My Firefox hasn't updated, and I haven't received any notifications. I manually ran the Update Manager, and I'm told Breezy is up to date? Is there something I need to configure?

Darryl[/QUOTE] The latest version available in Breezy is 1.0.8.

If you keep Breezy, you'll never get the latest Firefox from the repositories.
Try [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) instead.

---

### Post by jimrz on 2006-06-03
[QUOTE=aysiu]The latest version available in Breezy is 1.0.8.

If you keep Breezy, you'll never get the latest Firefox from the repositories.
Try [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) instead.[/QUOTE]

aysiu-

   Does your FF script work for dapper? If not, are you planning to create one that does?

   Sorry, I am not really lazy. I just do not yet have the skills (or maybe confidence in what I do have) to create one. That and the fact that your breezy version worked so beautifully are what prompted the questions.

jim

---

### Post by jdong on 2006-06-03
Guys, have some patience... These security updates will hit Ubuntu repositories, just give it some time. We can't just shove updates into the repositories the moment they come out with no testing... that could create a lot more problems than it'd solve.

Just sit tight, keep your cool, and let things run their course.

---

### Post by aysiu on 2006-06-03
[QUOTE=jimrz]aysiu-

   Does your FF script work for dapper? If not, are you planning to create one that does?

   Sorry, I am not really lazy. I just do not yet have the skills (or maybe confidence in what I do have) to create one. That and the fact that your breezy version worked so beautifully are what prompted the questions.

jim[/QUOTE] Well, at this point, it's no longer my script--nanotube has taken over and improved it amazingly.

It now works on Dapper and Breezy. It now asks what locale you want. It checks to make sure it's installing the latest version. The script is quite sophisticated after nanotube's changes.

---

### Post by jimrz on 2006-06-04
[QUOTE=aysiu]Well, at this point, it's no longer my script--nanotube has taken over and improved it amazingly.

It now works on Dapper and Breezy. It now asks what locale you want. It checks to make sure it's installing the latest version. The script is quite sophisticated after nanotube's changes.[/QUOTE]

Thanks aysiu...is it still the one on psychocats.net?

---

### Post by aysiu on 2006-06-04
[QUOTE=jimrz]Thanks aysiu...is it still the one on psychocats.net?[/QUOTE] I've now updated my [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) page to link to nanotube's script (the new script is at a very hard-to-remember URL).

---

### Post by jimrz on 2006-06-04
[QUOTE=aysiu]I've now updated my [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) page to link to nanotube's script (the new script is at a very hard-to-remember URL).[/QUOTE]

thank you

---

### Post by jdong on 2006-06-04
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/48043](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/48043)

> 
Hi,

John Dong [2006-06-04 20:30 -0000]:
> This is a security issue. Is there any plan to include this in dapper-
> security yet?

Yes, very soon (next week).


That's from Martin Pitt, he's the top dog when it comes to security updates :)

---

