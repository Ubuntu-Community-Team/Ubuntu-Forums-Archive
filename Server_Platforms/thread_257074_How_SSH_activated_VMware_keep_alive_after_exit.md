---
title: "How? SSH activated VMware keep alive after exit?"
date: 2006-09-14
forum: Server Platforms
---

### Post by luckylucky on 2006-09-14
Hi everyone,

I am hoping someone could help me out here with hopefully a simple solution to a little need.

I have a home computer (running Ubuntu of course!:) that I have SSH access into from anywhere in the world (so even if traveling I still have access to my files).

On the computer I have an Ubuntu-server VMware app running a web server... works great!

The problem (hoping you have a solution)

If I need to reboot the physical computer obviously my VMware server gets shut down too.  I can easily activate it remotely to turn it on via SSH but the problem is that as soon as I exit the ssh session it cancels the running program (VMware), and thus my virtual server disappears.  

I've heard that you can do "screen" in ssh to keep alive, but either I don't know how to use screen, or it doesn't keep VMware running after I leave the ssh session.

The question:

How to I keep VMware running after I exit out of ssh?

Thanks for your answers to this question... really appreciate it!

---

### Post by Iowan on 2006-09-14
Another distro I have uses the **fork** command to create a separate process.  Another option is to append the ampersand (&) to the end of the command.  Either/neither might work...

---

### Post by mannheim on 2006-09-14
Does starting the app with "nohup" work:

```
$ nohup vmware ... 
```

A process started with nohup ("no hang up") is not sent a SIGHUP signal when the shell is closed; this is intended for the purpose you describe, though I don't know if it works with vmware.

---

### Post by lamego on 2006-09-14
Are you using vmware server ? The usual install does set it up to start with the system boot.

---

### Post by inthewayboy on 2006-09-14
Yeah, I haven't had a chance to play with the linux version, but the Win32 VMWare Server has an option to configure the VM's to run using the system account. That means you can have it start the VM at boot (Without any user interaction) as well as shut it down when you power cycle the host. I would imagine there is some similar function in the linux version.

If not, there has to be some simple shell script that you could run at system start the would do this for you. Should check out the VMWare forums and see what they have there.

---

### Post by luckylucky on 2006-09-15
Thank you to the last two posts.  Your suggestion led me to find the better answer to this need than the SSH solution I was embarking on.  I installed VMware server on the computer (removing the VM player) and found, as you mentioned, that there is an option to get it to automatically start the selected VMware app(s) at boot up of the physical machine.  This is PERFECT!!!  Now when I reboot the physical computer it will gracefully shutdown the VMware apps (my Ubuntu server), then when the physical computer boots it will automatically boot the selected VMware apps.

Honestly, I can't believe that VMware just gives away the VMware server product for free.  Bless them for this fabulous product that is certain to advance the world of computers forward, and help ease the integration of linux into this world!

BTW I now use Ubuntu ~ 98%, it is my "regular" OS on 3 computers, have gotten my employees on Ubuntu, and even my primary business partner is now "getting into it".  Ubuntu ROCKS!  IMO it is the best desktop linux around period (especially when XGL becomes normally supported in a future release).  I'm playing with Ubuntu Server to see how good it is, and have it running my home servers, however I am still using CentOS on all production servers.  So far I've experienced a few inconsistencies with some programs not finding config files because debian puts them in differnt places than they expect to find them (whereas they are in the "proper" place on Fedora & CentOS (and of course RH too).  I'm going to wait until Ubuntu Server is a bit more mature and gets a good reputation before putting my money on it.  But none-the-less as far as Desktop distros go, after changing preferences (I'm not fond of brown), and after playing around with many distros I have settled on Ubuntu as being what I consider to be the best Desktop distro overall.  Yay Ubuntu!

---

### Post by amorangi on 2006-09-24
Could you let us in on the secret? How did you do it?

---

### Post by luckylucky on 2006-10-07
Hmmm... how ***DID*** I do it?  Lemme think, it's been a few weeks.

Ok, here is what I remember, and my suggestions.  This may be a bit of swiss cheese, but hopefully it'll do the trick for getting you there.

First of all I did a fresh install of Xubuntu on the physical machine.  Why?  It uses up less resources and ram, so figured to use that as my base install.  Of course I also set up a bunch of partitions for my own purposes, but that is irrelevant info here.

