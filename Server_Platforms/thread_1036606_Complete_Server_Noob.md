---
title: "Complete Server Noob"
date: 2009-01-11
forum: Server Platforms
---

### Post by lightningrod66 on 2009-01-11
I am trying to install Ubuntu 8.10 LAMP server to use as a webserver.  I have two other computers running WinXP Pro networked in a WORKGROUP (not DOMAIN).  I will be using one of the WinXp machines to edit webpages, then put them on the webserver.  I have managed to install the LAMP server, but my network configuration is screwed somewhere because I cannot get internet access.  I have cable modem->router->computers.  Each computer has been assigned a static IP address (192.168.1.x)  My router (gateway) is 192.168.1.1, subnet mask is 255.255.255.0, the WORKGROUP name is TESTLAB.  During the install it asks for the domain (?) The box I am installing ubuntu on has onboard LAN as well as a Linksys PCI NIC.  I am using the Linksys only.  During the install, how do I get the correct information so that the internet will work?  I saw somewhere to use vi to edit the /etc/network/interface, but I don't know how to use vi with CLI only.  I typed sudo vi /etc/network/interfaces at the command prompt, and it brought up the file for editing, but I don't know how to edit and save changes this way.  Once I get the internet connection working and get the server to be accessable from my Windows machines, I will be fine.  I just am stuck at this point because I have no connection.

---

### Post by blackened on 2009-01-11
vi is a big pain if you are unfamiliar with it (but tremendously powerful when you learn it). It might benefit you to use nano instead.

```
sudo nano /etc/network/interfaces
```

Would be helpful if you post the contents of that file, as well as 
```
ifconfig
```
and
```
lshw -C network
```

You may have a hard time doing this from the cli though. I would still advise against installing a gui on a server.

---

### Post by lightningrod66 on 2009-01-11
I will post the contents of those files.  I only tried vi because that was an example I saw for editing.  I found some basic commands to edit with vi so I used that.

---

### Post by theozzlives on 2009-01-11
> **lightningrod66 said:**
> I am trying to install Ubuntu 8.10 LAMP server to use as a webserver.  I have two other computers running WinXP Pro networked in a WORKGROUP (not DOMAIN).  I will be using one of the WinXp machines to edit webpages, then put them on the webserver.  I have managed to install the LAMP server, but my network configuration is screwed somewhere because I cannot get internet access.  I have cable modem->router->computers.  Each computer has been assigned a static IP address (192.168.1.x)  My router (gateway) is 192.168.1.1, subnet mask is 255.255.255.0, the WORKGROUP name is TESTLAB.  During the install it asks for the domain (?) The box I am installing ubuntu on has onboard LAN as well as a Linksys PCI NIC.  I am using the Linksys only.  During the install, how do I get the correct information so that the internet will work?  I saw somewhere to use vi to edit the /etc/network/interface, but I don't know how to use vi with CLI only.  I typed sudo vi /etc/network/interfaces at the command prompt, and it brought up the file for editing, but I don't know how to edit and save changes this way.  Once I get the internet connection working and get the server to be accessable from my Windows machines, I will be fine.  I just am stuck at this point because I have no connection.

You have to ask (and probably pay) your ISP for a static address. Your router IPs are local only.

---

### Post by lightningrod66 on 2009-01-11
> **blackened said:**
> vi is a big pain if you are unfamiliar with it (but tremendously powerful when you learn it). It might benefit you to use nano instead.

```
sudo nano /etc/network/interfaces
```

Would be helpful if you post the contents of that file, as well as 
```
ifconfig
```
and
```
lshw -C network
```

You may have a hard time doing this from the cli though. I would still advise against installing a gui on a server.

Here are the contents:

