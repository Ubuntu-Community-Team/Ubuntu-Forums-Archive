---
title: "Not enough signatures found for remote repository"
date: 2019-06-05
forum: Server Platforms
---

### Post by james.w.krych on 2019-06-05
Hello,

I am trying to resolve an issue that appeared on a test server at work and my own server at home. In both, I maintain a mirror of the Ubuntu (18 - Bionic) repos. I have been getting the following error and nothing I do seems to fix the problem:

Not enough signatures found for remote repository update-bionic

I have tried multiple mirrors to sync to and each one gives me the error.
Currently using: [http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) bionic

ANY help would be appreciated.Respectfully,

James

---

### Post by Xian on 2019-06-06
See if this information is helpful:

[https://askubuntu.com/questions/1106362/landscape-standalone-server-18-03-on-ubuntu-18-04-cannot-sync-pocket-from-demo](https://askubuntu.com/questions/1106362/landscape-standalone-server-18-03-on-ubuntu-18-04-cannot-sync-pocket-from-demo)

---

### Post by james.w.krych on 2019-06-07
Yes, I did conduct those steps and still got the same results back.

---

### Post by james.w.krych on 2019-06-07
When I run the following, I get this:

jak238@landscapetest:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key 3B4FE6ACC0B21F32
Executing: /tmp/apt-key-gpghome.KIEK08AjJ0/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-key 3B4FE6ACC0B21F32
gpg: key 3B4FE6ACC0B21F32: 20 signatures not checked due to missing keys
gpg: key 3B4FE6ACC0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jak238@landscapetest:~$

Could someone explain this statement?
"gpg: key 3B4FE6ACC0B21F32: 20 signatures not checked due to missing keys"

And how to resolve?

---

### Post by kc1di on 2019-06-07
It means the key can not be found so it's either obsolete or was not issued correctly try removing that repository from your apt list and re installing it.

---

### Post by james.w.krych on 2019-06-07
Here is what the sources.list reveals
```
#landscapetest:/etc/apt: cat sources.list
#


# deb cdrom:[Ubuntu-Server 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# deb cdrom:[Ubuntu-Server 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
#landscapetest:/etc/apt:
```

---

### Post by #&amp;thj^% on 2019-06-07
you seem to have a hybrid going on here>>Not so good:
IE:
```

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
 deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
 deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
```
You have sources for both 16.04 and 18.04, best way to create total havoc.
**EDIT: after deadflowr added code tags the xenial repos now show commented out, so never mind.**
Please Please use CODE TAGS always...Good Luck

---

### Post by james.w.krych on 2019-06-07
Unfortunately, the initial server was 16.04 but was upgraded. This was working as of several weeks ago without issue.

My server at home was begun strictly as an 18.04LTS, yet it too started having the same issues about a week after this one server.

Which should be commented out?

---

### Post by #&amp;thj^% on 2019-06-07
> **james.w.krych said:**
> Unfortunately, the initial server was 16.04 but was upgraded. This was working as of several weeks ago without issue.

My server at home was begun strictly as an 18.04LTS, yet it too started having the same issues about a week after this one server.

Which should be commented out?

I edited my above post, after deadflowr added the "Very Needed Code Tags" and all looks good now outside of your problem your now experiencing.
BTW: I have stopped using the ubuntu server editions, and moved on.(Just my choice)

---

### Post by james.w.krych on 2019-06-07
Thanks!

---

### Post by #&amp;thj^% on 2019-06-07
Give this a shot, The automatic download using apt-key adv --recv-keys may not work behind a firewall.

In this case, open the webpage of [Ubuntu Key Server ]("http://keyserver.ubuntu.com/")in your web browser and search for the string 0x<hexadecimal code of your missing key or keys>.

---

### Post by james.w.krych on 2019-06-11
Will try again.

James

---

### Post by james.w.krych on 2019-06-11
Okay, I have included screenshots and the results via the command line.

Here is the error:
```
ERROR: Condition '40976EAF437D05B5' not fulfilled for './lists/update-bionic_bionic_InRelease'.
Signatures in './lists/update-bionic_bionic_InRelease':
'3B4FE6ACC0B21F32' (signed 2018-04-26): missing pubkey
Error: Not enough signatures found for remote repository update-bionic ([http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) bionic)!
There have been errors!


```Now, I did go to the Ubuntu Key Server page and entered in the string. These I have the screenshots for.
[ATTACH=CONFIG]283407[/ATTACH][ATTACH=CONFIG]283408[/ATTACH][ATTACH=CONFIG]283409[/ATTACH]


I SSH'd into the server and then sudo'd to root. I used nano to create the NewKey.asc.

Here are the steps and results.

#landscapetest:/root: apt-key add NewKey.asc
OK
#landscapetest:/root:

_***I have to export some settings first.***_

```
#landscapetest:/root: !1849
export LANDSCAPE_API_URI="https://landscapetest/api/"
#landscapetest:/root: !1850
export LANDSCAPE_API_KEY="SHB0OELRFXKZ0LLV2818"
#landscapetest:/root: !1851
export LANDSCAPE_API_SECRET="6IK0yf0Df0tsT6nWurNwdamzmQyZKMxckO2QZvgY"
#landscapetest:/root:

```
[U][I][B]Now, I attempt to sync the repo.
[/B][/I][/U]

```
#landscapetest:/root: landscape-api sync-mirror-pocket release bionic ubuntu
{u'activity_status': u'undelivered',
 u'children': [{u'activity_status': u'undelivered',
                u'children': [],
                u'completion_time': None,
                u'creation_time': u'2019-06-11T06:28:07Z',
                u'creator': {u'email': u'krych@musc.edu',
                             u'id': 1,
                             u'name': u'James Krych'},
                u'id': 280,
                u'modification_time': u'2019-06-11T06:28:07Z',
                u'parent_id': 279,
                u'pocket_id': 25,
                u'pocket_name': u'release',
                u'progress': 0,
                u'result_code': None,
                u'result_text': None,
                u'schedule_after_time': None,
                u'schedule_before_time': None,
                u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
                u'type': u'SyncPocketRequest'}],
 u'completion_time': None,
 u'creation_time': u'2019-06-11T06:28:07Z',
 u'creator': {u'email': u'krych@musc.edu', u'id': 1, u'name': u'James Krych'},
 u'deliver_delay_window': 0,
 u'id': 279,
 u'parent_id': None,
 u'result_code': None,
 u'result_text': None,
 u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
 u'type': u'ActivityGroup'}
#landscapetest:/root:
```

_***Now I query the results to see if it was successful.***_

```
#landscapetest:/root: landscape-api get-activities --query id:280
[{u'activity_status': u'failed',
  u'children': [],
  u'completion_time': u'2019-06-11T06:28:08Z',
  u'creation_time': u'2019-06-11T06:28:07Z',
  u'creator': {u'email': u'krych@musc.edu',
               u'id': 1,
               u'name': u'James Krych'},
  u'id': 280,
  u'modification_time': u'2019-06-11T06:28:08Z',
  u'parent_id': 279,
  u'pocket_id': 25,
  u'pocket_name': u'release',
  u'progress': 0,
  u'result_code': 250,
  u'result_text': u"ERROR: Condition '40976EAF437D05B5' not fulfilled for './lists/update-bionic_bionic_InRelease'.\r\nSignatures in './lists/update-bionic_bionic_InRelease':\r\n'3B4FE6ACC0B21F32' (signed 2018-04-26): missing pubkey\r\nError: Not enough signatures found for remote repository update-bionic ([http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) bionic)!\r\nThere have been errors!\r\n",
  u'schedule_after_time': None,
  u'schedule_before_time': None,
  u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
  u'type': u'SyncPocketRequest'}]
#landscapetest:/root:
```

_***So, as we ca***__***n see, it keeps on failing. Mind you, prior to this all falling apart in early May, syncing the repos completed without any failures.***_

---

### Post by james.w.krych on 2019-08-22
No change.

---

