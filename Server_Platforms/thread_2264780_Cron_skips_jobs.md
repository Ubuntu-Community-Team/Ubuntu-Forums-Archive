---
title: "Cron skips jobs"
date: 2015-02-10
forum: Server Platforms
---

### Post by sgofferj on 2015-02-10
Hi,

I'm seeing a weird problem at my main server. I have the following entries:
```

# - Weekdays ---------------------------------------------------------------------------
00   07   *    *    1-5  root     /usr/bin/wol bc:ae:c5:bf:45:7c >/dev/null 2>&1

45   05   *    *    1-5  sgofferj /storage/exec/soundalarm.pl Army/FirstCall.mp3 >/dev/null 2>&1
00   06   *    *    1-5  sgofferj /storage/exec/soundalarm.pl Army/Reveille.mp3 A3 >/dev/null 2>&1
45   06   *    *    1-5  sgofferj /storage/exec/soundalarm.pl Army/Reveille.mp3 A3 >/dev/null 2>&1
00   08   *    *    1-5  sgofferj /storage/exec/soundalarm.pl Army/Assembly.mp3 >/dev/null 2>&1
00   18   *    *    1-5  sgofferj /storage/exec/soundalarm.pl Army/Retreat.mp3 >/dev/null 2>&1
00   22   *    *    1-5  sgofferj /storage/exec/soundalarm.pl Army/CallToQuarters.mp3 >/dev/null 2>&1

```

