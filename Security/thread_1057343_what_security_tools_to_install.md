---
title: "what security tools to install"
date: 2009-02-01
forum: Security
---

### Post by tednumber8 on 2009-02-01
I would like to know what security tools I should install on ubuntu.

A list of GUI tools preferably

---

### Post by HermanAB on 2009-02-01
None.

Ubuntu is secure out of the box.  Relax and enjoy it!

Cheers,

Herman

---

### Post by Divider on 2009-02-02
If your worried about security, turn on ufw.

```
sudo ufw enable
```

---

### Post by brian_p on 2009-02-02
> **tednumber8 said:**
> I would like to know what security tools I should install on ubuntu.

What do mean by 'security tools'? In your searches which tools for Linux have attracted your attention?

---

### Post by OrangeCrate on 2009-02-02
Here's a good read on Ubuntu security...

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by tednumber8 on 2009-02-02
I'm not sure If I've been as clear as I meant to be.

I'm looking for security tools, more like monttoring tools, it's a learning process and I feel that getting my hands on any tools that are of interest to me. will keep me ubuntuing for a long time to come.

Any suggestions?

---

### Post by Koori23 on 2009-02-02
John the Ripper (password cracking)(sudo aptitude install john)
**Nmap** (Commandline) **Zenmap** (Gui) port scanning
**ntop** -Monitoring packets in a similar fashion to the "htop" command.
**Etherreal** -Packet capture GUI
**Netstat** command. Default in Ubuntu. This is the tell all of what's going on network wise on your machine. With it's options, you can determine EVERYTHING that's going on in your system. What services are listening, what ports are open and where.. 

Enabling ufw firewall logging would be one tool you can use. That way you can analyze what IP's are connecting to your machine and at what port. 
---Along with logging IP's. You can use WHOIS to determine who it is that's connecting    to you.

You could read about AppArmor profiles (Apparmor is installed by default) and attempt to implement some for Internet facing applications.

In short, NMap and it's GUI variant are very helpful. Firewall logs coupled with WHOIS are very important tools. So, you have many tools at your disposal installed by default or it's REALLY easy to install them with little system footprint.

---

### Post by OrangeCrate on 2009-02-02
See here:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

About half way down that page, is a conversation called "The Ubuntu Mindset". Reading that section should give you some good ideas on monitoring tools you can work with...

---

### Post by kevdog on 2009-02-02
Wireshark is also very helpful for packet monitoring.

---

### Post by cjacobsen on 2009-02-02
Zenmap - A network mapper
GUFW - A GUI for UFW
Nessus - A vulnerability scanner

There are a lot of goof tools that don't come with GUI but logs events for you, like fail2ban, SNORT, UFW, Apache, SSHD

I've written some howto's on most of these applications on my blog if you're interested.

---

### Post by hyper_ch on 2009-02-04
what are you afraid of?

---

### Post by tednumber8 on 2009-02-04
Nothing other than anyone else. I'm just out to learn.

Thanks everyone..

---

### Post by hellz99 on 2009-02-04
if you're opening a port to ssh into your box then denyhosts is great.

---

### Post by tednumber8 on 2009-02-04
> **hellz99 said:**
> if you're opening a port to ssh into your box then denyhosts is great.

I've installed it but don't understand.

Is it only a background running program.

---

### Post by hyper_ch on 2009-02-04
if you are concerned about security don't just install all the things people tell you. First research what those things do.

---

### Post by cariboo on 2009-02-04
If you have set up denyhosts properly, it should locally email you a list of denied hosts. Open a Applications-->Accessories-->terminal and type:

```
mail
```

jim

---

