---
title: "Connecting to a switch: network is unreachable"
date: 2010-03-09
forum: Server Platforms
---

### Post by AnthonyA on 2010-03-09
Hello everyone!

First, a little background on what I am trying to do. I am a newbie to ubuntu and a bit of a newbie to client/server networking. I installed a copy of Ubuntu Server 8.04 with the latest release of EBox Platform on my HP laptop to mess around with. I am hoping to get it working as an authentication and file server for a couple of computers in the future.

I am having some trouble with connecting to my network. Basically, I have my Ubuntu Server plugged into a switch via ethernet cable. I also have a computer running Windows XP Home plugged into the switch. I'm just trying to get them to ping, nothing fancy yet (I'm just playing around, as I said).

I have tried setting up a static IP using the universal instructions concerning /etc/network/interfaces (adding in auto eth0 with all the parameters to make it static). I also set up a static IP with my Windows XP computer. I'm doing this because I can't use DHCP with the switch.

So, with these static IP settings configured, I try to ping the XP computer. I get the error "connect: network is unreachable" I also get an error when I try to ping the Ubuntu server from the XP machine. Neither one seems to be able to communicate.

I have ruled out the switch as the problem because I connected two XP machines with static IP addresses and they could ping just fine. Also, I connected the XP machine to a router and the Ubuntu server to a router. I configured DHCP on both (again, in the /etc/network/interfaces) and they could ping and talk just fine.

I'm just at a loss. They seem to be connected fine and I can't get them to ping. Like I said, I am a definite newbie to Ubuntu, and I'm just starting to learn client server networking. Also, I'm very new to command prompt and terminal, but I'm learning. Any help that anyone could provide with this matter would be greatly appreciated.

Thanks so much!

Anthony

---

### Post by AnthonyA on 2010-03-09
Here's an update on this:

I tried connecting the Ubuntu server to my router and the Windows XP computer to my router. I gave the ubuntu server a static IP in /etc/network/interfaces

address: 192.168.254.5
netmask 255.255.255.0
network 192.168.254.0
gateway 192.168.254.254  <---My router's IP address

I saved these changes and restarted the computer.

When I restarted the computer, EBox showed the computer as connected with an IP address of 192.168.254.2 (clearly not what I had set). So I checked the /etc/network/interfaces file and it displayed the following:

iface eth0 inet dhcp


So basically, when I set a static IP, the darn thing just reverts to a DHCP when I restart it.

If anyone has any ideas, I would greatly appreciate them. You all know much more than I do, I'm sure.

Thanks,

Anthony

---

### Post by Iowan on 2010-03-09
I presume the netmask ( [COLOR="Red"]25[/COLOR].255.255.0)is a typo...
How did you edit */etc/network/interfaces*?
 Did you use **sudo** (or **gksudo gedit**)?

---

### Post by AnthonyA on 2010-03-10
Yes that would be a typo. My bad, thanks for pointing it out.

I used "sudo nano /etc/network/interfaces"

---

### Post by Iowan on 2010-03-10
Hmmm... Reason I asked was to see if you might have neglected the "sudo" part - and the file didn't actually save the edits. Have you checked it after editing - but before restarting (to verify the edits got saved)?

---

### Post by spynappels on 2010-03-11
Just checking that that you replaced the dhcp in

```
iface eth0 inet dhcp
```

with static?

Your /etc/network/interfaces file should look something like this

```
iface eth0 inet static

address: 192.168.254.5
netmask 255.255.255.0
network 192.168.254.0
gateway 192.168.254.254
``` 

then save and check as Iowan has said.

Rather than restarting the computer, just restart the networking stack

```
sudo /etc/init.d/networking restart
```

and then check the ip config

```
ifconfig eth0
```

If that still does not work, can you post the actual content of your interfaces file and the output of ifconfig?

Also, you are running server rather than desktop, aren't you?

---

### Post by AnthonyA on 2010-03-11
Hey everyone,
 
I was finally able to get everything to work last night. I read somewhere that I should uninstall the DHCP server, which is did with:
 
```
 
sudo apt-get remove dhcp3

```
 
Once I did that and configured my router to disable DHCP, it worked fine with my router. I was able to ping my Windows XP computer and it was able to ping Ubuntu.
 
Then I plugged everything into the switch instead of the router. It still worked fine. I was very excited :D
 
Oddly enough, I can't seem to find the article that said to uninstall the DHCP server :(
 
I'm sort of annoyed that I can't relocate this article, but oh well. At least it works!
 
Thanks for all of your help. I really appreciate it.

---

### Post by Iowan on 2010-03-12
[[SOLVED]]("http://https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  :p

---

