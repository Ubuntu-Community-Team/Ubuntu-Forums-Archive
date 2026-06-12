---
title: "where is samba in init.d directory"
date: 2010-05-19
forum: Server Platforms
---

### Post by Timothytech on 2010-05-19
I just installed ubuntu 10.04 on a pc... the server edition. i went to restart samba and it is not in the init.d directory. is there a different folder for server plateforms? cause im use to my 9.10 desktop edition. 


also one more question, when i "ls" the /ect/ directory of course i cant see the whole thing because my monitor only shows the bottom of the file, is there a way to list it like the "more" commands, or possibly scroll up?

---

### Post by BoneKracker on 2010-05-19
> **Timothytech said:**
> when i "ls" the /ect/ directory of course i cant see the whole thing because my monitor only shows the bottom of the file, is there a way to list it like the "more" commands, or possibly scroll up?
```
ls | less
```

---

### Post by cdenley on 2010-05-19
Samba has been seperated into smbd and nmbd for 10.04. Also, there should still be symlinks in /etc/init.d for backwards compatibility, but I think the proper way is now to use the "service" command.
```

sudo service smbd restart
sudo service nmbd restart

```

---

### Post by richardjh on 2010-05-19
With regard to the paging and ls disappearing up the screen, a very useful thing to know is that you can 

Page up in a console using 
```
Shift+Page Up
```and down using 
```
Shift+Page Down
```Obviously, in a terminal emulator like gnome terminal, you can use the scroll bar.

There will come a time when you will be glad you know that. :)

---

### Post by Timothytech on 2010-05-19
thank you so much!! im new to linux but was getting pissy that all i knew of 9.10 was irrelevant for 10.04. thank you all very much! as for the scrolling that i needed too

---

### Post by lisati on 2010-05-19
> **Timothytech said:**
> I just installed ubuntu 10.04 on a pc... the server edition. i went to restart samba and it is not in the init.d directory. is there a different folder for server plateforms? cause im use to my 9.10 desktop edition. 


also one more question, when i "ls" the [COLOR="Red"]/ect/[/COLOR] directory of course i cant see the whole thing because my monitor only shows the bottom of the file, is there a way to list it like the "more" commands, or possibly scroll up?

Typo? Try the "[etc]("http://en.wikipedia.org/wiki/Et_cetera")" directory instead of the "[ect]("http://en.wikipedia.org/wiki/Electroconvulsive_therapy")" directory.

---

### Post by BoneKracker on 2010-05-20
> **lisati said:**
> Typo? Try the "[etc]("http://en.wikipedia.org/wiki/Et_cetera")" directory instead of the "[ect]("http://en.wikipedia.org/wiki/Electroconvulsive_therapy")" directory.

Electroconvulsive therapy, indeed. :lol:

Obviously that was just a typo in his forum post.  If he had made that typo in his actually shell command, he wouldn't have had so much output that it scrolled off-screen, now would he? :roll:

---

### Post by wkulecz on 2010-05-20
> **cdenley said:**
> Samba has been seperated into smbd and nmbd for 10.04. Also, there should still be symlinks in /etc/init.d for backwards compatibility, but I think the proper way is now to use the "service" command.
```

sudo service smbd restart
sudo service nmbd restart

```

I figured that out, and my samba server works after I start it manually, but how to I make it start automatically on reboot?

I like the faster boot up of the new way, but seems a lot of things have fallen through the cracks and are missing instructions.  As I recall all previous versions, installing samba packages made smbd & nmbd start automatically.

