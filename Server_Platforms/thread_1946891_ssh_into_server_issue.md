---
title: "ssh into server issue?"
date: 2012-03-25
forum: Server Platforms
---

### Post by gmenfan83 on 2012-03-25
Ok I am a bit confused. I recently set up a virtual Ubuntu server on my windows desktop. My primary machine is a Mac. From my server I type "ifconfig" to get my information etc. there are 2 displays. Etho and loop back. Now when I try to ssh into my server from my Mac using my etho inet address I get an empty prompt in terminal. When I use my loop back address which is 127.0.0.1 (I believe to be standard) I get a prompt for password. I enter it but it almost seems as if though I'm ssh'ing right back into my Mac.  I hope I am making sense. If I explained any of this wrongly I apologize. Please have patience as I am new to this. Thank you.

---

### Post by darkod on 2012-03-25
The 127.0.0.1 is the localhost address. So yes, with it you are ssh-ing into the Mac.

Did you maybe enable any firewall on the server? If you did, unless you open port 22 (or another port if you changed it) it will not let you in.

Also, first make sure the network on the server is working fine. Log in on it and try
ping 8.8.8.8

for example. If you receive a reply the internet is working and most probably the network setup.

Also try to ping the Mac address from the server, and the server address from the Mac.

Unless an activated firewall is blocking you, it sounds like a network issue. Double check it.

---

### Post by gmenfan83 on 2012-03-25
@Darkod. Thanks for the reply. I do not believe i have enabled a firewall server side. The only installations i made to the server were, LAMP,  and mail server upon installation. I ran "ping 8.8.8.8 from the server and am getting output "64 bytes from 8.8.8.8: icmp_seq= then numbers are displaying in ascending order, ex icmp_seq=336 ttl=52 time " " and so on. I am not sure how to enable or open port 22, do i edit my ssh config file? I also have firewall enabled on my Mac but tested this wit it disabled and received the same results. I also have remote login enabled on my Mac. Thanks for the help

---

### Post by darkod on 2012-03-25
It looks like the internet on the server is working fine.

If you try to ping the server IP from the Mac, does it return a reply?

Also, I don't know how is it working on a Mac, but how are you trying the ssh, similar to linux with:
ssh username@server_ip?

---

### Post by darkod on 2012-03-25
PS. It just occurred to me. If the only roles you installed were LAMP and mail, ssh server is not installed. It doesn't get installed by default. Did you select it from the roles list during install?

If not, you need to add it with:
sudo apt-get install openssh-server

---

### Post by gmenfan83 on 2012-03-25
I apologize for not mentioning that i did intact install open ssh as you describe after the initial server installation.
If i ping the server from the Mac i get he same results as the server ping. I am attempting to login "ssh 127.0.0.1"

---

### Post by darkod on 2012-03-25
Try with:
ssh username@ip

replacing username with the user you created on the server during the install, and the ip with the actual server ip.

In case ssh on the Mac works differently, also try:
ssh ip

Don't try the ssh 127.0.0.1, that is trying to ssh into the machine you are doing it from, in this case the Mac. You can't enter the server with that. 127.0.0.1 is the local machine address in any OS (in most of them anyway).

---

### Post by darkod on 2012-03-25
I also found one command to test if ssh is running correctly on the server.

You need to execute on the server:
sudo netstat -natp | grep ssh

That should show you if the service is up and running, and the ip and port on which it is listening. It would look like ip:port. The standard port is 22.

---

### Post by gmenfan83 on 2012-03-25
when i check the port as advised it is in fact port 22. Now the only other address i can enter other than my loop back inet address(127.0.0.1) is the ethos inet address which when i enter it (example jay@ethos inet address) as instructed my terminal goes to an empty prompt. I have a cursor but there is no  prompt. Hence after i attempt ssh there is no "Jason-iMac$". It is just the cursor.

---

### Post by BertN45 on 2012-03-25
Often if you use virtual machine software, you will not be able to enter your VM from the local network, because the VM (Ubuntu Server) is behind a NAT. You can only go from the VM to your local PCs and not the other way around. You have to change the network settings of the VM. For example in Virtualbox you have to change the network tab of the VM from NAT to Bridged. In this way the server becomes a full member of the LAN.

---

### Post by gmenfan83 on 2012-03-25
Thank you @ BertN45. I switched my network settings to bridged which changed my ethos inet address and allows me to ssh from my Mac into my ubuntu server properly! I appreciate the help involved with my inquiry! Now just so i understand, what address did my etho0 inet address change to once i altered my network settings to bridged?

---

