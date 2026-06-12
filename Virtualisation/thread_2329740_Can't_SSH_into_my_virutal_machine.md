---
title: "Can't SSH into my virutal machine"
date: 2016-07-04
forum: Virtualisation
---

### Post by warren55 on 2016-07-04
When I try to ssh into the server I get the message connection failed.  I also can't copy and past code from the win 7 machine and the guest Ubuntu.

---

### Post by TheFu on 2016-07-04
Which virtualization tool/hypervisor is being used?  Without that, we cannot really help.
Also, is the VM running inside a NAT network or is it bridged?
Is the firewall enabled, but allowing ssh inbound connections?

---

### Post by warren55 on 2016-07-05
I'm using Virtualbox set to bridge mode.  Thanks to your prior help I can now access the VMs ip address to login to the server for another computer on the network.  I'm running Ubuntu 14.04 server using the CLI.  I don't know how to access the firewall in Ubuntu.  BTW when I boot directly into an Ubuntu install (no virtual machine) on the same computer I can ssh into it from another computer on the network.  Not in front of computer now but have the 2 settings that reference sharing clipboard to bidirectional but still can't paste into the VM terminal.

---

### Post by TheFu on 2016-07-05
**ssh**
So the ssh connection is solved?

**Copy/paste:**
Have you loaded the "guest additions" for virtualbox?  That is needed for copy/paste to work between the hostOS and guest. In some other hypervisors, copy/paste between the guest and host are not possible from "the console." Another method is needed.  I don't use the console much ---- only when things are really bad. The console has lots and lots of unnecessary overhead. Use ssh.

