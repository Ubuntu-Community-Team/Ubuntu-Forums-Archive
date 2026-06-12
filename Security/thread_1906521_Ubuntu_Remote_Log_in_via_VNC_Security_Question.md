---
title: "Ubuntu Remote Log in via VNC Security Question"
date: 2012-01-09
forum: Security
---

### Post by chiques on 2012-01-09
Hello Awesome Ubuntu Linux Community,

I would like to start off by thanking all of you for such a great platform and support. 

Some background for my issue:

I have Ubuntu 10.04 LTS- the Lucid Lynx and required remote log in. I had some problems but eventually solved them by installing an application called “Vino”. Ultimately I was able to remote log in to this workstation.

When I remote log in to this desktop a purple bubble pops up on the top right of the screen with network information from the machine which is remote logging into the 10.04 workstation. This is fine and expected. 

Here is my concern:

Yesterday I was starring at my desktop and I noticed that bubble pop up and go away. Need be said, **_I WAS NOT LOGGING IN_** to my machine. 

1. Is there a log which keeps track of all requests to remote log in to my 10.04 machine?

2. What security measure's should I be taking to make sure I see/monitor all requests and connections to my machine?

3. What are the possibilities that my machine can have a worm or was hijacked?

Thanks in advanced for any advice.

---

### Post by MadsRC on 2012-01-09
I don't know much about Remote Login and VNC, but when you find the log file, you could install conky, and have that list the latest entries of those logs.

I do that with my syslog, ufw log and one more (Can't remember, not at home).

---

### Post by HermanAB on 2012-01-11
Howdy,

Don't use VNC.  It is a sure fire way to get your machine hacked.  Works every time.  There are many tales of woe on these forums and it is always VNC.

So, do yourself a favour and read the snailbook at snailbook.org and use SSH for remote login.

---

### Post by OpSecShellshock on 2012-01-11
Answer to the first question I think is yes, it does log connection attempts. I'm not sure where, though. The application may keep its own logs, or it may write attempts to /var/log/auth.log or something like that.

Answer to the second question is that once you find where the attempts are logged to, check those logs every day, probably several times. This advice only presumes that you intend to continue using it, and intend to leave the computer on and connected all the time but...

The answer to your third question is that if you have VNC installed and active, then getting compromised by an intruder is inevitable. I suspect that's exactly what happened in the situation you described. I would personally reinstall after something like that. Best advice: don't use VNC for remote access. Among other issues, it does not support sufficiently strong authentication and potential intruders are scanning for it all the time.

---

### Post by dirtrider1 on 2012-01-11
As stated above VNC is inherently not very secure, but if you must use it I recommend firewalling VNC for LAN access only and use a VPN or SSH to access your LAN and then connect to the VNC server.

---

### Post by chiques on 2012-01-11
I truly appreciate the opinions. 

From this point on, I will be officially freaked :roll::roll::roll: out and avoid using VNC to remote log in to my workstation from the internet at all costs. 

I have deleted my port forward settings on my firewall/router (if this is not sufficient please advice).

Is there a way to determine if my workstation has been compromised by (purchase an anti-virus application or)installing something on the repository?

[COLOR="Red"]**It would really suck if there was a keylogger worm that recorded transmitted my username and passwords.**[/COLOR]

Wow, I didn't realize it was so easy to open up Linux for attack! Windows yes, but not Ubuntu. :(:(:(

---

### Post by hackertarget on 2012-01-11
No need to freak out, the only sure way to ensure there is no keylogger is to rebuild your system. Antivirus products will typically only look for windows based malware. You could try rkhunter, chkrootkit or ossec, as they all are able to detect root kits on your system.

Do not give up on remote access if you have a need for it. There is much power in the remote management capabilities of Linux.

To keep it simple for your situation I would recommend opening a high port on your router that forwards to 22 on your Linux box. This will stop the noise from ssh brute forcers. Then familiarize yourself with port forwarding concepts and use VNC through that ssh tunnel you have created.

---

### Post by Dangertux on 2012-01-11
Poorly configured linux is actually easier to compromise than a default configuration of Windows. On top of that, it's almost as easy to poorly configure linux as it is to install Windows. ;-)

Don't use VNC, use SSH for remote administration, love your CLI environment, it loves you :-)

---

### Post by movieman on 2012-01-12
> **Dangertux said:**
> Don't use VNC, use SSH for remote administration, love your CLI environment, it loves you :-)

VNC is fine, but it should only ever listen to localhost. Use SSH to forward the VNC port to the remote machine and you're safe; anyone who can access VNC would first have to hack your SSH server so your system is toast anyway.

---

