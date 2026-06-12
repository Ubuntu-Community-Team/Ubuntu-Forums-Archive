---
title: "ACL broken in Trusty ubuntu?"
date: 2014-09-19
forum: Security
---

### Post by Byb on 2014-09-19
Hi all
I'm digging around for weeks.
Coming from Windows, I still feel a newb in Linux although five years  are since I first looked Linux in the eyes, removing Xandros from my  eeepc for eeebuntu.
Ok, enough for oldies.
Since weeks I try to move my video/music/photo files from my old Windows  to a fresh Trusty in a fresh pc, but no way I can gain the same ease of  use in files management:
What I want: **me** and **she** have full control over the existing+new folders/files (let's call that a living **tree**, which means growing), and **minidlna** has the minimum necessary, say rx on the tree branches (old+new folders) and read regular leaves (old+new files). **Others** need no access. No matter the plane and where the folders/files come from: the only thing important is where they land.
In the walk and searches, I learned changing umask is highly  discouraged, and that I'd instead use chmod g+s and acl, as advised even  in official ubuntu doc. And I said yesss, that is :razz:.
So I fertilized the ext4 ground with acl in fstab, although not necessary, installed acl
```
sudo su
addgroup readymediagroup --gid 29999 (to keep further users/groups ids numbers synch'ed)
adduser me readymediagroup
adduser she readymediagroup

```
 and rebooted.
:confused:  Alas! I can't get this sexy friendly *setfacl* syntax to work, so I wrote a  little script to help understanding, and then tried many syntax  variations for the setfacl command, but I never can get it to work.
```
#!/bin/bash
mkdir -pv /srv/test
echo $? 1
rm -rf /srv/test/200402
echo $? 2
chown -Rv me:readymediagroup /srv/test
echo $? 3
chmod -Rv a-srwx /srv/test
echo $? 4
chmod -Rv ug-x /srv/test
echo $? 5
chmod -Rv u+rwX /srv/test
echo $? 6
chmod -Rv g+rwXs /srv/test
echo $? 7
setfacl -Rm  d:u::rwx,d:g::rwx,d:o:-,d:g:readymediagroup:rwx,d:u:she:rwx,d:u:me:rwx,d:g:me:rwx,d:g:she:rwx,d:u:minidlna:rx,d:m::rwx,d:m:rwx,u:me:rwx,u:she:rwx,g:me:rwx,g:she:rwx,g:readymediagroup:rwx,u:minidlna:rx,o:-,m::rwx,m:rwx  /srv/test
echo $? 8
getfacl -t /srv/test
echo $? 9
```
then I run
```
me@srv$ sudo rm -r test/
[sudo] password for me: 
me@nux:/srv$ sudo ~/acl.sh 
mkdir: create folder «/srv/test»
0 1
[rm -rf /srv/test/200402 return code below]
0 2
«/srv/test» ownership changed from root:root to me:readymediagroup
0 3
«/srv/test» mode changed from 0755 (rwxr-xr-x) to 0000 (---------)
0 4
«/srv/test» kept at 0000 (---------).
0 5
«/srv/test» mode changed from 0000 (---------) to 0700 (rwx------)
0 6
«/srv/test» mode changed from 0700 (rwx------) to 2770 (rwxrws---)
0 7
[setfacl return code below]
0 8
getfacl : removing first « / » from absolute path names
# file: srv/test
USER   me              rwx  rwx
user   minidlna         r-x  r-x
user   me              rwx  rwx
user   she            rwx  rwx
GROUP  readymediagroup  rwx  rwx
group  me              rwx  rwx
group  she            rwx  rwx
group  readymediagroup  rwx  rwx
mask                    rwx  rwx
other                   ---  ---

0 9
```
At this time everything is ok.
then the **non default** effective entries permissions are denied(=capitalized) for everybody but USER (maybe because nonDefault mask is lost?).
```
me@nux:/srv$ cp -rv /media/me/USPEED/200402/ /srv/test/
«/media/me/USPEED/200402/» -> «/srv/test/200402»
«/media/me/USPEED/200402/P2220368.JPG» -> «/srv/test/200402/P2220368.JPG»
me@nux:/srv$ getfacl -t test/200402/
# file: test/200402/
USER   me              rwx  rwx
user   minidlna         R-X  r-x
user   me              RWX  rwx
user   she            RWX  rwx
GROUP  readymediagroup  RWX  rwx
group  me              RWX  rwx
group  she            RWX  rwx
group  readymediagroup  RWX  rwx
mask                    ---  rwx
other                   ---  ---

```
As a result files inside loose their wx access
```

me@nux:/srv$ getfacl -t test/200402/P2220368.JPG 
# file: test/200402/P2220368.JPG
USER   me              rw-     
user   minidlna         r-X     
user   me              rWX     
user   she            rWX     
GROUP  readymediagroup  rWX     
group  me              rWX     
group  she            rWX     
group  readymediagroup  rWX     
mask                    r--     
other                   ---     
me@nux:/srv$ su she
Password : 
she@nux:/srv$ cd test/200402/
bash: cd: test/200402/: Permission denied

```
:sad:
And/but the strange, although, but this is coherent with parent ACL Default entries:
```

me@nux:/srv$ mkdir test/200402/toto
me@nux:/srv$ getfacl -t test/200402/toto/
# file: test/200402/toto/
USER   me              rwx  rwx
user   minidlna         r-x  r-x
user   me              rwx  rwx
user   she            rwx  rwx
GROUP  readymediagroup  rwx  rwx
group  me              rwx  rwx
group  she            rwx  rwx
group  readymediagroup  rwx  rwx
mask                    rwx  rwx
other                   ---  ---

```
Puzzled.
Please help

---

### Post by thnewguy on 2014-09-19
It seems to me the main issue here is what you are doing does not require ACL. With just a couple of users on the system who will share rights over a tree of directories you just need to have a common group. You appear to have created this group early on, so you're all set. Just make sure that new directories you create in the shared location have the proper group and you can set the directories to have the proper permissions.

Coming from Windows it probably feels like you need ACL since that is the closest thing Linux has to the fine-grained permissions Windows uses. However, Linu has a much simplier user/group set of permissions that do not require ACL.

---

### Post by Byb on 2014-09-19
Hi thnewguy
The need of acl is because 
1: setguid only triggers ownership inheritance, not permissions inheritance.
2: and I need a group of full power humans and a limited privileges user (minidlna who is the id running the program).
so I do not have to manually set permissions on every new subtree creation.

Windows allowed this in the times of NT4/2k[3]/xp: propagation

I wander how small companies/associations with no tech inside deal with this difficulty when it comes to be 2 or more teams. Maybe a coder wrote them a daemon that monitors new files/folders (like minidlna uses inotify) and applies a preset of permissions on each unmatch?

But maybe I'm fully blind so that I can't see the huge easy way. Feel free to enlight me.

Bye bye

---

### Post by Byb on 2014-10-03
Yes, they are broken : [http://debbugs.gnu.org/cgi/bugreport.cgi?bug=8527]("http://debbugs.gnu.org/db/85/8527.html")

---

### Post by thnewguy on 2014-10-03
For maintaining a set of permissions on files that will be created in a directory you can use umask. Setting the user's umask permissions will ensure that everyone in the proper group will be able to access the files.

In short: use setguid to make sure newly created files/folders have the proper ownership. Use umask to make sure newly created files/folders have the proper permissions set on them.

This sort of problem does not require scripts or monitoring directories. It just requires folders and users are set up with the proper permissions.

---

### Post by Byb on 2014-10-03
Changing umask is disrecommanded everywhere about ubuntu/debian

---

