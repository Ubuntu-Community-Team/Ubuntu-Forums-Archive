---
title: "Remote access/control ubuntu server"
date: 2008-05-13
forum: Server Platforms
---

### Post by Mr_Whippy on 2008-05-13
Hi all,

Thanks again for taking the time to read this,

hopefully a quick question what do i need to do to allow remote access/control of my ubuntu server, I am not looking for a GUI control really i wont to get my head around the CL, i will be running virtual servers on the system as well.

---

### Post by bluefrog on 2008-05-13
install openssh-server and you're all set
then
ssh your-user@your-server-IP

James Dupin

---

### Post by cdtech on 2008-05-13
And a command line from the terminal "slogin user@yourserver". I also use putty when I'm on my windows desktop.

---

### Post by Mr_Whippy on 2008-05-13
so all i need to do one the desktop is type sudo get-apt openssh-server that will install it, then from my desktop run a CL and type ssh usrname@server-ip, cheers thanks for that, 

i will be going down the putty route i think for my windows box to.

thanks again

---

### Post by Mr_Whippy on 2008-05-13
hey again all,

well i have installed openssh both client and server, on the correct machines however when i try to connect i get a "no route to host message", also i cant ping the server. however i know i have a static ip set up on it, do i need to open any ports or change any settings. 

am of to google now also but thanks for any help

---

### Post by whitey on 2008-05-13
> **Mr_Whippy said:**
> 
when i try to connect i get a "no route to host message", also i cant ping the server. however i know i have a static ip set up on it, do i need to open any ports or change any settings. 


Can you ping out from your linux box to another box on your network?  Sounds like you have some networking issues you need to solve before you head back to the sshd problem.

run the following from the console, and see if you get an IP adress:

# ifconfig

---

### Post by cdtech on 2008-05-13
Do you have a web server setup? Can you view that? Ping an external site such as google or something. It may be a firewall issue. You have to open the port to listen on your static IP (port 22).

Never mind, I just re read > "no route to host message" it's a network issue.

---

### Post by Thirtysixway on 2008-05-13
If you're behind a router and you want to access your server over the internet, you may need to forward the port on the router.

---

### Post by Mr_Whippy on 2008-05-13
looks like your right whitey.

i get nothing when i ping from either machine to each other, and i get nothing on the #ifconfig either, 

at the moment all i have running is the server, an ubuntu client, my router all connected through a switch, i have given the server a static ip, the ubuntu client is the machine with two nics in it, so that is connected to the router then to the switch. i have no dns apart from what is on the switch could that be the problem

thanks for the help so far

---

### Post by Mr_Whippy on 2008-05-13
all the machines are inside the network, the router is just the connection to the outside world, however it seems that the router can only see the two nics on the client machine as well. i am thinking about taking the dhcp down, however i have a "personal" pc downstairs that i use for gaming etc.. that is not effectively on this network, that may be affected by doing this.

---

### Post by whitey on 2008-05-14
Try to setup your NIC on your box to run DHCP, once you have DHCP running and can get an IP address, then you can use static routes.  I would also check the owners manual on our router, some of them do deal well with routing non-dhcp clients.  Even if you turn off DHCP on your router, it may not properly route to your static server.  It will however remember your MAC address on your linux box so if you restart your server it will reassign the original IP address.

---

### Post by Mr_Whippy on 2008-05-15
Cheers again whitey i will give that a go, I was playing cricket last night so didnt get chance to have a look at anything will try to get on it tonight, with what you have recomended.

thanks again for your help

---

### Post by hyper_ch on 2008-05-15
I'd also recommend to install [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

---

