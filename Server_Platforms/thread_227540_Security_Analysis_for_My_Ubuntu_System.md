---
title: "Security Analysis for My Ubuntu System"
date: 2006-08-01
forum: Server Platforms
---

### Post by waveslider on 2006-08-01
I am concerned about the security of my system, since I am totally new to Ubuntu & Linux.

I am using Firestarter, but not ClamAV. The description of ClamAV on their web site says it is primarily for the mail server, and I use Gmail, so I don't think it's necessary.

I've read countless posts saying that anti-virus is not *really* necessary for Ubuntu, so that's cool.

I guess what I'm looking for is some kind of tool, preferably with a GUI frontend, that will anazlyze my system for security holes and/or vunerabilities. Does anyone know of anything like this?

Thanks!
Tom

---

### Post by Ziox on 2006-08-01
> **waveslider said:**
> I am concerned about the security of my system, since I am totally new to Ubuntu & Linux.

I am using Firestarter, but not ClamAV. The description of ClamAV on their web site says it is primarily for the mail server, and I use Gmail, so I don't think it's necessary.

I've read countless posts saying that anti-virus is not *really* necessary for Ubuntu, so that's cool.

I guess what I'm looking for is some kind of tool, preferably with a GUI frontend, that will anazlyze my system for security holes and/or vunerabilities. Does anyone know of anything like this?

Thanks!
Tom

I think the only security hole there are are open ports, which are closed by default in Ubuntu.  But there is a nice app called nmap that will scan all the basic ports and see if any of them are open.

to install nmap:

sudo aptitude install nmap

to use it (very basic, I don't know any advance command yet):

(sudo - forgot if it is required or not) nmap <you're IP address>

---

### Post by lazyd2 on 2006-08-01
> **Ziox said:**
> I think the only security hole there are are open ports, which are closed by default in Ubuntu.  But there is a nice app called nmap that will scan all the basic ports and see if any of them are open.

to install nmap:

sudo aptitude install nmap

to use it (very basic, I don't know any advance command yet):

(sudo - forgot if it is required or not) nmap <you're IP address>
Thanks for the info

---

### Post by Ziox on 2006-08-01
> **lazyd2 said:**
> Thanks for the info

You're welcomed.  But i think a better way to check the ports is to use this website [Shield's Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by waveslider on 2006-08-01
> **Ziox said:**
> I think the only security hole there are are open ports, which are closed by default in Ubuntu.  But there is a nice app called nmap that will scan all the basic ports and see if any of them are open.



Thanks! Yes, I'm familiar with nmap, written by H D Moore. That dude is a genius.

I don't have any ports open, but I will still try nmap, just in case. I guess I was just alarmed by the sheer quantity of people who were attempting to connect to my pc (viewable from Events in Firestarter) and wanted some reassurance (AS IF it was necessary in Ubuntu) that I was protected.

---

### Post by waveslider on 2006-08-01
Ok, now I am confused.

According to the GUI in Firestarter, I have no open ports for incoming traffic, but nmap reports that I have the following open:

SSH, IPP, & VNC. I opened VNC when I was attempting to setup a remote desktop connection from work, but it turns out our admin at work won't allow that, so I *thought* I turned it off through Firestarter (ports 5900 & 5901) at home. Firestarter doesn't display it as an open port. Help?

---

### Post by Christopher on 2006-08-03
Is there a GUI for Nmap or is it via console only?  Thank you in advance.

---

### Post by Christopher on 2006-08-03
> **Ziox said:**
> 
to install nmap:

sudo aptitude install nmap



I did it this way, but isnt it apt-get install nmap ?  I was wondering if it really matters.

---

### Post by kriding on 2006-08-03
> **Christopher said:**
> I did it this way, but isnt it apt-get install nmap ?  I was wondering if it really matters.

Either way can be used, but aptitude is better for any dependencies

---

### Post by Christopher on 2006-08-03
> **kriding said:**
> Either way can be used, but aptitude is better for any dependencies

How do i install the GUI for nmap?

---

### Post by kriding on 2006-08-03
> **Christopher said:**
> How do i install the GUI for nmap?

```
sudo aptitude nmapfe  
```

this should do it

---

### Post by airtonix on 2006-08-05
> **Ziox said:**
> You're welcomed.  But i think a better way to check the ports is to use this website [Shield's Up!]("https://www.grc.com/x/ne.dll?bh0bkyd2")


Actually dude, since that guy has modified his software to suit the FBI requirements.....i would not touch it..

that and the fact that his whole site feels like a pimp for ZoneAlarm....a piece of software that does not make me feel secure....

ANd not once does he mention Sygate Firewall (Personal or Pro).....which i feel is much closer to IPtables manipulated by Firestarter

---

### Post by Ziox on 2006-08-05
> **airtonix said:**
> Actually dude, since that guy has modified his software to suit the FBI requirements.....i would not touch it..

that and the fact that his whole site feels like a pimp for ZoneAlarm....a piece of software that does not make me feel secure....

ANd not once does he mention Sygate Firewall (Personal or Pro).....which i feel is much closer to IPtables manipulated by Firestarter

That's all personal opinion....whether you try that site or not, it is totally up to you. I'm just suggesting different methods to test security and stuff like that...

---

