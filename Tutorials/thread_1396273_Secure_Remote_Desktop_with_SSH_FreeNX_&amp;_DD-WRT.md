---
title: "Secure Remote Desktop with SSH FreeNX &amp; DD-WRT"
date: 2010-02-01
forum: Tutorials
---

### Post by 2hot6ft2 on 2010-02-01
**[SIZE="3"]For a Secure Remote Desktop on Ubuntu 9.10 here is how I did it using OpenSSH, FreeNX and a router with DD-WRT v24.[/SIZE]**

Pic of it in use at bottom of post, transferring a file and remote desktop at the same time.

For the purposes of this guide I will use a Desktop as the Server (Host) which is at home.
The Client will be a Laptop that I can use to control the Desktop remotely.

First you should already be familiar with the Terminal which is where you enter commands (anything in a "Code:" box). In Ubuntu it is in
Applications > Accessories > Terminal
In Kubuntu it is usually on the lower left taskbar and is called Konsole
I am using Ubuntu so you may have to make some adjustments to this guide if you are not using Ubuntu.

**[SIZE="3"]Installing OpenSSH[/SIZE]** (for the rest of this guide I will refer to it as only SSH)

**Installing the Server on the Desktop (Host)**
```
sudo apt-get update
```
then
```
sudo apt-get install openssh-server
```
then we want to backup the original configuration file and protect it from being overwritten with
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original
```
and
```
sudo chmod a-w /etc/ssh/sshd_config.original
```
Choosing a port other than the default port number 22. You can use just about any port number but it's best to stay away from commonly used ports something between 1024 and 65536, but between 49151 and 65536 is usually better. I recommend AGAINST using 2222 or 8888 like the guides use as "examples". You can find more info on ports at these links among others:
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
[http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html](http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html).

Once you have chosen a port to use. To change the default port from 22 to another port number open the config file using
```
gksu gedit /etc/ssh/sshd_config
```
Find the line that says:
> #Port 22
change the 22 to the port number you decided to use and uncomment it by removing the "#" so it will look like 
> Port 22
but with your port number.
There are other things to be changed in this file later, but for right now the idea is to get it up and running, then we can tweak it and secure it better so click on Save and close it.
Restart the server using
```
sudo /etc/init.d/ssh restart
```
You can replace "restart" with "stop" or "start" if you want to stop or start the SSH server. Stopping it when it's not going to be used is a good idea, you can always start it again.


**Installing the Client on the Laptop**
```
sudo apt-get update
```
then
```
sudo apt-get install openssh-client
```
then to change the port on the Client to the same as the Host run
```
gksu gedit /etc/ssh/ssh_config
```
Find the line that says:
> #Port 22
change the 22 to the port number you decided to use and remove the "#" so it will look like 
> Port 22
but with your port number.
---------------
Both host and client config files will need to be changed so edit both to the same port #.

sshd_config is the configuration file for the SSH Server (Host) (/etc/ssh/sshd_config).
ssh_config is the configuration file for the SSH Client (/etc/ssh/ssh_config).
Make sure you don't get them mixed up.
---------------

**[SIZE="3"]Static IP Address for the server & port forwarding[/SIZE]**

While I am using a router with dd-wrt firmware and have included the instructions for it. It is not required as long as you can set port forwarding and static IP Addresses in your routers configuration to accomplish the same thing.

This would be a good time to give your server (host) and Client static IP addresses using your router. You should already know how to access your routers configuration since you set up your network and put dd-wrt on it.
You can find out the servers MAC Address of the adapter (it will be like xx:xx:xx:xx:xx:xx where the x's are leters and numbers), and its current IP address by opening a Terminal and putting in:
```
ifconfig
```
Do the same with the Client.

In DD-WRT v24 you would go to Services > Services > Static Leases and click on Add (twice if you are going to give them both static IP Addresses), this will open 3 boxes where you can put your adapters
> "MAC Address - A description or name like Server or Client (no spaces allowed) - IP Address you want the adapter to have"
More ifo and a guide here: [http://www.dd-wrt.com/wiki/index.php/Static_DHCP]("http://www.dd-wrt.com/wiki/index.php/Static_DHCP")
Be sure to set your static IPs outside of your automatic DHCP address range (see the above guide).
Click on "Apply Changes" at the bottom of the page to make it take effect immediately. The router will reboot itself and the changes will be in effect. So wait for it to reboot.

While you're in the routers configuration you can also set a "port forward" if you plan on accessing your server (host) from outside your LAN (Local Area Network). In other words from the Internet by going to NAT/QoS > Port Forwarding, enable it and put in your info consisting of:
> A name (whatever you want)
Port From (the port you will use in the Client for when you want to connect to the server from outside your LAN)
Protocol (Both, TCP is needed, I'm not sure if UDP is)
IP Address (the static IP Address you just assigned to your server (host) above)
Port To (the port # you set SSH to on your server (host))
Tick the box to Enable
Click on "Apply Changes" at the bottom of the page to make it take effect immediately. The router will reboot itself and the changes will be in effect. Again wait for it to reboot.
Port forwarding guide here: [http://www.dd-wrt.com/wiki/index.php/Port_Forwarding]("http://www.dd-wrt.com/wiki/index.php/Port_Forwarding")
You can have and save profiles so one for the LAN and one for accessing it from outside the LAN is simple so you don't have to use the same port # as SSH.


**[SIZE="3"]Firewall, Opening a port[/SIZE]**

A rule should be added to the servers firewall to allow connections to the servers port. I'm using firestarter, if you're using something else the see the documentation for the one you're using. If using Firestarter open it.
System > Administration > Firestarter

The Staus tab should show it as active
Click on the Policy tab, then left click in the bottom box, then on the + sign.
Here you can enter a Name or use the drop down
Change the port # to the one you setup SSH to use.
And choose who can connect to it. You can choose from Everyone, LAN only, a specific IP Address, or IP Addresses.
You can set it to the IP Address of your client for now (if you want) while configuring things and change it later so you'll be able to connect to it from anywhere.
Click Add, then the Check mark to apply the settings then you can close it.

**[SIZE="2"]Connecting for the first time[/SIZE]**

If you want to easily be able to tell if you made it to the server make a file (an empty text file) in the home folder on the server so you'll know you're looking at that folder and not the one on the client. Name it something unique MADE-IT or WhoooHooo. Whatever you pick a name you can delete the file anytime you want later.
Use this to connect to the server (changing the port from 22 to what you made it and the IP Address to the one you gave the server):
```
ssh -p 22 192.168.?.???
```
If you put in a password earlier then it will ask for it so enter it and hit Enter.
Once it connects use
```
ls
```
That will list the files in the servers home folder and you should see the file you made (MADE-IT, WhoooHooo or whatever).

If everything looks good then congratulations you have an active SSH Server and Client working. If not go back thru and see what's wrong. This is far from secure at this point. So next we want to secure it.


**[SIZE="3"]Passwords and Keys[/SIZE]**

You should really read this page
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys]("http://help.ubuntu.com/community/SSH/OpenSSH/Keys")
since I'm not going to reproduce it all here since it's very good.
Don't just start putting in the commands... Read it all first since at first it says to use
```
ssh-keygen -t rsa
```
but farther down the page it changes that (increasing it's strength) to this
```
ssh-keygen -t rsa -b 4096
```

When you get to the part in the above titled "Password Authentication" it recommends disabling password authentication altogether. Which we will, but if you do it right now you wont be able to test FreeNX yet, as FreeNX requires it to be enabled to work by default. Disabling it will come later.
There is a link there for "strong passwords" this will come in handy it leads here:
[http://help.ubuntu.com/community/StrongPasswords]("http://help.ubuntu.com/community/StrongPasswords")

Once you finish the instructions on that page you should be able to connect like before with:
```
ssh -p 22 192.168.?.???
```
Again changing the port from 22 to what you made it and the IP Address to the one you gave the server
But without being prompted for a password.

SSH should now be setup, have a static IP Address, you should be able to connect to it by terminal without a password using the keys, and from another computer that doesn't have they keys with a password (at this point).

**Tranferring files using a GUI (Graphical User Interface) like nautilus or krusader**

Nautilus (Ubuntu)
Places > Connect to server
Service Type: SSH
Server: IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/
You can check the "Add Bookmark" box and it will show up under Places as Whatever you name it so you can just click on it like a folder.
Click on Connect

krusader (Kubuntu)
Tools > New Net Connection
Protocol: fish://
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Click on Connect

I'm not sure how or if it can be done with Konqueror

Some others that can be used

gFTP
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Select SSH2
Click on the icon to the left of Host that has 2 computers to connect (and disconnect)

Dolphin (also has a split view to work on 2 folders at one time)
Click on Networks on the left
Click on Add Network Folder
Select Secure shell (ssh)
Click on Next
Put in your Name
Put in your Username (username on the host computer)
Server: The IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/
Encoding: Change to (Unicode UTF-8) or whatever works for you
Checking "Create an icon for this remote folder" is up to you
Click on Connect

Gigolo
Click on Connect
Service type: SSH
Server: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Click on Connect
The server will show up in the window (sftp for (username) on (IP Address of the server))


**[SIZE="3"]Installing FreeNX[/SIZE]** for the graphical remote desktop

The guide here [http://help.ubuntu.com/community/FreeNX]("http://help.ubuntu.com/community/FreeNX") is real good so just follow the parts in it for:

Installing the FreeNX server on Ubuntu Karmic (9.10)
Installing the NX Client
How to start/stop FreeNX
Configuring SSH port (some you have already done and you'll be using the port you gave the server earlier)
and
Using custom SSH keys
************
Note: When setting up the Custom Keys in FreeNX I just went with Create new custom keys and Authenticate via SSH. I am not familiar with the other options and I didn't write the wiki for FreeNX.
************
Thanks to Zalbor there is another option and I'll quote it here along with how it should change things.
> **Zalbor said:**
> 
You said to pick "SSH" authentication when running dpkg-reconfigure, and later on you change the node.conf file to disallow it and use another (PASSDB) first. You could simply choose "PASSDB" when reconfiguring.
My understanding is that if you follow those instructions you would NOT need to change these 2 lines in the /etc/nxserver/node.conf file as described in this how to and those being:
> change
#ENABLE_PASSDB_AUTHENTICATION="0"
and
#ENABLE_SSH_AUTHENTICATION="1"
to
ENABLE_PASSDB_AUTHENTICATION="1"
ENABLE_SSH_AUTHENTICATION="0"
So disregard those changes if you choose "PASSDB" when reconfiguring.
Since I haven't tried it myself I'm leaving them in the how to for now until I'm sure they can be omitted. I probably wont upgrade this server for a while to try it out myself, so if you try it let me know how it goes.

While I don't agree with the "SU" solution in it since I believe that would defeat the whole purpose of the keys.
Zalbor provided some good detailed information about how his/her install in the reply to this how to in post #8 here: [POST #8]("http://ubuntuforums.org/showpost.php?p=9025942&postcount=8")
*************
Once you finish that there are a few more things to do

Remember, we didn't disable password authentication in SSH.

So we're going to edit 2 files on the server (host)
/etc/ssh/sshd_config
and
/etc/nxserver/node.conf

So open a terminal.
Applications > Accessories > Terminal
and use:
```
gksu gedit /etc/ssh/sshd_config
```
Hit Enter
Type in your password and hit Enter

> (uncomment & change the following by removing the # and any space from the beginning of the lines.)
change
#PasswordAuthentication yes
to
PasswordAuthentication no
add
AllowUsers nx <yourusername> (yourusername is the name you use when logging in on the server normally)
UsePAM yes (already there at bottom place AllowUsers above this)

Save the file and close it then use:
```
gksu gedit /etc/nxserver/node.conf
```

> (uncomment & change the following by removing the # and any space from the beginning of the lines if you haven't already)
#SSHD_PORT=22 change to the SSH port number and uncomment the line by removing the # sign
change
#ENABLE_PASSDB_AUTHENTICATION="0"
and
#ENABLE_SSH_AUTHENTICATION="1"
to
ENABLE_PASSDB_AUTHENTICATION="1"
ENABLE_SSH_AUTHENTICATION="0"

Save the file and close it then use this to create a account on the NX server:
```
sudo nxserver --adduser (yourusername)
```
(yourusername is the name you use when logging in on the server normally)
NX server will reply with:

> NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Public key added to: /home/yourusername/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye

and add a password

```
sudo nxserver --passwd (yourusername)
```
> NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
New password: **(enter your NEW password here and hit Enter (I wont be displayed)see below)**
Password changed.
NX> 999 Bye

(you can paste in a good long premade password which is what you will put into the freenx client so make it a good one you'll only need to put it into the FreeNX client for each profile once if you tick the save password in the configuration for (Home and Away)
I'm not sure how long it can be but it can handle at least 30 characters see:
[http://help.ubuntu.com/community/StrongPasswords]("http://help.ubuntu.com/community/StrongPasswords")

Don't forget to restart the sshd daemon after making that change using:
```
sudo /etc/init.d/ssh restart
```

I am not sure if it is really necessary but I guess it can do no harm to restart to freenx server.
```
sudo /etc/init.d/freenx-server restart
```

In Ubuntu the FreeNX client will be under Applications > Internet > NX Client For Linux > (take your pick, there is a wizard if you need it, I just use the top one).

Start the FreeNX Client and you should be able to connect the client to the server (host) on your LOCAL network using yourusername and the password you just created. Once you put in yourusername and the password then click on "configure", put the IP Address of the server (Host) where it says Host, put in the port # you gave SSH, tick the save password box and import the key file you created when installing FreeNX, then save at the bottom. Then OK then you should already have your username and password in there so Hit Login.

You should be able to connect over your LAN now. If not go back thru and check everything until you can.

You can have and save more than one profile so one for the LAN and one for accessing it from outside the LAN for EXAMPLES:
Home: the IP Address of the server (host) is used along with the SSH port #.
Away: the DynDNS .com address we will get later is used along with the port # we forwarded in the router "Port From" (above).

**What's done and what's left to do:**

SSH installed, configured and secured. (Done)
FreeNX installed, configured and secured. (Done)
Router configured to forward port to SSH server. (Done)
Static IP Address for server configured in router. (Done)

Now to set it up so we can access it from outside the LAN. That means from the Internet when we're away from home using the Laptop that we setup as the client.

If you have a STATIC IP Address from your ISP then all you will need to do is setup your Away profile under "Configure > General > Host" to point to that IP Address and put in the port you setup in DD-WRT's Port Forwaring "Port From" along with your username and password.

If your ISP gives you a Dynamic IP Address that changes then look in your routers DD-WRT setting under "Setup > DDNS". Enable it and you'll find a long list of services like DynDNS.org that you can use to setup a .com, .net, .org, etc. for free.

What these services do is you'll get url like "billybobsburgers.dydns.org" (That's just an example you get to pick the name). You'll put that info into your DD-WRT router and whenever your ISP changes your IP Address it will update so that "billybobsburgers.dydns.org" would still point to your router.

So pick one and go sign up for your url.

Then you would just put your "billybobsburgers.dydns.org" url into the Away profile under "Configure > General > Host" and put in the port you setup in DD-WRT's Port Forwaring "Port From" along with your username and password that you created earlier. Tick the save password box and import the key file you created when installing FreeNX, then save at the bottom. Then OK then you should already have your username and password in there so Hit Login.

Now you should be able to logon using it from anywhere. You can try it without going anywhere since FreeNX is pointing to the url as host if everything is setup right it will work. If somethings not right it wont.

**[SIZE="3"]NOTES:[/SIZE]**

-----
**How to start/stop/restart FreeNX**

The FreeNX server is not a service but uses ssh. The following command will stop the FreeNX program from accepting connections. 
```
sudo /etc/init.d/freenx-server stop
```
(Replace stop with start for starting it again or restart to restart it)
-----

**How to start/stop/restart the SSH Server**
```
sudo /etc/init.d/ssh stop
```
(Replace stop with start for starting it again or restart to restart it)
-----

If you don't plan on using the server anytime soon stopping FreeNX then SSH can only help your systems security
If you want to start them again start SSH first then start FreeNX

******

**You can make other changes to the files if you want but here's the ones we've done.**

**On the Server**

**MODS TO /etc/ssh/sshd_config**
> #PORT 22 (change the number and remove the # before it)
change
#PasswordAuthentication yes
to
PasswordAuthentication no
add
AllowUsers nx
AllowUsers (yourusername)
UsePAM yes (already there at bottom place AllowUsers above this)
AllowUsers can be shortened to
> AllowUsers nx (yourusername)
Both on the same line with a space between them.

**MODS TO /etc/nxserver/node.conf**
> #SSHD_PORT=22 change to the SSH port number and uncomment the line by removing the # sign
change
#ENABLE_PASSDB_AUTHENTICATION="0"
and
#ENABLE_SSH_AUTHENTICATION="1"
to
ENABLE_PASSDB_AUTHENTICATION="1"
ENABLE_SSH_AUTHENTICATION="0"

**On the Client**

**MODS TO /etc/ssh/sshd_config**
> Changed the line
#   Port 22
to
Port (the number of the SSH port you set on the server)
--------

**Other things you can do**

If you want a banner to be displayed whenever someone logs in thru a terminal a sample banner can be found here
[http://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("http://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

On the server edit the /etc/issue.net
```
gksu gedit /etc/issue.net
```
Type or paste your banner in it (it should be empty at first)
Save and close

On the server edit the /etc/ssh/sshd_config file
```
gksu gedit /etc/ssh/sshd_config
```
Change
> #Banner /etc/issue.net
to
Banner /etc/issue.net
Save and close

Don't forget to restart the SSH Server for it to take effect with
```
sudo /etc/init.d/ssh restart
```
*******

**Here's a good page to read**
[Top 20 OpenSSH Server Best Security Practices]("http://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html")

*******

**[SIZE="3"]Uninstalling if you decide you don't want it anymore[/SIZE]**

**On the Client run**
```
sudo apt-get purge nxclient openssh-client
```

**On the Server (Host) run**
```
sudo /etc/init.d/freenx-server stop
sudo /etc/init.d/ssh stop
sudo apt-get purge freenx openssh-server

