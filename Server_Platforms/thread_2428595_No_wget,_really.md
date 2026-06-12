---
title: "No wget, really?"
date: 2019-10-06
forum: Server Platforms
---

### Post by Russell John on 2019-10-06
Never faced this problem before, quite dumbfounded about it. Using Ubuntu 18.04.1 LTS on DigitalOcean, fresh Droplet.

```
root@nyc1:~# wget http://www.rfxn.com/downloads/maldetect-current.tar.gz

Command 'wget' not found, but can be installed with:

apt install wget
```

Attempting to install wget:

```
root@nyc1:~# apt install wget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version (1.19.4-1ubuntu2.2).
0 upgraded, 0 newly installed, 0 to remove and 236 not upgraded.
```

Can anyone shed some light on this? Thanks.

---

### Post by TheFu on 2019-10-06
Check the PATH environment variable.  Using wget as root isn't wise, BTW.
/usr/bin/wget
is where it should be.  

If you've played with any firejail extra commands, there might be a link in /usr/local/bin/wget that is stale.

I'm a little concerned that the system hasn't been properly patched from the output shown. Please run:
```
sudo apt update
sudo apt upgrade

```to get those 230+ packages that need to be patched, patched.

---

### Post by LHammonds on 2019-10-07
I agree with TheFu, sounds like a PATH issue.

```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

The above is the default path for Ubuntu Server 18.04.3 LTS.  I recommend you use the "echo $PATH" command to see what yours is set to.

If you are logging in with a Bash shell and have no path at all you can type this command to add the above path to your login profile (customize it however you want):

```
echo 'export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"' >> ~/.bashrc
```

If you need this set for all users, you can add a script to /etc/profile.d/

LHammonds

---

