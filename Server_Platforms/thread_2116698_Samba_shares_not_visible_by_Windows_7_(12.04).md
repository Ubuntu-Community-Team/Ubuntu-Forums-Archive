---
title: "Samba shares not visible by Windows 7 (12.04)"
date: 2013-02-16
forum: Server Platforms
---

### Post by apkatt on 2013-02-16
Hi, I have just made a fresh install with 12.04LTS which comes with Samba 3.6.3. I have set up a number of shares using Webmin, it works just as it should and the fileserver (the netbios name) **show up in Finder on OS X machines**.

However, on Windows 7, the server does not show up under the network. I have spent the last two days going through possible solutions, one that seemed promising was the resolve order = bcast. This did not solve the problem however.

All computers are in the same workgroup and smbtree returns all computers, including the Windows 7 machines. All users are present on both UNIX and Samba. Security is by groups (only one group so far), and per folder. All folders are mode 770. The server IP is static with a DHCP enabled router in the network (dsl modem).

I feel that I have tried everything suggested by Google by now, anyone have any idea of what might be the problem?

```
[global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n$
        obey pam restrictions = yes
        force group = staff
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        netbios name = fileserver
        writeable = yes
        server string =
        path = /home
        unix password sync = yes
        workgroup = WORKGROUP
        os level = 20
        valid users = @sudo,@staff
        syslog = 0
        security = user
        usershare allow guests = yes
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        pam password change = yes

```

Example share

```
[PAM]
        create mode = 770
        path = /home/PAM
        directory mode = 770

[CORE]
        create mode = 770
        path = /home/CORE
        directory mode = 770


[MEDIA]
        create mode = 770
        path = /home/MEDIA
        directory mode = 770

```

---

### Post by PowerBarry43 on 2013-02-16
Hi

Try typing in the address bar in windows explorer:

\\<ip of server>

eg

\\192.168.1.50

then hit enter

Hope this helps!

Barry

---

### Post by darkod on 2013-02-17
Try avoiding setting up shares with Webmin. Use ssh. In fact, try not to use webmin at all. I have read somewhere that it's not in the repositories for a reason, it handles config files differently.

For example, your [global] section is extremely big. I don't know whether that's because of webmin, or you need all those options, but I'be never seen such a large section.

Try accessing the server by IP, not in Network.

Try setting up share through ssh and see if it can be detected and used.

---

### Post by apkatt on 2013-02-17
> **darkod said:**
> Try avoiding setting up shares with Webmin. Use ssh. In fact, try not to use webmin at all. I have read somewhere that it's not in the repositories for a reason, it handles config files differently.

For example, your [global] section is extremely big. I don't know whether that's because of webmin, or you need all those options, but I'be never seen such a large section.

Try accessing the server by IP, not in Network.

Try setting up share through ssh and see if it can be detected and used.

Just to clarify, it works fine mapping the shares in Windows 7 by simply inputting the IP of the Linux machine. The problem is that the server does not show up under the Network tab in Windows Explorer like it should as a SMB resource.

I will try to remove the force user and valid groups from global and see if that helps.

---

### Post by Jasoni on 2013-02-18
Make your samba server as a server for those names.
Add to global section of /etc/samba/smb.conf

[I]domain master = yes
[/I]*local master = yes*[I]
preferred master = yes[/I][I]
os level = 65[/I]
*wins support = yes*

Depending of the operating systems found in your local network, the most suitable for that will take care of the names.
In a windows world NT is the strongest.  7 and Xp are little bit weaker (in this case).
Os level number tells to the other computers how 'strong' it is. The better the number, it will will the lottery when they compete each other.

os level = 65 tells that it will win all the windows machines and your samba will come as your local name server in this case.
I guess there don't have to be nesseccary that domain master line in a conf file but maybe you could try and see.

---

### Post by apkatt on 2013-02-18
> **Jasoni said:**
> Make your samba server as a server for those names.
Add to global section of /etc/samba/smb.conf

[I]domain master = yes
[/I]*local master = yes*[I]
preferred master = yes[/I][I]
os level = 65[/I]
*wins support = yes*

