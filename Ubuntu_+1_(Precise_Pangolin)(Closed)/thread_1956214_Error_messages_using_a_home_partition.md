---
title: "Error messages using a home partition"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by JHCKX on 2012-04-10
I've got Ubuntu 10.04 on one partition, 12.04 on a "test" partition, and both systems share a home partition. No problems on 12.04 but when I boot into 10.04, I get error messages, that not all language components have been installed, app armour needs an update, and nautilus needs to be restarted for dropbox. I click the appropriate button but I get the same messages the next time and they seem pretty bogus anyway. 

Has anyone else had similar experiences or do you know a way to get rid of these messages?

---

### Post by oldfred on 2012-04-10
Generally best not to share a /home. Systems are designed to be updated so using an older /home in a new install is ok, but going back can lead to problems.

I found that /home user settings are tiny. I have all data in separate data partitions, moved some hidden data folders like Firefox & Thunderbird profiles to a shared partition and found only about 256K was left. I do have .wine with is over 1GB now still in /home.

So you can easily copy the old settings to your new install & they will get updated without changing your old settings if you just keep /home separate. Then shared data where in most cases it does not matter.

---

### Post by dcstar on 2012-04-12
> **oldfred said:**
> Generally best not to share a /home. Systems are designed to be updated so using an older /home in a new install is ok, but going back can lead to problems.
........

You can use shared /home if you **only** use the same version of things like Gnome in the different systems you boot.

10.04 and 12.04 use radically different versions of Gnome and are not backwards compatible once the initial conversion from old to new is done.

---

### Post by JHCKX on 2012-04-12
> **dcstar said:**
> 
10.04 and 12.04 use radically different versions of Gnome and are not backwards compatible once the initial conversion from old to new is done.

I know that gedit has its configuration files at a different location for gnome2 and gnome3, clearly other settings do this as well (but not all perhaps). OTOH, most things work fine in both versions, it's just the bogus startup messages

---

