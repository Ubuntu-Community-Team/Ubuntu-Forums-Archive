---
title: "ssh login from outside of network...problem is it dont happen"
date: 2007-01-07
forum: Server Platforms
---

### Post by wraithe on 2007-01-07
I have ubuntu 5.10 breezy set up as a samba server with internet connection sharing using masq...
What i need is to be able to ssh into this box from home, i can do this with my pc on lan but cant from outside of the lan...
i installed samba and done the bridging with ssh, but have tried to get in from outside and it isnt there...
now i may have the ip wrong, or have the port closed...at this stage i have no authority key setup, till i get this sorted, then i can close it up...i may need to change what eth* it is listening tooo, but dont know if that is it either...
I have it still set to port 22, and have only samba and masq setup...this is a server box with no graphics...so i cant use these lil clicks and stuff like most of the info i have found , shows...

i am logging in using putty on a winxp machine, and from outside i have got a friend trying using putty also on a winxp machine...
I need to be able to log as both admin and root to this linux box....
I may not have my ip address from the internet right, cant be sure as i dont know what it is, and not sure if i got the right one to start with...

---

### Post by kidders on 2007-01-07
Hi there,

It seems from your post that you're already aware of all the things that need to be right in order to get SSH working for you. Just try to think things through logically...

[LIST]
[*]If something is sitting between your Linux box and the internet, is it configured to forward port 22 to the right place?
[*]Is SSH bound to the right interface & port?
[*]Is your linux box's firewall blocking incoming connections on port 22?
[/LIST]

What error message do you receive when you try to connect?

---

### Post by gaebriel on 2007-01-07
If you can use putty from a internal box and access SSH, then iptables (linux firewall) is allowing access to SSH. Most likely you need to configure your internet router to forward TCP port 22 traffic to this internal IP of this Ubuntu server. What kind of internet router do you have? 

How many NICs do you have in this box? Does it have a public IP? You can answer both of those questions by running `ifconfig` from the shell. To get the public IP of your internet connection, run `elinks whatismyip.com` from the shell. If elinks isn't installed just use apt-get to install it. To make sure the local ubuntu firewall is allowing SSH access across all interfaces run `sudo iptables -I INPUT 1 -p tcp 22 -j ACCEPT`.

---

### Post by wraithe on 2007-01-07
thanks kidders...
i knew it was something i had missed, damm router...
spent about 12 hours trying to find what i had missed, turned out to be something so simple...
usually the case...
always believe that it only takes someone else to suggest something and it can be found...
ok now onto last job of pass key then onto limiting users to accessing one site and others to full internet access...
I shall be back for more advice...
Thank you again....](*,)



PS: Gabriel, that command dont work right, didnt have time to work it out, but one of the variables is wrong...sorry, but thanks for the help....

---

### Post by kidders on 2007-01-07
Glad you're sorted.

To open an iptables firewall to incoming TCP connections on port 22, you could use **sudo iptables -I INPUT -p tcp --dport 22 -j ACCEPT** ... but I don't think you need it any more anyhow. :-)

---

### Post by wraithe on 2007-01-08
outside logins are working fine now, just need to get the isp where this unit has to go, to give us a static ip and all shall be gold...
I hate love jobs, but then its good to see things done right too...just went and checked the dsl router where i have to put this unit, and found a heap of ports open, was setup by a tech thats regarded as a good one in town, glad we get along cause i just gave him a mouthful about being so slack...
now onto key gen and all shall be secure somewhat...
cheers guys and thanks a heap...
=D>

---

