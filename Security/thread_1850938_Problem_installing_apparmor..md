---
title: "Problem installing apparmor."
date: 2011-09-27
forum: Security
---

### Post by arroy_0209 on 2011-09-27
I am using ubuntu 10.04 LTS and mozilla firefox 3.6.22.

I have tried to install apparmor in complain mode but without success so far. The commands I have used sequentially are as follows. (The file usr.bin.firefox is present in the concerned dir)

sudo apparmor_status
cd /etc/apparmor.d
sudo complain firefox
```
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.

```sudo /etc/init.d/apparmor restart
 ```
* Reloading AppArmor  profiles                                                                                                    Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                    [ OK ]

```After this if I use: sudo apparmor_status, I am getting the following which shows that firefox is not in complain mode. 
```
apparmor module is loaded.
10 profiles are loaded.
10 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode :
   /usr/bin/evince (1999) 
   /usr/sbin/cupsd (1163) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```1. What went wrong?

Second, when I used sudo aa-logprof (even though firefox was not found to be in proper mode), I faced problems and have doubts about what I got. The response were
```

Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

Repository: http://apparmor.test.opensuse.org/backend/api

Would you like to enable access to the
profile repository?

(E)nable Repository / (D)isable Repository / Ask Me (L)ater

Repository: http://apparmor.test.opensuse.org/backend/api

Would you like to upload newly created and changed profiles to
      the profile repository?

(Y)es / (N)o / Ask Me (L)ater

Create New User?

(Y)es / [(N)o]
Username: my_name
Password:   

Save Configuration? 

[(Y)es] / (N)o

Login failure
 Please check username and password and try again.
RPC::XML::Client::send_request: HTTP server error: Not Found

```I was unaware that I would be asked these questions (like creation of new user, saving configuration etc, since these were not indicated from where I learned about installing apparmor.) 

2.Please tell me if I am supposed to give same username and password as I use to log in my desktop or create some other username and password. How many users should I create?(the prog is asking for one after another). I guess I ought to save configuration (or else please correct me). 

3. Why am I always getting the message "HTTP server not found"? my internet connection is ok. What else should I do now?  

4. Strangely, in the password field above, when I typed my password, it was visible. This is the first time I found that password was visible while typing. This never happens elsewhere. Is this usual with this program?

5. I have done an extremely stupid thing i.e., I gave my usual username and password in the fields above. Now how do I know if my computer had been attacked or not? (In my firewall configuration I have denied all inbound programs and services, like amule, deluge, ktorrent, nicotine, qbittorrent, trnasmission, ftp, http, imap, nfs, pop3, samba, smtp, ssh, vnc, zeroconf). The only service I allow outward is http, all other program and services are blocked. Still I think I should reinstall ubuntu.

---

### Post by arroy_0209 on 2011-09-27
[FONT=Garamond][SIZE=1]I have myself solved the problem. The command 
sudo aa-complain firefox 
is effective. This was followed by [FONT=monospace]
[/FONT]sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
[/SIZE][/FONT][FONT=Book Antiqua][SIZE=2][FONT=Garamond][SIZE=1]sudo aa-logprof is not giving anything significant from
 /var/log/messages. 

If you have any other suggestions, please share with me. 
I am worried because I revealed my password to 
external world. I have changed it promptly.[/SIZE][/FONT]
[/SIZE][/FONT]

---

