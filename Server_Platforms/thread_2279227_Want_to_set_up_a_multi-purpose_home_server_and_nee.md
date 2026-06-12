---
title: "Want to set up a multi-purpose home server and need help getting started"
date: 2015-05-22
forum: Server Platforms
---

### Post by Silman on 2015-05-22
Hello All!
I want to build a home server for the following purposes:

* store files/media as a backup from PCs who have access to it  
* Stream said media to specific computer connected to it or to a TV connected to the server
* Game server for minecreaft/terraria/etc (this will not be running 100% of the time and i will want to turn it off and on in order to free up memory for other tasks when needed
* Host webpages to the internet (if i can connect it to the internet)

I want it to have multiple account so many users in the home can have their own files on it with private permissions.

I also would prefer if i could access it from the internet if possible. This way if i really need to i can connect to it from anywhere and pull files from it. I know this actually may be really difficult since my external IP may not be static (As many companies such as comcast, the ISP i'm unfortunately on) actually may change your external IP occasionally (but not very often). I know there are work arounds for this though.


A little background about myself:

I am a Physics and Electrical Engineering Major with a minor in computer science. I do know a fair share of C,C++, and python. But i do not know PHP or other server languages. I have familiarity with windows/osx/linux, but my linux/terminal skills are not top notch.

I have tried to set up a webserver in the past but school got in the way so i became too busy to pursue it. Now i have more time and want to make a home media server which also can host games and serve up webpages to the internet.

How do i begin doing all this? How do i make sure the server is compatible with windows/OSX/Linux. 

I was hoping to make it a linux server since i know its probably the best (although i am not a linux master). 

If i can connect it to the internet (so i can access these files from anywhere) how do i secure it? How do i make it so only specific users can log in?

I have a computer in mind, [here are it's specs]([http://www.cnet.com/products/hp-pavilion-a6750y/specs/](http://www.cnet.com/products/hp-pavilion-a6750y/specs/)). It's got no additional upgrades (so it has the RAM it came with - 8GB). Everything that it comes with is what it has, its a little old but its what i got already so i want to try it out.

[FONT=verdana]I have the hardware I listed. Its a very old (read: 6 year) desktop I got a while back. I want it to be partly project but with an easy learning curve. I dont want to write my own streaming service application but I don't want it to all be "set it and forget it" as I do want to learn the basics of networking devices and connecting servers to the internet for file transfer/remote control/ etc[/FONT]
[FONT=verdana]I don't know if virtualizing everything is the best for two reasons: 1) virtualization requires much more RAM 2) it seems kind of complex for this job[/FONT]
[FONT=verdana]I want to be able to have full control of everything remotely too, and if a virtual machine goes down how could i start it remotely? (maybe this isnt actually an issue)[/FONT]
[FONT=verdana]I've looked into some things like Plex and OwnCloud but i want to make sure they integrate (i.e. i can upload media to the server with OwnCloud which Plex can then stream). I am totally open to alternatives, i only mention plex and OwnCloud because they came up in my research.[/FONT]

[FONT=verdana]can you access your owncloud from outside your local LAN?

 Can i point my server to the internet using NameCheaps Dynamic DNS service and be able to upload/download from anywhere?[/FONT]
[FONT=verdana]
I i wanted could i have the server display a desktop? Or is that ubuntu desktop only? If i had my server connected to a TV is it possible to open up chrome on the server and be able to use netflix as i would a normal computer? Or can servers not have GUI windows, only text?[/FONT]
[FONT=verdana]
I have somewhat of a fear of not having GUI windows. For instance, how can i download and set up NameCheaps Dynamic DNS client i can open chrome to download it. How do i configure it if i can click the buttons to configure it? How do i know its running when i restart the server or at all while the server is on?[/FONT]

---

### Post by darkod on 2015-05-22
For sharing files use Samba, that is compatible with windows and linux, and I believe OSX too. You will have multiple users on the servers and each can have private folders that only them can access.

For streaming you can use minidlna, mediatomb, or similar. There is a number of packages available.

Dynamic DNS is not an issue also. Note that your home router might offer DDNS too, so you can do it on router level if you have access to it and if you prefer it. If not, there is also a number of DDNS clients for ubuntu server. Not sure if Namecheap DDNS is one of them, you can check their website. If there is, most probably it will be installed and configured from the command line, no need for GUI download and configuration. If I'm not mistaken there is a noIP client for ubuntu. That is also one popular DDNS service.

Hosting web can be done by apache2 or nginx (which might be simpler to setup and mantain).

Opening the server to the internet has to be done carefully. Never open too much, just the minimum you need (just the ports you need). It would be best if you limit the outside access to specific IPs but if you plan to access it from different places (different networks) you can't really use source IP filtering. You will not know the public IP where you are connecting from.

The same as above applies for you having remote access. The most recommended is probably sftp or scp. It also depends on the OS you plan to connect from. DO NOT use plain unsecure ftp. The scp option might be best because it uses the same ssh port as ssh access. And you can configure it to work with ssh key only, not with a password. That way you can avoid someone trying to get in by guessing a password.

There is plenty of info and tutorials for ubuntu on the web. When you start if you get stuck with something come back with a more specific question.

As for hardware, most HW is good enough for ubuntu server because it doesn't take much resources. Unless you have bad luck and it doesn't support some of the HW but that is very rare.

You can have a GUI on the server but that is not a very good idea. First, it will consume more resources and most of the time there is no need for that. And from security point of view a GUI gives more options for attacks especially if you put the server on the internet. Your home router firewall is usually a good protection from outside attacks but anyway be careful.

---

### Post by Silman on 2015-05-22
Thanks for the reply.

I will be accessing the server from windows, linux, and OSX (OSX and windows the most, linux rarely).

I have heard Plex is good for streaming too, is this a good option?

And OwnCloud for file uploading, does samba have users with private folders?

The GUI i wouldnt want all the time, just occaisionally. But its not necessary if its too much of a hassle.

---

### Post by TheFu on 2015-05-22
darkod speaks the truth.
Inside the LAN, I use samba for Windows-to-Linux file access.
Inside the LAN, I use NFS for Linux-to-Linux file access (even for the same places shared through samba).
Outside the LAN, I use sftp. If you install ssh, you get sftp for free. Be certain to install fail2ban to block brute force attacks quickly.

I use plex. Works great inside the LAN, if you don't need any security for file access. That's a problem with all DLNA servers - zero security.  You can use the system firewall to block all except specific static IPs on the LAN from plex access if you like. 

I wouldn't use OwnCloud without a full VPN like openVPN. The security just isn't very good otherwise, IHMO.

DynDNS is easy to setup. Most routers have built-in support. There are free versions, so check the list that your router has and pick from that.

As to what you can, cannot and should not do around GUIs and connectivity to the internet - that is something that completely depends on your risk factors.  I would NEVER run a web server on the same machine I use for internal file sharing. It is just too risky, IMHO.  Web servers get popped every day and if you aren't an expert at web server security, you should expect to be hacked. Plan on it.  Be certain to have excellent backups, versioned, off site too.

Good general questions. When/if you have specific questions, it is best to ask 1 at a time and have a clear, concise title.

---

### Post by Lars Noodén on 2015-05-22
> **TheFu said:**
> Outside the LAN, I use sftp. If you install ssh, you get sftp for free. Be certain to install fail2ban to block brute force attacks quickly.


+1

I use sftp and rsync (which also goes over SSH these days) both locally and remotely so I can have the same method both on the LAN and Internet.  In addition to fail2ban, there is also [sshguard](http://www.sshguard.net/) which does about the same thing as fail2ban, despite the name.  In some aspects it is better, so take at least a glance at both before choosing.  Anyway, SFTP works great for Linux and, back when I had it, OS X anywhere there is connectivity.  The only shortcomings I can complain about are that the Linux file managers don't support keys yet and the OS X file manager does not support SFTP yet.  However, the regular shell utilities on both operating systems do support keys and are identical on both OS X and Linux, so transition between using the two systems is pain-free and secure.  

The web servers *themselves* are probably fine if you are serving static pages or SSI with noexec ... BUT ... web applications that you add on top are definitely not fine and will require constant monitoring and readiness to update.

---

### Post by TheFu on 2015-05-22
There are great sftp clients for **every** platform.  WinSCP is good on Windows. Filezilla is another popular option.  Android, iOS, Maemo and every platform I know with IP networking has an sftp client. Do not confuse sftp with ftps or "plain ftp" - these are NOT the same. You want sftp.

When going over the internet, using keys is necessary. If you use passwords, you've already failed, IMHO.  ssh-keys are one of those security things that is both more secure AND more convenient. Hard to believe, I know.

Just tested pcmanfm (a Linux file manager) with sftp (URI: sftp://hadar/ ) ... keys are definitely used, so I don't know understand what Lars means when he says keys aren't supported?  Perhaps the generation of keys just isn't possible from inside the file managers, but the keys do for for connections. I don't use nautilus or thunar, but I'd be surprised if pre-made ssh-keys didn't work.

---

### Post by Lars Noodén on 2015-05-22
Nautilus and Thunar do not support keys.  But it's good to hear that PCManFM now does.  Keys are necessary.

---

### Post by TheFu on 2015-05-22
> **Lars Noodén said:**
> Nautilus and Thunar do not support keys.  But it's good to hear that PCManFM now does.  Keys are necessary.

So I tested from a different desktop that has thunar. The sftp connection "just worked" and I don't know how it would work without keys. My keys are in the default locations and had already been unlocked for the day.  Also, I use ssh-agent.

Found this: 	
> If you're using Gnome, you can go to: Places -> Connect to Server in nautilus and choose SSH. If you have a SSH agent running and configured, no password will be asked! (This is the same as sftp://userid@servername/directory in Nautilus) [https://stackoverflow.com/questions/299412/is-there-any-winscp-equivalent-for-linux](https://stackoverflow.com/questions/299412/is-there-any-winscp-equivalent-for-linux)

---

### Post by Lars Noodén on 2015-05-22
> **TheFu said:**
> So I tested from a different desktop that has thunar. The sftp connection "just worked" and I don't know how it would work without keys. My keys are in the default locations and had already been unlocked for the day.  Also, I use ssh-agent.

Found this: 	
 [https://stackoverflow.com/questions/299412/is-there-any-winscp-equivalent-for-linux](https://stackoverflow.com/questions/299412/is-there-any-winscp-equivalent-for-linux)

Interesting.  On several iterations of Ubuntu 14.04 LTS, keys and file managers have not (and do not) worked for me, even with the key loaded into ssh-agent.  But on another machine Lubuntu 14.04 both nautilus and pcmanfm work fine with keys and they will even ask for the key's passphrase. ... I have just tried a fresh installation of plain Ubuntu 14.04 LTS in a VM and Nautilus works there with keys, unlike my regular account on my regular machine.  So I am happy to have been wrong there and I guess Nautilus actually does support keys.  However, now I have to search for whatever cruft I have in my regular account that prevents Nautilus or the others from finding the agent.

@Silman, I stand corrected.  Keys work with the current linux file managers.

---

### Post by TheFu on 2015-05-22
~/.ssh/* permissions?  600 is generally needed there for everything except the .pub (public key files). Plus the dir must be 700.
Since I switched over to using **ssh-copy-id** to push keys around, haven't had that issue.

If that isn't it, we can try swapping SSH-AGENT setup stuff, if you like.

---

### Post by Lars Noodén on 2015-05-24
> **TheFu said:**
> ~/.ssh/* permissions?  600 is generally needed there for everything except the .pub (public key files). Plus the dir must be 700.
Since I switched over to using **ssh-copy-id** to push keys around, haven't had that issue.

If that isn't it, we can try swapping SSH-AGENT setup stuff, if you like.

Thanks.  The agent works fine, I use it all the time with the native clients.  It's just that with the file managers, I've got something different.  Cogitating some while, I recall now [bug 1195911](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1195911) and having to work around it.  Currently, the keyring causes choking on more than a small number of loaded keys.  The file managers seem to obey ssh_config's settings, so a work-around is to create a host shortcut there that includes a specification of [IdentityFile](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html) set explicitly for that host.  In fact, that's probably the only way to deal with more than a few keys until such time as the SSH protocol supports some kind of authentication key negotiation.

@Silman, there are now a lot of options for using keys and graphical file transfer.

---

### Post by TheFu on 2015-05-24
I use the ~/.ssh/config file extensively and have 50+ hosts inside that file. That probably explains it.  I like to use it as documentation (and settings) for my seldom used logins.  I think any tool that is based on libssh will use it. It is nice not having to remember userids and odd port numbers.

---

