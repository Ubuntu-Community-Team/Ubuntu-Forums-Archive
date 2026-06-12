---
title: "Which process make sudo gconftool on my computer ?"
date: 2010-01-29
forum: Security
---

### Post by yocec on 2010-01-29
Hello, 

On my HTPC/Server unbuntu box I have installed logwatch in order to get a daily look on my computer activity.

And I often have this line in the report : 
>  root => my_user
 -------------
 /usr/bin/gconftool - 3 Times.


The corresponding line in auth.log are :
> ./auth.log:Jan 28 07:59:31 sweetBox sudo:     root : TTY=unknown ; PWD=/ ; USER=my_user ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
./auth.log:Jan 28 07:59:32 sweetBox sudo:     root : TTY=unknown ; PWD=/ ; USER=my_user ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
./auth.log:Jan 28 07:59:32 sweetBox sudo:     root : TTY=unknown ; PWD=/ ; USER=my_user ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port


This computer is mainly used for watching movies on my TV (throught Freevo), download linux distribution of course (throught headless Deluge), download podcast (throught podracer), make backup (with rsnapshot)

It's a minimal Ubuntu installation (command line system), there is no Gnome (only xfce4 that I never use)

This computer is accessed throught SSH and NFS

I don't know wich process/script make this sudo..

Any idea ?

Thanks

---

### Post by BkkBonanza on 2010-01-29
sweetBox - is using gconftool to request info about whether any proxy server is configured. The --get option just means it's trying to find out if a proxy is in effect, probably so it can use it if it is.

---

### Post by yocec on 2010-01-29
Thanks and I already understood this, my question is more which program/process/script do this ?

Why use it gconftool wich is a Gnome configuration tool (and there is no Gnome on sweetBox) ?


The goal is to understand in order maybe to desactivate the cron job, or uninstall programm ...

---

### Post by BkkBonanza on 2010-01-29
You might try looking in /etc/sudoers to see what programs are enabled for sudo privilages. Or perhaps using ps at the time when the call is made (maybe during boot?) to see what programs are active at that time. I don't know of a log that will tell you what process made the request. 

Most likely this is just an informational request regardless of whether gnome is installed. That is, the program is asking for info just in case a proxy is set, and ignores the result since no gnome is present anyway. Sometimes programmers will code this in as a "just in case" feature. If gnome were present then it may take advantage of it. My guess is to de-activate it you would have to manually patch the code to skip that check. So I suppose if it's in a script you could do a grep on all the scripts to find the "gconftool" string. Something like,

grep -r gconftool /home /usr

---

### Post by cdenley on 2010-01-29
Apt is scheduled to check for updates daily, and it uses the proxy configuration of your admin user created during install retrieved using gconftool.
```

cdenley@ubuntu:~$ grep -A 4 gconf /etc/cron.daily/apt
# set the proxy based on the admin users gconf settings
admin_user=$(getent group admin|cut -d: -f4|cut -d, -f1)
if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
       use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy 2>/dev/null)
       host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host 2>/dev/null)
       port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port 2>/dev/null)
       if [ "$use" = "true" ] && [ -n "$host" ] && [ -n "$port" ]; then
               export http_proxy="http://$host:$port/"
       fi
fi

```

---

### Post by BkkBonanza on 2010-01-29
@cdenley
Nice find. I'd never have figured that.
Interesting that gconftool is used by apt even though it's decidedly not gnome based. I'd have thought it would have used an env variable but I guess on most systems they don't get set by users so this probably works better. I'll have to remember that.

Ah, but I see it uses it as a backup when the env variable isn't set, and then updates the env too.

---

### Post by yocec on 2010-02-22
Sorry for the late answer....
Many thanks cdenley

---

