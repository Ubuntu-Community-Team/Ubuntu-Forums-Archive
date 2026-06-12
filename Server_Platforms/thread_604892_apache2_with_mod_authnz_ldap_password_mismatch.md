---
title: "apache2 with mod_authnz_ldap: password mismatch"
date: 2007-11-06
forum: Server Platforms
---

### Post by gehirnmann on 2007-11-06
I have Apache 2, with mod_authnz_ldap on ubuntu.
I try to connect to an Active Directory, where I have a group "Users" which acutally consists of "SBSUsers" where all users are in. This is the default config for a Small Business Server from MS$.

the config seems ok, as what I can see:


[PHP]<IFModule mod_dav_svn.c>
 <Location /svn>
    DAV svn
    SVNParentPath /some/path/to/svn
    SVNPathAuthz off

    AuthBasicProvider ldap
    AuthBasicAuthoritative On

    AuthzLDAPAuthoritative off

    AuthType Basic

    AuthName "SVN Repositories"

    AuthLDAPBindDN "CN=UserName,CN=SBSUsers,DC=DOMAIN,DC=DE"

    AuthLDAPBindPassword passwd
    AuthLDAPURL "ldap://SERVER.DOMAIN.DE:389/CN=SBSUsers,DC=DOMAIN,DC=DE?sAMAccountName?sub?(objectClass=*)"
        
    Require valid-user

    </Location>
</IFModule>[/PHP]


the error message is always the same for "ldap_simple_bind_s()": "password mismatch", even invalid usernames or "CN=" flags do not change this. :confused:
I also tried changing the "AuthzLDAPAuthoritative off/on".. no change!
From my understanding of the error messag, it seems as if the binding to the ldap succeeds, but the actual authentication is wrong. is that correct?

any ideas?
thanx.

---

### Post by csylvia on 2008-05-09
I am having the exact same issue.  Did you find a resolution?

---

