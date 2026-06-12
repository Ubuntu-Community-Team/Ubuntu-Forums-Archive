---
title: "server journey almost complete...now to link clients"
date: 2009-06-15
forum: Server Platforms
---

### Post by chokey on 2009-06-15
over the past few days i've been struggling as a newbie with building my own home server with the key goal of file sharing for the family.  I've searched multiple forums and blogs to get to where i've got to.  

installed jaunty and after fighting with the command line (it took me ages to work out how to edit files - ended up trying VIM and then nano - learnt a huge amount through trial and error...) ended up with ebox as my brain was fried. current status attached.

btw - just to really finish me off, I managed to fry my router and settings in the middle of the set-up....ahhhh!!!  what do you do for help when you can't get online!!?!?!?!

the server seems to be running fine with a static IP address.  I can SShell in to it from a networked PC running jaunty and can access fine through ebox.  I've installed all modules for ebox.

Now i need to set up the home PC's to log in to the server and create shared folders/directories for music, photos, documents etc.  I'd like to give my family the ability to view the photo's etc. but i'd rather prevent them from deleting everything.

**question**:  how do I reconfigure my jaunty laptop (running netbook remix) so that it begins to log in/authenticate to the server and ultimately see the shared directories?  what packages do i need on the client?  how do i point it to authenticate with the server? 

**question**:  now the server is up and running, how often do i need to go in and 'manage' it?  are there any nifty reporting tools i can use to throw me messages if there is an exception?

**question**: how do i set up VPN in to the server.  my firewall is a watchguard soho6, so allows VPN tunnels.

**question**: other than just file sharing, what else could i begin to use the server for?  it's a dual xeon, raid 1 configured server that i'm recycling from my old business. webserver for my little website? 

PS.  and a huge thank you to all you contributors who have answered my daft questions without knowing it from all your previous posts.

---

### Post by Macchi on 2009-06-15
> question: how do I reconfigure my jaunty laptop (running netbook remix) so that it begins to log in/authenticate to the server and ultimately see the shared directories? what packages do i need on the client? how do i point it to authenticate with the server? 

question: now the server is up and running, how often do i need to go in and 'manage' it? are there any nifty reporting tools i can use to throw me messages if there is an exception?

question: how do i set up VPN in to the server. my firewall is a watchguard soho6, so allows VPN tunnels.

question: other than just file sharing, what else could i begin to use the server for? it's a dual xeon, raid 1 configured server that i'm recycling from my old business. webserver for my little website? 


One fast solution that I use is to install the server with raid 1, for instance with the alternate-install CD, so that it gets the ubuntu-desktop. Then I add openssh-server, attach a printer and create a shared catalog for the files. This can be done in a couple of minutes with the graphical users interface. Finally I would allow remote login through xdmcp and install nx-server.

(By the way: I know that we are officially not supposed to have a desktop environment installed on a server, but it depends on the type of server and the application area. Personally I believe that administration exclusively through a command line closes the doors for many less experienced users attempting to enter Linux. The performance price and extra storage requirements of having a desktop installed is not a problem for modern machines. The risk for security issues can be avoided if the machine is managed with care. For less experienced users there is a higher risk of doing mistakes on the command line that late can be very difficult to diagnose.)

To answer the questions from CHOKEY:
- You will be able to access the smb share from your laptop running Jaunty. Reflect upon user permissions so that some users shall be able to read but not delete some files, for instance pictures and music.

- You should configure automatic security updates and regularly run the update manager...

- Instead of VPN you could access your server securely through ssh on a non-standard port (for instance 12345). You can configure file access from any Ubuntu desktop and you can access the server with a remote desktop through nx. (I could accessed my desktop environment in Stockholm through ssh from a machine in Brussels, and also use test machines in Italy).

- Besides file sharing, there are many many useful services for a Ubuntu server: Try attaching printers to the server, add some extra storage for backup and archiving on usb hard disks, or add a music streaming server. Webservers for experiments maybe handy. I have had a virtual machines on my server so that I could offer users their own windows computer for every through a remote desktop. If a problem occurred on the Windows (virtual) machine, it could be recovered to a fresh state (snapshot) in a couple of minutes. Try also web cache (squid) and content filtering (willow etc)?  

Keep in touch if you need more details.

