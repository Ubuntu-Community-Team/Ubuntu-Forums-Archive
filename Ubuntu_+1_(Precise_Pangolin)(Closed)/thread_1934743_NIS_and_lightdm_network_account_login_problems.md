---
title: "NIS and lightdm network account login problems"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by borzwazie on 2012-03-02
Hi all - two problems with 12.04 Precise Pangolin beta that I haven't seen discussed here yet:

NIS, and lightdm.

First of all, there seems to be some sort of race condition with ypbind and network, in that I can't bind to the ypserver upon startup. If I restart ypbind afterward, all is well. I will note that I am not using broadcast NIS servers here.

To work around this issue, I had to put an entry in /etc/hosts for the long and short names of the NIS server:

```

# an example NIS server name. Probably not yours.
192.168.1.1    nis nis.freakynetwork.mine

```

After this, ypcat passwd, etc work on boot without having to restart ypbind. Probably we need some additional delay built into ypbind startup for DNS to become available.

The second issue I ran into is with lightdm. I could not figure out how to make lightdm show me "Other" logins, even though NIS was working. In the end, I had to move back to gdm, which worked immediately.

Hopefully this helps someone else, and if I missed the specific bug searching here, please feel free to correct me.

EDIT: Minor things: I don't care at all for app launchers on every screen in multi-monitor, and the edge detection between the two screens drives me up a wall, but you can eliminate most of that with ccsm. That said, I think this beta runs better than 11.10 did for me.

---

### Post by grahammechanical on 2012-03-02
Well, it just goes to show does it not?

A lot of work has gone in to getting the Launcher to appear on both screens in dual monitor mode. It seems that a lot of people wanted it that way. But not you.

At the LightDM log on screen we click on the Ubuntu icon just by the password panel. You also need alternative User Interfaces installed otherwise the most you will see is Ubuntu and Ubuntu 2D.

Regards.

---

### Post by borzwazie on 2012-03-02
> **grahammechanical said:**
> Well, it just goes to show does it not?

A lot of work has gone in to getting the Launcher to appear on both screens in dual monitor mode. It seems that a lot of people wanted it that way. But not you.

At the LightDM log on screen we click on the Ubuntu icon just by the password panel. You also need alternative User Interfaces installed otherwise the most you will see is Ubuntu and Ubuntu 2D.

Regards.

Regarding the "Alternative User Interfaces" - that's not what I'm talking about at all. The 12.04 lightdm greeter doesn't give any non-local user (read: network account) the ability to login. In 11.10, you could choose "Other..." but that option doesn't exist in 12.04. I suspect a bug, rather than a deliberate omission.

For the multi-monitor launcher, yes, not for me. Yucky. YMMV. Nothing personal, it's just redundant clutter to me. Plus, I'm afraid I don't get the decision to make the center between two monitors "sticky."

---

### Post by effenberg0x0 on 2012-03-03
Did you cd /var/yp and ran 'make' to update the user db? 
BTW, when the service is restarted, does cat /etc/passwd shows remote users with UIDs > 500? (Lightdm displays only these, see cat /etc/lightdm/users.conf).

I'm just guessing here (I use NFS with idmapd to sync UIDs GIDs. No NIS).

Regards,
Effenberg

---

