---
title: "Virtual Windows guest cannot reach Ubuntu host private LAN"
date: 2015-02-02
forum: Virtualisation
---

### Post by Leandro_Martinez on 2015-02-02
Hello everyone,
Today I did setup without any problem WinXP as guest on an Oracle VM@Ubuntu 12; the guest got access to inet immediately via the auto LAN the Oracle VM setups, meaning, I can ping 8.8.4.4 from inside the guest without problem, but *cannot *ping private IP adresses like 192.168.101.108 which is in this case a printer (I can do that from Ubuntu, the host). I have been reading about bridging connections, but I'm not really sure if that's the solution for this problem; also, since Unity, I have not been a much fan of Ubuntu, so there are somethings I probably don't know, but I need to make this work because of my job; could anyone help me here please?

---

### Post by TheFu on 2015-02-03
Welcome to the forums.

Don't use NAT, use bridge mode.

You don't have to use Unity. There must be 50 other GUI options out there. No need to reinstall the OS either. Just install a different desktop, logout, select the other desktop from the login page, then login.  To prevent different settings from trashing settings for different desktops, it is best to create a new userid for each trial desktop as you experiment.

---

### Post by Leandro_Martinez on 2015-02-03
Thanks for the help TheFu; I'm currently not in the box with the problem but I'll try posting from there to add more details. What I remember however, is that when I selected "Bridged" in the first tab of network configuration, it wouldn't let me choose it because there was "no adapater associated" or something like that. Again, I'll try to post a screenshot from the computer with the problem.
Anyway, is there any special configuration I should setup in the Oracle VM in order to be able to use bridged mode? Thanks a lot.

Here's a screenshot of the Virtualbox's window and the problem when I try to choose bridge (sorry it's in Spanish, Adaptador puente = Bridged device)

[IMG]http://s29.postimg.org/a2fjd6flj/Captura_de_pantalla_de_2015_02_03_09_26_04.png[/IMG]

---

### Post by TheFu on 2015-02-03
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) . 
If any of the other network tabs are enabled, disconnect the cable for those.
Also - pay careful attention to the type of adapter as spelled out in the link provided above. Of course, there are always the vbox instructions too: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

Ah ... WinXP.  Support ended for that about a year ago. Time to retire it. Really, you shouldn't allow it on any network at all, ever.

---

### Post by Leandro_Martinez on 2015-02-03
Thanks a lot for your help.... I was able to connect a printer from the WinXP guest using NAT but after that I had problems with sharing a folder via Samba because the VirtualBox couldn't recognize the installed "guest setup" or something.

Anyway, I solved the problem creating another VirtualBox but from root, then I was able to use Bridged connection; then the guest got a direct DHCP IP and could browse all the LAN and Internet.
So, in the end, if someone has this kind of problem again, be sure to be root to avoid lot of problems.

---

### Post by TheFu on 2015-02-04
I think just being in the **vboxusr** group will let this work. [http://askubuntu.com/questions/377778/how-to-add-users-to-vboxusers](http://askubuntu.com/questions/377778/how-to-add-users-to-vboxusers)

---

