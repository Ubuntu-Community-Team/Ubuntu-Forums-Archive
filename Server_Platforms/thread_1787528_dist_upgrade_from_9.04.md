---
title: "dist upgrade from 9.04"
date: 2011-06-21
forum: Server Platforms
---

### Post by TheMightyGirth on 2011-06-21
Hi All,

I am trying to upgrade a server from 9.04 to the 10.04. Basically as it was running so well it got forgotten about until now and I don't seem to be able to do it.

I understand that I have to update 9.04 to 9.10, then 9.10 to 10.04 however when I follow the "From 9.04 to 9.10" instructions found [here ]("https://help.ubuntu.com/community/UpgradeNotes")I get the following error;

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

It looks to me like it's trying to do the update in one big jump. Does anyone have any advice on how to go about doing this update.

Thanks in advance

Gareth

---

### Post by brettg on 2011-06-21
"An upgrade from 'jaunty' to 'lucid"

You clearly have lucid instead of Karmic in your sources.list file.

Fix this with;
```

sudo sed -i s/lucid/karmic/g /etc/apt/sources.list

```

Repeat to go to Lucid

```
sudo sed -i s/karmic/lucid/g /etc/apt/sources.list
```

Note: If you have references to lucid elsewhere in apt then these need to be removed or changed as well. You can check this with;

```
grep -r lucid /etc/apt/
```

You will need to issue an apt-get update command after making these changes of course.

---

### Post by TheMightyGirth on 2011-06-22
Thanks for the response Brett,

I have run grep through the sources.lst and checked the rest of /etc/apt and it looks clear. I don't want to risk running this through in the middle of a day (it's 10:15am here) so will give it a shot at the end of the day.

again, thanks for the pointer. I'll post back with my results.

Gareth

---

### Post by TheMightyGirth on 2011-06-22
Still get the same error after trying the first code. Looking at my sources.list though I only have references to jaunty. I hope that first sed was supposed to be;

```
sudo sed -i s/jaunty/lucid/g /etc/apt/sources.list
```

As I'm about to try that instead.

---

### Post by TheMightyGirth on 2011-06-22
Ok, so that didn't work either.

I have now been through [this]("https://help.ubuntu.com/community/EOLUpgrades") process and all was going well until it suggested runing do-release-upgrade and I got the same error. Still looks like it's trying to jump a version.

Now running ```
grep -r lucid /
``` to see what that pulls up

---

### Post by TheMightyGirth on 2011-06-22
Nope, I got nothing.

I need a way to tell do-release-upgrade to get Karmic not Lucid.

---

### Post by TheMightyGirth on 2011-06-23
Hi All,

Finally managed to get this to work late last night.

I ended up doing the following;

created new /etc/apt/sources.list as per [this page]("https://help.ubuntu.com/community/EOLUpgrades/Jaunty") but replaced "old-releases" with "archive" and "jaunty" with "karmic"

```
apt-get update
apt-get upgrade
apt-get dist-upgrade

```
reboot

```
lsb_release -a
```
This then had me at v9.10
```
apt-get update
apt-get upgrade
apt-get install update-manager-core
```
(just to be sure)

reboot

```
do-release-upgrade
```

reboot when prompted

```
lsb_release -a
```
and I'm now updated to v10.04.

---

