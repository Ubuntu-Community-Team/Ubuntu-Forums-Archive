---
title: "SSH error: “Corrupted MAC on input” or “Bad packet length”"
date: 2012-09-18
forum: Server Platforms
---

### Post by AncientPC on 2012-09-18
I have 3 boxes set up as shown:

[IMG]http://i.imgur.com/5Z6K1.png[/IMG]

The DFW box can communicate to the SFO / internet just fine, and I send files AUS -> DFW. However, every time I trying transferring DFW -> AUS it fails over SSH (ssh client, rsync, scp, sftp, etc) with the following error:

```
    Corrupted MAC on input.
    Disconnecting: Packet corrupt

```
Occasionally I'll get a different error:

```
    Bad packet length 2097180.
    Disconnecting: Packet corrupt

```
I've restarted the DFW box, as well as replaced the network cable. I'm not sure what else might be causing problems.

Right now to get files from DFW I have to use DFW -> SFO -> AUS which is not optimal.

---

### Post by SlugSlug on 2012-09-18
Last time I seen anything like this was on a Windows Network and was due to MTU settings (I think MTU on server1 was set higher than the switch was (or could handle?)  between Server1 & Server2)

---

### Post by AncientPC on 2012-09-18
> **SlugSlug said:**
> Last time I seen anything like this was on a Windows Network and was due to MTU settings (I think MTU on server1 was set higher than the switch was (or could handle?)  between Server1 & Server2)

That sounds like a likely source of the problem. Trying to login to the router remotely I get:

> An error occurred during a connection to dallas.server.net:8443.

SSL received a record with an incorrect Message Authentication Code.

(Error code: ssl_error_bad_mac_read)

I then proxy through the San Francisco box, at which point I can login to my router. However I checked the MTU and it's set to 1500 (the same as my local router).

---

### Post by markbl on 2012-09-19
I have seen ssh "bad packet length" errors when the ssh client is a very old version wrt to the ssh server.

---

### Post by stmiller on 2012-09-19
Can you temporarily increase log level on the ssh server:

/etc/ssh/sshd_config

LogLevel DEBUG3



Or try to connect with ssh user@host -vvv  ?

That may provide more information.

---

