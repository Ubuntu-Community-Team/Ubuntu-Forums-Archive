---
title: "Cant connect to VMWare server using remote console"
date: 2006-02-25
forum: Server Platforms
---

### Post by hannabal on 2006-02-25
People, i'm at my wits end! I have tried everything I can think of. I am a relative newby to linux (I have been using it for a few years but not digging very deep).

I have just built a new server on an AMD64 dual core architecture (Using a Nforce4 motherboard in case thats usefull to know) I am using a breezy flavour of Ubutu. I have installed Webmin, and VNC4server (Which is currently crashing, but thats a different problem), I can ssh to the machine, I can hit the webmin interface, but I can not connect the VMWare remote console to the VMWare server installed on the machine! If I do it on the server, (in gnome) I can connect to "Local Machine", but even thewre if I enter the ip address it will refuse to connect. Running VM's is the sole purpose of this machine so this is a show stopper... I get an error stating "the connection was activly refused" when I try to connect form enywhere....

HELP PLEASE!!!!

Jamie

---

### Post by suRoot on 2006-02-25
Are both these machines on the same LAN, or is there a firewall in the way?

VMWare remote console uses port 902 by default.  From a console, can you

```
telnet <ip-of-remote-host> 902
```

You should get this banner if so

```
220 VMware Authentication Daemon Version 1.10: SSL Required, MKSDisplayProtocol:VNC
```

If you don't get that banner, something - either on that machine or between the host & remote is blocking that port.  Also make sure you have the vmware console running on the remote box.

---

### Post by hannabal on 2006-02-25
They are on the same lan, there is no firewall between them...... I can't even connect to the VMWare server from the machine it's on if I try to connect vi IP address... I can only get to it using "Localhost" option in the vmware console....

---

### Post by baastie on 2006-02-27
Hi,

Did everything go okay with compiling the new Vmware software on your install ?

When you startup vmware does it give errors somewhere ?

Dit you try to install the additional web interface ( https 8333 ) for vmware ?

Grtz ?

---

### Post by drifting on 2006-06-25
I have the same problem, wonder if you resolved it?
The same machine I was trying to act as the remote client works fine with another VMware server on my network, dare I say the other server is Windows 2003 :)
Pretty new to Ubuntu, so can only assume port 902 is being blocked?

Paul.

---

### Post by slade208 on 2006-07-14
I had the same problem. FYI I am a noob as well to Ubuntu. I had the same issue with the details below but this is how I got it fixed. In all honesty I was not expecting any problems since I had installed vmware before on suse.

Ubtunu version: Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) with an installed vmware server release 1

Symtpons: unable to connect to remote console with anything other than a localhost with the actual console. No telnet localhost 902 even

Solution: I know this is noob but I am noob to ubuntu. Vmware server console(vm-authd) depends on xinetd. xinetd is not installed by default in Ubuntu

1. Open synaptic or use apt-get to download xinetd
2. confirmed xinet running with ps waux
3. re-run vmware-config.pl should ask to rerun vm mui config also if you have it
4. re-ran vmware-config-server-console
5. telnet localhost 902 , confirmed
6. connected with server console from another host

---

### Post by drifting on 2006-07-14
Thanks ever so much for your help, that sorted my main problem. The second problem I had was that I installed Firestarter, and you guessed it, it was blocking port 902!

Thanks

---

### Post by HeXonX on 2006-08-16
This did the trick! I was really surprised that Dapper doesn't include xinetd by default. This is one of the few things that frustrates me about Ubuntu, that some really obvious and necessary packages are left uninstalled.

> **slade208 said:**
> I had the same problem. FYI I am a noob as well to Ubuntu. I had the same issue with the details below but this is how I got it fixed. In all honesty I was not expecting any problems since I had installed vmware before on suse.

Ubtunu version: Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) with an installed vmware server release 1

Symtpons: unable to connect to remote console with anything other than a localhost with the actual console. No telnet localhost 902 even

Solution: I know this is noob but I am noob to ubuntu. Vmware server console(vm-authd) depends on xinetd. xinetd is not installed by default in Ubuntu

