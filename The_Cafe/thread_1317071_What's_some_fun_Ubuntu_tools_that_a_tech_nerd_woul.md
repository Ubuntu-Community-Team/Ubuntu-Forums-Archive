---
title: "What's some fun Ubuntu tools that a tech nerd would get a kick out of?"
date: 2009-11-06
forum: The Cafe
---

### Post by Roasted on 2009-11-06
I work in the IT field, but mostly in Windows networks. We have a lot of tools, to manage servers, disk usage, uptime, etc. Are there any applications like that that I can add into Ubuntu to manage the status of, say, my Samba services for my file server? Or perhaps a detailed listing of the status of my hard drives, etc? What about a really nice VNC frontend that displays all of the computer names on the network and allows me to pick and choose based on computer name/IP address which one I want to connect to?

Just curious if there's more tools out there for Ubuntu than I'm aware. What do you guys think?

---

### Post by Giblet5 on 2009-11-06
I presume you want GUI tools since you come from a Windows background...

I find [mrtg]("http://oss.oetiker.ch/mrtg/") useful for monitoring routers. And phpmyadmin is a nice way to monitor/admin your MySQL database server.

Everything else is better done from the command line.

You *have* to embrace the command line to get beyond basic functionality on Linux systems.

---

### Post by kripkenstein on 2009-11-06
There are plenty of such tools, probably more than on Windows. But the vast majority will likely be console tools, which might take a little getting used to if you are coming from Windows. It's worth it though (for example, it's often possible to control these tools from scripts, to automate things in a much more easy way than with GUI apps).

For example, for monitoring hard drives there is smartctl, for monitoring cpus there is cpufreq-info, for monitoring the network iftop, etc. etc.

---

### Post by NoaHall on 2009-11-06
Hm, you might want to have a play with Conky.

---

### Post by CJ Master on 2009-11-06
> **NoaHall said:**
> Hm, you might want to have a play with Conky.

I was thinking the same thing.

---

### Post by earthpigg on 2009-11-06
```
man lshw
```
example:
```
sudo lshw | grep product
```

always nice to run from a LiveCD before purchasing a used computer. in addition to the obvious badblocks and memtest86+.

