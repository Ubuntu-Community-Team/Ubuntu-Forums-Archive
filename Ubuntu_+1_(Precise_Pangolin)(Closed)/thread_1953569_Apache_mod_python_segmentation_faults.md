---
title: "Apache mod_python segmentation faults"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by The Cog on 2012-04-06
Has anyone else seen lots of these on 12.04? I'm using 64-bit server install on vmware. The same MySQL database and apache web pages work perfectly on Debian6 so I don't think it's a coding error.

---

### Post by The Cog on 2012-04-10
Bump.

Does this backtrace from mysql errors.log help point out where the problem might be?
```
[Tue Apr 10 14:36:01 2012] [notice] mod_python (pid=31897, interpreter='172.31.166.200'): Importing module '/var/www/login.py'
[Tue Apr 10 14:36:02 2012] [notice] mod_python (pid=31897, interpreter='172.31.166.200'): Importing module '/var/www/am-console/agents/index.py'
[Tue Apr 10 14:36:03 2012] [notice] child pid 31897 exit signal Segmentation fault (11)
[Tue Apr 10 14:36:03 2012] [notice] child pid 31898 exit signal Segmentation fault (11)
*** glibc detected *** /usr/sbin/apache2: double free or corruption (!prev): 0x00007f3fb40051f0 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7e626)[0x7f3fd9ba9626]
/usr/lib/x86_64-linux-gnu/libmysqlclient.so.18(vio_delete+0x1f)[0x7f3fc28b4aaf]
/usr/lib/x86_64-linux-gnu/libmysqlclient.so.18(end_server+0x35)[0x7f3fc28a1485]
/usr/lib/x86_64-linux-gnu/libmysqlclient.so.18(mysql_close+0x61)[0x7f3fc28a32a1]
/usr/lib/python2.7/dist-packages/_mysql.so(+0x4ff4)[0x7f3fc2db5ff4]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x53a5)[0x7f3fd6dd3845]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x614b)[0x7f3fd6dd45eb]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalCodeEx+0x855)[0x7f3fd6d9e605]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x5420)[0x7f3fd6dd38c0]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x614b)[0x7f3fd6dd45eb]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x614b)[0x7f3fd6dd45eb]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x614b)[0x7f3fd6dd45eb]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalCodeEx+0x855)[0x7f3fd6d9e605]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalFrameEx+0x5420)[0x7f3fd6dd38c0]
/usr/lib/libpython2.7.so.1.0(PyEval_EvalCodeEx+0x855)[0x7f3fd6d9e605]
/usr/lib/libpython2.7.so.1.0(+0x5c7bd)[0x7f3fd6d9e7bd]
/usr/lib/libpython2.7.so.1.0(PyObject_Call+0x53)[0x7f3fd6e82e83]
/usr/lib/libpython2.7.so.1.0(+0x1251cf)[0x7f3fd6e671cf]
/usr/lib/libpython2.7.so.1.0(PyObject_Call+0x53)[0x7f3fd6e82e83]
/usr/lib/libpython2.7.so.1.0(+0x1419eb)[0x7f3fd6e839eb]
/usr/lib/libpython2.7.so.1.0(PyObject_CallMethod+0xc1)[0x7f3fd6e509a1]
/usr/lib/apache2/modules/mod_python.so(+0x1ab33)[0x7f3fd7259b33]
/usr/lib/apache2/modules/mod_python.so(+0x1d15a)[0x7f3fd725c15a]
/usr/sbin/apache2(ap_run_access_checker+0x40)[0x7f3fda9ff4f0]
/usr/sbin/apache2(ap_process_request_internal+0x1ce)[0x7f3fdaa0130e]
/usr/sbin/apache2(ap_process_request+0x190)[0x7f3fdaa14940]
/usr/sbin/apache2(+0x4e778)[0x7f3fdaa11778]
/usr/sbin/apache2(ap_run_process_connection+0x48)[0x7f3fdaa0b658]
/usr/sbin/apache2(+0x57b1c)[0x7f3fdaa1ab1c]
/usr/lib/libapr-1.so.0(+0x2e417)[0x7f3fda133417]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x7e9a)[0x7f3fd9eefe9a]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x6d)[0x7f3fd9c1d4bd]
======= Memory map: ========

```

---

### Post by The Cog on 2012-04-11
Solved. 

One module was accidentally using a module-level reference to a class containing a MySQL connection. This meant that under load, the connecton might be used by multiple mod-python threads at the same time, with something of a conflict of interest. Solution is to ensure that each request gets exclusive use of its own connection - either a connection pool with thread-safe check-out and check-in or a new connection for each request.

Doh!

---

