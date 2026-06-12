---
title: "Newbie SSH Question"
date: 2011-01-20
forum: Security
---

### Post by jhargis1012 on 2011-01-20
Hello.

I am very inexperienced with Ubuntu (and Linux in general). I was trying to setup/learn SSH before realizing (from reading various tutorials) that I probably left my computer fairly vulnerable to malicious logins. For now, I've removed the SSH server using the synaptic package manager (at least I hope I did) until I get a better idea of how to use it properly.

My main question:

1: is the "last" command a good way of seeing who's been on your computer (including from the outside)? Or will SSH logins not be logged here?

2: when I use the "who" command, I see two instances of my own username. Why is this?

Thanks a bunch.

---

### Post by CharlesA on 2011-01-20
When you use "who" it shows any time you are logged in. You'll be there twice, since you are signed into the GUI and thru a terminal.

You can check /var/log/auth.log for failed logins.

Also note: If you install openssh-server, and don't have it open to the internet you "should" be ok.  By open to the internet, I mean have that port forwarded on your router.

---

### Post by Kirboosy on 2011-01-21
You can also install a program called "denyhosts". It scans your SSH logs for brute force attacks and automatically bans the IPs that the attacks are coming from.

Just an extra precaution if you are still worried about security.

Another thing is I would recommend not using the default port if you want to access your server remotely over the internet. Now if someone really wanted to they would be able to still figure out what port you are using but I know some places block the default SSH port. If you use a random port like 55000 it will sometimes let the connection go through. 

Keeping things random tends to keep a hacker on his toes. Defaults are always known so its up to the user to secure it further.

---

### Post by The Cog on 2011-01-21
You can also configure a list of users/addresses that are allowed to connect, like:
AllowUsers andy@1.2.3.4,billy@5.6.7.8

[http://www.faqs.org/docs/securing/chap15sec122.html](http://www.faqs.org/docs/securing/chap15sec122.html)

Best is probably to use certificates and disallow passwords.

---

### Post by jhargis1012 on 2011-01-21
Thank you, guys.

CharlesA, how do I view /var/log/auth.log? Still getting the hang of this.

---

### Post by CharlesA on 2011-01-21
> **jhargis1012 said:**
> Thank you, guys.

CharlesA, how do I view /var/log/auth.log? Still getting the hang of this.
I use vim or filter it out using grep.

---

### Post by The Cog on 2011-01-21
```
less  /var/log/auth.log
```
Use "Q" to quit.

---

### Post by cariboo on 2011-01-21
You can also use System->Administration->Log File Viewer, to view the logs.

Personally I use cat, grep and less

---

### Post by jhargis1012 on 2011-01-21
I see. Thank you.

---

### Post by mr-woof on 2011-01-22
I've been very interested in SSH over the last couple of months, I set up a test environment with the help of the chaps on here and it seemed to work well, so I've just installed SSH server again on my mediatomb laptop to act as a SSH proxy for me when I'm out and about using my netbook. If you do open the server to the baddies on the net make sure you disable password authentication and use SSH keys. These are the steps I've followed when installed and configuring ssh for use with my netbook:

Change the following values in the sshd_config file:

change PasswordAuthentication to yes (just for now)
change port 22 to port XXXX
change loginGraceTime 120 to LoginGraceTime 20
PermitRootLogin to no
change log level from INFO to VERBOSE
save and restart ssh
/etc/init.d/ssh restart

On the device you want to use the proxy/connect on

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa -b 4096
cd .ssh
ssh-copy-id -i id_rsa.pub user@x.x.x.x (server user name/ip)


On the server again:
sudo nano /etc/ssh/sshd_config 

change PasswordAuthentication to no

sudo /etc/init.d/ssh restart


on the device:
login with ssh user@x.x.x.x

Then install fail2ban and denyhosts for extra security, banning of brute force type stuff. I forwarded the port on my router to the static on the laptop and connected fine via the net. 

Hope that helps, have I missed any other steps out anyone or does that look ok?

---

### Post by amra.sonntag on 2011-01-23
While mr-woof more or less covered it all. There are 1 or 2 things, that you can do.

Add in sshd_config ```
AllowUser XXXX
``` to only allow the specified user a chance to identify using SSH. You probably don't want to name this one admin or remote or test. ;)

You can can enable your in built firewall and add a Limit directive. Using UFW you would do something like this:
```

ufw allow xxx/tcp  # where xxx is your port for ssh, to allow inbound traffic on it
ufw limit xxx/tcp    # to limit strange requests
ufw enable             # to start your firewall with the new rules

ufw status verbose # to check if it works

```

So - I just wanted to add to your paranoia. :P

---

