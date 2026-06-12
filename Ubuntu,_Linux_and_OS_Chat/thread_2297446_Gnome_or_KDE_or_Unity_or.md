---
title: "Gnome or KDE or Unity or ???"
date: 2015-10-03
forum: Ubuntu, Linux and OS Chat
---

### Post by sanssadness on 2015-10-03
I'm running Ubuntu 14.04. I've been trying to get the correct network manager for an OpenVPN client installed, but I don't know which one is the right one. One page suggested network-manager-openvpn-kde for KDE or network-manager-openvpn-gnome for GNOME.

As an Ubuntu newbie, I have to ask, am I using KDE or GNOME? Or is it Unity? I'm getting so much conflicting information. Which network manager is the right one for me?

---

### Post by mystics on 2015-10-03
If you just got Ubuntu, then you got Unity. If you got something like Kubuntu or Xubuntu, you would get whatever desktop environment came with that. My guess is you're using Unity. In that case, just install network-manager-openvpn.

---

### Post by sanssadness on 2015-10-03
Yea I just got Ubuntu, not Kubuntu or one of the other variants. Is there documentation about packages anywhere? I see a listing of packages on Ubuntu's site, but the packages don't have any descriptions on them. The only sources I know of that describe the functionality of the package are third party sites.

---

### Post by mystics on 2015-10-03
The Ubuntu Software Center should give things like a description and even rating on a lot of programs. The Synaptic Package Manager can also be used for getting descriptions.

---

### Post by Bucky Ball on 2015-10-03
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Which desktop environment is right for you depends on how you like to work. Will make little difference to network manager.

As for your open-vpn issues, post a dedicated thread on that in ***Networking and Wireless*** would be the best plan. Little to do with the desktop environment.

Good luck. :)

---

### Post by night_sky2 on 2015-10-04
Xfce FTW. The only DE that manage to find that perfect balance between customization power, visual appeal and ressource efficiency. It works perfectly on hardware old and new.

---

### Post by mystics on 2015-10-04
I just want to point out that the OP wasn't asking about which desktop environment was best. They were confused about the fact that they were being told to install network managers that had -kde or -gnome appended to the name despite not having either of those DEs. So as much as I want to join in advising Xfce, advising DEs is irrelevant to what the OP was asking for.

---

### Post by deadflowr on 2015-10-04
For all in tents and porpoises, unity is a gnome desktop.
It simply runs it's own user interface vs other gnome desktops.
But the base is gnome.

---

### Post by yoshii on 2015-10-06
in case it wasnt clear from what others wrote above, Kubuntu uses KDE and Xubuntu uses Xfce and Ubuntu uses Unity.  Ubuntu Studio uses Xfce also.  Lubuntu uses LXDE I think.  
Isn't there just something called **network-manager?**

---

### Post by Bucky Ball on 2015-10-06
> **yoshi2 said:**
> 
Isn't there just something called **network-manager?**

Yep. Did you try looking in the repos? It runs in the terminal. If you want a GUI for it, you need to install one, like network-manager-gnome. From Synaptics description of that:

> 
This package contains a systray applet for GNOME's notification area but it also works for other desktop environments which provide a systray like KDE
or Xfce. It displays the available networks and allows users to easily switch between them. For encrypted networks it will prompt the user for the key/passphrase and it can optionally store them in the gnome-keyring.

---

### Post by sanssadness on 2015-10-15
Thanks for all the helpful replies! If any of the posts did not directly address my question, I consider it my fault for not using a better title, which seemed to be asking about desktop environments.

In my defense, I felt using a narrow title asking about only OpenVPN would discourage most posters who could contribute something from viewing this thread in the first place. After all, assuming that the names of the packages describe the desktop environment they're for, I only needed to know the right desktop environment to install the right package. So ultimately, the question is really about what desktop environment I have, and your replies certainly helped answer that.

network-manager-openvpn was the right package for Ubuntu, but I believe it also installed network-manager-openvpn-gnome as a dependent package (it's been too long, but marking network-manager-openvpn for removal in Synaptic Package manager also requires marking network-manager-openvpn-gnome for removal).

---

