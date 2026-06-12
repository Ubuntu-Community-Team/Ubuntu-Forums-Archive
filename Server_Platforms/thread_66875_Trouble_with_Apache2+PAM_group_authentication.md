---
title: "Trouble with Apache2+PAM group authentication"
date: 2005-09-18
forum: Server Platforms
---

### Post by Molerat on 2005-09-18
I'd like to use Linux users and groups for all my authentication needs.  What I am trying to do right now is get Apache2 + PAM + SVN set up.  Things work fine for **user** authentication, but fail when I try to switch to **group** authentication.

Now for some caveats:  I think I have read all the relevant portions of the SVN, Apache2, and PAM documentation.  I've searched Google, but have run into a lot of deadends.  I didn't see anything here so I thought I would see if I anyone could help.

First, I am running the Preview Release of Breezy.

Here are the modules I have in /etc/apache2/mods-enabled:

```

auth_pam.load
dav.load
dav_fs.load
dav_svn.load
cgi.load
dav_fs.conf
dav_svn.conf

```

Here is the relevant portion of my /etc/apache2/sites-enabled/default:

```


     <Location /svn>
                DAV svn
                SVNParentPath MYPATH

                AuthPAM_Enabled on
                AllowOverride AuthConfig
                AuthGroupFile /etc/group

                AuthName "Secure SVN"
                AuthType Basic

#               This works fine:
#               Require user MYUSERNAME

#             This is what I want but it breaks:
                Require group "svn"
        </Location>

```

This all works fine for regular user authentication.  But I don't want to have to edit my Apache configuration everytime I want to add users to svn.  Instead I want to add users to the group file.  Hence I want to Apache to check by group.  Unfortunately, when I try that, I get:

```

[date] [error] [client 192.168.23.221] access to /svn/ failed, reason: user USERNAME not allowed access

```

Now what I take from this is that my username and password is successfully checked, but the group check is failing.  I've tried changing the group to about everything I can think of, just to get *something* working.

I cannot figure out what might be wrong.  The only thing that I can think of is that id does not list all the groups that I am a member of.  I'm using the User & Groups manager in System > Adminsitration to add users to the svn group, and the changes show up in /etc/group; however, id does not list the group.  I don't know if this is relevant or not.

So, does anyone have any ideas?  Is there more information I can provide?  I really don't have any other ideas right now.

---

### Post by LordHunter317 on 2005-09-18
FWIW, I couldn't ever get it working either, I think it's a bug in mod_auth_pam.

Using mod_auth_pam against system accounts is a huge security risk anyway and is probably simply best not done.

---

### Post by Molerat on 2005-09-18
[QUOTE=LordHunter317]FWIW, I couldn't ever get it working either, I think it's a bug in mod_auth_pam.

Using mod_auth_pam against system accounts is a huge security risk anyway and is probably simply best not done.[/QUOTE]

This seems to be the case.

I guess I could see how this can be a security issue.  Ugh.  Is there any centrally manage users and groups that doesn't require a Ph. D. in computer science and mathematics?

I really don't want to maintain 12 different userlists...

---

### Post by LordHunter317 on 2005-09-19
If only Apache needs to see the accounts, a MySQL or PostgreSQL user db isn't impossible to setup.

If everythign does, LDAP is your only modern recourse.  Which isn't bad if you don't bother with openldap.

---