The administration->samba GUI tool made setting up a share trivial and painless (although a few of the defaults are not what I'd like, it "just worked") and although it started the service after creating the the share and enabling some users, the service was not running after a reboot :(

--wally.

---

### Post by cdenley on 2010-05-20
> **wkulecz said:**
> 
I like the faster boot up of the new way, but seems a lot of things have fallen through the cracks and are missing instructions.  As I recall all previous versions, installing samba packages made smbd & nmbd start automatically.


Yes, and it still does, but if you enable "bind interfaces only", then it will fail to bind to interfaces which aren't up when samba is started.

---

### Post by wkulecz on 2010-05-20
> **cdenley said:**
> Yes, and it still does, but if you enable "bind interfaces only", then it will fail to bind to interfaces which aren't up when samba is started.

This doesn't make sense, I didn't enable "bind interfaces only" I'm using the default setup as enabled by the GUI tool.  I tweak settings to my taste only after things otherwise appear to work correctly. Since it doesn't start after a reboot, I'm not there yet.

If this it the default, then starting smbd/nmbd before the network interfaces are configured would surely seem to be a bug!

Where is the "master" list of services that start automatically kept?
How would I make the smbd start depend on network services startup completing?

I knew how to do this easily with the old /etc/rc5.d/Snn_initScript scheme.  I've no clue here and there seems to be no tools to control start up service or docs about doing it.

At least this change appears to speed up booting so I see the benefits but the apparent lack on doc for such a major change in an LTS release is rather annoying.  There doesn't seem to be a 10.04 server setup guide, 8.04 is the one linked in the sticky, which uses the "old" way :(

--wally.

Followup:

I verified in the smb.conf file created by the GUI system->administration->samba tool has both "interfaces" and "bind interfaces only = yes" commented out.

---

### Post by cdenley on 2010-05-20
I tested it, and simply installing the samba package does result in smbd being started at boot. The only scenario I could think of where startup could be a problem is if samba attempts to bind to specific interfaces which aren't up. You can edit the upstart configurations if this is a problem.

/etc/init/smbd.conf
```

description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

**start on (local-filesystems and net-device-up IFACE=lo and net-device-up IFACE=eth0)**
stop on runlevel [!2345]

respawn

pre-start script
	RUN_MODE="daemons"

	[ -r /etc/default/samba ] && . /etc/default/samba

	[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

	install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F

```
You need a "net-device-up IFACE=ethX" for each interface which needs to be up before that service starts. I don't know of any upstart configuration which says to start when all configured interfaces are up.

---

### Post by wkulecz on 2010-05-20
Thanks I stumbled on the the solution while you were posting.

Here is where I bitch again about change for the sake of change.  

Upstart is a big win, reboot was very very fast compared to 8.04.  However in 9.10 where I found a bit of docs, it was /etc/events.d to control upstart where in 10.04 its now /etc/init with no mention of the change anywhere in the "normal" Ubuntu places as far as I can tell :(   But I stumbled upon [http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/) via google which led to the changes I mention below.



my /etc/init/smbd.conf had:
start on local-filesystems

changed it to match that in /etc/init/nmbd.conf:
start on (local-filesystems and net-device-up IFACE!=lo)

And presto, samba is up after a (fast!) reboot.

I installed samba from the "software center" instead of synaptic like I usually do, perhaps that is where the bug is.  As I said it started and worked after I created the share with the GUI tool which was very easy to use, but I still need to tweak the create masks for my needs, no biggie, the defaults are probably "safer" but I need multible Windows users to share a share with full file control via a common group membership.

Thanks for posting the answer!

--wally.

---

### Post by cdenley on 2010-05-20
> **wkulecz said:**
> 
changed it to match that in /etc/init/nmbd.conf:
start on (local-filesystems and net-device-up IFACE!=lo)

That will work if you only have one network interface beside lo.
> **wkulecz said:**
> 
I installed samba from the "software center" instead of synaptic like I usually do, perhaps that is where the bug is.

Regardless of what package manager you use, it still installs the same packages from the same repository. The default configuration is to listen on all interfaces for connections, which means it would start fine with the default upstart configurations.

---

### Post by Timothytech on 2010-05-20
> **wkulecz said:**
> Thanks I stumbled on the the solution while you were posting.

Here is where I bitch again about change for the sake of change.  

Upstart is a big win, reboot was very very fast compared to 8.04.  However in 9.10 where I found a bit of docs, it was /etc/events.d to control upstart where in 10.04 its now /etc/init with no mention of the change anywhere in the "normal" Ubuntu places as far as I can tell :(   But I stumbled upon [http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/) via google which led to the changes I mention below.



my /etc/init/smbd.conf had:
start on local-filesystems

changed it to match that in /etc/init/nmbd.conf:
start on (local-filesystems and net-device-up IFACE!=lo)

And presto, samba is up after a (fast!) reboot.

I installed samba from the "software center" instead of synaptic like I usually do, perhaps that is where the bug is.  As I said it started and worked after I created the share with the GUI tool which was very easy to use, but I still need to tweak the create masks for my needs, no biggie, the defaults are probably "safer" but I need multible Windows users to share a share with full file control via a common group membership.

Thanks for posting the answer!

--wally.

I installed samba from the OS installation process and it didnt have the correct line, just like yours. so its not just the software manager... I dont care too much for this OS version at the moment.

---

### Post by cdenley on 2010-05-20
> **Timothytech said:**
> I installed samba from the OS installation process and it didnt have the correct line, just like yours. so its not just the software manager... I dont care too much for this OS version at the moment.

"correct line"? This is the correct (default) configuration for /etc/init/smbd.conf, which works fine with the default smb.conf.
```

description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

**start on local-filesystems**
stop on runlevel [!2345]

respawn

pre-start script
	RUN_MODE="daemons"

	[ -r /etc/default/samba ] && . /etc/default/samba

	[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

	install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F

```

---

### Post by Timothytech on 2010-05-20
oh, sorry i skimmed throught, but samba didnt start my default until i added the "new device Iface" line so for me it was correct :)

---

### Post by cdenley on 2010-05-20
> **Timothytech said:**
> oh, sorry i skimmed throught, but samba didnt start my default until i added the "new device Iface" line so for me it was correct :)

I still think you must have changed something in smb.conf, then, because I tested it, and it worked fine. By default, samba doesn't need interfaces to be up in order to run.

---

### Post by bab1 on 2010-05-20
> **cdenley said:**
> I still think you must have changed something in smb.conf, then, because I tested it, and it worked fine. By default, samba doesn't need interfaces to be up in order to run.

Are you sure of that.  I believe it does.  I know that smbd is reloaded every time a dhcp managed interface lease is renewed even if the IP address does not change.  The daemon needs to communicate with others in the network to work.

---

### Post by cdenley on 2010-05-20
> **bab1 said:**
> The daemon needs to communicate with others in the network to work.

In order for it to function as a server, obviously it needs interfaces to communicate over. However, it can run or start fine before the interfaces are up. Then when the interfaces are up, it will continue to run and now function as a server.

---

### Post by gabak on 2010-06-22
why did they change it???

---

### Post by cdenley on 2010-06-22
> **gabak said:**
> why did they change it???

Because ubuntu uses upstart, and has been transitioning from a sysv configuration to an upstart configuration for some time.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

