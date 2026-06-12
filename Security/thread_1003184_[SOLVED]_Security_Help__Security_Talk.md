---
title: "[SOLVED] Security Help | Security Talk"
date: 2008-12-05
forum: Security
---

### Post by Valtiel on 2008-12-05
I recently installed Ubuntu 8.10 making it my fist and hopefully full dive into Linux/Ubuntu. 

In my quest to educate myself about Linux/Ubuntu, I came across "The Big Ol' Ubuntu Security Resource" found at [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

While the english part of the article sounds nice in all its ways, the technical talk part of it not so much since i can't understand it. I'm here ask you for you help so I can understand these commands, what they do/mean. Moreover, I would like to know if the suggestions and steps described on the article are necessary. 

The following is from the article. In bold is the commands that I have no idea about what they really do. By that I mean, I want to make sure that these commands do what they article says they do.

---From article---

Modifying Default Settings

The first set of basic critical changes requires you to modify three insecure default system settings:

    * Reconfiguring shared memory
      Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:

      tmpfs /dev/shm tmpfs defaults,ro 0 0
    * Disabling SSH root login
      Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:

      PermitRootLogin yes

      to

      PermitRootLogin no
    * Limiting access to the "su" program
      Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:

      sudo chown root:admin /bin/su sudo
      chmod 04750 /bin/su

---

### Post by OrangeCrate on 2008-12-05
If you're interested, a simpler discussion of Ubuntu security can be found here:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by Valtiel on 2008-12-05
> **OrangeCrate said:**
> If you're interested, a simpler discussion of Ubuntu security can be found here:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

Thanks for the link. 

As I was reading the article, I found the following

[INDENT]By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open.
Address : <http://psychocats.net/ubuntu/security#bestpractices>[/INDENT]

That contradicts another article I was reading earlier, which said that by default Ubuntu allows all traffic

[INDENT]Iptables is a firewall, installed by default on all official Ubuntu distributions (Ubuntu, Kubuntu, Xubuntu). When you install Ubuntu, iptables is there, but it allows all traffic by default. 
Address : <https://help.ubuntu.com/community/IptablesHowTo>[/INDENT]


Does this make any sense or do I need a clarification as far as "allows all traffic by default" goes. If so, can you clarify this to me?

In the HowTo iptables they mention Ubuntu 8.04 was this changed for Ubuntu 8.10?

---

### Post by Kinstonian on 2008-12-05
By default, Ubuntu doesn't have any services accepting remote network connections.  While it also installs a firewall (iptables), that firewall isn't enabled and filtering traffic unless you configure it otherwise.

---

### Post by Valtiel on 2008-12-05
> **Kinstonian said:**
> By default, Ubuntu doesn't have any services accepting remote network connections.  While it also installs a firewall (iptables), that firewall isn't enabled and filtering traffic unless you configure it otherwise.

I was trying to set up iptables, but the whole terminal and commands is something that I stop interacting with years ago. [I blame windows lol] so getting back to it has been kind of hard specially with unknown commands.

Reading the artilce at [http://psychocats.net/ubuntu/security#bestpractices](http://psychocats.net/ubuntu/security#bestpractices) I came to find out that the firewall software int he repository use iptables thus giving iptables a GUI [good news for me]

Now in the article it says that Firestarter is for GNOME & Guarddog is for KDE. In an earlier thread I made, I was told that while Firestarter is an outstanding firewall software, the project is no longer being supported. I would like to install a software that is still supported by its developers.

I have ubuntu 10 running GNOME. Can I run Guarddog? I see it come up in the repository when I search for "Firewall"

---

### Post by Kinstonian on 2008-12-05
Try the GUFW...

---

### Post by lovinglinux on 2008-12-06
> **Valtiel said:**
> Does this make any sense or do I need a clarification as far as "allows all traffic by default" goes. If so, can you clarify this to me?

By default, Ubuntu allows all traffic, but since there isn't any service listening to ports by default, the ports are indeed closed. The traffic sent to your machine will pass through the firewall but won't go anywhere after that.

A port closed is different from a "stealth" port. Closed means that the connection attempt reached the machine, but wasn't able to enter the port. Is like someone knocking on your door in the front yard but there is nobody in the house to open the door. When you have a "stealth" port, then the machine trying to connect doesn't know if your machine actually exists. Is like someone looking for your house with your address, but he can't find the house because it's invisible.

When your firewall is active, the ports can be opened, but you can't reach them. Is like a house with open ports and some children playing in the doorstep, but there is a concrete wall surrounding the house, so you can't see what is happening inside or enter it, unless someone from inside invites you.

When you configure the firewall to drop packages, then the wall (and everything behind it) is also invisible. When you configure the firewall to reject packages, then is like when you have a sign in the wall entrance saying "Private property. No trespassing!" 

You should only be concerned with firewall traffic if you open ports, like when you run a server or a p2p application. Nevertheless, I keep my firewall up and running all the time, even behind a router with closed ports. Former Windows user paranoia? Maybe :)

Additionally, I have also [[COLOR="Red"]**moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/") running all the time. In my opinion, security is never too much.

> **Valtiel said:**
> Now in the article it says that Firestarter is for GNOME & Guarddog is for KDE. In an earlier thread I made, I was told that while Firestarter is an outstanding firewall software, the project is no longer being supported. I would like to install a software that is still supported by its developers.

There are a lot of discussions here in the forum about if Firestarter is being developed or not. Some people say "its not" because it doesn't need further development, but the web site is updated. So, Is not like a children left alone in a basket on your doorstep. Is more like a grown up young adult which still have contact with it's parents, but has a well established personal life. Which doesn't mean he can't screw his life in the future and need support from his parents to get back on track. (I feel so educational today :) ).

Some people say there are issues when you run the Firestarter, because it runs as root and have a bug that could be exploited to gain root access to your machine. But as long as you use Firestarter to configure the iptables, then close the GUI you should be fine. The iptables will do it's job in the background and it's only the GUI which runs as root. So basically, Firestarter and ufw/gufw are just iptables managers, that translate human-readable configurations into iptables commands. Firestarter does create correct iptables rules, like ufw does, but it has some functionality that ufw hasn't. For instance, Firestarter allows you to control outbound traffic while ufw does not.

I tried ufw, but didn't like it. Firestarter is much more like the those firewalls I used on Windows (Comodo Firewall).

In my opinion, you could use Firestarter for now and try to learn iptables commands. Is not that hard. Then when you feel you are ready to switch, drop  Firestarter and create your own iptables rules.

> **Valtiel said:**
> In the HowTo iptables they mention Ubuntu 8.04 was this changed for Ubuntu 8.10?

Not that I'm aware of. I guess since this is security stuff, if something had changed, they would update the info or at least put a warning. So, don't worry.

---

### Post by OrangeCrate on 2008-12-06
As said, Firestarter is not a firewall, it just a simple interface to configure iptables, which is your actual firewall.

Though the average user doesn't need to do anything to iptables to be safe, the default configuration is just fine, if you decide that you want to go the Firestarter route, here's a good tutorial to use:

**Installing and Configuring Firestarter**

[http://books.google.com/books?id=YkptQV6f7L8C&pg=PA135&lpg=PA135&dq=icmp+filtering+firestarter&source=web&ots=trCwp50fts&sig=a2nXVIi83Kzed-6inh6z1qlh4DE#PPA131,M1](http://books.google.com/books?id=YkptQV6f7L8C&pg=PA135&lpg=PA135&dq=icmp+filtering+firestarter&source=web&ots=trCwp50fts&sig=a2nXVIi83Kzed-6inh6z1qlh4DE#PPA131,M1)

And, here's the **Firestarter documentation**:

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by HermanAB on 2008-12-06
The most important thing with UNIX security, is to use strong passwords for EVERYTHING.

My passwords are 16 character semi-pronounceable.

Cheers,

Herman

---

### Post by OrangeCrate on 2008-12-06
> **HermanAB said:**
> **The most important thing with UNIX security, is to use strong passwords for EVERYTHING.**

My passwords are 16 character semi-pronounceable.

Cheers,

Herman

+1

And I only add this post to emphasis what Herman has said. Strong passwords are key.

Test yours here:

[http://www.microsoft.com/protect/yourself/password/checker.mspx](http://www.microsoft.com/protect/yourself/password/checker.mspx)

(Yes, that's Microsoft's checker, but I use that one, because I know beyond a reasonable doubt, that it's a legit site. Some others are not.)

---

### Post by Valtiel on 2008-12-08
Thank you so much guys for your replies. I was away from my computer over the weekend thus not able to  digest the reading over my time off away from work. 

Anyways, I will go over them and report back.

Btw, I took the MS password checker for a ride and whoa, even though my password is 12 character long with a twist here and there, its strength is just medium. Yup, time to change that baby up. Rrrrr :mad:

---

### Post by Valtiel on 2008-12-09
Thank you very much guys for your input and all the clarification, tips and useful documentation.

Here is the one last clarification I have regarding this issue before closing it off.

**Lovinglinux said:**

[INDENT]Some people say there are issues when you run the Firestarter, because it runs as root and have a bug that could be exploited to gain root access to your machine. But **as long as you use Firestarter to configure the iptables, then close the GUI you should be fine.**
[/INDENT]


Now I wonder, can I've Firestarter running on the background [icon on the Panel-Bar] without having to worry about the bug that affect Firestarter's GUI?

I know that iptables is running even when firestart isn't running, but I like to manage my network and see all the connections that are taking place. Firestarter shows me these connections [not very detailed but something is something]

If having Firestart running on the Panel-Bar isn't a problem [as far as the GUI bug goes] then how can I have Firestarter start when the system starts?

Any clarification on this would be outstanding.

---

### Post by bodhi.zazen on 2008-12-09
> **Valtiel said:**
> Now I wonder, can I've Firestarter running on the background [icon on the Panel-Bar] without having to worry about the bug that affect Firestarter's GUI?

Yes, that is exactly what we are talking about. You should close Firestarter, not minimize it to the tray (it is still running if it is minimized to the tray).

> I know that iptables is running even when firestart isn't running, but I like to manage my network and see all the connections that are taking place. Firestarter shows me these connections [not very detailed but something is something]

If having Firestart running on the Panel-Bar isn't a problem [as far as the GUI bug goes] then how can I have Firestarter start when the system starts?

Any clarification on this would be outstanding.

Use a different tool to monitor your network activity. There is a tutorial on how to use snort for example.

---

### Post by kevdog on 2008-12-09
Wireshark is good also to monitor raw packets.

---

### Post by lovinglinux on 2008-12-09
> **Valtiel said:**
> I know that iptables is running even when firestart isn't running, but I like to manage my network and see all the connections that are taking place. Firestarter shows me these connections [not very detailed but something is something]

You could also use simpler applications to do that. I use iptstate. It also runs at root (I guess they all do) but nobody commented if this would be a security risk.

Anyway, to install iptstate run:

```

sudo apt-get install iptstate
```

To launch it, just run "sudo iptstate".

---

### Post by Valtiel on 2008-12-10
Beautiful guys.  Thank you very much for you input. I ended up using Wireshark to monitor my network and WHOAH! Am I getting my money's worth or what :KS  It is a great application.

---