However, during yesterday and today, some of those were skipped. This is an exempt from today's syslog:
```

Feb 10 06:45:01 nostromo CRON[19627]: (sgofferj) CMD (/storage/exec/soundalarm.pl Army/Reveille.mp3 A3 >/dev/null 2>&1)
Feb  8 05:10:01 nostromo CRON[19558]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:42:01 nostromo CRON[19559]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:43:01 nostromo CRON[19583]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:44:01 nostromo CRON[19595]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:45:01 nostromo CRON[19626]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:45:01 nostromo CRON[19627]: (sgofferj) CMD (/storage/exec/soundalarm.pl Army/Reveille.mp3 A3 >/dev/null 2>&1)
Feb 10 06:45:01 nostromo CRON[19628]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 06:45:01 nostromo CRON[19633]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 06:45:01 nostromo CRON[19634]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 06:47:01 nostromo CRON[20326]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:48:01 nostromo CRON[20351]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:49:01 nostromo CRON[20364]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:50:01 nostromo CRON[20386]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb  7 05:40:01 nostromo CRON[20389]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:50:01 nostromo CRON[20389]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 06:50:01 nostromo CRON[20390]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:50:01 nostromo CRON[20391]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 06:53:01 nostromo CRON[21047]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:54:01 nostromo CRON[21067]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:55:01 nostromo CRON[21088]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 06:55:01 nostromo CRON[21089]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 06:55:01 nostromo CRON[21091]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 06:55:01 nostromo CRON[21095]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:56:01 nostromo CRON[21713]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:57:01 nostromo CRON[21732]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 06:58:01 nostromo CRON[21748]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  6 08:07:01 nostromo CRON[21773]: message repeated 2 times: [ (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)]
Feb 10 06:59:01 nostromo CRON[21774]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:00:01 nostromo CRON[21798]: (root) CMD (    /storage/exec/siptop.sh 2>/dev/null 1>/dev/null)
Feb 10 07:00:01 nostromo CRON[21797]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:00:01 nostromo CRON[21801]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:00:01 nostromo CRON[21804]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:00:01 nostromo CRON[21803]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:01:01 nostromo CRON[22459]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  4 22:05:01 nostromo CRON[22504]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:03:01 nostromo CRON[22505]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:04:01 nostromo CRON[22522]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  8 16:28:01 nostromo CRON[22543]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:05:01 nostromo CRON[22543]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:05:01 nostromo CRON[22545]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:05:01 nostromo CRON[22546]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:06:01 nostromo CRON[23170]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:09:01 nostromo CRON[23227]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:09:01 nostromo CRON[23229]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 10 07:10:01 nostromo CRON[23307]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:10:01 nostromo CRON[23310]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:10:01 nostromo CRON[23315]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:13:01 nostromo CRON[23991]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:14:01 nostromo CRON[24011]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  8 01:57:01 nostromo CRON[24019]: message repeated 2 times: [ (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)]
Feb 10 07:15:02 nostromo CRON[24034]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:15:02 nostromo CRON[24035]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb  8 01:58:01 nostromo CRON[24033]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:15:02 nostromo CRON[24039]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:15:02 nostromo CRON[24044]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:16:01 nostromo CRON[24657]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 03:40:02 nostromo CRON[24676]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:17:01 nostromo CRON[24676]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 07:17:01 nostromo CRON[24677]: (root) CMD (    /usr/sbin/ntpdate ntp2.ptb.de >/dev/null 2>&1)
Feb 10 07:18:01 nostromo CRON[24693]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:19:01 nostromo CRON[24713]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:20:01 nostromo CRON[24733]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:20:01 nostromo CRON[24736]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Jan 29 18:43:01 nostromo CRON[24731]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  5 12:20:01 nostromo CRON[24744]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:20:01 nostromo CRON[24744]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb  6 19:35:01 nostromo CRON[25346]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:21:01 nostromo CRON[25347]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:22:01 nostromo CRON[25362]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:23:01 nostromo CRON[25377]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:24:01 nostromo CRON[25389]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:25:01 nostromo CRON[25415]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:25:01 nostromo CRON[25416]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:25:01 nostromo CRON[25419]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:25:01 nostromo CRON[25418]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:28:01 nostromo CRON[26067]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:29:01 nostromo CRON[26078]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:30:01 nostromo CRON[26108]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:30:01 nostromo CRON[26109]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:30:01 nostromo CRON[26112]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:30:01 nostromo CRON[26113]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:31:01 nostromo CRON[26740]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:32:01 nostromo CRON[26763]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:33:01 nostromo CRON[26782]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:34:01 nostromo CRON[26793]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:35:01 nostromo CRON[26820]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:35:01 nostromo CRON[26826]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:35:01 nostromo CRON[26828]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:35:01 nostromo CRON[26827]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:36:01 nostromo CRON[27426]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:37:01 nostromo CRON[27442]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:38:01 nostromo CRON[27464]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:39:01 nostromo CRON[27479]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:39:01 nostromo CRON[27480]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 10 07:40:01 nostromo CRON[27546]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:40:01 nostromo CRON[27549]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:40:01 nostromo CRON[27548]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:40:01 nostromo CRON[27552]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:41:01 nostromo CRON[28181]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:42:01 nostromo CRON[28200]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:43:01 nostromo CRON[28217]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Jan 29 00:59:01 nostromo CRON[28248]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:44:01 nostromo CRON[28249]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Jan 27 22:57:01 nostromo CRON[28285]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:45:01 nostromo CRON[28285]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:45:01 nostromo CRON[28286]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:45:01 nostromo CRON[28289]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:45:01 nostromo CRON[28290]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:47:01 nostromo CRON[28944]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:49:01 nostromo CRON[28984]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:50:01 nostromo CRON[29007]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:50:01 nostromo CRON[29009]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:50:01 nostromo CRON[29010]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:50:01 nostromo CRON[29012]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:51:01 nostromo CRON[29623]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  7 17:38:01 nostromo CRON[29636]: message repeated 2 times: [ (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)]
Feb 10 07:52:01 nostromo CRON[29637]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:54:01 nostromo CRON[29671]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb  5 16:28:01 nostromo CRON[29695]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:55:01 nostromo CRON[29699]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 07:55:01 nostromo CRON[29700]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 07:55:01 nostromo CRON[29711]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 07:56:01 nostromo CRON[30314]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 07:57:01 nostromo CRON[30328]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:00:01 nostromo CRON[30395]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:00:01 nostromo CRON[30396]: (sgofferj) CMD (/storage/exec/soundalarm.pl Army/Assembly.mp3 >/dev/null 2>&1)
Feb 10 08:00:01 nostromo CRON[30400]: (root) CMD (    /storage/exec/siptop.sh 2>/dev/null 1>/dev/null)
Feb  6 05:28:01 nostromo CRON[30401]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:00:01 nostromo CRON[30401]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 08:00:01 nostromo CRON[30402]: (root) CMD (    /storage/webserver/weather/grads/getdata.sh 00)
Feb 10 08:00:01 nostromo CRON[30406]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 08:00:01 nostromo CRON[30412]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 08:01:01 nostromo CRON[31062]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:02:01 nostromo CRON[31076]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:03:01 nostromo CRON[31104]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:04:01 nostromo CRON[31117]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:05:01 nostromo CRON[31148]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 08:05:01 nostromo CRON[31150]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:05:01 nostromo CRON[31151]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 08:05:01 nostromo CRON[31152]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 00:46:01 nostromo CRON[31761]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:06:01 nostromo CRON[31762]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:07:01 nostromo CRON[31792]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:08:01 nostromo CRON[31825]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:09:01 nostromo CRON[31840]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:09:01 nostromo CRON[31841]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 10 08:10:01 nostromo CRON[31921]: (root) CMD (    /storage/exec/checktorrents.sh 2>/dev/null 1>/dev/null)
Feb 10 08:10:01 nostromo CRON[31922]: (root) CMD (    /storage/exec/status-nostromo.sh >/dev/null 2>&1)
Feb 10 08:10:01 nostromo CRON[31923]: (root) CMD (    /storage/exec/checkip.sh 2>/dev/null 1>/dev/null)
Feb 10 08:10:01 nostromo CRON[31925]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:11:01 nostromo CRON[32556]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:12:01 nostromo CRON[32581]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)
Feb 10 08:13:01 nostromo CRON[32600]: (root) CMD (    /storage/exec/checkinternet.sh 2>/dev/null 1>/dev/null)

```

