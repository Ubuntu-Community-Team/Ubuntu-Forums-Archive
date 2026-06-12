---
title: "Mouse pointer Problem with Vbox"
date: 2011-06-06
forum: Virtualisation
---

### Post by Jake.Debord on 2011-06-06
My mouse doesn't correspond with the mouse displayed on the vm.

I am using RDP, can anyone give any tips or help?

---

### Post by CharlesA on 2011-06-06
It does that until you install the guest additions. Royal pain in the butt when you are trying to do installs!

---

### Post by Jake.Debord on 2011-06-06
Oh, I assumed that was a part of the extension package...

-1 to vbox for not just packing it all together

:(

---

### Post by CharlesA on 2011-06-06
The guest additions are different for each type of OS, so they have to be installed separately.

Not that hard to do, but the mouse thing gets really annoying when you are trying to get something accomplished.

---

### Post by Jake.Debord on 2011-06-06
Ohhh, I see that makes more sense. Can I use the same ISO for every VM? I only see one ISO in my files

---

### Post by CharlesA on 2011-06-06
You can add different ISOs and whatnot, but you have to add it from the settings dialog box by clicking on the cd drive then selecting choose a virtual cd/dvd file after clicking on the icon that looks like a cd.

See attached. :)

---

### Post by Jake.Debord on 2011-06-06
I'm running on a headless though, so I'll need to find another Howto lol >.<

any suggestions?

---

### Post by CharlesA on 2011-06-06
I've been using [phpvirtualbox]("http://code.google.com/p/phpvirtualbox/") on my headless VM host.

You can also forward X over SSH to get to the GUI.

---

### Post by Jake.Debord on 2011-06-06
Thanks, I'll check it out!

---

### Post by CharlesA on 2011-06-06
Welcome. :)

---

### Post by Jake.Debord on 2011-06-06
Ok, got it going, but where do I edit creditials to login? The page asks for login information and I never ran across a place that specified those?

I feel so needy lol... I'm blaming it on being Monday

---

### Post by CharlesA on 2011-06-06
> **Jake.Debord said:**
> Ok, got it going, but where do I edit creditials to login? The page asks for login information and I never ran across a place that specified those?

I feel so needy lol... I'm blaming it on being Monday
Lol

Login to phpvirtualbox and go to file > preferences > users

---

### Post by Jake.Debord on 2011-06-07
I try to login and get a "Not Found" error then I click on details and it displays this code:

```
Exception Object
(
    [message:protected] => Not Found
    [string:Exception:private] => 
    [code:protected] => 64
    [file:protected] => /var/www/vbox/phpvirtualbox-4.0-6/lib/vboxconnector.php
    [line:protected] => 107
    [trace:Exception:private] => Array
        (
            [0] => Array
                (
                    [file] => /var/www/vbox/phpvirtualbox-4.0-6/lib/vboxconnector.php
                    [line] => 238
                    [function] => __vboxwebsrvConnect
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                        )

                )

            [1] => Array
                (
                    [file] => /var/www/vbox/phpvirtualbox-4.0-6/lib/auth/Builtin.php
                    [line] => 21
                    [function] => connect
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                        )

                )

            [2] => Array
                (
                    [file] => /var/www/vbox/phpvirtualbox-4.0-6/lib/ajax.php
                    [line] => 111
                    [function] => login
                    [class] => phpvbAuthBuiltin
                    [type] => ->
                    [args] => Array
                        (
                            [0] => admin
                            [1] => admin
                        )

                )

        )

    [previous:Exception:private] => 
)

```

---

### Post by Jake.Debord on 2011-06-07
Nvm my last post... I got ahead of myself and edited something in the config I shouldn't have. But, changed it back and now its working :P

---

### Post by Jake.Debord on 2011-06-07
I must have some curse on me against this running smoothly...

I run vboxwebsrv -b -p 18083 -H localhost
then can connect through phpvbox without a problem

