---
title: "Trying to set up a homeserver"
date: 2010-07-27
forum: Server Platforms
---

### Post by youngros on 2010-07-27
Basics Windows XP Pro host, Xubuntu guest on VMware player.

I've been trying to follow the tutuorial here [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1) and I know it is 3 years old but some of the basics must be the same.

I have got to the part about installing and configuring Samba. Now I as probably most do have a dynamic IP address. I really don't want to start messing around with  4 other computers on the router and losing internet access.

Now when I try and type in from a windows machine the server name Firefox just returns file not found.

I need some more info to get me sorted on this. Do I need to set up something else?

Are there any better tutorials out there, I have seen those from howtoforge but it is still not clear on the subject.

Testing this out first on VMware before I build a server to work as filesharing as not all the computers here run all the time although they are networked, or have  monitors and also to work as a backup system. Would probably use as a server for small websites although have paid hosting.

---

### Post by CharlesA on 2010-07-27
Make sure that you are using Bridged networking not NAT in VMWare.

You could try just typing in the IP address of the server and see if you can connect to it from there. If you can, then you have a problem with name resolution.

---

### Post by youngros on 2010-07-27
I've now set it bridged networking (not seen anything about that before!!) still can't get in typing either the sever name or the IP address but interesting enough it showed up on Network Magic, first as Samba and then as the same name as the computer it is hosted on, so something is working. Do I need to restart anything?

Network Magic is showing it as offline and also as a Microsoft Windows Server 2003, one of the odd things about Network Magic I presume?

---

### Post by CharlesA on 2010-07-27
Never heard of network magic.

Is the server getting an ip address at all?

You can check with *ifconfig*, then try to ping something like google.com and see if it gets a response.

Are you able to ping the windows machines by ip address?

---

### Post by youngros on 2010-07-27
Network Magic very much a Windows utility although think it works on a Mac as well, usefull for networking and sharing of files and folders etc. It is now showing the Server as on.

There is an assigned IP address to the server.

I can ping google.com and the IP address of this computer

Edit to say that I can ping the server from this computer.

---

### Post by CharlesA on 2010-07-27
See if you can ping the server from it's IP address and then try to connect to one of the shares by the IP.

---

### Post by youngros on 2010-07-27
I can ping the server from its IP not sure what you mean by connecting to one of the shares by IP

---

### Post by youngros on 2010-07-27
Should I be able to see the server on Windows network? I can see the machine it is hosted on.

---

### Post by arrrghhh on 2010-07-27
What network setting do you have in vmware?  Is it bridged or NAT?  Like CharlesA said, use bridged.

To connect to one of the shares via IP:

On a Windows machine that is on your LAN, go to start -> run (or Win key + R) to bring up a prompt.

Then, in that box put "\\ip.addr\" to see if anything comes up.  For example, my Ubuntu server is 192.168.0.99 on my network.  If I go to "\\192.168.0.99\" on my Win7 laptop, I get an explorer window that shows all my Samba shares.

Please enter that in without the quotes and let us know how it works.

---

