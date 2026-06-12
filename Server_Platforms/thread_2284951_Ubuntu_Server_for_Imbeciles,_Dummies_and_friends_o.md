---
title: "Ubuntu Server for Imbeciles, Dummies and friends of Idiots needed"
date: 2015-07-02
forum: Server Platforms
---

### Post by Admiral_Krank on 2015-07-02
Hi Guys,

OK, I'm not as deft as this title, but I need help with something I'm working on.  I'm making an Ubuntu server as a media centre (using Emby).  So far, I've managed to install emby and it's up and running.  Here's my overall objectives and issues to date:
(1) I want to have all the files served off the /srv directory - how can I permission ubuntu to allow me to edit folders, and add files within this directory?
(2) be able to copy files from windows - off and on.  I really don't know squat about core networking concepts and how they relate - for instance, I do't understand the difference between groups and domains.  I've installed samba, and I think that's what's allowing me to access some files if I'm accessing the server with a monitor.  But I would like to be able to access the server headless, per say, and push files from windows - using the linux server remotely - does anyone have some good high level (non verbose) recommendations on this topic?

For clarity, all the computers on my network are 192.168.2.1, 192,168.2.2, etc...  I think this is called the same IP range/subnet???

(3) access the server headlessly.  I'm going to give this server to a family member, at another location, and I'll need to either access and admin it remotely from my house, or from their house when I'm over, but again without a monitor, and likely from windows, any recommendations for resources?

Thanks

---

### Post by mastablasta on 2015-07-02
> **Admiral_Krank said:**
> 
(1) I want to have all the files served off the /srv directory - how can I permission ubuntu to allow me to edit folders, and add files within this directory?

it's probably "emby" or it's user that needs the access. chmod and chown should take care of that: 
e.g.

[http://ss64.com/bash/chown.html](http://ss64.com/bash/chown.html)
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

> 
(2) be able to copy files from windows - off and on.  I really don't know squat about core networking concepts and how they relate - for instance, I do't understand the difference between groups and domains.  I've installed samba, and I think that's what's allowing me to access some files if I'm accessing the server with a monitor.  But I would like to be able to access the server headless, per say, and push files from windows - using the linux server remotely - does anyone have some good high level (non verbose) recommendations on this topic?


it might be easier to just use sFTP along with WinSCP or Filezilla and this relates to item 3. of course you can always setup SAMBA. should be easy to setup. [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

> 
(3) access the server headlessly.  I'm going to give this server to a family member, at another location, and I'll need to either access and admin it remotely from my house, or from their house when I'm over, but again without a monitor, and likely from windows, any recommendations for resources?


install OpenSSH server and create identification keys. you can then use Putty on windows to administer the server via terminal. make sure you secure the server properly (since you plan to open its port to the web) or at least whitelist the IP that will access it. [https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

if you would rather administer a server via WebGUI have a look at Ajenti or maybe even Zentyal. though Zentyal is a bit more business oriented but it does aim for full compatiblity with Windows PC's. I like Ajenti as it has a built in terminal and "notepad" which is better and easier than nano or vim editors available on command line.

make sure you secure the server. I don't use hardening on media server since it is only on LAN, but you want to access it from the internet so be sure you harden it as much as possible. here is one guide: [http://hardenubuntu.com/](http://hardenubuntu.com/)

fail2ban will help stop (hinder) the hack attempts on ssh: [https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)

you will want automatic updates: [https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)

edit: looks like a lot of things to do. it otok me a while the first time. after disk died and I did it second time I used about 30 mins...

---

### Post by Lars Noodén on 2015-07-02
1) If the directory is not used for any other purpose and you are the only one using that particular directory, then you can change ownership of it to your own account and then have full write access:

```

sudo chown krank /srv/

```

If you are sharing write access, then a group is needed and there are a few different, but easy, steps needed.

3) The way to do remote access is via SSH and the package openssh-server provides that for you.  It also gives you an SFTP server as part of the deal which may or may not address #2, I can't answer about that other OS.  With SSH your access will be nearly 100% the same as local via the terminal, the main difference being you can't press buttons or change DVDs and so on.  But when you install the SSH server, you should also configure it so that you are using keys for authentication rather than passwords.  The reason being is that any machine connected to the Internet is being scanned more or less continuously and once the find remote access, they will start trying to guess the passwords.  Keys are the best way to interfere with that, say many.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Ask as needed as you go along.

---

### Post by TheFu on 2015-07-03
+1 on using ssh and setting up ssh keys.
Something not mentioned was when you deliver this machine to the remote location, you'll need to open the ssh port on their router and probably want to setup a dynamic DNS service to make finding their IP on the internet easy. Most home routers have support for 5 differnt dyndns providers - find a free one that doesn't make you manually login and confirm the account every month.  Of course, this is only necessary if the remote location is on a DHCP address from the ISP - pretty much every residential ISP does this.  It won't hurt to setup if the IP is static.  Oh - and you **Must** set the server with a static IP on the LAN (both in your house and when you move it to the other location.

Besides all of this the recommendations above are good.  I'd stay with only ssh and sftp to move files on and off the system. It will work on the LAN and over the internet when you have openssh-server setup correctly.  Samba is a hassle and will confuse many users since using samba over the internet is a bad idea. Using sftp over the internet is considered secure.

Windows programs - WinSCP, putty.
Any file browser on Linux has those sftp built-in and you can use any terminal you like to ssh into the remote machine.

It is likely that you will need a little stronger network knowledge to make this stuff work. IP networking over the internet doesn't "just work." It isn't hard to learn enough.  grc.com/sn ep. 25-30 or so explain what you need to know. The specifics are slightly different based on the OS, router, and your network.

---

