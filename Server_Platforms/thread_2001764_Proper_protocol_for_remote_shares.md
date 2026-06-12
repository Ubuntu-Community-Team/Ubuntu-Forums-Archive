---
title: "Proper protocol for remote shares"
date: 2012-06-11
forum: Server Platforms
---

### Post by natomb on 2012-06-11
Hello together,


I would like to get your opinion on the following situation.

I have a server "s1" with a large disk array. s1 runs samba and could also run nfs.
I have a second server "s2" which should be the mail server. The mail of the users shall be kept on s1 in a dedicated and shared /mail directory.
Users are managed in an LDAP directory.

For the mail agents I plan to use dovecot, postfix and fetchmail and maildir as the mailbox format.

My question to you is:
Would you mount a samba share on s2 or would you use nfs? The samba mount would be realized as described here: [http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/). The nfs mount would be realized as described in the ubuntu howtos (e.g. [http://wiki.ubuntuusers.de/NFS](http://wiki.ubuntuusers.de/NFS))

If you prefer to use samba (option 1), then how would you instruct the mail agents to use the one particular user used to mount the samba share, e.g. docsadm as in the tutorial?

Option 2 is not my preferred option because I will have alien notebooks in the network and do not want to setup kerberos due to also a high change frequency of friendly computers, i.e. alien as well as own computers come and go into the network on a merely hourly basis.


Thank you very much in advance
  Bjoern

---

### Post by SeijiSensei on 2012-06-11
For *nix-to-*nix file sharing I'd always pick NFS over Samba.  Since you're using maildir, the locking issues that affect NFS+mbox aren't going to be a problem.  Why complicate matters with a file-sharing solution that requires rewriting ownerships and permissions into the SMB format on one end and rewriting them back again on the other?

You don't need Kerberos to do any of this.  Besides the users aren't going to be connecting directly to the shared directories anyway.  Their usage will be handled by dovecot.  In fact, your best bet in such a fluid situation as the one you describe might be to set up Squirrelmail and have most of your users read their mail via a web browser.  For the people who really need a standalone client like Thunderbird, just set them up to use IMAP.

---

### Post by natomb on 2012-06-12
SeijiSensei, thank you for your reply.


I see I must be more specific on the scenario.

Mail is not the only service offered in the network but also iSCSI, MySQL, www, samba, ldap, rtsp, ... . VLAN also could not be setup and currently there are no measures against IP and MAC spoofing. Thus, an "evil" user could fake the IP / MAC address of the mail server and then connect to the NFS share.

Unfortunately budget restrictions do not permit adequate infrastructure to make the network more secure. Thus, I am limited to service configuration.

I also do not want to "rewrite" user permissions on the maildirs of the users. It is totally fine if all maildirs are owned by one (administrative) user, while dovecot handles the user authentication and proper retrieval of the user's mailbox. I think the latter dovecot can do. But I am not sure if it is possible to spool mail into different user's maildir with the same UID. This seems to be the problem, I think.

Does anyone has experience with instructing Postfix / Dovecot to access (and write) all maildirs of all users using just one particular UID?


Thank you again
  Bjoern

---

