---
title: "New startup system gives me gray hairs..."
date: 2010-05-21
forum: Server Platforms
---

### Post by pezball on 2010-05-21
System startup on my Ubuntu Server 10.04 is a hit and miss now... sometimes only ssh and ntp and a few other processes are started... total around 130 processes, while with a full startup it should be around 160... at least ssh runs so I can access it by remote but I always have to double check if all things been started... very annoying

Sometimes all starts except mysql...  with mysql complaining that it can not open up port 3306... why would port 3306 be busy... no other process should use it...

This new startup system seems to be buggy to say the least, I rather wait 15!!! minutes longer for an old style sequential startup, than have to reboot the server and pray for good luck.. i assume it's a timing problem so that processes never start if they by chance get woken up in the wrong millisecond... :confused: ...or somehow the resources they need are busy so they simply refuse to start... either way it should not happen...

Whatever the reason... I do not want to be forced to control what has been started or not every time i reboot... it should just work... :mad:

---

### Post by ian dobson on 2010-05-21
Hi,

I can understand your problems with upstart. For a server you don't need to reboot that often so the old init script method doesn't make too much of a difference. With a desktop/appliance (MythTV frontend) the time it takes to startup effects the "user experiance" and upstart can help there by starting processes in parallel.

You should be able to get upstart to just start your deamons in the old way. I'll take abit of work recreating your init scripts (or you do have a pre-upgrade backup), as upstart can/does start the /etc/init.d/rc script that start the rcX.d init scripts.

Another way to solve your problems is to findout what deamon is dependant on what service (mysql can bind to a port on an IP/ethernet port, and if the ethernet/TCPIP isn't up the bind will fail) and make sure upstart is configured so that the services/deamons start in the correct order.

Maybe you have a mysql database listening on port 3306 of IP 192.xxx on ETH1 so you need to tell upstart that you can only start mysql when:-

eth1 is up and your local file systems are up (or network filesystems whennyour database is on a NFS share).

Another way to make sure everything starts in the correct order is to add a small script to the upstart configuration that checks if the services required are there before starting the deamon. In my case mythtv-backend relies on a m3u file for the channel list, and this is on the local apache server, so I changed the mythtv-backend.conf file to include a loop waiting for apache to be up and running:-

# MythTV Backend service

```

description     "MythTV Backend"
author          "Matt Mossholder <matt@mossholder.com>"

start on (local-filesystems and net-device-up IFACE=eth0)
stop on runlevel [016]

#expect fork
respawn

pre-start script
    # wait for listen on port 80
    while ! nc -q0 localhost 80 </dev/null >/dev/null 2>&1; do
        sleep 1;
    done
end script

script
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script

```

Don't give up just yet. Upstart will be a wonderful tool someday, once are the dependancy problems are solved (This is more a ubuntu problem as upstart does what it's told todo).

Regards
Ian Dobson

---

### Post by pezball on 2010-05-21
Ya I could probably use old script style...
 
But what happens when an update arrives for a package which I have changed to use old init.d script style? Can it handle that or will it want to overwrite my changes, as it did when i upgraded from 9.10 to 10.04? Old scripts were replaced by links to new upstart system... without questions asked... 
 
If I make too many changes it might screw things up with updates and upgrades, so I am not sure if that's a good way to go...
 
The new system is probably not bad, but still requires a lot trimming it seems... both in the init scripts and maybe also in the upstart manager itself...
 
Changing in the new scripts might be an idea, provided i find some decent documentation for the new system... about in which ways tests can be done in the start / stop section... I only found out there is a new upstart system when I noticed that things look different in /etc/init.d, but I have not looked into the details... for example what is the name of the upstart system package?
 
The little disadvantage with upgrading Ubuntu is that big changes are often made between distributions, and developers expect everybody to know how to find out about those changes... you upgrade and all goes well, but behind the scenes many things have changed, and during upgrade there is not much info about it too...
 
Another issue is the mix of old and new upstart... I assume that could also lead to some problems...
 
Apache for example was not started when things went wrong, and it is not using the new system... but it might depend on something else which uses the new system... but in old scripts it can not easily wait for some other process to start... it expects to be started in old priority way...
 
The old rc startup system is started using the new system, so if the new system fails all the old startup fails too... no wonder many processes were missing...

---

### Post by ian dobson on 2010-05-21
> **pezball said:**
> Ya I could probably use old script style...
 
The old rc startup system is started using the new system, so if the new system fails all the old startup fails too... no wonder many processes were missing...

