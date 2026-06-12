---
title: "VMWare Server 2.0.2 on Ubuntu 9.10 often fails to start and often crashes."
date: 2009-12-22
forum: Virtualisation
---

### Post by michwill on 2009-12-22
Hi All,

I'm having a bit of an issue with "VMware Server 2 for Linux Operating Systems 64-bit version Version 2.0.2 | 203138 - 10/26/09".  I'm running Ubuntu 9.10 Karmic Koala with all updates as of this writing.  Basically the Web Interface randomly crashes and doesn't always restart upon system restart.  I'm often forced to "sudo /etc/init.d/vmware restart".  Also, all of my Guest OSes crawl, even after updating VMWare Tools.

I was previously running version 2.0 with Ubuntu 8.04 and performed all incremental updates and patches.  However, I'm still experiencing severe issues.  Are there any recommended courses of action short of wiping and reinstalling?  I'm on a 2GHz quad-core Xeon with 8 GB of memory.  The uname output is as follows:

Linux core64 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

Thanks in advance.

---

### Post by flushmylog on 2010-02-24
Experiencing same problem.
Same version of vmware server and Ubuntu.

My Web Interface was also intermittently hanging but now its not so intermittent anymore...

Fails to open the site no matter reboot, cold boot, stop start of vmware, different browser sessions, connecting from remote machine, nothing.
Stays on "Waiting for 127.0.0.1..."
Never times out.

From netstat I can see it is listening on that port:
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN  

I can also see my browser session established:
tcp        0      0 127.0.0.1:39561         127.0.0.1:8333          ESTABLISHED
tcp        0      0 127.0.0.1:8333          127.0.0.1:39561         ESTABLISHED

No errors in logfiles in /var/log/vmware/webAccess

Luckily I saved a shortcut (opens the VMware Remote Console to the vm) to one of my vmware machines before this happened.

Weird enough that connects to 8333 as well but works fine.

Now I'm stuck with not being able to control or change settings.

Internet also seems to be pretty dry on solution for this issue.

So beware before you run this version combination.

---

### Post by jerzyo on 2010-03-06
I have the same problem. Can anyone help me?

---

### Post by danteuk on 2010-03-17
Same here, running the vmware_config.pl and re-booting used to fix this but not anymore.
Kubuntu 9.10(64bit) / VMware-server-2.0.2-203138.x86_64
Linux Borodin 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

I'm using shell scripts to launch the remote console so I can still use my virtual machines.
problem now is I need to create a new one and without the Web UI it's a pain, I've made the .vmx based on another machine used vmware-vdiskmanager
to make the disk, but I can't launch the machine because it just says it can't find it, even though it's in the same place as the other machines.

Logs are useless and contain nothing remotely helpful for either problem.

---

### Post by HermanAB on 2010-03-17
Hmmm, VMware Server should not be lightly discarded...

It should be thrown, with great force!

You would do much better with VMware Workstation or VMware Player.

---

### Post by robertco on 2010-05-30
About vmware server web management or vmware UI or web console please read what follow, these are two sequential posts I've written on radu.cotescu.com blog

Dear Radu,
 we installed Ubuntu 9.10 64 bit  with vmware server 2.0.2.
Thank you for your script.
Everything  works fine… but we too have had the issue with web UI or web management  interface: it stops working.


Services are running and connecting  to 8333 with VMware Infrastructure Client 2.5 (the one from ESX 3.5)  does work.


It is really tomcat that have some issues.
We  removed and reinstalled vmware and after that webui started.
With the webUI  started, we left it there just open, we went to have a coffee and when  back the web management interface was not able to refresh… service was  gone bad.
Really bad issue.