Did you notice the wrong dates in between? What could be the issue here?

---

### Post by TheFu on 2015-02-10
That doesn't look like the correct format for a crontab.

```
m h  dom mon dow   command
```

There isn't any userid. That is controlled by the specific crontab file.  Also, it is good to be reminded that cron doesn't bring much environment with it - so any program/script which depends on any environment settings - like HOME - need that set manually.  Also, paths to any files need to be absolute, not relative. No environment, means no CWD.

Last - trying to access the audio device without the userid being logged into the console brings on another issue.  Ubuntu decided years ago to automatically add the audio group to a user session at login on the console, but not for other logins like ssh.  cron isn't a login at all.  If you want a userid to be able to access the audio devices, that userid needs to be added to the audio group manually.

I'd remove all output redirection to see what the script output is.

The changing of dates ... don't know what that is.  I'd setup a monitor script to watch for that and grab the process list when it happens and perhaps see which process it touching the clock.

---

### Post by sgofferj on 2015-02-10
Well, it's /etc/crontab, not a user crontab...
I probably should have told that that stuff is running for well 7 years without problems. It's not so that I just set it up and it doesn't work. I just switched  from OpenSuSE to Ubuntu server some 9 months ago and thought maybe I'm  running into some Ubuntu-specific issue here. The changing of the times does coincide with the non-execution of the scripts.

---

### Post by TheFu on 2015-02-10
Well, that's the answer then.  If the minute doesn't hit that time in the clock, then cron won't do anything. Is there a time issue?  Does your network have a solid NTP server?  Are other jobs running that change/update the time, causing it to skip?

Having the correct time is a pet peeve of mine. 

Another knowledge gap closed - thanks.  I've never in 25 yrs used /etc/crontab. OTOH, it is there and has 3 things inside it to run anacron jobs for daily, weekly, monthly use.

---

### Post by sgofferj on 2015-02-10
I like to use /etc/crontab because it allows me to manage all central stuff centrally without having to jump between user crontabs.

