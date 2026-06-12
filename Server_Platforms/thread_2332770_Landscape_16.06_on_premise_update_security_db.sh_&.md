---
title: "Landscape 16.06 on premise update_security_db.sh &quot;No JSON object&quot; Error"
date: 2016-08-03
forum: Server Platforms
---

### Post by jeinteractive on 2016-08-03
Issues with the update_security_db.sh script.
It downloads the file but appears to fail when parsing, any suggestions?

> 
Dload  Upload   Total   Spent    Left  Speed
100 9812k  100 9812k    0     0   345k      0  0:00:28  0:00:28 --:--:--  434k'
+ '[' 0 -ne 0 ']'
+ mv -f /var/lib/landscape/usndb.pickle.bz2-new /var/lib/landscape/usndb.pickle.                      bz2
+ cd /opt/canonical/landscape
+ set -o pipefail
+ bzcat /var/lib/landscape/usndb.pickle.bz2
+ ./process-usns /dev/stdin
+ pipe_to_syslog update-security-db
+ tag=update-security-db
++ get_logger_arguments
++ grep -q :
++ echo /dev/log
++ '[' -n /dev/log ']'
++ '[' /dev/log '!=' /dev/log ']'
++ echo ''
+ args=
+ logger -s -p user.error -t update-security-db
update-security-db: Traceback (most recent call last):
update-security-db:   File "./process-usns", line 7, in <module>
update-security-db:     canonical.landscape.scripts.usn.run()
update-security-db:   File "/opt/canonical/landscape/canonical/landscape/scripts                      /batch.py", line 66, in __call__
update-security-db:     code = self.run()
update-security-db:   File "/opt/canonical/landscape/canonical/landscape/scripts                      /usn.py", line 40, in run
update-security-db:     changeset = update_from_usn_tool_db(db)
update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/p                      ackage/usn.py", line 195, in update_from_usn_tool_db
update-security-db:     added=added_package_usns_map, removed=removed_package_us                      ns_map)
update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/p                      ackage/client.py", line 38, in query
update-security-db:     return self._query(method, params)
update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/p                      ackage/client.py", line 60, in _query
update-security-db:     raise PackageSearchRequestError(loads(error.body)["Error                      "])
update-security-db:   File "/usr/lib/python2.7/json/__init__.py", line 338, in l                      oads
update-security-db:     return _default_decoder.decode(s)
update-security-db:   File "/usr/lib/python2.7/json/decoder.py", line 366, in de                      code
update-security-db:     obj, end = self.raw_decode(s, idx=_w(s, 0).end())
update-security-db:   File "/usr/lib/python2.7/json/decoder.py", line 384, in ra                      w_decode
update-security-db:     raise ValueError("No JSON object could be decoded")
update-security-db: ValueError: No JSON object could be decoded
+ '[' 1 -ne 0 ']'
+ alert_admin update_security_db.sh
+ echo 'Error running /opt/canonical/landscape/scripts/update_security_db.sh: 0'
Error running /opt/canonical/landscape/scripts/update_security_db.sh: 0
+ echo 'Check out the syslog output for script update_security_db.sh.'
Check out the syslog output for script update_security_db.sh.
+ exit 1
+ release_lock update_security_db.sh
+ get_distributed_lock update_security_db.sh --release
+ local command=/opt/canonical/landscape/get-distributed-lock
+ /opt/canonical/landscape/get-distributed-lock update_security_db.sh --release
+ rm -f /var/lock/update_security.lock


/var/log/landscape-server/update-security-db.log

> Aug  3 14:17:43 update-security-db ERR  Traceback (most recent call last):
Aug  3 14:17:43 update-security-db ERR    File "./process-usns", line 7, in <module>
Aug  3 14:17:43 update-security-db ERR      canonical.landscape.scripts.usn.run()
Aug  3 14:17:43 update-security-db ERR    File "/opt/canonical/landscape/canonical/landscape/scripts/batch.py", line 66, in __call__
Aug  3 14:17:43 update-security-db ERR      code = self.run()
Aug  3 14:17:43 update-security-db ERR    File "/opt/canonical/landscape/canonical/landscape/scripts/usn.py", line 40, in run
Aug  3 14:17:43 update-security-db ERR      changeset = update_from_usn_tool_db(db)
Aug  3 14:17:43 update-security-db ERR    File "/opt/canonical/landscape/canonical/landscape/model/package/usn.py", line 195, in update_from_usn_tool_db
Aug  3 14:17:43 update-security-db ERR      added=added_package_usns_map, removed=removed_package_usns_map)
Aug  3 14:17:43 update-security-db ERR    File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 38, in query
Aug  3 14:17:43 update-security-db ERR      return self._query(method, params)
Aug  3 14:17:43 update-security-db ERR    File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 60, in _query
Aug  3 14:17:43 update-security-db ERR      raise PackageSearchRequestError(loads(error.body)["Error"])
Aug  3 14:17:43 update-security-db ERR    File "/usr/lib/python2.7/json/__init__.py", line 338, in loads
Aug  3 14:17:43 update-security-db ERR      return _default_decoder.decode(s)
Aug  3 14:17:43 update-security-db ERR    File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
Aug  3 14:17:43 update-security-db ERR      obj, end = self.raw_decode(s, idx=_w(s, 0).end())
Aug  3 14:17:43 update-security-db ERR    File "/usr/lib/python2.7/json/decoder.py", line 384, in raw_decode
Aug  3 14:17:43 update-security-db ERR      raise ValueError("No JSON object could be decoded")
Aug  3 14:17:43 update-security-db ERR  ValueError: No JSON object could be decoded


---

