---
title: "Unattended upgrades break things every time"
date: 2017-03-23
forum: Server Platforms
---

### Post by Gottier on 2017-03-23
Ubuntu 16.04.

I've got a pretty standard LAMP stack on a webserver. The only thing that's a little different is that AutoSSH is keeping an SSH connection going to an external database. Super basic.

The last two times an unattended upgrade has done its thing, the server has some issues. Last time I couldn't reboot. This time mysql and php were wonky. 

What's the best way to disable this unattended upgrade. I want to do it manually. I can't have this server randomly going down or messing things up.

---

### Post by deadflowr on 2017-03-23
Comment out the entries in the unattended-upgrades file in /etc/apt/apt.conf.d/
Should be 50unattended-upgrades.
Turn it from something like this
```
Unattended-Upgrade::Allowed-Origins {  
        "${distro_id}:${distro_codename}";
	"${distro_id}:${distro_codename}-security";
```
to something like this
```
Unattended-Upgrade::Allowed-Origins {  
//      "${distro_id}:${distro_codename}";
//	"${distro_id}:${distro_codename}-security";
```


And of course alternatively to that, you can always add packages to the blacklist section, if you want.
(That's probably a little more involved, though.)

While I'm sure there is a simple on/off command to disable unattended-upgrades, this method is just easy to do.
And maybe a separate function that is used by unattended-upgrades is something you find useful.
So turning it off wholesale might not be the best solution.

---

### Post by ian-weisser on 2017-03-23
There is no command to disable - if installed, it runs.
However, it's trivial to uninstall: sudo apt purge unattended-upgrades

'purge' instead of 'remove' because many of the important apt settings are in /etc...and that's really hat you are trying to uninstall.

---

