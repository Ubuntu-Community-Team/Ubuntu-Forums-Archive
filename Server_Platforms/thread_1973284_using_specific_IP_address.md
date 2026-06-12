---
title: "using specific IP address"
date: 2012-05-04
forum: Server Platforms
---

### Post by batb on 2012-05-04
I have ubuntu setup on two virtual machines. Being a newbie to Linux system admin., I want to understand how to tell the Linux on the two virtual machines that they are to use  specific IP addresses instead of obtaining them from the DHCP servers?
I need that because I want to forward requests on a specific port to a specific machine.

---

### Post by darkod on 2012-05-04
Depending on the VM software, you might need to create another virtual network adapter since the first one might be used as NAT for the hosts.

Otherwise, the network info on the server is in /etc/network/interfaces. I find the nano editor easiest to use, and you will need to use sudo to edit those system files:
sudo nano /etc/network/interfaces

The dhcp setup looks like:
auto eth0
iface eth0 inet dhcp

The static setup is:
auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask x.x.x.x
   gateway x.x.x.x
   dns-nameservers x.x.x.x y.y.y.y (optional, for static DNS)

---

### Post by CharlesA on 2012-05-04
> **darkod said:**
> Depending on the VM software, you might need to create another virtual network adapter since the first one might be used as NAT for the hosts.

Otherwise, the network info on the server is in /etc/network/interfaces. I find the nano editor easiest to use, and you will need to use sudo to edit those system files:
sudo nano /etc/network/interfaces

The dhcp setup looks like:
auto eth0
iface eth0 inet dhcp

The static setup is:
auto eth0
iface eth0 inet static
   address x.x.x.x
   netmask x.x.x.x
   gateway x.x.x.x
   dns-nameservers x.x.x.x y.y.y.y (optional, for static DNS)
This would allow you to set a static IP.

As for having the VM on the same network as everyone else, use bridged networking.

What VM software you using using?

---

### Post by batb on 2012-05-04
VM software is: Oracle's VM VirtualBox 4.1.14 for Windows hosts

****

---

### Post by CharlesA on 2012-05-04
> **batb said:**
> VM software is: Oracle's VM VirtualBox 4.1.14 for Windows hosts

****
Open the VM settings, select network and then select "bridged" instead of NAT.

---

### Post by batb on 2012-05-04
@darkod, @CharlesA, thanks.
follow-up q?
can servers/workstations talk to each other only via IP addresses or can they do so via server names also

---

### Post by arrrghhh on 2012-05-04
> **batb said:**
> can servers/workstations talk to each other only via IP addresses or can they do so via server names also

