---
title: "Securing SSH to AD groups and local user"
date: 2016-07-06
forum: Security
---

### Post by dave.sutherland on 2016-07-06
I am attempting to limit access via SSH to only specific AD groups, but would like to allow a local user account as well.  I seem to be able to get either one or the other to work, but not both.

I have modified the sshd_config by adding AllowGroups ad_access_group (where ad_access_group is the name of the AD group) and AllowUsers admin (where admin is the local account name).

AD group access works how you would expect, but the local user, admin, gets a permission denied.  It appears as if it ignoring the AllowUsers when the AllowGroups is configured.  If I comment out the AllowGroups, then the local account can gain access.  

Any ideas?

---

### Post by &amp;KyT$0P# on 2016-07-06
It looks like that maybe by design?  From the sshd_config man page:
```

     **AllowGroups**
             This keyword can be followed by a list of group name patterns,
             separated by spaces.  If specified, login is allowed only for
             users whose primary group or supplementary group list matches one
             of the patterns.  Only group names are valid; a numerical group
             ID is not recognized.  By default, login is allowed for all
             groups.  [COLOR="#FF0000"]The allow/deny directives are processed in the following
             order: DenyUsers, AllowUsers, DenyGroups, and finally
             AllowGroups.[/COLOR]

             See PATTERNS in ssh_config(5) for more information on patterns.
```
(colorizing mine)

Does it work if you create an extra group and add to it only the local users you want allowed to accessing SSH, then add this group to AllowGroups?

---

### Post by dave.sutherland on 2016-07-06
I read that part as well, what is interesting is the order in which it is processed.  If I read it right, it appears that if both AllowUsers and AllowGroups are configured it should process the AllowUsers first, and the local account is in that list.  Why would it continue to check to the AllowGroups?  I also do not see anything that leads me to believe that it has anything to do with AD. I will attempt to create a local group, add the local user to it and then add that group to the AllowGroups Config.  I will also check my sshd_config, I believe I have the AllowGroups in the config before the AllowUsers, maybe that is what is causing the issue.

---

### Post by dave.sutherland on 2016-07-06
So I tried reordering the AllowUsers and AllowGroups, restarted SSH and attempted a log in by the local user and that did not work.  I then created a local user group and added the local user to it.  Then restarted SSH, and attempted to login and finally was met with success.  That seems to have taken care of my issue at this time.  Thanks for the suggestion.

---

### Post by &amp;KyT$0P# on 2016-07-06
You're welcome! :KS

---

