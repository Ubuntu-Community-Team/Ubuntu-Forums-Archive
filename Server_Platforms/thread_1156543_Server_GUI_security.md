---
title: "Server GUI security"
date: 2009-05-11
forum: Server Platforms
---

### Post by dearmrdear on 2009-05-11
I'm still learning to cli and doing better everyday, but I still need a gui at my present level of abililty. My question is:  can I uninstall the gui after I'm done with the "training wheels"? I've read a lot about gui's being unessesary security risks so would uninstalling them return U-server to the original security status?

Also:
If possible can anyone explain to a noob what the security risks are with a gui?
Thnx

---

### Post by PacSci on 2009-05-11
I'm not sure exactly what security risks having a GUI involves - probably involving the possibility of someone intercepting your X Server, but that could stilll happen with a CLI. Basically, it's just that there are more places for a cracker to launch an attack against.

As for removal, it depends on what desktop you're using. The easy way is "sudo apt-get purge xorg" which disables your X server and makes it impossible to log in to a GUI, but that will leave remnants of the desktop like GConf, Xfconf, installed apps, session managers, etc. scattered about, which you'd have to track down manually. If you can find them, there are some load-bearing packages like "libgtk2.0-0" or "gconf2-common" that will take out most of your GUI, but like all load-bearing weights, they can take out some other important stuff too.

---

### Post by andrea000 on 2009-05-12
A desktop install of Ubuntu will be able to do everything the server can. You could potentially just 
install the desktop and then add the server apps you want on the local machine.You could also install
a desktop and disable X by default then you can start and stop it when you need to.

---

### Post by netJackDaw on 2009-05-12
One few important remarks! A server should only expose the services it is meant to serve, having unnecessary services and applications installed only makes the attack surface of the server larger. This is also reflected in the release support time frames for desktops and servers. The LTS support time frame for servers is 5 years and for desktops only 3 years. If you install desktop components to your server they are only supported for the shorter time frame.

---

### Post by dearmrdear on 2009-05-12
Correct me if I'm wrong (Please!) Isn't the basis of Ubuntu desktop the same as server but with X and similar apps? So if I was to one-by-one uninstall those apps that are not used by the server (multimedia etc.) I would get down to a basic server? This is of course keeping those apps that are necessary to run a home file server (samba, ssh, etc.)
The reason was that Ubuntu desktop found and mounted my second hard drive eaisier that I could from the command line, I'm slowly getting better I just want it up and running quiclky.

---

### Post by netJackDaw on 2009-05-12
Essentially the desktop and server editions are the same but the kernel for the server edition have other optimizations than the desktop version. Check this article: [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

### Post by dearmrdear on 2009-05-13
Thanks for the help everyone! I'm learning to use Ubuntu/linux with the desktop version and will be switching to the server version soon. I've only set-up a home type file server, nothing exotic like LAMP, Email etc. Thanks again :biggrin:

---