/etc/network/interfaces
```
The primary network interface
iface eth0 inet static
        address 192.168.1.102
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 68.87.66.196 68.87.64.196
        dns-search lan
```
*****************************************************************
ifconfig
```
eth0    Link encap:Ethernet  HWaddr 00:0a:e6:c6:83:b6
        inet addr:192.168.1.102  Bcast:192.168.1.255 Mask: 255.255.255.0
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0.B)  TX bytes:0 (0.0.B)
        Interrupt:10 Base address:0xc000

lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.255.255.0
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:12 errors:0 dropped:0 overruns:0 frame:0
        TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:964 (964.0.B) TX bytes:964 (964.0.B)
```
*****************************************************************
lshw -C network
(I am not sure how to post this one as it fills up more than what the screen shows.  I was able to type the other contents because I could see it all on the screen, but this command shows info for both eth0 and eth1 and I don't know how to scroll up on the screen to see where it starts)

One thing I could try is to take out the Linksys PCI card and just use the onboard LAN so that there is only one possible interface.  When I was running the WAMP server, the Linksys worked, but for this Ubuntu server it may be best to simplify.

If someone can tell me how to get to the beginning of the lshw contents, I will post that as well.  I am looking at the server's screen and typing the contents on another computer.

---

### Post by lightningrod66 on 2009-01-11
> **theozzlives said:**
> You have to ask (and probably pay) your ISP for a static address. Your router IPs are local only.

Maybe you are confused by my post.  I have been running a Windows-based web server for several years.  In my LOCAL network (WORKGROUP) I have assigned static IP adresses for each computer (there are 3 - 192.168.1.100, 192.168.1.101, and 192.168.1.102)
My OUTSIDE IP address changes because it is not static (cable), but I am using a dynamic DNS service so that my website can always be at the same address.

---

### Post by lightningrod66 on 2009-01-11
Let me clarify something so that it is more clear what I am trying to do.  I have an in-place Windows network with 2 computers connected via a WORKGROUP (not a domain) and I want the Ubuntu box to be another node in this WORKGROUP, and for the 3 computers to be able to see each other and exchange files.  I only want to use the Ubuntu server as a webserver.  It just needs to sit here and serve webpages.  I will create and edit these webpages on another computer and move them to the server.  At this point, I have installed the Ubuntu server twice (trying two different approaches for network during the install) and I still can't connect to internet OR my other computers.  I don't have a problem with not having a GUI once I get this network thing figured out.  I should be able to manage it after that, I am just not that experienced trying to do this configuring and editing from CLI.  I am sure that there is something I am still missing during the install but I don't know what it is yet.

Hopefully my posts don't sound rude or unappreciative.  I don't mean for them to.  I appreciate any and all help, I am just a little frustrated because I haven't found any instructions anywhere on how to get an Ubuntu server to join a Windows WORKGROUP(most of the things I have seen assume that the server is on a DOMAIN).  You would think that this would be a fairly common thing, but I haven't seen it yet.  Hopefully my explanations are clear enough.  I am sure that I am not the first person to try this :) so there has to be others who have gotten this to work.

---

