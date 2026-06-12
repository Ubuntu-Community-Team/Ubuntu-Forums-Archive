---
title: "svn + ldap + manage repos"
date: 2007-05-31
forum: Server Platforms
---

### Post by mwerlberger on 2007-05-31
Hi!

I'm already running an Ubuntu server and I'm almost happy. One big Problem I have is running the thing without LDAP. So I want to switch to LDAP and change all the user-auth and stuff in that way. Ok many literature can be found on these topics. But now to my problem: I also have running many svn repos on the machine from several users. Every user has its own repo within the home direcotry connecting with ssh+svn or https to it. I'm absolutely not satisfied with it because all the time a users needs another shared svn i have to change all the apache stuff to give https access to the single repo.

Is there a proper way to work out a strategy for one SVN repo for all users where everybody has an own project or sub-repo or what else... Make the repo https accessable and every user can manage user files to give access to their project partners. A Web-Interface for managing repos and user-accounts for SVN would be perfect of course...

Example scenario:
User XYZ creates a new repo for project MakeThingsEasier. There are working 5 people with him so he adds a user-config file for authenticating those 5 peoples and not annoying the sysadmin (me) to create a repo and all config for the user accounts for https access.

Hope somebody had to deal with this and can give me some hints/links/ideas.....

Kind regards,
 Manuel

---

### Post by craigp84 on 2007-05-31
Hi Manuel,

There's nothing pre-baked for this i don't think.

Rolling your own's easy anyway. Just make a quick shell script.

It might be easier to group the repo's under a shared area and define SVNParentPath in apache rather than SVNPAth.

Alternatively, it's trivial to have your "create_svn_repo.sh" script add repo's to /etc/apache2/conf.d directory then force a reload of apache.

Just an example, you fill in the blanks:

```

#!/bin/sh

if [ x = x$1 ]; then
  echo "Error: Please supply a repository name as a parameter to this script"
  echo "Usage: $0 <repo-name>"
  exit 1
fi

repo_name="/path/to/shared/$1"

if [ -e $repo_name ]; then
  echo "Error: A repo named $1 already exists."
  exit 1
fi

svnadmin create $repo_name

# Set any permissions, group ownerships etc here
# chgrp <blaa> 

cat - > /etc/apache2/conf.d/svn-$1.repo <<APACHE
<Location /svn/$1>
DAV svn
SVNPath $repo_name
</Location>
APACHE

cat - > $repo_name/.htpasswd <<HTPASSWD
AuthName "$1 SVN Repo"
AuthType Basic
LDAP_Server localhost
LDAP_Port 389
Base_DN "dc=example,dc=com"
UID_Attr UserID
require valid-user
# Comment out the above, uncomment the below to restrict to specific users
#require user craig manuel
HTPASSWD

# Reload apache, no interruption to clients
/etc/init.d/apache2 force-reload


```

I've just typed that into this web form so there's possibly some typos but you should get the idea from it.

Running it would be "create_repo.sh craig" which would go create a repo called craig and give any authenticated users access. It would also provide a template .htpasswd to be cusomised to restrict access to specific users.

Hope this helps,

-c

---

### Post by mwerlberger on 2007-05-31
That sounds very nice indeed. SVNParentPath is the thing i watched out and apperntly always read over it...

Thx for the shell script. I will give that a try when i did the LDAP thing...

Regards,
 Manuel

---

