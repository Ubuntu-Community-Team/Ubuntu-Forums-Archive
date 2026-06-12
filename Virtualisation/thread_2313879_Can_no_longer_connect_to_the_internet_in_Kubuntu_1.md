---
title: "Can no longer connect to the internet in Kubuntu 14.04 VirtualBox VM"
date: 2016-02-16
forum: Virtualisation
---

### Post by spacer.x-infinity on 2016-02-16
Hi everyone,
I'm new to the forums and to Linux in general. I'm not even sure if I'm posting this in the right place because, while it's a specialized problem I'm experiencing, my level of linux knowledge is *far* from specialized. 

Anyway, here's what I'm trying to do:

I have two laptops, one of which is a Toshiba Satellite L-500 with a hard install of Kubuntu 14.04 and the other of which is a Samsung 305V4A running a Windows 7 Home Premium host and a Kubuntu 14.04 VirtualBox VM. Over the past few days, I've been trying to configure an SSH server to run on key-based authentication between my main Kubuntu system and the VM on the other laptop. Prior to my attempt at configuring key-based authentication, I'd already been successful at downloading and installing the *openssh-server* package on both systems, setting the the VM to "Bridged" mode, and SSHing into it from the Toshiba. 

However, ever since I tried to configure key-based authentication, I notice that the VM displays the "Booting system without full network configuration" message upon start-up. When it's finally booted and I click on Firefox, it just says "server not found." I've read threads both on this forum and others from people who have had similar problems but none that were quite the same and none of which provided any solutions. As per one suggestion, I tried running the *dmesg | grep eth0* command in the VM's terminal window just to diagnose the problem and noticed a line that read "e1000: eth0 NIC Link is Down."

Also, when I run the command *sudo ssh 192.xxx.x.xxx* from the other computer and enter my password when prompted for it, I get a message that says "Permission denied (publickey)." Now, as far as know, I was able to successfully trade public keys between the two systems with the *scp ssh_host_dsa_key.pub 192.xxx.x.xxx* command. I was under the impression that, once key-based logins was successfully configured, I could SSH between the two systems without having to enter a password. 

What exactly am I doing wrong? How do I restore my VM's internet connection and properly configure key-based SSH logins between the two computers? :confused:

Any help would be most appreciated.

---

### Post by TheFu on 2016-02-16
Best to ask this in the virtualization sub-forum to begin, since that is commonly the issue.

A) verify that the IP address of all the machines didn't change.
B) verify that the "cable connected" checkbox for the VM settings inside virtualbox didn't get de-checked.
C) Did you setup the VM with wifi or with wired ethernet on the hostOS?  Is that still the method being used?
D) Windows firewall not blocking inbound connections?
E) Still using a "bridged" connection?

Let's start with those for now.  Please answer all.

---

### Post by spacer.x-infinity on 2016-02-16
Answers are as follows:

A) Ran *ifconfig* on both machines and discovered that all IPs are the same as when I began SSH public key configuration. In fact, prior to even attempting this, I recall editing the *interfaces* file in the VM's */etc/network* directory and setting all IPs associated with eth0 to 'static.'
 B) "Cable connected" setting is currently checked.
C) Set up the VM on a WIFI connection and that is what I'm still using.
D) Windows Firewall "Incoming connections" setting reads "Block all connections to programs that are not on the list of allowed programs." This didn't seem to pose any connection problems prior to configuring key-based SSH logins and I'm not exactly sure why. My understanding was that any programs launched within the VM were autonomous from the host OS. In any case, is this creating a problem for me and what can I do to fix it?
E) Yes, the connection is still set to "bridged."

Anyway, thanks for any help you can provide. Also, if a mod feels the need to move this thread to the 'virtualization' sub-forum, then that's fine by me; but, if not that's cool too.

Cheers.

---

### Post by TheFu on 2016-02-16
On the ssh server-side - what are the permissions for ~/.ssh/ and the files inside it?  If you used ssh-copy-id to push the keys over, it should be fine. If you did it manually, the umask may have "helped" you in a way that won't work.

Next step is to run the ssh-server daemon in debug mode and watch the inbound connection fail. If the debug messages don't happen, then a firewall or something on the client is preventing it.   Thought I'd written an article about troubleshooting ssh connections ... can't find it now. I'll keep looking.

wifi is problematic for connections (IMHO). Is it all still working on the hostOS?  I've done over 1200 wifi deployments and always avoid it whenever possible.

