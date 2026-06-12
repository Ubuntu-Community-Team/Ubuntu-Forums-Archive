---
title: "Migrating Samba from Debian Sid to Hardy 8.04 LTS"
date: 2008-04-30
forum: Server Platforms
---

### Post by Malbojia on 2008-04-30
Good Afternoon,

I have a old server under Debian 3.1 that runs samba. It recently ran out of room and figured it was time for a upgrade.

So i setup another box with 8.04 LTS server editions with samba as a service and bigger room with mdm under a RAID 5.

What I'm trying to do now is migrate the old samba over to the new one. From looking around google I had edited the group, gshadow, shadow and passwd to reflect the changes on the new machine. I copied over my smb.conf and made the changes. I copied over /var/lib/samba/* to the new server to make sure.

After that I did a rsync -avrzp -e ssh@oldbox:/home/* .
to transfer the files over retaining permissions

When i start up the service i can access shares located in /home/ with their respected usernames and passwords. It's users with no groups well their under 'users' that I cant access their assign folder located in smb.conf.

I'll get in windows "The group name can not be found". to "user does not exist.

I have my head against the well right now. I Also made sure all folders in /home had their corrects group allocations.

Thanks for the help.

---

