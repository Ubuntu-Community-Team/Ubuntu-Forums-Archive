---
title: "Sharing with Windows 8"
date: 2013-06-24
forum: Server Platforms
---

### Post by smed121 on 2013-06-24
Hello,
I work for a design company, And we have being using a machine with ubuntu 12.04 on it for the past year to back up our data by going to network > ubuntu machine > and just saving or accessing our files from here.

However, we have just got 2 new machines that run Windows 8 and whatever i do i cant seem to get the shared folders to show in the network.

---

### Post by volkswagner on 2013-06-24
[Check your network discovery]("http://www.eightforums.com/tutorials/9840-network-discovery-turn-off-windows-8-a.html") settings.

Are you on the same workgroup/domain?

What type of authentication are you using for SAMBA?

Can the Win8 machines "see" other windows shared resources?

---

### Post by smed121 on 2013-06-25
Hello,
Thanks for your reply much appreciated.

My network discovery settings are turned on.

We are on the same workgroup "promediauk"

It is currently on "User"

I could see the other pc's in the office when my workgroup was set to "workgroup" but since i have changed that i only see my own resources.

Thanks, For your help.

**EDIT**: I got it to work, For other people that come across this thread i will briefly run through what i did below, I'm not sure exactly what i did but just try this :)

Firstly, Setup your samba on Ubuntu, Make sure that your workgroup names are the same.

Secondly, On your windows 8 machine press **Start Key + X** and open command prompt as admin.
Now enter the following.
> netsh advfirewall firewall [COLOR=#0000ff]set[/COLOR] rule group="[COLOR=#8b0000]File and Printer Sharing[/COLOR]" [COLOR=#0000ff]new[/COLOR] enable=Yes

After i did this it popped up on my network. (I'm sorry if this didn't work for you i tried about 15 different methods over the last day so it may have been a mixture of them all.)

---

