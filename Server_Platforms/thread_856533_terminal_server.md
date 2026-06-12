---
title: "terminal server"
date: 2008-07-11
forum: Server Platforms
---

### Post by Tallwood on 2008-07-11
I am trying to lock down desktop environments on diskless client machines. The GUI profile editor within Edubuntu doesn't seem to save preferences, and I have read on the Gnome Sabayon section that the preferences will not populate target machines.

Am I going about this wrong? Or am I SOL for now? :confused:

Basically all I want the client to see is a Firefox icon when they boot in to the desktop.

---

### Post by bluefrog on 2008-07-12
put a firefox launcher in /etc/skel/Desktop.

anyway, sabayon and pessulus are your best friends.

---

### Post by Tallwood on 2008-07-14
When I try to customize the client profile to only show a firefox icon and no panels or quicklaunch icons on the dock it doesn't seem to save when I reboot the client.
I'm using the built in profile editor.
Has anyone else experienced this problem or does it sound like I'm going about it wrong?

Also, I'll look in to the directory mentioned above for the client desktop. I don't have a problem with the firefox icon showing up, just with the dock panels and menus repopulating to default. Plus the client desktop has full permissions to change the panels and add icons, etc. When I look in the users and groups I don't see any where to change permissions. And, I've tried to chmod a particular client's home directory, but then it won't boot in to terminal server at all.

---

### Post by Tallwood on 2008-07-16
So I've got the desktop configured to look enough like we need it with sabayon and pessulus, but I can't lock down the changes. Meaning, if the user knows enough or fools around enough with the desktop they are able to add panels/main menu items as needed. Maybe we are setting up the users incorrectly?? We set them up as desktop users and not admins.

and we'll just control firefox through the shorewall.

---

### Post by Tallwood on 2008-07-19
Ok, so I'm toying around with plain old LTSP running off CentOS 5. I can not find out how to run Sabayon and it doesn't even have Pessulus as an option. I thought all Gnomes nowadays came with these built in?

I can find Sabayon in the filesystem and run the executable, but it won't allow me to edit the profile I've made. When I click edit it gives me a conflict of some sort. I'm guessing some dependencies or something are missing.

Any ideas to successfully accomplish my problem above?

---

### Post by Tallwood on 2008-07-21
If anyone reads this that has successfully locked down diskless clients on any LTSP platform, please share with me what distro you used and any extra steps necessary. Thank you.

---

### Post by maybeway36 on 2008-07-23
One way to do this might be to use Metacity only and have Firefox start up on login and log off when it is closed. Put this in ~/.xsession:
```
#!/bin/sh
metacity&
exec firefox
```
There will be no panels for them to mess around with :P

---

### Post by Tallwood on 2008-07-24
Ok, I will try that tomorrow.

We deployed all the clients today and they are booted from the server via NIC w/ PXE.
This customer doesn't go live until Monday with all this, so I will play around with some configs tomorrow and hopefully not over the weekend.:)

---

### Post by Tallwood on 2008-07-25
> **maybeway36 said:**
> One way to do this might be to use Metacity only and have Firefox start up on login and log off when it is closed. Put this in ~/.xsession:
```
#!/bin/sh
metacity&
exec firefox
```
There will be no panels for them to mess around with :P



Ok, I went looking for where to put this config and could not find anything of use. Here is what a locate of xsession turned up.

[root@ltsp ~]# locate xsession
/home/agent101/.xsession-errors
/home/agent102/.xsession-errors
/home/agent103/.xsession-errors
/home/agent104/.xsession-errors
/home/agent105/.xsession-errors
/home/agent106/.xsession-errors
/home/agent201/.xsession-errors
/home/agent202/.xsession-errors
/home/agent203/.xsession-errors
/home/agent204/.xsession-errors
/home/agent205/.xsession-errors
/home/agent206/.xsession-errors
/home/agent299/.xsession-errors
/root/.xsession-errors
/usr/share/xsessions
/usr/share/xsessions/gnome.desktop
/usr/share/xsessions/icewm.desktop
/usr/share/xsessions/kde.desktop
/usr/share/xsessions/reset.desktop
[root@ltsp ~]# cd ~/.xsession
bash: cd: /root/.xsession: No such file or directory
[root@ltsp ~]# cat ~/.xsession
cat: /root/.xsession: No such file or directory
[root@ltsp ~]# 


Am I looking in the wrong place?


Also, the GUI profile editor does not seem to save the majority of the desktop settings configured. For instance, I've tried to delete and/or uncheck the Instant Messenger app in Applications/Internet, and it will reappear each and every time I open the profile editor back up to edit the agent profile. Maybe I'm leaving some dependencies that Instant Messenger relies on. Does anyone have any leads on this?

If I can get the above xsession file ironed out so only Firefox will open then the profile editor is obsolete.

Thanks in advance,
Jason.

---

### Post by Tallwood on 2008-07-25
also, all the .xsession-errors files are hidden or unavailable to me for some reason. I am logged in as root.

---

### Post by Tallwood on 2008-07-29
Ok, so we went live yesterday.
These thin clients are used to access a web based application only. This part works like a charm.
We have had up to 6 clients logged in to a Dell PE850 running LTSP. By the end of the week they expect to have all 14 up and running.
One more problem I need to find out how to resolve is whenever I minimize a browser or application window it closes out the window.
I believe the applets involved in this are the window switcher and window list applets. I have them available on the server on the users profiles. I am thinking I may need to restart the server as I've tried restarting the clients with no success on this issue.

Let me know if anyone else has any ideas.

---