BUT,
I'm guessing vboxwebsrv crashes from something because after something happens I can't connect with phpvbox until I go back and run the previous command I mentioned.

here is the error phpvbox displays:

```
An error occurred communicating with your vboxwebsrv. No more  requests will be sent by phpVirtualBox until the error is corrected and  this page is refreshed. The details of this connection error should be  displayed in a subsequent dialog box.

```

Do you ever get this? I'm probably just overlooking something again :(

---

### Post by CharlesA on 2011-06-07
Check this out here:
[http://code.google.com/p/phpvirtualbox/wiki/vboxwebServiceConfigLinux](http://code.google.com/p/phpvirtualbox/wiki/vboxwebServiceConfigLinux)

I use that instead of running the command manually.

Create a file: /etc/default/virtualbox
```
VBOXWEB_USER=username
```

Start the web server:

```
 sudo service vboxweb-service start
```

You should be able to connect now. :)

---

### Post by Jake.Debord on 2011-06-07
I have that file and its setup with my root username...


What port does vwebserver use as default? Because, I can't connect by running the command you just suggested, but if I run the command I mentioned with the port in the options it works... :(

I think your command would work but my config.php is setup to connect on localhost:18083 so thats why I have to specify. Or am I wrong?

---

### Post by CharlesA on 2011-06-07
> **Jake.Debord said:**
> 
I think your command would work but my config.php is setup to connect on localhost:18083 so thats why I have to specify. Or am I wrong?

I have the same thing listed in my config.php:

```
/* SOAP URL of vboxwebsrv (not phpVirtualBox's URL) */
var $location = 'http://127.0.0.1:18083/';

```

When you start the service, does it tell you anything?

It needs to be run as the same user that you are running virtualbox as.

---

### Post by Jake.Debord on 2011-06-07
Ugh, I got ahead of myself again and had a wrong username in the config.php 

changed it to match the VBOXWEB_USER

Now it logs in correctly, but doesn't show my VM. I'm assuming my VM is running as a different user also and I'll need to change it as well...

---

### Post by Jake.Debord on 2011-06-07
Nope, I had the VM setup under MY /home and not under the vboxuser /home

From now on, I will not be starting projects on a Monday ever, as I thoroughly mucked it up lol.

I'm just glad you helped me and I didn't have to scrap it!

---

### Post by CharlesA on 2011-06-07
You can always move ~/.VirtualBox and ~/VirtualBox VMs to the other home directory in order to get the VMs running under a different user. :)

---

### Post by Jake.Debord on 2011-06-07
Yea, that's what I did :)

---

