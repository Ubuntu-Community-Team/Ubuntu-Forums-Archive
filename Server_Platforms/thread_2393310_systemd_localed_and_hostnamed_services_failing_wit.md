---
title: "systemd localed and hostnamed services failing with the same namespace errors"
date: 2018-06-01
forum: Server Platforms
---

### Post by like-last-yesterday-final on 2018-06-01
I am running an Ubuntu 16.04.4 LTS server instance on Amazon Web Services. Both the systemd-localed and systemd-hostnamed services are failing, and so are commands that use them.

The best errors I get are "[FONT=courier new]status=226/NAMESPACE[/FONT]" and "[FONT=courier new]Failed at step NAMESPACE spawning /lib/systemd/systemd-*: Invalid argument[/FONT]".

I've searched around the internet, and I cannot find anyone else having this exact problem. Similar problems seem to stem from missing hostname configuration files breaking hostnamed, though I wouldn't expect that to break localed as well. I've tried a few fixes I found like that, though some seemed inapplicable, and none worked. Other problems came from missing kernel modules, but I think I've got what's needed. I am using the official kernels provided by the default repositories baked into the ubuntu/images/hvm-ssd/ubuntu-xenial-16.04-amd64-server-20180126 AWS EC2 AMI.

See below for all the relevant information I could think of. Can anybody help me figure out what's going on here, or give me some next step troubleshooting tips?

