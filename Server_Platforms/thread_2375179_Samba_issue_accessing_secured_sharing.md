---
title: "Samba issue accessing secured sharing"
date: 2017-10-22
forum: Server Platforms
---

### Post by gain74 on 2017-10-22
Hello,

I have an issue in Ubuntu 16.04.3.

I need to secure access to a shared folder from Windows 10.

I have two Ubuntu users "user01" and "user02". I converted users into Samba users.

I created a shared folder named "test" (owner is "user01").

In this scenario, I need user01 and user02 to have full access to share and any other users not to be able to have access to it.

Following is the section for this share:

[test]
    valid users = user02
    path = /media/data/test
    read only = no
    browseable = yes
    create mask = 0640
    directory mask = 0750
    writeable = yes

From Windows, if I try to access to the share as user01, I have full access to create/read/write/delete files/folders. If I try to access share as user02, I get authorization error (user does not have access to the share) and it does not let me access content.

I tried following multiple suggestions I found similar to my scenario but none of them worked.

This is the easiest scenario I have (and it is causing a lot of pain)... I am worried that when I have to setup more complex scenarios (granting read only to specific users/groups, read/write to different users/groups, and no access to others), it will be a nightmare. I have to setup over 50 shares, each with their own rules.

Any help is really appreciated.

Thanks.

---

### Post by darkod on 2017-10-23
How about filesystem permissions of the test folder? When sharing through samba you have to take into account both:
1. Linux filesystem permissions
2. Samba user access

You will need to create one group, lets say group01 and add user01 and user02. Then on the test folder give rwx to group01. Check if that helps you out.

If user02 has no permissions on the test folder, it will not be allowed access regardless that the samba share definition says it is a valid user for the share.

---

### Post by Morbius1 on 2017-10-23
I do not understand your post.
> 
[test]
    valid users = user02
    path = /media/data/test
    read only = no
    browseable = yes
    create mask = 0640
    directory mask = 0750
    writeable = yes
> I need user01 and user02 to have full access to share and any other users not to be able to have access to it.
The only user that will gain access to that share is user02 because that is the only one specified by the [COLOR=#0000cd]**valid users**[/COLOR] line.
> From Windows, if I try to access to the share as user01, I have full access to create/read/write/delete files/folders.
I don't see how that is possible because of the same [COLOR=#0000cd]**valid users = user02**[/COLOR] issue. You may have another share to /media/data perhaps that user01 has access to and from there he can access the /media/data/test folder but he can't access it from the [test] share.
> If I try to access share as user02, I get authorization error (user does  not have access to the share) and it does not let me access content.

That's the part that darkod is talking about. Linux permissions and samba permissions have to be in sync.

---

### Post by gain74 on 2017-11-06
Hi,

Thanks darkod and Morbius1.

Sorry for my late reply. I had to work on a different issue. I will try to check Linux permissions in the next couple of days.

Thank you again for your help.

---

