---
title: "There is something wrong with my trac datebase"
date: 2009-07-09
forum: Server Platforms
---

### Post by wangfeng3769 on 2009-07-09
[SIZE=5][COLOR=Red][SIZE=4];)Hello guys .
       After I create the trac project "test ",I execute the command "sudo tracd --port 8000 /repo/trac/test " at the terminal ,then I write down the adress "http://127.0.1.1:8000/test" in the AD bar,but something happens,It shows in the web page as below:[/SIZE]
[/COLOR][/SIZE]Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/web/api.py", line 377, in send_error
    'text/html')
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/web/chrome.py", line 725, in render_template
    req.chrome[type_].append(
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/web/api.py", line 195, in __getattr__
    value = self.callbacks[name](self)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/web/chrome.py", line 489, in prepare_request
    for category, name, text in contributor.get_navigation_items(req):
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/ticket/web_ui.py", line 163, in get_navigation_items
    if 'TICKET_CREATE' in req.perm:
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/perm.py", line 524, in has_permission
    return self._has_permission(action, resource)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/perm.py", line 538, in _has_permission
    check_permission(action, perm.username, resource, perm)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/perm.py", line 425, in check_permission
    perm)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/perm.py", line 282, in check_permission
    get_user_permissions(username)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/perm.py", line 357, in get_user_permissions
    for perm in self.store.get_user_permissions(username):
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/perm.py", line 173, in get_user_permissions
    db = self.env.get_db_cnx()
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/env.py", line 273, in get_db_cnx
    return DatabaseManager(self).get_connection()
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/db/api.py", line 87, in get_connection
    return self._cnx_pool.get_cnx(self.timeout or None)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/db/pool.py", line 176, in get_cnx
    return _backend.get_cnx(self._connector, self._kwargs, timeout)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/db/pool.py", line 109, in get_cnx
    cnx = connector.get_connection(**kwargs)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/db/sqlite_backend.py", line 126, in get_connection
    return SQLiteConnection(path, log, params)
  File "/usr/local/lib/python2.6/dist-packages/Trac-0.11.5rc1-py2.6.egg/trac/db/sqlite_backend.py", line 179, in __init__
    % (getuser(), path))
[COLOR=Blue]TracError: The user wangfeng requires read _and_ write permissions to the database file /repo/trac/test/db/trac.db and the directory it is located in.
How do I deal  with it .
I need you help . THanks 
[/COLOR]

---

