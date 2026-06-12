---
title: "ntfs-3g Testing user permissions"
date: 2017-11-07
forum: Ubuntu, Linux and OS Chat
---

### Post by jeff.sadowski on 2017-11-07
I created a couple of maybe useful scripts and have been trying out
user mapping.

It seems a bit off and I would like to know more about ACL support.

create_mapping.sh is a script I use to create the mapping file from my
active directory I created a DOMAIN_ADMIN_PASSWD.sh
with content similar to to use create_mapping.sh

DOMAIN=<myADdomain>
ADMIN=<userOnAD>
PASSWORD=<userpassword>

I used ldapsearch and wbinfo to generate a user mapping file ~/ntfs-3g.usermap

ntfs-3g.usermap.bat is a batch file that created the user mapping file
documented in the man page using wmic



For my first test I created an ntfs partition on a windows 7 machine
connected to my domain.
I used my ntfs-3g.usermap.bat file that I copied to my drive.

Then I created a few test directories and checked the permissions.
I found it interesting that windows by default created permissions for
the computer that inherited downward.
I removed those permissions and created some of my own.

I created a test partition and added a group "group1" that could read
and list directories.
I added all permissions for my user "user1".

I created a directory under it "test\test2" and added permissions for
another user "user2" with all permissions.
I then logged in as that other user "user2" and created a file in that
"test\test2\testing.txt"

I then cleanly unmounted it in windows and attached it to my linux
machine that uses winbind using rfc2307 for user mapping
I logged in with the "user1" user and plugged in the disk.

I saw that the user of "test" and the group of "test" where of my user
and my default group

When I looked at "test/test2" it was showing the owner of "user2"

It didn't seem to be acting quite right.

getfacl test
didn't show the other group I added.

I tried creating a file from "user1"
it created the file as root with no permissions for me to edit it.

I tried unmounting and mounting with option permissions

then again I created another file and it still created it with root

I'm using ubuntu-16.04
I'm not sure to find out what version of ntfs-3g I have

I found the acl option and mounted it with that.

It still shows the wrong owner for test/test2 however I now have
correct permissions as user1

I went back to my windows machine and created test\test2\testing2.txt
as "user1" then unmounted it and moved it to my linux machine and
mounted it with permissions,acl options ls -l test/test2 shows "user2"
as the owner for testing that isn't right.
getfacl test/test2/* shows that "user1" has rrx permissions on each
file but shows the owner as "user2". Odd behaviour.

---

