---
title: "Fresh install 14.04.1 restored backups openldap+samba settings, ldap groups invalid"
date: 2014-09-04
forum: Server Platforms
---

### Post by Pro_D on 2014-09-04
So I installed 14.04.1 fresh because I couldn't get 12.04.5 to do a proper upgrade (only partial, even repeatedly restoring binary backup of partition to try again), probably because I did a few "make install" instead of "checkinstall" but that's a guess (I haven't had ubuntu upgrade properly yet).  I also have Lubuntu-Desktop installed (ubuntu server first) as I find it just too darned useful to have gui applications on a server, if for no other reason than to run them via X11 forwarding (though I do VNC in now and then).

I've restored backups of openldap and samba configurations.  In ldap case I used slapadd to restore from backed up slapcat ldiffs from the old system.  Samba apparently can do in place upgrades to it's data files in most cases (at least after about 2.2) so that went smoothly.
In the end I'm able to authenticate computers/users on windows machines like before (no change on their end) and they are able to browse each other's shares including shares which are restricted by group.
Windows machines are able to browse shares of the server but ONLY if the share is limited by user account and NOT by group.  (Hadn't tried non-ldap groups.)

On the server machine when I try something like 'chown :"Domain Users" directory' I get back "chown: invalid group: Domain Users"  Tabbed auto-completion works for the other ldap groups which don't have a space in it (ie Administrators).  Similar error (replace Domain Users with Administrators).
On the windows machines when I try to browse a share which the filesystem is restricted by an ldap group I get back "The group name could not be found."  Found out that removing the directive "force group" in smb.conf allowed the windows user to connect to the share, doesn't fix the local linux side of things though.  I'm not getting anything that seems to lead somewhere via smbd logs level set to 1 nor at 3.  The logs implied normal operation for uid and gid.

This leads me to think that the permissions mechanism for the server aren't referencing ldap groups properly.  Directories which retain ldap permissions (from before the upgrade) show the group name properly instead of the group as a number.
The only difference from a fresh install and rebuilding from scratch (my old configuration) and now is that I restored the ldap databases from backup and that I am now using the /etc/ldap/slap.d/ directory configuration instead of a single flat file /etc/ldap/slap.conf.
I still have a read only view of the old 12.04.5 including the old mount points so I can have a look around and interrogate old data files.  I can also boot into that if needed, though I've disabled most services.  On the thought that maybe I was missing a package this time around on the old system I did a "dpkg --list |grep 'ldap'|less" and verified that all the packages I had before are also in 14.04.1 now (or at least equivalent).  Actually there was one package, on the old system I had "libldap-2.4-2:i386" which is absent on 14.04.1 but I gather that the ":i386" is for x86 compatibility.  Both systems are x64.

ldap stuff generally confounds me.  I don't really know what information could be of use.  It seems like openldap is functioning correctly though...
"getent group" looks right in that the ldap groups are listed with expected memberships.  Though I don't remember the asterisks (Domain Users:*:513).  I've not used this command much in the past.
"id <username>" gives expected output for group membership, including ldap groups.
After some time figured out that the directive in samba "Force Group =" was helping to cause the windows error, however that directive (unlike valid users which no longer works for me) is one that I use (read list and write list seem to provide for what valid users was doing).

After spending the bulk of yesterday searching on this and a chunk of this morning I'm at a loss.

[edit]
I Can't believe I didn't notice but I was missing libpam-smbpass and libpam-winbind (also winbind) which I had on the old configuration.  I don't think I was using winbind (ie disabled the service), hard to remember.

Unfortunately it didn't fix things, though I've got some new errors to research...
When I "sudo -s" I now get several lines, starting with "no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory"
That doesn't sound good...  The other lines look like log entries from either smbd or openldap.  Also some new entries in my logs.
The full output:
```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
WARNING: The "null passwords" option is deprecated
WARNING: The "idmap backend" option is deprecated
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
smbldap_search_domain_info: Searching for:[(&(objectClass=sambaDomain)(sambaDomainName=MYDOMAIN))]
smbldap_open_connection: connection opened
ldap_connect_system: successful connection to the LDAP server
init_sam_from_ldap: Entry found for user: theuser
Forcing Primary Group to 'Domain Users' for theuser
init_sam_from_ldap: Entry found for user: theuser
Forcing Primary Group to 'Domain Users' for theuser
init_ldap_from_sam: Setting entry for user: theuser
Could not set userPassword attribute due to an objectClass violation -- ignoring
ldapsam_update_sam_account: successfully modified uid = theserver in the LDAP database
```

Gonna go look around for those a bit, will edit again if I (don't) get anywhere.  I find the bit about an objectClass violation most interesting/worth pursuit.
(I edited the output for the domain and user names to be more generic, the deprecated warnings are from the older configuration for samba however looking at the online docs for samba says nothing about them being deprecated nor suggesting an alternative.)
[/edit]

[edit2]
On further reading I happened on [this bug report]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186") which indicates the bug isn't expected to be rolled into Ubuntu until 14.04.2 (or unless I want to build it myself or use a ppa to stick on closer to upstream)

Additionally it seems like it's unrelated.  The additional errors I get in my logs are the same errors I used to get in my logs.  To put it another way it would seem I didn't need the additional libpam modules to access ldap groups, something else is broken.  All I've done by adding those modules is get distracted (on this particular problem)...

As far as what libpam-smbd does... there is only one user which lives both on the local system and in the ldap database.  All the other users are either specifically part of linux or ldap with no more overlap so I *might* not need this component.  (From reading it syncs passwords between local linux and domain ldap database).

<sigh> I feel so out of my depth...

So rehashing a bit (on the central problem).
-local users/groups fine.
-able to log in to the server with ldap users.  (avoiding assumption: local users log in fine too.)
-surprisingly group permissions get set on new files/folders created by ldap users locally, their primary group is "Domain Users" and echo "test" > file.txt followed by ls -ld file.txt shows the group as "Domain Users" (quotes mine)
-chown :ldapGroup results in invalid group error as either the primary user (setup the system with), root (sudo -s), or ldap users. (this seems closest in connection to the core issue.)

Everything else seems secondary/will be fixed once ldap groups can be utilized.
[/edit2]

---

### Post by bab1 on 2014-09-04
> **Pro_D said:**
> So I installed 14.04.1 fresh because I couldn't get 12.04.5 to do a proper upgrade...

Are you aware of the fact that The ***samba package ***on Ubuntu 14.04 has major changes to the Samba server?  All the earlier versions of Ubuntu package called *samba* **installed Samba v3**.  In Ubuntu 14.04 and later the *samba * package **installs Samba v**4.  The distinction is that Samba v4 (4.1) installs all the parts for LDAP and Kerbros operation. It is fully compatible with Windows Servers that implement Active Directory Domain Controller (AD DC).  

The Samba.org version of OpenLDAP may not be compatible with your version of OpenLAP.

If I was contemplating upgrading to Ubuntu 14.04 and specifically Samba v4.1 using OpenLAP, I think I would create an LDIF file of all my data and upload that to my fully functioning Ubuntu/Sambav4 (4.1) AD/DC.  It should be much simpler to go with Samba v4's version of "DC Promo" to create the domain controller than you modifying things as you are trying to do right now.  There are plenty of tutorials out there by now.  I'd probably [start with this one]("https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO") and maybe [this too]("http://ubuntuforums.org/showthread.php?t=2146198").

If you want to stay with Samba v3 (v3.6) you will have to deal with Ubuntu 12.04.5 LTS.  This version is good until 2017.

Hopefully this is all being tried as a test install rather than something you rely for daily use.

---

