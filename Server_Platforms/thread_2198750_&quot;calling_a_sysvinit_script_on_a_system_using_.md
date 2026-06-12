---
title: "&quot;calling a sysvinit script on a system using upstart isn't supported&quot;"
date: 2014-01-10
forum: Server Platforms
---

### Post by paul.stead.main on 2014-01-10
[COLOR=#000000][FONT=Helvetica Neue]I've installed the server no problems but when it comes to setting up the networking side of things i.e. when I type in vi /etc/network/interfaces I fill in the following 
[/FONT][/COLOR][COLOR=#333333][FONT=arial](space) Address 192.168.0.250[/FONT][/COLOR]
[COLOR=#333333][FONT=arial](space) Netmask 255.255.255.0 [/FONT][/COLOR]
[COLOR=#333333][FONT=arial](space) Network 192.168.0.0 [/FONT][/COLOR]
[COLOR=#333333][FONT=arial](space) Broadcast 192.168.0.255[/FONT][/COLOR]
[COLOR=#333333][FONT=arial](space) Gateway 192.168.0.1[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]
I then type in :qw 

Then finally I type in /etc/init.d/networking restart Now here is my problem I get the following message: 

calling a sysvinit script on a system using upstart isn't supported please us the "service command instead" 

I'm now stuck on how to use the service command can anyone help?

I have been watching the following VT [http://www.youtube.com/watch?v=ndAYZ0DJ-U4](http://www.youtube.com/watch?v=ndAYZ0DJ-U4)

Any help will be great![/FONT][/COLOR]

---

### Post by tfrue on 2014-01-10
I don't know if this will help, but when you edit most files out of your /home directory, use sudo. So:
```
sudo vi /etc/network/interfaces
```
And I believe you should use :wq not :qw

The syntax to restart any service in Ubuntu is:
```
sudo service *servicename* restart
```

So for your instance:
```
sudo service networking restart
```

Good Luck,
Chris

---

### Post by paul.stead.main on 2014-01-12
Chris
Many thanks for that it now works a treat.

Would you know how to add an extra HDD to the server as my PC has one installed? Is it a simple exercise or not?

Paul

---

### Post by tfrue on 2014-01-12
It's not hard. I'm using Ubuntu Server 13.10 with two HDD and an external HDD, but I have a simple set up. All you do is install the HDD, use fdisk or parted to make sure that the HDD is present, format it (If needed), and mount it! You also would want to edit the /etc/fstab file so it will mount at boot. But that's pretty much it, at least that is working fantastic for me.

Chris

---

