---
title: "Server auto-suspend?"
date: 2009-11-23
forum: Server Platforms
---

### Post by fkjensen on 2009-11-23
Hi guys,
 
Have been searching quite a bit and found many similar questions, but no answers so far...
 
I have a home server running ubuntu. With emphasis on **home**, it really doesn't need to be running all the time. Hence I would like it to suspend, when not in use, and wake up when needed (just like a commercial NAS or home server).
 
So far I can:
- Suspend with 'pm-suspend'.
- WOL from another computer.
- WOL from a squeezebox.
 
So far so good, but now I would like to:
(1) Auto-suspend when not in use.
(2) Wake up when I try to access my network drive from another computer (windows).
 
I am sure that (1) can be done, but how?
The desktop version of ubuntu has some kind of auto-suspend, right?
 
As for (2), I think, it could depend on my ethernet adaptor (wake on traffic to ip...?), but I not sure?
 
The system is an Intel D945GSEJT.
 
~Frank

---

### Post by inspiral on 2009-11-24
Hey

I think we are working toward the same thing:

[http://ubuntuforums.org/showthread.php?t=1335126](http://ubuntuforums.org/showthread.php?t=1335126)

My system wakes no problem when I pick up the Duet Remote but it doesn't when I access a Samba from my desktop but I'm still to properly investigate this.

Up till now I was assuming I could use the Gnome Power Management util to shut down the system when not is use but I've just found out it uses the screensaver util to trigger a suspend action and the problem with screensaver is that is only monitors user input ie mouse and keyboard not the activity of apps or shared folders.

The solution for us I think is some kind of util to watch a number of nominated apps and then perform an action after a certain timeout.

btw do you get me on the suspend then hibernate requirement ?

---

### Post by fkjensen on 2009-11-24
> **inspiral said:**
> 
I think we are working toward the same thing:
[http://ubuntuforums.org/showthread.php?t=1335126](http://ubuntuforums.org/showthread.php?t=1335126)

 
Yeah, and I have seen others with the same request, but no solution yet. A bit strange, I think. :?
 
> **inspiral said:**
> 
My system wakes no problem when I pick up the Duet Remote but it doesn't when I access a Samba from my desktop but I'm still to properly investigate this.

 
The Squeezebox sends a WOL to the last server it was connected to. I don't think windows will do this, when trying to connect to a computer on the network - but it should if it was up to me ;) 
 
> **inspiral said:**
> 
Up till now I was assuming I could use the Gnome Power Management util to shut down the system when not is use but I've just found out it uses the screensaver util to trigger a suspend action and the problem with screensaver is that is only monitors user input ie mouse and keyboard not the activity of apps or shared folders.

 
Damn, I was thinking; "when it can be done in the desktop version, of cause it can be done on a server", but I guess I was wrong. :|
 
> **inspiral said:**
> 
The solution for us I think is some kind of util to watch a number of nominated apps and then perform an action after a certain timeout.

 
Ok, who will write this? I'll be happy to test it :D
 
> **inspiral said:**
> 
btw do you get me on the suspend then hibernate requirement ?

 
Yeah, I get your idea, and I think there is hope if the hardware supports it (and we can get the other problems sorted).
Check out: [http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html](http://blog.dustinkirkland.com/2009/02/ubuntu-server-suspendhibernateresume.html)
and the script: [http://people.canonical.com/~apw/suspend-resume/test-suspend](http://people.canonical.com/~apw/suspend-resume/test-suspend)
It suspends the system and wakes it up after a fixed period of time. Hence you could make a script to
- suspend
- wake up after x min
- hibernate
- if woken up before x min -> break script
Like blazemore suggests in your other thread ([http://ubuntuforums.org/showthread.php?t=1335126](http://ubuntuforums.org/showthread.php?t=1335126))
But I know nothing about scripting - yet :P
 
~Frank

---

### Post by inspiral on 2009-11-26
>>Yeah, and I have seen others with the same request, but no solution yet. A bit strange, I think.

tbh I'm rather disappointed by the power management built into Ubuntu, what we're looking for seems such an obvious requirement for a home server

Anyway enough of the moaning and back to solving the problems.

To solve the WOL from a Windows box I:

[LIST]
[*]Downloaded [www.depicus.com/]("http://www.depicus.com/")**wake-on-lan**/**wake-on-lan**-**cmd**.aspx
[*]Put the full command line required into a batch file
[*]Added a shortcut to the Desktop
[*]Then dble click the shortcut, wait a bit and then access the network drive
[/LIST]
Not exactly elegant and manual(boo) but it works.

This leave the more fundamental issues:

[LIST]
[*]Monitoring the system is being accessed or serving tune via Squeezebox and then triggering an event if not
[LIST]
[*]This is the difficult one, you could ether monitor specific processes via Top or another similar tool or maybe monitor the use of the network port
[/LIST]
 
[*]Going to Hibernate from the Suspend state if the system remains un-accessed
[LIST]
[*]This is easier, the script you  point  out has the command line syntax required to Suspend for a period of time then to come back up and do something else: [http://people.canonical.com/~apw/sus...e/test-suspend]("http://people.canonical.com/%7Eapw/suspend-resume/test-suspend")
[*]Not sure how you get it to recognise if it came up of it's own accord or by WOL/pwr_button
[/LIST]
 
[/LIST]
I'm afraid on the scripting front I'm pretty hopeless, I gave if up a long time ago for just that reason :rolleyes:

I guess we could raise this subject on the Squeezebox forum but would've though this is fairly generic functionality.

Thoughts Frank/anyone ?

---

### Post by fkjensen on 2009-11-29
> **inspiral said:**
> 
Monitoring the system is being accessed or serving tune via Squeezebox and then triggering an event if not.
This is the difficult one, you could ether monitor specific processes via Top or another similar tool or maybe monitor the use of the network port

 
Yes this is indeed the tricky one. Any help would be greatly appreciated.
 
> **inspiral said:**
> 
Going to Hibernate from the Suspend state if the system remains un-accessed

 
I am sure, we can solve the suspend->hibernate problem, once we have solved the auto-suspend problem, so let's concentrate on the later.
 
~Frank

---

### Post by inspiral on 2009-11-30
I thought this tool might offer something that would allow us to use the Screensaver trigger as it can activate dynamically when a process starts:

[http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page](http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page)

But the problem is the Squeezbox is a sever that starts when you boot bot just when you start the tool meaning Caffeine triggers all the time never letting the system go to sleep unless you artificially kill the SB service.

Better look for something else I suppose....

---

### Post by fkjensen on 2009-12-09
<-Bump->
 
Anyone with some god ideas for auto-suspending a server when not in use?
 
~Frank

---

### Post by Muttley99 on 2009-12-09
Well, I'm looking to do exactly the same! I also have the same intel mobo for the server as you.
I use WOL-Packet manager sender for waking the server from windows 7, this works well.
I'll get back to you over the next few days.

---

### Post by fkjensen on 2009-12-10
I found this: [http://www.linuxquestions.org/questions/linux-server-73/auto-suspend-for-my-home-server-730037/#post3569957](http://www.linuxquestions.org/questions/linux-server-73/auto-suspend-for-my-home-server-730037/#post3569957)
 
I haven't tried it yet. I would like to know what it does, but I don't know anything about scripts, so it's going to take me a little while to decipher. :-k
 
~Frank

---

### Post by cmsj on 2009-12-10
perhaps powernap would be relevant to your interests.

---

### Post by fkjensen on 2009-12-11
Looks like that could be it! Thank you. :D
 
Can I use apt-get to install it? I can only find a tar.gz-file, and although I am sure that would work just fine, I am a total linux-newbie, and I have only used apt-get so far :-?
 
Is it included in 9.10? I am currently running 9.4.
 
~Frank

---

### Post by inspiral on 2009-12-11
This should do it:

sudo apt-get install powernap

Just installed it but not even read the man page yet so need to investigate the possibilities....

---

### Post by inspiral on 2009-12-11
Hmmmmm looks fairly broken to me:

 * Starting powernap                                                            Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get link status: Operation not permitted
Traceback (most recent call last):
  File "/usr/sbin/powernapd", line 37, in <module>
    logging.basicConfig(filename=LOG, format='%(asctime)s %(levelname)-8s %(message)s', datefmt='%Y-%m-%d_%H:%M:%S', level=logging.DEBUG,)
  File "/usr/lib/python2.6/logging/__init__.py", line 1394, in basicConfig
    hdlr = FileHandler(filename, mode)
  File "/usr/lib/python2.6/logging/__init__.py", line 819, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 838, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/var/log/powernap.log'
rory@ion:/etc/powernap$

Ooops spoke too soon sorry, you need to be root to restart the daemon

---

### Post by reddevil2064 on 2009-12-11
> **inspiral said:**
> Hmmmmm looks fairly broken to me:

 * Starting powernap                                                            Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get link status: Operation not permitted
Traceback (most recent call last):
  File "/usr/sbin/powernapd", line 37, in <module>
    logging.basicConfig(filename=LOG, format='%(asctime)s %(levelname)-8s %(message)s', datefmt='%Y-%m-%d_%H:%M:%S', level=logging.DEBUG,)
  File "/usr/lib/python2.6/logging/__init__.py", line 1394, in basicConfig
    hdlr = FileHandler(filename, mode)
  File "/usr/lib/python2.6/logging/__init__.py", line 819, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 838, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/var/log/powernap.log'
rory@ion:/etc/powernap$

Ooops spoke too soon sorry, you need to be root to restart the daemon
sudo away. I'm looking for similar functionality, keep us informed.

---

### Post by fkjensen on 2009-12-12
> **inspiral said:**
> This should do it:
 
sudo apt-get install powernap
 
Just installed it but not even read the man page yet so need to investigate the possibilities....
 
Do you run 9.10? I don't think it's part of 9.4, as I can't install it with apt-get.
 
~Frank

---

### Post by Muttley99 on 2009-12-12
I've just installed it on 9-10 and it does work ok for suspend but I've not tried the other functions.

---

### Post by fkjensen on 2009-12-12
How do I install it on 9.4?
 
~Frank

---

### Post by trundlenut on 2009-12-12
> **fkjensen said:**
> How do I install it on 9.4?
 
~Frank

Look at the launchpad pages for powernap, I think you have to add a PPA to your apt sources file, there are versions in the main repos for jaunty and karmic but for older versions you need to add the PPA.

---

### Post by Muttley99 on 2009-12-13
Progress up to now...

Powernap works at shutting down NAS server after 5 minutes of inactivity. To use powernap with pm-suspend, an 'action' file needs to be created and made executable in etc/powernap/
I've also created an icon on my kubuntu client which when clicked will wake the NAS, this also works well. Which means that starting the NAS from a client computer start is also easily accomplished by setting a script in KDE's autostart.

The problem I have right now is that sometimes the NAS wakes and doesn't fully load....

...I'll check the logs!

---

### Post by inspiral on 2009-12-14
> **Muttley99 said:**
> Progress up to now...

Powernap works at shutting down NAS server after 5 minutes of inactivity. 




Hi Muttley

What processes are you using to keep the NAS/server up (via the config file) ? I've been trying to find one that don't keep it up all the time, without much success unfortunately  :(

I want my box to provide Squeezebox streams plus files and print services to Windows clients both via Samba then sleep when not but the processes associated with these services never go away and hence powernap never powers down.

It's not much help to you but my box goes down and up from suspend and hibernate using WOL 100% reliably, my plan is to add a script to the action file to put the box in suspend for a period then take it down to hibernate if not used for a further period.

Cheers

---

### Post by inspiral on 2009-12-14
> **inspiral said:**
>  my plan is to add the commands to the action file to put the box in suspend for a period then take it down to hibernate if not used for a further period.


FYI this is the sequence I'm thinking of:

[LIST]
[*]zero wake alarm timer
[*]set wake alarm timer
[*]suspend
[*][I]box will then either be awoken via button, keyboard , WOL or alarm
[/I]
[*]check if woken early
[*]hibernate if false
[*]exit script if true
[/LIST]
 This will only work if the 'action' script continues to run once awoken from suspend.

At mo I know how to do everything apart from check to see if the box is woken early but think this'll probably be possible by comparing the current time against the alarm time.

I'm going to extract the alarm relevant cmds from the following script:

[http://people.canonical.com/%7Eapw/suspend-resume/test-suspend](http://people.canonical.com/%7Eapw/suspend-resume/test-suspend)

	# Request wakeup from the RTC or ACPI alarm timers.  Set the timeout
	# at 'now' + $timeout seconds.
	#
	ctl='/sys/class/rtc/rtc0/wakealarm'
	if [ -f "$ctl" ]; then
		time=`date '+%s' -d "+ $timeout seconds"`
		# Cancel any outstanding timers.
		echo "0" >"$ctl"
		# rtcN/wakealarm uses absolute time in seconds
		echo "$time" >"$ctl"
		return 0
	fi
	ctl='/proc/acpi/alarm'
	if [ -f "$ctl" ]; then
		echo `date '+%F %H:%M:%S' -d '+ '$timeout' seconds'` >"$ctl"
		return 0

Thanks to the original authors :D

I'm going to test all this manually first, I'll post the results once done.

---

### Post by Muttley99 on 2009-12-14
Inspiral,

I like your thinking! ;)
I'm playing with a basic action script right now which just pm-suspends after 10 minutes of inactivity; I've set smb,nfs,ssh as events for monitoring. I've just got my Kubuntu client to finally auto login to the server and suspend the NAS without passwords :D
With some more tweaking, this could work out well!
I'll get back to you this week with a final analysis.

---

### Post by inspiral on 2009-12-14
Weahay, I got all it all working, may not be especially elegant but it works, just add it to the end of the powernap action script:

#
LOGDIR='/etc/powernap'
LOGFILE="$LOGDIR/suspend_then_hibernate.log"
# Clear logfiles
cp /dev/null $LOGFILE
cp /dev/null $LOGFILE".debug"
exec 1>$LOGFILE
# Send debug output to debug log
exec 2>$LOGFILE".debug"

setup_wakeup_timer ()
{
        #Change this value to vary the time(in seconds) suspended
        suspend_timeout="60"

        #
        # Request wakeup from the RTC or ACPI alarm timers.  Set the timeout
        # at 'now' + $suspend_timeout seconds.
        #
        ctl='/sys/class/rtc/rtc0/wakealarm'
        if [ -f "$ctl" ]; then
                wake_time=`date '+%s' -d "+ $suspend_timeout seconds"`
                # Cancel any outstanding timers.
                echo "0" >"$ctl"
                # rtcN/wakealarm uses absolute time in seconds
                echo "$wake_time" >"$ctl"
                return 0
        fi
        ctl='/proc/acpi/alarm'
        if [ -f "$ctl" ]; then
                echo `date '+%F %H:%M:%S' -d '+ '$suspend_timeout' seconds'` >"$ctl"
                return 0
        fi

        echo "no method to awaken machine automatically" 1>&2
        exit 1
}

suspend_system ()
{
        echo "Nobody using me so I'll suspend for the time being"
        pm-suspend >> "$LOGFILE"
}

awoken_early ()
# Did I awake early ?
{
        grace="5"
        time_now=`date '+%s' #-d "+ $grace seconds"`

                if [ "$time_now" -le "$wake_time" ]; then
        echo "Awoken early so I won't hibernate as somebody wants me"
        exit 1
     fi
}

hibernate_system ()
{
        echo "Nobody wanted me in the suspend period so I'll hibernate"
        pm-hibernate >> "$LOGFILE"
}

# Run the scripts
setup_wakeup_timer
suspend_system
awoken_early
hibernate_system

---

### Post by inspiral on 2009-12-14
Oh dear the forum ate my indenting :(

---

### Post by Muttley99 on 2009-12-15
> **inspiral said:**
> Oh dear the forum ate my indenting :(

So, what exactly do you have working here? My script writing skills are minimal!

---

### Post by inspiral on 2009-12-15
When powernap decides the system is not being used to do the following via the action script:

[LIST]
[*]zero wake alarm timer
[*]set wake alarm timer to bring the system back up in x seconds
[*]suspend
[*][I]system will then either be awoken by the power button, keyboard , WOL or the alarm
[/I]
[*]check if woken early ie. anything other than the alarm
[*]if woken early exit action script and leave system up
[*]if not woken early hibernate
[*][I]system can then either be awoken by the power button, keyboard or WOL and when this happens powernap will start monitoring system use from scratch again
[/I]
[/LIST]

This allows the system to suspend for short periods and to be brought back up quickly when you need it but when left unused for longer periods go into hibernate which saves more power but takes a bit longer to come back up.

Make sense ?

How are you getting on identifying processes that show the system in being used ?

Cheers

---

### Post by Muttley99 on 2009-12-15
I just run 'ps' and picked off some running processes which I believe are required for my use; i.e. smbd,nfsd etc.
I've placed them in the powernap config file. This did work for samba and ssh and login but doesn't seem to work for nfsd. I need to check further.
Thanks for the info!

---

### Post by inspiral on 2009-12-15
Hmmm I tried adding just 'smbd' to the powernap config file and powernap just kept finding it regardless of being used or not by a remote(XP in my case) computer, I didn't try 'smb'.

Are your other computers running linux or some form of windows ? I thought that linux doesn't need Samba, I could be wrong though...What do you use nfsd for ?

btw do you use Squeezbox ?

---

### Post by inspiral on 2009-12-15
> **Muttley99 said:**
> I just run 'ps' and picked off some running processes which I believe are required for my use; i.e. smbd,nfsd etc.
I've placed them in the powernap config file. This did work for samba and ssh and login but doesn't seem to work for nfsd. I need to check further.
Thanks for the info!

Actually when you say 'seem to work' what do you mean, that powernap saw the processes in use and started the countdown to action once the processes stopped being used ? And did you systematically go through each access method ?

---

### Post by Muttley99 on 2009-12-15
I may give it a go tonight!
If i'm logged in to the server Powernap doesn't suspend - even without activity. I have a windows 7 netbook (hence the samba) and a kubuntu desktop (nfs). The desktop autofs mounts nfs shares on startup. The server doesn't suspend while connected to nfs BUT doesn't suspend after nfs disconnection either. 
I need to play around with the settings because last week I had it suspending five minutes after my kubuntu destop shutdown. I'm an idiot! should have saved the config file while at that state! #-o

---

### Post by Muttley99 on 2009-12-15
Got the config file working okay again, NAS suspends as normal after inactivity :D
Also, my screen corruption on startup seems to be fixed by adding 'pm-suspend --quirk-s3-mode' to the action file :D
I ssh to the NAS and checked it didn't suspend; this worked!
I have my Kubuntu desktop mounted nfs shares from the NAS, after adding 'nfsd' to the config file, NAS still suspended even when I accessed the shares from the client! 8-[
I don't understand why nfs shares are not preventing suspend! any ideas?

---

### Post by fkjensen on 2009-12-16
Muttley, which processes do you monitor?
 
~Frank

---

### Post by Muttley99 on 2009-12-17
I've just got smbd and ssh at the moment. I had nfsd in the list but this didn't work. I'm wondering if I place the path to nfsd in the config file it may work? I biggest problem I find here is there is little or no documentation for PowerNap available. Maybe I could try adding an alias to the config file and listing nfsd as normal? what do you think?

---

### Post by Muttley99 on 2009-12-17
looks like I need to specify the path:-

[HTML]Sample Configuration

In the Ubuntu Enterprise Cloud case, the configuration file, /etc/powernap/config, might look something like:

MONITORED_PROCESSES = [ "^/usr/bin/kvm " ]
ABSENT_SECONDS = 300
GRACE_SECONDS = 60

Thus, if no instance of kvm runs for 5 minutes, then the system will emit a warning, and powernap after a 1 minute grace period.[/HTML]

---

### Post by drejom on 2010-01-11
Hi,

I'm trying to set this up in a desktop system, but it seems not to be noticing my usb mouse/keystrokes and suspending mid-use. As far as i can tell, powernap is only monitoring /dev/ptmx, the pseudo-terminal. My mouse/keyboard are usb devices (/dev/usb/hiddev). Is there anyway to have it monitor other /dev files for activity or should this go as a feature request on launchpad?
Cheers
Drejom

---

### Post by JvdBosch on 2010-01-20
I've been following this topic as I too have build a NAS/FTP/Squeezebox server. I'm having trouble with setting up powernap, because of the monitored processes. I've set these processes:

```
MONITORED_PROCESSES = [ "smbd", "sshd: .*\[priv\]$" , "proftpd" , "webmin/miniserv.pl", "sabnzbdplus" ]
```But a lot of them remain active even though there's no activity. Samba for example.

```
[2010-01-20 10:03:43] Examining process table
[2010-01-20 10:03:43]   Looking for [smbd]
[2010-01-20 10:03:43]     Process found, reset absent time [0/300]
[2010-01-20 10:03:43]   Looking for [sshd: .*\[priv\]$]
[2010-01-20 10:03:43]     Process found, reset absent time [0/300]
[2010-01-20 10:03:43]   Looking for [proftpd]
[2010-01-20 10:03:43]     Process not found, increment absent time [954/300]
[2010-01-20 10:03:43]     Process absent for >= threshold, so mark absent
[2010-01-20 10:03:43]   Looking for [webmin/miniserv.pl]
[2010-01-20 10:03:43]     Process found, reset absent time [0/300]
[2010-01-20 10:03:43]   Looking for [sabnzbdplus]
[2010-01-20 10:03:43]     Process not found, increment absent time [954/300]
[2010-01-20 10:03:43]     Process absent for >= threshold, so mark absent

```How did you guys solve this? Can we have powernap check if a process is alive AND active?

---

### Post by nazz7707 on 2010-03-21
have you looked at the SBC SrvrPowerCtrl plugin? All suspend / hibernate / wol options are available and it works like a charm....

---

### Post by wanky on 2010-04-17
> **JvdBosch said:**
> I've been following this topic as I too have build a NAS/FTP/Squeezebox server. I'm having trouble with setting up powernap, because of the monitored processes. I've set these processes:

```
MONITORED_PROCESSES = [ "smbd", "sshd: .*\[priv\]$" , "proftpd" , "webmin/miniserv.pl", "sabnzbdplus" ]
```But a lot of them remain active even though there's no activity. Samba for example.

```
[2010-01-20 10:03:43] Examining process table
[2010-01-20 10:03:43]   Looking for [smbd]
[2010-01-20 10:03:43]     Process found, reset absent time [0/300]
[2010-01-20 10:03:43]   Looking for [sshd: .*\[priv\]$]
[2010-01-20 10:03:43]     Process found, reset absent time [0/300]
[2010-01-20 10:03:43]   Looking for [proftpd]
[2010-01-20 10:03:43]     Process not found, increment absent time [954/300]
[2010-01-20 10:03:43]     Process absent for >= threshold, so mark absent
[2010-01-20 10:03:43]   Looking for [webmin/miniserv.pl]
[2010-01-20 10:03:43]     Process found, reset absent time [0/300]
[2010-01-20 10:03:43]   Looking for [sabnzbdplus]
[2010-01-20 10:03:43]     Process not found, increment absent time [954/300]
[2010-01-20 10:03:43]     Process absent for >= threshold, so mark absent

```How did you guys solve this? Can we have powernap check if a process is alive AND active?

Having the same issue with powernap. Anybody have solved it yet?

Cheers
wanky

---

### Post by rodgull on 2010-04-19
All,

Not sure if anyone is still looking at this thread, but I have been looking through the powernap launchpad site and found a patch that Konrad Klimaszewski has added which adds MONITORED_IO_PROCESS, which checks that the process is actually active, as well as present.  

I believe this is what is needed (for me too!).  Reading through the actual patch, the examples are for samba, nfs and lighttpd.

see [https://bugs.launchpad.net/powernap/+bug/531773](https://bugs.launchpad.net/powernap/+bug/531773)

Now we just need Dustin to merge the changes....

Rod

---

### Post by rodgull on 2010-04-19
Also, powernap uses the command ```
ps -eo args
``` as the list to compare against the MONITORED_PROCESSES config list.

Hence running that command on your system will show how the processes appear to powernap. 

Enjoy,
Rod

---

### Post by wanky on 2010-04-19
> **rodgull said:**
> Also, powernap uses the command ```
ps -eo args
``` as the list to compare against the MONITORED_PROCESSES config list.

Hence running that command on your system will show how the processes appear to powernap. 

Enjoy,
Rod
Hi Rod,
thanks for the information. I have seen this patch too and added it to powernap. I didn't work for me. But I did it by editing the files and not automatically applying the patch (and I used the latest version of powernap. The patch was made for another rev, but I haven't seen any major changes).

Anyway, there seems to be a solution, so I'll wait :).

Cheers
wanky

---

### Post by parti02 on 2010-07-30
I tried also powernap_1.10-0ubuntu1 for maverik, same problem.
Any solutions?

Gruß
Parti

---

### Post by Muttley99 on 2010-07-30
I still use this for my NAS but it's a shame it doesn't quite manage what it promises! The documentation seems to be scarce too. It does work monitoring ssh, as I've set mine up to shut down the NAS 15 minutes after ssh logout.

---

### Post by mchlor on 2012-01-15
confirmed it doesn't work on oneric.  auto-suspend and wakeup = the great achillis heel of linux servers at least for home use.

---

### Post by Hamiltonwbp on 2012-01-16
Hi, 

I am pretty new to Ubuntu world! I am a mechanical engineer and trying to setup a NAS to share video and music file in my home. I setup the Ubuntu 11.10 on one of my old computers and get Samba server setup. I have 2 disks in my computer. Sda is the system where hosts Ubuntu and sdb is the one has all the video and audio files. 

Now I am thinking to save energy. Since I don't want the server to run all the time. My strategy is when I need the server , I will use WOL to wake it up. But if the server detects there is activities of the disks for more than 10 minutes. It will power off. 

So far the WOL part is working. But the power off part only partially works. The system turn if off no matter what I am doing. Even when I am accessing a large video file for the server, it is still power off. So it seems the Disk monitor function is not working at all. 

I am wondering is anyone here has the similar problem and would like to share the experience. 

Thanks

---

### Post by kaayman on 2013-01-05
Hello guys,

This is an old thread, but it seems I can share some useful information on powernap.
I use this utility on my NAS to shut it down when it is not used.

Not used means (in my opinion) no network access to samba shares/no active sabnzbd/no usage of squeezebox. I also monitor if xbmc is running.

The network related processes need to be configured in de the powernap config file(/etc/powernap/config. I have added my configuration file at the bottom of this post.

What is does is the following:
Check if network activity is detected for the following programs:
- proftpd
- squeezebox
- samba shares
- sabnzbdplus 

You have to configure these processes in the configuration section [IOMonitor] not [ProcessMonitor]. This last option will check if processes are started, and samba shares are always running/sleeping but present. You want to put them under IOMonitor to check if the processes really pass data over the network


[LIST]
[*]After 15 minutes of inactivity it will perform a powersave action.
[*]After 1 hour it will perform the action defined in the file /etc/powernap/action. In my case a shutdown.
[*]Go to powersave
[/LIST]
In will check for activity every 60 seconds. Note if you're monitoring  processes (using ProcessMonitor, you may want to decrease this value.  Otherwise it is possible that powernap will miss the process.

The following configuration file worked with ubuntu 11.10. Now i'm using it with 12.10. For some reason samba is reporting network usage, when it's not used. I adjusted the python script to work around this.

Here is my configuration:
> 
[powernap]
# This is the configuration file for PowerNap.
# See powernap(1) for more information.

# This file is Python syntax, and will be sourced by the powernap daemon
# on start. To enact changes to this configuration, restart the daemon.
# Example:
#   sudo service powernap restart

# The ACTION_METHOD variable determines what action to take.
# The possible actions are:
# 0 - powersave
# 1 - suspend
# 2 - hibernate
# 3 - poweroff
# 4 - best-effort
# The default mode of operation is powersave. This method will use the
# "pm-powersave" command and will execute hooks locate in "/etc/pm/power.d" and
# "/usr/lib/pm-utils/power.d".
# The best-effort method, witll first, it will try a user-defined script
# at "/etc/powernap/action", or suspend, hibernate, poweroff.
ACTION_METHOD = 0

# Number of seconds that all monitors must have no activity or must be absent.
# The default is an absence period of 30 seconds.
# Example:
#   ABSENT_SECONDS = 30
**ABSENT_SECONDS = 900**

# Grace period, after (ABSENT_SECONDS - GRACE_SECONDS) have elapsed with all of
# the Monitors with absent activity, the system will send a Wall message for an
# administrator to warn that the system will perform the "/usr/sbin/powernap"
# action in GRACE_SECONDS.
# The default grace period is 6 seconds.
# Example:
#   GRACE_SECONDS = 6
GRACE_SECONDS = 6

# The powernap daemon will wake every INTERVAL_SECONDS and check for activity
# to all of the monitors.  Lower values of INTERVAL_SECONDS will provide
# more detailed process monitoring but will consume more system resources.
# Higher values of INTERVAL_SECONDS will consume less system resources, but
# might miss activity that execute for less than INTERVAL_SECONDS.
# The minimum runtime of any monitor should not be less than INTERVAL_SECONDS.
# The default interval is 1 second.
# Example:
#   INTERVAL_SECONDS = 1
INTERVAL_SECONDS = 60

# The powernap daemon will issue a warning message to the console whenever it
# has entered into GRACE period. This warning message will warn the user that
# it is about to perform an ACTION.
# This warning message is done using the "wall" command, notifying all the
# users connected to a console.
# The default is set to 'yes' to WARN the user. It can be disabled by setting
# the option to 'n' or 'no', or can simply be commented.
# Example
#   WARN = y
#   WARN = n
WARN = y

# The powernap daemon logs errors to /var/log/powernap.err, and some basic
# information to /var/log/powernap.log.  To change the verbosity of this
# logging, set DEBUG to 0, 1, 2, or 3:
# The default debug level is 0.
#    DEBUG = 1
#    DEBUG = 2
DEBUG = 0

# The powernap daemon can watch for changes in the configuration file in
# /etc/powernap directory without having to restart it.
# The default value is n.
#    WATCH_CONFIG = y
#    WATCH_CONFIG = n
WATCH_CONFIG = n

# Kernel Modules that are to be disabled when running PowerNap on Powersave
# mode
#KERN_MODULES = btusb sco tfcomm bnep

# Network Services that are to be disabled when running PowerNap on
# PowerSave mode
#SERVICES = postgresql-8.4 apache2 ntp network-manager

############################################################################
####                        STAGE2 ACTION                               ####
############################################################################
[powernap-stage2]
# Number of seconds that all monitors must have no activity or must be absent
# while running in PowerSave mode to perform the STAGE2_ACTION_METHOD.
# The default value is to be disabled by default. If you wish to enable the
# Second Stage Action method, set the STAGE2_ABSENT_SECONDS and ensure that
# STAGE2_ACTION_METHOD is set correctly.
# Example:
#   STAGE2_ABSENT_SECONDS = 500
**STAGE2_ABSENT_SECONDS = 3600**

# The STAGE2_ACTION_METHOD variable determines what action should be taken
# after a period on inactivity while under PowerSave Mode (See ACTION_METHOD
# above).
# The possible actions are:
# 1 - suspend
# 2 - hibernate
# 3 - poweroff
# 4 - best-effort
# The default mode of operation is best-effort. This method will try to
# user-defined script  at "/etc/powernap/action", or suspend, hibernate,
# or poweroff the machine.
**STAGE2_ACTION_METHOD = 4**

############################################################################
####                          MONITORS                                  ####
############################################################################

# The [WoLMonitor] section lists all ports on which the WoL Monitor will be
# listening for WoL Packets for any of the network interfaces.
# Once a WoL Packet is received, the WoLMonitor will compare the data received
# with all the network interfaces (eth's) to determine wether it is destined
# for any of the network interfaces.
# The default is to monitor ports 7 and 9 for WoL data packets. It can also be
# set to any other port on which the machine is receiving WoL packets
# Example:
#  wol1052 = 1052
[WoLMonitor]
wol7 = 7
wol9 = 9

# The [ConsoleMonitor] section enables or disables  monitoring of activity
# in the Console (tty), also tracking activity from any locally connected
# mouse and keyboard (PS2 Only).
# The default is enabled, set to 'y'. It can be disabled by setting it to 'n'.
# Examples:
#  console = y
#  console = n
[ConsoleMonitor]
ptmx = y

# The [ProcessMonitor] section lists all the processes to Monitor by using
# regular expressions.
# Each item listed will be compared against the output of "ps -eo args".
# The default is to monitor /sbin/init, which should always be running.
# Examples:
#  mplayer = "mplayer "
#  sshd = "sshd: .*\[priv\]$"
#  kvm = "kvm "
[ProcessMonitor]
#init = "^/sbin/init"
**xbmc = "^/usr/lib/xbmc/xbmc.bin" **

# The [LoadMonitor] section defines the load threshold.  When the system load
# according to /proc/loadavg is above this value, then system will be deemed
# 'active' and will not powernap.  If the system is already powernapping, then
# the system will awake out of the powernap mode if the load raises above the
# threshold.
# If the threshold is set to "n" (which is default), threshold is automatically
# calculated to be the number of online processors, as determined by:
#   getconf _NPROCESSORS_ONLN
# Example:
#   threshold = 1.5
#   threshold = 9999
#   threshold = 0
#   threshold = n
[LoadMonitor]
threshold = n

# The [TCPMonitor] section lists all the TCP ports on which to watch for
# established connections using netstat(8). It supports both, single TCP
# as well as port ranges.
# There is no default TCP Monitor.
# Examples:
#  ssh = 22
#  http = 80
#  https = 443
#  other = 64500-65000
[TCPMonitor]
#ssh = 22

# The [UDPMonitor] section lists all the UDP ports on which to listen
# for data.
# Each item listed will BIND a UDP port and listen to any data. Keep
# in mind that this port will be bined and no other application will
# be able to use this port.
# There is no default UDP Monitor.
# Examples:
#  udp-1 = 1025
#  udp-2 = 2048
[UDPMonitor]
#udp-1025 = 1025

# The [IOMonitor] section lists all the processes to Monitor for IO
# activity. A regular expressions is used to find the processes PIDs, which
# are later used to monitor IO.
# There is no default IO Monitor.
# Examples:
#  kvm-io = "kvm"
#  mysqld-io = "mysql"
[IOMonitor]
#kvm-io = "kvm"
#mysqld-io = "mysql"
[B]squeezebox="/usr/sbin/squeezeboxserver"
sabnzbd="/usr/bin/sabnzbdplus"
proftpd="proftpd:"
samba = "smbd" [/B]

# The [InputMonitor] section lists the USB Input devices for which to track
# events. Currently, only two types of devices are supported, mouse and keyboard.
# Both InputMonitor's are enabled by default. In the case there are no USB
# devices connected, PowerNap will ignore these settings.
# To disable, set them to "n" or "no", or simply comment them.
# Examples:
#  keyboard = n
#  keyboard = y
[InputMonitor]
keyboard = y
mouse = y

# The [DiskMonitor] section lists the disk devices for which to track
# standby/sleep status.  If any of the devices are active/idle the
# system will be deemed 'active' and will not powernap. Generally useful
# for monitoring data drives (e.g. NAS), but will not typically work to
# monitor the root drive. Note also that this plugin only reacts to the
# state of the drive and does not modify the behavior of the drive
# directly. Therefore it only makes sense to monitor a drive that has
# already been configured to standby or sleep.  
# To disable checking specific drives, set them to "n" or "no",
# or simply comment them.
# Examples:
#  sda = y
#  sdb = n
[DiskMonitor]
#sda = y
 

---

### Post by inspiral on 2013-01-08
Thanks very much for that Kaayman :p

I never managed to get IOMonitor working even though I tried alsorts. I'll give your config a bash and see if it works.

>>Now i'm using it with 12.10. For some reason samba is reporting network  usage, when it's not used. I adjusted the python script to work around  this.

What did you change to get this working ?

Cheerio

---

### Post by jobarjo on 2013-07-10
Hi

I tried sleepd, and it works quite nice.
I simply set it up to suspend if the network activity goes below 20 packet/s
This threshold is useful because you may have a browser having tcp connections with very few packets.
It works very well.

But, I haven't found how to tell it to monitor video players or screensaver. (as video players disable screen saver)
powernap doesn't seem to have the network monitoring threshold feature.
Monitoring the server load doesn't seem very robust, as a browser can use cpu for animations for example.

If someone has a good solution for suspending a home server, not during video playback (player or flash player in browser...) that would be nice.

I thought about a monitoring process looking at the  screensaver. 
Computer can go to sleep if network activity is low and screen dpms is shutdown (monitoring xset q?)
sleepd can be controled with sleepctl on or off only.

---

### Post by wanky on 2013-07-11
Hi,

I still use [powernap]("https://launchpad.net/powernap") and it works very well for me. I monitor afpd (when no drive is mounted over the network, server goes to sleep). I haven't figured out yet, how to configure it for smbd though. But since I mainly use Macs within my network this is a working solution.
Before this approach I monitored ssh. So when I needed the server to "stay alive", I opened up a ssh-session. Closing it leaded to send the server to sleep.

Cheers
wanky

---

### Post by bellera on 2014-02-26
I started to use **powernap** some weeks ago and I have problems in same machines with USB keyboards & USB mouses.

Please see my comments at [https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/872109](https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/872109)

Any idea?

Josep Pujadas-Jubany

---

