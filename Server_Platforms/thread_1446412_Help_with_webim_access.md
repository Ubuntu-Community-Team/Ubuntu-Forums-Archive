---
title: "Help with webim access"
date: 2010-04-04
forum: Server Platforms
---

### Post by cK` on 2010-04-04
Hello i have a few questions about Unbuntu Server.

First off i am obsoletely 100% brand new to anything linux.

I recently installed the newest Unbuntu server edition onto my server and installed webmin. 

I am having a problem with webmin, when i remote view it from a computer that is connected to the same network eveything works great. But when i try to view it from a computer not on the network my browser username:10000 does not exist.

I have my ip permissions set to all users in webmin. Also i tryed to get into the /etc/webmin/miniserv.conf but instead of getting me to the allow= and denied= it says permission denied.


Can anyone please explain how i can view my server with webmin on a computer outside the network???

-Thanks so much

---

### Post by dudumomo on 2010-04-04
That's weird..
How did you install webmin ?

May be this link can help you: [http://www.freelydifferent.com/self-hosting/webmin-webbased-interface-system-administration/](http://www.freelydifferent.com/self-hosting/webmin-webbased-interface-system-administration/)

Anyway, usually, if your port 10000 is open into your firewall, you should be able to connect to your webmin interface. (I guess you do)
Relating to your user, this one has to be able to run any command with "sudo"

---

### Post by cK` on 2010-04-04
> **dudumomo said:**
> That's weird..
How did you install webmin ?

May be this link can help you: [http://www.freelydifferent.com/self-hosting/webmin-webbased-interface-system-administration/](http://www.freelydifferent.com/self-hosting/webmin-webbased-interface-system-administration/)

Anyway, usually, if your port 10000 is open into your firewall, you should be able to connect to your webmin interface. (I guess you do)
Relating to your user, this one has to be able to run any command with "sudo"

I uninstall-ed webmin and reinstalled it using the above tutorial. Same problem =/

So like i said before i can view my webmin from this computer (its in my garage and also connect to the same router my server is connected to). But i cannot view it from the computer in my house or any other computer (not connected to the same router that my server and this computer are connected to). Am i missing somthing? Do i need to tell unbuntu to read connections outside of my network?

Regarding my user

When executing this line of code i am logged into the user i created when installing Unbuntu server edition

/etc/webmin/miniserv.conf

when executing this code i get this error

-bash : /etc/webmin/miniserv.conf : Permission Denied.

When typing in this code i am logged into the same user that i created when installing the OS, i also used to edit the sources.list and install webmin, it even asked for a root password. 

So i think i am using a user that can use all sudo commands right??

Thanks for the help!

---

### Post by dudumomo on 2010-04-04
Actually, to modify a file from /etc/ you need to have the root privileges. (With the command sudo)

I didn't understand quite well, do you have access to your webmin interface from another computer outside your network ?
May be you can give me the URL.

If you don't have access to webmin, check if you have correctly open the port 10000

---

### Post by cK` on 2010-04-04
Sorry for the confusion.

No i do not have access to my webmin from a computer outside of my network. I CAN however access and login to webmin from another computer inside my network.

---

### Post by cK` on 2010-04-04
Oh and my URL is [https://server:10000/](https://server:10000/)

It wont work though.

I have a feeling its going to be somthing like "Well first you have to set up webmin to view server outside of the network" But i have read that is does that by default.  If its an obviouse anwser i am sorry. But i have been pulling teeth trying to figure this out :lolflag:

---

### Post by dudumomo on 2010-04-04
[https://server](https://server) is not a correct domain name !
Try instead with your IP:[http://www.whatismyip.com/](http://www.whatismyip.com/)
[https://62.25.etc..:10000](https://62.25.etc..:10000)

---

### Post by cK` on 2010-04-04
I forgot to mention [https://server:1000](https://server:1000) will work on the network but not on the web.

Anyway, 

I believe i can only use that website with a server browser?


I typed in sudo ifconfig to view my ip and it gave me 2.

one had .1 at the end and the other had .255 at the end. Other than that they were the same ip numbers and neither worked.

[http://192.168.122.1:10000/](http://192.168.122.1:10000/)
[https://192.168.122.255:10000/](https://192.168.122.255:10000/)

---

### Post by dudumomo on 2010-04-04
server:10000 is the name of your machine, then you will be able to see it only within your local network.
If you want to be able to use trough internet, you need either to use your Internet IP or to use a domain name (There are some free domain name if you want, as dyndns)

the command ifconfig gives you only your local IP.
so this IP will work only within your local network.

You have to use your "internet" IP address.
This website will give it to you: [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by cK` on 2010-04-04
I completely understand what your saying and i thank you very much for answering such a basic question.



I am sorry, but i do not know how to view a website with unbuntu server. Or through webmin. In otherwords I dont know where to put that URL.

---

### Post by dudumomo on 2010-04-04
Euh...webmin is a web administration interface for your Ubuntu Server.
When you need to enter: [https://yourwebsite.com:10000](https://yourwebsite.com:10000) into your browser to get access to your admin panel.

In my case, if you go to: [www.freelydifferent.com:10000](www.freelydifferent.com:10000) you will have see the webmin login page.
But from my local network, I simply need to go to 192.168.0.1:1000 or serverwebmin:10000 (if serverwebmin was the name of the computer)

---

### Post by steev182 on 2010-04-04
On the computer you are accessing ubuntuforums.

just go to [www.whatsmyip.com](www.whatsmyip.com) and then if you've opened port 10000 you should be able to go to [http://ipfromwhatsmyip:10000](http://ipfromwhatsmyip:10000)

---

### Post by cK` on 2010-04-04
> **steev182 said:**
> On the computer you are accessing ubuntuforums.

just go to [www.whatsmyip.com](www.whatsmyip.com) and then if you've opened port 10000 you should be able to go to [http://ipfromwhatsmyip:10000](http://ipfromwhatsmyip:10000)

I need to open port 10000 on the firewall right? I think i opened it because server:1000 works but myip:10000 does not work.

Didnt Dudumomo say that myip:10000 will only work on a machine that is connect to the same network as the unbuntu server?

When i go to this website
[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) 
and type in my port it says its closed, am i doing something wrong?

Is there a reason i can use server:1000 to login but not myip:10000 if my port 10000 if closed?

---

### Post by jfmanamtr on 2010-04-04
Ok. Are you using server:1000 or server:10000? The exact server port you use when going server:port is important. Cause if you can access it internally on port 1000, then that is the port you will need to forward through your firewall to access it from ip:port.
 
~John

---

### Post by dudumomo on 2010-04-04
With your "internet" IP:10000 if the port 10000 is correctly opened, you should have access to your webmin panel.

Can you PM me with your IP if you don't mind.

You can also ping your IP from another machine outside your network.

How did you open your port ?
Do you have a Box, router ?

Edit: oh ? server:1000 works ? weird to use the port 1,000 and not the 10,000

---

### Post by spynappels on 2010-04-04
You need to set up Port Forwarding on your router/modem. forward your Webmin port (normally 10000)  from outside to the LAN IP of your server (192.168.1.x). Google Port Forwarding and the name of your router to get specific instructions.

---

### Post by cK` on 2010-04-04
In windows i opened port 10000 by logging into my Dlink EBR2310 router

I put the ip i got from the command ipconfig /all in  as the ip 

[IMG]http://i447.photobucket.com/albums/qq199/cking111/untitled.jpg[/IMG]

I put 10000 as my start and stop  port. I set it to TCP saved my changes and then tryed to use my ip from whatismyip.com to login but is still acting like the port is not open.



Oh and no i cannot use 1000 to login i meant to say 10000 sorry i forgot a zero.

---

### Post by CharlesA on 2010-04-04
If you are trying to access webmin from the local network by using the external IP, it won't work (same thing as getting a busy signal).

It would probably be simpler and safer to just SSH into the box and tunnel webmin over SSH. (Then again I like SSH...)

---

### Post by cK` on 2010-04-05
I got ssh to work but i do not know how to "tunnel webmin over ssh"

Is their a guide i could read? i am trying to google it but have not found anything helpful yet.


Oh and i figured out that my ports were not opened correct and now i can view my server via webmin from a computer outside the network. but your said tunnelings webmin over ssh would be safer?



Thanks!

---

### Post by CharlesA on 2010-04-05
It would probably be safer, yes. SSH encrypts the traffic, where as the regular webmin uses SSL (which does encryption as well, but having a web interface accessable from the internet sounds like a bad idea)

The way I have it set up is that I only have the SSH port open on my router and I've got SSH locked down with iptables and key auth. If I need to access something like webmin remotely, all I have to do is run this:

```
ssh -L 10000:192.168.1.2:10000 user@host
```

Then I can connect by opening a web browser and pointing it to [https://127.0.0.1:10000](https://127.0.0.1:10000)

You'd get an "invalid certificate" but that's normal since it is self signed.

Here's a tutorial: [http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

---

### Post by dudumomo on 2010-04-05
Hi.
You can indeed you SSH.
But in anycase it is not normal that you cannot connect to your webmin interface from outside your network.

I'm not really sure, but did you try to open not only TCP but also UDP ?
And why are you using the command ipconfig to get your IP from windows ?

---

### Post by CharlesA on 2010-04-05
Typically, the ports would need to be opened on the router, which is why you cannot access it from outside your LAN.

---

### Post by cK` on 2010-04-05
> **CharlesA said:**
> It would probably be safer, yes. SSH encrypts the traffic, where as the regular webmin uses SSL (which does encryption as well, but having a web interface accessable from the internet sounds like a bad idea)

The way I have it set up is that I only have the SSH port open on my router and I've got SSH locked down with iptables and key auth. If I need to access something like webmin remotely, all I have to do is run this:

```
ssh -L 10000:192.168.1.2:10000 user@host
```

Then I can connect by opening a web browser and pointing it to [https://127.0.0.1:10000](https://127.0.0.1:10000)

You'd get an "invalid certificate" but that's normal since it is self signed.

Here's a tutorial: [http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)



Thanks, sounds like what i need to do also.







> **dudumomo said:**
> Hi.
You can indeed you SSH.
But in anycase it is not normal that you cannot connect to your webmin interface from outside your network.

I'm not really sure, but did you try to open not only TCP but also UDP ?
And why are you using the command ipconfig to get your IP from windows ?



I am now able to accsess webmin from outside my network!

Thank you, and everyone else who helped me i thank you also. It would have been 1 billion times harder to figure it out without you all your help.


I did not have my ports open correctly](*,)

---

### Post by cK` on 2010-04-07
Hey guys i got a new problem. I reinstalled unbuntu server today for noobie reasons and i then tryed to reinstall webmin and this is what i did. 

 

after typing this to install webmin

sudo apt-get install webmin

it started doing its thing and then it halts. Giving me the following message

"Package webmin is not available, but is referred to by another package. this may mean that the package is missing, had been obsoleted , or is only available from another source."


The first thing i did after installing unbuntu server was edit the sources list like this.

cd /etc/apt/

then i tpyed sudo nano sources.list
I uncommented everything with "deb" in front of it

I also uncommented 
deb cdrom:[unbuntu-servers 9.10 _karmic koala_

i then typed this
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.510_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510_all.deb)

after getting that i typed this
apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

then i tryed to install it and got that error.




Can any explain to me what is happening here?



I also tryed to install it using this tutorial [http://www.freelydifferent.com/self-hosting/webmin-webbased-interface-system-administration/](http://www.freelydifferent.com/self-hosting/webmin-webbased-interface-system-administration/)

When i got to the part when i need to type 

sudo apt-get install update this is what happened

W: Failed to fetch cdrom://unbuntu-server 9.10 _karmic_ koala_ect....
please use apt-cd to make this cdrom recognized by apt.


If anyone could explain to me what is going on it would be much appreciated.

-Thanks!



First i edited the sources.list
cd /etc/apt/


then i tpyed sudo nano sources.list

I uncommented everything with "deb" in front of it

I also uncommented 
deb cdrom:[unbuntu-servers 9.10 _karmic koala_

i then typed this
sudo wget [http://prdownloads.sourceforge.net/w..._1.510_all.deb](http://prdownloads.sourceforge.net/w..._1.510_all.deb)

after getting that i typed this

apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

When that was finished i typed this
sudo apt-get install webmin

it started doing its thing and then it halts. Giving me the following message

"Package webmin is not available, but is referred to by another package. this may mean that the package is missing, had been obsoleted , or is only available from another source."


Can any explain to me what is happening here?




I also tryed installing it using this tutorial given to me by DUDUMOMO early in the week.

[http://www.freelydifferent.com/self-...dministration/](http://www.freelydifferent.com/self-...dministration/)

When i got to the part when i need to type 

sudo apt-get install update this is what happened

W: Failed to fetch cdrom://unbuntu-server 9.10 _karmic_ koala_ect....
please use apt-cd to make this cdrom recognized by apt.

W: Failed to fetch [http://download.webmin.com/repository/dists/sarge/contrib/binary-ect](http://download.webmin.com/repository/dists/sarge/contrib/binary-ect)....



I have been looking around for reason of why this might be happening, some say i need the right perl downloads, but i have checked that and they are all updated, i have also checked my sources.list so i really dont know whats wrong. ANy help would be awesome.

I know this has nothing to do with the original topic but i did not want to make a new thread.

Especially if its painfully obvious.


-Thanks!

---

