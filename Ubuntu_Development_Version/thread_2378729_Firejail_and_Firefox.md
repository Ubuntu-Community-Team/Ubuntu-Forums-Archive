---
title: "Firejail and Firefox"
date: 2017-10-01
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2017-10-01
I use Firefox for Internet banking only so use it with ```
firejail --private firefox 
``` option. No Addons/Web extension enabled.  For regular surfing I use Chromium ```
firejail chromium
```

So I dont really care about the changes.

---

### Post by poorguy on 2017-11-19
> **linuxyogi said:**
> I use Firefox for Internet banking only so use it with ```
firejail --private firefox 
``` option. No Addons/Web extension enabled.
Any difference using terminal command **firejail   firefox**  and then using **"New Private Window"** then what you are using.

---

### Post by &amp;KyT$0P# on 2017-11-19
> **poorguy said:**
> Any difference using terminal command **firejail   firefox**  and then using **"New Private Window"** then what you are using.
It's totally different.  From [FONT=Courier New]man firejail[/FONT] -
```
       --private
              Mount new /root and /home/user directories in temporary filesys&#8208;
              tems.  All  modifications  are  discarded  when  the  sandbox is
              closed.

              Example:
              $ firejail --private firefox


```
Your method keeps the real [FONT=Courier New]/root[/FONT] and [FONT=Courier New]/home/user[/FONT] directories, and also enables private browsing in Firefox.

---

### Post by linuxyogi on 2017-11-25
> **poorguy said:**
> Any difference using terminal command **firejail   firefox**  and then using **"New Private Window"** then what you are using.

I can no longer use firejail. When I start firefox with ```
firejail firefox
``` I get 

[ATTACH=CONFIG]277666[/ATTACH]

I am using 18.04.

---

### Post by &amp;KyT$0P# on 2017-11-25
> **linuxyogi said:**
> I can no longer use firejail. When I start firefox with ```
firejail firefox
``` I get 

[ATTACH=CONFIG]277666[/ATTACH]

I am using 18.04.
What happens if you run
```
firejail --noprofile firefox
```

---

### Post by linuxyogi on 2017-11-25
> **halogen2 said:**
> What happens if you run
```
firejail --noprofile firefox
```

If I do ```
firejail --noprofile firefox
``` firefox connects to web successfully.

What is the meaning of "--noprofile" ?

I just found out that if I use the "--noprofile" option I can access the entire /home which was not the case with ```
 firejail firefox
```.

With ```
firejail firefox
``` only the ~/Downloads folder was reachable.

---

### Post by &amp;KyT$0P# on 2017-11-26
> **linuxyogi said:**
> If I do ```
firejail --noprofile firefox
``` firefox connects to web successfully.

What is the meaning of "--noprofile" ?
[FONT=Courier New]firejail[/FONT] by default uses "profiles" to add extra sandboxing tuned to each application.  These profiles are located in [FONT=Courier New]/etc/firejail[/FONT] (system-wide / default) and [FONT=Courier New]~/.config/firejail[/FONT] (per-user, useful for overriding system-wide profiles).  [FONT=Courier New]--noprofile[/FONT] disables the use of these profiles.

Try copying the firefox profile into your per-user profiles, and adding a line like this -
```
dns 127.0.0.53
```
I don't use 18.04 yet, so I'm not sure if 127.0.0.53 is the right IP.  The correct IP address is the actual IP your computer uses as a DNS server, as given by this command -
```
cat /etc/resolv.conf
```

---

### Post by linuxyogi on 2017-11-26
> **halogen2 said:**
> [FONT=Courier New]firejail[/FONT] by default uses "profiles" to add extra sandboxing tuned to each application.  These profiles are located in [FONT=Courier New]/etc/firejail[/FONT] (system-wide / default) and [FONT=Courier New]~/.config/firejail[/FONT] (per-user, useful for overriding system-wide profiles).  [FONT=Courier New]--noprofile[/FONT] disables the use of these profiles.

Try copying the firefox profile into your per-user profiles, and adding a line like this -
```
dns 127.0.0.53
```
I don't use 18.04 yet, so I'm not sure if 127.0.0.53 is the right IP.  The correct IP address is the actual IP your computer uses as a DNS server, as given by this command -
```
cat /etc/resolv.conf
```

