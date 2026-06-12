---
title: "Linux server management with Cockpit"
date: 2021-03-18
forum: Ubuntu, Linux and OS Chat
---

### Post by him610 on 2021-03-18
Read an interesting article recently about Linux server management tool, 'Cockpit,' at [https://opensource.com/article/20/11/cockpit-server-management]("https://opensource.com/article/20/11/cockpit-server-management")
Has anyone else downloaded Cockpit to use as management tool? What do you think about it?

---

### Post by TheFu on 2021-03-18
Any webapp based systems management tool seems like a huge security risk to me. There are millions of professional hackers in the world today. They all learn how to break into web servers.  webmin, phpMyAdmin, phpLDAPadmin all scare me.
The fact that cockpit provides a shell interface **REALLY** scares me. 

Securing ssh is a well-solved problem.
Securing the 10,000 hacks against a modern webapp is a constantly changing problem.

But managers like pretty applications and they can allow junior system administrators quick access to make small changes.  On a fairly secure LAN, I wouldn't be completely against that, provided the sr admins had setup strict access controls, perhaps even localhost-only access to that jr admins have to create an ssh-tunnel even to access the management tool.

BTW, I installed it on a VM here, played with it for about 10 minutes, then purged it.  The computer wasn't a central system to my network, so perhaps I didn't get to see all the kewl things it can do.

---

### Post by him610 on 2021-03-18
@TheFu
I appreciate your input about Cockpit. I have always trusted your opinion on things. I figure I am only a novice compared to some of the folks that frequent these forums. Some of the things that are discussed I only partially understand.

Here is a link to the Cockpit Transport Architecture... [https://raw.githubusercontent.com/cockpit-project/cockpit/master/doc/cockpit-transport.png]("https://raw.githubusercontent.com/cockpit-project/cockpit/master/doc/cockpit-transport.png")
Looks like it does use sshd

---

### Post by TheFu on 2021-03-18
Webapps = danger
ssh != danger
The ssh connections don't scare me, since to be any use, those need to be key-based.  That is mathematically secure, provided good key management and strengths are used - or just use ed25519  keys and be good for 10 yrs.

It is the web front-end that makes me nervous. Hooking up a web front-end to any admin tool AND not forcing a localhost-only connection is terrible security.  Some things are just bad ideas.  This tool let's someone with a web browser, using a local SSL cert, have admin control over your system with just a freakin' userid/password.  That's just crazy to me.  Humans are terrible at passwords.  Locally signed SSL certs are scary too.  Sure, some people will get a real cert and setup localhost-only access, but that isn't the default.  The Cockpit guys made choices worthy of Adobe or Microsoft with those.  IMHO.  

Tools like these should be secure by default, and make the user/admin remove those security aspects if they want.  If they can't figure out how to do that, IMHO, that's a good reason why they shouldn't.

This is all opinion.  Lots of people will disagree.  After they get hacked the first time, maybe their stance will change.  Mind did.

---

### Post by DuckHook on 2021-03-21
I think the devil is in the details. In this case, perhaps it should be: the *angel* is in the details.

The problems with server admin in general and Linux server admin in particular are its obscurity and arcanery. Seasoned server admins like you find it second natured to lock down precisely the right locks, turn the right knobs, press the right buttons and make the right sacrifices to the right entities. Newbie/part time admins like me find it really hard. We don't even know that such&#8209;and&#8209;such a knob or button exists in the first place. For example, I only discovered quite by accident and but recently that one must make ***two*** changes to sshd.config to disable password login. Webmin makes those changes for me properly and automatically.

Granted, this is a very limited example of where molly&#8209;coddling is advantageous. I'm sure they are offset by more numerous examples where a suite like Webmin is disadvantageous. In fact, I've read up on them and know that Webmin suffered a supply chain poisoning attack just two years ago. I also get your point that borrowing a lumbering browser built from 20 million lines of code to run a critical server app gives us 20 million lines of potential trouble. But I also appreciate that, without OpenWRT's mini HTML interface, I would never have dared to replace the firmware in my otherwise obsolete NAS appliances and convert them into fully updated (and far safer) devices. Almost every router out there is managed through an HTML interface and there are few devices more central to LAN safety than my router. Speaking only personally, if I had to manage my router using only the command line, I would probably break down in tears and go hide in the corner.

The choice between ease of use and real security is a tug&#8209;of&#8209;war. Understood. I also understand your point about the default on these things being too loosey&#8209;goosey and ought to start out super hardened. But I'm mindful that, in the absence of easier tools, many will just throw up their hands in despair and do nothing at all, which is far worse than having realistic means to set at least some minimal standards.

---

### Post by TheFu on 2021-03-21
Save this script. Modify 2 lines near the top. Be happy.  Best if ssh-keys have been setup and a host-alias is in **~/.ssh/config** on the client machine to connect to the ssh-server system.  Here's an example stanza:
```
host remote.domain.com
  hostname 123.45.67.89
  port 2222
  user my_username

```

The "hostname" can be resolved by DNS, /etc/hosts, mDNS, or just slam an IP address in there. You'll never need to know the IP, non-standard port, or even your username again. These will be automatically passed for any ssh-based connection - ssh, scp, sftp, rsync, sshfs, and 50 others. It also works for URLs in Linux File managers: sftp://remote.domain.com/  .

Here's the ssh tunnel script that will launch a new chromium that can securely connect to the remote system/LAN:
```
#!/bin/bash

PORT=64001  # non-standard port to connect locally
SSH_SRV=remote.domain.com   # OR use the **IP address** OR use the **host-alias** from ~/.ssh/config

# ##########[ Shouldn't need to change anything below here ]##########
# Only start SOCKS proxy if necessary
if  [ $(/bin/ps -eaf |/bin/grep ssh |/bin/grep -c $PORT ) = 0 ] ; then

   # Setup SOCKS proxy through home server. 
   # The ssh-server port is configured in the ~/.ssh/config file **host-alias**

   echo "Starting ssh SOCKS Proxy"
   /usr/bin/ssh  -f -C -D $PORT  $SSH_SRV  -NT &
fi 

# ##########[ Start private firejail with chromium, going through ]##########
# 
# just setup SOCKS proxy
sleep 3;
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:$PORT "; 
/usr/bin/firejail  --private chromium-browser \
         --proxy-server="socks5://localhost:$PORT " &

exit 0;
```

---

