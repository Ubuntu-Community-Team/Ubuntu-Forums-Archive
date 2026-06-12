---
title: "Starting directory for vsftpd"
date: 2007-11-01
forum: Server Platforms
---

### Post by elamericano on 2007-11-01
I don't mean the root directory. As I understand it, the ftp root directory has to be read-only for security purposes. In any case, the daemon won't start if I make it writable. Fine, but then I don't want my anonymous users to start there. They may just logoff if it gives an error when they try to upload. I want to create a subfolder and have them start there.

I don't see a way to start in a different folder than root in vsftpd.conf, but can I run a cd command when users logon?

---

### Post by HermanAB on 2007-11-01
It is described nicely in the vsftpd.conf man page.

---

### Post by elamericano on 2007-11-01
I'm a traditionalist. You should say RTFM if that's what you mean. FYI, I read that page completely right before posting.

Is it anon_root which is supposed to work - remember, I don't want to change the root or it will just force me to make the new directory read-only. I'm trying to start one directory lower than the root.

If you want to be less cryptic, Herman, you're welcome to try again.

---

### Post by elamericano on 2007-11-01
Forgot to mention, I experimented with anon_root, and I couldn't set it to anything without causing "500 OOPS: cannot change directory" on login. I've given the proper group permissions already. I even su'ed to the ftp user and cd'ed to my folders locally without any problem. All this before posting the first time, OK?

---

### Post by elamericano on 2007-11-02
Aww jeez, thanks a lot Herman, you killed my thread.

---

### Post by ruibernardo on 2007-11-03
> **elamericano said:**
> Forgot to mention, I experimented with anon_root, and I couldn't set it to anything without causing "500 OOPS: cannot change directory" on login. I've given the proper group permissions already. I even su'ed to the ftp user and cd'ed to my folders locally without any problem. All this before posting the first time, OK?

I'm not sure, but I think that vsftpd don't allow you to set the starting directory in a directory that is writeable by the user. You can have a sub-directory for uploads, but this one can't be the starting point for the chroot - security reasons.

EDIT: at least for the anonymous user.

---

### Post by elamericano on 2007-11-04
Thanks, I didn't consider that as a possible reason for that error message, since it emphatically refused to start the server at all when the default root was writable.

I tried your idea and made everything non-writable, but it didn't matter. It's like anon_root doesn't work at all. Maybe it can only be used in confunction with some other parameter, although I didn't see that in the [inadequate] documentation.

Is anyone using anon_root successfully with the latest vsftp?

Maybe it can't be done with vsftp. I didn't think it was asking too much to start my users in a writable directory. They will be primarily uploading, after all.

Hmmm, Proftp actually has a user guide... that may be the answer. I don't actually need a lot of features. I'd mostly like something that's easy to administer.Other suggestions are welcome.

---

### Post by elamericano on 2007-11-04
> anon_root
    This option represents a directory which vsftpd will try to change into after an anonymous login. Failure is silently ignored.

Untrue. Failure actually causes login rejection. Nice man page=user guide approach :roll:

---

### Post by elamericano on 2007-11-04
Proftpd has the DefaultChdir option to accomplish this.

---