Seems you are really new, so some directed, organized, learning is in order. Skills that build on the last skill learned. Lots of sources for this stuff. Here are a few:
* [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
* [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - free pdf book.
but there isn't any replacement for experience and time.

If you really want to run Linux servers inside a VM, virtualbox isn't the best choice.  Xen or KVM are. Both are extremely stable and used by all the "big boys" for their virtualization. Openstack is based on KVM, for example.  Virtualbox is mainly used for "desktop-on-desktop" virtualization.

The firewall is part of the kernel. There are lots of different programs which can access it.  iptables is the main one used on servers, but there are others. Pick one and use that. Avoid mixing them.

---

### Post by warren55 on 2016-07-05
ssh
Not solved.  When running the Virtualbox Ubuntu on a windows 7 from HDD 1 machine I can't ssh.  If I boot another HDD2 on that computer with only Ubuntu on it I can ssh into it.
Thanks for the links I'll look into them.

---

### Post by TheFu on 2016-07-05
Let's step back. Stay on the ssh issue only.

What is the IP of the host machine?
What is the IP of the guest machine (running openssh-server)?
What is the IP of the ssh client machine?

Does the guest machine have a firewall enabled?
Does the host machine have a firewall enabled?

---

### Post by &amp;KyT$0P# on 2016-07-05
I'd just give the VM an additional network adapter set to a host-only network and SSH using that.  In my experience VirtualBox can be finicky about some kinds of networking

---

### Post by TheFu on 2016-07-05
> **halogen2 said:**
> I'd just give the VM an additional network adapter set to a host-only network and SSH using that.  In my experience VirtualBox can be finicky about some kinds of networking

I never had any issues with vbox networking, beside how slow it was, but I didn't do anything other than bridged networking and only wired, never wifi.  Plus, I haven't touched vbox in 2-3 yrs, so maybe Win10 screwed some things - vaguely recall something about that. Did run it on Xp, Vista and Win7 ... never had networking issues after fixing the default settings to those that are more efficient. About the time I stopped, think the vbox team switched the defaults to what I'd been suggesting for a few years.

---

### Post by warren55 on 2016-07-05
What is the IP of the host machine? 192.168.1.5 Window 7
What is the IP of the guest machine (running openssh-server)?192.168.1.8 Ubuntu running in Virtualbox, I did not install openssh only what comes with Ubuntu 14.04 server
What is the IP of the ssh client machine?Will look up when I get home but its 192.168.1.x Windows 10 computer
 
Does the guest machine have a firewall enabled?No
Does the host machine have a firewall enabled?Yes

---

### Post by &amp;KyT$0P# on 2016-07-05
Oh, you're trying to SSH from an external machine, not host-to-guest.  Never mind about host-only network adapter then. :oops:

Does SSH to the VM work from the host itself?

---

### Post by warren55 on 2016-07-05
Have not tried to ssh to the VM from the host. Can give it go when I get home.  Thanks for replying.

---

### Post by TheFu on 2016-07-05
All on same subnet. Good. Simplifies things.

Must install **openssh-server** on the guestOS if you expect that to work. Don't think it is installed by default.
Also must allow the virtualbox network to pass thru the Windows firewall.

---

### Post by warren55 on 2016-07-05
> **TheFu said:**
> 
Must install **openssh-server** on the guestOS if you expect that to work.
Will install openssh-server when I get home.  Is that needed because it's a VM?

---

### Post by &amp;KyT$0P# on 2016-07-05
openssh-server provides the capability to connect to the machine by SSH.  If nothing is listening for SSH connections on the machine you're trying to connect to, then the machine won't know what to do with the SSH connection attempt and thus refuse it.

---

### Post by warren55 on 2016-07-05
When I installed Ubuntu server on a physical HDD prior to trying the VM I was able to ssh into it without installing openssh-server.  Just trying to understand whats going on.

---

### Post by &amp;KyT$0P# on 2016-07-05
Last I checked Ubuntu server comes with openssh-server [selected to be] installed by default

---

### Post by warren55 on 2016-07-05
after installing openssh-server on the guest ubuntu machine it says I already have the latest version, so I guess it's installed by default

---

### Post by TheFu on 2016-07-05
From a client ssh machine, run **ssh -vvvv server** to get detailed debugging info. Dont think that works from Windows. Sorry.

---

### Post by warren55 on 2016-07-06
Only have windows machines.  I also tried to change the Ubuntu machine IP to a static 192.168.1.50 but still can't ssh in.  Any other ideas?

---

### Post by &amp;KyT$0P# on 2016-07-06
As a test, you might try temporarily disconnecting your host from the Internet (for safety), disable its firewall(s), and see if SSH from the host works then.

If so, it's a matter of re-enabling firewall and adjusting firewall settings. (No idea how to do it I don't use Windows)

If not, does SSH even work from the Ubuntu machine itself?  Try it both ways
```
ssh user@127.0.0.1
ssh user@192.168.1.50
```
(obviously, replacing "user" with your username you want to use for SSH)

---

### Post by TheFu on 2016-07-06
ssh is really, really, really, picky about permissions on ~/.ssh/ and the files inside there.  The "ubuntu ssh" guide will lay out those permissions.

Also, double check all the dumb things. You wouldn't be the first person using the wrong IP for the wrong machine ... I have.

---

### Post by warren55 on 2016-07-06
Halogen2:
I get the same error with the firewall turned off and get connection refused from the ubuntu machine.
TheFu:
I'm trying to ssh to 192.168.1.50 my static IP
eth0      Link encap:Ethernet  HWaddr 08:00:27:36:7d:c5  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe36:7dc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14990 errors:0 dropped:3 overruns:0 frame:0
          TX packets:5713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20231550 (20.2 MB)  TX bytes:1918216 (1.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1950959 (1.9 MB)  TX bytes:1950959 (1.9 MB)

will check the permissions guide.
I don't know if it matters but I can ping from the windows 10 machine the 192.168.1.50 ubuntu vm and can ping from the ubuntu vm my router,windows 10 and host computers.

---

### Post by MAFoElffen on 2016-07-06
> **warren55 said:**
> When I try to ssh into the server I get the message connection failed.  I also can't copy and past code from the win 7 machine and the guest Ubuntu.
Yes, I do have a few questions and a few ideas.

Install another virtualbox vm guest as, say Lubuntu. Let the network be internal, can talk with other VM's. let the network setting stay as dhcp.

With your origina vm off, go to setting, add hardwre, add nic... and match the network setting with the other VM Guest.

Boot the first vm. At a terminal, check the IP addresses. Note the IP of the internal vlan connection. The do 
```

netstat -vl | grep ":22"

```
That would let you know if your VM guest id listening on port 22 for an ssh client to call it...

Boot the second VM. At a terminal, check the IP address. Ping the first vm. If successful, try to ssh to it on that IP. If it works.

My next question is that you said you only have "Windows Machines"... So you are doing ssh through what? Putty? On the install of Putty, It's setup opens appropriate port through the Windows firewall. But whatever you use, if you open an admin cmd window, then do
```

netstat -anb

```
But that command will should ports associated which the applications that are using those ports... Then you would know if the application you are using in Windows to do ssh, is getting though your firewall.

Just some thoughts.

EDIT-- One thing I caught from your first post, if you are connecting linux (from a terminal session) to Linux via ssh, you can cut and paste from the terminal to that local Linux Session... But a VM to it's Windows Host... no. Windows ssh to anyhitng via putty no. The reason for that, is that both are graphics screen representation of the text console, not an actual text console. One thing I do to capture text from screens is to redirect ouput to a tex file, then transfer the text file to wherever. You can still do this with Putty (redirecting to a file on the Linux remote host and using scp in Putty).

---

### Post by TheFu on 2016-07-07
Would really be helpful if code tags were used when posting cmds and output here. Hard to read otherwise. Please.

Pinging is good - but is it by IP or by name? The details are important.  Forget that - **always** use IP for now for everything, including ssh.  Would be helpful if the commands AND the output were shown (using code tags) for all commands. We don't have to assume stuff that way.

I think there is a CLI version of ssh in putty.  Might support the "verbose" flags, so you can see the connection attempt and fail.  At the same time, you can watch the connect on the ssh-server on the Linux machine. I wrote a troubleshooting guide for ssh last year, but never finished it. Let me see if it can be found.  [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) - sorry, it isn't written for Windows or beginners.

I use Windows daily for 2 tasks and about 10 min, but the rest of the time it Unix/Linux.  Only use ssh from Windows if there isn't any other choice. Vaguely remember the copy/paste from putty being better than other options on that platform, but nowhere as good as from a proper xterm.

---

### Post by warren55 on 2016-07-07
Ping is only iwith IP.  Will work on the other suggestions and get back to you.

---

### Post by MAFoElffen on 2016-07-07
> **TheFu said:**
> ...
I think there is a CLI version of ssh in putty.  Might support the "verbose" flags, so you can see the connection attempt and fail.  At the same time, you can watch the connect on the ssh-server on the Linux machine. I wrote a troubleshooting guide for ssh last year, but never finished it. Let me see if it can be found.  [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) - sorry, it isn't written for Windows or beginners.
...

I would have liked to have seen that, but I get a 403 Forbidden (nginx) on your link. I get the same on just the blog.jdpfu.com and [www.jdpfu.com](www.jdpfu.com)...

---

### Post by TheFu on 2016-07-07
> **MAFoElffen said:**
> I would have liked to have seen that, but I get a 403 Forbidden (nginx) on your link. I get the same on just the blog.jdpfu.com and [www.jdpfu.com](www.jdpfu.com)...

Have had lots of abuse and started blocking subnets as needed years ago.  Can only suggest trying
* wayback machine
* google cache
* VPN
* TOR
to see the content. Might not see recent stuff, but anything over a week old gets grabbed by these archives. ... er ... except the wayback machine doesn't seem to have this article for some, unknown, reason.

Sorry for the inconvenience, but I don't have a better answer at this point to stop abuse for a non-commercial website, run as a hobby, within my personal limitations.

I really do need to put these options for seeing the content into the 403 error page.

---

### Post by steeldriver on 2016-07-07
If you have installed the "full" PuTTY package in Windows, you should be able to run plink.exe from the Windows cmd prompt with a (single) -v flag e.g.

```

"C:\Program Files (x86)\PuTTY\plink.exe" -v steeldriver@192.168.1.5

```

---

### Post by MAFoElffen on 2016-07-07
Here's a peek at your content:
[Troubleshooting ssh Connections]("http://webcache.googleusercontent.com/search?q=cache:http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections")

---

### Post by warren55 on 2016-07-08
Steeldriver:
I don't have plink, putty seems to be a standalone exe file.

I did install bitvise ssh client and it gives a log:
10:56:41.839 Current date: 2016-07-08
10:56:41.839 Bitvise SSH Client 7.12, a fully featured SSH client for Windows.
Copyright (C) 2000-2016 by Bitvise Limited.
10:56:41.839 Visit [www.bitvise.com](www.bitvise.com) for latest information about our SSH software.
10:56:41.839 Run 'BvSsh -help' to learn about supported command-line parameters.
10:56:41.839 Cryptographic provider: Windows CNG (x86) with additions
10:56:42.018 Loading default profile.
10:56:42.018 Loading default profile failed: RegOpenKeyExW() failed: Windows error 2: The system cannot find the file specified.
10:56:42.018 Loading a blank profile.
10:57:17.284 Started a new SSH2 session.
10:57:17.291 Connecting to SSH2 server 192.168.1.50:22.
10:57:18.289 Connecton failed. FlowSocketConnector: Failed to connect to target address. Windows error 10061: No connection could be made because the target machine actively refused it.
10:57:18.294 The SSH2 session has been terminated.

---

### Post by &amp;KyT$0P# on 2016-07-08
> **warren55 said:**
> get connection refused from the ubuntu machine.
So step 1 is getting that working.  How did this turn out? -
> **MAFoElffen said:**
> Yes, I do have a few questions and a few ideas.

...
Boot the first vm. At a terminal, check the IP addresses. Note the IP of the internal vlan connection. The do 
```

netstat -vl | grep ":22"

```
That would let you know if your VM guest id listening on port 22 for an ssh client to call it...

EDIT
netstat might display the ports by name instead of number - if so, change the grep command, to get this
```

netstat -vl | grep -P -i ":(22|ssh)"

```

---

### Post by warren55 on 2016-07-08
I hope I'm following the directions correctly,
1)Installed Lubuntu on another VM and set the network to "internal network" no option for DHCP
2)added another network adapter 2 to the Ubuntu VM with it off set to "internal network" and I left the original adapter 1 set to Bridged Adapter.
3)booted the Ubuntu VM typed ifconfig and eth0 was 192.168.1.50 (I made this the static IP of the VM)
4)in terminal I typed netstat -vl | grep ":22"
got netstat no support for AFIPX,AX25,X25,NETROM on this system

