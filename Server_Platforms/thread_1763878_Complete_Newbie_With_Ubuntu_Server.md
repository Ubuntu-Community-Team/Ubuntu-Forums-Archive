---
title: "Complete Newbie With Ubuntu Server"
date: 2011-05-21
forum: Server Platforms
---

### Post by poker158149 on 2011-05-21
Hello everyone!

I'm no amateur when it comes to Ubuntu Desktop, but Ubuntu Server is a whole new ball game. I have a used computer that I received from a friend, so I decided to play with it and install Ubuntu Server on it because I've always wanted to try it. Well, it wasn't at all what I expected. I do have to say, I love the white-text-on-a-black-background-only look. I have no idea where to start, what to do, anything. I don't even think I installed it correctly. And by that I mean I think I messed up the setting up the network part. I don't know which I.P. to use or which gateway to use. I know the I.P.'s of my other computers, but I don't know how to check this computer's I.P.. I know what my subnet mask is, but that's about it. And after I do get it installed, I don't know how to check if I'm connected to the internet or not. I try pinging a few sites, but I just keep getting "host not found"; and then I try to install, for example, the gnome GUI, but every time I try I just get "package not found," which I am assuming is because I'm not connected to the internet.

I've done searches and read the guides, but none of it helps. They all assume the user knows what he is doing previous to dealing with the server software.

If anyone has the patience to read all of this and help me out, I would be very grateful :P.

Thanks to anyone who tries!

---

### Post by Ryan Dwyer on 2011-05-21
Will the computer be using a static IP or will it be using DHCP?

You can run ifconfig to see your interfaces and their IPs. Most machines will have eth0, but if you have a second network interface then you might also have eth1 (or wlan0 or something).

You can configure the network interfaces by editing /etc/network/interfaces (type "sudo nano /etc/network/interfaces"). There are many guides that explain the structure of this file. Once done, run sudo /etc/init.d/networking restart.

If you still have problems, try pinging both a domain name and external IP address such as 8.8.8.8 (a Google server). If the IP is pingable but the domain name isn't then it's a problem with DNS. If the IP isn't pingable then it's a connectivity problem.

---

### Post by poker158149 on 2011-05-21
Thank you for replying.

It won't be using DHCP because when I installed the server, it said it couldn't connect to DHCP. So I assume I'm on a static I.P.

I went to edit /etc/network/interfaces file and found that it's using an I.P. for a DNS that is not my network's DNS. Also, it's looking for domain name that doesn't exist. During the install it asked me to put a domain name in, it could be made up, and I did. Is it trying to connect to that domain name? Because I just made it up for the install.

---

### Post by slooksterpsv on 2011-05-21
Here's a few commands you should get comfortable using:

nano - for a text editor, I normally type in pico, to do any commands listed at the bottom hold CTRL if it has a ^ and press the key (e.g. Exit ^X = CTRL + X)

ifconfig - shows information for your network card, also you can specify a device like so: ifconfig eth0 to get specific information on the eth0 device.

man <command> - if you want to find out about a command type in man command like this: man ifconfig - use up and down to scroll through the documentation, press q to quit.

If you're having DNS issues do this:

sudo nano /etc/resolv.conf - this starts editing resolv.conf which contains nameserver information.
Put a # in front of the line that says nameserver 192.168.x.1 (where x = octet # for your network, usually its 192.168.1.1 - some modem-routers have it as 192.168.0.1)
Now add the following to the bottom:
nameserver 8.8.4.4
Press CTRL+O and press Enter to save the file. Now type in ping google.com and see if it works.

---

### Post by poker158149 on 2011-05-21
Those will come in handy, thank you. 

The nameserver that was in my resolv.conf was not 192.168.1.1 like it should have been. That's my problem, it was not set up properly.
My I.P. address is 24.252.96.160 and it put my nameserver as 24.252.96.1, which it is not.

I did what you said and changed the nameserver to 8.8.4.4 and tried to ping google.com, but it came back saying "ping: host unknown google.com"

---

### Post by slooksterpsv on 2011-05-21
> **poker158149 said:**
> Those will come in handy, thank you. 

The nameserver that was in my resolv.conf was not 192.168.1.1 like it should have been. That's my problem, it was not set up properly.
My I.P. address is 24.252.96.160 and it put my nameserver as 24.252.96.1, which it is not.

I did what you said and changed the nameserver to 8.8.4.4 and tried to ping google.com, but it came back saying "ping: host unknown google.com"

To change the IP address you can try:

sudo dhclient

and that should try to get a DHCP IP Addresse, or you can set one temporarily with:

sudo ifconfig eth0 <ipaddress>

---

### Post by poker158149 on 2011-05-21
I ran the sudo dhclient command and then checked my ifconfig, and now it doesn't have an I.P. address under eth0. 
I also tried to change the I.P., but I honestly don't see what that does, or even know what to change it too.

I'm sorry, this is all new to me.

EDIT: Just to clarify, does it make a difference that I'm on Wi-Fi and not plugged into Ethernet?

---

### Post by slooksterpsv on 2011-05-21
> **poker158149 said:**
> I ran the sudo dhclient command and then checked my ifconfig, and now it doesn't have an I.P. address under eth0. 
I also tried to change the I.P., but I honestly don't see what that does, or even know what to change it too.

I'm sorry, this is all new to me.

EDIT: Just to clarify, does it make a difference that I'm on Wi-Fi and not plugged into Ethernet?

Yes it does, Wifi it'll be wlan0, umm to connect via terminal... mine sometimes does and doesn't work, usually I mess up and forget how to put in a WEP 40-bit key. But here's the gist of what you do;

sudo iwconfig wlan0 essid "your_network_name" key "your_wireless_key" channel auto rate auto

Type in: man iwconfig to find out more how to do it.

---

### Post by drdos2006 on 2011-05-21
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood





```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by poker158149 on 2011-05-21
@slooksterpsv: 
I tried that and it found my essid successfully, but I don't know what to do about the key. I assume that isn't the network's password because it told me invalid argument.
I read into the manual and found that it says passphrase isn't currently supported. Does that mean I can't enter my password for the network? I don't know how else to connect to it.

@drdos2006:
I assume I need to be connected to the internet to do that, which I am having trouble doing. I tried that and it told me 
```
Resolving prdownloads.sourceforge.net... failed: Temporary failure in name resolution.
wget: unable to resolve host address 'prdownloads.sourceforge.net'
```

---

### Post by slooksterpsv on 2011-05-21
Password would be the same as key. It should work though, when I've used it with like a WPA key it's worked.

Anyways when you do the passphrase it should look like this (if it's a word or phrase try it the second way)

sudo iwconfig wlan0 essid MyNetwork key abcde012345
sudo iwconfig wlan0 essid MyNetwork key s:mynetpass

Then do: sudo dhclient
afterwards to get an IP.

---

### Post by poker158149 on 2011-05-22
I did it the first time without "s:" and it came up with:
```

Error for wireless request "Set Encode" (8B2A) :
     invalid argument "MyPasswordHere".

```Then I tried it with the "s:" and it came up with this:

```

Error for wireless request "Set Encode" (8B2A) :
     SET failed on device wlan0 ; Invalid argument.

```

EDIT: Oh, and an update for you. I went into my router configuration just to check, and it turns out my router is using DHCP. 
But when I went to install Ubuntu Server, it told me either it's messed up or the hardware doesn't support it, so I thought I didn't have it enabled when I did.

---

### Post by poker158149 on 2011-05-25
Update for all of you - I plugged it into an Ethernet cable and got it working.

Thank you all for your patience and trying to help me. I just decided to do a little playing around and eventually got it figured out.

---

