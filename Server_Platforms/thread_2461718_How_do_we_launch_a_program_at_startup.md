---
title: "How do we launch a program at startup"
date: 2021-05-06
forum: Server Platforms
---

### Post by schmitta on 2021-05-06
I am running server 21.04 on a raspberry pi. I need to run a script at powerup. The machine now does a autologin but I am unable to get @reboot sh ~/rpi/startrpi.sh to run. I need a program to run all the time the system is up to display data to the user and to log the data. I need the data to display on the terminal which I believe runs on tty1. I have tried crontab, getty and other suggestions given on the internet and have worked several weeks with no luck. I can't use the raspberry pi Linux as they have crippled ability for a program to run at powerup for their own reasons. That is why I am on ubuntu server. I am running a RPi 3B. Any help would be greatly appreciated.

[COLOR=#000000][FONT=Verdana]I tried:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]@reboot sh ~/rpi/startrpi.sh[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]to get a script to execute[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]the script is:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]#!/bin/bash/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]cd ~/rpi[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]exec ./term[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]term is a C program that takes what comes in from a USB RS232 and prints it out on tty1[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]./term does work[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I am trying to display information to the user on tty1 after the system boots up[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]./term is to run continuously while the system is up[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]maybe I should write a deamon to do this?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]thank you for helping me.[/FONT][/COLOR]

---

### Post by scorp123 on 2021-05-06
> **schmitta said:**
>  maybe I should write a deamon to do this?

You could define your own system service?

Create a service definition in **/etc/systemd/system** ... you need to be superuser "root" to do this. So you need to use "sudo" + an editor, e.g.
```
sudo gedit /etc/systemd/system/serial-term.service
OR:
sudo vim /etc/systemd/system/serial-term.service
OR:
sudo nano /etc/systemd/system/serial-term.service
```
(... whichever editor works for you and you are comfortable with ...)


Content could be something like this:
```
[Unit]
Description=Serial-Terminal
Requires=network.target
After=systemd-user-sessions.service

[Service]
Type=simple
Restart=always
# Please edit the line below as needed.
# Use the full path to the program you wish to run
ExecStart=/full/path/to/the/term/program
# If you leave "User=" away then superuser "root" will be used.
# The user you use here MUST HAVE permission to run the program
# AND the permission to access / read / write to the serial device.
# Either create such a user or use "root".
User=mytermserviceuser

[Install]
WantedBy=multi-user.target
```

Once that's done you can tell "systemctl" to reload all its service definitions:
```
sudo systemctl daemon-reload
```

If there's no error message it means this was a success.

Now you can enable and start the service:
```
sudo systemctl enable serial-term.service
sudo systemctl start serial-term.service
```

You can check if it has worked by e.g.:
```
sudo systemctl status serial-term.service
```

You can investigate errors e.g. by:
```
sudo journalctl -xe
```

---

### Post by LHammonds on 2021-05-06
> **schmitta said:**
> I am running server 21.04 on a raspberry pi. I need to run a script at powerup. The machine now does a autologin but I am unable to get @reboot sh ~/rpi/startrpi.sh to run. I need a program to run all the time the system is up to display data to the user and to log the data. I need the data to display on the terminal which I believe runs on tty1. I have tried crontab, getty and other suggestions given on the internet and have worked several weeks with no luck. I can't use the raspberry pi Linux as they have crippled ability for a program to run at powerup for their own reasons. That is why I am on ubuntu server. I am running a RPi 3B. Any help would be greatly appreciated.

[COLOR=#000000][FONT=Verdana]I tried:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]@reboot sh ~/rpi/startrpi.sh[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]to get a script to execute[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]the script is:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]#!/bin/bash/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]cd ~/rpi[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]exec ./term[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]term is a C program that takes what comes in from a USB RS232 and prints it out on tty1[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]./term does work[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I am trying to display information to the user on tty1 after the system boots up[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]./term is to run continuously while the system is up[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]maybe I should write a deamon to do this?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]thank you for helping me.[/FONT][/COLOR]

The problem is in your script.  You should not reference relative paths...they can change...especially depending on which user account it is being run under.  There also should not be a trailing slash after "bash"

You did not mention which user is running the crontab schedule.  I will assume root.

```
crontab -e -u root
```

```

# Crontab SYNTAX:
#       __________ Minute (0-59)
#      / _________ Hour (0-23)
#     / /  _______ Day Of Month (1-31)
#    / /  /   ____ MONth (1-12)
#   / /  /   /   _ Day Of Week (0-7) (Sun = 0 or 7)
#  / /  /   /   /  -------------------------------------------------------------
# m h dom mon dow  command <arguments> > /dev/null 2>&1

@reboot [COLOR=#000000][FONT=Verdana]/root/rpi/startrpi.sh[/FONT][/COLOR]

```

/root/rpi/startrpi.sh
```

[COLOR=#000000][FONT=Verdana]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]cd /root/rpi[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]exec /root/rpi/term[/FONT][/COLOR]

```

NOTE: You probably do not need the "change directory" command in the script but if your term application is using relative paths too, it "might" be necessary.

---

### Post by schmitta on 2021-05-06
changed it to your way. did a sudo reboot on the raspberry pi and nothing came out even though the hardware before the rpi indicated data was being sent to it.

---

### Post by schmitta on 2021-05-06
did it your way and got the following:

```
ubuntu@ubuntu:~$ sudo systemctl daemon-reload
ubuntu@ubuntu:~$ sudo systemctl enable serial-term.service
Created symlink /etc/systemd/system/multi-user.target.wants/serial-term.service &#8594; /etc/systemd/system/serial-term.service.
ubuntu@ubuntu:~$ sudo systemctl start serial-term.service
ubuntu@ubuntu:~$ sudo systemctl status serial-term.service
&#9679; serial-term.service - Serial-Terminal
     Loaded: loaded (/etc/systemd/system/serial-term.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2021-05-07 01:14:46 UTC; 1min 3s ago
    Process: 2251 ExecStart=/home/ubuntu/rpi/term (code=exited, status=217/USER)
   Main PID: 2251 (code=exited, status=217/USER)


May 07 01:14:46 ubuntu systemd[1]: serial-term.service: Scheduled restart job, restart counter is at 5.
May 07 01:14:46 ubuntu systemd[1]: Stopped Serial-Terminal.
May 07 01:14:46 ubuntu systemd[1]: serial-term.service: Start request repeated too quickly.
May 07 01:14:46 ubuntu systemd[1]: serial-term.service: Failed with result 'exit-code'.
May 07 01:14:46 ubuntu systemd[1]: Failed to start Serial-Terminal.
ubuntu@ubuntu:~$

examined the journal and got:

ubuntu@ubuntu:~$ sudo journalctl -xe
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A stop job for unit serial-term.service has finished.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 1375 and the job result is done.
May 07 01:14:46 ubuntu systemd[1]: serial-term.service: Start request repeated too quickly.
May 07 01:14:46 ubuntu systemd[1]: serial-term.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; The unit serial-term.service has entered the 'failed' state with result 'exit-code'.
May 07 01:14:46 ubuntu systemd[1]: Failed to start Serial-Terminal.
&#9617;&#9617; Subject: A start job for unit serial-term.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit serial-term.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 1375 and the job result is failed.
May 07 01:15:49 ubuntu sudo[2252]:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/systemctl sta>
May 07 01:15:49 ubuntu sudo[2252]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=1000)
May 07 01:15:51 ubuntu sudo[2252]: pam_unix(sudo:session): session closed for user root
May 07 01:17:01 ubuntu CRON[2258]: pam_unix(cron:session): session opened for user root by (uid=0)
May 07 01:17:01 ubuntu CRON[2259]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 07 01:17:01 ubuntu CRON[2258]: pam_unix(cron:session): session closed for user root
May 07 01:18:42 ubuntu sudo[2265]:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/journalctl -xe
May 07 01:18:42 ubuntu sudo[2265]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=1000)
lines 4797-4825/4825 (END)

I did all the previous by ssh ubuntu@10.0.0.14

Looked at the crt output for the RPI and nothing was printing.

did a sudo reboot directly on the RPI and a red [failed] displayed on the crt during boot for the Serial-Terminal

nothing printed after the boot.

looked at the journalctl and got;

ubuntu@ubuntu:~$ sudo journalctl -xe
&#9617;&#9617;
&#9617;&#9617; The unit systemd-fsckd.service has successfully entered the 'dead' state.
May 07 01:23:36 ubuntu systemd[1]: systemd-hostnamed.service: Succeeded.
&#9617;&#9617; Subject: Unit succeeded
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; The unit systemd-hostnamed.service has successfully entered the 'dead' state.
May 07 01:27:18 ubuntu sshd[2040]: Accepted password for ubuntu from 10.0.0.119 port 53098 ssh2
May 07 01:27:18 ubuntu sshd[2040]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
May 07 01:27:18 ubuntu systemd-logind[1693]: New session 5 of user ubuntu.
&#9617;&#9617; Subject: A new session 5 has been created for user ubuntu
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; Documentation: sd-login(3)
&#9617;&#9617;
&#9617;&#9617; A new session with the ID 5 has been created for the user ubuntu.
&#9617;&#9617;
&#9617;&#9617; The leading process of the session is 2040.
May 07 01:27:18 ubuntu systemd[1]: Started Session 5 of user ubuntu.
&#9617;&#9617; Subject: A start job for unit session-5.scope has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit session-5.scope has finished successfully.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 1194.
May 07 01:27:40 ubuntu sudo[2118]:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/journalctl -xe
May 07 01:27:40 ubuntu sudo[2118]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=1000)
lines 4911-4939/4939 (END)

```

Thank you for your help -- still need help.

---

### Post by schmitta on 2021-05-06
```
rebooted daemons 
enabled and started serial-term.service
looked at status and got
ubuntu@ubuntu:~$ sudo systemctl status serial-term.service
&#9679; serial-term.service - Serial-Terminal
     Loaded: loaded (/etc/systemd/system/serial-term.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2021-05-07 01:37:12 UTC; 29s ago
    Process: 2215 ExecStart=/home/ubuntu/rpi/term (code=exited, status=217/USER)
   Main PID: 2215 (code=exited, status=217/USER)


May 07 01:37:12 ubuntu systemd[1]: serial-term.service: Scheduled restart job, restart counter is at 5.
May 07 01:37:12 ubuntu systemd[1]: Stopped Serial-Terminal.
May 07 01:37:12 ubuntu systemd[1]: serial-term.service: Start request repeated too quickly.
May 07 01:37:12 ubuntu systemd[1]: serial-term.service: Failed with result 'exit-code'.
May 07 01:37:12 ubuntu systemd[1]: Failed to start Serial-Terminal.
ubuntu@ubuntu:~$


looked at the journalctl and got

ubuntu@ubuntu:~$ sudo journalctl -xe
&#9617;&#9617;
&#9617;&#9617; The job identifier is 1807 and the job result is failed.
May 07 01:37:33 ubuntu systemd[1]: Starting Cleanup of Temporary Directories...
&#9617;&#9617; Subject: A start job for unit systemd-tmpfiles-clean.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-tmpfiles-clean.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 1894.
May 07 01:37:33 ubuntu systemd[1]: systemd-tmpfiles-clean.service: Succeeded.
&#9617;&#9617; Subject: Unit succeeded
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; The unit systemd-tmpfiles-clean.service has successfully entered the 'dead' state.
May 07 01:37:33 ubuntu systemd[1]: Finished Cleanup of Temporary Directories.
&#9617;&#9617; Subject: A start job for unit systemd-tmpfiles-clean.service has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-tmpfiles-clean.service has finished successfully.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 1894.
May 07 01:37:42 ubuntu sudo[2217]:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/systemctl sta>
May 07 01:37:42 ubuntu sudo[2217]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=1000)
May 07 01:37:44 ubuntu sudo[2217]: pam_unix(sudo:session): session closed for user root
May 07 01:40:07 ubuntu sudo[2226]:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/journalctl -xe
May 07 01:40:07 ubuntu sudo[2226]: pam_unix(sudo:session): session opened for user root by ubuntu(uid=1000)
lines 4871-4899/4899 (END)
```

note that this will be located 300 miles away so I will not be able to reboot the daemons or use systemctl

---

### Post by schmitta on 2021-05-06
I need to do two things. Display the data on the linux crt and log the data to disk. I have software that does this when I load and run it on the linux crt. The os is a ubuntu server so there is no gui; no terminal you can enter bash commands when the system stops loading on the crt and keyboard. What I need to do is execute a script on tty1 that runs my software. How do I do that? I am not an expert on linux. can the daemon execute a script ? What should I do to accomplish the above?

---

### Post by schmitta on 2021-05-07
I got it to work


I added my script to the end of ~/.bashrc and it executed it and printed on the terminal


i.e.


to /home/ubuntu/.bashrc I added at the end


/home/ubuntu/rpi/startrpi.sh


and the program started to execute. it also executes when I ssh in to the raspberry pi. I
can stop it by cntl+C and then get my work done. Praise GOD!!!!

---

