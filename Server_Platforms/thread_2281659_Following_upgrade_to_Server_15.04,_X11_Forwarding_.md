---
title: "Following upgrade to Server 15.04, X11 Forwarding is broken"
date: 2015-06-08
forum: Server Platforms
---

### Post by Surfrock66 on 2015-06-08
I performed an in-place upgrade from 14.10 -> 15.04.  Now, GTK apps will not X11 forward.  I was under the impression that Mir would not be in place until 15.10 which was when I would have probably held back on upgrading.

Some command output:

```
surfrock66@sr66-blade:/$ easytag
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(easytag:13278): Gtk-WARNING **: cannot open display:
surfrock66@sr66-blade:/$ baobab
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
surfrock66@sr66-blade:/$ gedit
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(gedit:13348): Gtk-WARNING **: cannot open display:

```

Pretty ticked off.  The server does have an X session running, and I can X11 forward from other devices so I know my client works.

I've done some research:
    [http://ubuntuforums.org/showthread.php?t=2266456](http://ubuntuforums.org/showthread.php?t=2266456)
    [http://ubuntuforums.org/showthread.php?t=2256737](http://ubuntuforums.org/showthread.php?t=2256737)

No help anywhere.  I'm assuming I don't actually have mir installed, but something on the system has implemented mir hooks in the interim in prep for the eventual mir implementation.

x2go still works, but X11 forwarding was a huge part of my workflow and I'm extremely ticked off, I've been trying to troubleshoot it since the day 15.04 came out.

I'm happy to provide any configuration/output needed.

---

### Post by TheFu on 2015-06-08
I don't know anything about mir and don't touch non-LTS releases, but I do know X11.

Where is the X/server running?
Where is the X/client running?
What is the DISPLAY environment?
Is ssh involved or not?

X-forwarding is normally an ssh thing, not used with raw X11 connections happen over a LAN. So, if you can clarify those things, we can probably help fix any configuration issue.

---

### Post by Surfrock66 on 2015-06-08
> **TheFu said:**
> I don't know anything about mir and don't touch non-LTS releases, but I do know X11.

Where is the X/server running?
Where is the X/client running?
What is the DISPLAY environment?
Is ssh involved or not?

X-forwarding is normally an ssh thing, not used with raw X11 connections happen over a LAN. So, if you can clarify those things, we can probably help fix any configuration issue.

Server is running from my home server; a Dell poweredge SC 1425 in my server closet.
I ran 3 X clients, got the same results on each:
    Debian Sid laptop over the LAN, ssh session using a shortcut created when it was working on 14.10
    Windows work laptop using Cygwin over the WAN, ssh session using a shortcut created when it was working on 14.10
    Windows work laptop using MobaXterm over the WAN, fresh ssh session.

All 3 clients can successfully run an X11 forwarded client from another computer (all 3 were my System76 desktop running from my house)

Do you mean the environment variable?  On my laptop it's :0, but oddly on the ssh session to my home server, "echo $DISPLAY" returns nothing...

EDIT TO CLARIFY: I have an alias to connect to my server; the command is "ssh -p #### -X IP" and in that, "echo $DISPLAY" returns a blank line.  If I get into the server over x2go or VNC, "echo $DISPLAY" returns :0.  Here's the relevant bits from /etc/ssh/sshd_config:

```
surfrock66@sr66-blade:~$ cat /etc/ssh/sshd_config | grep X
X11Forwarding yes
X11DisplayOffset 10

```

ssh is absolutely involved, non-standard port using key authentication.  Same sessions that have worked since I built this server in 2012.

---

### Post by TheFu on 2015-06-08
a) X11 clients and servers are backwards of what we normally see as the "client" and the "server".  The X-client is the remote system and the "X-server" is the machine with the display you sit behind.  Important only for troubleshooting or if you are an X/Windows programmer, like I was.

b) ssh X-forwarding must be enabled on the remote server **sshd_config** AND requested by the ssh client. 
For the ssh server the setting is:
```
$ egrep -i forward /etc/ssh/sshd_config 
X11Forwarding yes
```
and from the ssh client machine, use **ssh -X userid@server**  or you can configure ~/.ssh/config to have the userid/server/ports and make life easier.  ssh -X will setup the tunnel and make the correct DISPLAY after the remote connection is made.  I don't put the X11Forwarding into the client config - sometimes I want it and other times not so much.