### Post by yue232qi121 on 2009-01-11
there are four kinds of jewelry,[wholesale jewelry](http://www.jewelryol.com/),[fashion jewelry](http://www.jewelryol.com/),[handmade jewelry](http://www.jewelryol.com/) and [costume jewelry](http://www.jewelryol.com/) ,which one do you like ?

---

### Post by lightningrod66 on 2009-01-11
> what do you choose 

--------------------------------------------------------------------------------

there are four kinds of jewelry,wholesale jewelry,fashion jewelry,handmade jewelry and costume jewelry ,which one do you like ?

??? What will my answer to this question tell you ???

EDIT: I was replying to someone's post here, but now the original post is gone.
????????

---

### Post by lightningrod66 on 2009-01-11
I am going to remove the Linksys PCI network card and just use the onboard LAN, then re-install the server again.  If you have an answer to any of my previous posts, please go ahead and reply because the information could still be useful even if I manage to get this working by eliminating one of the interfaces (I don't know if this will help me or not, but it will be one more thing to try :)).  I will post whatever solution works, so that it will be there for someone else having the same problem.

Thanks to all so far who have replied :)  We WILL get this thing working!!!

---

### Post by volkswagner on 2009-01-11
You say you have onboard and a pci card.  When you run ifconfig they should both show up, do they? Your output only shows eth0.

After editing interfaces file you need to restart networking to allow changes to take.

```
sudo /etc/init.d/networking restart
```

Make sure your network card is recognized.  List pci devices should give you a clue.

```
lspci
```

Is DHCP active on your router.  If it is, it's good practice to assign addresses outside the DHCP range, like 192.168.11, ignore if your router is assigning the static address.  My cheap router won't.  :p

A good command to know is, host....this is a quick check to see if internet is working.

```
host google.com
```

Should output the name servers of Google.

Can you ping the server from one of your xp machines?

Booting a live CD can verify your hardware is working in Linux.

---

### Post by lightningrod66 on 2009-01-11
> **volkswagner said:**
> You say you have onboard and a pci card.  When you run ifconfig they should both show up, do they? Your output only shows eth0.

That is correct - it only shows eth0. When I run the "lshw -C" command, I believe it shows network0 and network1.  It scrolls so fast to the end that I can't see the beginning of it, but I see it shows network1 disabled.  If I knew how to scroll up on the screen I could tell.  Just pushing the up arrow, or Page Up key doesn't work.


> **volkswagner said:**
> 
After editing interfaces file you need to restart networking to allow changes to take.

```
sudo /etc/init.d/networking restart
```

I did the restart after editing


> **volkswagner said:**
> 
Make sure your network card is recognized.  List pci devices should give you a clue.

```
lspci
```

Is DHCP active on your router.  If it is, it's good practice to assign addresses outside the DHCP range, like 192.168.11, ignore if your router is assigning the static address.  My cheap router won't.  :p

My router has DHCP enabled, but I have it starting at 192.168.1.110 so that when my son uses his laptop or his Nintendo DS or his Nintendo Wii he can connect to the wireless without taking one of my "reserved" IP addresses


> **volkswagner said:**
> 
A good command to know is, host....this is a quick check to see if internet is working.

```
host google.com
```

Should output the name servers of Google.

Can you ping the server from one of your xp machines?

No I cannot ping the server.  "request timed out"


> **volkswagner said:**
> 
Booting a live CD can verify your hardware is working in Linux.

---

### Post by lightningrod66 on 2009-01-11
OK.  I removed the Linksys PCI network card and re-installed ubuntu server 8.10.  During the install, it didn't ask me about network settings this time (the last two times I entered information).  Now it has botted up and I can connect to internet, but I can't see it from my other computers.  The install setup the network eth0 with dhcp.  SO - I now have internet connection, but how can I
1) set a static IP (192.168.0.102) because my router forwards port 80 to that address
2) see the server from my Windoze boxes

I (we) are getting very close now, but some tweaking remains :)

EDIT: After booting, I tried "ping www.google.com"  It IS pinging, but it is STILL pinging!  (for about 10 minutes now!!) How do I stop it?

---

### Post by albinootje on 2009-01-11
> **lightningrod66 said:**
> 
lshw -C network
(I am not sure how to post this one as it fills up more than what the screen shows.  I was able to type the other contents because I could see it all on the screen, but this command shows info for both eth0 and eth1 and I don't know how to scroll up on the screen to see where it starts)


Linux has the really cool shift-pageup, and shift-pagedown in virtual console or terminal to scroll back and forth through the "text console history buffer". (In FreeBSD you have to press scroll-lock first, and then you can do the same)

Years ago, if you would boot without a graphical Display Manager it was even possible to scroll back till the very beginning, even to the point before Linux would start booting! :) Not sure whether that's still possible

---

