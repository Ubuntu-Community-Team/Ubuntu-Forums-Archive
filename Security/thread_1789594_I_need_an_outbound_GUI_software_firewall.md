---
title: "I need an outbound GUI software firewall"
date: 2011-06-24
forum: Security
---

### Post by bubba2 on 2011-06-24
A reply to this closed thread
[http://ubuntuforums.org/showthread.php?t=1696699](http://ubuntuforums.org/showthread.php?t=1696699)

It is all talk and no action in this thread.ZoneAlarm does not exist for Ubuntu but here are some other ways to control network access.

To stop a program from accessing the network:
  # Install sux,create a new user bob,set network rules for him and run gedit (or whatever program that shoud be stopped) as bob
  sudo apt-get install sux
  sudo useradd bob -c "Example user bob" -d /home/bob -m -s /bin/bash -g users
  sudo iptables -A OUTPUT -m owner --uid-owner bob -j DROP
  sudo sux bob gedit

To stop all programs from accessing the network except one:
  # Create a new user bob,set network rules for bubba (thats me) and run gedit as bob
  sudo useradd bob -c "Example user bob" -d /home/bob -m -s /bin/bash -g users
  sudo iptables -A OUTPUT -m owner --uid-owner bubba -j DROP
  sudo sux bob gedit

To be more user friendly it is possible to edit the meny with alacarte to run programs as different users.
There are more examples here
[http://www.linuxjournal.com/article/6091](http://www.linuxjournal.com/article/6091)

---

### Post by scruffyeagle on 2011-08-27
> **bubba2 said:**
> A reply to this closed thread
[http://ubuntuforums.org/showthread.php?t=1696699](http://ubuntuforums.org/showthread.php?t=1696699)

It is all talk and no action in this thread.ZoneAlarm does not exist for Ubuntu but here are some other ways to control network access.

To stop a program from accessing the network:
  # Install sux,create a new user bob,set network rules for him and run gedit (or whatever program that shoud be stopped) as bob
  sudo apt-get install sux
  sudo useradd bob -c "Example user bob" -d /home/bob -m -s /bin/bash -g users
  sudo iptables -A OUTPUT -m owner --uid-owner bob -j DROP
  sudo sux bob gedit

To stop all programs from accessing the network except one:
  # Create a new user bob,set network rules for bubba (thats me) and run gedit as bob
  sudo useradd bob -c "Example user bob" -d /home/bob -m -s /bin/bash -g users
  sudo iptables -A OUTPUT -m owner --uid-owner bubba -j DROP
  sudo sux bob gedit

To be more user friendly it is possible to edit the meny with alacarte to run programs as different users.
There are more examples here
[http://www.linuxjournal.com/article/6091](http://www.linuxjournal.com/article/6091)

I don't fully understand sux, but on the surface this doesn't seem sufficient to compensate for the problem. What if the utility initiating a secret connection is a printer driver?

---

### Post by ottosykora on 2011-08-27
>What if the utility initiating a secret connection is a printer driver?<

yes, or just simple DNS request or..

---

### Post by haqking on 2011-08-27
> **bubba2 said:**
> A reply to this closed thread
[http://ubuntuforums.org/showthread.php?t=1696699](http://ubuntuforums.org/showthread.php?t=1696699)

It is all talk and no action in this thread.ZoneAlarm does not exist for Ubuntu but here are some other ways to control network access.

To stop a program from accessing the network:
  # Install sux,create a new user bob,set network rules for him and run gedit (or whatever program that shoud be stopped) as bob
  sudo apt-get install sux
  sudo useradd bob -c "Example user bob" -d /home/bob -m -s /bin/bash -g users
  sudo iptables -A OUTPUT -m owner --uid-owner bob -j DROP
  sudo sux bob gedit

To stop all programs from accessing the network except one:
  # Create a new user bob,set network rules for bubba (thats me) and run gedit as bob
  sudo useradd bob -c "Example user bob" -d /home/bob -m -s /bin/bash -g users
  sudo iptables -A OUTPUT -m owner --uid-owner bubba -j DROP
  sudo sux bob gedit

To be more user friendly it is possible to edit the meny with alacarte to run programs as different users.
There are more examples here
[http://www.linuxjournal.com/article/6091](http://www.linuxjournal.com/article/6091)


all talk no action.

It was answered a multiple of times.

IPTables,
UFW.GUFW
<snipped unmaintained front-end firewall GUI>

take you pick, they can all block outgoing connections

as stated unless a user inititates them there are none

---

### Post by inphektion on 2011-08-27
anyone ever look at this? [http://configserver.com/cp/csf.html](http://configserver.com/cp/csf.html)

i've never used on a desktop but on a server its very good.  Gives me a bit more piece of mind over iptables alone.

---

### Post by Dangertux on 2011-08-27
> **inphektion said:**
> anyone ever look at this? [http://configserver.com/cp/csf.html](http://configserver.com/cp/csf.html)

i've never used on a desktop but on a server its very good.  Gives me a bit more piece of mind over iptables alone.

It's not a bad tool. But not sure why it gives you more peace of mind than iptables, like most Linux "firewalls" all it does is include configurable iptables scripts. It also grabs up the logs from different places (like mod-security) and makes them easier to read.

Still a decent piece of software though.

---

### Post by inphektion on 2011-08-27
Just because it does a bit more than iptables.  Its like a mix of iptables, fail2ban, logwatch, and maybe a few more in one.  Alerts sent if server load avg is high, ping flood detection, etc.  

Honestly of all the servers i need to manage i use it on two that i feel maybe are more targetable.  The rest i am fine with my iptables config, fail2ban, logwatch, logcheck, and on some aide.

---

### Post by scruffyeagle on 2011-08-27
> **haqking said:**
> all talk no action.

It was answered a multiple of times.

IPTables,
UFW.GUFW
 <snipped unmaintained front-end firewall GUI>

take you pick, they can all block outgoing connections

as stated unless a user inititates them there are none

Hi, haqking!

How about a little more talk?
Pick one, and explain how it could

a) Block a printer driver from initiating a secret connection, and

b) Notify the Admin that there was a problem involving that particular printer driver; i.e., that the attempt had occurred, and the source of the attempt.

TIA!

---

### Post by bubba2 on 2011-08-28
> **ottosykora said:**
> yes, or just simple DNS request or..
Strange that I have not seen this. Do you have your DNS configured in a special way?

> **scruffyeagle said:**
> I don't fully understand sux, but on the surface this doesn't seem sufficient to compensate for the problem. What if the utility initiating a secret connection is a printer driver?

The purpose of sux is to launch the application as another user.

The printer driver sounds interesting. Do you have any more details?
Remember that it is a normal user without sudo privileges.

---

### Post by cariboo on 2011-08-28
> **scruffyeagle said:**
> Hi, haqking!

How about a little more talk?
Pick one, and explain how it could

a) Block a printer driver from initiating a secret connection, and

b) Notify the Admin that there was a problem involving that particular printer driver; i.e., that the attempt had occurred, and the source of the attempt.

TIA!

Could you give us an example of this? I've never heard of a printer creating a secret connection, and how would this "driver" do it.

Keep in mind that all the printer drivers available during the install, come either from a trusted repository, or directly from the manufacturer.

---

### Post by scruffyeagle on 2011-08-29
> **cariboo907 said:**
> Could you give us an example of this? I've never heard of a printer creating a secret connection, and how would this "driver" do it.

Keep in mind that all the printer drivers available during the install, come either from a trusted repository, or directly from the manufacturer.

**_To cariboo907 & bubba2_**: No, I've only been studying Linux about 2 months now, so I'm sorry but I can't provide any examples. Some people are great at trivia & details. Others forget details, but are great at discerning the general shape of things and the flow of functions. If I was great, I'd be in that 2nd category. The idea that a printer driver could initiate a secret connection is something I picked up during my endless reading of threads here at the forum. You know, after a while you can pretty much tell by reading what people write, what their respective levels of expertise are. I'd read a post where the author was saying that this is both possible and probable - and that, manufacturers are making a marketing shift toward providing dedicated drivers for their equipment, slated for use within Linux OS's. I had the impression that the person writing the post was advanced enough in his mastery of Linux/Ubuntu to be well founded in what he was asserting. At which point, I decided that until I had strong evidence to the contrary, I should believe it too.

I place absolutely no trust at all, in the good intentions of _any_ corporation. Their only values are measured in monetary units of profit. If they can invade our privacy and thereby increase their profits without risk of legal penalizations, they'll do it without hesitation.

I'm far from expert, at this point. All I can do is guess based on what I've read so far. A printer driver might be in an excellent position to launch a secret connection. Being associated with a device common to all Users of the system, it's possible that with a small amount of data mining it could spoof the identity of the current User for the sake of launching a connection. Or, perhaps when it discerns a live connection to internet available, it could launch a connection on its own authority. The default configuration of the firewall in Ubuntu is forbidding all inbound and allowing all outbound - so what would prevent it? As a system device, it has its own identity of a sort. It even belongs to a group. Besides, outbound connections don't require sudo authority. It is a program, and the default firewall configuration allows programs to initiate connections. Unless there's some protocol in the OS that specifically forbids drivers (or selected programs) from initiating outbound connections, what would prevent it from succeeding? It could potentially invade the privacy of every User on the system including the Admin(s), and relay that information to the corporation that created it. That could include things like the directory structures and file names of everyone who includes the printer as an available device in their profile, and even contents of files. And, if it can establish an active connection, and send information, is it much of a leap to think that it could also receive instructions for what to do next?

This isn't paranoid thinking. It's a critical assessment of the situation, based on the information currently available. I've come to perceive it as a new problem the Linux OS must cope with. And, new problems (as a general rule) require new solutions.

---

