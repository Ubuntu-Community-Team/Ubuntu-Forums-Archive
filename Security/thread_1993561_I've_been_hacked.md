---
title: "I've been hacked"
date: 2012-06-02
forum: Security
---

### Post by michaelneath on 2012-06-02
My Ubuntu machine was hacked yesterday: as I watched, a fresh tab was opened in Chrome, taken to moneygram.com, and then the details for a transfer to Romania were typed in.  I moved the cursor to another box while the hacker was typing and they noticed, deleted the characters and went back to the original box.  I then unplugged my router.

How can I find out if this is wardriving or a hack via ssh or some other way?  I've changed my wifi passkey and I switch the router off when it's not being used, but how can I protect against an internet connection intrusion?

Is one form of attack more likely given that my computer was being remotely controlled in this way?

Thanks for any help you can give me.

Michael

---

### Post by The Cog on 2012-06-02
I think you most likely left the VNC service enabled. It's a remote desktop setting somewhere (can't remember where though). The dangerous thing is a checkbox that says to allow the internet to connect, but doesn't warn you that this will actually use UPnP to reconfigure your router to forward incoming connections to your PC.

You can verify which ports on your computer are accepting connections with the command:
```
netstat -lt
```
vnc will show up as port 5900 if it's accepting calls.

---

### Post by 0011235813 on 2012-06-02
Also, check your firewall status...
```

#If you haven't already done so, enable ufw
sudo ufw enable
#Now show what ports are open and to whom
sudo ufw status verbose
#If remote desktop is the problem, turn off all incoming connections
sudo ufw default deny
#Or just the standard SSH port
sudo ufw deny 22
#If extra paranoid, turn off PING
gksudo gedit /etc/ufw/before.rules
#Go to the bit that is commented "ok icmp codes", and edit it to say:
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DENY
-A ufw-before-input -p icmp --icmp-type source-quench -j DENY
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DENY
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DENY
-A ufw-before-input -p icmp --icmp-type echo-request -j DENY

```
Hopefully that will solve your problem.

EDIT: @The Cog. I've just noticed that command is in QUOTE tags. In case there is any confusion.

---

### Post by michaelneath on 2012-06-02
Thank you both so much for your replies.  Yes, the remote desktop was on and without a password required!  I've switched it off and set those firewall rules.

Thank you!

---

### Post by 0011235813 on 2012-06-02
If you notice any similar issues, don't hesitate to post it. You may want to mark this thread as solved by clicking on Thread Tools- Mark This Thread as Solved.

---

### Post by HermanAB on 2012-06-03
Cangratulations!  There are many tales of VNC woe on these forums and you have joined the club.

The moral of the story is: Don't play with a daemon before reading up on what it does and how it works and when you are done playing, disable it.

---

### Post by michaelneath on 2012-06-03
Yes, it was very spooky.  I'm just glad I was there to stop it.  I don't know if they'd've been able to use my account details or if they were going to use my machine with someone else's account to hide their IP address.

I've been using Ubuntu for years - I'm not a noob.  I can't remember ever leaving the VNC server open with no password!  Surely I wouldn't do anything that dumb...

---

### Post by CharlesA on 2012-06-03
Keep in mind - if you have had VNC enabled for a while and only saw someone using the machine when you were at it, it may have been used when you were not at it.

Personally I would backup your home folder, wipe the machine and restore my files from backups.

---

### Post by mr-woof on 2012-06-03
I'm with Charles on this, if this was the first time they had been on the machine, surely they would of had a look around and not open a tab straight away?

Might be worth having a look back at /var/log/auth.log and see if there is anything in there, they might of been on your machine for months.

Backup your data, format and re-install, also untick upnp on your router.

---

### Post by CharlesA on 2012-06-03
Better yet, don't use VNC.

---

### Post by michaelneath on 2012-06-03
I've reinstalled on my root partition, as advised.  Thanks for your advice.  I do think that they were just trying to do a quick transfer that would be associated with my IP rather that their own.  That seemed to be their purpose, rather than messing up my system pointlessly.  Or might a keylogger have been installed?

Dunno - anyway, I have reinstalled; switched off VNC and its ports; and installed and configured fail2ban.  Hopefully, I should be reasonably safe now!

Michael

---

### Post by CharlesA on 2012-06-03
Once someone has access to a system, you don't know what they could have done unless you do a forensic analysis. A reinstall is easier to do. ;)

---

### Post by matt_symes on 2012-06-03
Ignore this post. I'm going blind.

---

### Post by 0011235813 on 2012-06-03
> **michaelneath said:**
> I've reinstalled on my root partition, as advised.  Thanks for your advice.  I do think that they were just trying to do a quick transfer that would be associated with my IP rather that their own.  That seemed to be their purpose, rather than messing up my system pointlessly.  Or might a keylogger have been installed?

Dunno - anyway, I have reinstalled; switched off VNC and its ports; and installed and configured fail2ban.  Hopefully, I should be reasonably safe now!

Michael
I'll just mention fail2ban is for servers that run services like FTP, and isn't really beneficial to desktops/laptops. You should also focus on browser configuration and apparmor, the wikis will have help.

---

### Post by Paddy Landau on 2012-06-03
> **CharlesA said:**
> Better yet, don't use VNC.
+1.

There is a version of VNC that uses encryption, but sadly it works on Windows and not on Ubuntu.

This is one glaring hole in Linux — how to connect both easily and securely between computers. It can be done, but not easily.

---

