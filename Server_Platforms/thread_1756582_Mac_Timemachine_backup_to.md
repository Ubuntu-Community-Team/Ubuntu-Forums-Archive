---
title: "Mac Timemachine backup to"
date: 2011-05-12
forum: Server Platforms
---

### Post by sdmike6 on 2011-05-12
I've been following these two tutorials:

[LIST]
[*][http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html](http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html)

[*][http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)
[/LIST]

I have it all setup but my issue is when I connect to the server on the mac it will not let me connect.

So when I connect using afp://"server address"
I get prompted to enter credentials but nothing I use will let me in.

There are no log files for netatalk so I feel like this is a huge guessing game I'm losing at :(

What steps should I take to resolve this?

---

### Post by samosamo on 2011-05-12
I am just assuming you are using valid credentials, so why don't you go ahead and post the relevant netatalk config files for us to see. Enclose them in CODE tags for better formatting.

---

### Post by stmiller on 2011-05-12
You can enable logging in netatalk. It's a bit complicated to get this going, but possible...

---

### Post by rubylaser on 2011-05-13
This is not too tricky to get working. Some of the things have changed with newer versions of Snow Leopard.  The first difference is this file...
```
nano /etc/netatalk/afpd.conf
```
You need to have this line from the tutorial
```
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh

```
look like this instead...
```
 - - transall -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword -advertise_ssh
```

And, I normally set this file
```
nano /etc/netatalk/AppleVolumes.default
```
up like this, instead of following the directions...
```
/var/TimeMachine TimeMachine allow:username1,username2 cnidscheme:dbd options:usedots,upriv
```
Also, sometimes, you need to create an empty file in that directory
```
touch /var/TimeMachine/.com.apple.timemachine
```
And, make sure you ran this command on your mac
```
defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1
```
Finally, restart netatalk and you should be okay.

This working well for me with (15) 10.6.7 clients.

---

### Post by ShiftyPowers on 2011-05-17
thanks Rubylaser.  This worked for me but I think there is a typo in the cnidscheme:cdb part of your instructions.  I think it has to be "dbd" in order for it to work.  Your way worked but was throwing some warnings when I connected.  So I fixed it following the instructions here:

[http://forums.freebsd.org/showthread.php?t=20324]("http://forums.freebsd.org/showthread.php?t=20324")

> **rubylaser said:**
> This is not too tricky to get working. Some of the things have changed with newer versions of Snow Leopard.  The first difference is this file...
```
nano /etc/netatalk/afpd.conf
```
You need to have this line from the tutorial
```
- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh

```
look like this instead...
```
 - - transall -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword -advertise_ssh
```

And, I normally set this file
```
nano /etc/netatalk/AppleVolumes.default
```
up like this, instead of following the directions...
```
/var/TimeMachine TimeMachine allow:username1,username2 cnidscheme:cdb options:usedots,upriv
```
Also, sometimes, you need to create an empty file in that directory
[CODE}touch /var/TimeMachine/.com.apple.timemachine[/CODE]
And, make sure you ran this command on your mac
```
defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1
```
Finally, restart netatalk and you should be okay.

This working well for me with (15) 10.6.7 clients.

---

### Post by rubylaser on 2011-05-17
You're right, that's what I get for not sshing into my box, and seeing what I actually did.  I updated my post to show the correct directions.  Thanks.

---

### Post by sdmike6 on 2011-05-25
Sorry for the late reply, I have been really busy at work.

I resolved my issue by building netatalk from source instead of installing it with apt-get.

---

### Post by oldguy2011 on 2011-07-06
hi, i thought i would ask here rather than start a new thread. i was able to get afp shares to work and timemachine backup will run without tweaking client and without creating a spasebundle, time machine creates a sparsebundle on the afp share all by itself.

i want to run time machine server on 11.04 (desktop 64-bit) for 10.6.8 clients, i figure os x 10.7 will break it but some fix should come along, hoping on netatalk 2.2 production release at some point. if i can't even get 10.6 clients to backup correctly i'm in trouble.

every subsequent time machine backup reports the disk id changed and starts a new sparsebundle after "use this disk" is selected.

i am a newb and have spent days on this. i created my own afp_voluuid.conf since netatalk didn't do it even though option:tm was set. i created adisk.service in avahi. nothing changed the error. i attempted to install netatalk 2.2b4 but i can't even tell if that installed correctly. i ended up just double-clicking configure from the extracted netatalk tar.gz 2.2b4 and it appeared to automatically place files somewhere but i could not find the command to check the installed version, i never could get any of the makefile commands to work. some variant of berkeley db appeared to already be installed (4.8 i think) and i had installed netatalk 2.1 from ubuntu software center...

after following kremaliscious and others i thought my issue was not broadcasting a uuid but what i tried to resolve that did not appear to work, or that is not the problem... TIA!

I am wondering if 10.6.8 broke something. I never was able to try any of this on older os x versions.

---

