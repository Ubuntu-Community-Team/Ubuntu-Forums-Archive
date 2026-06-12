---
title: "Group and user permissions on mediawiki"
date: 2013-01-07
forum: Server Platforms
---

### Post by sunnysthakur on 2013-01-07
I am working on setup a wiki which should have users and group having read or write permission.
Before that we were using simple write to all methodology.

Now the challenge is this that i have created a 3 users and all of the 3 are able to write to wiki and update the page. Now what i what to do is that 2 users can write and one is able to view only.

I did a little bit R 'n' D but didn't success. Below were the things i did but didn't succeed.

By adding the below code in Localsettings.php 2 user can read [they are not able to edit] but one can write.

$wgGroupPermissions['Trusted'] = $wgGroupPermissions['user'];
$wgGroupPermissions['user'   ]['edit']          = false;
$wgGroupPermissions['Trusted']['edit']          = true;
$wgGroupPermissions['sysop'  ]['edit']          = true;

Another thing i did.

INSERT INTO user_groups (ug_user, ug_group) VALUES ('3', 'bureaucrat'); 
INSERT INTO user_groups (ug_user, ug_group) VALUES ('3', 'sysop');

Assign bureaucrat and sysop rights to user whose id is 3 but nothing happen.
Again userid 1 is able to edit but users having userid 3 again not able to edit, however both have same groups permissions now.

Please help me to resolve this issue.

Note :- I am using mediawiki 1.9.2

---