Ok, so I just trapped the event but still have no idea what caused it. I started xclock on the server and a console with tail-f syslog and stared on the clock. After some minutes, I noticed that the clock seemed to freeze for about 1/4 - half a second. On xclock, the time just froze but at the same time, a cron job came to the log with a messed up time. Very very weird. And definitely something I can't have. I'll try deactivating the automatic update in ntpd now and see if that helps...

---

### Post by TheFu on 2015-02-10
I didn't mean to imply that using /etc/crontab was bad - just that I'd never used it or seen it used.  I'm thinking about moving my crontab management across my 30-ish servers there - easier for ansible to manage 1 file than 5.

About the NTP - the way it works is by constantly monitoring multiple time servers. In theory, those should all be synched to within 100ms - worst case. Perhaps your box is connecting to multiple NTP servers and 1 isn't properly being synched?

If you have multiple machines on the same subnet, make 1 of them the time server and point all the others towards it - remove the other time servers for these "clients" - only 1 box should point externally for time.  I'd recommend the time server NOT be Windows - Windows thinks that +/- 5 minutes is close enough, which is a complete failure, IMHO.

BTW - whenever a system has trouble keeping time, the first thing to check is the CMOS battery.

---

### Post by sgofferj on 2015-02-10
Ok, error also occurs with ntpd disabled. Cron restart doesn't help either. As I mentioned, this server is supposed to be the time server for the network... CMOS battery... after 9 months? The machine runs 24/7. Can a depleted battery affect a running machine? I have to admit that I'm not very competent regarding hardware stuff... The board is an Asus P9D-V with a Xeon E3-1240L V3. Rather quality stuff, I would assume...
The interesting thing is that xclock doesn't show a "wrong" time. It only seems to "freeze" for a short moment. I also went through the process list and checked what could be a trouble maker but nothing jumps at me at first glance...

---

### Post by sgofferj on 2015-02-10
Well, used the opportunity of the downtime to run full updates on all software, firmware, etc. Now, machine is back up. Let's see...

---

### Post by TheFu on 2015-02-10
Quality and reputation means nothing. A failure is a failure and can happen regardless of the board, model, vendor.

[https://unix.stackexchange.com/questions/108283/what-could-cause-the-clock-to-jump-by-5-minutes](https://unix.stackexchange.com/questions/108283/what-could-cause-the-clock-to-jump-by-5-minutes)

I'd setup an every minute crontab that appends to a file with the current date and indents it should the prior line be more than 1.1 min older OR if the date isn't the same.  Look for a pattern. If there is one, look for software modifying the clock - RTC.  If there isn't a pattern, it is probably bad hardware or the cmos battery.

---

### Post by sgofferj on 2015-02-10
Good idea, will do. So far, no weird jumps since the reboot... Let's see. I'll report back if it occurs again and I can track something down.

---

### Post by sgofferj on 2015-03-07
The issue occured again. However, again it seems to be only CRON which sees the time changes.
I kept running this script in a screen:
```
#!/bin/bash

oldTime=$(date +%s)
oldPsOutput=$(ps faux)
while sleep 1
do
  currentTime=$(date +%s)
  currentPsOutput=$(ps faux)
  if [ "$currentTime" -lt "$oldTime" ]  # clock change detected?
  then
    (
        echo '========='
        echo "$currentTime < $oldTime"
        echo "$oldPsOutput"
        echo ':::::::::'
        echo "$currentPsOutput"
    ) | mail -s "Time jump" root
  fi 
  oldPsOutput=$currentPsOutput
  oldTime=$currentTime
done
```
But although I see time jumps in the syslog, I don't get any alarm mails. I start assuming a bug in CRON here...

---

### Post by sgofferj on 2015-03-07
Noticed something else...
The machine is syslog server for 4 servers and 3 network devices of which one is a firewall which logs verbosely, i.e. it logs the hell out of the server.
Still, time jumps sho ONLY in log messages from the local CRON instance. /var/log/firewall does not show a single time jump. Neither do log entries from other local services, e.g. DHCPD, tftpd, bind, etc.
I opened a bug about that now.

---

