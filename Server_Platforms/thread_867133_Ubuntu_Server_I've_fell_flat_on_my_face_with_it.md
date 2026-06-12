---
title: "Ubuntu Server: I've fell flat on my face with it"
date: 2008-07-22
forum: Server Platforms
---

### Post by spoons on 2008-07-22
Ignore... look down. Thanks to the person who fixed this.

---

### Post by spoons on 2008-07-22
Hi there.

We wanted some file space that we could all share on the home network, and have it show up on My Computer as an extra drive (my dad runs Windows - Linux confuses him)

Now, I've read that to communicate with Windows my Ubuntu Server (8.04) I need to have SAMBA. So I selected Samba in the installer.

Now I can log into the server... but I don't have a clue how to set it up. Looking at the Ubuntu Server Guide makes my brain hurt and I'm not sure where to start exactly. I keep getting told I need a DNS Server, but I don't know why.

All we want to do is store some files. (one 40gb HDD for the OS, two 750GB HDDs for the storage)

Help is greatly appreciated, my dad is on the verge of putting Windows Server on to replace Ubuntu.

EDIT: Our Server PC is connected into a Netgear router, which connects to another Netgear router via ethernet mains adapters. This second router goes to the BT wifi router than handles the wireless laptop and the actual internet connection. Long winded, but it works.

---

