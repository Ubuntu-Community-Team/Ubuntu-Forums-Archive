---
title: "Ubuntu AD Join - Kerberos Ticket not used when gio mount SMB Share"
date: 2023-08-24
forum: Security
---

### Post by furydev on 2023-08-24
Dear All, 

I have an SSSD joined Active Directory Domain. Its important Ubuntu uses SSSD as it ties in with other methods we use well. The intergration seems to work well. 

However - when we use our Kerberos tickets to gio mount smb shares - the mount asks for a password. Which is curious as klist shows we have a valid ticket. 

If we kinit and enter the password for the user the gio mount then takes place without asking for credentials.

We are desperate to get this working as it lets the dev team use their OS of choice. 

Any pointers gratefully received.

---

### Post by dotdotdot3 on 2023-09-06
Hi.

My setup also authenticates and AD via SSSD, and I mount quite a few locations, including the home directory.
I use pam_mount and never had any authentication issues like the ones you describe.

Would that be a solution for you?

---

