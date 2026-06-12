---
title: "Clock in UTC format in Unity."
date: 2016-09-17
forum: Ubuntu Development Version
---

### Post by Zergy on 2016-09-17
Hello,

I updated my PC to Ubuntu 16.10 some days ago, but since, the clock is only show in UTC format in GUI.

[LIST][*]The PC don't have any dual boot, the EUFI clock use UTC time.
[*][The date command show the right time, with timezone (UTC+1) and daylight saving time.]("http://zergy.zergy.net/Images/DateUbuntu1610.png")
[*]I noticed it's possible to show hour from other place in date & time setting, but it doesn't change the default clock.[/LIST]
Maybe future update will resolve the problem…
If some of you have some ideas.

Thank you.

---

### Post by ajgreeny on 2016-09-17
What timezone is the computer set to?

---

### Post by Zergy on 2016-09-18
It set for UTC+1 (offset of 2 hours with UTC time du to daylight saving.)
If think it's just a problem with the clock applet as the date command return the correct time.

---

### Post by PaulW2U on 2016-09-18
> **Zergy said:**
> It set for UTC+1 (offset of 2 hours with UTC time du to daylight saving.)
If think it's just a problem with the clock applet as the date command return the correct time.
I'm not seeing a problem on a freshly installed Ubuntu which completely wiped all previous settings. I'm on UTC+1 here and the clock displays correctly. 

If I click on the map in "Time & Date Settings" and change my location then the time changes immediately to show the correct local time in that location.

Do you see this problem if you log in as another user or into the Guest Session?

---

### Post by Zergy on 2016-09-18
I tried by creating another user by the problem remain, maybe a problem occurred during the update process.
When I go in Date & Time Settings, timezone change don't seems to be saved.
I think I will go for a fresh install if future updates doesn't solve it.

---

### Post by VMC on 2016-09-18
> **Zergy said:**
> Hello,

I updated my PC to Ubuntu 16.10 some days ago, but since, the clock is only show in UTC format in GUI.

[LIST]
[*]The PC don't have any dual boot, the EUFI clock use UTC time.
[*][The date command show the right time, with timezone (UTC+1) and daylight saving time.]("http://zergy.zergy.net/Images/DateUbuntu1610.png")
[*]I noticed it's possible to show hour from other place in date & time setting, but it doesn't change the default clock.
[/LIST]
Maybe future update will resolve the problem…
If some of you have some ideas.

Thank you.
What does the command ' **timedatectl**' show.

---

### Post by TheCosmicFrog on 2016-10-17
This same issue is affecting me since updating to Ubuntu 16.10. The **date** command returns the correct date/time (UTC+1), but the clock applet continues to display UTC time. Choosing my location in the **Time & Date** screen doesn't get saved.

In my case, running **datetimectl** with no arguments just stalls and never returns.

This was a 16.04 -> 16.10 dist-upgrade. OP, let me know if you have any luck with a clean install.

---

### Post by WamBamBoozle on 2016-10-24
I'm hitting this too. timedatectl polls for a minute or so, then indicates status:

```
root@zzz:/# timedatectl status
Failed to query server: Connection timed out
```

---

