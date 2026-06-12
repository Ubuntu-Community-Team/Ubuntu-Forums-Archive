---
title: "How to fix FTP Credentials and Retrieving Directory Listing Issue"
date: 2018-01-10
forum: Security
---

### Post by serpentsoft on 2018-01-10
Hi all, I asked this question a lot yesterday and no help I cannot believe that professionals in all forums cannot solve that.
[B]
My System Info (I'm using AWS VPC, EC2, Classic Load Balancer)[/B]

[LIST]
[*] Ubuntu 16.04
[*] Virtualmin
[*] Using SSL through LetsEncrypt module
[*] ProFTPD module Main
[*] I Removed FirewallD and using IP Tables
[*] Main Domain is a WordPress
[/LIST]
I know there're a lot subjects for this issue and I read dozens of documentations but unfortunately nothing of those solutions working with me,  I installed virtualmin correctly (I think) I'll write the commands that I run to make sure it's ok setup 
[B]
Commands[/B]

```
sudo apt-get update 
sudo apt-get dist-upgrade -y
-> This message **A new version of /boot/grub/menu.lst is available but the version installed currently has been locally modified** appeared ONCE during setup and I chose **Install the package maintainer's version**
-> Reboot the system 
wget https://software.virtualmin.com/gpl/scripts/install.sh -O /root/virtualmin-install.sh

```

Then I create the first virtual server for my main domain and sub domains and request LetsEncrypt certificates and all working very well.

[B]
My Issue with FTP, WordPress and FileZilla[/B]

1- I tried to login in FileZilla with Host: [EMAIL="ftp@DOMAIN_NAME.com"]ftp@DOMAIN_NAME.com[/EMAIL] but I received the following messages...

    Status:    Initializing TLS...
    Status:    Verifying certificate...
    Status:    TLS connection established.
    Status:    Logged in
    Status:    Retrieving directory listing...
    Status:    Server sent passive reply with unroutable address. Using server address instead.
    Command:    MLSD
    Error:    Connection timed out after 20 seconds of inactivity
    Error:    Failed to retrieve directory listing

I made some searches and I see this command **modprobe ip_conntrack_ftp** in {https://www.virtualmin.com/documentation/web/faq#toc-ftp-service-isnt-working-Llnjz8K8} so I run it and reboot the system but the same messages appear ..

2- In my main domain I cannot add new plugin or media file and FTP credentials box appear too (I think it's related).
[B]
My solutions after some search
[/B]
1- I made some searches and I see this command {modprobe ipconntrackftp} in {[https://www.virtualmin.com/documentation/web/faq#toc-ftp-service-isnt-working-Llnjz8K8](https://www.virtualmin.com/documentation/web/faq#toc-ftp-service-isnt-working-Llnjz8K8)} so I make the following steps Then I Reboot the system.


[LIST]
[*]sudo modprobe ip_conntrack_ftp
[*]sudo modprobe ip_nat_ftp
[*]Add the line {ip_conntrack_ftp} to {/etc/modules}
[*]Add the line {ip_nat_ftp} to {/etc/modules}
[*]sudo reboot
[/LIST]

2- I made some changes to {/etc/proftpd/proftpd.conf} and {/etc/proftpd/modules.conf} .. These are my new settings

[B]/etc/proftpd/proftpd.conf
[/B]
```
Include /etc/proftpd/conf.d/
<Global>
PassivePorts 49152 49252
</Global>

```

[B]/etc/proftpd/modules.conf
[/B]
```

<VirtualHost 10.0.0.161>
ServerName MYDOMAIN.com
<Anonymous /home/MYDOMAIN/ftp>
User ftp
Group nogroup
UserAlias anonymous ftp
<Limit WRITE>
DenyAll
</Limit>
RequireValidShell off
</Anonymous>
</VirtualHost>

```

3- I removed all IP Tables from { **Virtualmin menu Webmin . Networking . Linux Firewall** **& Linux IPv6 Firewall** } and add those only under { Incoming packets (INPUT) - Only applies to packets addressed to this host}

```


[TABLE="class: table table-striped table-hover table-condensed dataTable no-footer, width: 1455"]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is UDP and destination port is domain[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is 20000[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is 10000[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is http[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is https[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is ftp-data[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is ftp[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is imaps[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is imap[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is pop3s[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is pop3[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is domain[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is submission[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer even, bgcolor: #feffff"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is smtp[/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[TD="class: text-center, width: 32, align: center"][/TD]
[/TR]
[TR="class: ui_checked_columns cursor-pointer odd, bgcolor: #F9F9F9"]
[TD="class: ui_checked_checkbox, width: 5"][/TD]
[TD="width: 30%"]Accept[/TD]
[TD]If protocol is TCP and destination port is ssh[/TD]
[/TR]
[/TABLE]

```


**The Result After 2 days of searching and 400 tabs opened** .. Nothing Changed the same message appear in FileZilla and I cannot add or upload plugin and media in my WordPress website.

[B]
Just determine which section in the server responsible for such issues because I cannot using my WordPress site so far,

 Thanks for your help.[/B]

---

### Post by TheFu on 2018-01-10
So, I don't use almost anything you listed above, but wanted to respond so you know someone is reading.

The technique to make these things work is to start simple, get it working, then make a backup and try the next thing.  That is important, especially when you are new.  New to Linux, new to a program, new to a service provider.  Start simple and add 1 thing at a time.

Be certain to check the log files for issues and monitor the system performance. Plus, I wouldn't leave FTP running all the time. Only enable it for the 2 minutes you need to update wordpress and I'd lock down where plain FTP can come from to just the IPs where the WP updates come.

That's all I got. Sorry.

---

### Post by HermanAB on 2018-01-14
"Status: Server sent passive reply with unroutable address. Using server address instead."

Network stack is called that for a reason - it is a stove pipe of dependencies.

Nothing will work if the network is configured wrong.

Futzing with ports and forwarding won't do anything useful if the IP addresses are bad.

Also bear in  mind that FTP is insecure and exposes the usernames and passwords.  Therefore, you should use FTP in Anonymous mode on selected public directories only.  Do not attempt to use FTP with authentication, since it is futile and completely breaks whatever security you had going.

---