1. Open synaptic or use apt-get to download xinetd
2. confirmed xinet running with ps waux
3. re-run vmware-config.pl should ask to rerun vm mui config also if you have it
4. re-ran vmware-config-server-console
5. telnet localhost 902 , confirmed
6. connected with server console from another host

---

### Post by SquishyMarbles on 2006-08-18
Hi guys, I'm really new to VMWare, and I've got a quick question, I think.  This particularly helpful thread has solved my connectivity problem, but I've got a slightly different question.

What can I expect when I do finally connect to a remote virtual host?  I don't know if I should expect a VNC-like functionality or what.  I've got VMWare Server running on Windows, and VMWare Server running on Linux, and I can use each of them to host a new guest OS.  However, I cannot seem to setup anything that allows any sort of remote manipulation.  I'm lost in what sort of functionality to expect here, and the connectivity permutations here.

Maybe more specifically, how do I add users to some list of allowed remote users?  I can't even do that....

---

### Post by SquishyMarbles on 2006-08-19
Nevermind, I got it.  Now, the user account on my Windows box has no password for it, and I think that is what's keeping my from connecting the Linux VMWare Server Console back to the Windows server console.  Does anyone know this for certain?  I'm actually not really willing to setup another account on this Windows box to check that theory, although I may have to...

---

### Post by SquishyMarbles on 2006-08-19
Nevermind, I got it.  Now, the user account on my Windows box has no password for it, and I think that is what's keeping my from connecting the Linux VMWare Server Console back to the Windows server console.  Does anyone know this for certain?  I'm actually not really willing to setup another account on this Windows box to check that theory, although I may have to...

---

### Post by SquishyMarbles on 2006-08-19
Okay, I can't get the Linux Console to connect back to the Windows one.  Does anybody have any ideas, even though this isn't a Windows board? =)

I've installed VMWare server on the Windows XP Pro box, which also has IIS installed, and it's currently hosting a web interface at <ip-address>:8222 that's working just fine.  However, no username that I put into the thing gets recognized.  When connecting to the VMWare Linux server, I use my Linux username and password, but I can't do the same with my Windows username and password.  Any ideas?  Thanks for the help.  At least I'm not starting new threads on this stuff. =)

---

### Post by slade208 on 2006-08-21
Squishy

I am kinda new to vmware as well. I had some questions regarding your situation with vmware installed on your xp machine.

1. Have you opened up a vmware console on the xp and connected to itself?
2. Have you tried connecting with the administrators account?
3. Is port 902 open and listening on the xp machine? if you can connect to pass a username and password from your linux box to your windows box then the answer to this is yes

---

### Post by Floppyjoe on 2007-06-23
> **slade208 said:**
> I had the same problem. FYI I am a noob as well to Ubuntu. I had the same issue with the details below but this is how I got it fixed. In all honesty I was not expecting any problems since I had installed vmware before on suse.

Ubtunu version: Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) with an installed vmware server release 1

Symtpons: unable to connect to remote console with anything other than a localhost with the actual console. No telnet localhost 902 even

Solution: I know this is noob but I am noob to ubuntu. Vmware server console(vm-authd) depends on xinetd. xinetd is not installed by default in Ubuntu

1. Open synaptic or use apt-get to download xinetd
2. confirmed xinet running with ps waux
3. re-run vmware-config.pl should ask to rerun vm mui config also if you have it
4. re-ran vmware-config-server-console
5. telnet localhost 902 , confirmed
6. connected with server console from another host

I just did step #1 here and it fixed my connection issues.
Regards,
Floppyjoe

---

### Post by remmosf on 2007-07-30
Well FYI i have two ubuntu machines. A notebook and a stationary computer. I wanted to connect to the virtual machines running on the stationary computer from my notebook. I have installed vmware server on both machines (but nothing besides that). Ubuntu is 7.04

This post helped:
[https://bugs.launchpad.net/ubuntu/+bug/112937](https://bugs.launchpad.net/ubuntu/+bug/112937)

but you have to use the solution mentioned last (qoute):

...I solved it by setting the content of the file /etc/pam.d/vmware-authd with

#%PAM-1.0

@include common-auth
@include common-account

.....

Hope this helps others. I had a hard time solving it.

cheers
Remmosf

---