```
Remove the firewall rule from the server.
Disable the Port Forward on the router.

Removing everything is sure easier than setting it up.

*******

**[SIZE="3"]References:[/SIZE]**

Installing OpenSSH
[http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

I wanted stronger keys so I followed this for the keys
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Strong Passwords
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

Installing FreeNX
[http://help.ubuntu.com/community/FreeNX](http://help.ubuntu.com/community/FreeNX)

Thread on FreeNX Security in the Ubuntu Forum
[Secured freeNX using custom keys. But ssh now open]("http://ubuntuforums.org/showthread.php?t=1062942")

DD-WRT Static IP Address Leases
[http://www.dd-wrt.com/wiki/index.php/Static_DHCP](http://www.dd-wrt.com/wiki/index.php/Static_DHCP)

DD-WRT Port Forwarding
[http://www.dd-wrt.com/wiki/index.php/Port_Forwarding](http://www.dd-wrt.com/wiki/index.php/Port_Forwarding)

Display Banner
[http://help.ubuntu.com/community/SSH/OpenSSH/Configuring](http://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Port Lists
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
[http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html](http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html)

**[SIZE="3"]More information[/SIZE]**

**Shadowing a running session and taking control of it**

To shadow the servers desktop with FreeNX.
All you have to do is in the NX Client go to Configure and set (everything is the same as earlier except).
Desktop: Set to Shadow

You'll have to play with the screen size a little but you can resize it once it's open.

When you click on Login you will get a Available sessions window.
Try the top one first and click on Attach. See pic. at bottom.
if that doesn't work try the next one.
That's it.

*************

Playing sound thru a FreeNX session
[http://www.nomachine.com/ar/view.php?ar_id=AR03D00355](http://www.nomachine.com/ar/view.php?ar_id=AR03D00355)

More Documentation including RDP and VNC thru FreeNX
[http://www.nomachine.com/configuration.php](http://www.nomachine.com/configuration.php)

---

### Post by AlexanderDGreat on 2010-03-03
Hey sir, your tutorial is the easiest to FOLLOW if anyone needed a REMOTE connection to their Ubuntu! Worked for me!

I've a question though what are the differences between freenx, vinagre, xtightvncviewer, etc... Why did you choose FreeNX?

PS I've 1 comment can you put Steps, so if people needed to refer to them, they'll say, I'm stuck in step 2, step 4, etc...

Once again great tutorial! 5 stars! :)

---

### Post by AlexanderDGreat on 2010-03-03
One more thing, is it possible that you also include in your tutorial if I want to create CUSTOM KEYS in FreeNX? There were a lot of options when I ran: 

```
sudo dpkg-reconfigure freenx-server
```

I just chose Create new custom keys and Authenticate via SSH, I don't know the consequences of other choices. Thanks & more power! :)

---

### Post by 2hot6ft2 on 2010-03-03
> **AlexanderDGreat said:**
> Hey sir, your tutorial is the easiest to FOLLOW if anyone needed a REMOTE connection to their Ubuntu! Worked for me!

I've a question though what are the differences between freenx, vinagre, xtightvncviewer, etc... Why did you choose FreeNX?

PS I've 1 comment can you put Steps, so if people needed to refer to them, they'll say, I'm stuck in step 2, step 4, etc...

Once again great tutorial! 5 stars! :)
Glad you liked it.
If you want a comparison of the various remote desktop options take a look at this link:
[Comparison of remote desktop software]("http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software")

The reason I went with FreeNX is that VNC is less secure and FreeNX is faster due to its compression from what I have read about it. I think it was on Wikipedia where I read it but I don't have a link handy but here's a good starting point:
[URL="http://en.wikipedia.org/wiki/NX_technology"]NX technology
[/URL]

I'll look at it and see about numbering it but that would sure make it seem like a look of steps if you mean each command.
If you mean by section the way I look at it there are really only 6 main sections. If someone is having a problem I would think they would say what the problem is they are having rather than saying I'm having a problem with 4.c. and expecting myself or anyone else to look for it to try and figure out what they are referring to.
> **AlexanderDGreat said:**
> One more thing, is it possible that you also include in your tutorial if I want to create CUSTOM KEYS in FreeNX? There were a lot of options when I ran: 

```
sudo dpkg-reconfigure freenx-server
```

I just chose Create new custom keys and Authenticate via SSH, I don't know the consequences of other choices. Thanks & more power! :)
I added
> Note: When setting up the Custom Keys in FreeNX just go with Create new custom keys and Authenticate via SSH. I am not familiar with the other options and I didn't write the wiki for FreeNX.
To the guide since like you I went with the "Create new custom keys and Authenticate via SSH, I don't know the consequences of other choices."

Someone that is more familiar with the other options should add the information to the Wiki for FreeNX. I can't add what I don't know.

Thanks for the input.

---

### Post by AlexanderDGreat on 2010-03-05
I'm enjoying my Remote Desktop in the office and home, vice versa, it would've taken me months to figure this one out and understand all those VNCs and compare them. Thank you so much for your time & contribution to the community. More power to your tutorials! :)

---

### Post by 2hot6ft2 on 2010-03-05
> **AlexanderDGreat said:**
> I'm enjoying my Remote Desktop in the office and home, vice versa, it would've taken me months to figure this one out and understand all those VNCs and compare them. Thank you so much for your time & contribution to the community. More power to your tutorials! :)
That makes doing it all worth while as long as someone has found it helpful and useful.:biggrin:

---

### Post by Zalbor on 2010-03-25
Thanks for the guide, I've been wanting to set up a remote desktop configuration and it seems like this will do the job, I'll let you know when I'm done.

However, I'd like to ask a few of questions.
First, I understand you're getting by FreeNX's need for SSH server to use password authentication by disabling SSH authentication and enabing PASSDB authentication, is that right? But in the FreeNX manpage, it says that PASSDB is deprecated. [This page](http://www.mail-archive.com/freenx-team@lists.launchpad.net/msg00424.html) explains why, and suggests using SU authentication instead of SSH. Do you think PASSDB is more secure?
Second, I plan to connect to my Ubuntu computer from a Windows one, using the NX client. Will I have to somehow generate a public SSH key on the Windows computer and transfer it to the Ubuntu one, for that to work (since SSH needs it) or does NX take care of that?

---

### Post by Zalbor on 2010-03-25
It worked! Thanks for the guide!
(I actually only did the ssh/nx parts, my router isn't compatible with dd-wrt).

I have a couple of things you could fix:
You said to pick "SSH" authentication when running dpkg-reconfigure, and later on you change the node.conf file to disallow it and use another (PASSDB) first. You could simply choose "PASSDB" when reconfiguring.

Also, I made it work with SU like that link I posted explains. Except that there's a (big) mistake in it.

It says to open the /etc/nxserver/nxacl file and add a function like
```
if [ "$2" == "allowed_user" ]
then
    echo "user allowed_user is allowed"
    exit 0
