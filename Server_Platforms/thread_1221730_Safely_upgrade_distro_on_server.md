---
title: "Safely upgrade distro on server"
date: 2009-07-24
forum: Server Platforms
---

### Post by thezood on 2009-07-24
Hello folks!

A friend of mine is running a small Ubuntu server. Now he wants to add some functionality like a proxy server (preferably using Squid). The problem is, he's running ubuntu 7.04 on it. We would like to upgrade the server so that we at least have access to repositories. Another problem is that we are several hundred miles away from the physical location of the server and we're afraid we'll lose critical settings if we try to upgrade the server by SSH console (there's no X windows on the machine). 

Does anyone have any tips of how we can upgrade the machine without loosing all settings? The most critical settings is the static IP settings, because if those were to get removed we will have no way of reaching the machine short of driving to it.

---

### Post by cdenley on 2009-07-24
It is possible, though difficult. Ubuntu does not support a 7.04 > 8.04 upgrade. You can try editing /etc/apt/sources.list, then do a
```

sudo apt-get update
sudo apt-get dist-upgrade

```
but that isn't guaranteed to work well or at all. The "correct" way would be to do a fresh install, but this is very difficult to do remotely.
[https://help.ubuntu.com/community/Installation/OverSSH](https://help.ubuntu.com/community/Installation/OverSSH)

---

### Post by Cheesemill on 2009-07-24
You're going to have problems trying to do this, as support for 7.04 ran out in October last year. You cannot upgrade straight to 8.04, you have to go to 7.10 first but support for this ended in April so the repositories are no longer available.

I know it's a long way away but in all honesty I think a fresh install of 8.04 would be your best option.

---

### Post by thezood on 2009-07-24
Yep, that confirms what I thought. I think if we'd try it, we'd end up with an unreachable machine anyway. Thanks for your quick responses.

---

### Post by koenn on 2009-07-24
I think i's possible to do this, but tricky - If it were my problem, i'd probably attempt a remote upgrade, but plan for having to drive their and fix it locally just in case. 

In a case like this, you really should be using LTS, or arrange for 6 monthly upgrades. Getting stuck without a migration path is not really an option. 

upgrade && distupgrade are plan B. Ubuntu tends to make low-level changes that require special fixes during release upgrades, that's why upgrade-manager is the preferred route

given that you have to traverse unsupported releases, this may not work but you should give it a try anyway. 

```

sudo apt-get install update-manager-core
sudo do-release-upgrade
```


old releases are archived at [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
you can make sources.list point to those and try to upgrade - in stages, 
1- 7.04 to 7.10 , make sure it's working
2- 7.10 to 8.04, this is an LTS so just keep it up to date and upgrade to the next LTS before this one expires.

in each stage, you'll do
- modify sources.list
- apt get update, upgrade, dist-upgrade
- apt-get install -f  ('fix missing') to get you out of trouble when packages half-install for some reason.
repeat (dist-)upgrade / fix missing untill apt-get returns a clean 'nothing to do'

you can do this over ssh - ssh sessions are maintained even when ssh itself is upgraded, and IIRC even when the ssh service is restarted. But do read the msg displayed during the upgrade process.

lastly, you probably need to reboot to start using the new kernel.
then start all over for the 7.10 to 8.04 step.


If it's a real server I don't think you should worry too much about loosing network. If you have desktop user-friendly stuff such as network-manager installed there, there's a risk that it want's to manage your network conf and make a mess of it, but otherwise this is reasonably save.

---

### Post by thezood on 2009-07-25
> **koenn said:**
> If it's a real server I don't think you should worry too much about loosing network. If you have desktop user-friendly stuff such as network-manager installed there, there's a risk that it want's to manage your network conf and make a mess of it, but otherwise this is reasonably save.

Great tips! Thanks. It won't hurt to try. The real worry is that the configuration files for the network connection will be overwritten and thereby losing the static IP configuration. But perhaps that could be managed as well, perhaps through have the server send an e-mail with the current IP adress or something like that.

---

### Post by tubezninja on 2009-07-25
> **thezood said:**
> Yep, that confirms what I thought. I think if we'd try it, we'd end up with an unreachable machine anyway. Thanks for your quick responses.

For what it's worth, I've done remote ubuntu distro upgrades via SSH many times now, and haven't had one fail yet.  I've never lost network settings during a do-release-upgrade.  However, my upgrades have all been between current, supported versions.

In the future, it might be best to upgrade to at least the next LTS release before support runs out on the current installed release, so you can avoid having to do fresh installs.

---

### Post by koenn on 2009-07-25
> **thezood said:**
> Great tips! Thanks. It won't hurt to try. The real worry is that the configuration files for the network connection will be overwritten and thereby losing the static IP configuration. But perhaps that could be managed as well, perhaps through have the server send an e-mail with the current IP adress or something like that.

nah, debian-installer detects config files that have been modified by the user and leaves them alone, or at least gives you the option to keep them,  during the install


if you're insecure about this, you could set up a dyndns account for the time being, so you can always find your server by its dyndns fqdn.

---

