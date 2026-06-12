---
title: "Network authentication at home."
date: 2020-01-11
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2020-01-11
I need to streamline user creation and uids / gids across 12 lxd containers, a desktop, and 5 pxe booted media centers / desktops using LTSP. Right now I use the same uids and gids but its getting a bit unmanageable. Thinking an nfs shared /home that can be mounted anywhere and on any device with the exception of my lxd containers where the directories would be added via lxc config.

I'm stuck on ldap or nis. Ideally I'd like to add a user in one place and have it available across the network along with a single home directory. I really don't understand either. I've tried nis with no success awhile back. Where should I go from here?

---

### Post by TheFu on 2020-01-11
NIS isn't secure, but it is really easy.  I ran NIS for a few different companies in the 1990s for years.  I don't recall the details, but once you have it down, it is 5 minutes to setup the maps for passwd, group, hosts, netgroups and/or services.

LDAP on Ubuntu is lacking.  Enterprises seem to use either RHEL or CentOS and run FreeIPA as the server.  I've heard that FreeIPA Server is available for Ubuntu/Debian, but I've not tried it.  I use an LDAP server built into Zimbra, but only because Zimbra is mandatory for the network here.

If you have the same users and groups and don't want the hassle of using FreeIPA for a tiny environment, perhaps something like **ansible** to automate it would be viable?  Heck, a 10 line script could be used, just go with uids that are a little higher than the defaults - say 1050-1070.  To make NFS happy, the uid numbers have to match on all systems.

Something worth considering is how much Canonical's future use of snap packages might break with NFS.  Saw a thread about NFS and snapd a few days ago.  It was unclear whether there was any resolution for NFS and snaps or not.  Have you seen any issues?

---

### Post by Tadaen_Sylvermane on 2020-01-12
I ended up going with NIS for now. I haven't got my desktop / server working off it yet but that seems to be an issue with GDM3 and Nis in 18.04. My Nis however is covering all containers and ltsp pxe boot machines. Leaving me a total of 3 "machines" to manage users on. I'd rather it just be 2, the laptop and the Nis server but I'll take what I can get.

As far as the NFS is considered I'm not sure it's going to be a problem. As most of my focus is LTSP for all deployment and my LTSP servers are in LXD containers then I can just share my server /home/"$USER" directories via lxc config device add to the proper machines. Seems to work just fine so I'm avoiding NFS mostly. The only nfs use is direct media sources in Kodi.

---