### Post by grb19 on 2016-10-25
Hi,
I had the same error and managed to fix it. These two threads actually brought me to a solution:
[https://bbs.archlinux.org/viewtopic.php?id=164974](https://bbs.archlinux.org/viewtopic.php?id=164974)
[https://www.reddit.com/r/linuxquestions/comments/4vln5o/cant_start_systemdtimesyncdservice/](https://www.reddit.com/r/linuxquestions/comments/4vln5o/cant_start_systemdtimesyncdservice/)

It seems, that the service systemd-timedated fails to start, in the new ubuntu 16.10 version. 
You can check that with 

sudo service systemd-timedated status

if it says something like "Failed to start Time & Date Service.", then this solution might work for you.

For me a temporary workaround can be found by commenting out the line ProtectHome=yes in 
/lib/systemd/system/systemd-timedated.service

This error seems to happen, if for some reason /home actually is a symlink to somewhere else.

---

### Post by zika on 2016-10-25
SystemD... Not UpStart...
```
:~$ sudo systemctl status systemd-timedated.service 
&#9679; systemd-timedated.service - Time & Date Service
   Loaded: loaded (/lib/systemd/system/systemd-timedated.service; static; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:systemd-timedated.service(8)
           man:localtime(5)
           [http://www.freedesktop.org/wiki/Software/systemd/timedated](http://www.freedesktop.org/wiki/Software/systemd/timedated)
:~$ sudo systemctl enable systemd-timedated.service 
The unit files have no installation config (WantedBy, RequiredBy, Also, Alias
settings in the [Install] section, and DefaultInstance for template units).
This means they are not meant to be enabled using systemctl.
Possible reasons for having this kind of units are:
1) A unit may be statically enabled by being symlinked from another unit's
   .wants/ or .requires/ directory.
2) A unit's purpose may be to act as a helper for some other unit which has
   a requirement dependency on it.
3) A unit may be started when needed via activation (socket, path, timer,
   D-Bus, udev, scripted systemctl call, ...).
4) In case of template units, the unit is meant to be enabled with some
   instance name specified.
:~$ sudo systemctl start systemd-timedated.service                    
:~$ sudo systemctl status systemd-timedated.service 
&#9679; systemd-timedated.service - Time & Date Service                               
   Loaded: loaded (/lib/systemd/system/systemd-timedated.service; static; vendor preset: enabled)                                                                                                                                                                                
   Active: active (running) since Tue 2016-10-25 18:52:56 CEST; 13s ago                                                                                                                                                                                                          
     Docs: man:systemd-timedated.service(8)                                                                                                                                                                                                                                      
           man:localtime(5)                                                                                                                                                                                                                                                      
           [http://www.freedesktop.org/wiki/Software/systemd/timedated](http://www.freedesktop.org/wiki/Software/systemd/timedated)                                                                                                                                                                                                            
 Main PID: 8543 (systemd-timedat)                                                                                                                                                                                                                                                
      CPU: 17ms                                                                                                                                                                                                                                                                  
   CGroup: /system.slice/systemd-timedated.service                                                                                                                                                                                                                               
           &#9492;&#9472;8543 /lib/systemd/systemd-timedated                                                                                                                                                                                                                                 
                                                                                                                                                                                                                                                                                 
okt 25 18:52:56 _..._ systemd[1]: Starting Time & Date Service...                                                                                                                                                                                                                 
okt 25 18:52:56 _..._ systemd[1]: Started Time & Date Service. 
```No changes made in aforementioned file at the time of output given above...

---

### Post by grb19 on 2016-11-14
ok, maybe I didn't explain it extensively:

original state: (even after restarting systemd-timesyncd.service)

```
systemctl status systemd-timesyncd.service[COLOR=#ff0000]&#9679;[/COLOR] systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: [COLOR=#ff0000]failed[/COLOR] (Result: start-limit-hit) since Mo 2016-11-14 12:40:48 CET; 46s ago
     Docs: man:systemd-timesyncd.service(8)
  Process: 5690 ExecStart=/lib/systemd/systemd-timesyncd [COLOR=#ff0000](code=exited, status=226/NAMESPACE)[/COLOR]
 Main PID: 5690 (code=exited, status=226/NAMESPACE)


Nov 14 12:40:48 pcname systemd[1]: [COLOR=#ff0000]Failed to start Network Time Synchronization.[/COLOR]
Nov 14 12:40:48 pcname systemd[1]: systemd-timesyncd.service: Unit entered failed state.
Nov 14 12:40:48 pcname systemd[1]: systemd-timesyncd.service: Failed with result 'exit-code'.
Nov 14 12:40:48 pcname systemd[1]: systemd-timesyncd.service: Service has no hold-off time, scheduling restart.
Nov 14 12:40:48 pcname systemd[1]: Stopped Network Time Synchronization.
Nov 14 12:40:48 pcname systemd[1]: systemd-timesyncd.service: Start request repeated too quickly.
Nov 14 12:40:48 pcname systemd[1]: [COLOR=#ff0000]Failed to start Network Time Synchronization.[/COLOR]
Nov 14 12:40:48 pcname systemd[1]: systemd-timesyncd.service: Unit entered failed state.
Nov 14 12:40:48 pcname systemd[1]: systemd-timesyncd.service: Failed with result 'start-limit-hit'.

```

The important part here is, that it actually fails to start properly. In your case, it actually seems to run fine from the start. It just becomes inactive after a while.

[COLOR=#000000]As mentioned before: For me a temporary workaround can be found by commenting out the line ProtectHome=yes in [/COLOR]
[COLOR=#000000]/lib/systemd/system/systemd-timedated.service

Then it looks as follows:

[/COLOR]```
systemctl status systemd-timesyncd.service [COLOR=#00ff00]&#9679;[/COLOR] systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: [COLOR=#00ff00]active (running)[/COLOR] since Mo 2016-11-14 12:42:12 CET; 6min ago
     Docs: man:systemd-timesyncd.service(8)
 Main PID: 6215 (systemd-timesyn)
   Status: "Synchronized to time server **********."
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/systemd-timesyncd.service
           &#9492;&#9472;6215 /lib/systemd/systemd-timesyncd


Nov 14 12:42:12 pcname systemd[1]: Starting Network Time Synchronization...
Nov 14 12:42:12 pcname systemd[1]: Started Network Time Synchronization.

Nov 14 12:42:18 pcname systemd-timesyncd[6215]: Synchronized to time server *********.
```

Since this helped it seems, that systemd-timesyncd has some problems with symbolic links and network drives. We use a symbolic link from /home/ to /import/home, which is a network drive. Output of "mount":
nasls5:/srv/ls5/home on /import/home type nfs (rw,relatime,vers=3,rsize=8192,wsize=8192,namlen=255,hard,nolock,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=********,mountvers=3,mountport=42854,mountproto=udp,local_lock=all,addr=*******)


[COLOR=#000000]
[/COLOR]

---

### Post by Zergy on 2016-11-21
I finally upgraded to ubuntu 16.10 last week, thank you for your trick, it worked like a charm. :)
I also use a symlink for /home (/home -> /var/home), it seem that the "ProtectHome" option of systemd don't like that.

---

