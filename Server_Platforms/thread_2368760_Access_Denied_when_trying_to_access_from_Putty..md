---
title: "Access Denied when trying to access from Putty."
date: 2017-08-14
forum: Server Platforms
---

### Post by gamerliko on 2017-08-14
Hello,
I am rather new with Ubuntu and I installed Ubuntu Server 7.10.  I made sure to install OpenSSH.  I can connect to the server thru putty, but when I try to login, I put the right password and met with access denied.

Any ideas?

Sorry, completely new.

Ps. I am just wanting to run a simple MUD server and byond server for people.

---

### Post by vocx on 2017-08-14
> **gamerliko said:**
> Hello,
I am rather new with Ubuntu and I installed Ubuntu Server 7.10.  I made sure to install OpenSSH.  I can connect to the server thru putty, but when I try to login, I put the right password and met with access denied.

Any ideas?

Sorry, completely new.

Ps. I am just wanting to run a simple MUD server and byond server for people.
What version of Ubuntu are you running exactly? Ubuntu 7.10 would have been released in October 2007, so it'd be ancient. If you made a mistake and mean 17.10, this is also troubling, as this version has not been released yet.

You should be using something like Ubuntu 16.04 or 17.04.

---

### Post by gamerliko on 2017-08-14
> **vocx said:**
> What version of Ubuntu are you running exactly. Ubuntu 7.10 would have been released in October 2007, so it'd be ancient. If you made a mistake and mean, 17.10, this is also troubling, as this version has not been released yet.

You should be using something like Ubuntu 16.04 or 17.04.


I made a typo and its 17.10.

[ATTACH=CONFIG]276405[/ATTACH]

---

### Post by vocx on 2017-08-14
> **gamerliko said:**
> I made a typo and its 17.10.


This version is still in development. Why did you install it? I recommend you install the previous version, 17.04 or 16.04 which is a long term support (LTS) release and quite stable.

If you use 17.10 you will be using software that is still in development, and thus you may get strange errors that are difficult to troubleshoot.

---

### Post by gamerliko on 2017-08-14
> **vocx said:**
> This version is still in development. Why did you install it? I recommend you install the previous version, 17.04 or 16.04 which is a long term support (LTS) release and quite stable.

If you use 17.10 you will be using software that is still in development, and thus you may get strange errors that are difficult to troubleshoot.

I was having the same issue in 17.04.  I could connect thru ssh, but always denied after the password was put in.

---

### Post by wildmanne39 on 2017-08-14
I recommend installing 16.04 because it has 5 years support and you do not want to reinstall a server every few months, if you are going to install 16.04 or even 17.04 I will move this thread to the server section where it belongs. Please let us know.

Thanks

---

### Post by gamerliko on 2017-08-14
> **wildmanne39 said:**
> I recommend installing 16.04 because it has 5 years support and you do not want to reinstall a server every few months, if you are going to install 16.04 or even 17.04 I will move this thread to the server section where it belongs. Please let us know.

Thanks

I am installing 17.04 as we speak.  I still run into the same issue.  It allows me to connect via putty, but access denies me after the password for even root.

---

### Post by wildmanne39 on 2017-08-14
*Thread moved to **Server Platforms**.*

Just so you know 17.04 will run out of support in January 2018.

---

### Post by sp40140 on 2017-08-14
So after installing the OS, what steps did you take to configure SSH? What if any changes did you make to server? 
What is the actual command you are using to connect to server?
On a side note:
What will you be using this "server" for? 
The reason I ask is that you have old hardware. Full Ubuntu desktop might not be best choice for it. May be you should go for something lite like xubuntu or lubuntu.
Also, it looks like you have gui (based on the screenshot you posted above) on "server" version. Could you explain your reasoning behind it? 
Or have you just installed regular Ubuntu desktop version and just using it as server?
You can also use NX Client or VNC to access the GUI. They have their positives and negatives. So, depends on how you plan to use the machine.

---

### Post by gamerliko on 2017-08-14
> **sp40140 said:**
> So after installing the OS, what steps did you take to configure SSH? What if any changes did you make to server? 
What is the actual command you are using to connect to server?
On a side note:
What will you be using this "server" for? 
The reason I ask is that you have old hardware. Full Ubuntu desktop might not be best choice for it. May be you should go for something lite like xubuntu or lubuntu.
Also, it looks like you have gui (based on the screenshot you posted above) on "server" version. Could you explain your reasoning behind it? 
Or have you just installed regular Ubuntu desktop version and just using it as server?
You can also use NX Client or VNC to access the GUI. They have their positives and negatives. So, depends on how you plan to use the machine.

