---
title: "can't log off unity7 after updates"
date: 2016-11-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-11-12
Update/upgrade .. can't log out of unity7 DE.

---

### Post by QIII on 2016-11-12
Could you describe the behavior you are observing in a little more detail?

I thought you were the one who should be telling us all about how to fix things!  :)

Disappointed.  :(

---

### Post by ventrical on 2016-11-12
> **QIII said:**
> Could you describe the behavior you are observing in a little more detail?

I thought you were the one who should be telling us all about how to fix things!  :)

Disappointed.  :(

hehehe .. thanks..


 When I log on to default desktop (unity7) (zesty) todays updates| when I click the panel pulldown all is working but when I click  'log out'  it just does nothing . No apport error .. nothing. It just stays in unity 7 desktop and does not go back to  lightdm.

Regards..

ps. Yes.. I want to file a bug but want to make sure which package is best to file against.

 regards..

---

### Post by dino99 on 2016-11-12
maybe a zombie process is still running; glance at htop or similar to kill it

---

### Post by ventrical on 2016-11-12
I logged into unity8 from re-boot. Logs out ok from unity8. Then log on to unity7 and can now log out from unity7 back to lightdm.

---

### Post by mc4man on 2016-11-12
It seems very inconsistent atm  & inability to log out from 7 happens quite often here. 
(on some occasions get a  log out to a black screen
Also wireless is screwed up, sometimes get an indicator, sometimes not. Many times connected but no Internet access (have to disconnect, reconnect..

---

### Post by ventrical on 2016-11-12
> **mc4man said:**
> It seems very inconsistent atm  & inability to log out from 7 happens quite often here. 
(on some occasions get a  log out to a black screen
Also wireless is screwed up, sometimes get an indicator, sometimes not. Many times connected but no Internet access (have to disconnect, reconnect..

yes.. I get that too .. a carry over from YY. 

uh... what package do you suggest I can file a bug against with the intermittent log out problem  with unity7?

regards..

---

### Post by mc4man on 2016-11-12
> **ventrical said:**
> yes.. I get that too .. a carry over from YY. 

uh... what package do you suggest I can file a bug against with the intermittent log out problem  with unity7?

regards..
Not sure yet, maybe indicator-session? 
At least here most user side logs are mia, at least in previous location of ~/.cache/upstart, ex. 
 ```
.cache/upstart$ ls
click-user-hooks.log
untrusted-helper-type-end-url-overlay.log  
url-dispatcher.log
systemd-graphical-session.log  
upstart-event-bridge.log

```
That's all.. (- the above 5 are pretty much worthless

---

### Post by mc4man on 2016-11-12
Out of curiosity - do you know the current log out command (used to be gnome-session-quit

If your log out fails I think this may 'sorta'  work, may not cause a true log out... - 
```
/usr/lib/gnome-session/run-systemd-session ubuntu-session.target
```

---

### Post by ventrical on 2016-11-13
> **mc4man said:**
> Out of curiosity - do you know the current log out command (used to be gnome-session-quit

If your log out fails I think this may 'sorta'  work, may not cause a true log out... - 
```
/usr/lib/gnome-session/run-systemd-session ubuntu-session.target
```

Yeah .. that worked just swell.


Second:

It is :
```

sudo logout now

```

in cli. I think.

---

### Post by zika on 2016-11-13
This is why I love *x:```
$ cat run-systemd-session 
#!/bin/sh
set -e
# some old Qt programs still check this long-deprecated env var
dbus-update-activation-environment --systemd GNOME_DESKTOP_SESSION_ID=this-is-deprecated


# stop any lingering active units from a previous session
systemctl --user stop graphical-session.target graphical-session-pre.target
                                                                                
# robustness: if the previous graphical session left some failed units,         
# reset them so that they don't break this startup                              
for unit in $(systemctl --user --no-legend --state=failed list-units | cut -f1 -d' '); do                                               
    if [ "$(systemctl --user show -p PartOf --value $unit)" = "graphical-session.target" ]; then                                        
        systemctl --user reset-failed $unit                                                                                             
    fi                                                                                                                                  
done                                                                                                                                    
                                                                                                                                        
# FIXME: synthesize After=graphical-session-pre.target dependencies until this                                                          
# can be done declaratively (https://github.com/systemd/systemd/issues/3750)                                                            
# This could be a generator, but we don't want to penalize non-graphical logins                                                         
# with this.                                                                                                                            
systemctl --user list-unit-files --no-legend | while read unit status _; do                                                             
    [ "${unit%.*********" != "$unit" ] || continue                                                                                       
    [ "$status" != "$disabled" ] || continue                                                                                            
    if [ "$(systemctl --user show -p PartOf --value $unit)" = "graphical-session.target" ]; then                                        
        mkdir -p "$XDG_RUNTIME_DIR/systemd/user/${unit}.d"                                                                              
        printf '[Unit]\nAfter=graphical-session-pre.target\n' > "$XDG_RUNTIME_DIR/systemd/user/${unit}.d/graphical-session-pre.conf"    
    fi                                                                                                                                  
done                                                                                                                                    
systemctl --user daemon-reload                                                                                                          
                                                                                                                                        
systemctl --user start --wait "$1"                                                                                                      
                                                                                                                                        
dbus-update-activation-environment --systemd GNOME_DESKTOP_SESSION_ID=                                                                  
                                                                                                                                        
# Delay killing the X server until all graphical units stopped                                                                          
systemctl --user stop graphical-session-pre.target
```You can (almost) always understand why something did work and how to do it next time... ;)

---

### Post by mc4man on 2016-11-22
Could be related to either,
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1637758](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1637758)
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1643711](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1643711) # most likely a dupe of above bug..
Here I'm finding it's a matter of time, for log out about 2 min. or so.

---

### Post by ventrical on 2016-11-23
It was working for about a week or so .. this morning also ... THEN .. update/upgrade and it's busted again. One has to reboot first to get the effect.

Regards..

---

### Post by ventrical on 2016-11-23
Yes .. it's busted again after today's upgrades.

---

### Post by mc4man on 2016-11-24
Edit: Not Fixed here with latest lightdm package - 1.21.1-0ubuntu2, seemed ok for one boot, now back to same inc. certain autostarts being delayed (PolicyKit Auth.., nm-applet, ect.

---

### Post by ventrical on 2016-11-24
I can run a few programs/apps and it then seems I can log off from the session .. but it is intermittent.

---

### Post by mc4man on 2016-11-24
> **ventrical said:**
> I can run a few programs/apps and it then seems I can log off from the session .. but it is intermittent.
For curiosity you could try - In System Settings > User Accounts set to auto login. Reboot & see if you can log out immediately  after desktop shows up.

---

### Post by ventrical on 2016-11-24
> **mc4man said:**
> For curiosity you could try - In System Settings > User Accounts set to auto login. Reboot & see if you can log out immediately  after desktop shows up.

Yeah .. it works as you said .. but it comes up with the login keyring locked and I have to enter password.. so no problem really.  Uh.. it blinks the plymouth screen about 4 or 5 times.. it sort of like it is bootstrapping itself a few times before it will go to the desktop with the keyring notification.

---

### Post by mc4man on 2016-12-05
This (logout) seems to be caused by unity8* even if one never logs into it. 
Also here wireless is a mess in 17.04, doesn't connect for 60-120 secs, then after 10 min lose the internet until a reboot.

Purging unity8 & then an autoremove followed by a  reboot  resolves all these issues & the inability to run polkit actions right after login, ect.

---