fi
```

Except that this won't work for 3 reasons!

One, if you place this in a function, "$2" will be empty. You have to add a line like
> USER=$2
earlier in the file and then use "$USER" in that function.

Second, even then it will do nothing because without an explicit "exit 1" command, it will be thought of as a success.

Third, if the script reports a success then it can't echo a message like the one above, it needs to echo $CMDLINE or NX won't work.

In the end, I added these to the file to make it work (bold are pre-existing lines):
```
...
**CMDLINE="$1"**
USER="$2"
[...]
allow_specific_user()
{
	if [ "$USER" == "allowed_user" ]
        then
                allow_all
	else
		echo "user $USER is not allowed"
		exit 1
        fi
}
**#allow_all**
allow_specific_user
```
(I commented the "allow_all" line at the end).

---

### Post by 2hot6ft2 on 2010-03-25
Glad you liked it and it's working. I'll look into the link you provided and what all you found and did. Thanks for all the info on what you changed and how detailed it is. Nice work.

Edit: Guess I'll have to fire up my server and try things out with your changes.

---

### Post by Zalbor on 2010-03-25
No problem.

Currently I have a strange problem; I can connect from a VM on this computer, but not from another computer in the network, although the VM should be viewed as another network computer. I'm not sure if it's related to choosing SU instead of SSH or PASSDB, but I'm looking into it...

---

### Post by 2hot6ft2 on 2010-03-25
Let's see what I can and can't answer here. Keep in mind I just made this as a how I did it and there are people that know a lot more about it than myself.
> **Zalbor said:**
> 
However, I'd like to ask a few of questions.
First, I understand you're getting by FreeNX's need for SSH server to use password authentication by disabling SSH authentication and enabing PASSDB authentication, is that right? But in the FreeNX manpage, it says that PASSDB is deprecated. [This page](http://www.mail-archive.com/freenx-team@lists.launchpad.net/msg00424.html) explains why, and suggests using SU authentication instead of SSH. Do you think PASSDB is more secure?
Well SU (Super User) is basically "root", so I would have to say yes. And although PASSDB may be depreciated I'm still reluctant to allow SU  authentication instead of SSH since SSH  authentication is by key and not a SU password. Perhaps I'm misunderstanding something here.
> **Zalbor said:**
> Second, I plan to connect to my Ubuntu computer from a Windows one, using the NX client. Will I have to somehow generate a public SSH key on the Windows computer and transfer it to the Ubuntu one, for that to work (since SSH needs it) or does NX take care of that?
Right you will need to transfer the key to the other machine and NX does not do it for you as you already figured out below.
> **Zalbor said:**
> 
I have a couple of things you could fix:
You said to pick "SSH" authentication when running dpkg-reconfigure, and later on you change the node.conf file to disallow it and use another (PASSDB) first. You could simply choose "PASSDB" when reconfiguring.
As I said I have only done it by choosing SSH and was not aware how that would work so I'll add that to the how to. Thank you.
> **Zalbor said:**
> 
Also, I made it work with SU like that link I posted explains. Except that there's a (big) mistake in it.

It says to open the /etc/nxserver/nxacl file and add a function like
```
if [ "$2" == "allowed_user" ]
then
    echo "user allowed_user is allowed"
    exit 0