I think you misunderstood me. Many startup processes have been converted to upstart, but not all. The ones that haven't been changed over still user the /etc/init.d scripting system. So if you get rid of all the upstart scripts execept for afew of the really important ones (mount,mount-all,networking etc) you can start the remaining scripts using the upstart "rc" script that emulates the old way with rcX.d

Regards
Ian Dobson

---

### Post by pezball on 2010-05-21
No I did not misunderstand you.
 
 
I only point out that when apache and other processes which use **old** system do not start, it might be a side effect of problems with the **new **system, cos they rely on old start priority system, and they do not care much about which processes have already been started with the new system.
They have no easy way to determine if their requirements have been met, since they only rely on that other processes start in a certain priorty order, which the new system does not obey.
 
An example... let's say that process A has priority 8 with old system and process B has priority 7... meaning, that B should always start before A... now with new system for B, it can start at any time, including after A, cos A does not have to wait for B at priority 7. That can give problems if A depends on B, unless the script for A has a loop which waits for B to run... it does not, cos the old priority system avoided such problems...
 
/etc/init/rc starts the old upstarts on certain runlevels, at any point in time, so it might now start up an old style process before it was allowed to do so with the old system, since old process startup priorities are not considered by the new... It simply starts whenever conditions are met and it has processor time to spare.
 
 
The new system will be better but only after all dependency chains for all the /etc/init files have been fully implemented, so that one process is guaranteed to wait until **all** of its dependencies are met... simply waiting for net-device-up for example is apparently no guarantee for success, mysql is one example... yet the start rule for mysql says net-device-up... it's not good if users need to manually change these files and add IFACE=eth0 etc, since most Ubuntu users are not computer wizards...  
 
 
in /etc/init.d are now links to the new system for processes which use that... the old startup files are not there... that is what I mean when I say that it might be issues when updates come... if i replace one of the links with an old style file... does it become overwritten by a link again after an update?

---

### Post by picbits on 2010-05-21
I'm feeling your pain.

I've been battling with upstart problems since 10.04 was released.

I have a headless server upstairs which will startup fine 9/10 times but the other time will refuse to run the apache, mail, myth and some other processes which screws me up if I've had to do a remote restart of it. I've spent weeks trying to sort out the upstart problems but not really got anywhere with it.

And this week ..........

I installed 10.04 64 Bit Desktop on an Acer Revo, put MythTv on it and all was fine. I've then put Lirc on it and wondered why it won't start up on boot - same problem. Jobs in init.d are not running, runlevel is reporting "unknown" and its screwing everything up.

If I run "telinit 2" then everything (I think) starts again until the next boot.

I've been using Ubuntu for 6 or 7 years now and have never had as many problems as I have with this upstart.

I can see the advantages of it but its literally taken up weeks of my time trying to get things sorted. I've got a server install to do at a clients next month but what OS do I use ? I certainly won't be using 10.04 as I can't rely on it :(

Rant over (for the moment !)

---

### Post by pezball on 2010-05-21
@picbits...
 
Ya it's sure not 100% ready yet, but it will be great once they have sorted out all dependencies... :) Especially people who have multicore processors will benefit if processes can start simultanously... saves lots time...
 
 
But as I said in the previous post, the old and new system do not interact so they start things independently of each other, and it can give random issues... the start scripts for the old system can no longer rely on startup priority for the processes which now use new system... they need to have loops which wait for their dependencies to be ready instead... so it's a lot editing to be done in those files...
 
runlevel "unknown" sounds like a very serious problem, since it means all the /etc/init.d scripts are never ever run... rc which starts those scripts, is started when the system reaches a normal runlevel... so unknown is a serious bug somewhere... it means the system is in a more or less void state... it's possible that I have same problem here when Apache and others refuse to start... Interesting info... but does not make me any wiser...

---

### Post by pezball on 2010-05-21
I am testing my server now, with small changes in /etc/init/mysql.conf and /etc/init/rc-sysinit.conf

In both files I have set 'net-device-up IFACE=eth0' so they wait for my real network card to be active... vital for mysql since I have it accessible from other pc's... and rc-sysinit handles the runlevel... and triggers conditions which allow the old start system to activate, so it might help with Apache problems...


I have done one reboot and all started perfectly... :P but will wait and see if it lasts for next reboot too...  at least a simple change and hopefully it works...

---

### Post by picbits on 2010-05-21
Pezball - I've been trying something as suggested on another thread with great success (so far !)

I was asked by Ian Dobson to remove ureadahead (apt-get remove ureadahead) and since doing this, my machine which was 50/50 on starting with services has been performing 100% correctly.

