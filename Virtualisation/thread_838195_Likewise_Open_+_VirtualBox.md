---
title: "Likewise Open + VirtualBox"
date: 2008-06-23
forum: Virtualisation
---

### Post by sco01 on 2008-06-23
Hello,

I'm logged in against an AD server using Likewize Open. I installed VirtualBox but i can't run it using the domain user. I have added the domain user (on the format domain\user) to the /etc/group file for the vboxusers group and logged out and back in again. The only way for me to get virtualbox running is to start it from a terminal with sudo or to run using a local account that belongs to the vboxusers group. I notice that typing "id" in a terminal only returns the domain groups and not the local groups. Any ideas?

//stefan

It is strange, but the group member names for vboxusers are case sensitive even if no other group seems to care about case. I usually log in with the following username syntax: domain\user. This gets translated to DOMAIN\user by the AD so the who command reports me as DOMAIN\user. When i added this user (using uppercase domain) to /etc/group for the vboxusers group and logged out/in again i got the problem described above. simply changing the user name to all lowercase in the group file made it work. 

Can somebody explain why this group is case sensitive when the admin group is case insensitive?

//Stefan

---