If the ssh-server config doesn't ahve that setting, you won't be allowed to use X11forwarding through ssh, period. If you have to change the setting, don't forget to restart the openssh server there.

Don't have a clue about cygwin anymore. You'll still need a local X-Server running on a Windows machine, if you expect this to work. I find x2go easier than dealing with X11 on Windows.  In fact, I'd run a tiny linux inside a VM before dealing with cygwin.  In a business environment, push for a commercial X-server like hummingbird or Xceed. Haven't used any in ... well .... 13 yrs, but they did work well.

Ok - that should cover everything.  If it doesn't, verify that the client and server can ping each other using the same names on the network. Good luck.

---

### Post by Surfrock66 on 2015-06-08
> **TheFu said:**
> a) X11 clients and servers are backwards of what we normally see as the "client" and the "server".  The X-client is the remote system and the "X-server" is the machine with the display you sit behind.  Important only for troubleshooting or if you are an X/Windows programmer, like I was.

You're right, I just refer to the sr66-blade machine as "server" so much I didn't even think about reversing it for X.  That being said, the configuration is the same on both.

> **TheFu said:**
> b) ssh X-forwarding must be enabled on the remote server **sshd_config** AND requested by the ssh client. 
For the ssh server the setting is:
```
$ egrep -i forward /etc/ssh/sshd_config 
X11Forwarding yes
```
and from the ssh client machine, use **ssh -X userid@server**  or you can configure ~/.ssh/config to have the userid/server/ports and make life easier.  ssh -X will setup the tunnel and make the correct DISPLAY after the remote connection is made.  I don't put the X11Forwarding into the client config - sometimes I want it and other times not so much.

This is set.  On my laptop (the client machine, with the X11 Server):

```
surfrock66@sr66-darter:~$ egrep -i forward /etc/ssh/sshd_config
X11Forwarding yes
```

On the server (the X11 client):
```
surfrock66@sr66-blade:~$ egrep -i forward /etc/ssh/sshd_config
X11Forwarding yes
```

From this client laptop, I invoke X-11 forwarded apps in 2 ways; the aliased ssh connection string, and from a shortcut in my awesomeWM menu.  Here's the strings for both (I blocked the port numbers):

```
# SSH Shortcuts
alias hda='ssh -p #### -X hda.surfrock66.com'
alias mc='ssh -p #### teh3l3m3nts@mc.teh3l3m3nts.com'
alias sr66-darter='ssh -p #### -X 192.168.1.65'
alias sr66-dell='ssh -p #### -X 192.168.1.47'
#alias sr66-hp='ssh -p #### 192.168.1.10'
alias sr66-hp='ssh -p #### -X sr66-hp.hda.surfrock66.com'
alias sr66-nas='ssh -p #### surfrock66@192.168.1.36'
alias sr76='ssh -p #### -X sr76.hda.surfrock66.com'
```

All of them are initiating client sessions that should permit X11 forwarding.  Now for the AwesomeWM shortcuts:

```
myhdaforwardedapps = {
	{ "Baobab", "xterm -e 'ssh -X -p ### surfrock66@192.168.1.22 -t baobab'" },
	{ "EasyTag", "xterm -e 'ssh -X -p ### surfrock66@192.168.1.22 -t easytag'" },
	{ "File Manager", "xterm -e 'ssh -X -p ### surfrock66@192.168.1.22 -t pcmanfm'" },
	{ "Terminator", "xterm -e 'ssh -X -p ### surfrock66@192.168.1.22 -t terminator'" },
}
```

