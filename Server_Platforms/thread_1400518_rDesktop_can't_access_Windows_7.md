---
title: "rDesktop can't access Windows 7"
date: 2010-02-07
forum: Server Platforms
---

### Post by Sugi on 2010-02-07
I can't get rdesktop to access the windows 7 box.  
"rdesktop ipaddress"
"Autoselected keyboard map en-us
Error: ipaddress: unable to connect

I am on Ubuntu 9.10 64 bit
access to Windows 7
With Allow access from any version of Remote Desktop

Sugi

---

### Post by Xianath on 2010-02-07
Windows firewall?

---

### Post by volkswagner on 2010-02-07
If it is not a firewall issue, perhaps you don't have a password set on the Windows user.  Windows won't allow remote access for accounts without a password.

---

### Post by Sugi on 2010-02-07
The firewall either allows it or is off.

Should I just make an new account on windows 7 for reomote acces just to make this easier?

Sugi

---

### Post by volkswagner on 2010-02-07
> **Sugi said:**
> The firewall either allows it or is off.

Should I just make an new account on windows 7 for reomote acces just to make this easier?

Sugi


Adding a user or setting a password would be which you prefer.  If you set a password for your main user, you can still have it login automatically if that is an issue for you.

---

### Post by Sugi on 2010-02-07
volkswagner, I had the windows 7 computer add a new account just for remote access, but still the same message.
autoselected keyboard map en-us
Error: doireek.webhop.net: unable to connect

Sugi

---

### Post by volkswagner on 2010-02-09
Are you trying to connect from outside your LAN?  If so, are you able to rdesktop from inside your LAN?  Can you successfully ping the ip address?  If you are trying outside your LAN, you need to forward the proper port via your router settings.

---

### Post by Steve H on 2010-09-25
I'm having the same issues...

Ubuntu Karmic --> rdesktop --> Vista Ultimate

```
~$ rdesktop -u*VistaUsername* -p*mypassword* 192.168.0.102 -g1024x768 -a16 -xl
Autoselected keyboard map en-gb
ERROR: 192.168.0.102: unable to connect
```

On the Vista side I'm getting only a few Event Viewer entries showing that I tried to connect. It showing something like "Someone tried to connect using explicit credentials". When i look further down the entry is says the the TargetUser "getafix", which is my Linux user!! It looks like rdesktop isn't sending the correct credentials...

Vista has it firewall turned off and Remote Assistance switched on.

gnome-rdp doesn't even register as trying to connect on the Win7 side.

---

### Post by CharlesA on 2010-09-25
If you are using Vista and 7, you need to make sure remote desktop is enabled and is set to "Allow connections from computers running and version of Remote Desktop (less secure)."

That'll allow you to connect.

---

### Post by Steve H on 2010-09-25
> **CharlesA said:**
> If you are using Vista and 7, you need to make sure remote desktop is enabled and is set to "Allow connections from computers running and version of Remote Desktop (less secure)."

That'll allow you to connect.

Unfortunately not. I've switched that on and off several times now with no effect. I'm looking in to my router, firewall and network settings now. I can ping the machine and connect to it's shares but just not remote desktop. So I know routing is working...I think?!

---

### Post by CharlesA on 2010-09-25
Try running nmap against that machine to make sure port 3389 is open.

---

### Post by Steve H on 2010-09-25
> **CharlesA said:**
> Try running nmap against that machine to make sure port 3389 is open.
```

nmap 192.168.0.102 -PN

Starting Nmap 5.00 ( http://nmap.org ) at 2010-09-25 15:57 BST
Interesting ports on 192.168.0.102:
Not shown: 995 filtered ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2869/tcp open  unknown
5357/tcp open  unknown
```

Looks like the port isn't open...I did notice that the Terminal Service service wasn't running on the Vista machine. That's now running.

[I][B]
ADDITION[/B][/I]
SORTED. I hadn't started the service, I'd set Terminal Services to Auto, but not actually started it!! FACE PALM!! :)

---

### Post by CharlesA on 2010-09-25
Try the nmap scan again and see if port 3389 is open now.

---

### Post by R.Bucky on 2010-09-25
It is my understanding that RDP is not enabled in W7 if you do not have the Professional or above version, similar to XP. In that case, you will need to run VNC server on the W7 box.

Alternatively, your router will need to have the proper configuration in the Port Forward settings to your network. Double check the LAN address and use that instead of the host name.

---

### Post by CharlesA on 2010-09-25
> **R.Bucky said:**
> It is my understanding that RDP is not enabled in W7 if you do not have the Professional or above version, similar to XP. In that case, you will need to run VNC server on the W7 box.

Correct. The "Home" versions don't include RDP.

You don't need to deal with port forwarding unless you want to connect from outside your local network.

@Steve H: I checked a clean install of Vista Ultimate x64. All I did was enable remote desktop and I was able to connect from the same LAN using rdesktop without any problems.

It definitely sounds like a firewall problem.

---

### Post by Steve H on 2010-09-25
I've got it sorted now, it was Terminal Services set to "Disabled" on Vista. I set to "Auto" and started the service BINGO!! I could connect via RDP.

However that threw up the problem that RDP locked the screen of the Vista machine when I logged in remotely, which is no use to me. I really needed to "remote control" the Vista system as it's my Media Centre PC, which doesn't have a kb or mouse and sometimes needs a restart.

So in the end I installed UltraVNC Server on the Vista box and now I've got it all working.

I can control the Vista system without it locking the desktop while being controlled.Sweet!

Thanks for the help folks

:)

---

### Post by Maddmaxx on 2011-10-25
There is more to it than that, at least in my experience, with 3 windows 7 ultimate boxes, an Ubuntu 11.10 box and a MacbookPro.  El MacBookPro has the ability to handle 128 bit encryption for the remote session with it's default client, but I have yet to find an Ubuntu solution.  

So far the only solution for Ubuntu that I know of is to allow the lesser level of encryption, (a setting in W7 professional or higher I believe). I wouldn't recommend it if you're opening up port 3389 to that system though.  Keep your security settings for any servers to the max for all systems if at all possible. 

Maybe someone with more humanity knowhow can weigh in... 

Cheers!:guitar:

---