### Post by hyper_ch on 2008-07-22
(1) should that computer act as server only (no person using it to surf, write some text document, email, ....)? If so, maybe install the server software again (as you can't login anymore)

(2) then update it
```

sudo apt-get update && sudo apt-get upgrade

```

(3) then install ssh server and denyhosts
```

sudo apt-get install openssh-server denyhosts

```
openssh-server will allow you to login through the terminal on your computer into the server
denyhosts will prevent brute-forcing... after entering 3x a wrong user/password the connecting IP will be banned 

(4) login through ssh from your computer

(4.1) open a terminal

(4.2) enter
```

ssh user@server

```

replace "server" with the ip of the server

(4.3.) press yes for the key and enter the password

now yo don't need anymore to touch the server. 

(5) then install samba server
```

sudo apt-get install samba

```

(6) the default samba config has quite a few nice examples - but we want it simple for now, so we back it up
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.org

```

(7) edit a new samba config in nano
```

sudo nano /etc/samba/smb.conf

```

(8) now paste this config (alter it accordingly)
```

[global]
workgroup = WORKGROUP
hosts deny = 192.168.0.1

[exchange]
comment = Exchange
path = /home/$USER/Exchange
read only = No
guest ok = Yes
public = Yes
browseable = Yes
create mask = 0666
directory mask = 0777

[music]
comment = Music
path = /home/$USER/Music
read only = Yes
guest ok = Yes
public = Yes
browseable = Yes
create mask = 0666
directory mask = 0777

[blablabla]
comment = blablabla
path = /home/$USER/blablabla
read only = Yes
guest ok = Yes
public = Yes
browseable = Yes
create mask = 0666
directory mask = 0777

```

replace:
WORKGROUP with your workgroup name
192.168.0.1 with your router's ip
$USER with your username (or adjust the path accordingly and create the according dirs)
The rest should be simple to comprehend.

(9) Press ctrl-x, enter, enter to save and exit nano

(10) restart samba server
```

sudo /etc/init.d/samba restart

```

Now it is available. However it would be good if you'd use a static IP on the server.

---

### Post by argail1980 on 2008-07-22
No, I don't think you need to install a DNS Server.


What srever version d'you have?
What exactly does not work? 
From what platform have you tried?
What is the error message?

---

### Post by Kolipoki on 2008-07-22
> **hyper_ch said:**
> ...

(3) then install ssh server and denyhosts
```

sudo apt-get install openssh-server denyhosts

```

Hyper, would you need to whitelist yourself first for Denyhost?

---

### Post by hyper_ch on 2008-07-22
depends;) do you remember your password?

---

### Post by Kolipoki on 2008-07-22
I made the question because some weeks ago I reached a dead end trying to install Denyhost (well now I'm not quite sure if it was actually with Denyhost). I couldn't Putty back after my first attempt. Since I didn't find/know the workaround (and also because it was a test server :) ) I ended reinstalling the whole 8.04 again.

BTW, that was a great walk-thru. /thumbs up

---

### Post by windependence on 2008-07-23
Great mini how-to HC.

-Tim

---

### Post by spoons on 2008-07-23
Hi everyone, thanks for the great replies!

Hyper-ch, when I log into the server remotely, is the username the same username used to log into the box itself? and is the password the same too?

Thanks again for helping an server-noob, looking forward to replies.

---

### Post by hyper_ch on 2008-07-23
have you tried it?

---

### Post by cox377 on 2008-07-23
> **Kolipoki said:**
> I made the question because some weeks ago I reached a dead end trying to install Denyhost (well now I'm not quite sure if it was actually with Denyhost). I couldn't Putty back after my first attempt. Since I didn't find/know the workaround (and also because it was a test server :) ) I ended reinstalling the whole 8.04 again.

BTW, that was a great walk-thru. /thumbs up

I think it works on 3 failures. It's pretty good, when you look at the list after about a month there were quite a few blocked.

CoXen

---

### Post by cox377 on 2008-07-23
> **spoons said:**
> Hi everyone, thanks for the great replies!

Hyper-ch, when I log into the server remotely, is the username the same username used to log into the box itself? and is the password the same too?

Thanks again for helping an server-noob, looking forward to replies.

The user name and password are the same.

Edit. You could have a look at webmin, maybe a little OTT for what you want.

---

### Post by spoons on 2008-07-25
Ok - update time.

I've got to the stage now where I can see two home folders on my Windows PC which is connected to the same router. It can read files off the server... but not write. in /etc/samba/smb.conf I have "read only = No" (without quotes) set for [exchange] and [software]. So I can't see why it can't write. Help is appreciated, I'm getting there! :)

I've also installed GNOME for a GUI to put myself back into familiar territory, I hope this doesn't complicate things further down the line?

Thanks all! :KS

---

### Post by Krupski on 2008-07-25
> **hyper_ch said:**
> 
(7) edit a new samba config in nano
```

sudo nano /etc/samba/smb.conf

```

(8) now paste this config (alter it accordingly)
```

[global]
workgroup = WORKGROUP
hosts deny = 192.168.0.1
..............

```



For a private home network, the SMB.CONF file can be a lot simpler. Here's what I use:

```


[global]
        workgroup = workgroup
        server string = Storage Drive
        security = share
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        os level = 65
        preferred master = yes
        wins support = yes
        create mask = 0644
        directory mask = 0755
        guest ok = yes
        store dos attributes = yes
        dos filemode = yes

[shared]
        comment = storage
        path = /home/shared
        read only = no

```

I don't need to have individual accounts on my NAS box to allow my son and daughter to access the file server... nor do I get grief when they try to access it and forget that Unix IS case sensitive for usernames while Windows is not.

Of course, the above SMB.CONF is a security nightmare... but since I'm behind a NAT firewall router AND my ISP purposely blocks port 137 and 138, I have no worries that an outside hacker will get in (I hope!)  :)

-- Roger

---

### Post by spynappels on 2008-08-15
> **Krupski said:**
> For a private home network, the SMB.CONF file can be a lot simpler. Here's what I use:

```


[global]
        workgroup = workgroup
        server string = Storage Drive
        security = share
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        os level = 65
        preferred master = yes
        wins support = yes
        create mask = 0644
        directory mask = 0755
        guest ok = yes
        store dos attributes = yes
        dos filemode = yes

[shared]
        comment = storage
        path = /home/shared
        read only = no

```

I don't need to have individual accounts on my NAS box to allow my son and daughter to access the file server... nor do I get grief when they try to access it and forget that Unix IS case sensitive for usernames while Windows is not.

Of course, the above SMB.CONF is a security nightmare... but since I'm behind a NAT firewall router AND my ISP purposely blocks port 137 and 138, I have no worries that an outside hacker will get in (I hope!)  :)

-- Roger

  Thanks for that, i've used that and can now see the drive from my Windows network. Unfortunately, when I try to access the folder, I'm denied access. I wonder whether this is due to the fact that I did not actually create the folder first on the server?  If so, can someone just talk me through that? Thanks.
Stefan.

---

### Post by windependence on 2008-08-15
Stefan, do you have the same users on all your boxes with matching passwords? This is essential for SAMBA to work smoothly.

-Tim

---

### Post by spynappels on 2008-08-15
I have Server 8.04 on an HP e.pc. I am trying to access it from my work laptop, which is on another domain. The server uses workgroup as its workgroup name while the laptop uses wuerth as its workgroup name. Could this be the problem? I did have it working before with server 7.04 but a friend set that up for me. that HDD died and I got a new one and am now trying to set it up for myself.

---

### Post by spynappels on 2008-08-15
Ok, I've now changed the above code to use wuerth as my workgroup and I can now open the shared folder. However, when I try to save a file to it, I get an "Access is denied, make sure that the disk is not full or write protected and that the file is not currently in use"

Any ideas what to do  now? I just want to be able to access that folder from any computer connected to my network, the whole network is behind a firewall so security should be ok. I just want to be able to store stuff on the server and get to it from my laptop or my wife's computer or whatever.

---

### Post by windependence on 2008-08-15
If you are routing SMB over the internet security is definitely NOT ok. You shoulld be using VPN or some other kind of tunnel to access the shares. Am I hearing you right, you have smaba shares exposed to the internet?

-Tim

---

### Post by spynappels on 2008-08-15
No, I'm sorry, I should probably have explained that better. I just mean any computer connected through my router or to my home wireless network. If I want to connect remotely, I will use a VPN, but I just want to get the share up and running first.
  Thanks for your help so far though!

---

### Post by Uluen on 2008-08-15
```
# smbpasswd -a yourusername
```

```
# man smbpasswd
```

---

### Post by windependence on 2008-08-15
> **spynappels said:**
> No, I'm sorry, I should probably have explained that better. I just mean any computer connected through my router or to my home wireless network. If I want to connect remotely, I will use a VPN, but I just want to get the share up and running first.
  Thanks for your help so far though!

Well I think it was my fault because when I read your post about the work laptop, I just ASSUMED you were accessing it from work ;)

You know what happens when you *** u me.

The poster above os trying to tell you that in addition to the user existing on the Linux box, you also have to create a samba user for each one too. So you should have the same user on the Windows machine, the Linux box, and as a samba user on the Linux box.

-Tim

---

### Post by spynappels on 2008-08-15
Ok, I've set up my smbpasswd on the server and when I try to save a file to the shared folder on the server from my Ubuntu Desktop machine, I still get a permission denied message. I'm wondering if it is easier to get it working from an Ubuntu machine first?

  Is there a problem with the smb.conf file?

---

### Post by windependence on 2008-08-15
Try changing your directory mask to 775

Also what is the directory name and path to the shared folder?

don't forget to restart smb and nmb after you make the changes.

```
/etc/init.d/samba restart
```

-Tim

---

### Post by spynappels on 2008-08-15
Ok did that and now I can't see the shared folder anymore.

When you say what is the directory name and path, do you mean /home/shared?
I think I created that directory, but how can I check that using command line? :confused: I'm used to having a GUI to work with.

---

### Post by windependence on 2008-08-15
Yes, that's the one. I see it in your config file.

So now, try 

```
sudo chmod -R 775 /home/shared
```

and then add these lines to your samba config file under global:

```
security = user
encrypt passwords = true
map to guest = bad user
guest account = nobody
```

Then restart samba again.

-Tim

---

### Post by spynappels on 2008-08-15
Right. I've done the above. I cannot now see the shared folder from my Ubuntu machine. I can see it from the Windows machine, but I am still denied access when I try to copy anything to it. I created a test file consisting of text in the shared folder, and I can open it on my Windows machine, and copy it to my windows machine. I cannot edit and save it though.
 This feels like a permission problem, although I do not profess to know much about it.

---

### Post by windependence on 2008-08-15
OK change directories to /home and do:

```
ls -la
```

and post me the output. I think it's an ownership issue.

-Tim

---

### Post by spynappels on 2008-08-15
Thank you very much for your patience with me!!!

Here is the output:

total 16
drwxr-xr-x  4 root       root       4096 2008-08-15 11:13 .
drwxr-xr-x 21 root       root       4096 2008-08-14 13:59 ..
drwxrwxr-x  2 root       root       4096 2008-08-15 18:06 shared
drwxr-xr-x  2 spynappels spynappels 4096 2008-08-14 15:41 spynappels


Does this mean that the shared folder is owned by the root and that is why I cannot access it?

---

### Post by windependence on 2008-08-15
Yep. I think that's it. If you chown it to your user, I think you will be OK. Try it. ;)

Hey if we don't fix it this morning I will work with you again tonight. I work nights and it's noon here so I will have to get some sleep soon, but don't worry we'll get it.

-Tim

---

### Post by spynappels on 2008-08-15
Dude! You rock!  Copying files to my server as I speak. Just for information, WinXP allows you to map a drive letter to a folder using different username and password than you may be logged into your local machine as. It seems to be working anyway so thanks very much!!!

---

### Post by alecz20 on 2008-08-20
> **windependence said:**
> ...

The poster above os trying to tell you that in addition to the user existing on the Linux box, you also have to create a samba user for each one too. So you should have the same user on the Windows machine, the Linux box, and as a samba user on the Linux box.

-Tim

Hey, nice thread... covers the basics very nice. I plan to set up a file/media server in a few days.

I was wondering though... Since Windows does not require the users to have passwords, how can a Windows user still access and write to a samba share on a Ubuntu Server? How would one create the entry for that user in Samba?

In other words... can there be an "Anonymus share", where ANYONE can write to? I suppose that could be owned by root, but the permissions need to be 777 or something like that?

Thanks.

---

### Post by Ximbiot on 2008-08-20
> **alecz20 said:**
> In other words... can there be an "Anonymus share", where ANYONE can write to? I suppose that could be owned by root, but the permissions need to be 777 or something like that?

I've seen people share /tmp from Samba for this purpose.  I think one of my old RH distros had a Samba with /tmp shared as [temp] that way by default or at least set up so you could remove comment markers and enable it.

I think the gist was that you create the share like any other share, pointing it at /tmp, making sure guest access is turned on, and writable is set to true.  Of course, putting it somewhere else and setting permissions to 777 as you suggested would work as well.

---

### Post by windependence on 2008-08-21
> **alecz20 said:**
> Hey, nice thread... covers the basics very nice. I plan to set up a file/media server in a few days.

I was wondering though... Since Windows does not require the users to have passwords, how can a Windows user still access and write to a samba share on a Ubuntu Server? How would one create the entry for that user in Samba?

In other words... can there be an "Anonymus share", where ANYONE can write to? I suppose that could be owned by root, but the permissions need to be 777 or something like that?

Thanks.

Thanks for the compliment! :)

Yes, you can set up a globally accessible share. You do it in the samba configuration file. The permissions don't necessarily have to be 777. I have never set up one of these globally accessed shares but I know it can be done.

-Tim

---

### Post by Uluen on 2008-08-21
> **windependence said:**
> The poster above os trying to tell you [...]I think I was pretty clear but that's my style, I usually give clues and point people in the right direction.

I know I learn more by figuring out thing myself than to be given a complete howto :)

---

