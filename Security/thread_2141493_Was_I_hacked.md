---
title: "Was I hacked?"
date: 2013-05-02
forum: Security
---

### Post by Trino00 on 2013-05-02
Hi all. 

I notice some weird behavior in the computer from my work and it seems like someone was trying to hack in, but I'm not sure if he got through. The problem is that we have installed an ssh server in this pc and somebody (from work) created a account with an easy password and a hacker got access through this account. Luckily this account did not have root privileges.

I opened the auth.log and there are a lot of entries via ssh trying to gain access to other accounts like the following:

```

Apr 28 22:44:43 <PC> sshd[10578]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<HOST>
Apr 28 22:44:45 <PC> sshd[10578]: Failed password for invalid user test from <IP> port 38978 ssh2
Apr 28 22:44:45 <PC> sshd[10578]: Received disconnect from <IP>: 11: Bye Bye [preauth]
Apr 28 22:44:47 <PC> sshd[10580]: Invalid user webmaster from <IP>
Apr 28 22:44:47 <PC> sshd[10580]: input_userauth_request: invalid user webmaster [preauth]
Apr 28 22:44:47 <PC> sshd[10580]: pam_unix(sshd:auth): check pass; user unknown
Apr 28 22:44:47 <PC> sshd[10580]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<HOST> 
Apr 28 22:44:49 <PC> sshd[10580]: Failed password for invalid user webmaster from <IP> port 40052 ssh2

```

From looking at the look it doesn't seem he got access to another account, but if he did he could have erased the traces. Since I'm not an expert on this I can't be sure...

Is there a way I can get some more information about the attack and check whether or not the hacker got root access?

Also, there are a lot of lines like the following in the log, are they possibly related to the attack?

```

Apr 28 10:47:01 <PC> CRON[389]: pam_unix(cron:session): session closed for user <user>
Apr 28 10:48:01 <PC> CRON[395]: pam_unix(cron:session): session opened for user <user> by (uid=0)
Apr 28 10:48:01 <PC> CRON[395]: pam_unix(cron:session): session closed for user <user>
Apr 28 10:49:01 <PC> CRON[400]: pam_unix(cron:session): session opened for user <user> by (uid=0)
Apr 28 10:49:01 <PC> CRON[400]: pam_unix(cron:session): session closed for user <user>
Apr 28 10:50:01 <PC> CRON[405]: pam_unix(cron:session): session opened for user <user> by (uid=0)
Apr 28 10:50:01 <PC> CRON[405]: pam_unix(cron:session): session closed for user <user>

```


Thanks in advance.

---

### Post by daredent on 2013-05-03
First step is change the password.

