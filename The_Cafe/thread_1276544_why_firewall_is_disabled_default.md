---
title: "why firewall is disabled default?"
date: 2009-09-27
forum: The Cafe
---

### Post by abhilashm86 on 2009-09-27
hi friends, i want to know why in ubuntu, firewall is kept disabled?
is it better to disable firewall, 
my status in jaunty was, ```
abhilash@abhi:~$ sudo ufw status
Status: inactive
abhilash@abhi:~$ 

```
why does this happen, even check your firewall status, i want to know about why has it been disabled and any advantages!!

---

### Post by credobyte on 2009-09-27
If you don't hold a server, you don't need ( *usually* ) a firewall.

---

### Post by mcduck on 2009-09-27
> **abhilashm86 said:**
> hi friends, i want to know why in ubuntu, firewall is kept disabled?
is it better to disable firewall, 
my status in jaunty was, ```
abhilash@abhi:~$ sudo ufw status
Status: inactive
abhilash@abhi:~$ 

```
why does this happen, even check your firewall status, i want to know about why has it been disabled and any advantages!!

The default setup doesn't have any running services that would listen for incoming connections from network, so running a firewall would be pointless.

You only need to enable a firewall if you install any server software that listens for incoming connections.

---

### Post by lovinglinux on 2009-09-27
The firewall (iptables/netfilter) is actually not disabled, it always run in the background, but it has only allow rules, which means all traffic is allowed.

To see that, run this command:

```
sudo iptables -L
```

As already mentioned in previous replies, the firewall allows all traffic because there are no servers running by default, listening to any ports. So all traffic will be allowed to reach your machine ports, but they all be rejected, since all ports are already closed. You don't need a firewall rule to block a port that is already closed.

UFW is just a firewall manager. This one comes disabled by default, probably because not every user would use it. For instance, lots of people use Firestarter as the firewall manager (which I do not recommend). When you enabled UFW, it creates new iptables rules that block some traffic. Firestarter does the same thing. So if UFW comes enabled by default and the user install and activate Firestarter, it's iptables rules would overwrite UFW rules and possibly create some conflicts. So the user needs to enable UFW or install and activate another firewall manager or create iptables rules by itself.

---

### Post by The Cog on 2009-09-27
As has been said, Ubuntu (by default) has no runnng network services, so any incoming connection attempts will be rejected. So no need for a firewall to block unwanted connections.

Now imagine what would happen if you **did** have a firewall and you then decided to install a web server for instance. Because of the firewall, nobody would be able to connect to the webserver. So you would have to go into the firewall configuration and chenge it to allow incoming connections to the webserver. So all the firewall has done is to waste your time.

The reason windows needs a firewall is that it is so hard to find and disable all the network services (along with any security flaws they have) that windows runs by default. 

The most common reason you might want a firewall with Ubuntu would be whan you install a service and then want to restrict which IP addresses can connect to it. Often, a service can be configured to only accept connections from specified addresses, but not always, and then a firewall can be used to selectively block addresses. You can also use a firewall to rate-limit incoming connections. But in either of these instances, you know for sure you need a firewall. There is no point in installing a firewall "just in case". Linux isn't windows.

---

### Post by abhilashm86 on 2009-09-28
the explanation is worth billions, thanks friends:) i just disabled my firewall!!
yes when i used windows back 8 months before switching ubuntu, always windows told to enable and some problems......
also now i got the point, firewall is mainly for web-servers, 
i have 2 myths, just want to know its correct or why?
does enabling firewall will block certain ports? will firewall disable port forwading and make torrents slow??

---

### Post by lovinglinux on 2009-09-28
> **abhilashm86 said:**
> also now i got the point, firewall is mainly for web-servers

Not only for web servers. Any application that listen to a port is a server, that includes web servers, ssh servers, samba servers and BitTorrent clients. 

Most of the time a firewall is also not necessary when running servers. Why? Because if you are running a server, you probably want to let other machines to connect to it (BitTorrent for example), so blocking the port will prevent other user to accessing the service provided by the server. 