Next I installed the open ssh server on the Xubuntu.  I opened up synaptic package manager, searched for openssh, then installed the server.  I then went into the config files to change the ssh port (22) to a non-standard port (it's my secret, but you can pick just about any number you want) for security purposes.

Next I went into "Networking" in "System" >> "Administration" to change the properties of my network card to have a fixed local IP on my home network (i.e. 192.168.1.144) rather than dynamically being assigned one through DHCP.

Next I shut down the computer.  Unplugged the monitor, keyboard & mouse.  I then pushed the power button on the computer and walked away.

From another computer I logged into my Router (linksys = [http://192.168.1.1/](http://192.168.1.1/)) and did a "Port Range Forward" of my chosen port number (let's pretend it is 2222) to the local IP of the machine (192.168.1.144).

(((tip: you can also set up dynamic DNS (DDNS) directly in linksys so that you can access your home server through a domain like whatever.homelinux.net.  It's real easy to set up, and the instructions are inside your linksys admin site.)

Then I SSHed into the Xubuntu server, and since the openssh server starts at boot up of the machine you can ssh into it even if it's at the login screen.

Then from my laptop upstairs I SSHed into the Xubuntu server with the -X flag so that I can work on that remote machine with a GUI.  The -p flag is to identify the non-standard ssh port.  Note that the "X" is capital, and "p" is lower case.
ssh -X username@192.168.1.144 -p 2222
obviously replace username with your account, the IP with the one you actually used, and 2222 with the port you changed it to, or omit the "-p 2222" if you didn't make any changes.

then at the prompt type:
firefox
and you'll find your web browser open up.  Though it looks like it is happening on your local machine it is actually the browser window from your server machine (evidenced by the fact that it behaves a little slow).  Then you go to [www.vmware.com](www.vmware.com) and download the free vmware server (with all the extras you can download).  Save it on your "Desktop" (/home/user/Desktop), but remember you are saving it on the Desktop of your remote server machine.

Then close your browser window to return you to your ssh terminal.

Install build essentials:
sudo apt-get install build-essential
accepting whatever it wants you to agree to.

Then type in the following code:
sudo apt-get install linux-headers-`uname -r`
and it'll install some more stuff for you.

In your ssh shell type:
nautilus
It will open your nautilus file browser seeing the files on your remote machine.  Then go back to the files you downloaded from VMware, un-tar them (by right-clicking & select "open with Xarchiver").  Make a mental note where you put the untared files.

Close the nautilus window to return to your ssh shell terminal.

Change directory (cd) to where you have you installer files of the main vmware server program.  Then type in the following:
sudo ./vmware-install.pl
or it may be a different name than what I've shown above, but it will have the .pl extension.
Agree to whatever the program asks of you, and the standard defaults are generally ok.

Next go to the VMware website and somewhere there (maybe someone could dig up the link?) is a how to tutorial page of the vmware server packages.  You should read that for more specific information.  Or you could just "chance it" and just install all the other downloaded vmware server components you downloaded by basically following the above steps of untaring & installing.

When you have all the components installed you'll want to reboot your Xubuntu machine.  Simply type in the following:
sudo shutdown -r now
and go away for a coffee or go to the bathroom for about 10 minutes.

When you come back then re-login via ssh to your Xubuntu server.  Make sure you use your -X flag to be able to view vmware with your GUI.

In your ssh terminal type:
sudo vmware
and now you should see the vmware server window appear (after a few moments).  Now you can play around with it's settings.

I think now your vmware server will automatically load when you boot up the computer.  If I'm wrong about this then please someone correct me.

If you have a vmware application, such as an Ubuntu server inside vmware, you could set up the option from within the vmware server options about that appliance the option for your Ubuntu server (vmware appliance) to automatically boot up when the physical computer boots, and for it to gracefully shutdown when the physical computer shuts down.

Now you can play around with your Ubuntu server (vm app) any way you want to.

Hope this "how to" helped, and I hope you have fun with all of this!

BTW, having this server in my basement is absolutely incredible, and came in handy while I was away on vacation (accessing files).  I'm sure you can think of countless ways to have fun with your new basement server with the vmware server solution (and send the people at vmware a thank you card for such a marvellous free product/gift for us).

---