fi
```

Except that this won't work for 3 reasons!

One, if you place this in a function, "$2" will be empty. You have to add a line like

earlier in the file and then use "$USER" in that function.

Second, even then it will do nothing because without an explicit "exit 1" command, it will be thought of as a success.

Third, if the script reports a success then it can't echo a message like the one above, it needs to echo $CMDLINE or NX won't work.

In the end, I added these to the file to make it work (bold are pre-existing lines):
```
...
**CMDLINE="$1"**
USER="$2"
[...]
allow_specific_user()
{
	if [ "$USER" == "allowed_user" ]
        then
                allow_all
	else
		echo "user $USER is not allowed"
		exit 1
        fi
}
**#allow_all**
allow_specific_user
```
(I commented the "allow_all" line at the end).
While I don't see the advantage of allowing SU as I said earlier perhaps someone will enlighten me.
And the link to that conversation with the freenx team by someone was very interesting.
In any case thank you for for providing such a detailed explanation of what your fix was for correcting the errors with their method along with how you fixed it.

I will link to your post in the how to so people have the information you provided before they complete the set up.

---

### Post by Zalbor on 2010-03-25
I think you misunderstood: The post in that link wasn't mine! I just found it through google.

As for SU, I admit I don't know exactly how the command works. I assumed it just meant that the "nx" user uses the "su" command to gain the rights of another (as "su issun") would give you the rights of "issun".

---

### Post by 2hot6ft2 on 2010-03-25
> **Zalbor said:**
> No problem.

Currently I have a strange problem; I can connect from a VM on this computer, but not from another computer in the network, although the VM should be viewed as another network computer. I'm not sure if it's related to choosing SU instead of SSH or PASSDB, but I'm looking into it...
I remember you asking about that a few days ago in the forum (at least I think it was you). I have absolutely no idea when it comes to a VM. I've never set one up or used one. I'll have to leave that in your hands. But I doubt that it has to do with choosing PASSDB instead of SSH.

---

### Post by 2hot6ft2 on 2010-03-25
> **Zalbor said:**
> I think you misunderstood: The post in that link wasn't mine! I just found it through google.

As for SU, I admit I don't know exactly how the command works. I assumed it just meant that the "nx" user uses the "su" command to gain the rights of another (as "su issun") would give you the rights of "issun".
You're right I thought it was you talking to the freenx team and corrected what I said. I like the info it gives although I'll admit I don't understand the thinking behind using SU.

P.S. here's the first part of that conversation and it was in reference to the FreeNX guide in the help pages (it was a link at the bottom of the page). Notice the date "Fri, 13 Nov 2009"
[http://www.mail-archive.com/freenx-team@lists.launchpad.net/msg00423.html](http://www.mail-archive.com/freenx-team@lists.launchpad.net/msg00423.html)
So I guess that should have been covered in the FreeNX guide but was left out for probably the same reason (the SU solution) here:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by Blackwolf_Oz on 2010-04-07
Thanks 2hot6ft2:)

Can you add this how to to Oz guides too ? :guitar:

---

### Post by 2hot6ft2 on 2010-04-07
> **legend1264 said:**
> Thanks 2hot6ft2:)

Can you add this how to to Oz guides too ? :guitar:
Sure thing. It took me a moment for Oz to kick in, I was stuck thinking of The Wizard of Oz...

---

### Post by gatorbrit on 2010-04-20
Hi - great how to.   But (!) when I connect remotely using qtnx to view my server desktop I don't see the programs that I have running - it is like i have login on it.   I'd like to be able to access my existing (running) desktop.

Thks

---

### Post by 2hot6ft2 on 2010-04-20
> **gatorbrit said:**
> Hi - great how to.   But (!) when I connect remotely using qtnx to view my server desktop I don't see the programs that I have running - it is like i have login on it.   I'd like to be able to access my existing (running) desktop.

Thks
Thanks.
qtnx? Can't place off hand what that is.
I figured out how to shadow the servers desktop with FreeNX. And I'm adding it to the guide now.

On the server you need to edit the node.conf file so run
```
gksu gedit /etc/nxserver/node.conf
```
Under this section
###########################################
# Restriction directives
###########################################

Change these 3 by uncommenting them
From this
```

