---
title: "Xenial upgrade to systemd breaks multiple sshd configuration"
date: 2016-10-07
forum: Server Platforms
---

### Post by BrianB2 on 2016-10-07
I've recently upgraded two servers from 12.04 LTS to 16.04. Each server had a second openssh sshd process that I converted from initv to upstart several years ago. I was very annoyed to discover the second daemons were not running, and nothing I could do would start them.

I found the ancient post [https://ubuntuforums.org/showthread.php?t=1497376](https://ubuntuforums.org/showthread.php?t=1497376), which stubbornly and uselessly comes to the top of all my searches. I also found [https://access.redhat.com/solutions/1166283](https://access.redhat.com/solutions/1166283), which was MUCH more helpful. Unfortunately, after re-interpreting it for ubuntu, I still could't get the second instance to start.

systemctl status showed there was an important difference:

&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/etc/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2016-10-07 09:39:10 AEST; 9h ago

&#9679; ssh2.service - LSB: OpenBSD Secure Shell server
   Loaded: loaded (/etc/init.d/ssh2; bad; vendor preset: enabled)
   Active: active (exited) since Mon 2016-10-03 03:56:34 BST; 4 days ago

Although I had created a seemingly valid clone of the first sshd's systemd files, they were not being processed. Instead, systemd's rather limited initv emulation was failing to handle my original (unchanged) second instance configuration.

I recently rebooted the system following non-related maintenance activities and was astonished to discover the second sshd instance was running! I am not entirely sure why this happened, but I will post my changes to document what has worked for me. I will verify these steps by replicating the changes onto another server which currently refuses to run ssh2.

---

### Post by BrianB2 on 2016-10-08
Because my system had successfully run the second sshd under systemv and upstart, it already had */etc/ssh/sshd2_config* as a clone of *sshd_config*, but with a different **Port** and the extra **PidFile /var/run/sshd2.pid**.

When it ran under systemv, you can see from the systemctl messages (above) that systemd was picking up my cloned */etc/init.d/ssh2* file with the appropriate changes,

I had previously cloned */etc/default/ssh2* to include the change **SSHD_OPTS="-D -f /etc/ssh/sshd2_config"**. Unfortunately, systemd does not seem to use this vital environment variable under its systemv emulation mode. Nor did it use the exec line at the end of */etc/init.d/ssh2*, which carried a "belt and braces" override of the port and pid file.

Because my upstart /etc/init/ssh2.conf file had been similarly cloned and the second daemon was not starting, I believe others are correct when they say systemd ignores all your upstart customisation.

I decided to clone the working systemd files from ssh to create a native configuration for my ssh2.

---

### Post by BrianB2 on 2016-10-08
I learnt that */etc/systemd/system/sshd.service* is just a symlink created by the systemd enable command. The real configuration file is */lib/systemd/system/ssh.service*. ***Warning:*** the original is called **ssh.service** but the enabled symlink is called **sshd.service**!

I created a clone file */lib/systemd/system/ssh2.service* and made the following changes to the **Unit** section:
[INDENT]Description=OpenBSD Secure Shell second server
After=network.target auditd.service sshd.service
[/INDENT]
Note: I added the name of the first ssh to the After parameter so the two ssh daemons would be started sequentially.

.. and to the **Service** section:
[INDENT]EnvironmentFile=-/etc/default/ssh2
ExecStart=/usr/sbin/sshd -D  -f /etc/ssh/sshd2_config $SSHD_OPTS
[/INDENT]

.. and to the **Install** section:
[INDENT]Alias=sshd2.service[/INDENT]
Note: this defines the different name for the symlink file.

I also cloned */lib/systemd/system/ssh.socket* with appropriate changes for ssh2, bit systemctl tells me this systemd service is disabled at installation, so I think it dis not required.

---

### Post by BrianB2 on 2016-10-08
So I then try to start it and found this disappointing result:

brian@gamay:/lib/systemd/system$ sudo systemctl start ssh2
brian@gamay:/lib/systemd/system$ systemctl status ssh2
&#9679; ssh2.service - LSB: OpenBSD Secure Shell server
   Loaded: loaded (/etc/init.d/ssh2; bad; vendor preset: enabled)
   Active: active (exited) since Mon 2016-10-03 03:56:34 BST; 5 days ago

It appears as if none of my work has had the slightest effect!

I found a hint somewhere that systemd needs to be triggered to regenerate its internal tables with **sudo systemctl daemon-reload**.

Once I did this, **systemctl status ssh2** was as follows:
&#9679; ssh2.service - OpenBSD Secure Shell second server
   Loaded: loaded (/lib/systemd/system/ssh2.service; disabled; vendor preset: enabled)
   Active: active (exited) since Mon 2016-10-03 03:56:34 BST; 5 days ago

My new service was then recognised by systemd, but was currently disabled. I confirmed it with **systemctl is-enabled ssh2**

.. and fixed it with**sudo systemctl enable ssh2**, which created the */etc/systemd/system/sshd2.service* symlink.

Unfortunately, that didn't seem to be sufficient. It's status is now:
&#9679; ssh2.service - OpenBSD Secure Shell second server
   Loaded: loaded (/lib/systemd/system/ssh2.service; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2016-10-03 03:56:34 BST; 5 days ago

In slight desperation, I rebooted the server. The status became:
&#9679; ssh2.service - OpenBSD Secure Shell second server
   Loaded: loaded (/lib/systemd/system/ssh2.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2016-10-08 11:43:15 BST; 1min 26s ago
 Main PID: 3476 (sshd)
    Tasks: 1

Job done, but not 100% understood!

HTH

---