Update: found the draft article from August. Hasn't been published and I didn't re-read it now.
> 
Most of these steps really aren't necessary - they are included just to see if something commonly addressed automatically has been screwed by you or the network guys.  It is almost never the network, so be nice before accusing others for your mistake.

# Verify the ssh server is running/installed - service ssh status
# Verify the firewall isn't blocking it  - iptables -L
#* server-side firewall - lsof
#* client-side firewall - lsof
#* any edge routers blocking (this can be ingress and egress routers) - have to login to each router and look for blocking.
# Verify IP connection is working - ping IP
# Verify name resolution is working - ping hostname
# Check remote ssh server directory and file permissions are strict.
#* ~/.ssh/ must be 700 and owned by the remote userid
#* ~/.ssh/* - all files should be 600 and owned by the remote userid - especially authorized_keys, authorized_keys2, config, id_rsa, known_hosts.
#*  1 file can be 644 ... id_rsa.pub - public keys can be less strict.
# Test from localhost - ssh localhost - did that work?
# Test from another system on the same LAN - ssh remoteUser@LAN-IP - did that  work?
# Test from another system on the same LAN using the hostname - ssh remoteUser@LAN-hostname - did that work?
# Test over the internet - ssh remoteUser@WAN-IP - did that work?

The tests above will isolate the type of issue.  If the default configuration files in /etc/ssh/ have been modified, put them back to the original settings and try again. Restart the ssh-server daemon.

If you are using passwords, try ssh-keys. If you are using keys, try passwords be certain to put back the keys after!!!).  Passwords should NEVER be used over the internet.  ssh-keygen, ssh-copy-id are some important tools.

All server-side settings belong in /etc/ssh/sshd_config.
Client-side settings belong in either /etc/ssh/ssh_config or ~/.ssh/config - use the user, client-side settings to control aliases, non-standard ports and different userids for remote systems.

Lots of assumptions above:
* No networking issues exist. That is addressed in "another article":/2013/03/01/linux-troubleshooting-101-networking.
* _server_ has a static IP on the LAN.
* _default port_ 22/tcp, is used.
* double NAT adds complexity. If you use this, you need to handle those added complexities.
* Name resolution is working on the LAN - that can be DNS, /etc/hosts.  I suppose avahi/zeroconf might work, but I remove that on every system do to bad luck with it previously.
* _router_ WAN ports for ssh forward to internal LAN server IP port 22/tcp. Feel free to use port translation from a different port on the WAN side of the router to the LAN side. Some netgear home routers do not support this feature.
* ssh security is addressed in "another article":/2011/08/23/securing-ssh-connections-and-blocking-failures.
* ssh capabilities are addressed in "another article":/2014/09/23/you-don-t-know-ssh-about-ssh.

Does this cover most things for ssh troubleshooting?
What is missing?

The links to other articles are relative on my blog. Anyway, hope this helps.

---

### Post by spacer.x-infinity on 2016-02-17
TheFu:

To answer your question about the permissions of ~/.ssh and its contents, the *ls -ld ~/.ssh* command yields the following output:

```
drwx------ 2 primary-user primary-user 4096 Feb 15 17:17
```

And, from the *ls -l ~/.ssh* command:

```

-rw-r--r-- 1 primary-user primary user 626 Feb 15 17:13 192.xxx.x.xxx 
-rw-rw-r--1 primary-user primary user     0 Feb 15 17:17 authorized_keys
-rw------- 1 primary-user primary-user 751 Feb 15 17:10 id_dsa
-rw-r--r-- 1 primary-user primary-user 626 Feb 15 17:10 id_dsa.pub
-rw-r--r-- 1 primary-user primary-user 666 Feb 15 17:15 known_hosts

```

I also noticed that, when I ran the *service ssh status* command on both machines, it returned the text *status: Unknown job: ssh.* This struck me as odd considering that I specifically remember installing the *openssh-server* package on each of them.

Regarding my use of a WIFI connection to configure SSH, while it may not be ideal, it is pretty much my only option considering that it is a home network that I don't personally own and that other people use. On the plus side, the only place that the network connection seems to be failing is within the VM itself and not on the Windows 7 host or the or the remote machine with the Kubuntu 14.04 hard install.

Hope this info gives you a little more to work with in devising a solution.

---

### Post by slickymaster on 2016-02-17
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by spacer.x-infinity on 2016-02-17
By the way, I also ran the ssh-server daemon in debug mode using the */usr/sbin/sshd -d -p 2222* command as suggested [here]("http://www.unixlore.net/articles/troubleshooting-ssh-connections.html"). Not exactly sure what all of this means but thought the info might be useful:

```

debug1: sshd version OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: could not open key file '/etc/ssh/ssh_host_rsa_key': Permission denied
Could not load host key: /etc/ssh/ssh_host_rsa_key
debug1: could not open key file '/etc/ssh/ssh_host_dsa_key': Permission denied
Could not load host key: /etc/ssh/ssh_host_dsa_key
debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key': Permission denied
Could not load host key: /etc/ssh/ssh_host_ecdsa_key
debug1: could not open key file '/etc/ssh/ssh_host_ed25519_key': Permission denied
Could not load host key: /etc/ssh/ssh_host_ed25519_key
debug1: setgroups() failed: Operation not permitted
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: rexec_argv[2]='-p'
debug1: rexec_argv[3]='2222'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 2222 on 0.0.0.0.
Server listening on 0.0.0.0 port 2222.
debug1: Bind to port 2222 on ::.
Server listening on :: port 2222.

```

---

### Post by TheFu on 2016-02-17
sshd must be run as root. That's the error above with the *permission denied*. Use **sudo**.

File permissions in ~/.ssh/ are wrong. Fix those as already spelled out above.

Also, please edit all the copy/paste and please use code-tags [http://blog.jdpfu.com/code_tags](http://blog.jdpfu.com/code_tags) so things line up. Much easier to read. Also, show the EXACT COMMAND you typed with the output. We don't want to guess or assume, copy/paste is safer.

Wifi isn't an issue for ssh, it is an issue for all connectivity. Computers know that wifi sucks and that bandwidth is constantly changing with all wifi connections.  Humans don't see this. The main concern is for people who change between wired and wifi connections on the hostOS - this causes the VM to see 2 different NICs, even if both are configured as e1000. If you stay with only wifi, that confusion should be minimal - until it isn't (first time you connect with wired ethernet and try to run the VM. I speak from experience. Or perhaps I'm just dumb. ;)

```
hadar:~/.ssh$ ll
total 44
drwx------  2 thefu thefu 4096 Aug 20  2014 ./
drwxr-xr-x 23 thefu thefu 4096 Feb 16 11:24 ../
-rw-------  1 thefu thefu 3115 Jul  8  2015 authorized_keys
-rw-------  1 thefu thefu 1750 Sep 25  2013 config
-rw-------  1 thefu thefu 1679 Sep 25  2013 id_rsa
-rw-r--r--  1 thefu thefu  390 Sep 25  2013 id_rsa.pub
-rw-------  1 thefu thefu 5992 Jul 18  2015 known_hosts
-rw-------  1 thefu thefu 4658 Aug 20  2014 known_hosts.old
-rw-rw-r--  1 thefu thefu  468 Oct 14  2013 putty-key.pub
```
See how the pub keys aren't locked down, but everything else is?  ssh checks for this.
Also, note how easy it is to read when things line up?

---

### Post by spacer.x-infinity on 2016-02-18
.

---

### Post by spacer.x-infinity on 2016-02-26
Update:

Alright, after more than a week of bumbling around trying to restore my network connection and configure SSH public key authentication, I've finally gotten the bugs worked out. Apparently, the first time I tried to export my public key to the remote machine, I tried to do it manually with the *scp* command rather than using the *ssh-copy-id* command, which is infinitely more straightforward. After a subsequent uninstall/reinstall of my entire VM along with a total reconfiguration of SSH, I then managed to successfully transfer the key over to the remote machine but neglected to install it into the home directory of the host machine using the *cat id_rsa.pub >> 192.xxx.x.xxx* command. Only after a third and final uninstall/reinstall of the VM and yet another reconfiguration of SSH did I manage to install the public key correctly on both my local and remote machines. At any rate, my network connection has been re-established, file/directory permissions have been properly set, and public key authentication is now in effect. As slow on the uptake as I may have been, I do appreciate the help.

---

### Post by TheFu on 2016-02-26
Setup is straightforward, once you know it, as with most things.  If name resolution is working so the client and server know each other by the same, correct, names - that's the first part.  IPs don't matter. OTOH, I only connect to a local machine once by IP address just after install. From that point on, it is by-name only.

On the server side, NOTHING need be done directly beside installing and enabling openssh-server (allowing firewall rules for inbound connections, if enabled).

On the client side, ssh-keygen, then ssh-copy-id to the server - THAT's it.  No manual copying is needed. No manual changing of permissions or even creation of the ~/.ssh/ on the server-side is needed. No need to touch any files. If ssh-copy-id is used, the directory and permissions are handled properly.