```

= == = === = == = ==== = == = === = == =


root@sadbox:~# gdbus introspect --system --dest org.freedesktop.locale1 --object-path /org/freedesktop/locale1
Error: Timeout was reached


= == = === = == =


root@sadbox:~# systemctl status systemd-localed
&#9679; systemd-localed.service - Locale Service
   Loaded: loaded (/lib/systemd/system/systemd-localed.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-05-29 13:14:52 EDT; 24s ago
     Docs: man:systemd-localed.service(8)
           man:locale.conf(5)
           man:vconsole.conf(5)
           http://www.freedesktop.org/wiki/Software/systemd/localed
  Process: 15578 ExecStart=/lib/systemd/systemd-localed (code=exited, status=226/NAMESPACE)
 Main PID: 15578 (code=exited, status=226/NAMESPACE)


May 29 13:14:52 sadbox.example.com systemd[1]: Starting Locale Service...
May 29 13:14:52 sadbox.example.com systemd[1]: systemd-localed.service: Main process exited, code=exited, status=226/NAMESPACE
May 29 13:14:52 sadbox.example.com systemd[1]: Failed to start Locale Service.
May 29 13:14:52 sadbox.example.com systemd[1]: systemd-localed.service: Unit entered failed state.
May 29 13:14:52 sadbox.example.com systemd[1]: systemd-localed.service: Failed with result 'exit-code'.


= == =


root@sadbox:~# systemctl restart systemd-localed
Job for systemd-localed.service failed because the control process exited with error code. See "systemctl status systemd-localed.service" and "journalctl -xe" for details.


= == = === = == =


root@sadbox:~# journalctl -xe
May 29 13:15:35 sadbox.example.com systemd[1]: Stopped Locale Service.
-- Subject: Unit systemd-localed.service has finished shutting down
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-localed.service has finished shutting down.
May 29 13:15:35 sadbox.example.com systemd[1]: Starting Locale Service...
-- Subject: Unit systemd-localed.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-localed.service has begun starting up.
May 29 13:15:35 sadbox.example.com systemd[17016]: systemd-localed.service: Failed at step NAMESPACE spawning /lib/systemd/systemd-localed: Invalid argument
-- Subject: Process /lib/systemd/systemd-localed could not be executed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- The process /lib/systemd/systemd-localed could not be executed and failed.
-- 
-- The error number returned by this process is 22.
May 29 13:15:35 sadbox.example.com systemd[1]: systemd-localed.service: Main process exited, code=exited, status=226/NAMESPACE
May 29 13:15:35 sadbox.example.com systemd[1]: Failed to start Locale Service.
-- Subject: Unit systemd-localed.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-localed.service has failed.
-- 
-- The result is failed.
May 29 13:15:35 sadbox.example.com audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=systemd-localed comm="systemd" exe="/lib/systemd/systemd" hostname=? addr=? terminal=? res=failed'
May 29 13:15:35 sadbox.example.com systemd[1]: systemd-localed.service: Unit entered failed state.
May 29 13:15:35 sadbox.example.com systemd[1]: systemd-localed.service: Failed with result 'exit-code'.


= == = === = == = ==== = == = === = == =


root@sadbox:~# hostnamectl set-hostname sadbox.example.com
Could not set property: Connection timed out


= == =


root@sadbox:~# hostnamectl set-hostname sadbox.example.com
Could not set property: Failed to activate service 'org.freedesktop.hostname1': timed out


= == = === = == =


root@sadbox:~# systemctl status systemd-hostnamed
&#9679; systemd-hostnamed.service - Hostname Service
   Loaded: loaded (/lib/systemd/system/systemd-hostnamed.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-05-29 13:17:51 EDT; 1min 28s ago
     Docs: man:systemd-hostnamed.service(8)
           man:hostname(5)
           man:machine-info(5)
           http://www.freedesktop.org/wiki/Software/systemd/hostnamed
  Process: 20144 ExecStart=/lib/systemd/systemd-hostnamed (code=exited, status=226/NAMESPACE)
 Main PID: 20144 (code=exited, status=226/NAMESPACE)


May 29 13:17:51 sadbox.example.com systemd[1]: Starting Hostname Service...
May 29 13:17:51 sadbox.example.com systemd[1]: systemd-hostnamed.service: Main process exited, code=exited, status=226/NAMESPACE
May 29 13:17:51 sadbox.example.com systemd[1]: Failed to start Hostname Service.
May 29 13:17:51 sadbox.example.com systemd[1]: systemd-hostnamed.service: Unit entered failed state.
May 29 13:17:51 sadbox.example.com systemd[1]: systemd-hostnamed.service: Failed with result 'exit-code'.


= == =


root@sadbox:~# systemctl restart systemd-hostnamed
Job for systemd-hostnamed.service failed because the control process exited with error code. See "systemctl status systemd-hostnamed.service" and "journalctl -xe" for details.


= == = === = == =


root@sadbox:~# journalctl -xe
May 29 13:19:51 sadbox.example.com systemd[1]: Stopped Hostname Service.
-- Subject: Unit systemd-hostnamed.service has finished shutting down
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-hostnamed.service has finished shutting down.
May 29 13:19:51 sadbox.example.com systemd[1]: Starting Hostname Service...
-- Subject: Unit systemd-hostnamed.service has begun start-up
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-hostnamed.service has begun starting up.
May 29 13:19:51 sadbox.example.com systemd[23381]: systemd-hostnamed.service: Failed at step NAMESPACE spawning /lib/systemd/systemd-hostnamed: Invalid argument
-- Subject: Process /lib/systemd/systemd-hostnamed could not be executed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- The process /lib/systemd/systemd-hostnamed could not be executed and failed.
-- 
-- The error number returned by this process is 22.
May 29 13:19:51 sadbox.example.com systemd[1]: systemd-hostnamed.service: Main process exited, code=exited, status=226/NAMESPACE
May 29 13:19:51 sadbox.example.com systemd[1]: Failed to start Hostname Service.
-- Subject: Unit systemd-hostnamed.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit systemd-hostnamed.service has failed.
-- 
-- The result is failed.
May 29 13:19:51 sadbox.example.com audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=systemd-hostnamed comm="systemd" exe="/lib/systemd/systemd" hostname=? addr=? terminal=? res=failed'
May 29 13:19:51 sadbox.example.com systemd[1]: systemd-hostnamed.service: Unit entered failed state.
May 29 13:19:51 sadbox.example.com systemd[1]: systemd-hostnamed.service: Failed with result 'exit-code'.


= == = === = == = ==== = == = === = == =


root@sadbox:~# uname -a
Linux sadbox.example.com 4.4.0-1060-aws #69-Ubuntu SMP Sun May 20 13:42:07 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


= == =


root@sadbox:~# egrep 'NAMESPACES|NET_NS' /boot/config-4.4.0-1060-aws
CONFIG_NAMESPACES=y
CONFIG_NET_NS=y


= == = === = == = ==== = == = === = == =

```

