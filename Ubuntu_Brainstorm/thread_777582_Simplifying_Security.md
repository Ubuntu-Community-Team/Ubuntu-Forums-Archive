---
title: "Simplifying Security"
date: 2008-05-01
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-01
I'm thinking of putting the below in as an initial specification - does anyone have any suggestions, comments or improvements?

> Currently there are many security trade-offs in Ubuntu (for example extra services like avahi running by default).

I propose that security is tiered into easy to select levels, which can be selected by the user, or customized.  There would be two types of security - local and remote, and 3 levels for each.

[SIZE="4"]Local Security[/SIZE]
[LIST]
[*]**High Security**
The bootloader password would be enabled.  If a system error occurs, it will not drop to a root prompt without a password.  Disk encryption may be enabled by default.  Password complexity rules will be enforced.  This mode can be used for kiosk computers or high security installations.
[*]**Medium Security**
The current security defaults.  This mode can be used for home computers with multiple users or small offices.
[*]**No Security**
There will be passwordless automatic logon to a default user.  Sudo will require just a single click to allow administrative actions.  This mode can be used for home computers with a single user where local physical security is unimportant.
[/LIST]
[SIZE="4"]Remote Security[/SIZE]
[LIST]
[*]**Very High Security**
No incoming or outgoing connections are allowed by default.  The system does not respond to pings.  Remote logins are not permitted.  Exceptions may be made only by users with sudo access.  This mode can be used for business mission critical computers connected directly to the public internet.
[*]**High Security**
The current security defaults.  Outgoing connections are allowed, and a minimal number of services accept incoming connections.  Remote user logins (vnc, ssh, XDMCP) are disabled by default.  This mode can be used for computers connected directly to the internet.
[*]**Medium Security**
As above except remote logins are allowed with a password.  This mode can be used for home computers on a relatively secure internal network protected by a hardware firewall/NAT router.
[/LIST]
The default configuration would be Medium local security and High remote security.

---

### Post by Ripfox on 2008-05-01
> **CrazyGuy123 said:**
> I'm thinking of putting the below in as an initial specification - does anyone have any suggestions, comments or improvements?

Save a spell check, it's not a bad concept.

---