Did the following 

```
cp /etc/firejail/firefox.profile ~/.config/firejail  
```
```
nano ~/.config/firejail
```


Then added 


```
# Firejail profile for firefox
# This file is overwritten after every install/update
# Persistent local customizations
include /etc/firejail/firefox.local
# Persistent global definitions
include /etc/firejail/globals.local

noblacklist ~/.cache/mozilla
noblacklist ~/.config/okularpartrc
noblacklist ~/.config/okularrc
noblacklist ~/.config/qpdfview
noblacklist ~/.kde/share/apps/okular
noblacklist ~/.kde/share/config/okularpartrc
noblacklist ~/.kde/share/config/okularrc
noblacklist ~/.kde4/share/apps/okular
noblacklist ~/.kde4/share/config/okularpartrc
noblacklist ~/.kde4/share/config/okularrc
noblacklist ~/.local/share/gnome-shell/extensions
noblacklist ~/.local/share/okular
noblacklist ~/.local/share/qpdfview
noblacklist ~/.mozilla
noblacklist ~/.pki

include /etc/firejail/disable-common.inc
include /etc/firejail/disable-devel.inc
include /etc/firejail/disable-programs.inc

mkdir ~/.cache/mozilla/firefox
mkdir ~/.mozilla
mkdir ~/.pki
whitelist ${DOWNLOADS}
whitelist ~/.cache/gnome-mplayer/plugin
whitelist ~/.cache/mozilla/firefox
whitelist ~/.config/gnome-mplayer
whitelist ~/.config/okularpartrc
whitelist ~/.config/okularrc
whitelist ~/.config/pipelight-silverlight5.1
whitelist ~/.config/pipelight-widevine
whitelist ~/.config/qpdfview
whitelist ~/.kde/share/apps/okular
whitelist ~/.kde/share/config/okularpartrc
whitelist ~/.kde/share/config/okularrc
whitelist ~/.kde4/share/apps/okular
whitelist ~/.kde4/share/config/okularpartrc
whitelist ~/.kde4/share/config/okularrc
whitelist ~/.keysnail.js
whitelist ~/.lastpass
whitelist ~/.local/share/gnome-shell/extensions
whitelist ~/.local/share/okular
whitelist ~/.local/share/qpdfview
whitelist ~/.mozilla
whitelist ~/.pentadactyl
whitelist ~/.pentadactylrc
whitelist ~/.pki
whitelist ~/.vimperator
whitelist ~/.vimperatorrc
whitelist ~/.wine-pipelight
whitelist ~/.wine-pipelight64
whitelist ~/.zotero
whitelist ~/dwhelper
include /etc/firejail/whitelist-common.inc

caps.drop all
netfilter
nodvd
nogroups
nonewprivs
noroot
notv
protocol unix,inet,inet6,netlink
seccomp
shell none
tracelog

# private-bin firefox,which,sh,dbus-launch,dbus-send,env
private-dev
# private-etc passwd,group,hostname,hosts,localtime,nsswitch.conf,resolv.conf,xdg,gtk-2.0,gtk-3.0,X11,pango,fonts,firefox,mime.types,mailcap,asound.conf,pulse
private-tmp

noexec ${HOME}
noexec /tmp
[COLOR=#ff0000]dns 127.0.0.53[/COLOR]
```

```
cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
[COLOR=#ff0000]nameserver 127.0.0.53[/COLOR]

```

Still cant connect with ```
firejail firefox
```

---

### Post by linuxyogi on 2017-11-26
Bump

---

### Post by lisati on 2017-11-28
*Thread moved to **Ubuntu Development Version**.*

---

### Post by zika on 2017-11-29
Does```
/usr/bin/firejail --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox
```work?

---

### Post by linuxyogi on 2017-11-29
> **zika said:**
> Does```
/usr/bin/firejail --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox
```work?

Yes that works but I can read the entire home folder which was not the case with ```
firejail firefox 
```

---

