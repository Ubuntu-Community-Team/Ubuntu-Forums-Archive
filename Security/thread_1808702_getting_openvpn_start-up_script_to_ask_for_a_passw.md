---
title: "getting openvpn start-up script to ask for a password"
date: 2011-07-20
forum: Security
---

### Post by greybeard95a on 2011-07-20
Hi all,

I have to say, I'm a little astonished at how anxious people are to bypass password checks on networks, all for the convenience of having things come up automatically.  But given the world as we find it, I'm seeking a different approach.

I have an OpenVPN network.  It works fine, but for my laptop, I've selected a client certificate that requires a password, so that if it falls into nefarious hands, the thief will not have immediate access to the VPN.

I'm trying not to have any data at all on the laptop (yes, a waste of a 500GB drive).  So I want the VPN up even before I log in through the GUI.

It would be nice if the boot-up sequence would pause for the openvpn start script to ask for this password.  I see the script contains a line "# X-Interactive:     true" which I understand from documentation is supposed to accomplish this.  But it doesn't.  OpenVPN simply fails to start, which is better than the alternative, but a pain.

I have already disabled the splash screen (having been around Linux for over ten years, I am more comfortable seeing boot-up messages anyway, though even on this x86 they flash on so quickly I'm not sure I'm really gaining anything).

What am I missing?

Thanks!

---

### Post by stlsaint on 2011-07-21
Have you tried visiting the official openvpn website or the irc channel?

---

### Post by greybeard95a on 2011-07-22
The modification I'm seeking is in the Ubuntu startup sequence.  If I run the start script by hand, it does indeed ask for the password.

I would like it to ask for the password when the system is booting.

Thanks!

---