### Post by albinootje on 2009-01-11
> **lightningrod66 said:**
> OK.  I removed the Linksys PCI network card and re-installed ubuntu server 8.10.  During the install, it didn't ask me about network settings this time (the last two times I entered information).  Now it has botted up and I can connect to internet, but I can't see it from my other computers.  The install setup the network eth0 with dhcp.  SO - I now have internet connection, but how can I
1) set a static IP (192.168.0.102) because my router forwards port 80 to that address
2) see the server from my Windoze boxes

I (we) are getting very close now, but some tweaking remains :)

EDIT: After booting, I tried "ping www.google.com"  It IS pinging, but it is STILL pinging!  (for about 10 minutes now!!) How do I stop it?

Use the ctl-c key combination to stop it.

See here for your question about configuring a static ip-address :
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

What do you mean with "see the server from my Windoze boxes" ?
Earlier you wrote about "joining the DOMAIN", which confused me a bit.
You mean that your clients can see and use the shares from your Ubuntu server ?
Did you configure Samba properly already ?

See here for more info and trouble-shooting Samba :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by lightningrod66 on 2009-01-11
> **albinootje said:**
> Use the ctl-c key combination to stop it.

See here for your question about configuring a static ip-address :
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

What do you mean with "see the server from my Windoze boxes" ?
Earlier you wrote about "joining the DOMAIN", which confused me a bit.
You mean that your clients can see and use the shares from your Ubuntu server ?
Did you configure Samba properly already ?

Apparently I didn't explain this part well enough.  I have 3 computers on a Home network.  Windows Xp Pro on 2 of them, and Ubuntu server is 3rd.  The Windows machines were already on this network in a WORKGROUP.  Unlike what we have at work, which is a Windows network on a DOMAIN.  The name of my WORKGROUP is TESTLAB.  I have a cable modem going into a router (192.168.1.1 configured as a gateway).  From the router (via ethernet) the computers are connected with static IP adresses (192.168.1.100-WinXP, 192.168.1.101-WinXP, and 192.168.1.102-for ubuntu server).  I want the ubuntu server to be a part of this network so that I can see the server from my other 2 computers in order to place created/edited web pages on it.

During the ubuntu server install (3rd attempt) I chose LAMP server and Samba File server.  I know that they have been installed because at bootup, I can see those things loading.  I haven't done any type of configuring as of yet.  I am trying to figure out some CLI commands to get things done.

Sorry to seem like such a mess, but I am used to working with Red Hat and SuSE, though not server installs (KDE and GNOME, workstations only).  I haven't had much experience with CLI so I am trying to learn, while trying to get my server operating at the same time.  I just need some help with a couple of things to get me going
1) give the server the static IP of 192.168.1.102 so that my router can forward port 80 to it for webserving
2)let my WinXP machines have access to it so I can get the necessary files onto it.
3) learn about a few basic necessary CLI commands in order to get these things done, then when it is operating normally, I can learn more of CLI.

I will use phpMyAdmin for the MySQL things, and I will try Webmin for other server config issues.

All the help so far has been excellent, and I am learning :)


> **albinootje said:**
> 
See here for more info and trouble-shooting Samba :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by lightningrod66 on 2009-01-12
OK I think I am getting the hang of this :)  Thanks to your help, I have Samba configured, and have a static IP address on this server.  I still can't see it from the other computers, but a netscan shows it.  I still need to tweak the Samba probably.  I also wondered how to download and install webmin on this server.  How do I connect to a website, download the file, then install it?

If webmin works the way I think it does, I can manage the server via a webpage.  Then I can configure apache and samba and whatever through a web browser.

This is exciting!  I know some of you are yawning right now, but just remember when you had to set up your first server with no gui :)

---

### Post by albinootje on 2009-01-12
> **lightningrod66 said:**
> I have Samba configured, and have a static IP address on this server.  I still can't see it from the other computers, but a netscan shows it.  I still need to tweak the Samba probably.  I also wondered how to download and install webmin on this server.


Years ago I've used webmin for Samba, and that looked good, although I noticed some annoyances. Last week I tried it again, and it has completely changed, imho much worse :(