I opened sshd_config and added "AddUsers username"  that is all I could really find when I googled up the access denied.   I am using putty to try to connect to my server computer.  

I am back on 17.04 and no GUI anymore.  Just the terminal now.  I am wanting to just use it to host MUDS, BYOND games, and websites for said games.

When I do enter the ipsite from a different computer I do see the ubunutu website success page.

---

### Post by darkod on 2017-08-15
You mentioned root user. Is that what you are trying to login with? In ubuntu the root user is disabled by default and you should use the user (username) you created during installation.

In the terminal login screen can you login with the same credentials you are trying for ssh?

I also recommend you use 16.04 LTS instead of 17.04 because it has muchlonger support. Even for home servers use only LTS releases... You don't want the OS to run out of support in a few months, just after you have configured everything. Since you are starting to install your server now, it is perfect moment to make the OS decision. Before it has any important data and config in it.

---

### Post by gamerliko on 2017-08-15
> **darkod said:**
> You mentioned root user. Is that what you are trying to login with? In ubuntu the root user is disabled by default and you should use the user (username) you created during installation.

In the terminal login screen can you login with the same credentials you are trying for ssh?

I also recommend you use 16.04 LTS instead of 17.04 because it has muchlonger support. Even for home servers use only LTS releases... You don't want the OS to run out of support in a few months, just after you have configured everything. Since you are starting to install your server now, it is perfect moment to make the OS decision. Before it has any important data and config in it.


Sorry took so long to reply.  Had to get a cd disc that could hold 16.04 LTS.  I just installed it and upgrade/updated it.  

When installing the 16.04 I created the name "liko" for the username.  

I did steps 1-8 on this website:

[http://linux-sys-adm.com/ubuntu-16.04-lts-how-to-install-and-configure-ssh/](http://linux-sys-adm.com/ubuntu-16.04-lts-how-to-install-and-configure-ssh/)

I am still being met with access denied when trying to login with "liko".

---

### Post by steeldriver on 2017-08-15
Step 4 involves changing the default port - are you taking that into account when connecting with PuTTY?

Step 6 changes the AllowedUsers - did you allow your user?

Personally I would not mess with /etc/ssh/sshd_config until I had the basics working

---

### Post by darkod on 2017-08-15
Why are you trying all that? During the server installation, at the step to select software you want to install, there is option to select OpenSSH Server. That is enough for basic ssh to be working.

If you are trying to change too many things in the config you are obviously making it to stop working. First install basic default ubuntu server with openssh, try it and it should work. If you want to change some things later, you can but be very careful what you change.

---

### Post by gamerliko on 2017-08-15
> **darkod said:**
> Why are you trying all that? During the server installation, at the step to select software you want to install, there is option to select OpenSSH Server. That is enough for basic ssh to be working.

If you are trying to change too many things in the config you are obviously making it to stop working. First install basic default ubuntu server with openssh, try it and it should work. If you want to change some things later, you can but be very careful what you change.

I did select openssh.  I left the port to 22.  I restored the back up and it allows me to connect all the  way to the password. I put the password in for any user and it just says access denied. I've checked the password 100 times to make sure it is right.  
I did try ssh liko@localhost had me enter the password and it connect that way thru the terminal.

---

### Post by gamerliko on 2017-08-15
> **gamerliko said:**
> I did select openssh.  I left the port to 22.  I restored the back up and it allows me to connect all the  way to the password. I put the password in for any user and it just says access denied. I've checked the password 100 times to make sure it is right.  
I did try ssh liko@localhost had me enter the password and it connect that way thru the terminal.


Update:  I reinstalled the server completely.  Left all the sshd_config file alone.

It does allow me to connect with ssh -v localhost..which prompts me to enter username liko password and it works successfully.
I walk over to the laptop on same network and when i input the password correctly, I get access denied.
I tried from phone while not on the same network, it allows me to connect ,but I get access denied when inputting the password.

---

### Post by darkod on 2017-08-15
What are you using to connect remotely, the server ip? Does it have static ip on the LAN?

It works locally but it doesn't remotely. It sounds to me like you are not accessing the machine you think you are.

---

