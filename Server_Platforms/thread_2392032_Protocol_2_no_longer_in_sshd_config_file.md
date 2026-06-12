---
title: "Protocol 2 no longer in sshd_config file"
date: 2018-05-15
forum: Server Platforms
---

### Post by tleroy1 on 2018-05-15
In Ubuntu 18.04 Server, in the /etc/ssh/sshd_config file, there is no longer a commented out line for Protocol 2.

Does this mean that Ubuntu 18.04 no longer supports legacy versions of the SSH protocol and this entry is deprecated?

I saw nothing about this in the Release Notes: [COLOR=#29303B][FONT=Arial]https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes[/FONT][/COLOR][COLOR=#29303B][FONT=Arial]&#8203;

It would be great if any changes to configuration files were listed there.

Kind regards,

Ted[/FONT][/COLOR]

---

### Post by Doug S on 2018-05-16
> **tleroy1 said:**
> In Ubuntu 18.04 Server, in the /etc/ssh/sshd_config file, there is no longer a commented out line for Protocol 2.

Does this mean that Ubuntu 18.04 no longer supports legacy versions of the SSH protocol and this entry is deprecated?

I think what has happened is that protocol 1 has been deleted, and thus there is no longer an option for protocol because there is only the one (meaning protocol 2) now.
 
Reference:
[https://www.openssh.com/txt/release-7.6](https://www.openssh.com/txt/release-7.6) see "Potentially-incompatible changes" (copied below):

```
This release includes a number of changes that may affect existing
configurations:

 * ssh(1): delete SSH protocol version 1 support, associated
   configuration options and documentation.
```

---

### Post by tleroy1 on 2018-05-29
> **Doug S said:**
> I think what has happened is that protocol 1 has been deleted, and thus there is no longer an option for protocol because there is only the one (meaning protocol 2) now.
 
Reference:
[https://www.openssh.com/txt/release-7.6](https://www.openssh.com/txt/release-7.6) see "Potentially-incompatible changes" (copied below):

```
This release includes a number of changes that may affect existing
configurations:

 * ssh(1): delete SSH protocol version 1 support, associated
   configuration options and documentation.
```

Thanks Doug,

I missed that in the release notes. That answers my question.

Kind regards,

Ted

---