### Post by youngros on 2010-07-27
On three different machines, one of which is windows7 I get windows cannot access \\ip.addr\  the network path was not found :(

---

### Post by CharlesA on 2010-07-27
Something is wrong with your samba set up. Even if name resolution isn't working, you should be able to access it by ip address.

Try running *testparm* and posting any errors/warnings.

---

### Post by arrrghhh on 2010-07-27
> **youngros said:**
> On three different machines, one of which is windows7 I get windows cannot access \\ip.addr\  the network path was not found :(

I'm assuming you actually put a valid IP in that "ip.addr" field...?

Also, did we establish that you can ping the virtual server from these three different machines?  I was kinda assuming we had already established that (unless I didn't follow the thread properly, in which case I apologize for putting the cart before the horse...)

---

### Post by youngros on 2010-07-27
I'm wondering if this is a firewall issue. On this computer which has an AVG firewall the workgroup setting shows the range to be from 1.12 - 1.24 but certainly the ubuntu is 1.10 and another computer is 1.12 but the ubuntu pings!! that is sat on top of a host with 1.15 and a Comodo firewall.

Will look at extending the range of the firewall settings, done it before just need to remember how.

---

### Post by arrrghhh on 2010-07-27
May want to disable the firewalls, if only to rule that piece out.

Were you able to ping the ubuntu virtual server IP from one of the Win workstations?

---

### Post by youngros on 2010-07-27
Bit of rebooting to see what happens
I can ping the server from all three machines 
I now get a box come up that says Enter network password?
So which user name and password is it after?

---

### Post by arrrghhh on 2010-07-27
> **youngros said:**
> I now get a box come up that says Enter network password?
So which user name and password is it after?

I believe the user that has access to the folder on the Linux box...

---

### Post by youngros on 2010-07-27
well I've typed in every single user name password combo and nothing...so looks like a purge on samba and reinstall unless there is a way of finding the username and password

---

### Post by arrrghhh on 2010-07-27
> **youngros said:**
> well I've typed in every single user name password combo and nothing...so looks like a purge on samba and reinstall unless there is a way of finding the username and password

I only have one user/pass on my Linux box, that one always works for me...

With that said, I swear I've set mine up w/o any pass auth, and it seems no other workstations in my network get the user/pass prompt but me...

---

### Post by CharlesA on 2010-07-27
Did you create a smb password by running smbpasswd?

```
sudo smbpasswd -a username
```

I ran into that problem before I remembered that I needed to set a smb password.

I just did a test install on a VM and after installing samba with apt-get and setting a password for the samba user, I was able to connect by using the ip address.

---

### Post by arrrghhh on 2010-07-27
> **CharlesA said:**
> Did you create a smb password by running *smbpasswd username*

I ran into that problem before I remembered that I needed to set a smb password.

Hrm, I need to re-read the samba setup guide in that case.  I don't recall doing that either :)

---

### Post by CharlesA on 2010-07-27
> **arrrghhh said:**
> Hrm, I need to re-read the samba setup guide in that case.  I don't recall doing that either :)

All I did was this:

```
sudo apt-get install samba
sudo smbpasswd -a ubuntu
sudo service smbd restart
```

Start > Run > \\192.168.1.30

I got a prompt for a username/password.

---

### Post by arrrghhh on 2010-07-27
Yea, I setup samba (this last time at least) with Webmin.  Maybe it bungled something, because when I setup samba originally (years ago...) via the command line/conf files, I didn't have any issues setting it up without authentication...

---

### Post by CharlesA on 2010-07-27
Interesting. I set up Samba with webmin on my main server but I had to set the password from webmin's samba user/password area.

---

### Post by CharlesA on 2010-07-27
Ok. I did a "reinstall" of the applications that are on my physical server on a VM except this time I didn't install Webmin.

I wasn't able to connect to any shares "out of the box" and had to use smbpasswd to add a smb user and set their password.

```
sudo smbpasswd -a username
```

Thanks for helping me learn something new. :-)

---

### Post by arrrghhh on 2010-07-27
> **CharlesA said:**
> Ok. I did a "reinstall" of the applications that are on my physical server on a VM except this time I didn't install Webmin.

I wasn't able to connect to any shares "out of the box" and had to use smbpasswd to add a smb user and set their password.

```
sudo smbpasswd -a username
```

Thanks for helping me learn something new. :-)

Haha, I think we both did.  I'm going to try and fiddle with my setup to see if I can get rid of the password prompts!

---

### Post by CharlesA on 2010-07-27
> **arrrghhh said:**
> Haha, I think we both did.  I'm going to try and fiddle with my setup to see if I can get rid of the password prompts!

This is what one of my share definitions look like:

```
[Charles]
        comment = Charles' Folder
        path = /array/charles
        invalid users = clone, htpc
        write list = charles
        create mask = 0660
        directory mask = 0770
```

The directory permissions are as follows:

```
charles@atlantis:~$ ls -ld /array/charles
drwxrwx--- 2 charles charles 4096 2010-07-27 19:10 /array/charles

```

My Windows password matches the password that I set using smbpasswd, and since Windows likes to automatically try to authenticate using your windows logon, I don't get prompted for a password as long as the user account/password both match.

Hopefully we aren't derailing this thread too much.

---

### Post by arrrghhh on 2010-07-27
No worries, I think I got it... Webmin has a lot of nice features for samba, just don't use it to update your system... sheesh!

---

### Post by CharlesA on 2010-07-28
Agreed about the features for Samba, but it's kinda pointless once you get the shares and permissions configured (imho, since I just copy smb.conf from the old install to the new install).

---

### Post by youngros on 2010-07-28
Decided to go a different route and to use the Ubuntu server install. I followed the howtoforge guide to get it installed plus their guide on installing Samba. The only thing I didn't do and don't know how much effect it will have was when setting up the directories I forgot the trailing slash after /home/shares/allusers.....will this make any difference?

So far so good Samba is installed and I can run the ip address and I get to see the shares folder, and it doesn't prompt for a password....so maybe I missed something there.
I can't see the folders in the browser only if I use IE, is that usual?

---

### Post by arrrghhh on 2010-07-28
> **youngros said:**
> The only thing I didn't do and don't know how much effect it will have was when setting up the directories I forgot the trailing slash after /home/shares/allusers.....will this make any difference?

Shouldn't be a big deal... If it is, just add it and restart the smbd service :D

> **youngros said:**
> So far so good Samba is installed and I can run the ip address and I get to see the shares folder, and it doesn't prompt for a password....so maybe I missed something there.

Perhaps... do you want it to prompt you for a password?  CharlesA hit on a good point, if you use the same user/pass as your Win machine, it'll probably just auto-authenticate.

> **youngros said:**
> I can't see the folders in the browser only if I use IE, is that usual?

Uhm... What?  You're trying to browse your samba shares in firefox?  Just use Windows Explorer.  The reason it works in IE is probably related to the tight integration the browser has with the OS, kinda like Konquerer.  I just use Win+R (opens a run prompt) and navigate to the share, or make UNC-path shortcuts on my desktop to get to the samba shares.

---

### Post by youngros on 2010-07-28
Uhm... What?  You're trying to browse your samba shares in firefox?   Just use Windows Explorer.  The reason it works in IE is probably  related to the tight integration the browser has with the OS, kinda like  Konquerer.  I just use Win+R (opens a run prompt) and navigate to the  share, or make UNC-path shortcuts on my desktop to get to the samba  shares.

Yes!! I don't use IE and not installed it on this computer, maybe I will have to.

No password on this computer as it is not a live system then it is not so important, should I run a live system then yes maybe it would be.

---

### Post by arrrghhh on 2010-07-28
> **youngros said:**
> Yes!! I don't use IE and not installed it on this computer, maybe I will have to.

No password on this computer as it is not a live system then it is not so important, should I run a live system then yes maybe it would be.

Windows Explorer cannot be removed.  Just use it on a Win machine.

If authentication is an issue, you'll have to flesh out your smb.conf file.  It probably just doesn't have that setting enabled.

---

### Post by youngros on 2010-07-28
[SIZE=2]Windows7 so it's there but not installed. Not a default on a UK version.
Got putty installed on windows and downloaded webmin, the tutorial i'm looking at says install all these presumably to get webmin to work, is that correct?

apt-get install apache2 vsftpd quota bind9 perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime rssh libio-pty-perl libmd5-perl
etherwake ethtool ntpdate libio-socket-ssl-perl[/SIZE][SIZE=2]
[/SIZE]

---

### Post by arrrghhh on 2010-07-28
I.... I don't understand what you're asking.  You CANNOT remove Windows Explorer.  Keep in mind this is NOT Internet Explorer.

---

### Post by CharlesA on 2010-07-28
This script will install the dependencies that webmin requires and download and install Webmin:

Note: You need to run it with **sudo**

```
#!/bin/bash

WEBMIN=webmin_1.510-2_all.deb

apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions --assume-yes
 wget http://prdownloads.sourceforge.net/webadmin/$WEBMIN && dpkg -i $WEBMIN
```

You can install apache, bind9, etc if you need them from the webmin interface.

As for opening the shares in IE, I have a feeling you are just using Windows Explorer, not IE. Whenever you go "Start > Run > \\ipaddressgoeshere" it opens it in Windows Explorer.

---

### Post by youngros on 2010-07-28
> As for opening the shares in IE, I have a feeling you are just using  Windows Explorer, not IE. Whenever you go "Start > Run >  \\ipaddressgoeshere" it opens it in Windows Explorer. 	

Yes that is what I mean, not good at explaining things at times.

Anyway webmin installed and works in Firefox!! Now just need to find my way around that.

Hopefully by the time I've got all this sorted and working thanks to you guys. I will have all the bits for my server proper.

---

### Post by CharlesA on 2010-07-28
> **youngros said:**
> Yes that is what I mean, not good at explaining things at times.

Anyway webmin installed and works in Firefox!! Now just need to find my way around that.

Hopefully by the time I've got all this sorted and working thanks to you guys. I will have all the bits for my server proper.

Webmin should work in any browser, I know I've used it in both IE and Firefox, should work in Chrome and Opera too.

It's got a fairly easy to use UI; configuring the different packages might be a bit confusing, but there is documentation around the web on them.

---

### Post by arrrghhh on 2010-07-28
> **youngros said:**
> Yes that is what I mean, not good at explaining things at times.

Anyway webmin installed and works in Firefox!! Now just need to find my way around that.

Hopefully by the time I've got all this sorted and working thanks to you guys. I will have all the bits for my server proper.

No worries at all.  Glad to see it's workin for ya - Webmin is great, just DON'T use it to update your system (it'll offer to update packages... just do it yourself with apt-get or aptitude...)

Everything else in Webmin seems great, except it doesn't seem to quite understand the new way Ubuntu does init scripts.  It didn't restart samba for me successfully, it tried to use the /etc/init.d script which is no longer valid.

---

### Post by CharlesA on 2010-07-28
> **arrrghhh said:**
> No worries at all.  Glad to see it's workin for ya - Webmin is great, just DON'T use it to update your system (it'll offer to update packages... just do it yourself with apt-get or aptitude...)

Everything else in Webmin seems great, except it doesn't seem to quite understand the new way Ubuntu does init scripts.  It didn't restart samba for me successfully, it tried to use the /etc/init.d script which is no longer valid.
For webmin, you need to go into the "module config" and change the command to start/stop/restart the process.

For Samba I use this:

service smbd stop &&& service smbd start && service nmbd stop && service nmbd start

The same goes for the other services.

---

### Post by arrrghhh on 2010-07-28
> **CharlesA said:**
> For webmin, you need to go into the "module config" and change the command to start/stop/restart the process.

For Samba I use this:

service smbd stop &&& service smbd start && service nmbd stop && service nmbd start

The same goes for the other services.

Ah, I figured there was something I could've changed.  I guess I should look into it before I complain about it :P

What about updates?  I prefer to do them myself, but seeing updates in Webmin is bothering me.  It's a little off-topic, but not really haha!

---

### Post by CharlesA on 2010-07-28
I just use **apt-get upgrade** from the terminal myself. I don't think I've actually done an update in webmin.

I just know that after an apt-get upgrade, and refreshing webmin it says everything is up-to-date.

---