Depending of the operating systems found in your local network, the most suitable for that will take care of the names.
In a windows world NT is the strongest.  7 and Xp are little bit weaker (in this case).
Os level number tells to the other computers how 'strong' it is. The better the number, it will will the lottery when they compete each other.

os level = 65 tells that it will win all the windows machines and your samba will come as your local name server in this case.
I guess there don't have to be nesseccary that domain master line in a conf file but maybe you could try and see.

Thanks, will try.

---

### Post by andrewhamming on 2013-03-03
Im having the exact same issue with the same setup. I just tried the above changes there was no change :(

Any other ideas?

Thanks Hammo

---

### Post by darkod on 2013-03-03
What same issue exactly? The OP said the shares work fine if accessed by IP but the server name doesn't appear in Network, etc. For me, that is not a huge deal.

Also, the OP has a large number of options in the [global] section of smb.conf as I pointed out in my post. Do you need so many options, or you want to do simple shares? For simple shares you only need few lines in smb.conf and I wouldn't use webmin, again, as I pointed out in my post.

---

### Post by andrewhamming on 2013-03-03
Sorry for not explaining in more detail.

My samba shares also work if I manually input the ip address or hostname of the file server.
I also have a large amount of options in global but that is to deal with the fact that my share is accessed by linux, windows and mac computers here at home. Basically its all our music, photo's and movies. Everyone needs full read/write access, hence so many options.

I do not use webmin its all done by console via ssh.

My mates come over for lan partys frequently and it would be nice if the shares showed up in there network places rather then me having to tell em all the ip/hostname. I use it to shares maps and stuff for csgo rather then us all dl them. I have to say ubuntu server runs csgo dedicated server quite well ;)

I know this is not a huge issue its just annoying that it doesn't show up. I have googled for a few hours to try and find solution but to no avail.
Also this smb.conf used to show shares in network places before I moved the server to the grannyflat and installed Ubuntu Server 12.04.

I can post my smb.conf and also dhcp.conf for you to have a boo peep at if your interested. I think it may be an error in my dhcp server config somewhere.

Thanks for taking the time to help people out too!!

Hammo

---

### Post by darkod on 2013-03-04
Unfortunately, I'm not a big expert for samba especially with complex permissions/shares.

But if you want RW open shares for all, it's very easy. I have my server set up at home with only few lines in smb.conf. I repeat, I have shares open for RW to all, no usernames and passwords are necessary.

You said in your home everyone needs full RW access which sounds like what I've got. I can post you screenshots from putty session (the server is headless of course) of my setup. Works fine from win7 and ubuntu.

---

### Post by koenn on 2013-03-04
That "shares showing up in Network Neighborhood" thinks is in fact rather complex. 
It used to be a simple NetBIOS feature in that file servers would broadcast their available shares to anyone who cared to listen. 
But NetBIOS is old en deprecated (even by Microsoft) so recent Windows versions (both servers and clients)  don't  default to it anymore.
(shares are supposed to be published in Active DIrectory so clients can look them up, and access them directly over TCP/IP, without the NetBIOS layer in between)
It's possible that recent samba versions, aiming to mimic Windows file sharing, don't broadcast all that stuff by default.

On top of that, there are a number of settings in samba that can make shares  invisible to users that don't have access rights (access based enumeration, hide unwriteable, ... )
 

try adding this to a share definition and see if it makes a difference
```
browsable = yes
```

you can check defaults values (not present in smb.conf)  by running
```
testparm -v
```

---

### Post by darkod on 2013-03-04
Here is an attachment of my setup, nothing in it really.

The workgroup option in [global] might make the difference, it might help showing the server to all computers in WORKGROUP. Of course, if your friends come with their computers set to their own home workgroups, this doesn't help.

My file server does show under Network in win7.

---

### Post by andrewhamming on 2013-03-31
Thanks for the reply, I ended up purging smb on server and re installing with min options in smb.conf and all works fine now :)

---

### Post by ally_uk on 2013-03-31
Agree with the person who said avoid Webmin I was looking at your Global configuration and was like wow that is huge :)

If you want to take your Samba Configuration further and add security 

[http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend)

[http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html](http://www.ubuntugeek.com/howto-setup-samba-server-with-tdbsam-backend.html)

I have used both and they both work with Windows 7 hope it helps :)

---

