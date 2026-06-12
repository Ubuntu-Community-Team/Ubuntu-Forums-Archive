---
title: "Annoying Firefox and NetworkManager &quot;dependencies&quot;"
date: 2009-11-13
forum: Ubuntu One (CLOSED)
---

### Post by RavanH on 2009-11-13
Despite of the promising service, I think I'll not be using Ubuntu One as long as two very annoying problems I have run into, have not been taken care off. These are:

[LIST][*] U1 will not run first time "Authorize Your Computer" routine when Firefox is not set as the default browser (Preferred Applications)

[*] U1 will not connect on systems that do not use NetworkManager for their internet connection.[/LIST]

Is there any outlook on these things being addressed in the near future?

Thanks!

---

### Post by RavanH on 2009-11-14
To fix the NM problem, a patch has been suggested on [https://bugs.launchpad.net/ubuntuone-client/+bug/357395](https://bugs.launchpad.net/ubuntuone-client/+bug/357395) (comment #46) by nickurak:

```
cd /usr/share/pyshared/ubuntuone/oauthdesktop/; wget -O - http://nickurak.ca/ubuntuone-ignore-missing-nm.patch | sudo patch -p0
```

No idea if it is save to do this but at least there is progress on this issue :)

---

### Post by DarkN00b on 2009-11-15
I can confirm that fixed my connection problems. Ubuntu-One now authorizes and syncs correctly.

This is the full text of the patch: ```
--- auth.py.dist	2009-10-29 07:53:44.000000000 -0600
+++ auth.py	2009-11-13 17:58:58.161394889 -0700
@@ -290,7 +290,8 @@
 
             def got_error(error):
                 """Handler for D-Bus errors when calling state()."""
-                logger.error("Unable to contact NetworkManager")
+                logger.error("Unable to contact NetworkManager. Trying anyway.")
+                self.acquire_access_token(description, store)
 
             iface.state(reply_handler=got_state, error_handler=got_error)
```

It appears to be safe.

---

### Post by gerowen on 2009-11-18
When I do the sudo patch -p0 it just sits there, no real processor or hard drive activity while it sits there.

---

### Post by DarkN00b on 2009-11-22
> **marcusdean.adams said:**
> When I do the sudo patch -p0 it just sits there, no real processor or hard drive activity while it sits there.

You have to run it as a superuser. Try ```
cd /usr/share/pyshared/ubuntuone/oauthdesktop/; wget -O - http://nickurak.ca/ubuntuone-ignore-missing-nm.patch | sudo patch -p0
```

That should do it.

---

### Post by gerowen on 2009-11-22
It just started working, I deleted the directory ~/.local/share/ubuntuone/syncdaemon and the ~/.config/ubuntuone/ubuntuone-client.conf files and it started connecting while I'm using wicd.

---

### Post by feydrutha on 2009-11-26
> **RavanH said:**
> 
[LIST][*] U1 will not run first time "Authorize Your Computer" routine when Firefox is not set as the default browser (Preferred Applications)

[*] U1 will not connect on systems that do not use NetworkManager for their internet connection.[/LIST]


I also encountered the second problem you mention when trying to use ubuntu one. In my case, there was no fundamental reason I couldn't use NetworkManager (desktop computer with a single wired etherenet card using dhcp... doesn't get any simpler!). So I solved it by installing network manager and removing the lines about eth0 from /etc/network/interfaces. 

The problem was that there was no feedback whatsoever, until I ran ubuntuone-client-applet and got an error message about network manager being missing. Even then it took me a while to realise I really did not have network manager installed.

Easily worked around in my case. Still, I suppose the default behavior should be to try to reach the server to test for connectivity when network manager is not available to provide this information.

---

### Post by joshuahoover on 2009-11-30
> **feydrutha said:**
> I also encountered the second problem you mention when trying to use ubuntu one. In my case, there was no fundamental reason I couldn't use NetworkManager (desktop computer with a single wired etherenet card using dhcp... doesn't get any simpler!). So I solved it by installing network manager and removing the lines about eth0 from /etc/network/interfaces. 

The problem was that there was no feedback whatsoever, until I ran ubuntuone-client-applet and got an error message about network manager being missing. Even then it took me a while to realise I really did not have network manager installed.

Easily worked around in my case. Still, I suppose the default behavior should be to try to reach the server to test for connectivity when network manager is not available to provide this information.

For those having problems with the Ubuntu One dependency on NetworkManager, please follow these instructions on installing the Ubuntu One beta PPA for Karmic:

[https://answers.edge.launchpad.net/ubuntuone-client/+faq/836](https://answers.edge.launchpad.net/ubuntuone-client/+faq/836)

Thank you,

Joshua

---