#ENABLE_DESKTOP_SHARING=1
#ENABLE_SESSION_SHADOWING_AUTHORIZATION=0
#ENABLE_INTERACTIVE_SESSION_SHADOWING=1

```
To this
```

ENABLE_DESKTOP_SHARING=1
ENABLE_SESSION_SHADOWING_AUTHORIZATION=0
ENABLE_INTERACTIVE_SESSION_SHADOWING=1
```

And whatever else you want.

Then in the NX Client go to Configure and set (everything is the same as in the guide except).
Desktop: Set to Shadow

You'll have to play with the screen size a little but you can resize it once it's open.

When you click on Login you will get a Available sessions window.
Try the top one first and click on Attach.
if that doesn't work try the next one.
That's it.

:guitar:

---

### Post by gatorbrit on 2010-04-29
Thanks for the update on shadowing.    Turns out that all you actually need to do is select the shadow option in the NX client on the laptop.   Changing the parameters on the server doesn't seem to make any difference.

I am able to access my session remotely, but I have a couple of remaining issues.

First, because I use a dual monitor display on the server, the laptop tries to cram this all into one window making it all very small.   Second, the connection is very slow when I shadow.

Thanks for the howto...!!
:)

---

### Post by 2hot6ft2 on 2010-04-29
> **gatorbrit said:**
> Thanks for the update on shadowing.    Turns out that all you actually need to do is select the shadow option in the NX client on the laptop.   Changing the parameters on the server doesn't seem to make any difference.
You're right. I'm in shock. #-o](*,)
I made the adjustment to the guides (all 3 of them).
Thank you so much for pointing that out.=D>
> **gatorbrit said:**
> 
First, because I use a dual monitor display on the server, the laptop tries to cram this all into one window making it all very small.   Second, the connection is very slow when I shadow.

Thanks for the howto...!!
:)
I'm not running a dual monitor setup so I can't play with the settings to find out what's possible there. If you find out any settings to make that situation work in another way let me know and I'll add it to the guides.

There is a slight lag when shadowing as compared to running a new x session. If you want it to be a bit more responsive try it without using shadowing. I guess that's the trade off. I still think it's better than the other options that are available.

You're welcome, and I'm always looking for any new tricks or settings that will make it work in more ways so feel free to let me know if you figure any useful settings for a dual monitor setup.
:guitar:

---

### Post by gatorbrit on 2010-04-29
Glad to help and provide some input.   One thing i found for the dual monitor display is that I can just go in (via the client) and temporarily disable the second screen.   This helped a lot.   When I exit I just re-enable that screen.

Thanks again.

---

### Post by 2hot6ft2 on 2010-04-29
> **gatorbrit said:**
> Glad to help and provide some input.   One thing i found for the dual monitor display is that I can just go in (via the client) and temporarily disable the second screen.   This helped a lot.   When I exit I just re-enable that screen.

Thanks again.
At least you can do that from the client so while it may not be the ideal solution at least it works for a quick work around.

You're welcome and thanks again.:)

---

### Post by Shark_AtK12 on 2010-04-30
Very helpful, thanks

---

### Post by 2hot6ft2 on 2010-04-30
> **Shark_AtK12 said:**
> Very helpful, thanks
Glad you found it useful. You're welcome.
:guitar:

---

### Post by Ozitraveller on 2010-06-13
Failure so far.

I can ping from both ends, but ssh times out. I've even re-built the server but still no go. I have a NetComm NB5Plus4 router.

Also my laptop is continuously freezing (10.04) doesn't help.

I'd appreciate any thoughts on getting this running.

Cheers

---

### Post by 2hot6ft2 on 2010-06-13
Only thing that comes to mind is make sure you opened the port on the server otherwise it would just drop the connection attempt silently. It's not like pinging (different port).

Timing out would could be a network error since it should say something if they were talking so it may be in the router settings. Not letting it connect to the server.

It's also a possibility that the freezing issue is related since if the freezing is related to the network adapter that could do it too.
Double check your settings.

Time to call it a night here and I have college tomorrow so it may be a couple days before I can get back to this again.
Can't think of anything else useful to add right now so good luck. I'll try to check this again as soon as I can.

I take it you did try connecting thru the terminal.
ssh -p port# serversipaddress
:confused:

---

### Post by Ozitraveller on 2010-06-14
Yes connected thru a terminal using
ssh -p port# serversipaddress

It's curious I can ping in both directions, only using ip though, not hostname.

I didn't think it was difficult.

I haven't set the server to static ip yet.

I'm confused too.

Thanks for your quick reply.

---

### Post by 2hot6ft2 on 2010-06-14
> **Ozitraveller said:**
> 
It's curious I can ping in both directions, only using ip though, not hostname.

Thanks for your quick reply.
The couple times I tried using the hostname it didn't work either but it works using the dyndns url and the IP Address. Might check to make sure the host name is right.
```
cat /etc/hosts
```
I haven't really dug into it as far as using the hostname since I set static IP Addresses and was done. Might have to use
ssh -p port# username@hostname

But if it connects when you use
ssh -p port# serversipaddress
then it's connecting and working.
;)
I'll play with it some more when I get a chance I've installed Ultimate Edition 2.7 so I need to set it all up again anyway one of these days.
:guitar:

---

### Post by Ozitraveller on 2010-06-15
> **2hot6ft2 said:**
> The couple times I tried using the hostname it didn't work either but it works using the dyndns url and the IP Address. Might check to make sure the host name is right.
```
cat /etc/hosts
```
I haven't really dug into it as far as using the hostname since I set static IP Addresses and was done. Might have to use
ssh -p port# username@hostname

But if it connects when you use
ssh -p port# serversipaddress
then it's connecting and working.
;)
I'll play with it some more when I get a chance I've installed Ultimate Edition 2.7 so I need to set it all up again anyway one of these days.
:guitar:

No worries, thanks for the help.

I'm going to break it all done and start from scratch again. Just to be sure. :)

---

### Post by 2hot6ft2 on 2010-06-15
> **Ozitraveller said:**
> No worries, thanks for the help.

I'm going to break it all done and start from scratch again. Just to be sure. :)
You're welcome. I plan on building a pc in a few weeks so once I get all the parts and everything else setup the way I want it I'll be doing it again then too, and when I do it I'll update the guide so more of the info. is in it and less linking to other info. but it works real good. I use it when at school between classes sometimes.
Shadowing is slow but then the school only has G band WiFi that I use.
:guitar:

---

### Post by Ozitraveller on 2010-06-15
I look forward to the update when you have the time.

Thanks again.

---

### Post by Ozitraveller on 2010-06-16
Ok I can login using ssh. The firewall on the server was the issue.  I have generated the keys. ssh-copy-id <username>@<host> doesn't work, I get a message about can't resolve host. So I copied the file to the server (usb). But logging in still asks for a password.

---

### Post by 2hot6ft2 on 2010-06-18
Once you copy the keys one to the server and the other to the client you have to edit the sshd file on the server and set Password Authentication to No so it will use the keys without asking for a password.
Glad you figured it out.
:guitar:

---

### Post by Ozitraveller on 2010-06-18
> **2hot6ft2 said:**
> Once you copy the keys one to the server and the other to the client you have to edit the sshd file on the server and set Password Authentication to No so it will use the keys without asking for a password.
Glad you figured it out.
:guitar:

Thanks. I really need to go thru this all myself and document it properly. :)

---

### Post by 2hot6ft2 on 2010-06-19
> **Ozitraveller said:**
> Thanks. I really need to go thru this all myself and document it properly. :)
It was covered in the guide after installing freenx and setting up the keys it went on to making it more secure by disabling password authentication.
So many things to do and so little time.
:popcorn:

---

### Post by Ozitraveller on 2010-06-19
I've been looking at external connection to my server, because I have a dynamic external ip. I could have it changed but I can't be bothered. So I though this might be useful to add to your instructions.

[http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)
Use our No-IP™ Free Dynamic DNS (DDNS) and redirection service to map a static or dynamic IP address or long URL to an easy to remember subdomain such as yourname.no-ip.org.

No-IP Free is our entry level service. Use yourname.no-ip.com instead of a hard to remember IP address or URL. Additionally use our dynamic update client to keep track of your dynamic IP address. You will always be able to get to your computer even if you IP address is dynamically assigned.

[http://www.no-ip.com/downloads.php](http://www.no-ip.com/downloads.php)
windows, mac, linux

Thanks for your effort.

I'd like to see this moved to Tutorials & Tricks too.

---

### Post by jdsmofo on 2011-04-24
This is a terrific guide.  I have been able to set it up so that I can control the desktop at home from the laptop at home, and to control the desktop at work from the laptop at work.  At work, the desktop is wired, and the laptop is from WiFi, but everything still works well.  However, I cannot control the desktop at work from the laptop at home.  In fact, I cannot even get an ssh connection, which just times out. I thiink that the issue is the router at home.  I have set it so that the laptop has a static ip address, and set it for port forwarding.  However, this last part is probably not correct, since I don't really know what I am doing. Suppose that the server is setup to use ssh on port 1000.  How should port forwarding be set on my home router, where the client is?  Should it also be external port 1000 and internal port of 1000?  Or something else?  Any help is greatly appreciated.

---

### Post by jdsmofo on 2011-07-16
Now I have problems within my own network using nomachine.  However, nobody seems to support this service anymore.

---

### Post by 2hot6ft2 on 2011-07-19
> **jdsmofo said:**
> Now I have problems within my own network using nomachine.  However, nobody seems to support this service anymore.
It's been a while since I saw this thread. I thought it had been long forgotten.

Google bought the code for FreeNX so they have changed it quite a bit. That was sometime last year or the year before.

As far as the ports and connecting to your own LAN goes some ISP's and some routers wont let you do it, but if you setup a free dyndns.com account it should still work. At least mine did last time I played with it, which has been a while now.

I set FreeNX to send on one port then in my router I set it to forward that port to another port on my desktop which had the server running with that port set to receive ssh connections.

Your work probably has all but a few incoming ports closed. Check with the IT department there to see if they will allow you a port to use. If they say no don't take it personally since their main concern is network safety. Open going out doesn't mean it's open coming in.

Check all your settings if you're still having issues. It's probably something simple once you find it.

I hope google revives freenx. It was a great program but they bought it because the code was a mess and they wanted it to work too.
:popcorn:
> [Neatx]("http://code.google.com/p/neatx")

[Neatx]("http://code.google.com/p/neatx") is a similar system to FreeNX, produced by Google.

It's Open Source, secure (SSH based), but does have some feature drawbacks compared to FreeNX. License: GPL2
From here: [http://help.ubuntu.com/community/FreeNX]("http://help.ubuntu.com/community/FreeNX")

---

### Post by pulck on 2011-12-22
Sorry to open up an old thread, but has anyone managed to use this guide recently?

I have followed the guide religiously, but my NX client will not log in with Password Authentication switched off on the server. I always get a '204 Authentication failed' error. I'm running the latest version of the client software (v. 3.5.0-7) so could it be that?

---

### Post by AlexanderDGreat on 2011-12-22
Install guide for NoMachine NX on Lucid 10.4 
[http://ubuntuforums.org/showthread.php?t=1546856](http://ubuntuforums.org/showthread.php?t=1546856)


NoMachine NX: simple setup without adding users 
[http://ubuntuforums.org/showthread.php?t=941530](http://ubuntuforums.org/showthread.php?t=941530)


NX service unavailable or access is disabled 
[http://ubuntuforums.org/showthread.php?t=1012056](http://ubuntuforums.org/showthread.php?t=1012056)


NXServer NX Server - ssh works but NX has authentication falure
[http://ubuntuforums.org/archive/index.php/t-449382.html](http://ubuntuforums.org/archive/index.php/t-449382.html)


[SOLVED] NX Server Suddenly Quit Working? 
[http://ubuntuforums.org/showthread.php?t=982554](http://ubuntuforums.org/showthread.php?t=982554)


These are more updated, recently.

---

### Post by AlexanderDGreat on 2011-12-22
double

---

### Post by derpishi on 2012-06-27
I have tried these suggestions. here is my output from windows nx client that does not allow me to connect: any suggestions:

```
NX> 203 NXSSH running with pid: 3428
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.11.2 on port: 8888
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: mvyvoda
NX> 102 Password: 
NX> 103 Welcome to: Vyvoda-Laptock user: mvyvoda
NX> 105 listsession --user="mvyvoda" --status="suspended,running" --geometry="1280x800x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'mvyvoda' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: mvyvoda
NX> 105 startsession  --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Vyvoda-Laptock" --type="unix-kde" --geometry="1274x747" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1274x747x32+render" 