---

### Post by arkaitzmugica on 2018-09-19
I've got the same issue with hostnamectl. Have you solved it?

---

### Post by like-last-yesterday-final on 2018-09-19
Good timing. Just yesterday, I discovered what's causing this problem. We're installing a product called Tableau Server for Linux, and it comes with FlexNet Publisher software licensing. Tableau runs FlexNet licensing as a service inside a user instance of systemd. When I stop this FlexNet service, the problem goes away. I will be confirming this on another box, and then opening a bug report with Tableau. In the meantime, I'll also be looking for workaround solutions.
```
tableau@sadbox:~$ systemctl --user stop fnplicenseservice_0.service
```

---

### Post by like-last-yesterday-final on 2018-12-10
I got a response from Tableau support. The suggested fix worked. Here is the response, edited for brevity:
> One of our development engineers used the below command to provide more context about the underlying error when trying to launch systemd-hostnamed while FNPLicenseService is running:
```

sudo strace -ff -o /tmp/strace.log -s 2048 -p 1 -e all & sudo systemctl start systemd-hostnamed.service

```
The output of this command looks like:
```

[1] 10904
strace: Process 1 attached
strace: Process 10916 attached
strace: Process 10923 attached
strace: Process 10924 attached
Job for systemd-hostnamed.service failed because the control process exited with error code. See "systemctl status systemd-hostnamed.service" and "journalctl -xe" for details.

```
In this case, the process of systemd-hostnamed is 10916, and log file /tmp/strace.log.10916 shows the below error message:
```

......
statfs("/dev/shm/FlexNetFs.34526", {f_type="TMPFS_MAGIC", f_bsize=4096, f_blocks=4118175, f_bfree=4118169, f_bavail=4118169, f_files=4118175, f_ffree=4118166, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=38}) = 0
mount(NULL, "/dev/shm/FlexNetFs.34526", NULL, MS_NOSUID|MS_NODEV|MS_REMOUNT|MS_BIND, NULL) = -1 EINVAL (Invalid argument)
close(3)                                = 0
......

```
(note the error message "invalid argument", which is also shown in the system log file).

The issue seems to be related to that version of systemd (229) and its mount/umount of the tmpfs /dev/shm/FlexNetFs* If the running a similar trace in your system proves to be the same type of error, we noted a workaround: 

1. Open the service unit file by running this command:
```

sudo vi /lib/systemd/system/systemd-hostnamed.service

```
2. Modify the file by changing "[FONT=courier new]PrivateDevices=yes[/FONT]" to "[FONT=courier new]PrivateDevices=no[/FONT]" and save the change.

3. Reload systemd by running this command:
```

sudo systemctl daemon-reload

```
Note: Conventionally we would use the "[FONT=courier new]systemctl edit systemd-hostnamed.service[/FONT]" command to put an override.conf file in /etc/systemd/system/systemd-hostnamed.service.d, but did not take effect in our testing.

I tried "[FONT=courier new]systemctl edit systemd-hostnamed.service[/FONT]" myself, and I put in this:
```

[Service]
PrivateDevices=no

```
And then I ran:
```

systemctl daemon-reload
systemctl restart systemd-hostnamed.service

```
And that worked for me. I think the "[FONT=courier new][Service][/FONT]" line is important.

I hope this helps other people in the future. BTW, I found PrivateDevices on [freedesktop.org]("https://www.freedesktop.org/software/systemd/man/systemd.exec.html"), and it says this:
> 
Note that the implementation of this setting might be impossible (for example if mount namespaces are not available), and the unit should be written in a way that does not solely rely on this setting for security.

So I think this a "nice to have" security feature, but shouldn't be depended on. Sounds safe to disable.

---

### Post by howefield on 2018-12-10
Moved to the "*Server Platforms*" forum.

---