Much more interesting is Swat, the default Samba configuration software, but there you need to log in as root. In Ubuntu the root account is disabled *and* has no password set, .. a pity.

You can try this software (coming from RedHat Linux) :
```

sudo apt-get install system-config-samba

```
After that -> System -> Administration -> Samba

For your setup it is important to make sure that your Ubuntu box is using the same workgroup name as the other machines in your LAN.
With the GUI tool (system-config-samba) you can do that.

---

### Post by volkswagner on 2009-01-12
> **lightningrod66 said:**
>  How do I connect to a website, download the file, then install it?

```
wget
```

to download the lastest, change the directory, like /tmp, then download, you will then need to follow the install directions for debian at Webmin's site.

```
cd /tmp
```

download the latest webmin .deb package

```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.441_all.deb
```

After download completes, stay in that directory to install as per Webmin site.

---

### Post by lightningrod66 on 2009-01-12
> **albinootje said:**
> Years ago I've used webmin for Samba, and that looked good, although I noticed some annoyances. Last week I tried it again, and it has completely changed, imho much worse :(

Much more interesting is Swat, the default Samba configuration software, but there you need to log in as root. In Ubuntu the root account is disabled *and* has no password set, .. a pity.

You can try this software (coming from RedHat Linux) :
```

sudo apt-get install system-config-samba

```
After that -> System -> Administration -> Samba

For your setup it is important to make sure that your Ubuntu box is using the same workgroup name as the other machines in your LAN.
With the GUI tool (system-config-samba) you can do that.

Thanks for the info.  I am using the server edition so I can't use a gui tool.

I was hoping that Webmin would be for complete server configuration - not just Samba.

My server is using the same workgroup name, but there is still no connection between computers.  I do have internet access for the server, so I can download and install things.  I'm sure that somewhere I will see a setting or something that I didn't get right with Samba.

These forums are the greatest thing ever for learning!  I used to subscribe to the MaximumLinux forum before it went away :(

---

### Post by albinootje on 2009-01-12
> **lightningrod66 said:**
> Thanks for the info.  I am using the server edition so I can't use a gui tool.

Sorry about that.
If you don't mind setting a root password for using Swat, then try it.

I've read that on the ubuntuforums.org it's kind of forbidden to tell users how to fully enable the root account, but I'm sure you can find out if you want to try Swat. 
In other words, I find it kind of a pity that Ubuntu includes Swat in the repositories, while it really wants a root login to work with.
And I'm not sure whether Swat enforces https:// 
Perhaps I should test it again, although Life without a root password is kind of comforting :)

Swat is is a web based GUI.
> 
I was hoping that Webmin would be for complete server configuration - not just Samba.

Yes, correct.  Feel free to try it.
I dislike the current setup of webmin, where I find it hard to navigate with the left frame of it. The older webmin version years ago was so much nicer imho.

> 
My server is using the same workgroup name, but there is still no connection between computers.  I do have internet access for the server, so I can download and install things.  I'm sure that somewhere I will see a setting or something that I didn't get right with Samba.


Please test with smbclient on your Ubuntu box first, and then later with an Ubuntu installation cdrom (live session) on your clients in the LAN.

I recommend this because smbclient will give you proper error messages.
See again :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by KEKinSTL on 2009-01-12
BTW you mentioned:  "...and I don't know how to scroll up the screen..."

less is more:  for any file larger than your screen height, try this i.e.:
   ls -la  | less
<space> or <Page Up> or <Ctrl>+<U> and <Page Down> or <Ctrl>+<D> give page up and down.  Up and down arrows scroll line-at-a-time.
Ciao.
ken

---

### Post by volkswagner on 2009-01-12
> **lightningrod66 said:**
> Thanks for the info.  I am using the server edition so I can't use a gui tool.

I was hoping that Webmin would be for complete server configuration - not just Samba.

My server is using the same workgroup name, but there is still no connection between computers.  I do have internet access for the server, so I can download and install things.  I'm sure that somewhere I will see a setting or something that I didn't get right with Samba.