All of these shortcuts worked before the upgrade.  

> **TheFu said:**
> If the ssh-server config doesn't ahve that setting, you won't be allowed to use X11forwarding through ssh, period. If you have to change the setting, don't forget to restart the openssh server there.

It's set correctly :/

> **TheFu said:**
> Don't have a clue about cygwin anymore. You'll still need a local X-Server running on a Windows machine, if you expect this to work. I find x2go easier than dealing with X11 on Windows.  In fact, I'd run a tiny linux inside a VM before dealing with cygwin.  In a business environment, push for a commercial X-server like hummingbird or Xceed. Haven't used any in ... well .... 13 yrs, but they did work well.

Ok - that should cover everything.  If it doesn't, verify that the client and server can ping each other using the same names on the network. Good luck.

I still have to use cygwin portable just due to silly enterprise rules, but it works fine.  I can forward, say, my file manager from my laptop or desktop, just no longer from my server.  I keep ssh connections alive all day, and they work the same before and after the upgrade, with the exception of the X11 forwarding and this Mir message.

---

### Post by TheFu on 2015-06-08
Ok - sounds like you've got everything covered.  I'd file a bug.

The X11Forward setting matters not at all on the ssh client side.

BTW, check out the ~/.ssh/config file - it will make your aliases unnecessary AND available for all other ssh-using tools like rsync, scp, sftp across the entire platform ... at least for UNIX/Linux clients. This is an ssh-client only thing. Don't have a clue how to do that on Windows.

---

### Post by Surfrock66 on 2015-06-09
Bug submitted, but as I can't figure out which package the break is in, it is marked as invalid.

[https://bugs.launchpad.net/ubuntu/+bug/1463263](https://bugs.launchpad.net/ubuntu/+bug/1463263)

Pretty fed up.  This was my last Ubuntu machine, I've got all my dependencies ready for a switch to Debian Testing.  Even if Mir isn't the default, from where I'm sitting its implementation is poisoning functionality :/

---

### Post by cariboo on 2015-06-10
If you aren't sure what package to file the bug against, just file it against Linux.

---

### Post by TheFu on 2015-06-10
> **Surfrock66 said:**
> Bug submitted, but as I can't figure out which package the break is in, it is marked as invalid.

[https://bugs.launchpad.net/ubuntu/+bug/1463263](https://bugs.launchpad.net/ubuntu/+bug/1463263)

Pretty fed up.  This was my last Ubuntu machine, I've got all my dependencies ready for a switch to Debian Testing.  Even if Mir isn't the default, from where I'm sitting its implementation is poisoning functionality :/

Please don't take this wrong way.  I'm a former C/C++ developer - did it for about a decade.  Just read the bug.  

"ssh-based X11 forwarding" not working in 15.04 is what I'd name it.  Then I'd show 1 simple test case trying to run 1 pure-X11 application.

**Option A**
```

Setup:
  * remote thefu@172.16.1.111 (x-client)
  * local  172.16.1.100 with X-server running
  * sshd_config has X11Forwarding enabled.

Steps:
\ssh -p 7522 -X thefu@172.16.1.111 xterm -sb &
I'm running an X-server (xorg 1:7.7+1ubuntu8.1) on the local machine and that firewalls have all been disabled.

```

DO NOT mention x2go.  DO NOT mention your "workflow."
DO NOT mention anything that is not directly related to X11 and ssh.

It would be **even better** if the testing is without ssh, assuming there is a server on the LAN which allows it.  The bug as listed simply has too many moving parts for anyone to pinpoint the issue.  
**Option B**
```

Setup:
  * remote thefu@172.16.1.111 (x-client)
  * local  172.16.1.100 with X-server running
Steps:
1) ssh into a remote system - ssh -p 7522 thefu@172.16.1.111
2) xhost + 172.16.1.111 # from local machine .100
3) export DISPLAY=172.16.1.100:0; xterm -sb &

These systems are on the same subnet connected to the SAME, unmanaged, switch. No firewalls enabled on either the client or server.

```

Keep it short, but with enough steps to be reproduced without having to install **any** extra packages.

If opt B doesn't work, that means it is X11 related and has ZERO to do with ssh. Change the bug title to match.

I'm just trying to help.

---

### Post by Surfrock66 on 2015-06-10
You're right; a lot of the extra info was because I copied a forum post into the bug report, but I've been stumped so I'm over-including info.

I'll re-perform the test when I get home tonight, I'm not on the LAN for now.

---

### Post by Surfrock66 on 2015-06-11
So, if I understand correctly, I did this, the 3rd command of #2 fouled me up a bit:

Setup:
  * remote surfrock66@192.168.1.22 (x-client)
  * local 192.168.1.65 with X-server running
Steps:
1) ssh into a remote system - ssh -p 669 surfrock66@192.168.1.22
2) xhost + 192.168.1.22 # from local machine .65
3) export DISPLAY=192.168.1.65; xterm -sb &

