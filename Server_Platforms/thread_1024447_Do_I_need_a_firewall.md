---
title: "Do I need a firewall?"
date: 2008-12-29
forum: Server Platforms
---

### Post by Twizzle on 2008-12-29
I have setup a home server using Ubuntu 8.10 server edition to manage file sharing and emails. All my internet access goes through my Linksys WRT54GS router.

Under the 'Port Range Forward' settings on the router, I have allowed ports 80, 433, 10000 (webmin) and 22 to forward to the sever and that's it. As a result I can access it remotely, which is what I need, but I am a bit paranoid that someone might be able to access it.

I have seen in my system logs that there are failed attempts to relay emails and access via ssh but nothing that suggests that someone has got in.

Should I be installing a firewall on the sever as well as using the router or is that overkill?

---

### Post by windependence on 2008-12-29
They are what they are - FAILED attempts. They will never go away unless you pull out the ethernet cable. ;)

You should be fine with a good hardware firewall and decent secure passwords. Use random characters and preferably don't make an actual dictionary word.

Finally, have confidence that those failed attempts you see are a GOOD thing. That means they didn't get in. You could also go a long way by turning off ping on your router, that way they won't even know you're there.

-Tim

---

### Post by skippymo on 2008-12-29
i agree failed attempts are failed attempts but a nice smoothwall box would be awesome for you easy install and browser interface....google smoothwall for the distro.

---

### Post by amauk on 2008-12-29
you've got a few options

1)
change the port numbers (particularly ssh)
you'll have to remember it, and ssh in with
user@host -p port

this is the easiest to do,
and while it'll stop most automated attacks
if someone really wants to access your system, they'll find out the port number

2)
install denyhosts (it's in the repos)
denyhosts is a daemon that monitors your
/var/log/auth.log for failed login attempts

if certain criteria are met, it'll ban the IP - append it to /etc/hosts.deny
(either for a time, or permanently)

you can set it up email alerts for any bans, etc.

but all it stops is people repeatedly guessing the password
someone could find out your password by other means

3)
Setup public/private keys for ssh
rather than just needing a password (which is brute-force-able) you'll also need the server's public key

It's just a file located in ~/.ssh/

Something you know (password)
Something you have (public key)

this is the most secure way of adding extra security to ssh

If you want to ssh in from other locations, you will need to carry the key with you (usb stick, or something)

---

### Post by Superslobberface on 2008-12-29
I don't think it is overkill.

I suggest using [firestarter]("http://www.fs-security.com/")

"Firestarter is an Open Source visual firewall program. The software aims to combine ease of use with powerful features, therefore serving both Linux desktop users and system administrators."
[https://help.ubuntu.com/community/Firestarter]("https://help.ubuntu.com/community/Firestarter")

It provides additional piece of mind.

```

sudo apt-get install firestarter

```

Configure the inbound traffic policy to only allow connections from trusted hosts
I currently have my work and other "trusted" ip address/ranges listed:
```

192.168.0.1./24
127.0.0.1
68.xxx.xxx.xxx (work address not shown)

```

---

### Post by halovivek on 2008-12-29
> **Superslobberface said:**
> I don't think it is overkill.

I suggest using [firestarter]("http://www.fs-security.com/")

"Firestarter is an Open Source visual firewall program. The software aims to combine ease of use with powerful features, therefore serving both Linux desktop users and system administrators."
[https://help.ubuntu.com/community/Firestarter]("https://help.ubuntu.com/community/Firestarter")

It provides additional piece of mind.

```

sudo apt-get install firestarter

```

Configure the inbound traffic policy to only allow connections from trusted hosts
I currently have my work and other "trusted" ip address/ranges listed:
```

192.168.0.1./24
127.0.0.1
68.xxx.xxx.xxx (work address not shown)

```

hi
i have installed ubuntu 64 bit and i will keep my system always to internet connection and i will not shut down. i will restart the system once in a week. i am using laptop. so if i download this one. will it secure my system more or may leave the system as it is. will it prevent my system from the hackers?
thanks
:P

---

### Post by windependence on 2008-12-29
> **skippymo said:**
> i agree failed attempts are failed attempts but a nice smoothwall box would be awesome for you easy install and browser interface....google smoothwall for the distro.

Good suggestion. I also forgot to mention you could use pfsense (since I'm a big BSD fan) or even untangle.

-Tim

---

### Post by jamesrfla on 2008-12-29
It might be a good idea to change web min port to something else so it will be harder for people to find. Also make sure the password to login is long and complicated. As for SSH I would set up SSH keys. Only people with this key can get into your server. I would also change the port number for SSH too.

---

### Post by Twizzle on 2008-12-30
Thanks for the suggestions / advice - I like the sound of denyhosts as it seems a lot of the failed attempts are from one IP address at the moment. Im also looking at smoothwall.

The only problem with using a key for SSH is that I use Putty on my Nokia N95 to SSH in from time to time - I assume that there is no way to manage that sort of set up (I will do some googling though!)

As far as passwords go, what are the real chances of someone using bruteforce? I may be totally wrong but as I understand it, it is just slowly working your way through every known word in the dictionary isn't it? Just putting a few numbers after a work would mess that up wouldnt it?

And would a hacker really try brute force on a random server - it's not like he / she knows my server belongs to a bank or something so would it be worth the effort?

Again - I may be totally wrong and naive here!

---

### Post by windependence on 2008-12-30
Changing the default port on applications really accomplishes nothing at all. Script kiddies using scanners are scanning for all open ports anyway. They ARE going to find the open port. This is really not a problem as long as the rest of your security is configured properly.

-Tim

---

### Post by jerome1232 on 2008-12-30
Personally I think something like denyhosts or fail2ban is good enough (in conjunction with a good password or keybased authentication of course). That way you can see in your logs what ip's have tried to get in, and they get 5 attempts per ip at their disposal.

Switching ports just stops those bots that only bother to check if there's a service listening on port 22.

---

