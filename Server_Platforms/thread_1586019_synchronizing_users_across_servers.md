---
title: "synchronizing users across servers?"
date: 2010-10-01
forum: Server Platforms
---

### Post by Pitt Stains on 2010-10-01
Hello,

I wonder if other people have this problem... sometimes I need to duplicate most or all of a server from one machine to another.  The part where I most tend to have issues is with recreating the users.  Sometimes the UIDs don't match up because of differences between the two systems, which gives funky results, like files owned by the wrong user.

Or, sometimes, I just need to create the same 10 users on x number of machines, and it's tedious to do this 10x times.  Plus, then, if you need to change a password or delete a user, you have to do it x times.

Any recommendations on how to centralize users/auth?

Thanks!
-Pitt

---

### Post by the_original_billq on 2010-10-01
You can use a naming service like NIS or LDAP.
You can also use NFS/autofs to share your user home directories so they don't have to be duplicated and synced.

If your setup is small, you can use your best machine as your NIS & NFS server.  Setup your other machines as workstations to authenticate and mount home directories from your server.

You can also use Samba and LDAP for user authentication, which is very handy if you also want to share space with Windows-based PC's.

The Ubuntu server guide goes through the LDAP and Samba setup, and finding how-to's on NIS/NFS is also pretty easy via google.

HTH,

Bill

---

### Post by koenn on 2010-10-01
the "adduser' command has an option that lets you set a UID, you can use that to keep UID's consistent across machines.

you might want to wrap a script around it if you have to create a lot of accounts on a lot of machines, or the re-create a given setup

this will only work well for the initial creation of accounts, not for later changes in passwords and such


alternatively, or in combination with the above,  copying (scp, rsync, ..)  password and shadow files across all machines might also work, but you should test that first, and pay attention to your service/system accounts


Like Bill said, LDAP or NIS are made for this kind of thing, so they're worth a look, but may be just too complex for a small environment

---

### Post by SeijiSensei on 2010-10-01
[http://ubuntuforums.org/showpost.php?p=9893886&postcount=9](http://ubuntuforums.org/showpost.php?p=9893886&postcount=9)

---