A firewall is useful if you are running a server but want to limit who can access it. For example you might want to run a ssh or vnc server to access your home desktop form your office computer, but also prevent other machines on the Internet to reach it. Then you can create a firewall rule that will allow only incoming traffic from the IP of your office computer. So, you will still be able to connect to your machine remotely, but minimizing the risks of an intruder doing the same. On the other hand, if you are using a BitTorrent client, you will want to connect to as many peers as you can, so blocking the access to the torrent port with the firewall will prevent other peers from requesting connections to your BitTorrent client.

> **abhilashm86 said:**
> i have 2 myths, just want to know its correct or why?
does enabling firewall will block certain ports?

Depends on the rules you create. I'm not sure about the default UFW rules, because I don't use it. But I guess when you enable it, all unrequested incoming traffic is blocked. UFW does not allow you to block outgoing traffic without tweaking config files, so all outgoing traffic is allowed. The incoming traffic related to outgoing requests originated from your computer is also allowed. For example, if you are using Bittorrent you will be able to request connections to other peers and download data from them (outgoing and related incoming), but they will not be able to request connections to you (unrequested incoming) unless you open the BitTorrent port in the firewall.

If you are interested in using UFW, you can install [GUFW](apt:gufw) which is a graphical interface to control UFW. That will allow you to easily create firewall rules.

> **abhilashm86 said:**
> will firewall disable port forwading...

It will not disable port-forwarding, because that is a thing you do on the router. Nevertheless, it will block the traffic forwarded by the router to your machine. So, in fact it has the same effect as disabling port-forwarding, but the traffic is blocked at different levels. When you disable port-forwarding in the router, the unrequested incoming traffic is stopped in the router, while the firewall will stop it before reaching the torrent port on your machine. To properly download torrents you need to properly forward the traffic to your machine/port and open the port in the firewall, otherwise incoming unrequested connections won't reach your BitTorrent client.

> **abhilashm86 said:**
> ..and make torrents slow??

Possibly, but not necessarily. I explain this properly in the tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). The tutorial also has instructions on how to open and troubleshoot ports, how does several factors affect torrent speed, how to troubleshoot connections speeds, how to protect your machine for torrent use and more.

---

### Post by Arup on 2009-09-28
As most of us are behind a NAT router using a PPPPoE connection, firewall is not needed as its redundant filtering. However for other connections, GUFW is there, so is the excellent Firestarter. Both are excellent GUI to the IP chains firewall.

---

### Post by 3rdalbum on 2009-09-28
Windows does require a firewall, because by default it listens to incoming ports that it doesn't need to listen to. To make matters worse, the programs listening are running as administrator and are a popular target for worms and other sorts of malware.

Ubuntu doesn't listen by default, and a personal firewall is only useful for blocking services that you **only want to access on that computer**. The only time you want to do that is if you are running Apache and PHP to test a website locally.

If you have a home network with some computers running Windows, or some Linux machines running various services, then you are usually protected by a firewall in your modem/router; this will allow local network access to your services, but block non-local access.

---

### Post by abhilashm86 on 2009-09-28
> **lovinglinux said:**
> 
Possibly, but not necessarily. I explain this properly in the tutorial [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). The tutorial also has instructions on how to open and troubleshoot ports, how does several factors affect torrent speed, how to troubleshoot connections speeds, how to protect your machine for torrent use and more.

thanks once again lovinglinux!! i'll go through your bittorrent and stuff n come back i've i have doubts, most of things are clearer now friends, i'm noob at network stuff, now understanding the concepts:)

---

### Post by Neezer on 2009-10-15
I have a similar question regarding firewalls and ubuntu.

I am running ssh right now as I am away from home. If I were to enable ufw would it cut me off from ssh? I have a server at home that I am working on configuring and I want to work on it while away. I'll be gone for a few weeks with lots of free time, so I don't want to risk losing my ssh connection.

If this is better asked in a new topic then let me know and I'll start one.

---

### Post by lovinglinux on 2009-10-15
> **Neezer said:**
> I have a similar question regarding firewalls and ubuntu.

I am running ssh right now as I am away from home. If I were to enable ufw would it cut me off from ssh? I have a server at home that I am working on configuring and I want to work on it while away. I'll be gone for a few weeks with lots of free time, so I don't want to risk losing my ssh connection.

If this is better asked in a new topic then let me know and I'll start one.

