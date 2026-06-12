---
title: "Edubuntu Thin Client (using LTSP)"
date: 2007-06-05
forum: Server Platforms
---

### Post by Amal on 2007-06-05
[COLOR="Red"]Dear All,

We don't know how to set a thin client and let other PCs to boot from the server, we are trying all of our best and until today we couldn't let a PC to boot from a server that includes edubuntu.

We entered to this link [http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)
but it includes theory and not the exact way of doing it. Please help as we need to submit an urgent task.

We would appreciate if anyone can provide us with the exact steps to do so.

Thank you,
edubuntu students.[/COLOR]

---

### Post by Amal on 2007-06-07
[FONT="Verdana"]

**Hi (Ed)Ubuntu Team**,

Please do help us on this issue. We are working on **Edubuntu Thin Client Project**. We have installed version 7.04 classroom server. We were following the steps available on Edubuntu official site ( [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted) ) up to these steps we are only done with the server side :p.

Now we are confused :( how to **run** the thin client, in other words how to **boot** from the installed server. We want to run 4 other PCs from this server to **build our classroom Edubuntu lab** where there will be a teacher & students in it. 

Topology: 5 PCs connected by a cable to a switch. The switch is connected with a cable to LAN. One of the Client PCs runs Knoppix & the others Windows Server 2000.

This is very urgent, we tried our best but couldn't figure it out. We would be greatly thankful if you could add your valuable support to us. 

We need steps to apply for building the thin client (Documentation, tutorial, handbook). 

**Regards**,
Amal & Team ;)

[/FONT]

---

### Post by snoop on 2007-06-07
I believe these links have more information on what you need.

