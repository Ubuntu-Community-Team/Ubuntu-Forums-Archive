---
title: "Ubuntu One doesn't seem to start without manual 'intervention'"
date: 2010-05-17
forum: Ubuntu One (CLOSED)
---

### Post by QwUo173Hy on 2010-05-17
In my Startup Applications, there is an Ubuntu One entry, with the command:

/bin/sh -c '[ -d "$HOME/Ubuntu One" ] && ubuntuone-launch'

But when I drop files into the Documents, which is marked for sync and does it perfectly, I actually need to start Ubuntu One from the MeMenu. Or I should say, it seems that I need to because I need to connect my computer from that menu each time.

Is it possible to have it work automatically or is this a known issue that's on the back burner for now?

Many thanks,
Jarlath

PS - In case it's a factor, I have a Startup entry run 'rm -drf /home/<me>/Ubuntu One' at startup.

---

### Post by joshuahoover on 2010-05-18
> **jarlath said:**
> In my Startup Applications, there is an Ubuntu One entry, with the command:

/bin/sh -c '[ -d "$HOME/Ubuntu One" ] && ubuntuone-launch'

But when I drop files into the Documents, which is marked for sync and does it perfectly, I actually need to start Ubuntu One from the MeMenu. Or I should say, it seems that I need to because I need to connect my computer from that menu each time.

Is it possible to have it work automatically or is this a known issue that's on the back burner for now?

Many thanks,
Jarlath

PS - In case it's a factor, I have a Startup entry run 'rm -drf /home/<me>/Ubuntu One' at startup.

Hi Jarlath,

Ubuntu One should auto-start and connect at startup in Ubuntu 10.04 LTS and with our beta PPA. After your computer boots up and a minute after being logged in, can you run the following command and let me know the output?

```
u1sdtool -s
```

Thank you,

Joshua

---

### Post by QwUo173Hy on 2010-05-18
> **joshuahoover said:**
> Hi Jarlath,

Ubuntu One should auto-start and connect at startup in Ubuntu 10.04 LTS and with our beta PPA. After your computer boots up and a minute after being logged in, can you run the following command and let me know the output?

```
u1sdtool -s
```Thank you,

Joshua

Hi Joshua,

I ran the command about 5 minutes after startup. I'll run it again and see if there's a difference 1 minute after. It took nearly 60 seconds for the command to return, but I could hear disk activity. Here is the output:

```
jarlath@jarlath-laptop:~$ u1sdtool -s
State: LOCAL_RESCAN
    connection: Not User Not Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

jarlath@jarlath-laptop:~$ 

```

<edit>I just checked 1 minute after startup and the results are the same. I have an internet connection at the time of running the command.

---

### Post by joshuahoover on 2010-05-20
> **jarlath said:**
> Hi Joshua,

I ran the command about 5 minutes after startup. I'll run it again and see if there's a difference 1 minute after. It took nearly 60 seconds for the command to return, but I could hear disk activity. Here is the output:

```
jarlath@jarlath-laptop:~$ u1sdtool -s
State: LOCAL_RESCAN
    connection: Not User Not Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

jarlath@jarlath-laptop:~$ 

```<edit>I just checked 1 minute after startup and the results are the same. I have an internet connection at the time of running the command.

Hi Jarlath,

OK, it's not connecting for some reason. In oder to better troubleshoot this, can you do the following?

[LIST=1]
[*]In a terminal session run:
sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py \
echo -e "[logging]\nlevel = DEBUG" >  ~/.config/ubuntuone/logging.conf
[*]Restart your computer and let it sit for a few minutes and then file a bug at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)
[*]Run this command, replacing ###### with the bug number from the step above: apport-collect -p ubuntuone-client ######
[/LIST]
Once you've done this, please let me know here the bug number so I can be sure it gets some immediate attention. :)

Thanks!

Joshua

---

### Post by QwUo173Hy on 2010-05-21
Joshua,

Thank you so much. [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584019](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584019)

Kind regards,
Jarlath

---

### Post by joshuahoover on 2010-05-24
> **jarlath said:**
> Joshua,

Thank you so much. [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584019](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/584019)

Kind regards,
Jarlath

I'm following up on this at the bug report in case other users have similar issues and see this thread, they can follow along there.

Thank you,

Joshua

---