Yes, it will cut you off. But you can create a rule to allow incoming traffic on the ssh port, which usually 22. Keep in mind that you will probably get lots of hits from people trying to break in. So secure your ssh connection using authentication keys and other security settings.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by Neezer on 2009-10-15
I followed the steps to generate an ssh key on my ubuntu machine through ssh. I'm not sure if I am running off of the key system, or the password...

I logged out and then logged back in and still was prompted for my password.

I looked in my sshd_config file, and my pubkeyauthentication and rsaauthentication are turned on

```

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

```

not really sure what to do from here to secure up the system.

---

### Post by lovinglinux on 2009-10-15
> **Neezer said:**
> I followed the steps to generate an ssh key on my ubuntu machine through ssh. I'm not sure if I am running off of the key system, or the password...

I logged out and then logged back in and still was prompted for my password.

I looked in my sshd_config file, and my pubkeyauthentication and rsaauthentication are turned on

```

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

```

not really sure what to do from here to secure up the system.


Be careful if you don't have physical access to the remote machine, otherwise you might lock yourself out of it, when messing with authentication settings. That being said, I guess you need to disable password authentication in the ssh config. Then it will use only the key to log in.

---

### Post by Neezer on 2009-10-16
> **lovinglinux said:**
> Be careful if you don't have physical access to the remote machine, otherwise you might lock yourself out of it, when messing with authentication settings. That being said, I guess you need to disable password authentication in the ssh config. Then it will use only the key to log in.


Thanks. what about on the windows side? on my remote machine I am running putty. How do I get the key to my windows machine so that it will connect?

---

### Post by lovinglinux on 2009-10-16
> **Neezer said:**
> Thanks. what about on the windows side? on my remote machine I am running putty. How do I get the key to my windows machine so that it will connect?

I don't use putty, but check [this](http://www.linuxjournal.com/article/8904). Scroll down to the "Automating the Connection"

---

### Post by CharlesA on 2009-10-16
> **Neezer said:**
> Thanks. what about on the windows side? on my remote machine I am running putty. How do I get the key to my windows machine so that it will connect?

