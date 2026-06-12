---
title: "Windows 10: Samba Server is visible, but cannot access it (error code: 0x80070035)"
date: 2022-04-03
forum: Server Platforms
---

### Post by harryparser on 2022-04-03
I first set up samba using Ubuntu's instructions: ([https://ubuntu.com/tutorials/install-and-configure-samba#1-overview](https://ubuntu.com/tutorials/install-and-configure-samba#1-overview))


My initial issue was that the network was not appearing so I used christgau's wsdd.py script following the instructions on Dev Answers: ([https://devanswers.co/discover-ubuntu-machines-samba-shares-windows-10-network/](https://devanswers.co/discover-ubuntu-machines-samba-shares-windows-10-network/)). In the process, I also allowed ports 5357/tcp and 3702 udp. Now the server shows up but when I click it, I don't get any sort of prompt for credentials and simply get the message:


"Windows cannot access server \\[server name] 
Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify and resolve network problems, click Diagnose"


I tried Orange Sherbet's solution from superuser: ([https://superuser.com/questions/1320007/one-particular-windows-10-pc-cant-access-samba-share-0x80070035-solved](https://superuser.com/questions/1320007/one-particular-windows-10-pc-cant-access-samba-share-0x80070035-solved)) but that didn't work. As for Pit's solution right after Orange's, I did not have a smb ports = 139 line in my smb.conf. Speaking of which, my smb.conf looks radically different from several of the ones I've seen posted on various forums. To create it, I simply followed the previously mentioned Ubuntu's Instruction. Perhaps the issue is within there? I'll post it if needed.

---

### Post by Morbius1 on 2022-04-03
> Speaking of which, my smb.conf looks radically different from several of the ones I've seen posted on various forums.
Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

And tell us what version of Ubuntu you are using.

---

### Post by SeijiSensei on 2022-04-03
Usually the "cannot access server" error is a name-resolution problem. Try using \\ip.addr.of.server\share (e.g, \\10.10.10.10\myshare) and see how that goes.

You can add hostnames to the "hosts" file in Windows: c:\windows\system32\drivers\etc\hosts

