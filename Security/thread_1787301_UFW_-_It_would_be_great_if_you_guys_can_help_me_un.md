---
title: "UFW - It would be great if you guys can help me understand."
date: 2011-06-21
forum: Security
---

### Post by Linux_will_prevail on 2011-06-21
Guys I am a Linux newbie so please bear with me if I sound stupid. I was checking out how to set up a firewall for my system and landed on this webpage:

[http://www.tuxradar.com/content/10-simple-ways-make-your-linux-box-more-secure](http://www.tuxradar.com/content/10-simple-ways-make-your-linux-box-more-secure)

But I am so confused with how this ufw application works. What I understand is that once I set it to "default deny" it prevents unauthorized incoming connection but what does it mean when the author says to add exceptions for services I need? When do I need to do that? Also what's an SSH server? I googled it but it went tangent over my head.

---

### Post by uRock on 2011-06-21
You can use the GUFW tool to to input allowances for incoming connections, such as Samba shares or Remote Desktop. GUFW is just a simple graphical interface for UFW.

GUFW can easily be installed via the Ubuntu Software Center, Synaptic Package Manager or running **sudo apt-get install gufw** in a terminal.

SSH stands for Secure SHell, which is commonly used as an encrypted means to log into other systems for administration purposes, though some use it like a VPN tunnel while on public networks to make life hard for eaves droppers.

---

### Post by BkkBonanza on 2011-06-21
A "service" (on linux called a daemon as well) is a program running always (in the background) that achieves some function or goal. So if you run a "web server" then it must listen for incoming connections of users requesting web pages. There are many different kinds of things you may choose to have running and if you do then you will have to allow the firewall to pass traffic for that service, otherwise it is cut off by the firewall deny rule.

Another example, if you run a mail server program it cannot handle requests for mail if the firewall is blocking traffic - so that's a case where if you want the mail server to function then you will need to add a rule that allows inbound connections to it.

By default Ubuntu does not have services running that require open ports. But it is quite common that people do want some services that will require it. 

SSH is a server that would require an open port to function. It provides the ability for an outside user to connect and get a terminal/console to do things on the system. So obviously the wrong person getting access that way could do quite a bit of damage. But web servers all over the world use SSH as one main way of doing admin work. It's one very basic and essential service that is often used on servers.

A SHELL is a program that exceutes user commands and SSH stands for SECURE SHELL, because it supports using encryption to send/receive it's traffic over the network. Desktop users often don't need to run SSH and it's not installed by default on a desktop install but it is installed and running on most server installs. It also has a number of other useful functions built in and so it's a bit of a swiss-army knife for remote system admin work.

---