We tried made the modification  described by jalung in the post #9 in this thread:
 [http://communities.vmware.com/message/1098804#1098804](http://communities.vmware.com/message/1098804#1098804)
more  or less what you say above: hal daemon hald
but it doesn’t work.  It faked to work, but it does not.
Some moths later, do you have  any fix on this issue?
Thank you
 Roberto


FIRST POST finished here, but later we made some additional attempts to next discover that the fix was working with something else to know, pelase read the second mesage:


IMPORTANT UPDATE on my previous message.
MODIFICATIONS  TO FIX VMWARE SERVER WEB MANAGEMENT ARE WORKING !!!
 Please note  that on ubuntu, the modifications descripted in the link above must be  adapted to ubuntu syntax to start the two daemons.
**After that  modification some secondary issues are coming and they all are caused by  the different windows browsers** (we are connecting from windows)


If  connecting to vmware UI from Explorer 8, you may have to set the  Compatibility Visualization.

 From firefox some clear the cache is  needed.


[I]I wanna tell you one story.
 Strange but true: we  edited the hosts windows file to add our vmware-1 and vmware-2 servers.
 Well: pointing firefox to [https://vmware-1:8333]("https://vmware-1:8333/") does not open the UI, while  ponting to vmware-1 tcp ip address, it does.
 You may think it is due  to some mistypings in the hosts file… no it isn’t because repeating the  test with Explorer 8 the vmware web management shows the login box in  both cases (!?!?!??!!!  O_o?!!?)[/I]


Anyway, now vmware server for  linux web management interface works, but beware because issues are  coming from browsers too.


Looks like that with Explorer 8 it is  more simple to connect.

 Note that on another pc we do have an old  Explorer 6 and during testings it does seem it is easier much more.


Last  but not least:
PRO: when connected, the vmware user interface  works without interruptions
 CON: sometime looks like vmware web  management gooes to sleep, some refreshes in the browser makes the login  page to appear again correctly (done with explorer)
Hope this can  help, we lost days on this issue.


Ciao
 Roberto
[URL="http://www.fastec.eu/"]http://www.fastec.eu/alta-disponibilita-cluster-high-availability.html
[/URL]

---

### Post by robertco on 2010-05-30
Web User Interface issues a part, now formally fixed,

would you like to kindly report your experiences with:

- Ubuntu Server 9.10 64 bit (please declare you kernel version)
- vmware 2.0.2 64 bit VMware-server-2.0.2-203138.x86_64
- 64 bit windows server guests
- other windows server guests
- other windows guests

Here you our actual experience

we are testing
- ubuntu server 64 bit with default installation kernel 2.6.31-[COLOR=#000000]14
- [/COLOR]VMware-server-2.0.2-203138.x86_64
- windows 2k3 as unique VM guest (during testings it was XP Pro SP3)

1) first issue we had was the web interface issues, **now fixed** (see previous post)
2) during setup, movements and tests (while you shut down and start the whole server) after some server starts and or power cycles, vmware failed to start. To check it we manually stopped vmware from init.d and we discovered an issues with Virtual Network, in fact trying to start vmware from init.d failed with a message sentencing about some modules not good for current kernel version O_o!?!? (hey bud! nobody changed them and ubuntu updates are disabled...)
We had run again ***vmware-config.pl*** , an operation that requires you to delete some vm* modules, next the script does recompile the deleted modules and as last step, it does start vmware services.
After this configure script run, vmware started fine.

Since the reconfiguration, we already restarted some times the whole server, nothing bad has happen.

We are now monitoring the issue and each time that is possible, we will restart the whole ubuntu 64 bit server to see if the issue repeats.

To be true, the whole testing period was made with an upgraded kernel and only in the last two days we downgraded it because of web interface issues. When fixed the vmware 2.0.2 web UI, we did not re upgraded the kernek. Anyway now we will test kernel sub version 14 next we will re update it.

**Re update the kernel means also to recompile vmware** with the proper _**[Radu]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/")**_'s script that is combined with the proper _**[Ramon]("http://risesecurity.org/2010/01/10/vmware-server-2-0-2-update-patch/")**_'s patch (I write here both the links for correctness. Have a look to Ramon web site and kudos him, but beware that the patch should be already included in the Radu's script)
WARNING: on Radu's blog there is a post for any ubuntu kernel version, browse the blog and choose the more proper Radu's script.

Any your personal experience is welcome, expecially talking about stability, networking and so on.

i.e. somebody says that vmware 2.0.2 is more reliable and works like a charm on Ubuntu 8.04LTS, months and months without issues.

Thank you

Ciao
 Roberto
[http://www.fastec.eu/alta-disponibilita-cluster-high-availability.html]("http://www.fastec.eu/")

---