Output:

surfrock66@sr66-blade:~$ export DISPLAY=192.168.1.65
surfrock66@sr66-blade:~$ xterm -sb &
[1] 7050
surfrock66@sr66-blade:~$ xterm: Xt error: Can't open display: 192.168.1.65

These systems are on the same subnet connected to the SAME, unmanaged, switch. No firewalls enabled on either the client or server.

Seems, according to the suggestion in that thread, that it's an X11 bug. I will mark it as such.

---

### Post by TheFu on 2015-06-11
Sorry - my mistake. Left off the most critical part.
[B]
export DISPLAY=192.168.1.65:0[/B]

DISPLAY has 3 parts.
* IP
* card
* head
where the "head" is assumed, if not provided and the IP is assumed localhost if not provided.

---

### Post by Surfrock66 on 2015-06-12
> **TheFu said:**
> Sorry - my mistake. Left off the most critical part.
[B]
export DISPLAY=192.168.1.65:0[/B]

DISPLAY has 3 parts.
* IP
* card
* head
where the "head" is assumed, if not provided and the IP is assumed localhost if not provided.

Same thing :/

surfrock66@sr66-blade:~$ export DISPLAY=192.168.1.65:0
surfrock66@sr66-blade:~$ xterm -sb &
[1] 24705
surfrock66@sr66-blade:~$ xterm: Xt error: Can't open display: 192.168.1.65:0
^C
[1]+  Exit 1                  xterm -sb

---

### Post by TheFu on 2015-06-12
Did you forget the xhost +?

---

### Post by Surfrock66 on 2015-06-12
No, I just didn't include it here.  I had 2 terminal windows open, and I did it in a 2nd terminal window.  That should still work, correct?

---

### Post by TheFu on 2015-06-12
The xhost + uses IPs/hosts, not DISPLAY and happens on the system running the X-Server.

---

### Post by Surfrock66 on 2015-06-12
Ok, lemme make sure i understand...here's exactly what I did:

2 windows on my client laptop, running the x-server:

Window 1:
```
surfrock66@sr66-darter:~$ ssh -p 669 surfrock66@192.168.1.22
surfrock66@sr66-blade:~$ 
```

Window 2: 
```
surfrock66@sr66-darter:~$ xhost + 192.168.1.22
```

Window 1: 
```
surfrock66@sr66-blade:~$ export DISPLAY=192.168.1.65:0
surfrock66@sr66-blade:~$ xterm -sb &
[1] 24705
surfrock66@sr66-blade:~$ xterm: Xt error: Can't open display: 192.168.1.65:0
^C
[1]+ Exit 1 xterm -sb
```

---

