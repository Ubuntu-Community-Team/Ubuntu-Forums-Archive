---
title: "keystont installation problem"
date: 2013-02-24
forum: Server Platforms
---

### Post by mehdisoltani on 2013-02-24
I installed kestone for OPENSTACK  on ubuntu server 12.04 by the command
[B]apt-get install keystone python-keystone python-keystoneclient
[/B]from the manual which is maintained by Openstack.org
I  modified  **/etc/keystone/keystone**.conf by the instructions.
but when i wanted to restart keyston service that is also written in manual service kestone restart , it could not  stop and start service.
also after the service is restarted this instruction should be run
[B]keystone-manage db_sync
[/B]but it showed me this error
[B]Traceback (most recent call last):
  File "/usr/bin/keystone-manage", line 28, in <module>
    cli.main(argv=sys.argv, config_files=config_files)
  File "/usr/lib/python2.7/dist-packages/keystone/cli.py", line 155, in main
    default_config_files=config_files)
  File "/usr/lib/python2.7/dist-packages/keystone/openstack/common/cfg.py", line 1026, in __call__
    self._parse_config_files()
  File "/usr/lib/python2.7/dist-packages/keystone/openstack/common/cfg.py", line 1492, in _parse_config_files
    raise ConfigFileParseError(pe.filename, str(pe))
keystone.openstack.common.cfg.ConfigFileParseError: Failed to parse /etc/keystone/keystone.conf: at /etc/keystone/keystone.conf:3, Unexpected continuation line: ' admin_token = mehdiadmin'[/B]

please somebody tell me what should i do

---

### Post by mehdisoltani on 2013-02-24
I installed kestone for OPENSTACK  on ubuntu server 12.04 by the command
[B]apt-get install keystone python-keystone python-keystoneclient
[/B]from the manual which is maintained by Openstack.org
I  modified  **/etc/keystone/keystone**.conf by the instructions.
but when i wanted to restart keyston service that is also written in manual service kestone restart , it could not  stop and start service.
also after the service is restarted this instruction should be run
[B]keystone-manage db_sync
[/B]but it showed me this error
[B]Traceback (most recent call last):
  File "/usr/bin/keystone-manage", line 28, in <module>
    cli.main(argv=sys.argv, config_files=config_files)
  File "/usr/lib/python2.7/dist-packages/keystone/cli.py", line 155, in main
    default_config_files=config_files)
  File "/usr/lib/python2.7/dist-packages/keystone/openstack/common/cfg.py", line 1026, in __call__
    self._parse_config_files()
  File "/usr/lib/python2.7/dist-packages/keystone/openstack/common/cfg.py", line 1492, in _parse_config_files
    raise ConfigFileParseError(pe.filename, str(pe))
keystone.openstack.common.cfg.ConfigFileParseError: Failed to parse /etc/keystone/keystone.conf: at /etc/keystone/keystone.conf:3, Unexpected continuation line: ' admin_token = mehdiadmin'[/B]

please somebody tell me what should i do

---

### Post by Sef on 2013-02-24
Please do not duplicate the same problem in different forums.  Thank you.

---

### Post by colossal100 on 2013-02-27
I also had this problem. Removing first space character from the line resolved the problem.
admin_token = password

I think I left the space when I removed the #.

Hope it helps.

---

### Post by Yuanzhen Gu on 2013-06-17
very helpful for me !! thanks!

> **colossal100 said:**
> I also had this problem. Removing first space character from the line resolved the problem.
admin_token = password

I think I left the space when I removed the #.

Hope it helps.

---

