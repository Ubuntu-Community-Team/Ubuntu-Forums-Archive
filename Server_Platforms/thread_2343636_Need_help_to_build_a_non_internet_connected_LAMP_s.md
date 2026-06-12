---
title: "Need help to build a non internet connected LAMP server"
date: 2016-11-17
forum: Server Platforms
---

### Post by alfoz on 2016-11-17
Hi everyone. hopefully someone out there can sympathize with me and help me out.
I am a total newbie to ubuntu and therefore struggle to understand some of the directions given ( i am coming over from windows AGGGGHHHHHHHH).
Ok a bit of background.
i am starting out alone a a web designer. no issues there i use my pc to write them quite happily.
now to test the sites usability and for proof reading i was using wamp (Xamp). but found that it really slugged up pc as to being unusable.
At present i only have access to mobile wifi due to demographic reasons ( new build and not all services are in place yet)
as you can imagine uploading to a test host server is costing a fortune.
So i have come up with hat some look at as a hairbrained scheme but in theory is quite possible.
run my own LAMP server over a private LAN so i can test sites out on all devices, rather than chewing up data.
problems i have are after installing ubunto 14.04 LTS (tried the server and just couldnt get head round it). is when following various tutorials they seem to "fall off a cliff" after a while, they all start off fine giving full commands and about three quarters through seem to miss the commands off to get to a certain stage. (IE create this directory... where upon there is no makedir command it there . or now access root).
 i can get the LAMP installed and get it to a stage where i can see the test page on pc vie using the ubuntu pc IP address.
is there a way without the internet i can set a domain name.
from there what is the best way to upload files to the /var/www folder ( ie filezilla.)
i run ubuntu into a wired router so in theory i can set it to a static IP as it would never change
basicaly rather than typing in 192.168.2.3 i would rather have a virtual domain name set up of webserver.com.
can some one with a lot more knowledge than myself help me out here please as i seem to be getting nowhere after a fortnight of trying . remembering that the ubuntu pc will NOT have access to internet so registering domains  externally is not an option it would have to be virtual ( bind9 i think but trying to set it up blind is near impossible)
sorry for the long winded first post
Many thanks
Alfoz

---

### Post by wildmanne39 on 2016-11-17
I recommend that you break that block of text up and make it easy to read. Can you state in short terms what you are trying to accomplish and what you have tried?
Thanks

---

### Post by wildmanne39 on 2016-11-17
*Thread moved to **Server Platforms**.*

---

### Post by alfoz on 2016-11-17
Hi Wildman.
Basically I want to "build" a non internet connected LAMP server to test websites on without having to redort to mobile 3g internet connection.
Has anyone got a full "preferably in detail" guide.
I have got as far as getting ubunto 14.04 LTS installed and got the LAMP package installed  as to being able to see the test page in Firefox. on ubunto pc and windows pc.. thats it. that's as far as I can get without screwing it up and having to reload it  (16 times so far lol)

---

### Post by dudumomo on 2016-11-18
Hi Alfoz,

This is something many others devs or web designers are actually doing. So it should not be too difficult.

You have install Ubuntu and LAMP packages already and it seems to be working right? Let me answer your others questions:

1) How to upload files
For your question on how to upload files, the easiest way will be by using Filezilla with SFTP connection (FTP over SSH), using your login/password of your server. Not additional effort needed

2) How to set up a domain name for local network
Here it depends on what you want to do:
- If you will always have the same clients connecting to your server, you could set up your clients in the host file to know that "myserver" = "192.168.1.xx"
This is simple to do, but you have to do it on all the machines connected to the network. 
- If you want to make it automatic, your router should be able to do it. You can usually assign a name to a MAC Address. So with your Server's Mac address (sudo ifconfig -a), you can try to find such option in your router. Once done, all devices connected to your network (Even new machines) will be able to find your server by its name.
- If you want to make it automatic and your router don't have such feature, you can run your own DNS Server (with Dnsmasq) and do it. But more complicated. (But easier than with bind9)

3) How to get a static IP
2 choices:
- In your router setting, assign your MAC address to a static IP (Like a domain name)
- On your server, configure it to get a static IP ==> [http://freedif.org/network-configuration-static-ip-on-linux/](http://freedif.org/network-configuration-static-ip-on-linux/) Very simple to do.

Good luck !

---

### Post by mastablasta on 2016-11-18
when i test i use virtualbox and then just load images such as those found at bitnami stack (or in turnkey linux). everything is preset and ready to go. well except for your virtual domain name. not sure why you would need that. just put each site in it's own folder. when you go live you can move the whole forlder on server and point apache/ngnix to it.

also using ubutnu desktop as server is a waste of resoruces. if you really must have a desktop loaded then take something light instead such as Lubuntu.

---

### Post by alfoz on 2016-11-18
hi mastablasta. I am running a virtual environment on my windows pc already but it wont display to other devices (tablets phones etc) hence i decided to build my own dedicated apache server that i can access with various devices by logging into my LAN. I went for the desktop as i am just not comfortable using just command line interface ( too much of windows im afraid)
Hi dudumomo. thanks for that. thats as i understood it and got a basic install via following numerous online tutorials on the setup.
However i just cant do anything other than punch in http:192.168.2.3 ( local ip addy of ubunto pc) on any device on lan and just see a welcome page.
total newbie to the network side of things and just dont get it. In theory if i can see the welcome http page (created when i followed tutorial on install) then the server is there visable and working. This however is not the case. I just cant do anything other than look at that page. i cant copy folders via a usb drive key. i cant log in via filezilla.  
basically i think i need a full in depth (written for idiots) guide to installing and configuring ubunto to run as a dedicated apache server. having searched high and low and following numerous tutorials i am back at square one as all the tutorials assume that server is connected to broadband which as stated in first post i wont be able to access for about six months due to demographic reasons. and i cant keep it connected to mobile 3g as its just not practical.
alfoz

---

### Post by darkod on 2016-11-18
1. To upload/copy files to the server:
Have you enabled ssh server on it? If you download and open putty on your windows PC, can you login with your ubuntu user to the ubuntu IP using ssh session?

If you haven't installed ssh server on your server, do:
```
sudo apt-get install openssh-server
```

You need to do that in terminal of course. Most commands issued for servers are command line, not GUI, so get used to it (even though you installed desktop version). After you have ssh server installed, you can reach your server over ssh session from any device on the LAN.

That will also make scp available to copy files to the server. I recommend winscp, it's free and does perfect job. Filezilla is OK but mainly directed to ftp and I find it unnecessarily complicated for simple scp transfer. Note that in ubuntu you don't log in directly as root and go anywhere to copy anything. First copy to your user home folder, then use ssh session and move the files where you want to.

If you intend to keep only one domain in apache, you don't even need to bother modifying anything. Just copy your web files to the default folder which is /var/www/html. If the apache welcome page shows up now, it works. Any web files put into that folder, if properly designed, will display that site. You don't even need specifically to link it to a domain name, by opening http://<server IP> from the LAN, it will open.

If you want to use domain name on clients, you need to make entry in the local hosts file as suggested...

---

### Post by SeijiSensei on 2016-11-18
You're probably using NAT as the networking model for the virtual hosts you set up which is why other machines on the network cannot see them.  If you're using VirtualBox go to the Network settings and switch the interface to "bridged." Now the virtual guest will get an address on the same network as its physical host and be visible anywhere the physical host is.

---

