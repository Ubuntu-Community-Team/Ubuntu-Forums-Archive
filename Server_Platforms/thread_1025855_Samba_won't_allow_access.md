---
title: "Samba won't allow access"
date: 2008-12-30
forum: Server Platforms
---

### Post by borahshadow on 2008-12-30
Hi I just upgraded my server from dapper to hardy and needed to set samba back up.

I copied my smb.conf that was working perfectly in dapper. Then I added my user name to the samba config with
> 
sudo smbpasswd -a USERNAME
sudo smbpasswd -e USERNAME

I replaced USERNAME with my user.

Then I restarted samba and to be on the safe side I rebooted.

However no computers can access the share. The server is set up with the same static IP that it used to have and the same name. However on a windows box on the network previously mapped drives don't work and if I manually navigate to it from "My network places > Workgroup computers> server-home > shared it brings up a password box.

If I try to access if from my kubuntu computer all the ways that I have tried to access it fail too.

Here is my smb.conf> 
[global]
        netbios name = SERVER-HOME
        load printers = yes
        name resolve order = hosts wins bcast
        server string =
        announce version = 5.0
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        workgroup = WORKGROUP
        syslog only = yes
        username map = /etc/samba/smbusers
        null passwords = true
        printcap name = CUPS
        syslog = 1
        security = share
        passdb backend = tdbsam
        wins support = no
        unix extensions = no
    ; General server settings

[shared]
        writeable = yes
        path = /data/shared
        force group = MYUSER (on the server it is the real username)
        force user = MYUSER
        create mask = 0644
        public = yes
        directory mask = 0755
        browseable = yes
        guest ok = yes

 I don't want to start editing things because it was working fine on dapper and I don't want to mess anything up. I think my problem is more likely from misconfiguring somewhere else.

PS. I selected samba file server from the tasksel menu in the installer if that makes any difference.

---

### Post by Drezard on 2008-12-30
What error message are you getting? And are the directories you are trying to share owned by root?

Daniel

---

### Post by borahshadow on 2008-12-30
nope the shared directories are just exactly how they were in dapper, chmod 777. The drive with the data was not touched when I reinstalled the only thing that could be different could be the samba version, samba setup, or the fstab options on the mounted drive.

