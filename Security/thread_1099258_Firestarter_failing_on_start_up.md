---
title: "Firestarter failing on start up"
date: 2009-03-18
forum: Security
---

### Post by mhinder on 2009-03-18
Hello,
I am dual booting windows vista and ubuntu on my laptop and when I boot ubuntu it loads like normal but after a while it lists all of the scripts (I think) and it says "OK" for all of them except for Firestarter for which it says "fail" in red letters. Any idea of what I can do to fix this?

---

### Post by lovinglinux on 2009-03-18
Does it stall there or you are able to get into the login screen?

I don't know what could be causing this, but you could try uninstalling Firstarter and running UFW instead, which is the default firewall manager now. If you need a GUI, then you could install GUFW. Unless you really want Firestarter. Unfortunately, I can't help you with that.

---

### Post by bodhi.zazen on 2009-03-18
This is getting to be more and more common with firestarter.

It has not been maintained since 2005 and is showing it's age.

Most commonly this happens when you have configured a complex firewall or have multiple interfaces, some of them may be virtual such as VMWare.

Why do you need a firewall ?

+1 for ufw / gufw.

---

### Post by lovinglinux on 2009-03-18
I guess you are just switching to Ubuntu, probably from Windows. When I switched, I loved Firestarter, because it made me feel like running a Windows-like firewall (I was an avid Comodo user). But soon I realized that there are other ways of setting up a firewall. If don't want to have much trouble, than ufw is great option, but if you are willing to learn some cool new stuff and have all the control on your hands, then you should try to learn about iptables. This is the real firewall that comes with Ubuntu by default. Firestarter and UFW are just simplified firewall managers, which create rules for the iptables.

More about this at [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

There is also [this excellent tutorial about Ubuntu security]("http://ubuntuforums.org/showthread.php?t=510812") written by bodhi.zazen

---

### Post by mhinder on 2009-03-19
I installed Firestarter before finding out that Ubuntu had a built in one (a habit from being used to Windows). I'll try uninstalling it and see what happens. I could never figure out how to work it anyhow. After I uninstall this will I still have a firewall protecting me?

---

### Post by lovinglinux on 2009-03-19
> **mhinder said:**
> I installed Firestarter before finding out that Ubuntu had a built in one (a habit from being used to Windows). I'll try uninstalling it and see what happens. I could never figure out how to work it anyhow. After I uninstall this will I still have a firewall protecting me?

No. You must understand that Ubuntu comes with a firewall called iptables, but it hasn't any rules to block traffic, so it will allow all traffic by default. You can create these rules with command-line or you can use firewall managers. Firestarter and UFW are firewall managers, which means they are tools that allow you to create firewall rules for iptables without actually knowing how to use iptables commands.

On thing that is interestingly different in Linux is that you can have several different frontend applications to control the same program (the backend). So basically, Firestarter and UFW are different frontend applications that use the same firewall backend (iptables). There are others, but those are the most popular.

The same happens with media players for example. You can use gnome-mplayer frontend, which is different than smplayer frontend, but both depend on mplayer backend, which is actually the media player.

---

### Post by lovinglinux on 2009-03-19
Just to complement my previous post...

To be protected you need to create the firewall rules by command-line or install a firewall manager. Since Firestarter is not working, I suggest installing ufw and gufw. To install them, run the following command in the terminal:

```
sudo apt-get install ufw gufw
```

Ufw is probably already installed, but I don't if gufw is. Anyways, the command doesn't mess anything if they are already installed.

After installation, you can launch the firewall manager through "Applications >>> System >>> Administration >>> Firewall Configuration" or you can run the following command:

```
gufw
```

Make sure you uninstall Firestarter, otherwise they can conflict with each other.

---

### Post by mhinder on 2009-03-19
Thank you for all of your help, that fixed everything.

---

### Post by hyper_ch on 2009-03-19
are you behind a router? If so I doubt if you even need to bother about a firewall on the computer itself. Rather configure the router.

---

