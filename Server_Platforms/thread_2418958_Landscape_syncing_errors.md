---
title: "Landscape syncing errors"
date: 2019-05-14
forum: Server Platforms
---

### Post by james.w.krych on 2019-05-14
Every week, I attempt to sync my Landscape server to the official repos since I have my clients point to it.

landscape-api sync-mirror-pocket release bionic ubuntu

This is what I get back when I query the progress.

#landscapetest:/root: landscape-api get-activities --query id:218
[{u'activity_status': u'failed',
  u'children': [],
  u'completion_time': u'2019-05-14T12:59:47Z',
  u'creation_time': u'2019-05-14T12:59:45Z',
  u'creator': {u'email': u'krych@musc.edu',
               u'id': 1,
               u'name': u'James Krych'},
  u'id': 218,
  u'modification_time': u'2019-05-14T12:59:47Z',
  u'parent_id': 217,
  u'pocket_id': 10,
  u'pocket_name': u'release',
  u'progress': 0,
  u'result_code': 250,
  u'result_text': u"ERROR: Condition '40976EAF437D05B5' not fulfilled for './lists/update-bionic_bionic_InRelease'.\r\nSignatures in './lists/update-bionic_bionic_InRelease':\r\n'3B4FE6ACC0B21F32' (signed 2018-04-26): missing pubkey\r\nError: Not enough signatures found for remote repository update-bionic ([http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic)!\r\nThere have been errors!\r\n",
  u'schedule_after_time': None,
  u'schedule_before_time': None,
  u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
  u'type': u'SyncPocketRequest'}]
#landscapetest:/root:

I can do this:
 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32

But, I am now getting a mind-block and I am trying to get the exact steps to resolve this issue.

James

---

### Post by james.w.krych on 2019-05-16
I removed all of the previous GPG keys and recreated one, exported it into a file called mirror-key.asc and then imported it into landscape-api. I also recreated the series.

I also restarted using lsctl restart

When I tried the following:
#landscapetest:/root: landscape-api sync-mirror-pocket release bionic ubuntu
{u'activity_status': u'undelivered',
 u'children': [{u'activity_status': u'undelivered',
                u'children': [],
                u'completion_time': None,
                u'creation_time': u'2019-05-16T12:50:10Z',
                u'creator': {u'email': u'krych@musc.edu',
                             u'id': 1,
                             u'name': u'James Krych'},
                u'id': 230,
                u'modification_time': u'2019-05-16T12:50:10Z',
                u'parent_id': 229,
                u'pocket_id': 13,
                u'pocket_name': u'release',
                u'progress': 0,
                u'result_code': None,
                u'result_text': None,
                u'schedule_after_time': None,
                u'schedule_before_time': None,
                u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
                u'type': u'SyncPocketRequest'}],
 u'completion_time': None,
 u'creation_time': u'2019-05-16T12:50:10Z',
 u'creator': {u'email': u'krych@musc.edu', u'id': 1, u'name': u'James Krych'},
 u'deliver_delay_window': 0,
 u'id': 229,
 u'parent_id': None,
 u'result_code': None,
 u'result_text': None,
 u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
 u'type': u'ActivityGroup'}
#landscapetest:/root:

But, when I queried it...
#landscapetest:/root: landscape-api get-activities --query id:230
[{u'activity_status': u'failed',
  u'children': [],
  u'completion_time': u'2019-05-16T12:50:10Z',
  u'creation_time': u'2019-05-16T12:50:10Z',
  u'creator': {u'email': u'krych@musc.edu',
               u'id': 1,
               u'name': u'James Krych'},
  u'id': 230,
  u'modification_time': u'2019-05-16T12:50:10Z',
  u'parent_id': 229,
  u'pocket_id': 13,
  u'pocket_name': u'release',
  u'progress': 0,
  u'result_code': 250,
  u'result_text': u"ERROR: Condition '40976EAF437D05B5' not fulfilled for './lists/update-bionic_bionic_InRelease'.\r\nSignatures in './lists/update-bionic_bionic_InRelease':\r\n'3B4FE6ACC0B21F32' (signed 2018-04-26): missing pubkey\r\nError: Not enough signatures found for remote repository update-bionic ([http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic)!\r\nThere have been errors!\r\n",
  u'schedule_after_time': None,
  u'schedule_before_time': None,
  u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
  u'type': u'SyncPocketRequest'}]
#landscapetest:/root:

---

### Post by james.w.krych on 2019-05-23
Now that my home server is also suffering from this, how can this be resolved?

"u'result_text': u"ERROR: Condition 'CB1CD4BC8644FC41' not fulfilled for './lists/update-bionic_bionic_InRelease'"

---

