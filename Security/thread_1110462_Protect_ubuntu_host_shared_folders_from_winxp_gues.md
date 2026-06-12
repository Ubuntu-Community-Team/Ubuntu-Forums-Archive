---
title: "Protect ubuntu host shared folders from winxp guest on VBox?"
date: 2009-03-29
forum: Security
---

### Post by talz13 on 2009-03-29
Are there some steps to take to protect the data on my ubuntu system from any nasties that winxp in VirtualBox might pick up?  I have my "Documents" folder shared to the winxp VM, but am concerned that if something got on xp it could just wipe out the data in ubuntu, since it is R/W shared.  I never really thought about it before, but it could be pretty bad!

---

### Post by bodhi.zazen on 2009-03-30
First assign your windows guest a static IP address

Just block your samba ports from your windows ip address, either in your samba config file or with iptables.

---

### Post by talz13 on 2009-03-30
Well, that's all well and good, but it still needs access to the VirtualBox shares.  I run nod32 AV on the windows VMs, and try not to do much internet browsing on there.  Can you filter what gets to a VM on host networking?  With iptables or using moblock?  Would that even do anything?

---

### Post by bodhi.zazen on 2009-03-30
> **talz13 said:**
> Well, that's all well and good, but it still needs access to the VirtualBox shares.  I run nod32 AV on the windows VMs, and try not to do much internet browsing on there.  Can you filter what gets to a VM on host networking?  With iptables or using moblock?  Would that even do anything?

It seems to me you are making this more complicated then it needs to be.

You can block your samba traffic with iptables or within your smaba config file.

In samba , add a single line to /etc/samba/smb.conf

```
"hosts deny = 111.22.333.44"
```

See : [https://help.ubuntu.com/community/SettingUpSamba#File%20Sharing%20(Advanced](https://help.ubuntu.com/community/SettingUpSamba#File%20Sharing%20(Advanced))

Where 111.22.333.44 is your windows IP address.

You can also block samba traffic with iptables

sudo iptables -A INPUT -s 111.22.333.44 -p tcp --dport samba_tcp_ports -j DROP

You will need to fill in your windows ip address and samba tcp ports.

You will also need to save those changes or they will be lost when you reboot.

See :  [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

As far as sharing files you have many options, shared forlders, use a flash driver, use another network protocol such as ssh (winscp).

I do not think either solution I posted will affect these protocols.

---

### Post by talz13 on 2009-03-30
I guess I'm looking from the perspective of protecting the shared files from infection by a compromised VM that has access to them.  I guess there's not a great way of protecting accessible files from a machine that has access to them, is there, without revoking access...

---

### Post by bodhi.zazen on 2009-03-30
> **talz13 said:**
> I guess I'm looking from the perspective of protecting the shared files from infection by a compromised VM that has access to them.  I guess there's not a great way of protecting accessible files from a machine that has access to them, is there, without revoking access...

Not that I know of ...

You could perhaps give read only access.

---

### Post by hyper_ch on 2009-03-30
can't you make it just "read only" in the vbox share? in vmware you can mark shared folders from host as read only.

---

### Post by talz13 on 2009-03-30
> **hyper_ch said:**
> can't you make it just "read only" in the vbox share? in vmware you can mark shared folders from host as read only.

True, you can, just that it still needs write access.  I think I'm just living in a dream world here lol... I guess I'll just have to keep up good antivirus, etc. on the VMs to try to prevent havoc on the shares.

---

### Post by hyper_ch on 2009-03-30
well, you can make most of it read only and only one "exchange" folder write access...

---

### Post by talz13 on 2009-03-30
> **hyper_ch said:**
> well, you can make most of it read only and only one "exchange" folder write access...

That might work, I'll have to try it out.

---