Not saying its the answer or solution but so far its working for me.

---

### Post by picbits on 2010-05-21
Oh and I tried the iface=eth0 fix earlier today and it didn't make any difference for my problem - fingers crossed you get yours sorted :)

---

### Post by pezball on 2010-05-21
Ya let's hope it works... at least for mysql it should make a difference, cos it's been complaining that it can not open up a network port... no wonder if the interface was not open in time...

About the rc-sysinit I have no clue but it's worth trying at least... mysql has had random start problems since i upgraded to 10.04, but the syslevel issue has only been occuring today for some reason...

Anyway... at least I have found something to try...

The reason they use **IFACE=lo** if any at all, is that u **can** run a server without any external connections... on localhost only... or u may use eth1... so they can probably not really specify the interface in the default config files...

---

### Post by ian dobson on 2010-05-22
Hi,

I found another thread with upstart problems, and there removing upstart seems to have solved the sometimes works/doesn't.

Do you have ureadahead installed? maybe try uninstalling it.


Regards
Ian Dobson

---

### Post by pezball on 2010-05-22
yes ureadahead is installed... i did not remove anything from default install...
 
I did reprofile it right now by removing pack files in /var/lib/ureadahead... just to see what difference that makes, and the boot took at least twice as long while reprofiling, so apparently ureadahead makes a lot difference on boot speed  :)
 
however, it should not be able to break the upstart dependency chain, (big bug if it does), so things should still boot in the correct order when it's active... provided that /etc/init files are set to wait for the correct events... the key to a successful boot is to make all the correct changes there... then it does not matter if ureadahead makes a 10 second or 10 minute boot...
 
I'll leave ureadahead for now, since I want to test my other changes a little more... reboot worked after I did thoes changes so I want to see if it still works on future reboots... so it was not just a lucky hit...

---

### Post by picbits on 2010-05-22
My fresh install server now fails around 1 in 10 times on the init scripts on bootup (ureadahead enabled). Its certainly got better for some reason.

My Revo (MythTv frontend) was failing 50% of the time but having removed ureadahead has not had a single problem.

---

### Post by pezball on 2010-05-23
ok cool... ya i guess ureadahead gives much tighter timing (and hence more likely problems) since the startup does not have to wait for the hard drive...
 
but the basic issue is still with the new startup which may not always keep a process waiting until all real life situation dependencies are fulfilled... if all the dependencies are not specified in /etc/init... especially true for network since default for many processes is that it waits for any network... including localhost which is much quicker than eth0... if u use eth0 or other adapter u might be better off adding that in all the upstart scripts to make sure it waits long enough...
 
I use DHCP from my router with a fixed ip set for the server... not fixed ip in the server itself... so means eth0 is not ready until it's received the ip number... in such situation adding IFACE=eth0 can make a lot difference for tasks which need it activated on start, since localhost is ready in milliseconds while ip number request can take seconds...

---

### Post by pezball on 2010-05-24
Have done a reboot today, for reasons not related to this issue, and all started perfectly... keeping fingers crossed... :)
 
Keeping this thread open for now... want to see that the good result is not a matter of good luck ;) before I consider it to be solved...
 
I consider the mysql start problem to be fully solved, so the issue now is with the undefined syslevel... if it's a problem for 1 in 100 reboots, it can be considered as almost not a problem... but perfection is the goal, since I want to just hit the power button on my server and not have to worry about it... especially since i only access it over ssh... no monitor and keyboard and other optional extras on the server...  ;)

---

### Post by MBianchi on 2010-06-07
Please do the following experiment.

	Boot
	Open an Xterm or equivalent.
	Issue the command
		runlevel

If you get back "unknown" you have an unreliable boot.
	See   [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

In particular, some/many things in  /etc/init.d/rc2.d  and  /etc/init/*.conf
are unlikely to have run.

As you will see from the bug report, "unreliable" means it
	seldom / sometimes / often / almost-always   fails
In my experience, different random hacks have different random results.

The one almost reliable fix is to comment out the line
		console output
in
	/etc/init/mountall.conf
	/etc/init/rc.conf
	/etc/init/rc-sysinit.conf
	/etc/init/ufw.conf

((
	NOTE there are directories  /etc/init  _AND_  /etc/init.d ,  both
	associated with getting the system booted, but _totally_ different in
	structure, architecture, functionality .........
	  Both need to work for a reliable boot.
))


See also my comments #54 and #73 in the bug report.
And see my Bug report  [https://bugs.launchpad.net/null/+bug/581291](https://bugs.launchpad.net/null/+bug/581291) .

---

