---
title: "SSH Setup Question (Require KeyAuth for Only Remote Connections)"
date: 2010-02-14
forum: Security
---

### Post by sablefoxx on 2010-02-14
I've setup ssh on my main home server which I use as a file server and to tunnel through while not at home.

Here's my question, is it possible to require key based auth from only remote connections but still allow local IPs (i.e. my local 192.168.1.0/24 network) to connect with only a password?

The theory being since it is much more difficult to break into a server requiring key based auth I'd only expose that to the Internet, while not having to create keys for all the machines on my LAN.

Or if not/too much work is the a better way to achieve the same level security?  I've tried Google/Search and haven't found much.  I should note I have ssh running on a non-default port, and have disabled root logins entirely.

Thx for the help :p

---

### Post by FuturePilot on 2010-02-14
> **sablefoxx said:**
> 
The theory being since it is much more difficult to break into a server requiring key based auth I'd only expose that to the Internet, while not having to create keys for all the machines on my LAN.


You don't have to make a different key for each client. 

I would recommend against using password auth at all. Keys are much more secure.

---

### Post by Satoru-san on 2010-02-14
> **FuturePilot said:**
> You don't have to make a different key for each client. 

I would recommend against using password auth at all. Keys are much more secure.
Yes. They are.

```
Feb 12 21:04:17 mushwars sshd[11660]: Invalid user staff from 61.19.73.45
Feb 12 21:04:21 mushwars sshd[11662]: Invalid user sales from 61.19.73.45
Feb 12 21:04:24 mushwars sshd[11664]: Invalid user recruit from 61.19.73.45
Feb 12 21:04:28 mushwars sshd[11666]: Invalid user alias from 61.19.73.45
Feb 12 21:04:31 mushwars sshd[11668]: Invalid user office from 61.19.73.45
Feb 12 21:04:35 mushwars sshd[11670]: Invalid user samba from 61.19.73.45
Feb 12 21:04:38 mushwars sshd[11672]: Invalid user tomcat from 61.19.73.45
Feb 12 21:04:42 mushwars sshd[11674]: Invalid user webadmin from 61.19.73.45
Feb 12 21:04:45 mushwars sshd[11676]: Invalid user spam from 61.19.73.45
Feb 12 21:04:49 mushwars sshd[11678]: Invalid user virus from 61.19.73.45
Feb 12 21:04:52 mushwars sshd[11680]: Invalid user cyrus from 61.19.73.45
Feb 12 21:04:56 mushwars sshd[11682]: Invalid user oracle from 61.19.73.45
Feb 12 21:05:00 mushwars sshd[11684]: Invalid user michael from 61.19.73.45
Feb 12 21:05:07 mushwars sshd[11692]: Invalid user test from 61.19.73.45
Feb 12 21:05:10 mushwars sshd[11694]: Invalid user webmaster from 61.19.73.45
Feb 12 21:05:18 mushwars sshd[11698]: Invalid user postfix from 61.19.73.45
Feb 12 21:05:21 mushwars sshd[11700]: Invalid user postgres from 61.19.73.45
Feb 12 21:05:24 mushwars sshd[11702]: Invalid user paul from 61.19.73.45
Feb 12 21:05:34 mushwars sshd[11706]: Invalid user guest from 61.19.73.45
Feb 12 21:05:38 mushwars sshd[11708]: Invalid user admin from 61.19.73.45
Feb 12 21:05:42 mushwars sshd[11710]: Invalid user linux from 61.19.73.45
Feb 12 21:05:45 mushwars sshd[11712]: Invalid user user from 61.19.73.45
Feb 12 21:05:48 mushwars sshd[11714]: Invalid user david from 61.19.73.45
Feb 12 21:05:56 mushwars sshd[11716]: Invalid user web from 61.19.73.45
Feb 12 21:06:03 mushwars sshd[11720]: Invalid user pgsql from 61.19.73.45
Feb 12 21:06:09 mushwars sshd[11724]: Invalid user info from 61.19.73.45
Feb 12 21:06:13 mushwars sshd[11726]: Invalid user tony from 61.19.73.45
Feb 12 21:06:16 mushwars sshd[11728]: Invalid user core from 61.19.73.45
Feb 12 21:06:20 mushwars sshd[11730]: Invalid user newsletter from 61.19.73.45
Feb 12 21:06:23 mushwars sshd[11732]: Invalid user named from 61.19.73.45
Feb 12 21:06:27 mushwars sshd[11734]: Invalid user visitor from 61.19.73.45
Feb 12 21:06:31 mushwars sshd[11736]: Invalid user ftpuser from 61.19.73.45
Feb 12 21:06:34 mushwars sshd[11738]: Invalid user username from 61.19.73.45
Feb 12 21:06:38 mushwars sshd[11740]: Invalid user administrator from 61.19.73.45
Feb 12 21:06:42 mushwars sshd[11742]: Invalid user library from 61.19.73.45
Feb 12 21:06:46 mushwars sshd[11744]: Invalid user test from 61.19.73.45
Feb 12 21:06:56 mushwars sshd[11750]: Invalid user admin from 61.19.73.45
Feb 12 21:07:00 mushwars sshd[11752]: Invalid user guest from 61.19.73.45
Feb 12 21:07:05 mushwars sshd[11754]: Invalid user master from 61.19.73.45
Feb 12 21:07:26 mushwars sshd[11766]: Invalid user admin from 61.19.73.45
Feb 12 21:07:30 mushwars sshd[11768]: Invalid user admin from 61.19.73.45
Feb 12 21:07:33 mushwars sshd[11770]: Invalid user admin from 61.19.73.45
Feb 12 21:07:36 mushwars sshd[11772]: Invalid user admin from 61.19.73.45
Feb 12 21:07:46 mushwars sshd[11778]: Invalid user test from 61.19.73.45
Feb 12 21:07:50 mushwars sshd[11780]: Invalid user test from 61.19.73.45
Feb 12 21:07:53 mushwars sshd[11782]: Invalid user webmaster from 61.19.73.45
Feb 12 21:07:59 mushwars sshd[11784]: Invalid user username from 61.19.73.45
Feb 12 21:08:03 mushwars sshd[11786]: Invalid user user from 61.19.73.45
Feb 12 21:08:10 mushwars sshd[11790]: Invalid user admin from 61.19.73.45
Feb 12 21:08:14 mushwars sshd[11792]: Invalid user test from 61.19.73.45
Feb 12 21:08:28 mushwars sshd[11800]: Invalid user danny from 61.19.73.45
Feb 12 21:08:31 mushwars sshd[11802]: Invalid user alex from 61.19.73.45
Feb 12 21:08:38 mushwars sshd[11806]: Invalid user mike from 61.19.73.45
Feb 12 21:08:42 mushwars sshd[11808]: Invalid user alan from 61.19.73.45
Feb 12 21:08:46 mushwars sshd[11810]: Invalid user data from 61.19.73.45
Feb 12 21:08:49 mushwars sshd[11812]: Invalid user www-data from 61.19.73.45
Feb 12 21:08:52 mushwars sshd[11814]: Invalid user http from 61.19.73.45
Feb 12 21:08:57 mushwars sshd[11816]: Invalid user httpd from 61.19.73.45
Feb 12 21:09:00 mushwars sshd[11818]: Invalid user pop from 61.19.73.45
Feb 12 21:09:11 mushwars sshd[11824]: Invalid user backup from 61.19.73.45
Feb 12 21:09:14 mushwars sshd[11826]: Invalid user info from 61.19.73.45
Feb 12 21:09:18 mushwars sshd[11828]: Invalid user shop from 61.19.73.45
Feb 12 21:09:21 mushwars sshd[11830]: Invalid user sales from 61.19.73.45
Feb 12 21:09:24 mushwars sshd[11832]: Invalid user web from 61.19.73.45
Feb 12 21:09:29 mushwars sshd[11834]: Invalid user www from 61.19.73.45
Feb 12 21:09:33 mushwars sshd[11836]: Invalid user wwwrun from 61.19.73.45
Feb 12 21:09:36 mushwars sshd[11838]: Invalid user adam from 61.19.73.45
Feb 12 21:09:40 mushwars sshd[11840]: Invalid user stephen from 61.19.73.45
Feb 12 21:09:43 mushwars sshd[11842]: Invalid user richard from 61.19.73.45
Feb 12 21:09:46 mushwars sshd[11844]: Invalid user george from 61.19.73.45
Feb 12 21:09:50 mushwars sshd[11846]: Invalid user john from 61.19.73.45
Feb 12 21:09:56 mushwars sshd[11850]: Invalid user angel from 61.19.73.45
Feb 12 21:10:03 mushwars sshd[11854]: Invalid user pgsql from 61.19.73.45
Feb 12 21:10:13 mushwars sshd[11876]: Invalid user ident from 61.19.73.45
Feb 12 21:10:17 mushwars sshd[11878]: Invalid user webpop from 61.19.73.45
Feb 12 21:10:20 mushwars sshd[11880]: Invalid user susan from 61.19.73.45
Feb 12 21:10:24 mushwars sshd[11882]: Invalid user sunny from 61.19.73.45
Feb 12 21:10:27 mushwars sshd[11884]: Invalid user steven from 61.19.73.45
Feb 12 21:10:30 mushwars sshd[11886]: Invalid user ssh from 61.19.73.45
Feb 12 21:10:34 mushwars sshd[11888]: Invalid user search from 61.19.73.45
Feb 12 21:10:37 mushwars sshd[11890]: Invalid user sara from 61.19.73.45
Feb 12 21:10:40 mushwars sshd[11892]: Invalid user robert from 61.19.73.45
Feb 12 21:10:44 mushwars sshd[11894]: Invalid user richard from 61.19.73.45
Feb 12 21:10:47 mushwars sshd[11896]: Invalid user party from 61.19.73.45
Feb 12 21:10:50 mushwars sshd[11898]: Invalid user amanda from 61.19.73.45
Feb 12 21:10:53 mushwars sshd[11900]: Invalid user rpm from 61.19.73.45
Feb 12 21:11:00 mushwars sshd[11904]: Invalid user sgi from 61.19.73.45
Feb 12 21:11:06 mushwars sshd[11908]: Invalid user users from 61.19.73.45
Feb 12 21:11:09 mushwars sshd[11910]: Invalid user admins from 61.19.73.45
Feb 12 21:11:13 mushwars sshd[11912]: Invalid user admins from 61.19.73.45
Feb 12 21:11:43 mushwars sshd[11930]: Invalid user dean from 61.19.73.45
Feb 12 21:11:47 mushwars sshd[11932]: Invalid user unknown from 61.19.73.45
Feb 12 21:11:51 mushwars sshd[11935]: Invalid user securityagent from 61.19.73.45
Feb 12 21:11:54 mushwars sshd[11937]: Invalid user tokend from 61.19.73.45
Feb 12 21:11:57 mushwars sshd[11939]: Invalid user windowserver from 61.19.73.45
Feb 12 21:12:00 mushwars sshd[11941]: Invalid user appowner from 61.19.73.45
Feb 12 21:12:04 mushwars sshd[11943]: Invalid user xgridagent from 61.19.73.45
Feb 12 21:12:07 mushwars sshd[11945]: Invalid user agent from 61.19.73.45
Feb 12 21:12:10 mushwars sshd[11947]: Invalid user xgridcontroller from 61.19.73.45
Feb 12 21:12:14 mushwars sshd[11949]: Invalid user jabber from 61.19.73.45
Feb 12 21:12:16 mushwars sshd[11951]: Invalid user amavisd from 61.19.73.45
Feb 12 21:12:20 mushwars sshd[11953]: Invalid user clamav from 61.19.73.45
Feb 12 21:12:23 mushwars sshd[11955]: Invalid user appserver from 61.19.73.45
Feb 12 21:12:27 mushwars sshd[11957]: Invalid user mailman from 61.19.73.45
Feb 12 21:12:30 mushwars sshd[11959]: Invalid user cyrusimap from 61.19.73.45
Feb 12 21:12:33 mushwars sshd[11961]: Invalid user qtss from 61.19.73.45
Feb 12 21:12:36 mushwars sshd[11963]: Invalid user eppc from 61.19.73.45
Feb 12 21:12:39 mushwars sshd[11965]: Invalid user telnetd from 61.19.73.45
Feb 12 21:12:43 mushwars sshd[11967]: Invalid user identd from 61.19.73.45
Feb 12 21:12:46 mushwars sshd[11969]: Invalid user gnats from 61.19.73.45
Feb 12 21:12:50 mushwars sshd[11971]: Invalid user jeff from 61.19.73.45
Feb 12 21:12:53 mushwars sshd[11973]: Invalid user irc from 61.19.73.45
Feb 12 21:12:56 mushwars sshd[11975]: Invalid user list from 61.19.73.45
Feb 12 21:13:00 mushwars sshd[11977]: Invalid user eleve from 61.19.73.45
Feb 12 21:13:03 mushwars sshd[11979]: Invalid user proxy from 61.19.73.45
Feb 12 21:13:06 mushwars sshd[11981]: Invalid user sys from 61.19.73.45
Feb 12 21:13:09 mushwars sshd[11983]: Invalid user zzz from 61.19.73.45
Feb 12 21:13:13 mushwars sshd[11985]: Invalid user frank from 61.19.73.45
Feb 12 21:13:16 mushwars sshd[11987]: Invalid user dan from 61.19.73.45
Feb 12 21:13:19 mushwars sshd[11989]: Invalid user james from 61.19.73.45
Feb 12 21:13:22 mushwars sshd[11991]: Invalid user snort from 61.19.73.45
Feb 12 21:13:26 mushwars sshd[11993]: Invalid user radiomail from 61.19.73.45
Feb 12 21:13:29 mushwars sshd[11995]: Invalid user harrypotter from 61.19.73.45
Feb 12 21:13:33 mushwars sshd[11997]: Invalid user divine from 61.19.73.45
Feb 12 21:13:36 mushwars sshd[11999]: Invalid user popa3d from 61.19.73.45
Feb 12 21:13:39 mushwars sshd[12001]: Invalid user aptproxy from 61.19.73.45
Feb 12 21:13:42 mushwars sshd[12003]: Invalid user desktop from 61.19.73.45
Feb 12 21:13:45 mushwars sshd[12005]: Invalid user workshop from 61.19.73.45
Feb 12 21:13:48 mushwars sshd[12007]: Invalid user mailnull from 61.19.73.45
Feb 12 21:13:51 mushwars sshd[12009]: Invalid user nfsnobody from 61.19.73.45
Feb 12 21:13:54 mushwars sshd[12011]: Invalid user rpcuser from 61.19.73.45
Feb 12 21:13:57 mushwars sshd[12013]: Invalid user rpc from 61.19.73.45
Feb 12 21:14:00 mushwars sshd[12015]: Invalid user gopher from 61.19.73.45
Feb 13 03:34:59 mushwars sshd[12962]: Invalid user tester from 221.224.164.195
Feb 13 03:35:02 mushwars sshd[12964]: Invalid user linux from 221.224.164.195
Feb 13 03:35:04 mushwars sshd[12970]: Invalid user usuario from 221.224.164.195
Feb 13 03:35:07 mushwars sshd[12972]: Invalid user suporte from 221.224.164.195
Feb 13 03:35:10 mushwars sshd[12974]: Invalid user postgres from 221.224.164.195
Feb 13 03:35:28 mushwars sshd[12986]: Invalid user oracle from 221.224.164.195
Feb 13 03:35:30 mushwars sshd[12988]: Invalid user test from 221.224.164.195

```

---

### Post by sablefoxx on 2010-02-14
Oh, okay I guess I can do it properly and use only key based auth.  Thx for the suggestions!

Follow up question, is there a disadvantage is using only one pub key for multiple systems?  I was under the impression you were supposed to have one key per client...

---

### Post by FuturePilot on 2010-02-14
> **sablefoxx said:**
> 
Follow up question, is there a disadvantage is using only one pub key for multiple systems?  

Not that I know of.

---