---

### Post by &amp;KyT$0P# on 2016-07-08
Looks right to me.  Because you only got the error line out of netstat, try with the grep command modified to account for named ports, is the output any different?

---

### Post by warren55 on 2016-07-08
I'm not sure what you mean by "try with the grep command modified to account for named ports" .

Sorry didn't see your edit.  I get the same errors with > netstat -vl | grep -P -i ":(22|ssh)"

---

### Post by steeldriver on 2016-07-08
I'd typically use

```

sudo netstat -nlpt | grep ssh

```

('sudo' is required in order to see the program name - i.e. sshd in this case).

---

### Post by &amp;KyT$0P# on 2016-07-08
My edit to this post: [http://ubuntuforums.org/showthread.php?t=2329740&p=13515021&viewfull=1#post13515021](http://ubuntuforums.org/showthread.php?t=2329740&p=13515021&viewfull=1#post13515021)

The netstat line you enter in the Terminal is two commands, 1) netstat, 2) grep.  The output stream of the netstat command is being piped to AKA sent to the grep command (that's the meaning of the | symbol in bash/sh/ksh).

---

### Post by warren55 on 2016-07-08
[ATTACH=CONFIG]270025[/ATTACH]
```
sudo netstat -nlpt | grep ssh
``` doesn't do anyting

---

### Post by steeldriver on 2016-07-08
So you apparently do NOT have an SSH server running on the VM

---

### Post by &amp;KyT$0P# on 2016-07-08
As a double-check for if sshd is running, what do you get if you run this command?
```
ps aux | grep ssh
```
If it only shows the line about grep ssh, and nothing about sshd, then we need to figure out how to start sshd or why it's not starting.  In /etc/sshd_config, look for a line that starts with "SyslogFacility".  What is it set to?

If it's set to "AUTH", see if this command gives any useful information?
```
cat /var/log/auth.log | grep -i -F 'ssh'
```

---

### Post by warren55 on 2016-07-08
sudo apt-get install openssh-server fixed the problem.  I thought that we established it was installed with the ubuntu install earlier in the thread.  Thanks so much for the help and patience.

---

### Post by &amp;KyT$0P# on 2016-07-08
You're welcome! :KS

---

### Post by TheFu on 2016-07-09
> **warren55 said:**
> sudo apt-get install openssh-server fixed the problem.  I thought that we established it was installed with the ubuntu install earlier in the thread.  Thanks so much for the help and patience.

Glad it is finally solved. Was going to offer a voice chat today.

**YOU** assumed it was installed, but didn't show the commands used to validate that fact. Assuming is bad.  That is the danger we all face - no always understanding the output provided.  This is why it is best to post the exact command and the exact, relevant, output from it.  Some days each of us isn't at our best and a second set of eyes would have seen the **dpkg -l |grep openssh** output and known it wasn't installed.

BTW, you can see where this is a 3 minute thing, once you know what you are doing.  A few other tips for ssh.
* ssh-copy-id - don't push the public keys manually which risks setting the wrong permissions on directories and files, and CRLF accidentally being added to important files (breaking them).
* edit your personal ~/.ssh/config file to add any hosts you have access to. If just 1-2 machines, not a big deal, but if you work on machines around the world with different userids and different ports for each, it is nice to never need to know that stuff. Every command that leverages ssh seems to honor the settings in this file ... that includes rsync, rdiff-backup, sftp, ....   just never having to remember if it is -p or -P for the different commands to use a non-standard port makes it worth the effort alone for me.

---

### Post by warren55 on 2016-07-09
TheFu
Thanks again for you help, I just want to try to understand what happened.  When I previouly typed the command to install openssh it said I already had the latest version.  After all the back and forth I tried it again and it installed.  Not clear on why.

---

### Post by MAFoElffen on 2016-07-09
LOL! I've been there before.

Like most diagnostics-- Go by layers and rule them out, one-by-one. Such as, do I have a link light? I chased a problem in a Cisco Routing/Switching class for almost an hour ... and when I found the problem, I found that my instructor had disabled a port setting in my switch to see if I would catch it. Boy, did I feel embarrassed. (Security practice is set all unused ports to off/disabled.) I could see it was plugged in, but didn't verify that I had a link light. Then I didn't verify with a console (until later) that the ports I was using were all turned on.

But, to credit that experience ... after that, I remembered his antic's and what I learned from them. They help me to remember to check things like that, and to remember to stay humble.

---