[https://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/](https://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/)

---

### Post by harryparser on 2022-04-03
Here is the output for test parm
```

# Global parameters
[global]
        client max protocol = SMB3
        client min protocol = SMB2
        log file = /var/log/samba/log.%m
        logging = file
        max log size = 1000
        ntlm auth = ntlmv1-permitted
        obey pam restrictions = Yes
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        server min protocol = SMB2
        server role = standalone server
        server string = %h server (Samba, Ubuntu)
        unix password sync = Yes
        idmap config * : backend = tdb




[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[sambashare]
        comment = Samba on Ubuntu
        path = /home/username/sambashare
        read only = No

```

I get no output for net usershare info --long 

And I am currently using Ubuntu 20.04.4 Live Server AMD 64

---

### Post by harryparser on 2022-04-03
```

[COLOR=#000000]Usually the "cannot access server" error is a name-resolution problem. Try using \\ip.addr.of.server\share (e.g, \\10.10.10.10\myshare) and see how that goes.[/COLOR]

```

This was how the Ubuntu installation instruction had us connect to the shared folder, but unfortunately I get the same result and same error code. 

```

[COLOR=#000000]You can add hostnames to the "hosts" file in Windows: c:\windows\system32\drivers\etc\hosts[/COLOR]

```

After trying this, I was actually able to enter my credentials and enter the server! Thanks! But I still get the same message but this time with an error code 0x80070043. Will try to look into it further but any help is appreciated.

---

### Post by Morbius1 on 2022-04-04
If you have to monkey around with hosts files on the Windows machine wsdd on the Ubuntu server isn't running or isn't running properly.

Run the following command to find it's status and post the output if it's not running:
```
sudo service wsdd status
```

I recreated your share definition and get the same error:
[ATTACH=CONFIG]290214[/ATTACH]
The reason I got that error is because there is no such path as /home/username/sambashare.

So my first stupid question of the day is do you really have a Linux user named "username"? Or did you just post "username" because you don't want us to know your real name.

And if you have the firewall enabled on the Ubuntu machine disable it for now please:
```
sudo ufw disable
```

---

### Post by rsteinmetz70112 on 2022-04-04
Mobius,

As far as I can tell wsdd is not part of the standard Ubuntu Samba install and as far as I can tell it's not in the repositories. I've never needed it for any of my installs.

---

### Post by Morbius1 on 2022-04-04
WSDD is not part of the standard install in Ubuntu 20.04 but the user implemented it himself:
> My initial issue was that the network was not appearing so I used christgau's wsdd.py script following the instructions on Dev Answers: ([https://devanswers.co/discover-ubunt...ws-10-network/](https://devanswers.co/discover-ubunt...ws-10-network/)).

If he got the files from github in the last week or so there may be an issue which is easy enough to fix. The wsdd status will tell us if it's not running.

WSDD will be in the repositories for Ubuntu 22.04 however so it's implementation will be just a package install: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1831441](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1831441)

As you can see I've waited a long time for this.

He could have used mDNS to connect to the Linux server but Ubuntu Server doesn't install avahi-daemon by default.

---

### Post by harryparser on 2022-04-05
Mobius

That was not a stupid question at all as you were correct in that 'username' was left as username. However, upon changing it to my actual username in the smb.config, I am no longer able to get inside the server to see the sambashare folder as I did after following SeijiSensei's instructions with hostnames, and am met with the error code x80070035. Upon changing it back, I am able to access the server again and see the sambashare folder but still not access it. I'm not really sure what's going on. 

WSDD is shown to be active and running. Here is the output:
> &#9679; wsdd.service - Web Services Dynamic Discovery host daemon     Loaded: loaded (/etc/systemd/system/wsdd.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2022-04-04 15:44:41 PDT; 10h ago
   Main PID: 1334 (python3)
      Tasks: 1 (limit: 38436)
     Memory: 14.5M
     CGroup: /system.slice/wsdd.service
             &#9492;&#9472;1334 python3 /usr/bin/wsdd --shortlog




As for disabling the firewall, still no difference. I recall running "sudo ufw allow samba" as part of the setup process. Would that have been sufficient?

---

### Post by harryparser on 2022-04-05
Just for further clarification:

On the windows device that I am using to attempt to the samba server,

1. I have tried both adding a username and password using windows credential manager or removing any credentials for the server altogether
2. I do not have Enable Insecure Guest Logons enabled within the Group Policy Editor Laman Workstation Folder
3. I have all instances of AllowInsecureGuestAuth set to 0 and RequireSecuritySignature set to 1 within my regedit
4. I do not have SMB 1.0/CIFS Client enabled within Windows Feature
5. Network Discovery is turned on for private but switched off for public , security password is set to 128 bit, password protected sharing is on (but have tried all combinations of settings)
I assumed I could avoid sacrificing security in steps 3 - 4 with the use of the wsdd script.

---

### Post by Morbius1 on 2022-04-05
Not sure what to make of all that either but I'm beginning to think this is a Linux permissions problem.

While I try to reproduce this can you make one adjustment to your share definition?

I'm assuming your share definition looks something like this now:
> [sambashare]
    comment = Samba on Ubuntu
    path = /home/harry/sambashare
    read only = no
    browsable = yes
Change it to this:
> [sambashare]
    comment = Samba on Ubuntu
    path = /home/harry/sambashare
    read only = no
    browsable = yes
    **[COLOR="#FF0000"]force user = harry[/COLOR]**
*[COLOR="#0000FF"]I also assume the /home/harry/sambashare folder is owned by the user "harry"[/COLOR]*

Then restart smbd:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2022-04-05
Duplicate post

---

### Post by Morbius1 on 2022-04-05
Things aren't looking good on my end.

I took a test box and made it's smb.conf match yours.
I already enabled WSDD manually as you have done.

I only made 2 changes to how you are set up:

I changed the sambashare path to my user: /home/tester/sambashare
I didn't make any changes to the internal plumbing of the Win10 box ( hosts file, enabling / disabling SMB1, etc..... ).

I changed the column setting in explorer to show me the "Discovery Method" so that I would know if I were using WSD in Win10 and that is exactly how I am discovering the Ubuntu server:
.
[ATTACH=CONFIG]290221[/ATTACH]
.
I can then expand the server to see it's shares:
[ATTACH=CONFIG]290227[/ATTACH]
.
I can then expand the share to add a file from Win10 Explorer to that Ubuntu share:
[ATTACH=CONFIG]290226[/ATTACH]

A long winded way of saying I cannot reproduce your symptom.

There's something else going on in your setup and I guess I'm not smart enough to see it yet.

---

### Post by harryparser on 2022-04-05
Mobius

Do not sell yourself short, your help has still been a valuable learning experience for me. As another approach, I tried typing run in my windows search bar, and then typed my server's ip address into it and received the following message:

> You Can&#8217;t Access This Shared Folder Because Your Organization&#8217;s Security Policies Block Unauthenticated Guest Access


To resolve this, I commented out the line 'map to guest = bad user' and am now asked for credentials. However, when I enter my credentials (for the server), I am told the username or password is incorrect. Any suggestions or intuitions here? If this is relevant, the username on the server is different from the username on my windows machine.

---

### Post by harryparser on 2022-04-05
I was able to solve this accursed issue once and for all. 

Within my smb.conf file,

After commenting out the line
>  map to guest = bad user 

I added the line,
> ntlm auth = true[FONT=var(--ff-mono)]

[/FONT]And now I'm able to access the sambashare folder with no issue.

---

### Post by #&amp;thj^% on 2022-04-05
Impressive, good job. (I had noticed that as well, but waiting for Morbis1)
and helpful to others searching.

---