### Post by Jake.Debord on 2011-06-07
Do you know of any common issues that would cause vboxweb-service to crash repeatedly? I run it, it crashes... and phpcirtualbox looses connection. Then I have to go in and stop vboxweb-service manually and start it back before phpvirtualbox will connect back again :(((

I can't seem to find anyone else with this problem?

---

### Post by CharlesA on 2011-06-07
I haven't heard of it before, to be honest.

Does the service start up ok after a reboot?

---

### Post by Jake.Debord on 2011-06-08
So far as I can tell it starts ok at boot. It may be a phpvirtualbox issue... It looses connection but vboxweb-service is still running. However, until I restart vboxweb-service phpvirtualbox will not reconnect.

---

### Post by CharlesA on 2011-06-08
Hmm. Check out the issues over at the phpvirtualbox site and if you don't see something similar, make a new post and see if anyone had run into the same problem.

---

### Post by Jake.Debord on 2011-06-09
I've posted a thread and we will see. *crosses fingers*

but I looked thru my auth.log and maybe you can tell me something if you look it it


```
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: Too many open files
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_unix.so
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_winbind.so): /lib/security/pam_winbind.so: cannot open shared object file: Too many open files
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_winbind.so
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_deny.so): /lib/security/pam_deny.so: cannot open shared object file: Too many open files
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_deny.so
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_permit.so): /lib/security/pam_permit.so: cannot open shared object file: Too many open files
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_permit.so
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_smbpass.so): /lib/security/pam_smbpass.so: cannot open shared object file: Too many open files
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_smbpass.so
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_ck_connector.so): /lib/security/pam_ck_connector.so: cannot open shared object file: Too many open files
Jun  9 14:56:19 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_ck_connector.so
Jun  9 14:56:21 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: Too many open files
Jun  9 14:56:21 DoraleeII vboxwebsrv: PAM adding faulty module: /lib/security/pam_unix.so
Jun  9 14:56:21 DoraleeII vboxwebsrv: PAM unable to dlopen(/lib/security/pam_winbind.so): /lib/security/pam_winbind.so: cannot open shared object file: Too many open files
```

---

### Post by CharlesA on 2011-06-09
I haven't run into that. What OS are you running for the host?

Run this:

```
ulimit -a
```

---

### Post by Jake.Debord on 2011-06-09
this is the output you requested:

```

$ ulimit -a
time(seconds)        unlimited
file(blocks)         unlimited
data(kbytes)         unlimited
stack(kbytes)        8192
coredump(blocks)     0
memory(kbytes)       unlimited
locked memory(kbytes) 64
process              unlimited
nofiles              1024
vmemory(kbytes)      unlimited
locks                unlimited

```

---

### Post by CharlesA on 2011-06-09
Hrm. What OS?

Mine says this:

```
charles@Thor:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

### Post by Jake.Debord on 2011-06-09
Sorry, meant to put that in there

I run Ubuntu 10.10 server headless

---

### Post by Jake.Debord on 2011-06-09
What file do I edit to change the user that virtualbox runs as???

I can't remember :( and I'm thinking it may have something to do with me switching from my user over to the actual vboxuser that i moved the vm over to earlier...

---

### Post by Jake.Debord on 2011-06-09
I think I may have pegged the origin of the problem:

```
Jun  9 15:54:15 DoraleeII sudo:  jdebord : TTY=pts/0 ; PWD=/home/jdebord ; USER=root ; COMMAND=/usr/sbin/service vboxweb-service start Jun  9 15:54:19 DoraleeII sshd[27050]: pam_unix(sshd:session): session closed for user jdebord Jun  9 15:54:24 DoraleeII vboxwebsrv: pam_smbpass(login:auth): Cannot access samba password database, not running as root.
```

---

### Post by Jake.Debord on 2011-06-09
Seems I may have fixed it with this command:

VBoxManage setproperty websrvauthlibrary null

Its been running for a few minutes and the logs are clear so far.
last time the log started showing lines 5 seconds after it started until it died 8 minutes later

*Crossing fingers*

---

### Post by CharlesA on 2011-06-09
Hmm. Hope it works. It's strange that starting the web server would cause complaints about Samba.

---

### Post by Jake.Debord on 2011-06-10
Well, and your suspicion is correct. Turns out it wasn't. That samba error was just coincidentally occurring the same time I was troubleshooting the vboxwebsrv. Turns out somehow a while back the winbind function was turned on and we are not on any kind of windows domain or with AD so it was complaining about being turned on but not setup... further inspection into the log file showed the authentication errors directly related to vbox that was the last post with log file i posted. By setting the  webservauthlibrary to null it fixed my authentication issues, but now there is no authentication on phpvirtualbox, if you go to it, it takes you right on in. I'm not thrilled about this, but until I can figure out where my usr/pass don't match and line up it will have to remain unathenticated :(

---

### Post by CharlesA on 2011-06-10
Glad you were able to (sorta) figure it out.

Did you already raise an issue over at the phpvirtualbox page?

---

### Post by Jake.Debord on 2011-06-10
Never made it that far. I made a topic on virtualbox page, but went home for the day before I could get to phpvbox... I may do it later today though, hopefully to help someone else in need.

---

### Post by CharlesA on 2011-06-10
Hope you are able to get it sorted out. :)

---