The only reason this might be more complicated is if different ssh-keys are used for different servers - perhaps work vs home vs side-jobs.  However, with a 4K key, I don't see the point. I've never heard of a 4K public key being reversed 1K keys, yes, but not anything larger. Every client has different keys, so their public keys each get added to the server-side ~/.ssh/authorized_keys file thanks to ssh-copy-id. 

The reason that my directory above has both client AND server files is because I manage every system thru ssh, so they all run openssh-server.  I might have 1 pure server ... yep - my blog VM - it has 3 files:```

~/.ssh$ ls
authorized_keys  config  known_hosts

```
They are 600 permissions.  If the blog VM gets hacked, I didn't want anyone being able to hop to any of the other systems.  Same applies for email servers - inbound ssh, yep. Outbound - NOPE.

I can recall before ssh-copy-id was created all the times I had issues.  Sometimes things would work and sometimes not - think it was due to different checking either due to server config files or different defaults in the ssh code version being run. This was during the time between ssh1 and ssh2.  
Things are much better these days.

What is the **cat id_rsa.pub >> 192.xxx.x.xxx** for? I don't understand.  I'm also confused by all the uninstall/reinstall stuff.  Wouldn't creating new test accounts to try things out have been easier?  Or am I missing something important?

---

### Post by spacer.x-infinity on 2016-02-27
> What is the **cat id_rsa.pub >> 192.xxx.x.xxx** for?

Pardon me, I typed that wrong. I meant to say *cat id_rsa.pub >> .ssh/authorized_keys.* I've basically been following along with Matthew Helmke's 2014 Edition of *Ubuntu Unleashed;* and, while it gets the job done in the way of a basic introduction, I'm finding that, as I cross-reference it with other resources available on the internet, some of the information it provides is incomplete. For instance, it made no mention of the *ssh-copy-id* command whatsoever. Only after googling "ssh public key authentication tutorial" did I even learn that it existed.

> I'm also confused by all the uninstall/reinstall stuff.  Wouldn't  creating new test accounts to try things out have been easier?  Or am I  missing something important? 				

The only important thing you're missing is that I am a bit more of a dumbass with this stuff than you give me credit for. ;) Had it occurred to me that creating test accounts was even an option, I would have done so but, in my unrelenting genius, I decided to just uninstall the VM completely and start again from scratch. Not the most practical decision, sure, but it saved me a lot of needless confusion.

Anyway, just thought you'd like to know that you were proven right about the pitfalls of manually transferring the public key from one machine to another. Thanks again for your help.

---

### Post by TheFu on 2016-02-27
Don't be too hard on any books.  Part of being an "expert" is being around a long time.  ssh-copy-id wasn't around since the beginning so doing it manually was the only way. Think I discovered it around 2005-ish ... so I had over a decade of doing it manually.  Old-timers don't always go back to relearn new ways for things that are already mastered.

Whenever there is an issue on a system, the first part to troubleshooting it is to create another, new, fresh account and see if it persists.  Linux is multi-user. Configurations are stored per-userid, so creating a new userid will start fresh.  It is strange some of the times an entire system seemed broke, when creating a new userid showed it wasn't the system, just my user that was the issue.

Another thing that is extremely powerful that many old-timers don't know about is the ~/.ssh/config file.  One of my peers was NOT using it and had been writing tiny scripts/aliases to deal with different ports, userids and option for every server.  He'd have scripts for logins, rsync, and the backup tool - anything based on ssh.  That "config" file is amazing and every tool that leveraged ssh/libssh seems to honor it.  I use it as a way to document all the different systems I have logins on around the world and to set options for specific needs. 

```
host cent18
   user root
   hostname cent18.foo
   port 21022
   # LocalForward 5901 cent18:5901
   # LocalForward 5902 cent18:5902

```
Handy for all that - I get to say **ssh cent18** and it logs me in as root@cent18 using the correct port. If I need VNC on that box, but want it through an ssh tunnel too, uncomment 1 of the other lines, as needed. The connect to vnc on a local port 5901 to actually tunnel to the other machine and connect to its 5901 port. Very handy.  

ssh can do some amazing things and it can be relatively secure if some of the defaults are changed.

Reinstalling a system is good practice, but reconfiguring a system over and over shouldn't be a hassle. Lots of tools make that less painful. Ask in another thread, if interested.

Anyways, think we are done here.

---

