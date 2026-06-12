---
title: "GUWF on 11.10"
date: 2011-10-21
forum: Security
---

### Post by GrouchyGaijin on 2011-10-21
Hi Guys,

I'm running 11.10 and installed GUWF.
Do you know how I can have it start when I login?
Now I have to click the lock icon and type in my root password to get GUWF to start.

I'm also curious, if I restart GUWF remembers the settings I had been using.  If I logout then back in, I have to choose the settings again.

I'm not doing anything fancy, in - deny out - allow.

---

### Post by haqking on 2011-10-21
> **GrouchyGaijin said:**
> Hi Guys,

I'm running 11.10 and installed GUWF.
Do you know how I can have it start when I login?
Now I have to click the lock icon and type in my root password to get GUWF to start.

I'm also curious, if I restart GUWF remembers the settings I had been using.  If I logout then back in, I have to choose the settings again.

I'm not doing anything fancy, in - deny out - allow.

GUFW is just the GUI for UFW which is just an interface to manipulate IPTables which controls netfilter which is the firewall in the Linux kernel

Why do you want the GUI to start when you login  ?

from terminal

```
sudo ufw default deny
```

which by default denies all incoming (preferred)

the opposite would be as follows (but not recommended)

```
sudo ufw default allow
```

and then the following to enable with the default setting applied as above

```
sudo ufw enable
```

is all you need and use GUFW to configure rules if you need them.

However if you are behind a router or havent installed any particular services then the default settings are fine as there is no services listening on any port by default.

---

### Post by Iowan on 2011-10-21
Moved to new thread.

---

### Post by SparTacux on 2011-10-21
GUFW is one of those programs you run once just to set it up then forget about it. The settings you made in GUFW are always set when your computer is turned on and thus protecting your system. The only time you need to run GUFW again is to make changes to your firewall settings.

If you enabled logging in GUFW ( preferences ) you can see the firewall in action by viewing your UFW log in system log viewer ( System > Administartion >  Log File Viewer ) You'll see in the logs what traffic is allowed and blocked  as it happens.

Hope that helps.

---

### Post by GrouchyGaijin on 2011-10-21
> **haqking said:**
> 

Why do you want the GUI to start when you login  ?

from terminal

```
sudo ufw default deny
```

```
sudo ufw default allow
```

```
sudo ufw enable
```

is all you need and use GUFW to configure rules if you need them.



Thank you!
Here is another stupid question.  How can I get a sudo command to run at login?

---

### Post by haqking on 2011-10-21
> **GrouchyGaijin said:**
> Thank you!
Here is another stupid question.  How can I get a sudo command to run at login?

what is the command ?

if you refer to the above, you only need to run them once, the service will stay running and start when you start the machine

---

### Post by GrouchyGaijin on 2011-10-21
> **haqking said:**
> 

if you refer to the above, you only need to run them once, the service will stay running and start when you start the machine

Thanks,

I see that when I run:
```
sudo ufw default deny
```
I get a message saying that my 
```
Default incoming policy changed to 'deny'
```

If I run allow, this too affects the incoming policy.

Do I need or should I run anything for the outgoing policy? (I guess not since I was setting it to allow with the gui anyway.)

---

### Post by haqking on 2011-10-21
> **GrouchyGaijin said:**
> Thanks,

I see that when I run:
```
sudo ufw default deny
```
I get a message saying that my 
```
Default incoming policy changed to 'deny'
```

If I run allow, this too affects the incoming policy.

Do I need or should I run anything for the outgoing policy? (I guess not since I was setting it to allow with the gui anyway.)

sorry my bad i worded it wrong, i didnt mean run them both, i was giving you the commands, the deny is the preferred obviously, i was just giving you the allow command, i have edited my original post, i thought you would get what i meant

---

### Post by GrouchyGaijin on 2011-10-21
Thank you for the help.
I really appreciate it.

---

### Post by haqking on 2011-10-21
> **GrouchyGaijin said:**
> Thank you for the help.
I really appreciate it.

no worries you are welcome.

just do the default deny and enable and thats it, forget about it usually on a desktop, if you are behind a router you have that firewall anyways.

Though nothing is 100% secure

mark as solved if thread is answered.

cheers

---