These forums are the greatest thing ever for learning!  I used to subscribe to the MaximumLinux forum before it went away :(


Did you install Webmin yet, not sure if you saw post #18.

Webmin can be used to configure so much.  It has a file upload/download tool plus a file browse tool.  You can do so much without even using samba.

---

### Post by lightningrod66 on 2009-01-12
> **KEKinSTL said:**
> BTW you mentioned:  "...and I don't know how to scroll up the screen..."

less is more:  for any file larger than your screen height, try this i.e.:
   ls -la  | less
<space> or <Page Up> or <Ctrl>+<U> and <Page Down> or <Ctrl>+<D> give page up and down.  Up and down arrows scroll line-at-a-time.
Ciao.
ken

I tried the PageUp and PageDown buttons, as well as the Up-Down arrows.  None of those worked.  Shift+PageUp or Shift+PageDown works though.

I will try the |less command next time to see what that does :)

Thanks for your info!

---

### Post by lightningrod66 on 2009-01-12
> **volkswagner said:**
> Did you install Webmin yet, not sure if you saw post #18.

Webmin can be used to configure so much.  It has a file upload/download tool plus a file browse tool.  You can do so much without even using samba.

I haven't been home since I saw that post.  I will download and install later tonight.

I looked at the website and it looks like a wonderful tool to use while you are learning how to do the same tasks via CLI :)

---

### Post by albinootje on 2009-01-12
> **lightningrod66 said:**
> I haven't been home since I saw that post.  I will download and install later tonight.

I looked at the website and it looks like a wonderful tool to use while you are learning how to do the same tasks via CLI :)

I've tried reinstalling webmin, and i noticed the no-script add-on in Firefox made webmin appear pretty badly since I forgot to allow localhost:10000, after allowing that it looks so much better :)

Thanks for reminding.

---

### Post by lightningrod66 on 2009-01-14
OK.  I have downloaded and installed Webmin.  It appears to be working as I can now access my server via the web.  I have one question left and that will probably be the end of this thread and we can consider it SOLVED.

My question is this:  I have installed SAMBA.  I am trying to share the /var/www directory so that I can put files into it from a Windows XP machine for my website.

I have the WORKGROUP set correctly, and I can see the shared directory on the Ubuntu server from my Windows machine.  I can even open the files.  The problem is that I cannot put any files INTO /var/www from the Windows machine.  It looks like I have read permission, but not write permission.  I played with the Samba settings for permissions, users, groups, etc and still have not got it.  When I look at the list of users in Samba, it doesn't show any Windows users, only Linux (Unix) users.  I cannot add a Windows user either.  I am sure it is just a matter of giving permissions to a Windows user, but I haven't figured out where to do that.  If someone knows how to get this thing right it will end my server issues altogether :)

The best case scenario for me would be if someone also was using Webmin and their Linux machine was on a Windows network and posted screenshots of where/how to do this.  CLI configs will also work though :)

---

### Post by albinootje on 2009-01-14
> **lightningrod66 said:**
> 
I played with the Samba settings for permissions, users, groups, etc and still have not got it. 

I've just tested it.
To have a Samba user, go to "edit samba users", find your own username, and change the password for that, with "new password".
Don't worry, this will change the password for your samba user, and not your already existing system "Unix" user.

To write via Samba in /var/www, use "force Unix user=root", and "force Unix group=root". 
See screenshot.

---

### Post by lightningrod66 on 2009-01-14
> **albinootje said:**
> I've just tested it.
To have a Samba user, go to "edit samba users", find your own username, and change the password for that, with "new password".
Don't worry, this will change the password for your samba user, and not your already existing system "Unix" user.

To write via Samba in /var/www, use "force Unix user=root", and "force Unix group=root". 
See screenshot.

Thanks.  That did it :)  I was confused because I was looking for a Windows user.

Thanks to all who assisted in this adventure for me.  It has been very educational!  We can now consider the case closed :)

---