### Post by zika on 2017-11-29
> **linuxyogi said:**
> Yes that works but I can read the entire home folder which was not the case with ```
firejail firefox 
```I did not claim that given was a solution, just wanted to see what is the current situation at that install. What about```
[COLOR=#000000][FONT=&quot]/usr/bin/firejail --private --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox[/FONT][/COLOR] 
```?

---

### Post by linuxyogi on 2017-11-29
> **zika said:**
> I did not claim that given was a solution, just wanted to see what is the current situation at that install. What about```
[COLOR=#000000][FONT=&amp]/usr/bin/firejail --private --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox[/FONT][/COLOR] 
```?

```
[COLOR=#000000][FONT=&amp]/usr/bin/firejail --private --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox[/FONT][/COLOR]
```

^^ That also connects successfully.

---

### Post by zika on 2017-11-29
> **linuxyogi said:**
> ```
[COLOR=#000000][FONT=&amp]/usr/bin/firejail --private --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox[/FONT][/COLOR]
```^^ That also connects successfully.But, does it meet Your goal of making Your home folder unaccessible? If it does than You have all You need to adjust Your FireFox FireJail profile to meet Your goal...

---

### Post by linuxyogi on 2017-11-29
> **zika said:**
> But, does it meet Your goal of making Your home folder unaccessible? If it does than You have all You need to adjust Your FireFox FireJail profile to meet Your goal...

No, I can still browse my entire /home/username.

---

### Post by zika on 2017-11-29
> **linuxyogi said:**
> No, I can still browse my entire /home/username.Then something is wrong since that works on so many machines I've tried it on... ;) 'Re You sure that it is Your home that You see? You can browse actual home folder from FF (Ctrl-O)?

---

### Post by linuxyogi on 2017-11-29
> **zika said:**
> Then something is wrong since that works on so many machines I've tried it on... ;) 'Re You sure that it is Your home that You see? You can browse actual home folder from FF (Ctrl-O)?

I am really sorry. I just double checked and I cant browser my  /home/username. Thanks a lot. 

No the next question how do I configure the FF icon to use firejail ?

---

### Post by linuxyogi on 2017-11-29
Soory one more thing every time I launch FF with 

```
[COLOR=#000000][FONT=&amp]/usr/bin/firejail --private --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox[/FONT][/COLOR]
```

I get a new FF window meaning no bookmarks/history how do I get those back ?

---

### Post by zika on 2017-11-29
> **linuxyogi said:**
> Soory one more thing every time I launch FF with```
[COLOR=#000000][FONT=&amp]/usr/bin/firejail --private --noroot --noprofile --dns=8.8.8.8 --dns=9.9.9.9 /usr/bin/firefox[/FONT][/COLOR]
```I get a new FF window meaning no bookmarks/history how do I get those back ?Than it is working... ;) You can, now customize what You do want to have access to and what should be kept behind... Do stroll through [https://firejail.wordpress.com/features-3/man-firejail/](https://firejail.wordpress.com/features-3/man-firejail/) and search for *blacklist* and *private*... You will see how much You could do and that it is only Your imagination that is a limit... ;)

---

### Post by linuxyogi on 2017-11-29
> **zika said:**
> Than it is working... ;) You can, now customize what You do want to have access to and what should be kept behind... Do stroll through [https://firejail.wordpress.com/features-3/man-firejail/](https://firejail.wordpress.com/features-3/man-firejail/) and search for *blacklist* and *private*... You will see how much You could do and that it is only Your imagination that is a limit... ;)

If I run 

```
$ /usr/bin/firejail --noroot --noprofile --dns=8.8.8.8 --dns=8.8.4.4 /usr/bin/firefox


```

leaving the **--private **I  get back my settings but back to square one meaning I can mount my entire /home/username.

---

### Post by zika on 2017-11-29
> **linuxyogi said:**
> If I run ```
$ /usr/bin/firejail --noroot --noprofile --dns=8.8.8.8 --dns=8.8.4.4 /usr/bin/firefox
```leaving the **--private **I  get back my settings but back to square one meaning I can mount my entire /home/username.Exactly as You should and as I did write above... Leaving You to play and explore. Have fun... ;)
Hint:```
...--private --private-home=.mozilla...
``` ... ;)

---