Assuming DNS is in place (or manual modification of the client's hosts files) then yes.

A dnsmasq or DNS/DHCP server would take care of the name resolution for you.  Otherwise the only way to talk is via IP.

---

### Post by CharlesA on 2012-05-04
> **arrrghhh said:**
> Assuming DNS is in place (or manual modification of the client's hosts files) then yes.

A dnsmasq or DNS/DHCP server would take care of the name resolution for you.  Otherwise the only way to talk is via IP.

This about covers it. :)

---

### Post by batb on 2012-05-04
@arrrghhh, @CharlesA, thanks

---

### Post by batb on 2012-05-06
follow-up question: [COLOR=#1f497d][FONT=&quot]I  need a little help with the server, including, how to I get it to load  the Gnome UI by default, so I can use the menu there to access all the  system administration tools, instead of having to try to remember them  all and enter them correctly on the command line?[/FONT][/COLOR]

---

### Post by darkod on 2012-05-06
Did you install the UI? A server by default has no UI, it is command line only.

And that is recommended for a server.

---

### Post by CharlesA on 2012-05-06
> **batb said:**
> follow-up question: [COLOR=#1f497d][FONT=&quot]I  need a little help with the server, including, how to I get it to load  the Gnome UI by default, so I can use the menu there to access all the  system administration tools, instead of having to try to remember them  all and enter them correctly on the command line?[/FONT][/COLOR]

You can install a GUI, but it is a better idea to just install Ubuntu Desktop instead of Ubuntu Server edition.

In any case, there are only so many commands you use to admin a system. Take notes. ;)

> **darkod said:**
> Did you install the UI? A server by default has no UI, it is command line only.

And that is recommended for a server.

+1.

---

### Post by batb on 2012-05-06
> **darkod said:**
> Did you install the UI? A server by default has no UI, it is command line only.

And that is recommended for a server.

[COLOR=#1F497D][FONT=&quot]I  don't know if I installed the UI.  I just let the install proceed, on the virtual machine,  using Oracle's VM software, and just accepted the defaults.  How do I find out, and what do I do if Gnome isn't installed,  and then, I guess, how to tell it to start when I log on.[/FONT][/COLOR]

---

### Post by CharlesA on 2012-05-06
> **batb said:**
> [COLOR=#1F497D][FONT=&quot]I  don't know.  I just let the install proceed, on the virtual machine,  using Oracle's VM software, and just accepted the defaults.  How do I find out, and what do I do if Gnome isn't installed,  and then, I guess, how to tell it to start when I log on.[/FONT][/COLOR]
```
sudo apt-get install gnome-panel
```

---

### Post by batb on 2012-05-06
> **CharlesA said:**
> ```
sudo apt-get install gnome-panel
```

it installed ok. now, how do I start it and configure it to start as soon as I log on.

---

### Post by CharlesA on 2012-05-06
It should have installed lightdm as well. Try starting that and see what happens.

---

### Post by arrrghhh on 2012-05-06
> **CharlesA said:**
> You can install a GUI, but it is a better idea to just install Ubuntu Desktop instead of Ubuntu Server edition.

This ^^.  Ubuntu has multiple editions for a reason.  If you want/"need" a UI, Ubuntu Desktop is for you.  If you don't want a UI and just want a headless server, Ubuntu Server is for you.  

> **batb said:**
> it installed ok. now, how do I start it and configure it to start as soon as I log on.

Don't try to fit a square peg into a round hole.  Install Ubuntu Desktop.  It's a VM, easily blown away.

---

### Post by CharlesA on 2012-05-06
> **arrrghhh said:**
> This ^^.  Ubuntu has multiple editions for a reason.  If you want/"need" a UI, Ubuntu Desktop is for you.  If you don't want a UI and just want a headless server, Ubuntu Server is for you.

Aye. I've tried to install a GUI on the server edition before but ran into problems with it not starting due to having no monitor attached.

Now I just use CLI for my main server and a VM with a GUI for my web development box, which hosts a LAMP server and the few programs I use to write my web pages with. ;)

---

### Post by arrrghhh on 2012-05-06
> **CharlesA said:**
> Aye. I've tried to install a GUI on the server edition before but ran into problems with it not starting due to having no monitor attached.

Now I just use CLI for my main server and a VM with a GUI for my web development box, which hosts a LAMP server and the few programs I use to write my web pages with. ;)

Hah, almost the same here.  I never tried to install a GUI on the Server edition, but I run a VM thru VBoxHeadless in order to get RDP'd into my office (they require WinXP...)

---

### Post by batb on 2012-05-06
got it....thanks guys....dropped the server edition

---

### Post by CharlesA on 2012-05-06
> **arrrghhh said:**
> Hah, almost the same here.  I never tried to install a GUI on the Server edition, but I run a VM thru VBoxHeadless in order to get RDP'd into my office (they require WinXP...)

Sounds about like mine. I've been running VBox headless for a while now. I use FreeNX to connect to the GUI of the VM. ;)

> **batb said:**
> got it....thanks guys....dropped the server edition

Good luck!

---

### Post by Vegan on 2012-05-06
I use a Cisco box and I use it for DHCP and all of my VMs seem to like that approach. This way the whole enterprise is all accessible.

---

### Post by CharlesA on 2012-05-07
> **Vegan said:**
> I use a Cisco box and I use it for DHCP and all of my VMs seem to like that approach. This way the whole enterprise is all accessible.
I do the same, my router is set for local dns/dhcp.

I don't think I have any of my VMs set to static IPs, but I do have them set as reserved via their MAC.

---

### Post by DonThompson on 2012-06-15
I'd love to know the logic behind the GUI-less server.  I understand the GUI may take resources, but...
> it could be installed but started manually when needed
> stuff (file locations, names of code bits that do things,  how things are done, etc) changes with each distribution and not everybody wants to have to know how the developers of THIS version are thinking in order to run a server - the goal of many of us is to get the job done.

---

### Post by CharlesA on 2012-06-15
> **DonThompson said:**
> I'd love to know the logic behind the GUI-less server.  I understand the GUI may take resources, but...
> it could be installed but started manually when needed
> stuff (file locations, names of code bits that do things,  how things are done, etc) changes with each distribution and not everybody wants to have to know how the developers of THIS version are thinking in order to run a server - the goal of many of us is to get the job done.
Generally more packages installed = more attack surface.

99% of commands are the same between linux distros of the same family (Redhat, Debian, etc).

If you are running a server, you want the least amount of packages installed to get the job done and that means running it CLI only.

You learn one distro, and get good at it, you can easily adapt to other distros.

---

### Post by rubylaser on 2012-06-15
> **CharlesA said:**
> Generally more packages installed = more attack surface.

99% of commands are the same between linux distros of the same family (Redhat, Debian, etc).

If you are running a server, you want the least amount of packages installed to get the job done and that means running it CLI only.

You learn one distro, and get good at it, you can easily adapt to other distros.

+1.  All of these are great reasons to not use a GUI on a server.  Plus you get the benefit of really understanding how things work.  It makes troubleshooting much easier if/when you need to do it.

---

### Post by arrrghhh on 2012-06-16
> **rubylaser said:**
> +1.  All of these are great reasons to not use a GUI on a server.  Plus you get the benefit of really understanding how things work.  It makes troubleshooting much easier if/when you need to do it.

x2.  Knowing the CLI is very useful - and I find myself much faster at getting things done in the CLI than with a GUI.

Now there's certain things that simply are better seen/laid out with a GUI.  I just use web front-ends or the like to manage those.  Sorting thru stuff I find an NFS mount or samba mount get that done nicely :).

So no GUI certainly isn't for everyone - but if you give it a shot, I think you'll be surprised at how well it works.  With that said, if you want a full-blown DE - Ubuntu Desktop ships with one out of the box.  Installing one onto Ubuntu Server is like shoving a square peg into a round hole - why put in the extra effort?

---

### Post by CharlesA on 2012-06-16
> **arrrghhh said:**
> 
Now there's certain things that simply are better seen/laid out with a GUI.  I just use web front-ends or the like to manage those.  Sorting thru stuff I find an NFS mount or samba mount get that done nicely :).

Aye. I used to use Webmin for Samba, but not anymore - it's easier to just SSH in and add share definitions or users from there.

A tad bit less work too cuz everything is done from the terminal.

---

