---
title: "Courier-imap not working after upgrade to 8.04"
date: 2008-05-26
forum: Server Platforms
---

### Post by penguintutor on 2008-05-26
I have upgraded my server to Ubuntu 8.04. I have a couple of little things that I've already fixed, but the one that has got me is courier-imap authentication problems. 

I had installed courier-imap using mostly default configuration on 7.10. I used standard authentication against system users (ie. username stewart - maildir in /home/stewart/Maildir ) using the shadow username & password.

Since the upgrade authentication does not work. I just get unable to login from the clients. Network connectivity is working, it's just authentication that's broken.

Can anyone point me in the right direction for how to configure the authentication? Googling gives me results on using mysql, but I just want basic text based authentication at the moment, which I believe should just work. 

authdaemonrc has - 

authmodulelist="authpam"

and pam.d/imap has:

@include common-auth
@include common-account
@include common-password
@include common-session


Please let me know where I should be looking.

Thanks

---

### Post by penguintutor on 2008-05-28
Well I haven't quite fixed the original problem, but I have found a workaround.

I turned full debugging on for courier-imap and it seamed to be authenticating OK at the server, but still not allowing connections

```
May 27 23:10:24 linuxserver1 imapd: Connection, ip=[::ffff:192.168.1.201]
May 27 23:10:28 linuxserver1 authdaemond: received auth request, service=imap, authtype=login
May 27 23:10:28 linuxserver1 authdaemond: pam_service=imap, pam_username=penguin
May 27 23:10:30 linuxserver1 imapd: Connection, ip=[::ffff:192.168.1.201]
May 27 23:10:30 linuxserver1 authdaemond: received auth request, service=imap, authtype=login
May 27 23:10:30 linuxserver1 authdaemond: pam_service=imap, pam_username=penguin
May 27 23:10:33 linuxserver1 imapd: Connection, ip=[::ffff:192.168.1.201]
May 27 23:10:33 linuxserver1 authdaemond: received auth request, service=imap, authtype=login
```

I could not see any reason for it failing at all.

I tried uninstalling and reinstalling courier-imap and courier-auth, which made no difference.

So I sort of accepted defeat and replaced courier-imap with dovecot. A few small configuration changes later (set to Maildir rather than mbox) and I am up and running again. 

Only problem now is the 3500 spam emails that I've received in the last few days :-( SPAM Assassin and the Thunderbird spam filter have between them get those down to about 100 or so.

---

