---
title: "I started gettingsome new Dovecot log entries.  They look kinda scary.  Can you check"
date: 2017-07-18
forum: Security
---

### Post by MechaMechanism on 2017-07-18
SOLVED.  Research on the net says this is normal.  Nothing got through.

Ubuntu 17.04.  Desktop
Static IP
Only use Postfix occasionally to send automated emails
Only one user on desktop, me
Followed the howto here; [https://help.ubuntu.com/lts/serverguide/postfix.html](https://help.ubuntu.com/lts/serverguide/postfix.html)
Don't need multiple users.
Only use this desktop to send machine generated automatic emails about twice a day.

I'm pretty sure I'm not cracked yet.  I only use dovecot for email authentication.  If I could run Postfix on it's own I would.
I think apparmor is doing it's job.

Can anybody tell me how to get Postfix to do TLS without Dovecot.  Postfix on it's own would be great.

Here are the logs;
>   dovecot: auth: Error: anvil-auth-penalty: Anvil queries timed out after 5 secs - aborting queries: 1403 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for beatrice: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for gus: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for hope: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for jean: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for jefferson: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for jennie: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for jennifer: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for joanne: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for lars: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for lee: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for lexus: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for maggie: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for magic: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for mailscanner: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for moses: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for natalia: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for ralph: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for romeo: Shutting down: 2 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for ronaldo: Shutting down: 2 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for ronnie: Shutting down: 3 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for roob: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for root2: Shutting down: 4 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for rosa: Shutting down: 2 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for rosalie: Shutting down: 2 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for rose: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for seller: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for trunk: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for turbo: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for tyson: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for universal: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for unsubscribe: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for username: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for vanessa: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for verify: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for veronica: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for video: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for vincent: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for violeta: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for virgil: Shutting down: 1 Time(s)
  dovecot: auth: Error: auth worker: Aborted PASSV request for whitney: Shutting down: 1 Time(s)
  dovecot: auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied: 4091 Time(s)
  dovecot: auth: Error: read(anvil-auth-penalty) failed: read(size=1024) failed: Connection reset by peer: 395 Time(s)
  dovecot: message repeated 10 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 137 Time(s)
  dovecot: message repeated 2 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 257 Time(s)
  dovecot: message repeated 3 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 180 Time(s)
  dovecot: message repeated 4 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 201 Time(s)
  dovecot: message repeated 5 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 152 Time(s)
  dovecot: message repeated 6 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 89 Time(s)
  dovecot: message repeated 7 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 88 Time(s)
  dovecot: message repeated 8 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 100 Time(s)
  dovecot: message repeated 9 times: [ auth: Error: net_connect_unix(anvil-auth-penalty) failed: Permission denied]: 107 Time(s) 
Here's Postfix log too;

Postfix
  10247   SASL authentication failed                  10,247
    778   Miscellaneous warnings                         778
212.689K  Bytes accepted                             217,794
  1.771K  Bytes sent via SMTP                          1,814
========   ==================================================
      5   Accepted                                   100.00%
--------   --------------------------------------------------
      5   Total                                      100.00%
========   ==================================================
   1303   Connections                                  1,303
    605   Connections lost (inbound)                     605
   1303   Disconnections                               1,303
      6   Removed from queue                               6
      4   Sent via SMTP                                    4
      2   Bounced (remote)                                 2
      1   Notifications sent                               1
      3   Connection failures (outbound)                   3
      2   Timeouts (inbound)                               2
     21   Hostname verification errors (FCRDNS)           21
    299   SMTP protocol violations                       299

---