NX> 1000 NXNODE - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 700 Session id: Vyvoda-Laptock-1000-C881C871271B42D7D060BC2579FBD6BC
NX> 705 Session display: 1000
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 4301afcaffece275181b9fa8e77ebe08
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 4301afcaffece275181b9fa8e77ebe08
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
/usr/NX/bin/nxshadowacl: 3: [: 1: unexpected operator
/usr/NX/bin/nxnode: line 553:  6831 Terminated              PATH="$PATH_BIN:$PATH" $PATH_BIN/nxagent $P $R -name "NX - $user@$SERVER_NAME:$display - $session (GPL Edition)" -option "$USER_FAKE_HOME/.nx/C-$sess_id/options" $K $G $B $FP $AGENT_EXTRA_OPTIONS_X :$display 2>&3
/usr/NX/bin/nxserver: line 1531:  6461 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 105 xrdb: No such file or directory
xrdb: Can't open display ':1000'
xrdb: No such file or directory
xrdb: Can't open display ':1000'
/usr/NX/bin/nxnode: line 338: startkde: command not found
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/mvyvoda/.nx/F-C-Vyvoda-Laptock-1000-C881C871271B42D7D060BC2579FBD6BC/session". You might also want to try: ssh -X myserver; /usr/NX/bin/nxnode --agent to test the basic functionality. Session log follows:
NX> 1006 Session status: closed
Can't open /usr/NX/var/db/running/sessionId{C881C871271B42D7D060BC2579FBD6BC}: No such file or directory.
mv: cannot stat `/usr/NX/var/db/running/sessionId{C881C871271B42D7D060BC2579FBD6BC}': No such file or directory
NX> 280 Exiting on signal: 15


```

---

