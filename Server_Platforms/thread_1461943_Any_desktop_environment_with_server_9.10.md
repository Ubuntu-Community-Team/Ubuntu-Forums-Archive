---
title: "Any desktop environment with server 9.10?"
date: 2010-04-24
forum: Server Platforms
---

### Post by victor_sk on 2010-04-24
Hi everyone,

I am a different distribution Linux user but considering to install Ubuntu Server 9.10 to run my personal website.

Question about Ubuntu Server version - does it come with some desktop environment like Gnome or KDE?  I would be running Ubuntu Server on my home machine so it would be a nice bonus if I could use it to browse internet or check email.

Thanks,
Victor.

---

### Post by windependence on 2010-04-24
No, it doesn't but you can install one (not recommended). 

If I were you, I would just use the desktop version and serve your site from there. The benefits you gain from using the server edition are geared toward heavy traffic more CPU intensive applications than you will ever need even if your site gets 15,000 page views per day. 

The GUI is not included in the server version for a reason: security & overhead. It is not needed to run your web server. I understand the desire to open a browser once in a while. For a great setup on one machine you might want to consider virtualizing using VBox or Vmware Server and you can have the server version AND the desktop running on one box!

-Tim

---

### Post by Vegan on 2010-04-24
I suggest webmin as an alternative to a GUI. I use a GUI as a backup only after I have installed the server.

I need a backup GUI but I have enough RAM to not worry.
:guitar:

---

### Post by windependence on 2010-04-24
> **Vegan said:**
> I suggest webmin as an alternative to a GUI. I use a GUI as a backup only after I have installed the server.

I need a backup GUI but I have enough RAM to not worry.
:guitar:
Did you read his post? He wants to be able to open a BROWSER on the server. WebMin isn't gonna do that for him.

-Tim

---

### Post by utnubuuser on 2010-04-25
Virtual sounds like the way to go.  -- on a side note, you moght want to have a look at Turnkey Linux - Ubuntu based server appliances - very, very handy.

---

### Post by Cosma on 2010-04-25
> **windependence said:**
> 
For a great setup on one machine you might want to consider virtualizing using VBox or Vmware Server and you can have the server version AND the desktop running on one box!


i am also 100% for the virtualization idea. but there is one thing that always makes me wonder when reading this forum. why do people never suggest to run kvm?
it's the default virtualization platform of ubuntu and runs just as good as vmware or virtualbox.

---

### Post by koenn on 2010-04-25
doen't kvm require a CPU with virtualiation support ? 
I imagine fairly recent server hardware will include that, but I 'm not to sure you'll get it on mainstream desktops and laptops.

---

### Post by Cosma on 2010-04-25
> **koenn said:**
> doen't kvm require a CPU with virtualiation support ? 
I imagine fairly recent server hardware will include that, but I 'm not to sure you'll get it on mainstream desktops and laptops.

you need intel vt or amd-v support but that is included in nearly all current cpu's and even many older ones (like some pentium4 already).

vmware and virtualbox both can run vm's without that but the performance isn't very great so i wouldn't really do any virtualization without intel vt or amd-v.

---

### Post by windependence on 2010-04-26
> **Cosma said:**
> you need intel vt or amd-v support but that is included in nearly all current cpu's and even many older ones (like some pentium4 already).

vmware and virtualbox both can run vm's without that but the performance isn't very great so i wouldn't really do any virtualization without intel vt or amd-v.
I usually don't mention anything other than VMware ESXi, but I thought I'd be nice and mention VBox while I was at it. So much for trying :-) I don't want to start a virtualization war here but VMware is light years ahead of the others in terms of features and stability. Ah yes and bare metal ESXi is free (as in beer) too. Performance is just fine with the others as the kernel is optimized for virtualization in general.

-Tim

---

### Post by ipina on 2010-05-10
I'm somewhat confused. As far as I know, Webmin is a web-based interface which do needs a web browser.

---

### Post by TheFuturian on 2010-05-10
> **ipina said:**
> I'm somewhat confused. As far as I know, Webmin is a web-based interface which do needs a web browser.

Yeah, but most people will use a web-browser on a remote machine, not on the server itself..

---

