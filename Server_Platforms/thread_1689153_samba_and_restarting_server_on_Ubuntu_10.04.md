---
title: "samba and restarting server on Ubuntu 10.04"
date: 2011-02-16
forum: Server Platforms
---

### Post by cormu7 on 2011-02-16
Hello, 

I am running Ubuntu 10.04 and have been using samba. Every time I restart the server, I subsequently have trouble accessing the shared server folders via samba from a windows desktop computer.

I tried typing these two commands:

>    sudo restart smbd   

and

>  sudo restart nmbd   

And that doesn't seem to work. 

Do you have to start or restart samba on the command if you restart your linux server each time out?

Thanks,

cor

---

### Post by cormu7 on 2011-02-22
I was able to figure it out, thanks.

---

### Post by cormu7 on 2011-03-09
okay, i thought i was able to figure this out.

what i did was change my /etc/init/smb.conf file

> description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on local-filesystems
stop on runlevel [!2345]

respawn

pre-start script
    RUN_MODE="daemons"

    [ -r /etc/default/samba ] && . /etc/default/samba

    [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F
where it says "exec smbd -F", I changed that to "exec smbd -D", and that seemed to allow be to use samba from windows to connect to my server.

and when i typed
> ps -ef|grep mbdi would receive this output

> root      3533     1  0 08:23 ?        00:00:00 smbd -D
root      3537  3533  0 08:23 ?        00:00:00 smbd -D
root      3543     1  0 08:23 ?        00:00:00 nmbd -D
it was my understanding that that change would automatically start samba on reboot.

however, a couple of weeks later, with the same output above, i could not access the server via samba. i would get  the "not accessible/permission" warning.

running the start/restart smbd and start/restart nbmd commands don't seem to work either.

any thoughts?

cor

---

