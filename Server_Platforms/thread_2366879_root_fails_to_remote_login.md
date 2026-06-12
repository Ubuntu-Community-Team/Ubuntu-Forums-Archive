---
title: "root fails to remote login"
date: 2017-07-22
forum: Server Platforms
---

### Post by satimis on 2017-07-22
Hi all,

Ubuntu 16.04 server

User can ssh remote-login with password but root fails.

&#10219; ssh root@ip_address
Permission denied, please try again.

Root password is correct

/etc/ssh/ssh_config```

.....
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

Having tried adding;
PermitRootLogin yes

to ssh_config and restart ssh - sudo service restart ssh

still fail.

Please help.  Thanks

Edit:
After remote-login as user.  I can "su root" with root password

Regards
satimis

---

### Post by efflandt on 2017-07-22
Allowing root login (especially with just a password) would be very foolish. By default Ubuntu does not even have a root login for the system (you should use sudo). Do you realize how many script kiddies around the world are trying to crack root and other passwords for ssh?

You are looking at the wrong file, ssh server (daemon) settings are controlled by /etc/ssh/sshd_config. I don't even allow passwords for normal users (keys only), I specifically set "PasswordAuthentication no" (besides default "PermitRootLogin no"). So script kiddies can try password cracks until they are blue in the face and never get in.

And from using Linux for over 20 years I believe the correct way to su to root would be "su -" so you inherit root's environment. Otherwise if you do something as root using your normal user's environment you may end up with problems due to certain files and configurations in your user's home directory with only permissions for root.

PS: I even use Linux keys on my Android phone to ssh or sftp to my PC.

---

### Post by oldos2er on 2017-07-22
See posts #9 and #10 [here]("https://ubuntuforums.org/showthread.php?t=2336776").

---

### Post by satimis on 2017-07-22
Hi all,

Thanks for your advice.

It looks quite strange to me here.

I have 3 ubuntu 16.04 servers newly installed on 3 VMs of VirtualBox.  One of them can remote-login as root with root passwords.  Other 2 unable to remote-login as root with root password.  I can remote-login them as user.  Then login as root.

Root password works on both 'su' and 'su -'

satimis

---

### Post by wildmanne39 on 2017-07-22
*Thread moved to **Server Platforms**.*

---

### Post by BenginM on 2017-07-22
IS this for real ! 

did you read what** efflandt and what oldos2er point you to...!**[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=937632")

---

### Post by satimis on 2017-07-22
> **BenginM said:**
> IS this for real ! 

did you read what** efflandt and what oldos2er point you to...!**[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=937632")
Hi,

I'm curious to find out how it happens?

I followed;
Initial Server Setup with Ubuntu 16.04
[https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

to setup the server

Step On - Root Login (from Host terminal)
$ ssh root@your_server_ip

according to my recollection, after some minor struggling on /etc/default/grup
then I can remote login as root.

After remote running;
$ sudo apt-get update ; sudo apt-get upgrade

I still could remote login as root.  My editing on /etc/default/grub was completely wiped out.

Current /etc/default/grub```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x1024

GRUB_GFXMODE=1280x1024x24
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_COMLINE_lINUX_DEFAULT="psmouse.proto=imps quiet nosplash"
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```


For the other two ubuntu 16.04 servers I ran;```

$ sudo apt-get update ; sudo apt-get upgrade

```
on their console before I tried remote login as root.

Then I have tried editing /etc/default/grub without result.

In fact I don't need remote login as root.  I can remote login as user then "su -"

Just for curiosity

Regards
satimis

---

### Post by CharlesA on 2017-07-23
You don't need to login as root because the user you created during install has access to sudo.

As far as having root already enabled.. any VPS will only have the root user by default, unless you install it yourself.

---

### Post by satimis on 2017-07-23
> **CharlesA said:**
> You don't need to login as root because the user you created during install has access to sudo.

As far as having root already enabled.. any VPS will only have the root user by default, unless you install it yourself.
Hi,

Thanks for your advice.

Just created another Ubuntu 16.04 server, remote-login as user and ran;
```

$ sudo apt-get install update ; sudo apt-get upgrade

then
$ sudo apt-get install dist-upgrade

```

Afterwards I couldn't remote-login as root disregarding making changes on /etc/ssh/ssh_config

It concludes my observation that;
If immediately after installation completed before running update and upgrade.  I can change /etc/ssh/ssh_config to allow root to remote-login.  It continues to work even after running update and upgrade later.

I would stop here.  Lot of thanks for all advice

Regards
satimis

---

### Post by cariboo on 2017-07-23
Just as an aside, you don't need to use sudo if you are root.

---

### Post by satimis on 2017-07-23
> **cariboo said:**
> Just as an aside, you don't need to use sudo if you are root.

Noted and thanks

satimis

---

### Post by TheFu on 2017-07-25
> **satimis said:**
>  I can change /etc/ssh/ssh_config to allow root to remote-login.  

That is the wrong file, as already mentioned above.

However, why ignore all the excellent advice here to not allow remote root access?  These people with decades of experience ARE trying to help you.

Use sudo and use a different account.

Perhaps the better question is  - "How to perform remote administration over ssh without using root since I know it is bad?"

Here's what I do on a server in the 1st 5 minutes:
[http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

---