---

### Post by Iowan on 2009-06-15
> **chokey said:**
> 
**question**:  how do I reconfigure my jaunty laptop (running netbook remix) so that it begins to log in/authenticate to the server and ultimately see the shared directories?  what packages do i need on the client?  how do i point it to authenticate with the server? 
Your signature suggests you are running a *nix system (Windows-free zone). What are you using to share files (NFS?) [This]("http://ubuntuforums.org/showthread.php?t=249889") How-To comes highly recommended.

---

### Post by ghen on 2009-06-16
> **Macchi said:**
> (By the way: I know that we are officially not supposed to have a desktop environment installed on a server, but it depends on the type of server and the application area. Personally I believe that administration exclusively through a command line closes the doors for many less experienced users attempting to enter Linux. The performance price and extra storage requirements of having a desktop installed is not a problem for modern machines. The risk for security issues can be avoided if the machine is managed with care. For less experienced users there is a higher risk of doing mistakes on the command line that late can be very difficult to diagnose.)

A good compromise I found is to install Ubuntu Server and then

apt-get install xorg gdm gnome-core

for just a minimal desktop environment for minor administrative tasks like system monitor.

---

### Post by Macchi on 2009-06-16
> **ghen said:**
> A good compromise I found is to install Ubuntu Server and then

apt-get install xorg gdm gnome-core

for just a minimal desktop environment for minor administrative tasks like system monitor.

Definitely better to simply install xorg gdm and gnome-core!


The type of server that I have mentioned earlier is an integrated "all-in-one" solution for small groups, containing servers for encrypted remote access(ssh), raid central storage of files (also shared on smb), printer server, and terminal server for remote (desktop). Sometimes I also have a virtualization solution to be able to offer remote Windows desktops. The advantage of having everything in one box is that it facilitates installation, maintenance and administration. It is necessary to have good off-site backup of all data and also have a reserve machine for replacement in case of serious hardware failure,  since all the eggs are in one basket.

---

### Post by chokey on 2009-06-16
> **Iowan said:**
> Your signature suggests you are running a *nix system (Windows-free zone). What are you using to share files (NFS?) [This]("http://ubuntuforums.org/showthread.php?t=249889") How-To comes highly recommended.

thank you - fantastic tips.

originally, i'd set up samba shares and this shows through ebox.  

and you are correct...the reality is that there isn't going to be any windows access, so NFS looks like the way to go.

if I uninstall samba from the server will that break anything?  and then i can jsut have a clean NFS?

---

### Post by chokey on 2009-06-16
latest update:
installed xorg and now have xnest on client with a graphical user face.  having messed about with the command line for a while i'm having to relearn how to manage the server via gui.  it feels nicer, but the command line was very powerful and it was helping me learn about how linux works.

also, managed to get the HP printer working on the network..  HURRAH.  this was a major triumph as this has really frustrated me up until today.

now my next problem (you fix one and move on to the next!).

shared files - I seem to be missing my server.mydomain.com/files.

so when i try to mount it from the client, it obviously fails.  does this have something to do with the aforementioned samba set-up?

---

### Post by ghen on 2009-06-17
is it only the share that is broken or has the entire folder disappeared from the server? 

You can definitely just uninstall samba and install NFS. It won't break anything,but run a apt-get autoremove after uninstalling samba to get rid of the unused [COLOR="Silver"]dependencies[/COLOR] edit: packages.

I don't know if there's anything lingering after removing samba since I'm a linux newbie as well, so if you have the choice a full reinstall for the final computer is recommended once you know everything works correctly but before putting all your files on it.

---

### Post by Macchi on 2009-06-17
This maybe obvious for many of you, but when uninstalling software it is a good idea to purge the configuration files, so that they won't haunt your system in a later reincarnation, I meant reinstallation. It is also good to remove and purge orphan packages with autoremove. Apt-get will install and remove all dependencies automatically.

```
sudo apt-get remove --purge samba samba-common
sudo apt-get autoremove --purge

```

Keeping samba on the system may be useful for talking to a guest Mac or Windows.

---

### Post by chokey on 2009-06-19
> **ghen said:**
> is it only the share that is broken or has the entire folder disappeared from the server? 


it seems to be just the :files that doesn't exist on the server.

---