[http://www.edubuntu.org/ThinClientConfig](http://www.edubuntu.org/ThinClientConfig)

[http://www.edubuntu.org/Documentation](http://www.edubuntu.org/Documentation)

---

### Post by Amal on 2007-06-08
[FONT="Verdana"]**Hi snoop**,

Thanks a lot for your precious add, but we are done with these steps on the server side.
We want to know what is **next**? How can we make **client PCs** boot from Edubuntu server? 

We found a link for client booting options, we'll try to apply it on PC which has Knoppix OS, and refer back to you guys.

**Link**:
Client boot options (  [http://schools.coe.ru.ac.za/wiki/Building_Thin_Client_Labs](http://schools.coe.ru.ac.za/wiki/Building_Thin_Client_Labs) )

**Regards**,
Amal & Team[/FONT]

---

### Post by snoop on 2007-06-08
I believe this article has everything on setting up the clients and the server, hope this helps.

[http://www.freesoftwaremagazine.com/articles/linux_terminal_server](http://www.freesoftwaremagazine.com/articles/linux_terminal_server)

---

### Post by manway on 2007-06-12
Here are some of the steps I took to install the Edubuntu Server. 

From the desktop, Click Root Terminal

1. Install SSH Server
apt-get install ssh openssh-server

2. Edit network configuration files
sudo gedit  /etc/network/interfaces

3. Edit hosts file. 
sudo gedit /etc/network/hosts

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.20 192.168.0.250;
  option domain-name "example.com";
  option domain-name-servers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;

  filename "/ltsp/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

4. To prevent the resolve.conf file from getting "reset", and changing your network configuration, do the following:

From the system prompt, type chattr +i /etc/resolv.conf and press Enter.

5.echo HCSU > /etc/hostname

6. Install LTSP for Thin Client Server.

sudo apt-get install ltsp-server-standalone openssh-server

sudo ltsp-build-client --arch i386

sudo ltsp-update-sshkeys 

7. Edit DHCPD.conf file for LTSP Thin Client Server
sudo gedit /etc/ltsp/dhcpd.conf
 
authoritative;
subnet 192.168.7.0 netmask 255.255.255.0 {
range 192.168.7.220 192.168.7.250;
option domain-name “lab.stsn.ac.id”;
option domain-name-servers 192.168.7.1;
option broadcast-address 192.168.7.255;
option routers 192.168.7.1;
option subnet-mask 255.255.255.0;
filename “/ltsp/pxelinux.0&#8243;;
option root-path “/opt/ltsp/i386&#8243;;
}

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.20 192.168.0.250;
  option domain-name "HCSU";
  option domain-name-servers 192.168.0.3;
  option broadcast-address 192.168.0.255;
  option routers 192.168.0.1;
  option subnet-mask 255.255.255.0;

# if substring(option vendor-class-identifier, 0, 9 ) = “PXECLIENT” { 
filename “/ltsp/i386/pxelinux.0”;
}
else {
filename “/ltsp/i386/nbi.img”;
}
option root-path “/opt/ltsp/i386”;
}


/etc/init.d/dhcp3-servcer restart

9. Install Apache Webserver

sudo aptitude -r install apache2

sudo /etc/init.d/apache2 restart

10. Install Backup Software

apt-get  install sbackup 

11. Install SchoolTool (Alpha Version)

sudo apt-get install build-essential
sudo apt-get install python-dev
sudo apt-get install python-imaging
sudo apt-get install python-libxml2
download ez_setup.py
cp /home/michaelanway/ez_setup.py 
Python ez_setup.py


Download alpha2-install.sh from
[ftp://ftp.schooltool.org/pub/schooltool/setup-scripts/alpha2-install.sh](ftp://ftp.schooltool.org/pub/schooltool/setup-scripts/alpha2-install.sh)
to /usr/local/share directory

download python-2.4.3tar.tgz file from [http://www.python.org/download/releases/2.4.3/](http://www.python.org/download/releases/2.4.3/).

cp Python-2.4.3.tgz /usr/local/share

cd /usr/local/share
tar -zxvf Python-2.4.3.tgz
cd Python-2.4.3/
./configure
make
make install

cp /home/ma/alpha2-install.sh /usr/local/share/schooltool/
cd /usr/local/share/schooltool/

chmod +x alpha2-install.sh 
./alpha2-install.sh.

Cd st2006-alpha2/st/

./bin/schooltool-server
From web browser, type [http://locahost:7800](http://locahost:7800)
Login: manager
Password: schooltool
Ignore error message when it runs the tests. 

In the fall, apt-get install schooltool can be used to install School Tool

11. Install Microsoft Fonts
sudo apt-get install msttcorefonts

12. Install Multimedia Support
sudo apt-get install totem-xine vorbis-tools sox faad lame \imagemagick ffmpeg mjpegtools

13. Install java
sudo apt-get install sun-java5-jre sun-java5-plugin \sun-java5-fonts

14. Install Adobe Flash Plugins

Download latest Adobe Flash plugin Linux file from Adobe.com

Uncompress install_flash_player_X_linux.tar.gz. (X = version of Adobe Flash)* 
A directory called install_flash_player_X_linux is created.* Navigate to this directory.

From the command line of Root Terminal, type ./flashplayer-installer to run the installer.*

15. Install mplayer.

16. Install MySQL

In order to install MySQL, we run 
apt-get install mysql-server mysql-client libmysqlclient15-dev
We want MySQL to listen on all interfaces, not just localhost, therefore we edit /etc/mysql/my.cnf and comment out the line bind-address = 127.0.0.1:
vi /etc/mysql/my.cnf

[...]
#bind-address           = 127.0.0.1
[...]

Then we restart MySQL:
/etc/init.d/mysql restart
Now check that networking is enabled. Run 
netstat -tap
In the output you should see a line like this one: 
tcp********0******0**:mysql******************:**********************LISTEN*****22565/mysqld
Run 
mysqladmin -u root password yourrootsqlpassword
mysqladmin -h server1.example.com -u root password yourrootsqlpassword
to set a password for the user root (otherwise anybody can access your MySQL database!). 

18. Add users
Use the Users and Groups from the System menu, and aslo the following;

$ sudo chroot /opt/ltsp/*architecture*/    (architecture i.e. i385)
$ sudo adduser *username* 

17. Add group driven menus
sudo aptitude install edubuntu-menus


My server is working, and I am able to login from a client and surf the internet. The last thing I am trying to do is figure out how to get the common desktops and menus for all users, and I am still trying to get SchoolTool working.  I have missed a step somewhere, and I have not been able to get it to work yet. 

Also, you will need to create boot CD for client  if you are not able to connect via the network BIOS. You can burn an ISO image from [http://rom-o-matic.net/](http://rom-o-matic.net/)

Hope this helps. I suffered through this as a newbie to Linux.

---

### Post by Amal on 2007-06-13
Hi Guys,

Sorry for late reply, I had an exam. Currently am not at the lab, once I reach there I will apply your steps as they seem very relevant to me. 

Thanks snoop + manway ;)

Regards,
Amal

---

### Post by clarknova on 2007-06-22
Amal,

manway has written a thorough step-by-step for creating a server from ubuntu and booting thin clients. If you have installed Edubuntu Server x86_64 Feisty, as I have, then you will only need to perform one of the above commands and you will be booting x86 thin clients:

> sudo ltsp-build-client --arch i386

Or in any case that worked in my case. Repeating the above command for other architectures would also require editing dhcpd.conf as well, I think.

Let us know how it goes. :)

db

---

### Post by locutus42 on 2007-07-13
nice step-by-step manway, thanks.  I'm also working through an LTSP installation( in VMware to get kinks out ) and will post my steps starting with installing from the Edubutu 7.04 server CD via commandline install option.

But, as I have clients booting just fine right now, what I can't get working is the lts.conf customization settings( file: /opt/ltsp/i386/etc/lts.conf ).  I've added simple MAC address sections with XSERVER=visa or XSERVER=sis but can't figure out where to check to see if this is getting loaded on the client XServer. Since the client is really running from the server, any checks for the standard things( /var/log/Xorg.0.log ) shows the servers logs and not client stuff.  Anybody know where I can check to see if customizations to lts.conf regarding XSERVER are happening?

---

### Post by Keen101 on 2007-07-13
[http://coloco.ubuntu-rocks.org/](http://coloco.ubuntu-rocks.org/)

The CoLoCo team is always willing to help. :)

What the session audience didn’t know was that while they were away we booted up a quad-processor thin-client server and had re-routed the network in the room to go through the server (which was now acting as a router). Before long, there was a pleasant orange glow coming from the room as approximately 40 laptop screens were sitting at Edubuntu Thin-Client login screens! We had transformed this windows lab into a fully functioning Linux lab in under 5 minutes!

I believe they used a HP server with two gigs of ram.

e-mail Jim for more info: 

[email]jhutchinson@windsor.k12.co.us[/email]

good luck :)

-keen101
Loveland, co.

---

### Post by locutus42 on 2007-07-14
fantastic story and I loved how you first treated them to software they could use/install on Windows to make them feel right at home before the big splash with LTSP and Edubutu.

One thought I've had is to get LTSP/Edubutu configured on a 4GHz laptop, grab some cables, a switch, powerstrip, and 2 Ebox's bolted 2 LCDs and see if I can't demo it to a few local schools. I've got to get the Ebox boot process sped up some since it takes a good 4-5 minutes to boot now and looks like half of that is tied somewhere in the kdm/Xserver startup.

So nice work and I'm glad to see Canonical and HP stepping up to help. Especially HP since they've walked on the 'other' side of the line for so long.

BTW, I've found that the "System Settins" shows the local X-Server and driver in the "Monitor & Display" option. Turns out the SiS driver is getting loaded and by swapping in "LDM_REMOTECMD=/usr/bin/firefox" into lts.conf, I was able to prove that customizations were working. Now to track down what the heck is taking it so long to boot to the login screen. It happens even after logout so my guess is it's font related.

---

### Post by leetcharmer on 2007-07-21
Is it possible to connect to the edubuntu server with a computer that already has ubuntu installed to be a thin client, so that way it can either be a regular desktop, or a thin client?

---

### Post by locutus42 on 2007-07-21
> **leetcharmer said:**
> Is it possible to connect to the edubuntu server with a computer that already has ubuntu installed to be a thin client, so that way it can either be a regular desktop, or a thin client?

sure, it's pretty easy actually. You can change the boot process to boot off the network/PXE and then it'll boot as a thin client. For these clients, you should customize lts.conf so it boots using it's local swap partition.

I'm thinking another, more transparent way, might be to create a very small boot partition which will start the network boot instead of having to go into the system BIOS every time you want to switch back and forth from local to thin client. I believe there is data on the k12ltsp.org site on doing something like this though it might be about boot floppies. If so, those 1.4MB images could be copied to a 1.4MB HD partition and made to boot via grub.

---

### Post by leetcharmer on 2007-07-21
do you know if it's possible to boot into the thin client host if the two machines are on the same network connected equally into a router, opposed to having two ethernet adapters in the ltsp host?  How would I go about logging in that way?

---

### Post by locutus42 on 2007-07-21
> **leetcharmer said:**
> do you know if it's possible to boot into the thin client host if the two machines are on the same network connected equally into a router, opposed to having two ethernet adapters in the ltsp host?  How would I go about logging in that way?

also yes, just make sure you only have one dhcp server to hand out IP addresses and you're going to  want to setup the dhcp server on the host so that it's handing out the correct gateway and dns stuff too.

it's all free so just download and start playing around. If you don't have the extra hardware yet, get the VMware server( also free ) and start installing there on whatever machine you have but one with alittle extra RAM.

---

### Post by leetcharmer on 2007-07-21
so I can't let the Linksys Router be the DHCP server anymore? :(

---

