---
title: "Running a python script by cron at reboot?"
date: 2023-09-24
forum: Server Platforms
---

### Post by chortle on 2023-09-24
I used crontab -e to create an entry which should run a python script at reboot using [COLOR=#404040][FONT=monospace]@reboot

I used the full path of python3 followed by the full path of the python script.

The script should run 24/7. It looks monitors a block chain for events and sends a message to discord when the events take place. Output from the command line should go to a file. 

It doesn't seem to get started. 

Did I forget something, like having to enable cron? Where are logs which could show what is happening? [/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2023-09-24
You should instead use systemd service files. That is the way its being done. Cron won't die soon but it's not the ideal way to do what you are trying to.

---

### Post by MAFoElffen on 2023-09-24
Questions:
Did you include the shabang in your Python script? If so then you just enter the /full/path/to/PythonScript.py. You understand that right?


If you manually run your script as root or as your user, does it successfully send a message to discord?

Is your cron entry configured to run as that user? If not run by root, then you add a -u user_name option

Do you have a line in your Python script to send a syslog entry to the syslog?
```

import syslog

## Other code
syslog.syslog('My Reboot Python script executed!')

```
You can check that later via
```

grep 'syslog_module' /var/log/syslog

```
And as said by another user, I have created a /usr/lib/systemd/system/pre-reboot.service unit file o one of my machines that executes right before a reboot. It looks like this
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep . /usr/lib/systemd/system/pre-reboot.service
[Unit]
Description=Pre-Reboot Processes
DefaultDependencies=no
Before=reboot.target
# This works because it is installed in the target and will be
#   executed before the target state is entered
# Also consider kexec.target
[Service]
Type=oneshot
User=mafoelffen
Group=mafoelffen
ExecStart=/usr/bin/pre-reboot.sh
[Install]
WantedBy=reboot.target

```
The script has to have the permissions set to execute for both cron and systemd to be able to execute.

To get systemd to be able to use that unit file, then do
```

sudo systemctl enable pre-reboot.service
sudo systemctl start pre-reboot.service
sudo systemctl status pre-root.service

```

---