### Post by Tallwood on 2008-08-01
I made some changes in Pessulus/Sabayon manager to the user profile to allow for the window switching applet and it only effected half of the user accounts. I am going to log in from a known effected account on a different client to make sure the changes follow the account as I presume they will.

Anyone ever had anything like that happen before?

---

### Post by Tallwood on 2008-08-14
Ok, the window switching applet was solved by a restart of the LTS. As I assume most other applet problems would be solved by this.
So far since my last post we have had no major problems. We now have 14 thin clients running. 2 Manager type machines, and 12 agent type machines.
This installation is in an outbound call center where we are running a predictive dialer through a web interface off the thin clients.
I'm still looking for solutions as to how to completely lock down the desktops, so as to minimize client downtime due to inadvertant changes made.

Let me know if you have any suggesions or questions.

---

### Post by Tallwood on 2008-09-16
So, 4 weeks in, and no glitches so far. The application that runs on these clients is a web based portal to another server. Once logged in on the portal the users don't really have time to fool around on the workstations as the portal keeps track of active time within the portal, etc. and these employees are all production based pay. So, we haven't needed to completely lockdown the desktops. And, without HDs on the clients we won't really have much of a maintenance concern as their is nothing being downloaded off the net.

Let me know if you have any questions.

---

### Post by Tallwood on 2009-03-18
Does anyone know of a way to backup and restore a terminal server OS to another identical server. Basically I want an exact install with all changes I've made to the terminal server on another server. I am trying to do this so I can then move on with our load balancing project.

Thanks.

---

### Post by OoteR on 2009-03-18
I would just use PING and image the server, then you can just toss the image onto the new server, boot up, change the IP information/hostname etc and be all set. 

ping.windowsdream.com

---

### Post by koenn on 2009-03-18
> **Tallwood said:**
> Does anyone know of a way to backup and restore a terminal server OS to another identical server. Basically I want an exact install with all changes I've made to the terminal server on another server. I am trying to do this so I can then move on with our load balancing project.

Thanks.
rsync them ?

I've tried this once to se if it'd work, and it did
notes: [http://users.telenet.be/mydotcom/howto/linux/clone.htm](http://users.telenet.be/mydotcom/howto/linux/clone.htm)

I only tested it as a concept.
In tral life, there are a few caveats :

your hardware needs to be identical, or at least close enough that hw-specific settings on one machine also work on the other
I tested it in between virtual machines on the same host, so hardware wasn't an issue.

some things need to remain unique : hostnames, ip addresses, ... you'll have to find a solution for this. 

rsync transfers files, and can't look beneath your directory tree. Your mount points on both machines need to match if you want a real clone.

---

### Post by Tallwood on 2009-04-02
Ok, so we've got both servers identical.

Now, I'm trying to set up load-balance and failover between the two. I've tried editing the dhcpd-k12ltsp.conf files to prioritize which one is primary/secondary, etc. and i've also adjusted the dhcpd-master file to match.

The problem is, dhcp won't start after these changes.

Does anyone have a good write up on setting this up? The one I used didn't seem to work lol.

---

### Post by Tallwood on 2009-04-06
So, the problem I'm getting after building the files as instructed in

[https://wiki.edubuntu.org/EdubuntuDHCPload-balancingFailover](https://wiki.edubuntu.org/EdubuntuDHCPload-balancingFailover)

, the log file tells me it can't access the dhcpd-k12ltsp.failover file.

I created it as root, and even tried changing it to a 775 permissions file. The original dhcp conf file does not have execute permissions, so i'm not sure why this one file would need it.

Am I misunderstanding what the "includes" in the .conf file is suggesting?

---

### Post by Tallwood on 2009-04-15
So, it turns out that we had some syntax errors in our config files. And, we tried several different examples of config files. The whole lot of them are wrong.

---

### Post by Tallwood on 2009-08-10
An update on this project.
We have 24+ users on 2 terminal servers now.
The load balance is set at 50/50.
And with thin client machines we have experienced minimal user error. Actually our only hardware failure has been a monitor or two.

---

### Post by sixstorm on 2009-08-10
> **Tallwood said:**
> An update on this project.
We have 24+ users on 2 terminal servers now.
The load balance is set at 50/50.
And with thin client machines we have experienced minimal user error. Actually our only hardware failure has been a monitor or two.

That's really cool that you have a real working terminal server, with it being Linux and all ;)  I'm looking into some free alternatives to MS objects, such as terminal servers, etc.  Will keep this thread/project in mind when I get to diving into it.

---

### Post by Tallwood on 2009-09-15
Please do.
And let us know if you have any questions about it.
We have network printing capable for all clients as well.

---

### Post by Tallwood on 2009-10-15
Ok, we are putting together another LTSP project. This time the terminal server(s) will need to have access to the internet, and on top of that we would like to limit what terminals have internet access. I know I have struggled with this task in MS terminal services. Does anyone have a suggestion of how to accomplish this access restriction? Or a good place to look for research?

Thanks,

---

### Post by Tallwood on 2009-10-26
We still have not found a solution to limit internet access on some of the thin clients.
Does anyone know if iptables is capable of limiting http traffic based on MAC addresses? For instance, can I restrict some of my internal MACs from reaching the external NIC of the terminal server. Keep in mind they obviously have to reach the internal NIC of the terminal server, and the way this network is designed they will have to reach some services located beyond the external NIC. Really I need to a port forward but in reverse, so only the internal port is forwarded to an external address.
I'm not even sure that is possible????????

TIA.

---

### Post by Tallwood on 2010-05-21
No new updates to report.

We have 2 separate LTSP systems up and running now at 2 different locations. Both of them are call centers.
Would still like to find a way to block or pass certain thin clients from getting past the FW. For now we have to block or pass certain http sites, which can be tedious.

---

