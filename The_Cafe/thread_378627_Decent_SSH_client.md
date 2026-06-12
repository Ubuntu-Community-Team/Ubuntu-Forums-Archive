---
title: "Decent SSH client"
date: 2007-03-07
forum: The Cafe
---

### Post by Sharra on 2007-03-07
Hello,

I'm looking for a decent SSH client that has more features then Putty.. I am looking for something specifically that supports better tunneling options, something closer to SecureCRT on windows.. Anyone have any recommendations?

Thanks!

---

### Post by Somenoob on 2007-03-07
the OpenSSH client is pretty good.

---

### Post by SishGupta on 2007-03-07
Whats wrong with putty's tunneling? I use it a lot and I find it works well.


Here is a list that might help you out:
[http://en.wikipedia.org/wiki/Comparison_of_SSH_clients](http://en.wikipedia.org/wiki/Comparison_of_SSH_clients)

---

### Post by Brunellus on 2007-03-07
why do you need a separate ssh client?

---

### Post by bpence on 2007-10-29
If you're looking for a good Windows [SSH]("http://www.celestialsoftware.net")client with nice tunneling options and a TABBED interface, try AbsoluteTelnet:

[http://www.celestialsoftware.net]("http://www.celestialsoftware.net")


Brian

---

### Post by n3tfury on 2007-10-29
lol putty's not "decent"?  since most people here don't use windows, why don't you list these features that SecureCRT has that you like so well?  you might be able to get better opinions.

---

### Post by n3tfury on 2007-10-29
> **bpence said:**
> If you're looking for a good Windows [SSH]("http://www.celestialsoftware.net")client with nice tunneling options and a TABBED interface, try AbsoluteTelnet:

[http://www.celestialsoftware.net]("http://www.celestialsoftware.net")


Brian

er, he's not looking for a windows client.  read the initial post again.

---

### Post by LookTJ on 2007-10-29
> **n3tfury said:**
> er, he's not looking for a windows client.  read the initial post again.
He is looking for Windows client. [B]HINT: He is looking for a decent client with more features than PuTTY. PuTTY is a Windows client, not a Linux client.
[/B]

---

### Post by n3tfury on 2007-10-29
who the heck looks for a windows client in a linux forum?  i retract my second post, but not my first, nor my third.

---

### Post by LookTJ on 2007-10-29
> **n3tfury said:**
> who the heck looks for a windows client in a linux forum?People that want to install a windows client on their flash/usb drive to connect to their ssh server and tunnel through IE or firefox on a different with Windows only. (ex. Library, School, Work.)

---

### Post by n3tfury on 2007-10-29
as many zealouts as there are around here, it's shocking to say the least.

---

### Post by scorp123 on 2007-10-29
> **Taylor said:**
> He is looking for Windows client. [B]HINT: He is looking for a decent client with more features than PuTTY. PuTTY is a Windows client, not a Linux client.
[/B]  ```
apt-cache search putty

pterm - PuTTY terminal emulator
putty - Telnet/SSH client for X
putty-tools - command-line tools for SSH, SCP, and SFTP
```

[http://en.wikipedia.org/wiki/PuTTY](http://en.wikipedia.org/wiki/PuTTY)
".... PuTTY was originally written for Microsoft Windows, but is has been ported to various other operating systems. Official ports are available for some Unix-like platforms, with work-in-progress ports to Classic Mac OS and Mac OS X, and unofficial ports have been contributed to platforms such as Symbian powered mobile phones. ...."

Maybe it would help if you folks checked your facts before flaming people seeking for help? Just a suggestion of course. :)

---

### Post by LookTJ on 2007-10-29
> **scorp123 said:**
> ```
apt-cache search putty

pterm - PuTTY terminal emulator
putty - Telnet/SSH client for X
putty-tools - command-line tools for SSH, SCP, and SFTP
```[http://en.wikipedia.org/wiki/PuTTY](http://en.wikipedia.org/wiki/PuTTY)
Thanks for correcting me ;)

---

### Post by scorp123 on 2007-10-29
> **Sharra said:**
>  I am looking for something specifically that supports better tunneling options I'd recommend using the command line ... Sorry if I sound sarcastic here. That is not my intention. But as you are dealing with the command line anyway it's probably best to get familiar with the tunnelling options that you can define via the **-L:** or **-R:** (for a reverse tunnel) switches of the **ssh** command. If you google around for this you will find many examples of defining tunnels this way. It's very powerful too. You also may want to check ssh's manual:  ```
man ssh
```

One example from me: This here creates a tunnel to a remote host "192.168.1.2" that is exporting it's desktop via the "Remote Desktop" feature: ```
ssh -L 5810:192.168.1.2:5800 -L 5910:192.168.1.2:5900 youraccount@remotehost
``` Once the connection to "remotehost" is established ("remotehost" and 192.168.1.2 are not necessarily the same machine here!) the ports 5800 and 5900 of my actual target 192.168.1.2 get redirected to 5810 and 5910 of my local machine; hence connecting my VNC client to **"localhost:10"** will give me a connection to 192.168.1.2's exported desktop.

I have this stuff as a script on my desktop ... one click and I'm in. So ultimately this can be very user-friendly if you are willing to accept some minor learning curve.

I honestly don't know of any ssh client (at least not for free) that will give you what you want here ... "Putty" probably already was your best (free) bet. On UNIX-like operating systems most people use the native command line client anyway and there is hardly a "market" or "need" for programs such as "SecureCRT" on UNIX-like operating systems.

I hope this response was at least a bit more helpful than what you unfortunately have already seen in this thread. :)

---

### Post by Phil Airtime on 2007-10-29
The university I work with has Putty on the Start menu of its computer terminals, but the ports are blocked! Go figure, as they say in the USA.

---

### Post by eldragon on 2007-10-29
just switch your ssh server's port to 25 or 110, i bet those are not blocked.... :D

cheers

---

### Post by tencent on 2007-10-29
a port that is hardly ever blocked is 443 (SSL or better known [https://)](https://)). I had to use it in highschool as it was the only port other than 80 open to the net.

---

### Post by geeknik on 2007-10-29
> **Taylor said:**
> He is looking for Windows client. [B]HINT: He is looking for a decent client with more features than PuTTY. PuTTY is a Windows client, not a Linux client.
[/B]

So what happens when I run apt-get install putty? Oh look, Putty is a linux client. :)

---

### Post by scorp123 on 2007-10-30
> **Phil Airtime said:**
> The university I work with has Putty on the Start menu of its computer terminals, but the ports are blocked! Go figure, as they say in the USA. Probably a firewall in between.

---

### Post by bruce89 on 2007-10-30
> **geeknik said:**
> So what happens when I run apt-get install putty? Oh look, Putty is a linux client. :)

> **scorp123 said:**
> ```
apt-cache search putty

pterm - PuTTY terminal emulator
putty - Telnet/SSH client for X
putty-tools - command-line tools for SSH, SCP, and SFTP
```

[http://en.wikipedia.org/wiki/PuTTY](http://en.wikipedia.org/wiki/PuTTY)
".... PuTTY was originally written for Microsoft Windows, but is has been ported to various other operating systems. Official ports are available for some Unix-like platforms, with work-in-progress ports to Classic Mac OS and Mac OS X, and unofficial ports have been contributed to platforms such as Symbian powered mobile phones. ...."

Maybe it would help if you folks checked your facts before flaming people seeking for help? Just a suggestion of course. :)

Spot the connection?

---