The network errors are fairly un descriptive. in kubuntu it says something about does not exist I think (I'm not at that network to test right now) and under windows it gives a range of errors depending on whether I try to map a dirve or use a already mapped drive or when I just browse to the share and try to click on it it pops up a password dialog box with the user name guest (not able to be changed) and no password that I try works.

---

### Post by cariboo on 2008-12-30
Run testparm to see if there are any errors that show up and what output do you get when you run:

```
smbclient -L <server> -U%
```

If your smb.conf is right you should get an output something like this:

```
smbclient -L willy  -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	images          Disk      iso images
	updates         Disk      Project Dakota
	data            Disk      Data directory
	music           Disk      Music library
	movies          Disk      TV Shows and Movies
	print$          Disk      Printer Drivers
	HP_LaserJet_5P_LPT_parport0_HPLIP Printer   HP LaserJet 5P
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)
	WINMCLEESE           

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

Jim

---

### Post by borahshadow on 2008-12-30
testparm showed ok and this is the result of that command. It looks like I think it should.

> Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

        Sharename       Type      Comment
        ---------       ----      -------
        shared          Disk
        IPC$            IPC       IPC Service ()
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

        Server               Comment
        ---------            -------
        DEN
        SERVER-HOME

        Workgroup            Master
        ---------            -------
        WORKGROUP            SERVER-HOME



here is testparm BTW
> Load smb config files from /etc/samba/smb.conf
Processing section "[shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string =
        security = SHARE
        null passwords = Yes
        passdb backend = tdbsam
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        unix extensions = No
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = CUPS

[shared]
        path = /data/shared
        force user = MYUSER (it does have my correct username I just blanked it out here)
        force group = MYUSER 
        read only = No
        create mask = 0644
        guest ok = Yes


That is weird. I just noticed when I look at /etc/samba/smb.conf it shows everything but the output of testparm has many lines missing. Could that be the problem?

---

### Post by capscrew on 2008-12-31
It's not a problem.  The smbd daemon just takes a little longer to parse the smb.conf file with all the comments and non used sections.  The testparm outputs only the used (usefull) lines.  The Samba documentation describes the use of the testparm output to create a smb.conf file with no comments.  

First you copy the commented smb.conf file
```
sudo cp smb.conf smb.conf.master
```
Now that we have a copy of the commented file we can create a new uncommented smb.conf file using the following```
sudo testparm smb.conf.master > smb.conf
```

---

### Post by borahshadow on 2008-12-31
Sorry but I already copied the master smb.conf to a copy and I inserted my own custom smb.conf that was working with dapper. It is posted in the first post in this thread. The testparm output skips lines. Even those lines that were not commented. Compare the posted output of testparm and the smb.conf that I posted in the first post.

---

### Post by capscrew on 2008-12-31
I believe you will find the original smb.conf file at```
/usr/share/samba/smb.conf
```

> The testparm output skips lines. Even those lines that were not commented.

This is not inconsistent with what I said.  Consider your use of:```
netbios name = SERVER-HOME
```

Your use of of the directive ```
wins support = no
```  negates the  the need for a netbios name.  The testparm utility understands this and responds appropriately.

---

### Post by borahshadow on 2008-12-31
hmm ok I understand. but I still don't understand what I did different or why it won't work under hardy but it did under dapper. Have there been significant changes in samba since then?

---

### Post by capscrew on 2008-12-31
> Have there been significant changes in samba since then?

Could be.  Did Dapper use Samba 2 or 3?  I used the same smb.conf file from my Gutsy server when I created Samba on Hardy.  I had no problems.

More likely is that you don't have the users setup correctly.  I realize that you have "share" rather than "user" security on the Samba share and it should accept any user, but obviously it does not.

Here are the relevant sections of my working Samba 3 installation.

Global```
[global]
        workgroup = <Your_WorkGroup_Here>
        server string = %h
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        guest account = nobody
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spas
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

```

Share
```
  comment = Public Share
        path = /<path_to>/share
        read only = No
        create mask = 0775
        directory mask = 0775
        guest ok = Yes

```

This is pretty spare, but I have found that most of the default settings are fine by me.  If you want to have "share security" instead of "user security" then you will have to declare that explicitly.  The default is "user security" and I would leave it as that.  Note that I have explicitly allowed guests in my Public Share.

Note that the guest is mapped to the user nobody in this configuration. See: 
```
map to guest = Bad User [COLOR="Red"]<--this means a non recognized user[/COLOR]
guest account = nobody [COLOR="Red"]<-- Map the non recognized to the user nobody[/COLOR]

```

You could map the guest to your MYUSER and force the guest group.  Such as:
```
map to guest = Bad User [COLOR="green"]<--this means a non recognized user[/COLOR]
guest account = MYUSER [COLOR="green"]<-- Map the non recognized to the user MYUSER 
This user probably should be in the smbpasswd database and have a user login [/color]

force group =MYUSER [COLOR="Green"]<-- Make sure this group exists[/COLOR]

```

---

### Post by borahshadow on 2008-12-31
Dapper had samba version 3.022 and hardy has samba version 3.028a.

Here is what I want I just want a shared folder that is basically wide open on the server. The files on the server should be owned by one user preferably MYUSER. That should avoid any permissions conflicts. Everybody who accesses the share over the network should access it as MYUSER. Does that make sense?

Thanks for your help. Especially over the holidays.

---

### Post by capscrew on 2008-12-31
I think the configuration I suggested will do just that.  I my public share is open to anyone that is on my network.  I have tested it before by adding users that have no login to the Samba server and no smbpasswd.  They still have access via the guset account.  I have a user login "smbuser" and a group "smbguest" that I use for anonymous users.  But you can use your MYUSER:MYUSER login:group setup.  I can't see any problems.

Most of what I needed to learn was at [http://us1.samba.org/samba/docs/]("http://us1.samba.org/samba/docs/")

The following is very good and has great examples.  Be aware that the basic install is for Red Hat, but after that all the configurations are the same as in Ubuntu.  [http://www.samba.org/samba/docs/Samba3-ByExample.pdf]("http://www.samba.org/samba/docs/Samba3-ByExample.pdf")

Have a Happy New Year.  I will be back to help on Friday.

---

### Post by borahshadow on 2008-12-31
Ok thanks for that. I'll see if I can get it to work from your configuration and from the information in those links that you posted.

Happy New Year everybody and thanks for your help.

---

### Post by windependence on 2009-01-01
> **borahshadow said:**
> Dapper had samba version 3.022 and hardy has samba version 3.028a.

Here is what I want I just want a shared folder that is basically wide open on the server. The files on the server should be owned by one user preferably MYUSER. That should avoid any permissions conflicts. Everybody who accesses the share over the network should access it as MYUSER. Does that make sense?

Thanks for your help. Especially over the holidays.

Might want to consider a tiny bit of security maybe? That is why capscrew suggested user level security, unless you are fond of getting hacked. 

-Tim

---

### Post by borahshadow on 2009-01-01
ok sorry but what is the difference between user and share level security?

---

### Post by borahshadow on 2009-01-01
Sometimes I hate simple solutions. My biggest source of confusion was why it was not working with my config that used to work.
When I installed I selected samba file server to save myself a step of "sudo apt-get install samba"

I don't know if that was the problem or if I didn't need to add my user with the smbpasswd.
However with that said this is what I did..
I ran sudo tasksel and deselected the samba file server.
I then ran sudo apt-get install samba
I made sure that uninstalling and reinstalling samba didn't erase my config and then restarted samba with sudo /etc/init.d/samba restart.

It now seems to be working.

---

