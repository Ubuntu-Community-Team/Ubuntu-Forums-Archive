---
title: "[ubuntu] Two NetworkManager icons after upgrading to Trusty"
date: 2014-03-07
forum: Ubuntu Development Version
---

### Post by toxic-hero on 2014-03-07
since i upgraded to Trusty i have two networkmanager icons on my panel. is this tamporary, will one of them go away with the release of Trusty, or is there something wrong here that needs to be fixed?

[ATTACH=CONFIG]250918[/ATTACH]

---

### Post by Iowan on 2014-03-07
Moved to Ubuntu +1

---

### Post by Mateusz Stachowski on 2014-03-07
That second network icon is from Unity 8. This is the package: [indicator-network]("http://packages.ubuntu.com/trusty/indicator-network"). If you don't have Unity 8 installed it is most likely safe to remove that package.

The default NetworkManager icon comes from: [network-manager-gnome]("http://packages.ubuntu.com/trusty/network-manager-gnome").

---

### Post by wgarcia on 2014-03-07
Shouldn't it be a bug that it shows in Unity 7?

---

### Post by toxic-hero on 2014-03-07
> **Mateusz Stachowski said:**
> That second network icon is from Unity 8. This is the package: [indicator-network]("http://packages.ubuntu.com/trusty/indicator-network"). If you don't have Unity 8 installed it is most likely safe to remove that package.

The default NetworkManager icon comes from: [network-manager-gnome]("http://packages.ubuntu.com/trusty/network-manager-gnome").

hey, thanks for suggestion! the problem is that if i try to uninstall indicator-network with synaptic it also want to uninstall several other packages that i need (ubuntu-system-settings, account-plugin-ubuntuone...). i also found out that i have at lest some packages of unity 8 installed (unity8, unity8-private, unity8-fake-env). any suggestion how to uninstall not needed packages (the indicator especially) without breaking something?

---

### Post by Mateusz Stachowski on 2014-03-07
If you want to have Unity 8 than for all I know you can't remove indicator-network.

The ubuntu-system-settings is also a package needed by Unity 8. The system settings for regular Unity 7 in 14.04 are provided by unity-control-center.

---

### Post by Alan F on 2014-03-07
This happened to my install 3-4 weeks ago following an update.

Easiest way to resolve is to stop the 'network' application in startup applications.

When you run 'startup applications' you will find that the standard ones are invisible. To see these, see instructions at ...

[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

Following this, unticking 'network', reboot, and bingo, only one icon.

---

### Post by grahammechanical on 2014-03-07
Do you have the Proposed repository enabled? If so you will get stuff like that. I installed Unity 8 session manager and I got the phone/tablet Network Manager icon as well as the standard Network Manager icon.

It is intended that 14.04 users will have the option of loading into a Unity 8 review session but whether that option will be provided by default or the user will need to install something, I cannot say. But this stuff is being offered for testing through the proposed repository.

If you look in the Dash you will also find Browser, the Ubuntu Web Browser from the phone/tablet code base. That is installed now by default. It is all part of the convergence strategy that intended to be completed by the release of 14.10. So, expect to see a lot more of this kind of thing, especially if we keep on the development branch.

Oh, by the way, over the last few days I have been getting Click packaging stuff as well.

Regards.

---

### Post by toxic-hero on 2014-03-07
> **Mateusz Stachowski said:**
> If you want to have Unity 8 than for all I know you can't remove indicator-network.

The ubuntu-system-settings is also a package needed by Unity 8. The system settings for regular Unity 7 in 14.04 are provided by unity-control-center.

no, i don't really want to have unity 8, it was just installed when i upgraded to Trusty. do you know how to uninstall it the easy way?


> **Alan F said:**
> This happened to my install 3-4 weeks ago following an update.

Easiest way to resolve is to stop the 'network' application in startup applications.

When you run 'startup applications' you will find that the standard ones are invisible. To see these, see instructions at ...

[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

Following this, unticking 'network', reboot, and bingo, only one icon.

the problem with this is that it disables the wrong (unity7) icon. and unity8 one doesn't fully work so it can't really replace the old one for me.
also unity7 network isn't present in the startup applications.

> **grahammechanical said:**
> Do you have the Proposed repository enabled? If so you will get stuff like that. I installed Unity 8 session manager and I got the phone/tablet Network Manager icon as well as the standard Network Manager icon.

It is intended that 14.04 users will have the option of loading into a Unity 8 review session but whether that option will be provided by default or the user will need to install something, I cannot say. But this stuff is being offered for testing through the proposed repository.

If you look in the Dash you will also find Browser, the Ubuntu Web Browser from the phone/tablet code base. That is installed now by default. It is all part of the convergence strategy that intended to be completed by the release of 14.10. So, expect to see a lot more of this kind of thing, especially if we keep on the development branch.

Oh, by the way, over the last few days I have been getting Click packaging stuff as well.

Regards.

no, i don't have the proposed repository enabled.

---

### Post by toxic-hero on 2014-03-07
allright, i said enough is enough, uninstalled those packages and everything is just fine now. unity8 waiting for the autumn... thanks guys for your help!

---