Then check this thread.  Good luck.
[http://ubuntuforums.org/showthread.php?t=1424924](http://ubuntuforums.org/showthread.php?t=1424924)

---

### Post by CharlesA on 2013-05-03
All those lines show are invalid users with no successful authentication. Why do you think you got hacked?

If you check the logs and don't see huge gaps or missing logs, you should be "OK"

Check the Did I just get owned page in the Basic Security link in my sig.

---

### Post by CharlesA on 2013-05-03
By the way, your auth.log will probably look something like this:

```
Apr 16 00:46:30 vps sshd[29688]: Invalid user user0 from 115.238.73.16
Apr 16 00:49:12 vps sshd[29859]: Invalid user oracle from 115.238.73.16
Apr 16 00:49:18 vps sshd[29865]: Invalid user nagios from 115.238.73.16
Apr 16 00:50:28 vps sshd[29938]: Invalid user oracle from 115.238.73.16
Apr 16 00:50:30 vps sshd[29941]: Invalid user msr from 115.238.73.16
Apr 16 00:52:40 vps sshd[30073]: Invalid user oracle from 115.238.73.16
Apr 16 00:52:44 vps sshd[30078]: Invalid user test from 115.238.73.16
Apr 16 03:45:21 vps sshd[30616]: Invalid user oracle from 86.109.100.24
Apr 16 03:45:22 vps sshd[30619]: Invalid user test from 86.109.100.24
Apr 16 03:45:34 vps sshd[30635]: Invalid user teamspeak from 86.109.100.24
Apr 16 03:45:36 vps sshd[30637]: Invalid user teamspeak from 86.109.100.24
Apr 16 03:45:38 vps sshd[30639]: Invalid user nagios from 86.109.100.24
Apr 16 03:45:40 vps sshd[30641]: Invalid user postgres from 86.109.100.24
Apr 16 04:29:51 vps sshd[30791]: Did not receive identification string from 54.251.250.122
Apr 16 06:58:32 vps sshd[31550]: Did not receive identification string from 202.28.123.194
Apr 16 07:26:21 vps sshd[31632]: Invalid user teamspeak from 96.45.18.226
Apr 16 07:26:22 vps sshd[31635]: Invalid user nagios from 96.45.18.226
Apr 16 08:03:45 vps sshd[31733]: Invalid user db2inst1 from 183.62.232.93
Apr 16 08:03:49 vps sshd[31738]: Invalid user prueba from 183.62.232.93
Apr 16 08:03:53 vps sshd[31742]: Invalid user postgres from 183.62.232.93
Apr 16 08:04:01 vps sshd[31750]: Invalid user mythtv from 183.62.232.93
Apr 16 08:04:08 vps sshd[31759]: Invalid user kai from 183.62.232.93
Apr 16 08:04:10 vps sshd[31761]: Invalid user mmroot from 183.62.232.93
Apr 16 08:04:20 vps sshd[31771]: Invalid user x from 183.62.232.93
Apr 16 08:04:22 vps sshd[31773]: Invalid user user from 183.62.232.93
Apr 16 08:04:36 vps sshd[31787]: Invalid user rob from 183.62.232.93
Apr 16 08:04:46 vps sshd[31797]: Invalid user organize1 from 183.62.232.93
Apr 16 08:04:48 vps sshd[31799]: Invalid user tommy from 183.62.232.93
Apr 16 08:05:13 vps sshd[31826]: Invalid user www from 183.62.232.93
Apr 16 08:05:21 vps sshd[31834]: Invalid user nagios from 183.62.232.93
Apr 16 08:05:44 vps sshd[31860]: Invalid user alumno from 183.62.232.93
Apr 16 08:06:12 vps sshd[31889]: Invalid user guest from 183.62.232.93
Apr 16 08:06:15 vps sshd[31893]: Invalid user shobo from 183.62.232.93
Apr 16 08:06:23 vps sshd[31901]: Invalid user oratest from 183.62.232.93
Apr 16 08:06:29 vps sshd[31907]: Invalid user mircte from 183.62.232.93
Apr 16 08:06:31 vps sshd[31909]: Invalid user eduis from 183.62.232.93
Apr 16 08:06:33 vps sshd[31911]: Invalid user lions from 183.62.232.93
Apr 16 08:06:35 vps sshd[31913]: Invalid user ftp_wooripa from 183.62.232.93
Apr 16 08:06:37 vps sshd[31915]: Invalid user forevermd from 183.62.232.93
Apr 16 08:06:39 vps sshd[31917]: Invalid user webmaster from 183.62.232.93
Apr 16 08:06:43 vps sshd[31921]: Invalid user ewt from 183.62.232.93
Apr 16 08:06:47 vps sshd[31925]: Invalid user rppt from 183.62.232.93
Apr 16 08:06:49 vps sshd[31927]: Invalid user www from 183.62.232.93
Apr 16 08:06:51 vps sshd[31929]: Invalid user fm from 183.62.232.93
Apr 16 08:06:56 vps sshd[31935]: Invalid user Giani from 183.62.232.93
Apr 16 08:07:12 vps sshd[31952]: Invalid user eb from 183.62.232.93
Apr 16 08:07:18 vps sshd[31958]: Invalid user i-heart from 183.62.232.93
Apr 16 08:07:26 vps sshd[31966]: Invalid user veronique from 183.62.232.93
Apr 16 08:07:28 vps sshd[31968]: Invalid user web from 183.62.232.93
Apr 16 08:07:34 vps sshd[31974]: Invalid user multitrode from 183.62.232.93
Apr 16 08:07:36 vps sshd[31976]: Invalid user public from 183.62.232.93
Apr 16 08:07:41 vps sshd[31982]: Invalid user multirode from 183.62.232.93
Apr 16 08:07:43 vps sshd[31984]: Invalid user filecoupon from 183.62.232.93
Apr 16 08:07:51 vps sshd[31992]: Invalid user eclasi from 183.62.232.93
Apr 16 08:07:55 vps sshd[31996]: Invalid user apple_search from 183.62.232.93
Apr 16 08:07:59 vps sshd[32000]: Invalid user content from 183.62.232.93
Apr 16 08:08:03 vps sshd[32004]: Invalid user httpd from 183.62.232.93
Apr 16 08:08:05 vps sshd[32007]: Invalid user yangjun from 183.62.232.93
Apr 16 08:08:07 vps sshd[32009]: Invalid user trustconsult from 183.62.232.93
Apr 16 08:08:09 vps sshd[32011]: Invalid user mircte from 183.62.232.93
Apr 16 08:08:11 vps sshd[32013]: Invalid user mircte from 183.62.232.93
Apr 16 08:08:15 vps sshd[32017]: Invalid user eduis from 183.62.232.93
Apr 16 08:08:20 vps sshd[32023]: Invalid user ssl from 183.62.232.93
Apr 16 08:08:30 vps sshd[32033]: Invalid user oracle from 183.62.232.93
Apr 16 08:08:34 vps sshd[32037]: Invalid user oracle from 183.62.232.93
Apr 16 08:08:36 vps sshd[32039]: Invalid user oracle from 183.62.232.93
Apr 16 08:08:40 vps sshd[32043]: Invalid user smcgrath from 183.62.232.93
Apr 16 08:08:42 vps sshd[32045]: Invalid user scott from 183.62.232.93
Apr 16 08:08:50 vps sshd[32053]: Invalid user deng from 183.62.232.93
Apr 16 08:08:54 vps sshd[32057]: Invalid user webmaster from 183.62.232.93
Apr 16 08:08:58 vps sshd[32061]: Invalid user webmaster from 183.62.232.93
Apr 16 08:09:02 vps sshd[32065]: Invalid user oracle from 183.62.232.93
Apr 16 08:09:04 vps sshd[32082]: Invalid user nagios from 183.62.232.93
Apr 16 08:09:06 vps sshd[32085]: Invalid user i-heart from 183.62.232.93
Apr 16 08:09:09 vps sshd[32089]: Invalid user utnet from 183.62.232.93
Apr 16 08:09:15 vps sshd[32095]: Invalid user mpsoc from 183.62.232.93
Apr 16 08:09:17 vps sshd[32097]: Invalid user lipo from 183.62.232.93
Apr 16 08:09:25 vps sshd[32105]: Invalid user brightcorea from 183.62.232.93
Apr 16 08:09:27 vps sshd[32107]: Invalid user suniltex from 183.62.232.93
Apr 16 08:09:29 vps sshd[32109]: Invalid user gwool from 183.62.232.93
Apr 16 08:09:31 vps sshd[32111]: Invalid user kkamja from 183.62.232.93
Apr 16 08:09:33 vps sshd[32113]: Invalid user forevermd from 183.62.232.93
Apr 16 08:09:35 vps sshd[32115]: Invalid user quegen from 183.62.232.93
Apr 16 08:09:45 vps sshd[32125]: Invalid user www from 183.62.232.93
Apr 16 08:09:52 vps sshd[32133]: Invalid user ic from 183.62.232.93
Apr 16 08:09:58 vps sshd[32139]: Invalid user sir from 183.62.232.93
Apr 16 08:10:12 vps sshd[32152]: Invalid user ss2701 from 183.62.232.93
Apr 16 08:10:16 vps sshd[32156]: Invalid user dwsadm from 183.62.232.93
Apr 16 08:10:26 vps sshd[32166]: Invalid user mbkim from 183.62.232.93
Apr 16 08:10:30 vps sshd[32170]: Invalid user jhshin from 183.62.232.93
Apr 16 08:10:32 vps sshd[32172]: Invalid user nexus from 183.62.232.93
Apr 16 08:10:38 vps sshd[32180]: Invalid user crond from 183.62.232.93
Apr 16 08:10:47 vps sshd[32190]: Invalid user search from 183.62.232.93
Apr 16 08:10:49 vps sshd[32192]: Invalid user ss2701 from 183.62.232.93
Apr 16 08:10:51 vps sshd[32194]: Invalid user tst from 183.62.232.93
Apr 16 08:13:17 vps sshd[32343]: Invalid user tryit from 183.62.232.93
Apr 16 08:13:23 vps sshd[32350]: Invalid user luis from 183.62.232.93
Apr 16 08:13:25 vps sshd[32352]: Invalid user ip from 183.62.232.93
Apr 16 08:13:27 vps sshd[32354]: Invalid user mpsoc from 183.62.232.93
Apr 16 08:13:31 vps sshd[32358]: Invalid user netcool from 183.62.232.93
Apr 16 08:14:20 vps sshd[32409]: Invalid user public from 183.62.232.93
Apr 16 08:14:25 vps sshd[32415]: Invalid user eggbreaker2 from 183.62.232.93
Apr 16 08:14:27 vps sshd[32417]: Invalid user network from 183.62.232.93
Apr 16 08:14:56 vps sshd[32443]: Invalid user xtreme from 183.62.232.93
Apr 16 08:15:00 vps sshd[32447]: Invalid user ftpd from 183.62.232.93
Apr 16 08:15:02 vps sshd[32449]: Invalid user ale from 183.62.232.93
Apr 16 08:15:09 vps sshd[32458]: Invalid user hub from 183.62.232.93
Apr 16 08:15:21 vps sshd[32470]: Invalid user inx from 183.62.232.93
Apr 16 08:15:29 vps sshd[32480]: Invalid user oracle from 183.62.232.93
Apr 16 08:15:49 vps sshd[32500]: Invalid user guest from 183.62.232.93
Apr 16 08:15:52 vps sshd[32504]: Invalid user oracle from 183.62.232.93
Apr 16 08:16:12 vps sshd[32525]: Invalid user msr from 183.62.232.93
Apr 16 08:16:16 vps sshd[32529]: Invalid user ddtddt from 183.62.232.93
Apr 16 08:16:20 vps sshd[32533]: Invalid user pjtas from 183.62.232.93
Apr 16 08:16:22 vps sshd[32535]: Invalid user whg from 183.62.232.93
Apr 16 08:16:24 vps sshd[32537]: Invalid user sandbox from 183.62.232.93
Apr 16 08:16:33 vps sshd[32547]: Invalid user hub from 183.62.232.93
Apr 16 08:16:35 vps sshd[32549]: Invalid user mooon from 183.62.232.93
Apr 16 08:16:37 vps sshd[32551]: Invalid user bluecore from 183.62.232.93
Apr 16 08:16:39 vps sshd[32553]: Invalid user cjh from 183.62.232.93
Apr 16 08:16:48 vps sshd[32559]: Invalid user info from 183.62.232.93
Apr 16 08:16:50 vps sshd[32561]: Invalid user demuji from 183.62.232.93
Apr 16 08:16:56 vps sshd[32567]: Invalid user diskbook from 183.62.232.93
Apr 16 08:16:58 vps sshd[32569]: Invalid user diskbook from 183.62.232.93
Apr 16 08:17:00 vps sshd[32571]: Invalid user diskbook from 183.62.232.93
Apr 16 08:17:04 vps sshd[32575]: Invalid user firefox from 183.62.232.93
Apr 16 08:17:06 vps sshd[32578]: Invalid user user0 from 183.62.232.93
Apr 16 08:17:10 vps sshd[32582]: Invalid user mysql0 from 183.62.232.93
Apr 16 08:17:12 vps sshd[32584]: Invalid user user0 from 183.62.232.93
Apr 16 08:17:18 vps sshd[32590]: Invalid user firefox from 183.62.232.93
Apr 16 08:17:21 vps sshd[32594]: Invalid user user0 from 183.62.232.93
Apr 16 08:17:25 vps sshd[32598]: Invalid user swsgest from 183.62.232.93
Apr 16 08:17:27 vps sshd[32600]: Invalid user megafile from 183.62.232.93
Apr 16 08:17:29 vps sshd[32602]: Invalid user i-heart from 183.62.232.93
Apr 16 08:17:31 vps sshd[32604]: Invalid user i-heart from 183.62.232.93
Apr 16 08:17:35 vps sshd[32608]: Invalid user bash from 183.62.232.93
Apr 16 08:17:39 vps sshd[32612]: Invalid user taz from 183.62.232.93
Apr 16 08:17:43 vps sshd[32616]: Invalid user PruncuTz from 183.62.232.93
Apr 16 08:17:49 vps sshd[32622]: Invalid user paulb from 183.62.232.93
Apr 16 08:17:51 vps sshd[32624]: Invalid user michael from 183.62.232.93
Apr 16 08:17:57 vps sshd[32630]: Invalid user lday from 183.62.232.93
Apr 16 08:17:59 vps sshd[32632]: Invalid user nagios from 183.62.232.93
Apr 16 08:18:04 vps sshd[32639]: Invalid user svn from 183.62.232.93
Apr 16 08:18:14 vps sshd[32649]: Invalid user joyko from 183.62.232.93
Apr 16 08:18:16 vps sshd[32651]: Invalid user user0 from 183.62.232.93
Apr 16 08:18:22 vps sshd[32657]: Invalid user sshserver from 183.62.232.93
Apr 16 08:18:28 vps sshd[32663]: Invalid user server from 183.62.232.93
Apr 16 08:18:34 vps sshd[32669]: Invalid user vivian from 183.62.232.93
Apr 16 08:18:36 vps sshd[32671]: Invalid user prince from 183.62.232.93
Apr 16 08:18:40 vps sshd[32675]: Invalid user tomcat from 183.62.232.93
Apr 16 08:18:46 vps sshd[32681]: Invalid user lovetravel-ftp from 183.62.232.93
Apr 16 08:18:58 vps sshd[32693]: Invalid user ftpuser from 183.62.232.93
Apr 16 08:19:06 vps sshd[32702]: Invalid user idclicksucai from 183.62.232.93
Apr 16 08:19:07 vps sshd[32704]: Invalid user gamme from 183.62.232.93
Apr 16 08:19:13 vps sshd[32710]: Invalid user xmap from 183.62.232.93
Apr 16 08:19:24 vps sshd[32718]: Invalid user mysqll from 183.62.232.93
Apr 16 08:19:26 vps sshd[32720]: Invalid user test from 183.62.232.93
Apr 16 08:19:34 vps sshd[32728]: Invalid user mysqll from 183.62.232.93
Apr 16 08:19:40 vps sshd[32734]: Invalid user eddy from 183.62.232.93
Apr 16 08:19:48 vps sshd[32742]: Invalid user eddy from 183.62.232.93
Apr 16 08:19:51 vps sshd[32746]: Invalid user moon from 183.62.232.93
Apr 16 08:19:57 vps sshd[32752]: Invalid user vizz from 183.62.232.93
Apr 16 08:19:59 vps sshd[32754]: Invalid user herosys from 183.62.232.93
Apr 16 08:20:17 vps sshd[305]: Invalid user img_data from 183.62.232.93
Apr 16 08:20:23 vps sshd[311]: Invalid user hhzls from 183.62.232.93
Apr 16 08:20:27 vps sshd[315]: Invalid user tanglp from 183.62.232.93
Apr 16 08:20:36 vps sshd[327]: Invalid user ttf from 183.62.232.93
Apr 16 08:20:46 vps sshd[337]: Invalid user template5 from 183.62.232.93
Apr 16 08:20:52 vps sshd[343]: Invalid user appluat from 183.62.232.93
Apr 16 08:20:56 vps sshd[347]: Invalid user appltest from 183.62.232.93
Apr 16 08:21:10 vps sshd[362]: Invalid user plechlo from 183.62.232.93
Apr 16 08:21:12 vps sshd[364]: Invalid user dmd from 183.62.232.93
Apr 16 08:21:14 vps sshd[366]: Invalid user mviara from 183.62.232.93
Apr 16 08:21:50 vps sshd[400]: Invalid user arthur from 183.62.232.93
Apr 16 08:21:52 vps sshd[402]: Invalid user rayyau from 183.62.232.93
Apr 16 08:21:58 vps sshd[408]: Invalid user user0 from 183.62.232.93
Apr 16 08:22:01 vps sshd[413]: Invalid user user0 from 183.62.232.93
Apr 16 08:22:05 vps sshd[419]: Invalid user mark from 183.62.232.93
Apr 16 08:22:37 vps sshd[454]: Invalid user dolby from 183.62.232.93
Apr 16 08:22:39 vps sshd[456]: Invalid user dolby from 183.62.232.93
Apr 16 08:22:41 vps sshd[458]: Invalid user cladhaire from 183.62.232.93
Apr 16 08:22:42 vps sshd[460]: Invalid user mercy from 183.62.232.93
Apr 16 08:22:46 vps sshd[464]: Invalid user paulos from 183.62.232.93
Apr 16 08:22:48 vps sshd[466]: Invalid user lex from 183.62.232.93
Apr 16 08:22:50 vps sshd[468]: Invalid user bkalle from 183.62.232.93
Apr 16 08:22:52 vps sshd[470]: Invalid user tazelaar from 183.62.232.93
Apr 16 08:22:54 vps sshd[472]: Invalid user pabon from 183.62.232.93
Apr 16 08:23:02 vps sshd[480]: Invalid user paul from 183.62.232.93
Apr 16 08:23:10 vps sshd[489]: Invalid user cwalsh from 183.62.232.93
Apr 16 08:23:14 vps sshd[493]: Invalid user cwalsh from 183.62.232.93
Apr 16 08:23:16 vps sshd[495]: Invalid user evil from 183.62.232.93
Apr 16 08:23:48 vps sshd[525]: Invalid user best from 183.62.232.93
Apr 16 08:24:27 vps sshd[566]: Invalid user a from 183.62.232.93
Apr 16 08:24:29 vps sshd[568]: Invalid user fslbsmo from 183.62.232.93
Apr 16 08:24:31 vps sshd[570]: Invalid user danger from 183.62.232.93
Apr 16 08:24:33 vps sshd[572]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:35 vps sshd[574]: Invalid user bash from 183.62.232.93
Apr 16 08:24:37 vps sshd[576]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:39 vps sshd[578]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:45 vps sshd[584]: Invalid user dna1admin from 183.62.232.93
Apr 16 08:24:47 vps sshd[586]: Invalid user test from 183.62.232.93
Apr 16 08:24:53 vps sshd[592]: Invalid user oracle from 183.62.232.93
Apr 16 08:24:55 vps sshd[594]: Invalid user tmax from 183.62.232.93
Apr 16 08:24:58 vps sshd[598]: Invalid user langliguo from 183.62.232.93
Apr 16 08:25:00 vps sshd[600]: Invalid user oracle from 183.62.232.93
Apr 16 08:25:08 vps sshd[609]: Invalid user test from 183.62.232.93
Apr 16 08:25:18 vps sshd[619]: Invalid user royalsoft from 183.62.232.93
Apr 16 08:25:22 vps sshd[623]: Invalid user 2012eduworld-2 from 183.62.232.93
Apr 16 08:25:30 vps sshd[633]: Invalid user perfectpond.org from 183.62.232.93
Apr 16 08:25:34 vps sshd[637]: Invalid user gis from 183.62.232.93
Apr 16 08:25:43 vps sshd[652]: Invalid user jboss from 183.62.232.93
Apr 16 08:25:47 vps sshd[656]: Invalid user ftp from 183.62.232.93
Apr 16 08:26:04 vps sshd[671]: Invalid user ftp2 from 183.62.232.93
Apr 16 08:26:06 vps sshd[674]: Invalid user savitarna from 183.62.232.93
Apr 16 08:26:08 vps sshd[676]: Invalid user robertas from 183.62.232.93
Apr 16 08:26:10 vps sshd[678]: Invalid user tadas from 183.62.232.93
Apr 16 08:26:12 vps sshd[680]: Invalid user tadas from 183.62.232.93
Apr 16 08:26:14 vps sshd[682]: Invalid user robertas from 183.62.232.93
Apr 16 08:26:24 vps sshd[692]: Invalid user savitarna from 183.62.232.93
Apr 16 12:08:25 vps sshd[1140]: Did not receive identification string from 200.77.161.1
Apr 16 14:09:57 vps sshd[1402]: Did not receive identification string from 79.133.201.90
Apr 16 19:18:18 vps sshd[2028]: Did not receive identification string from 202.121.166.203

```

These are just bots trying to bruteforce your ssh server and if you have ssh open to the internet (and it looks like you do), it is usually best to use keys instead of passwords, but if you need to use passwords use a super strong one so it isn't easily cracked.

The above chunk were the access attempts for ***one*** day before I implemented this firewall script:

```

#!/bin/bash

iptables=/sbin/iptables

# Flush current rules
$iptables -F

# Accept Established/Related traffic
$iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Accept ICMP packets
$iptables -A INPUT -p icmp -m limit --limit 1/sec  -j ACCEPT
# Impliment 90 minute lockout by rejecting any connections from an IP that is trying to bruteforce SSH.
# Blame Doug S: http://ubuntuforums.org/showthread.php?t=2137073
# Log anything that gets rejected - Commment this line out if you don't want logging enabled.
$iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j LOG --log-prefix "SSH Attack: " --log-level info
$iptables -A INPUT -m recent --update --hitcount 3 --seconds 5400 --name SSH -j REJECT
$iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --set --name SSH -j ACCEPT
# Allow loopback
$iptables -A INPUT -i lo -j ACCEPT
# Reject everything else
$iptables -A INPUT -j REJECT

```

Now this is what one day of login attempts looks like:
```

Apr 30 00:43:18 vps sshd[24489]: Invalid user tomcat from 61.177.143.130
Apr 30 00:43:19 vps sshd[24492]: Invalid user tomcat from 61.177.143.130
Apr 30 00:43:21 vps sshd[24494]: Invalid user user01 from 61.177.143.130
Apr 30 12:14:10 vps sshd[26043]: Address 178.172.235.46 maps to 178-172-235-46.hoster.by, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr 30 12:14:11 vps sshd[26046]: Address 178.172.235.46 maps to 178-172-235-46.hoster.by, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Apr 30 13:10:55 vps sshd[26166]: Invalid user ant from 61.155.177.58
Apr 30 13:10:57 vps sshd[26169]: Invalid user office from 61.155.177.58
Apr 30 13:10:59 vps sshd[26171]: Invalid user pc from 61.155.177.58
Apr 30 18:17:40 vps sshd[26801]: Did not receive identification string from 202.112.112.236
Apr 30 19:10:15 vps sshd[26913]: Invalid user 1 from 61.177.143.130
Apr 30 19:10:17 vps sshd[26916]: Invalid user a from 61.177.143.130
Apr 30 19:10:18 vps sshd[26918]: Invalid user aaa from 61.177.143.130
Apr 30 19:14:51 vps sshd[26928]: Invalid user 5s1admin from 117.79.91.55
Apr 30 19:14:53 vps sshd[26930]: Invalid user HonestQiao from 117.79.91.55
Apr 30 23:10:18 vps sshd[27417]: Invalid user management from 61.177.143.130
Apr 30 23:10:20 vps sshd[27420]: Invalid user mana from 61.177.143.130
Apr 30 23:10:24 vps sshd[27422]: Invalid user manufacturing from 61.177.143.130

```

Big difference huh?

---

### Post by Trino00 on 2013-05-03
I thought that I was hacked because there are like 8k of attempts to connect to other accounts in less than 3 days. 

Anyway, I'll read the article in pointed out, reconfigure the ssh and use the firewall to increase the security. Thanks!

---

### Post by SlugSlug on 2013-05-03
instal denyhosts it will block IPs when the they fail to login after about 5 attempts

```
 sudo apt-get install denyhosts
```

You could use fail2ban instead/aswell if you have other services like SMTP or FTP

---

### Post by daredent on 2013-05-03
Here is another good starting point:
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by Microrobot on 2013-05-04
For SSH never use default password, if you did not you are fine.

---

### Post by CharlesA on 2013-05-04
> **Microrobot said:**
> For SSH never use default password, if you did not you are fine.

What default password would that be? You pick your own password during install and the root account is locked by default.

---

### Post by HermanAB on 2013-05-04
Years ago, some vagrant made a SSH password brute forcer and my servers got around 10,000 SSH login attempts per hour.  I fixed it with an iptables rate limit rule:
iptables -A INPUT -p tcp --dport 22 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m limit --limit 3/min --limit-burst 3 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP

---

