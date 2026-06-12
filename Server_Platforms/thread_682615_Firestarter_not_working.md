---
title: "Firestarter not working"
date: 2008-01-30
forum: Server Platforms
---

### Post by quarkhirad on 2008-01-30
Ok now guys i got firestarter working. Then i when i started it started the firewall wizard. i clicked forward . Then it asked me for the network device. I selected Ethernet device (eth0) (this corresponds to my wired lan connection ) Then it has two check box's one saying start the fire wall on dial out and the other saying ip address is assigned by DHCP.

I checked the first one about starting the firewall . The second one i left unchecked as my network is manual and not DHCP. I then clicked Forward .

On the next page i got a check box to enable internet connection sharing. I checked that two. Then in the drop box i selected Ethernet device ( eth0). When i clicked next it said that the internet connection device and local network cannot be the same. Hence i clicked back and changed the network device to ipv6 (sit 0 ) (or something like that). Let the remaining settings same and then clicked forward.

This time when i chose to enable internet connection sharing and chose Ethernet device (eth0) it allowed me. I then clicked save on the next page and then the programme gave me a error message stating

Failed to start Firewall
The device sit0 is not ready

Please check your network device settings and make sure your internet connection is active.


Help how do i get this correct . Please tell me how to set up firestarter

---

### Post by p_quarles on 2008-01-30
It sounds like you are trying to share a connection using only one NIC. I'm not sure that's possible. :D

---

### Post by hyper_ch on 2008-01-30
are you sure you need firestarter at all?

---

### Post by quarkhirad on 2008-01-30
Ok well i wanted to telnet to my desktop server which is having ubuntu 6.06 LTS but i could not do so it just refuses to connect.Hence i thought that i could but up a firewall on the system and then allow only the port for telnet that is 23 and i should be able to telnet . 

I have a desktop with an intel motherboard 1.73Ghz p4 with 256Mb ram and a 10/100mbps lan for connecting to the network. If this info helps

khirad

---

### Post by p_quarles on 2008-01-30
Just need a little more info here:

--Is there some reason you need to use Telnet rather than SSH?
--Have you installed a Telnet server on the machine to which you are trying to connect?
--Can you give us a more detailed description of your network layout? I'm gathering that there are three separate machines here, but I'm not completely sure.

---

### Post by quarkhirad on 2008-01-30
> **p_quarles said:**
> Just need a little more info here:

--Is there some reason you need to use Telnet rather than SSH?

Yes it is because my clients who will use this services use windows. As far as i am aware windows does not connect using ssh ( like if i click on start the run and type telnet x.y.z.a then it conects to my server with ip x.y.z.a but if i type ssh instead it doesnt work ) Until you install a software like putty or some such software. Since telling my clients install putty is not possible i shall have to do with telnet. I know telnet is less secure but i cant help it. 



--Have you installed a Telnet server on the machine to which you are trying to connect?

I dont know . I installed the following

apt-get install telnetd

Did i leave anything else????



--Can you give us a more detailed description of your network layout? I'm gathering that there are three separate machines here, but I'm not completely sure.


Ok i am studying in a college. In this college we have a computer lab in which there are 120 desktops. They all are connected to a 100mbps switch by a cat 5 cable ( the switch is connect to the internet. I dont know how as the admins wont talk.). Each desktop is assigned an ip address 192.x.y.z . Then there is an ISA server that is used as a proxy server for the comps to get the internet.  

I wanted to have a common space so that faculty notes, downloaded software ( note i only allow open source or free software  NO PIRACY. I am against it myself ), and other things can be shared. Hence i created a file server. I took a desktop installed ubuntu 6.06 then installed samba and then shared a folder called buffer. So now if i want to give my classmate a file xyz. I just go to file browser type smb://x.y.z.a (x.y.z.a is ip of my server) and then open the share folder called buffer put the file in and its shared to any comp in the college lab.Now all my friend has to do is copy it from the share folder.

 Now people would download software and then take it . Due to this a software say firefox browser was downloaded 12 times in five days ( this is not a joke its true ) . Hence using shell programing i got it to act as a download manager. Hers how i created a user called daclub. Now when people telnet to my server they get a prompt to type in user and password. They type daclub as user and then type in the password. The script then asks for the url of the file to be downloaded. Then it checks if the file is already downloaded (this is done by checking a certain shared folder called downloads.) if it isnt then it starts the download and if it is then it tells them the download exists. Now i have created this but i cant test it if i cant telnet to my server. Help :( :( :( :( :( :( :(

 

Now thats why i need Telnet.

---

### Post by p_quarles on 2008-01-30
You don't need to enable a shared connection to do that. Heck, you don't even need Firestarter to do that. Just run the telnet client to the server.

If that doesn't work, there's another issue here and I'm not sure what that would be.

---

### Post by quarkhirad on 2008-01-30
Dear p_quarles

Ok  now i am not too sure about what u mean by 

Just run the telnet client to the server.

Ok so lets get down to square one. After i finished by programing. I came over to my personal laptop that  is connected to the network and then in the terminal i typed the following 

ping x.y.z.a 

i got a reply each time ranging between 0.3ms  to 1 ms 

then typed 

telnet x.y.z.a

Trying x.y.z.a...
telnet: connect to address x.y.z.a: connection refused
tenet: Unable to connect to remote host: Connection refused

it then returned me to the $ promt of the terminal. Now how do i solve this. 

 thanks

---

### Post by p_quarles on 2008-01-30
Do you have a telnet server installed on the machine to which you are trying to connect? Is there a firewall somewhere between your laptop and the remote machine?

---

### Post by quarkhirad on 2008-02-01
On my laptop ( laptop has ubuntu 7.10) when i searched in synaptics for telnet i got a package called telnet and this package is installed. 

On the desktop ( this is the server to which i need to connect and it has ubuntu 6.10) i searched for a package called telnet and got a package called telnetd and telnet both are installed. 

Now as far as firewall there is no firewall between my laptop and the desktop server. 

Also i would like to say that when i try to telnet from laptop to desktop or desktop to laptop both dont work.  It still gives the same error ( see post no 8 )

---

### Post by oedha on 2008-02-01
why dont you use ssh ?
if you still want telnet.......do like p_quarles said :)
~E~

---

### Post by p_quarles on 2008-02-01
Basically, you need to have telnetd installed on the server you want to connect to. I've never used that program (and don't particularly advise it) since it's not encrypted at all (SSH is). You may have to manually start the telnet server. The best advice I can give you is to read the included documentation:
```
man telnetd
```
In the meantime, I'm moving this thread to Servers & Security, as you may get more and better information there.

---

### Post by quarkhirad on 2008-02-01
Ok guys here is some good news 

I got to speak to the original creator of the server ( the original server was a P4 1.73 , 128mb ram and had ubuntu 4.06. So i got a new system and implemented the same on this new system)  and told him to read the thread he told me how to get ssh up and then i can create an icon on system in a shared folder where people click it and it will connect to my server via ssh . I like that . Off course i have got ssh up now just need to go through some documentation to do it. Hope it works . If it works i shall post the solution here.

---