You can add the key to putty: [http://www.aota.net/Telnet/puttykeyauth.php4](http://www.aota.net/Telnet/puttykeyauth.php4)

EDIT: I have my firewall set to only accept connections from specific IP addresses. If you are connecting from the same network all the time, you can add those IP addresses to the firewall rules so that you can be a bit more secure.

e.g., it'll drop everything that is on the port yer SSH server is listening on that is **not  **coming from the IP address you specified.

---

### Post by lovinglinux on 2009-10-16
> **CharlesA said:**
> EDIT: I have my firewall set to only accept connections from specific IP addresses. If you are connecting from the same network all the time, you can add those IP addresses to the firewall rules so that you can be a bit more secure.

e.g., it'll drop everything that is on the port yer SSH server is listening on that is **not  **coming from the IP address you specified.

+1 for that

---

### Post by mike555 on 2009-10-16
if any person is still on dialup starting the firewall might be a good idea , but if you have dsl or cable modem it probably has a firewall builtin ...... there are websites that will check your computer for leaks ... like ...    [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Neezer on 2009-10-16
> **CharlesA said:**
> You can add the key to putty: [http://www.aota.net/Telnet/puttykeyauth.php4](http://www.aota.net/Telnet/puttykeyauth.php4)

EDIT: I have my firewall set to only accept connections from specific IP addresses. If you are connecting from the same network all the time, you can add those IP addresses to the firewall rules so that you can be a bit more secure.

e.g., it'll drop everything that is on the port yer SSH server is listening on that is **not  **coming from the IP address you specified.

I went through the process on that website, and generated a private key and stuff....then I put the settings into putty, but i'm still being asked for my username and password when I log on to my ubuntu box.

do I need to edit my sshd_config file to not allow password login? 

It is my understanding that the private key is on the host machine (in this case, my server box) and the public key can be put on any machine wishing to log into the host. I am not really sure how I got the private key onto the ubuntu box.

I went into my .ssh/authorized_keys file on my ubuntu server box and all it says is "paste public keys contents here" which comes from the line I was told to enter in the key authentication process that I was following.

---

### Post by CharlesA on 2009-10-16
> **Neezer said:**
> I went through the process on that website, and generated a private key and stuff....then I put the settings into putty, but i'm still being asked for my username and password when I log on to my ubuntu box.

do I need to edit my sshd_config file to not allow password login? 

It is my understanding that the private key is on the host machine (in this case, my server box) and the public key can be put on any machine wishing to log into the host. I am not really sure how I got the private key onto the ubuntu box.

I went into my .ssh/authorized_keys file on my ubuntu server box and all it says is "paste public keys contents here" which comes from the line I was told to enter in the key authentication process that I was following.

It's the other way around. You need the public key on the server and private key on the machine that wants to connect. You add the public key to authorized_keys.

For my install I used the ssh-keygen to create the keys then transfer the private key to my windows machine and used putty-gen to convert it to a key that putty could use.

If you need to know the settings, I'll SSH into my server and post the sshd_config file.

---

### Post by Neezer on 2009-10-16
> **CharlesA said:**
> It's the other way around. You need the public key on the server and private key on the machine that wants to connect. You add the public key to authorized_keys.

For my install I used the ssh-keygen to create the keys then transfer the private key to my windows machine and used putty-gen to convert it to a key that putty could use.

If you need to know the settings, I'll SSH into my server and post the sshd_config file.

so this is what I have in my .ssh folder

```

nate@server:~/.ssh$ la
.  ..  authorized_keys  id_rsa  id_rsa.pub  known_hosts

```

the id_rsa has a file with a bunch of letters and numbers and stuff....I think that is my private key. and then id_rsa.pub and just one very long line of letters numbers and a few symbols...

So should I be able to take copy paste the private key into a notepad or something? then use puttygen to make it a key?

---

### Post by CharlesA on 2009-10-16
> **Neezer said:**
> so this is what I have in my .ssh folder

```

nate@server:~/.ssh$ la
.  ..  authorized_keys  id_rsa  id_rsa.pub  known_hosts

```the id_rsa has a file with a bunch of letters and numbers and stuff....I think that is my private key. and then id_rsa.pub and just one very long line of letters numbers and a few symbols...

So should I be able to take copy paste the private key into a notepad or something? then use puttygen to make it a key?

id_rsa.pub is the public key. You add the public key to authorized_keys.

```
cat id_rsa.pub >> authorized_keys
```

Copy the private key over to the windows box, run it thru putty-gen and then tell putty to use that key.

You should be able to connect.

Sidenote: Until you are 100% sure that you have the keys working correctly, do **not** disable password logins. I did that and ended up having to go to the local machine to reenabled password logins.

---

### Post by Neezer on 2009-10-16
> **CharlesA said:**
> id_rsa.pub is the public key. You add the public key to authorized_keys.

```
cat id_rsa.pub >> authorized_keys
```

Copy the private key over to the windows box, run it thru putty-gen and then tell putty to use that key.

You should be able to connect.

Sidenote: Until you are 100% sure that you have the keys working correctly, do **not** disable password logins. I did that and ended up having to go to the local machine to reenabled password logins.

I see what you mean. I went through the process of copying the id_rsa file into a text file in windows. I used puttygen to create a private key from it.

I went Conversions -> import key

went through the process of everything and then got this

```

Server refused our key
nate@75.71.165.69's password:

```

so the server wouldn't accept my key, but since I haven't disabled the password login, i am still able to get into my server

If I delete the files

~$/.ssh/id_rsa
~$/.ssh/id_rsa.pub

then remake the keys via command line, I should be able to go through this process again right?

I didn't write down the passphrase I used to create the keys on my ubuntu server, so I am not 100% sure I used the correct one when I generated the private key using puttygen.

I'm going to try to recreate a new public key on my ubuntu machine and see what happens.


**EDIT: SUCCESS **

so before going through the work above, I looked in my authorized keys file, and it still said paste key here. so I put the key in there and everything worked great!!! I think I'm going to wait until I am at home in 3 weeks before I go and turn off the password option in the sshd_config file.

---

### Post by CharlesA on 2009-10-16
If you aren't going to disable the password login, you should have something like fail2ban or denyhosts to block ip addresses after xx failed login attempts.

---

### Post by OpenGuard on 2009-10-16
To make this forum more active ? At least a few threads per day ( ok, maybe less than that .. who cares ) on how to enable ( or why it's disabled ) firewall.
From my point of view, firewall SHOULD be enabled by default - it would decrease the fear level that something might go wrong.

---

### Post by Neezer on 2009-10-16
> **CharlesA said:**
> If you aren't going to disable the password login, you should have something like fail2ban or denyhosts to block ip addresses after xx failed login attempts.

are these applications that I can install, or are they options that I can code into my sshd_config file?

EDIT: google is my friend!

fournd this: [http://setdosa.blogspot.com/2008/11/fail2ban-ubuntu-804-server-hardy.html](http://setdosa.blogspot.com/2008/11/fail2ban-ubuntu-804-server-hardy.html)

followed directions for setting it up. It should be running....but I have no idea how I might test it other than try to log in with a password a few times and see if I get banned. But then I would be stuck not being able to log in.

---

### Post by misfitpierce on 2009-10-16
UFW is disabled maybe by default but the IPTables are auto on by default with all ports closed up and locked down by default.

---

### Post by FuturePilot on 2009-10-16
> **misfitpierce said:**
> UFW is disabled maybe by default but the IPTables are auto on by default with all ports closed up and locked down by default.

No. There are no rules in iptables on Ubuntu by default.

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by hoppipolla on 2009-10-16
Linux doesn't keep many ports open by default and is largely secure, so you usually don't need one. Plus, most people are behind router hardware firewalls. And Linux doesn't get many viruses if any anyway :)

I use one regardless though... lol :)

> **misfitpierce said:**
> UFW is disabled maybe by default but the IPTables are auto on by default with all ports closed up and locked down by default.

Oh maybe, to be honest I don't understand much about the way IPTables works :)

---

### Post by Sam on 2009-10-16
> **OpenGuard said:**
> From my point of view, firewall SHOULD be enabled by default - it would decrease the fear level that something might go wrong.

Do you want an antivirus too? Sorry, but no. A little education is needed here for the users, but for the zillionth time, linux is not windows!

---

### Post by OpenGuard on 2009-10-16
> **hoppipolla said:**
> Linux doesn't keep many ports open by default and is largely secure, so you usually don't need one. Plus, most people are behind router hardware firewalls. And Linux doesn't get many viruses if any anyway :)

I use one regardless though... lol :)



Oh maybe, to be honest I don't understand much about the way IPTables works :)

Linux got root.

---

### Post by lovinglinux on 2009-10-16
> **CharlesA said:**
> If you aren't going to disable the password login, you should have something like fail2ban or denyhosts to block ip addresses after xx failed login attempts.

Disabling the password authentication doesn't mean anyone can log in. The OP is trying to use key authentication, so disabling the password is part of the process, so only machines with authorized keys can log in.


> **misfitpierce said:**
> UFW is disabled maybe by default but the IPTables are auto on by default with all ports closed up and locked down by default.

No, iptables is always running, but they allow all traffic by default, as already mentioned. Nevertheless, the ports are already closed because there is no server listening to any ports. So any incoming unrequested connections will be refused, even with the firewall allowing all traffic.

---

### Post by OpenGuard on 2009-10-17
> **Sam said:**
> Do you want an antivirus too? Sorry, but no. A little education is needed here for the users, but for the zillionth time, linux is not windows!

You are just kidding, right ? Every single user on Windows should have a firewall and anti-virus; every single user on Linux should have a firewall ( unless properly configured, iptables is *not *a firewall ).

---

### Post by 3rdalbum on 2009-10-17
> **OpenGuard said:**
> You are just kidding, right ? ...every single user on Linux should have a firewall ( unless properly configured, iptables is *not *a firewall ).

If you do not have any programs listening to incoming ports, then you don't need a firewall. But I think the person you were replying to was talking about personal firewalls; if you're on a network that's already behind a NAT firewall, then you don't need a firewall on the client as well. Windows users sometimes seem to think that a firewall performs the same function as anti-virus, you know: "If the first firewall doesn't stop the viruses, then maybe the second one will".

---

### Post by Sam on 2009-10-17
> **OpenGuard said:**
> You are just kidding, right ? Every single user on Windows should have a firewall and anti-virus; every single user on Linux should have a firewall ( unless properly configured, iptables is *not *a firewall ).

I was kidding you with the first sentence, but I'm totally serious for the latter.

There is no need to block ports that are NOT open. It does not add an additional layer of security.

---