access all your music and movies from [anywhere in the world]("http://ubuntuforums.org/showthread.php?p=8246884") that you have internet access:
[http://wiki.archlinux.org/index.php/SSH](http://wiki.archlinux.org/index.php/SSH)
combined with free services provided by these guys if you have a dynamic IP:
[http://en.wikipedia.org/wiki/Dyndns](http://en.wikipedia.org/wiki/Dyndns)

(ssh can obviously do a lot more than that, but you get the idea :D )


if you limit yourself only to GUI apps, you will be ***severely*** crippling yourself.

---

### Post by Sealbhach on 2009-11-06
hardinfo gives a nice overview of your system.

Etherape gives a visual display of your internet connections.

tdfsb is a fun thing to play with.

.

---

### Post by jnew93 on 2009-11-06
Something like htop is a nice terminal tool for actually managing system processes. If you just want neat graphs and cool readouts, use conky and write a cool config. :p

---

### Post by Wee_Guy on 2009-11-06
Install _[Screenlets]("http://www.screenlets.org/index.php/Home")_, then enable the Sysmonitor screenlet (seen on the right side of _[this screenshot]("http://www.screenlets.org/index.php/Image:Widget_Layer.png")_)
```
sudo apt-get install screenlets
```Also, there are many system monitors for the menu bar, for example_ [GNOME Sensors Applet]("http://sensors-applet.sourceforge.net/")_, which monitors system temperatures and fanspeeds.
```
sudo apt-get install sensors-applet
```

---

### Post by Roasted on 2009-11-06
Guys - I've been on Ubuntu for several years. I have no issues working with the command line.

It's just my problem is, we're in a Windows environment, and with a network this big we have several tools to help manage our stuff.

I always try to think about what it would be like with Ubuntu in the same large environment. What tools would we use to get the same jobs done we do with Windows computers? What network admin program could we use to manage all VNC connections and connect remotely on the fly? What program could manage our servers and tell me the current status of them?

Command line or GUI, it's all the same to me. Point is I'm curious what comparable applications there are for large Ubuntu networks.

---

### Post by Dragonbite on 2009-11-06
I assume you mean FREE (or at least free)? Otherwise, Canonical uses [[COLOR="Blue"]Landscape[/COLOR]]("http://www.canonical.com/projects/landscape") and I'm sure Red Hat should have some tools to help.

I know it wasn't on a large scale (and heaven knows I'm not very server/network savvy) but when I installed CentOS a while back they had a couple of (GUI) tools to help manage Samba and Apache.  I haven't found them anywhere else.

---

### Post by earthpigg on 2009-11-06
> What program could manage our servers and tell me the current status of them?

Command line or GUI, it's all the same to me. Point is I'm curious what comparable applications there are for large Ubuntu networks.

i told you, ssh :D

observe:

(i've sensored my user name and domain name)

(red stuff is where something interesting just happened)

```
[chris: ~]$ df -Th && uname -a
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     11G  5.5G  4.4G  56% /
none         tmpfs    3.0G  160K  3.0G   1% /dev
none         tmpfs    3.0G     0  3.0G   0% /dev/shm
/dev/sda2     ext4     49G   28G   19G  61% /home
***[COLOR="Red"]Linux chris-desktop 2.6.31-ARCH[/COLOR]*** #1 SMP PREEMPT Tue Oct 13 11:33:39 CEST 2009 x86_64 Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz GenuineIntel GNU/Linux
***[chris: ~]$[COLOR="Red"] callmom[/COLOR]***
Connecting...
[email]username@domain.homelinux.net[/email]'s password: 
[COLOR="Red"][chris@mom-desktop ~][/COLOR]$ df -Th && uname -a
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4     28G  2.5G   24G  10% /
tmpfs        tmpfs   1003M     0 1003M   0% /lib/init/rw
varrun       tmpfs   1003M  120K 1003M   1% /var/run
varlock      tmpfs   1003M     0 1003M   0% /var/lock
udev         tmpfs   1003M  144K 1002M   1% /dev
tmpfs        tmpfs   1003M  1.4M 1001M   1% /dev/shm
/dev/sda3     ext4    198G  125G   64G  67% /home
***[COLOR="Red"]Linux mom-desktop 2.6.28-15-generic #52-Ubuntu[/COLOR]*** SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
[chris@mom-desktop ~]$ logout
Connection to domain.homelinux.net closed.
[chris: ~]$
```

i can fully administer and control my mom's computer from anywhere i am at with my netbook. or any other computer i trust with ssh installed. i can do and control ***everything***. install stuff, delete stuff, kill frozen applications she has running, check uptime, launch Synaptic Package Manger with its GUI (synaptic is not even installed on my computer), view logfiles, etc. everything, just as if i where physically sitting at the 'server' itself.

if it's only use was as a server, i would have absolutely no need for a keyboard, mouse, or monitor to be attached to it any longer.

how do ***you*** perform the expected computer tech support for your mother?

:D


edit:

this line from my ~/.bashrc may be helpful...
```
alias callmom='echo "Connecting..." && ssh -X -p 11111 loginname@domain.homelinux.net'
```

11111 is not actually the port number i use. loginname and domain aren't actually the login name or domain i use. you get the idea, though.

edit2:

i also use it to store movies and music, so i can listen or watch them wherever i am at with my netbook.

```
alias mountmedia='sshfs -p 11111 loginname@domain.homelinux.net:/home/media ~/mount'
```

and poof, my netbook with its 8gb hard drive now has a folder containing 200gb of music and movies that i can navigate to.

the 'server' has a user named 'media'. me and my mother have full read/write access to all of username media's stuff, and there is no way to actually login as user 'media'.

also serves as an easy way to do periodic offsite backup.


how much does a Windows sysadmin guy get paid to set something like that up, out of curiosity? and, since we have some professional IT tech's in the windows world around, how much would the needed software cost?

---

### Post by Roasted on 2009-11-06
Yeahhhhhhhhh okay how about a GUI tool then. :lolflag:

---

### Post by earthpigg on 2009-11-06
> **Roasted said:**
> Yeahhhhhhhhh okay how about a GUI tool then. :lolflag:

*nix servers traditionally do not have any GUI installed. would be very limiting. 

Ubuntu's server edition does not come with one, but you could install one if you wish. it is entirely possible to simply use remote desktop viewer to 'physically' take control of the mouse and see the screen on the 'server', of course, but that isn't fun.

and this stuff isn't ***that*** hard. it took me about two hours to [learn how ssh works, set it up, and have it fully configured]("http://wiki.archlinux.org/index.php/SSH"). ive never done anything similar in the past, and have zero IT education or certifications. and im a slow learner.

are you really going to let yourself be intimidated by something a dumb Marine grunt can set up? you are an IT professional! :D

---

### Post by NoaHall on 2009-11-06
You should write some scripts to do things. I currently have >50 scripts that I wrote to perform various things.

---

### Post by Roasted on 2009-11-06
> **earthpigg said:**
> *nix servers traditionally do not have any GUI installed. would be very limiting. 

Ubuntu's server edition does not come with one, but you could install one if you wish. it is entirely possible to simply use remote desktop viewer to 'physically' take control of the mouse and see the screen on the 'server', of course, but that isn't fun.

and this stuff isn't ***that*** hard. it took me about two hours to [learn how ssh works, set it up, and have it fully configured]("http://wiki.archlinux.org/index.php/SSH"). ive never done anything similar in the past, and have zero IT education or certifications. and im a slow learner.

are you really going to let yourself be intimidated by something a dumb Marine grunt can set up? you are an IT professional! :D

Ahhh, duh. I don't know why I wasn't thinking about that.

You see, my Ubuntu desktop at home runs Samba, so I kept thinking my computer = ubuntu = gui = samba = file server, blah blah. 

So anyway, I guess my question is kind of flawed, because you guys are right - I'd be using CLI if I were on a true Ubuntu Server. My idea in the back of my mind while asking the question was an Ubuntu desktop edition, though.

So, let me ask a stupider question yet: If I were running Ubuntu desktop edition as a server, how could I apply my original question to this?

---

### Post by twright on 2009-11-06
> **Roasted said:**
> Ahhh, duh. I don't know why I wasn't thinking about that.

You see, my Ubuntu desktop at home runs Samba, so I kept thinking my computer = ubuntu = gui = samba = file server, blah blah. 

So anyway, I guess my question is kind of flawed, because you guys are right - I'd be using CLI if I were on a true Ubuntu Server. My idea in the back of my mind while asking the question was an Ubuntu desktop edition, though.

So, let me ask a stupider question yet: If I were running Ubuntu desktop edition as a server, how could I apply my original question to this?
Exactly the same way... (most of server stuff is installed anyway)

Actually if you wanted an nice GUI way of doing things you could try Webmin or Landscape from Canonical.

---

### Post by earthpigg on 2009-11-06
> **Roasted said:**
> Ahhh, duh. I don't know why I wasn't thinking about that.

You see, my Ubuntu desktop at home runs Samba, so I kept thinking my computer = ubuntu = gui = samba = file server, blah blah. 

So anyway, I guess my question is kind of flawed, because you guys are right - I'd be using CLI if I were on a true Ubuntu Server. My idea in the back of my mind while asking the question was an Ubuntu desktop edition, though.

So, let me ask a stupider question yet: If I were running Ubuntu desktop edition as a server, how could I apply my original question to this?

the difference between a 'server' and 'desktop', in the linux world, is ***very*** trivial. you can use "Ubuntu Server Edition" as a desktop, and "Ubuntu Desktop Edition" as a server.

or, you can use desktop as ***both***:
the 'server' in all the examples above is my mother's home desktop, with a desktop version of ubuntu installed. she plays facebook games on it every day, often at the same time as i am streaming music from it onto my netbook at my girlfriends house. the server-type stuff was added & configured as an afterthought. and there are a dozen ways i could have gone about it. i happened to pick ssh.

every *nix machine is potentially a server. thats how unix started, after all. just install a few apps, configure them, and you are done.

---

### Post by benj1 on 2009-11-06
> **earthpigg said:**
> 
are you really going to let yourself be intimidated by something a dumb Marine grunt can set up? you are an IT professional!

do we have to imagine the drill sergeant from full metal jacket shouting that ?

SIR YES SIR :lolflag:

@OP
im sure linux probably has more and better tools for this kind of thing, after all it actually has a majority market share in the server market.

---

### Post by Roasted on 2009-11-06
Do you have to ssh through terminal in the moms computer vs my netbook @ GF's house situation?

Like if I want to SSH into my Ubuntu desktop at my house from my buddys house on my Ubuntu laptop, what do I need? Forwarded ports on the router? external IP address? 

And how do you stream music through the terminal? Or so you SSH through the GUI somehow so you can see and navigate to the files and double click to play?

---

### Post by CharlesA on 2009-11-06
> **Roasted said:**
> Like if I want to SSH into my Ubuntu desktop at my house from my buddys house on my Ubuntu laptop, what do I need? Forwarded ports on the router? external IP address? 

And how do you stream music through the terminal? Or so you SSH through the GUI somehow so you can see and navigate to the files and double click to play?

The only thing you would need to know to SSH to your desktop at your place from anywhere else is to forward the port on your home router and either know yer external IP address or setup dynamic DNS. Oh, and you'd need an SSH client. ;)

From what I understand you mount it as sshfs and it acts just as a local drive, but streams stuff over the internet. You'd access it from the desktop.

I think the only real tool I use is SSH to access my server.

---

### Post by twright on 2009-11-06
> **CharlesA said:**
> The only thing you would need to know to SSH to your desktop at your place from anywhere else is to forward the port on your home router and either know yer external IP address or setup dynamic DNS. Oh, and you'd need an SSH client. ;)

From what I understand you mount it as sshfs and it acts just as a local drive, but streams stuff over the internet. You'd access it from the desktop.

I think the only real tool I use is SSH to access my server.
Never mind messing around sshfs on the commandline, just use "Connect to Server..." in the places menu and you can connect via SSH, FTP or just about anything else for that matter.

---

### Post by CharlesA on 2009-11-06
> **twright said:**
> Never mind messing around sshfs on the commandline, just use "Connect to Server..." in the places menu and you can connect via SSH, FTP or just about anything else for that matter.

Oh nice! Thanks for the infos.

I wonder if you would be able to do that with Putty...

---

### Post by Roasted on 2009-11-07
> **twright said:**
> Never mind messing around sshfs on the commandline, just use "Connect to Server..." in the places menu and you can connect via SSH, FTP or just about anything else for that matter.

I don't mean to sound like an idiot, but SSH is something I only started playing with about, oh, a day ago... so I'm still getting my feet wet with it.

Say my external IP is 208.100.200.4, and my internal IP is 192.168.1.100.

If I go to places - connect to server, what all am I doing to connect to my computer? This is assuming I am connecting from an Ubuntu laptop on my work network to my Ubuntu desktop at home.

---

### Post by cariboo on 2009-11-07
If you don't have port forwarding setup in router nothing will happen. Unless you leave your server on 24/7 and never reboot, I would suggest setting up a static ip address on the server, then forward from that ip address to port 22 on your router, you'll have to check with your router documentation, how to exactly do port forwarding.

Once that is setup, just access your external ip from your work network. For example if you wanted to copy a file  from your server using nautilus, type in the location bar:

```
sftp://you@<your_external_ip_address>
``` 

I would also suggest setting up key based ssh access instead of using just a password. Have a look [here]("http://https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for a howto.

How come no-one has mentioned Hot Babe?

---

### Post by Roasted on 2009-11-07
> **cariboo907 said:**
> If you don't have port forwarding setup in router nothing will happen. Unless you leave your server on 24/7 and never reboot, I would suggest setting up a static ip address on the server, then forward from that ip address to port 22 on your router, you'll have to check with your router documentation, how to exactly do port forwarding.

Once that is setup, just access your external ip from your work network. For example if you wanted to copy a file  from your server using nautilus, type in the location bar:

```
sftp://you@<your_external_ip_address>
``` 

I would also suggest setting up key based ssh access instead of using just a password. Have a look [here]("http://https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for a howto.

How come no-one has mentioned Hot Babe?

Ahh, I see. So once the external connection hits my router, my router already knows port 22 is forwarded to me.

The million dollar question is - what if I need 2 computers on my network to be SSH-able?

---

### Post by cariboo on 2009-11-07
I would suggest using different ports 22 for one and 2200 for the other.

---

### Post by LookTJ on 2009-11-07
You can monitor bandwidth on your computer with vnstat.

---

### Post by LookTJ on 2009-11-07
> **cariboo907 said:**
> I would suggest using different ports 22 for one and 2200 for the other.
Can't you map port 22 with different IPs to different host ports in the router?

for example. private:22 to public:22 and other-private:22 to public:2220?

or would it be much simpler changing the SSH configuration?

---

### Post by Bodsda on 2009-11-07
Not relevant to the current direction of the conversation, but I recently came across a small program that I think is quite handy. It's called Angry IP Scanner. You can get downloads [here]("http://www.angryip.org/w/Download"). 

Angry IP Scanner can scan subnets and give you information on live IP's. Quite a useful way of making sure Scott the Script Kiddie next door isn't hopping on your network.

---

### Post by 00ber n00b on 2009-11-07
> **earthpigg said:**
> *nix servers traditionally do not have any GUI installed. would be very limiting. 

Ubuntu's server edition does not come with one, but you could install one if you wish. it is entirely possible to simply use remote desktop viewer to 'physically' take control of the mouse and see the screen on the 'server', of course, but that isn't fun.

and this stuff isn't ***that*** hard. it took me about two hours to [learn how ssh works, set it up, and have it fully configured]("http://wiki.archlinux.org/index.php/SSH"). ive never done anything similar in the past, and have zero IT education or certifications. and im a slow learner.

are you really going to let yourself be intimidated by something a dumb Marine grunt can set up? you are an IT professional! :D

Grrrrrrrr Kill!

I will be subscribing to your ssh thread...will need it in the future.

---

### Post by earthpigg on 2009-11-07
> **Roasted said:**
> The million dollar question is - what if I need 2 computers on my network to be SSH-able?

the way i set it up:

the one computer is accessible from the outside world as established in the router's settings.

from there, i use a command line web browser (lynx) to view the 'local' IP's of the others on the LAN.

each computer has a single port open (none use 22), a list is maintained on the primary 'server' computer as an alias in my .bashrc. once i ssh to the server, i type 'listports' and it reminds me what ports each computer listens to.

then i go ahead and type 'callrouter' and open the router's web interface in lynx (again, alias in .bashrc). go to its 'status' page and it shows the internal IP addresses of other computers on the LAN.

using that, i ssh to other computer from the first ssh connection.

netbook ---(ssh)---> mom's desktop ---(ssh)---> other computers on the LAN.


ssh within ssh. have played with ssh within ssh within ssh within ssh within ssh, to eventually open a terminal in the computer i was currently using. no useful reason to do that, except i was playing around.

---