### Post by TheFu on 2015-06-15
Looks like a bug in X11 capabilities.  libXt is fairly low level (these days).
I'm able to reproduce this error, but my situation isn't simple enough to post for a bug. At least not from the X-server machine I did the testing on.  It appears that x2go and ssh -X could massively interfere with nominal X remote displays controlled through just the DISPLAY and xhost+ methods.

I need to get onto a pure X11 desktop and try this stuff again.

For example, my DISPLAY under x2go had to be 172.22.22.11:51.  If I had a prior ssh -X connection to the remote system, then ssh automatically set the DISPLAY for me to DISPLAY=localhost:10.0 ... which really didn't make sense with the current ssh session NOT having any X-forward requested. Appears to me that some basic X11/ssh behavior has changed. Don't know when this might have happened, since I haven't looked into this in a decade, at least.

---

### Post by Surfrock66 on 2015-06-15
> **TheFu said:**
> Looks like a bug in X11 capabilities.  libXt is fairly low level (these days).
I'm able to reproduce this error, but my situation isn't simple enough to post for a bug. At least not from the X-server machine I did the testing on.  It appears that x2go and ssh -X could massively interfere with nominal X remote displays controlled through just the DISPLAY and xhost+ methods.

I need to get onto a pure X11 desktop and try this stuff again.

For example, my DISPLAY under x2go had to be 172.22.22.11:51.  If I had a prior ssh -X connection to the remote system, then ssh automatically set the DISPLAY for me to DISPLAY=localhost:10.0 ... which really didn't make sense with the current ssh session NOT having any X-forward requested. Appears to me that some basic X11/ssh behavior has changed. Don't know when this might have happened, since I haven't looked into this in a decade, at least.

Awesome, I'm glad I'm not totally nuts!  It died the day I did my upgrade to 15.04; and I'm just on the normal Ubuntu Server repos.

---

### Post by TheFu on 2015-06-15
Just tested it on a pair of 14.04 LTS systems.  Same issue.  Pure X11 - no x2go. No VNC. No ssh -X.
```

$ xhost + romulus
$ ssh romulus
$ export DISPLAY=c720:0
thefu@romulus:~$ xterm -sb &
[1] 19013
thefu@romulus:~$ xterm: Xt error: Can't open display: 172.22.22.13:0

[1]+  Exit 1                  xterm -sb
```

Also tried it using IP addresses everywhere.
Both systems are wired ethernet, on the same switch.```

ssh -X romulus xterm -sb # works fine.
```
All systems here share the same /etc/hosts file (ansible rocks!), so they know each other by name too.

In short, I've reproduced it.

```
$ ssh -X romulus xterm -sb &
[1] 18294
thefu@c720:~$ Warning: No xauth data; using fake authentication data for X11 forwarding.

```
Ran 
```
xauth generate `echo $DISPLAY`
```
to fix the *no xauth data* warning.

Also validated that on the X-Server there aren't any firewall rules which impact this - only have a fail2ban rule.

I need to do some more research on recent X11 changes.

Update:
I spoke with an Ubuntu Dev about this for 15 min on Saturday. He suggested it was a Mir bug and that you should get on the IRC Mir channel and ask for a workaround. He was shocked that the xterm was having any issue at all, since that is an Xt/xlib program.  

The more I think about that today, the more I think there's an issue on the X-server side (firewall or just some small detail).  The fact that it used to work fine is perplexing. IRC is probably the best way for more help.

---

### Post by TheFu on 2015-07-24
Ran into the X11 ssh X11Forward issue on a new system.

**ssh -X userid@system** wasn't working.
Found this post: [http://www.cyberciti.biz/faq/how-to-fix-x11-forwarding-request-failed-on-channel-0/](http://www.cyberciti.biz/faq/how-to-fix-x11-forwarding-request-failed-on-channel-0/) which says to add **X11UseLocalhost no** to the remote "system" sshd_config file. I did. The command above started working.  Read the manpage about this setting - I don't see anything terrible about it on a well controlled network. I won''t do it on an internet connected system, however.

---

